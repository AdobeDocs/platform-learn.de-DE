---
title: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten von Event Hub in Azure
description: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten von Event Hub in Azure
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 9434ac83-5554-48bf-838c-7346d571efbf
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---

# 13.1 Konfigurieren der Microsoft Azure EventHub-Umgebung

Azure Event Hubs ist ein hochskalierbarer Publish-Subscribe-Service, der Millionen von Ereignissen pro Sekunde aufnehmen und in mehrere Anwendungen streamen kann. Auf diese Weise können Sie die enormen Datenmengen, die von Ihren verbundenen Geräten und Anwendungen erzeugt werden, verarbeiten und analysieren.

## 13.1.1 Was ist Azure Event Hub?

Azure Event Hubs ist eine Big Data-Streaming-Plattform und ein Dienst zur Erfassung von Ereignissen. Es kann Millionen von Ereignissen pro Sekunde empfangen und verarbeiten. An einen Ereignis-Hub gesendete Daten können mithilfe eines beliebigen Echtzeit-Analytics-Anbieters oder von Batch-/Speicheradaptern umgewandelt und gespeichert werden.

Ereignis-Hubs stellen die **Vorderseite** für eine Ereignis-Pipeline, die in Lösungsarchitekturen häufig als Ereignisaufnahme bezeichnet wird. Ein Ereignisaufruf ist eine Komponente oder ein Dienst, die bzw. der zwischen Ereignis-Herausgebern (wie Adobe Experience Platform RTCDP) und Ereigniskonsumenten sitzt, um die Produktion eines Ereignisstreams von der Nutzung dieser Ereignisse zu trennen. Event Hubs bietet eine einheitliche Streaming-Plattform mit Zeitaufbewahrungspuffer, wodurch Ereignisproduzenten von Ereigniskonsumenten abgekoppelt werden.

## 13.1.2 Namespace für Ereignis-Hubs erstellen

Navigieren Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Ressource erstellen**.

![1-01-open-azure-portal.png](./images/1-01-open-azure-portal.png)

Geben Sie im Ressourcen-Bildschirm **Ereignis** in der Suchleiste und wählen Sie **Ereignis-Hubs** aus der Dropdown-Liste:

![1-02-search-event-hubs.png](./images/1-02-search-event-hubs.png)

Klicken Sie auf **Erstellen**:

![1-03-event-hub-create.png](./images/1-03-event-hub-create.png)

Wenn Sie in Azure zum ersten Mal eine Ressource erstellen, müssen Sie eine neue erstellen **Ressourcengruppe**. Wenn Sie bereits über eine Ressourcengruppe verfügen, können Sie diese auswählen (oder eine neue erstellen).

Auswählen **Neu erstellen**, benennen Sie Ihre Gruppe. `--demoProfileLdap---aep-enablement`.

![1-04-create-resource-group.png](./images/1-04-create-resource-group.png)

Führen Sie den Test der Felder wie angegeben durch:

- Namespace : Definieren Sie Ihren Namespace. Er muss eindeutig sein. Verwenden Sie das folgende Muster. `--demoProfileLdap---aep-enablement`
- Ort: **Westeuropa** bezieht sich auf das Azure-Rechenzentrum in Amsterdam
- Preisklasse: **Allgemein**
- Durchsatzeinheiten: **1**

![1-05-create-namespace.png](./images/1-05-create-namespace.png)

Klicken **Überprüfen und erstellen**.

![1-06-namespace-review-create.png](./images/1-06-namespace-review-create.png)

Klicken Sie auf **Erstellen**.

![1-07-namespace-create.png](./images/1-07-namespace-create.png)

Die Bereitstellung Ihrer Ressourcengruppe kann 1-2 Minuten dauern. Nach erfolgreichem Abschluss wird der folgende Bildschirm angezeigt:

![1-08-namespace-deploy.png](./images/1-08-namespace-deploy.png)

## 13.1.3 Einrichten des Ereignis-Hub in Azure

Navigieren Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Alle Ressourcen**.

![1-09-all-resources.png](./images/1-09-all-resources.png)

Wählen Sie in der Liste der Ressourcen Ihre `--demoProfileLdap---aep-enablement` namespace:

![1-10-list-resources.png](./images/1-10-list-resources.png)

In `--demoProfileLdap---aep-enablement` Detailbildschirm, wählen Sie **Ereignis-Hubs**:

![1-11-eventhub-namespace.png](./images/1-11-eventhub-namespace.png)

Klicken **+ Ereignis-Hub**.

![1-12-add-event-hub.png](./images/1-12-add-event-hub.png)

Verwendung `--demoProfileLdap---aep-enablement-event-hub` als Namen angeben und auf **Erstellen**.

![1-13-create-event-hub.png](./images/1-13-create-event-hub.png)

Klicken **Ereignis-Hubs** in Ihrem Ereignis-Hub-Namespace. Sie sollten jetzt Ihre **Ereignis-Hub** aufgelistet. In diesem Fall können Sie zur nächsten Übung übergehen.

![1-14-event-hub-list.png](./images/1-14-event-hub-list.png)

## 13.1.4 Azure-Speicherkonto einrichten

Um Ihre Azure Event Hub-Funktion in späteren Übungen zu debuggen, müssen Sie im Rahmen der Einrichtung Ihres Visual Studio Code-Projekts ein Azure Storage-Konto bereitstellen. Sie erstellen jetzt dieses Azure Storage-Konto.

Navigieren Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home) und wählen Sie **Erstellen einer Ressource**.

![1-15-event-hub-storage.png](./images/1-15-event-hub-storage.png)

Eingabe **Speicher** in der Suche und wählen Sie **Speicherkonto** aus der Liste.

![1-16-event-hub-search-storage.png](./images/1-16-event-hub-search-storage.png)

Wählen Sie **Erstellen** aus.

![1-17-event-hub-create-storage.png](./images/1-17-event-hub-create-storage.png)

Geben Sie Ihre **Ressourcengruppe** (zu Beginn dieser Übung erstellt), verwenden Sie `--demoProfileLdap--aepstorage` als Namen Ihres Speicherkontos verwenden, und wählen Sie **Lokal redundanter Speicher (LRS)** Klicken Sie auf **Überprüfen und erstellen**.

![1-18-event-hub-create-review-storage.png](./images/1-18-event-hub-create-review-storage.png)

Klicken Sie auf **Erstellen**.

![1-19-event-hub-submit-storage.png](./images/1-19-event-hub-submit-storage.png)

Die Erstellung Ihres Speicherkontos dauert einige Sekunden:

![1-20-event-hub-deploy-storage.png](./images/1-20-event-hub-deploy-storage.png)

Wenn Sie fertig sind, zeigt der Bildschirm **Zu Ressource wechseln** Schaltfläche.

Klicken **Microsoft Azure**.

![1-21-event-hub-deploy-ready-storage.png](./images/1-21-event-hub-deploy-ready-storage.png)

Ihr Speicherkonto ist jetzt unter **Letzte Ressourcen**.

![1-22-event-hub-deploy-resources-list.png](./images/1-22-event-hub-deploy-resources-list.png)

Nächster Schritt: [13.2 Konfigurieren des Azure Event Hub-Ziels in Adobe Experience Platform](./ex2.md)

[Zurück zu Modul 13](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
