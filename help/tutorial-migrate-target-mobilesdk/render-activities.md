---
title: Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie eine Adobe Target-Implementierung von at.js 2.x auf das Adobe Experience Platform Web SDK migrieren. Zu den Themen gehören die Bibliotheksübersicht, Implementierungsunterschiede und andere bemerkenswerte Hinweise.
source-git-commit: 009548969b88d1bfa6eac23f65b1ca2144f27c34
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---

# Render Target-Aktivitäten, die den formularbasierten Composer verwenden

Einige Target-Implementierungen können regionale Mboxes (jetzt als &quot;Bereiche&quot;bezeichnet) verwenden, um Inhalte aus Aktivitäten bereitzustellen, die den formularbasierten Experience Composer verwenden. Wenn Ihre at.js-Target-Implementierung Mboxes verwendet, müssen Sie Folgendes tun:

* Aktualisieren Sie alle Verweise Ihrer at.js-Implementierung, die `getOffer()` oder `getOffers()` verwenden, auf die entsprechenden Platform Web SDK-Methoden.
* Fügen Sie dem Trigger ein `propositionDisplay` -Ereignis Code hinzu, damit eine Impression gezählt wird.

## Anfordern und Anwenden von Inhalten auf Anforderung

Aktivitäten, die mit dem formularbasierten Composer von Target erstellt und an regionale Mboxes gesendet werden, können nicht automatisch vom Platform Web SDK gerendert werden. Ähnlich wie bei at.js müssen Angebote, die an bestimmte Target-Orte bereitgestellt werden, bei Bedarf gerendert werden.


+++at.js-Beispiel mit `getOffer()` und `applyOffer()`:

1. Führen Sie `getOffer()` aus, um ein Angebot für einen Ort anzufordern.
1. Führen Sie `applyOffer()` aus, um das Angebot an einen angegebenen Selektor zu rendern.
1. Eine Aktivitätsimpression wird zum Zeitpunkt der `getOffer()` -Anfrage automatisch erhöht

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

++ + Platform Web SDK-Entsprechung mit dem Befehl `applyPropositions` :

1. Führen Sie den Befehl `sendEvent` aus, um Angebote (Vorschläge) für einen oder mehrere Orte (Bereiche) anzufordern.
1. Führen Sie den Befehl `applyPropositions` mit dem Metadatenobjekt aus, das Anweisungen zum Anwenden von Inhalten auf die Seite für jeden Bereich enthält.
1. Führen Sie den Befehl `sendEvent` mit dem Ereignistyp `decisioning.propositionDisplay` aus, um eine Impression zu verfolgen.

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

Das Platform Web SDK bietet eine bessere Kontrolle beim Anwenden formularbasierter Aktivitäten auf die Seite mithilfe des Befehls `applyPropositions` mit dem angegebenen Wert `actionType`:

| `actionType` | Beschreibung | at.js `applyOffer()` | Platform Web SDK `applyPropositions` |
| --- | --- | --- | --- |
| `setHtml` | Löschen Sie den Inhalt des Containers und fügen Sie dann das Angebot zum Container hinzu. | Ja (immer verwendet) | Ja |
| `replaceHtml` | Entfernen Sie den Container und ersetzen Sie ihn durch das Angebot. | Nein | Ja |
| `appendHtml` | Hängt das Angebot nach der angegebenen Auswahl an | Nein | Ja |

Weitere Darstellungsoptionen und Beispiele finden Sie in der [dedizierten Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html) zum Rendern von Inhalten mit dem Platform Web SDK .

## Implementierungsbeispiel

Die folgende Beispielseite baut auf der im vorherigen Abschnitt beschriebenen Implementierung auf und fügt nur zusätzliche Bereiche zum Befehl `sendEvent` hinzu.

+++Platform Web SDK-Beispiel mit mehreren Scopes

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

Als Nächstes erfahren Sie, wie Sie [Target-Parameter mithilfe des Platform Web SDK übergeben](send-parameters.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Optimierungserweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
