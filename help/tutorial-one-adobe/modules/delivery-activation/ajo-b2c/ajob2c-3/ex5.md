---
title: Offer Decisioning - Entscheidung in einer E-Mail verwenden
description: Entscheidung in einer E-Mail verwenden
kt: 5342
doc-type: tutorial
exl-id: c94b4ed4-0122-4cfd-a69f-40ae2063d449
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 12%

---

# 3.3.5 Entscheidung in einer E-Mail verwenden

In dieser Übung verwenden Sie Ihre Entscheidung, um den Versand einer E-Mail und einer SMS zu personalisieren.

Wechseln Sie zu **Journey**. Suchen Sie die Journey, die Sie in Übung 3.1.3 erstellt haben, die `--aepUserLdap-- - Registration Journey` heißt. Klicken Sie auf den Journey, um ihn zu öffnen.

![Journey Optimizer](./images/emailoffer1.png)

Sie werden es dann sehen. Klicken Sie auf **… Weitere** und klicken Sie dann auf **Neue Version erstellen**.

![Journey Optimizer](./images/journey1.png)

Klicken Sie **Neue Version erstellen**.

![Journey Optimizer](./images/journey2.png)

Klicken Sie auf die **E-Mail**-Aktion und dann auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/journey3.png)

Anschließend wird das Nachrichten-Dashboard angezeigt. Klicken Sie **E-Mail-Textkörper bearbeiten**.

![Journey Optimizer](./images/emailoffer2.png)

Sie werden es dann sehen. Ziehen Sie eine neue **1:1** Spalten-Strukturkomponente auf die Arbeitsfläche.

![Journey Optimizer](./images/emailoffer6.png)

Gehen Sie im Menü zu **Inhalt**. Wählen Sie die Komponente **Angebotsentscheidung** aus und ziehen Sie diese Komponente wie angegeben per Drag-and-Drop in den Platzhalter für Inhaltsangebote der E-Mail. Klicken Sie dann auf **Hinzufügen**.

![Journey Optimizer](./images/emailoffer7.png)

Wählen Sie den Platzierungstyp aus, den Sie in die E-Mail aufnehmen möchten. Wählen Sie **Dropdown** Menü „Platzierungen“ die Option **E-Mail - Bild** und wählen Sie dann Ihre `--aepUserLdap-- - CitiSignal Decision` aus. Klicken Sie auf **Hinzufügen**.

![Journey Optimizer](./images/emailoffer8.png)

Sie können jetzt alle personalisierten Angebote und das Fallback-Angebot durchlaufen, wobei alle im E-Mail-Designer visualisiert werden. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/emailoffer9.png)

Klicken Sie nun auf den Pfeil, um zum vorherigen Bildschirm zurückzukehren.

![Journey Optimizer](./images/emailoffer13.png)

Klicken Sie auf den Pfeil oben links, um zu Ihrem Journey zurückzukehren.

![Journey Optimizer](./images/emailoffer14.png)

Klicken Sie auf **Speichern**, um die Aktion **E-Mail** zu schließen.

![Journey Optimizer](./images/emailoffer14a.png)

Klicken Sie **Veröffentlichen**, um Ihre aktualisierte Journey zu veröffentlichen.

![Journey Optimizer](./images/emailoffer14b.png)

Bestätigen Sie durch erneutes Klicken **Veröffentlichen**.

![Journey Optimizer](./images/emailoffer15.png)

Ihre Nachricht ist jetzt veröffentlicht.

![Journey Optimizer](./images/emailoffer16.png)

Wenn Sie auf der Demo-Website ein neues Konto erstellen, erhalten Sie jetzt diese E-Mail:

![Journey Optimizer](./images/emailoffer17.png)

Du hast diese Übung beendet.

## Nächste Schritte

Wechseln Sie zu [3.3.6. Testen Sie Ihre Entscheidung mithilfe der API](./ex6.md){target="_blank"}

Zurück zu [Offer Decisioning](offer-decisioning.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
