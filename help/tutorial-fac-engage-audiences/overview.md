---
title: Interagieren mit Audiences aus Ihrer Data Warehouse mithilfe der Federated Audience Composition
description: Die Federated Audience-Komposition ist eine leistungsstarke Funktion, mit der Datenarchitekten und Dateningenieure Zielgruppen direkt aus Data Warehouses von Drittanbietern erstellen und anreichern können.
breadcrumb-title: Überblick
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11T00:00:00Z
exl-id: 9d5a2e40-6cda-4164-87db-1bfffe3438e3
source-git-commit: dd5f594a54a9cab8ef78d36d2cf15a9b5f2b682a
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Interagieren mit Audiences aus Ihrer Data Warehouse mithilfe der Federated Audience Composition

Federated Audience Composition (FAC) ist eine leistungsstarke Funktion, die für Adobe Real-Time Customer Data Platform (Real-Time CDP)- und Adobe Journey Optimizer-Umgebungen verfügbar ist. Datenarchitekten und Dateningenieure können hochwertige Zielgruppen direkt in [unterstützten Unternehmens-Data-Warehouses“ kuratieren und aktivieren](https://experienceleague.adobe.com/de/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"} ohne Kundendaten in Adobe Experience Platform (AEP) kopieren oder verschieben zu müssen. Dieser zusammensetzbare CDP-Ansatz (eine maßgeschneiderte Lösung für Kunden) stimmt mit Branchentrends überein und ermöglicht es Unternehmen, ihre Dateninfrastruktur für personalisierte digitale Erlebnisse zu nutzen und gleichzeitig die Data Governance beizubehalten.

## Geschäftskontext

SecurFinancial ist ein führendes Finanzdienstleistungsunternehmen. Es nutzt die Fülle an Kundendaten aus unterschiedlichen Quellen, um Angebote und Kampagnen für eine große Anzahl von Segmenten zu personalisieren. Sie planen, die Funktion Adobe Real-Time CDP Federated Audience Composition zu verwenden, um Zielgruppen aus ihrem Data Warehouse zu kuratieren und gleichzeitig für die Ziele von Adobe Experience Platform zu aktivieren, sowie Adobe Journey Optimizer, um eine maßgeschneiderte Lösung zur Bereitstellung personalisierter Kundenerlebnisse bereitzustellen.

## Geschäftsszenario

SecurFinancial möchte eine E-Mail-Kampagne starten, um Kunden erneut anzusprechen, die sich für einen Kredit auf der Grundlage eines guten Kredits vorqualifiziert haben und keinen aktiven Kredit in ihrem SecurFinancial-Portfolio haben. Während sie Online-Verhaltensdaten in Echtzeit erfassen, stehen sie vor Herausforderungen bei der Identifizierung einer Vorqualifizierung, da sie keine Kreditinformationen in AEP aufnehmen können. Um vorqualifizierte Kundinnen und Kunden zu qualifizieren, ohne eingeschränkte Daten zu verschieben, werden sie die Federated Audience-Komposition verwenden, um ihre Verhaltenszielgruppe von AEP anzureichern.

## Handbuch

Dieses Handbuch zeigt, wie wir das SecureFinancial Business-Szenario unterstützen. Es geht insbesondere darum, wie Zielgruppen für Systeme verfügbar gemacht werden, die diese Zielgruppen benötigen, einschließlich eines S3-Speicherkontos, einer Journey in Journey Optimizer zum Steuern einer E-Mail-Kampagne und des Retargeting vor Ort für Kunden, die vorab für einen Kredit genehmigt wurden.

Die Schritte umfassen Folgendes:

1. Adobe Experience Platform mit einem Unternehmens-Data Warehouse verbinden.
2. Erstellen Sie eine Zielgruppe mithilfe der Federated Audience-Komposition.
3. Zuordnen einer zusammengeführten Zielgruppe zum externen Amazon S3-Ziel.
4. Erstellen Sie eine Kunden-Journey mit Federated-Audience-Daten.
5. Eine Zielgruppe mit Federated-Daten anreichern.
6. Fördern Sie eine sofort einsetzbare Personalisierung in der Edge.

## Voraussetzungen

Um ähnliche Aktivitäten in Ihrer Umgebung durchzuführen, müssen Sie Folgendes sicherstellen:

- Zugriff auf ein Adobe Experience Platform-Konto, das mit Real-Time CDP oder Journey Optimizer bereitgestellt wurde.
- Systemadministratorberechtigungen oder die Möglichkeit, Berechtigungen konfigurieren zu lassen.
- Vertrautheit mit Adobe Experience Platform-Konzepten wie Schemata, Datensätzen und Zielgruppen (empfohlen: Absolvieren Sie die Seite [Einführung in die Adobe Experience Platform-](https://experienceleague.adobe.com/de/playlists/experience-platform-introduction?lang=en){target="_blank"}) in Experience League.
- Zugriff auf ein unterstütztes [Enterprise Data Warehouse](https://experienceleague.adobe.com/de/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"}.
- Grundlegende Kenntnisse von SQL für die Abfrage von Data Warehouses.
- **Sandbox-Umgebungen**: Erstellen Sie eine Sandbox in der Instanz Ihrer Organisation, um sicher zu experimentieren, ohne die Produktionsdaten zu beeinflussen.
- **Data Warehouse-Verbindung**: In diesem Tutorial wird eine Snowflake-Verbindung verwendet, Sie können jedoch jedes [unterstützte Data Warehouse“ ](https://experienceleague.adobe.com/de/docs/federated-audience-composition/using/start/access-prerequisites).

Sehen wir uns zunächst die [Hochrangige Architektur und Fluss für Federated Audience-Komposition“ ](fac-architecture-and-flow.md).
