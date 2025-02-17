---
title: Journey Optimizer - Ereignis erstellen
description: Journey Optimizer - Ereignis erstellen
kt: 5342
doc-type: tutorial
exl-id: 2c03cc8d-0106-4fa5-80c6-e25712ca2eab
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 1%

---

# 3.1.1 Ereignis erstellen

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`.

![ACOP](./images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend auf die Schaltfläche **Verwalten** unter **Ereignisse**.

![ACOP](./images/acopmenu.png)

Anschließend sehen Sie eine Übersicht über alle verfügbaren Ereignisse. Klicken Sie auf **Ereignis erstellen**, um mit der Erstellung Ihres eigenen Ereignisses zu beginnen.

![ACOP](./images/emptyevent.png)

Daraufhin wird ein neues, leeres Ereignisfenster angezeigt.

![ACOP](./images/emptyevent1.png)

Zunächst geben Sie Ihrem Ereignis einen Namen wie den folgenden: `--aepUserLdap--AccountCreationEvent`.
Legen Sie die Beschreibung auf `Account Creation Event` fest, stellen Sie sicher, **der** auf **Unitär** und wählen Sie für die Auswahl **Ereignis-ID-Typ** die Option **Systemgeneriert**.

![ACOP](./images/eventdescription.png)

Als Nächstes sehen Sie die Schemaauswahl. Verwenden Sie das Schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nach Auswahl des Schemas werden Sie eine Reihe von Feldern sehen, die im Abschnitt **Payload** ausgewählt sind. Bewegen Sie nun den Mauszeiger über den **Payload**-Abschnitt und es werden drei Symbole angezeigt. Klicken Sie auf das **Bearbeiten**-Symbol.

![ACOP](./images/eventpayload.png)

Es wird ein Popup-Fenster **Felder** angezeigt, in dem Sie einige der Felder auswählen können, die wir zur Personalisierung der E-Mail benötigen.  Wir wählen später unter Verwendung der bereits in Adobe Experience Platform vorhandenen Daten andere Profilattribute aus.

![ACOP](./images/eventfields.png)

Wählen Sie in der `--aepTenantId--.demoEnvironment` die Felder **brandLogo** und **brandName** aus.

![ACOP](./images/eventpayloadbr.png)

Wählen Sie im `--aepTenantId--.identification.core` das Feld **E-Mail** aus. Klicken Sie auf **OK**, um Ihre Änderungen zu speichern.

![ACOP](./images/eventpayloadbrid.png)

Sie sollten das dann sehen. Legen Sie den **Namespace** auf **ECID (ECID)** fest. Klicken Sie auf **Speichern**.

![ACOP](./images/eventsave.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert.

![ACOP](./images/eventdone.png)

Klicken Sie erneut auf das Ereignis, um den Bildschirm **Ereignis bearbeiten** erneut zu öffnen. Bewegen Sie den Mauszeiger erneut über **Feld** Payload“, um die drei Symbole erneut anzuzeigen. Klicken Sie auf das Symbol **Payload anzeigen**.

![ACOP](./images/viewevent.png)

Im Folgenden sehen Sie ein Beispiel für die erwartete Payload.

![ACOP](./images/fullpayload.png)

Ihr Ereignis verfügt über eine eindeutige Orchestrierungs-eventID, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID` sehen.

Die Ereignis-ID ist die, die an Adobe Experience Platform gesendet werden muss, um die Journey, die Sie als Nächstes erstellen, in einen Trigger zu bringen. Merken Sie sich diese eventID, da Sie sie in einer der nächsten Übungen benötigen werden.
`"eventID": "5ae9b8d3f68eb555502b0c07d03ef71780600c4bd0373a4065c692ae0bfbd34d"`

Klicken Sie auf **OK**.

![ACOP](./images/payloadeventID.png)

Klicken Sie **Abbrechen**.

![ACOP](./images/payloadeventID1.png)

Sie haben jetzt diese Übung beendet.

## Nächste Schritte

Navigieren Sie zu [3.1.2 Erstellen Sie Fragmente zur Verwendung in Ihrer Nachricht](./ex2.md){target="_blank"}

Zurück zu [Adobe Journey Optimizer: Orchestrierung](./journey-orchestration-create-account.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
