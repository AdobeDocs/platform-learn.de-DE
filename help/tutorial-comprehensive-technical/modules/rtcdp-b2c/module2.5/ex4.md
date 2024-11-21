---
title: Datenerfassung und serverseitige Weiterleitung in Echtzeit - Erstellen und Konfigurieren einer Google Cloud-Funktion
description: Erstellen und Konfigurieren einer Google Cloud-Funktion
kt: 5342
doc-type: tutorial
exl-id: ee73ce3a-baaa-432a-9626-249be9aaeff2
source-git-commit: 7779e249b4ca03c243cf522811cd81370002d51a
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 1%

---

# 2.5.4 Ereignisse an GCP-Pub/Sub weiterleiten

>[!NOTE]
>
>Für diese Übung benötigen Sie Zugriff auf eine Google Cloud Platform-Umgebung. Wenn Sie noch keinen Zugriff auf GCP haben, erstellen Sie ein neues Konto mit Ihrer persönlichen E-Mail-Adresse.

## Google Cloud-Pub/Unterthema erstellen

Wechseln Sie zu [https://console.cloud.google.com/](https://console.cloud.google.com/). Geben Sie in der Suchleiste `pub/sub` ein. Klicken Sie auf das Suchergebnis **Pub/Sub - Globales Echtzeit-Messaging**.

![GCP](./images/gcp1.png)

Dann wirst du das sehen. Klicken Sie auf **THEMA ERSTELLEN**.

![GCP](./images/gcp2.png)

Dann wirst du das sehen. Verwenden Sie für Ihre Themen-ID `--aepUserLdap---event-forwarding`. Klicken Sie auf **Erstellen**.

![GCP](./images/gcp6.png)

Ihr Thema wird jetzt erstellt. Klicken Sie auf die **Abonnement-ID** des Themas.

![GCP](./images/gcp7.png)

Dann wirst du das sehen. Kopieren Sie den **Themennamen** in die Zwischenablage und speichern Sie ihn, wie Sie ihn in den nächsten Übungen benötigen.

![GCP](./images/gcp8.png)

Gehen wir jetzt zur Adobe Experience Platform-Ereignisweiterleitung für die Datenerfassung, um Ihre Eigenschaft für die Ereignisweiterleitung zu aktualisieren und Ereignisse an das Pub/Sub-Programm weiterzuleiten.


## Aktualisieren Sie Ihre Ereignisweiterleitungseigenschaft: Geheimnisse

**Geheimnisse** in den Eigenschaften für die Ereignisweiterleitung werden verwendet, um Anmeldeinformationen zu speichern, die für die Authentifizierung bei externen APIs verwendet werden. In diesem Beispiel müssen Sie ein Geheimnis konfigurieren, um Ihr OAuth-Token für die Google Cloud-Plattform zu speichern, das zur Authentifizierung bei der Verwendung von Pub/Sub zum Streamen von Daten an GCP verwendet wird.

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/) und gehen Sie zu **Geheimnisse**. Klicken Sie auf **Neues Geheimnis erstellen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/secret1.png)

Dann wirst du das sehen. Befolgen Sie diese Anweisungen:

- Name: use `--aepUserLdap---gcp-secret`
- Zielumgebung: Wählen Sie **Entwicklung** aus.
- Typ: **Google OAuth 2**
- Aktivieren Sie das Kontrollkästchen für **Pub/Sub**

Klicken Sie auf **Geheimnis erstellen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/secret2.png)

Nachdem Sie auf **Geheimnis erstellen** geklickt haben, wird ein Popup angezeigt, in dem Sie die Authentifizierung zwischen dem Geheimnis der Ereignisweiterleitungseigenschaft und Google einrichten können. Klicken Sie auf **Geheimnis erstellen und autorisieren `--aepUserLdap---gcp-secret` mit Google**.

![Adobe Experience Platform-Datenerfassung SSF](./images/secret3.png)

Klicken Sie auf , um Ihr Google-Konto auszuwählen.

![Adobe Experience Platform-Datenerfassung SSF](./images/secret4.png)

Klicken Sie auf **Weiter**.

>[!NOTE]
>
>Ihre Popup-Nachricht kann variieren. Bitte genehmigen/erlauben Sie den beantragten Zugriff, um die Übung fortzusetzen.

![Adobe Experience Platform-Datenerfassung SSF](./images/secret5.png)

Nach erfolgreicher Authentifizierung wird dies angezeigt.

![Adobe Experience Platform-Datenerfassung SSF](./images/secret6.png)

Ihr Geheimnis wurde jetzt erfolgreich konfiguriert und kann in einem Datenelement verwendet werden.

## Eigenschaft für die Ereignisweiterleitung aktualisieren: Datenelement

Um Ihr Geheimnis in Ihrer Ereignisweiterleitungseigenschaft zu verwenden, müssen Sie ein Datenelement erstellen, das den Wert des Geheimnisses speichert.

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/) und gehen Sie zu **Ereignisweiterleitung**. Suchen Sie die Eigenschaft &quot;Ereignisweiterleitung&quot;und klicken Sie darauf, um sie zu öffnen.

![Adobe Experience Platform-Datenerfassung SSF](./images/prop1.png)

Gehen Sie im linken Menü zu **Datenelemente**. Klicken Sie auf **Datenelement hinzufügen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/de1gcp.png)

Konfigurieren Sie Ihr Datenelement wie folgt:

- Name: **GCP Secret**
- Erweiterung: **Core**
- Datenelementtyp: **geheim**
- Entwicklungs-Geheimnis: Wählen Sie das erstellte Geheimnis mit dem Namen `--aepUserLdap---gcp-secret` aus.

Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassung SSF](./images/secret7.png)

## Eigenschaft für die Ereignisweiterleitung aktualisieren: Erweiterung

Wenn Ihr Geheimnis und Ihr Datenelement konfiguriert sind, können Sie jetzt die Erweiterung für die Google Cloud-Plattform in Ihrer Eigenschaft &quot;Ereignisweiterleitung&quot;einrichten.

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/), gehen Sie zu **Ereignisweiterleitung** und öffnen Sie Ihre Eigenschaft &quot;Ereignisweiterleitung&quot;.

![Adobe Experience Platform-Datenerfassung SSF](./images/prop1.png)

Navigieren Sie als Nächstes zu **Erweiterungen**, zu **Katalog**. Klicken Sie auf die Erweiterung **Google Cloud Platform** und dann auf **Installieren**.

![Adobe Experience Platform-Datenerfassung SSF](./images/gext2.png)

Dann wirst du das sehen. Klicken Sie auf das Symbol Datenelement .

![Adobe Experience Platform-Datenerfassung SSF](./images/gext3.png)

Wählen Sie das Datenelement aus, das Sie in der vorherigen Übung erstellt haben und den Namen **GCP-Geheimnis** trägt. Klicken Sie auf **Auswählen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/gext4.png)

Dann wirst du das sehen. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassung SSF](./images/gext5.png)

## Aktualisieren der Ereignisweiterleitungseigenschaft: Aktualisieren einer Regel

Nachdem Ihre Google Cloud Platform-Erweiterung konfiguriert wurde, können Sie eine Regel definieren, um die Weiterleitung von Ereignisdaten an Ihr Pub-/Unterthema zu starten. Dazu müssen Sie Ihre Regel **Alle Seiten** aktualisieren, die Sie in einer der vorherigen Übungen erstellt haben.

Gehen Sie im linken Menü zu **Regeln**. In der vorherigen Übung haben Sie die Regel **Alle Seiten** erstellt. Klicken Sie auf diese Regel, um sie zu öffnen.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl1gcp.png)

Dann wirst du das machen. Klicken Sie auf das Symbol **+** unter **Aktionen** , um eine neue Aktion hinzuzufügen.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl2gcp.png)

Dann wirst du das sehen. Wählen Sie Folgendes aus:

- Wählen Sie die Erweiterung **Extension**: **Google Cloud Platform** aus.
- Wählen Sie den **Aktionstyp**: **Daten an Cloud-Pub/Sub senden** aus.

Geben Sie den folgenden **Namen** ein: **Google Cloud-Plattform - Daten an Cloud-Pub/Sub senden**. Sie sollten jetzt Folgendes sehen:

![Adobe Experience Platform-Datenerfassung SSF](./images/rl5gcp.png)

Jetzt müssen Sie das zuvor erstellte Pub-/Unterthema konfigurieren.

Den **Themennamen** finden Sie hier, kopieren Sie ihn.

![GCP](./images/gcp8.png)

Fügen Sie den **Themennamen** in Ihre Regelkonfiguration ein. Klicken Sie anschließend auf das Symbol Datenelement neben dem Feld **Daten (erforderlich)** .

![Adobe Experience Platform-Datenerfassung SSF](./images/rl6gcp.png)

Wählen Sie **XDM Event** und klicken Sie auf **Select**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl7gcp.png)

Dann wirst du das sehen. Klicken Sie auf **Änderungen beibehalten**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl8gcp.png)

Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl9gcp.png)

Dann wirst du das sehen.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl10gcp.png)

## Veröffentlichen der Änderungen

Ihre Konfiguration ist jetzt abgeschlossen. Wechseln Sie zu **Veröffentlichungsfluss** , um Ihre Änderungen zu veröffentlichen. Öffnen Sie Ihre Entwicklungsbibliothek **Main**, indem Sie wie angegeben auf **Bearbeiten** klicken.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl12gcp.png)

Klicken Sie auf die Schaltfläche **Alle geänderten Ressourcen hinzufügen** , nach der Ihre Regel und Ihr Datenelement in dieser Bibliothek angezeigt werden. Klicken Sie anschließend auf **Speichern und für Entwicklung erstellen**. Ihre Änderungen werden jetzt bereitgestellt.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl13gcp.png)

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

Wechseln Sie Ihre Ansicht in Ihr Google Cloud-Pub/Sub und gehen Sie zu **NACHRICHTEN**. Klicken Sie auf **PULL** und nach einigen Sekunden werden einige Meldungen in der Liste angezeigt. Klicken Sie auf eine Nachricht, um ihren Inhalt zu visualisieren.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook3gcp.png)

Sie können jetzt die XDM-Payload Ihres Ereignisses in Google Pub/Sub sehen. Sie haben jetzt erfolgreich von der Adobe Experience Platform-Datenerfassung erfasste Daten in Echtzeit an einen Google Cloud-Pub-/Sub-Endpunkt gesendet. Von dort können diese Daten von jeder beliebigen Google Cloud Platform-Anwendung verwendet werden, z. B. BigQuery für Speicherung und Reporting oder für Anwendungsfälle des maschinellen Lernens.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook4gcp.png)

Nächster Schritt: [2.5.5 Ereignisse an AWS Kinesis und AWS S3 weiterleiten](./ex5.md)

[Zurück zu Modul 2.5](./aep-data-collection-ssf.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
