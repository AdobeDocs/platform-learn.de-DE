---
title: Ersetzen Sie die Erweiterung SDK - Migration von Adobe Target zur Erweiterung Adobe Journey Optimizer - Decisioning Mobile .
description: Erfahren Sie, wie Sie SDK bei der Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung ersetzen.
exl-id: f1b77cad-792b-4a80-acff-e1a2f29250e1
source-git-commit: 348554b5a2d43d7a882e8259b39a57af13d41ff4
workflow-type: tm+mt
source-wordcount: '1558'
ht-degree: 3%

---

# Ersetzen Sie Target SDK durch Optimieren von SDK

Erfahren Sie, wie Sie Ihre Adobe Target-Implementierung auf der Seite ersetzen, um von at.js zu Platform Web SDK zu migrieren. Ein einfacher Ersatz besteht aus den folgenden Schritten:

* Überprüfen Sie Ihre Target-Verwaltungseinstellungen und notieren Sie sich Ihre IMS-Organisations-ID
* Ersetzen Sie die at.js-Bibliothek durch Platform Web SDK
* Aktualisieren des Ausblendungs-Snippets für synchrone Bibliotheksimplementierungen
* Konfigurieren von Platform Web SDK

>[!NOTE]
>
>Die angegebenen Beispiele dienen nur zur Veranschaulichung, und Ihre tatsächliche Target-Implementierung kann abweichen. Wenn Ihre bestehende Target-Implementierung den Datenerfassungs-Tag-Manager von Adobe verwendet, können Sie auch im Tutorial [Platform Web SDK Target-Implementierung](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html) weitere Informationen einsehen.


## Überprüfen der Target-Administrationseinstellungen

Der erste Schritt bei der Migration von Target zu Platform Web SDK besteht darin, Ihre Einstellungen im Abschnitt **[!UICONTROL Administration]** der Target-Benutzeroberfläche zu überprüfen.

### [!UICONTROL Implementierung]

#### [!UICONTROL Kontodetails]

* **[!UICONTROL IMS-Organisations-ID]** - Notieren Sie sich diesen Wert, da er zur Konfiguration der Platform Web SDK erforderlich ist.
* **[!UICONTROL On-Device Decisioning]** - Diese Funktion wird von Platform Web SDK nicht unterstützt. Diese Einstellung kann nach der Migration deaktiviert werden, wenn at.js nicht mehr auf einer Ihrer Websites verwendet wird oder Anwendungsfälle auf Serverseite für die geräteinterne Entscheidungsfindung vorliegen.

#### [!UICONTROL Implementierungsmethoden]

Alle bearbeitbaren Einstellungen im Abschnitt **[!UICONTROL Implementierungsmethoden]** gelten nur für at.js. Mit diesen Einstellungen wird eine benutzerdefinierte at.js-Bibliothek für Ihre Implementierung erstellt. Überprüfen Sie diese Einstellungen, um festzustellen, ob Sie benutzerdefinierten Code haben oder Erstanbieter- und Drittanbieter-Cookies für domänenübergreifende Anwendungsfälle setzen.

Die Einstellung **[!UICONTROL Profillebensdauer]** kann nur durch die Adobe-Kundenunterstützung geändert werden. Die Lebensdauer des Target-Besucherprofils wird durch Ihren Implementierungsansatz nicht beeinflusst. Sowohl at.js als auch Platform Web SDK verwenden dieselbe Lebensdauer des Besucherprofils.

#### [!UICONTROL Datenschutz]

* **[!UICONTROL Maskieren von Besucher-IP-Adressen]** - Diese Einstellung wirkt sich auf die Geotargeting-Funktionen aus. Sowohl at.js als auch Platform Web SDK verwenden für das Geotargeting dieselben Backend-IP-Verschleierungseinstellungen.

### [!UICONTROL Umgebungen]

Die Platform Web SDK verwendet eine Datenstromkonfiguration, mit der Sie explizit eine [!UICONTROL Umgebungs-ID] für separate Entwicklungs-, Staging- und Produktionsdatenströme definieren können. Der Hauptanwendungsfall für diese Konfiguration ist eine Mobile-App-Implementierung, bei der URLs nicht vorhanden sind, um Umgebungen einfach unterscheiden zu können. Die Einstellung ist optional, kann jedoch verwendet werden, um sicherzustellen, dass alle Anforderungen ordnungsgemäß mit der angegebenen Umgebung verknüpft sind. Dies unterscheidet sich von einer at.js-Implementierung, bei der Sie Zielumgebungen auf der Grundlage von Domains und Hostgruppenregeln zuweisen müssen.

>[!NOTE]
>
>Wenn in der Datenstromkonfiguration keine Umgebungs-ID angegeben ist, verwendet Target die Domain-zu-Umgebung-Zuordnung, wie im Abschnitt **Hosts** angegeben.

Weitere Informationen finden Sie im Handbuch [Datenstromkonfiguration](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) und in der Dokumentation [Hosts](https://experienceleague.adobe.com/docs/target/using/administer/hosts.html?lang=de).

## Bereitstellen von Platform Web SDK

Die Target-Funktion wird sowohl von at.js als auch von Platform Web SDK bereitgestellt. Wenn beide Bibliotheken gleichzeitig verwendet werden, können Rendering- und Tracking-Probleme auftreten. Um erfolgreich zu Platform Web SDK zu migrieren, müssen Sie zunächst at.js entfernen und durch Platform Web SDK (alloy.js) ersetzen.

Nehmen wir an, es gäbe eine einfache Target-Implementierung mit at.js:

* Eine Datenschicht am oberen Seitenrand bietet Informationen für Target und andere Programme
* Eine oder mehrere Hilfsbibliotheken von Drittanbietern, deren Funktionen in Target-Aktivitäten verwendet werden können (z. B. jQuery)
* Ein Code-Ausschnitt zum Vorab-Ausblenden, um Flackern zu minimieren
* Die Target-at.js-Bibliothek wird asynchron mit Standardeinstellungen geladen, um Aktivitäten automatisch anzufordern und zu rendern:

+++at.js-Beispielimplementierung auf einer HTML-Seite

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
  <!--prehiding snippet for Target with asynchronous deployment-->
  <script>
    ;(function(win, doc, style, timeout) {
      var STYLE_ID = 'at-body-style';

      function getParent() {
        return doc.getElementsByTagName('head')[0];
      }

      function addStyle(parent, id, def) {
        if (!parent) {
          return;
        }
        var style = doc.createElement('style');
        style.id = id;
        style.innerHTML = def;
        parent.appendChild(style);
      }

      function removeStyle(parent, id) {
        if (!parent) {
          return;
        }
        var style = doc.getElementById(id);
        if (!style) {
          return;
        }
        parent.removeChild(style);
      }
      addStyle(getParent(), STYLE_ID, style);
      setTimeout(function() {
        removeStyle(getParent(), STYLE_ID);
      }, timeout);
    }(window, document, "body {opacity: 0 !important}", 3000));
  </script>
  <!--Target at.js library loaded asynchonously-->
  <script src="/libraries/at.js" async></script>
</head>
<body>
  <h1 id="title">Home Page</h1><br><br>
  <p id="bodyText">Navigation</p><br><br>
  <a id="home" class="navigationLink" href="#">Home</a><br>
  <a id="pageA" class="navigationLink" href="#">Page A</a><br>
  <a id="pageB" class="navigationLink" href="#">Page B</a><br>
  <a id="pageC" class="navigationLink" href="#">Page C</a><br>
  <div>Homepage Hero Banner Content</div>
</body>
</html>
```

+++

Um Target auf die Verwendung von Platform Web SDK zu aktualisieren, entfernen Sie zunächst at.js:

```HTML
<!--Target at.js library loaded asynchonously-->
<script src="/libraries/at.js" async></script>
```

Und ersetzen Sie mit der Alloy-JavaScript-Bibliothek oder dem Tag-Einbettungs-Code und der Adobe Experience Platform Web SDK-Erweiterung:

>[!BEGINTABS]

>[!TAB JavaScript]

```HTML
<!--Platform Web SDK base code-->
<script>
  !function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||
  []).push(o),n[o]=function(){var u=arguments;return new Promise(
  function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}
  (window,["alloy"]);
</script>
<!--Platform Web SDK loaded asynchonously. Change the src to use the latest supported version.-->
<script src="https://cdn1.adoberesources.net/alloy/2.13.1/alloy.min.js" async></script>
```

>[!TAB Tags]

```HTML
<!--Tags Header Embed Code: REPLACE WITH THE INSTALL CODE FROM YOUR OWN ENVIRONMENT-->
<script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
```

Fügen Sie in der Tag-Eigenschaft die Adobe Experience Platform Web SDK-Erweiterung hinzu:

<!--![Add the Adobe Experience Platform Web SDK extension](assets/library-tags-addExtension.png){zoomable="yes"}-->


>[!ENDTABS]

Die vordefinierte eigenständige Version erfordert einen „Basis-Code“, der direkt zur Seite hinzugefügt wird. Dadurch wird eine globale Funktion namens „Alloy“ erstellt. Verwenden Sie diese Funktion, um mit dem SDK zu interagieren. Wenn Sie der globalen Funktion einen anderen Namen geben möchten, ändern Sie den `alloy`.

Weitere Informationen zu [ und Bereitstellungsoptionen finden Sie in der ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html?lang=de) zur Installation von Platform Web SDK .


## Ansatz zum Verbergen von Inhalten aktualisieren

Abhängig davon, ob die Bibliothek asynchron oder synchron geladen wird, kann die Implementierung von Platform Web SDK ein Code-Fragment zum Vorab-Ausblenden erfordern.

### Asynchrone Implementierung

Genau wie bei at.js kann es beim asynchronen Laden der Platform Web SDK-Bibliothek passieren, dass das Rendering der Seite abgeschlossen wird, bevor Target einen Austausch des Inhalts durchgeführt hat. Dies kann zum so genannten „Flackern“ führen, bei dem Standardinhalte kurz angezeigt werden, bevor sie durch die von Target angegebenen personalisierten Inhalte ersetzt werden. Wenn Sie dieses Flackern vermeiden möchten, empfiehlt Adobe, unmittelbar vor dem asynchronen Platform Web SDK-Skript-Verweis oder dem Tag-Einbettungs-Code ein spezielles Code-Fragment zum Vorab-Ausblenden hinzuzufügen.

Wenn Ihre Implementierung wie die obigen Beispiele asynchron ist, ersetzen Sie das Code-Fragment zum Vorab-Ausblenden von at.js durch die folgende Version, die mit Platform Web SDK kompatibel ist:

```HTML
<!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
<script>
  !function(e,a,n,t){var i=e.head;if(i){
  if (a) return;
  var o=e.createElement("style");
  o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
  (document, document.location.href.indexOf("mboxEdit") !== -1, "body { opacity: 0 !important }", 3000);
</script>
```

Durch den Code-Ausschnitt zum Vorab-Ausblenden wird ein Stil-Tag im Kopf der Seite mit der von Ihnen ausgewählten CSS-Definition erstellt. Dieses Stil-Tag wird entfernt, wenn eine Antwort von Target empfangen wird oder die Zeitüberschreitung erreicht wird.

Das Vorab-Ausblendverhalten wird durch zwei Konfigurationen am Ende des Ausschnitts gesteuert.

* `body { opacity: 0 !important }` gibt die CSS-Definition an, die für die Vorab-Ausblendung bis zum Laden von Target verwendet werden soll. Standardmäßig ist die gesamte Seite ausgeblendet. Sie können diese Definition aktualisieren, um die Selektoren anzuzeigen, die Sie vorab ausblenden möchten, und um anzugeben, wie Sie sie ausblenden möchten. Sie können mehrere Definitionen einbeziehen, da dieser Wert einfach in das Stil-Tag zum Vorab-Ausblenden eingefügt wird. Wenn Sie ein leicht identifizierbares Container-Element haben, das den Inhalt unter Ihrer Navigation umschließt, können Sie diese Einstellung verwenden, um die Vorab-Ausblendung auf dieses Container-Element zu beschränken.

* `3000` gibt den Timeout-Wert in Millisekunden für die Vorab-Ausblendung an. Wenn vor Ablauf der maximalen Wartezeit keine Antwort von Target eingeht, wird das Stil-Tag zum Vorab-Ausblenden entfernt. Das Erreichen dieser maximalen Wartezeit sollte selten sein.

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie das richtige Snippet für Platform Web SDK verwenden, da es eine andere Stil-ID als `alloy-prehiding` verwendet. Wenn der Code-Ausschnitt zum Vorab-Ausblenden für at.js verwendet wird, funktioniert er möglicherweise nicht ordnungsgemäß.

### Synchrone Implementierung

Adobe empfiehlt, Platform Web SDK asynchron zu implementieren, um eine optimale Gesamtseitenleistung zu erzielen. Wenn jedoch die alloy.js-Bibliothek oder der Tag-Einbettungs-Code synchron geladen wird, ist das Code-Fragment zum Vorab-Ausblenden nicht erforderlich. Stattdessen wird der Vorab-Ausblendungsstil in der Konfiguration von Platform Web SDK festgelegt.

Der Stil zum Vorab-Ausblenden für synchrone Implementierungen kann mit der Option [`prehidingStyle`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#prehidingStyle) konfiguriert werden. Die Konfiguration von Platform Web SDK wird im nächsten Abschnitt behandelt.

Weitere Informationen zur Verwaltung von Flackern in Platform Web SDK finden Sie im Handbuch unter [Verwalten von Flackern für personalisierte Erlebnisse](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/manage-flicker.html)

## Konfigurieren von Platform Web SDK

Die Platform Web SDK muss bei jedem Laden der Seite konfiguriert werden. Im folgenden Beispiel wird davon ausgegangen, dass die gesamte Site in einer einzigen Bereitstellung auf Platform Web SDK aktualisiert wird:

>[!BEGINTABS]

>[!TAB JavaScript]

Der `configure`-Befehl muss immer der erste SDK-Befehl sein, der aufgerufen wird. Der `edgeConfigId` ist die [!UICONTROL Datenstrom-ID]

```JavaScript
alloy("configure", {
  "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
  "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
});
```

>[!TAB Tags]

In Tags-Implementierungen werden viele Felder automatisch ausgefüllt oder können aus Dropdown-Menüs ausgewählt werden. Beachten Sie, dass [!UICONTROL  Platform-] und [!UICONTROL Datenströme] für jede Umgebung ausgewählt werden können. Der Datenstrom ändert sich je nach Status der Tag-Bibliothek im Veröffentlichungsprozess.

<!--![configuring the Web SDK tag extension](assets/tags-config.png){zoomable="yes"}-->
>[!ENDTABS]

Wenn Sie Seite für Seite von at.js zu Platform Web SDK migrieren möchten, sind die folgenden Konfigurationsoptionen erforderlich:


>[!BEGINTABS]

>[!TAB JavaScript]

```JavaScript
alloy("configure", {
  "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
  "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg",
  "targetMigrationEnabled":true,
  "idMigrationEnabled":true
});
```

>[!TAB Tags]

<!--![configuring the Web SDK tag extension migration options](assets/tags-config-migration.png){zoomable="yes"}-->

>[!ENDTABS]

Die bemerkenswerten Konfigurationsoptionen in Bezug auf Target sind unten beschrieben:

| Option | Beschreibung | Beispielwert |
| --- | --- | --- |
| `edgeConfigId` | Die Datenstrom-ID | `ebebf826-a01f-4458-8cec-ef61de241c93` |
| `orgId` | Adobe Experience Cloud-Organisations-ID | `ADB3LETTERSANDNUMBERS@AdobeOrg` |
| `targetMigrationEnabled` | Verwenden Sie diese Option, damit die Web-SDK die veralteten „mbox“- und „mboxEdgeCluster“-Cookies, die von at.js verwendet werden, lesen und schreiben kann. Auf diese Weise wird das Besucherprofil beibehalten, wenn Sie von einer Seite, die Web SDK verwendet, zu einer Seite wechseln, die die at.js-Bibliothek verwendet, und umgekehrt. | `true` |
| `idMigrationEnabled` | Wenn „true“, liest der SDK alte AMCV-Cookies und legt sie fest. Diese Option hilft beim Übergang zur Verwendung von Platform Web SDK, während einige Teile der Site möglicherweise weiterhin Visitor.js verwenden. | `true` |
| `thirdPartyCookiesEnabled` | Aktiviert die Einstellung von Adobe-Drittanbieter-Cookies. Die SDK kann die Besucher-ID in einem Drittanbieterkontext beibehalten, damit dieselbe Besucher-ID Website-übergreifend verwendet werden kann. Verwenden Sie diese Option, wenn Sie mehrere Sites haben. Manchmal ist diese Option jedoch aus Datenschutzgründen nicht erwünscht. | `true` |
| `prehidingStyle` | Wird verwendet, um eine CSS-Stildefinition zu erstellen, die Inhaltsbereiche Ihrer Web-Seite ausblendet, während personalisierter Inhalt vom Server geladen wird. Dies wird nur bei synchronen Bereitstellungen der SDK verwendet. | `body { opacity: 0 !important }` |

Eine vollständige Liste der Optionen finden Sie im Handbuch [Konfigurieren von Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html).

## Implementierungsbeispiel

Sobald die Platform Web SDK ordnungsgemäß eingerichtet ist, würde die Beispielseite wie folgt aussehen.

>[!BEGINTABS]

>[!TAB JavaScript]

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
  <script src="https://cdn1.adoberesources.net/alloy/2.13.1/alloy.min.js" async></script>
  
  <!--Configure Platform Web SDK-->
  <script>
    alloy("configure", {
      "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
      "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
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

Seiten-Code:

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

<!--![Add the Adobe Experience Platform Web SDK extension](assets/library-tags-addExtension.png){zoomable="yes"}-->

Fügen Sie die gewünschten Konfigurationen hinzu:
<!--![configuring the Web SDK tag extension migration options](assets/tags-config-migration.png){zoomable="yes"}-->


>[!ENDTABS]



Beachten Sie, dass durch einfaches Einschließen und Konfigurieren der Platform Web SDK-Bibliothek wie oben gezeigt keine Netzwerkaufrufe an das Adobe Edge-Netzwerk ausgeführt werden.

Erfahren Sie als Nächstes[ wie Sie formularbasierte Aktivitäten ](render-activities.md) die Seite anfordern und anwenden.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
