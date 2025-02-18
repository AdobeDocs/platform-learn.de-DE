---
title: Überblick - Umfassendes technisches Tutorial - One Adobe
description: Umfassendes technisches Tutorial - One Adobe
doc-type: multipage-overview
exl-id: 5bc0d621-0662-4d94-80a0-b6c173c0ac9e
source-git-commit: 9169b0f9be7f192fd7e16ddcc2ae32f6a8cca92c
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 2%

---

# Umfassendes technisches Tutorial - One Adobe

![Tech Insiders](./assets/images/techinsiders.png){width="50px" align="left"}

## Übersicht

Dieses Tutorial ist sehr vielfältig und bietet klare Einblicke in die folgenden Programme:

- Adobe Firefly Services
- Adobe Photoshop
- Adobe Workfront und Adobe Workfront Fusion
- Adobe Experience Manager Cloud Service, Sites, Assets und Edge Delivery Services
- Adobe Experience Platform
- Adobe Real-Time CDP
- Adobe Journey Optimizer


Dieses Tutorial konzentriert sich nicht nur auf Adobe-Anwendungen, sondern berücksichtigt das allgemeinere Ökosystem, in dem Marken operieren. Um dies zu erreichen, konzentrieren sich einige Lektionen darauf, wie Nicht-Adobe-Anwendungen in Adobe-Anwendungen integriert werden. Auf diese Weise erhalten Sie einen tiefen Einblick in die Zusammenarbeit der folgenden Programme mit Adobe Experience Platform:

- Amazon AWS
- Google Cloud Platform
- Microsoft Azure
- Postman
- Snowflake
- ...

## Voraussetzungen

Wenn Sie dieses Tutorial mit Ihrer eigenen Adobe Experience Cloud-Instanz durchführen möchten, müssen die folgenden Programme in Ihrer Instanz bereitgestellt werden und Sie müssen auf Folgendes zugreifen können:

- Adobe Firefly [https://firefly.adobe.com/](https://firefly.adobe.com/){target="_blank"}
- Adobe Photoshop
- Adobe Workfront
- Adobe Workfront Fusion [https://fusion.adobe.com/](https://fusion.adobe.com/){target="_blank"}
- Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform){target="_blank"}
- Adobe Experience Platform-Datenerfassung: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/){target="_blank"}
- Zugriff auf das Demosystem: [https://dsn.adobe.com/](https://dsn.adobe.com/){target="_blank"}

## Abschluss und Zertifizierung

Dieses Tutorial ist Teil eines Adobe-Zertifizierungskurses. Sie können sich neben diesem Tutorial unter [https://certification.adobe.com für den Kurs ](https://certification.adobe.com).

Für jedes Modul, das Sie mit dem folgenden Tutorial abschließen, müssen Sie einen Abschlussnachweis wie [ angegeben ](./completion.md).

## Inhaltsstatus

Um den Status der folgenden Inhalte zu überprüfen, gehen Sie bitte zur [Statusseite](./status.md){target="_blank"}.

### Erste Schritte

[Erste Schritte](./modules/getting-started/gettingstarted/getting-started.md){target="_blank"}

In diesem grundlegenden Modul bereiten Sie alles vor, damit Sie auf die Demo-Umgebung zugreifen und sie verwenden können.

### 1. Workflow und Planung

### 2. Erstellung und Produktion

[1.1 Adobe Firefly Services](./modules/creation-production/module1.1/firefly-services.md){target="_blank"}

In diesem Modul verwenden Sie Adobe Firefly Services-APIs, Photoshop-APIs und Microsoft Azure Storage-Services, um Bilder zu generieren und programmgesteuert zu speichern.

[1.2 Creative Workflow-Automatisierung mit Workfront Fusion](./modules/creation-production/module1.2/automation.md){target="_blank"}

In diesem grundlegenden Modul verwenden Sie Adobe Workfront Fusion, um Ihre Workflows zur Inhaltserstellung zu automatisieren und zu skalieren.

### 3. Asset-Management

[1.1 Adobe Experience Manager Cloud Service und Edge Delivery Services](./modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}

In diesem Grundmodul richten Sie Ihr Adobe Experience Manager Cloud Service-Programm, Ihre Site und Ihr Assets-Repository ein.

[1.2 Workflow-Management mit Adobe Workfront](./modules/asset-mgmt/module2.2/workfront.md){target="_blank"}

In diesem grundlegenden Modul konfigurieren und verwenden Sie Adobe Workfront, um Genehmigungsflüsse zu verwalten, und Sie verwenden Integrationen mit Adobe Experience Manager Assets, dem universellen Editor, Photoshop und mehr.

### 4. Versand und Aktivierung

#### Datenerfassung

[1.1 Foundation - Einrichtung von Adobe Experience Platform Data Collection und Web SDK](./modules/delivery-activation/datacollection/dc1.1/data-ingestion-launch-web-sdk.md)

In diesem grundlegenden Modul erfahren Sie mehr über die Datenerfassung in Adobe Experience Platform und die neue Web-SDK-Erweiterung.

[1.2 Foundation - Datenaufnahme](./modules/delivery-activation/datacollection/dc1.2/data-ingestion.md)

In diesem grundlegenden Modul nehmen Sie Daten aus verschiedenen Quellen in Adobe Experience Platform auf

[1.3 Federated Audience-Komposition](./modules/delivery-activation/datacollection/dc1.3/fac.md)

In diesem Modul erfahren Sie, wie Sie ein Federated-Audiences-Modell einrichten und Zielgruppen mithilfe von Federated-Daten generieren.

#### Real-Time CDP B2C

[2.1 Foundation - Echtzeit-Kundenprofil](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-1/real-time-customer-profile.md)

In diesem grundlegenden Modul lernen Sie das Echtzeit-Kundenprofil in Adobe Experience Platform kennen, indem Sie die Benutzeroberfläche und API verwenden.

[2.2 Intelligent Services](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-2/intelligent-services.md)

In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Intelligent Services einrichten, konfigurieren und verwenden.

[2.3 Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-3/real-time-cdp-build-a-segment-take-action.md)

In diesem Modul konfigurieren Sie eine Zielgruppe und aktivieren die Zielgruppe für mehrere Ziele, einschließlich Google DV360, Adobe Target und AWS S3.

[2.4 Real-Time CDP: Audience Activation zu Microsoft Azure Event Hub](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-4/segment-activation-microsoft-azure-eventhub.md)

In diesem Modul richten Sie ein Microsoft Azure EventHub-Ziel als Echtzeit-Ziel für Adobe Experience Platform Real-Time CDP ein.

[2.5 Real-Time CDP-Verbindungen: Ereignisweiterleitung](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-5/aep-data-collection-ssf.md)

In diesem Modul leiten Sie Daten Server-seitig an mehrere Endpunkte weiter, z. B. Google Cloud Platform Pub/Sub und AWS Kinesis.

[2.6 Streamen Sie Daten von Apache Kafka nach Real-Time CDP](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-6/aep-apache-kafka.md)

In diesem Modul erfahren Sie, wie Sie Ihren eigenen Apache Kafka-Cluster einrichten und Daten in Adobe Experience Platform streamen.

#### Adobe Journey Optimizer B2C

[3.1 Adobe Journey Optimizer: Orchestrierung](./modules/delivery-activation/ajo-b2c/ajob2c-1/journey-orchestration-create-account.md)

In diesem Modul werden Sie Adobe Journey Optimizer verwenden, um eine Trigger-basierte Journey zu erstellen.

[3.2 Adobe Journey Optimizer: Externe Datenquellen und benutzerdefinierte Aktionen](./modules/delivery-activation/ajo-b2c/ajob2c-2/journey-orchestration-external-weather-api-sms.md)

In diesem Modul verwenden Sie Adobe Journey Optimizer, um das Kundenverhalten sowohl online als auch offline zu überwachen und auf verschiedene Kanäle intelligent, kontextbezogen und in Echtzeit zu reagieren.

[3.3 Adobe Journey Optimizer: Offer Decisioning](./modules/delivery-activation/ajo-b2c/ajob2c-3/offer-decisioning.md)

In diesem Modul verwenden Sie Adobe Journey Optimizer zum Konfigurieren personalisierter Angebote und Ihrer eigenen Angebotsentscheidung.

[3.4 Adobe Journey Optimizer: Veranstaltungsbasierte Journey](./modules/delivery-activation/ajo-b2c/ajob2c-4/journeyoptimizer.md)

In diesem Modul erfahren Sie alles, was es über Journey Optimizer zu wissen gibt. Damit können Unternehmen vernetzte, kontextuelle und personalisierte Erlebnisse für ihre Kunden entwerfen und bereitstellen.

[3.5 Adobe Journey Optimizer: Übersetzungsdienstleistungen](./modules/delivery-activation/ajo-b2c/ajob2c-5/ajotranslationsvcs.md)

In diesem Modul erfahren Sie, wie Sie in Adobe Journey Optimizer Übersetzungsdienste einrichten und verwenden können, um Ihre Nachrichten für Ihre Kunden zu lokalisieren.

### 5. Reporting und Erkenntnisse

#### Adobe Customer Journey Analytics

[1.1 Customer Journey Analytics: Erstellen eines Dashboards mit Analysis Workspace zusätzlich zu Adobe Experience Platform](./modules/reporting-insights/cja-b2c/cjab2c-1/customer-journey-analytics-build-a-dashboard.md)

In diesem Modul erhalten Sie Online- bis Offline-Einblicke, indem Sie ein Dashboard konfigurieren, das Omni-Channel-Daten enthält.

[1.2 Customer Journey Analytics: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector](./modules/reporting-insights/cja-b2c/cjab2c-2/customer-journey-analytics-bigquery-gcp.md)

In diesem Modul richten Sie Ihre eigene Instanz von Google Cloud Platform ein, laden Demodaten in Google Cloud Platform und verwenden dann den BigQuery Source Connector , um diese Daten von Google Cloud Platform in Adobe Experience Platform aufzunehmen.

#### Data Distiller

[2.1 Abfrage-Service](./modules/reporting-insights/datadistiller/dd-1/query-service.md)

In diesem Modul erfahren Sie, wie Sie den Abfrage-Service von Adobe Experience Platform verwenden.

![Tech Insiders](./assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.
