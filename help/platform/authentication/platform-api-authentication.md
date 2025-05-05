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
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 10%

---

# Authentifizieren und Zugreifen auf [!DNL Experience Platform] APIs

Erfahren Sie mehr über die ersten Schritte mit Adobe Experience Platform-APIs. Dieses Tutorial führt Sie durch den Prozess zum Erstellen von Authentifizierungsdaten und zum Erstellen von Experience Platform-API-Anfragen.

## Erstellen eines Projekts in Adobe Developer Console und Exportieren einer Postman-Umgebung{#export-integration-details-to-postman}

[[!DNL Postman]](https://www.postman.com/) ist ein Drittanbieterprogramm, mit dem Entwickler schnell und einfach mit Adobe Experience Platform-APIs interagieren können.

Die Funktion [&#128279;](https://developer.adobe.com/console/home)**Details für Postman exportieren** von Adobe Developer Console bietet eine einfache Möglichkeit, die Kontodetails zu exportieren, die für den Zugriff auf und die Interaktion mit Experience Platform-APIs in einer einzigen Postman-Umgebungsdatei erforderlich sind, sodass Werte von Adobe Developer Console nicht mehr kopiert und in Postman eingefügt werden müssen.

>[!IMPORTANT]
>
>Um auf die [Adobe Developer Console](https://developer.adobe.com/console/home) zugreifen zu können, müssen Sie entweder [Systemadministrator](https://helpx.adobe.com/de/enterprise/using/admin-roles.html) oder [Entwickler](https://helpx.adobe.com/de/enterprise/using/manage-developers.html#:~:text=Add%20developers%20to%20a%20single%20product%20profile&amp;text=In%20the%20Admin%20Console%2C%20navigate,in%20the%20upper%2Dright%20corner.) in der [Adobe Admin Console ](https://adminconsole.adobe.com).
>
> Nachdem Sie Ihre API-Anmeldedaten erstellt haben, muss ein Systemadministrator die Anmeldedaten mit einer Rolle in der Experience Platform verknüpfen.

>[!VIDEO](https://video.tv.adobe.com/v/31575/?learn=on&enablevpops&captions=ger)

## Erstellen eines Zugriffs-Tokens mit Postman{#generate-an-access-token-with-postman}

Verwenden Sie die [Adobe Identity Management Service APIs](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) um ein Zugriffstoken für den Zugriff auf die Adobe Experience Platform APIs zu erhalten.

>[!VIDEO](https://video.tv.adobe.com/v/32919/?learn=on&enablevpops&captions=ger)


## Interagieren mit Experience Platform-APIs mithilfe von Postman

Erkunden Sie die Interaktion mit Adobe Experience Platform-APIs mithilfe der [von Adobe bereitgestellten Experience Platform-API](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)Postman-Sammlungen, die auf den [Adobe Developer Console-Umgebungsvariablen ](#export-integration-details-to-postman) dem [generierten Zugriffstoken](#generate-an-access-token-with-postman) aufbauen.

>[!VIDEO](https://video.tv.adobe.com/v/32918/?learn=on&enablevpops&captions=ger)


## In diesen Videos referenzierte Ressourcen

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [Beispiele für Adobe Experience Platform Postman](https://github.com/adobe/experience-platform-postman-samples)
   * [Identity Management System Postman Collection zum Generieren von Zugriffstoken](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
   * [Adobe Experience Platform API Postman-Sammlungen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Postman herunterladen](https://www.postman.com/)
