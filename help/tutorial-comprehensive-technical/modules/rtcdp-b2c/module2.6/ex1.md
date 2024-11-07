---
title: Einführung in Apache Kafka
description: Einführung in Apache Kafka
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# 2.6.1 Einführung in Apache Kafka

## 2.6.1.1 Einführung

Jede Organisation beginnt auf sehr einfache Weise aus der Datenperspektive. Das Datenökosystem eines Unternehmens beginnt mit einem Quellsystem und einer Zielgruppe. Das Quellsystem sendet Daten an das Zielsystem, und das ist es. Einfach, nicht wahr?
Wenn es nur so einfach bleiben würde. Unternehmen übertreffen diese einfache Einrichtung schnell, und die Anzahl der Quellsysteme und Zielsysteme steigt schnell. Alle diese verschiedenen Quellen und Ziele müssen Daten miteinander austauschen, und die Dinge werden schnell sehr komplex.
Wenn beispielsweise eine Organisation über 4 Quellen und 6 Ziele verfügt und alle diese Anwendungen miteinander kommunizieren müssen, müssen Sie 24 Integrationen erstellen... Jede dieser Integrationen hat eigene Schwierigkeiten:

- Protokoll: Transport der Daten (TCP, HTTP, REST, FTP, ...)
- Datenformat: Wie werden die Daten analysiert (binär, CSV, JSON, Parquet usw.)
- Datenschema und Entwicklung: Was ist das Datenmodell und wie wird es sich entwickeln?

Jedes Mal, wenn Sie ein Quellsystem an ein Zielsystem anschließen, erhöht sich die Belastung dieser Systeme durch diese Verbindung.

Wie löst man das? Hier kommt Apache Kafka ins Bild. Apache Kafka ermöglicht es einem Unternehmen, Datenströme und Systeme durch die Bereitstellung eines gemeinsamen, weit verbreiteten Messaging-Systems mit hohem Durchsatz zu entkoppeln. Source-Systeme senden ihre Daten an Apache Kafka, und die Zielsysteme nutzen Daten von Apache Kafka.

Denken Sie an alle Datenquellen, die Unternehmen verwalten müssen:

- Website-Ereignisse
- App-Ereignisse
- POS-Ereignisse
- CRM-Daten
- Callcenter-Daten
- Transaktionsverlauf
- ...

Denken Sie an alle Zieltypen, die Unternehmen in ihrem Ökosystem verwenden und die möglicherweise Daten aus diesen Quellsystemen benötigen:

- CRM
- Datensee
- E-Mail-System
- Prüfung
- analytics
- ...

Apache Kafka wurde von LinkedIn gegründet und ist jetzt ein Open-Source-Projekt, das hauptsächlich von Confluent betreut wird.
Apache Kafka bietet eine verteilte, widerstandsfähige Architektur, die fehlertolerant ist. Er kann horizontal auf 100 s Makler skaliert und auf Millionen von Nachrichten pro Sekunde skaliert werden. Es bietet eine hohe Leistung mit Latenzen von weniger als 10 ms, die sich ideal für Echtzeit-Anwendungsfälle eignen.

Beispiele für Anwendungsfälle:

- Messaging-System
- Aktivitätsverfolgung
- Erfassen von Metriken aus vielen verschiedenen Standorten
- Erfassung von Anwendungsprotokollen
- Streamverarbeitung (mit Kafka Streams API oder Spark)
- Entkopplung von Systemabhängigkeiten
- Integration mit Spark, Flink, Storm, Hadoop und vielen anderen Big Data-Technologien.

Beispiel:

- Netflix verwendet Kafka, um Empfehlungen in Echtzeit anzuwenden, während Sie Fernsehsendungen ansehen
- Uber verwendet Kafka, um Benutzer-, Taxi- und Reisedaten in Echtzeit zu sammeln, um die Nachfrage zu berechnen und vorherzusagen und die Preissteigerungen in Echtzeit zu berechnen.
- LinkedIn verwendet Kafka, um Spam zu verhindern, Benutzerinteraktionen zu sammeln und bessere Verbindungsempfehlungen in Echtzeit zu erhalten

Für alle diese Anwendungsfälle wird Kafka nur als Transportmittel eingesetzt. Kafka ist wirklich gut darin, Daten zwischen Anwendungen zu verschieben.

## 2.6.1.2 Kafka-Terminologie

### Nachricht

Eine Nachricht ist eine Mitteilung, die von einem System an Kafka gesendet wird. Eine Nachricht enthält eine Payload und eine Payload enthält Datenelemente. Beispielsweise wird ein Erlebnisereignis, das von einer Website an Adobe Experience Platform gesendet wird, als Nachricht betrachtet.

### Themen, Partitionen, Versätze

Ein Thema ist ein bestimmter Datenstrom, der einer Tabelle in einer Datenbank ähnelt. Sie können beliebig viele Themen haben und ein Thema wird anhand seines Namens identifiziert. Themen werden in Partitionen aufgeteilt. Jede Partition wird sortiert und jede Nachricht innerhalb einer Partition erhält eine inkrementelle ID, die als **offset** bezeichnet wird. Nachrichten werden in einem Thema, auf einer Partition gespeichert und mithilfe eines Versatzes referenziert. Nachrichten werden nur für eine begrenzte Zeit aufbewahrt (standardmäßig 1 Woche). Sobald eine Nachricht in eine Partition geschrieben wurde, kann sie nicht mehr geändert werden.

### Broker

Ein Broker ähnelt einem Server. Ein Kafka-Cluster besteht aus mehreren Brokern (Servern). Jeder Broker wird mit einer ID identifiziert und enthält bestimmte Themenpartitionen.

### Replikation

Kafka ist ein verteiltes System. Eines der wichtigen Dinge eines verteilten Systems ist, dass Daten sicher gespeichert werden und daher eine Replikation erforderlich ist. Wenn ein Broker (Server) ausfällt, sollte ein anderer Broker (Server) dennoch Zugriff auf Nachrichten gewähren können, die ursprünglich auf dem heruntergestuften Broker gespeichert wurden. Die Replikation erstellt Kopien von Nachrichten über mehrere Makler hinweg, um sicherzustellen, dass keine Daten verloren gehen.

### Hersteller

Wie werden Daten an Kafka gesendet? Das ist die Rolle eines Produzenten. Ein Produzent stellt eine Verbindung zu einem Quellsystem her, nimmt Daten aus dem Quellsystem und schreibt diese Daten dann in Themen auf Partitionen. Basierend auf der Konfiguration Ihres Kafka-Clusters werden Produzenten automatisch wissen, an welchen Broker und welche Partition sie schreiben sollen. In einem verteilten System mit mehreren Maklern und Replikationsstrategie speichert ein Hersteller Daten zufällig über mehrere Makler hinweg, was bedeutet, dass er automatisch Lastenausgleich durchführt.

### Nachrichtenschlüssel

Die Hersteller können einen Schlüssel mit der Nachricht senden. Ein Schlüssel kann eine beliebige Zeichenfolge, Zahl usw. sein. Wenn kein Schlüssel angegeben wird, wird eine Nachricht zufällig an Makler gesendet. Wenn ein Schlüssel gesendet wird, gehen alle Nachrichten für diesen Schlüssel immer zur selben Partition. Ein Nachrichtenschlüssel als solcher wird verwendet, um Nachrichten basierend auf einem bestimmten Feld anzuordnen.

### Verbraucher

Verbraucher lesen Daten aus einem Apache Kafka-Thema und geben diese Daten dann für Zielsysteme frei. Die Verbraucher wissen, von welchem Broker sie lesen können. Daten werden von einem Verbraucher in der richtigen Reihenfolge innerhalb jeder Partition gelesen. Verbraucher lesen Daten in Verbrauchergruppen.

### Zookeeper

ZooKeeper ist im Wesentlichen ein Dienst für verteilte Systeme, der einen hierarchischen Schlüsselwertspeicher anbietet, der zur Bereitstellung eines dezentralen Konfigurationsdienstes, eines Synchronisierungsdienstes und einer Namensregistrierung für große verteilte Systeme verwendet wird. Zookeeper muss ausgeführt werden, bevor Sie Apache Kafka verwenden können, und Zookeeper ist sozusagen der Meister der Zeremonie für Kafka, der verteilte Dienste im Backend verwaltet, während Kafka Ereignisse produziert und verbraucht.

Du hast diese Übung beendet.

Nächster Schritt: [2.6.2 Kafka-Cluster installieren und konfigurieren](./ex2.md)

[Zurück zu Modul 2.6](./aep-apache-kafka.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
