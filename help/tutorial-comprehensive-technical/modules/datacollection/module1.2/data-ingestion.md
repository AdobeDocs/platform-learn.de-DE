---
title: Foundation - Datenaufnahme
description: Foundation - Datenaufnahme
kt: 5342
doc-type: tutorial
exl-id: 976d801a-3dcb-4cd9-8b9f-b1c964fe7c25
source-git-commit: bd46be455f88007174f7e6be9a1ce5f508edc09b
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 1%

---

# 1.2 Foundation - Datenaufnahme

In diesem Modul soll alles über die Datenaufnahme erfahren. Sie erfahren mehr über die Datenaufnahme in Streaming und Batch. Sie implementieren die Streaming-Datenaufnahme mithilfe von Launch, damit das Kundenverhalten auf der Hands-On-Lab-Website in Echtzeit an Adobe Experience Platform gestreamt wird. Sie erfahren mehr über die Batch-Datenaufnahme mithilfe eines Adobe Experience Platform-Workflows, der eine CSV-Datei einem XDM-Schema zuordnet und sie dann in Adobe Experience Platform aufnimmt.

## Lernziele

- Erfahren Sie, wie Sie ein XDM-Schema in Adobe Experience Platform erstellen
- Erfahren Sie, wie Sie in Adobe Experience Platform Datensätze erstellen
- Erfahren Sie, wie Sie in Launch einen Streaming-Endpunkt erstellen und die Adobe Experience Platform-Erweiterung konfigurieren
- Erfahren Sie, wie Sie in Launch Regeln erstellen, um Daten an Adobe Experience Platform zu streamen
- Erfahren Sie, wie Sie Adobe Experience Platform Launch in eine Webseite integrieren.
- Erfahren Sie, wie Sie mit einem Adobe Experience Platform-Workflow eine CSV-Datei in Adobe Experience Platform aufnehmen können

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf Adobe Experience Platform Launch: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Zugriff auf Postman

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben

## Übungen

[1.2.1 Erkunden der Website](./ex1.md)

In dieser Übung erkunden Sie die Website, die Sie im Rahmen dieser Aktivierung verwenden werden.

[1.2.2 Konfigurieren von Schemata und Set-Bezeichnern](./ex2.md)

In dieser Übung konfigurieren Sie die erforderlichen XDM-Schemas, um Profilinformationen und Kundenverhalten zu erfassen. In jedem XDM-Schema müssen Sie auch eine primäre Kennung konfigurieren, mit der alle Informationen verknüpft werden.

[1.2.3 Konfigurieren von Datensätzen](./ex3.md)

In dieser Übung rufen Sie die erforderlichen Datensätze ab, um Profilinformationen und Kundenverhalten zu erfassen und zu speichern.

[1.2.4 Datenaufnahme aus Offline-Quellen](./ex4.md)

In dieser Übung gehen Sie auf die Website und in die App und verhalten sich wie ein Kunde, der Daten an Platform streamt.

[1.2.5 Data Landing Zone](./ex5.md)

Richten Sie Ihren Source-Connector für die Data Landing Zone mit Azure Blob Storage ein.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Überblick über die Vorteile.

![Tech Insiders](./../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um alles über Adobe Experience Platform und seine Programme zu erfahren. Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.

[Zurück zu „Alle Module“](../../../overview.md)
