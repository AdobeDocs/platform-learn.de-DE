---
title: Überwachen von Ereignissen in Slack
description: Erfahren Sie, wie Sie Experience Platform-Benachrichtigungen in Slack erhalten, indem Sie sie mit einem Adobe App Builder-Webhook-Proxy integrieren.
feature: Monitoring
role: Developer, Admin
level: Intermediate
duration: 519
last-substantial-update: 2026-02-24T00:00:00Z
jira: KT-20339
exl-id: 6d4a072c-9eef-4a38-9459-9e1cbd66bfb5
source-git-commit: 4ec7a800ef963f9b1257e2f246428abff32e9b94
workflow-type: tm+mt
source-wordcount: '1539'
ht-degree: 0%

---

# Überwachen von Experience Platform-Ereignissen in Slack

Erfahren Sie, wie Sie Experience Platform-Benachrichtigungen in Slack erhalten, indem Sie sie mit einem Adobe App Builder-Webhook-Proxy integrieren. Dateningenieure und Administratoren möchten möglicherweise proaktive Benachrichtigungen in Slack von Adobe Experience Platform erhalten, um den Zustand ihrer Platform-Implementierungen zu überwachen. In diesem Tutorial werden die Architektur und Implementierungsschritte zum Verbinden von Adobe I/O Events mit Slack mithilfe von Adobe App Builder beschrieben.


>[!VIDEO](https://video.tv.adobe.com/v/3480183?learn=on)

## Warum ein Webhook-Proxy?

Das direkte Verbinden von Adobe I/O Events mit einem eingehenden Slack-Webhook ist aufgrund einer Protokollabweichung im Verifizierungsprozess nicht möglich.

* **Die Herausforderung**: Wenn Sie einen Webhook bei Adobe I/O Events registrieren, sendet Adobe eine „Challenge“-Anfrage (entweder eine `GET` oder eine `POST`) an Ihren Endpunkt. Ihr Endpunkt muss diese Herausforderung erfolgreich verarbeiten und den spezifischen Wert zurückgeben, um die Eigentümerschaft zu bestätigen.

* **Die Einschränkung**: Die eingehenden Webhooks von Slack sind nur für die Aufnahme von JSON-Payloads für Messaging konzipiert. Sie haben keine Logik, um den Verifizierungs-Handshake von Adobe zu erkennen oder darauf zu reagieren.

* **Die Lösung**: Bereitstellen eines Webhook-Zwischen-Proxys mit Adobe App Builder. Dieser Proxy befindet sich zwischen Adobe und Slack, um:
   1. Fangen Sie die Anfrage von Adobe ab und reagieren Sie auf die Verifizierungs-Challenge.
   1. Formatieren Sie die Payload in eine Slack-kompatible Nachricht und leiten Sie sie an Slack weiter.

* **Bereitstellungsmethode**: Laufzeitaktionen.  Laufzeitaktionen sind im Lieferumfang von Adobe App Builder enthalten. Bei Verwendung einer Laufzeitaktion (keine Web-Aktion) als Ereignishandler verarbeitet Adobe I/O Events automatisch die Signaturüberprüfung und die Antwort auf die Herausforderung. Laufzeitaktionen sind der empfohlene Ansatz, da sie weniger Code benötigen und integrierte Sicherheit bieten.

## Überblick über die Architektur

### Was ist Adobe Developer Console?

Adobe Developer Console ist das zentrale Portal zur Verwaltung Ihrer Adobe-Projekte, APIs und Berechtigungen. Hier erstellen Sie Ihr Projekt, konfigurieren die Authentifizierung und registrieren Ihre Webhooks.

### Was ist App Builder?

Adobe App Builder ist ein vollständiges Framework, mit dem Unternehmensentwickler Cloud-native Programme erstellen können.

* **Bereitstellung**: App Builder ist nicht standardmäßig aktiviert. Es muss für Ihr Unternehmen als Funktion bereitgestellt werden. Stellen Sie sicher, dass Ihr Unternehmen über die **[!DNL App Builder]** Berechtigung verfügt.

* **Projektvorlage**: App Builder-Projekte werden speziell mithilfe der Vorlage **[!UICONTROL App Builder]** im [!DNL Developer Console] erstellt ([!UICONTROL Projekt aus Vorlage] > [!UICONTROL App Builder]). Die Vorlage richtet automatisch die erforderlichen Arbeitsbereiche und Laufzeitumgebungen ein.

* **Erste Schritte mit App Builder**: Lesen Sie die Dokumentation [um Ihr erstes Projekt aus der Vorlage bereitzustellen und zu &#x200B;](https://developer.adobe.com/app-builder/docs/get_started/app_builder_get_started/first-app){target=_blank}.

### Was ist Adobe I/O Runtime?

Adobe I/O Runtime ist die Server-lose Plattform für App Builder. Dadurch können Entwickler Code (Functions-as-a-Service) bereitstellen, der als Reaktion auf HTTP-Anfragen ausgeführt wird, ohne die Server-Infrastruktur zu verwalten.

In dieser Implementierung verwenden wir eine **Aktion**. Eine Aktion ist eine statuslose Funktion (geschrieben in Node.js), die auf der Adobe I/O Runtime ausgeführt wird. Unsere Aktion dient als öffentlicher HTTP-Endpunkt, mit dem Adobe I/O Events kommuniziert.

Weitere Informationen finden Sie in der Dokumentation zu [Adobe I/O Runtime](https://developer.adobe.com/runtime/){target=_blank}.

## Implementierungshandbuch

### Voraussetzungen

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* **Zugriff auf Adobe Developer Console**: Sie müssen Zugriff auf eine Systemadministrator- oder [Entwicklerrolle](../admin/add-developers.md) innerhalb eines Unternehmens haben, für das App Builder aktiviert ist.

  >[!TIP]
  > Um die Bereitstellung von App Builder zu überprüfen, melden Sie sich bei [Adobe Developer Console](https://developer.adobe.com/console/){target=_blank} an, stellen Sie sicher, dass Sie sich in der gewünschten Organisation befinden, wählen Sie **[!UICONTROL Projekt aus Vorlage erstellen]** und stellen Sie sicher, dass die App Builder-Vorlage verfügbar ist. Ist dies nicht der Fall, lesen Sie bitte den Abschnitt „Häufig gestellte Fragen zu App Builder[&#x200B; „So erhalten Sie App Builder](https://developer.adobe.com/app-builder/docs/intro_and_overview/faq#how-to-get-app-builder){target=_blank}&quot;


* **Node.js &amp; npm**: Dieses Projekt erfordert Node.js, das NPM (Node Package Manager) enthält. NPM wird verwendet, um die Adobe-CLI zu installieren und Projektabhängigkeiten zu verwalten.

   * [Node.js herunterladen (LTS-Version empfohlen)](https://nodejs.org/){target=_blank}
   * [npm Getting Started Guide](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm){target=_blank} - Eine Anleitung zur Überprüfung Ihrer Installation.

* **`aio CLI`**: Über Ihr Terminal installiert: `npm install -g @adobe/aio-cli`
* **Slack-App-Konfiguration**: Sie müssen eine Slack-App in Ihrem Arbeitsbereich einrichten und einen **Incoming Webhook** aktivieren.

   * [Erstellen einer Slack-App](https://api.slack.com/apps){target=_blank}
   * [Handbuch zu eingehenden Webhooks für Slack](https://docs.slack.dev/messaging/sending-messages-using-incoming-webhooks/){target=_blank} - Folgen Sie diesem Handbuch, um Ihre App zu erstellen und die Webhook-URL zu generieren (beginnt mit `https://hooks.slack.com/`…).

### Schritt 1: Erstellen eines Projekts in Adobe Developer Console

Erstellen Sie zunächst ein Projekt mit der App Builder-Vorlage in Adobe Developer Console:

1. Anmelden bei [Adobe Developer Console](https://developer.adobe.com/console)
1. Wählen Sie **[!UICONTROL Projekt aus Vorlage erstellen]**
1. App Builder-Vorlage auswählen
1. Geben Sie einen Projekttitel ein, z. B. `Slack webhook integration`
1. Wählen Sie **[!UICONTROL Speichern]**

### Initialisieren der Laufzeitumgebung

Führen Sie die folgenden Befehle in Ihrem Terminal aus, um die Projektstruktur zu erstellen:

#### Anmelden bei `aio`

```
aio login
```

#### Schritt 2: Initialisieren eines neuen App Builder-Projekts

```
aio app init slack-webhook-proxy
```

1. Wählen Sie Ihre Organisation aus und drücken Sie **Eingabetaste**
1. Wählen Sie das Projekt aus, das Sie im vorherigen Schritt erstellt haben (z. B. `Slack webhook integration`), und drücken Sie die **Eingabetaste**
1. Wählen Sie die Option **[!UICONTROL Nur von meiner Organisation unterstützte Vorlagen]** aus
1. Überspringen Sie den Beispielabschnitt, indem Sie die **Eingabetaste** drücken
1. Stellen Sie bei Aufforderung sicher, dass die folgenden Komponenten ausgewählt sind (der Kreis sollte ausgefüllt sein) und drücken Sie die **Eingabetaste**:
   1. **[!UICONTROL Aktionen: Laufzeitaktionen bereitstellen]**
   1. **[!UICONTROL Ereignisse: In Adobe I/O Events veröffentlichen]**
   1. **[!UICONTROL Web Assets: Bereitstellen für gehostete statische Assets]**
1. Navigieren Sie mit den Pfeilen „Nach oben“ und „Nach unten“ durch die eingehende Liste, wählen Sie **[!UICONTROL Adobe Experience Platform: Echtzeit-Kundenprofil aus]** drücken Sie die **Eingabetaste**
1. **[!UICONTROL Generisch]** Aktionen werden automatisch generiert
1. Wählen Sie &quot;**[!UICONTROL HTML/JS]** für die Benutzeroberfläche aus und drücken Sie die **Eingabetaste**
1. Behalten Sie **[!UICONTROL generisch]** als Beispielaktion bei, um zu demonstrieren, wie auf einen externen API-Namen zugegriffen werden kann, und drücken Sie die **Eingabetaste**
1. Behalten Sie **[!UICONTROL publish-events]** als Beispielaktionsnamen bei, um Nachrichten im Cloud-Ereignisformat zu erstellen, und drücken Sie die **Eingabetaste**

Die App-Initialisierung sollte abgeschlossen sein.

#### Navigieren Sie zum Projektverzeichnis

```
cd slack-webhook-proxy
```

#### Hinzufügen der Web-Aktion

```
aio app add action
```

1. Wählen Sie **[!UICONTROL Nur Vorlagen, die von meiner Organisation unterstützt werden]** und drücken Sie die **Eingabetaste**
2. Siehe die Aktion **[!UICONTROL publish-events]** in der angezeigten Tabelle; drücken Sie **Leertaste**, um die Aktion auszuwählen. Wenn der Kreis neben dem Namen ausgefüllt ist, wie im Video-Tutorial gezeigt, drücken Sie die **Eingabetaste**
3. Benennen Sie die `webhook-proxy`

### Schritt 3: Proxy-Aktionscode aktualisieren

Erstellen/ändern Sie in einer IDE oder einem Texteditor den `actions/webhook-proxy/index.js` mit folgendem Code. Diese Implementierung leitet Ereignisse an Slack weiter. Die Signaturüberprüfung und die Verarbeitung von Challenges erfolgen bei Verwendung der Laufzeitaktionsregistrierung automatisch.

```javascript
const fetch = require("node-fetch");
const { Core } = require("@adobe/aio-sdk");
 
/**
 * Adobe I/O Events to Slack Runtime Proxy
 *
 * Receives events from Adobe I/O Events and forwards them to Slack.
 * Signature verification and challenge handling are automatic when
 * using Runtime Action registration (non-web action).
 */
async function main(params) {
  const logger = Core.Logger("webhook-proxy", { level: params.LOG_LEVEL || "info" });
 
  try {
    logger.info(`Event received: ${JSON.stringify(params)}`);
 
    // Forward to Slack
    return forwardToSlack(params, params.SLACK_WEBHOOK_URL, logger);
 
  } catch (error) {
    logger.error(`Error: ${error.message}`);
    return { statusCode: 500, body: { error: "Internal server error" } };
  }
}
 
/**
 * Forwards the event payload to Slack
 */
async function forwardToSlack(payload, webhookUrl, logger) {
  if (!webhookUrl) {
    logger.error("SLACK_WEBHOOK_URL not configured");
    return { statusCode: 500, body: { error: "Server configuration error" } };
  }
 
  // Extract Adobe headers passed to runtime action
  const headers = {
    "x-adobe-event-code": payload["x-adobe-event-code"],
    "x-adobe-event-id": payload["x-adobe-event-id"],
    "x-adobe-provider": payload["x-adobe-provider"]
  };
 
  const slackMessage = buildSlackMessage(payload, headers);
 
  const response = await fetch(webhookUrl, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(slackMessage)
  });
 
  if (!response.ok) {
    const errorText = await response.text();
    logger.error(`Slack API error: ${response.status} - ${errorText}`);
    return { statusCode: response.status, body: { error: errorText } };
  }
 
  logger.info("Event forwarded to Slack");
  return { statusCode: 200, body: { success: true } };
}
 
/**
 * Builds a Slack Block Kit message from the event payload
 */
function buildSlackMessage(payload, headers) {
  // Adobe passes event code as x-adobe-event-code header (available in params for runtime actions)
  const eventType = headers["x-adobe-event-code"] ||
                    payload["x-adobe-event-code"] ||
                    payload.event_code ||
                    payload.type ||
                    payload.event_type ||
                    "Adobe Event";
  const eventId = headers["x-adobe-event-id"] || payload["x-adobe-event-id"] || payload.event_id || payload.id || "N/A";
  const eventData = payload.data || payload.event || payload;
 
  return {
    blocks: [
      {
        type: "header",
        text: { type: "plain_text", text: `Event: ${eventType}`, emoji: true }
      },
      {
        type: "section",
        fields: formatDataFields(eventData)
      },
      { type: "divider" },
      {
        type: "context",
        elements: [{
          type: "mrkdwn",
          text: `*Event ID:* ${eventId}  |  *Time:* ${new Date().toISOString()}`
        }]
      }
    ]
  };
}
 
/**
 * Formats event data as Slack mrkdwn fields
 */
function formatDataFields(data, maxFields = 10) {
  if (typeof data !== "object" || data === null) {
    return [{ type: "mrkdwn", text: `*Payload:*\n${String(data)}` }];
  }
 
  const entries = Object.entries(data);
  if (entries.length === 0) {
    return [{ type: "mrkdwn", text: "_No data provided_" }];
  }
 
  return entries.slice(0, maxFields).map(([key, value]) => ({
    type: "mrkdwn",
    text: `*${key}:*\n${typeof value === "object" ? `\`\`\`${JSON.stringify(value)}\`\`\`` : value}`
  }));
}
 
exports.main = main;
```

### Schritt 4: Konfigurieren der Aktion

Die Aktionskonfiguration in `app.config.yaml` ist wichtig. Web verwenden: Nein, um eine Nicht-Web-Aktion zu erstellen, die als Laufzeitaktion in der Developer Console registriert werden kann.

```yaml
application:
  runtimeManifest:
    packages:
      slack-webhook-proxy:
        license: Apache-2.0
        actions:
          webhook-proxy:
            function: actions/webhook-proxy/index.js
            web: no
            runtime: nodejs:22
            inputs:
              LOG_LEVEL: info
              SLACK_WEBHOOK_URL: $SLACK_WEBHOOK_URL
            annotations:
              require-adobe-auth: false
              final: true
```

#### Warum `web: no?`

Wenn Sie eine Nicht-Web-Aktion verwenden und diese über die Option „Laufzeitaktion“ in der Developer Console registrieren, wird Adobe I/O Events automatisch wie folgt konfiguriert:

* Verarbeitet Challenge-Verifizierung (`GET` und `POST`)
* Verifiziert digitale Signaturen, bevor Sie Ihre Aktion aufrufen
* Verkettet eine Signaturüberprüfungsaktion vor der Aktion

Das bedeutet, dass Ihr Code nur die Geschäftslogik (Weiterleitung an Slack) verarbeiten muss.

### Schritt 4: Aktualisieren der Umgebungsvariablen

Um Anmeldeinformationen sicher zu verwalten, verwenden wir Umgebungsvariablen. Erstellen/ändern Sie die `.env`-Datei im Stammverzeichnis Ihres Projekts, um Ihre Slack-Webhook-URL hinzuzufügen. Stellen Sie sicher, dass auf Ihrem System ausgeblendete Dateien angezeigt werden, wenn die `.env` nicht angezeigt wird:

```
# ... other .env file content ...
 
SLACK_WEBHOOK_URL=https://hooks.slack.com/services/YOUR/WEBHOOK/URL
```

### Schritt 5: Bereitstellen der Aktion

Stellen Sie nach dem Festlegen der Umgebungsvariablen die Aktion bereit. Stellen Sie sicher, dass Sie sich im Stammverzeichnis Ihres Projekts befinden, d. h. `slack-webhook-proxy`, wenn Sie diesen Befehl im Terminal ausführen.

```
aio app deploy
```

Ihre Aktion wird in Adobe I/O Runtime bereitgestellt und steht in der Developer Console zur Registrierung zur Verfügung.

### Schritt 6: Aktion in Adobe Developer Console registrieren

Nachdem Ihre Aktion bereitgestellt wurde, registrieren Sie sie als Ziel für Adobe Events.

1. Navigieren Sie zur [Adobe Developer Console &#x200B;](https://developer.adobe.com/console){target=_blank} öffnen Sie Ihr App Builder-Projekt.
1. **[!UICONTROL Workspace auswählen]**
1. Wählen Sie **[!UICONTROL Service hinzufügen]** und wählen Sie **[!UICONTROL Ereignis]** aus.
1. Adobe Experience Platform Wählen Sie **&#x200B;**&#x200B;als Produkt aus.
1. Wählen Sie **[!UICONTROL Platform-]**) als Ereignistyp aus.
1. Wählen Sie die spezifischen Ereignisse (oder alle) aus, über die Sie in Slack benachrichtigt werden möchten, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie oder [erstellen Sie Ihre OAuth-Anmeldedaten](https://experienceleague.adobe.com/de/docs/platform-learn/tutorials/api/platform-api-authentication){target=_blank}.
1. Konfigurieren Sie **[!UICONTROL Details zur Ereignisregistrierung]**:
   1. **[!UICONTROL Registrierungsname]**: Geben Sie Ihrer Registrierung einen beschreibenden Namen.
   1. **[!UICONTROL Registrierungsbeschreibung]**: Stellen Sie sicher, dass dies explizit ist, damit andere Mitwirkende wissen, was es tut.
   1. Wählen Sie **[!UICONTROL Weiter]**
   1. **[!UICONTROL Bereitstellungsmethode]**: Wählen Sie **[!UICONTROL Laufzeitaktion]** (nicht „Webhook„) aus.
   1. **[!UICONTROL Laufzeitaktion]** Wählen Sie `webhook-proxy` aus dem Dropdown-Menü aus (aktualisieren Sie die Seite, wenn Sie sie nicht sehen).
1. Wählen Sie **[!UICONTROL Konfigurierte Ereignisse speichern]** aus.


### Schritt 7: Mit einem Beispielereignis validieren

Sie können den gesamten Fluss End-to-End testen, indem Sie auf das Symbol „Beispielereignis senden“ neben einem konfigurierten Ereignis klicken.

Das Beispielereignis wird über den Kanal gesendet, den Sie beim Erstellen Ihrer Slack-App und des Webhooks konfiguriert haben. Es sollte etwas Ähnliches wie das folgende angezeigt werden:

![Beispiel für ein Überwachungsereignis in Slack](../assets/slack-monitor.png)

Herzlichen Glückwunsch, Sie haben Slack erfolgreich in Experience Platform Events integriert!

### Häufige Probleme

Im Folgenden finden Sie einige Probleme, auf die Sie bei der Konfiguration des Proxys stoßen können, sowie einige potenzielle Möglichkeiten, diese zu beheben.

* **IMS-Organisationen werden nicht angezeigt**: Wenn Ihre Liste der IMS-Organisationen bei der Ausführung nicht angezeigt wird, `aio app init` versuchen Sie Folgendes. Führen Sie `aio logout` in Ihrem Terminal aus, melden Sie sich bei Experience Cloud im Standard-Webbrowser ab und führen Sie `aio login` erneut aus.
* **Aktion wird nicht im Dropdown-** angezeigt: Stellen Sie sicher, dass `web: no` in `app.config.yaml` festgelegt ist. Im Dropdown-Menü Laufzeitaktion werden nur Nicht-Web-Aktionen angezeigt. Aktualisieren Sie die Developer Console-Seite nach der Bereitstellung.
* **Signaturüberprüfung fehlgeschlagen**: Wenn Sie dies in den Aktivierungsprotokollen sehen, bedeutet dies, dass der integrierte Validator von Adobe die Anfrage abgelehnt hat. Dies sollte nicht für legitime Adobe-Ereignisse geschehen. Überprüfen Sie, ob die Ereignisregistrierung korrekt konfiguriert ist.
* **Slack erhält keine Nachrichten**: Vergewissern Sie sich, dass `SLACK_WEBHOOK_URL` in Ihrer `.env` korrekt festgelegt ist und dass der eingehende Webhook für die Slack-App aktiviert ist.
* **Zeitüberschreitung bei Aktion**: Bei Laufzeitaktionen beträgt die Zeitüberschreitung 60 Sekunden. Wenn Ihre Aktion länger dauert, sollten Sie stattdessen den Journalansatz verwenden.
