---
title: Streamen von Daten von Apache Kafka nach Adobe Experience Platform
description: In diesem Modul erfahren Sie, wie Sie einen eigenen Apache Kafka-Cluster einrichten, Themen, Hersteller und Verbraucher definieren und Daten mit dem Adobe Experience Platform Sink Connector für Kafka Connect an Adobe Experience Platform streamen.
kt: 5342
doc-type: tutorial
exl-id: 2b7010f3-ab31-4099-aecd-fd4e73b7e96e
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 1%

---

# 2.6 Streamen von Daten von Apache Kafka nach Adobe Experience Platform

**Autoren: [Vivek Tiwari](https://www.linkedin.com/in/vivek-tiwari-25092656/), [Nipun nair](https://www.linkedin.com/in/nipunnair/), [Wouter van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul erfahren Sie, wie Sie einen eigenen Apache Kafka-Cluster einrichten, Themen, Hersteller und Verbraucher definieren und Daten über Kafka Connect über den Adobe Experience Platform Sink Connector an Adobe Experience Platform streamen.

## Lernziele

- Grundlegende Einrichtung eines lokalen Kafka-Clusters durchführen
- Erstellen eines Kafka-Themas, Verwenden eines Kafka-Herstellers und eines Kafka-Verbrauchers
- Konfigurieren von Kafka Connect und Adobe Experience Platform Sink Connector
- Manuelles Erstellen von Ereignissen und Anzeigen der Erfassung dieser Ereignisse in Adobe Experience Platform
- Verwenden Sie eine bestehende Twitter-Produktionsbibliothek von Kafka Connect, um Twitter-Daten in Adobe Experience Platform zu streamen.

## Voraussetzungen

- Java JDK11 oder höher muss auf Ihrem Computer installiert sein. Sie können dieses JDK hier herunterladen: [https://www.oracle.com/java/technologies/javase-jdk11-downloads.html](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- Zugriff auf Adobe Experience Platform

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben.

## Übungen

[2.6.1 Einführung in Apache Kafka](./ex1.md)

In dieser Übung lernen Sie die Grundlagen von Apache Kafka kennen

[2.6.2 Kafka-Cluster installieren und konfigurieren](./ex2.md)

In dieser Übung laden Sie Ihren grundlegenden Apache Kafka-Cluster herunter, installieren und konfigurieren ihn.

[2.6.3 HTTP-API-Streaming-Endpunkt in Adobe Experience Platform konfigurieren](./ex3.md)

In dieser Übung konfigurieren Sie einen HTTP-API-Source-Connector in Adobe Experience Platform.

[2.6.4 Installieren und Konfigurieren von Kafka Connect und Adobe Experience Platform Sink Connector](./ex4.md)

In dieser Übung verwenden Sie Kafka Connect zur Installation und Verwendung des Adobe Experience Platform Sink Connectors und senden Ereignisse manuell an Adobe Experience Platform.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investieren, um alles über Adobe Experience Platform und seine Anwendungen zu erfahren. Wenn Sie Fragen haben, möchten Sie allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com** senden.

[Zu allen Modulen zurückkehren](../../../overview.md)
