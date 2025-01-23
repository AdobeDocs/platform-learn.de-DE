---
title: Streamen von Daten von Apache Kafka nach Adobe Experience Platform
description: In diesem Modul erfahren Sie, wie Sie Ihren eigenen Apache Kafka-Cluster einrichten, Themen, Produzenten und Verbraucher definieren und Daten mit dem Adobe Experience Platform Sink Connector für Kafka Connect in Adobe Experience Platform streamen.
kt: 5342
doc-type: tutorial
exl-id: 2b7010f3-ab31-4099-aecd-fd4e73b7e96e
source-git-commit: bd46be455f88007174f7e6be9a1ce5f508edc09b
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 1%

---

# 2.6 Streamen Sie Daten von Apache Kafka nach Adobe Experience Platform

In diesem Modul erfahren Sie, wie Sie Ihren eigenen Apache Kafka-Cluster einrichten, Themen, Produzenten und Verbraucher definieren und Daten mithilfe des Adobe Experience Platform Sink Connectors über Kafka Connect in Adobe Experience Platform streamen.

## Lernziele

- Durchführen eines grundlegenden Setups eines lokalen Kafka-Clusters
- Erstellen eines Kafka-Themas, Verwenden eines Kafka-Produzenten und eines Kafka-Verbrauchers
- Konfigurieren von Kafka Connect und dem Adobe Experience Platform Sink Connector
- Manuelles Erstellen von Ereignissen und deren Aufnahme in Adobe Experience Platform
- Verwenden Sie eine bestehende Twitter-Producer-Bibliothek von Kafka Connect, um Twitter-Daten in Adobe Experience Platform zu streamen

## Voraussetzungen

- Java JDK23 oder höher muss auf Ihrem Computer installiert sein. Sie können dieses JDK hier herunterladen: [https://www.oracle.com/java/technologies/javase-jdk11-downloads.html](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- Zugriff auf Adobe Experience Platform

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben

## Übungen

[2.6.1 Einführung in Apache Kafka](./ex1.md)

In dieser Übung lernen Sie die Grundlagen von Apache Kafka kennen

[2.6.2 Installieren und Konfigurieren des Kafka-Clusters](./ex2.md)

In dieser Übung werden Sie Ihren grundlegenden Apache Kafka-Cluster herunterladen, installieren und konfigurieren.

[2.6.3 Konfigurieren des HTTP-API-Streaming-Endpunkts in Adobe Experience Platform](./ex3.md)

In dieser Übung konfigurieren Sie einen HTTP-API-Source-Connector in Adobe Experience Platform.

[2.6.4 Installieren und konfigurieren Sie Kafka Connect und den Adobe Experience Platform Sink Connector](./ex4.md)

In dieser Übung verwenden Sie Kafka Connect , um den Adobe Experience Platform Sink Connector zu installieren und zu verwenden, und Sie senden Ereignisse manuell in Adobe Experience Platform.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Überblick über die Vorteile.

![Tech Insiders](./../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um alles über Adobe Experience Platform und seine Programme zu erfahren. Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.

[Zurück zu „Alle Module“](../../../overview.md)
