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

Adobe Experience Cloud-Anwendungen haben traditionell Cookies generiert, um Geräte-IDs mithilfe verschiedener Technologien zu speichern, darunter:

1. Drittanbieter-Cookies
1. Erstanbieter-Cookies, die von einem Adobe-Server mithilfe der CNAME-Konfiguration eines Domänennamens gesetzt werden
1. Von JavaScript gesetzte Erstanbieter-Cookies

Jüngste Browseränderungen beschränken die Dauer dieser Cookie-Typen. Erstanbieter-Cookies sind am effektivsten, wenn sie mit einem kundeneigenen Server festgelegt werden, der einen DNS-A/AAAA-Eintrag anstelle eines DNS-CNAME verwendet. Mit der Funktion [ Erstanbieter-Geräte-ID (FPID)](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/identity/first-party-device-ids) können Kunden, die das Adobe Experience Platform Web SDK implementieren, Geräte-IDs in Cookies von Servern verwenden, die DNS-A/AAAA-Einträge verwenden. Diese IDs können dann an Adobe gesendet und als Samen zum Generieren von Experience Cloud-IDs (ECIDs) verwendet werden, die in Adobe Experience Cloud-Anwendungen weiterhin die primäre Kennung ist.

Im Folgenden finden Sie ein kurzes Beispiel für die Funktionsweise der Funktion:

![Erstanbieter-Geräte-IDs (FPIDs) und Experience Cloud-IDs (ECIDs)](../assets/kt-9728.png)

1. Der Browser eines Endbenutzers fordert eine Webseite vom Webserver oder CDN eines Kunden an.
1. Der Kunde generiert eine Geräte-ID (FPID) auf seinem Webserver oder CDN (der Webserver sollte mit dem DNS-A/AAAA-Datensatz des Domänennamens verknüpft sein).
1. Der Kunde setzt ein Erstanbieter-Cookie, um die FPID im Browser des Endbenutzers zu speichern.
1. Die Adobe Experience Platform Web SDK-Implementierung des Kunden sendet eine Anfrage an das Platform-Edge Network und entweder:
   1. Beinhaltet die FPID in der Identitätszuordnung.
   1. Konfiguriert einen CNAME für ihre Web SDK-Anforderungen und konfiguriert ihren Datenspeicher mit dem Namen ihres FPID-Cookies.
1. Experience Platform Edge Network erhält die FPID und generiert mit ihr eine Experience Cloud ID (ECID).
1. Die Antwort des Platform Web SDK sendet die ECID zurück an den Browser des Endbenutzers.
1. Wenn das `idMigrationEnabled=true`, verwendet das Platform Web SDK JavaScript, um die ECID als das `AMCV_` -Cookie im Browser des Endbenutzers zu speichern.
1. Wenn das `AMCV_` -Cookie abläuft, wiederholt sich der Prozess selbst. Solange dieselbe Erstanbieter-Geräte-ID verfügbar ist, wird ein neues `AMCV_` -Cookie mit demselben ECID-Wert wie zuvor erstellt.

>[!NOTE]
>
>Die `idMigrationEnabled` muss nicht auf `true` gesetzt werden, um die FPID zu verwenden. Bei `idMigrationEnabled=false` wird jedoch möglicherweise kein `AMCV_` -Cookie angezeigt und muss in der Netzwerkantwort nach dem ECID-Wert suchen.


In diesem Tutorial wird anhand eines Beispiels, das die PHP-Skriptsprache verwendet, gezeigt, wie:

* Generieren einer UUIDv4
* UUIDv4-Wert in ein Cookie schreiben
* Cookie-Wert in die Identitätszuordnung aufnehmen
* ECID-Generierung validieren

Weitere Dokumentationen zu Erstanbieter-Geräte-IDs finden Sie in der Produktdokumentation.

## Generieren einer UUIDv4

PHP verfügt nicht über eine native Bibliothek für die UUID-Generierung, daher sind diese Codebeispiele umfangreicher als das, was wahrscheinlich erforderlich wäre, wenn eine andere Programmiersprache verwendet würde. PHP wurde für dieses Beispiel ausgewählt, weil es eine weithin unterstützte Server-seitige Sprache ist.


Wenn die folgende Funktion aufgerufen wird, generiert sie eine zufällige UUID-Version-4:

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

## UUIDv4-Wert in ein Cookie schreiben

Der folgende Code sendet eine Anfrage an die oben genannte Funktion, um eine UUID zu generieren. Anschließend werden die von Ihrem Unternehmen festgelegten Cookie-Flags festgelegt. Wenn bereits ein Cookie generiert wurde, wird die Gültigkeit verlängert.

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
>Das Cookie, das die Erstanbieter-Geräte-ID enthält, kann einen beliebigen Namen haben.

## Cookie-Wert in die Identity Map einschließen

Der letzte Schritt besteht darin, PHP zu verwenden, um den Cookie-Wert mit der Identity Map zu verbinden.


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
>Das Identitäts-Namespace-Symbol, das in der Identitätszuordnung verwendet wird, muss `FPID` heißen.
>
> `FPID` ist ein reservierter Identitäts-Namespace, der nicht in den Benutzeroberflächenlisten der Identitäts-Namespaces angezeigt wird.


## ECID-Generierung validieren

Validieren Sie die Implementierung, indem Sie sicherstellen, dass dieselbe ECID von Ihrer Erstanbieter-Geräte-ID generiert wird:

1. Generieren Sie ein FPID-Cookie.
1. Senden Sie mit dem Platform Web SDK eine Anfrage an Platform Edge Network.
1. Es wird ein Cookie im Format `AMCV_<IMSORGID@AdobeOrg>` generiert. Dieses Cookie enthält die ECID.
1. Notieren Sie sich den generierten Cookie-Wert und löschen Sie dann alle Cookies für Ihre Site mit Ausnahme des Cookies `FPID` .
1. Senden Sie eine weitere Anfrage an Platform Edge Network.
1. Vergewissern Sie sich, dass der Wert im `AMCV_<IMSORGID@AdobeOrg>` -Cookie mit dem Wert `ECID` übereinstimmt, der im gelöschten `AMCV_` -Cookie gesetzt wurde. Wenn der Cookie-Wert für eine bestimmte FPID identisch ist, war der Sitzungsprozess für die ECID erfolgreich.

Weitere Informationen zu dieser Funktion finden Sie in der [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html).
