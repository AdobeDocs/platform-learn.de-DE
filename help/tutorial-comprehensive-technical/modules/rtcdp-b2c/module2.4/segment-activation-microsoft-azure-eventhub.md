---
title: Segmentaktivierung für Microsoft Azure Event Hub
description: Segmentaktivierung für Microsoft Azure Event Hub
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# 2.4 Real-Time CDP: Segmentaktivierung für Microsoft Azure Event Hub

**Autoren: [Marc Meewis](https://www.linkedin.com/in/marcmeewis/), [Wouter van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul richten Sie ein Microsoft Azure EventHub-Ziel als Echtzeit-Ziel für die Echtzeit-Kundendatenplattform von Adobe Experience Platform ein. Sie richten außerdem eine Azure-Funktion ein, die in Echtzeit ausgelöst wird, sobald Adobe Experience Platform eine Segment-Payload für Ihr Azure EventHub-Ziel bereitstellt. Die Azure-Funktion, die Sie in Trigger nehmen, zeigt den Mechanismus der Aktivierungsfunktionen der Adobe Experience Platform-Echtzeit-Kundendatenplattform an.

Im Rahmen dieses Moduls erhalten Sie außerdem Informationen dazu, welche Echtzeit-Kundendatenplattform von Trigger tatsächlich eine Payload an ein bestimmtes Ziel bereitstellt. Wir besprechen auch den Status einer Segmentqualifikation und deren Zusammenhang mit der Aktivierung.

Die Echtzeit-Kundendatenplattform von Adobe Experience Platform unterstützt die Datenaktivierung für Streaming-Cloud-Speicher-Ziele, sodass Sie Zielgruppendaten und -Ereignisse in Echtzeit im JSON-Format an diese Ziele exportieren können. Anschließend können Sie die Geschäftslogik über diese Ereignisse in Ihren Zielen beschreiben

Microsoft Azure Event Hubs ist ein vollständig verwalteter Echtzeit-Datenerfassungsdienst, der einfach, vertrauenswürdig und skalierbar ist. Streamen Sie Millionen von Ereignissen pro Sekunde von einer beliebigen Quelle, um dynamische Datenpipelines zu erstellen und sofort auf geschäftliche Herausforderungen zu reagieren.

## Lernziele

- Kennenlernen der Microsoft Azure Event Hubs
- Richten Sie ein RTCDP-Ziel für Ihren Microsoft Azure Event Hub ein.
- Erfahren Sie, wann die Echtzeit-Kundendatenplattform aktiviert wird und wie die Aktivierungs-Payload aussieht.
- Einrichten von Visual Studio Code zum Entwickeln, Testen und Bereitstellen Ihres Azure-Projekts
- Erstellen und Bereitstellen einer Azure-Funktion, die von RTCDP bereitgestellte Segmentqualifikationen in Echtzeit nutzt

## Voraussetzungen

- Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform)
- Kenntnis der AEP Demo-Website-Umgebung
- Grundlegendes zur Definition, Verwendung und Aktivierung von Streaming-Segmenten in Adobe Experience Platform

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [0.1 - Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben.

## Übungen

[2.4.0 Umgebung konfigurieren](./ex0.md)

In dieser Übung richten Sie Ihre Microsoft Azure-Umgebung ein.

[2.4.1 Konfigurieren der Microsoft Azure EventHub-Umgebung](./ex1.md)

In dieser Übung richten Sie Ihre Microsoft Azure EventHub-Umgebung ein.

[2.4.2 Konfigurieren des Azure Event Hub-Ziels in Adobe Experience Platform](./ex2.md)

In dieser Übung richten Sie Ihre Echtzeit-Kundendatenplattform-Zielverbindung ein, die Segmente in Echtzeit an das EventHub sendet, das Sie in der vorherigen Übung konfiguriert haben.

[2.4.3 Segment erstellen](./ex3.md)

In dieser Übung erstellen Sie ein Streaming-Segment in Adobe Experience Platform

[2.4.4 Segment aktivieren](./ex4.md)

In dieser Übung aktivieren Sie Ihr Streaming-Segment für Ihr Echtzeit-CDP-EventHub-Ziel.

[2.4.5 Microsoft Azure-Projekt erstellen](./ex5.md)

In dieser Übung erstellen Sie eine Azure-Funktion, die in Echtzeit ausgelöst wird, wenn die Adobe Experience Platform Segmentqualifikationen für das entsprechende Azure Event Hub-Ziel aktiviert.

[2.4.6 End-to-End-Szenario](./ex6.md)

An diesem Punkt ist alles eingerichtet. Sie können jetzt auf Ihrer AEP Demo-Website surfen und Segmentqualifikationen für Ihre Microsoft Azure EventHub-Trigger-Funktion bereitstellen.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investieren, um alles über Adobe Experience Platform und seine Anwendungen zu erfahren. Wenn Sie Fragen haben, möchten Sie allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com** senden.

[Zu allen Modulen zurückkehren](../../../overview.md)
