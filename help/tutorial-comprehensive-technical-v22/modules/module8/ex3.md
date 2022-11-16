---
title: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Definition benutzerdefinierter Aktionen
description: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Definition benutzerdefinierter Aktionen
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 7ee5aee9-3740-4eee-9f53-a44fdb564a00
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 3%

---

# 8.3 Benutzerdefinierte Aktion definieren

In dieser Übung erstellen Sie zwei benutzerdefinierte Aktionen, indem Sie Adobe Journey Optimizer in Kombination verwenden.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxId--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend auf das **Verwalten** Schaltfläche unter **Aktionen**.

![Demo](./images/menuactions.png)

Sie werden dann die **Aktionen** Liste.

![Demo](./images/acthome.png)

Sie definieren eine Aktion, die einen Slack an einen Textkanal sendet.

## 8.3.1 Aktion: Text an Slack-Kanal senden

Sie verwenden jetzt einen vorhandenen Slack-Kanal und senden Nachrichten an diesen Slack-Kanal. Slack verfügt über eine benutzerfreundliche API, und wir verwenden Adobe Journey Optimizer zum Trigger ihrer API.

![Demo](./images/slack.png)

Klicken **Aktion erstellen** um eine neue Aktion hinzuzufügen.

![Demo](./images/adda.png)

Es wird ein leeres Action-Popup angezeigt.

![Demo](./images/emptyact.png)

Verwenden Sie als Namen für die Aktion . `--demoProfileLdap--TextSlack`. In diesem Beispiel lautet der Aktionsname `vangeluwTextSlack`.

Legen Sie Beschreibung auf fest: `Send Text to Slack`.

![Demo](./images/slackname.png)

Für **URL-Konfiguration** verwenden Sie Folgendes:

- URL: `https://2mnbfjyrre.execute-api.us-west-2.amazonaws.com/prod`
- Methode: **POST**

>[!NOTE]
>
>Die obige URL bezieht sich auf eine AWS-Lambda-Funktion, die Ihre Anfrage dann wie oben erwähnt an den Slack-Kanal weiterleitet. Dies geschieht, um den Zugriff auf einen Adobe-eigenen Slack-Kanal zu schützen. Wenn Sie über einen eigenen Slack-Kanal verfügen, sollten Sie eine Slack App erstellen über [https://api.slack.com/](https://api.slack.com/)müssen Sie dann einen eingehenden Webhook in dieser Slack-App erstellen und dann die oben genannte URL durch Ihre eingehende Webhook-URL ersetzen.

Sie müssen die Kopfzeilenfelder nicht ändern.

![Demo](./images/slackurl.png)

**Authentifizierung** auf **Keine Authentifizierung**.

![Demo](./images/slackauth.png)

Für **Aktionsparameter** müssen Sie festlegen, welche Felder an den Slack gesendet werden sollen. Logischerweise möchten wir, dass Adobe Journey Optimizer und Adobe Experience Platform das Gehirn der Personalisierung sind. Daher sollte der Text, der an den Slack gesendet werden soll, von Adobe Journey Optimizer definiert und dann zur Ausführung an den Slack gesendet werden.

Für die **Aktionsparameter**, klicken Sie auf die **Payload bearbeiten** Symbol.

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

FYI: Durch Angabe der folgenden Felder können Sie von Ihrer Journey auf diese Felder zugreifen und sie dynamisch über die Journey ausfüllen:

**&quot;toBeMapped&quot;: true,**

**&quot;dataType&quot;: &quot;string&quot;,**

**&quot;label&quot;: &quot;textToSlack&quot;**

Daraufhin sehen Sie Folgendes:

![Demo](./images/slackmsgpopup1.png)

Klicken Sie auf **Speichern**.

![Demo](./images/twiliomsgpopup2.png)

Scrollen Sie nach oben und klicken Sie auf **Speichern** zum Speichern der benutzerdefinierten Aktion erneut verwenden.

![Demo](./images/slackmsgpopup3.png)

Ihre benutzerdefinierte Aktion ist jetzt Teil der **Aktionen** Liste.

![Demo](./images/slackdone.png)

Sie haben Ereignisse, externe Datenquellen und Aktionen definiert. Lassen Sie uns das alles auf einer Journey zusammenfassen.

Nächster Schritt: [8.4 Journey und Nachrichten erstellen](./ex4.md)

[Zurück zu Modul 8](journey-orchestration-external-weather-api-sms.md)

[Zu allen Modulen zurückkehren](../../overview.md)
