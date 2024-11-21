---
title: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten von Event Hub in Azure
description: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten von Event Hub in Azure
kt: 5342
doc-type: tutorial
exl-id: 0c2e94ec-00e8-4f47-add7-ca3a08151225
source-git-commit: 216914c9d97827afaef90e21ed7d4f35eaef0cd3
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 1%

---

# 2.4.2 Konfigurieren der Microsoft Azure EventHub-Umgebung

Azure Event Hubs ist ein hochskalierbarer Publish-Subscribe-Service, der Millionen von Ereignissen pro Sekunde aufnehmen und in mehrere Anwendungen streamen kann. Auf diese Weise können Sie die enormen Datenmengen, die von Ihren verbundenen Geräten und Anwendungen erzeugt werden, verarbeiten und analysieren.

## Was sind Azure Event Hubs?

Azure Event Hubs ist eine Big Data-Streaming-Plattform und ein Dienst zur Erfassung von Ereignissen. Es kann Millionen von Ereignissen pro Sekunde empfangen und verarbeiten. An einen Ereignis-Hub gesendete Daten können mithilfe eines beliebigen Echtzeit-Analytics-Anbieters oder von Batch-/Speicheradaptern umgewandelt und gespeichert werden.

Ereignis-Hubs stellen die **Haustür** für eine Ereignis-Pipeline dar, die in Lösungsarchitekturen häufig als Ereignisaufnahme bezeichnet wird. Ein Ereignisaufruf ist eine Komponente oder ein Dienst, die bzw. der zwischen Ereignis-Herausgebern (wie Adobe Experience Platform RTCDP) und Ereigniskonsumenten sitzt, um die Produktion eines Ereignisstreams von der Nutzung dieser Ereignisse zu trennen. Event Hubs bietet eine einheitliche Streaming-Plattform mit Zeitaufbewahrungspuffer, wodurch Ereignisproduzenten von Ereigniskonsumenten abgekoppelt werden.

## Erstellen eines Ereignis-Hubs-Namespace

Wechseln Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Ressource erstellen** aus.

![1-01-open-azure-portal.png](./images/101openazureportal.png)

Geben Sie im Ressourcenbildschirm **Ereignis** in die Suchleiste ein. Suchen Sie die Karte **Ereignis-Hubs** , klicken Sie auf **Erstellen** und klicken Sie dann auf **Ereignis-Hubs**.

![1-02-search-event-hubs.png](./images/102searcheventhubs.png)

Wenn Sie in Azure zum ersten Mal eine Ressource erstellen, müssen Sie eine neue **Ressourcengruppe** erstellen. Wenn Sie bereits über eine Ressourcengruppe verfügen, können Sie diese auswählen (oder eine neue erstellen).

Klicken Sie auf **Neu erstellen** und benennen Sie Ihre Gruppe `--aepUserLdap---aep-enablement`. Klicken Sie auf **OK**.

![1-04-create-resource-group.png](./images/104createresourcegroup.png)

Füllen Sie die übrigen Felder wie angegeben aus:

- Namespace : Definieren Sie Ihren Namespace. Er muss eindeutig sein. Verwenden Sie das folgende Muster `--aepUserLdap---aep-enablement`
- Standort: Wählen Sie einen beliebigen Standort aus.
- Preisklasse: **Einfach**
- Durchsatzeinheiten: **1**

Klicken Sie auf **Überprüfen und erstellen**.

![1-05-create-namespace.png](./images/105createnamespace.png)

Klicken Sie auf **Erstellen**.

![1-07-namespace-create.png](./images/107namespacecreate.png)

Die Bereitstellung Ihrer Ressourcengruppe kann 1-2 Minuten dauern. Nach erfolgreichem Abschluss wird der folgende Bildschirm angezeigt:

![1-08-namespace-deploy.png](./images/108namespacedeploy.png)

## Einrichten des Ereignis-Hub in Azure

Wechseln Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Alle Ressourcen** aus.

![1-09-all-resources.png](./images/109allresources.png)

Klicken Sie in der Liste der Ressourcen auf Ihren `--aepUserLdap---aep-enablement` Ereignis-Hubs-Namespace:

![1-10-list-resources.png](./images/110listresources.png)

Wechseln Sie im Detailbildschirm von `--aepUserLdap---aep-enablement` zu **Entitäten** und klicken Sie auf **Ereignis-Hubs**:

![1-11-eventhub-namespace.png](./images/111eventhubnamespace.png)

Klicken Sie auf **+ Event Hub**.

![1-12-add-event-hub.png](./images/112addeventhub.png)

Verwenden Sie `--aepUserLdap---aep-enablement-event-hub` als Namen und klicken Sie auf **Überprüfen und Erstellen**.

![1-13-create-event-hub.png](./images/113createeventhub.png)

Klicken Sie auf **Erstellen**.

![1-13-create-event-hub.png](./images/113createeventhub1.png)

In **Ereignis-Hub** unter Ihrem Ereignis-Hub-Namespace wird nun Ihr **Ereignis-Hub** aufgelistet.

![1-14-event-hub-list.png](./images/114eventhublist.png)

## Einrichten Ihres Azure Storage-Kontos

Um Ihre Azure Event Hub-Funktion in späteren Übungen zu debuggen, müssen Sie im Rahmen der Einrichtung Ihres Visual Studio Code-Projekts ein Azure Storage-Konto bereitstellen. Sie erstellen jetzt dieses Azure Storage-Konto.

Wechseln Sie zu &quot;[https://portal.azure.com/#home](https://portal.azure.com/#home)&quot;und wählen Sie &quot;**Erstellen einer Ressource**&quot;.

![1-15-event-hub-storage.png](./images/115eventhubstorage.png)

Geben Sie **Speicherkonto** in die Suche ein, suchen Sie die Karte für **Speicherkonto** und klicken Sie auf **Speicherkonto**.

![1-16-event-hub-search-storage.png](./images/116eventhubsearchstorage.png)

Geben Sie Ihre **Ressourcengruppe** (erstellt zu Beginn dieser Übung), verwenden Sie `--aepUserLdap--aepstorage` als Namen Ihres Speicherkontos und wählen Sie **Lokal redundanter Speicher (LRS)** aus, und klicken Sie dann auf **Überprüfen und erstellen**.

![1-18-event-hub-create-review-storage.png](./images/118eventhubcreatereviewstorage.png)

Klicken Sie auf **Erstellen**.

![1-19-event-hub-submit-storage.png](./images/119eventhubsubmitstorage.png)

Die Erstellung unseres Speicherkontos dauert einige Sekunden:

![1-20-event-hub-deploy-storage.png](./images/120eventhubdeploystorage.png)

Wenn Sie fertig sind, wird auf Ihrem Bildschirm die Schaltfläche **Gehe zu Ressource** angezeigt.

Klicken Sie auf **Home**.

![1-21-event-hub-deploy-ready-storage.png](./images/121eventhubdeployreadystorage.png)

Ihr Speicherkonto ist jetzt unter **Letzte Ressourcen** sichtbar.

![1-22-event-hub-deploy-resources-list.png](./images/122eventhubdeployresourceslist.png)

Nächster Schritt: [2.4.3 Konfigurieren Sie Ihr Azure Event Hub-Ziel in Adobe Experience Platform](./ex3.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
