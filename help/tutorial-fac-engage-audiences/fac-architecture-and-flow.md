---
title: Zusammenstellung einer Federated Audience auf hoher Ebene - Architektur und Fluss
seo-title: Federated Audience Composition high-level architecture & flow | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Zusammenstellung einer Federated Audience auf hoher Ebene - Architektur und Fluss
description: Überblick über die allgemeine Architektur und den Fluss der Federated Audience-Komposition.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-high-level-architecture.jpg
exl-id: 4cb0b730-4206-476b-93d9-776dfbd464ff
source-git-commit: 0564f516cfba7ea09ac9da19d94f46d984e9e00a
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# Zusammenstellung einer Federated Audience auf hoher Ebene - Architektur und Fluss

Bevor wir in die Schritte zur Unterstützung des Geschäftsszenarios für SecurFinancial eintauchen, werden wir die allgemeine Architektur und den Ablauf für diesen zusammensetzbaren CDP-Ansatz überprüfen.

Das Federated Audience Composition-Modul in Adobe Experience Platform erweitert den Zugriff auf Data Warehouse-Datensätze, ohne die zugrunde liegenden Daten zu kopieren, wodurch Datenverschiebungen und Duplikate minimiert werden.

Dadurch erhalten Unternehmen auch die erforderliche zusammensetzbare Architektur, die bereits die erforderlichen Datenverwaltungsarbeiten in ihrem Warehouse abgeschlossen haben und ein Null-Copy-Muster verwenden möchten, bei dem Adobe Experience Platform zur Interaktionsmaschine wird.

Damit können Unternehmen Informationen, die in einem oder mehreren Data Warehouses gespeichert sind, schnell verarbeiten. Dadurch entfällt die Notwendigkeit, Daten in Adobe Experience Platform aufzunehmen. Darüber hinaus bietet sie Zugriff auf neue Datensätze, die sich in Data Warehouses von Unternehmen befinden, aber bis jetzt für Workflows zur Kundenerfahrung nicht zugänglich waren. Beispiele sind historische Transaktionen oder personenbezogene Daten, die auf aggregierter Zielgruppenebene für die Kundeninteraktion nützlich sind.

![fac-architecture](assets/fac-architecture.png)

Jetzt gehen wir zur Erstellung einer [Data Warehouse-Verbindung über](data-warehouse-connection.md).
