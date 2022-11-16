---
title: Übersicht
description: Ausgangspunkt für Dateningenieure, Datenanalysten, Datenarchitekten, Datenwissenschaftler, Orchestrierungstechniker und Marketingexperten, um ein umfassendes Verständnis des Geschäftswerts von Adobe Experience Platform und all seinen Anwendungsdiensten zu gewinnen.
doc-type: multipage-overview
hide: false
exl-id: 88c19383-c185-40f0-b118-6cb82db0ce0e
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1869'
ht-degree: 1%

---

# Umfassendes technisches Tutorial für Adobe Experience Platform

## Übersicht

Dieses Tutorial ist der perfekte Ausgangspunkt für Dateningenieure, Datenanalysten, Datenarchitekten, Datenwissenschaftler, Orchestrierungs-Ingenieure und Marketingexperten, um ein umfassendes Verständnis des Geschäftswerts von Adobe Experience Platform und all seinen Anwendungsdiensten zu gewinnen. Jede Lektion konzentriert sich auf eine echte Herausforderung, der sich Unternehmen im heutigen komplexen Personalisierungs-Ökosystem gegenübersehen, und unterteilt, wie Experience Platform diese Herausforderung in verschiedenen praktischen Übungen löst. Sehen Sie sich dieses Video an, um zu erfahren, welche Probleme Adobe Experience Platform bei der Lösung von Problemen hat.

>[!VIDEO](https://video.tv.adobe.com/v/344237?quality=12&enable=on)

Dieses Tutorial ist sehr vielfältig und bietet klare Einblicke in die folgenden Anwendungen:

- Adobe Experience Platform
- Adobe Experience Platform – Datenerfassung
- Real-time CDP
- Adobe Journey Optimizer
- Customer Journey Analytics
- Offer Decisioning

Dieses Tutorial konzentriert sich nicht nur auf Adobe-Anwendungen, sondern berücksichtigt auch das breitere Ökosystem, in dem Marken tätig sind. Um dies zu erreichen, liegt der Schwerpunkt in einigen Lektionen auf der Frage, wie _Nicht-Adobe_ -Anwendungen werden in Adobe Experience Platform integriert. Daher erhalten Sie ein tiefes Verständnis dafür, wie die folgenden Anwendungen mit Adobe Experience Platform zusammenarbeiten:

- Amazon: AWS Lambda, AWS S3, AWS Kinesis
- Google: Google Cloud Platform, Google BigQuery, Google Display&amp;Video 360, Google AdWords
- Microsoft: Power BI, Azure EventHub, Azure Blob Storage
- Salesforce: Tableau
- Apache Kafka
- Postman
- ...

Nach Abschluss dieses Tutorials können Sie:

- Schemas, Mixins, Datensätze und Identitäten konfigurieren
- Konfigurieren einer Adobe Experience Platform-Datenerfassungseigenschaft und Einrichten der neuen Web SDK-Erweiterung in der Adobe Experience Platform-Datenerfassung
- Daten in Adobe Experience Platform mithilfe von Adobe Experience Platform Data Collection, Google Tag Manager oder Amazon Alexa in Echtzeit streamen
- Batch-Aufnahme von Daten in Adobe Experience Platform mithilfe eines Workflows oder mithilfe einer Extract, Transform, Load (ETL)-Anwendung
- Echtzeit-Kundenprofil in Adobe Experience Platform visualisieren und verwenden
- Erstellen von Segmenten
- Verschiedene Adobe Experience Platform-APIs verwenden
- SQL zum Abfragen Ihrer Daten in Adobe Experience Platform verwenden
- Modelle für maschinelles Lernen konfigurieren, trainieren und bewerten in Adobe Experience Platform
- Verwenden Sie Journey Orchestration, um Trigger-basierte Journey in Echtzeit zu konfigurieren.
- Verwenden Sie die Echtzeit-Kundendatenplattform, um Maßnahmen zu ergreifen, indem Sie ein Segment für verschiedene Ziele aktivieren
- Verwenden Sie Customer Journey Analytics, um Berichte zu Omnichannel-Kundendaten aus verschiedenen Quellen zu erstellen, einschließlich Google BigQuery

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf die Adobe Experience Platform-Datenerfassung: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Zugriff auf Demo System: [https://dashboard.adobedemo.com/](https://dashboard.adobedemo.com/)

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Informationen zu diesem Tutorial

In diesen Lektionen implementieren Sie Adobe Experience Platform und Application Services mithilfe einer Demo-Website, die mehrere Branchen unterstützt. Die Demo-Website und die mobile App verfügen über eine umfangreiche Datenschicht und Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Es bietet Zugriff auf Demomarken wie **Luma**, **Citi Signal**, **EXP-Nachrichten**, **GEGENSTAND365**, **Carvelo** und mehrere andere. Sie erstellen Ihre eigene Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft in Ihrer eigenen Experience Cloud-Organisation und ordnen sie Ihrer Demowebsite zu. Dadurch werden Daten generiert, die an Ihre eigene Adobe Experience Platform-Instanz gesendet werden.

## Architektur

Bevor Sie mit den praktischen Übungen beginnen, sollten Sie sich die Architektur hinter diesem Tutorial ansehen. Wie Sie in der obigen Übersicht sehen, wird dieses Tutorial eine Reihe von Funktionen und Funktionen von Adobe Experience Platform genauer erläutern, aber auch mehrere Integrationen über verschiedene Quellen und Ziele hinweg diskutieren. Damit Sie die Architektur dieses Tutorials und die Gesamtpositionierung von Adobe Experience Platform in Ihrem Enterprise-Ökosystem richtig verstehen können, sollten Sie zunächst das Video und das Diagramm zur Architektur lesen.

Navigieren Sie zu [Architektur](./architecture.md).


## Videos

![Videos](./assets/images/yt.jpeg)

Sie finden viele interessante Videos von unseren Tech Academy Events, von Bootcamps und mehr über unsere [Community-YouTube-Kanal für Experience Maker](https://www.youtube.com/channel/UCUKG2dkZ9pYuZUPebQ21jUw).

Es wurden mehrere Videos erstellt, in denen Elemente der Aktivierung und leistungsstarke Integrationen zwischen Adobe Experience Platform- und Nicht-Adobe-Anwendungen vorgestellt werden. Klicken Sie auf den unten stehenden Link, um eine Übersicht über diese Videos zu erhalten.

Navigieren Sie zu [Videos](./videos.md).



## Wie wird Ihr Abschluss des umfassenden Tutorials für Adobe Experience Platform gemessen?

Wenn Sie an diesem Tutorial als Adobe Partner oder Mitarbeiter der Adobe teilnehmen, müssen Sie Ihren Fortschritt nach Abschluss jedes Aktivierungsmoduls übermitteln.

Hier finden Sie die Anforderungen und den Prozess für die Übermittlung des Versands: [Messen des Abschlusses](./completion.md)

## Inhalt

[0. Erste Schritte](./modules/module0/getting-started.md)

- **Zielgruppe:** Alle Teilnehmer des umfassenden Tutorials für Adobe Experience Platform
- **Voraussetzungen:** Zugriff auf Demo System Next, Adobe Experience Platform und Adobe Experience Platform Data Collection. Zugriff auf die standardmäßige Konfigurations-ID Ihrer Adobe Experience Platform-Umgebung.
- **Beschreibung:** In diesem grundlegenden Modul richten Sie alles ein, damit Sie auf die Demoumgebung zugreifen und sie verwenden können.
- **Zeitinvestition:** 30 Minuten

[1. Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und des Web-SDK](./modules/module1/data-ingestion-launch-web-sdk.md)

- **Zielgruppe:** Dateningenieur, Datenarchitektin
- **Voraussetzungen:** Zugriff auf die Datenerfassung von Adobe Experience Platform und Adobe Experience Platform.
- **Beschreibung:** In diesem grundlegenden Modul erfahren Sie mehr über die Adobe Experience Platform-Datenerfassung und die neue Web SDK-Erweiterung.
- **Zeitinvestition:** 30 Minuten

[2. Foundation - Datenerfassung](./modules/module2/data-ingestion.md)

- **Zielgruppe:** Dateningenieur, Datenarchitektin
- **Voraussetzungen:** Zugriff auf die Datenerfassung von Adobe Experience Platform und Adobe Experience Platform.
- **Beschreibung:** In diesem grundlegenden Modul erfassen Sie Daten von der Website in Platform
- **Zeitinvestition:** 120 Minuten

[3. Foundation - Echtzeit-Kundenprofil](./modules/module3/real-time-customer-profile.md)

- **Zielgruppe:** Data Engineer, Data Architect, Marketer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Postman
- **Beschreibung:** In diesem grundlegenden Modul untersuchen Sie das Echtzeit-Kundenprofil in Adobe Experience Platform, indem Sie die Benutzeroberfläche und die API verwenden.
- **Zeitinvestition:** 90 Minuten
- **Herunterladen dieser Assets**:
   - [Postman-Sammlungen](./assets/postman/postman_profile.zip)

[4. Query Service](./modules/module4/query-service.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst, BI-Experte
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Query Service, Power BI oder Tableau
- **Beschreibung:** In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Query Service verwenden.
- **Zeitinvestition:** 90 Minuten
- **Herunterladen dieser Assets**:
   - [JSON - Beispieldaten: Demosystem - Ereignis-Datensatz für Website](./assets/json/ee.json)
   - [JSON - Beispieldaten: Demosystem - Ereignis-Datensatz für Callcenter](./assets/json/callcenter.json)
   - [JSON - Beispieldaten: Demosystem - Profildatensatz für Treueprogramm](./assets/json/loyalty.json)

[5. Intelligent Services](./modules/module5/intelligent-services.md)

- **Zielgruppe:** Dateningenieur, Datenarchitekt, Datenwissenschaftler
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Intelligent Services
- **Beschreibung:** In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Intelligent Services einrichten, konfigurieren und verwenden.
- **Zeitinvestition:** 60 Minuten

[6. Real-Time CDP - Erstellen eines Segments und Ergreifen von Maßnahmen](./modules/module6/real-time-cdp-build-a-segment-take-action.md)

- **Zielgruppe:** Datenarchitekt, Orchestrierungs-Engineer, Marketer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Echtzeit-Kundendatenplattform, Adobe Audience Manager, Adobe Target, AWS S3
- **Beschreibung:** In diesem Modul konfigurieren Sie ein Segment, aktivieren es für Streaming-Segmentierung und aktivieren das Segment für verschiedene Ziele, darunter Google DV360-, Google AdWords-, Adobe Audience Manager-, Adobe Target- und S3-Ziele wie Salesforce Marketing Cloud.
- **Zeitinvestition:** 90 Minuten

[7. Adobe Journey Optimizer: Orchestrierung](./modules/module7/journey-orchestration-create-account.md)

- **Zielgruppe:** Data Engineer, Data Architect, Orchestration Engineer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Adobe Journey Optimizer
- **Beschreibung:** In diesem Modul verwenden Sie Adobe Journey Optimizer, um eine Trigger-basierte Journey zu erstellen.
- **Zeitinvestition:** 60 Minuten

[8. Adobe Journey Optimizer: Externe Datenquellen und benutzerdefinierte Aktionen](./modules/module8/journey-orchestration-external-weather-api-sms.md)

- **Zielgruppe:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Adobe Journey Optimizer, Open Weather API, Twilio
- **Beschreibung:** In diesem Modul verwenden Sie Adobe Journey Optimizer, um das Kundenverhalten sowohl online als auch offline zu überwachen und intelligent, kontextbezogen und in Echtzeit über verschiedene Kanäle zu reagieren.
- **Zeitinvestition:** 90 Minuten

[9. Adobe Journey Optimizer: offer decisioning](./modules/module9/offer-decisioning.md)

- **Zielgruppe:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Offer decisioning
- **Beschreibung:** In diesem Modul verwenden Sie den Anwendungsdienst Adobe Experience Platform - Angebote/Decisioning in einer praktischen Methode, um personalisierte Angebote und Ihre eigene Angebotsaktivität zu konfigurieren.
- **Zeitinvestition:** 120 Minuten

[10. Adobe Journey Optimizer: Ereignisbasierte Journey](./modules/module10/journeyoptimizer.md)

- **Zielgruppe:** E-Mail-Marketer, Orchestrierungsspezialist, Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Journey Optimizer
- **Beschreibung:** In diesem Modul erfahren Sie alles, was Sie über Journey Optimizer wissen müssen, um Unternehmen bei der Erstellung und Bereitstellung von vernetzten, kontextbezogenen und personalisierten Erlebnissen für ihre Kunden zu unterstützen.
- **Zeitinvestition:** 120 Minuten

[11. Customer Journey Analytics: Erstellen eines Dashboards mit Analysis Workspace über Adobe Experience Platform](./modules/module11/customer-journey-analytics-build-a-dashboard.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform und Customer Journey Analytics
- **Beschreibung:** In diesem Modul erhalten Sie Online- und Offline-Einblicke, indem Sie ein Dashboard konfigurieren, das kanalübergreifende Daten wie Website-Interaktionen, Mobile-App-Interaktionen, Callcenter-Interaktionen, In-Store-Interaktionen und vieles mehr enthält.
- **Zeitinvestition:** 120 Minuten

[12. Customer Journey Analytics: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector](./modules/module12/customer-journey-analytics-bigquery-gcp.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, Customer Journey Analytics, Google Cloud Platform, Google BigQuery
- **Beschreibung:** In diesem Modul richten Sie Ihre eigene Instanz von Google Cloud Platform ein, laden Demodaten in Google Cloud Platform und verwenden dann den BigQuery Source Connector, um diese Daten von Google Cloud Platform in Adobe Experience Platform aufzunehmen. Schließlich verwenden Sie Customer Journey Analytics, um diese Daten zu visualisieren.
- **Zeitinvestition:** 120 Minuten
- **Herunterladen dieser Assets**:
   - [JSON - Beispieldaten: Demo - Treuedaten](./assets/json/bqLoyalty.json)

[13. Real-Time CDP: Segmentaktivierung für Microsoft Azure Event Hub](./modules/module13/segment-activation-microsoft-azure-eventhub.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform, die Echtzeit-Kundendatenplattform und Microsoft Azure
- **Beschreibung:** In diesem Modul richten Sie ein Microsoft Azure EventHub-Ziel als Echtzeit-Ziel für die Echtzeit-Kundendatenplattform von Adobe Experience Platform ein. Sie richten außerdem eine Azure-Funktion ein und stellen sie bereit, die in Echtzeit ausgelöst wird, sobald Adobe Experience Platform eine Segment-Payload für Ihr Azure EventHub-Ziel bereitstellt. Die Azure-Funktion, die Sie in Trigger nehmen, zeigt den Mechanismus der Aktivierungsfunktionen der Adobe Experience Platform-Echtzeit-Kundendatenplattform an.
Im Rahmen dieses Moduls erhalten Sie außerdem Informationen dazu, welche Echtzeit-Kundendatenplattform von Trigger tatsächlich eine Payload an ein bestimmtes Ziel bereitstellt. Wir besprechen auch den Status einer Segmentqualifikation und deren Zusammenhang mit der Aktivierung.
- **Zeitinvestition:** 90 Minuten

[14. Real-Time CDP-Verbindungen: Ereignisweiterleitung](./modules/module14/aep-data-collection-ssf.md)

- **Zielgruppe:** Data Engineer, Data Architect, Data Analyst
- **Voraussetzungen:** Zugriff auf Real-Time CDP-Verbindungen, -Tags und Eigenschaften für die Ereignisweiterleitung
- **Beschreibung:** In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemas und die Datenerfassungseigenschaft von Adobe Experience Platform, um Daten zu erfassen und diese Daten dann Server-seitig an einen gewünschten Endpunkt weiterzuleiten.
- **Zeitinvestition:** 90 Minuten

[15. Streamen von Daten von Apache Kafka nach Real-Time CDP](./modules/module15/aep-apache-kafka.md)

- **Zielgruppe:** Data Analyst, Data Engineer, Datenarchitekt
- **Voraussetzungen:** Zugriff auf Adobe Experience Platform
- **Beschreibung:** In diesem Modul erfahren Sie, wie Sie einen eigenen Apache Kafka-Cluster einrichten, Themen, Hersteller und Verbraucher definieren und Daten mit dem Adobe Experience Platform Sink Connector für Kafka Connect an Adobe Experience Platform streamen.
- **Zeitinvestition:** 90 Minuten

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.
