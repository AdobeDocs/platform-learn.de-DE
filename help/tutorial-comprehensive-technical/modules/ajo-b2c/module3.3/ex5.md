---
title: Offer decisioning - Verwenden Sie Ihre Entscheidung in einer E-Mail
description: Verwenden Sie Ihre Entscheidung in einer E-Mail
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 11%

---

# 3.3.5 Ihre Entscheidung in einer E-Mail verwenden

In dieser Übung verwenden Sie Ihre Entscheidung, um den Versand einer E-Mail und einer SMS zu personalisieren.

Wechseln Sie zu **Journey**. Suchen Sie die Journey, die Sie in Übung 7.2 erstellt haben und die den Namen `--aepUserLdap-- - Account Creation Journey` trägt. Klicken Sie auf Ihre Journey, um sie zu öffnen.

![Journey Optimizer](./images/emailoffer1.png)

Dann wirst du das sehen. Klicken Sie auf **Neue Version erstellen**.

![Journey Optimizer](./images/journey1.png)

Klicken Sie auf **Neue Version erstellen**.

![Journey Optimizer](./images/journey2.png)

Klicken Sie auf die Aktion **E-Mail** und dann auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/journey3.png)

Daraufhin wird das Nachrichten-Dashboard angezeigt. Klicken Sie auf **E-Mail an Designer senden**.

![Journey Optimizer](./images/emailoffer2.png)

Dann wirst du das sehen.

![Journey Optimizer](./images/emailoffer5.png)

Dann wirst du das sehen. Ziehen Sie eine neue Strukturkomponente **1:1 column** auf die Arbeitsfläche.

![Journey Optimizer](./images/emailoffer6.png)

Wechseln Sie im Menü zu **Inhaltskomponenten**. Wählen Sie die Komponente **Angebotsentscheidung** aus und ziehen Sie diese Komponente wie angegeben in den Platzhalter für das Inhaltsangebot der E-Mail. Klicken Sie dann auf **Hinzufügen**.

![Journey Optimizer](./images/emailoffer7.png)

Wählen Sie den Platzierungstyp aus, den Sie in die E-Mail aufnehmen möchten. Wählen Sie im Dropdown-Menü **Platzierungen** die Option **E-Mail - Bild** aus und wählen Sie dann Ihre Entscheidung `--aepUserLdap-- - Luma Decision` aus. Klicken Sie auf **Hinzufügen**.

![Journey Optimizer](./images/emailoffer8.png)

Jetzt werden alle personalisierten Angebote und das Fallback-Angebot im E-Mail-Designer visualisiert. Klicken Sie auf **Inhalt simulieren** , um eine Vorschau der E-Mail-Nachricht mit einem echten Kundenprofil anzuzeigen.

![Journey Optimizer](./images/emailoffer9.png)

Bestimmen Sie zunächst, welches Profil Sie für die Vorschau verwenden möchten. Wählen Sie den Namespace **email** aus und geben Sie die E-Mail-Adresse eines Kundenprofils ein, das Sie auf der Demowebsite erstellt haben. Klicken Sie anschließend auf **Vorschau**.

![Journey Optimizer](./images/emailoffer10.png)

Nachdem die E-Mail angezeigt und das Angebot korrekt angezeigt wurde, klicken Sie auf die Schaltfläche **Schließen** .

![Journey Optimizer](./images/emailoffer11.png)

Klicken Sie abschließend auf **Speichern**.

![Journey Optimizer](./images/emailoffer12.png)

Klicken Sie nun auf den Pfeil, um zum vorherigen Bildschirm zurückzukehren.

![Journey Optimizer](./images/emailoffer13.png)

Dann wirst du das sehen. Klicken Sie auf den Pfeil oben links, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/emailoffer14.png)

Klicken Sie auf **OK** , um die Aktion **E-Mail** zu schließen.

![Journey Optimizer](./images/emailoffer14a.png)

Klicken Sie auf **Publish** , um Ihre aktualisierte Journey zu veröffentlichen.

![Journey Optimizer](./images/emailoffer14b.png)

Bestätigen Sie dies, indem Sie erneut auf **Publish** klicken.

![Journey Optimizer](./images/emailoffer15.png)

Ihre Nachricht ist jetzt veröffentlicht.

![Journey Optimizer](./images/emailoffer16.png)

Wenn Sie ein neues Konto auf der Demo-Website erstellen, erhalten Sie jetzt diese E-Mail:

![Journey Optimizer](./images/emailoffer17.png)

Du hast diese Übung beendet.

Nächster Schritt: [3.3.6 Testen Ihrer Entscheidung mithilfe der API](./ex6.md)

[Zurück zu Modul 3.3](./offer-decisioning.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
