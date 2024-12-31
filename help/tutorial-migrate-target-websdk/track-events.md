---
title: Tracking von Ereignissen - Migrieren von Target aus at.js 2.x nach Web SDK
description: Erfahren Sie, wie Sie Adobe Target-Konversionsereignisse mithilfe von Experience Platform Web SDK verfolgen.
exl-id: 5da772bc-de05-4ea9-afbd-3ef58bc7f025
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 1%

---

# Tracking von Target-Konversionsereignissen mit Platform Web SDK

Konversionsereignisse für Target können mit Platform Web SDK ähnlich wie bei at.js verfolgt werden. Konversionsereignisse fallen normalerweise in die folgenden Kategorien:

* Automatisch verfolgte Ereignisse, für die keine Konfiguration erforderlich ist
* Kaufkonversionsereignisse, die für eine Best-Practice-Implementierung von Platform Web SDK angepasst werden sollten
* Nicht-Kauf-Konversionsereignisse, die Code-Aktualisierungen erfordern

## Vergleich der Zielverfolgung

In der folgenden Tabelle wird verglichen, wie at.js und Platform Web SDK Konversionsereignisse verfolgen

| Aktivitätsziel | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Konversion > Angezeigte Seite | Verfolgt automatisch. Basiert auf dem Wert von `context.address.url` in der Payload der at.js-Anfrage. | Verfolgt automatisch. Basiert auf dem Wert von `xdm.web.webPageDetails.URL` in der `sendEvent` Payload |
| Konversion > Angezeigte Mbox | Verfolgt mit der Anfrage nach einem Anzeigespeicherort der Mbox oder einer Benachrichtigung mithilfe von `trackEvent()` oder `sendNotifications()` mit einem `type` Wert von `display`. | Verfolgt mit einem Platform Web SDK-`sendEvent`-Aufruf mit dem `eventType` von `decisioning.propositionDisplay`. |
| Konversion > Element angeklickt | Automatisches Tracking für VEC-basierte Aktivitäten. Erscheint als AT.js-Netzwerkaufruf mit einem `notifications`-Objekt in der Payload der Anfrage und einem `type` von `click`. | Automatisches Tracking für VEC-basierte Aktivitäten. Erscheint als Platform Web SDK `sendEvent`-Aufruf mit dem `eventType` von `decisioning.propositionInteract`. |
| Interaktion > Seitenansichten | Automatisch nachverfolgt | Automatisch nachverfolgt |
| Interaktion > Zeit vor Ort | Automatisch nachverfolgt | Automatisch nachverfolgt |

<!--
| Revenue > RPV, AOV, or Total Sales | Tracked based on the `orderTotal` parameter values for the specified mbox(es) | Tracked based on the `xdm.commerce.order.priceTotal` values. Its best to use the "any mbox" option in the goal setup. |
| Revenue > Orders | Tracked based on the unique `orderId` parameter values for the specified mbox(es) | Tracked based on the unique values for `xdm.commerce.order.purchaseID`. Its best to use the "any mbox" option in the goal setup. |
| Engagement > Custom Scoring | Tracked with the `mboxPageValue` parameter. Refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) for more details. | Tracked with `data.__adobe.target.mboxPageValue` in the `sendEvent` payload |
-->

## Automatisch getrackte Ereignisse

Die folgenden Konversionsziele erfordern keine spezifischen Anpassungen an Ihrer Implementierung:

* Konversion > Angezeigte Seite
* Konversion > Element angeklickt
* Interaktion > Seitenansichten
* Interaktion > Zeit vor Ort

>[!NOTE]
>
>Platform Web SDK ermöglicht eine bessere Kontrolle über die Werte, die in der Anfrage-Payload übergeben werden. Um sicherzustellen, dass Target-Funktionen wie QA-URLs und Konversionsziele für „Angezeigte Seite“ ordnungsgemäß funktionieren, überprüfen Sie, ob der `xdm.web.webPageDetails.URL`-Wert die vollständige Seiten-URL mit dem richtigen Groß-/Kleinschreibung enthält.

<!--
## Purchase conversion events

The following conversion goals are based on the order details information passed in the Platform Web SDK `sendEvent` payload:

* Revenue > Revenue per Visit (RPV)
* Revenue > Average Order Value (AOV)
* Revenue > Total Sales
* Revenue > Orders

Target at.js implementations typically use an order confirmation mbox with the `trackEvent()` or `sendNotifications()` functions to pass the order ID, order total, and a list of product IDs purchased. These methods are specific to Target.

The Platform Web SDK is a shared library for all Adobe applications and you may have other applications such as Adobe Analytics to consider. Because of this shared nature, its best send a single order confirmation call using the appropriate commerce XDM field group.

For more information and an example, refer to the tutorial section about [sending purchase parameters to Target](send-parameters.md#purchase-parameters). 
-->

## Benutzerdefinierte Ereignisse

Target-Implementierungen verwenden in der Regel benutzerdefinierte Konversionsereignisse, um Klicks für formularbasierte Aktivitäten zu verfolgen, eine Konversion in einem Fluss anzugeben oder Parameter zu übergeben, ohne neue Inhalte anzufordern.

In der folgenden Tabelle sind der at.js-Ansatz und das Platform Web SDK-Äquivalent für einige gängige Anwendungsfälle für das Konversions-Tracking aufgeführt.

| Anwendungsfall | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Verfolgen eines Klick-Konversionsereignisses für einen Mbox-Speicherort (Umfang) | Führen Sie `trackEvent()` oder `sendNotifications()` mit dem `type` Wert `click` für einen bestimmten Mbox-Speicherort aus. | Führt einen `sendEvent` Befehl mit dem Ereignistyp `decisioning.propositionInteract` aus |
| Verfolgen Sie ein benutzerdefiniertes Konversionsereignis, das auch zusätzliche Daten wie Zielgruppenprofilparameter enthalten kann | Führen Sie `trackEvent()` oder `sendNotifications()` mit dem `type` Wert `display` für einen bestimmten Mbox-Speicherort aus. | Führt einen `sendEvent` Befehl mit dem Ereignistyp `decisioning.propositionDisplay` aus |

>[!NOTE]
>
>Obwohl `decisioning.propositionDisplay` am häufigsten verwendet wird, um Impressions für bestimmte Bereiche zu inkrementieren, sollte es in der Regel auch als direkter Ersatz für at.js-`trackEvent()` verwendet werden. Die `trackEvent()`-Funktion ist standardmäßig auf einen Typ von `display` festgelegt, falls dieser nicht angegeben ist. Überprüfen Sie Ihre Implementierung, um sicherzustellen, dass Sie für alle definierten benutzerdefinierten Konversionen den richtigen Ereignistyp verwenden.

Weitere Informationen zur Verwendung von [`trackEvent()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-trackevent/) und [`sendNotifications()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-sendnotifications-atjs-21/) zum Tracking von Target-Ereignissen finden Sie in der entsprechenden at.js-Dokumentation .

at.js-Beispiel mit `trackEvent()` zum Tracking eines Klicks auf einen Mbox-Speicherort:

```JavaScript
adobe.target.trackEvent({
  "type": "click",
  "mbox": "homepage_hero"
});
```

Mit einer Implementierung von Platform Web SDK können Sie Ereignisse und Benutzeraktionen verfolgen, indem Sie den `sendEvent`-Befehl aufrufen, die `_experience.decisioning.propositions` XDM-Feldergruppe ausfüllen und den `eventType` auf einen von zwei Werten setzen:

* `decisioning.propositionDisplay`: Signalisiert das Rendering der Target-Aktivität.
* `decisioning.propositionInteract`: Signalisiert eine Benutzerinteraktion mit der Aktivität wie ein Mausklick.

Die `_experience.decisioning.propositions` XDM-Feldergruppe ist ein Array von -Objekten. Die Eigenschaften der einzelnen -Objekte werden von dem `result.propositions` abgeleitet, der im `sendEvent`-Befehl zurückgegeben wird: `{ id, scope, scopeDetails }`

```JavaScript
alloy("sendEvent", {
  xdm: { ...},
  decisionScopes: ["hero-banner"]
}).then(function (result) {
  var propositions = result.propositions;

  if (propositions) {
    // Find the discount proposition, if it exists.
    for (var i = 0; i < propositions.length; i++) {
      var proposition = propositions[i];
      for (var j = 0; j < proposition.items; j++) {
        var item = proposition.items[j];

        if (item.schema === "https://ns.adobe.com/personalization/measurement") {
          // add metric to the DOM element
          const button = document.getElementById("form-based-click-metric");

          button.addEventListener("click", event => {
            const executedPropositions = [
              {
                id: proposition.id,
                scope: proposition.scope,
                scopeDetails: proposition.scopeDetails
              }
            ];
            // send the click track event
            alloy("sendEvent", {
              "xdm": {
                "eventType": "decisioning.propositionInteract",
                "_experience": {
                  "decisioning": {
                    "propositions": executedPropositions
                  }
                }
              }
            });
          });
        }
      }
    }
  }
});
```

Erfahren Sie als Nächstes, wie Sie [Domain-übergreifende ID-Freigabe aktivieren](cross-domain.md) für konsistente Besucherprofile aktivieren.

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
