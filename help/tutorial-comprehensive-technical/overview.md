---
title: Übersicht
description: Ausgangspunkt für Dateningenieure, Datenanalysten, Datenarchitekten, Datenwissenschaftler, Orchestrierungstechniker und Marketingexperten, um ein umfassendes Verständnis des Geschäftswerts von Adobe Experience Platform und all seinen Anwendungsdiensten zu gewinnen.
doc-type: multipage-overview
hide: false
exl-id: 88c19383-c185-40f0-b118-6cb82db0ce0e
source-git-commit: 7d2f5f842559b2d6d9f115f3993268a4b36a0fe0
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 2%

---

# Umfassendes technisches Tutorial für Adobe Experience Platform

## Übersicht

Dieses Tutorial ist der perfekte Ausgangspunkt für Dateningenieure, Datenanalysten, Datenarchitekten, Datenwissenschaftler, Orchestrierungs-Ingenieure und Marketingexperten, um ein umfassendes Verständnis des Geschäftswerts von Adobe Experience Platform und all seinen Anwendungsdiensten zu gewinnen. Jede Lektion konzentriert sich auf eine echte Herausforderung, der Unternehmen im heutigen komplexen Personalisierungs-Ökosystem gegenüberstehen, und unterteilt, wie Experience Platform diese Herausforderung in verschiedenen praktischen Übungen löst.

Dieses Tutorial ist sehr vielfältig und bietet klare Einblicke in die folgenden Anwendungen:

- Adobe Experience Platform
- Adobe Experience Platform – Datenerfassung
- Real-time CDP
- Adobe Journey Optimizer
- Customer Journey Analytics

Dieses Tutorial konzentriert sich nicht nur auf Adobe-Anwendungen, sondern berücksichtigt auch das breitere Ökosystem, in dem Marken tätig sind. Dazu liegt der Schwerpunkt in einigen Lektionen auf der Integration von _Nicht-Adobe_-Anwendungen mit Adobe Experience Platform. Daher erhalten Sie ein tiefes Verständnis dafür, wie die folgenden Anwendungen mit Adobe Experience Platform zusammenarbeiten:

- Amazon: AWS Lambda, AWS S3, AWS Kinesis
- Google: Google Cloud Platform, Google BigQuery, Google Display&amp;Video 360, Google AdWords
- Microsoft: Power BI, Azure EventHub, Azure Blob Storage
- Salesforce: Tableau
- Apache Kafka
- Postman
- ...

Nach Abschluss der Übungen in diesem Tutorial können Sie:

- Konfigurieren von Schemas, Feldgruppen, Datensätzen und Identitäten
- Konfigurieren einer Adobe Experience Platform-Datenerfassungseigenschaft und Einrichten der neuen Web SDK-Erweiterung in der Adobe Experience Platform-Datenerfassung
- Daten in Adobe Experience Platform mithilfe der Adobe Experience Platform-Datenerfassung in Echtzeit streamen
- Batch-Aufnahme von Daten in Adobe Experience Platform mithilfe eines Workflows oder mithilfe einer Extract, Transform, Load (ETL)-Anwendung
- Echtzeit-Kundenprofil in Adobe Experience Platform visualisieren und verwenden
- Erstellen von Segmenten
- Verschiedene Adobe Experience Platform-APIs verwenden
- SQL zum Abfragen Ihrer Daten in Adobe Experience Platform verwenden
- Konfigurieren und Ausführen von Journey auf Basis von Triggern in Echtzeit
- Verwenden Sie die Echtzeit-Kundendatenplattform, um Maßnahmen zu ergreifen, indem Sie ein Segment für verschiedene Ziele aktivieren
- Verwenden Sie Customer Journey Analytics, um über Omnichannel-Kundendaten aus verschiedenen Quellen zu berichten, einschließlich Google BigQuery.

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf die Adobe Experience Platform-Datenerfassung: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Zugriff auf Demosystem: [https://dashboard.adobedemo.com/](https://dashboard.adobedemo.com/)

## Videos

Sie finden viele interessante Videos von unseren Tech Academy-Veranstaltungen, von Bootcamps und mehr über unseren YouTube-Kanal [Experience Makers Community](https://www.youtube.com/channel/UCUKG2dkZ9pYuZUPebQ21jUw).

## Inhalt

[0. Erste Schritte](./modules/gettingstarted/gettingstarted/getting-started.md)

- **Zielgruppe:** Alle Teilnehmer des umfassenden Tutorials für Adobe Experience Platform
- **Voraussetzungen:** Zugriff auf Demo System Next, Adobe Experience Platform und Adobe Experience Platform Data Collection.
- **Beschreibung:** In diesem grundlegenden Modul richten Sie alles ein, damit Sie auf die Demoumgebung zugreifen und sie verwenden können.
- **Zeitinvestition:** 30 Minuten

### 1. Datenerfassung

[1.1 Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und des Web-SDK](./modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md)

- **Audience:** Data Engineer, Data Architect
- **Voraussetzungen:** Zugriff auf die Datenerfassung von Adobe Experience Platform und Adobe Experience Platform.
- **Beschreibung:** In diesem grundlegenden Modul erfahren Sie mehr über die Adobe Experience Platform-Datenerfassung und die neue Web SDK-Erweiterung.
- **Zeitinvestition:** 30 Minuten

[1.2 Foundation - Datenerfassung](./modules/datacollection/module1.2/data-ingestion.md)

- **Audience:** Data Engineer, Data Architect
- **Voraussetzungen:** Zugriff auf die Datenerfassung von Adobe Experience Platform und Adobe Experience Platform.
- **Beschreibung:** In diesem grundlegenden Modul erfassen Sie Daten von der Website in Platform.
- **Zeitinvestition:** 120 Minuten

[1.3 Zusammengestellte Zielgruppen](./modules/datacollection/module1.3/fac.md)

- **Zielgruppe:** Data Analyst, Data Engineer, Data Architect
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform
- **Beschreibung:** In diesem Modul erfahren Sie, wie Sie einen eigenen Apache Kafka-Cluster einrichten, Themen, Hersteller und Verbraucher definieren und Daten mithilfe des Adobe Experience Platform Sink Connector for Kafka Connect an Adobe Experience Platform streamen.
- **Zeitinvestition:** 90 Minuten

### 2. Real-Time CDP B2C

[2.1 Foundation - Echtzeit-Kundenprofil](./modules/rtcdp-b2c/module2.1/real-time-customer-profile.md)

- **Audience:** Data Engineer, Data Architect, Marketer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Postman
- **Beschreibung:** In diesem grundlegenden Modul untersuchen Sie das Echtzeit-Kundenprofil in Adobe Experience Platform, indem Sie die Benutzeroberfläche und die API verwenden.
- **Zeitinvestition:** 90 Minuten
- **Laden Sie diese Assets herunter**:
   - [Postman-Sammlungen](./assets/postman/postman_profile.zip)

[2.2 Intelligent Services](./modules/rtcdp-b2c/module2.2/intelligent-services.md)

- **Audience:** Data Engineer, Data Architect, Data Scientist
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Intelligent Services
- **Beschreibung:** In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Intelligent Services einrichten, konfigurieren und verwenden.
- **Zeitinvestition:** 60 Minuten

[2.3 Real-Time CDP - Erstellen eines Segments und Handeln](./modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md)

- **Audience:** Data Architect, Orchestration Engineer, Marketer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Echtzeit-Kundendatenplattform, Adobe Audience Manager, Adobe Target, AWS S3
- **Beschreibung:** In diesem Modul konfigurieren Sie ein Segment, aktivieren es für die Streaming-Segmentierung und aktivieren das Segment für verschiedene Ziele, darunter Google DV360-, Google AdWords-, Adobe Audience Manager-, Adobe Target- und S3-Ziele wie Salesforce Marketing Cloud.
- **Zeitinvestition:** 90 Minuten

[2.4 Real-Time CDP: Segmentaktivierung für Microsoft Azure Event Hub](./modules/rtcdp-b2c/module2.4/segment-activation-microsoft-azure-eventhub.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, die Echtzeit-Kundendatenplattform und Microsoft Azure
- **Beschreibung:** In diesem Modul richten Sie ein Microsoft Azure EventHub-Ziel als Echtzeit-Ziel für die Adobe Experience Platform-Echtzeit-Kundendatenplattform ein. Sie richten außerdem eine Azure-Funktion ein, die in Echtzeit ausgelöst wird, sobald Adobe Experience Platform eine Segment-Payload für Ihr Azure EventHub-Ziel bereitstellt. Die Azure-Funktion, die Sie in Trigger nehmen, zeigt den Mechanismus der Aktivierungsfunktionen der Adobe Experience Platform-Echtzeit-Kundendatenplattform an.
Im Rahmen dieses Moduls erhalten Sie außerdem Informationen dazu, welche Echtzeit-Kundendatenplattform von Trigger tatsächlich eine Payload an ein bestimmtes Ziel bereitstellt. Wir besprechen auch den Status einer Segmentqualifikation und deren Zusammenhang mit der Aktivierung.
- **Zeitinvestition:** 90 Minuten

[2.5 Real-Time CDP-Verbindungen: Ereignisweiterleitung](./modules/rtcdp-b2c/module2.5/aep-data-collection-ssf.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Real-Time CDP-Verbindungen, -Tags und -Ereignisweiterleitungseigenschaften
- **Beschreibung:** In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemas und die Adobe Experience Platform-Datenerfassungseigenschaft, um Daten zu erfassen und diese Daten dann Server-seitig an einen gewünschten Endpunkt weiterzuleiten.
- **Zeitinvestition:** 90 Minuten

[2.6 Streamen von Daten von Apache Kafka nach Real-Time CDP](./modules/rtcdp-b2c/module2.6/aep-apache-kafka.md)

- **Zielgruppe:** Data Analyst, Data Engineer, Data Architect
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform
- **Beschreibung:** In diesem Modul erfahren Sie, wie Sie einen eigenen Apache Kafka-Cluster einrichten, Themen, Hersteller und Verbraucher definieren und Daten mithilfe des Adobe Experience Platform Sink Connector for Kafka Connect an Adobe Experience Platform streamen.
- **Zeitinvestition:** 90 Minuten

### 3. Adobe Journey Optimizer B2C

[3.1 Adobe Journey Optimizer: Orchestrierung](./modules/ajo-b2c/module3.1/journey-orchestration-create-account.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Adobe Journey Optimizer
- **Beschreibung:** In diesem Modul verwenden Sie Adobe Journey Optimizer, um eine Trigger-basierte Journey zu erstellen.
- **Zeitinvestition:** 60 Minuten

[3.2 Adobe Journey Optimizer: Externe Datenquellen und benutzerdefinierte Aktionen](./modules/ajo-b2c/module3.2/journey-orchestration-external-weather-api-sms.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Adobe Journey Optimizer, Open Weather API, Twilio
- **Beschreibung:** In diesem Modul verwenden Sie Adobe Journey Optimizer, um das Kundenverhalten sowohl online als auch offline zu überwachen und intelligent, kontextbezogen und in Echtzeit über verschiedene Kanäle zu reagieren.
- **Zeitinvestition:** 90 Minuten

[3.3 Adobe Journey Optimizer: Offer decisioning](./modules/ajo-b2c/module3.3/offer-decisioning.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Offer decisioning
- **Beschreibung:** In diesem Modul verwenden Sie den Anwendungsdienst Adobe Experience Platform - Angebote/Decisioning in einer praktischen Methode, um personalisierte Angebote und Ihre eigene Angebotsaktivität zu konfigurieren.
- **Zeitinvestition:** 120 Minuten

[3.4 Adobe Journey Optimizer: Ereignisbasierte Journey](./modules/ajo-b2c/module3.4/journeyoptimizer.md)

- **Zielgruppe:** E-Mail-Marketer, Orchestrierungsspezialist, Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Journey Optimizer
- **Beschreibung:** In diesem Modul erfahren Sie alles, was Sie über Journey Optimizer wissen müssen. So können Unternehmen verbundene, kontextbezogene und personalisierte Erlebnisse für ihre Kunden entwerfen und bereitstellen.
- **Zeitinvestition:** 120 Minuten

### 4. Adobe Customer Journey Analytics

[4.1 Customer Journey Analytics: Erstellen eines Dashboards mit Analysis Workspace über Adobe Experience Platform](./modules/cja-b2c/module4.1/customer-journey-analytics-build-a-dashboard.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Customer Journey Analytics
- **Beschreibung:** In diesem Modul erhalten Sie Online- zu Offline-Einblicke, indem Sie ein Dashboard konfigurieren, das kanalübergreifende Daten wie Website-Interaktionen, Mobile-App-Interaktionen, Callcenter-Interaktionen, In-Store-Interaktionen und vieles mehr enthält.
- **Zeitinvestition:** 120 Minuten

[4.2 Customer Journey Analytics: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector](./modules/cja-b2c/module4.2/customer-journey-analytics-bigquery-gcp.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Customer Journey Analytics, Google Cloud Platform, Google BigQuery
- **Beschreibung:** In diesem Modul richten Sie Ihre eigene Instanz der Google Cloud-Plattform ein, laden Demodaten in der Google Cloud-Plattform und verwenden dann den BigQuery Source Connector, um diese Daten von der Google Cloud-Plattform in Adobe Experience Platform aufzunehmen. Schließlich verwenden Sie Customer Journey Analytics, um diese Daten zu visualisieren.
- **Zeitinvestition:** 120 Minuten
- **Laden Sie diese Assets herunter**:
   - [JSON - Beispieldaten: Demo - Loyalitätsdaten](./assets/json/bqLoyalty.json)

### 5. Data Distiller

[5.1 Query Service](./modules/datadistiller/module5.1/query-service.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst, BI-Experte
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Query Service, Power BI oder Tableau
- **Beschreibung:** In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Query Service verwenden.
- **Zeitinvestition:** 90 Minuten
- **Laden Sie diese Assets herunter**:
   - [JSON - Beispieldaten: Demosystem - Ereignisdatensatz für Website](./assets/json/ee.json)
   - [JSON - Beispieldaten: Demosystem - Ereignis-Datensatz für Call Center](./assets/json/callcenter.json)
   - [JSON - Beispieldaten: Demosystem - Profildatensatz für Treueprogramm](./assets/json/loyalty.json)





