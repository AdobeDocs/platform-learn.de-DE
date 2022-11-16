---
title: Generieren von First-Party-Geräte-IDs
description: Erfahren Sie, wie Erstanbieter-Geräte-IDs generiert werden
feature: Web SDK
kt: 9728
thumbnail: KT-9728.jpeg
exl-id: 2e3c1f71-e224-4631-b680-a05ecd4c01e7
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 2%

---

# Generieren von First-Party-Geräte-IDs

Adobe Experience Cloud-Anwendungen haben traditionell Cookies generiert, um Geräte-IDs mithilfe verschiedener Technologien zu speichern, darunter:

1. Drittanbieter-Cookies
1. Erstanbieter-Cookies, die von einem Adobe-Server mithilfe der CNAME-Konfiguration eines Domänennamens gesetzt werden
1. Von JavaScript gesetzte Erstanbieter-Cookies

Jüngste Browseränderungen beschränken die Dauer dieser Cookie-Typen. Erstanbieter-Cookies sind am effektivsten, wenn sie mit einem kundeneigenen Server festgelegt werden, der einen DNS-A/AAAA-Eintrag anstelle eines DNS-CNAME verwendet. Mit der Erstanbieter-Geräte-ID (FPID)-Funktion können Kunden, die das Adobe Experience Platform Web SDK implementieren, Geräte-IDs in Cookies von Servern verwenden, die DNS-A/AAAA-Einträge verwenden. Diese IDs können dann an Adobe gesendet und als Samen zum Generieren von Experience Cloud-IDs (ECIDs) verwendet werden, die in Adobe Experience Cloud-Anwendungen weiterhin die primäre Kennung sind.

Im Folgenden finden Sie ein kurzes Beispiel für die Funktionsweise der Funktion:

![Erstanbieter-Geräte-IDs (FPIDs) und Experience Cloud-IDs (ECIDs)](../assets/kt-9728.png)

1. Der Browser eines Endbenutzers fordert eine Webseite vom Webserver oder CDN eines Kunden an.
1. Der Kunde generiert eine Geräte-ID (FPID) auf seinem Webserver oder CDN (der Webserver sollte mit dem DNS-A/AAAA-Datensatz des Domänennamens verknüpft sein).
1. Der Kunde setzt ein Erstanbieter-Cookie, um die FPID im Browser des Endbenutzers zu speichern.
1. Die Adobe Experience Platform Web SDK-Implementierung des Kunden sendet eine Anfrage an das Platform Edge Network, einschließlich der FPID in der Identitätszuordnung.
1. Experience Platform Edge Network empfängt die FPID und generiert mit ihr eine Experience Cloud-ID (ECID).
1. Die Antwort des Platform Web SDK sendet die ECID zurück an den Browser des Endbenutzers.
1. Platform Web SDK verwendet JavaScript, um die ECID als `AMCV_` -Cookie im Browser des Endbenutzers.
1. Im Ereignis wird die `AMCV_` -Cookie abläuft, wiederholt sich der Prozess selbst. Solange dieselbe Erstanbieter-Geräte-ID verfügbar ist, wird ein neuer `AMCV_` -Cookie mit demselben ECID-Wert wie zuvor erstellt.

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
>Das Identitäts-Namespace-Symbol, das in der Identitätszuordnung verwendet wird, muss aufgerufen werden `FPID`.
>
> `FPID` ist ein reservierter Identitäts-Namespace, der nicht in den Benutzeroberflächenlisten von Identitäts-Namespaces angezeigt wird.


## ECID-Generierung validieren

Validieren Sie die Implementierung, indem Sie sicherstellen, dass dieselbe ECID von Ihrer Erstanbieter-Geräte-ID generiert wird:

1. Generieren Sie ein FPID-Cookie.
1. Senden Sie mit dem Platform Web SDK eine Anfrage an Platform Edge Network.
1. Ein Cookie im Format `AMCV_<IMSORGID@AdobeOrg>` generiert wird. Dieses Cookie enthält die ECID.
1. Notieren Sie sich den generierten Cookie-Wert und löschen Sie dann alle Cookies für Ihre Site mit Ausnahme der `FPID` Cookie.
1. Senden Sie eine weitere Anfrage an Platform Edge Network.
1. Bestätigen Sie den Wert im `AMCV_<IMSORGID@AdobeOrg>` Cookie ist dasselbe `ECID` Wert wie in `AMCV_` -Cookie, das gelöscht wurde. Wenn der Cookie-Wert für eine bestimmte FPID identisch ist, war der Sitzungsprozess für die ECID erfolgreich.

Weitere Informationen zu dieser Funktion finden Sie unter [die Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html).
