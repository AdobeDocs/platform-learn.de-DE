---
title: Authentifizieren und Zugreifen auf Experience Platform-APIs
description: Erfahren Sie, wie Sie auf Adobe Experience Platform-APIs zugreifen können.
role: Developer
feature: API
kt: 3688
thumbnail: 28832.jpeg
last-substantial-update: 2023-06-21T00:00:00Z
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
source-git-commit: 60f509ef55ce121f572466a8f13953dba982a0ce
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 16%

---

# Authentifizierung und Zugriff [!DNL Experience Platform] APIs

Für Anfragen an Adobe Experience Platform-APIs benötigen Sie ein Entwicklerkonto für Experience Platformen.

## Erstellen eines Projekts in der Adobe Developer Console und Exportieren einer Postman-Umgebung

[[!DNL Postman]](https://www.postman.com/) ist ein Tool, mit dem Entwickler schnell und einfach mit Adobe Experience Platform-APIs interagieren können.

Die Adobe Developer-Konsole **Exportdetails für Postman** -Funktion bietet eine einfache Möglichkeit, alle Kontodetails zu exportieren, die für den Zugriff auf eine Experience Platform-API und deren Interaktion mit einer Postman-Umgebungsdatei erforderlich sind. Dadurch entfällt die Notwendigkeit, Werte aus der Adobe Developer-Konsole in Postman zu kopieren und einzufügen.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?quality=12&learn=on)

>[!IMPORTANT]
>
>Nachdem Sie Ihre API-Anmeldedaten erstellt haben, muss ein Systemadministrator in Ihrem Unternehmen die Berechtigung mit einer Experience Platform verknüpfen.


## Generieren eines Zugriffstokens mit Postman

Verwenden Sie die [Adobe Identity Management Service-APIs](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) , um ein Zugriffstoken für den Zugriff auf die Adobe Experience Platform-APIs zu erhalten.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?quality=12&learn=on)


## Interagieren mit Experience Platform-APIs mit Postman

Erkunden Sie die Interaktion mit Adobe Experience Platform-APIs mithilfe des [Von der Adobe bereitgestellte Experience Platform API - Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), aufbauend auf [Umgebungsvariablen der Adobe Developer-Konsole](#export-adobe-io-integration-details-to-postman) und [generiertes Zugriffstoken](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?quality=12&learn=on)


## Weitere Ressourcen

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [Beispiele für Adobe Experience Platform Postman](https://github.com/adobe/experience-platform-postman-samples)
   * [Identity Management System Postman Collection zum Generieren von Zugriffstoken](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
   * [Adobe Experience Platform API Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Postman herunterladen](https://www.postman.com/)
