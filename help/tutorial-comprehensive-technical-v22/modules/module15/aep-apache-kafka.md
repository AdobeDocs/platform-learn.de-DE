---
title: Streamen von Daten von Apache Kafka nach Adobe Experience Platform
description: In diesem Modul erfahren Sie, wie Sie einen eigenen Apache Kafka-Cluster einrichten, Themen, Hersteller und Verbraucher definieren und Daten mit dem Adobe Experience Platform Sink Connector für Kafka Connect an Adobe Experience Platform streamen.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: e1e283b1-93b7-4d06-b9ed-beac48a99c3f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 2%

---

# 15. Streamen von Daten von Apache Kafka nach Adobe Experience Platform

**Autoren: [Vivek Tiwari](https://www.linkedin.com/in/vivek-tiwari-25092656/), [Nipun Nair](https://www.linkedin.com/in/nipunnair/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul erfahren Sie, wie Sie einen eigenen Apache Kafka-Cluster einrichten, Themen, Hersteller und Verbraucher definieren und Daten über Kafka Connect über den Adobe Experience Platform Sink Connector an Adobe Experience Platform streamen.

## Lernziele

- Grundlegende Einrichtung eines lokalen Kafka-Clusters durchführen
- Erstellen eines Kafka-Themas, Verwenden eines Kafka-Herstellers und eines Kafka-Verbrauchers
- Konfigurieren von Kafka Connect und Adobe Experience Platform Sink Connector
- Manuelles Erstellen von Ereignissen und Anzeigen der Erfassung dieser Ereignisse in Adobe Experience Platform
- Verwenden Sie eine vorhandene Twitter-Produktionsbibliothek aus Kafka Connect, um Twitter-Daten in Adobe Experience Platform zu streamen.

## Voraussetzungen

- Java JDK11 oder höher muss auf Ihrem Computer installiert sein. Sie können dieses JDK hier herunterladen: [https://www.oracle.com/java/technologies/javase-jdk11-downloads.html](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- Zugriff auf Adobe Experience Platform

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem24.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--aepSandboxId--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[15.1 Einführung in Apache Kafka](./ex1.md)

In dieser Übung lernen Sie die Grundlagen von Apache Kafka kennen

[15.2 Kafka-Cluster installieren und konfigurieren](./ex2.md)

In dieser Übung laden Sie Ihren grundlegenden Apache Kafka-Cluster herunter, installieren und konfigurieren ihn.

[15.3 HTTP-API-Streaming-Endpunkt in Adobe Experience Platform konfigurieren](./ex3.md)

In dieser Übung konfigurieren Sie einen HTTP-API-Quell-Connector in Adobe Experience Platform.

[15.4 Installieren und Konfigurieren von Kafka Connect und Adobe Experience Platform Sink Connector](./ex4.md)

In dieser Übung verwenden Sie Kafka Connect zur Installation und Verwendung des Adobe Experience Platform Sink Connectors und senden Ereignisse manuell an Adobe Experience Platform.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
