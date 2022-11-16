---
title: Segmentaktivierung für Microsoft Azure Event Hub
description: Segmentaktivierung für Microsoft Azure Event Hub
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 73c2576d-0a69-4d56-a671-9ae1f75580b9
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---

# 13. Real-Time CDP: Segmentaktivierung für Microsoft Azure Event Hub

**Autoren: [Marc Meewis](https://www.linkedin.com/in/marcmeewis/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul richten Sie ein Microsoft Azure EventHub-Ziel als Echtzeit-Ziel für die Echtzeit-Kundendatenplattform von Adobe Experience Platform ein. Sie richten außerdem eine Azure-Funktion ein und stellen sie bereit, die in Echtzeit ausgelöst wird, sobald Adobe Experience Platform eine Segment-Payload für Ihr Azure EventHub-Ziel bereitstellt. Die Azure-Funktion, die Sie in Trigger nehmen, zeigt den Mechanismus der Aktivierungsfunktionen der Adobe Experience Platform-Echtzeit-Kundendatenplattform an.

Im Rahmen dieses Moduls erhalten Sie außerdem Informationen dazu, welche Echtzeit-Kundendatenplattform von Trigger tatsächlich eine Payload an ein bestimmtes Ziel bereitstellt. Wir besprechen auch den Status einer Segmentqualifikation und deren Zusammenhang mit der Aktivierung.

Die Echtzeit-Kundendatenplattform von Adobe Experience Platform unterstützt die Datenaktivierung für Streaming-Cloud-Speicher-Ziele, sodass Sie Zielgruppendaten und -Ereignisse in Echtzeit im JSON-Format an diese Ziele exportieren können. Anschließend können Sie die Geschäftslogik zusätzlich zu diesen Ereignissen in Ihren Zielen beschreiben

Microsoft Azure Event Hubs ist ein vollständig verwalteter Echtzeit-Datenerfassungsdienst, der einfach, vertrauenswürdig und skalierbar ist. Streamen Sie Millionen von Ereignissen pro Sekunde von einer beliebigen Quelle, um dynamische Datenpipelines zu erstellen und sofort auf geschäftliche Herausforderungen zu reagieren.

## Lernziele

- Kennenlernen der Microsoft Azure Event Hubs
- Richten Sie ein RTCDP-Ziel für Ihren Microsoft Azure Event Hub ein.
- Erfahren Sie, wann die Echtzeit-Kundendatenplattform aktiviert wird und wie die Aktivierungs-Payload aussieht.
- Einrichten von Visual Studio Code zum Entwickeln, Testen und Bereitstellen Ihres Azure-Projekts
- Erstellen und implementieren Sie eine Azure-Funktion, die von RTCDP bereitgestellte Segmentqualifikationen in Echtzeit nutzt

## Voraussetzungen

- Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform)
- Kenntnis der AEP Demo-Website-Umgebung
- Grundlegendes zur Definition, Verwendung und Aktivierung von Streaming-Segmenten in Adobe Experience Platform

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem18.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--module18sandbox--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[13.0 Umgebung konfigurieren](./ex0.md)

In dieser Übung richten Sie Ihre Microsoft Azure-Umgebung ein.

[13.1 Konfigurieren der Microsoft Azure EventHub-Umgebung](./ex1.md)

In dieser Übung richten Sie Ihre Microsoft Azure EventHub-Umgebung ein.

[13.2 Konfigurieren des Azure Event Hub-Ziels in Adobe Experience Platform](./ex2.md)

In dieser Übung richten Sie Ihre Echtzeit-Kundendatenplattform-Zielverbindung ein, die Segmente in Echtzeit an das EventHub sendet, das Sie in der vorherigen Übung konfiguriert haben.

[13.3 Segment erstellen](./ex3.md)

In dieser Übung erstellen Sie ein Streaming-Segment in Adobe Experience Platform

[13.4 Segment aktivieren](./ex4.md)

In dieser Übung aktivieren Sie Ihr Streaming-Segment für Ihr Echtzeit-CDP-EventHub-Ziel.

[13.5 Microsoft Azure-Projekt erstellen](./ex5.md)

In dieser Übung erstellen Sie eine Azure-Funktion, die in Echtzeit ausgelöst wird, wenn Adobe Experience Platform Segmentqualifikationen für das entsprechende Azure Event Hub-Ziel aktiviert.

[13.6 End-to-End-Szenario](./ex6.md)

An diesem Punkt ist alles eingerichtet. Sie können jetzt auf Ihrer AEP Demo-Website surfen und Segmentqualifikationen für Ihre Microsoft Azure EventHub-Trigger-Funktion bereitstellen.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
