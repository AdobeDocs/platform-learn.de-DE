---
title: Konfigurieren einer Journey mit Push-Nachrichten
description: Konfigurieren einer Journey mit Push-Nachrichten
kt: 5342
doc-type: tutorial
source-git-commit: 203590e3289d2e5342085bf8b6b4e3cd11859539
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 3%

---

# 3.3.2 Konfigurieren eines Journey mit Push-Nachrichten


## 3.4.4.6 Neues Ereignis erstellen

Zu **Journey Optimizer**. Wechseln Sie im linken Menü zu **Konfigurationen** und klicken Sie unter **Ereignisse** auf **Verwalten**.

![ACOP](./images/acopmenu.png)

Auf dem **Ereignisse** wird eine ähnliche Ansicht angezeigt. Klicken Sie **Ereignis erstellen**.

![ACOP](./images/add.png)

Anschließend wird eine leere Ereigniskonfiguration angezeigt.
Geben Sie Ihrem Ereignis zunächst einen Namen wie den folgenden: `--aepUserLdap--StoreEntryEvent` und legen Sie die Beschreibung auf `Store Entry Event` fest.
Als Nächstes sehen Sie **Auswahl** Ereignistyp). Wählen Sie **Unitär** aus.
Als Nächstes sehen Sie die Auswahl **Ereignis-ID-**). Wählen Sie **Systemgeneriert** aus.

![ACOP](./images/eventname.png)

Als Nächstes sehen Sie die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Verwenden Sie das Schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

Nach Auswahl des Schemas werden Sie eine Reihe von Feldern sehen, die im Abschnitt **Payload** ausgewählt sind. Ihr Ereignis ist jetzt vollständig konfiguriert.

Klicken Sie auf **Speichern**.

![ACOP](./images/eventschema.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert. Klicken Sie erneut auf Ihr Ereignis, um den Bildschirm **Ereignis bearbeiten** erneut zu öffnen.

![ACOP](./images/eventdone.png)

Bewegen Sie den Mauszeiger über **Feld** Payload“ und klicken Sie auf das Symbol **Payload anzeigen**.

![ACOP](./images/hover.png)

Im Folgenden sehen Sie ein Beispiel für die erwartete Payload.

Ihr Ereignis verfügt über eine eindeutige Orchestrierungs-eventID, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID` sehen.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, um die Journey, die Sie im nächsten Schritt erstellen, zum Trigger zu bringen. Notieren Sie sich diese eventID, da Sie sie im nächsten Schritt benötigen werden.
`"eventID": "89acd341ec2b7d1130c9a73535029debf2ac35f486bc99236b1a5091d6f4bc68"`

Klicken Sie **OK** gefolgt von **Abbrechen**.

## 3.4.4.7 Erstellen einer Journey

Wechseln Sie im Menü zu **Journey** und klicken Sie auf **Journey erstellen**.

![DSN](./images/sjourney1.png)

Sie werden es dann sehen. Geben Sie Ihrem Journey einen Namen. Verwenden Sie `--aepUserLdap-- - Store Entry journey`. Klicken Sie auf **Speichern**.

![DSN](./images/sjourney3.png)

Zunächst müssen Sie Ihr Ereignis als Ausgangspunkt Ihres Journey hinzufügen. Suchen Sie nach Ihrer `--aepUserLdap--StoreEntryEvent` und ziehen Sie sie per Drag-and-Drop auf die Arbeitsfläche. Klicken Sie auf **Speichern**.

![DSN](./images/sjourney4.png)

Suchen Sie als Nächstes unter **Aktionen** nach der **Push**-Aktion. Ziehen Sie die Aktion **Push** per Drag-and-Drop auf die Arbeitsfläche.

Legen Sie die **Kategorie** auf **Marketing** fest und wählen Sie eine Push-Oberfläche aus, mit der Sie Push-Benachrichtigungen senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **Push-iOS-Android**.

>[!NOTE]
>
>Es muss ein Kanal in Journey Optimizer vorhanden sein, der die **App-Oberfläche** wie zuvor beschrieben verwendet.

![ACOP](./images/journeyactions1push.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2push.png)

Sie werden es dann sehen. Klicken Sie auf **Personalisierung** für das Feld **Titel**.

![Push-Benachrichtigung](./images/bp5.png)

Sie werden es dann sehen. Sie können jetzt jedes Profilattribut direkt aus dem Echtzeit-Kundenprofil auswählen.

Suchen Sie nach dem Feld **Vorname** und klicken Sie dann auf das Symbol **+** neben dem Feld **Vorname**. Anschließend wird das Personalisierungs-Token für Vorname hinzugefügt: **{{profile.person.name.firstName}}**.

![Push-Benachrichtigung](./images/bp9.png)

Als Nächstes fügen Sie den Text **hinzu, willkommen in unserem Shop!** hinter **{{profile.person.name.firstName}}**.

Klicken Sie auf **Speichern**.

![Push-Benachrichtigung](./images/bp10.png)

Jetzt hast du das. Klicken Sie auf **Personalisierung** für das Feld **Hauptteil**.

![Push-Benachrichtigung](./images/bp11.png)

Geben Sie diesen Text ein **Klicken Sie hier, um einen Rabatt von 10 % zu erhalten, wenn Sie heute kaufen!** und klicken Sie auf **Speichern**.

![Push-Benachrichtigung](./images/bp12.png)

Dann hast du das hier. Klicken Sie auf den Pfeil oben links, um zu Ihrem Journey zurückzukehren.

![Journey Optimizer](./images/bp12a.png)

Klicken Sie **Speichern**, um die Push-Aktion zu schließen.

![DSN](./images/sjourney8.png)

Klicken Sie auf **Veröffentlichen**.

![DSN](./images/sjourney10.png)

Klicken **erneut auf** Veröffentlichen“.

![DSN](./images/sjourney10a.png)

Ihr Journey ist jetzt veröffentlicht.

![DSN](./images/sjourney11.png)

## 3.4.4.8 Testen von Journey- und Push-Nachrichten

Rufen Sie in Ihrer DX Demo 2.0-Mobile-App den Bildschirm &quot;**&quot;**. Klicken Sie auf **Schaltfläche** Store-Eintrag“.

>[!NOTE]
>
>Die **Store Entry**-Schaltfläche wird derzeit implementiert. Sie werden sie noch nicht in der App finden.

![DSN](./images/demo1b.png)

Stellen Sie sicher, dass Sie die App sofort schließen, nachdem Sie auf **Store-Eintrag**-Symbol geklickt haben, da sonst die Push-Nachricht nicht angezeigt wird.

Nach einigen Sekunden wird die Meldung angezeigt.

![DSN](./images/demo2.png)

Du hast diese Übung beendet.

## Nächste Schritte

Navigieren Sie zu [3.3.3 Konfigurieren einer Kampagne mit In-App-Nachrichten](./ex3.md){target="_blank"}

Zurück zu [Adobe Journey Optimizer: Push- und In-App-Nachrichten](ajopushinapp.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
