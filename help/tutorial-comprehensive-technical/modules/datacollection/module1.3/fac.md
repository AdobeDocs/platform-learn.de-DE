---
title: Datenerfassung - Zusammengestellte Zielgruppenkomposition
description: Datenerfassung - Zusammengestellte Zielgruppenkomposition
kt: 5342
doc-type: tutorial
exl-id: 44660f3e-0594-4578-9531-1c918992aa9d
source-git-commit: 3a19e88e820c63294eff38bb8f699a9f690afcb9
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# 1.3 Zusammengestellte Zielgruppenkomposition

**Autor: [Ludovic Latapie](https://www.linkedin.com/in/ludoviclatapie/), [Wouter van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul soll alles über die Erstellung von Zielgruppen mithilfe der Zusammenstellung von Federated Audience erfahren.

Federated Audience Komposition (FAC) in Experience Platform ermöglicht Ihnen den Zugriff auf und die Erstellung von Zielgruppen mit entsprechenden hochwertigen Attributen aus Unternehmensdatenlagern, die das Echtzeit-Kundenprofil und die Zielgruppen in Experience Platform anreichern und ergänzen, um eine verbesserte Segmentierung, Zielgruppenbestimmung, Aktivierung und Bereitstellung wirkungsvoller Kundenerlebnisse zu ermöglichen. Mit Federated Audience Komposition wird eine virtuelle Datenbank erstellt, indem Remote-Datenbanken über Metadaten verknüpft werden. Dieser Ansatz vereinfacht den Zugriff, reduziert Duplikate und verbessert das Benutzererlebnis für Endbenutzer. Teams erhalten beim Zusammenstellen von Zielgruppen für Interaktions-Workflows die Flexibilität, Datensätze direkt in Experience Platform aufzunehmen oder auf Datensätze zuzugreifen, die in Data Warehouse gespeichert sind. Dieser Ansatz nutzt Data Warehouse-Investitionen und -Assets, um Real-Time CDP und Journey Optimizer zu ergänzen. Zusammengestellte Zielgruppenzusammensetzung ermöglicht es Kunden, Batch- und Echtzeit-Funktionen über wichtige neue Anwendungsfallmuster hinweg zu nutzen und zu kombinieren:

- Zusammengestellte Zielgruppensegmentierung: Ein Team kann eine Zielgruppe mithilfe der marketerfreundlichen Drag &amp; Drop-Benutzeroberfläche für die Zielgruppenzusammensetzung in Real-Time CDP und Journey Optimizer erstellen, jedoch mit einer Abfrage, die an das Data Warehouse gesendet wird, wobei sensible zugrunde liegende Daten ohne Duplizierung verbleiben und ein flexibler Zugriff auf wichtige Datensätze möglich ist.
- Zielgruppen-Anreicherung: In Real-Time CDP und Journey Optimizer erstellte Zielgruppen können mit zusätzlichen Unternehmensdaten angereichert werden, um Targeting und Personalisierung durch zusätzliche profilbasierte und nicht profilbasierte Datensätze zu verbessern, die in Adobe Experience Platform nicht persistent sind. So kann beispielsweise eine Einzelhandelsmarke eine Audience der letzten Online-Käufer mit einer Liste der wichtigsten Orte ergänzen, um eine Audience für eine kanalübergreifende Online- und In-Store-Promotion zu erstellen.
- Profilanreicherung: Teams können Profilattribute aus Data Warehouse auswählen, die für aktuelle Erlebnisse von entscheidender Bedeutung sind, die in umsetzbaren Kundenprofilen gespeichert und über Journey Optimizer aufgerufen werden können. Diese zusätzlichen Datenpunkte stehen dann für nachgelagerte Segmentierung und Personalisierung zur Verfügung, die durch Ereignisverhalten ausgelöst wird, abhängig von der Benutzeraktion und dem Anwendungsfall des Kunden. Auf diese Weise können neben anderen Attributen und Verhaltenssignalen, die in einem Kundenprofil beibehalten werden, auch Attribute, die mit verknüpften Zielgruppen zusammengeführt werden, für die Segmentierung und Personalisierung im Moment verfügbar sein.

Zusammengestellte Zielgruppenkomposition bietet Real-Time CDP- und Journey Optimizer-Kunden die Flexibilität zu entscheiden, welche Daten sie verwenden möchten, wenn sie möchten, und hilft, unnötige Duplizierungen von Datensätzen oder Integrationsmustern zu vermeiden. Dies stellt eine einzigartige Kombination aus einem verknüpften Ansatz zur Verwendung von Unternehmensdaten zur Kuratierung von Zielgruppen und hochwertigen Attributen dar, kombiniert mit einem System, das für die kanalübergreifende Interaktion im Moment optimiert ist. Dies führt zu weniger Datenbewegungen, aber auch zu neuen Möglichkeiten, hochwertige Zielgruppen und Attribute für eine konsistente Aktivierung mit geringer Latenz über Kanäle hinweg zu nutzen.

## Lernziele

- Erfahren Sie, wie Sie Snowflake mit Adobe Experience Platform verbinden.
- Erfahren Sie, wie Sie ein Datenmodell für Ihre Federated Data in Adobe Experience Platform erstellen.
- Erfahren Sie, wie Sie in Adobe Experience Platform zusammengestellte Zielgruppenkompositionen erstellen.

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf ein Snowflake Data Warehouse

## Übungen

[1.3.1 Snowflake-Konto einrichten](./ex1.md)

In dieser Übung richten Sie Ihr Snowflake-Testkonto ein und verbinden es mit Adobe Experience Platform

[1.3.2 Schemas, Datenmodell und Links erstellen](./ex2.md)

In dieser Übung konfigurieren Sie Ihr Datenmodell in AEP für die verknüpften Daten.

[1.3.3 Föderierte Zusammensetzung erstellen](./ex3.md)

In dieser Übung konfigurieren Sie Ihr Datenmodell in AEP für die verknüpften Daten.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investieren, um alles über Adobe Experience Platform und seine Anwendungen zu erfahren. Wenn Sie Fragen haben, möchten Sie allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com** senden.

[Zu allen Modulen zurückkehren](../../../overview.md)
