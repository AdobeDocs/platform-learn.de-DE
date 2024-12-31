---
title: Offer decisioning - Entscheidung in einer E-Mail verwenden
description: Entscheidung in einer E-Mail verwenden
kt: 5342
doc-type: tutorial
exl-id: 7eddb239-2666-485a-b81a-1f7e6f3aeed2
source-git-commit: 348554b5a2d43d7a882e8259b39a57af13d41ff4
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 11%

---

# 3.3.5 Entscheidung in einer E-Mail verwenden

In dieser Übung verwenden Sie Ihre Entscheidung, um den Versand einer E-Mail und einer SMS zu personalisieren.

Wechseln Sie zu **Journey**. Suchen Sie die Journey, die Sie in Übung 7.2 erstellt haben, die `--aepUserLdap-- - Account Creation Journey` heißt. Klicken Sie auf den Journey, um ihn zu öffnen.

![Journey Optimizer](./images/emailoffer1.png)

Sie werden es dann sehen. Klicken Sie **Neue Version erstellen**.

![Journey Optimizer](./images/journey1.png)

Klicken Sie **Neue Version erstellen**.

![Journey Optimizer](./images/journey2.png)

Klicken Sie auf die **E-Mail**-Aktion und dann auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/journey3.png)

Anschließend wird das Nachrichten-Dashboard angezeigt. Klicken Sie auf **E-Mail an Designer**.

![Journey Optimizer](./images/emailoffer2.png)

Sie werden es dann sehen.

![Journey Optimizer](./images/emailoffer5.png)

Sie werden es dann sehen. Ziehen Sie eine neue **1:1** Spalten-Strukturkomponente auf die Arbeitsfläche.

![Journey Optimizer](./images/emailoffer6.png)

Navigieren Sie im Menü zu **Inhaltskomponenten**. Wählen Sie die Komponente **Angebotsentscheidung** aus und ziehen Sie diese Komponente wie angegeben per Drag-and-Drop in den Platzhalter für Inhaltsangebote der E-Mail. Klicken Sie dann auf **Hinzufügen**.

![Journey Optimizer](./images/emailoffer7.png)

Wählen Sie den Platzierungstyp aus, den Sie in die E-Mail aufnehmen möchten. Wählen Sie **Dropdown** Menü „Platzierungen“ die Option **E-Mail - Bild** und wählen Sie dann Ihre `--aepUserLdap-- - Luma Decision` aus. Klicken Sie auf **Hinzufügen**.

![Journey Optimizer](./images/emailoffer8.png)

Jetzt sehen Sie, wie alle personalisierten Angebote und das Fallback-Angebot im E-Mail-Designer visualisiert werden. Klicken Sie auf **Inhalt simulieren**, um eine Vorschau der E-Mail-Nachricht mit einem echten Kundenprofil anzuzeigen.

![Journey Optimizer](./images/emailoffer9.png)

Ermitteln Sie zunächst, welches Profil Sie für die Vorschau verwenden möchten. Wählen Sie den **E-**-Namespace aus und geben Sie die E-Mail-Adresse eines Kundenprofils ein, das Sie auf der Demo-Website erstellt haben. Klicken Sie anschließend auf **Vorschau**.

![Journey Optimizer](./images/emailoffer10.png)

Sobald die E-Mail angezeigt wurde und das Angebot korrekt angezeigt wird, klicken Sie auf die Schaltfläche **Schließen**.

![Journey Optimizer](./images/emailoffer11.png)

Klicken Sie abschließend auf **Speichern**.

![Journey Optimizer](./images/emailoffer12.png)

Klicken Sie nun auf den Pfeil, um zum vorherigen Bildschirm zurückzukehren.

![Journey Optimizer](./images/emailoffer13.png)

Sie werden es dann sehen. Klicken Sie auf den Pfeil oben links, um zu Ihrem Journey zurückzukehren.

![Journey Optimizer](./images/emailoffer14.png)

Klicken Sie auf **OK**, um die Aktion **E-Mail** zu schließen.

![Journey Optimizer](./images/emailoffer14a.png)

Klicken Sie auf **Publish**, um Ihre aktualisierte Journey zu veröffentlichen.

![Journey Optimizer](./images/emailoffer14b.png)

Bestätigen Sie durch erneutes Klicken auf **Publish**.

![Journey Optimizer](./images/emailoffer15.png)

Ihre Nachricht ist jetzt veröffentlicht.

![Journey Optimizer](./images/emailoffer16.png)

Wenn Sie auf der Demo-Website ein neues Konto erstellen, erhalten Sie jetzt diese E-Mail:

![Journey Optimizer](./images/emailoffer17.png)

Du hast diese Übung beendet.

Nächster Schritt: [3.3.6 Testen Sie Ihre Entscheidung mithilfe der API](./ex6.md)

[Zurück zum Modul 3.3](./offer-decisioning.md)

[Zurück zu „Alle Module“](./../../../overview.md)
