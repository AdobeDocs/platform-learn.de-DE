---
title: Ereignisse verfolgen | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Adobe Target-Konversionsereignisse mithilfe des Experience Platform Web SDK verfolgen.
source-git-commit: 43740912bc5a941aa21c5f38ed2c1aac74abffbc
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 1%

---


# Verfolgen von Target-Konversionsereignissen mit dem Platform Web SDK

Konversionsereignisse für Target können mit dem Platform Web SDK ähnlich wie bei at.js verfolgt werden. Konversionsereignisse fallen normalerweise in die folgenden Kategorien:

* Automatisch getrackte Ereignisse ohne Konfiguration
* Kaufkonversionsereignisse, die für eine Best Practice-Implementierung des Platform Web SDK angepasst werden sollten
* Konversionsereignisse ohne Kauf, für die Codeaktualisierungen erforderlich sind

>[!WARNING]
>
> Möglicherweise müssen nach dem 1. Oktober 2022 begonnene Implementierungen des Platform Web SDK die [Vorabruf-Problemumgehung](prefetch-workaround.md) um einige der auf dieser Seite beschriebenen Ereignisse erfolgreich zu verfolgen.

## Vergleich der Zielverfolgung

In der folgenden Tabelle wird verglichen, wie at.js und Platform Web SDK Konversionsereignisse verfolgen

| Aktivitätsziel | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Konversion > Seite angezeigt | Wird automatisch verfolgt. Basierend auf dem Wert von `context.address.url` in der at.js-Anfrage-Payload. | Wird automatisch verfolgt. Basierend auf dem Wert von `xdm.web.webPageDetails.URL` im `sendEvent` Nutzlast |
| Konversion > Mbox angezeigt | Verfolgung mit der Anforderung einer Anzeige-Mbox-Position oder einer Benachrichtigung mithilfe von `trackEvent()` oder `sendNotifications()` mit `type` Wert von `display`. | Mit einem Platform Web SDK verfolgt `sendEvent` mit dem Aufruf `eventType` von `decisioning.propositionDisplay`. |
| Konversion > Auf ein Element geklickt | Wird automatisch für VEC-basierte Aktivitäten verfolgt. Erscheint als at.js-Netzwerkaufruf mit einer `notifications` -Objekt in der Anfrage-Payload und ein `type` Wert von `click`. | Wird automatisch für VEC-basierte Aktivitäten verfolgt. Erscheint als Platform Web SDK `sendEvent` mit dem Aufruf `eventType` von `decisioning.propositionInteract`. |
| Interaktion > Seitenansichten | Wird automatisch verfolgt | Wird automatisch verfolgt |
| Interaktion > Besuchszeit pro Site | Wird automatisch verfolgt | Wird automatisch verfolgt |

<!--
| Revenue > RPV, AOV, or Total Sales | Tracked based on the `orderTotal` parameter values for the specified mbox(es) | Tracked based on the `xdm.commerce.order.priceTotal` values. Its best to use the "any mbox" option in the goal setup. |
| Revenue > Orders | Tracked based on the unique `orderId` parameter values for the specified mbox(es) | Tracked based on the unique values for `xdm.commerce.order.purchaseID`. Its best to use the "any mbox" option in the goal setup. |
| Engagement > Custom Scoring | Tracked with the `mboxPageValue` parameter. Refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) for more details. | Tracked with `data.__adobe.target.mboxPageValue` in the `sendEvent` payload |
-->

## Automatisch getrackte Ereignisse

Die folgenden Konversionsziele erfordern keine spezifischen Anpassungen Ihrer Implementierung:

* Konversion > Seite angezeigt
* Konversion > Auf ein Element geklickt
* Interaktion > Seitenansichten
* Interaktion > Besuchszeit pro Site

>[!NOTE]
>
>Das Platform Web SDK ermöglicht eine bessere Kontrolle über die Werte, die in der Anfrage-Payload übergeben werden. Um sicherzustellen, dass Target-Funktionen wie QA-URLs und die Konvertierungsziele &quot;Angezeigte Seite&quot;ordnungsgemäß funktionieren, überprüfen Sie, ob die `xdm.web.webPageDetails.URL` -Wert enthält die vollständige Seiten-URL mit der Groß-/Kleinschreibung.

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

## Benutzerspezifische Ereignisse

Target-Implementierungen verwenden in der Regel benutzerdefinierte Konversionsereignisse, um Klicks für formularbasierte Aktivitäten zu verfolgen, um eine Konversion in einem Fluss zu kennzeichnen oder um Parameter zu übergeben, ohne neue Inhalte anzufordern.

In der folgenden Tabelle werden der at.js-Ansatz und das Platform Web SDK-Äquivalent für einige gängige Anwendungsfälle für das Konversions-Tracking beschrieben.

| Anwendungsfall | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Tracking eines Klickkonversionsereignisses für eine Mbox-Position (Umfang) | Ausführen `trackEvent()` oder `sendNotifications()` mit `type` Wert von `click` für eine bestimmte Mbox-Position | Führen Sie einen `sendEvent` -Befehl mit dem Ereignistyp `decisioning.propositionInteract` |
| Tracking eines benutzerspezifischen Konversionsereignisses, das auch zusätzliche Daten enthalten kann, z. B. Target-Profilparameter | Ausführen `trackEvent()` oder `sendNotifications()` mit `type` Wert von `display` für eine bestimmte Mbox-Position | Führen Sie einen `sendEvent` -Befehl mit dem Ereignistyp `decisioning.propositionDisplay` |

>[!NOTE]
>
>Obwohl `decisioning.propositionDisplay` wird am häufigsten zur Erhöhung von Impressionen für bestimmte Bereiche verwendet und sollte auch als direkter Ersatz für at.js verwendet werden `trackEvent()` gewöhnlich. Die `trackEvent()` -Funktion standardmäßig auf einen Typ von `display` falls nicht angegeben. Überprüfen Sie Ihre Implementierung, um sicherzustellen, dass Sie den richtigen Ereignistyp für alle benutzerdefinierten Konvertierungen verwenden, die Sie definiert haben.

Weitere Informationen zur Verwendung von [`trackEvent()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-trackevent/) und [`sendNotifications()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-sendnotifications-atjs-21/) zur Verfolgung von Target-Ereignissen.

at.js-Beispiel mit `trackEvent()` , um einen Klick auf eine mbox-Position zu verfolgen:

```JavaScript
adobe.target.trackEvent({
  "type": "click",
  "mbox": "homepage_hero"
});
```

Mit einer Platform Web SDK-Implementierung können Sie Ereignisse und Benutzeraktionen verfolgen, indem Sie die `sendEvent` -Befehl eingeben und die `_experience.decisioning.propositions` XDM-Feldergruppe und legen Sie die `eventType` auf einen von zwei Werten:

* `decisioning.propositionDisplay`: Signalisiert das Rendering der Target-Aktivität.
* `decisioning.propositionInteract`: Signalisiert eine Benutzerinteraktion mit der Aktivität, z. B. einen Mausklick.

Die `_experience.decisioning.propositions` Die XDM-Feldergruppe ist ein Array von Objekten. Die Eigenschaften der einzelnen Objekte werden aus dem `result.propositions` , die in der `sendEvent` command: `{ id, scope, scopeDetails }`

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

Als Nächstes erfahren Sie, wie Sie [domänenübergreifende ID-Freigabe aktivieren](cross-domain.md) für konsistente Besucherprofile.

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).