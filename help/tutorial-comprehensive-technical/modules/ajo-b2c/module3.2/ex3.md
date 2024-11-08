---
title: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Definition benutzerdefinierter Aktionen
description: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Definition benutzerdefinierter Aktionen
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 3%

---

# 3.2.3 Benutzerdefinierte Aktion definieren

In dieser Übung erstellen Sie zwei benutzerdefinierte Aktionen, indem Sie Adobe Journey Optimizer in Kombination verwenden.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der Ansicht **Home** Ihrer Sandbox `--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend unter **Aktionen** auf die Schaltfläche **Verwalten** .

![Demo](./images/menuactions.png)

Daraufhin wird die Liste **Aktionen** angezeigt.

![Demo](./images/acthome.png)

Sie definieren eine Aktion, die einen Text an einen Slack-Kanal sendet.

## 3.2.3.1 Aktion: Text an Slack-Kanal senden

Sie verwenden jetzt einen vorhandenen Slack-Kanal und senden Nachrichten an diesen Slack-Kanal. Slack verfügt über eine benutzerfreundliche API, und wir verwenden Adobe Journey Optimizer zum Trigger ihrer API.

![Demo](./images/slack.png)

Klicken Sie auf **Aktion erstellen** , um eine neue Aktion hinzuzufügen.

![Demo](./images/adda.png)

Es wird ein leeres Action-Popup angezeigt.

![Demo](./images/emptyact.png)

Verwenden Sie als Namen für die Aktion `--aepUserLdap--TextSlack`. In diesem Beispiel lautet der Aktionsname `vangeluwTextSlack`.

Legen Sie für Beschreibung den Wert `Send Text to Slack` fest.

![Demo](./images/slackname.png)

Verwenden Sie für die **URL-Konfiguration** Folgendes:

- URL: `https://2mnbfjyrre.execute-api.us-west-2.amazonaws.com/prod`
- Methode: **POST**

>[!NOTE]
>
>Die obige URL bezieht sich auf eine AWS-Lambda-Funktion, die Ihre Anfrage dann wie oben erwähnt an den Slack-Kanal weiterleitet. Dies geschieht, um den Zugriff auf einen Slack-Kanal zu schützen, der sich im Besitz der Adobe befindet. Wenn Sie über einen eigenen Slack-Kanal verfügen, sollten Sie eine Slack-App über [https://api.slack.com/](https://api.slack.com/) erstellen, dann müssen Sie einen eingehenden Webhook in dieser Slack-App erstellen und dann die oben genannte URL durch Ihre eingehende Webhook-URL ersetzen.

Sie müssen die Kopfzeilenfelder nicht ändern.

![Demo](./images/slackurl.png)

**Authentifizierung** sollte auf **Keine Authentifizierung** eingestellt sein.

![Demo](./images/slackauth.png)

Für die **Aktionsparameter** müssen Sie definieren, welche Felder an Slack gesendet werden sollen. Logischerweise möchten wir, dass Adobe Journey Optimizer und Adobe Experience Platform das Gehirn der Personalisierung sind. Daher sollte der an Slack zu sendende Text von Adobe Journey Optimizer definiert und zur Ausführung an Slack gesendet werden.

Klicken Sie daher für die **Aktionsparameter** auf das Symbol **Payload bearbeiten** .

![Demo](./images/slackmsgp.png)

Dann sehen Sie ein leeres Popup-Fenster.

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

FYI: Durch Angabe der folgenden Felder können Sie von Ihrer Journey aus auf diese Felder zugreifen und sie dynamisch über die Journey ausfüllen:

**&quot;toBeMapped&quot;: true,**

**&quot;dataType&quot;: &quot;string&quot;,**

**&quot;label&quot;: &quot;textToSlack&quot;**

Daraufhin sehen Sie Folgendes:

![Demo](./images/slackmsgpopup1.png)

Klicken Sie auf **Speichern**.

![Demo](./images/twiliomsgpopup2.png)

Scrollen Sie nach oben und klicken Sie erneut auf **Speichern** , um Ihre benutzerdefinierte Aktion zu speichern.

![Demo](./images/slackmsgpopup3.png)

Ihre benutzerdefinierte Aktion ist jetzt Teil der Liste **Aktionen** .

![Demo](./images/slackdone.png)

Sie haben Ereignisse, externe Datenquellen und Aktionen definiert. Lassen Sie uns das alles auf einer Journey zusammenfassen.

Nächster Schritt: [3.2.4 Journey und Nachrichten erstellen](./ex4.md)

[Zurück zu Modul 8](journey-orchestration-external-weather-api-sms.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
