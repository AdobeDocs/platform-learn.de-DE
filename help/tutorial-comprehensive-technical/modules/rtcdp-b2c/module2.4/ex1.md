---
title: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten von Event Hub in Azure
description: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten von Event Hub in Azure
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 1%

---

# 2.4.1 Konfigurieren der Microsoft Azure EventHub-Umgebung

Azure Event Hubs ist ein hochskalierbarer Publish-Subscribe-Service, der Millionen von Ereignissen pro Sekunde aufnehmen und in mehrere Anwendungen streamen kann. Auf diese Weise können Sie die enormen Datenmengen, die von Ihren verbundenen Geräten und Anwendungen erzeugt werden, verarbeiten und analysieren.

## 2.4.1.1 Was ist Azure Event Hub?

Azure Event Hubs ist eine Big Data-Streaming-Plattform und ein Dienst zur Erfassung von Ereignissen. Es kann Millionen von Ereignissen pro Sekunde empfangen und verarbeiten. An einen Ereignis-Hub gesendete Daten können mithilfe eines beliebigen Echtzeit-Analytics-Anbieters oder von Batch-/Speicheradaptern umgewandelt und gespeichert werden.

Ereignis-Hubs stellen die **Haustür** für eine Ereignis-Pipeline dar, die in Lösungsarchitekturen häufig als Ereignisaufnahme bezeichnet wird. Ein Ereignisaufruf ist eine Komponente oder ein Dienst, die bzw. der zwischen Ereignis-Herausgebern (wie Adobe Experience Platform RTCDP) und Ereigniskonsumenten sitzt, um die Produktion eines Ereignisstreams von der Nutzung dieser Ereignisse zu trennen. Event Hubs bietet eine einheitliche Streaming-Plattform mit Zeitaufbewahrungspuffer, wodurch Ereignisproduzenten von Ereigniskonsumenten abgekoppelt werden.

## 2.4.1.2 Namespace für Ereignis-Hubs erstellen

Wechseln Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Ressource erstellen** aus.

![1-01-open-azure-portal.png](./images/1-01-open-azure-portal.png)

Geben Sie im Ressourcenbildschirm **Ereignis** in die Suchleiste ein und wählen Sie **Ereignis-Hubs** aus der Dropdown-Liste aus:

![1-02-search-event-hubs.png](./images/1-02-search-event-hubs.png)

Klicken Sie auf **Erstellen**:

![1-03-event-hub-create.png](./images/1-03-event-hub-create.png)

Wenn Sie in Azure zum ersten Mal eine Ressource erstellen, müssen Sie eine neue **Ressourcengruppe** erstellen. Wenn Sie bereits über eine Ressourcengruppe verfügen, können Sie diese auswählen (oder eine neue erstellen).

Wählen Sie **Neu erstellen** und benennen Sie Ihre Gruppe `--demoProfileLdap---aep-enablement`.

![1-04-create-resource-group.png](./images/1-04-create-resource-group.png)

Führen Sie den Test der Felder wie angegeben durch:

- Namespace : Definieren Sie Ihren Namespace. Er muss eindeutig sein. Verwenden Sie das folgende Muster `--demoProfileLdap---aep-enablement`
- Standort: **West-Europa** bezieht sich auf das Azure-Rechenzentrum in Amsterdam
- Preisklasse: **Einfach**
- Durchsatzeinheiten: **1**

![1-05-create-namespace.png](./images/1-05-create-namespace.png)

Klicken Sie auf **Überprüfen und erstellen**.

![1-06-namespace-review-create.png](./images/1-06-namespace-review-create.png)

Klicken Sie auf **Erstellen**.

![1-07-namespace-create.png](./images/1-07-namespace-create.png)

Die Bereitstellung Ihrer Ressourcengruppe kann 1-2 Minuten dauern. Nach erfolgreichem Abschluss wird der folgende Bildschirm angezeigt:

![1-08-namespace-deploy.png](./images/1-08-namespace-deploy.png)

## 2.4.1.3 Ereignis-Hub in Azure einrichten

Wechseln Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Alle Ressourcen** aus.

![1-09-all-resources.png](./images/1-09-all-resources.png)

Wählen Sie in der Ressourcenliste Ihren `--demoProfileLdap---aep-enablement`-Namespace aus:

![1-10-list-resources.png](./images/1-10-list-resources.png)

Wählen Sie im Detailbildschirm `--demoProfileLdap---aep-enablement` die Option **Ereignis-Hubs**:

![1-11-eventhub-namespace.png](./images/1-11-eventhub-namespace.png)

Klicken Sie auf **+ Event Hub**.

![1-12-add-event-hub.png](./images/1-12-add-event-hub.png)

Verwenden Sie `--demoProfileLdap---aep-enablement-event-hub` als Namen und klicken Sie auf **Erstellen**.

![1-13-create-event-hub.png](./images/1-13-create-event-hub.png)

Klicken Sie auf **Ereignis-Hubs** in Ihrem Ereignis-Hub-Namespace. Ihr **Ereignis-Hub** sollte jetzt aufgelistet sein. In diesem Fall können Sie zur nächsten Übung übergehen.

![1-14-event-hub-list.png](./images/1-14-event-hub-list.png)

## 2.4.1.4 Azure-Speicherkonto einrichten

Um Ihre Azure Event Hub-Funktion in späteren Übungen zu debuggen, müssen Sie im Rahmen der Einrichtung Ihres Visual Studio Code-Projekts ein Azure Storage-Konto bereitstellen. Sie erstellen jetzt dieses Azure Storage-Konto.

Wechseln Sie zu &quot;[https://portal.azure.com/#home](https://portal.azure.com/#home)&quot;und wählen Sie &quot;**Erstellen einer Ressource**&quot;.

![1-15-event-hub-storage.png](./images/1-15-event-hub-storage.png)

Geben Sie **storage** in die Suche ein und wählen Sie **Speicherkonto** aus der Liste aus.

![1-16-event-hub-search-storage.png](./images/1-16-event-hub-search-storage.png)

Wählen Sie **Erstellen** aus.

![1-17-event-hub-create-storage.png](./images/1-17-event-hub-create-storage.png)

Geben Sie Ihre **Ressourcengruppe** (erstellt zu Beginn dieser Übung), verwenden Sie `--demoProfileLdap--aepstorage` als Namen Ihres Speicherkontos, wählen Sie **Lokal redundanter Speicher (LRS)** aus und klicken Sie dann auf **Überprüfen und erstellen**.

![1-18-event-hub-create-review-storage.png](./images/1-18-event-hub-create-review-storage.png)

Klicken Sie auf **Erstellen**.

![1-19-event-hub-submit-storage.png](./images/1-19-event-hub-submit-storage.png)

Die Erstellung Ihres Speicherkontos dauert einige Sekunden:

![1-20-event-hub-deploy-storage.png](./images/1-20-event-hub-deploy-storage.png)

Wenn Sie fertig sind, wird auf Ihrem Bildschirm die Schaltfläche **Gehe zu Ressource** angezeigt.

Klicken Sie auf **Microsoft Azure**.

![1-21-event-hub-deploy-ready-storage.png](./images/1-21-event-hub-deploy-ready-storage.png)

Ihr Speicherkonto ist jetzt unter **Letzte Ressourcen** sichtbar.

![1-22-event-hub-deploy-resources-list.png](./images/1-22-event-hub-deploy-resources-list.png)

Nächster Schritt: [2.4.2 Konfigurieren Sie Ihr Azure Event Hub-Ziel in Adobe Experience Platform](./ex2.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
