---
title: Installieren und Konfigurieren des Kafka-Clusters
description: Installieren und Konfigurieren des Kafka-Clusters
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: adffeead-9bcb-4632-9a2c-c6da1c40b7f2
source-git-commit: be5a7dec47a83a14d74024015a15a9c24d04cd95
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# 2.6.2 Installieren und Konfigurieren des Kafka-Clusters

## Apache Kafka herunterladen

Wechseln Sie zu [https://kafka.apache.org/downloads](https://kafka.apache.org/downloads) und laden Sie die neueste veröffentlichte Version herunter. Wählen Sie die neueste Binärversion aus, in diesem Fall **3.9.**. Ihr Download wird gestartet.

![Kafka](./images/kafka1.png)

Erstellen Sie auf Ihrem Desktop einen Ordner mit dem Namen **Kafka_AEP** und legen Sie die heruntergeladene Datei in diesem Verzeichnis ab.

![Kafka](./images/kafka3.png)

Öffnen Sie ein **Terminal**-Fenster, indem Sie mit der rechten Maustaste auf den Ordner klicken und **Neues Terminal unter Ordner** klicken.

![Kafka](./images/kafka4.png)

Führen Sie diesen Befehl im Terminal-Fenster aus, um die heruntergeladene Datei zu entpacken:

`tar -xvf kafka_2.13-3.9.0.tgz`

>[!NOTE]
>
>Stellen Sie sicher, dass der obige Befehl der Version der heruntergeladenen Datei entspricht. Wenn Ihre Version aktueller ist, müssen Sie den obigen Befehl aktualisieren, damit er mit dieser Version übereinstimmt.

![Kafka](./images/kafka5.png)

Sie sehen dann Folgendes:

![Kafka](./images/kafka6.png)

Nach dem Dekomprimieren dieser Datei verfügen Sie nun über ein Verzeichnis wie dieses:

![Kafka](./images/kafka7.png)

Und in diesem Verzeichnis sehen Sie diese Unterverzeichnisse:

![Kafka](./images/kafka8.png)

Zurück zum Terminal-Fenster. Geben Sie den folgenden Befehl ein:

`cd kafka_2.13-3.9.0`

>[!NOTE]
>
>Stellen Sie sicher, dass der obige Befehl der Version der heruntergeladenen Datei entspricht. Wenn Ihre Version aktueller ist, müssen Sie den obigen Befehl aktualisieren, damit er mit dieser Version übereinstimmt.

![Kafka](./images/kafka9.png)

Geben Sie als Nächstes die `bin/kafka-topics.sh` ein.

![Kafka](./images/kafka10a.png)

Sie sollten dann diese Antwort sehen. Dies bedeutet, dass Kafka ordnungsgemäß installiert ist und Java einwandfrei funktioniert. (Erinnerung: Sie müssen Java 23 JDK installiert haben, damit dies funktioniert! Mithilfe des Befehls `java -version` können Sie sehen, welche Java-Version installiert wurde.)

![Kafka](./images/kafka10.png)

## Kafka starten

Um Kafka zu starten, müssen Sie Kafka Zookeeper und Kafka starten, in dieser Reihenfolge.

Öffnen Sie ein **Terminal**-Fenster, indem Sie mit der rechten Maustaste auf den Ordner **kafka_2.13-3.9.0** klicken und auf **Neues Terminal im Ordner** klicken.

![Kafka](./images/kafka11.png)

Geben Sie diesen Befehl ein:

`bin/zookeeper-server-start.sh config/zookeeper.properties`

![Kafka](./images/kafka12.png)

Sie sehen dann Folgendes:

![Kafka](./images/kafka13.png)

Lassen Sie dieses Fenster geöffnet, während Sie diese Übungen durchlaufen!

Öffnen Sie ein weiteres **Terminal**-Fenster, indem Sie mit der rechten Maustaste auf den Ordner **kafka_2.13-3.9.0** und dann auf **Neues Terminal im Ordner** klicken.

![Kafka](./images/kafka11.png)

Geben Sie diesen Befehl ein:

`bin/kafka-server-start.sh config/server.properties`

![Kafka](./images/kafka14.png)

Sie sehen dann Folgendes:

![Kafka](./images/kafka15.png)

Lassen Sie dieses Fenster geöffnet, während Sie diese Übungen durchlaufen!

## Kafka-Thema erstellen

Öffnen Sie ein **Terminal**-Fenster, indem Sie mit der rechten Maustaste auf den Ordner **kafka_2.13-3.9.0** klicken und auf **Neues Terminal im Ordner** klicken.

![Kafka](./images/kafka11.png)

Geben Sie diesen Befehl ein, um ein neues Kafka-Thema mit dem Namen **aepTest** zu erstellen. Dieses Thema wird in dieser Übung zum Testen verwendet.

`bin/kafka-topics.sh --create --topic aeptest --bootstrap-server localhost:9092`

Daraufhin wird eine Bestätigung angezeigt:

![Kafka](./images/kafka17a.png)

Geben Sie diesen Befehl ein, um ein neues Kafka-Thema mit dem Namen **aep“**. Dieser Artikel wird vom Adobe Experience Platform Sink Connector verwendet, den Sie in den nächsten Übungen konfigurieren werden.

`bin/kafka-topics.sh --create --topic aep --bootstrap-server localhost:9092`

Daraufhin wird eine ähnliche Bestätigung angezeigt:

![Kafka](./images/kafka17.png)

## Ereignisse erstellen

Wechseln Sie zurück zum Terminal-Fenster, in dem Sie Ihr erstes Kafka-Thema erstellt haben, und geben Sie den folgenden Befehl ein:

`bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic aeptest`

![Kafka](./images/kafka18.png)

Sie werden es dann sehen. Jede neue Zeile, gefolgt vom Drücken der Eingabetaste, führt dazu, dass eine neue Nachricht an das Thema (**) gesendet**.

![Kafka](./images/kafka19.png)

Geben Sie `Hello AEP` ein und drücken Sie die Eingabetaste. Ihre erste Veranstaltung wurde jetzt an Ihre lokale Kafka-Instanz zum Thema **aepTest** gesendet.

![Kafka](./images/kafka20.png)

Geben Sie `Hello AEP again.` ein und drücken Sie die Eingabetaste.

Geben Sie `AEP Data Collection is the best.` ein und drücken Sie die Eingabetaste.

Sie haben jetzt 3 Events zum Thema **aepTest** produziert. Diese Ereignisse können jetzt von einer Anwendung genutzt werden, die diese Daten möglicherweise benötigt.

![Kafka](./images/kafka21.png)

Klicken Sie auf Ihrer Tastatur gleichzeitig auf `Control` und `C`, um den Produzenten zu schließen.

![Kafka](./images/kafka22.png)

## Ereignisse verarbeiten

Geben Sie im selben Terminal-Fenster, in dem Sie Ereignisse generiert haben, den folgenden Befehl ein:

`bin/kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic aeptest --from-beginning`

Anschließend werden alle Nachrichten, die in der vorherigen Übung für das Thema &quot;**&quot; erstellt wurden** im Verbraucher angezeigt. So funktioniert Apache Kafka: Ein Produzent erstellt Ereignisse in einer Pipeline und ein Verbraucher nutzt diese Ereignisse.

![Kafka](./images/kafka23.png)

Klicken Sie auf Ihrer Tastatur gleichzeitig auf `Control` und `C`, um den Produzenten zu schließen.

![Kafka](./images/kafka24.png)

In dieser Übung haben Sie alle Grundlagen zum Einrichten eines lokalen Kafka-Clusters, zum Erstellen eines Kafka-Themas, zum Erstellen von Ereignissen und zum Konsumieren von Ereignissen durchlaufen.

Ziel dieses Moduls ist es, zu simulieren, was passieren würde, wenn ein echtes Unternehmen bereits einen Apache Kafka-Cluster implementiert hat und Daten von seinem Kafka-Cluster in Adobe Experience Platform streamen möchte.

Um eine solche Implementierung zu erleichtern, wurde ein Adobe Experience Platform Sink Connector erstellt, der mit Kafka Connect implementiert werden kann. Die Dokumentation zu diesem Adobe Experience Platform Sink Connector finden Sie hier: [https://github.com/adobe/experience-platform-streaming-connect](https://github.com/adobe/experience-platform-streaming-connect).

In den nächsten Übungen implementieren Sie alles, was Sie zur Verwendung dieses Adobe Experience Platform Sink Connectors benötigen, aus Ihrem eigenen lokalen Kafka-Cluster.

Schließen Sie das Terminal-Fenster.

Du hast diese Übung beendet.

Nächster Schritt: [2.6.3 HTTP-API-Endpunkt in Adobe Experience Platform konfigurieren](./ex3.md)

[Zurück zum Modul 2.6](./aep-apache-kafka.md)

[Zurück zu „Alle Module“](../../../overview.md)
