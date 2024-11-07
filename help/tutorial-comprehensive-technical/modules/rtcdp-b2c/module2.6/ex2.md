---
title: Kafka-Cluster installieren und konfigurieren
description: Kafka-Cluster installieren und konfigurieren
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: adffeead-9bcb-4632-9a2c-c6da1c40b7f2
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 0%

---

# 2.6.2 Kafka-Cluster installieren und konfigurieren

## 2.6.2.1 Apache Kafka herunterladen

Navigieren Sie zu [https://kafka.apache.org/downloads](https://kafka.apache.org/downloads) und laden Sie die neueste veröffentlichte Version herunter. Wählen Sie die neueste Binärversion aus, in diesem Fall **Scala 2.13**.

![Kafka](./images/kafka1.png)

Sie werden dann zu einer Mirrorseite geführt. Klicken Sie auf den Link zum Herunterladen von Kafka.

![Kafka](./images/kafka2.png)

Erstellen Sie auf Ihrem Desktop einen Ordner mit dem Namen **Kafka_AEP** und legen Sie die heruntergeladene Datei in diesem Verzeichnis ab.

![Kafka](./images/kafka3.png)

Öffnen Sie ein Fenster **Terminal** , indem Sie mit der rechten Maustaste auf Ihren Ordner klicken und auf **Neues Terminal im Ordner** klicken.

![Kafka](./images/kafka4.png)

Führen Sie diesen Befehl in Ihrem Terminal-Fenster aus, um die heruntergeladene Datei zu entpacken:

`tar -xvf kafka_2.13-3.1.0.tgz`

>[!NOTE]
>
>Überprüfen Sie, ob der obige Befehl mit der Version der heruntergeladenen Datei übereinstimmt. Wenn Ihre Version aktueller ist, müssen Sie den obigen Befehl entsprechend dieser Version aktualisieren.

![Kafka](./images/kafka5.png)

Daraufhin sehen Sie Folgendes:

![Kafka](./images/kafka6.png)

Nach dem Dekomprimieren dieser Datei haben Sie nun ein Verzeichnis wie dieses:

![Kafka](./images/kafka7.png)

Und in diesem Verzeichnis sehen Sie diese Unterverzeichnisse:

![Kafka](./images/kafka8.png)

Kehren Sie zu Ihrem Terminal-Fenster zurück. Geben Sie den folgenden Befehl ein:

`cd kafka_2.13-3.1.0`

>[!NOTE]
>
>Überprüfen Sie, ob der obige Befehl mit der Version der heruntergeladenen Datei übereinstimmt. Wenn Ihre Version aktueller ist, müssen Sie den obigen Befehl entsprechend dieser Version aktualisieren.

![Kafka](./images/kafka9.png)

Geben Sie als Nächstes den Befehl `bin/kafka-topics.sh` ein.

![Kafka](./images/kafka10a.png)

Sie sollten dann diese Antwort sehen. Dies bedeutet, dass Kafka ordnungsgemäß installiert ist und dass Java gut funktioniert. (Erinnerung: Sie benötigen Java 8 JDK oder Java 11 JDK installiert, damit dies funktioniert! Mit dem Befehl `java -version` können Sie sehen, welche Java-Version Sie installiert haben.)

![Kafka](./images/kafka10.png)

## 2.6.2.2 Kafka starten

Um Kafka zu starten, müssen Sie Kafka Zookeeper und Kafka in dieser Reihenfolge starten.

Öffnen Sie ein Fenster **Terminal** , indem Sie mit der rechten Maustaste auf den Ordner **kafka_2.13-3.1.0** klicken und auf **Neues Terminal im Ordner** klicken.

![Kafka](./images/kafka11.png)

Geben Sie diesen Befehl ein:

`bin/zookeeper-server-start.sh config/zookeeper.properties`

![Kafka](./images/kafka12.png)

Daraufhin sehen Sie Folgendes:

![Kafka](./images/kafka13.png)

Lassen Sie dieses Fenster offen, während Sie durch diese Übungen gehen!

Öffnen Sie ein weiteres, neues Fenster **Terminal** , indem Sie mit der rechten Maustaste auf Ihren Ordner **kafka_2.13-3.1.0** klicken und auf **Neues Terminal im Ordner** klicken.

![Kafka](./images/kafka11.png)

Geben Sie diesen Befehl ein:

`bin/kafka-server-start.sh config/server.properties`

![Kafka](./images/kafka14.png)

Daraufhin sehen Sie Folgendes:

![Kafka](./images/kafka15.png)

Lassen Sie dieses Fenster offen, während Sie durch diese Übungen gehen!

## 2.6.2.3 Kafka-Thema erstellen

Öffnen Sie ein Fenster **Terminal** , indem Sie mit der rechten Maustaste auf den Ordner **kafka_2.13-3.1.0** klicken und auf **Neues Terminal im Ordner** klicken.

![Kafka](./images/kafka11.png)

Geben Sie diesen Befehl ein, um ein neues Kafka-Thema mit dem Namen **apest** zu erstellen. Dieses Thema wird für Tests in dieser Übung verwendet.

`bin/kafka-topics.sh --create --topic aeptest --bootstrap-server localhost:9092`

![Kafka](./images/kafka16a.png)

Daraufhin wird eine ähnliche Bestätigung angezeigt:

![Kafka](./images/kafka17a.png)

Geben Sie diesen Befehl ein, um ein neues Kafka-Thema mit dem Namen **aep** zu erstellen. Dieses Thema wird vom Adobe Experience Platform Sink Connector verwendet, den Sie in den nächsten Übungen konfigurieren werden.

`bin/kafka-topics.sh --create --topic aep --bootstrap-server localhost:9092`

![Kafka](./images/kafka16.png)

Daraufhin wird eine ähnliche Bestätigung angezeigt:

![Kafka](./images/kafka17.png)

## 2.6.2.4 Ereignisse produzieren

Gehen Sie zurück zum Terminal-Fenster, in dem Sie Ihr erstes Kafka-Thema erstellt haben, und geben Sie den folgenden Befehl ein:

`bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic aeptest`

![Kafka](./images/kafka18.png)

Dann wirst du das sehen. Jede neue Zeile, gefolgt von dem Drücken der Schaltfläche &quot;Enter&quot;, führt dazu, dass eine neue Nachricht an das Thema **Akzeptest** gesendet wird.

![Kafka](./images/kafka19.png)

Geben Sie `Hello AEP` ein und drücken Sie die Eingabetaste. Ihr erstes Ereignis wurde jetzt an Ihre lokale Kafka-Instanz gesendet, in das Thema **Akzeptest**.

![Kafka](./images/kafka20.png)

Geben Sie `Hello AEP again.` ein und drücken Sie die Eingabetaste.

Geben Sie `AEP Data Collection is the best.` ein und drücken Sie die Eingabetaste.

Sie haben nun 3 Ereignisse zum Thema **Akzeptest** erstellt. Diese Ereignisse können jetzt von einer Anwendung genutzt werden, die diese Daten möglicherweise benötigt.

![Kafka](./images/kafka21.png)

Klicken Sie auf Ihrer Tastatur gleichzeitig auf `Control` und `C` , um Ihren Produzenten zu schließen.

![Kafka](./images/kafka22.png)

## 2.6.2.4 Verbrauchsereignisse

Geben Sie im selben Terminal-Fenster, das Sie zum Erstellen von Ereignissen verwendet haben, den folgenden Befehl ein:

`bin/kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic aeptest --from-beginning`

Anschließend werden alle Meldungen, die in der vorherigen Übung für das Thema **Akzeptanz** erstellt wurden, im Verbraucher angezeigt. So funktioniert Apache Kafka: Ein Hersteller erstellt Ereignisse in einer Pipeline, und ein Verbraucher verbraucht diese Ereignisse.

![Kafka](./images/kafka23.png)

Klicken Sie auf Ihrer Tastatur gleichzeitig auf `Control` und `C` , um Ihren Produzenten zu schließen.

![Kafka](./images/kafka24.png)

In dieser Übung haben Sie alle Grundlagen durchlaufen, um einen lokalen Kafka-Cluster einzurichten, ein Kafka-Thema zu erstellen, Ereignisse zu produzieren und Ereignisse zu nutzen.

Ziel dieses Moduls ist es zu simulieren, was passieren würde, wenn eine echte Organisation bereits einen Apache Kafka-Cluster implementiert hat und Daten aus ihrem Kafka-Cluster in Adobe Experience Platform streamen möchte.

Um eine solche Implementierung zu erleichtern, wurde ein Adobe Experience Platform Sink Connector erstellt, der mithilfe von Kafka Connect implementiert werden kann. Die Dokumentation zu diesem Adobe Experience Platform Sink Connector finden Sie hier: [https://github.com/adobe/experience-platform-streaming-connect](https://github.com/adobe/experience-platform-streaming-connect).

In den nächsten Übungen implementieren Sie alles, was Sie für die Verwendung dieses Adobe Experience Platform Sink-Connectors benötigen, aus Ihrem eigenen lokalen Kafka-Cluster.

Schließen Sie Ihr Terminal-Fenster.

Du hast diese Übung beendet.

Nächster Schritt: [2.6.3 HTTP-API-Endpunkt in Adobe Experience Platform konfigurieren](./ex3.md)

[Zurück zu Modul 2.6](./aep-apache-kafka.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
