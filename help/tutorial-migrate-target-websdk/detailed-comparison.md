---
title: Vergleich von at.js 2.x mit Web SDK | Migrieren von Target von at.js 2.x zum Web SDK
description: Lernen Sie die Unterschiede zwischen at.js 2.x und dem Platform Web SDK kennen, einschließlich Funktionen, Einstellungen und Datenfluss.
source-git-commit: 8209b13b745dbea418003b133a6834825947950e
workflow-type: tm+mt
source-wordcount: '2154'
ht-degree: 8%

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

|  | Target at.js 2.x | Platform Web-SDK |
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
| Kundenattribute | Unterstützt | Unterstützt  |
| Remote-Angebote | Unterstützt | Unterstützt |
| Weiterleitungsangebote | Unterstützt | Unterstützt. Eine Umleitung von einer Seite mit Platform Web SDK zu einer Seite mit at.js (und umgekehrt) wird jedoch nicht unterstützt. |
| On-Device Decisioning | Unterstützt | Derzeit nicht unterstützt |
| Vorabruf-mboxes | Unterstützt | Standardmäßig für alle neuen, nach dem 1. Oktober 2022 gestarteten Migrationen aktiviert |
| Benutzerspezifische Ereignisse | Unterstützt | Nicht unterstützt. Siehe [öffentliche Roadmap](https://github.com/orgs/adobe/projects/18/views/1?pane=item&amp;itemId=17372355{target="_blank"}) für den aktuellen Status. |
| Antwort-Token | Unterstützt | Unterstützt. Siehe Abschnitt [Dokumentation zu dedizierten Antwort-Token](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html) für Codebeispiele und Unterschiede zwischen at.js und Platform Web SDK |
| Datenanbieter   | Unterstützt | Nicht unterstützt. Benutzerdefinierter Code kann zum Trigger eines Platform Web SDK verwendet werden `sendEvent` -Befehl aus, nachdem Daten von einem anderen Anbieter abgerufen wurden. |


## Wichtige Hinweise

|  | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Flimmern | Das Vorabausblendungs-Snippet für asynchrone Implementierungen verwendet eine Stil-ID von `at-body-style`. at.js sucht nach dieser Element-ID, um den Stil zu entfernen, sobald eine Antwort empfangen wird. | Der standardmäßige Codeausschnitt zur Vorab-Ausblendung verwendet eine Stil-ID von `alloy-prehiding`. Das Web SDK ist nicht mit dem at.js-Codeausschnitt zur Vorab-Ausblendung kompatibel, daher muss es im Rahmen des Migrationsprozesses geändert werden. |
| Automatisches Rendern von Inhalten beim Laden der Seite | Wird mit einer globalen Target-Einstellung gesteuert. Aktiviert bei `pageLoadEnabled` auf `true`. | Wird im Platform Web SDK angegeben `sendEvent` Befehl. Aktiviert durch Festlegen der `renderDecisions` -Option `true`. |
| Manuelles Rendern von Inhalten | Die `applyOffer()` und `applyOffers()` Funktionen unterstützen nur HTML | Die `applyPropositions` unterstützt das Festlegen, Ersetzen oder Anhängen von HTML für mehr Flexibilität |
| Verfolgen benutzerspezifischer Ereignisse | Unterstützt mit `trackEvent()` und `sendNotifications()` Funktionen. Diese Funktionen sind spezifisch für Target und wirken sich nicht auf Adobe Analytics-Metriken aus. | Alle Daten aus dem Platform Web SDK `sendEvent` -Aufrufe an Target weitergeleitet werden. Zusätzliche Daten, die speziell für Target benötigt werden, sollten in die `sendEvent` -Befehl mit einem eventType von `decisioning.propositionDisplay` oder `decisioning.propositionInteract` , um sicherzustellen, dass Adobe Analytics-Metriken nicht betroffen sind. |
| Target CNAME | Unterstützt. Dies unterscheidet sich von dem für Analytics verwendeten CNAME und dem Experience Cloud-ID-Dienst. | Nicht mehr relevant. Ein einzelner CNAME kann für alle Platform Web SDK-Aufrufe verwendet werden. |
| Debugging | Die `mboxDisable`, `mboxDebug`und `mboxTrace` URL-Parameter können zum Debugging mit den Entwicklertools Ihres Browsers verwendet werden.<br><br>Der Adobe Experience Platform Debugger wird ebenfalls unterstützt. | Die `mboxDisable`, `mboxDebug`und `mboxTrace` URL-Parameter werden nicht unterstützt.<br><br>Sie können das Debugging des Web SDK aktivieren, indem Sie die `alloy_debug=true` in Ihre Abfragezeichenfolge oder in Ausführung `alloy("setDebug", { "enabled": true });` in Ihrer Entwicklerkonsole.<br><br>Die Adobe Experience Platform Debugger-Browsererweiterung kann verwendet werden, um einen Edge-Trace für das Debugging zu initiieren.<br><br>Siehe Abschnitt [Debugging des Platform Web SDK](debugging.md) Dokumentation finden Sie weitere Informationen. |
| Analytics for Target (A4T) | Verwendet SDID-Werte zum Zuordnen von Target- und Analytics-Aufrufen | Nativ unterstützt ohne Stitching |

>[!NOTE]
>
>Die Migration von Target zum Platform Web SDK unter Beibehaltung einer bestehenden AppMeasurement Adobe Analytics-Implementierung für eine bestimmte Seite wird nicht unterstützt.
>
> Sie können Ihre Implementierung von at.js (und AppMeasurement.js) auf Platform Web SDK jeweils eine Seite migrieren. Wenn Sie diesen Ansatz wählen, sollten Sie die [`idMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) und [`targetMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) Optionen zu `true` mit dem `configure` Befehl.

## &quot;at.js&quot;-Funktionen und Platform Web SDK-Entsprechungen

Viele at.js-Funktionen verwenden einen äquivalenten Ansatz mit dem Platform Web SDK, wie in der folgenden Tabelle beschrieben. Weitere Informationen zum [&quot;at.js&quot;-Funktionen](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), siehe Adobe Target-Entwicklerhandbuch.

| Funktion &quot;at.js 2.x&quot; | Platform Web SDK-Entsprechung |
| --- | --- | 
| `getOffer()` und `getOffers()` | Auf Anfrage und [automatische Wiedergabe](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#automatically-rendering-content) Target VEC-basierte Erlebnisse verwenden Sie die `sendEvent` und legen Sie die `renderDecisions` auf &quot;true&quot;gesetzt.<br><br>So fordern Sie formularbasierte Erlebnisse an oder an [Manuell rendern](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#manually-rendering-content) Inhalt angeben, ein Array von `decisionScopes` (mboxes) mit der `sendEvent` Befehl. |
| `applyOffer()` und `applyOffers()` | Verwenden Sie die [`applyPropositions`](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#applypropositions) -Befehl, um Inhalte anzuwenden. Sie können festlegen, dass HTML an einen bestimmten Selektor angehängt, ersetzt oder angehängt wird. |
| `triggerView()` | Das Platform Web SDK Trigger automatisch eine [Änderung der Ansicht](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/web-sdk-atjs-comparison.html#how-to-trigger-a-view-change-in-a-single-page-application) für die Zwecke des SPA VEC, wenn die `web.webPageDetails.viewName` -Eigenschaft festgelegt unter der `xdm` der `sendEvent` Befehl. |
| `trackEvent()` und `sendNotifications()` | Verwenden Sie die `sendEvent` -Befehl mit [spezifisch `eventType`](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/web-sdk-atjs-comparison.html#how-to-track-events) set:<br><br>`decisioning.propositionDisplay` signalisiert das Rendering einer Aktivität<br><br>`decisioning.propositionInteract` signalisiert eine Benutzerinteraktion mit einer Aktivität, z. B. einen Mausklick. |
| `targetGlobalSettings()` | Keine direkte Entsprechung. Siehe Abschnitt [Vergleich der Zieleinstellungen](detailed-comparison.md) für weitere Details. |
| `targetPageParams()` und `targetPageParamsAll()` | Alle Daten, die an die `xdm` der `sendEvent` -Befehl den Target-Mbox-Parametern zugeordnet. Da Mbox-Parameter mit serialisierter Punktnotation benannt werden, müssen Sie bei der Migration zum Platform Web SDK möglicherweise vorhandene Zielgruppen und Aktivitäten aktualisieren, um die neuen Mbox-Parameternamen zu verwenden. <br><br>Daten, die als Teil von `data.__adobe.target` des `sendEvent` -Befehl wird zugeordnet zu [Target-Profil und Recommendations-spezifische Parameter](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/target-overview.html#single-profile-update). |
| Benutzerdefinierte at.js-Ereignisse | Nicht unterstützt. Siehe [öffentliche Roadmap](https://github.com/orgs/adobe/projects/18/views/1?pane=item&amp;itemId=17372355{target="_blank"}) für den aktuellen Status. [Antwort-Token](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/accessing-response-tokens.html) als Teil der `propositions` in der Antwort der `sendEvent` aufrufen. |

## at.js-Einstellungen und entsprechende Platform Web SDK-Elemente

Die at.js-Bibliothek kann mit verschiedenen Einstellungen in der Target-Benutzeroberfläche konfiguriert und heruntergeladen werden. Diese Einstellungen können auch mit dem [`targetGlobalSettings()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/targetglobalsettings/) -Funktion. In der folgenden Tabelle werden diese Einstellungen mit denen des Platform Web SDK verglichen.

| at.js-Einstellung | Platform Web SDK-Entsprechung |
| --- | --- |
| `bodyHiddenStyle` | Legen Sie die [`prehidingStyle`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#prehidingStyle) mit dem `configure` command |
| `bodyHidingEnabled` | Wenn eine `prehidingStyle` wird mit dem `configure` -Befehl eingeben, ist diese Funktion aktiviert. Wenn kein Stil definiert ist, versucht das Platform Web SDK nicht, Inhalte auszublenden. |
| `clientCode` | Automatisch konfiguriert |
| `cookieDomain` | Nicht zutreffend |
| `crossDomain` | Legen Sie die `thirdPartyCookiesEnabled` -Option `true` mit dem `configure` -Befehl zum Aktivieren von Erstanbieter- und Drittanbieter-Cookies für domänenübergreifende Anwendungsfälle |
| `cspScriptNonce` und `cspStyleNonce` | Weitere Informationen finden Sie in der Dokumentation für [Konfigurieren eines CSP](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-a-csp.html) |
| `dataProviders` | Nicht unterstützt |
| `decisioningMethod` | Alle Platform Web SDK `sendEvent` -Befehle verwenden serverseitige Entscheidungsfindung. Hybride und geräteübergreifende Entscheidungen werden nicht unterstützt. |
| `defaultContentHiddenStyle` und `defaultContentVisibleStyle` | Gilt nur für at.js 1.x. Ähnlich wie bei at.js 2.x können Sie mit benutzerdefiniertem Code für formularbasierte Erlebnisse eine Flimmerverhinderung durchführen. |
| `deviceIdLifetime` | Nicht unterstützt. Wenn `targetMigrationEnabled` auf `true` mit dem `configure` -Befehl, die `mbox` -Cookie gesetzt wird, wobei die Gerätelebensdauer auf 2 Jahre festgelegt ist. Dieser Wert kann nicht konfiguriert werden. |
| `enabled` | Die Target-Funktion ist mit der Datenstream-Konfiguration aktiviert oder deaktiviert |
| `globalMboxAutoCreate` | Legen Sie die `renderDecisions` -Option `true` mit dem `sendEvent` -Befehl zum automatischen Abrufen und Rendern von VEC-basierten Erlebnissen.<br><br>Anfordern einer `decisionScope` für `__view__` , wenn Sie VEC-basierte Erlebnisse lieber manuell rendern möchten. |
| `imsOrgId` | Legen Sie die `orgId` mit dem `configure` command |
| `optinEnabled` und `optoutEnabled` | Siehe Platform Web SDK . [Datenschutzoptionen](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html). Die `defaultConsent` -Option gilt für alle vom Platform Web SDK unterstützten Adobe-Lösungen. |
| `overrideMboxEdgeServer` und `overrideMboxEdgeServerTimeout` | Nicht zutreffend. Alle Platform Web SDK-Anforderungen verwenden das Adobe Experience Platform Edge-Netzwerk. |
| `pageLoadEnabled` | Legen Sie die `renderDecisions` -Option `true` mit dem `sendEvent` command |
| `secureOnly` | Nicht unterstützt. Das Platform Web SDK setzt alle Cookies mit dem `secure` und `sameSite="none"` -Attribute. |
| `selectorsPollingTimeout` | Nicht unterstützt. Das Platform Web SDK verwendet einen Wert von 5 Sekunden. Benutzerdefinierter Code kann bei Bedarf zum manuellen Rendern von Inhalten verwendet werden. |
| `serverDomain` | Verwenden Sie die `edgeDomain` mit der Einstellung `configure` command |
| `telemetryEnabled` | Nicht zutreffend |
| `timeout` | Nicht unterstützt. Es wird empfohlen, sicherzustellen, dass jeder Flackern-Minderungscode eine geeignete Zeitüberschreitung enthält. |
| `viewsEnabled` | Nicht unterstützt. Inhalte für Target-Ansichten werden immer beim ersten abgerufen `sendEvent()` Aufruf if `renderDecisions` auf `true` oder `__view__` DecisionScope ist im Antrag enthalten. |
| `visitorApiTimeout` | Nicht zutreffend |


## Vergleich von Systemdiagrammen

Die folgenden Diagramme sollen Ihnen dabei helfen, die Unterschiede zwischen einem Datenfluss zwischen einer Target-Implementierung mit at.js und einer Implementierung mit dem Platform Web SDK zu verstehen.

### at.js 2.x-Systemdiagramm

![at.js 2.0-Verhalten beim Laden der Seite](assets/target-at-js-2x-diagram.png)

| Aufruf | Details |
| --- | --- |
| 1 | Ein Aufruf gibt die Experience Cloud-ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird bei einem weiteren Aufruf die Kunden-ID synchronisiert. |
| 2 | Die at.js-Bibliothek wird synchron geladen und blendet den Dokumenttext aus (at.js kann auch asynchron mit einem optionalen Pre-hiding-Snippet geladen werden, das auf der Seite implementiert ist). |
| 3 | Die Seitenladeanforderung umfasst alle konfigurierten Parameter, ECID, SDID und Kunden-ID. |
| 4 | Profilskripte werden ausgeführt und in den Profilspeicher eingespeist. Der Store ruft geeignete Zielgruppen aus der Zielgruppenbibliothek ab (z. B. über Analytics, Audience Manager usw. freigegebene Zielgruppen). Kundenattribute werden in einem Batch-Prozess an den Profilspeicher gesendet. |
| 5 | Basierend auf URL, Anforderungsparametern und Profildaten entscheidet Target, welche Aktivitäten und Erlebnisse für die aktuelle Seite und zukünftige Ansichten an den Besucher zurückgegeben werden sollen. |
| 6 | Zielgerichteter Inhalt, der zurück an die Seite gesendet wird, optional einschließlich Profilwerten für eine zusätzliche Personalisierung.<br><br>Die zielgerichteten Inhalte auf der aktuellen Seite werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern.<br><br>Zielgerichtete Inhalte für zukünftige Ansichten einer Einzelseitenanwendung werden im Browser zwischengespeichert, sodass sie sofort ohne zusätzlichen Server-Aufruf angewendet werden können, wenn die Ansichten ausgelöst werden. (Siehe nächstes Diagramm für das Verhalten triggerView() ). |
| 7 | Analytics-Daten, die von der Seite an die Datenerfassungsserver gesendet werden. |
| 8 | Target-Daten werden über die SDID mit Analytics-Daten abgeglichen und im Analytics-Berichtspeicher abgelegt. Analysedaten können dann über A4T-Berichte sowohl in Analytics als auch in Target angezeigt werden. |

Weitere Informationen finden Sie im Entwicklerhandbuch . [Target mit at.js für Einzelseitenanwendungen implementieren](https://developer.adobe.com/target/implement/client-side/atjs/how-to-deployatjs/target-atjs-single-page-application/).

### Systemdiagramm für das Platform Web SDK

![Abbildung der Adobe Target-Edge-Entscheidung mit dem Platform Web SDK](assets/target-platform-web-sdk.png)

| Aufruf | Details |
| --- | --- |
| 1 | Das Gerät lädt das Platform Web SDK. Das Platform Web SDK sendet eine Anfrage mit XDM-Daten, der ID der Datastreams-Umgebung, den übergebenen Parametern und der Kunden-ID (optional) an das Edge-Netzwerk. Seite (oder Container) ist vorab ausgeblendet. |
| 2 | Das Edge-Netzwerk sendet die Anfrage an die Edge-Dienste, um sie mit der Besucher-ID, der Zustimmung und anderen Besucherkontextinformationen wie Geolocation und gerätefreundlichen Namen anzureichern. |
| 3 | Das Edge-Netzwerk sendet die angereicherte Personalisierungsanforderung mit der Besucher-ID und den übergebenen Parametern an den Target-Edge. |
| 4 | Profilskripte werden ausgeführt und dann in den Target-Profilspeicher eingespeist. Der Profilspeicher ruft Segmente aus der Zielgruppenbibliothek ab (z. B. freigegebene Segmente aus Adobe Analytics, Adobe Audience Manager und Adobe Experience Platform). |
| 5 | Basierend auf URL-Anforderungsparametern und Profildaten bestimmt Target, welche Aktivitäten und Erlebnisse für den Besucher für die aktuelle Seitenansicht und für künftige vorab abgerufene Ansichten angezeigt werden sollen. Target sendet dies dann zurück an das Edge-Netzwerk. |
| 6 | a. Das Edge-Netzwerk sendet die Personalisierungsantwort zurück an die Seite, optional einschließlich der Profilwerte für eine zusätzliche Personalisierung. Personalisierte Inhalte auf der aktuellen Seite werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern.<br><br>b. Personalisierte Inhalte für Ansichten, die als Ergebnis von Benutzeraktionen in einer Einzelseiten-App (SPA) angezeigt werden, werden für sofortiges Rendering ohne zusätzliche Server-Aufrufe zwischengespeichert.<br><br>c. Das Edge-Netzwerk sendet die Besucher-ID und andere Werte in Cookies (z. B. Zustimmung, Sitzungs-ID, Identität, Cookie-Prüfung, Personalisierung usw.). |
| 7 | Das Edge-Netzwerk leitet Analytics for Target (A4T)-Details (Aktivitäts-, Erlebnis- und Konversionsmetadaten) an den Analytics-Edge weiter. |

Weitere Informationen finden Sie im Entwicklerhandbuch . [Target mithilfe des Platform Web SDK für Einzelseitenanwendungen implementieren](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/spa-implementation.html).

Wenn Sie über ein gutes technisches Verständnis Ihrer aktuellen Target-Implementierung und der von Ihnen verwendeten Funktionen verfügen, besteht der nächste Schritt darin, die [Ersteinrichtung](initial-setup.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).
