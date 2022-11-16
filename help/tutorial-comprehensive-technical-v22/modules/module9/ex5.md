---
title: offer decisioning - Verwenden Sie Ihre Entscheidung in einer E-Mail.
description: Verwenden Sie Ihre Entscheidung in einer E-Mail
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 0fb8c244-1025-479f-b82e-374d1aa5e4dc
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 11%

---

# 9.5 Ihre Entscheidung in einer E-Mail verwenden

In dieser Übung verwenden Sie Ihre Entscheidung, um den Versand einer E-Mail und einer SMS zu personalisieren.

Navigieren Sie zu **Journey**. Suchen Sie die Journey, die Sie in Übung 7.2 erstellt haben, die den Namen `--demoProfileLdap-- - Account Creation Journey`. Klicken Sie auf Ihre Journey, um sie zu öffnen.

![Journey Optimizer](./images/emailoffer1.png)

Dann wirst du das sehen. Klicken **Neue Version erstellen**.

![Journey Optimizer](./images/journey1.png)

Klicken **Neue Version erstellen**.

![Journey Optimizer](./images/journey2.png)

Klicken Sie auf **Email** und klicken Sie dann auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/journey3.png)

Daraufhin wird das Nachrichten-Dashboard angezeigt. Klicken **Email Designer**.

![Journey Optimizer](./images/emailoffer2.png)

Dann wirst du das sehen.

![Journey Optimizer](./images/emailoffer5.png)

Dann wirst du das sehen. Ziehen Sie eine neue **1:1-Spalte** Strukturkomponente auf der Arbeitsfläche.

![Journey Optimizer](./images/emailoffer6.png)

Gehen Sie im Menü zu **Inhaltskomponenten**. Wählen Sie die **Angebotsentscheidung** und ziehen Sie diese Komponente per Drag-and-Drop in den Platzhalter für das Inhaltsangebot der E-Mail. Klicken Sie anschließend auf **Hinzufügen**.

![Journey Optimizer](./images/emailoffer7.png)

Wählen Sie den Platzierungstyp aus, den Sie in die E-Mail aufnehmen möchten. Im **Praktika** Dropdown-Menüauswahl **E-Mail - Bild** und wählen Sie dann Ihre Entscheidung aus `--demoProfileLdap-- - Luma Decision`. Klicken Sie auf **Hinzufügen**.

![Journey Optimizer](./images/emailoffer8.png)

Jetzt werden alle personalisierten Angebote und das Fallback-Angebot im E-Mail-Designer visualisiert. Klicken  **Inhalt simulieren** um die E-Mail-Nachricht mit einem echten Kundenprofil in der Vorschau anzuzeigen.

![Journey Optimizer](./images/emailoffer9.png)

Bestimmen Sie zunächst, welches Profil Sie für die Vorschau verwenden möchten. Wählen Sie die **email** und geben Sie die E-Mail-Adresse eines Kundenprofils ein, das Sie auf der Demowebsite erstellt haben. Klicken Sie anschließend auf **Vorschau**.

![Journey Optimizer](./images/emailoffer10.png)

Nachdem die E-Mail angezeigt und das Angebot korrekt angezeigt wurde, klicken Sie auf die **Schließen** Schaltfläche.

![Journey Optimizer](./images/emailoffer11.png)

Klicken Sie abschließend auf **Speichern**.

![Journey Optimizer](./images/emailoffer12.png)

Klicken Sie nun auf den Pfeil, um zum vorherigen Bildschirm zurückzukehren.

![Journey Optimizer](./images/emailoffer13.png)

Dann wirst du das sehen. Klicken Sie auf den Pfeil in der oberen linken Ecke, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/emailoffer14.png)

Klicken **Ok** zum Schließen **Email** Aktion.

![Journey Optimizer](./images/emailoffer14a.png)

Klicken **Veröffentlichen** um Ihre aktualisierte Journey zu veröffentlichen.

![Journey Optimizer](./images/emailoffer14b.png)

Bestätigen durch Klicken auf **Veröffentlichen** erneut.

![Journey Optimizer](./images/emailoffer15.png)

Ihre Nachricht ist jetzt veröffentlicht.

![Journey Optimizer](./images/emailoffer16.png)

Wenn Sie ein neues Konto auf der Demo-Website erstellen, erhalten Sie jetzt diese E-Mail:

![Journey Optimizer](./images/emailoffer17.png)

Du hast diese Übung beendet.

Nächster Schritt: [9.6 Testen Ihrer Entscheidung mit der API](./ex6.md)

[Zurück zu Modul 9](./offer-decisioning.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
