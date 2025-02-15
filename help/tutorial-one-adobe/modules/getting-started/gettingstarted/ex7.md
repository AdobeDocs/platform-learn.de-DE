---
title: Erste Schritte - Einrichten von Postman
description: Erste Schritte - Einrichten von Postman
kt: 5342
doc-type: tutorial
source-git-commit: 431f7696df12c8c133aced57c0f639c682304dee
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Option 1: Verwenden von Postman

>[!IMPORTANT]
>
>Wenn Sie ein Adobe-Mitarbeiter sind, befolgen Sie die Anweisungen zum [ von PostBuster](./ex8.md)!

## Herunterladen der Postman-Umgebung

Wechseln Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"} und öffnen Sie Ihr Projekt.

![Neue Adobe I/O-Integration](./images/iopr.png){zoomable="yes"}

Klicken Sie auf die **Firefly - Firefly Services**-API. Klicken Sie dann auf **Für Postman herunterladen** und wählen Sie **OAuth Server-zu-Server** aus, um eine Postman-Umgebung herunterzuladen.

![Neue Adobe I/O-Integration](./images/iopm.png){zoomable="yes"}

## Postman-Authentifizierung bei Adobe I/O

Laden Sie unter [ Postman Downloads die entsprechende Version von Postman für Ihr Betriebssystem herunter und installieren Sie sie](https://www.postman.com/downloads/){target="_blank"}.

![Neue Adobe I/O-Integration](./images/getstarted.png){zoomable="yes"}

Starten Sie die Anwendung.

In Postman gibt es zwei Konzepte: Umgebungen und Sammlungen.

Die Umgebungsdatei enthält alle Umgebungsvariablen, die mehr oder weniger konsistent sind. In der Umgebung finden Sie Dinge wie die IMSOrg Ihrer Adobe-Umgebung sowie Sicherheitsberechtigungen wie Ihre Client-ID und andere. Sie haben die Umgebungsdatei zuvor während des Adobe I/O-Setups heruntergeladen und sie heißt **`oauth_server_to_server.postman_environment.json`**.

Die Sammlung enthält eine Reihe von API-Anfragen, die Sie verwenden können. Wir werden 2 Kollektionen verwenden

- 1 Sammlung für die Authentifizierung bei Adobe I/O
- 1 Sammlung für die Übungen in diesem Modul

Laden Sie [postman-ff.zip](./../../../assets/postman/postman-ff.zip) auf Ihren lokalen Desktop herunter.

![Neue Adobe I/O-Integration](./images/pmfolder.png){zoomable="yes"}

In **postman-ff.zip**-Datei befinden sich die folgenden Dateien:

- `Adobe IO - OAuth.postman_collection.json`
- `FF - Firefly Services Tech Insiders.postman_collection.json`

Entpacken Sie **postman-ff.zip** und speichern Sie die folgenden zwei Dateien in einem Ordner auf Ihrem Desktop:

- `Adobe IO - OAuth.postman_collection.json`
- `FF - Firefly Services Tech Insiders.postman_collection.json`
- `oauth_server_to_server.postman_environment.json`

![Neue Adobe I/O-Integration](./images/pmfolder1.png){zoomable="yes"}

Wählen Sie in Postman **Importieren** aus.

![Neue Adobe I/O-Integration](./images/postmanui.png){zoomable="yes"}

Wählen Sie **Dateien** aus.

![Neue Adobe I/O-Integration](./images/choosefiles.png){zoomable="yes"}

Wählen Sie die drei Dateien aus dem Ordner aus und klicken Sie dann auf **Öffnen** und **Importieren**.

![Neue Adobe I/O-Integration](./images/selectfiles.png){zoomable="yes"}

![Neue Adobe I/O-Integration](./images/impconfirm.png){zoomable="yes"}

Jetzt verfügen Sie über alles, was Sie in Postman benötigen, um über die APIs mit Firefly-Services zu interagieren.

## Anfordern eines Zugriffstokens

Als Nächstes müssen Sie ein Zugriffs-Token anfordern, um sicherzustellen, dass Sie ordnungsgemäß authentifiziert sind.

Vergewissern Sie sich, dass Sie die richtige Umgebung ausgewählt haben, bevor Sie eine Anfrage ausführen, indem Sie die Dropdown-Liste „Umgebung“ oben rechts überprüfen. Die ausgewählte Umgebung sollte einen Namen haben, der `--aepUserLdap-- One Adobe OAuth Credential` diesem ähnelt.

![Postman](./images/envselemea1.png){zoomable="yes"}

Die ausgewählte Umgebung sollte einen Namen haben, der `--aepUserLdap-- One Adobe OAuth Credential` diesem ähnelt.

![Postman](./images/envselemea.png){zoomable="yes"}

Nachdem Ihre Postman-Umgebung und Sammlungen konfiguriert wurden und funktionieren, können Sie sich von Postman bei Adobe I/O authentifizieren.

Wählen Sie in der Sammlung **Adobe IO - OAuth** die Anfrage mit dem Namen **POST - Zugriffstoken abrufen** und klicken Sie auf **Senden**.

Beachten Sie, **unter „Abfrageparameter** zwei Variablen referenziert werden, `API_KEY` und `CLIENT_SECRET`. Diese Variablen werden `--aepUserLdap-- One Adobe OAuth Credential` aus der ausgewählten Umgebung übernommen.

![Postman](./images/ioauth.png){zoomable="yes"}

Bei Erfolg wird eine Antwort mit einem Bearer-Token, einem Zugriffs-Token und einem Ablauffenster im Abschnitt **body** von Postman angezeigt.

![Postman](./images/ioauthresp.png){zoomable="yes"}

Es sollte eine ähnliche Antwort mit den folgenden Informationen angezeigt werden:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| token_type | **Bearer** |
| access_token | **eyJhbGciOiJSUz…** |
| expires_in | **86399** |

Das Adobe I/O **Bearer-Token** hat einen bestimmten Wert (das sehr lange Zugriffs-Token) und ein Gültigkeitsfenster und ist jetzt 24 Stunden lang gültig. Wenn Sie also nach 24 Stunden Postman zur Interaktion mit Adobe-APIs verwenden möchten, müssen Sie ein neues Token generieren, indem Sie diese Anfrage erneut ausführen.

Ihre Postman-Umgebung ist jetzt eingerichtet und funktioniert.

## Nächste Schritte

Gehen Sie zu [Anwendungen zu installieren](./ex9.md){target="_blank"}

Zurück zu [Erste Schritte](./getting-started.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
