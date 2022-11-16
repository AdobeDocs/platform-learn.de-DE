---
title: Foundation - Datenerfassung
description: Foundation - Datenerfassung
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: dbbc0539-ae1b-488d-b312-76a74d4d361f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 1%

---

# 2. Foundation - Datenerfassung

**Autor: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul besteht das Ziel darin, alles über die Datenerfassung zu erfahren. Sie erfahren mehr über die Datenerfassung in Streaming und Batch. Sie implementieren die Streaming-Datenerfassung mithilfe von Launch, sodass das Kundenverhalten auf der Hands-On-Lab-Website in Echtzeit an Adobe Experience Platform gestreamt wird. Sie erfahren mehr über die Batch-Datenerfassung, indem Sie einen Adobe Experience Platform-Workflow verwenden, um eine CSV-Datei zu erstellen, sie einem XDM-Schema zuzuordnen und sie dann in Adobe Experience Platform aufzunehmen.

## Lernziele

- Erfahren Sie, wie Sie ein XDM-Schema in Adobe Experience Platform erstellen
- Erfahren Sie, wie Sie in Adobe Experience Platform Datensätze erstellen.
- Erfahren Sie, wie Sie einen Streaming-Endpunkt erstellen und die Adobe Experience Platform-Erweiterung in Launch konfigurieren.
- Erfahren Sie, wie Sie in Launch Regeln erstellen, um Daten an Adobe Experience Platform zu streamen.
- Erfahren Sie, wie Sie Adobe Experience Platform Launch in eine Webseite integrieren.
- Erfahren Sie, wie Sie mit einem Adobe Experience Platform-Workflow eine CSV-Datei in Adobe Experience Platform erfassen.

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf Adobe Experience Platform Launch: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Zugriff auf [https://public.aepdemo.net](https://public.aepdemo.net)
- Zugriff auf Postman

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem2.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--module2sandbox--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[2.1 Website erkunden](./ex1.md)

In dieser Übung werden Sie die Website erkunden, die Sie als Teil dieser Aktivierung verwenden werden.

[2.2 Konfigurieren von Schemata und Festlegen von Kennungen](./ex2.md)

In dieser Übung konfigurieren Sie die erforderlichen XDM-Schemas, um Profilinformationen und Kundenverhalten zu erfassen. In jedem XDM-Schema müssen Sie auch eine primäre Kennung konfigurieren, mit der alle Informationen verknüpft werden.

[2.3 Datensätze konfigurieren](./ex3.md)

In dieser Übung rufen Sie die erforderlichen Datensätze ab, um Profilinformationen und Kundenverhalten zu erfassen und zu speichern.

[2.4 Datenerfassung aus Offline-Quellen](./ex4.md)

In dieser Übung werden Sie auf die Website und die mobile App gehen und sich wie ein Kunde verhalten, indem Sie Daten an Platform streamen.

[2.5 Einstiegszone für Daten](./ex5.md)

Richten Sie Ihren Data Landing Zone Source Connector mit Azure Blob Storage ein.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
