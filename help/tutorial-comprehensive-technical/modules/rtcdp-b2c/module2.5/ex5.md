---
title: Datenerfassung und Ereignisweiterleitung - Weiterleiten von Ereignissen an das AWS-Ökosystem
description: Weiterleiten von Ereignissen an das AWS-Ökosystem
kt: 5342
doc-type: tutorial
exl-id: 87c2c85d-f624-4972-a9c6-32ddf8a39570
source-git-commit: 7779e249b4ca03c243cf522811cd81370002d51a
workflow-type: tm+mt
source-wordcount: '1566'
ht-degree: 3%

---

# 2.5.5 Weiterleiten von Ereignissen an AWS Kinesis und AWS S3

>[!IMPORTANT]
>
>Der Abschluss dieser Übung ist optional und erfordert die Nutzung von AWS Kinesis Kosten. AWS bietet ein Konto der freien Ebene, mit dem Sie viele Dienste ohne Kosten testen und konfigurieren können. AWS Kinesis ist jedoch nicht Teil dieses Kontos der freien Ebene. Um diese Übung zu implementieren und zu testen, sind also Kosten für die Nutzung von AWS Kinesis erforderlich.

## Gut zu wissen

Adobe Experience Platform unterstützt verschiedene Amazon-Dienste als Ziel.
Kinesis und S3 sind beide [Profilexportziele](https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=en) und können als Teil von Adobe Experience Platforms Real-Time CDP verwendet werden.
Sie können einfach hochwertige Segmentereignisse und zugehörige Profilattribute in Ihre Systeme Ihrer Wahl einspeisen.

In dieser Übung erfahren Sie, wie Sie Ihren eigenen Amazon Kinesis-Stream einrichten, um Ereignisdaten aus dem Adobe Experience Platform Edge-Ökosystem an ein Cloud-Speicher-Ziel wie Amazon S3 zu streamen. Dies ist nützlich, wenn Sie Erlebnisereignisse aus Web- und mobilen Eigenschaften erfassen und zur Analyse und operativen Berichterstellung in Ihren Datensatz übertragen möchten. Datalakes erfassen Daten in der Regel im Batch-Modus mit großen täglichen Dateiimporten. Sie stellen keinen öffentlichen HTTP-Endpunkt bereit, der in Verbindung mit der Ereignisweiterleitung verwendet werden könnte.

Wenn Sie die oben genannten Anwendungsfälle unterstützen, müssen gestreamte Daten gepuffert oder in eine Warteschlange gestellt werden, bevor sie in eine Datei geschrieben werden. Es muss darauf geachtet werden, dass die Datei nicht für den Schreibzugriff über mehrere Prozesse hinweg geöffnet wird. Diese Aufgabe an ein dediziertes System zu delegieren ist ideal, um eine gute Skalierung zu erreichen und gleichzeitig ein hohes Serviceniveau zu gewährleisten. Hier kommt Kinesis zur Rettung.

Amazon Kinesis Data Streams konzentriert sich auf die Erfassung und Speicherung von Datenströmen. Kinesis Data Firewalls dienen der Bereitstellung von Datenströmen an ausgewählte Ziele, z. B. S3-Behälter.

Im Rahmen dieser Übung...

- Grundlegende Einrichtung eines Kinesis-Datenstreams durchführen
- Erstellen Sie einen Firewalls-Versand-Stream und verwenden Sie den S3-Behälter als Ziel.
- Konfigurieren des Amazon API-Gateways als REST-API-Endpunkt zum Empfangen Ihrer Ereignisdaten
- Weiterleiten von Rohereignisdaten von Adobe Edge an Ihren Kinesis-Stream

## Konfigurieren des AWS S3-Buckets

Wechseln Sie zu [https://console.aws.amazon.com](https://console.aws.amazon.com) und melden Sie sich mit Ihrem Amazon-Konto an.

![ETL](./../../../modules/rtcdp-b2c/module2.3/images/awshome.png)

Nach der Anmeldung werden Sie zur **AWS Management Console** weitergeleitet.

![ETL](./../../../modules/rtcdp-b2c/module2.3/images/awsconsole.png)

Suchen Sie im Menü **Dienste suchen** nach **s3**. Klicken Sie auf das erste Suchergebnis: **S3 - Skalierbarer Speicher in der Cloud**.

![ETL](./../../../modules/rtcdp-b2c/module2.3/images/awsconsoles3.png)

Dann sehen Sie die Homepage von **Amazon S3**. Klicken Sie auf **Behälter erstellen**.

![ETL](./../../../modules/rtcdp-b2c/module2.3/images/s3home.png)

Im Bildschirm **Behälter erstellen** müssen Sie zwei Elemente konfigurieren:

- Name: Verwenden Sie den Namen `eventforwarding---aepUserLdap--`.

![ETL](./images/bucketname.png)

Behalten Sie alle anderen Standardeinstellungen bei. Scrollen Sie nach unten und klicken Sie auf **Bucket erstellen**.

![ETL](./images/createbucket.png)

Sie werden sehen, wie Ihr Bucket erstellt wird und zur Amazon S3-Homepage weitergeleitet wird.

![ETL](./images/S3homeb.png)

## Konfigurieren des AWS Kinesis-Datenstreams

Suchen Sie im Menü **Dienste suchen** nach **Kinesis**. Klicken Sie auf das erste Suchergebnis: **Kinesis - Arbeiten mit Echtzeit-Streaming-Daten**.

![ETL](./images/kinesis1.png)

Wählen Sie **Kinesis Data Streams** aus. Klicken Sie auf **Datenstrom erstellen**.

![ETL](./images/kinesis2.png)

Verwenden Sie für den **Datenstrom-Namen** `--aepUserLdap---datastream`.

![ETL](./images/kinesis3.png)

Die anderen Einstellungen müssen nicht geändert werden. Scrollen Sie nach unten und klicken Sie auf **Datenstrom erstellen**.

![ETL](./images/kinesis4.png)

Dann wirst du das sehen. Sobald Ihr Datenstrom erfolgreich erstellt wurde, können Sie mit der nächsten Übung fortfahren.

![ETL](./images/kinesis5.png)

## Konfigurieren des AWS Firewalls-Bereitstellungs-Streams

Suchen Sie im Menü **Dienste suchen** nach **Kinesis**. Klicken Sie auf **Kinesis Data Firewalls**.

![ETL](./images/kinesis6.png)

Klicken Sie auf &quot;**Feuerlöschstrom erstellen**&quot;.

![ETL](./images/kinesis7.png)

Wählen Sie für **Source** die Option **Amazon Kinesis Data Streams**. Wählen Sie für **Ziel** **Amazon S3** aus. Klicken Sie auf **Durchsuchen** , um Ihren Daten-Stream auszuwählen.

![ETL](./images/kinesis8.png)

Wählen Sie Ihren Daten-Stream aus. Klicken Sie auf **Choose**.

![ETL](./images/kinesis9.png)

Dann wirst du das sehen. Denken Sie an den **Firehis stream name** , da Sie ihn später benötigen werden.

![ETL](./images/kinesis10.png)

Scrollen Sie nach unten, bis **Zieleinstellungen** angezeigt wird. Klicken Sie auf **Durchsuchen** , um Ihren S3-Behälter auszuwählen.

![ETL](./images/kinesis11.png)

Wählen Sie Ihren S3-Behälter aus und klicken Sie auf **Choose**.

![ETL](./images/kinesis12.png)

Dann wirst du so etwas sehen. Aktualisieren Sie die folgenden Einstellungen:

- Neues Trennzeichen: auf **Aktiviert** gesetzt
- Dynamische Partitionierung: auf **Nicht aktiviert** eingestellt

![ETL](./images/kinesis13.png)

Scrollen Sie noch ein wenig nach unten und klicken Sie auf **Feuerlöschstream erstellen**

![ETL](./images/kinesis15.png)

Nach einigen Minuten wird Ihr Fireschlauch-Stream erstellt und **aktiv**.

![ETL](./images/kinesis16.png)

## IAM-Benutzer erstellen

Klicken Sie im linken AWS IAM-Menü auf **Benutzer**. Daraufhin wird der Bildschirm **Benutzer** angezeigt. Klicken Sie auf **Benutzer erstellen**.

![ETL](./images/iammenu.png)

Konfigurieren Sie dann Ihren Benutzer:

- Benutzername: use `--aepUserLdap--_kinesis_forwarding`

Klicken Sie auf **Weiter**.

![ETL](./images/configuser.png)

Dann sehen Sie diesen Berechtigungsbildschirm. Klicken Sie auf **Richtlinien direkt anhängen**.

Geben Sie den Suchbegriff **kinesisfireschlauch** ein, um alle zugehörigen Richtlinien anzuzeigen. Wählen Sie die Richtlinie **AmazonKinesisFireschlauchFullAccess** aus. Scrollen Sie nach unten und klicken Sie auf **Weiter**.

![ETL](./images/perm2.png)

Überprüfen Sie Ihre Konfiguration. Klicken Sie auf **Benutzer erstellen**.

![ETL](./images/review.png)

Dann wirst du das sehen. Klicken Sie auf **Benutzer anzeigen**.

![ETL](./images/review1.png)

Klicken Sie auf **Berechtigungen hinzufügen** und klicken Sie auf **Inline-Richtlinie erstellen**.

![ETL](./images/pol1.png)

Dann wirst du das sehen. Wählen Sie den Dienst **Kinesis** aus.

![ETL](./images/pol2.png)

Wechseln Sie zu **Schreiben** und aktivieren Sie das Kontrollkästchen für **PutRecord**.

![ETL](./images/pol3.png)

Scrollen Sie nach unten zu **Ressourcen** und wählen Sie **Alle** aus. Klicken Sie auf **Weiter**.

![ETL](./images/pol4.png)

Nennen Sie Ihre Richtlinie wie folgt: **Kinesis_PutRecord** und klicken Sie auf **Richtlinie erstellen**.

![ETL](./images/pol5.png)

Dann wirst du das sehen. Klicken Sie auf **Sicherheitsberechtigungen**.

![ETL](./images/pol6.png)

Klicken Sie auf **Zugriffsschlüssel erstellen**.

![ETL](./images/cred.png)

Wählen Sie **Anwendung, die außerhalb von AWS ausgeführt wird**. Scrollen Sie nach unten und klicken Sie auf **Weiter**.

![ETL](./images/creda.png)

Klicken Sie auf **Zugriffsschlüssel erstellen**

![ETL](./images/credb.png)

Dann wirst du das sehen. Klicken Sie auf **Anzeigen** , um Ihren geheimen Zugriffsschlüssel anzuzeigen:

![ETL](./images/cred1.png)

Ihr **geheimer Zugriffsschlüssel** wird jetzt angezeigt.

>[!IMPORTANT]
>
>Speichern Sie Ihre Anmeldedaten in einer Textdatei auf Ihrem Computer.
>
> - Zugriffsschlüssel-ID: ...
> - Geheimer Zugriffsschlüssel: ...
>
> Wenn Sie auf **Fertig** klicken, werden Sie Ihre Anmeldedaten nie mehr sehen!

Klicken Sie auf **Fertig**.

![ETL](./images/cred2.png)

Sie haben jetzt erfolgreich einen IAM-Benutzer mit den entsprechenden Berechtigungen erstellt, die Sie beim Konfigurieren der AWS-Erweiterung in Ihrer Eigenschaft &quot;Event Forwarding&quot;angeben müssen.

## Eigenschaft für die Ereignisweiterleitung aktualisieren: Erweiterung

Wenn Ihr Geheimnis und Ihr Datenelement konfiguriert sind, können Sie jetzt die Erweiterung für die Google Cloud-Plattform in Ihrer Eigenschaft &quot;Ereignisweiterleitung&quot;einrichten.

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/), gehen Sie zu **Ereignisweiterleitung** und öffnen Sie Ihre Eigenschaft &quot;Ereignisweiterleitung&quot;.

![Adobe Experience Platform-Datenerfassung SSF](./images/prop1.png)

Navigieren Sie als Nächstes zu **Erweiterungen**, zu **Katalog**. Klicken Sie auf die Erweiterung **AWS** und dann auf **Installieren**.

![Adobe Experience Platform-Datenerfassung SSF](./images/awsext1.png)

Geben Sie die IAM-Benutzeranmeldeinformationen ein, die Sie in der vorherigen Übung generiert haben. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassung SSF](./images/awsext2.png)

Als Nächstes müssen Sie eine Regel konfigurieren, die die Weiterleitung von Ereignisdaten an Kinesis startet.

## Eigenschaft für die Ereignisweiterleitung aktualisieren: Regel

Gehen Sie im linken Menü zu **Regeln**. Klicken Sie auf , um die Regel **Alle Seiten** zu öffnen, die Sie in einer der vorherigen Übungen erstellt haben.

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws1.png)

Dann wirst du das sehen. Klicken Sie auf das Symbol **+** , um eine neue Aktion hinzuzufügen.

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws2.png)

Dann wirst du das sehen. Wählen Sie Folgendes aus:

- Wählen Sie die **Erweiterung**: **AWS**
- Wählen Sie den **Aktionstyp**: **Daten an Kinesis-Datenstream senden** aus.
- Name: **AWS - Senden von Daten an Kinesis Data Stream**

Sie sollten jetzt Folgendes sehen:

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws4.png)

Konfigurieren Sie als Nächstes Folgendes:

- Streamname: `--aepUserLdap---datastream`
- AWS-Region: Überprüfen Sie Ihre Region in Ihrer AWS-Datenstream-Einrichtung.
- Partition Key: **0**

Ihre AWS-Region finden Sie hier:

![Adobe Experience Platform-Datenerfassung SSF](./images/partkey.png)

Du solltest das jetzt haben. Klicken Sie anschließend auf das Datenelementsymbol für das Feld **Daten** .

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws5.png)

Wählen Sie **XDM Event** und klicken Sie auf **Select**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws5a.png)

Dann wirst du das haben. Klicken Sie auf **Änderungen beibehalten**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws5b.png)

Dann wirst du das sehen. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws7.png)

Wechseln Sie zu **Veröffentlichungsfluss** , um Ihre Änderungen zu veröffentlichen.
Öffnen Sie Ihre Entwicklungsbibliothek, indem Sie auf **Main** klicken.

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws11.png)

Klicken Sie auf die Schaltfläche **Alle geänderten Ressourcen hinzufügen** , nach der Ihre Regel- und Datenelementänderungen in dieser Bibliothek angezeigt werden. Klicken Sie anschließend auf **Speichern und für Entwicklung erstellen**. Ihre Änderungen werden jetzt bereitgestellt.

![Adobe Experience Platform-Datenerfassung SSF](./images/rlaws13.png)

Nach einigen Minuten werden Sie feststellen, dass die Implementierung abgeschlossen ist und getestet werden kann.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl14.png)

## Testen der Konfiguration

Wechseln Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf die drei Punkte **..** im Website-Projekt und dann auf **Ausführen** , um es zu öffnen.

![DSN](./../../datacollection/module1.1/images/web8.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../gettingstarted/gettingstarted/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../gettingstarted/gettingstarted/images/web7.png)

Wechseln Sie Ihre Ansicht zu **AWS**. Wenn Sie Ihren Datenstrom öffnen und auf die Registerkarte **Überwachung** wechseln, wird nun der eingehende Traffic angezeigt.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hookaws3.png)

Wenn Sie dann Ihren Data Fireham-Stream öffnen und auf die Registerkarte **Überwachung** wechseln, wird auch der eingehende Traffic angezeigt.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hookaws4.png)

Wenn Sie sich schließlich Ihren S3-Bucket ansehen, werden Sie feststellen, dass dort Dateien infolge Ihrer Datenerfassung erstellt werden.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hookaws5.png)

Wenn Sie eine solche Datei herunterladen und sie mit einem Texteditor öffnen, sehen Sie, dass sie die XDM-Payload aus den weitergeleiteten Ereignissen enthält.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hookaws6.png)

>[!IMPORTANT]
>
>Nachdem Ihr Setup erwartungsgemäß funktioniert hat, sollten Sie Ihren AWS Kinesis Data Stream und Data Firewalls umschalten, um zu vermeiden, dass Gebühren erhoben werden!

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 2.5](./aep-data-collection-ssf.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
