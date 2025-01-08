---
title: Erste Schritte mit Firefly-Services
description: Erste Schritte mit Firefly-Services
kt: 5342
doc-type: tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: 608fc570f9aa172db3578664e793f35fb3f1bf50
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 1%

---

# 1.1.1 Erste Schritte mit Firefly-Services

In dieser Übung verwenden Sie Postman und Adobe I/O, um Adobe Firefly Services-APIs abzufragen.

## Konfigurieren des Adobe I/O-Projekts

In dieser Übung verwenden Sie Adobe I/O sehr intensiv, um Abfragen nach Firefly Services-APIs durchzuführen. Gehen Sie wie folgt vor, um Adobe I/O einzurichten.

Wechseln Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home)

![Neue Integration Adobe I/O](./images/iohome.png)

Achten Sie darauf, dass Sie die richtige Instanz in der oberen rechten Ecke Ihres Bildschirms auswählen. Ihre Instanz ist `--aepImsOrgName--`. Klicken Sie **Neues Projekt erstellen**.

![Neue Integration Adobe I/O](./images/iocomp.png)

Wählen Sie **+ Zu Projekt hinzufügen** dann **API** aus.

![Neue Integration Adobe I/O](./images/adobe_io_access_api.png)

Sie sehen dann Folgendes:

![Neue Integration Adobe I/O](./images/api1.png)

Wählen Sie **Creative Cloud** und klicken Sie auf **Firefly - Firefly Services**. Klicken Sie auf **Weiter**.

![Neue Integration Adobe I/O](./images/api3.png)

Das wirst du jetzt sehen. Geben Sie einen Namen für Ihre Berechtigung ein: `--aepUserLdap-- - Firefly Services OAuth credential`. Klicken Sie auf **Weiter**.

![Neue Integration Adobe I/O](./images/api4.png)

Als Nächstes müssen Sie ein Produktprofil auswählen, das definiert, welche Berechtigungen für diese Integration verfügbar sind.

Wählen Sie das Profil **Standardkonfiguration für Firefly-Services** aus.

Klicken Sie **Konfigurierte API speichern**.

![Neue Integration Adobe I/O](./images/api9.png)

Ihre Adobe I/O-Integration ist jetzt bereit.

![Neue Integration Adobe I/O](./images/api11.png)

Klicken Sie auf **Schaltfläche „Für Postman herunterladen** und anschließend auf **OAuth Server-zu-Server**, um eine Postman-Umgebung herunterzuladen.

![Neue Integration Adobe I/O](./images/iopm.png)

Ihr IO-Projekt hat derzeit einen generischen Namen. Sie müssen Ihrer Integration einen Anzeigenamen geben. Klicken Sie auf **Projekt X** (oder einen ähnlichen Namen) wie angegeben

![Neue Integration Adobe I/O](./images/api13.png)

Klicken Sie **Projekt bearbeiten**.

![Neue Integration Adobe I/O](./images/api14.png)

Geben Sie einen Namen für Ihre Integration ein: `--aepUserLdap-- Firefly`.

Klicken Sie auf **Speichern**.

![Neue Integration Adobe I/O](./images/api15.png)

Das Setup Ihrer Adobe I/O-Integration ist jetzt abgeschlossen.

![Neue Integration Adobe I/O](./images/api16.png)

## Postman-Authentifizierung für Adobe I/O

Navigieren Sie zu [https://www.postman.com/downloads/](https://www.postman.com/downloads/).

Laden Sie die entsprechende Version von Postman für Ihr Betriebssystem herunter und installieren Sie sie.

![Neue Integration Adobe I/O](./images/getstarted.png)

Starten Sie die Anwendung nach der Installation von Postman.

In Postman gibt es zwei Konzepte: Umgebungen und Sammlungen.

- Die Umgebungsdatei enthält alle Umgebungsvariablen, die mehr oder weniger konsistent sind. In der Umgebung finden Sie Dinge wie die IMSOrg Ihrer Adobe-Umgebung zusammen mit Sicherheitsberechtigungen wie Ihre Client-ID und andere. Die Umgebungsdatei ist die Datei, die Sie während des Adobe I/O-Setups in der vorherigen Übung heruntergeladen haben. Sie heißt wie folgt: **`oauth_server_to_server.postman_environment.json`**.

- Die Sammlung enthält eine Reihe von API-Anfragen, die Sie verwenden können. Wir werden 2 Kollektionen verwenden
   - 1 Sammlung zur Authentifizierung beim Adobe I/O
   - 1 Sammlung für die Übungen in diesem Modul

Bitte laden Sie die Datei [postman.zip](./../../../assets/postman/postman-ff.zip) auf Ihren lokalen Desktop herunter.

![Neue Integration Adobe I/O](./images/pmfolder.png)

In dieser **postman.zip**-Datei finden Sie die folgenden Dateien:

- `Adobe IO - OAuth.postman_collection.json`
- `FF - Firefly Services Tech Insiders.postman_collection.json`

Entpacken Sie die **postman-ff.zip**-Datei und speichern Sie diese beiden Dateien in einem Ordner auf Ihrem Desktop, zusammen mit der heruntergeladenen Postman-Umgebung von Adobe I/O, der `oauth_server_to_server.postman_environment.json`. Sie müssen die folgenden drei Dateien in diesem Ordner haben:

![Neue Integration Adobe I/O](./images/pmfolder1.png)

Zurück zu Postman. Klicken Sie **Importieren**.

![Neue Integration Adobe I/O](./images/postmanui.png)

Klicken Sie auf **Dateien**.

![Neue Integration Adobe I/O](./images/choosefiles.png)

Navigieren Sie zu dem Ordner auf Ihrem Desktop, in den Sie die zwei heruntergeladenen Dateien extrahiert haben. Wählen Sie diese drei Dateien gleichzeitig aus und klicken Sie auf **Öffnen**.

![Neue Integration Adobe I/O](./images/selectfiles.png)

Nachdem Sie auf **Öffnen** geklickt haben, zeigt Ihnen Postman einen Überblick über die Umgebung und die Sammlungen, die Sie importieren möchten. Klicken Sie **Importieren**.

![Neue Integration Adobe I/O](./images/impconfirm.png)

Sie haben jetzt alles, was Sie in Postman benötigen, um über die APIs mit Firefly-Services zu interagieren.

Zunächst müssen Sie sicherstellen, dass Sie ordnungsgemäß authentifiziert sind. Um authentifiziert zu werden, müssen Sie ein Zugriffs-Token anfordern.

Stellen Sie sicher, dass Sie die richtige Umgebung ausgewählt haben, bevor Sie eine Anfrage ausführen. Sie können die aktuell ausgewählte Umgebung überprüfen, indem Sie die Dropdown-Liste Umgebung oben rechts überprüfen.

Die ausgewählte Umgebung sollte einen Namen haben, der `--aepUserLdap-- Firefly Services OAuth Credential` diesem ähnelt.

![Postman](./images/envselemea.png)

Ihre Postman-Umgebung und Sammlungen sind jetzt konfiguriert und funktionieren. Sie können sich jetzt von Postman auf Adobe I/O authentifizieren.

Wählen Sie in der Sammlung **Adobe-IO - OAuth** die Anfrage mit dem Namen **POST - Zugriffs-Token abrufen**. Sie werden feststellen, dass unter **params** 2 Variablen referenziert werden, `API_KEY` und `CLIENT_SECRET`. Diese Variablen werden `--aepUserLdap-- Firefly Services OAuth Credential` aus der ausgewählten Umgebung übernommen.

Klicken Sie auf **Senden**.

![Postman](./images/ioauth.png)

Nachdem Sie auf **Senden** geklickt haben, wird eine Antwort im Abschnitt **Hauptteil** von Postman angezeigt:

![Postman](./images/ioauthresp.png)

Wenn Ihre Konfiguration erfolgreich war, sollte eine ähnliche Antwort mit den folgenden Informationen angezeigt werden:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| token_type | **Bearer** |
| access_token | **eyJhbGciOiJSU…** |
| expires_in | **86399** |

Adobe I/O hat Ihnen ein **Bearer**-Token mit einem bestimmten Wert (dem sehr langen Zugriffs-Token) und einem Gültigkeitsfenster gegeben.

Das Token, das wir erhalten haben, ist jetzt 24 Stunden lang gültig. Wenn Sie also nach 24 Stunden Postman zur Authentifizierung bei Adobe I/O verwenden möchten, müssen Sie ein neues Token generieren, indem Sie diese Anfrage erneut ausführen.

## Firefly Services-API, Text 2 Bild

Jetzt können Sie Ihre erste Anfrage an Firefly Services-APIs senden.

Wählen Sie in der **FF - Firefly Services Tech Insiders**-Sammlung die Anfrage mit dem Namen **POST - Firefly - T2I V3** aus. Im **body**-Abschnitt wird eine Standardaufforderung mit dem folgenden `Horses in a field` angezeigt. Klicken Sie **Senden**, damit Firefly Services dieses Bild generiert.

![Firefly](./images/ff1.png)

Anschließend sehen Sie eine ähnliche Antwort mit einer Bild-URL. Kopieren Sie die Bild-URL und öffnen Sie sie in Ihrem Webbrowser.

![Firefly](./images/ff2.png)

Jetzt sehen Sie ein schönes Bild, das `horses in a field` darstellt.

![Firefly](./images/ff3.png)

Sie können mit der API-Anfrage spielen, bevor Sie mit der nächsten Übung fortfahren.

Nächster Schritt: [1.1.2 Anfordern von Bildern mit Spezifikationen](./ex2.md)

[Zurück zum Modul 1.1](./firefly-services.md)

[Zurück zu „Alle Module“](./../../../overview.md)
