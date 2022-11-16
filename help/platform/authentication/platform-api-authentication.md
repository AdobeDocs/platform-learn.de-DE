---
title: Authentifizieren und Zugreifen auf Experience Platform-APIs
description: Erfahren Sie, wie Sie auf Adobe Experience Platform-APIs zugreifen können.
role: Developer
feature: API
kt: 3688
thumbnail: 28832.jpeg
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 11%

---

# Authentifizierung und Zugriff [!DNL Experience Platform] APIs

Um Adobe Experience Platform-APIs aufrufen zu können, müssen Sie zunächst Zugriff auf ein Experience Platform-Entwicklerkonto erhalten.

Eine schrittweise Anleitung zum Zugriff auf ein Entwicklerkonto finden Sie unter [Tutorial zur Authentifizierung der Experience Platform-API](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html?lang=de).

## Erstellen und Exportieren der Experience Platform API in Postman

[Postman](https://www.getpostman.com/) ist ein Tool, mit dem Entwickler schnell und einfach mit Adobe Experience Platform-APIs interagieren können.

Die Adobe Developer-Konsole **Exportdetails für Postman** -Funktion bietet eine einfache Möglichkeit, alle Kontodetails zu exportieren, die für den Zugriff auf eine Experience Platform-API und deren Interaktion mit einer Postman-Umgebungsdatei erforderlich sind. Dadurch entfällt die Notwendigkeit, Werte aus der Adobe Developer-Konsole in Postman zu kopieren und einzufügen.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?quality=12&learn=on)

## Generieren eines Zugriffstokens mit Postman

Verwenden Sie die [Adobe Identity Management Service-APIs](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) , um ein Zugriffstoken für den Zugriff auf die Adobe Experience Platform-APIs zur Nicht-Produktions-Verwendung abzurufen

>[!VIDEO](https://video.tv.adobe.com/v/29698/?quality=12&learn=on)

>[!WARNING]
>
> Wie in der Postman-Sammlung zur Adobe I/O Access Token-Generierung angegeben, sind die angegebenen Generierungsmethoden für die Nicht-Produktionsumgebung geeignet. &quot;Lokales Signieren&quot;lädt eine JavaScript-Bibliothek von einem Drittanbieter-Host und das Remote-Signieren sendet den privaten Schlüssel an einen von Adoben verwalteten und verwalteten Webdienst. Während Adobe diesen privaten Schlüssel nicht speichert, sollten Produktionsschlüssel nie für andere freigegeben werden.

## Interagieren mit Adobe I/O-APIs mit Postman

Erkunden Sie die Interaktion mit Adobe I/O-APIs mithilfe der [Von der Adobe bereitgestellte Experience Platform API - Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), aufbauend auf [Umgebungsvariablen der Adobe I/O](#export-adobe-io-integration-details-to-postman) und [generiertes Zugriffstoken](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?quality=12&learn=on)

Beachten Sie, dass von der Adobe bereitgestellte Postman-Sammlungen möglicherweise nicht für jede Adobe I/O-API vorhanden sind. Die [Experience Platform API Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform) kann als Anleitung zum Definieren eigener Postman-Sammlungen für diese Anwendungsfälle verwendet werden.

## Weitere Ressourcen

* [Adobe I/O Console](https://console.adobe.io)
* [Beispiele für Adobe Experience Platform Postman](https://github.com/adobe/experience-platform-postman-samples)
   * [Postman-Sammlung für die Generierung von Adobe I/O-Zugriffstoken](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
   * [Adobe Experience Platform APIs Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Postman herunterladen](https://www.getpostman.com/)
