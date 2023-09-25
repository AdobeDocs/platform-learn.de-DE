---
title: Authentifizieren und Zugreifen auf Experience Platform-APIs
description: Erfahren Sie, wie Sie auf Adobe Experience Platform-APIs zugreifen können.
feature: API
role: Developer
level: Beginner
jira: KT-3688
thumbnail: 28832.jpeg
last-substantial-update: 2023-06-21T00:00:00Z
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 18%

---

# Authentifizieren und Aufrufen von [!DNL Experience Platform]-APIs

Erfahren Sie mehr über die ersten Schritte mit Adobe Experience Platform-APIs. Dieses Tutorial führt Sie durch den Prozess zum Erstellen von Authentifizierungsberechtigungen und zum Starten von Experience Platform-API-Anfragen.

## Erstellen eines Projekts in der Adobe Developer Console und Exportieren einer Postman-Umgebung{#export-integration-details-to-postman}

[[!DNL Postman]](https://www.postman.com/) ist eine Drittanbieteranwendung, mit der Entwickler schnell und einfach mit Adobe Experience Platform-APIs interagieren können.

[Die Adobe Developer-Konsole](https://developer.adobe.com/console/home) **Exportdetails für Postman** -Funktion bietet eine einfache Möglichkeit, die Kontodetails zu exportieren, die für den Zugriff auf Experience Platform-APIs und die Interaktion mit ihnen in einer einzigen Postman-Umgebungsdatei erforderlich sind. So müssen Werte nicht von der Adobe Developer-Konsole in Postman kopiert und eingefügt werden.

>[!IMPORTANT]
>
>So greifen Sie auf die [Adobe Developer-Konsole](https://developer.adobe.com/console/home), müssen Sie entweder [Systemadministrator](https://helpx.adobe.com/de/enterprise/using/admin-roles.html) oder [Entwickler](https://helpx.adobe.com/enterprise/using/manage-developers.html#:~:text=Add%20developers%20to%20a%20single%20product%20profile&amp;text=In%20the%20Admin%20Console%2C%20navigate,in%20the%20upper%2Dright%20corner.) im [Adobe Admin Console](https://adminconsole.adobe.com).
>
> Nachdem Sie Ihre API-Anmeldedaten erstellt haben, muss ein Systemadministrator die Berechtigung mit einer Rolle im Experience Platform verknüpfen.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?learn=on)

## Generieren eines Zugriffstokens mit Postman{#generate-an-access-token-with-postman}

Verwenden Sie die [Adobe Identity Management Service-APIs](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) , um ein Zugriffstoken für den Zugriff auf die Adobe Experience Platform-APIs zu erhalten.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?learn=on)


## Interagieren mit Experience Platform-APIs mithilfe von Postman

Erkunden Sie die Interaktion mit Adobe Experience Platform-APIs mithilfe des [Von Adobe bereitgestellte Experience Platform API-Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), aufbauend auf [Umgebungsvariablen der Adobe Developer-Konsole](#export-integration-details-to-postman) und [generiertes Zugriffstoken](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?learn=on)


## In diesen Videos referenzierte Ressourcen

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [Beispiele für Adobe Experience Platform Postman](https://github.com/adobe/experience-platform-postman-samples)
   * [Identity Management System Postman Collection zum Generieren von Zugriffstoken](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
   * [Adobe Experience Platform API Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Postman herunterladen](https://www.postman.com/)
