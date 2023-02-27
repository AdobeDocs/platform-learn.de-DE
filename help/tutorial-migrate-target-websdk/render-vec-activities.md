---
title: VEC-Aktivitäten rendern | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Visual Experience Composer-Aktivitäten mit einer Web SDK-Implementierung von Adobe Target abrufen und anwenden.
source-git-commit: ca2fade972a2f7f84134ee4ef9c0f24c5ab1c5c6
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 6%

---

# Render Adobe Target Visual Experience Composer (VEC)-Aktivitäten

Target-Aktivitäten werden entweder mit dem Visual Experience Composer (VEC) oder dem formularbasierten Composer eingerichtet. Das Platform Web SDK kann VEC-basierte Aktivitäten wie at.js abrufen und auf die Seite anwenden. Für diesen Teil der Migration werden Sie:

* Installieren der Visual Editing Helper-Browsererweiterung
* Führen Sie einen `sendEvent` mit dem Platform Web SDK aufrufen, um Aktivitäten anzufordern.
* Aktualisieren Sie alle Verweise Ihrer at.js-Implementierung, die `getOffers()` zum Ausführen eines Target `pageLoad` -Anfrage.

## Visual Editing Helper-Browsererweiterung

Mit der Adobe Experience Cloud Visual Editing Helper-Browsererweiterung für Google Chrome können Sie Websites zuverlässig im Adobe Target Visual Experience Composer (VEC) laden, um schnell und einfach Web-Erlebnisse zu erstellen und zu überprüfen.

Die Browsererweiterung &quot;Visual Editing Helper&quot;funktioniert mit Websites, die at.js oder das Platform Web SDK verwenden.

### Visual Editing Helper abrufen und installieren

1. Navigieren Sie zum [Adobe Experience Cloud Visual Editing Helper-Browsererweiterung im Chrome Web Store](https://chrome.google.com/webstore/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca).
1. Klicken Sie auf Hinzufügen zu **Chrome** > **Erweiterung hinzufügen**.
1. Öffnen Sie den VEC in Target.
1. Um die Erweiterung zu verwenden, klicken Sie auf das Symbol für die Visual Editing Helper-Browsererweiterung ![Symbol &quot;Visual Editing Extension&quot;](assets/VEC-Helper.png){zoomable=&quot;yes&quot;} in der Symbolleiste Ihres Chrome-Browsers, während Sie sich im VEC- oder QA-Modus befinden.

Die Visual Editing Helper wird automatisch aktiviert, wenn eine Website im VEC von Target geöffnet wird, um die Bearbeitung zu unterstützen. Die Erweiterung verfügt über keine bedingten Einstellungen. Die Erweiterung verarbeitet alle Einstellungen automatisch, einschließlich der SameSite Cookie-Einstellungen.

Weitere Informationen zu [Visual Editing Helper-Erweiterung](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/visual-editing-helper-extension.html) und [Fehlerbehebung für den Visual Experience Composer](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/troubleshoot-composer.html).

>[!IMPORTANT]
>
>Die neue [Visual Editing Helper-Erweiterung](https://chrome.google.com/webstore/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca) ersetzt die vorherige [Target VEC Helper-Browsererweiterung](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html). Wenn die ältere VEC Helper-Erweiterung installiert ist, sollte sie vor Verwendung der Visual Editing Helper-Erweiterung entfernt oder deaktiviert werden.

## Inhalt automatisch anfordern und anwenden

Nachdem das Platform Web SDK auf der Seite konfiguriert wurde, können Sie Inhalte von Target anfordern. Im Gegensatz zu at.js, das so konfiguriert werden kann, dass beim Laden der Bibliothek automatisch Inhalte angefordert werden, erfordert das Platform Web SDK die explizite Ausführung eines Befehls.

Wenn Ihre at.js-Implementierung die Variable `pageLoadEnabled` Einstellung auf `true` zur automatischen Darstellung von VEC-basierten Aktivitäten, führen Sie dann Folgendes aus `sendEvent` -Befehl mit dem Platform Web SDK:

>[!BEGINTABS]

>[!TAB JavaScript]

```Javascript
alloy("sendEvent", {
  "renderDecisions": true
});
```

>[!TAB Tags]

Verwenden Sie in -Tags die [!UICONTROL Ereignis senden] Aktionstyp mit dem [!UICONTROL visuelle Personalisierungsentscheidungen rendern] ausgewählte Option:

![Ereignis mit in Tags ausgewählten visuellen Personalisierungsentscheidungen rendern senden](assets/vec-sendEvent-renderTrue.png){zoomable=&quot;yes&quot;}

>[!ENDTABS]

<!--
When the Platform Web SDK renders an activity to the page with `renderDecisions` set to `true`, an additional notification call fires automatically to increment an impression and attribute the visitor to the activity. This call uses an event type with the value `decisioning.propositionDisplay`.

![Platform Web SDK call incrementing a Target impression](assets/target-impression-call.png){zoomable="yes"}
-->

## Anfordern und Anwenden von Inhalten auf Anforderung

Einige Target-Implementierungen erfordern eine benutzerdefinierte Verarbeitung von VEC-Angeboten, bevor sie auf die Seite angewendet werden. Oder sie fordern mehrere Orte in einem einzelnen Aufruf an. In einer at.js-Implementierung kann dies durch Festlegen von `pageLoadEnabled` nach `false` und unter Verwendung der `getOffers()` -Funktion zum Ausführen einer `pageLoad` -Anfrage.

+++ at.js-Beispiel mit `getOffers()` und `applyOffers()` Manuelles Rendern von VEC-basierten Aktivitäten

```JavaScript
adobe.target.getOffers({
  request: {
    execute: {
      pageLoad: {}
    }
  }
}).
then(response => adobe.target.applyOffers({ response: response }));
```

+++

Das Platform Web SDK verfügt über keine spezifische `pageLoad` -Ereignis. Alle Anforderungen für Target-Inhalte werden mit der `decisionScopes` mit der Option `sendEvent` Befehl. Die `__view__` Der Geltungsbereich dient dem Zweck der `pageLoad` -Anfrage.

+++ Ein äquivalentes Platform Web SDK `sendEvent` Ansatz:

1. Führen Sie einen `sendEvent` -Befehl, der Folgendes enthält: `__view__` Entscheidungsbereich
1. Anwenden des zurückgegebenen Inhalts auf die Seite mit der `applyPropositions` command
1. Führen Sie einen `sendEvent` mit dem Befehl `decisioning.propositionDisplay` Ereignistyp und Vorschlagsdetails zum Erhöhen einer Impression

```Javascript
alloy("sendEvent", {
  // Request the special "__view__" scope for target-global-mbox / pageLoad
  decisionScopes: ["__view__"]
}).then(function(result) {
  // Check if content (propositions) were returned
  if (result.propositions) {
    var retrievedPropositions = result.propositions;
    // Apply propositions to the page
    return alloy("applyPropositions", {
      propositions: retrievedPropositions
    }).then(function(applyPropositionsResult) {
      var renderedPropositions = applyPropositionsResult.propositions;
      // Send a display notification with the sendEvent command
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
  }
});
```

+++

>[!NOTE]
>
>Es ist möglich, [Manuelles Rendern von Änderungen](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#manually-rendering-content) im Visual Experience Composer erstellt wurden. Die manuelle Wiedergabe von VEC-basierten Änderungen ist nicht üblich. Überprüfen Sie, ob Ihre at.js-Implementierung die `getOffers()` -Funktion zum manuellen Ausführen einer Target-Funktion `pageLoad` -Anfrage ohne Verwendung von `applyOffers()` , um den Inhalt auf die Seite anzuwenden.

Das Platform Web SDK bietet Entwicklern eine große Flexibilität beim Anfordern und Rendern von Inhalten. Siehe Abschnitt [spezielle Dokumentation zum Rendern personalisierter Inhalte](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html) für zusätzliche Optionen und Details.

## Implementierungsbeispiel

Die grundlegende Platform Web SDK-Implementierung ist jetzt abgeschlossen.

>[!BEGINTABS]

>[!TAB JavaScript]

JavaScript-Beispiel mit automatischer Target-Inhaltsdarstellung:

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

  <!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
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
    
    // Send an event to the Adobe edge network and render Target content automatically 
    alloy("sendEvent", {
      "renderDecisions": true
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


>[!TAB Tags]

Tags-Beispielseite mit automatischem Target-Inhalts-Rendering:


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

  <!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
  <script>
    !function(e,a,n,t){var i=e.head;if(i){
    if (a) return;
    var o=e.createElement("style");
    o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
    (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
  </script>

    <!--Tags Header Embed Code: REPLACE WITH THE INSTALL CODE FROM YOUR OWN ENVIRONMENT-->
    <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
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

Fügen Sie in Tags die Adobe Experience Platform Web SDK-Erweiterung hinzu:

![Hinzufügen der Adobe Experience Platform Web SDK-Erweiterung](assets/library-tags-addExtension.png){zoomable=&quot;yes&quot;}

Fügen Sie die gewünschten Konfigurationen hinzu:
![Konfigurieren der Migrationsoptionen für die Web SDK-Tag-Erweiterung](assets/tags-config-migration.png){zoomable=&quot;yes&quot;}

Erstellen Sie eine Regel mit einer [!UICONTROL Ereignis senden] Maßnahmen und [!UICONTROL visuelle Personalisierungsentscheidungen rendern] selected:
![Senden eines Ereignisses mit in Tags ausgewählten Render-Personalisierungen](assets/vec-sendEvent-renderTrue.png){zoomable=&quot;yes&quot;}

>[!ENDTABS]

Als Nächstes erfahren Sie, wie Sie [Rendern formularbasierter Target-Aktivitäten](render-form-based-activities.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
