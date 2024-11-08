---
title: Journey Optimizer - Ereignis erstellen
description: Journey Optimizer - Ereignis erstellen
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 3.1.1 Ereignis erstellen

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der Ansicht **Home** Ihrer Sandbox `--aepSandboxName--`.

![ACOP](./images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend unter **Ereignisse** auf die Schaltfläche **Verwalten** .

![ACOP](./images/acopmenu.png)

Daraufhin wird eine Übersicht über alle verfügbaren Ereignisse angezeigt. Klicken Sie auf **Ereignis erstellen** , um mit der Erstellung Ihres eigenen Ereignisses zu beginnen.

![ACOP](./images/emptyevent.png)

Daraufhin wird ein neues, leeres Ereignisfenster angezeigt.

![ACOP](./images/emptyevent1.png)

Geben Sie Ihrem Ereignis zunächst einen Namen wie den folgenden: `--aepUserLdap--AccountCreationEvent`.

![ACOP](./images/eventname.png)

Fügen Sie als Nächstes eine Beschreibung wie `Account Creation Event` hinzu.

![ACOP](./images/eventdescription.png)

Stellen Sie als Nächstes sicher, dass der **Typ** auf **Einzeln** eingestellt ist, und wählen Sie für die Auswahl des **Ereignis-ID-Typs** die Option **Systemgeneriert** aus.

![ACOP](./images/eventidtype.png)

Als Nächstes folgt die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Verwenden Sie das Schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nach Auswahl des Schemas werden im Abschnitt **Payload** eine Reihe von Feldern ausgewählt. Sie sollten nun den Mauszeiger über den Abschnitt **Payload** bewegen und es werden drei Symbole angezeigt. Klicken Sie auf das Symbol **Bearbeiten**.

![ACOP](./images/eventpayload.png)

Es wird ein Popup-Fenster mit den **Feldern** angezeigt, in dem Sie einige der Felder auswählen müssen, die für die Personalisierung der E-Mail erforderlich sind.  Später werden wir mithilfe der bereits in Adobe Experience Platform vorhandenen Daten andere Profilattribute auswählen.

![ACOP](./images/eventfields.png)

Wählen Sie im Objekt `--aepTenantId--.demoEnvironment` die Felder **brandLogo** und **brandName** aus.

![ACOP](./images/eventpayloadbr.png)

Wählen Sie im Objekt `--aepTenantId--.identification.core` das Feld **email** aus.

![ACOP](./images/eventpayloadbrid.png)

Klicken Sie auf **OK** , um Ihre Änderungen zu speichern.

![ACOP](./images/saveok.png)

Daraufhin sollte Folgendes angezeigt werden:

![ACOP](./images/eventsave.png)

Klicken Sie erneut auf **Speichern** , um Ihre Änderungen zu speichern.

![ACOP](./images/save1.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert.

![ACOP](./images/eventdone.png)

Klicken Sie erneut auf das Ereignis, um den Bildschirm **Ereignis bearbeiten** erneut zu öffnen. Bewegen Sie den Mauszeiger erneut über das Feld **Payload** , um die 3 Symbole erneut anzuzeigen. Klicken Sie auf das Symbol **Payload anzeigen** .

![ACOP](./images/viewevent.png)

Sie sehen nun ein Beispiel der erwarteten Payload.

![ACOP](./images/fullpayload.png)

Ihr Ereignis verfügt über eine eindeutige eventID für die Orchestrierung, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID` sehen.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, um die in Übung 7.2 erstellte Journey Trigger. Merken Sie sich diese eventID, da Sie sie in Übung 7.3 benötigen werden.
`"eventID": "227402c540eb8f8855c6b2333adf6d54d7153d9d7d56fa475a6866081c574736"`

Klicken Sie auf **OK** und anschließend auf **Abbrechen**.

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [3.1.2 Journey Optimizer: Journey und E-Mail-Nachricht erstellen](./ex2.md)

[Zurück zu Modul 3.1](./journey-orchestration-create-account.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
