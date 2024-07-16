---
title: VEC-Aktivitäten rendern | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Visual Experience Composer-Aktivitäten mit einer Web SDK-Implementierung von Adobe Target abrufen und anwenden.
exl-id: bbbbfada-e236-44de-a7bf-5c63ff840db4
source-git-commit: 4690d41f92c83fe17eda588538d397ae1fa28af0
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Render Adobe Target Visual Experience Composer (VEC)-Aktivitäten

Target-Aktivitäten werden entweder mit dem Visual Experience Composer (VEC) oder dem formularbasierten Composer eingerichtet. Das Platform Web SDK kann VEC-basierte Aktivitäten wie at.js abrufen und auf die Seite anwenden. Für diesen Teil der Migration werden Sie:

* Installieren der Visual Editing Helper-Browsererweiterung
* Führen Sie einen `sendEvent` -Aufruf mit dem Platform Web SDK aus, um Aktivitäten anzufordern.
* Aktualisieren Sie alle Verweise Ihrer at.js-Implementierung, die `getOffers()` zur Ausführung einer Target `pageLoad` -Anfrage verwenden.

## Visual Editing Helper-Browsererweiterung

Mit der Adobe Experience Cloud Visual Editing Helper-Browsererweiterung für Google Chrome können Sie Websites zuverlässig im Adobe Target Visual Experience Composer (VEC) laden, um schnell und einfach Web-Erlebnisse zu erstellen und zu überprüfen.

Die Browsererweiterung &quot;Visual Editing Helper&quot;funktioniert mit Websites, die at.js oder das Platform Web SDK verwenden.

### Visual Editing Helper abrufen und installieren

1. Navigieren Sie zur Browsererweiterung [Adobe Experience Cloud Visual Editing Helper im Chrome Web Store](https://chrome.google.com/webstore/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca).
1. Klicken Sie auf Hinzufügen zu **Chrome** > **Erweiterung hinzufügen**.
1. Öffnen Sie den VEC in Target.
1. Um die Erweiterung zu verwenden, klicken Sie in der Symbolleiste des Chrome-Browsers im VEC- oder QA-Modus auf das Symbol für die Visual Editing Helper-Browsererweiterung ![Symbol für die visuelle Bearbeitungserweiterung](assets/VEC-Helper.png){zoomable="yes"}.

Der Visual Editing Helper wird automatisch aktiviert, wenn eine Website in Target VEC geöffnet wird, um die Bearbeitung zu unterstützen. Die Erweiterung verfügt über keine bedingten Einstellungen. Die Erweiterung verarbeitet alle Einstellungen automatisch, einschließlich der SameSite-Cookie-Einstellungen.

Weitere Informationen zur Erweiterung [Visual Editing Helper Extension](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/visual-editing-helper-extension.html) und zur Fehlerbehebung beim Visual Experience Composer](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/troubleshoot-composer.html) finden Sie in der entsprechenden Dokumentation.[

>[!IMPORTANT]
>
>Die neue Erweiterung [Visual Editing Helper Extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca) ersetzt die vorherige Browsererweiterung [Target VEC Helper Browser ](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html). Wenn die ältere VEC Helper-Erweiterung installiert ist, sollte sie vor Verwendung der Visual Editing Helper-Erweiterung entfernt oder deaktiviert werden.

## Inhalt automatisch anfordern und anwenden

Nachdem das Platform Web SDK auf der Seite konfiguriert wurde, können Sie Inhalte von Target anfordern. Im Gegensatz zu at.js, das so konfiguriert werden kann, dass beim Laden der Bibliothek automatisch Inhalte angefordert werden, erfordert das Platform Web SDK die explizite Ausführung eines Befehls.

Wenn für Ihre at.js-Implementierung die Einstellung `pageLoadEnabled` auf `true` gesetzt ist, die die automatische Wiedergabe von VEC-basierten Aktivitäten ermöglicht, führen Sie mit dem Platform Web SDK den folgenden `sendEvent`-Befehl aus:

>[!BEGINTABS]

>[!TAB JavaScript]

```Javascript
alloy("sendEvent", {
  "renderDecisions": true
});
```

>[!TAB Tags]

Verwenden Sie in Tags den Aktionstyp [!UICONTROL Ereignis senden] , wobei die Option [!UICONTROL visuelle Personalisierungsentscheidungen rendern] ausgewählt ist:

![Senden eines Ereignisses mit in Tags ausgewählten visuellen Personalisierungsentscheidungen &quot;Rendern&quot;](assets/vec-sendEvent-renderTrue.png){zoomable="yes"}

>[!ENDTABS]

<!--
When the Platform Web SDK renders an activity to the page with `renderDecisions` set to `true`, an additional notification call fires automatically to increment an impression and attribute the visitor to the activity. This call uses an event type with the value `decisioning.propositionDisplay`.

![Platform Web SDK call incrementing a Target impression](assets/target-impression-call.png){zoomable="yes"}
-->

## Anfordern und Anwenden von Inhalten auf Anforderung

Einige Target-Implementierungen erfordern eine benutzerdefinierte Verarbeitung von VEC-Angeboten, bevor sie auf die Seite angewendet werden. Oder sie fordern mehrere Orte in einem einzelnen Aufruf an. In einer at.js-Implementierung kann dies durch Festlegen von `pageLoadEnabled` auf `false` und Ausführen einer `pageLoad` -Anfrage mithilfe der `getOffers()` -Funktion erfolgen.

+++ at.js-Beispiel mit `getOffers()` und `applyOffers()` zum manuellen Rendern von VEC-basierten Aktivitäten

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

Das Platform Web SDK weist kein bestimmtes `pageLoad` -Ereignis auf. Alle Anforderungen für Target-Inhalt werden mit der Option `decisionScopes` mit dem Befehl `sendEvent` gesteuert. Der Gültigkeitsbereich `__view__` dient dem Zweck der `pageLoad` -Anfrage.

+++ Ein entsprechender Platform Web SDK `sendEvent` -Ansatz:

1. Führen Sie einen `sendEvent` -Befehl aus, der den Entscheidungsbereich `__view__` enthält.
1. Anwenden des zurückgegebenen Inhalts auf die Seite mit dem Befehl `applyPropositions`
1. Führen Sie einen `sendEvent` -Befehl mit dem Ereignistyp `decisioning.propositionDisplay` und Vorschlagsdetails aus, um eine Impression zu erhöhen.

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
>Es ist möglich, Änderungen, die im Visual Experience Composer vorgenommen wurden, durch [manuell zu rendern. ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#manually-rendering-content) Die manuelle Wiedergabe von VEC-basierten Änderungen ist nicht üblich. Überprüfen Sie, ob Ihre at.js-Implementierung die Funktion `getOffers()` verwendet, um eine Target `pageLoad`-Anfrage manuell auszuführen, ohne den Inhalt mit `applyOffers()` auf die Seite anzuwenden.

Das Platform Web SDK bietet Entwicklern eine große Flexibilität beim Anfordern und Rendern von Inhalten. Weitere Optionen und Details finden Sie in der [dedizierten Dokumentation zum Rendern personalisierter Inhalte](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html) .

## Implementierungsbeispiel

Die grundlegende Platform Web SDK-Implementierung ist jetzt abgeschlossen.

>[!BEGINTABS]

>[!TAB JavaScript]

JavaScript-Beispiel mit automatischem Target-Inhaltsrendering:

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

Tags-Beispielseite mit automatischem Target-Inhaltsrendering:


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

![Hinzufügen der Adobe Experience Platform Web SDK-Erweiterung](assets/library-tags-addExtension.png){zoomable="yes"}

Fügen Sie die gewünschten Konfigurationen hinzu:
![Konfigurieren der Migrationsoptionen für die Web SDK-Tag-Erweiterung](assets/tags-config-migration.png){zoomable="yes"}

Erstellen Sie eine Regel mit der ausgewählten Aktion [!UICONTROL Ereignis senden] und [!UICONTROL visuelle Personalisierungsentscheidungen rendern] :
![Ereignis mit in Tags ausgewählten Render-Personalisierungen senden](assets/vec-sendEvent-renderTrue.png){zoomable="yes"}

>[!ENDTABS]

Erfahren Sie als Nächstes, wie Sie formularbasierte Target-Aktivitäten anfordern und rendern [.](render-form-based-activities.md)

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
