---
title: Echtzeit-Kundendatenplattform - Erstellen Sie ein Segment und ergreifen Sie Maßnahmen - Senden Sie Ihr Segment an DV360
description: Echtzeit-Kundendatenplattform - Erstellen Sie ein Segment und ergreifen Sie Maßnahmen - Senden Sie Ihr Segment an DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 7a78260f-cd25-4ed0-801b-87174babaffe
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 3%

---

# 6.3 Maßnahmen ergreifen: Senden Ihres Segments an DV360

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](../module2/images/sb1.png)

Gehen Sie im linken Menü zu **Ziele**, gehen Sie dann zu **Katalog**. Sie werden dann die **Zielkatalog**.

![RTCDP](./images/rtcdpmenudest.png)

In **Ziele**, klicken Sie auf die **Segmente aktivieren** auf **Google Display &amp; Video 360** Karte.

![RTCDP](./images/rtcdpgoogleseg.png)

Wählen Sie Ihr Ziel aus und klicken Sie auf **Nächste**.

![RTCDP](./images/rtcdpcreatedest2.png)

Wählen Sie in der Liste der verfügbaren Segmente das Segment aus, das Sie in der vorherigen Übung erstellt haben. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest3.png)

Im **Segmentplan** Seite, klicken Sie auf **Nächste**.

![RTCDP](./images/rtcdpcreatedest4.png)

Abschließend zur **Überprüfen** Seite, klicken Sie auf **Beenden**.

![RTCDP](./images/rtcdpcreatedest5.png)

Ihr Segment ist jetzt mit Google DV360 verknüpft. Jedes Mal, wenn sich ein Kunde für dieses Segment qualifiziert, wird ein Signal an Google DV360 gesendet, um diesen Kunden bei Google DV360 in die Zielgruppe aufzunehmen.

Nächster Schritt: [6.4 Maßnahmen ergreifen: Senden Ihres Segments an ein S3-Ziel](./ex4.md)

[Zurück zu Modul 6](./real-time-cdp-build-a-segment-take-action.md)

[Zu allen Modulen zurückkehren](../../overview.md)
