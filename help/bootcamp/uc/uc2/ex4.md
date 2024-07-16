---
title: Bootcamp - Journey Optimizer Journey erstellen
description: Bootcamp - Journey Optimizer Journey erstellen
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Journeys
exl-id: e4464502-60c8-4fba-a429-169b7a4516c8
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 2%

---

# 2.4 Journey testen

## Journey-Fluss des Kunden

Öffnen Sie ein neues, sauberes Inkognito-Browserfenster und gehen Sie zu [https://bootcamp.aepdemo.net](https://bootcamp.aepdemo.net). Klicken Sie auf **Alle zulassen**. Basierend auf Ihrem Browsing-Verhalten im vorherigen Benutzerfluss wird auf der Startseite der Website eine Personalisierung angezeigt.

![DSN](./images/web8a.png)

Klicken Sie oben rechts auf dem Bildschirm auf das Symbol **Profil** .

![Demo](./images/web8b.png)

Klicken Sie auf **Konto erstellen**.

![Demo](./images/pv5.png)

Füllen Sie alle Formularfelder aus. Verwenden Sie einen echten Wert für E-Mail-Adresse und Telefonnummer, da dieser Wert in späteren Übungen zum Versand von E-Mails und SMS verwendet wird.

![Demo](./images/pv7a.png)

Scrollen Sie nach unten. Sie müssen jetzt die eventID Ihres benutzerspezifischen Ereignisses eingeben, das Sie in Übung 2.2 erstellt haben. Sie finden ihn hier:

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, um die von Ihnen erstellte Journey Trigger. Dies ist die eventID in diesem Beispiel: `19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f`

Füllen Sie die eventID im Feld **Ihre Ereignis-ID für die Kontoerstellung** aus und klicken Sie auf **Registrieren**.

![Demo](./images/pv8a.png)

Dann wirst du das sehen.

![Demo](./images/pv9.png)

Sie erhalten auch diese E-Mail, die die E-Mail ist, die Sie im Rahmen dieser Übung selbst erstellt haben.

![Demo](./images/pv10a.png)

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [2.5 Installieren und Verwenden der App](./ex5.md)

[Zurück zum Benutzerfluss 2](./uc2.md)

[Zu allen Modulen zurückkehren](../../overview.md)
