---
title: Einführung in Apache Kafka
description: Einführung in Apache Kafka
kt: 5342
doc-type: tutorial
exl-id: f2d770d1-6ae4-4c2a-82e7-bd1ba295c895
source-git-commit: 348554b5a2d43d7a882e8259b39a57af13d41ff4
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# 2.6.1 Einführung in Apache Kafka

## 2.6.1.1

Jedes Unternehmen beginnt ganz einfach aus der Datenperspektive. Das Daten-Ökosystem eines Unternehmens beginnt mit einem Quellsystem und einer Zielgruppe. Das Quellsystem sendet Daten an das Zielsystem, und das war&#39;s. Einfach, oder?
Wenn es doch nur so einfach bliebe. Unternehmen wachsen schnell aus diesem einfachen Setup heraus, und die Anzahl der Quell- und Zielsysteme steigt schnell. All diese verschiedenen Quellen und Ziele müssen Daten miteinander austauschen, und die Dinge werden schnell sehr komplex.
Wenn beispielsweise ein Unternehmen über 4 Quellen und 6 Ziele verfügt und alle diese Programme miteinander sprechen müssen, müssen Sie 24 Integrationen erstellen… Jede dieser Integrationen bringt ihre eigenen Schwierigkeiten mit sich:

- Protokoll: Wie werden Daten transportiert (TCP, HTTP, REST, FTP, …)
- Datenformat: Wie werden die Daten geparst (binär, CSV, JSON, Parquet, …)?
- Datenschema und -entwicklung: Was ist das Datenmodell und wie entwickelt es sich?

Darüber hinaus werden diese Systeme jedes Mal, wenn Sie ein Quellsystem mit einem Zielsystem verbinden, durch diese Verbindung stärker belastet.

Wie löst man das? Und hier kommt Apache Kafka ins Spiel. Apache Kafka ermöglicht es einem Unternehmen, Datenströme und Systeme durch ein gemeinsames, verteiltes Messaging-System mit hohem Durchsatz zu entkoppeln. Source-Systeme senden ihre Daten an Apache Kafka, und Zielsysteme nutzen Daten von Apache Kafka.

Denken Sie an alle Arten von Datenquellen, die Experience Manager verwalten muss:

- Website-Events
- Mobile-App-Ereignisse
- POS-Ereignisse
- CRM-Daten
- Callcenter-Daten
- Transaktionsverlauf
- ...

Und denken Sie an alle Arten von Zielen, die Unternehmen in ihrem Ökosystem verwenden und die möglicherweise alle Daten aus diesen Quellsystemen benötigen:

- CRM
- Data Lake
- E-Mail-System
- Audit
- analytics
- ...

Apache Kafka wurde von LinkedIn entwickelt und ist jetzt ein Open-Source-Projekt, das hauptsächlich von Confluent gepflegt wird.
Apache Kafka bietet eine verteilte, robuste Architektur, die fehlertolerant ist. Er kann horizontal auf 100 s von Brokern skaliert werden und kann auf Millionen von Nachrichten pro Sekunde skaliert werden. Es bietet eine hohe Leistung mit Latenzen von weniger als 10 ms, was ideal für Echtzeit-Anwendungsfälle ist.

Einige Anwendungsbeispiele:

- Messaging-System
- Aktivitäts-Tracking
- Sammeln von Metriken aus vielen verschiedenen Speicherorten
- Erfassen von Anwendungsprotokollen
- Stream-Verarbeitung (mit Kafka Streams-API oder Spark)
- Entkopplung von Systemabhängigkeiten
- Integration mit Spark, Flink, Storm, Hadoop und vielen anderen Big-Data-Technologien.

Beispiel:

- Netflix nutzt Kafka, um Empfehlungen in Echtzeit anzuwenden, während Sie Fernsehsendungen ansehen
- Uber verwendet Kafka, um Benutzer-, Taxi- und Reisedaten in Echtzeit zu erfassen, um Nachfrageprognosen und Preissteigerungen in Echtzeit zu berechnen
- LinkedIn verwendet Kafka, um Spam zu verhindern, Benutzerinteraktionen zu erfassen und in Echtzeit bessere Verbindungsempfehlungen zu geben

Für alle diese Anwendungsfälle wird Kafka nur als Transportmechanismus verwendet. Kafka ist wirklich gut darin, Daten zwischen Anwendungen zu verschieben.

## Terminologie von 2.6.1.2 Kafka

### Nachricht

Eine Nachricht ist eine Mitteilung, die von einem System an Kafka gesendet wird. Eine Nachricht enthält eine Payload und eine Payload enthält Datenelemente. Beispielsweise wird ein Erlebnisereignis, das von einer Website an Adobe Experience Platform gesendet wird, als Nachricht betrachtet.

### Thema, Partitionen, Versätze

Ein Thema ist ein bestimmter Datenstrom, der einer Tabelle in einer Datenbank ähnelt. Sie können beliebig viele Themen haben, und ein Thema wird durch seinen Namen identifiziert. Themen sind in Partitionen unterteilt. Jede Partition wird sortiert und jede Nachricht innerhalb einer Partition erhält eine inkrementelle ID, die als **bezeichnet**. Nachrichten werden in einem Thema auf einer Partition gespeichert und durch einen Offset referenziert. Nachrichten werden nur für eine begrenzte Zeit aufbewahrt (der Standardwert ist 1 Woche). Sobald eine Nachricht auf eine Partition geschrieben wurde, kann sie nicht mehr geändert werden.

### Broker

Ein Broker ähnelt einem Server. Ein Kafka-Cluster besteht aus mehreren Brokern (Servern). Jeder Broker wird mit einer ID identifiziert und enthält bestimmte Themenpartitionen.

### Replikation

Kafka ist ein verteiltes System. Eines der wichtigen Dinge bei einem verteilten System ist, dass Daten sicher gespeichert werden und daher eine Replikation erforderlich ist. Schließlich sollte ein anderer Broker (Server), wenn ein Broker (Server) ausfällt, immer noch in der Lage sein, Zugriff auf Nachrichten zu gewähren, die ursprünglich auf dem Broker gespeichert waren, der ausgefallen ist. Die Replikation erstellt Kopien von Nachrichten über mehrere Broker hinweg, um sicherzustellen, dass keine Daten verloren gehen.

### Produzenten

Wie werden Daten an Kafka gesendet? Das ist die Rolle eines Produzenten. Ein Produzent stellt eine Verbindung zu einem Quellsystem her und nimmt Daten aus dem Quellsystem auf und schreibt diese Daten dann in Themen auf Partitionen. Basierend auf der Konfiguration Ihres Kafka-Clusters wissen Produzenten automatisch, auf welchen Broker und welche Partition sie schreiben sollen. In einem verteilten System mit mehreren Brokern und Replikationsstrategie speichert ein Produzent Daten nach dem Zufallsprinzip über mehrere Broker hinweg, was bedeutet, dass er Lastenausgleich automatisch durchführt.

### Nachrichtenschlüssel

Produzenten können einen Schlüssel mit der Nachricht senden. Ein Schlüssel kann eine beliebige Zeichenfolge, Zahl usw. sein. Wenn kein Schlüssel bereitgestellt wird, wird eine Nachricht nach dem Zufallsprinzip an Broker gesendet. Wenn ein Schlüssel gesendet wird, gehen alle Nachrichten für diesen Schlüssel immer auf dieselbe Partition. Ein Nachrichtenschlüssel als solcher wird verwendet, um Nachrichten basierend auf einem bestimmten Feld zu sortieren.

### Verbraucher

Nutzerinnen und Nutzer lesen Daten aus einem Apache Kafka-Thema und geben diese Daten dann für Zielsysteme frei. Die Verbraucher wissen, von welchem Makler sie lesen können. Die Daten werden von einem Verbraucher in der richtigen Reihenfolge innerhalb jeder Partition gelesen. Verbraucher lesen Daten in Verbrauchergruppen.

### Tierpfleger

ZooKeeper ist im Wesentlichen ein Dienst für verteilte Systeme, der einen hierarchischen Schlüssel-Wert-Speicher bietet, der verwendet wird, um einen verteilten Konfigurations-Service, einen Synchronisierungs-Service und eine Namensregistrierung für große verteilte Systeme bereitzustellen. Zookeeper muss laufen, bevor man Apache Kafka verwenden kann, und Zookeeper ist sozusagen der Zeremonienmeister für Kafka, der verteilte Dienste im Backend verwaltet, während Kafka Ereignisse produziert und nutzt.

Du hast diese Übung beendet.

Nächster Schritt: [2.6.2 Installieren und konfigurieren Sie Ihren Kafka-Cluster](./ex2.md)

[Zurück zum Modul 2.6](./aep-apache-kafka.md)

[Zurück zu „Alle Module“](../../../overview.md)
