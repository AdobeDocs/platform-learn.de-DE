---
title: Bootcamp - Mischung aus physischem und digitalem - Journey Optimizer Event erstellen
description: Bootcamp - Mischung aus physischem und digitalem - Journey Optimizer Event erstellen
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: 3d47c686-c2d8-4961-a05b-0990025392fa
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 3.2 Ereignis erstellen

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `Bootcamp`. Um von einer Sandbox in eine andere zu wechseln, klicken Sie auf **Prod** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel trägt die Sandbox den Namen **Bootcamp2**. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`Bootcamp`.

![ACOP](./images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend auf die Schaltfläche **Verwalten** unter **Ereignisse**.

![ACOP](./images/acopmenu.png)

Anschließend sehen Sie eine Übersicht über alle verfügbaren Ereignisse. Klicken Sie auf **Ereignis erstellen**, um mit der Erstellung Ihres eigenen Ereignisses zu beginnen.

![ACOP](./images/emptyevent.png)

Daraufhin wird ein neues, leeres Ereignisfenster angezeigt.

Zunächst geben Sie Ihrem Ereignis einen Namen wie den folgenden: `yourLastNameBeaconEntryEvent` und fügen Sie eine Beschreibung wie diesen `Beacon Entry Event` hinzu.

![ACOP](./images/eventdescription.png)

Stellen Sie als Nächstes sicher **dass &quot;**&quot; auf **Unitär** eingestellt ist, und wählen Sie für die Auswahl **Ereignis-ID-Typ** die Option **Systemgeneriert**.

![ACOP](./images/eventidtype.png)

Als Nächstes sehen Sie die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Verwenden Sie das Schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nach Auswahl des Schemas werden Sie eine Reihe von Feldern sehen, die im Abschnitt **Felder** ausgewählt werden. Bewegen Sie nun den Mauszeiger über den **Felder** Abschnitt, und es werden drei Symbole angezeigt. Klicken Sie auf das **Bearbeiten**-Symbol.

![ACOP](./images/eventpayload.png)

Es wird ein Popup-Fenster **Felder** angezeigt, in dem Sie einige der Felder auswählen müssen, die wir für die Personalisierung des Journey benötigen.  Wir wählen später unter Verwendung der bereits in Adobe Experience Platform vorhandenen Daten andere Profilattribute aus.

![ACOP](./images/eventfields.png)

Scrollen Sie nach unten, bis Sie das Objekt `Place context` sehen, und aktivieren Sie das Kontrollkästchen. Damit wird der gesamte Kontext des Kundenstandorts der Journey zur Verfügung gestellt. Klicken Sie auf **OK**, um Ihre Änderungen zu speichern.

![ACOP](./images/eventpayloadbr.png)

Sie sollten das dann sehen. Klicken Sie **erneut auf** Speichern“, um Ihre Änderungen zu speichern.

![ACOP](./images/eventsave.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert.

![ACOP](./images/eventdone.png)

Klicken Sie erneut auf das Ereignis, um den Bildschirm **Ereignis bearbeiten** erneut zu öffnen. Bewegen Sie den Mauszeiger **Felder** erneut, um die drei Symbole anzuzeigen. Klicken Sie auf das **Ansicht**-Symbol.

![ACOP](./images/viewevent.png)

Im Folgenden sehen Sie ein Beispiel für die erwartete Payload.
Ihr Ereignis verfügt über eine eindeutige Orchestrierungs-eventID, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID` sehen.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, damit Sie die Journey, die Sie in einer der nächsten Übungen erstellen, in Trigger bringen können. Merken Sie sich diese eventID, da Sie sie später möglicherweise benötigen.
`"eventID": "e76c0bf0c77c3517e5b6f4c457a0754ebaf5f1f6b9357d74e0d8e13ae517c3d5"`

Klicken Sie **OK** gefolgt von einem Klick auf **Abbrechen**.

Sie haben jetzt diese Übung beendet.

Nächster Schritt: [3.3 Erstellen Sie Ihre Journey- und Push-Benachrichtigung](./ex3.md)

[Zurück zu Benutzerfluss 3](./uc3.md)

[Zurück zu „Alle Module“](../../overview.md)
