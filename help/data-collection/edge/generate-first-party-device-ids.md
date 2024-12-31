---
title: Erstanbieter-Geräte-IDs generieren
description: Erfahren Sie, wie Erstanbieter-Geräte-IDs generiert werden
feature: Web SDK
level: Experienced
jira: KT-9728
thumbnail: KT-9728.jpeg
exl-id: 2e3c1f71-e224-4631-b680-a05ecd4c01e7
source-git-commit: fd60f7ad338c81f5b32e7951d5a00b49c5aa1756
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# Erstanbieter-Geräte-IDs generieren

Adobe Experience Cloud-Anwendungen haben herkömmlicherweise Cookies generiert, um Geräte-IDs mit verschiedenen Technologien zu speichern, darunter:

1. Drittanbieter-Cookies
1. Erstanbieter-Cookies, die von einem Adobe-Server mithilfe der CNAME-Konfiguration eines Domain-Namens gesetzt werden
1. Erstanbieter-Cookies, die von JavaScript gesetzt werden

Jüngste Browser-Änderungen beschränken die Dauer dieser Cookie-Typen. Erstanbieter-Cookies sind am effektivsten, wenn sie mit einem kundeneigenen Server gesetzt werden, der einen DNS-A/AAAA-Eintrag anstelle eines DNS-CNAME verwendet. Mit [ Funktion „First-Party Device ID (FPID)“ ](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/identity/first-party-device-ids) Kunden, die Adobe Experience Platform Web SDK implementieren, Geräte-IDs in Cookies von Servern verwenden, die DNS-A/AAAA-Einträge verwenden. Diese IDs können dann an Adobe gesendet und als Seeds zum Generieren von Experience Cloud-IDs (ECIDs) verwendet werden, die weiterhin die primäre Kennung in Adobe Experience Cloud-Programmen sind.

Im Folgenden finden Sie ein kurzes Beispiel dafür, wie die Funktion funktioniert:

![First-Party-Geräte-IDs (FPIDs) und Experience Cloud-IDs (ECIDs)](../assets/kt-9728.png)

1. Der Browser eines Endbenutzers fordert eine Web-Seite vom Webserver oder CDN eines Kunden an.
1. Der Kunde generiert eine Geräte-ID (FPID) auf seinem Webserver oder CDN (der Webserver sollte an den DNS-A/AAAA-Eintrag des Domain-Namens gebunden sein).
1. Der Kunde setzt ein Erstanbieter-Cookie, um die FPID im Browser des Endbenutzers zu speichern.
1. Die Adobe Experience Platform Web SDK-Implementierung des Kunden stellt eine Anfrage an das Platform-Edge Network und führt eine der folgenden Aktionen aus:
   1. Schließt die FPID in die Identitätszuordnung ein.
   1. Konfiguriert einen CNAME für die Web-SDK-Anfragen und konfiguriert den Datenstrom mit dem Namen des FPID-Cookies.
1. Das Experience Platform-Edge Network empfängt die FPID und verwendet sie, um eine Experience Cloud-ID (ECID) zu generieren.
1. Die Antwort von Platform Web SDK sendet die ECID zurück an den Browser des Endbenutzers.
1. Wenn der `idMigrationEnabled=true` ist, verwendet Platform Web SDK JavaScript, um die ECID als `AMCV_` Cookie im Browser des Endbenutzers zu speichern.
1. Falls das `AMCV_`-Cookie abläuft, wiederholt sich der Prozess von selbst. Sofern dieselbe First-Party-Geräte-ID verfügbar ist, wird ein neues `AMCV_`-Cookie mit demselben ECID-Wert wie zuvor erstellt.

>[!NOTE]
>
>Die `idMigrationEnabled` muss nicht auf `true` gesetzt werden, um FPID zu verwenden. Bei `idMigrationEnabled=false` wird jedoch möglicherweise kein `AMCV_`-Cookie angezeigt. Sie müssen in der Netzwerkantwort nach dem ECID-Wert suchen.


In diesem Tutorial wird ein spezifisches Beispiel unter Verwendung der PHP-Skriptsprache verwendet, um Folgendes zu zeigen:

* Generieren eines UUIDv4
* Schreiben des UUIDv4-Werts in ein Cookie
* Cookie-Wert in die Identitätszuordnung einschließen
* Validieren der ECID-Generierung

Weitere Informationen zu Erstanbieter-Geräte-IDs finden Sie in der Produktdokumentation.

## Generieren eines UUIDv4

PHP hat keine native Bibliothek für die UUID-Generierung, sodass diese Code-Beispiele umfangreicher sind, als es wahrscheinlich wäre, wenn eine andere Programmiersprache verwendet würde. PHP wurde für dieses Beispiel gewählt, weil es eine häufig unterstützte Server-seitige Sprache ist.


Wenn die folgende Funktion aufgerufen wird, generiert sie eine zufällige UUID Version 4:

```
<?php
    
    function guidv4($data)
    {
        $data = $data ?? random_bytes(16);

        $data[6] = chr(ord($data[6]) & 0x0f | 0x40); // set version to 0100
        $data[8] = chr(ord($data[8]) & 0x3f | 0x80); // set bits 6-7 to 10

        return vsprintf('%s%s-%s-%s-%s-%s%s%s', str_split(bin2hex($data), 4));
    }

?>
```

## Schreiben des UUIDv4-Werts in ein Cookie

Der folgende Code führt eine -Anfrage an die oben stehende Funktion durch, um eine UUID zu generieren. Anschließend werden die von Ihrem Unternehmen beschlossenen Cookie-Flags gesetzt. Wenn bereits ein Cookie generiert wurde, wird die Gültigkeit verlängert.

```
<?php

    if(!isset($_COOKIE['FPID'])) {
        $cookie_value = guidv4(openssl_random_pseudo_bytes(16));        
        $arr_cookie_options = array (
        'expires' => time() + 60*60*24*30*13,
        'path' => '/',
        'domain' => 'mysiteurl.com',
        'secure' => true,
        'httponly' => true,
        'samesite' => 'lax'
        );
        setcookie($cookie_name, $cookie_value, $arr_cookie_options);
        $_COOKIE[$cookie_name] = $cookie_value;
    }
    else {
        $cookie_value = $_COOKIE[$cookie_name];
        $arr_cookie_options = array (
        'expires' => time() + 60*60*24*30*13,
        'path' => '/',
        'domain' => 'mysiteurl.com',
        'secure' => true,
        'httponly' => true,
        'samesite' => 'lax'
        );
        setcookie($cookie_name, $cookie_value, $arr_cookie_options);
    }

?>
```

>[!NOTE]
>
>Das Cookie, das die First-Party-Geräte-ID enthält, kann einen beliebigen Namen haben.

## Einschließen des Cookie-Werts in die Identitätszuordnung

Der letzte Schritt besteht darin, PHP zu verwenden, um den Cookie-Wert in die Identity Map zu übernehmen.


```
{
    "identityMap": {
        "FPID": [
                    {
                        "id": "<? echo $_COOKIE[$cookie_name] ?>",
                        "authenticatedState": "ambiguous",
                        "primary": true
                    }
                ]
        }
}
```

>[!IMPORTANT]
>
>Das in der Identitätszuordnung verwendete Identity-Namespace-Symbol muss `FPID` aufgerufen werden.
>
> `FPID` ist ein reservierter Identity-Namespace, der nicht in den Benutzeroberflächenlisten von Identity-Namespaces sichtbar ist.


## Validieren der ECID-Generierung

Überprüfen Sie die Implementierung, indem Sie bestätigen, dass dieselbe ECID von Ihrer First-Party-Geräte-ID generiert wird:

1. Erzeugen eines FPID-Cookies.
1. Senden Sie mit Platform Web SDK eine Anfrage an Platform Edge Network.
1. Es wird ein Cookie im Format `AMCV_<IMSORGID@AdobeOrg>` generiert. Dieses Cookie enthält die ECID.
1. Notieren Sie sich den generierten Cookie-Wert und löschen Sie dann alle Cookies für Ihre Site mit Ausnahme des `FPID`-Cookies.
1. Senden Sie eine weitere Anfrage an das Platform-Edge Network.
1. Bestätigen Sie, dass der Wert im `AMCV_<IMSORGID@AdobeOrg>`-Cookie mit dem `ECID` Wert im gelöschten `AMCV_`-Cookie übereinstimmt. Wenn der Cookie-Wert für eine bestimmte FPID gleich ist, war der Seeding-Prozess für die ECID erfolgreich.

Weitere Informationen zu dieser Funktion finden Sie unter [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html).
