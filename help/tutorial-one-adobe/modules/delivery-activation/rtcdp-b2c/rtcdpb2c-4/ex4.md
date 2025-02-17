---
title: Audience Activation zu Microsoft Azure Event Hub - Erstellen einer Zielgruppe
description: Audience Activation zu Microsoft Azure Event Hub - Erstellen einer Zielgruppe
kt: 5342
doc-type: tutorial
exl-id: d9450e18-7c9b-4a6c-8317-19baf99d43a3
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 3%

---

# 2.4.4 Erstellen einer Zielgruppe

## Einführung

Sie erstellen eine einfache Zielgruppe:

- **Interesse an Plänen** für die sich Kunden qualifizieren, wenn sie die Seite **Pläne** der Demo-Website von CitiSignal besuchen.

### Gut zu wissen

Die Real-Time CDP führt einen Trigger einer Aktivierung an ein Ziel durch, wenn Sie sich für eine Zielgruppe qualifizieren, die Teil der Aktivierungsliste dieses Ziels ist. In diesem Fall enthält die Payload der Zielgruppenqualifizierung, die an dieses Ziel gesendet wird, **alle Zielgruppen, für die Ihr Kundenprofil qualifiziert ist**.

Mit diesem Modul soll gezeigt werden, dass die Zielgruppenqualifizierung Ihres Kundenprofils nahezu in Echtzeit an Ihr Event Hub-Ziel gesendet wird.

### Zielgruppenstatus

Eine Zielgruppen-Qualifizierung in Adobe Experience Platform hat immer **status**-property und kann eine der folgenden sein:

- **Realisiert**: Dies zeigt eine neue Zielgruppen-Qualifizierung an
- **beendet**: Dies bedeutet, dass das Profil sich nicht mehr für die Zielgruppe qualifiziert

## Erstellen der Zielgruppe

Melden Sie sich über die folgende URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

Gehen Sie zu **Zielgruppen**. Klicken Sie auf die Schaltfläche **+ Zielgruppe erstellen**.

![Datenaufnahme](./images/seg.png)

Wählen Sie **Regel erstellen** und klicken Sie auf **Erstellen**.

![Datenaufnahme](./images/seg1.png)

Benennen Sie Ihre `--aepUserLdap-- - Interest in Plans`, legen Sie für die Auswertungsmethode **Edge fest** fügen Sie den Seitennamen aus dem Erlebnisereignis hinzu.

Klicken Sie auf **Ereignisse** und ziehen Sie per Drag-and-Drop **XDM ExperienceEvent > Web > Web-Seitendetails > Name**. Geben Sie **plans** als Wert ein:

![4-05-create-ee-2.png](./images/405createee2.png)

Drag-and-Drop **XDM ExperienceEvent > `--aepTenantId--` > demoEnvironment > brandName**. Geben Sie `--aepUserLdap--` als Wert ein, legen Sie den Vergleichsparameter auf **contains** fest und klicken Sie auf **Veröffentlichen**:

![4-05-create-ee-2-brand.png](./images/405createee2brand.png)

Ihre Zielgruppe ist jetzt veröffentlicht.

![4-05-create-ee-2-brand.png](./images/405createee2brand1.png)

## Nächste Schritte

Gehen Sie zu [2.4.5 Aktivieren Sie Ihre Zielgruppe](./ex5.md){target="_blank"}

Zurück zu [Real-Time CDP: Audience Activation zum Microsoft Azure Event Hub](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
