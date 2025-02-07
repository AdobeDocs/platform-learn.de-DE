---
title: Erste Schritte mit Firefly-Services
description: Erfahren Sie, wie Sie mit Postman und Adobe I/O Adobe Firefly-Services-APIs abfragen können
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: e6a549441d425801f2a554da9af803dca646009e
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---

# 1.1.1 Erste Schritte mit Firefly-Services

Erfahren Sie, wie Sie mit Postman und Adobe I/O Adobe Firefly-Services-APIs abfragen können.

## 1.1.1.2 Konfigurieren des Adobe I/O-Projekts

In dieser Übung wird Adobe I/O verwendet, um Abfragen nach Firefly-Services-APIs durchzuführen. Führen Sie die folgenden Schritte aus, um das Adobe I/O einzurichten.

1. Navigieren Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"}.

![Neue Integration Adobe I/O](./images/iohome.png)

1. Achten Sie darauf, dass Sie die richtige Instanz in der oberen rechten Ecke Ihres Bildschirms auswählen. Ihre Instanz ist `--aepImsOrgName--`. Wählen Sie anschließend **Neues Projekt erstellen**.

![Neue Integration Adobe I/O](./images/iocomp.png)

1. Wählen Sie **+ Zu Projekt hinzufügen** und dann **API**.

![Neue Integration Adobe I/O](./images/adobe_io_access_api.png)

Ihr Bildschirm sollte wie folgt aussehen.

![Neue Integration Adobe I/O](./images/api1.png)

1. Wählen Sie **Creative Cloud** und **Firefly - Firefly Services** aus und klicken Sie dann auf **Weiter**.

![Neue Integration Adobe I/O](./images/api3.png)

1. Geben Sie einen Namen für Ihre Berechtigung ein: `--aepUserLdap-- - Firefly Services OAuth credential`und wählen Sie **Weiter**.

![Neue Integration Adobe I/O](./images/api4.png)

1. Wählen Sie das Standardprofil **Standardkonfiguration für Firefly-**) und **Konfigurierte API speichern** aus.

![Neue Integration Adobe I/O](./images/api9.png)

Ihre Adobe I/O-Integration ist jetzt bereit.

![Neue Integration Adobe I/O](./images/api11.png)

## 1.1.1.3 Herunterladen der Postman-Umgebung

1. Wählen Sie **Für Postman herunterladen** und dann **OAuth-Server-zu-Server** aus, um eine Postman-Umgebung herunterzuladen.

![Neue Integration Adobe I/O](./images/iopm.png)

1. Wählen Sie Ihren Projektnamen aus.

![Neue Integration Adobe I/O](./images/api13.png)

1. Wählen Sie **Projekt bearbeiten** aus.

![Neue Integration Adobe I/O](./images/api14.png)

1. Geben Sie einen Anzeigenamen für Ihre Integration ein: `--aepUserLdap-- Firefly`und wählen Sie **Speichern**.

![Neue Integration Adobe I/O](./images/api15.png)

Das Setup Ihrer Adobe I/O-Integration ist jetzt abgeschlossen.

![Neue Integration Adobe I/O](./images/api16.png)

## Postman-Authentifizierung auf Adobe I/O 1.1.1.4

>[!IMPORTANT]
>
>Wenn Sie Adobe-Mitarbeiter sind, befolgen Sie bitte die Anweisungen hier zur Verwendung von [PostBuster](./../../../postbuster.md).

1. Laden Sie unter [ Postman Downloads die entsprechende Version von Postman für Ihr Betriebssystem herunter und installieren Sie sie](https://www.postman.com/downloads/){target="_blank"}.

![Neue Integration Adobe I/O](./images/getstarted.png)

1. Starten Sie die Anwendung.

In Postman gibt es zwei Konzepte: Umgebungen und Sammlungen.

- Die Umgebungsdatei enthält alle Umgebungsvariablen, die mehr oder weniger konsistent sind. In der Umgebung finden Sie Dinge wie die IMSOrg Ihrer Adobe-Umgebung zusammen mit Sicherheitsberechtigungen wie Ihre Client-ID und andere. Sie haben die Umgebungsdatei bereits während des Adobe I/O-Setups heruntergeladen und sie heißt **`oauth_server_to_server.postman_environment.json`**.

- Die Sammlung enthält eine Reihe von API-Anfragen, die Sie verwenden können. Wir werden 2 Kollektionen verwenden
   - 1 Sammlung zur Authentifizierung beim Adobe I/O
   - 1 Sammlung für die Übungen in diesem Modul

1. Laden Sie [postman.zip](./../../../assets/postman/postman-ff.zip) auf Ihren lokalen Desktop herunter.

![Neue Integration Adobe I/O](./images/pmfolder.png)

In **postman.zip**-Datei befinden sich die folgenden Dateien:

    - `Adobe IO - OAuth.postman_collection.json`
    - `FF - Firefly Services Tech Insiders.postman_collection.json`

1. Entpacken Sie **postman-ff.zip** und speichern Sie die folgenden zwei Dateien in einem Ordner auf Ihrem Desktop:
- Adobe IO - OAuth.postman_collection.json
- FF - Firefly Services Tech Insiders.postman_collection.json
- oauth_server_to_server.postman_environment.json

![Neue Integration Adobe I/O](./images/pmfolder1.png)

1. Wählen Sie in Postman **Importieren** aus.

![Neue Integration Adobe I/O](./images/postmanui.png)

1. Wählen Sie **Dateien** aus.

![Neue Integration Adobe I/O](./images/choosefiles.png)

1. Wählen Sie die drei Dateien aus dem Ordner aus und klicken Sie dann auf **Öffnen** und **Importieren**.

![Neue Integration Adobe I/O](./images/selectfiles.png)

![Neue Integration Adobe I/O](./images/impconfirm.png)

Jetzt verfügen Sie über alles, was Sie in Postman benötigen, um über die APIs mit Firefly-Services zu interagieren.

## 1.1.1.5 Anfordern eines Zugriffstokens

Als Nächstes müssen Sie ein Zugriffs-Token anfordern, um sicherzustellen, dass Sie ordnungsgemäß authentifiziert sind.

1. Vergewissern Sie sich, dass Sie die richtige Umgebung ausgewählt haben, bevor Sie eine Anfrage ausführen, indem Sie die Dropdown-Liste „Umgebung“ oben rechts überprüfen. Die ausgewählte Umgebung sollte einen Namen haben, der `--aepUserLdap-- Firefly Services OAuth Credential` diesem ähnelt.

![Postman](./images/envselemea1.png)

Die ausgewählte Umgebung sollte einen Namen haben, der `--aepUserLdap-- Firefly Services OAuth Credential` diesem ähnelt.

![Postman](./images/envselemea.png)

Nachdem Ihre Postman-Umgebung und Sammlungen konfiguriert wurden und funktionieren, können Sie sich von Postman bis Adobe I/O authentifizieren.

1. Wählen Sie in der Sammlung **Adobe-IO - OAuth** die Anfrage mit dem Namen **POST - Zugriffs-Token** und klicken Sie auf **Senden**.

Beachten Sie, **unter „Abfrageparameter** zwei Variablen referenziert werden, `API_KEY` und `CLIENT_SECRET`. Diese Variablen werden `--aepUserLdap-- Firefly Services OAuth Credential` aus der ausgewählten Umgebung übernommen.

![Postman](./images/ioauth.png)

Bei Erfolg wird eine Antwort mit einem Bearer-Token, einem Zugriffs-Token und einem Ablauffenster im Abschnitt **body** von Postman angezeigt.

![Postman](./images/ioauthresp.png)


Es sollte eine ähnliche Antwort mit den folgenden Informationen angezeigt werden:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| token_type | **Bearer** |
| access_token | **eyJhbGciOiJSU…** |
| expires_in | **86399** |

Das Adobe I/O **Bearer-Token** hat einen bestimmten Wert (das sehr lange Zugriffs-Token) und ein Gültigkeitsfenster und ist jetzt 24 Stunden lang gültig. Wenn Sie also nach 24 Stunden Postman zur Authentifizierung bei Adobe I/O verwenden möchten, müssen Sie ein neues Token generieren, indem Sie diese Anfrage erneut ausführen.

## 1.1.1.6 Firefly Services-API, Text 2 Bild

Jetzt können Sie Ihre erste Anfrage an Firefly Services-APIs senden.

1. Wählen Sie die Anfrage mit dem Namen **POST - Firefly - T2I V3** aus der Sammlung **FF - Firefly Services Tech Insiders** aus.

![Firefly](./images/ff1.png)

1. Kopieren Sie die Bild-URL aus der Antwort und öffnen Sie sie in Ihrem Webbrowser, um das Bild anzuzeigen.

![Firefly](./images/ff2.png)

Sie sollten ein schönes Bild sehen, das `horses in a field` darstellt.

![Firefly](./images/ff3.png)

Sie können mit der API-Anfrage spielen, bevor Sie mit der nächsten Übung fortfahren.

## Nächste Schritte

Navigieren Sie zu [Optimieren Ihres Firefly-Prozesses mit Microsoft Azure und vordefinierten URLs](./ex2.md){target="_blank"}

Zurück zu [Übersicht über Adobe Firefly-Services](./firefly-services.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
