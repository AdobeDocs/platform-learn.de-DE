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

## Kunden-Journey-Fluss

Öffnen Sie ein neues, sauberes Inkognito-Browser-Fenster und navigieren Sie zu [https://bootcamp.aepdemo.net](https://bootcamp.aepdemo.net). Klicken Sie **Alle zulassen**. Basierend auf Ihrem Browser-Verhalten im vorherigen Benutzerfluss sehen Sie, wie die Personalisierung auf der Homepage der Website erfolgt.

![DSN](./images/web8a.png)

Klicken Sie auf **Profil** in der oberen rechten Ecke des Bildschirms.

![Demo](./images/web8b.png)

Klicken Sie **Konto erstellen**.

![Demo](./images/pv5.png)

Füllen Sie alle Formularfelder aus. Verwenden Sie einen echten Wert für E-Mail-Adresse und Telefonnummer, da er in späteren Übungen für den Versand von E-Mails und SMS verwendet wird.

![Demo](./images/pv7a.png)

Scroll down. Sie müssen jetzt die eventID Ihres benutzerdefinierten Ereignisses eingeben, das Sie in Übung 2.2 erstellt haben. Sie finden sie hier:

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID ist das, was an Adobe Experience Platform gesendet werden muss, um die von Ihnen erstellte Journey zum Trigger zu bringen. Dies ist die eventID in diesem Beispiel: `19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f`

Füllen Sie das Feld eventID (Ihre Ereignis **ID für die Kontoerstellung) aus** klicken Sie auf **Registrieren**.

![Demo](./images/pv8a.png)

Sie werden es dann sehen.

![Demo](./images/pv9.png)

Sie erhalten auch diese E-Mail, also die E-Mail, die Sie im Rahmen dieser Übung selbst erstellt haben.

![Demo](./images/pv10a.png)

Sie haben jetzt diese Übung beendet.

Nächster Schritt: [2.5 Installieren und verwenden Sie die Mobile App](./ex5.md)

[Zurück zu Benutzerfluss 2](./uc2.md)

[Zurück zu „Alle Module“](../../overview.md)
