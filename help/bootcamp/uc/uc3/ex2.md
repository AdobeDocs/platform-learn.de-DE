---
title: Bootcamp - Vermischen von physisch und digital - Journey Optimizer Erstellen Sie Ihre Veranstaltung
description: Bootcamp - Vermischen von physisch und digital - Journey Optimizer Erstellen Sie Ihre Veranstaltung
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
source-wordcount: '453'
ht-degree: 0%

---

# 3.2 Ereignis erstellen

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `Bootcamp`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **Prod** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **Bootcamp2**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend auf das **Verwalten** Schaltfläche unter **Veranstaltungen**.

![ACOP](./images/acopmenu.png)

Daraufhin wird eine Übersicht über alle verfügbaren Ereignisse angezeigt. Klicken **Ereignis erstellen** , um mit der Erstellung Ihres eigenen Ereignisses zu beginnen.

![ACOP](./images/emptyevent.png)

Daraufhin wird ein neues, leeres Ereignisfenster angezeigt.

Geben Sie Ihrem Ereignis zunächst einen Namen wie den folgenden: `yourLastNameBeaconEntryEvent` und fügen Sie eine Beschreibung wie die folgende hinzu `Beacon Entry Event`.

![ACOP](./images/eventdescription.png)

Stellen Sie als Nächstes sicher, dass die **Typ** auf **Einzelfall** und für die **Ereignis-ID-Typ** Auswahl, wählen Sie **Systemgeneriert**.

![ACOP](./images/eventidtype.png)

Als Nächstes folgt die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Bitte verwenden Sie das Schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nach Auswahl des Schemas werden im **Felder** Abschnitt. Sie sollten jetzt den Mauszeiger über die **Felder** und Sie sehen 3 Symbole. Klicken Sie auf **Bearbeiten** Symbol.

![ACOP](./images/eventpayload.png)

Sie werden eine **Felder** -Fenster, in dem Sie einige der Felder auswählen müssen, die wir zum Personalisieren der Journey benötigen.  Später werden wir mithilfe der bereits in Adobe Experience Platform vorhandenen Daten andere Profilattribute auswählen.

![ACOP](./images/eventfields.png)

Scrollen Sie nach unten, bis das Objekt angezeigt wird `Place context` und aktivieren Sie das Kontrollkästchen. Dadurch wird der gesamte Kontext des Standorts des Kunden dem Journey zur Verfügung gestellt. Klicken **Ok** , um Ihre Änderungen zu speichern.

![ACOP](./images/eventpayloadbr.png)

Dann sollten Sie das sehen. Klicken **Speichern** erneut, um Ihre Änderungen zu speichern.

![ACOP](./images/eventsave.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert.

![ACOP](./images/eventdone.png)

Klicken Sie erneut auf das Ereignis, um die **Ereignis bearbeiten** erneut angezeigt. Bewegen **Felder** erneut, um die 3 Symbole anzuzeigen. Klicken Sie auf **Ansicht** Symbol.

![ACOP](./images/viewevent.png)

Sie sehen nun ein Beispiel der erwarteten Payload.
Ihr Ereignis verfügt über eine eindeutige eventID für die Orchestrierung, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, um die Journey Trigger, die Sie in einer der nächsten Übungen erstellen werden. Denken Sie an diese eventID, da Sie sie möglicherweise später benötigen.
`"eventID": "e76c0bf0c77c3517e5b6f4c457a0754ebaf5f1f6b9357d74e0d8e13ae517c3d5"`

Klicken **Ok**, gefolgt von einem Klick auf **Abbrechen**.

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [3.3 Journey- und Push-Benachrichtigung erstellen](./ex3.md)

[Zurück zum Benutzerfluss 3](./uc3.md)

[Zu allen Modulen zurückkehren](../../overview.md)
