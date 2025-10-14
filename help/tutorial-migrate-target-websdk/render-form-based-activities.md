---
title: Migrieren von Target aus at.js 2.x nach Web SDK
description: Erfahren Sie, wie Sie eine Adobe Target-Implementierung von at.js 2.x zu Adobe Experience Platform Web SDK migrieren. Zu den Themen gehören eine Übersicht über die Bibliothek, Implementierungsunterschiede und andere bemerkenswerte Hinweise.
exl-id: 43b9ae91-4524-4071-9eb4-12a0a8aec242
source-git-commit: 4690d41f92c83fe17eda588538d397ae1fa28af0
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 1%

---

# Rendern von Target-Aktivitäten, die den formularbasierten Composer verwenden

Einige Target-Implementierungen verwenden möglicherweise regionale Mboxes (jetzt als „Bereiche“ bezeichnet), um Inhalte aus Aktivitäten bereitzustellen, die den formularbasierten Experience Composer verwenden. Wenn Ihre at.js-Target-Implementierung Mboxes verwendet, müssen Sie Folgendes tun:

* Aktualisieren Sie alle Verweise aus Ihrer at.js-Implementierung, die `getOffer()` oder `getOffers()` zu den entsprechenden Platform Web SDK-Methoden verwenden.
* Fügen Sie Code zum Trigger eines `propositionDisplay` hinzu, damit eine Impression gezählt wird.

## Anfordern und Anwenden von Inhalten bei Bedarf

Aktivitäten, die mit dem formularbasierten Composer von Target erstellt und für regionale Mboxes bereitgestellt werden, können nicht automatisch von Platform Web SDK gerendert werden. Ähnlich wie at.js müssen Angebote, die an bestimmte Target-Speicherorte gesendet werden, nach Bedarf gerendert werden.


+++at.js-Beispiel mit `getOffer()` und `applyOffer()`:

1. `getOffer()` ausführen, um ein Angebot für einen Standort anzufordern
1. `applyOffer()` ausführen, um das Angebot an einen angegebenen Selektor zu rendern
1. Eine Aktivitäts-Impression wird zum Zeitpunkt der `getOffer()` automatisch inkrementiert

```JavaScript
// Retrieve an offer for the homepage-hero location
adobe.target.getOffer({
  "mbox": "homepage_hero",

  // Render offer to the #hero-banner selector
  "success": function(offers) {
    adobe.target.applyOffer({
      "mbox": "homepage_hero",
      "selector": "#hero-banner",
      "offer": offers
    });
  },
  "error": {
    console.log(error);
  },
  "timeout": 3000
});
```

+++

+++Platform Web SDK-Entsprechung mit dem `applyPropositions`:

1. Führen Sie `sendEvent` Befehl aus, um Angebote (Vorschläge) für einen oder mehrere Standorte (Bereiche) anzufordern
1. Führen Sie `applyPropositions` Befehl mit dem Metadatenobjekt aus, das Anweisungen zum Anwenden von Inhalten auf die Seite für jeden Bereich bereitstellt
1. Führen Sie `sendEvent` Befehl mit eventType des `decisioning.propositionDisplay` aus, um eine Impression zu verfolgen

```JavaScript
// Retrieve propositions for homepage_hero location (scope)
alloy("sendEvent", {
  "decisionScopes": ["homepage_hero"]
}).then(function(result) {
  var retrievedPropositions = result.propositions;
    
  // Render offer (proposition) to the #hero-banner selector by supplying extra metadata
  return alloy("applyPropositions", {
    "propositions": retrievedPropositions,
    "metadata": {
      // Specify each regional mbox or scope name along with a selector and actionType
      "homepage_hero": {
        "selector": "#hero-banner",
        "actionType": "setHtml"
      }
    }
  }).then(function(applyPropositionsResult) {
    var renderedPropositions = applyPropositionsResult.propositions;

    // Send the display notifications via sendEvent command
    alloy("sendEvent", {
      "xdm": {
        "eventType": "decisioning.propositionDisplay",
        "_experience": {
          "decisioning": {
            "propositions": renderedPropositions
          }
        }
      }
    });
  });
});
```

+++

Die Platform Web SDK bietet mehr Kontrolle darüber, wie formularbasierte Aktivitäten mithilfe des Befehls `applyPropositions` mit einer angegebenen `actionType` auf die Seite angewendet werden:

| `actionType` | Beschreibung | at.js-`applyOffer()` | Platform Web SDK-`applyPropositions` |
| --- | --- | --- | --- |
| `setHtml` | Löschen Sie den Inhalt des Containers und fügen Sie dann das Angebot zum Container hinzu | Ja (immer verwendet) | Ja |
| `replaceHtml` | Container entfernen und durch das Angebot ersetzen | Nein | Ja |
| `appendHtml` | Fügt das Angebot nach dem angegebenen Selektor an | Nein | Ja |

Weitere Informationen [&#x200B; Rendering-Optionen und Beispiele finden Sie in der &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html?lang=de) Dokumentation zum Rendern von Inhalten mit Platform Web SDK .

## Implementierungsbeispiel

Die folgende Beispielseite baut auf der im vorherigen Abschnitt beschriebenen Implementierung auf und fügt dem `sendEvent`-Befehl nur zusätzliche Bereiche hinzu.

+++Platform Web SDK-Beispiel mit mehreren Bereichen

```HTML
<!doctype html>
<html>
<head>
  <title>Example page</title>
  <!--Data Layer to enable rich data collection and targeting-->
  <script>
    var digitalData = { 
      // Data layer information goes here
    };
  </script>

  <!--Third party libraries that may be used by Target offers and modifications-->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.1/jquery.min.js"></script>

  <!--Prehiding snippet for Target with asynchronous deployment-->
  <script>
    !function(e,a,n,t){var i=e.head;if(i){
    if (a) return;
    var o=e.createElement("style");
    o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
    (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
  </script>

  <!--Platform Web SDK base code-->
  <script>
    !function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||
    []).push(o),n[o]=function(){var u=arguments;return new Promise(
    function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}
    (window,["alloy"]);
  </script>

  <!--Platform Web SDK loaded asynchonously. Change the src to use the latest supported version.-->
  <script src="https://cdn1.adoberesources.net/alloy/2.6.4/alloy.min.js" async></script>
  
  <!--Configure Platform Web SDK then send event-->
  <script>
    alloy("configure", {
      "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
      "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
    });
    alloy("sendEvent", {
      // Request and render VEC-based activities
      "renderDecisions": true,
      // Request content for form-based activities using the "homepage_hero" scope
      "decisionScopes": ["homepage_hero"]
    }).then(function(result) {
      var retrievedPropositions = result.propositions;
        
      // Render offer (proposition) to the #hero-banner selector by supplying extra metadata
      return alloy("applyPropositions", {
        "propositions": retrievedPropositions,
        "metadata": {
          // Specify each regional mbox or scope name along with a selector and actionType
          "homepage_hero": {
            "selector": "#hero-banner",
            "actionType": "setHtml"
          }
        }
      }).then(function(applyPropositionsResult) {
        var renderedPropositions = applyPropositionsResult.propositions;

        // Send the display notifications via sendEvent command
        alloy("sendEvent", {
          "xdm": {
            "eventType": "decisioning.propositionDisplay",
            "_experience": {
              "decisioning": {
                "propositions": renderedPropositions
              }
            }
          }
        });
      });
    });
  </script>
</head>
<body>
  <h1 id="title">Home Page</h1><br><br>
  <p id="bodyText">Navigation</p><br><br>
  <a id="home" class="navigationLink" href="#">Home</a><br>
  <a id="pageA" class="navigationLink" href="#">Page A</a><br>
  <a id="pageB" class="navigationLink" href="#">Page B</a><br>
  <a id="pageC" class="navigationLink" href="#">Page C</a><br>
  <div id="homepage-hero">Homepage Hero Banner Content</div>
</body>
</html>
```

Erfahren Sie als Nächstes, wie Sie [Target-Parameter mithilfe der Platform Web SDK übergeben](send-parameters.md).

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=de#M463) posten.
