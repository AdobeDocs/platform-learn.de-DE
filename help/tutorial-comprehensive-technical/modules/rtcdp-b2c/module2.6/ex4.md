---
title: Installieren und Konfigurieren von Kafka Connect und Adobe Experience Platform Sink Connector
description: Installieren und Konfigurieren von Kafka Connect und Adobe Experience Platform Sink Connector
kt: 5342
doc-type: tutorial
exl-id: 93ded4f9-0179-4186-9601-52f479350075
source-git-commit: 6485bfa1c75c43bb569f77c478a273ace24a61d4
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---

# 2.6.4 Installieren und Konfigurieren von Kafka Connect und Adobe Experience Platform Sink Connector

## Adobe Experience Platform Sink Connector herunterladen

Rufen Sie [https://github.com/adobe/experience-platform-streaming-connect/releases](https://github.com/adobe/experience-platform-streaming-connect/releases) auf und laden Sie die neueste offizielle Version des Adobe Experience Platform Sink Connectors herunter.

![Kafka](./images/kc1.png)

Laden Sie die Datei **streaming-connect-sink-0.0.27-java-11.jar** herunter.

![Kafka](./images/kc1a.png)

Platzieren Sie die Download-Datei **streaming-connect-sink-0.0.27-java-11.jar** auf Ihren Desktop.

![Kafka](./images/kc2.png)

## Konfigurieren von Kafka Connect

Wechseln Sie zum Ordner auf Ihrem Desktop mit dem Namen **Kafka_AEP** und navigieren Sie zum Ordner `kafka_2.13-3.9.0/config`.
Öffnen Sie in diesem Ordner die Datei **connect-distributed.properties** mit einem beliebigen Texteditor.

![Kafka](./images/kc3a.png)

Navigieren Sie in Ihrem Texteditor zu den Zeilen 34 und 35 und stellen Sie sicher, dass Sie die Felder `key.converter.schemas.enable` und `value.converter.schemas.enable` auf `false` setzen.

```json
key.converter.schemas.enable=false
value.converter.schemas.enable=false
```

Speichern Sie Ihre Änderungen in dieser Datei.

![Kafka](./images/kc3.png)

Gehen Sie anschließend zurück zum Ordner &quot;`kafka_2.13-3.1.0`&quot;, erstellen Sie manuell einen neuen Ordner und nennen Sie ihn &quot;`connectors`&quot;.

![Kafka](./images/kc4.png)

Klicken Sie mit der rechten Maustaste auf den neuen Ordner und klicken Sie auf **Neues Terminal im Ordner**.

![Kafka](./images/kc5.png)

Dann wirst du das sehen. Geben Sie den Befehl `pwd` ein, um den vollständigen Pfad für diesen Ordner abzurufen. Wählen Sie den vollständigen Pfad aus und kopieren Sie ihn in die Zwischenablage.

![Kafka](./images/kc6.png)

Gehen Sie zurück zum Texteditor, wechseln Sie zur Datei **connect-distributed.properties** und scrollen Sie zur letzten Zeile herunter (Zeile 89 im Screenshot). Sie sollten den Kommentar für die mit `# plugin.path=` beginnende Zeile aufheben (entfernen Sie `#`) und den vollständigen Pfad zum Ordner `connectors` einfügen. Das Ergebnis sollte in etwa wie folgt aussehen:

`plugin.path=/Users/woutervangeluwe/Desktop/Kafka_AEP/kafka_2.13-3.9.0/connectors`

Speichern Sie Ihre Änderungen in der Datei **connect-distribution.properties** und schließen Sie den Texteditor.

![Kafka](./images/kc7.png)

Kopieren Sie als Nächstes die neueste offizielle Version des Adobe Experience Platform Sink Connectors, die Sie in den Ordner `connectors` heruntergeladen haben. Die zuvor heruntergeladene Datei heißt **streaming-connect-sink-0.0.27-java-11.jar**, Sie können sie einfach in den Ordner `connectors` verschieben.

![Kafka](./images/kc8.png)

Als Nächstes öffnen Sie ein neues Terminal-Fenster auf der Ebene des Ordners **kafka_2.13-3.9.0** . Klicken Sie mit der rechten Maustaste auf diesen Ordner und klicken Sie auf **Neues Terminal im Ordner**.

Fügen Sie im Terminal-Fenster den folgenden Befehl ein: `bin/connect-distributed.sh config/connect-distributed.properties` und klicken Sie auf **Enter**. Mit diesem Befehl wird Kafka Connect gestartet und die Bibliothek des Adobe Experience Platform Sink Connectors geladen.

![Kafka](./images/kc9.png)

Nach ein paar Sekunden sehen Sie etwas wie Folgendes:

![Kafka](./images/kc10.png)

## Erstellen Ihres Adobe Experience Platform Sink-Connectors mit Postman

Sie können jetzt mit Kafka Connect über Postman interagieren. Laden Sie dazu [diese Postman-Sammlung](./../../../assets/postman/postman_kafka.zip) herunter und entpacken Sie sie auf Ihren lokalen Computer auf dem Desktop. Sie verfügen dann über eine Datei mit dem Namen `Kafka_AEP.postman_collection.json`.

![Kafka](./images/kc11a.png)

Sie müssen diese Datei in Postman importieren. Öffnen Sie dazu Postman, klicken Sie auf **Importieren**, ziehen Sie die Datei `Kafka_AEP.postman_collection.json` per Drag-and-Drop in das Popup-Fenster und klicken Sie auf **Importieren**.

![Kafka](./images/kc11b.png)

Diese Kollektion finden Sie dann im linken Menü von Postman. Klicken Sie auf die erste Anforderung, **GET Verfügbare Kafka Connect-Connectoren** , um sie zu öffnen.

![Kafka](./images/kc11c.png)

Dann wirst du das sehen. Klicken Sie auf die blaue Schaltfläche **Senden**, nach der eine leere Antwort `[]` angezeigt werden soll. Die leere Antwort ist darauf zurückzuführen, dass derzeit keine Kafka Connect-Connectoren definiert sind.

![Kafka](./images/kc11.png)

Um einen Connector zu erstellen, klicken Sie auf die zweite Anforderung in der Kafka-Sammlung, **POST AEP Sink Connector erstellen** und gehen Sie zu **Hauptteil**. Dann wirst du das sehen. In Zeile 11, wo es &quot;**&quot;aep.endpoint&quot;: &quot;&quot;**&quot;heißt, müssen Sie die URL des HTTP-API-Streaming-Endpunkts einfügen, die Sie am Ende einer der vorherigen Übungen erhalten haben. Die URL des HTTP-API-Streaming-Endpunkts sieht wie folgt aus: `https://dcs.adobedc.net/collection/63751d0f299eeb7aa48a2f22acb284ed64de575f8640986d8e5a935741be9067`.

![Kafka](./images/kc12a.png)

Nach dem Einfügen sollte der Hauptteil Ihrer Anforderung wie folgt aussehen: Klicken Sie auf die blaue Schaltfläche **Senden** , um Ihren Connector zu erstellen. Sie erhalten eine sofortige Antwort von der Erstellung Ihres Connectors.

![Kafka](./images/kc12.png)

Klicken Sie auf die erste Anforderung, **GET Verfügbare Kafka Connect-Connectoren** , um sie erneut zu öffnen, und klicken Sie erneut auf die blaue Schaltfläche **Senden** . Sie werden sehen, dass ein Kafka Connect-Connector vorhanden ist.

![Kafka](./images/kc13.png)

Öffnen Sie als Nächstes die dritte Anforderung in der Kafka-Sammlung, **GET Überprüfen Sie den Kafka Connect-Connector-Status**. Klicken Sie auf die blaue Schaltfläche **Senden** . Daraufhin erhalten Sie eine Antwort wie die unten stehende, in der erklärt wird, dass der Connector ausgeführt wird.

![Kafka](./images/kc14.png)

## Erstellen eines Erlebnisereignisses

Öffnen Sie ein neues Fenster **Terminal** , indem Sie mit der rechten Maustaste auf den Ordner **kafka_2.13-3.9.0** klicken und auf **Neues Terminal im Ordner** klicken.

![Kafka](./images/kafka11.png)

Geben Sie den folgenden Befehl ein:

`bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic aep`

Dann wirst du das sehen. Jede neue Zeile, gefolgt von der Schaltfläche &quot;Enter&quot;, führt dazu, dass eine neue Nachricht an das Thema **aep** gesendet wird.

![Kafka](./images/kc16.png)

Jetzt können Sie eine Nachricht senden, die vom Adobe Experience Platform Sink Connector genutzt wird und in Echtzeit in Adobe Experience Platform aufgenommen wird.

Nehmen Sie die folgende Beispielnutzlast für Erlebnisereignisse und kopieren Sie sie in einen Texteditor.

```json
{
  "header": {
    "datasetId": "61fe23fd242870194a6d779c",
    "imsOrgId": "--aepImsOrgID--",
    "source": {
      "name": "Launch"
    },
    "schemaRef": {
      "id": "https://ns.adobe.com/experienceplatform/schemas/b0190276c6e1e1e99cf56c99f4c07a6e517bf02091dcec90",
      "contentType": "application/vnd.adobe.xed-full+json;version=1"
    }
  },
  "body": {
    "xdmMeta": {
      "schemaRef": {
        "id": "https://ns.adobe.com/experienceplatform/schemas/b0190276c6e1e1e99cf56c99f4c07a6e517bf02091dcec90",
        "contentType": "application/vnd.adobe.xed-full+json;version=1"
      }
    },
    "xdmEntity": {
      "eventType": "callCenterInteractionKafka",
      "_id": "",
      "timestamp": "2024-11-25T09:54:12.232Z",
      "_experienceplatform": {
        "identification": {
          "core": {
            "phoneNumber": ""
          }
        },
        "interactionDetails": {
          "core": {
            "callCenterAgent": {
              "callID": "Support Contact - 3767767",
              "callTopic": "contract",
              "callFeeling": "negative"
            }
          }
        }
      }
    }
  }
}
```

Dann wirst du das sehen. Sie müssen zwei Felder manuell aktualisieren:

- **_id**: Setzen Sie es auf eine zufällige ID, etwa `--aepUserLdap--1234`
- **timestamp**: Aktualisieren Sie den Zeitstempel auf das aktuelle Datum und die aktuelle Uhrzeit
- **phoneNumber**: Geben Sie die phoneNumber des Kontos ein, das zuvor auf der Demowebsite erstellt wurde. Sie finden sie im Bedienfeld &quot;Profil-Viewer&quot;unter **Identitäten**.

Sie müssen auch diese Felder überprüfen und gegebenenfalls aktualisieren:

- **datasetId**: Sie müssen die Datensatz-ID für das Datensatz-Demo-System - Ereignis-Datensatz für Callcenter (Global v1.1) kopieren.

![Kafka](./images/kc20ds.png)

- **imsOrgID**: Ihre IMS-Organisations-ID ist `--aepImsOrgId--`

>[!NOTE]
>
>Das Feld **_id** muss für jede Datenerfassung eindeutig sein. Wenn Sie mehrere Ereignisse erzeugen, stellen Sie sicher, dass Sie das Feld **_id** jedes Mal auf einen neuen eindeutigen Wert aktualisieren.

Sie sollten dann etwas wie Folgendes haben:

![Kafka](./images/kc21.png)

Kopieren Sie dann Ihr gesamtes Erlebnisereignis in die Zwischenablage. Der Leerraum Ihrer JSON-Payload muss entfernt werden. Dazu verwenden wir ein Online-Tool. Wechseln Sie dazu zu [http://jsonviewer.stack.hu/](http://jsonviewer.stack.hu/) .

Fügen Sie Ihr Erlebnisereignis in den Editor ein und klicken Sie auf **Leerraum entfernen**.

![Kafka](./images/kc22a.png)

Wählen Sie anschließend den gesamten Ausgabetext aus und kopieren Sie ihn in die Zwischenablage.

![Kafka](./images/kc23.png)

Kehren Sie zu Ihrem Terminal-Fenster zurück.

![Kafka](./images/kc16.png)

Fügen Sie die neue Payload ohne Leerzeichen in das Terminal-Fenster ein und klicken Sie auf **Enter**.

![Kafka](./images/kc23a.png)

Gehen Sie anschließend zurück zu Ihrer Demo-Website und aktualisieren Sie die Seite. Sie sollten jetzt ein Erlebnisereignis in Ihrem Profil unter **Erlebnisereignisse** sehen, genau wie im Folgenden:

![Kafka](./images/kc24.png)

>[!NOTE]
>
>Wenn Ihre Callcenter-Interaktionen im Profil-Viewer-Bedienfeld angezeigt werden sollen, müssen Sie die folgende Beschriftung hinzufügen und in Ihrem Projekt unter [https://dsn.adobe.com](https://dsn.adobe.com) filtern, indem Sie zur Registerkarte **Profil-Viewer** navigieren und unter **Ereignisse** eine neue Zeile mit den folgenden Variablen hinzufügen:
>- **Bezeichnung des Ereignistyps**: Interaktionen im Callcenter
>- **Ereignistyp-Filter**: callCenterInteractionKafka
>- **Titel**: `--aepTenantId--.interactionDetails.core.callCenterAgent.callID`

![Kafka](./images/kc25.png)

Du hast diese Übung beendet.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 2.6](./aep-apache-kafka.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
