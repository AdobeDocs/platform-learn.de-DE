---
title: Erste Schritte mit Firefly Services
description: Erfahren Sie, wie Sie Postman und Adobe I/O verwenden, um Adobe Firefly Services-APIs abzufragen
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: 219945c74c620b9a4b93cb2b7462137118d42d33
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 1%

---

# 1.1.1 Erste Schritte mit Firefly Services

Erfahren Sie, wie Sie Postman und Adobe I/O verwenden, um Adobe Firefly Services-APIs abzufragen.

## Konfigurieren 1.1.1.1 Adobe I/O-Projekts

In dieser Übung wird Adobe I/O verwendet, um Abfragen nach Firefly Services-APIs durchzuführen. Führen Sie diese Schritte aus, um Adobe I/O einzurichten.

1. Navigieren Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"}.

![Neue Adobe I/O-Integration](./images/iohome.png){zoomable="yes"}

1. Achten Sie darauf, dass Sie die richtige Instanz in der oberen rechten Ecke Ihres Bildschirms auswählen. Ihre Instanz ist `--aepImsOrgName--`. Wählen Sie anschließend **Neues Projekt erstellen**.

![Neue Adobe I/O-Integration](./images/iocomp.png){zoomable="yes"}

1. Wählen Sie **+ Zu Projekt hinzufügen** und dann **API**.

![Neue Adobe I/O-Integration](./images/adobe_io_access_api.png){zoomable="yes"}

Ihr Bildschirm sollte wie folgt aussehen.

![Neue Adobe I/O-Integration](./images/api1.png){zoomable="yes"}

1. Wählen Sie **Creative Cloud** und **Firefly - Firefly Services** aus und klicken Sie dann auf **Weiter**.

![Neue Adobe I/O-Integration](./images/api3.png){zoomable="yes"}

1. Geben Sie einen Namen für Ihre Berechtigung ein: `--aepUserLdap-- - Firefly Services OAuth credential`und wählen Sie **Weiter**.

![Neue Adobe I/O-Integration](./images/api4.png){zoomable="yes"}

1. Wählen Sie das Standardprofil **Standardkonfiguration für Firefly Services** und dann **Konfigurierte API speichern** aus.

![Neue Adobe I/O-Integration](./images/api9.png){zoomable="yes"}

Ihre Adobe I/O-Integration ist jetzt bereit.

![Neue Adobe I/O-Integration](./images/api11.png){zoomable="yes"}

## 1.1.1.2 Herunterladen der Postman-Umgebung

1. Wählen Sie **Für Postman herunterladen** und dann **OAuth-Server-zu-Server** aus, um eine Postman-Umgebung herunterzuladen.

![Neue Adobe I/O-Integration](./images/iopm.png){zoomable="yes"}

1. Wählen Sie Ihren Projektnamen aus.

![Neue Adobe I/O-Integration](./images/api13.png){zoomable="yes"}

1. Wählen Sie **Projekt bearbeiten** aus.

![Neue Adobe I/O-Integration](./images/api14.png){zoomable="yes"}

1. Geben Sie einen Anzeigenamen für Ihre Integration ein: `--aepUserLdap-- Firefly`und wählen Sie **Speichern**.

![Neue Adobe I/O-Integration](./images/api15.png){zoomable="yes"}

Die Einrichtung Ihrer Adobe I/O-Integration ist jetzt abgeschlossen.

![Neue Adobe I/O-Integration](./images/api16.png){zoomable="yes"}

## 1.1.1.3 der Postman-Authentifizierung bei Adobe I/O

1. Laden Sie unter [ Postman Downloads die entsprechende Version von Postman für Ihr Betriebssystem herunter und installieren Sie sie](https://www.postman.com/downloads/){target="_blank"}.

![Neue Adobe I/O-Integration](./images/getstarted.png){zoomable="yes"}

1. Starten Sie die Anwendung.

In Postman gibt es zwei Konzepte: Umgebungen und Sammlungen.

- Die Umgebungsdatei enthält alle Umgebungsvariablen, die mehr oder weniger konsistent sind. In der Umgebung finden Sie Dinge wie die IMSOrg Ihrer Adobe-Umgebung sowie Sicherheitsberechtigungen wie Ihre Client-ID und andere. Sie haben die Umgebungsdatei zuvor während des Adobe I/O-Setups heruntergeladen und sie heißt **`oauth_server_to_server.postman_environment.json`**.

- Die Sammlung enthält eine Reihe von API-Anfragen, die Sie verwenden können. Wir werden 2 Kollektionen verwenden
   - 1 Sammlung für die Authentifizierung bei Adobe I/O
   - 1 Sammlung für die Übungen in diesem Modul

1. Laden Sie [postman-ff.zip](./../../../assets/postman/postman-ff.zip) auf Ihren lokalen Desktop herunter.

![Neue Adobe I/O-Integration](./images/pmfolder.png){zoomable="yes"}

In **postman.zip**-Datei befinden sich die folgenden Dateien:

    - `Adobe IO - OAuth.postman_collection.json`
    - `FF - Firefly Services Tech Insiders.postman_collection.json`

1. Entpacken Sie **postman-ff.zip** und speichern Sie die folgenden zwei Dateien in einem Ordner auf Ihrem Desktop:
- Adobe IO - OAuth.postman_collection.json
- FF - Firefly Services Tech Insiders.postman_collection.json
- oauth_server_to_server.postman_environment.json

![Neue Adobe I/O-Integration](./images/pmfolder1.png){zoomable="yes"}

1. Wählen Sie in Postman **Importieren** aus.

![Neue Adobe I/O-Integration](./images/postmanui.png){zoomable="yes"}

1. Wählen Sie **Dateien** aus.

![Neue Adobe I/O-Integration](./images/choosefiles.png){zoomable="yes"}

1. Wählen Sie die drei Dateien aus dem Ordner aus und klicken Sie dann auf **Öffnen** und **Importieren**.

![Neue Adobe I/O-Integration](./images/selectfiles.png){zoomable="yes"}

![Neue Adobe I/O-Integration](./images/impconfirm.png){zoomable="yes"}

Jetzt verfügen Sie über alles, was Sie in Postman benötigen, um über die APIs mit Firefly-Services zu interagieren.

## 1.1.1.4 Anfordern eines Zugriffstokens

Als Nächstes müssen Sie ein Zugriffs-Token anfordern, um sicherzustellen, dass Sie ordnungsgemäß authentifiziert sind.

1. Vergewissern Sie sich, dass Sie die richtige Umgebung ausgewählt haben, bevor Sie eine Anfrage ausführen, indem Sie die Dropdown-Liste „Umgebung“ oben rechts überprüfen. Die ausgewählte Umgebung sollte einen Namen haben, der `--aepUserLdap-- Firefly Services OAuth Credential` diesem ähnelt.

![Postman](./images/envselemea1.png){zoomable="yes"}

Die ausgewählte Umgebung sollte einen Namen haben, der `--aepUserLdap-- Firefly Services OAuth Credential` diesem ähnelt.

![Postman](./images/envselemea.png){zoomable="yes"}

Nachdem Ihre Postman-Umgebung und Sammlungen konfiguriert wurden und funktionieren, können Sie sich von Postman bei Adobe I/O authentifizieren.

1. Wählen Sie in der Sammlung **Adobe IO - OAuth** die Anfrage mit dem Namen **POST - Zugriffstoken abrufen** und klicken Sie auf **Senden**.

Beachten Sie, **unter „Abfrageparameter** zwei Variablen referenziert werden, `API_KEY` und `CLIENT_SECRET`. Diese Variablen werden `--aepUserLdap-- Firefly Services OAuth Credential` aus der ausgewählten Umgebung übernommen.

![Postman](./images/ioauth.png){zoomable="yes"}

Bei Erfolg wird eine Antwort mit einem Bearer-Token, einem Zugriffs-Token und einem Ablauffenster im Abschnitt **body** von Postman angezeigt.

![Postman](./images/ioauthresp.png){zoomable="yes"}


Es sollte eine ähnliche Antwort mit den folgenden Informationen angezeigt werden:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| token_type | **Bearer** |
| access_token | **eyJhbGciOiJSU…** |
| expires_in | **86399** |

Das Adobe I/O **Bearer-Token** hat einen bestimmten Wert (das sehr lange Zugriffs-Token) und ein Gültigkeitsfenster und ist jetzt 24 Stunden lang gültig. Wenn Sie also nach 24 Stunden Postman zur Authentifizierung bei Adobe I/O verwenden möchten, müssen Sie ein neues Token generieren, indem Sie diese Anfrage erneut ausführen.

## 1.1.1.5 Firefly Services-API, Text 2 Bild

Jetzt können Sie Ihre erste Anfrage an Firefly Services-APIs senden.

1. Wählen Sie die Anfrage **POST - Firefly - T2I V3** aus der Sammlung **FF - Firefly Services Tech Insiders** aus.

![Firefly](./images/ff1.png){zoomable="yes"}

1. Kopieren Sie die Bild-URL aus der Antwort und öffnen Sie sie in Ihrem Webbrowser, um das Bild anzuzeigen.

![Firefly](./images/ff2.png){zoomable="yes"}

Sie sollten ein schönes Bild sehen, das `horses in a field` darstellt.

![Firefly](./images/ff3.png){zoomable="yes"}

Sie können mit der API-Anfrage spielen, bevor Sie mit der nächsten Übung fortfahren.

## Nächste Schritte

Navigieren Sie zu [Optimieren Ihres Firefly-Prozesses mit Microsoft Azure und vordefinierten URLs](./ex2.md){target="_blank"}

Zurück zu [Übersicht über Adobe Firefly Services](./firefly-services.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
