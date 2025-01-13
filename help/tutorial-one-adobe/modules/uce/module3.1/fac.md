---
title: Datenerfassung - Federated Audience-Komposition
description: Datenerfassung - Federated Audience-Komposition
kt: 5342
doc-type: tutorial
source-git-commit: dc86e52b659d7b428aca03fdb041e7410901e1fd
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 3.1 Federated Audience-Komposition

In diesem Modul erfahren Sie alles über das Erstellen von Zielgruppen mithilfe der Federated Audience-Komposition.

Die Federated Audience Composition (FAC) in Experience Platform ermöglicht den Zugriff auf und die Erstellung von Zielgruppen mit entsprechenden hochwertigen Attributen aus Data Warehouses von Unternehmen. Dadurch werden das Echtzeit-Kundenprofil und die Zielgruppen in Experience Platform angereichert und ergänzt, was eine verbesserte Segmentierung, Zielgruppenbestimmung, Aktivierung und Bereitstellung wirkungsvoller Kundenerlebnisse ermöglicht. Mithilfe der Federated Audience Composition wird eine virtuelle Datenbank erstellt, indem Remote-Datenbanken über Metadaten verknüpft werden. Dieser Ansatz vereinfacht den Zugriff, reduziert Duplizierungen und verbessert das Anwendererlebnis. Teams haben die Möglichkeit, Datensätze direkt in Experience Platform aufzunehmen oder auf Datensätze zuzugreifen, die sich in Data Warehouses befinden, wenn Zielgruppen für Interaktions-Workflows zusammengestellt werden. Dieser Ansatz nutzt Data Warehouse-Investitionen und -Assets als Ergänzung zu Real-Time CDP und Journey Optimizer. Die Federated Audience-Komposition ermöglicht Kunden die Nutzung und Kombination von Batch- und Echtzeit-Funktionen über wichtige neue Anwendungsfallmuster hinweg:

- Federated Audience-Segmentierung: Ein Team kann eine Zielgruppe mithilfe der marketerfreundlichen Benutzeroberfläche für die Drag-and-Drop-Zielgruppenkomposition in Real-Time CDP und Journey Optimizer erstellen, jedoch mit einer an das Data Warehouse gepushten Abfrage, sodass sensible zugrunde liegende Daten im Warehouse ohne Duplizierung verbleiben und ein flexibler Zugriff auf wichtige Datensätze bereitgestellt wird.
- Zielgruppenanreicherung: In Real-Time CDP und Journey Optimizer erstellte Zielgruppen können mit zusätzlichen Unternehmensdaten angereichert werden, um das Targeting und die Personalisierung mit zusätzlichen profilbasierten und nicht profilbasierten Datensätzen zu verbessern, die in Adobe Experience Platform nicht beibehalten werden. Beispielsweise kann eine Einzelhandelsmarke eine Zielgruppe aus aktuellen Online-Käufern mit einer Liste von Top-Standorten aus Stein und Boden ergänzen, um eine Zielgruppe für eine kanalübergreifende Online- und In-Store-Promotion zu erstellen.
- Profilanreicherung: Teams können Profilattribute aus dem Data Warehouse auswählen, die für aktuelle Erlebnisse wichtig sind, damit sie in umsetzbaren Kundenprofilen, die sich in Real-Time CDP befinden und auf die über Journey Optimizer zugegriffen werden kann, beibehalten werden. Diese zusätzlichen Datenpunkte sind dann für die nachgelagerte Segmentierung und Personalisierung verfügbar, die durch das Verhalten von Ereignissen ausgelöst wird, je nach Benutzeraktion und Kundenanwendungsfall. Auf diese Weise können Attribute, die zusammen mit verbundenen Zielgruppen übermittelt werden, für die aktuelle Segmentierung und Personalisierung neben anderen Attributen und Verhaltenssignalen, die in einem Kundenprofil gespeichert sind, verfügbar sein.

Die Federated Audience-Komposition bietet Kunden von Real-Time CDP und Journey Optimizer die Flexibilität, zu entscheiden, welche Daten wann verwendet werden sollen, und hilft dabei, unnötige Duplikate von Datensätzen oder Integrationsmustern zu vermeiden. Dies stellt eine einzigartige Kombination aus einem föderierten Ansatz zur Verwendung von Unternehmensdaten zum Kuratieren von Zielgruppen und hochwertigen Attributen dar, kombiniert mit einem System, das für die aktuelle kanalübergreifende Interaktion optimiert ist. Dies führt zu weniger Datenverschiebungen, aber auch zu neuen Möglichkeiten, hochwertige Zielgruppen und Attribute für eine konsistente Aktivierung mit geringer Latenz über alle Kanäle hinweg zu nutzen.

## Lernziele

- Erfahren Sie, wie Sie Snowflake mit Adobe Experience Platform verbinden
- Erfahren Sie, wie Sie in Adobe Experience Platform ein Datenmodell für Ihre Federated Data erstellen
- Erfahren Sie, wie Sie in Adobe Experience Platform Federated Audience-Kompositionen erstellen

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf ein Snowflake Data Warehouse

## Übungen

[3.1.1 Einrichten der Snowflake-Umgebung](./ex1.md)

In dieser Übung richten Sie Ihr Snowflake-Testkonto ein und verbinden es mit Adobe Experience Platform

[3.1.2 Erstellen von Schemata, Datenmodellen und Links](./ex2.md)

In dieser Übung konfigurieren Sie Ihr Datenmodell in AEP für die Federated Data.

[3.1.3 Erstellen einer Verbundzusammensetzung](./ex3.md)

In dieser Übung konfigurieren Sie Ihr Datenmodell in AEP für die Federated Data.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Überblick über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um alles über Adobe Experience Platform und seine Programme zu erfahren. Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.

[Zurück zu „Alle Module“](../../../overview.md)
