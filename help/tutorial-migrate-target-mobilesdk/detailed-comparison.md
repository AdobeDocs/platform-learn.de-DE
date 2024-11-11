---
title: Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung
description: Erfahren Sie mehr über die Unterschiede zwischen der Target-Erweiterung und der Decisioning-Erweiterung, einschließlich Funktionen, Einstellungen und Datenfluss.
exl-id: 6c854049-4126-45cf-8b2b-683cf29549f3
source-git-commit: 05b0146256c6f8644e42f851498a0f49ff44bf68
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 4%

---

# Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung

Die Adobe Journey Optimizer - Decisioning-Erweiterung unterscheidet sich von der Adobe Target-Erweiterung für mobile Apps. Die folgenden Tabellen sind eine Referenz, die Sie bei der Bewertung von Bereichen Ihrer Implementierung unterstützen soll, auf die Sie sich während des Migrationsprozesses konzentrieren müssen.

Nachdem Sie die unten stehenden Informationen überprüft und Ihre aktuelle technische Target-Erweiterungsimplementierung bewertet haben, sollten Sie Folgendes verstehen:

- Welche Target-Funktionen werden von Adobe Journey Optimizer unterstützt - Decisioning
- Welche Adobe Target-Erweiterungsfunktionen verfügen über Adobe Journey Optimizer - Decisioning-Entsprechungen
- Anwendung von Target-Einstellungen mit Adobe Journey Optimizer - Decisioning
- Unterschiede zwischen dem Datenfluss der Adobe Target-Erweiterung und der Adobe Journey Optimizer - Decisioning-Erweiterung

Wenn Sie mit dem Platform Web SDK noch nicht vertraut sind, machen Sie sich keine Gedanken - die unten stehenden Elemente werden in diesem Tutorial ausführlicher behandelt.

## Funktionsvergleich

| Funktion | Target-Erweiterung | Decisioning-Erweiterung (Target über Edge) |
|---|---|---|
| Vorabruf-Modus | Unterstützt | Unterstützt |
| Ausführungsmodus | Unterstützt | Nicht unterstützt |
| Benutzerdefinierte Parameter | Unterstützt | Unterstützt* |
| Profilparameter | Unterstützt | Unterstützt* |
| Entitätsparameter | Unterstützt | Unterstützt* |
| Zielgruppen | Unterstützt | Unterstützt |
| Real-Time CDP-Zielgruppen | ??? | Unterstützt |
| Real-Time CDP-Attribute | ??? | Unterstützt |
| Lebenszyklusmetriken | Unterstützt | Unterstützt über Datenerfassungsregeln |
| thirdPartyId (mbox3rdPartyId) | Unterstützt | Wird über Identity Map und die Namespace-Konfiguration im Datastream unterstützt |
| Benachrichtigungen (anzeigen, klicken) | Unterstützt | Unterstützt |
| Antwort-Token | Unterstützt | Unterstützt |
| Analytics for Target (A4T) | Nur Client-seitig | Client- und Server-seitig |
| Mobile Vorschau (QA-Modus) | Unterstützt | Eingeschränkte Unterstützung für Assurance |

>[!IMPORTANT]
>
> \* In einer Anfrage gesendete Parameter gelten für alle Bereiche in der Anfrage. Wenn Sie verschiedene Parameter für verschiedene Bereiche festlegen müssen, müssen Sie zusätzliche Anforderungen stellen.



## Wichtige Hinweise

>[!NOTE]
>
>Die Migration von Target zum Platform Web SDK unter Beibehaltung einer bestehenden AppMeasurement Adobe Analytics-Implementierung für eine bestimmte Seite wird nicht unterstützt.
>
> Es ist möglich, Ihre at.js- (und AppMeasurement.js-) Implementierung auf Platform Web SDK einzeln zu migrieren. Wenn Sie diesen Ansatz wählen, ist es am besten, die Optionen [`idMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) und [`targetMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) mit dem Befehl `configure` auf `true` festzulegen.

## Funktionen der Target-Erweiterung und Entsprechungen der Decisioning-Erweiterung

Viele Target-Erweiterungsfunktionen verfügen über einen gleichwertigen Ansatz unter Verwendung der in der folgenden Tabelle beschriebenen Decisioning-Erweiterung. Weitere Informationen zu den [Funktionen](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/) finden Sie im Adobe Target-Entwicklerhandbuch.

| Target-Erweiterung | Entscheidungserweiterung | Anmerkungen |
| --- | --- | --- | 
| `prefetchContent` | `updatePropositions` |  |
| `retrieveLocationContent` | `getPropositions` | Bei Verwendung der API `getPropositions` wird kein Remote-Aufruf zum Abrufen nicht zwischengespeicherter Bereiche im SDK durchgeführt. |
| `displayedLocations` | Angebot -> `displayed()` | Darüber hinaus kann die Methode `generateDisplayInteractionXdm` Angebot verwendet werden, um das XDM für die Elementanzeige zu generieren. Anschließend kann die sendEvent-API des Edge-Netzwerk-SDK verwendet werden, um zusätzliche XDM-, Freiformdaten anzuhängen und ein Erlebnisereignis an die Remote-Umgebung zu senden. |
| `clickedLocation` | Angebot -> `tapped()` | Darüber hinaus kann die Methode `generateTapInteractionXdm` Angebot verwendet werden, um das XDM für das Tippen auf Elemente zu generieren. Anschließend kann die sendEvent-API des Edge-Netzwerk-SDK verwendet werden, um zusätzliche XDM-, Freiformdaten anzuhängen und ein Erlebnisereignis an die Remote-Umgebung zu senden. |
| `clearPrefetchCache` | `clearCachedPropositions` |  |
| `resetExperience` |  | Verwenden Sie die `removeIdentity` -API von Identity for Edge Network Extension für das SDK, um das Senden der Besucher-ID an das Edge-Netzwerk zu beenden. Weitere Informationen finden Sie in der Dokumentation zur removeIdentity-API ](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). [ <br><br>Hinweis: Die `resetIdentities` -API von Mobile Core löscht alle im SDK gespeicherten Identitäten, einschließlich der Experience Cloud ID (ECID), und sollte sparsam verwendet werden! |
| `getSessionId` |  | `state:store` Antwort-Handle enthält sitzungsbezogene Informationen. Die Edge-Netzwerkerweiterung hilft bei der Verwaltung, indem nicht abgelaufene Statusspeicherelemente an nachfolgende Anforderungen angehängt werden. |
| `setSessionId` |  | `state:store` Antwort-Handle enthält sitzungsbezogene Informationen. Die Edge-Netzwerkerweiterung hilft bei der Verwaltung, indem nicht abgelaufene Statusspeicherelemente an nachfolgende Anforderungen angehängt werden. |
| `getThirdPartyId` | n. z. | Verwenden Sie die updateIdentities-API von Identity für Edge Network-Erweiterung, um den Wert der Drittanbieter-ID anzugeben. Konfigurieren Sie dann den Namespace der Drittanbieter-ID im Datastream. Weitere Informationen finden Sie in der Dokumentation zur Target-Drittanbieter-ID für Mobilgeräte](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id).[ |
| `setThirdPartyId` | n. z. | Verwenden Sie die updateIdentities-API von Identity für Edge Network-Erweiterung, um den Wert der Drittanbieter-ID anzugeben. Konfigurieren Sie dann den Namespace der Drittanbieter-ID im Datastream. Weitere Informationen finden Sie in der Dokumentation zur Target-Drittanbieter-ID für Mobilgeräte](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id).[ |
| `getTntId` |  | `locationHint:result` Antwort-Handle enthält die Target-Standorthinweisinformationen. Es wird davon ausgegangen, dass Target Edge gemeinsam mit Experience Edge verwendet wird. <br> <br>Die Edge-Netzwerkerweiterung verwendet den EdgeNetwork-Standorthinweis, um den Edge-Netzwerkcluster zu bestimmen, an den Anforderungen gesendet werden sollen. Verwenden Sie die APIs `getLocationHint` und `setLocationHint` der Edge Network-Erweiterung, um Edge-Netzwerkstandorthinweise für SDKs (Hybridanwendungen) freizugeben. Weitere Informationen finden Sie in der [API-Dokumentation für `getLocationHint`](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |
| `setTntId` |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

## Target-Erweiterungseinstellungen und Entsprechungen von Decisioning-Erweiterungen

Die Target-Erweiterung kann mit verschiedenen Einstellungen in der ...

| Target-Erweiterung | Entscheidungserweiterung |
| --- | --- | 
| |  |


## Vergleich von Systemdiagrammen

Die folgenden Diagramme sollen Ihnen dabei helfen, die Datenflussunterschiede zwischen einer Target-Implementierung mit der Adobe Journey Optimizer - Decisioning-Erweiterung und einer Implementierung mit der Adobe Target-Erweiterung zu verstehen.

### Systemdiagramm der Target-Erweiterung



### Decisioning Extension-Systemdiagramm




>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Decisioning-Erweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
