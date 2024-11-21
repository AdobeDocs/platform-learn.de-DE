---
title: Audience Activation zu Microsoft Azure Event Hub - Zielgruppe aktivieren
description: Audience Activation zu Microsoft Azure Event Hub - Zielgruppe aktivieren
kt: 5342
doc-type: tutorial
exl-id: 89cfda0e-6c5e-45ab-9506-f0f0f6211e7f
source-git-commit: 216914c9d97827afaef90e21ed7d4f35eaef0cd3
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 4%

---

# 2.4.5 Zielgruppe aktivieren

## Hinzufügen von Zielgruppen zum Azure Event Hub-Ziel

In dieser Übung fügen Sie Ihre Audience `--aepUserLdap-- - Interest in Equipment` zu Ihrem `--aepUserLdap---aep-enablement` Azure Event Hub-Ziel hinzu.

Melden Sie sich bei Adobe Experience Platform an, indem Sie diese URL verwenden: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Wechseln Sie zu **Ziele** und klicken Sie dann auf **Durchsuchen**. Daraufhin werden alle verfügbaren Ziele angezeigt. Suchen Sie Ihr Ziel, klicken Sie auf die drei Punkte**...** wie unten angegeben und klicken Sie dann auf **Zielgruppen aktivieren**.

![5-01-select-destination.png](./images/501selectdestination.png)

Dann wirst du das sehen. Suchen Sie mithilfe Ihrer LDAP-Datei nach Ihrer Zielgruppe und wählen Sie `--aepUserLdap-- - Interest in Plans` aus der Zielgruppenliste aus.

Klicken Sie auf **Weiter**.

![5-04-select-segment.png](./images/504selectsegment.png)

Klicken Sie auf **Neues Feld hinzufügen**, klicken Sie auf Schema durchsuchen und wählen Sie das Feld `--aepTenantId--identification.core.ecid` aus (löschen Sie alle anderen Felder, die automatisch angezeigt werden).

Klicken Sie auf **Weiter**.

![5-05-select-attributes.png](./images/505selectattributes.png)

Klicken Sie auf **Fertigstellen**.

![5-06-destination-finish.png](./images/506destinationfinish.png)

Ihre Zielgruppe ist jetzt für Ihr Microsoft Event Hub-Ziel aktiviert.

![5-07-destination-segment-added.png](./images/507destinationsegmentadded.png)

Nächster Schritt: [2.4.6 Microsoft Azure Project erstellen](./ex6.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
