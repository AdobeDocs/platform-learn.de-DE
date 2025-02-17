---
title: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten von Event Hub in Azure
description: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten von Event Hub in Azure
kt: 5342
doc-type: tutorial
exl-id: 5c77d09f-18c8-4e29-9392-3f6f8004fa7c
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 1%

---

# 2.4.2 Konfigurieren der Microsoft Azure EventHub-Umgebung

Azure Event Hubs ist ein hochgradig skalierbarer Service für Veröffentlichungsabonnements, der Millionen von Ereignissen pro Sekunde aufnehmen und in mehrere Anwendungen streamen kann. Auf diese Weise können Sie die enormen Datenmengen verarbeiten und analysieren, die von Ihren verbundenen Geräten und Anwendungen produziert werden.

## Was ist Azure Event Hubs?

Azure Event Hubs ist eine Big-Data-Streaming-Plattform und ein Service zur Ereignisaufnahme. Es kann Millionen von Ereignissen pro Sekunde empfangen und verarbeiten. Daten, die an einen Ereignis-Hub gesendet werden, können mithilfe eines beliebigen Echtzeit-Analyseanbieters oder Batch-/Speicheradapters transformiert und gespeichert werden.

Event Hubs stellt die **Eingangstür** für eine Ereignis-Pipeline dar, die in Lösungsarchitekturen häufig als Ereignis-Aufnahme bezeichnet wird. Ein Ereignisaufnehmer ist eine Komponente oder ein Service, die bzw. der sich zwischen Ereignisherausgebern (wie Adobe Experience Platform RTCDP) und Ereigniskonsumenten befindet, um die Produktion eines Ereignis-Streams von der Nutzung dieser Ereignisse zu entkoppeln. Event Hubs bietet eine einheitliche Streaming-Plattform mit einem Zeitaufbewahrungspuffer, der Ereignisproduzenten von Ereigniskonsumenten entkoppelt.

## Erstellen eines Event Hubs-Namespace

Wechseln Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Ressource erstellen** aus.

![1-01-open-azure-portal.png](./images/101openazureportal.png)

Geben Sie im Bildschirm Ressource in **Suchleiste &quot;**&quot; ein. Suchen Sie die Karte **Event Hubs**, klicken Sie auf **Erstellen** und klicken Sie dann auf **Event Hubs**.

![1-02-search-event-hubs.png](./images/102searcheventhubs.png)

Wenn Sie zum ersten Mal eine Ressource in Azure erstellen, müssen Sie eine neue **Ressourcengruppe** erstellen. Wenn Sie bereits über eine Ressourcengruppe verfügen, können Sie diese auswählen (oder eine neue erstellen).

Klicken Sie auf **Neu erstellen** und benennen Sie Ihre Gruppe `--aepUserLdap---aep-enablement` klicken Sie auf **OK**.

![1-04-create-resource-group.png](./images/104createresourcegroup.png)

Füllen Sie den Rest der Felder wie angegeben aus:

- Namespace : Definieren Sie Ihren Namespace, muss er eindeutig sein. Verwenden Sie das folgende Muster `--aepUserLdap---aep-enablement`
- Speicherort: Beliebigen Speicherort auswählen
- Preisstufe: **Standard**
- Durchsatzeinheiten: **1**

Klicken Sie **Überprüfen + Erstellen**.

![1-05-create-namespace.png](./images/105createnamespace.png)

Klicken Sie auf **Erstellen**.

![1-07-namespace-create.png](./images/107namespacecreate.png)

Die Bereitstellung Ihrer Ressourcengruppe kann 1-2 Minuten dauern. Bei Erfolg wird der folgende Bildschirm angezeigt:

![1-08-namespace-deploy.png](./images/108namespacedeploy.png)

## Einrichten des Event Hub in Azure

Wechseln Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Alle Ressourcen** aus.

![1-09-all-resources.png](./images/109allresources.png)

Klicken Sie in der Ressourcenliste auf Ihren `--aepUserLdap---aep-enablement` Event Hubs-Namespace:

![1-10-list-resources.png](./images/110listresources.png)

Gehen Sie `--aepUserLdap---aep-enablement` Detailbildschirm zu **Entitäten** und klicken Sie auf **Ereignis-Hubs**:

![1-11-eventHub-namespace.png](./images/111eventhubnamespace.png)

Klicken Sie auf **+ Event Hub**.

![1-12-add-event-hub.png](./images/112addeventhub.png)

Verwenden Sie `--aepUserLdap---aep-enablement-event-hub` als Namen und klicken Sie auf **Überprüfen + Erstellen**.

![1-13-create-event-hub.png](./images/113createeventhub.png)

Klicken Sie auf **Erstellen**.

![1-13-create-event-hub.png](./images/113createeventhub1.png)

In **Event Hubs** unter Ihrem Event Hub-Namespace wird nun Ihr **Event Hub** aufgeführt.

![1-14-event-hub-list.png](./images/114eventhublist.png)

## Azure-Speicherkonto einrichten

Um Ihre Azure Event Hub-Funktion in späteren Übungen zu debuggen, müssen Sie im Rahmen Ihrer Visual Studio Code-Projekteinrichtung ein Azure-Speicherkonto bereitstellen. Jetzt erstellen Sie dieses Azure-Speicherkonto.

Wechseln Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Ressource erstellen** aus.

![1-15-event-hub-storage.png](./images/115eventhubstorage.png)

Geben Sie **Speicherkonto** in der Suche ein, suchen Sie die Karte für **Speicherkonto** und klicken Sie auf **Speicherkonto**.

![1-16-event-hub-search-storage.png](./images/116eventhubsearchstorage.png)

Geben Sie Ihre **Ressourcengruppe** (zu Beginn dieser Übung erstellt) an, verwenden Sie `--aepUserLdap--aepstorage` als Namen Ihres Speicherkontos und wählen Sie **Lokal redundanter Speicher (LRS)** und klicken Sie dann auf **Überprüfen + Erstellen**.

![1-18-event-hub-create-review-storage.png](./images/118eventhubcreatereviewstorage.png)

Klicken Sie auf **Erstellen**.

![1-19-event-hub-submit-storage.png](./images/119eventhubsubmitstorage.png)

Die Erstellung unseres Speicherkontos wird einige Sekunden dauern:

![1-20-event-hub-deploy-storage.png](./images/120eventhubdeploystorage.png)

Wenn Sie fertig sind, wird auf Ihrem Bildschirm die Schaltfläche **Zur Ressource wechseln** angezeigt.

Klicken Sie auf **Home**.

![1-21-event-hub-deploy-ready-storage.png](./images/121eventhubdeployreadystorage.png)

Ihr Speicherkonto ist jetzt unter &quot;**Ressourcen“**.

![1-22-event-hub-deploy-resources-list.png](./images/122eventhubdeployresourceslist.png)

## Nächste Schritte

Wechseln Sie zu [2.4.3 Konfigurieren Ihres Azure Event Hub-Ziels in Adobe Experience Platform](./ex3.md){target="_blank"}

Zurück zu [Real-Time CDP: Audience Activation zum Microsoft Azure Event Hub](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
