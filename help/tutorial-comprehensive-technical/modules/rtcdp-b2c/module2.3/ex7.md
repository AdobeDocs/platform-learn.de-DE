---
title: Echtzeit-Kundendatenplattform - Ziel-SDK
description: Echtzeit-Kundendatenplattform - Ziel-SDK
kt: 5342
doc-type: tutorial
exl-id: 5606ca2f-85ce-41b3-80f9-3c137f66a8c0
source-git-commit: 3a19e88e820c63294eff38bb8f699a9f690afcb9
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 6%

---

# 2.3.7 Destinations SDK

## Einrichten des Adobe I/O-Projekts

In dieser Übung verwenden Sie erneut Adobe I/O, um Adobe Experience Platform-APIs abzufragen. Wenn Sie Ihr Adobe I/O-Projekt noch nicht konfiguriert haben, gehen Sie zurück zu [Übung 3 in Modul 2.1](../module2.1/ex3.md) und befolgen Sie die Anweisungen dort.

## Postman-Authentifizierung für Adobe I/O

In dieser Übung verwenden Sie Postman erneut, um Adobe Experience Platform-APIs abzufragen. Wenn Sie Ihre Postman-Anwendung noch nicht konfiguriert haben, gehen Sie zurück zu [Übung 3 in Modul 2.1](../module2.1/ex3.md) und befolgen Sie die Anweisungen dort.

## Endpunkt und Format definieren

Für diese Übung benötigen Sie einen Endpunkt, der so konfiguriert werden muss, dass bei Qualifizierung eines Segments das Qualifikationsereignis an diesen Endpunkt gestreamt werden kann. In dieser Übung verwenden Sie einen Beispielendpunkt mit [https://webhook.site/](https://webhook.site/). Gehen Sie zu [https://webhook.site/](https://webhook.site/), wo Sie etwas Ähnliches sehen. Klicken Sie auf **In die Zwischenablage kopieren** , um die URL zu kopieren. Sie müssen diese URL in der nächsten Übung angeben. Die URL in diesem Beispiel lautet `https://webhook.site/e0eb530c-15b4-4a29-8b50-e40877d5490a`.

![Datenaufnahme](./images/webhook1.png)

Was das Format anbelangt, so verwenden wir eine Standardvorlage, die Segmentqualifikationen oder Nicht-Qualifikationen zusammen mit Metadaten wie Kundenkennungen streamt. Vorlagen können angepasst werden, um die Erwartungen bestimmter Endpunkte zu erfüllen. In dieser Übung verwenden wir jedoch eine Standardvorlage, was zu einer Payload wie dieser führt, die an den Endpunkt gestreamt wird.

```json
{
  "profiles": [
    {
      "identities": [
        {
          "type": "ecid",
          "id": "64626768309422151580190219823409897678"
        }
      ],
      "AdobeExperiencePlatformSegments": {
        "add": [
          "f58c723c-f1e5-40dd-8c79-7bb4ab47f041"
        ],
        "remove": []
      }
    }
  ]
}
```

## Erstellen einer Server- und Vorlagenkonfiguration

Der erste Schritt zum Erstellen Ihres eigenen Ziels in Adobe Experience Platform besteht darin, einen Server und eine Vorlagenkonfiguration zu erstellen.

Wechseln Sie dazu zu **Ziel-Authoring-API**, zu **Ziel-Server und Vorlagen** und klicken Sie auf , um die Anfrage **POST - Erstellen einer Zielserverkonfiguration** zu öffnen. Dann wirst du das sehen. Unter **Kopfzeilen** müssen Sie den Wert für den Schlüssel **x-sandbox-name** manuell aktualisieren und auf `--aepSandboxName--` festlegen. Wählen Sie den Wert **{{SANDBOX_NAME}}** aus.

![Datenaufnahme](./images/sdkpm1.png)

Ersetzen Sie sie durch `--aepSandboxName--`.

![Datenaufnahme](./images/sdkpm2.png)

Navigieren Sie als Nächstes zu **Hauptteil**. den Platzhalter **{{body}}** auswählen.

![Datenaufnahme](./images/sdkpm3.png)

Sie müssen jetzt den Platzhalter **{{body}}** durch den folgenden Code ersetzen:

```json
{
    "name": "Custom HTTP Destination",
    "destinationServerType": "URL_BASED",
    "urlBasedDestination": {
        "url": {
            "templatingStrategy": "PEBBLE_V1",
            "value": "yourURL"
        }
    },
    "httpTemplate": {
        "httpMethod": "POST",
        "requestBody": {
            "templatingStrategy": "PEBBLE_V1",
            "value": "{\n    \"profiles\": [\n    {%- for profile in input.profiles %}\n        {\n            \"identities\": [\n            {%- for idMapEntry in profile.identityMap -%}\n            {%- set namespace = idMapEntry.key -%}\n                {%- for identity in idMapEntry.value %}\n                {\n                    \"type\": \"{{ namespace }}\",\n                    \"id\": \"{{ identity.id }}\"\n                }{%- if not loop.last -%},{%- endif -%}\n                {%- endfor -%}{%- if not loop.last -%},{%- endif -%}\n            {% endfor %}\n            ],\n            \"AdobeExperiencePlatformSegments\": {\n                \"add\": [\n                {%- for segment in profile.segmentMembership.ups | added %}\n                    \"{{ segment.key }}\"{%- if not loop.last -%},{%- endif -%}\n                {% endfor %}\n                ],\n                \"remove\": [\n                {#- Alternative syntax for filtering segments by status: -#}\n                {% for segment in removedSegments(profile.segmentMembership.ups) %}\n                    \"{{ segment.key }}\"{%- if not loop.last -%},{%- endif -%}\n                {% endfor %}\n                ]\n            }\n        }{%- if not loop.last -%},{%- endif -%}\n    {% endfor %}\n    ]\n}"
        },
        "contentType": "application/json"
    }
}
```

Nach dem Einfügen des obigen Codes müssen Sie das Feld **urlBasedDestination.url.value** manuell aktualisieren und es auf die URL des Webhooks setzen, den Sie im vorherigen Schritt erstellt haben, nämlich `https://webhook.site/e0eb530c-15b4-4a29-8b50-e40877d5490a` in diesem Beispiel.

![Datenaufnahme](./images/sdkpm4.png)

Nach dem Aktualisieren des Felds **urlBasedDescription.url.value** sollte es wie folgt aussehen. Klicken Sie auf **Senden**.

![Datenaufnahme](./images/sdkpm5.png)

Nachdem Sie auf **Senden** geklickt haben, wird Ihre Servervorlage erstellt und als Teil der Antwort wird ein Feld namens **instanceId** angezeigt. Schreiben Sie es auf, wie Sie es im nächsten Schritt benötigen werden. In diesem Beispiel lautet die **instanceId**
2.`eb0f436f-dcf5-4993-a82d-0fcc09a6b36c`

![Datenaufnahme](./images/sdkpm6.png)

## Zielkonfiguration erstellen

Wechseln Sie in Postman unter **Ziel-Authoring-API** zu **Zielkonfigurationen** und klicken Sie auf , um die Anfrage **POST - Zielkonfiguration erstellen** zu öffnen. Dann wirst du das sehen. Unter **Kopfzeilen** müssen Sie den Wert für den Schlüssel **x-sandbox-name** manuell aktualisieren und auf `--aepSandboxName--` festlegen. Wählen Sie den Wert **{{SANDBOX_NAME}}** aus.

![Datenaufnahme](./images/sdkpm7.png)

Ersetzen Sie sie durch `--aepSandboxName--`.

![Datenaufnahme](./images/sdkpm8.png)

Navigieren Sie als Nächstes zu **Hauptteil**. den Platzhalter **{{body}}** auswählen.

![Datenaufnahme](./images/sdkpm9.png)

Sie müssen jetzt den Platzhalter **{{body}}** durch den folgenden Code ersetzen:

```json
{
    "name": "--aepUserLdap-- - Webhook",
    "description": "Exports segment qualifications and identities to a custom webhook via Destination SDK.",
    "status": "TEST",
    "customerAuthenticationConfigurations": [
        {
            "authType": "BEARER"
        }
    ],
    "customerDataFields": [
        {
            "name": "endpointsInstance",
            "type": "string",
            "title": "Select Endpoint",
            "description": "We could manage several instances across the globe for REST endpoints that our customers are provisioned for. Select your endpoint in the dropdown list.",
            "isRequired": true,
            "enum": [
                "US",
                "EU",
                "APAC",
                "NZ"
            ]
        }
    ],
    "uiAttributes": {
        "documentationLink": "https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en",
        "category": "streaming",
        "connectionType": "Server-to-server",
        "frequency": "Streaming"
    },
    "identityNamespaces": {
        "ecid": {
            "acceptsAttributes": true,
            "acceptsCustomNamespaces": false
        }
    },
    "segmentMappingConfig": {
        "mapExperiencePlatformSegmentName": true,
        "mapExperiencePlatformSegmentId": true,
        "mapUserInput": false
    },
    "aggregation": {
        "aggregationType": "BEST_EFFORT",
        "bestEffortAggregation": {
            "maxUsersPerRequest": "1000",
            "splitUserById": false
        }
    },
    "schemaConfig": {
        "profileRequired": false,
        "segmentRequired": true,
        "identityRequired": true
    },
    "destinationDelivery": [
        {
            "authenticationRule": "NONE",
            "destinationServerId": "yourTemplateInstanceID"
        }
    ]
}
```

![Datenaufnahme](./images/sdkpm11.png)

Nach dem Einfügen des obigen Codes müssen Sie das Feld **destinationDelivery manuell aktualisieren. destinationServerId** verwenden, müssen Sie dafür die **instanceId** der Ziel-Server-Vorlage festlegen, die Sie im vorherigen Schritt erstellt haben und in diesem Beispiel `eb0f436f-dcf5-4993-a82d-0fcc09a6b36c` lautete. Klicken Sie als Nächstes auf **Senden**.

![Datenaufnahme](./images/sdkpm10.png)

Dann sehen Sie diese Antwort.

![Datenaufnahme](./images/sdkpm12.png)

Ihr Ziel wird jetzt in Adobe Experience Platform erstellt. Lass uns dorthin gehen und es überprüfen.

Wechseln Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende [!UICONTROL Sandbox] ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Navigieren Sie im linken Menü zu **Ziele**, klicken Sie auf **Katalog** und scrollen Sie nach unten zur Kategorie **Streaming**. Ihr werdet dort jetzt euer Ziel sehen.

![Datenaufnahme](./images/destsdk1.png)

## Segment mit Ziel verknüpfen

Klicken Sie in **Ziele** > **Katalog** auf **Einrichten** Ihres Ziels, um Segmente zu Ihrem neuen Ziel hinzuzufügen.

![Datenaufnahme](./images/destsdk2.png)

Geben Sie ein Platzhalter-Träger-Token ein, z. B. **1234**. Klicken Sie auf **Mit Ziel verbinden**.

![Datenaufnahme](./images/destsdk3.png)

Dann wirst du das sehen. Verwenden Sie als Namen für Ihr Ziel `--aepUserLdap-- - Webhook`. Wählen Sie einen Endpunkt der Wahl aus, in diesem Beispiel **EU**. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/destsdk4.png)

Sie können optional eine Data Governance-Richtlinie auswählen. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/destsdk5.png)

Wählen Sie das zuvor erstellte Segment mit dem Namen `--aepUserLdap-- - Interest in PROTEUS FITNESS JACKSHIRT` aus. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/destsdk6.png)

Dann wirst du das sehen. Stellen Sie sicher, dass Sie das **SOURCE-FELD** `--aepTenantId--.identification.core.ecid` dem Feld `Identity: ecid` zuordnen. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/destsdk7.png)

Klicken Sie auf **Fertigstellen**.

![Datenaufnahme](./images/destsdk8.png)

Ihr Ziel ist jetzt live, neue Segmentqualifikationen werden jetzt an Ihren benutzerdefinierten Webhook gestreamt.

![Datenaufnahme](./images/destsdk9.png)

## Testen der Segmentaktivierung

Wechseln Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](../../gettingstarted/gettingstarted/images/web8.png)

Sie können nun den unten stehenden Fluss zum Zugriff auf die Website ausführen. Klicken Sie auf **Integrationen**.

![DSN](../../gettingstarted/gettingstarted/images/web1.png)

Wählen Sie auf der Seite **Integrationen** die Datenerfassungseigenschaft aus, die in Übung 0.1 erstellt wurde.

![DSN](../../gettingstarted/gettingstarted/images/web2.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../gettingstarted/gettingstarted/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../gettingstarted/gettingstarted/images/web7.png)

Gehen Sie von der Startseite **Luma** zu **Men** und klicken Sie auf das Produkt **PROTEUS FITNESS JACKSHIRT**.

![Datenaufnahme](./images/homenadia.png)

Sie haben jetzt die Produktseite für **PROTEUS FITNESS JACKSHIRT** besucht, was bedeutet, dass Sie sich jetzt für das Segment qualifizieren, das Sie zuvor in dieser Übung erstellt haben.

![Datenaufnahme](./images/homenadiapp.png)

Wenn Sie den Profil-Viewer öffnen und zu **Segmente** gehen, wird das Segment als qualifiziert angezeigt.

![Datenaufnahme](./images/homenadiapppb.png)

Kehren Sie jetzt zu Ihrem offenen Webhook auf [https://webhook.site/](https://webhook.site/) zurück, wo eine neue eingehende Anfrage angezeigt werden sollte, die von Adobe Experience Platform stammt und das Segmentqualifikationsereignis enthält.

![Datenaufnahme](./images/destsdk10.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
