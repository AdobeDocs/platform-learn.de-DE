---
title: Real-Time CDP - Ziele SDK
description: Real-Time CDP - Ziele SDK
kt: 5342
doc-type: tutorial
exl-id: c18acbf5-92f5-4cd2-a5aa-a5e9debb98c9
source-git-commit: 2d5ca888eb24c1f65b4ecd48030ec8d1659b7f84
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 6%

---

# 2.3.6 Ziele SDK

## Einrichten des Adobe I/O-Projekts

In dieser Übung verwenden Sie Adobe I/O erneut, um die APIs von Adobe Experience Platform abzufragen. Wenn Sie Ihr Adobe I/O-Projekt noch nicht konfiguriert haben, gehen Sie zurück zu [Übung 3 in Modul 2.1](../rtcdpb2c-1/ex3.md) und folgen Sie dort den Anweisungen.

>[!IMPORTANT]
>
>Wenn Sie ein Adobe-Mitarbeiter sind, befolgen Sie bitte die Anweisungen hier zur Verwendung von [PostBuster](./../../../../modules/getting-started/gettingstarted/ex8.md).

## Authentifizierung bei Adobe I/O

In dieser Übung verwenden Sie Postman erneut, um die APIs von Adobe Experience Platform abzufragen. Wenn Sie Ihr Postman-Programm noch nicht konfiguriert haben, gehen Sie zurück zu [Übung 3 in Modul 2.1](../rtcdpb2c-1/ex3.md) und folgen Sie dort den Anweisungen.

>[!IMPORTANT]
>
>Wenn Sie ein Adobe-Mitarbeiter sind, befolgen Sie bitte die Anweisungen hier zur Verwendung von [PostBuster](./../../../../modules/getting-started/gettingstarted/ex8.md).

## Endpunkt und Format definieren

Für diese Übung benötigen Sie einen Endpunkt, der so konfiguriert werden muss, dass das Qualifizierungsereignis an diesen Endpunkt gestreamt werden kann, wenn eine Zielgruppe qualifiziert ist. In dieser Übung verwenden Sie einen Beispielendpunkt mit [https://pipedream.com/requestbin](https://pipedream.com/requestbin). Wechseln Sie zu [https://pipedream.com/requestbin](https://pipedream.com/requestbin), erstellen Sie ein Konto und dann einen Arbeitsbereich. Nachdem der Arbeitsbereich erstellt wurde, sehen Sie etwas Ähnliches.

Klicken Sie **Kopieren**, um die URL zu kopieren. Sie müssen diese URL in der nächsten Übung angeben. Die URL in diesem Beispiel lautet `https://eodts05snjmjz67.m.pipedream.net`.

![Datenaufnahme](./images/webhook1.png)

Für das Format verwenden wir eine Standardvorlage, die Zielgruppenqualifikationen oder -aufhebungen zusammen mit Metadaten wie Kundenkennungen streamt. Vorlagen können so angepasst werden, dass sie den Erwartungen bestimmter Endpunkte entsprechen. In dieser Übung verwenden wir jedoch eine Standardvorlage erneut, was zu einer Payload wie dieser führt, die an den Endpunkt gestreamt wird.

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

Der erste Schritt zum Erstellen eines eigenen Ziels in Adobe Experience Platform besteht darin, eine Server- und Vorlagenkonfiguration mit Postman zu erstellen.

Öffnen Sie dazu Ihre Postman-Anwendung und navigieren Sie zu **Zielerstellungs-API**, zu **Zielserver und Vorlagen** und klicken Sie auf , um die Anfrage zu öffnen **POST - Erstellen einer Zielserverkonfiguration**.

>[!NOTE]
>
>Wenn Sie diese Postman-Sammlung nicht haben, gehen Sie zurück zu [Übung 3 in Modul 2.1](../rtcdpb2c-1/ex3.md) und folgen Sie den Anweisungen dort, um Postman mit den bereitgestellten Postman-Sammlungen einzurichten.

Sie werden es dann sehen. Unter **Headers** müssen Sie den Wert für den Schlüssel **x-sandbox-name** manuell aktualisieren und auf `--aepSandboxName--` setzen. Wählen Sie den Wert **{{SANDBOX_NAME}}**.

![Datenaufnahme](./images/sdkpm1.png)

Ersetzen Sie sie durch `--aepSandboxName--`.

![Datenaufnahme](./images/sdkpm2.png)

Gehen Sie dann zu **Body**. Wählen Sie die **{{body}}** Platzhalter aus.

![Datenaufnahme](./images/sdkpm3.png)

Jetzt müssen Sie den Platzhalter **{{body}}** durch den folgenden Code ersetzen:

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

Nach dem Einfügen des obigen Codes müssen Sie das Feld **urlBasedDestination.url.value** manuell aktualisieren und es auf die URL des Webhooks festlegen, den Sie im vorherigen Schritt erstellt haben, der in diesem Beispiel `https://eodts05snjmjz67.m.pipedream.net` wurde.

![Datenaufnahme](./images/sdkpm4.png)

Nach der Aktualisierung des Felds **urlBasedDestination.url.value** sollte es wie folgt aussehen. Klicken Sie auf **Senden**.

![Datenaufnahme](./images/sdkpm5.png)

>[!NOTE]
>
>Beachten Sie Folgendes: Bevor Sie eine Anfrage an Adobe I/O senden, benötigen Sie eine gültige `access_token`. Um einen gültigen `access_token` abzurufen, führen Sie die Anfrage **POST - Zugriffs-Token abrufen** in der Sammlung **Adobe IO - OAuth** aus.

Nachdem Sie auf **Senden** geklickt haben, wird Ihre Server-Vorlage erstellt und als Teil der Antwort wird ein Feld mit dem Namen **instanceId** angezeigt. Schreibe es auf, da du es im nächsten Schritt benötigst. In diesem Beispiel lautet die **instanceId**
`52482c90-8a1e-42fc-b729-7f0252e5cebd`.

![Datenaufnahme](./images/sdkpm6.png)

## Erstellen der Zielkonfiguration

Gehen Sie in Postman unter **Zielerstellungs-**) zu **Zielkonfigurationen** und klicken Sie darauf, um die Anfrage zu öffnen **POST - Zielkonfiguration erstellen**. Sie werden es dann sehen. Unter **Headers** müssen Sie den Wert für den Schlüssel **x-sandbox-name** manuell aktualisieren und auf `--aepSandboxName--` setzen. Wählen Sie den Wert **{{SANDBOX_NAME}}** aus und ersetzen Sie ihn durch `--aepSandboxName--`.

![Datenaufnahme](./images/sdkpm7.png)

Gehen Sie dann zu **Body**. Wählen Sie die **{{body}}** Platzhalter aus.

![Datenaufnahme](./images/sdkpm9.png)

Jetzt müssen Sie den Platzhalter **{{body}}** durch den folgenden Code ersetzen:

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

Nach dem Einfügen des obigen Codes müssen Sie das Feld &quot;**&quot; manuell aktualisieren. destinationServerId** festgelegt und auf die **instanceId** der Ziel-Server-Vorlage festgelegt werden muss, die Sie im vorherigen Schritt erstellt haben, der in diesem Beispiel `52482c90-8a1e-42fc-b729-7f0252e5cebd` wurde. Klicken Sie anschließend auf **Senden**.

![Datenaufnahme](./images/sdkpm10.png)

Sie werden dann diese Antwort sehen.

![Datenaufnahme](./images/sdkpm12.png)

Ihr Ziel wird jetzt in Adobe Experience Platform erstellt. Lassen Sie uns hingehen und es überprüfen.

Zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden [!UICONTROL Sandbox] wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

Gehen Sie im linken Menü zu **Ziele**, klicken Sie auf **Katalog** und blättern Sie nach unten zur Kategorie **Streaming**. Ihr Ziel ist jetzt dort verfügbar.

![Datenaufnahme](./images/destsdk1.png)

## Verknüpfen Ihrer Audience mit Ihrem Ziel

Klicken **unter** > **Katalog** auf **Einrichten** auf Ihrem Ziel, um Zielgruppen zu Ihrem neuen Ziel hinzuzufügen.

![Datenaufnahme](./images/destsdk2.png)

Geben Sie einen zufälligen Wert für das **Bearer-Token** ein, z. B **1234**. Klicken Sie **Mit Ziel verbinden**.

![Datenaufnahme](./images/destsdk3.png)

Sie werden es dann sehen. Verwenden Sie `--aepUserLdap-- - Webhook` als Namen für Ihr Ziel. Wählen Sie einen Endpunkt Ihrer Wahl aus, in diesem Beispiel **EU**. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/destsdk4.png)

Sie können optional eine Data-Governance-Richtlinie auswählen. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/destsdk5.png)

Wählen Sie die zuvor erstellte Zielgruppe mit dem Namen `--aepUserLdap-- - Interest in Galaxy S24` aus. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/destsdk6.png)

Sie werden es dann sehen. Stellen Sie sicher, dass Sie die **&#x200B;**&#x200B;SOURCE`--aepTenantId--.identification.core.ecid` der `Identity: ecid` zuordnen. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/destsdk7.png)

Klicken Sie auf **Fertigstellen**.

![Datenaufnahme](./images/destsdk8.png)

Ihr Ziel ist jetzt live, neue Zielgruppenqualifikationen werden jetzt an Ihren benutzerdefinierten Webhook gestreamt.

![Datenaufnahme](./images/destsdk9.png)

## Testen der Zielgruppenaktivierung

Navigieren Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf die 3 Punkte **…** in Ihrem Website-Projekt und dann auf **Ausführen**, um es zu öffnen.

![DSN](./../../datacollection/dc1.1/images/web8.png)

Anschließend wird Ihre Demo-Website geöffnet. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../../getting-started/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browser-Fenster.

![DSN](../../../getting-started/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../../getting-started/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../../getting-started/gettingstarted/images/web6.png)

Ihre Website wird dann in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../../getting-started/gettingstarted/images/web7.png)

In diesem Beispiel möchten Sie einer bestimmten Kundin oder einem bestimmten Kunden antworten, die bzw. der sich ein bestimmtes Produkt ansieht.
Gehen Sie auf der **Citi Signal**-Homepage zu **Telefone &amp; Geräte** und klicken Sie auf das Produkt **Galaxy S24**.

![Datenaufnahme](./images/homegalaxy.png)

Die Produktseite für Galaxy S24 wurde jetzt angezeigt, sodass sich Ihre Zielgruppe in den nächsten Minuten für Ihr Profil qualifiziert.

![Datenaufnahme](./images/homegalaxy1.png)

Wenn Sie den Profil-Viewer öffnen und zu **Zielgruppen** wechseln, sehen Sie, dass die Zielgruppe qualifiziert ist.

![Datenaufnahme](./images/homegalaxydsdk.png)

Gehen Sie nun zurück zu Ihrem geöffneten Webhook auf [https://eodts05snjmjz67.m.pipedream.net](https://eodts05snjmjz67.m.pipedream.net), wo eine neue eingehende Anfrage angezeigt werden sollte, die von Adobe Experience Platform stammt und das Zielgruppen-Qualifizierungsereignis enthält.

![Datenaufnahme](./images/destsdk10.png)

## Nächste Schritte

Kehren Sie zu [Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen](./real-time-cdp-build-a-segment-take-action.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
