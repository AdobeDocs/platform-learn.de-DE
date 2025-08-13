---
title: Ermöglichen Sie kanalübergreifende Einblicke mit Federated Audience Composition
description: Die Federated Audience-Komposition ist eine leistungsstarke Funktion, mit der Datenarchitekten und Dateningenieure Zielgruppen direkt aus Data Warehouses von Drittanbietern erstellen und anreichern können.
breadcrumb-title: Übersicht
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11T00:00:00Z
exl-id: 9d5a2e40-6cda-4164-87db-1bfffe3438e3
source-git-commit: a3c8d8b03472d01f491bf787ed647a696d3a5524
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Übersicht

Die Federated Audience-Komposition ist eine leistungsstarke Funktion, die für Adobe Real-Time Customer Data Platform (Real-Time CDP)- und Adobe Journey Optimizer-Umgebungen verfügbar ist. Datenarchitekten und Dateningenieure können damit Zielgruppen direkt aus Data Warehouses [unterstützten ](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"} von Drittanbietern erstellen und anreichern, ohne Daten nach Adobe Experience Platform zu replizieren. Dieses Tutorial bietet praktische Anleitungen für technische Benutzende, um Data Warehouses für Unternehmen miteinander zu verbinden, Zielgruppen zu erstellen und anzureichern und sie für personalisierte Marketing-Erlebnisse zu aktivieren.

## Visuelles Handbuch

In diesem visuellen Handbuch werden die Schritte für die einzelnen Aktivitäten erläutert, die zur Unterstützung verschiedener Aspekte des Geschäftsszenarios durchgeführt werden. Ziel ist es, Ihnen Aktivitäten bereitzustellen, die Sie in Ihrer Umgebung nutzen können, darunter:

- Adobe Experience Platform mit einem Unternehmens-Data Warehouse verbinden.
- Erstellen und verwalten Sie Zielgruppen mithilfe der Federated Audience-Komposition.
- Zuordnen von föderierten Zielgruppen zu externen Zielen, z. B. Amazon S3.
- Anreicherung vorhandener Audiences mit Federated-Daten.
- Erstellen Sie Zielgruppen, um eine „In-the-Moment“-Personalisierung zu fördern.
- Erstellen Sie Kunden-Journey mit Federated-Audience-Daten.

Dieses Handbuch richtet sich an Datenarchitekten und Dateningenieure, die mit Real-Time CDP oder Journey Optimizer arbeiten. Es wird davon ausgegangen, dass Sie mit Adobe Experience Platform und den grundlegenden Data Warehouse-Konzepten vertraut sind.

## Geschäftskontext

SecurFinancial ist ein führendes Finanzdienstleistungsunternehmen. Es nutzt die Fülle an Kundendaten aus unterschiedlichen Quellen, um Angebote und Kampagnen für eine große Anzahl von Segmenten zu personalisieren. Sie planen, die Adobe-Funktion &quot;Real-Time CDP Federated Audience Composition“ zu verwenden, mit der Unternehmen ihr bestehendes Data Warehouse nutzen können, während sie Adobe Experience Platform-Programme zur Bereitstellung personalisierter Kundenerlebnisse verwenden. Zu den wichtigsten Vorteilen gehören:

- **Zugriff auf Warehouse-Daten**: Erstellen Sie hochwertige Zielgruppen aus Datensätzen in unterstützten Data Warehouses ohne Datenreplikation.
- **Minimierte Datenverlagerung**: Abfragen von Daten direkt im Warehouse, Reduzierung von Duplikaten und Aufrechterhaltung von Data Governance.
- **Workflows für einheitliche Erlebnisse**: Kuratieren und aktivieren Sie Zielgruppen in Adobe Experience Platform für kanalübergreifende Anwendungsfälle.
- **Verbesserte Personalisierung**: Profile und Audiences mit Warehouse-Attributen anreichern, um ausgelöste Erlebnisse in Echtzeit zu ermöglichen.

## Geschäftsszenario

SecurFinancial möchte eine E-Mail-Kampagne starten, um Kunden erneut anzusprechen, die sich für einen Kredit auf der Grundlage eines guten Kredits vorqualifiziert haben und keinen aktiven Kredit in ihrem SecurFinancial-Portfolio haben. Während sie Online-Verhaltensdaten in Echtzeit aufnehmen, stehen sie vor Herausforderungen bei der Identifizierung der Präqualifikation, da sie keine Kreditinformationen in AEP aufnehmen können. Um vorqualifizierte Kundinnen und Kunden zu qualifizieren, ohne eingeschränkte Daten zu verschieben, werden sie die Federated Audience-Komposition verwenden, um ihre Verhaltenszielgruppe von AEP anzureichern.

## Voraussetzungen

Um ähnliche Aktivitäten in Ihrer Umgebung durchzuführen, müssen Sie Folgendes sicherstellen:

- Zugriff auf ein Adobe Experience Platform-Konto, das mit Real-Time CDP oder Journey Optimizer bereitgestellt wurde.
- Systemadministratorberechtigungen oder die Möglichkeit, Berechtigungen konfigurieren zu lassen.
- Vertrautheit mit Adobe Experience Platform-Konzepten wie Schemata, Datensätzen und Zielgruppen (empfohlen: Absolvieren Sie die Seite [Einführung in die Adobe Experience Platform-](https://experienceleague.adobe.com/en/playlists/experience-platform-introduction?lang=en){target="_blank"}) in Experience League.
- Zugriff auf ein unterstütztes Unternehmens-Data Warehouse (z. B. Amazon Redshift, Azure Synapse Analytics, Snowflake oder Google BigQuery).
- Grundlegende Kenntnisse von SQL für die Abfrage von Data Warehouses.
- **Sandbox-Umgebungen**: Erstellen Sie eine Sandbox in der Real-Time CDP-Instanz Ihres Unternehmens, um sicher zu experimentieren, ohne die Produktionsdaten zu beeinflussen.
- **Data Warehouse-Verbindung**: Dieses Tutorial verwendet eine Snowflake-Verbindung, Sie können jedoch jedes [unterstützte Cloud-Warehouse](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites) verwenden.

Beginnen wir mit der [Data Warehouse-Verbindung](data-warehouse-connection.md).
