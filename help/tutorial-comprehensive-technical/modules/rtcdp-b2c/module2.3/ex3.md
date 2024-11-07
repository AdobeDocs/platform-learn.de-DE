---
title: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln - Senden Sie Ihr Segment an DV360
description: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln - Senden Sie Ihr Segment an DV360
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 2%

---

# 2.3.3 Aktion durchführen: Senden Sie Ihr Segment an DV360

Wechseln Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende [!UICONTROL Sandbox] ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Wechseln Sie im linken Menü zu **Ziele** und gehen Sie dann zu **Katalog**. Daraufhin wird der **Zielkatalog** angezeigt.

![RTCDP](./images/rtcdpmenudest.png)

Klicken Sie in **Ziele** auf der Karte **Google Display &amp; Video 360** auf die Schaltfläche **Segmente aktivieren** .

![RTCDP](./images/rtcdpgoogleseg.png)

Wählen Sie Ihr Ziel aus und klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest2.png)

Wählen Sie in der Liste der verfügbaren Segmente das Segment aus, das Sie in der vorherigen Übung erstellt haben. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest3.png)

Klicken Sie auf der Seite **Segmentplan** auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4.png)

Klicken Sie abschließend auf der Seite **Überprüfen** auf **Beenden**.

![RTCDP](./images/rtcdpcreatedest5.png)

Ihr Segment ist jetzt mit Google DV360 verknüpft. Jedes Mal, wenn sich ein Kunde für dieses Segment qualifiziert, wird ein Signal an Google DV360 gesendet, um diesen Kunden bei Google DV360 in die Zielgruppe aufzunehmen.

Nächster Schritt: [2.3.4 Aktion ausführen: Senden Sie Ihr Segment an ein S3-Ziel](./ex4.md)

[Zurück zu Modul 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
