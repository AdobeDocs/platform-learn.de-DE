---
title: Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung
description: Erfahren Sie mehr über die Unterschiede zwischen der Target-Erweiterung und der Decisioning-Erweiterung, einschließlich Funktionen, Einstellungen und Datenfluss.
exl-id: 6c854049-4126-45cf-8b2b-683cf29549f3
source-git-commit: 8e4e23413c842f84159891287d09e8a6cfbbbc53
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 5%

---

# Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung

Die Adobe Journey Optimizer - Decisioning-Erweiterung unterscheidet sich von der Adobe Target-Erweiterung für mobile Apps. Die folgenden Tabellen sind eine Referenz, die Sie bei der Bewertung von Bereichen Ihrer Implementierung unterstützen soll, auf die Sie sich während des Migrationsprozesses konzentrieren müssen.

Nachdem Sie die unten stehenden Informationen überprüft und Ihre aktuelle technische Target-Erweiterungsimplementierung bewertet haben, sollten Sie Folgendes verstehen:

- Welche Target-Funktionen werden von Adobe Journey Optimizer unterstützt - Decisioning
- Welche Adobe Target-Erweiterungsfunktionen verfügen über Adobe Journey Optimizer - Decisioning-Entsprechungen
- Anwendung von Target-Einstellungen mit Adobe Journey Optimizer - Decisioning
- Datenfluss mithilfe der Adobe Journey Optimizer - Decisioning-Erweiterung


## Funktionsvergleich

| Funktion | Target-Erweiterung | Decisioning-Erweiterung (Target über Edge) |
|---|---|---|
| Vorabruf-Modus | Unterstützt | Unterstützt |
| Ausführungsmodus | Unterstützt | Nicht unterstützt |
| Benutzerdefinierte Parameter | Unterstützt | Unterstützt* |
| Profilparameter | Unterstützt | Unterstützt* |
| Entitätsparameter | Unterstützt | Unterstützt* |
| Zielgruppen | Unterstützt | Unterstützt |
| Real-Time CDP-Zielgruppen | Nicht unterstützt | Unterstützt |
| Real-Time CDP-Attribute | Nicht unterstützt | Unterstützt |
| Lebenszyklusmetriken | Unterstützt | Unterstützt über Datenerfassungsregeln |
| thirdPartyId (mbox3rdPartyId) | Unterstützt | Unterstützt über Identity Map und Target-Drittanbieter-ID-Namespace im Datastream |
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
>Behalten Sie die Konfiguration und die Einstellungen der Target-Erweiterungs-Tags bei, selbst wenn Sie Ihren App-Code in die Decisioning-Erweiterung migriert haben. Dadurch wird sichergestellt, dass Target weiterhin für Kunden funktioniert, die die App noch nicht auf die neue Version aktualisiert haben.
>
>Wenn Sie die Analytics for Target-Integration (A4T) verwenden, migrieren Sie Ihre Analytics-Implementierung auch mit der Edge Bridge-Erweiterung, während Sie Ihre Target-Implementierung zur Decisioning-Erweiterung migrieren.

## Funktionen der Target-Erweiterung und Entsprechungen der Decisioning-Erweiterung

Viele Target-Erweiterungsfunktionen verfügen über einen gleichwertigen Ansatz unter Verwendung der in der folgenden Tabelle beschriebenen Decisioning-Erweiterung. Weitere Informationen zu den [Funktionen](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/) finden Sie im Adobe Target-Entwicklerhandbuch.

| Target-Erweiterung | Entscheidungserweiterung | Anmerkungen |
| --- | --- | --- | 
| `prefetchContent` | `updatePropositions` |  |
| `retrieveLocationContent` | `getPropositions` | Bei Verwendung der API `getPropositions` wird kein Remote-Aufruf zum Abrufen nicht zwischengespeicherter Bereiche im SDK durchgeführt. |
| `displayedLocations` | Angebot -> `displayed()` | Darüber hinaus kann die Methode `generateDisplayInteractionXdm` Angebot verwendet werden, um das XDM für die Elementanzeige zu generieren. Anschließend kann die sendEvent-API des Edge-Netzwerk-SDK verwendet werden, um zusätzliche XDM-, Freiformdaten anzuhängen und ein Erlebnisereignis an die Remote-Umgebung zu senden. |
| `clickedLocation` | Angebot -> `tapped()` | Darüber hinaus kann die Methode `generateTapInteractionXdm` Angebot verwendet werden, um das XDM für das Tippen auf Elemente zu generieren. Anschließend kann die sendEvent-API des Edge-Netzwerk-SDK verwendet werden, um zusätzliche XDM-, Freiformdaten anzuhängen und ein Erlebnisereignis an die Remote-Umgebung zu senden. |
| `clearPrefetchCache` | `clearCachedPropositions` |  |
| `resetExperience` | n. z. | Verwenden Sie die `removeIdentity` -API von Identity for Edge Network Extension für das SDK, um das Senden der Besucher-ID an das Edge-Netzwerk zu beenden. Weitere Informationen finden Sie in der Dokumentation zur removeIdentity-API ](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). [ <br><br>Hinweis: Die `resetIdentities` -API von Mobile Core löscht alle im SDK gespeicherten Identitäten, einschließlich der Experience Cloud ID (ECID), und sollte sparsam verwendet werden! |
| `getSessionId` | n. z. | `state:store` Antwort-Handle enthält sitzungsbezogene Informationen. Die Edge-Netzwerkerweiterung hilft bei der Verwaltung, indem nicht abgelaufene Statusspeicherelemente an nachfolgende Anforderungen angehängt werden. |
| `setSessionId` | n. z. | `state:store` Antwort-Handle enthält sitzungsbezogene Informationen. Die Edge-Netzwerkerweiterung hilft bei der Verwaltung, indem nicht abgelaufene Statusspeicherelemente an nachfolgende Anforderungen angehängt werden. |
| `getThirdPartyId` | n. z. | Verwenden Sie die updateIdentities-API von Identity für Edge Network-Erweiterung, um den Wert der Drittanbieter-ID anzugeben. Konfigurieren Sie dann den Namespace der Drittanbieter-ID im Datastream. Weitere Informationen finden Sie in der Dokumentation zur Target-Drittanbieter-ID für Mobilgeräte](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id).[ |
| `setThirdPartyId` | n. z. | Verwenden Sie die updateIdentities-API von Identity für Edge Network-Erweiterung, um den Wert der Drittanbieter-ID anzugeben. Konfigurieren Sie dann den Namespace der Drittanbieter-ID im Datastream. Weitere Informationen finden Sie in der Dokumentation zur Target-Drittanbieter-ID für Mobilgeräte](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id).[ |
| `getTntId` | n. z. | `locationHint:result` Antwort-Handle enthält die Target-Standorthinweisinformationen. Es wird davon ausgegangen, dass Target Edge gemeinsam mit Experience Edge verwendet wird. <br> <br>Die Edge-Netzwerkerweiterung verwendet den EdgeNetwork-Standorthinweis, um den Edge-Netzwerkcluster zu bestimmen, an den Anforderungen gesendet werden sollen. Verwenden Sie die APIs `getLocationHint` und `setLocationHint` der Edge Network-Erweiterung, um Edge-Netzwerkstandorthinweise für SDKs (Hybridanwendungen) freizugeben. Weitere Informationen finden Sie in der [API-Dokumentation für `getLocationHint`](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |
| `setTntId` | n. z. | `locationHint:result` Antwort-Handle enthält die Target-Standorthinweisinformationen. Es wird davon ausgegangen, dass Target Edge gemeinsam mit Experience Edge verwendet wird. <br> <br>Die Edge-Netzwerkerweiterung verwendet den EdgeNetwork-Standorthinweis, um den Edge-Netzwerkcluster zu bestimmen, an den Anforderungen gesendet werden sollen. Verwenden Sie die APIs `getLocationHint` und `setLocationHint` der Edge Network-Erweiterung, um Edge-Netzwerkstandorthinweise für SDKs (Hybridanwendungen) freizugeben. Weitere Informationen finden Sie in der [API-Dokumentation für `getLocationHint`](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |

## Target-Erweiterungseinstellungen und Entsprechungen von Decisioning-Erweiterungen

Die Target-Erweiterung verfügt über [konfigurierbare Einstellungen](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) , die [im Datastream](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#adobe-experience-platform-data-collection-setup) mit der Decisioning-Erweiterung konfiguriert sind.

| Target-Erweiterung | Entscheidungserweiterung | Anmerkungen |
| --- | --- | --- | 
| Clientcode | n. z. | Wird automatisch von der Kante mithilfe der IMS-Org-Details eingestellt |
| Umgebungs-ID | Target-Umgebungs-ID | Im Datastream konfiguriert |
| Target Workspace-Eigenschaft | Eigenschafts-Token | Im Datastream konfiguriert |
| Maximale Wartezeit | Nicht konfigurierbar | Der Timeout mit der Decisioning-Erweiterung beträgt 10 Sekunden. |
| Serverdomäne | Edge Network Domain | Wird in der Adobe Experience Platform Edge Network-Erweiterung festgelegt |

>[!IMPORTANT]
>
> Behalten Sie die Target-Erweiterungseinstellungen bei, selbst wenn Sie Ihren App-Code in die Decisioning-Erweiterung migriert haben. Dadurch wird sichergestellt, dass Target für Benutzer, die ihre App noch nicht aktualisiert haben, weiterhin funktioniert.

## Decisioning Extension-Systemdiagramm

Das folgende Diagramm soll Ihnen beim Verständnis des Datenflusses mithilfe der Adobe Journey Optimizer - Decisioning-Erweiterung helfen.

![Adobe Target Edge Decisioning mit clientseitigem Mobile SDK](assets/diagram.png)


>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Decisioning-Erweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
