---
title: Echtzeit-Kundendatenplattform - Erstellen Sie ein Segment und ergreifen Sie Maßnahmen - Konfigurieren Sie ein Werbeziel wie Google DV360
description: Echtzeit-Kundendatenplattform - Erstellen Sie ein Segment und ergreifen Sie Maßnahmen - Konfigurieren Sie ein Werbeziel wie Google DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 40441815-428a-48dc-a12e-91220d4ba307
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# 6.2 Werbeziele wie Google DV360 konfigurieren

>[!IMPORTANT]
>
>Der folgende Inhalt ist als FYI gedacht - Sie tun dies **NOT** müssen ein neues Ziel für DV360 konfigurieren. Das Ziel wurde bereits erstellt und Sie können es in der nächsten Übung verwenden.

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](../module2/images/sb1.png)

Gehen Sie im linken Menü zu **Ziele**, gehen Sie dann zu **Katalog**. Sie werden dann die **Zielkatalog**.

![RTCDP](./images/rtcdp.png)

In **Ziele** klicken Sie auf **Google Display &amp; Video 360** und klicken Sie anschließend auf **+ Einrichtung**.

![RTCDP](./images/rtcdpgoogle.png)

Dann wirst du das sehen. Klicken **Mit Ziel verbinden**.

![RTCDP](./images/rtcdpgooglecreate1.png)

Im nächsten Bildschirm können Sie Ihr Ziel auf Google DV360 konfigurieren.

![RTCDP](./images/rtcdpgooglecreatedest.png)

Geben Sie einen Wert in die Felder ein **Name** und **Beschreibung**.

Das Feld **Konto-ID** ist die **Advertiser-ID** des DV360-Kontos. Sie finden dies hier:

![RTCDP](./images/rtcdpgoogledv360advid.png)

Die **Kontotyp** auf **Advertiser einladen**.

Jetzt hast du das. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpgoogldv360new.png)

>[!NOTE]
>
>Google muss die Adobe der Zulassungsliste durchführen, damit Adobe Experience Platform Daten an Google DV360 senden kann. Wenden Sie sich an Ihren Google-Kundenbetreuer, um diesen Datenfluss zu aktivieren.

Nachdem Sie das Ziel erstellt haben, sehen Sie dies. Sie können optional eine Data Governance-Richtlinie auswählen. Klicken Sie anschließend auf **Speichern und beenden**.

![RTCDP](./images/rtcdpcreatedest1.png)

Daraufhin wird eine Liste der verfügbaren Ziele angezeigt.
In der nächsten Übung verbinden Sie das in der vorherigen Übung erstellte Segment mit dem Google DV360-Ziel.

Nächster Schritt: [6.3 Maßnahmen ergreifen: Senden Ihres Segments an DV360](./ex3.md)

[Zurück zu Modul 6](./real-time-cdp-build-a-segment-take-action.md)

[Zu allen Modulen zurückkehren](../../overview.md)
