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
source-wordcount: '263'
ht-degree: 10%

---

# [!DNL Experience Platform]-APIs authentifizieren und aufrufen

Erfahren Sie mehr über die ersten Schritte mit Adobe Experience Platform-APIs. Dieses Tutorial führt Sie durch den Prozess zum Erstellen von Authentifizierungsberechtigungen und zum Starten von Experience Platform-API-Anfragen.

## Erstellen eines Projekts in Adobe Developer Console und Exportieren einer Postman-Umgebung{#export-integration-details-to-postman}

[[!DNL Postman]](https://www.postman.com/) ist eine Drittanbieteranwendung, mit der Entwickler schnell und einfach mit Adobe Experience Platform-APIs interagieren können.

Die Funktion [Adobe Developer Console](https://developer.adobe.com/console/home) **Exportdetails für Postman** bietet eine einfache Möglichkeit, die Kontodetails zu exportieren, die für den Zugriff auf und die Interaktion mit Experience Platform-APIs in einer einzelnen Postman-Umgebungsdatei erforderlich sind. So müssen Werte nicht mehr aus Adobe Developer Console kopiert und in Postman eingefügt werden.

>[!IMPORTANT]
>
>Um auf den [Adobe Developer Console](https://developer.adobe.com/console/home) zugreifen zu können, müssen Sie entweder ein [Systemadministrator](https://helpx.adobe.com/de/enterprise/using/admin-roles.html) oder ein [Entwickler](https://helpx.adobe.com/enterprise/using/manage-developers.html#:~:text=Add%20developers%20to%20a%20single%20product%20profile&amp;text=In%20the%20Admin%20Console%2C%20navigate,in%20the%20upper%2Dright%20corner.) in der [Adobe Admin Console](https://adminconsole.adobe.com) sein.
>
> Nachdem Sie Ihre API-Anmeldedaten erstellt haben, muss ein Systemadministrator die Berechtigung mit einer Rolle im Experience Platform verknüpfen.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?learn=on)

## Generieren eines Zugriffstokens mit Postman{#generate-an-access-token-with-postman}

Verwenden Sie die [Adobe Identity Management-Dienst-APIs](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) , um ein Zugriffstoken für den Zugriff auf die Adobe Experience Platform-APIs abzurufen.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?learn=on)


## Interagieren mit Experience Platform-APIs mithilfe von Postman

Erkunden Sie die Interaktion mit Adobe Experience Platform-APIs mithilfe der [vom Adobe bereitgestellten Experience Platform API Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), basierend auf den [Adobe Developer Console-Umgebungsvariablen](#export-integration-details-to-postman) und dem [generierten Zugriffstoken](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?learn=on)


## In diesen Videos referenzierte Ressourcen

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [Adobe Experience Platform Postman-Beispiele](https://github.com/adobe/experience-platform-postman-samples)
   * [Identity Management System Postman Collection zum Generieren von Zugriffstoken](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
   * [Adobe Experience Platform API Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Postman herunterladen](https://www.postman.com/)
