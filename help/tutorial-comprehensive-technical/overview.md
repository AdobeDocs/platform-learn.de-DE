---
title: Übersicht
description: Ausgangspunkt für Dateningenieure, Datenanalysten, Datenarchitekten, Datenwissenschaftler, Orchestrierungsingenieure und Marketing-Experten, um ein umfassendes Verständnis des Geschäftswerts von Adobe Experience Platform und aller seiner Anwendungs-Services zu erhalten.
doc-type: multipage-overview
exl-id: 88c19383-c185-40f0-b118-6cb82db0ce0e
source-git-commit: bd46be455f88007174f7e6be9a1ce5f508edc09b
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 2%

---

# Umfassendes technisches Tutorial für Adobe Experience Platform

![Tech Insiders](./assets/images/techinsiders.png){width="50px" align="left"}

## Übersicht

Dieses Tutorial ist der perfekte Ausgangspunkt für Dateningenieure, Datenanalysten, Datenarchitekten, Datenwissenschaftler, Orchestrierungsingenieure und Marketing-Experten, um ein umfassendes Verständnis des Geschäftswerts von Adobe Experience Platform und aller seiner Anwendungs-Services zu erhalten. Jede Lektion konzentriert sich auf eine echte Herausforderung, vor der Unternehmen im heutigen komplexen Ökosystem der Personalisierung stehen, und schlüsselt die Möglichkeiten des Experience Platform bei der Lösung dieser Herausforderung in verschiedenen praktischen Übungen auf.

Dieses Tutorial ist sehr vielfältig und bietet klare Einblicke in die folgenden Programme:

- Adobe Experience Platform
- Adobe Experience Platform – Datenerfassung
- Real-time CDP
- Adobe Journey Optimizer
- Customer Journey Analytics

Dieses Tutorial konzentriert sich nicht nur auf Adobe-Anwendungen, sondern berücksichtigt das allgemeinere Ökosystem, in dem Marken operieren. Um dies zu erreichen, konzentrieren sich einige Lektionen darauf, wie _Nicht-Adobe_-Anwendungen mit Adobe Experience Platform integriert werden. Auf diese Weise erhalten Sie einen tiefen Einblick in die Zusammenarbeit der folgenden Programme mit Adobe Experience Platform:

- Amazon: AWS Lambda, AWS S3, AWS Kinesis
- Google: Google Cloud Platform, Google BigQuery, Google Display&amp;Video 360, Google AdWords
- Microsoft: Power BI, Azure EventHub, Azure Blob Storage
- Salesforce: Tableau
- Apache Kafka
- Postman
- ...

Nach Abschluss der Übungen in dieser Anleitung haben Sie folgende Möglichkeiten:

- Konfigurieren von Schemata, Feldergruppen, Datensätzen und Identitäten
- Konfigurieren Sie eine Adobe Experience Platform-Datenerfassungseigenschaft und richten Sie die neue Web-SDK-Erweiterung in der Adobe Experience Platform-Datenerfassung ein
- Streamen von Daten in Echtzeit in Adobe Experience Platform mithilfe der Adobe Experience Platform-Datenerfassung
- Batch-Aufnahme von Daten in Adobe Experience Platform mithilfe eines Workflows oder einer ETL-Anwendung (Extract, Transform, Load)
- Visualisieren und Verwenden des Echtzeit-Kundenprofils in Adobe Experience Platform
- Erstellen von Zielgruppen
- Verschiedene Adobe Experience Platform-APIs nutzen
- SQL verwenden, um Daten in Adobe Experience Platform abzufragen
- Konfigurieren und Ausführen von Trigger-basierten Journey in Echtzeit
- Verwenden Sie die Real-Time CDP, um eine Zielgruppe für verschiedene Ziele zu aktivieren
- Verwenden Sie Customer Journey Analytics, um Berichte zu Omni-Channel-Kundendaten aus verschiedenen Quellen zu erstellen, einschließlich Google BigQuery.

## Voraussetzungen

Wenn Sie dieses Tutorial mit Ihrer eigenen Adobe Experience Platform-Instanz durchführen möchten, befolgen Sie die Anweisungen [hier](./setup.md), um Ihre Organisation für das Tutorial vorzubereiten.

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf die Adobe Experience Platform-Datenerfassung: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Zugriff auf das Demosystem: [https://dsn.adobe.com/](https://dsn.adobe.com/)

## Videos

Viele interessante Videos finden Sie in unseren Webinaren zur Tech Academy, in Bootcamps und vielem mehr auf unserem [Experience Makers Community YouTube-](https://www.youtube.com/channel/UCUKG2dkZ9pYuZUPebQ21jUw).

## Abschluss und Zertifizierung

Dieses Tutorial ist Teil eines Adobe-Zertifizierungskurses. Sie können sich neben diesem Tutorial unter [https://certification.adobe.com für den Kurs ](https://certification.adobe.com).

Für jedes Modul, das Sie mit dem folgenden Tutorial abschließen, müssen Sie einen Abschlussnachweis wie [ angegeben ](./completion.md).

## Inhalt

Um den Status der folgenden Inhalte zu überprüfen, gehen Sie bitte zur [Statusseite](./status.md).

[0. Erste Schritte](./modules/gettingstarted/gettingstarted/getting-started.md)

In diesem grundlegenden Modul werden Sie alles so einrichten, dass Sie auf die Demo-Umgebung zugreifen und sie verwenden können.

**Zeitaufwand:** 30 Minuten

### 1. Datenerfassung

[1.1 Foundation - Einrichtung von Adobe Experience Platform Data Collection und Web SDK](./modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md)

In diesem grundlegenden Modul erfahren Sie mehr über die Datenerfassung in Adobe Experience Platform und die neue Web-SDK-Erweiterung.

**Zeitaufwand:** 30 Minuten

[1.2 Foundation - Datenaufnahme](./modules/datacollection/module1.2/data-ingestion.md)

In diesem grundlegenden Modul nehmen Sie Daten aus verschiedenen Quellen in Adobe Experience Platform auf

**Zeitaufwand:** 120 Minuten

[1.3 Federated Audience-Komposition](./modules/datacollection/module1.3/fac.md)

In diesem Modul erfahren Sie, wie Sie ein Federated-Audiences-Modell einrichten und Zielgruppen mithilfe von Federated-Daten generieren.

**Zeitaufwand:** 90 Minuten

### 2. Real-Time CDP B2C

[2.1 Foundation - Echtzeit-Kundenprofil](./modules/rtcdp-b2c/module2.1/real-time-customer-profile.md)

In diesem grundlegenden Modul lernen Sie das Echtzeit-Kundenprofil in Adobe Experience Platform kennen, indem Sie die Benutzeroberfläche und API verwenden.

**Zeitaufwand:** 90 Minuten

[2.2 Intelligent Services](./modules/rtcdp-b2c/module2.2/intelligent-services.md)

In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Intelligent Services einrichten, konfigurieren und verwenden.

**Zeitaufwand:** 60 Minuten

[2.3 Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen](./modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md)

In diesem Modul konfigurieren Sie eine Zielgruppe und aktivieren die Zielgruppe für mehrere Ziele, einschließlich Google DV360, Adobe Target und AWS S3.

**Zeitaufwand:** 90 Minuten

[2.4 Real-Time CDP: Audience Activation zum Microsoft Azure Event Hub](./modules/rtcdp-b2c/module2.4/segment-activation-microsoft-azure-eventhub.md)

In diesem Modul richten Sie ein Microsoft Azure EventHub-Ziel als Echtzeit-Ziel für Adobe Experience Platform Real-Time CDP ein. Sie werden auch eine Azure-Funktion einrichten und bereitstellen, die in Echtzeit ausgelöst wird, wenn Adobe Experience Platform eine Zielgruppen-Payload an Ihr Azure EventHub-Ziel sendet. Die Azure-Funktion, die Sie in den Trigger nehmen, zeigt den Mechanismus der Aktivierungsfunktionen von Adobe Experience Platform Real-time CDP.
In diesem Modul erfahren Sie auch, welche Trigger Real-Time CDP-Programme tatsächlich eine Payload an ein bestimmtes Ziel senden. Wir besprechen auch den Status einer Zielgruppen-Qualifizierung und wie er mit der Aktivierung zusammenhängt.

**Zeitaufwand:** 90 Minuten

[2.5 Real-Time CDP-Verbindungen: Ereignisweiterleitung](./modules/rtcdp-b2c/module2.5/aep-data-collection-ssf.md)

In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemata und die Datenerfassungseigenschaft von Adobe Experience Platform, um Daten zu erfassen, und leiten diese Daten dann Server-seitig an mehrere Endpunkte weiter, z. B. Google Cloud Platform Pub/Sub und AWS Kinesis.

**Zeitaufwand:** 90 Minuten

[2.6 Streamen Sie Daten von Apache Kafka nach Real-Time CDP](./modules/rtcdp-b2c/module2.6/aep-apache-kafka.md)

In diesem Modul erfahren Sie, wie Sie Ihren eigenen Apache Kafka-Cluster einrichten, Themen, Produzenten und Verbraucher definieren und Daten mit dem Adobe Experience Platform Sink Connector für Kafka Connect in Adobe Experience Platform streamen.

**Zeitaufwand:** 90 Minuten

### 3. Adobe Journey Optimizer B2C

[3.1 Adobe Journey Optimizer: Orchestrierung](./modules/ajo-b2c/module3.1/journey-orchestration-create-account.md)

In diesem Modul werden Sie Adobe Journey Optimizer verwenden, um eine Trigger-basierte Journey zu erstellen.

**Zeitaufwand:** 60 Minuten

[3.2 Adobe Journey Optimizer: Externe Datenquellen und benutzerdefinierte Aktionen](./modules/ajo-b2c/module3.2/journey-orchestration-external-weather-api-sms.md)

In diesem Modul verwenden Sie Adobe Journey Optimizer, um das Kundenverhalten sowohl online als auch offline zu überwachen und auf verschiedene Kanäle intelligent, kontextbezogen und in Echtzeit zu reagieren.

**Zeitaufwand:** 90 Minuten

[3.3 Adobe Journey Optimizer: Offer decisioning](./modules/ajo-b2c/module3.3/offer-decisioning.md)

In diesem Modul verwenden Sie den Anwendungs-Service Adobe Experience Platform - Angebote/Decisioning, um personalisierte Angebote und Ihre eigene Angebotsaktivität zu konfigurieren.

**Zeitaufwand:** 120 Minuten

[3.4 Adobe Journey Optimizer: Veranstaltungsbasierte Journey](./modules/ajo-b2c/module3.4/journeyoptimizer.md)

In diesem Modul erfahren Sie alles, was es über Journey Optimizer zu wissen gibt. Damit können Unternehmen vernetzte, kontextuelle und personalisierte Erlebnisse für ihre Kunden entwerfen und bereitstellen.

**Zeitaufwand:** 120 Minuten

### 4. Adobe Customer Journey Analytics

[4.1 Customer Journey Analytics: Erstellen eines Dashboards mit Analysis Workspace zusätzlich zu Adobe Experience Platform](./modules/cja-b2c/module4.1/customer-journey-analytics-build-a-dashboard.md)

In diesem Modul erhalten Sie Online- bis Offline-Einblicke, indem Sie ein Dashboard konfigurieren, das Omni-Channel-Daten wie Website-Interaktionen, Mobile-App-Interaktionen, Callcenter-Interaktionen, In-Store-Interaktionen und vieles mehr enthält.

**Zeitaufwand:** 120 Minuten

[4.2 Customer Journey Analytics: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector](./modules/cja-b2c/module4.2/customer-journey-analytics-bigquery-gcp.md)

In diesem Modul richten Sie Ihre eigene Instanz von Google Cloud Platform ein, laden Demodaten in Google Cloud Platform und verwenden dann den BigQuery Source Connector , um diese Daten von Google Cloud Platform in Adobe Experience Platform aufzunehmen. Zum Schluss verwenden Sie Customer Journey Analytics zur Visualisierung dieser Daten.

**Zeitaufwand:** 120 Minuten

### 5. Daten-Distiller

[5.1 Abfrage-Service](./modules/datadistiller/module5.1/query-service.md)

In diesem Modul erfahren Sie, wie Sie den Abfrage-Service von Adobe Experience Platform verwenden.

**Zeitaufwand:** 90 Minuten

![Tech Insiders](./assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.
