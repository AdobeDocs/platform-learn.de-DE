---
title: Vergleich von at.js 2.x mit Web SDK - Migrieren von Target von at.js 2.x zu Web SDK
description: Erfahren Sie mehr über die Unterschiede zwischen at.js 2.x und Platform Web SDK, einschließlich Funktionen, Einstellungen und Datenfluss.
exl-id: b6f0ac2b-0d8e-46ce-8e9f-7bbc61eb20ec
source-git-commit: 7d3c1728925e322f9313cf71f081500e0c0bac0b
workflow-type: tm+mt
source-wordcount: '2018'
ht-degree: 4%

---

# Vergleich von at.js mit Platform Web SDK

Die eigenständige Adobe Target at.js-Bibliothek unterscheidet sich erheblich von Platform Web SDK. Die folgenden Tabellen dienen als Referenz bei der Bewertung von Bereichen Ihrer Implementierung, auf die Sie sich während des Migrationsprozesses möglicherweise konzentrieren müssen.

Nachdem Sie die folgenden Informationen durchgelesen und Ihre aktuelle technische at.js-Implementierung bewertet haben, sollten Sie Folgendes verstehen:

- Welche Target-Funktionen von Platform Web SDK unterstützt werden
- Welche at.js-Funktionen haben Platform Web SDK-Entsprechungen?
- Anwenden von Target-Einstellungen mit Platform Web SDK
- Unterschiede beim Datenfluss von at.js und Platform Web SDK

Wenn Sie mit Platform Web SDK noch nicht vertraut sind, können Sie sich keine Sorgen machen. Die folgenden Elemente werden in diesem Tutorial ausführlicher behandelt.

## Funktionsvergleich

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Zielprofil aktualisieren | Unterstützt | Unterstützt |
| Trigger-Ansicht für SPAs | Unterstützt | Unterstützt |
| Target Recommendations | Unterstützt | Unterstützt |
| Formularbasierte Angebote abrufen | Unterstützt | Unterstützt |
| Verfolgen von Ereignissen | Unterstützt | Unterstützt |
| A4T: Einzelseitenanwendung | Unterstützt | Unterstützt |
| A4T: Klick-Tracking | Unterstützt | Unterstützt |
| A4T: Client-seitige Protokollierung | Unterstützt | Unterstützt |
| A4T: Server-seitige Protokollierung | Unterstützt | Unterstützt |
| Angebote anwenden | Unterstützt | Unterstützt |
| Ansicht in SPA ohne Benachrichtigungen neu rendern | Unterstützt | Unterstützt |
| Hybride Anwendungen | Unterstützt | Unterstützt |
| QA-URLs | Unterstützt | Unterstützt |
| Mbox-Drittanbieter-IDs | Unterstützt | Unterstützt |
| Kundenattribute | Unterstützt | Unterstützt |
| Remote-Angebote | Unterstützt | Teilweise unterstützt. Dynamische Remote-Angebote werden nicht unterstützt. |
| Umleitungsangebote | Unterstützt | Unterstützt. Eine Umleitung von einer Seite mit Platform Web SDK zu einer Seite mit at.js (und in umgekehrter Richtung) wird jedoch nicht unterstützt. |
| Geräteinterne Entscheidungsfindung | Unterstützt | Derzeit nicht unterstützt |
| Prefetch-Mboxes | Unterstützt für benutzerdefinierte Bereiche und SPA VEC | Der Vorabruf ist der Standardmodus für Web SDK |
| Benutzerspezifische Ereignisse | Unterstützt | Nicht unterstützt. Den aktuellen Status finden Sie [ &quot;](https://github.com/orgs/adobe/projects/18/views/1?pane=item&itemId=17372355{target="_blank"}) Roadmap“. |
| Antwort-Token | Unterstützt | Unterstützt. Code-Beispiele und [ zwischen at.js und Platform Web SDK finden Sie in ](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html?lang=de) Dokumentation zu dedizierten Antwort-Token . |
| Datenanbieter | Unterstützt | Nicht unterstützt. Benutzerdefinierter Code kann zum Trigger eines Platform Web SDK-`sendEvent`-Befehls verwendet werden, nachdem Daten von einem anderen Anbieter abgerufen wurden. |


## Bemerkenswerte Hinweise

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Flimmerschutz | Der Code-Ausschnitt zum Vorab-Ausblenden für asynchrone Implementierungen verwendet die Stil-ID `at-body-style`. at.js sucht nach dieser Element-ID, um den Stil zu entfernen, sobald eine Antwort eingeht. | Der standardmäßige Code-Ausschnitt zum Vorab-Ausblenden verwendet die Stil-ID `alloy-prehiding`. Das Web-SDK ist nicht mit dem Code-Ausschnitt zum Vorab-Ausblenden von at.js kompatibel, sodass es im Rahmen des Migrationsprozesses geändert werden muss. |
| Inhalt beim Laden der Seite automatisch rendern | Gesteuert mit einer globalen Zielgruppeneinstellung. Aktiviert, wenn `pageLoadEnabled` auf `true` gesetzt ist. | Wird im `sendEvent`-Befehl von Platform Web SDK angegeben. Aktiviert, indem die Option `renderDecisions` auf `true` gesetzt wird. |
| Manuelles Rendern von Inhalt | Die `applyOffer()`- und `applyOffers()` unterstützen nur das Festlegen von HTML | Der Befehl `applyPropositions` unterstützt das Festlegen, Ersetzen oder Anhängen von HTML für zusätzliche Flexibilität |
| Verfolgen benutzerdefinierter Ereignisse | Unterstützt mit `trackEvent()`- und `sendNotifications()`. Diese Funktionen sind Target-spezifisch und wirken sich nicht auf Adobe Analytics-Metriken aus. | Alle Daten aus Platform Web SDK `sendEvent`-Aufrufen werden an Target weitergeleitet. Zusätzliche Daten, die speziell für Target benötigt werden, sollten mit dem `sendEvent`-Befehl mit dem eventType-Wert `decisioning.propositionDisplay` oder `decisioning.propositionInteract` aufgenommen werden, um sicherzustellen, dass Adobe Analytics-Metriken nicht betroffen sind. |
| CNAME des Ziels | Unterstützt. Dies ist unabhängig vom CNAME, der für Analytics und den Experience Cloud ID-Service verwendet wird. | Nicht mehr relevant. Für alle Aufrufe von Platform Web SDK kann ein einziger CNAME verwendet werden. |
| Debugging | Die `mboxDisable`-, `mboxDebug`- und `mboxTrace`-URL-Parameter können zum Debugging mit den Entwickler-Tools Ihres Browsers verwendet werden.<br><br>Adobe Experience Platform Debugger ist auch ein unterstütztes Debugging-Tool. | Die URL-Parameter `mboxDisable`, `mboxDebug` und `mboxTrace` werden nicht unterstützt.<br><br>Sie können das Debugging von Web SDK aktivieren, indem Sie die `alloy_debug=true` zu Ihrer Abfragezeichenfolge hinzufügen oder `alloy("setDebug", { "enabled": true });` in Ihrer Entwicklerkonsole ausführen.<br><br>Die Adobe Experience Platform Debugger-Browser-Erweiterung kann verwendet werden, um eine Edge-Ablaufverfolgung für das Debugging zu initiieren.<br><br> Informationen finden Sie in der Dokumentation [Debuggen der Platform Web ](debugging.md) SDK&quot;. |
| Analytics for Target (A4T) | Verwendet SDID-Werte zum Zusammenfügen von Target- und Analytics-Aufrufen | Nativ unterstützt, ohne dass Stitching erforderlich ist |

>[!NOTE]
>
>Das Migrieren von Target zu Platform Web SDK unter Beibehaltung einer bestehenden AppMeasurement Adobe Analytics-Implementierung für eine bestimmte Seite wird nicht unterstützt.
>
> Es ist möglich, Ihre Implementierung von at.js (und AppMeasurement.js) Seite für Seite zu Platform Web SDK zu migrieren. Wenn Sie diesen Ansatz verwenden, ist es am besten, die [`idMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html?lang=de#id-migration-enabled)- und [`targetMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html?lang=de#targetMigrationEnabled)-Optionen so festzulegen, dass sie mit dem `true`-Befehl `configure`.

## at.js-Funktionen und Platform Web SDK-Entsprechungen

Viele at.js-Funktionen verwenden einen äquivalenten Ansatz unter Verwendung von Platform Web SDK, wie in der folgenden Tabelle beschrieben. Weitere Informationen zu den [at.js-Funktionen](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/) finden Sie im Adobe Target-Entwicklerhandbuch.

| Funktion at.js 2.x | Platform Web SDK-Entsprechung |
| --- | --- | 
| `getOffer()` und `getOffers()` | Um VEC-basierte Erlebnisse für [ anzufordern und ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html?lang=de#automatically-rendering-content)automatisch zu rendern), verwenden Sie den Befehl `sendEvent` und setzen die Option `renderDecisions` auf „true“.<br><br>Um formularbasierte Erlebnisse anzufordern oder Inhalte [manuell zu rendern](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html?lang=de#manually-rendering-content) geben Sie mit dem Befehl `decisionScopes` ein Array von `sendEvent` (Mboxes) an. |
| `applyOffer()` und `applyOffers()` | Verwenden Sie den Befehl [`applyPropositions`](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html?lang=de#applypropositions) zum Anwenden von Inhalten. Sie können HTML festlegen, ersetzen oder an einen bestimmten Selektor anhängen. |
| `triggerView()` | Platform Web SDK Trigger automatisch eine [Ansichtsänderung](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/web-sdk-atjs-comparison.html?lang=de#how-to-trigger-a-view-change-in-a-single-page-application) für den SPA-VEC, wenn die `web.webPageDetails.viewName`-Eigenschaft unter der `xdm`-Option des `sendEvent`-Befehls festgelegt ist. |
| `trackEvent()` und `sendNotifications()` | Verwenden Sie den `sendEvent`-Befehl mit einem [spezifischen `eventType`](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/web-sdk-atjs-comparison.html?lang=de#how-to-track-events): <br><br>`decisioning.propositionDisplay` signalisiert das Rendern einer Aktivität<br><br>`decisioning.propositionInteract` signalisiert eine Benutzerinteraktion mit einer Aktivität, wie z. B. einen Mausklick. |
| `targetGlobalSettings()` | Keine direkte Entsprechung. Weitere Informationen finden Sie [ „Vergleich ](detailed-comparison.md) Zielgruppeneinstellungen“. |
| `targetPageParams()` und `targetPageParamsAll()` | Alle in der Option `xdm` des Befehls `sendEvent` übergebenen Daten werden den Target-Mbox-Parametern zugeordnet. Da Mbox-Parameter mit serialisierter Punktnotation benannt werden, müssen Sie bei der Migration zu Platform Web SDK möglicherweise vorhandene Zielgruppen und Aktivitäten aktualisieren, um die neuen Mbox-Parameternamen zu verwenden. <br><br>Daten, die im Rahmen der `data.__adobe.target` des `sendEvent`-Befehls übergeben werden, werden [Zielprofil- und Recommendations-spezifischen Parametern) ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/target-overview.html?lang=de#single-profile-update). |
| Benutzerdefinierte at.js-Ereignisse | Nicht unterstützt. Den aktuellen Status finden Sie [ &quot;](https://github.com/orgs/adobe/projects/18/views/1?pane=item&itemId=17372355{target="_blank"}) Roadmap“. [Antwort-Token](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/accessing-response-tokens.html?lang=de) werden als Teil der `propositions` in der Antwort des `sendEvent`-Aufrufs bereitgestellt. |

## at.js-Einstellungen und Entsprechungen von Platform Web SDK

Die at.js-Bibliothek kann mit verschiedenen Einstellungen in der Target-Benutzeroberfläche konfiguriert und heruntergeladen werden. Diese Einstellungen können auch mit der Funktion [`targetGlobalSettings()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/targetglobalsettings/) aktualisiert werden. In der folgenden Tabelle werden diese Einstellungen mit denen verglichen, die in Platform Web SDK verfügbar sind.

| at.js-Einstellung | Platform Web SDK-Entsprechung |
| --- | --- |
| `bodyHiddenStyle` | Legen Sie die [`prehidingStyle`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html?lang=de#prehidingStyle) mit dem Befehl `configure` fest |
| `bodyHidingEnabled` | Wenn ein `prehidingStyle` mit dem Befehl `configure` definiert wird, ist diese Funktion aktiviert. Wenn kein Stil definiert ist, versucht Platform Web SDK nicht, Inhalte auszublenden. |
| `clientCode` | Automatisch konfiguriert |
| `cookieDomain` | Nicht zutreffend |
| `crossDomain` | Legen Sie die Option `thirdPartyCookiesEnabled` auf `true` mit dem Befehl `configure` fest, um Erstanbieter- und Drittanbieter-Cookies für domänenübergreifende Anwendungsfälle zu aktivieren |
| `cspScriptNonce` und `cspStyleNonce` | Weitere Informationen finden Sie in der Dokumentation [Konfigurieren eines CSP](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-a-csp.html?lang=de) |
| `dataProviders` | Nicht unterstützt |
| `decisioningMethod` | Alle Platform Web SDK-`sendEvent` verwenden serverseitige Entscheidungsfindung. Hybride und geräteinterne Entscheidungsfindung werden nicht unterstützt. |
| `defaultContentHiddenStyle` und `defaultContentVisibleStyle` | Gilt nur für at.js 1.x. Ähnlich wie at.js 2.x kann jede Art von Flimmerschutz für formularbasierte Erlebnisse mit benutzerdefiniertem Code erreicht werden. |
| `deviceIdLifetime` | Nicht unterstützt. Wenn `targetMigrationEnabled` mit dem `true`-Befehl auf `configure` gesetzt ist, wird das `mbox`-Cookie gesetzt, wobei die Lebensdauer des Geräts auf 2 Jahre eingestellt ist. Dieser Wert kann nicht konfiguriert werden. |
| `enabled` | Die Target-Funktion wird mit der Datenstromkonfiguration aktiviert oder deaktiviert |
| `globalMboxAutoCreate` | Legen Sie die `renderDecisions` `true`-Option fest, um mit dem `sendEvent`-Befehl automatisch VEC-basierte Erlebnisse abzurufen und zu rendern.<br><br>Fordern Sie eine `decisionScope` für `__view__` an, wenn Sie es vorziehen, VEC-basierte Erlebnisse manuell zu rendern. |
| `imsOrgId` | Legen Sie die `orgId` mit dem Befehl `configure` fest |
| `optinEnabled` und `optoutEnabled` | Siehe Platform Web SDK [Datenschutzoptionen](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=de). Die Option `defaultConsent` gilt für alle Adobe-Lösungen, die von Platform Web SDK unterstützt werden. |
| `overrideMboxEdgeServer` und `overrideMboxEdgeServerTimeout` | Nicht zutreffend. Alle Platform Web SDK-Anfragen verwenden das Adobe Experience Platform Edge-Netzwerk. |
| `pageLoadEnabled` | Legen Sie mit dem Befehl `renderDecisions` die `true` Option auf `sendEvent` fest. |
| `secureOnly` | Nicht unterstützt. Platform Web SDK setzt alle Cookies mit den Attributen `secure` und `sameSite="none"`. |
| `selectorsPollingTimeout` | Nicht unterstützt. Die Platform Web SDK verwendet einen Wert von 5 Sekunden. Benutzerdefinierter Code kann bei Bedarf zum manuellen Rendern von Inhalten verwendet werden. |
| `serverDomain` | Verwenden Sie die `edgeDomain` mit dem Befehl `configure` . |
| `telemetryEnabled` | Nicht zutreffend |
| `timeout` | Nicht unterstützt. Es wird empfohlen, sicherzustellen, dass jeder Flimmerminderungs-Code eine geeignete Zeitüberschreitung enthält. |
| `viewsEnabled` | Nicht unterstützt. Inhalte für Target-Ansichten werden immer beim ersten `sendEvent()`-Aufruf abgerufen, wenn `renderDecisions` auf `true` festgelegt oder der Entscheidungsumfang der `__view__` in der Anfrage enthalten ist. |
| `visitorApiTimeout` | Nicht zutreffend |


## Vergleich von Systemdiagrammen

Die folgenden Diagramme sollen Ihnen dabei helfen, die Datenflussunterschiede zwischen einer Target-Implementierung mit at.js und einer Implementierung mit Platform Web SDK zu verstehen.

### Systemdiagramm für at.js 2.x

![Verhalten von at.js 2.0 beim Laden der Seite](assets/target-at-js-2x-diagram.png){zoomable="yes"}

| Anruf | Details |
| --- | --- |
| 1 | Der Aufruf gibt die Experience Cloud-ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird die Kunden-ID durch einen weiteren Aufruf synchronisiert. |
| 2 | Die at.js-Bibliothek wird synchron geladen und blendet den Hauptteil des Dokuments aus (at.js kann auch asynchron geladen werden, wobei ein optionales Snippet zum Vorab-Ausblenden auf der Seite implementiert wird). |
| 3 | Seitenladeanfrage erfolgt, einschließlich aller konfigurierten Parameter, ECID, SDID und Kunden-ID. |
| 4 | Profilskripte werden ausgeführt und in den Profilspeicher übertragen. Der Store fordert qualifizierte Zielgruppen aus der Zielgruppenbibliothek an (z. B. aus Analytics, Audience Manager freigegebene Zielgruppen usw.). Kundenattribute werden in einem Batch-Prozess an den Profilspeicher gesendet. |
| 5 | Basierend auf URL, Anfrageparametern und Profildaten entscheidet Target, welche Aktivitäten und Erlebnisse für die aktuelle Seite und zukünftige Ansichten an den Besucher zurückgegeben werden sollen. |
| 6 | Zielgerichteter Inhalt, der an die Seite zurückgesendet wird, optional einschließlich Profilwerten für eine zusätzliche Personalisierung.<br><br>Zielgerichtete Inhalte auf der aktuellen Seite werden so schnell wie möglich angezeigt, ohne dass der Standardinhalt flackert.<br><br>Zielgerichtete Inhalte für zukünftige Ansichten einer Einzelseitenanwendung werden im Browser zwischengespeichert, sodass sie sofort ohne zusätzlichen Server-Aufruf angewendet werden können, wenn die Ansichten ausgelöst werden. |
| 7 | Analysedaten werden von der Seite an die Datenerfassungs-Server gesendet. |
| 8 | Zieldaten werden über die SDID mit Analytics-Daten abgeglichen und in den Analytics-Reporting-Speicher verarbeitet. Analytics-Daten können dann sowohl in Analytics als auch in Target über A4T-Berichte angezeigt werden. |

Weitere Informationen zur Implementierung von Target (mithilfe [.js für Einzelseitenanwendungen) finden Sie im ](https://developer.adobe.com/target/implement/client-side/atjs/how-to-deployatjs/target-atjs-single-page-application/).

### Systemdiagramm für Platform Web SDK

![Abbildung der Adobe Target-Edge-Entscheidungsfindung mit Platform Web SDK](assets/target-platform-web-sdk.png)

| Anruf | Details |
| --- | --- |
| 1 | Das Gerät lädt die Platform Web SDK. Platform Web SDK sendet eine Anfrage mit XDM-Daten, der Datenstrom-Umgebungs-ID, den weitergegebenen Parametern und der Kunden-ID an das Edge-Netzwerk (optional). Seite (oder Container) wird ausgeblendet. |
| 2 | Das Edge-Netzwerk sendet die Anfrage an die Edge-Services, um sie mit der Besucher-ID, dem Einverständnis und anderen Besucherkontextinformationen wie Geolokalisierung und gerätefreundlichen Namen anzureichern. |
| 3 | Das Edge-Netzwerk sendet die angereicherte Personalisierungsanfrage mit der Besucher-ID und den weitergegebenen Parametern an den Target-Edge. |
| 4 | Profilskripte werden ausgeführt und fließen dann in den Target-Profilspeicher ein. Der Profilspeicher ruft Segmente aus der Zielgruppenbibliothek ab (z. B. freigegebene Segmente aus Adobe Analytics, Adobe Audience Manager oder Adobe Experience Platform). |
| 5 | Basierend auf URL-Anfrageparametern und Profildaten bestimmt Target, welche Aktivitäten und Erlebnisse für den Besucher in der aktuellen Seitenansicht und für zukünftige vorab abgerufene Ansichten angezeigt werden sollen. Target sendet diese dann zurück an das Edge-Netzwerk. |
| 6 | a. Das Edge Network sendet die Personalisierungsantwort zurück an die Seite, wobei optional Profilwerte für die zusätzliche Personalisierung enthalten sind. Personalisierte Inhalte auf der aktuellen Seite werden so schnell wie möglich ohne Flackern der Standardinhalte angezeigt.<br><br> B. Personalisierte Inhalte für Ansichten, die als Ergebnis von Benutzeraktionen in einer Single Page Application (SPA) angezeigt werden, werden zwischengespeichert, um sie sofort ohne zusätzliche Server-Aufrufe wiederzugeben.<br><br>c. Das Edge Network sendet die Besucher-ID und andere Werte in Cookies (z. B. Einverständnis, Sitzungs-ID, Identität, Cookie-Prüfung, Personalisierung usw.). |
| 7 | Das Edge Network leitet Analytics for Target(A4T)-Details (Aktivitäts-, Erlebnis- und Konversionsmetadaten) an den Analytics-Edge weiter. |

Im Entwicklerhandbuch finden Sie weitere Informationen zur [ von Target mithilfe von Platform Web SDK für Einzelseitenanwendungen](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/spa-implementation.html?lang=de).

Nachdem Sie über ein gutes technisches Verständnis Ihrer aktuellen Target-Implementierung und der von Ihnen verwendeten Funktionen verfügen, besteht der nächste Schritt darin, die [Ersteinrichtung“ ](initial-setup.md).

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=de#M463) posten.
