---
title: Journey Optimizer - Ereignis erstellen
description: Journey Optimizer - Ereignis erstellen
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: e35d2357-21f9-4566-b2a1-cc0cf0c64956
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 7.1 Ereignis erstellen

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxId--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `--aepSandboxId--`.

![ACOP](./images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend auf das **Verwalten** Schaltfläche unter **Veranstaltungen**.

![ACOP](./images/acopmenu.png)

Daraufhin wird eine Übersicht über alle verfügbaren Ereignisse angezeigt. Klicken **Ereignis erstellen** , um mit der Erstellung Ihres eigenen Ereignisses zu beginnen.

![ACOP](./images/emptyevent.png)

Daraufhin wird ein neues, leeres Ereignisfenster angezeigt.

![ACOP](./images/emptyevent1.png)

Geben Sie Ihrem Ereignis zunächst einen Namen wie den folgenden: `--demoProfileLdap--AccountCreationEvent`.

![ACOP](./images/eventname.png)

Fügen Sie als Nächstes eine Beschreibung wie die folgende hinzu `Account Creation Event`.

![ACOP](./images/eventdescription.png)

Stellen Sie als Nächstes sicher, dass die **Typ** auf **Einzelfall** und für die **Ereignis-ID-Typ** Auswahl, wählen Sie **Systemgeneriert**.

![ACOP](./images/eventidtype.png)

Als Nächstes folgt die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Bitte verwenden Sie das Schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nach Auswahl des Schemas werden im **Nutzlast** Abschnitt. Sie sollten jetzt den Mauszeiger über die **Nutzlast** und Sie sehen 3 Symbole. Klicken Sie auf **Bearbeiten** Symbol.

![ACOP](./images/eventpayload.png)

Sie werden eine **Felder** -Fenster, in dem Sie einige der Felder auswählen müssen, die zur Personalisierung der E-Mail erforderlich sind.  Später werden wir mithilfe der bereits in Adobe Experience Platform vorhandenen Daten andere Profilattribute auswählen.

![ACOP](./images/eventfields.png)

Im -Objekt `--aepTenantId--.demoEnvironment`, wählen Sie bitte die Felder aus. **brandLogo** und **brandName**.

![ACOP](./images/eventpayloadbr.png)

Im -Objekt `--aepTenantId--.identification.core`, wählen Sie das Feld aus. **email**.

![ACOP](./images/eventpayloadbrid.png)

Klicken **Ok** , um Ihre Änderungen zu speichern.

![ACOP](./images/saveok.png)

Daraufhin sollte Folgendes angezeigt werden:

![ACOP](./images/eventsave.png)

Klicken **Speichern** erneut, um Ihre Änderungen zu speichern.

![ACOP](./images/save1.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert.

![ACOP](./images/eventdone.png)

Klicken Sie erneut auf das Ereignis, um die **Ereignis bearbeiten** erneut angezeigt. Bewegen Sie den Mauszeiger über die **Nutzlast** erneut ein, um die 3 Symbole erneut anzuzeigen. Klicken Sie auf **Payload anzeigen** Symbol.

![ACOP](./images/viewevent.png)

Sie sehen nun ein Beispiel der erwarteten Payload.

![ACOP](./images/fullpayload.png)

Ihr Ereignis verfügt über eine eindeutige Orchestrierungs-eventID, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, um die Journey Trigger, die Sie in Übung 7.2 erstellen werden. Denken Sie an diese eventID, wie Sie sie in Übung 7.3 benötigen werden.
`"eventID": "227402c540eb8f8855c6b2333adf6d54d7153d9d7d56fa475a6866081c574736"`

Klicken **Ok**, gefolgt von einem Klick auf **Abbrechen**.

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [7.2 Journey Optimizer: Journey und E-Mail-Nachricht erstellen](./ex2.md)

[Zurück zu Modul 7](./journey-orchestration-create-account.md)

[Zu allen Modulen zurückkehren](../../overview.md)
