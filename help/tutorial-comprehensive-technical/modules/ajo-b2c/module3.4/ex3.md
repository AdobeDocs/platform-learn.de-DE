---
title: Adobe Journey Optimizer - Anwenden der Personalisierung in einer E-Mail-Nachricht
description: In dieser Übung wird erläutert, wie die Segmentpersonalisierung in einem E-Mail-Inhalt verwendet wird
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 10%

---

# 3.4.3 Personalisierung in einer E-Mail-Nachricht anwenden

Melden Sie sich bei Adobe Experience Cloud an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Adobe Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepTenantId--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** .

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

## 3.4.3.1 Segmentbasierte Personalisierung

In dieser Übung verbessern Sie Ihre Newsletter-E-Mail-Nachricht mit einem personalisierten Text, der auf der Segmentmitgliedschaft basiert.

Wechseln Sie zu **Journey**. Suchen Sie die Newsletter-Journey, die Sie in der vorherigen Übung erstellt haben. Suchen Sie nach `--aepUserLdap-- - Newsletter`. Klicken Sie auf Ihre Journey, um sie zu öffnen.

![Journey Optimizer](./images/sbp1.png)

Dann wirst du das sehen. Klicken Sie auf **Duplizieren**.

![Journey Optimizer](./images/sbp2.png)

Klicken Sie auf **Duplizieren**.

![Journey Optimizer](./images/sbp3.png)

Wählen Sie die Aktion **E-Mail** aus und klicken Sie auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/sbp3a.png)

Klicken Sie auf **E-Mail an Designer senden**.

![Journey Optimizer](./images/sbp4.png)

Dann wirst du das sehen.

![Journey Optimizer](./images/sbp5.png)

Öffnen Sie **Inhaltskomponenten** und ziehen Sie eine Komponente **Text** unter den aktuellen Newsletter-Inhalt.

![Journey Optimizer](./images/sbp6.png)

Wählen Sie den gesamten Standardtext aus und löschen Sie ihn. Klicken Sie dann in der Symbolleiste auf die Schaltfläche **Personalisierung hinzufügen** .

![Journey Optimizer](./images/sbp7.png)

Daraufhin sehen Sie Folgendes:

![Journey Optimizer](./images/seg1.png)

Klicken Sie im linken Menü auf **Segmentmitgliedschaften**.

![Journey Optimizer](./images/seg2.png)

>[!NOTE]
>
>Wenn Sie Ihr Segment nicht in dieser Liste finden, scrollen Sie nach unten, um Anweisungen zum manuellen Abrufen der Segment-ID zu erhalten.

Wählen Sie das Segment `Luma - Women's Category Interest` aus und klicken Sie auf das Symbol **+** , das wie folgt aussehen soll:

![Journey Optimizer](./images/seg3.png)

Lassen Sie dann die erste Zeile unverändert und ersetzen Sie die Zeilen 2 und 3 durch diesen Code:

``
    Psssst... a private sale in the women category will launch soon, we will keep you posted
{%else%}
    Thanks for taking the time to read our newsletter. Here is a 10% promo code to use on the website: READER10
{%/if%}
``

Dann haben Sie Folgendes:

![Journey Optimizer](./images/seg4.png)

Klicken Sie auf **Validieren** , um sicherzustellen, dass der Code korrekt ist. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/sbp8.png)

Sie können diese Nachricht jetzt speichern, indem Sie oben rechts auf die Schaltfläche **Speichern** klicken. Klicken Sie dann auf **Inhalt simulieren**.

![Journey Optimizer](./images/sbp9.png)

Wählen Sie eines der Profile aus, die Sie im Rahmen dieses Tutorials erstellt haben, und klicken Sie auf **Vorschau**. Sie sehen dann das Ergebnis Ihrer Konfiguration.

![Journey Optimizer](./images/sbp10.png)

Dann wirst du das sehen. Klicken Sie dann auf **Close**.

![Journey Optimizer](./images/sbp10fff.png)

Gehen Sie zurück zum Nachrichten-Dashboard, indem Sie in der oberen linken Ecke auf den Pfeil **11} neben dem Betreffzeilentext klicken.**

![Journey Optimizer](./images/sbp11.png)

Klicken Sie auf den Pfeil oben links, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/oc79afff.png)

Klicken Sie auf **OK** , um Ihre E-Mail-Aktion zu schließen.

![Journey Optimizer](./images/oc79bfff.png)

Ändern Sie Ihren **Zeitplan** in **einmal** und definieren Sie ein **Datum/Uhrzeit**. Klicken Sie auf **OK**.

>[!NOTE]
>
>Datum und Uhrzeit des Nachrichtenversands müssen innerhalb von mehr als einer Stunde liegen.

![Journey Optimizer](./images/sbp18.png)

Klicken Sie auf die Schaltfläche **Publish** im Journey.

![Journey Optimizer](./images/sbp19.png)

Klicken Sie erneut im Popup-Fenster auf **Publish** .

![Journey Optimizer](./images/sbp20.png)

Ihre grundlegende Newsletter-Journey ist jetzt veröffentlicht. Ihre Newsletter-E-Mail-Nachricht wird nach Ihrem Zeitplan gesendet und Ihre Journey wird beendet, sobald die letzte E-Mail gesendet wurde.

![Journey Optimizer](./images/sbp20fff.png)

Du hast diese Übung beendet.

Nächster Schritt: [3.4.4 Push-Benachrichtigungen für iOS einrichten und verwenden](./ex4.md)

[Zurück zu Modul 3.4](./journeyoptimizer.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
