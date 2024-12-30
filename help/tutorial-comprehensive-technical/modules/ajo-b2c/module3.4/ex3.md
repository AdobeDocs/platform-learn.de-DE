---
title: Adobe Journey Optimizer - Personalisierung in einer E-Mail-Nachricht anwenden
description: In dieser Übung wird erläutert, wie die Segmentpersonalisierung in E-Mail-Inhalten verwendet wird
kt: 5342
doc-type: tutorial
exl-id: bb5f8130-0237-4381-bc1e-f6b62950b1fc
source-git-commit: c531412a2c0a5c216f49560e01fb26b9b7e71869
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 11%

---

# 3.4.3 Personalisierung in einer E-Mail-Nachricht anwenden

Melden Sie sich bei Adobe Experience Cloud an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Adobe Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepTenantId--``.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

## 3.4.3.1 segmentbasierte Personalisierung

In dieser Übung verbessern Sie Ihre Newsletter-E-Mail-Nachricht mit einem personalisierten Text, der auf der Segmentzugehörigkeit basiert.

Wechseln Sie zu **Journey**. Suchen Sie die Newsletter-Journey, die Sie in der vorherigen Übung erstellt haben. Suchen Sie nach `--aepUserLdap-- - Newsletter`. Klicken Sie auf den Journey, um ihn zu öffnen.

![Journey Optimizer](./images/sbp1.png)

Sie werden es dann sehen. Klicken Sie auf **Duplizieren**.

![Journey Optimizer](./images/sbp2.png)

Klicken Sie auf **Duplizieren**.

![Journey Optimizer](./images/sbp3.png)

Wählen Sie Ihre Aktion **E** und klicken Sie auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/sbp3a.png)

Klicken Sie auf **E-Mail an Designer**.

![Journey Optimizer](./images/sbp4.png)

Sie werden es dann sehen.

![Journey Optimizer](./images/sbp5.png)

Öffnen Sie **Inhaltskomponenten** und ziehen Sie eine **Text**-Komponente unter den aktuellen Newsletter-Inhalt.

![Journey Optimizer](./images/sbp6.png)

Wählen Sie den gesamten Standardtext aus und löschen Sie ihn. Klicken Sie dann auf die **Personalisierung hinzufügen** in der Symbolleiste.

![Journey Optimizer](./images/sbp7.png)

Sie sehen dann Folgendes:

![Journey Optimizer](./images/seg1.png)

Klicken Sie im linken Menü auf **Segmentzugehörigkeit**.

![Journey Optimizer](./images/seg2.png)

>[!NOTE]
>
>Wenn Sie Ihr Segment nicht in dieser Liste finden können, scrollen Sie ein wenig nach unten, um Anweisungen zum manuellen Abrufen der Segment-ID zu finden.

Wählen Sie die `Luma - Women's Category Interest` aus und klicken Sie auf das Symbol **+** , das wie folgt aussehen sollte:

![Journey Optimizer](./images/seg3.png)

Sie sollten dann die erste Zeile so lassen, wie sie ist, und Zeile 2 und 3 durch diesen Code ersetzen:

``
    Psssst... a private sale in the women category will launch soon, we will keep you posted
{%else%}
    Thanks for taking the time to read our newsletter. Here is a 10% promo code to use on the website: READER10
{%/if%}
``

Sie erhalten dann Folgendes:

![Journey Optimizer](./images/seg4.png)

Klicken Sie auf **Validieren**, um sicherzustellen, dass der Code korrekt ist. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/sbp8.png)

Sie können diese Nachricht jetzt speichern, indem Sie auf die **Speichern**-Schaltfläche oben rechts klicken. Klicken Sie dann auf **Inhalt simulieren**.

![Journey Optimizer](./images/sbp9.png)

Wählen Sie eines der Profile aus, die Sie im Rahmen dieses Tutorials erstellt haben, und klicken Sie auf **Vorschau**. Anschließend werden die Ergebnisse Ihrer Konfiguration angezeigt.

![Journey Optimizer](./images/sbp10.png)

Sie werden es dann sehen. Klicken Sie dann auf **Schließen**.

![Journey Optimizer](./images/sbp10fff.png)

Kehren Sie zum Nachrichten-Dashboard zurück, indem Sie auf den **Pfeil** neben dem Betreffzeilentext in der oberen linken Ecke klicken.

![Journey Optimizer](./images/sbp11.png)

Klicken Sie auf den Pfeil oben links, um zu Ihrem Journey zurückzukehren.

![Journey Optimizer](./images/oc79afff.png)

Klicken Sie auf **OK**, um die E-Mail-Aktion zu schließen.

![Journey Optimizer](./images/oc79bfff.png)

Ändern Sie **Zeitplan** in **Einmal** und definieren Sie ein **Datum/Uhrzeit**. Klicken Sie auf **OK**.

>[!NOTE]
>
>Datum und Uhrzeit des Nachrichtenversands müssen innerhalb von mehr als einer Stunde liegen.

![Journey Optimizer](./images/sbp18.png)

Klicken Sie auf die Schaltfläche **Publish** auf der Journey.

![Journey Optimizer](./images/sbp19.png)

Klicken Sie im Popup-Fenster erneut auf **Publish**.

![Journey Optimizer](./images/sbp20.png)

Ihre Standard-Newsletter-Journey ist jetzt veröffentlicht. Ihre Newsletter-E-Mail-Nachricht wird auf der Grundlage Ihres Zeitplans gesendet und Ihr Journey wird gestoppt, sobald die letzte E-Mail gesendet wurde.

![Journey Optimizer](./images/sbp20fff.png)

Du hast diese Übung beendet.

Nächster Schritt: [3.4.4 Einrichten und Verwenden von Push-Benachrichtigungen für iOS](./ex4.md)

[Zurück zum Modul 3.4](./journeyoptimizer.md)

[Zurück zu „Alle Module“](../../../overview.md)
