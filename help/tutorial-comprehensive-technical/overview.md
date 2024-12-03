---
title: Übersicht
description: Ausgangspunkt für Dateningenieure, Datenanalysten, Datenarchitekten, Datenwissenschaftler, Orchestrierungstechniker und Marketingexperten, um ein umfassendes Verständnis des Geschäftswerts von Adobe Experience Platform und all seinen Anwendungsdiensten zu gewinnen.
doc-type: multipage-overview
source-git-commit: 8270f69dd04714e217ddbb4d125157799cba2940
workflow-type: tm+mt
source-wordcount: '1207'
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
- Erstellen von Zielgruppen
- Verschiedene Adobe Experience Platform-APIs verwenden
- SQL zum Abfragen Ihrer Daten in Adobe Experience Platform verwenden
- Konfigurieren und Ausführen von Journey auf Basis von Triggern in Echtzeit
- Verwenden Sie die Echtzeit-Kundendatenplattform, um Maßnahmen zu ergreifen, indem Sie eine Zielgruppe für verschiedene Ziele aktivieren
- Verwenden Sie Customer Journey Analytics, um über Omnichannel-Kundendaten aus verschiedenen Quellen zu berichten, einschließlich Google BigQuery.

## Voraussetzungen

Wenn Sie dieses Tutorial mit Ihrer eigenen Adobe Experience Platform-Instanz durchführen möchten, befolgen Sie die Anweisungen [hier](./setup.md) , um Ihre Organisation für das Tutorial vorzubereiten.

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf die Adobe Experience Platform-Datenerfassung: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Zugriff auf Demosystem: [https://dsn.adobe.com/](https://dsn.adobe.com/)

## Videos

Sie finden viele interessante Videos aus unseren Tech Academy-Webinaren, aus Bootcamps und mehr über unseren YouTube-Kanal [Experience Makers Community](https://www.youtube.com/channel/UCUKG2dkZ9pYuZUPebQ21jUw).

## Abschluss und Zertifizierung

Dieses Tutorial ist Teil eines Adobe-Zertifizierungskurses. Sie können sich für den Kurs neben diesem Tutorial anmelden, indem Sie zu [https://certification.adobe.com](https://certification.adobe.com) navigieren.

Für jedes Modul, das Sie mithilfe des unten stehenden Tutorials abschließen, müssen Sie einen Abschlussnachweis gemäß [hier](./completion.md) einreichen.

## Inhalt

[0. Erste Schritte](./modules/gettingstarted/gettingstarted/getting-started.md)

In diesem grundlegenden Modul richten Sie alles ein, damit Sie auf die Demoumgebung zugreifen und sie verwenden können.

**Zeitinvestition:** 30 Minuten

### 1. Datenerfassung

[1.1 Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und des Web-SDK](./modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md)

In diesem grundlegenden Modul erfahren Sie mehr über die Adobe Experience Platform-Datenerfassung und die neue Web SDK-Erweiterung.

**Zeitinvestition:** 30 Minuten

[1.2 Foundation - Datenerfassung](./modules/datacollection/module1.2/data-ingestion.md)

In diesem grundlegenden Modul erfassen Sie Daten aus verschiedenen Quellen in Adobe Experience Platform.

**Zeitinvestition:** 120 Minuten

[1.3 Zusammengestellte Zielgruppenkomposition](./modules/datacollection/module1.3/fac.md)

In diesem Modul erfahren Sie, wie Sie ein Federated Audiences-Modell einrichten und Zielgruppen mithilfe von Federated-Daten generieren.

**Zeitinvestition:** 90 Minuten

### 2. Real-Time CDP B2C

[2.1 Foundation - Echtzeit-Kundenprofil](./modules/rtcdp-b2c/module2.1/real-time-customer-profile.md)

In diesem grundlegenden Modul untersuchen Sie das Echtzeit-Kundenprofil in Adobe Experience Platform, indem Sie die Benutzeroberfläche und die API verwenden.

**Zeitinvestition:** 90 Minuten

[2.2 Intelligent Services](./modules/rtcdp-b2c/module2.2/intelligent-services.md)

In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Intelligent Services einrichten, konfigurieren und verwenden.

**Zeitinvestition:** 60 Minuten

[2.3 Real-Time CDP - Erstellen einer Zielgruppe und Ergreifen von Maßnahmen](./modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md)

In diesem Modul konfigurieren Sie eine Zielgruppe und aktivieren die Zielgruppe für verschiedene Ziele, einschließlich Google DV360, Adobe Target und AWS S3.

**Zeitinvestition:** 90 Minuten

[2.4 Real-Time CDP: Audience Activation zu Microsoft Azure Event Hub](./modules/rtcdp-b2c/module2.4/segment-activation-microsoft-azure-eventhub.md)

In diesem Modul richten Sie ein Microsoft Azure EventHub-Ziel als Echtzeit-Ziel für die Echtzeit-Kundendatenplattform von Adobe Experience Platform ein. Sie richten außerdem eine Azure-Funktion ein und stellen sie bereit, die in Echtzeit ausgelöst wird, sobald Adobe Experience Platform eine Zielgruppen-Payload für Ihr Azure EventHub-Ziel bereitstellt. Die Azure-Funktion, die Sie in Trigger nehmen, zeigt den Mechanismus der Aktivierungsfunktionen der Adobe Experience Platform-Echtzeit-Kundendatenplattform an.
Im Rahmen dieses Moduls erhalten Sie außerdem Informationen dazu, welche Echtzeit-Kundendatenplattform von Trigger tatsächlich eine Payload an ein bestimmtes Ziel bereitstellt. Wir besprechen auch den Status einer Audience-Qualifizierung und deren Zusammenhang mit der Aktivierung.

**Zeitinvestition:** 90 Minuten

[2.5 Real-Time CDP-Verbindungen: Ereignisweiterleitung](./modules/rtcdp-b2c/module2.5/aep-data-collection-ssf.md)

In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemas und die Datenerfassungseigenschaft von Adobe Experience Platform, um Daten zu erfassen und diese Daten dann Server-seitig an mehrere Endpunkte wie Google Cloud Platform Pub/Sub und AWS Kinesis weiterzuleiten.

**Zeitinvestition:** 90 Minuten

[2.6 Streamen von Daten von Apache Kafka nach Real-Time CDP](./modules/rtcdp-b2c/module2.6/aep-apache-kafka.md)

In diesem Modul erfahren Sie, wie Sie einen eigenen Apache Kafka-Cluster einrichten, Themen, Hersteller und Verbraucher definieren und Daten mit dem Adobe Experience Platform Sink Connector für Kafka Connect an Adobe Experience Platform streamen.

**Zeitinvestition:** 90 Minuten

### 3. Adobe Journey Optimizer B2C

[3.1 Adobe Journey Optimizer: Orchestrierung](./modules/ajo-b2c/module3.1/journey-orchestration-create-account.md)

In diesem Modul verwenden Sie Adobe Journey Optimizer, um eine Trigger-basierte Journey zu erstellen.

**Zeitinvestition:** 60 Minuten

[3.2 Adobe Journey Optimizer: Externe Datenquellen und benutzerdefinierte Aktionen](./modules/ajo-b2c/module3.2/journey-orchestration-external-weather-api-sms.md)

In diesem Modul verwenden Sie Adobe Journey Optimizer, um das Kundenverhalten sowohl online als auch offline zu überwachen und intelligent, kontextbezogen und in Echtzeit über verschiedene Kanäle zu reagieren.

**Zeitinvestition:** 90 Minuten

[3.3 Adobe Journey Optimizer: Offer decisioning](./modules/ajo-b2c/module3.3/offer-decisioning.md)

In diesem Modul verwenden Sie den Anwendungsdienst Adobe Experience Platform - Angebote/Decisioning in einer praktischen Methode, um personalisierte Angebote und Ihre eigene Angebotsaktivität zu konfigurieren.

**Zeitinvestition:** 120 Minuten

[3.4 Adobe Journey Optimizer: Ereignisbasierte Journey](./modules/ajo-b2c/module3.4/journeyoptimizer.md)

In diesem Modul erfahren Sie alles, was Sie über Journey Optimizer wissen müssen, um Unternehmen bei der Erstellung und Bereitstellung von vernetzten, kontextbezogenen und personalisierten Erlebnissen für ihre Kunden zu unterstützen.

**Zeitinvestition:** 120 Minuten

### 4. Adobe Customer Journey Analytics

[4.1 Customer Journey Analytics: Erstellen eines Dashboards mit Analysis Workspace über Adobe Experience Platform](./modules/cja-b2c/module4.1/customer-journey-analytics-build-a-dashboard.md)

In diesem Modul erhalten Sie Online- und Offline-Einblicke, indem Sie ein Dashboard konfigurieren, das kanalübergreifende Daten wie Website-Interaktionen, Mobile-App-Interaktionen, Callcenter-Interaktionen, In-Store-Interaktionen und vieles mehr enthält.

**Zeitinvestition:** 120 Minuten

[4.2 Customer Journey Analytics: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector](./modules/cja-b2c/module4.2/customer-journey-analytics-bigquery-gcp.md)

In diesem Modul richten Sie Ihre eigene Instanz von Google Cloud Platform ein, laden Demodaten in Google Cloud Platform und verwenden dann den BigQuery Source Connector, um diese Daten von Google Cloud Platform in Adobe Experience Platform aufzunehmen. Schließlich verwenden Sie Customer Journey Analytics, um diese Daten zu visualisieren.

**Zeitinvestition:** 120 Minuten

### 5. Data Distiller

[5.1 Query Service](./modules/datadistiller/module5.1/query-service.md)

In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Query Service verwenden.

**Zeitinvestition:** 90 Minuten