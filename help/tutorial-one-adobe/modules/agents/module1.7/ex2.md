---
title: Verwenden des Cursors zur Entwicklung Ihres Projekts
description: Verwenden des Cursors zur Entwicklung Ihres Projekts
kt: 5342
doc-type: tutorial
exl-id: c73498b6-5e08-41b5-81a9-c0a76a6e2792
source-git-commit: 25901342e8d9c46b0edce3b2092b9f1d66ba5849
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 0%

---

# 1.7.2 Verwenden Sie Cursor, um Ihr Projekt zu entwickeln

## 1.7.2.1 Einrichten von Verzeichnis und Tools

Erstellen Sie auf Ihrem Desktop ein neues Verzeichnis mit dem Namen `--aepUserLdap---commerce`

![Commerce und Agent](./images/cursorai1.png)

Klicken Sie mit der rechten Maustaste auf den Ordner und wählen Sie **Neues Terminal unter Ordner**.

![Commerce und Agent](./images/cursorai2.png)

Sie sollten das dann sehen.

![Commerce und Agent](./images/cursorai3.png)

Sie müssen jetzt ein vorhandenes GitHub-Repository klonen, das Sie anzeigen können [https://github.com/adobe/commerce-integration-starter-kit](https://github.com/adobe/commerce-integration-starter-kit).

Dieses Repository ist das Integrations-Starter-Kit von Adobe, das Adobe Developer App Builder verwendet, um die Verbindungszuverlässigkeit in Echtzeit zu verbessern und die Time-to-Market für Integrationen zwischen Adobe Commerce und anderen Back-Office-Systemen wie ERPs, CRMs und PIMs zu reduzieren.

![Commerce und Agent](./images/cursorai4.png)

Es gibt mehrere Möglichkeiten, dieses Repository zu klonen, in diesem Beispiel wird Terminal verwendet.

Geben Sie den folgenden Befehl in Ihr Terminal-Fenster ein und führen Sie ihn aus.

`git clone https://github.com/adobe/commerce-integration-starter-kit`

![Commerce und Agent](./images/cursorai5.png)

Nach einigen Sekunden sollten Sie dieses Ergebnis sehen.

![Commerce und Agent](./images/cursorai6.png)

Als Nächstes sollten Sie zum soeben erstellten Ordner navigieren. Geben Sie den folgenden Befehl ein und führen Sie ihn dann aus.

`cd commerce-integration-starter-kit`

![Commerce und Agent](./images/cursorai7.png)

Sie sollten das dann sehen.

![Commerce und Agent](./images/cursorai8.png)

Als Nächstes müssen Sie die Commerce-Erweiterbarkeits-Tools für Cursor einrichten. Geben Sie den folgenden Befehl ein und führen Sie ihn dann aus.

`aio commerce extensibility tools-setup`

![Commerce und Agent](./images/cursorai9.png)

Wählen Sie **Aktuelles Verzeichnis** aus.

![Commerce und Agent](./images/cursorai10.png)

Wählen Sie **Cursor**.

![Commerce und Agent](./images/cursorai11.png)

Wählen Sie **npm** aus.

![Commerce und Agent](./images/cursorai12.png)

Nach ein paar Minuten sollten Sie das hier sehen.

![Commerce und Agent](./images/cursorai13.png)

Durch die Installation der Commerce-Erweiterbarkeits-Tools für den Cursor steht nun ein MCP-Server als Teil Ihrer Cursor-Umgebung zur Verfügung. In den nächsten Übungen verwenden Sie diesen MCP-Server, um das App Builder-Projekt zu entwickeln und bereitzustellen.

## 1.7.2.2 Webhook einrichten

Für diese Übung benötigen Sie einen Webhook, der so konfiguriert werden muss, dass bei der Erstellung einer Bestellung das Auftragsereignis an diesen Webhook gestreamt werden kann. In dieser Übung verwenden Sie einen Beispielendpunkt mit [https://pipedream.com/requestbin](https://pipedream.com/requestbin).

Wechseln Sie zu [https://pipedream.com/requestbin](https://pipedream.com/requestbin), erstellen Sie ein Konto und dann einen Arbeitsbereich. Nachdem der Arbeitsbereich erstellt wurde, sehen Sie etwas Ähnliches.

Klicken Sie **Kopieren**, um die URL zu kopieren. Sie müssen diese URL in der nächsten Übung angeben. Die URL in diesem Beispiel lautet `https://eodts05snjmjz67.m.pipedream.net`.

![Cursor + Commerce](./images/webhook1.png)

## 1.7.2.3 App mit Cursor erstellen

Cursor öffnen. Klicken Sie **Projekt öffnen**.

![Cursor + Commerce](./images/cursorai14.png)

Navigieren Sie zu dem von Ihnen erstellten Ordner, der `--aepUserLdap---commerce` benannt werden sollte. Wählen Sie in diesem Ordner den Ordner aus, der `commerce-integration-starter-kit` heißt. Klicken Sie auf **Öffnen**.

![Cursor + Commerce](./images/cursorai15.png)

Sie sollten das dann sehen. Stellen Sie vor dem Fortfahren sicher, dass der Ordner der obersten Ebene, der in Cursor geöffnet ist, `commerce-integration-starter-kit` ist.

![Cursor + Commerce](./images/cursorai16.png)

Verwenden Sie den Tastaturbefehl `Cmd + Shift + J`, um die Cursor-Einstellungen zu öffnen. Sie sollten das dann sehen. Navigieren Sie zu **Tools und MCP**.

![Cursor + Commerce](./images/cursorai17.png)

Aktivieren Sie den MCP-Server **commerce-extensibility**. Klicken Sie anschließend auf das **X**, um das Fenster zu schließen.

![Cursor + Commerce](./images/cursorai18.png)

Kopieren Sie die folgende Eingabeaufforderung und fügen Sie sie in den Cursor ein. Klicken Sie dann auf die Schaltfläche **Senden**.

`I would like to build an app that subscribes to order created events and sends them to a configurable URL with basic authentication`

![Cursor + Commerce](./images/cursorai19.png)

Der Cursor beginnt mit dem Denken und der Ausführung. Der Cursor wird Sie einige Male um Bestätigung bitten. Klicken Sie dann auf **Ausführen**. Dies kann je nach den Überlegungen und Ihren Einstellungen 5 bis 10 Mal passieren.

![Cursor + Commerce](./images/cursorai20.png)

Nach ein paar Minuten sollten Sie so etwas sehen.

![Cursor + Commerce](./images/cursorai21.png)

Der nächste Schritt besteht darin, wie vom Cursor angegeben, eine Datei mit dem Namen `.env` zu erstellen und dort die erforderlichen Variablen anzugeben.

## 1.7.2.4 Erstellen der Datei .env

Wählen Sie die Datei **env.dist** aus. Geben Sie den `Cmd + C` und dann den `Cmd + V` ein.

![Cursor + Commerce](./images/cursorai22.png)

Benennen Sie die neu erstellte Datei in `.env` um.

![Cursor + Commerce](./images/cursorai23.png)

Als Nächstes müssen Sie die Werte für alle Variablen in der Datei **.env** angeben.

![Cursor + Commerce](./images/cursorai24.png)

Hier finden Sie alle erforderlichen Informationen.

### Commerce-Endpunkte

Diese Variablen finden Sie unter [https://experience.adobe.com](https://experience.adobe.com). Auf **Commerce**.

![Cursor + Commerce](./images/cursorai25.png)

Sie sollten das dann sehen. Klicken Sie auf **information**-Symbol neben Ihrer ACS-Umgebung, die `--aepUserLdap-- - ACCS` benannt werden sollte. Kopieren Sie die Werte des REST-Endpunkts und des GraphQL-Endpunkts.

In diesem Beispiel sind dies die Werte, die kopiert werden sollen. Fügen Sie sie neben den folgenden Variablen in die Datei **.env in** Zeilen 6 und 7 ein.


- **COMMERCE_BASE_URL** = https://na1-sandbox.api.commerce.adobe.com/Lkp3U7tvTBNAmpFvwnZJ4B/
- **COMMERCE_GRAPHQL_ENDPOINT** = https://na1-sandbox.api.commerce.adobe.com/Lkp3U7tvTBNAmpFvwnZJ4B/graphql

![Cursor + Commerce](./images/cursorai26.png)

Sie sollten dies dann in der Datei **.env** haben.

![Cursor + Commerce](./images/cursorai26a.png)

### Adobe I/O-Projektvariablen

Diese Variablen finden Sie unter [https://developer.adobe.com/console](https://developer.adobe.com/console). Navigieren Sie **Projekte** und klicken Sie, um das in der vorherigen Übung erstellte Adobe I/O-Projekt zu öffnen, das `--aepUserLdap-- Commerce Events` benannt werden sollte.

![Cursor + Commerce](./images/cursorai27.png)

Wechseln Sie zu **Produktion**.

![Cursor + Commerce](./images/cursorai28.png)

Wechseln Sie zu **OAuth Server-zu-Server**. Sie sollten das dann sehen.

![Cursor + Commerce](./images/cursorai29.png)

Kopieren Sie die Werte der Felder **Client-ID**, **Client-Geheimnis**, **ID des technischen Kontos**, **E-Mail-Adresse des technischen Kontos** und **Organisations-ID** und fügen Sie sie neben den folgenden Variablen in die Datei **.env** in den Zeilen 13-17 ein.

- **OAUTH_CLIENT_ID**= **Client ID**
- **OAUTH_CLIENT_SECRET**= **Client-Geheimnis**
- **OAUTH_TECHNICAL_ACCOUNT_ID**= (ID **technischen Kontos**
- **OAUTH_TECHNICAL_ACCOUNT_EMAIL**= **E-MAIL-ADRESSE DES TECHNISCHEN KONTOS**
- **OAUTH_ORG_ID**= **ORGANISATIONS-ID**

Sie sollten dies dann in der Datei **.env** haben.

![Cursor + Commerce](./images/cursorai29a.png)

### COMMERCE_ADOBE_IO_EVENTS_MERCHANT_ID

Geben Sie für das Feld **COMMERCE_ADOBE_IO_EVENTS_MERCHANT_ID=** den Wert `--aepUserLdap--_commerce_events` in Zeile 34 in der Datei **.env** ein.

Sie sollten dies dann in der Datei **.env** haben.

![Cursor + Commerce](./images/cursorai30.png)

### Workspace-Konfigurationen

Um diese Variablen abzurufen, gehen Sie zurück zu Ihrem Adobe I/O-Projekt und klicken Sie auf **Übersicht über Workspace**.

Nachdem Sie zur **Übersicht über Workspace** gewechselt haben, sollten Sie sich die URL ansehen, die wie folgt aussehen sollte: **https://developer.adobe.com/console/projects/133309/4566206088345586770/workspaces/4566206088345619105/details**.

Die erste Zahl in diesem Beispiel, 133309, ist der Wert, der für das Feld **IO_CONSUMER_ID“ verwendet**.
Die zweite Zahl in diesem Beispiel, 4566206088345586770, ist der Wert, der für das Feld **IO_PROJECT_ID“ verwendet**.
Die dritte Zahl in diesem Beispiel, 4566206088345619105, ist der Wert, der für das Feld **IO_WORKSPACE_ID“ verwendet**.

![Cursor + Commerce](./images/cursorai31.png)

- **IO_CONSUMER_ID**= 133309
- **IO_PROJECT_ID**= 4566206088345586770
- **IO_WORKSPACE_ID**= 4566206088345619105

Kopieren Sie diese Werte und fügen Sie sie neben den folgenden Variablen in die Datei **.env** in den Zeilen 42-44 ein.

![Cursor + Commerce](./images/cursorai32.png)

### EVENT_PREFIX

Geben Sie für das Feld **EVENT_PREFIX =** den Wert `--aepUserLdap--_` Zeile 47 in der Datei **.env** ein.

Sie sollten dies dann in der Datei **.env** haben.

![Cursor + Commerce](./images/cursorai33.png)

### Webhook

Für das Feld **ORDER_WEBHOOK_URL** sollten Sie die URL des zuvor in dieser Übung erstellten Webhooks einfügen, der wie folgt aussehen sollte: `https://eodts05snjmjz67.m.pipedream.net`.

Sie sollten dies dann in der Datei **.env** haben.

![Cursor + Commerce](./images/cursorai34.png)

### App Builder-Anmeldedaten

Sie sollten die folgenden Variablen in der Datei **.env** in den Zeilen 54-55 aktualisieren:

- **AIO_RUNTIME_NAMESPACE**=
- **AIO_RUNTIME_AUTH**=

Sie können die Werte für diese Variablen abrufen, indem Sie zu Ihrem Adobe I/O-Projekt zurückkehren. Gehen Sie zu **Übersicht über Workspace** und klicken Sie auf **Alle herunterladen**.

![Cursor + Commerce](./images/cursorai35.png)

Eine Datei wie diese wird dann heruntergeladen. Öffnen Sie diese Datei mit einem Texteditor.

![Cursor + Commerce](./images/cursorai36.png)

Scrollen Sie nach rechts, bis Sie **runtime** sehen. Anschließend sollte das Feld **name** angezeigt werden, das den Wert für **AIO_RUNTIME_NAMESPACE** enthält.

![Cursor + Commerce](./images/cursorai37.png)

Scrollen Sie weiter nach rechts, bis Sie **auth** sehen, das den Wert für **AIO_RUNTIME_AUTH** enthält.

![Cursor + Commerce](./images/cursorai38.png)

Fügen Sie beide Werte in die Datei **.env** in die Zeilen 54-55 ein. Sie sollten dann über dieses verfügen.

![Cursor + Commerce](./images/cursorai39.png)

Ihre **.env**-Datei ist jetzt vollständig konfiguriert.

## 1.7.2.5 workspace.json

Im vorherigen Schritt haben Sie eine Datei wie diese aus Ihrem Adobe I/O-Projekt heruntergeladen.

![Cursor + Commerce](./images/cursorai36.png)

Benennen Sie diese Datei um und verwenden Sie den Namen `workspace.json`.

![Cursor + Commerce](./images/cursorai40.png)

Kopieren Sie die Datei in das Verzeichnis **scripts**>**onboarding**>**config**.

![Cursor + Commerce](./images/cursorai41.png)

## 1.7.2.6 Adobe I/O-Anmeldung

Navigieren Sie zurück zum Terminal-Fenster, das Sie zuvor verwendet hatten. Geben Sie den `aio login` ein.

![Cursor + Commerce](./images/cursorai44.png)

Dies sollte Ihnen dann nach der Anmeldung über Ihren Browser angezeigt werden.

![Cursor + Commerce](./images/cursorai45.png)

## 1.7.2.7 bereit zur Bereitstellung

Kopieren Sie die folgende Eingabeaufforderung und fügen Sie sie in den Cursor ein. Klicken Sie dann auf die Schaltfläche **Senden**.

`Please deploy this code to Adobe I/O`

![Cursor + Commerce](./images/cursorai42.png)

Klicken Sie **Ausführen**, um die Aktion zuzulassen. Der Cursor bittet Sie möglicherweise mehrmals, eine Aktion zu bestätigen.

![Cursor + Commerce](./images/cursorai43.png)

Die Bereitstellung ist dann nach einigen Minuten abgeschlossen.

![Cursor + Commerce](./images/cursorai46.png)

Kopieren Sie die folgende Eingabeaufforderung und fügen Sie sie in den Cursor ein. Klicken Sie dann auf die Schaltfläche **Senden**.

`run the onboarding to commerce`

![Cursor + Commerce](./images/cursorai50.png)

Nach ein paar Minuten sollten Sie das hier sehen.

![Cursor + Commerce](./images/cursorai51.png)

Kopieren Sie die folgende Eingabeaufforderung und fügen Sie sie in den Cursor ein. Klicken Sie dann auf die Schaltfläche **Senden**.

`subscribe to commerce events`

![Cursor + Commerce](./images/cursorai47.png)

Nach ein paar Minuten sollten Sie das hier sehen.

![Cursor + Commerce](./images/cursorai49.png)

## 1.7.2.8 Konfiguration in Adobe Commerce as a Cloud Service überprüfen

Navigieren Sie zu [https://experience.adobe.com](https://experience.adobe.com). Auf **Commerce**.

![Cursor + Commerce](./images/cursorai60.png)

Klicken Sie auf Ihre Adobe Commerce as a Cloud Service-Umgebung, um sie zu öffnen, und melden Sie sich an.

![Cursor + Commerce](./images/cursorai61.png)

Navigieren Sie **System** und dann zu **Ereignisabonnements**.

![Cursor + Commerce](./images/cursorai62.png)

Sie sollten dann diese Liste der Ereignisabonnements sehen.

![Cursor + Commerce](./images/cursorai63.png)

Wechseln Sie zu **Stores** und dann zu **Configuration**.

![Cursor + Commerce](./images/cursorai64.png)

Navigieren Sie zu **Adobe Services** und wählen Sie **Adobe I/O Events** aus. Anschließend sollten Sie sehen, dass das Feld **Adobe I/O Workspace** Konfigurationeinen Wert von einigen Asterisken hat und das Feld **Händler-ID** auch einen Wert wie `--aepUserLdap--_commerce_events` haben sollte.

![Cursor + Commerce](./images/cursorai65.png)

Mit dieser Konfiguration können Sie jetzt Ihre Konfiguration testen.

## 1.7.2.9 Testen des Szenarios

Öffnen Sie Ihre Website.

![Cursor + Commerce](./images/cursorai101.png)

Navigieren Sie zu **Uhren** und klicken Sie auf ein beliebiges Produkt.

![Cursor + Commerce](./images/cursorai102.png)

Konfigurieren Sie das Produkt und klicken Sie auf **Zum Warenkorb hinzufügen**.

![Cursor + Commerce](./images/cursorai103.png)

Klicken Sie auf **Warenkorb** und wählen Sie **Checkout** aus.

![Cursor + Commerce](./images/cursorai104.png)

Füllen Sie Ihre Daten aus und klicken Sie auf **Bestellung aufgeben**.

![Cursor + Commerce](./images/cursorai105.png)

Anschließend sollte eine Bestellbestätigung angezeigt werden.

![Cursor + Commerce](./images/cursorai106.png)

Wechseln Sie zu Ihrer Webhook-Anwendung. Sie sollten jetzt ein eingehendes Ereignis für die gerade bestätigte Bestellung sehen.

![Cursor + Commerce](./images/cursorai107.png)

## 1.7.2.10 des Adobe I/O-Debuggens

Kehren Sie zu Ihrem Adobe I/O-Projekt zurück. Zur Übersicht über **Workspace**. Sie sollten etwas Ähnliches sehen. Scroll ein bisschen nach unten.

![Cursor + Commerce](./images/cursorai108.png)

Klicken, um **Commerce Order Sync** zu öffnen.

![Cursor + Commerce](./images/cursorai109.png)

Navigieren Sie zu **Debug-Ablaufverfolgung**. Dort finden Sie die neuesten eingehenden Ereignisse zusammen mit ihrer Payload. Dies ist hilfreich, um zu verstehen, welche Ereignisse verarbeitet wurden und ob sie erfolgreich verarbeitet wurden.

![Cursor + Commerce](./images/cursorai110.png)

## Nächste Schritte

Zurück zu [Intelligent Developer Tools for Adobe Commerce](./aiassisteddev.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
