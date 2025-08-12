---
title: Ermöglichen Sie kanalübergreifende Einblicke mit Federated Audience Composition
description: Die Federated Audience-Komposition ist eine leistungsstarke Funktion, mit der Datenarchitekten und Dateningenieure Zielgruppen direkt aus Data Warehouses von Drittanbietern erstellen und anreichern können.
breadcrumb-title: Übersicht
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11T00:00:00Z
source-git-commit: a5ae2695763bc3d6dce786861dcbc15f3422c035
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---


# Übersicht

Die Federated Audience-Komposition ist eine leistungsstarke Funktion, die für Adobe Real-Time Customer Data Platform (Real-Time CDP)- und Adobe Journey Optimizer-Umgebungen verfügbar ist. Datenarchitekten und Dateningenieure können damit Zielgruppen direkt aus Data Warehouses [unterstützten ](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"} von Drittanbietern erstellen und anreichern, ohne Daten nach Adobe Experience Platform zu replizieren. Dieses Tutorial bietet praktische Anleitungen für technische Benutzende, um Data Warehouses für Unternehmen miteinander zu verbinden, Zielgruppen zu erstellen und anzureichern und sie für personalisierte Marketing-Erlebnisse zu aktivieren.

## Lernziele

Durch Abschluss dieses Tutorials werden Sie:

- Erfahren Sie, wie Sie Adobe Experience Platform mit einem Unternehmens-Data Warehouse verbinden.
- Erfahren Sie, wie Sie Zielgruppen mithilfe der Federated Audience-Komposition erstellen und verwalten.
- Erfahren Sie, wie Sie vorhandene Zielgruppen mit Warehouse-Daten anreichern.
- Zuordnen von föderierten Zielgruppen zu externen Zielen, z. B. Amazon S3.
- Erstellen Sie Kunden-Journey mit Federated-Audience-Daten.
- Validieren von Daten und Prozessen durch praktische Übungen und Demos.

Dieses Tutorial richtet sich an Datenarchitekten und Dateningenieure, die mit Real-Time CDP oder Journey Optimizer arbeiten. Es wird davon ausgegangen, dass Sie mit Adobe Experience Platform und den grundlegenden Data Warehouse-Konzepten vertraut sind.

## Geschäftskontext

SecurFinancial ist ein führendes Finanzdienstleistungsunternehmen. Es nutzt die Fülle an Kundendaten aus unterschiedlichen Quellen, um Angebote und Kampagnen für eine große Anzahl von Segmenten zu personalisieren. Sie planen, die Adobe-Funktion &quot;Real-Time CDP Federated Audience Composition“ zu verwenden, mit der Unternehmen ihr bestehendes Data Warehouse nutzen können, während sie Adobe Experience Platform-Programme zur Bereitstellung personalisierter Kundenerlebnisse verwenden. Zu den wichtigsten Vorteilen gehören:

- **Zugriff auf Warehouse-Daten**: Erstellen Sie hochwertige Zielgruppen aus Datensätzen in unterstützten Data Warehouses ohne Datenreplikation.
- **Minimierte Datenverlagerung**: Abfragen von Daten direkt im Warehouse, Reduzierung von Duplikaten und Aufrechterhaltung von Data Governance.
- **Workflows für einheitliche Erlebnisse**: Kuratieren und aktivieren Sie Zielgruppen in Adobe Experience Platform für kanalübergreifende Anwendungsfälle.
- **Verbesserte Personalisierung**: Profile und Audiences mit Warehouse-Attributen anreichern, um ausgelöste Erlebnisse in Echtzeit zu ermöglichen.

## Geschäftsszenario

SecurFinancial möchte eine E-Mail-Kampagne starten, um Kunden erneut anzusprechen, die sich für einen Kredit auf der Grundlage eines guten Kredits vorqualifiziert haben und keinen aktiven Kredit in ihrem SecurFinancial-Portfolio haben. Während sie Online-Verhaltensdaten in Echtzeit aufnehmen, stehen sie vor Herausforderungen bei der Identifizierung der Präqualifikation, da sie keine Kreditinformationen in AEP aufnehmen können. Um vorqualifizierte Kundinnen und Kunden zu qualifizieren, ohne eingeschränkte Daten zu verschieben, werden sie die Federated Audience-Komposition verwenden, um ihre Verhaltenszielgruppe von AEP anzureichern.



## Voraussetzungen

Um diesem Tutorial zu folgen, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Zugriff auf ein Adobe Experience Platform-Konto, das mit Real-Time CDP oder Journey Optimizer bereitgestellt wurde.
- Systemadministratorberechtigungen oder die Möglichkeit, Berechtigungen konfigurieren zu lassen.
- Vertrautheit mit Adobe Experience Platform-Konzepten wie Schemata, Datensätzen und Zielgruppen (empfohlen: Absolvieren Sie die Seite [Einführung in die Adobe Experience Platform-](https://experienceleague.adobe.com/en/playlists/experience-platform-introduction?lang=en){target="_blank"}) in Experience League.
- Zugriff auf ein unterstütztes Unternehmens-Data Warehouse (z. B. Amazon Redshift, Azure Synapse Analytics, Snowflake oder Google BigQuery).
- Grundlegende Kenntnisse von SQL für die Abfrage von Data Warehouses.

## Verwenden dieses Tutorials

Dieses Tutorial ist für technische Benutzende strukturiert. Die Lektionen bauen aufeinander auf, also vervollständigen Sie sie in der richtigen Reihenfolge, sofern nicht anders angegeben.

## Technische Hinweise

- **Sandbox-Umgebungen**: Erstellen Sie eine Sandbox in der Real-Time CDP-Instanz Ihres Unternehmens, um sicher zu experimentieren, ohne die Produktionsdaten zu beeinflussen.
- **Data Warehouse-Verbindung**: Dieses Tutorial verwendet eine Snowflake-Verbindung, Sie können jedoch jedes [unterstützte Cloud-Warehouse](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites) verwenden.

Beginnen Sie mit der Lektion [Data Warehouse-Verbindung](data-warehouse-connection.md), um mit der Konfiguration Ihrer Umgebung zu beginnen.
