---
title: Audience Activation zu Microsoft Azure Event Hub - Erstellen einer Zielgruppe
description: Audience Activation zu Microsoft Azure Event Hub - Erstellen einer Zielgruppe
kt: 5342
doc-type: tutorial
exl-id: 56f6a6dc-82aa-4b64-a3f6-b6f59c484ccb
source-git-commit: 216914c9d97827afaef90e21ed7d4f35eaef0cd3
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---

# 2.4.4 Erstellen einer Zielgruppe

## Einführung

Sie erstellen eine einfache Zielgruppe:

- **Interesse an Plänen** , für die sich Kunden qualifizieren, wenn sie die Seite **Pläne** der Demowebsite von CitiSignal besuchen.

### Gut zu wissen

Die Echtzeit-Kundendatenplattform Trigger eine Aktivierung an ein Ziel, wenn Sie sich für eine Zielgruppe qualifizieren, die Teil der Aktivierungsliste dieses Ziels ist. In diesem Fall enthält die Payload der Zielgruppenqualifizierung, die an dieses Ziel gesendet wird, **alle Zielgruppen, für die Ihr Kundenprofil qualifiziert ist**.

Ziel dieses Moduls ist es, zu zeigen, dass die Zielgruppenqualifikation Ihres Kundenprofils nahezu in Echtzeit an Ihr Event Hub-Ziel gesendet wird.

### Zielgruppenstatus

Eine Zielgruppenqualifizierung in Adobe Experience Platform hat immer die Eigenschaft **status** und kann eine der folgenden sein:

- **realisiert**: Dies bedeutet eine neue Zielgruppenqualifikation
- **exited**: Dies bedeutet, dass das Profil nicht mehr für die Zielgruppe qualifiziert ist.

## Audience erstellen

Melden Sie sich bei Adobe Experience Platform an, indem Sie diese URL verwenden: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Wechseln Sie zu **Zielgruppen**. Klicken Sie auf die Schaltfläche **+ Audience erstellen** .

![Datenaufnahme](./images/seg.png)

Wählen Sie **Regel erstellen** und klicken Sie auf **Erstellen**.

![Datenaufnahme](./images/seg1.png)

Benennen Sie Ihre Zielgruppe mit &quot;`--aepUserLdap-- - Interest in Plans`&quot;, legen Sie die Auswertungsmethode auf &quot;**Edge**&quot;fest und fügen Sie den Seitennamen aus dem Erlebnisereignis hinzu.

Klicken Sie auf **Ereignisse** und ziehen Sie **XDM ExperienceEvent > Web > Web page details > Name** per Drag-and-Drop. Geben Sie **plans** als Wert ein:

![4-05-create-ee-2.png](./images/405createee2.png)

Ziehen Sie **XDM ExperienceEvent > `--aepTenantId--` > demoEnvironment > brandName** in den Arbeitsbereich. Geben Sie `--aepUserLdap--` als Wert ein, setzen Sie den Vergleichsparameter auf **contains** und klicken Sie auf **Publish**:

![4-05-create-ee-2-brand.png](./images/405createee2brand.png)

Ihre Audience ist jetzt veröffentlicht.

![4-05-create-ee-2-brand.png](./images/405createee2brand1.png)

Nächster Schritt: [2.4.5 Ihre Audience aktivieren](./ex5.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
