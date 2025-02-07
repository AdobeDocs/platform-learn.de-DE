---
title: Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung
description: Erfahren Sie mehr über die Unterschiede zwischen der Target-Erweiterung und der Decisioning-Erweiterung, einschließlich Funktionen, Einstellungen und Datenfluss.
exl-id: 6c854049-4126-45cf-8b2b-683cf29549f3
source-git-commit: cb08ad8a1ffd687d7748ca02643b11b2243cd1a7
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 4%

---

# Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung

Die Adobe Journey Optimizer - Decisioning-Erweiterung unterscheidet sich von der Adobe Target-Erweiterung für Mobile Apps. Die folgenden Tabellen dienen als Referenz bei der Bewertung von Bereichen Ihrer Implementierung, auf die Sie sich während des Migrationsprozesses möglicherweise konzentrieren müssen.

Nachdem Sie die folgenden Informationen durchgelesen und Ihre aktuelle Implementierung der technischen Target-Erweiterung bewertet haben, sollten Sie Folgendes verstehen:

- Welche Target-Funktionen von Adobe Journey Optimizer unterstützt werden - Decisioning
- Welche Adobe Target-Erweiterungsfunktionen über Adobe Journey Optimizer verfügen - Entscheidungsäquivalente
- Anwenden von Target-Einstellungen mit Adobe Journey Optimizer - Decisioning
- Fluss der Daten mithilfe der Adobe Journey Optimizer - Decisioning-Erweiterung

## Operative Unterschiede

| | Target-Erweiterung | Decisioning-Erweiterung |
|---|---|---|
| Prozess | Änderungen an einer Target-Implementierung können auf einen Prozess folgen, der im Vergleich zu anderen Programmen wie Analytics eine andere Kadenz oder andere QS-Anforderungen hat. | Bei Änderungen an einer Implementierung der Decisioning-Erweiterung sollten alle nachgelagerten Anwendungen berücksichtigt und der QA- und Veröffentlichungsprozess entsprechend angepasst werden. |
| Zusammenarbeit | Target-spezifische Daten können direkt in den Target-Aufrufen übergeben werden. Wenn die Target-Berichtsquelle Adobe Analytics (A4T) ist, können Target-spezifische Daten auch an Adobe Analytics übergeben werden, wenn geeignete Tracking-Methoden in der Target-Erweiterung für die Anzeige von Target-Inhalten und die Interaktion aufgerufen werden. | Daten, die in den Decisioning-Erweiterungsaufrufen übergeben werden, können sowohl an Target als auch an Analytics weitergeleitet werden, wenn die Target-Berichtsquelle Adobe Analytics (A4T) ist, Adobe Analytics im Daten-Stream aktiviert ist und geeignete Tracking-Methoden in der Decisioning-Erweiterung aufgerufen werden, wenn Target-Inhalte angezeigt werden und mit ihnen interagiert wird. |

## Grundlegende Unterschiede

| | Target-Erweiterung | Decisioning-Erweiterung |
|---|---|---|
| Abhängigkeiten | Hängt nur von Mobile Core SDK ab | Hängt von Mobile Core und Edge Network SDK ab |
| Bibliotheksfunktion | Unterstützt nur das Abrufen von Inhalten aus Adobe Target | Unterstützung für das Abrufen von Inhalten von Adobe Target und Offer decisioning |
| Anfragen | Target-Aufrufe sind weitgehend unabhängig von anderen Netzwerkaufrufen | Target-Netzwerkaufrufe werden zusammen mit Netzwerkaufrufen für andere Edge-basierte Lösungen wie Messaging in Edge SDK in die Warteschlange gestellt und seriell ausgeführt. |
| Edge Network | Verwendet den Target-Serverwert oder das Adobe Experience Cloud-Edge Network mit dem Clientcode (clientcode.tt.omtrdc.net), die beide in der [Target-Konfiguration](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) in der Datenerfassungs-UI angegeben sind | Verwendet die Edge-Netzwerkdomäne, die in der Adobe Experience Platform-[Edge Network-Konfiguration ](https://developer.adobe.com/client-sdks/edge/edge-network/#configure-the-edge-network-extension-in-data-collection-ui) der Datenerfassungs-Benutzeroberfläche angegeben ist. |
| Allgemeine Terminologie | mbox, targetParameters | Entscheidungsumfang, Zuordnung (Android)/Wörterbuch (iOS) für Zielparameter |
| Standardinhalt | Ermöglicht die Übergabe Client-seitiger Standardinhalte in TargetRequest, die zurückgegeben wird, wenn der Netzwerkaufruf fehlschlägt oder zu einem Fehler führt. | Ermöglicht nicht die Übergabe Client-seitiger Standardinhalte. Gibt keinen Inhalt zurück, wenn der Netzwerkaufruf fehlschlägt oder zu einem Fehler führt. |
| Zielparameter | Ermöglicht die Übergabe globaler TargetParameters pro Anfrage und verschiedener TargetParameters pro Mbox | Ermöglicht die Übergabe globaler TargetParameters nur pro Anfrage |



## Funktionsvergleich

| Funktion | Target-Erweiterung | Decisioning-Erweiterung (Target über Edge) |
|---|---|---|
| Vorheriger Abrufmodus | Unterstützt | Unterstützt |
| Ausführungsmodus | Unterstützt | Nicht unterstützt |
| Benutzerdefinierte Parameter | Unterstützt | Unterstützt* |
| Profilparameter | Unterstützt | Unterstützt* |
| Entitätsparameter | Unterstützt | Unterstützt* |
| Zielgruppen | Unterstützt | Unterstützt |
| Real-Time CDP-Zielgruppen | Nicht unterstützt | Unterstützt |
| Real-Time CDP-Attribute | Nicht unterstützt | Unterstützt |
| Lebenszyklusmetriken | Unterstützt | Unterstützt durch Datenerfassungsregeln |
| thirdPartyId (mbox3rdPartyId) | Unterstützt | Unterstützt über Identity Map und Target Third-Party-ID-Namespace im Datenstrom |
| Benachrichtigungen (Anzeige, Klick) | Unterstützt | Unterstützt |
| Antwort-Token | Unterstützt | Unterstützt |
| Analytics for Target (A4T) | Nur Client-seitig | Client- und Server-seitig |
| Mobile-Vorschau (QA-Modus) | Unterstützt | Eingeschränkter Support mit Assurance |

>[!IMPORTANT]
>
> \* Die in einer Anfrage gesendeten Parameter gelten für alle Bereiche in der Anfrage. Wenn Sie für verschiedene Bereiche unterschiedliche Parameter festlegen müssen, müssen Sie zusätzliche Anfragen stellen.



## Bemerkenswerte Hinweise

>[!NOTE]
>
>Behalten Sie die Konfiguration und die Einstellungen für Target-Erweiterungs-Tags bei, auch nachdem Sie Ihren App-Code zur Decisioning-Erweiterung migriert haben. Dadurch wird sichergestellt, dass Target auch für Kunden funktioniert, die die App noch nicht auf die neue Version aktualisiert haben.
>
>Wenn Sie die Analytics for Target-Integration (A4T) verwenden, müssen Sie auch Ihre Analytics-Implementierung mit der Edge Bridge-Erweiterung migrieren, während Sie gleichzeitig Ihre Target-Implementierung in die Decisioning-Erweiterung migrieren.

## Funktionen der Erweiterung „Target“ und Entsprechungen der Entscheidungserweiterung

Viele Target-Erweiterungsfunktionen verwenden einen gleichwertigen Ansatz unter Verwendung der in der folgenden Tabelle beschriebenen Decisioning-Erweiterung. Weitere Informationen zu [Funktionen](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/) finden Sie im Adobe Target-Entwicklerhandbuch.

| Target-Erweiterung | Decisioning-Erweiterung | Anmerkungen |
| --- | --- | --- | 
| `prefetchContent` | `updatePropositions` |  |
| `retrieveLocationContent` | `getPropositions` | Bei Verwendung `getPropositions` -API wird kein Remote-Aufruf durchgeführt, um nicht zwischengespeicherte Bereiche in der SDK abzurufen. |
| `displayedLocations` | Angebot -> `displayed()` | Darüber hinaus kann `generateDisplayInteractionXdm` Angebotsmethode verwendet werden, um das XDM für die Elementanzeige zu generieren. Anschließend kann die sendEvent-API des Edge-Netzwerk-SDK verwendet werden, um zusätzliche XDM- und Freiformdaten anzuhängen und ein Erlebnisereignis an die Remote-Instanz zu senden. |
| `clickedLocation` | Angebot -> `tapped()` | Darüber hinaus kann `generateTapInteractionXdm` Angebotsmethode verwendet werden, um das XDM-Element für das Tippen zu generieren. Anschließend kann die sendEvent-API des Edge-Netzwerk-SDK verwendet werden, um zusätzliche XDM- und Freiformdaten anzuhängen und ein Erlebnisereignis an die Remote-Instanz zu senden. |
| `clearPrefetchCache` | `clearCachedPropositions` |  |
| `resetExperience` | n. z. | Verwenden Sie `removeIdentity` API der Identity for Edge Network-Erweiterung für SDK, um das Senden der Besucherkennung an das Edge-Netzwerk zu stoppen. Weitere Informationen finden Sie unter [Dokumentation zur removeIdentity-API](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). <br><br>Hinweis: Die `resetIdentities`-API von Mobile Core löscht alle in der SDK gespeicherten Identitäten, einschließlich der Experience Cloud-ID (ECID), und sollte sparsam verwendet werden! |
| `getSessionId` | n. z. | `state:store` Antwort-Handle enthält sitzungsbezogene Informationen. Die Edge-Netzwerkerweiterung erleichtert die Verwaltung, indem sie nicht abgelaufene Statusspeicherelemente an nachfolgende Anfragen anhängt. |
| `setSessionId` | n. z. | `state:store` Antwort-Handle enthält sitzungsbezogene Informationen. Die Edge-Netzwerkerweiterung erleichtert die Verwaltung, indem sie nicht abgelaufene Statusspeicherelemente an nachfolgende Anfragen anhängt. |
| `getThirdPartyId` | n. z. | Verwenden Sie die updateIdentities-API der Identity for Edge Network-Erweiterung, um den Wert der Drittanbieter-ID anzugeben. Konfigurieren Sie dann den Namespace der Drittanbieter-ID im Datenstrom. Weitere Informationen finden Sie unter [Target Third-Party-ID für Mobilgeräte](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| `setThirdPartyId` | n. z. | Verwenden Sie die updateIdentities-API der Identity for Edge Network-Erweiterung, um den Wert der Drittanbieter-ID anzugeben. Konfigurieren Sie dann den Namespace der Drittanbieter-ID im Datenstrom. Weitere Informationen finden Sie unter [Target Third-Party-ID für Mobilgeräte](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| `getTntId` | n. z. | `locationHint:result` Antwort-Handle enthält die Informationen zum Ziel-Standorthinweis. Es wird davon ausgegangen, dass Target Edge mit Experience Edge zusammengelegt wird. <br> <br>Die Edge-Netzwerkerweiterung verwendet den EdgeNetwork-Standorthinweis, um den Edge-Netzwerkcluster zu ermitteln, an den Anforderungen gesendet werden sollen. Verwenden Sie zum Freigeben von Edge-Standorthinweisen über SDKs (Hybrid-Apps) `getLocationHint` und `setLocationHint` Sie APIs über die Edge Network-Erweiterung. Weitere Informationen finden Sie unter [die `getLocationHint` API-Dokumentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |
| `setTntId` | n. z. | `locationHint:result` Antwort-Handle enthält die Informationen zum Ziel-Standorthinweis. Es wird davon ausgegangen, dass Target Edge mit Experience Edge zusammengelegt wird. <br> <br>Die Edge-Netzwerkerweiterung verwendet den EdgeNetwork-Standorthinweis, um den Edge-Netzwerkcluster zu ermitteln, an den Anforderungen gesendet werden sollen. Verwenden Sie zum Freigeben von Edge-Standorthinweisen über SDKs (Hybrid-Apps) `getLocationHint` und `setLocationHint` Sie APIs über die Edge Network-Erweiterung. Weitere Informationen finden Sie unter [die `getLocationHint` API-Dokumentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |

## Einstellungen der Target-Erweiterung und Entsprechungen der Decisioning-Erweiterung

Die Target-Erweiterung verfügt über [konfigurierbare Einstellungen](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) die [im Datenstrom konfiguriert) ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#adobe-experience-platform-data-collection-setup) der Decisioning-Erweiterung konfiguriert werden.

| Target-Erweiterung | Decisioning-Erweiterung | Anmerkungen |
| --- | --- | --- | 
| Clientcode | n. z. | Wird automatisch vom Edge mithilfe der IMS-Organisationsdetails festgelegt |
| Umgebungs-ID | Zielumgebungs-ID | Im Datenstrom konfiguriert |
| Workspace-Zieleigenschaft | Eigenschafts-Token | Im Datenstrom konfiguriert |
| Maximale Wartezeit | Nicht konfigurierbar | Die maximale Wartezeit mit der Decisioning-Erweiterung beträgt 10 Sekunden |
| Serverdomäne | Edge Network-Domain | In der Adobe Experience Platform-Edge Network-Erweiterung festgelegt |

>[!IMPORTANT]
>
> Behalten Sie die Einstellungen der Target-Erweiterung bei, auch nachdem Sie Ihren App-Code zur Decisioning-Erweiterung migriert haben. Dadurch wird sichergestellt, dass Target auch weiterhin für Benutzende funktioniert, die ihre App noch nicht aktualisiert haben.

## Systemdiagramm der Decisioning-Erweiterung

Das folgende Diagramm soll Ihnen dabei helfen, den Datenfluss mithilfe der Adobe Journey Optimizer - Decisioning-Erweiterung zu verstehen.

![Adobe Target Edge Decisioning mit Client-seitigem Mobile SDK](assets/diagram.png)


>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
