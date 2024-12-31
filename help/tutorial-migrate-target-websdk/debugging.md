---
title: Debugging - Migrieren von Target von at.js 2.x zu Web SDK
description: Erfahren Sie, wie Sie mit der Adobe Experience Platform Web SDK eine Adobe Target-Implementierung debuggen. Zu den behandelten Themen gehören Debugging-Optionen, Browser-Erweiterungen und Unterschiede zwischen at.js und Platform Web SDK.
exl-id: 20699551-a708-469a-8980-67586db82787
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 3%

---

# Target mit Platform Web SDK debuggen

Überprüfen von Target-Aktivitäten und Debuggen von Web SDK zur Fehlerbehebung bei Problemen mit der Implementierung, der Bereitstellung von Inhalten oder der Zielgruppen-Qualifizierung. Auf dieser Seite des Migrationshandbuchs werden die Unterschiede zwischen dem Debugging mit at.js und Platform Web SDK erläutert.

In der folgenden Tabelle sind die Funktionen und die Unterstützung für Tests und Debugging-Ansätze zusammengefasst.

| Funktion oder Tool | at.js-Unterstützung | Platform Web SDK-Unterstützung |
| --- | --- | --- |
| Aktivitäts-QA-URLs | Ja | Ja |
| `mboxDisable` URL-Parameter | Ja | Informationen zum Deaktivieren der Target[Funktion finden Sie ](#disable-target-functionality) |
| `mboxDebug` URL-Parameter | Ja | Verwenden Sie `alloy_debug` Parameter für ähnliche Debugging-Informationen |
| `mboxTrace` URL-Parameter | Ja | Verwenden der Browser-Erweiterung &quot;Experience Platform Debugger“ |
| Adobe Experience Platform Debugger-Erweiterung | Ja | Ja |
| `alloy_debug` URL-Parameter | Nicht zutreffend | Ja |
| Adobe Experience Platform Assurance | Nicht zutreffend | Ja |

## Adobe Experience Platform Debugger-Browser-Erweiterung

Die Adobe Experience Platform Debugger-Erweiterung für Chrome und Firefox untersucht Ihre Web-Seiten und hilft Ihnen bei der Überprüfung Ihrer Adobe Experience Cloud-Implementierungen.

Sie können Platform Debugger auf jeder Web-Seite ausführen. Die Erweiterung hat Zugriff auf öffentliche Daten. Um über die Erweiterung auf nicht öffentliche Daten wie Target-Trace-Informationen zuzugreifen, müssen Sie sich über den Link **[!UICONTROL Anmelden]** beim Experience Cloud authentifizieren.

### Abrufen und Installieren des Adobe Experience Platform Debuggers

Der Adobe Experience Platform Debugger kann in den Browsern Google Chrome oder Mozilla Firefox installiert werden. Folgen Sie dem entsprechenden Link unten, um die Erweiterung in Ihrem bevorzugten Browser zu installieren:

- [Chrome](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)
- [Firefox](https://addons.mozilla.org/de/firefox/addon/adobe-experience-platform-dbg/)

Nach der Installation der Chrome-Erweiterung oder des Firefox-Add-ons wird ein Symbol (![](assets/start-icon.jpg)) zur Erweiterungsleiste hinzugefügt. Wählen Sie dieses Symbol aus, um die Erweiterung zu öffnen.

Weitere Informationen zur Erweiterung [Adobe Experience Platform Debugger und zum Debugging ](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) Adobe-Web-Anwendungen finden Sie im entsprechenden Handbuch.

## Vorschau von Target-Aktivitäten mit QA-URLs

Sowohl at.js als auch Platform Web SDK ermöglichen die Vorschau von Target-Aktivitäten mithilfe von Target-QA-URLs. Beide Implementierungsmethoden unterstützen dieselben QA-Funktionen.

Target-QA-URLs, die funktionieren, indem at.js oder Platform Web SDK angewiesen werden, ein bestimmtes Cookie in Ihren Browser namens &quot;`at_qa_mode`&quot; zu schreiben. Dieses Cookie wird verwendet, um die Qualifizierung für eine bestimmte Aktivität und ein bestimmtes Erlebnis zu erzwingen.

>[!CAUTION]
>
>Die Funktionalität des Target-QA-Modus wird von Platform Web SDK ab Version 2.13.0 unterstützt. Der QA-Modus von Target wird basierend auf dem im `sendEvent`-Aufruf übergebenen `xdm.web.webPageDetails.URL` aktiviert. Änderungen an diesem Wert, wie die Kleinschreibung aller Zeichen, können dazu führen, dass der Target-QA-Modus nicht ordnungsgemäß funktioniert.

Weitere Informationen zu Target-Aktivitäts-QA finden [ im entsprechenden Handbuch ](https://experienceleague.adobe.com/docs/target/using/activities/activity-qa/activity-qa.html).

## Target-Implementierung debuggen

In der folgenden Tabelle sind die Unterschiede zwischen der Debugging-Taktik von at.js und Platform Web SDK aufgeführt:

| at.js-Funktion | Platform Web SDK-Entsprechung |
| --- | --- |
| **Mbox deaktivieren** - Deaktivieren von Target beim Abrufen und Rendern, um zu überprüfen, ob die Seite ohne Target-Interaktionen fehlerhaft ist<br><br>Seite mit URL-Parameter laden: `mboxDisable=true` | Keine direkte Entsprechung. Sie können mit den Entwickler-Tools Ihres Browsers alle Anfragen von Platform Web SDK blockieren. |
| **Mbox Debug** - Protokolliert jede at.js-Aktion in der Browser-Konsole, um Rendering-Probleme zu beheben <br><br> Seite mit URL-Parameter laden: `mboxDebug=true` | **Alloy Debug** protokolliert detaillierte Aktionen der SDK, einschließlich, aber nicht beschränkt auf Target-Personalisierungsaktionen.<br><br>Seite mit URL-Parameter laden: `alloy_debug=true` <br /><br />Oder `alloy("setDebug", { "enabled": true });` in Ihrer Entwicklerkonsole ausführen |
| **Target Trace** - Mit einem in der Target-Benutzeroberfläche generierten Mbox-Trace-Token ist unter `window.___target_trace` Objekt ein Trace-Objekt mit Details verfügbar, die am Entscheidungsprozess beteiligt waren.<br><br>Seite mit URL-Parameter laden: `mboxTrace=window&authorization={TOKEN}` | Verwenden Sie die Adobe Experience Platform Debugger-Erweiterung oder Platform Assurance. |

>[!NOTE]
>
>Alle oben aufgeführten at.js-Debugging-Funktionen sind mit erweiterten Funktionen im Adobe Experience Platform Debugger verfügbar.

### Target-Funktion deaktivieren

Die Platform Web SDK verfügt derzeit über keine Funktion zur selektiven Unterdrückung von Target-Antworten. Es ist jedoch möglich, die Platform Web SDK-Anfragen mit den Entwickler-Tools Ihres Browsers, verschiedenen Browser-Erweiterungen oder Anwendungen von Drittanbietern zu unterdrücken. So blockieren Sie beispielsweise Platform Web SDK mit Google Chrome:

1. Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle auf der Seite und wählen Sie **Inspect**
1. Wählen Sie die Registerkarte **Netzwerk** aus
1. Filtern Sie nach dem `//ee//`, um nur Platform Web SDK-Aufrufe anzuzeigen
1. Seite neu laden
1. Klicken Sie mit der rechten Maustaste auf eine der gefilterten Netzwerkanfragen und wählen Sie **Domain für Blockieranfragen**
1. Laden Sie die Seite neu. Die Netzwerkanfrage ist blockiert.
1. Wenn Sie mit dem Debugging fertig sind, klicken Sie mit der rechten Maustaste auf die blockierte Netzwerkanfrage und wählen Sie **Blockierung aufheben** oder schließen Sie den Bereich für Entwickler-Tools

### Debug-Protokollierung anzeigen

Die Debug-Protokollierung für at.js mithilfe des `mboxDebug=true`-URL-Parameters zeigt detaillierte Informationen zu jeder Target-Anfrage, -Antwort und dem Versuch an, den Inhalt auf der Seite zu rendern. Platform Web SDK verfügt über eine ähnliche Debugging-Protokollierung mit dem `alloy_debug=true` URL-Parameter.

| Protokollierte Informationen | at.js (`mboxDebug=true`) | Platform Web SDK (`alloy_debug=true`) |
| --- | --- | --- |
| Protokollpräfix für die Filterung | `AT:` | `[alloy]` |
| Details zur Seitenladeanfrage | Ja | Ja |
| Mbox- oder Bereichsanfragedetails | Ja | Ja |
| Status der Anfrage | Ja | Ja |
| Antwortdetails | Ja | Ja |
| Rendering-Status | Erfolg und Fehler | Nur Fehler |
| Rendering-Details | Ja | Ja |

>[!NOTE]
>
>Debug-Protokolle für at.js und Platform Web SDK bieten einen ähnlichen Detaillierungsgrad, mit dem Hinweis, dass Web SDK nur über Rendering-Fehler benachrichtigt, die auf ungültige Selektoren zurückzuführen sind. Die Debug-Protokollierung bestätigt derzeit nicht, dass das Rendern erfolgreich war.

### Anzeigen von Zielspuren

Target-Traces bieten detaillierte Informationen zu Aktivitätsqualifikationen und zum Zielgruppenprofil des Besuchers. Da Target-Traces Informationen enthalten, die nicht öffentlich verfügbar sind, erfordert ihre Anzeige ein Autorisierungs-Token oder die Authentifizierung innerhalb des Adobe Experience Platform Debugger-Browser-Erweiterungsfensters.

| Methode der Zielverfolgung | at.js | Platform Web-SDK |
| --- | --- | --- |
| `mboxTrace` URL-Parameter | Ja | Nein |
| Adobe Experience Platform Debugger-Browser-Erweiterung | Ja | Ja |
| Adobe Experience Platform Assurance | Nein | Ja |


Gehen Sie wie folgt vor, um Platform Web SDK Target-Ablaufverfolgungen mit dem Adobe Experience Platform Debugger anzuzeigen:

1. Navigieren Sie zu einer Seite auf Ihrer Site, auf der Target mit Platform Web SDK implementiert wurde
1. Öffnen Sie die Browsererweiterung, indem Sie auf das Symbol (![](assets/start-icon.jpg)) in der Navigationsleiste des Adobe Experience Platform Debuggers klicken
1. Wählen Sie den Link **[!UICONTROL Anmelden]** aus
1. Authentifizierung mit Ihrer Adobe Experience Cloud-Anmeldung
1. Wählen Sie auf **[!UICONTROL linken Seite]** Protokolle“ aus
1. Wählen Sie die Registerkarte **[!UICONTROL Edge]** oben aus.
1. Geben Sie Ihrer Debugsitzung optional einen Namen und klicken Sie auf die Schaltfläche **[!UICONTROL Verbinden]**
1. Laden Sie die Seite neu. Das Protokoll sollte nun detaillierte Informationen zu den Edge Network-Interaktionen enthalten.
1. Konzentrieren Sie sich auf die Protokolleinträge, die mit „Target Traces“ in der Beschreibung beginnen, und wählen Sie **[!UICONTROL Anzeigen]**, um Details zur Target-Verfolgung anzuzeigen

![Anzeigen von Target-Spuren mit dem Adobe Experience Platform Debugger ](assets/target-trace-debugger.png){zoomable="yes"}

Nach Auswahl **[!UICONTROL Ansicht]** wird eine Überlagerung angezeigt, in der die folgenden Informationen zur Anfrage angezeigt werden:

- Übereinstimmende Aktivitäten
- Nicht übereinstimmende Aktivitäten
- Anfragedetails
- Profil-Snapshot

Weitere Informationen zu Target-Traces finden Sie [ entsprechenden Handbuch ](https://experienceleague.adobe.com/docs/target/using/activities/troubleshoot-activities/content-trouble.html) Debugging der Bereitstellung von Target-Inhalten .

### Fehlerbehebung bei Assurance

Target-Trace-Informationen sind sowohl in der Adobe Experience Platform Debugger-Browser-Erweiterung als auch in der Assurance-Anwendung (ehemals Project Griffon) sichtbar. Gehen Sie wie folgt vor, um Target-Ablaufverfolgungen in Assurance anzuzeigen:

1. Öffnen Sie die Adobe Experience Platform Debugger-Browser-Erweiterung und verbinden Sie eine Remote-Debugging-Sitzung wie oben beschrieben
1. Wählen Sie den Link mit Ihrem Sitzungsnamen über dem Debugging-Protokoll aus
1. Platform Assurance lädt und zeigt eine detaillierte Protokollierung für alle Adobe-Anwendungen an, die im Daten-Stream für Ihre Implementierung konfiguriert sind
1. Filtern des Protokolls nach `adobe.target`
1. Wählen Sie einen Protokolleintrag mit dem Typ `com.adobe.target.trace`
1. Erweitern Sie die Details der Payload und zeigen Sie die Informationen unter `context > targetTrace` an

![Anzeigen von Target-Spuren mit Assurance](assets/target-trace-assurance.png){zoomable="yes"}

## Prüfen von Netzwerkanfragen und -antworten

Die Anfrage-Payload und die Antwort der Platform Web SDK-`sendEvent` unterscheiden sich von at.js. Die folgende Übersicht sollte Ihnen dabei helfen, die Struktur der Anfrage und Antwort zu verstehen, während Sie die Netzwerkaufrufe mit den Entwickler-Tools Ihres Browsers untersuchen.

### Payload der Inhaltsanfrage

![Targeting bestimmter Elemente der Platform Web SDK-Payload](assets/target-payload.png){zoomable="yes"}

- Profil, Entität und andere Nicht-Mbox-Parameter werden im Ereignis-Array unter `data.__adobe.target` übergeben
- Entscheidungsumfänge befinden sich im Ereignis-Array unter `query.personalization.decisionScopes`
- XDM-Daten, die nachgelagerten Mbox-Parametern zugeordnet werden, befinden sich im Ereignis-Array unter `xdm`

### Text der Inhaltsantwort

![Targeting bestimmter Elemente des Platform Web SDK-Antworttextes](assets/target-response.png){zoomable="yes"}

- Die Platform Web SDK gibt Aktionen für alle Adobe-Anwendungen unter dem `handle`-Objekt zurück
- Die `personalization:decisions` Aktion gibt eine Antwort von Target oder offer decisioning an
- Die Zielvorschläge werden als Array dargestellt, wobei jeder eine eindeutige Vorschlags-ID mit dem Präfix `AT:`
- Entscheidungsumfang und Aktivitätsdetails befinden sich im Vorschläge-Array
- Angebotsdetails befinden sich im `items`-Array unter `data`
- Antwort-Token befinden sich im `items`-Array unter `meta`

### Payload des Vorschlagsereignisses

![Beispiel für Target-Vorschlagsereignis](assets/target-proposition-event.png){zoomable="yes"}

- Target-spezifische SDK-Ereignisse werden entweder für eine Impression `decisioning.propositionDisplay` oder für eine Interaktion `decisioning.propositionInteract`, z. B. einen Klick
- Die Details des Vorschlagsereignisses befinden sich im Ereignis-Array unter `xdm._experience.decisioning`
- Die Vorschlagskennung des Anzeige- oder Interaktionsereignisses sollte mit der Vorschlagskennung des von Target zurückgegebenen Inhalts übereinstimmen.


Herzlichen Glückwunsch, Sie haben das Ende des Tutorials erreicht! Viel Glück bei der Migration Ihrer Adobe Target-Implementierung zu Web SDK!

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
