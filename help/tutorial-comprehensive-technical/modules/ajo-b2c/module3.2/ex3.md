---
title: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Definieren benutzerdefinierter Aktionen
description: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Definieren benutzerdefinierter Aktionen
kt: 5342
doc-type: tutorial
exl-id: d9bdc4c6-7539-4646-9b75-f397b792479f
source-git-commit: c531412a2c0a5c216f49560e01fb26b9b7e71869
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 3%

---

# 3.2.3 Definieren einer benutzerdefinierten Aktion

In dieser Übung erstellen Sie eine benutzerdefinierte Aktion, um eine Nachricht an einen Slack-Kanal zu senden.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

Sie verwenden jetzt einen vorhandenen Slack-Kanal und senden Nachrichten an diesen Slack-Kanal. Slack verfügt über eine benutzerfreundliche API, und Sie werden Adobe Journey Optimizer zum Trigger ihrer API verwenden.

![Demo](./images/slack.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend auf die Schaltfläche **Verwalten** unter **Aktionen**.

![Demo](./images/menuactions.png)

Anschließend wird die Liste **Aktionen** angezeigt. Klicken Sie **Aktion erstellen**.

![Demo](./images/acthome.png)

Es wird ein leeres Aktionspopup angezeigt.

![Demo](./images/emptyact.png)

Verwenden Sie `--aepUserLdap--TextSlack` als Namen für die Aktion.

Beschreibung festlegen auf: `Send Message to Slack`.

Verwenden Sie für **URL** Konfiguration Folgendes:

- URL: `https://2mnbfjyrre.execute-api.us-west-2.amazonaws.com/prod`
- Methode: **POST**

>[!NOTE]
>
>Die obige URL bezieht sich auf eine AWS Lambda-Funktion, die Ihre Anfrage dann wie oben beschrieben an den Slack-Kanal weiterleitet. Dies dient dem Schutz des Zugriffs auf einen Adobe-eigenen Slack-Kanal. Wenn Sie über einen eigenen Slack-Kanal verfügen, sollten Sie eine Slack-App über [https://api.slack.com/](https://api.slack.com/) erstellen. Erstellen Sie dann in dieser Slack-App einen eingehenden Webhook und ersetzen Sie dann die obige URL durch Ihre eingehende Webhook-URL.

![Demo](./images/slackname.png)

Sie müssen die Header-Felder nicht ändern.

![Demo](./images/slackurl.png)

**Authentifizierung** sollte auf &quot;**Authentifizierung“** werden.

![Demo](./images/slackauth.png)

Unter **Payloads** müssen Sie definieren, welche Felder zum Slack gesendet werden sollen. Logischerweise möchten Sie, dass Adobe Journey Optimizer und Adobe Experience Platform das Gehirn der Personalisierung sind. Daher sollte der Text, der an Slack gesendet wird, von Adobe Journey Optimizer definiert und dann zur Ausführung an Slack gesendet werden.

Klicken Sie für **Anfrage** auf das Symbol **Payload bearbeiten**.

![Demo](./images/slackmsgp.png)

Daraufhin wird ein leeres Popup-Fenster angezeigt.

![Demo](./images/slackmsgpopup.png)

Kopieren Sie den unten stehenden Text und fügen Sie ihn in das leere Popup-Fenster ein.

```json
{
 "text": {
  "toBeMapped": true,
  "dataType": "string",
  "label": "textToSlack"
 }
}
```

Sie sehen dann Folgendes:

![Demo](./images/slackmsgpopup1.png)

Scrollen Sie nach oben und klicken Sie noch **auf** Speichern“, um Ihre Aktion zu speichern.

![Demo](./images/slackmsgpopup3.png)

Ihre benutzerdefinierte Aktion ist jetzt Teil der Liste **Aktionen** .

![Demo](./images/slackdone.png)

Sie haben Ereignisse, externe Datenquellen und Aktionen definiert. Lassen Sie uns das alles in einer Journey zusammenfassen.

Nächster Schritt: [3.2.4 Erstellen Sie Ihren Journey und Ihre Nachrichten](./ex4.md)

[Zurück zum Modul 3.2](journey-orchestration-external-weather-api-sms.md)

[Zurück zu „Alle Module“](../../../overview.md)
