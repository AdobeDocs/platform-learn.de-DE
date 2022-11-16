---
title: Adobe Journey Optimizer - Anwenden der Personalisierung in einer E-Mail-Nachricht
description: In dieser Übung erfahren Sie, wie Sie die Segmentpersonalisierung in einem E-Mail-Inhalt verwenden.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 573ecfba-4f1d-4242-8358-1d33109aaea3
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 11%

---

# 10.3 Personalisierung in einer E-Mail-Nachricht anwenden

Melden Sie sich bei Adobe Experience Cloud an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Adobe Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

Sie werden zum **Startseite** in Journey Optimizer anzeigen. Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepTenantId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm.

![ACOP](../module7/images/acoptriglp.png)

## 10.3.1 Segmentbasierte Personalisierung

In dieser Übung verbessern Sie Ihre Newsletter-E-Mail-Nachricht mit einem personalisierten Text, der auf der Segmentmitgliedschaft basiert.

Navigieren Sie zu **Journey**. Suchen Sie die Newsletter-Journey, die Sie in der vorherigen Übung erstellt haben. Suchen Sie nach `--demoProfileLdap-- - Newsletter`. Klicken Sie auf Ihre Journey, um sie zu öffnen.

![Journey Optimizer](./images/sbp1.png)

Dann wirst du das sehen. Klicken Sie auf **Duplizieren**.

![Journey Optimizer](./images/sbp2.png)

Klicken Sie auf ** Duplizieren**.

![Journey Optimizer](./images/sbp3.png)

Wählen Sie Ihre **Email** Aktion und klicken Sie auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/sbp3a.png)

Klicken **Email Designer**.

![Journey Optimizer](./images/sbp4.png)

Dann wirst du das sehen.

![Journey Optimizer](./images/sbp5.png)

Öffnen **Inhaltskomponenten** und ziehen Sie eine **Text** -Komponente unterhalb des aktuellen Newsletterinhalts.

![Journey Optimizer](./images/sbp6.png)

Wählen Sie den gesamten Standardtext aus und löschen Sie ihn. Klicken Sie dann auf die **Personalisierung hinzufügen** in der Symbolleiste.

![Journey Optimizer](./images/sbp7.png)

Daraufhin sehen Sie Folgendes:

![Journey Optimizer](./images/seg1.png)

Klicken Sie im linken Menü auf **Segmentzugehörigkeiten**.

![Journey Optimizer](./images/seg2.png)

>[!NOTE]
>
>Wenn Sie Ihr Segment nicht in dieser Liste finden, scrollen Sie nach unten, um Anweisungen zum manuellen Abrufen der Segment-ID zu erhalten.

Segment auswählen `Luma - Women's Category Interest` und klicken Sie auf **+** -Symbol, das wie folgt aussehen sollte:

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

Klicken **Bestätigen** um sicherzustellen, dass der Code korrekt ist. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/sbp8.png)

Sie können diese Nachricht jetzt speichern, indem Sie auf **Speichern** in der oberen rechten Ecke. Klicken Sie anschließend auf **Inhalt simulieren**.

![Journey Optimizer](./images/sbp9.png)

Wählen Sie eines der Profile aus, die Sie im Rahmen dieses Tutorials erstellt haben, und klicken Sie auf **Vorschau**. Sie sehen dann das Ergebnis Ihrer Konfiguration.

![Journey Optimizer](./images/sbp10.png)

Dann wirst du das sehen. Klicken Sie anschließend auf **Schließen**.

![Journey Optimizer](./images/sbp10fff.png)

Gehen Sie zum Nachrichten-Dashboard zurück, indem Sie auf die Schaltfläche **Pfeil** neben dem Betreffzeilentext in der oberen linken Ecke.

![Journey Optimizer](./images/sbp11.png)

Klicken Sie auf den Pfeil in der oberen linken Ecke, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/oc79afff.png)

Klicken **Ok** um Ihre E-Mail-Aktion zu schließen.

![Journey Optimizer](./images/oc79bfff.png)

Ändern Sie Ihre **Zeitplan** nach **Einmal** und definieren Sie eine **Datum/Uhrzeit**. Klicken Sie auf **OK**.

>[!NOTE]
>
>Datum und Uhrzeit des Nachrichtenversands müssen innerhalb von mehr als einer Stunde liegen.

![Journey Optimizer](./images/sbp18.png)

Klicken Sie auf **Veröffentlichen** in der Journey.

![Journey Optimizer](./images/sbp19.png)

Klicken Sie im Popup-Fenster auf **Veröffentlichen** erneut.

![Journey Optimizer](./images/sbp20.png)

Ihre grundlegende Newsletter-Journey ist jetzt veröffentlicht. Ihre Newsletter-E-Mail-Nachricht wird nach Ihrem Zeitplan gesendet und Ihre Journey wird beendet, sobald die letzte E-Mail gesendet wurde.

![Journey Optimizer](./images/sbp20fff.png)

Du hast diese Übung beendet.

Nächster Schritt: [10.4 Push-Benachrichtigungen für iOS einrichten und verwenden](./ex4.md)

[Zurück zu Modul 10](./journeyoptimizer.md)

[Zu allen Modulen zurückkehren](../../overview.md)
