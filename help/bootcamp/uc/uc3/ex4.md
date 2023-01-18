---
title: Bootcamp - Zusammenfügen von physischem und digitalem - Testen Sie Ihre Journey
description: Bootcamp - Zusammenfügen von physischem und digitalem - Testen Sie Ihre Journey
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 45c77177-9ea9-4c3d-a40e-c04a747938eb
source-git-commit: ead28f5631fc430c41e8c756b23dc69ffe19510e
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 1%

---

# 3.4 Journey testen

Um Ihre Journey zu testen, müssen Sie die Ereignis-ID des Ereignisses verwenden, das Sie in Übung 3.2 erstellt haben. Diese sieht wie folgt aus.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, damit der Journey Trigger werden kann. In diesem Beispiel lautet die eventID:
`e76c0bf0c77c3517e5b6f4c457a0754ebaf5f1f6b9357d74e0d8e13ae517c3d5`.

Öffnen Sie die mobile App und rufen Sie die Startseite auf. Klicken Sie auf das Symbol **Einstellungen**.

![DSN](./images/appsett.png)

Fügen Sie Ihre eventID in das Feld ein. **Beacon EventID** und klicken Sie auf **Speichern**.

![DSN](./images/beacon1.png)

Bevor Sie fortfahren, öffnen Sie bitte diese Webseite auf Ihrem Computer: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html)

Daraufhin sehen Sie Folgendes:

![DSN](./images/screen1.png)

Gehen Sie dann zurück zur Homepage. Klicken Sie auf **Beacon** Symbol.

![DSN](./images/app23.png)

Dann wirst du das sehen. Wählen Sie zuerst **Bootcamp Screen Beacon** und klicken Sie dann auf **Einstieg** Schaltfläche. Auf diese Weise können Sie einen Beacon-Eintrag simulieren.

![DSN](./images/app21.png)

Sehen Sie sich nun den Bildschirm im Geschäft an. Das zuletzt angezeigte Produkt wird innerhalb von 5 Sekunden angezeigt.

![DSN](./images/beacon3.png)

Sie erhalten auch Ihre Push-Benachrichtigung.

![DSN](./images/beacon2.png)

Du bist jetzt mit dieser Übung fertig.

[Zurück zum Benutzerfluss 3](./uc3.md)

[Zu allen Modulen zurückkehren](../../overview.md)
