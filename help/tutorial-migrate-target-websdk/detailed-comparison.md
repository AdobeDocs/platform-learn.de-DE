---
title: Vergleich von at.js 2.x mit Web SDK | Migrieren von Target von at.js 2.x zum Web SDK
description: Lernen Sie die Unterschiede zwischen at.js 2.x und dem Platform Web SDK kennen, einschließlich Funktionen, Einstellungen und Datenfluss.
exl-id: b6f0ac2b-0d8e-46ce-8e9f-7bbc61eb20ec
source-git-commit: 299b9586fb5c8e9c9ef3427e08035806af1d9a6b
workflow-type: tm+mt
source-wordcount: '2007'
ht-degree: 4%

---

# Vergleich von at.js mit dem Platform Web SDK

Die eigenständige Adobe Target at.js-Bibliothek unterscheidet sich erheblich vom Platform Web SDK. Die folgenden Tabellen sind eine Referenz, die Sie bei der Bewertung von Bereichen Ihrer Implementierung unterstützen soll, auf die Sie sich während des Migrationsprozesses konzentrieren müssen.

Nachdem Sie die unten stehenden Informationen überprüft und Ihre aktuelle technische at.js-Implementierung bewertet haben, sollten Sie Folgendes verstehen:

- Welche Target-Funktionen werden vom Platform Web SDK unterstützt?
- Welche at.js-Funktionen verfügen über Platform Web SDK-Entsprechungen
- Anwendung von Target-Einstellungen mit dem Platform Web SDK
- Unterschiede zwischen dem Datenfluss von at.js und dem Platform Web SDK

Wenn Sie mit dem Platform Web SDK noch nicht vertraut sind, machen Sie sich keine Gedanken - die unten stehenden Elemente werden in diesem Tutorial ausführlicher behandelt.

## Funktionsvergleich

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Target-Profil aktualisieren | Unterstützt | Unterstützt |
| Trigger-Ansicht für SPA | Unterstützt | Unterstützt |
| Target Recommendations | Unterstützt | Unterstützt |
| Formularbasierte Angebote abrufen | Unterstützt | Unterstützt |
| Verfolgen von Ereignissen | Unterstützt | Unterstützt |
| A4T: Einzelseitenanwendung | Unterstützt | Unterstützt |
| A4T: Klick-Tracking | Unterstützt | Unterstützt |
| A4T: Clientseitige Protokollierung | Unterstützt | Unterstützt |
| A4T: Serverseitige Protokollierung | Unterstützt | Unterstützt |
| Angebote anwenden | Unterstützt | Unterstützt |
| Ansicht in SPA ohne Benachrichtigungen erneut rendern | Unterstützt | Unterstützt |
| Hybride Anwendungen | Unterstützt | Unterstützt |
| QA-URLs | Unterstützt | Unterstützt |
| Mbox-Drittanbieter-IDs | Unterstützt | Unterstützt |
| Kundenattribute | Unterstützt | Unterstützt |
| Remote-Angebote | Unterstützt | Unterstützt |
| Umleitungsangebote | Unterstützt | Unterstützt. Eine Umleitung von einer Seite mit Platform Web SDK zu einer Seite mit at.js (und umgekehrt) wird jedoch nicht unterstützt. |
| On-Device Decisioning | Unterstützt | Derzeit nicht unterstützt |
| Vorabruf-mboxes | Unterstützt für benutzerdefinierte Bereiche und SPA VEC | Der Vorabruf ist der Standardmodus für das Web SDK. |
| Benutzerspezifische Ereignisse | Unterstützt | Nicht unterstützt. Informationen zum aktuellen Status finden Sie in der [öffentlichen Roadmap](https://github.com/orgs/adobe/projects/18/views/1?pane=item&amp;itemId=17372355{target="_blank"}) . |
| Antwort-Token | Unterstützt | Unterstützt. Codebeispiele und Unterschiede zwischen at.js und dem Platform Web SDK finden Sie in der Dokumentation zu den [dedizierten Antwort-Token](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html) . |
| Datenanbieter | Unterstützt | Nicht unterstützt. Mit benutzerdefiniertem Code kann ein Platform Web SDK `sendEvent` -Befehl Trigger werden, nachdem Daten von einem anderen Anbieter abgerufen wurden. |


## Wichtige Hinweise

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Flimmern | Das Vorabausblendungs-Snippet für asynchrone Implementierungen verwendet eine Stil-ID von `at-body-style`. at.js sucht nach dieser Element-ID, um den Stil zu entfernen, sobald eine Antwort empfangen wird. | Der standardmäßige Codeausschnitt zur Vorab-Ausblendung verwendet die Stil-ID `alloy-prehiding`. Das Web SDK ist nicht mit dem at.js-Codeausschnitt zur Vorab-Ausblendung kompatibel, daher muss es im Rahmen des Migrationsprozesses geändert werden. |
| Automatisches Rendern von Inhalten beim Laden der Seite | Wird mit einer globalen Target-Einstellung gesteuert. Aktiviert, wenn `pageLoadEnabled` auf `true` gesetzt ist. | Wird im Befehl &quot;Platform Web SDK `sendEvent`&quot;angegeben. Aktiviert durch Festlegen der `renderDecisions` -Option auf `true`. |
| Manuelles Rendern von Inhalten | Die Funktionen `applyOffer()` und `applyOffers()` unterstützen nur das Festlegen von HTML | Der Befehl `applyPropositions` unterstützt das Festlegen, Ersetzen oder Anhängen von HTML für mehr Flexibilität |
| Verfolgen benutzerspezifischer Ereignisse | Unterstützt mit den Funktionen `trackEvent()` und `sendNotifications()`. Diese Funktionen sind spezifisch für Target und wirken sich nicht auf Adobe Analytics-Metriken aus. | Alle Daten aus Platform Web SDK `sendEvent` -Aufrufen werden an Target weitergeleitet. Zusätzliche Daten, die speziell für Target benötigt werden, sollten mit dem Befehl `sendEvent` mit dem Ereignistyp `decisioning.propositionDisplay` oder `decisioning.propositionInteract` eingeschlossen werden, um sicherzustellen, dass Adobe Analytics-Metriken nicht betroffen sind. |
| Target CNAME | Unterstützt. Dies unterscheidet sich vom CNAME, der für Analytics und den Experience Cloud ID-Dienst verwendet wird. | Nicht mehr relevant. Ein einzelner CNAME kann für alle Platform Web SDK-Aufrufe verwendet werden. |
| Debugging | Die URL-Parameter `mboxDisable`, `mboxDebug` und `mboxTrace` können zum Debugging mit den Entwicklertools Ihres Browsers verwendet werden.<br><br>Der Adobe Experience Platform Debugger ist auch ein unterstütztes Debugging-Tool. | Die URL-Parameter `mboxDisable`, `mboxDebug` und `mboxTrace` werden nicht unterstützt.<br><br>Sie können das Debugging des Web SDK aktivieren, indem Sie die `alloy_debug=true` zu Ihrer Abfragezeichenfolge hinzufügen oder `alloy("setDebug", { "enabled": true });` in Ihrer Entwicklerkonsole ausführen.<br><br>Die Adobe Experience Platform Debugger-Browsererweiterung kann verwendet werden, um einen Edge-Trace für das Debugging zu initiieren.Weitere Informationen finden Sie in der Dokumentation zum [Debugging des Platform Web SDK](debugging.md) .<br><br> |
| Analytics for Target (A4T) | Verwendet SDID-Werte zum Zuordnen von Target- und Analytics-Aufrufen | Nativ unterstützt ohne Stitching |

>[!NOTE]
>
>Die Migration von Target zum Platform Web SDK unter Beibehaltung einer bestehenden AppMeasurement Adobe Analytics-Implementierung für eine bestimmte Seite wird nicht unterstützt.
>
> Es ist möglich, Ihre at.js- (und AppMeasurement.js-) Implementierung auf Platform Web SDK einzeln zu migrieren. Wenn Sie diesen Ansatz wählen, ist es am besten, die Optionen [`idMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) und [`targetMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) mit dem Befehl `configure` auf `true` festzulegen.

## &quot;at.js&quot;-Funktionen und Platform Web SDK-Entsprechungen

Viele at.js-Funktionen verwenden einen äquivalenten Ansatz mit dem Platform Web SDK, wie in der folgenden Tabelle beschrieben. Weitere Informationen zu den [at.js-Funktionen](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/) finden Sie im Adobe Target-Entwicklerhandbuch.

| Funktion &quot;at.js 2.x&quot; | Platform Web SDK-Entsprechung |
| --- | --- | 
| `getOffer()` und `getOffers()` | Verwenden Sie zum Anfordern und [ automatischen Rendern von ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#automatically-rendering-content) VEC-basierten Erlebnissen auf Target den Befehl `sendEvent` und legen Sie die Option `renderDecisions` auf &quot;true&quot;fest.<br><br>Um formularbasierte Erlebnisse anzufordern oder um [manuell Inhalte zu rendern](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#manually-rendering-content), geben Sie ein Array von `decisionScopes` (mboxes) mit dem Befehl `sendEvent` an. |
| `applyOffer()` und `applyOffers()` | Verwenden Sie den Befehl [`applyPropositions`](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#applypropositions) , um Inhalte anzuwenden. Sie können festlegen, HTML an einen bestimmten Selektor anzuhängen, ihn zu ersetzen oder anzuhängen. |
| `triggerView()` | Das Platform Web SDK Trigger für die Zwecke des SPA VEC automatisch eine [Ansichtsänderung](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/web-sdk-atjs-comparison.html#how-to-trigger-a-view-change-in-a-single-page-application), wenn die Eigenschaft `web.webPageDetails.viewName` unter der Option `xdm` des Befehls `sendEvent` festgelegt ist. |
| `trackEvent()` und `sendNotifications()` | Verwenden Sie den Befehl `sendEvent` mit einem [spezifischen `eventType`](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/web-sdk-atjs-comparison.html#how-to-track-events) -Satz: <br><br>`decisioning.propositionDisplay` signalisiert die Wiedergabe einer Aktivität.<br><br>`decisioning.propositionInteract` signalisiert eine Benutzerinteraktion mit einer Aktivität, z. B. einen Mausklick. |
| `targetGlobalSettings()` | Keine direkte Entsprechung. Weitere Informationen finden Sie im [Vergleich der Target-Einstellungen](detailed-comparison.md) . |
| `targetPageParams()` und `targetPageParamsAll()` | Alle Daten, die in der Option `xdm` des Befehls `sendEvent` übergeben werden, werden Target-Mbox-Parametern zugeordnet. Da Mbox-Parameter mit serialisierter Punktnotation benannt werden, müssen Sie bei der Migration zum Platform Web SDK möglicherweise vorhandene Zielgruppen und Aktivitäten aktualisieren, um die neuen Mbox-Parameternamen zu verwenden. <br><br>Daten, die als Teil von `data.__adobe.target` des Befehls `sendEvent` übergeben werden, werden [Target-Profil und Recommendations-spezifische Parameter](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/target-overview.html#single-profile-update) zugeordnet. |
| Benutzerdefinierte at.js-Ereignisse | Nicht unterstützt. Informationen zum aktuellen Status finden Sie in der [öffentlichen Roadmap](https://github.com/orgs/adobe/projects/18/views/1?pane=item&amp;itemId=17372355{target="_blank"}) . [Antwort-Token](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/accessing-response-tokens.html?lang=de) werden als Teil des `propositions` in der Antwort des `sendEvent` -Aufrufs bereitgestellt. |

## at.js-Einstellungen und entsprechende Platform Web SDK-Elemente

Die at.js-Bibliothek kann mit verschiedenen Einstellungen in der Target-Benutzeroberfläche konfiguriert und heruntergeladen werden. Diese Einstellungen können auch mit der Funktion [`targetGlobalSettings()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/targetglobalsettings/) aktualisiert werden. In der folgenden Tabelle werden diese Einstellungen mit denen des Platform Web SDK verglichen.

| at.js-Einstellung | Platform Web SDK-Entsprechung |
| --- | --- |
| `bodyHiddenStyle` | Setzen Sie den [`prehidingStyle`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#prehidingStyle) mit dem Befehl `configure` |
| `bodyHidingEnabled` | Wenn eine `prehidingStyle` mit dem Befehl `configure` definiert ist, ist diese Funktion aktiviert. Wenn kein Stil definiert ist, versucht das Platform Web SDK nicht, Inhalte auszublenden. |
| `clientCode` | Automatisch konfiguriert |
| `cookieDomain` | Nicht zutreffend |
| `crossDomain` | Setzen Sie die Option `thirdPartyCookiesEnabled` mit dem Befehl `configure` auf `true` , um Erstanbieter- und Drittanbieter-Cookies für domänenübergreifende Anwendungsfälle zu aktivieren. |
| `cspScriptNonce` und `cspStyleNonce` | Weitere Informationen finden Sie in der Dokumentation zum [Konfigurieren eines CSP](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-a-csp.html) |
| `dataProviders` | Nicht unterstützt |
| `decisioningMethod` | Alle Befehle des Platform Web SDK `sendEvent` verwenden serverseitige Entscheidungsfindung. Hybride und geräteübergreifende Entscheidungen werden nicht unterstützt. |
| `defaultContentHiddenStyle` und `defaultContentVisibleStyle` | Gilt nur für at.js 1.x. Ähnlich wie bei at.js 2.x können Sie mit benutzerdefiniertem Code für formularbasierte Erlebnisse eine Flimmerverhinderung durchführen. |
| `deviceIdLifetime` | Nicht unterstützt. Wenn `targetMigrationEnabled` mit dem Befehl `configure` auf `true` gesetzt ist, wird das Cookie `mbox` gesetzt, wobei die Gerätelebensdauer auf 2 Jahre eingestellt ist. Dieser Wert kann nicht konfiguriert werden. |
| `enabled` | Die Target-Funktion ist mit der Datenstream-Konfiguration aktiviert oder deaktiviert |
| `globalMboxAutoCreate` | Setzen Sie die Option `renderDecisions` mit dem Befehl `sendEvent` auf `true` , um VEC-basierte Erlebnisse automatisch abzurufen und zu rendern.<br><br>Fordern Sie einen `decisionScope` für `__view__` an, wenn Sie VEC-basierte Erlebnisse lieber manuell rendern möchten. |
| `imsOrgId` | Setzen Sie `orgId` mit dem Befehl `configure` |
| `optinEnabled` und `optoutEnabled` | Siehe Platform Web SDK [Datenschutzoptionen](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html). Die Option `defaultConsent` gilt für alle Adobe-Lösungen, die vom Platform Web SDK unterstützt werden. |
| `overrideMboxEdgeServer` und `overrideMboxEdgeServerTimeout` | Nicht zutreffend. Alle Platform Web SDK-Anforderungen verwenden das Adobe Experience Platform Edge-Netzwerk. |
| `pageLoadEnabled` | Setzen Sie die `renderDecisions` -Option mit dem Befehl `sendEvent` auf `true` |
| `secureOnly` | Nicht unterstützt. Das Platform Web SDK setzt alle Cookies mit den Attributen `secure` und `sameSite="none"`. |
| `selectorsPollingTimeout` | Nicht unterstützt. Das Platform Web SDK verwendet einen Wert von 5 Sekunden. Benutzerdefinierter Code kann bei Bedarf zum manuellen Rendern von Inhalten verwendet werden. |
| `serverDomain` | Verwenden Sie die Einstellung `edgeDomain` mit dem Befehl `configure` . |
| `telemetryEnabled` | Nicht zutreffend |
| `timeout` | Nicht unterstützt. Es wird empfohlen, sicherzustellen, dass jeder Flackern-Minderungscode eine geeignete Zeitüberschreitung enthält. |
| `viewsEnabled` | Nicht unterstützt. Inhalte für Target-Ansichten werden immer beim ersten `sendEvent()` -Aufruf abgerufen, wenn `renderDecisions` auf `true` oder der `__view__` decisionScope in der Anfrage enthalten ist. |
| `visitorApiTimeout` | Nicht zutreffend |


## Vergleich von Systemdiagrammen

Die folgenden Diagramme sollen Ihnen dabei helfen, die Unterschiede zwischen einem Datenfluss zwischen einer Target-Implementierung mit at.js und einer Implementierung mit dem Platform Web SDK zu verstehen.

### at.js 2.x-Systemdiagramm

![Verhalten von at.js 2.0 beim Laden der Seite](assets/target-at-js-2x-diagram.png){zoomable="yes"}

| Aufruf | Details |
| --- | --- |
| 1 | Ein Aufruf gibt Experience Cloud ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird bei einem weiteren Aufruf die Kunden-ID synchronisiert. |
| 2 | Die at.js-Bibliothek wird synchron geladen und blendet den Dokumenttext aus (at.js kann auch asynchron mit einem optionalen Pre-hiding-Snippet geladen werden, das auf der Seite implementiert ist). |
| 3 | Die Seitenladeanforderung umfasst alle konfigurierten Parameter, ECID, SDID und Kunden-ID. |
| 4 | Profilskripte werden ausgeführt und in den Profilspeicher eingespeist. Der Store ruft geeignete Zielgruppen aus der Zielgruppenbibliothek ab (z. B. über Analytics, Audience Manager usw. freigegebene Zielgruppen). Kundenattribute werden in einem Batch-Prozess an den Profilspeicher gesendet. |
| 5 | Basierend auf URL, Anforderungsparametern und Profildaten entscheidet Target, welche Aktivitäten und Erlebnisse für die aktuelle Seite und zukünftige Ansichten an den Besucher zurückgegeben werden sollen. |
| 6 | Zielgerichteter Inhalt, der zurück an die Seite gesendet wird, optional einschließlich Profilwerten für eine zusätzliche Personalisierung.<br><br>Zielgerichteter Inhalt auf der aktuellen Seite wird so schnell wie möglich bereitgestellt, ohne dass Standardinhalte flackern.<br><br>Zielgerichteter Inhalt für zukünftige Ansichten einer Einzelseitenanwendung wird im Browser zwischengespeichert, sodass er sofort ohne zusätzlichen Server-Aufruf angewendet werden kann, wenn die Ansichten ausgelöst werden. |
| 7 | Analytics-Daten, die von der Seite an die Datenerfassungsserver gesendet werden. |
| 8 | Target-Daten werden über die SDID mit Analytics-Daten abgeglichen und im Analytics-Berichtspeicher verarbeitet. Analytics-Daten können dann sowohl in Analytics als auch in Target über A4T-Berichte angezeigt werden. |

Weitere Informationen zur Implementierung von Target mit at.js für Einzelseitenanwendungen finden Sie im Entwicklerhandbuch](https://developer.adobe.com/target/implement/client-side/atjs/how-to-deployatjs/target-atjs-single-page-application/).[

### Systemdiagramm für das Platform Web SDK

![Diagramm der Adobe Target-Edge-Entscheidung mit dem Platform Web SDK](assets/target-platform-web-sdk.png)

| Aufruf | Details |
| --- | --- |
| 1 | Das Gerät lädt das Platform Web SDK. Das Platform Web SDK sendet eine Anfrage mit XDM-Daten, der ID der Datastreams-Umgebung, den übergebenen Parametern und der Kunden-ID (optional) an das Edge-Netzwerk. Seite (oder Container) ist vorab ausgeblendet. |
| 2 | Das Edge-Netzwerk sendet die Anfrage an die Edge-Dienste, um sie mit der Besucher-ID, der Zustimmung und anderen Besucherkontextinformationen wie Geolocation und gerätefreundlichen Namen anzureichern. |
| 3 | Das Edge-Netzwerk sendet die angereicherte Personalisierungsanforderung mit der Besucher-ID und den übergebenen Parametern an den Target-Edge. |
| 4 | Profilskripte werden ausgeführt und dann in den Target-Profilspeicher eingespeist. Der Profilspeicher ruft Segmente aus der Zielgruppenbibliothek ab (z. B. freigegebene Segmente aus Adobe Analytics, Adobe Audience Manager und Adobe Experience Platform). |
| 5 | Basierend auf URL-Anforderungsparametern und Profildaten bestimmt Target, welche Aktivitäten und Erlebnisse für den Besucher für die aktuelle Seitenansicht und für künftige vorab abgerufene Ansichten angezeigt werden sollen. Target sendet diese dann zurück an das Edge-Netzwerk. |
| 6 | a. Das Edge-Netzwerk sendet die Personalisierungsantwort zurück an die Seite, optional einschließlich der Profilwerte für eine zusätzliche Personalisierung. Personalisierte Inhalte auf der aktuellen Seite werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern.<br><br>b. Personalisierte Inhalte für Ansichten, die als Ergebnis von Benutzeraktionen in einer Einzelseiten-App (SPA) angezeigt werden, werden für sofortiges Rendering ohne zusätzliche Server-Aufrufe zwischengespeichert.<br><br>c. Das Edge-Netzwerk sendet die Besucher-ID und andere Werte in Cookies (z. B. Zustimmung, Sitzungs-ID, Identität, Cookie-Überprüfung, Personalisierung usw.). |
| 7 | Das Edge-Netzwerk leitet Analytics for Target (A4T)-Details (Aktivitäts-, Erlebnis- und Konversionsmetadaten) an den Analytics-Edge weiter. |

Weitere Informationen zur Implementierung von Target mit dem Platform Web SDK für Einzelseitenanwendungen finden Sie im Entwicklerhandbuch](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/spa-implementation.html) .[

Nachdem Sie ein gutes technisches Verständnis Ihrer aktuellen Target-Implementierung und der von Ihnen verwendeten Funktionen haben, besteht der nächste Schritt darin, die [Ersteinrichtung](initial-setup.md) durchzuführen.

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
