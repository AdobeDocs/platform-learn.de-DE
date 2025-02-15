---
title: Erste Schritte mit Firefly Services
description: Erfahren Sie, wie Sie Postman und Adobe I/O verwenden, um Adobe Firefly Services-APIs abzufragen
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: 5ee9c3b7cde5444ecceca4b01cc275d6263d8a59
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 1.1.1 Erste Schritte mit Firefly Services

Erfahren Sie, wie Sie Postman und Adobe I/O verwenden, um Adobe Firefly Services-APIs abzufragen.

## Voraussetzungen für 1.1.1.1

Bevor Sie mit dieser Übung fortfahren, müssen Sie das Setup von [Ihr Adobe I/O-Projekt](./../../../modules/getting-started/gettingstarted/ex6.md) abgeschlossen haben. Außerdem müssen Sie eine Anwendung für die Interaktion mit APIs konfiguriert haben, z. B. [Postman](./../../../modules/getting-started/gettingstarted/ex7.md) oder [PostBuster](./../../../modules/getting-started/gettingstarted/ex8.md).

## 1.1.1.2 Adobe I/O - access_token

Wählen Sie in der Sammlung **Adobe IO - OAuth** die Anfrage mit dem Namen **POST - Zugriffstoken abrufen** und klicken Sie auf **Senden**. Die Antwort sollte ein neues &quot;**&quot;**.

![Postman](./images/ioauthresp.png){zoomable="yes"}

## 1.1.1.3 Firefly Services-API, Text 2 Bild

Nachdem Sie nun über ein gültiges und neues Zugriffs-Token verfügen, können Sie Ihre erste Anfrage an Firefly Services-APIs senden.

Wählen Sie die Anfrage **POST - Firefly - T2I V3** aus der Sammlung **FF - Firefly Services Tech Insiders** aus.

![Firefly](./images/ff1.png){zoomable="yes"}

Kopieren Sie die Bild-URL aus der Antwort und öffnen Sie sie in Ihrem Webbrowser, um das Bild anzuzeigen.

![Firefly](./images/ff2.png){zoomable="yes"}

Sie sollten ein schönes Bild sehen, das `horses in a field` darstellt.

![Firefly](./images/ff3.png){zoomable="yes"}

Sie können mit der API-Anfrage spielen, bevor Sie mit der nächsten Übung fortfahren.

## Nächste Schritte

Navigieren Sie zu [Optimieren Ihres Firefly-Prozesses mit Microsoft Azure und vordefinierten URLs](./ex2.md){target="_blank"}

Zurück zu [Übersicht über Adobe Firefly Services](./firefly-services.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
