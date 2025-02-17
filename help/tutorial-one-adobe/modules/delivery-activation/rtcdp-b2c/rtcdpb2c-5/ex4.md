---
title: Datenerfassung und Server-seitige Weiterleitung in Echtzeit - Erstellen und Konfigurieren einer Google Cloud-Funktion
description: Erstellen und Konfigurieren einer Google Cloud-Funktion
kt: 5342
doc-type: tutorial
exl-id: bdee5a9b-2f1a-467e-9edc-a2e10a263694
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 1%

---

# 2.5.4 Weiterleiten von Ereignissen an GCP Pub/Sub

>[!NOTE]
>
>Für diese Übung benötigen Sie Zugriff auf eine Google Cloud Platform-Umgebung. Wenn Sie noch keinen Zugriff auf GCP haben, erstellen Sie ein neues Konto mit Ihrer persönlichen E-Mail-Adresse.

## Erstellen eines Google Cloud Pub/Sub-Themas

Navigieren Sie zu [https://console.cloud.google.com/](https://console.cloud.google.com/). Geben Sie in der Suchleiste `pub/sub` ein. Klicken Sie auf das Suchergebnis **Pub/Sub - Globale Echtzeit-Nachrichten**.

![GCP](./images/gcp1.png)

Sie werden es dann sehen. Klicken Sie **THEMA ERSTELLEN**.

![GCP](./images/gcp2.png)

Sie werden es dann sehen. Verwenden Sie für Ihre Themen-ID `--aepUserLdap---event-forwarding`. Klicken Sie auf **Erstellen**.

![GCP](./images/gcp6.png)

Ihr Thema wurde erstellt. Klicken Sie auf die „Abonnement **ID“ des**.

![GCP](./images/gcp7.png)

Sie werden es dann sehen. Kopieren Sie den **Themennamen** in die Zwischenablage und speichern Sie ihn so, wie Sie ihn in den nächsten Übungen benötigen werden.

![GCP](./images/gcp8.png)

Wechseln wir jetzt zur Ereignisweiterleitung bei der Adobe Experience Platform-Datenerfassung, um Ihre Ereignisweiterleitungseigenschaft zu aktualisieren und mit der Ereignisweiterleitung an Pub/Sub zu beginnen.


## Aktualisieren Sie die Ereignisweiterleitungseigenschaft: Geheimnisse

**Geheimnisse** in den Properties der Ereignisweiterleitung werden zum Speichern von Anmeldeinformationen verwendet, die für die Authentifizierung bei externen APIs verwendet werden. In diesem Beispiel müssen Sie einen geheimen Schlüssel konfigurieren, um Ihr Google Cloud Platform OAuth-Token zu speichern, das zur Authentifizierung verwendet wird, wenn Pub/Sub zum Streamen von Daten an GCP verwendet wird.

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/) und dann zu **Secrets**. Klicken Sie **Neue geheimen Daten erstellen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/secret1.png)

Sie werden es dann sehen. Befolgen Sie diese Anweisungen:

- Name: use `--aepUserLdap---gcp-secret`
- Zielumgebung: Wählen Sie **Entwicklung**
- Typ: **Google OAuth 2**
- Aktivieren Sie das Kontrollkästchen für **Pub/Sub**

Klicken Sie **Geheimnis erstellen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/secret2.png)

Nachdem Sie auf **Geheimnis erstellen** geklickt haben, wird ein Popup angezeigt, in dem Sie die Authentifizierung zwischen dem Geheimnis Ihrer Ereignisweiterleitungseigenschaft und Google einrichten können. Klicken Sie **Geheimnis `--aepUserLdap---gcp-secret` mit Google erstellen und autorisieren**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/secret3.png)

Klicken Sie, um Ihr Google-Konto auszuwählen.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/secret4.png)

Klicken Sie auf **Weiter**.

>[!NOTE]
>
>Ihre Popup-Nachricht kann variieren. Bitte autorisieren/erlauben Sie den angeforderten Zugriff, um die Übung fortsetzen zu können.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/secret5.png)

Nach erfolgreicher Authentifizierung sehen Sie Folgendes.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/secret6.png)

Die geheimen Daten wurden erfolgreich konfiguriert und können in einem Datenelement verwendet werden.

## Aktualisieren der Ereignisweiterleitungseigenschaft: Datenelement

Um Ihre geheimen Daten in der Ereignisweiterleitungs-Eigenschaft zu verwenden, müssen Sie ein Datenelement erstellen, in dem der Wert der geheimen Daten gespeichert wird.

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/) und dann zu **Ereignisweiterleitung**. Suchen Sie Ihre Ereignisweiterleitungs-Eigenschaft und klicken Sie darauf, um sie zu öffnen.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/prop1.png)

Wechseln Sie im linken Menü zu **Datenelemente**. Klicken Sie **Datenelement hinzufügen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/de1gcp.png)

Konfigurieren Sie Ihr Datenelement wie folgt:

- Name: **GCP-Geheimnis**
- Erweiterung: **core**
- Datenelementtyp: **secret**
- Entwicklungsgeheimnis : Wählen Sie die von Ihnen erstellten geheimen Daten aus, die `--aepUserLdap---gcp-secret` heißen

Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/secret7.png)

## Aktualisieren Sie die Ereignisweiterleitungseigenschaft: Erweiterung

Nachdem Sie Ihre geheimen Daten und Ihr Datenelement konfiguriert haben, können Sie jetzt die Erweiterung für Google Cloud Platform in Ihrer Ereignisweiterleitungs-Eigenschaft einrichten.

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/), wechseln Sie zu **Ereignisweiterleitung** und öffnen Sie Ihre Ereignisweiterleitungseigenschaft.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/prop1.png)

Gehen Sie dann zu **Erweiterungen**, zu **Katalog**. Klicken Sie auf die Erweiterung **Google Cloud Platform** und dann auf **Installieren**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/gext2.png)

Sie werden es dann sehen. Klicken Sie auf das Symbol Datenelement .

![Adobe Experience Platform-Datenerfassungs-SSF](./images/gext3.png)

Wählen Sie das Datenelement aus, das Sie in der vorherigen Übung erstellt haben. Es heißt **GCP-Geheimnis**. Klicken Sie auf **Auswählen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/gext4.png)

Sie werden es dann sehen. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/gext5.png)

## Aktualisieren der Ereignisweiterleitungseigenschaft: Aktualisieren einer Regel

Nachdem Sie Ihre Google Cloud Platform-Erweiterung konfiguriert haben, können Sie eine Regel definieren, um mit der Weiterleitung von Ereignisdaten an Ihr Pub/Sub-Thema zu beginnen. Dazu müssen Sie Ihre Regel **Alle Seiten** aktualisieren, die Sie in einer der vorherigen Übungen erstellt haben.

Navigieren Sie im linken Menü zu **Regeln**. In der vorherigen Übung haben Sie die Regel &quot;**Seiten“**. Klicken Sie auf diese Regel, um sie zu öffnen.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl1gcp.png)

Dann wirst du das hier. Klicken Sie auf das Symbol **+** unter **Aktionen**, um eine neue Aktion hinzuzufügen.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl2gcp.png)

Sie werden es dann sehen. Nehmen Sie die folgende Auswahl vor:

- Wählen Sie **Erweiterung** aus: **Google Cloud Platform**.
- Wählen Sie den **Aktionstyp** aus: **Daten an Cloud Pub/Sub senden**.

Daraus sollte folgender **bestehenName**: **Google Cloud Platform - Senden von Daten an Cloud Pub/Sub**. Sie sollten dies jetzt sehen:

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl5gcp.png)

Jetzt müssen Sie das zuvor erstellte Pub/Sub-Thema konfigurieren.

Den **Themennamen“ finden** hier kopieren.

![GCP](./images/gcp8.png)

Fügen Sie den **Themennamen** in Ihre Regelkonfiguration ein. Klicken Sie anschließend auf das Datenelementsymbol neben dem Feld **Daten (erforderlich)**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl6gcp.png)

Wählen Sie **XDM-Ereignis** aus und klicken Sie auf **Auswählen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl7gcp.png)

Sie werden es dann sehen. Klicken Sie auf **Änderungen beibehalten**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl8gcp.png)

Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl9gcp.png)

Sie werden es dann sehen.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl10gcp.png)

## Veröffentlichen der Änderungen

Ihre Konfiguration ist jetzt abgeschlossen. Gehen Sie zu **Veröffentlichungsfluss**, um Ihre Änderungen zu veröffentlichen. Öffnen Sie Ihre Entwicklungsbibliothek **Main**, indem Sie wie **auf** Bearbeiten“ klicken.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl12gcp.png)

Klicken Sie auf **Schaltfläche „Alle geänderten Ressourcen hinzufügen**. Danach werden Ihre Regel und Ihr Datenelement in dieser Bibliothek angezeigt. Klicken Sie anschließend auf **Für Entwicklung speichern und erstellen**. Ihre Änderungen werden jetzt bereitgestellt.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl13gcp.png)

Nach einigen Minuten sehen Sie, dass die Bereitstellung abgeschlossen ist und getestet werden kann.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl14.png)

## Testen der Konfiguration

Navigieren Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf die 3 Punkte **…** in Ihrem Website-Projekt und dann auf **Ausführen**, um es zu öffnen.

![DSN](./../../datacollection/dc1.1/images/web8.png)

Anschließend wird Ihre Demo-Website geöffnet. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../../getting-started/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browser-Fenster.

![DSN](../../../getting-started/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../../getting-started/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../../getting-started/gettingstarted/images/web6.png)

Ihre Website wird dann in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../../getting-started/gettingstarted/images/web7.png)

Wechseln Sie zur Ansicht Ihres Google Cloud Pub/Sub und navigieren Sie zu **NACHRICHTEN**. Klicken Sie **PULL** und nach einigen Sekunden werden einige Meldungen in der Liste angezeigt. Klicken Sie auf eine Nachricht, um deren Inhalt zu visualisieren.

![Einrichtung der Adobe Experience Platform-Datenerfassung](./images/hook3gcp.png)

Jetzt können Sie die XDM-Payload Ihres Ereignisses in Google Pub/Sub sehen. Sie haben jetzt erfolgreich Daten, die von der Adobe Experience Platform-Datenerfassung erfasst wurden, in Echtzeit an einen Google Cloud Pub/Sub-Endpunkt gesendet. Von dort aus können diese Daten von jeder Google Cloud Platform-Anwendung verwendet werden, z. B. BigQuery für Speicherung und Reporting oder für Anwendungsfälle des maschinellen Lernens.

![Einrichtung der Adobe Experience Platform-Datenerfassung](./images/hook4gcp.png)

## Nächste Schritte

Navigieren Sie zu [2.5.5 Ereignisse an AWS Kinesis und AWS S3 weiterleiten](./ex5.md){target="_blank"}

Zurück zu [Real-Time CDP Connections: Ereignisweiterleitung](./aep-data-collection-ssf.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
