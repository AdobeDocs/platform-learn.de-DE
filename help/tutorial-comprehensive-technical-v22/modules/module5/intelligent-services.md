---
title: Intelligent Services
description: Intelligent Services
kt: 5342
audience: Data Engineer, Data Architect, Data Scientist
doc-type: tutorial
activity: develop
exl-id: 99b56722-95bf-4c51-b4d6-8b5a8e5fd936
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 16%

---

# 5. Intelligent Services

**Autoren: [Diptiman Badajena](https://www.linkedin.com/in/diptiman-badajena-1b178019/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul erfahren Sie, wie Sie Adobe Experience Platform Intelligent Services einrichten, konfigurieren und verwenden.

## Lernziele

- Kennenlernen von Adobe Experience Platform
- Schema/Datensatz für die Verwendung mit Intelligent Services konfigurieren
- Erstellen einer neuen Customer AI-Instanz
- Scoring-Dashboard und Segmentierung

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem5.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--module10sandbox--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[5.1 Customer AI - Datenvorbereitung (Aufnahme)](./ex1.md)

Kundendaten werden mit dem Experience-Datenmodell (XDM) in Adobe Experience Platform erfasst und transformiert. Insbesondere müssen alle Datensätze, die in Intelligent Services verwendet werden, dem XDM-Schema Consumer ExperienceEvent (CEE) entsprechen.

[5.2 Customer AI - Erstellen einer neuen Instanz (Konfigurieren)](./ex2.md)

Der Marketing-Analyst konfiguriert die gewünschten Vorhersagen, indem er Verfahrensregeln festlegt und relevante Daten identifiziert. Planen Sie nach dem Konfigurieren des Modells Ausführungen und Bewertungen.

[5.3 Customer AI - Scoring-Dashboard und Segmentierung (Vorhersagen und Handeln)](./ex3.md)

Nachdem die Modelle Training und Bewertung abgeschlossen haben, werden die Ergebnisse in Platform zurückgeschrieben. Sie können festlegen, welche Aktionen mit den Prognosen ausgeführt werden sollen, z. B. das Definieren von Segmenten, das Erstellen benutzerdefinierter Dashboards usw.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
