---
title: Audience Activation zu Microsoft Azure Event Hub - Zielgruppe aktivieren
description: Audience Activation zu Microsoft Azure Event Hub - Zielgruppe aktivieren
kt: 5342
doc-type: tutorial
exl-id: e6bac0ce-4a1e-4458-af3e-3d6ac40b9cb5
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 5%

---

# 2.4.5 Zielgruppe aktivieren

## Zielgruppe zum Azure Event Hub-Ziel hinzufügen

In dieser Übung fügen Sie Ihre `--aepUserLdap-- - Interest in Plans` zu Ihrem `--aepUserLdap---aep-enablement` Azure Event Hub -Ziel hinzu.

Melden Sie sich über die folgende URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

Gehen Sie zu **Ziele** und klicken Sie dann auf **Durchsuchen**. Anschließend werden alle verfügbaren Ziele angezeigt. Suchen Sie Ihr Ziel und klicken Sie auf die drei Punkte&#x200B;**…** wie unten angegeben und klicken Sie dann auf **Zielgruppen aktivieren**.

![5-01-select-destination.png](./images/501selectdestination.png)

Sie werden es dann sehen. Suchen Sie mithilfe Ihres LDAP nach Ihrer Audience und wählen Sie `--aepUserLdap-- - Interest in Plans` aus der Liste der Audiences aus.

Klicken Sie auf **Weiter**.

![5-04-select-segment.png](./images/504selectsegment.png)

Klicken Sie **Neues Feld hinzufügen**, klicken Sie auf Schema durchsuchen und wählen Sie die `--aepTenantId--identification.core.ecid` aus (löschen Sie alle anderen Felder, die automatisch angezeigt werden sollen).

Klicken Sie auf **Weiter**.

![5-05-select-attributes.png](./images/505selectattributes.png)

Klicken Sie auf **Fertigstellen**.

![5-06-destination-finish.png](./images/506destinationfinish.png)

Ihre Zielgruppe ist jetzt für Ihr Microsoft Event Hub-Ziel aktiviert.

![5-07-destination-segment-added.png](./images/507destinationsegmentadded.png)

## Nächste Schritte

Navigieren Sie zu [2.4.6 Erstellen Sie Ihr Microsoft Azure-Projekt](./ex6.md){target="_blank"}

Zurück zu [Real-Time CDP: Audience Activation zum Microsoft Azure Event Hub](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
