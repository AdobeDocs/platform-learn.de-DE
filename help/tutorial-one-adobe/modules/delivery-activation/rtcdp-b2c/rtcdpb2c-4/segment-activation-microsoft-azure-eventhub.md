---
title: Audience Activation zu Microsoft Azure Event Hub
description: Audience Activation zu Microsoft Azure Event Hub
kt: 5342
doc-type: tutorial
exl-id: c1f5566d-0f57-4554-95ee-950d66373716
source-git-commit: 2d5ca888eb24c1f65b4ecd48030ec8d1659b7f84
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# 2.4 Real-Time CDP: Audience Activation zu Microsoft Azure Event Hub

In diesem Modul richten Sie ein Microsoft Azure EventHub-Ziel als Echtzeit-Ziel für Adobe Experience Platform Real-time CDP ein. Sie werden auch eine Azure-Funktion einrichten und bereitstellen, die in Echtzeit ausgelöst wird, wenn Adobe Experience Platform eine Zielgruppen-Payload an Ihr Azure EventHub-Ziel sendet. Die Azure-Funktion, die Sie in die Trigger nehmen, zeigt den Mechanismus der Aktivierungsfunktionen von Adobe Experience Platform Real-time CDP.

In diesem Modul erfahren Sie auch, welche Trigger Real-Time CDP-Programme tatsächlich eine Payload an ein bestimmtes Ziel senden. Wir besprechen auch den Status einer Zielgruppen-Qualifizierung und wie sie mit der Aktivierung zusammenhängt.

Adobe Experience Platform Real-Time CDP unterstützt die Datenaktivierung für Streaming-Cloud-Speicher-Ziele, sodass Sie Zielgruppendaten und -ereignisse in Echtzeit im JSON-Format an diese Ziele exportieren können. Anschließend können Sie die Geschäftslogik zusätzlich zu diesen Ereignissen in Ihren Zielen beschreiben

Microsoft Azure Event Hubs ist ein vollständig verwalteter Service zur Datenaufnahme in Echtzeit, der einfach, vertrauenswürdig und skalierbar ist. Streamen Sie Millionen von Ereignissen pro Sekunde aus jeder Quelle, um dynamische Daten-Pipelines zu erstellen und sofort auf geschäftliche Herausforderungen zu reagieren.

## Lernziele

- Machen Sie sich mit den Microsoft Azure Event Hubs vertraut
- Einrichten eines RTCDP-Ziels für Ihren Microsoft Azure Event Hub
- Erfahren Sie, wann die Real-Time CDP aktiviert wird und wie die Aktivierungs-Payload aussieht
- Einrichten von Visual Studio Code zum Entwickeln, Testen und Bereitstellen des Azure-Projekts
- Erstellen und Bereitstellen einer Azure-Funktion, die Zielgruppenqualifikationen nutzt, die in Echtzeit von RTCDP bereitgestellt werden

## Voraussetzungen

- Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform)
- Erfahren Sie, wie Sie Zielgruppen in Adobe Experience Platform definieren, verwenden und aktivieren

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../../getting-started/gettingstarted/ex1.md) beschrieben

## Übungen

[2.4.1 Konfigurieren der Umgebung](./ex1.md)

In dieser Übung richten Sie Ihre Microsoft Azure-Umgebung ein.

[2.4.2 Konfigurieren der Microsoft Azure EventHub-Umgebung](./ex2.md)

In dieser Übung richten Sie Ihre Microsoft Azure EventHub-Umgebung ein.

[2.4.3 Konfigurieren des Azure Event Hub-Ziels in Adobe Experience Platform](./ex3.md)

In dieser Übung richten Sie Ihre Real-Time CDP-Zielverbindung ein, die Zielgruppen in Echtzeit an die Event Hub-Instanz bereitstellt, die Sie in der vorherigen Übung konfiguriert haben.

[2.4.4 Erstellen einer Zielgruppe](./ex4.md)

In dieser Übung erstellen Sie eine Zielgruppe in Adobe Experience Platform

[2.4.5 Zielgruppe aktivieren](./ex5.md)

In dieser Übung aktivieren Sie Ihre Zielgruppe für Ihr EventHub-Ziel.

[2.4.6 Microsoft Azure-Projekt erstellen](./ex6.md)

In dieser Übung erstellen Sie eine Azure-Funktion, die in Echtzeit ausgelöst wird, wenn Adobe Experience Platform Zielgruppenqualifikationen für das entsprechende Azure Event Hub-Ziel bereitstellt.

[2.4.7 End-to-End-Szenario](./ex7.md)

An dieser Stelle ist alles eingerichtet. Sie können jetzt auf Ihrer Demo-Website surfen und Zielgruppenqualifikationen für Ihre Microsoft Azure Event Hub-Trigger-Funktion erhalten.

![Tech Insiders](./../../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um alles über Adobe Experience Platform und seine Programme zu erfahren. Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.

[Zurück zu „Alle Module“](./../../../../overview.md)
