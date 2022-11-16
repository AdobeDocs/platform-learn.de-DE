---
title: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr
description: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 7f3d6dcb-845d-4ff1-97c3-8e93b8d2c624
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 1%

---

# 8. Adobe Journey Optimizer: Externe Datenquellen und benutzerdefinierte Aktionen

**Autor: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul verwenden Sie Adobe Journey Optimizer, um das Kundenverhalten zu überwachen, sowohl online als auch offline, und darauf intelligent, kontextbezogen und in Echtzeit zu reagieren. Sie haben bereits eine erste praktische Erfahrung mit Adobe Journey Optimizer in Modul 6 gemacht. In dieser Übung werden Sie ein wenig tiefer gehen und einen erweiterten Anwendungsfall untersuchen, bei dem externe Datenquellen als Teil einer Journey verwendet werden.

## Lernziele

- Erfahren Sie, wie Sie in Adobe Journey Optimizer Ereignisse, externe Datenquellen und Journey erstellen.
- Erfahren Sie, wie Sie Wetterinformationen aus der Open Weather API nutzen können.
- Erfahren Sie, wie Sie benutzerdefinierte Aktionsziele wie Twilio und Slack aus Adobe Journey Optimizer verwenden.

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf Adobe Journey Optimizer
- Zugriff auf die Open Weather-API

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem12.png)

## Geschäftskontext

Als Marke haben Sie stark in die Personalisierung von Online-Erlebnissen investiert. Jetzt möchten Sie so kontextuell und relevant für Offline-Erlebnisse sein.
In diesem Modul verwenden Sie die Präsenz eines Kunden in einem Offline-Store, um dann innerhalb des Stores ein personalisiertes Erlebnis bereitzustellen, indem Sie diesem Kunden relevante Inhalte auf unseren In-Store-Bildschirmen präsentieren. Gleichzeitig möchten wir diesem Kunden eine personalisierte Push- oder SMS-Nachricht in Echtzeit senden.
Als Marke verstehen Sie auch, dass der Kontext das Interesse eines Kunden stark beeinflusst. Daher möchten Sie die aktuellen Wetterinformationen des Standorts dieses Kunden einbringen, um zu entscheiden, welche Inhalte oder Werbeaktionen angezeigt werden sollen.

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--aepSandboxId--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[8.1 Ereignis definieren](./ex1.md)

Erfahren Sie, wie Sie mit Adobe Journey Optimizer ein benutzerspezifisches Ereignis definieren.

[8.2 Externe Datenquelle definieren](./ex2.md)

Erfahren Sie, wie Sie eine externe Datenquelle mit Adobe Journey Optimizer konfigurieren.

[8.3 Benutzerdefinierte Aktion definieren](./ex3.md)

Erfahren Sie, wie Sie mit Adobe Journey Optimizer eine externe Aktion definieren.

[8.4 Journey und Nachrichten erstellen](./ex4.md)

Kombinieren Sie Ereignisse, Datenquellen und Aktionen zu einer intelligenten und kontextbezogenen Journey.

[8.5 Trigger Journey](./ex5.md)

Trigger der spezifischen Journey.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
