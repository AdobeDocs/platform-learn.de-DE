---
title: Debuggen | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie eine Adobe Target-Implementierung mit dem Adobe Experience Platform Web SDK debuggen. Zu den Themen gehören Debugging-Optionen, Browsererweiterungen und Unterschiede zwischen at.js und dem Platform Web SDK.
source-git-commit: 287ebcb275c4fca574dbd6cdf7e07ba4268bddb5
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 3%

---

# Target mit dem Platform Web SDK debuggen

Überprüfung von Target-Aktivitäten und Debugging des Web SDK zur Fehlerbehebung bei Implementierungs-, Inhaltsbereitstellungs- oder Zielgruppenqualifizierungsproblemen. Auf dieser Seite des Migrationshandbuchs werden die Unterschiede zwischen dem Debugging mit at.js und dem Platform Web SDK erläutert.

Die nachstehende Tabelle fasst Funktionen und Unterstützung für Test- und Debugging-Ansätze zusammen.

| Funktion oder Tool | Unterstützung von &quot;at.js&quot; | Unterstützung für Platform Web SDK |
| --- | --- | --- |
| Aktivitäts-QA-URLs | Ja | Ja |
| `mboxDisable` URL-Parameter | Ja | Weitere Informationen finden Sie unter [Target-Funktion deaktivieren](#disable-target-functionality) |
| `mboxDebug` URL-Parameter | Ja | Verwendung `alloy_debug` Parameter für ähnliche Debugging-Informationen |
| `mboxTrace` URL-Parameter | Ja | Verwenden der Browsererweiterung &quot;Experience Platform Debugger&quot; |
| Adobe Experience Platform Debugger-Erweiterung | Ja | Ja |
| `alloy_debug` URL-Parameter | Nicht zutreffend | Ja |
| Adobe Experience Platform Assurance | Nicht zutreffend | Ja |

## Adobe Experience Platform Debugger-Browsererweiterung

Die Adobe Experience Platform Debugger-Erweiterung für Chrome und Firefox überprüft Ihre Webseiten und unterstützt Sie bei der Validierung Ihrer Adobe Experience Cloud-Implementierungen.

Sie können Platform Debugger auf jeder Webseite ausführen und die Erweiterung hat Zugriff auf öffentliche Daten. Um mithilfe der Erweiterung auf nicht öffentliche Daten zuzugreifen, wie z. B. Target-Trace-Informationen, müssen Sie sich bei Experience Cloud über die **[!UICONTROL Anmelden]** Link.

### Adobe Experience Platform Debugger abrufen und installieren

Der Adobe Experience Platform Debugger kann in Google Chrome- oder Mozilla Firefox-Browsern installiert werden. Folgen Sie dem folgenden Link, um die Erweiterung in Ihrem bevorzugten Browser zu installieren:

- [Chrome](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)
- [Firefox](https://addons.mozilla.org/de/firefox/addon/adobe-experience-platform-dbg/)

Nach der Installation der Chrome-Erweiterung oder des Firefox-Add-ons wird ein Symbol (![](assets/start-icon.jpg)) wird der Erweiterungsleiste hinzugefügt. Wählen Sie dieses Symbol aus, um die Erweiterung zu öffnen.

Weitere Informationen zu [Adobe Experience Platform Debugger-Erweiterung](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) und wie Sie alle Adobe-Webanwendungen debuggen.

## Vorschau von Target-Aktivitäten mit QA-URLs

Sowohl at.js als auch Platform Web SDK ermöglichen es Ihnen, Target-Aktivitäten mithilfe von Target-QA-URLs in der Vorschau anzuzeigen. Beide Implementierungsmethoden unterstützen dieselben QA-Funktionen.

Target-QA-URLs, die funktionieren, indem at.js oder Platform Web SDK angewiesen werden, ein bestimmtes Cookie in Ihren Browser mit dem Namen `at_qa_mode`. Dieses Cookie wird verwendet, um die Qualifizierung für eine bestimmte Aktivität und ein bestimmtes Erlebnis zu erzwingen.

>[!CAUTION]
>
>Die Funktionalität des Target-QA-Modus wird von der Platform Web SDK-Version 2.13.0 oder höher unterstützt. Der QA-Modus von Target wird basierend auf dem `xdm.web.webPageDetails.URL` Wert, der an die `sendEvent` aufrufen. Änderungen an diesem Wert, z. B. Kleinbuchstaben für alle Zeichen, können verhindern, dass der Target-QA-Modus ordnungsgemäß funktioniert.

Weitere Informationen finden Sie im entsprechenden Handbuch [Target-Aktivitäts-QA](https://experienceleague.adobe.com/docs/target/using/activities/activity-qa/activity-qa.html).

## Target-Implementierung debuggen

In der folgenden Tabelle werden die Unterschiede zwischen der Debugging-Taktik von at.js und Platform Web SDK erläutert:

| &quot;at.js&quot;-Funktion | Platform Web SDK-Entsprechung |
| --- | --- |
| **Mbox deaktivieren** - Deaktivieren Sie Target vom Abrufen und Rendern, um zu überprüfen, ob die Seite ohne Target-Interaktionen beschädigt ist.<br><br>Seite mit URL-Parameter laden: `mboxDisable=true` | Keine direkte Entsprechung. Sie können alle Platform Web SDK-Anforderungen mit den Entwicklertools Ihres Browsers blockieren. |
| **Mbox Debug** - protokolliert jede at.js-Aktion in der Browser-Konsole, um Probleme beim Rendering zu beheben<br><br>Seite mit URL-Parameter laden: `mboxDebug=true` | **Alloy Debug** - protokolliert detaillierte Aktionen des SDK, einschließlich, aber nicht beschränkt auf Target-Personalisierungsaktionen.<br><br>Seite mit URL-Parameter laden: `alloy_debug=true`  <br /><br />Oder ausführen `alloy("setDebug", { "enabled": true });` in der Entwicklerkonsole |
| **Target Trace** - mit einem Mbox-Trace-Token, das in der Target-Benutzeroberfläche generiert wurde, ist ein Trace-Objekt mit Details, die am Entscheidungsprozess beteiligt waren, verfügbar unter `window.___target_trace` -Objekt.<br><br>Seite mit URL-Parameter laden: `mboxTrace=window&authorization={TOKEN}` | Verwenden Sie die Adobe Experience Platform Debugger-Erweiterung oder Platform Assurance. |

>[!NOTE]
>
>Alle oben aufgeführten at.js-Debugging-Funktionen sind mit erweiterten Funktionen in Adobe Experience Platform Debugger verfügbar.

### Funktion &quot;Target deaktivieren&quot;

Das Platform Web SDK verfügt derzeit nicht über eine Funktion, um Target-Antworten selektiv zu unterdrücken. Es ist jedoch möglich, die Platform Web SDK-Anforderungen mit den Entwicklertools Ihres Browsers, verschiedenen Browsererweiterungen oder Drittanbieteranwendungen zu unterdrücken. So blockieren Sie beispielsweise das Platform Web SDK mit Google Chrome:

1. Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle auf der Seite und wählen Sie **Inspect**
1. Wählen Sie die **Netzwerk** tab
1. Nach Zeichenfolge filtern `//ee//` nur Platform Web SDK-Aufrufe anzeigen
1. Seite neu laden
1. Klicken Sie mit der rechten Maustaste auf eine der gefilterten Netzwerkanforderungen und wählen Sie **Anforderungsdomäne blockieren**
1. Laden Sie die Seite neu und beachten Sie, dass die Netzwerkanforderung blockiert ist.
1. Wenn Sie das Debugging abgeschlossen haben, klicken Sie mit der rechten Maustaste auf die blockierte Netzwerkanforderung und wählen Sie **Entsperren** oder schließen Sie das Bedienfeld &quot;Entwicklertools&quot;

### Debug-Protokollierung anzeigen

Debug-Protokollierung für at.js mithilfe der `mboxDebug=true` Der URL-Parameter zeigt detaillierte Informationen zu den einzelnen Target-Anforderungen, -Antworten und Versuchen, den Inhalt auf der Seite zu rendern. Das Platform Web SDK weist eine ähnliche Debug-Protokollierung mithilfe der `alloy_debug=true` URL-Parameter.

| Protokollierte Informationen | at.js (`mboxDebug=true`) | Platform Web-SDK (`alloy_debug=true`) |
| --- | --- | --- |
| Protokollierpräfix für Filter | `AT:` | `[alloy]` |
| Details zur Seitenladeanforderung | Ja | Ja |
| Details zu Mbox- oder Scope-Anfragen | Ja | Ja |
| Anfragestatus | Ja | Ja |
| Reaktionsdetails | Ja | Ja |
| Rendering-Status | Erfolg und Fehler | Nur Fehler |
| Renderdetails | Ja | Ja |

>[!NOTE]
>
>Debug-Protokolle für at.js und Platform Web SDK bieten eine ähnliche Detailebene mit der wichtigen Ausnahme, dass das Web SDK nur über Rendering-Fehler aufgrund ungültiger Selektoren benachrichtigt. Die Debug-Protokollierung bestätigt derzeit nicht, dass das Rendering erfolgreich war.

### Target-Traces anzeigen

Target-Traces enthalten detaillierte Informationen zu Aktivitätsqualifikationen und zum Target-Profil des Besuchers. Da Target-Traces Informationen enthalten, die nicht öffentlich verfügbar sind, ist für die Anzeige dieser Informationen ein Autorisierungstoken oder eine Authentifizierung innerhalb des Browsererweiterungsfensters von Adobe Experience Platform Debugger erforderlich.

| Target-Trace-Methode | at.js | Platform Web-SDK |
| --- | --- | --- |
| `mboxTrace` URL-Parameter | Ja | Nein |
| Adobe Experience Platform Debugger-Browsererweiterung | Ja | Ja |
| Adobe Experience Platform Assurance | Nein | Ja |


Um Platform Web SDK Target-Traces mit dem Adobe Experience Platform Debugger anzuzeigen, gehen Sie wie folgt vor:

1. Navigieren Sie zu einer Seite Ihrer Site, auf der Target mit dem Platform Web SDK implementiert ist.
1. Öffnen Sie die Adobe Experience Platform Debugger-Erweiterung, indem Sie auf das Symbol (![](assets/start-icon.jpg)) in der Navigationsleiste Ihres Browsers
1. Wählen Sie die **[!UICONTROL Anmelden]** link
1. Authentifizierung mit Ihrer Adobe Experience Cloud-Anmeldung
1. Wählen Sie die **[!UICONTROL Protokolle]** Registerkarte links
1. Wählen Sie die **[!UICONTROL Edge]** Registerkarte oben
1. Benennen Sie optional Ihre Debugging-Sitzung und klicken Sie auf die Schaltfläche **[!UICONTROL Verbinden]** button
1. Laden Sie die Seite neu, und das Protokoll sollte mit detaillierten Informationen zu den Interaktionen im Edge-Netzwerk gefüllt werden.
1. Konzentrieren Sie sich auf die Protokolleinträge, die in der Beschreibung mit &quot;Target Traces&quot;beginnen, und wählen Sie **[!UICONTROL Ansicht]** Anzeigen von Target-Trace-Details

![Anzeigen von Target-Traces mit Adobe Experience Platform Debugger](assets/target-trace-debugger.png){zoomable=&quot;yes&quot;}

Nach Auswahl **[!UICONTROL Ansicht]** wird eine Überlagerung angezeigt, über die Sie die folgenden Informationen zur Anfrage sehen können:

- Abgeschlossene Aktivitäten
- Nicht übereinstimmende Aktivitäten
- Anfragedetails
- Profil-Snapshot

Weitere Informationen finden Sie im entsprechenden Handbuch zu [Debugging der Target-Inhaltsbereitstellung](https://experienceleague.adobe.com/docs/target/using/activities/troubleshoot-activities/content-trouble.html) für weitere Informationen zu Target-Traces.

### Fehlerbehebung bei der Zuverlässigkeitsprüfung

Target-Trace-Informationen sind sowohl in der Browsererweiterung &quot;Adobe Experience Platform Debugger&quot;als auch in der Anwendung &quot;Assurance&quot;(ehemals &quot;Project Griffon&quot;) sichtbar. Gehen Sie wie folgt vor, um Target-Traces innerhalb von Assurance anzuzeigen:

1. Öffnen Sie die Adobe Experience Platform Debugger-Browsererweiterung und verbinden Sie wie oben beschrieben eine Remote-Debugging-Sitzung.
1. Wählen Sie den Link mit Ihrem Sitzungsnamen über dem Debugging-Protokoll aus.
1. Platform Assurance lädt und zeigt eine detaillierte Protokollierung für alle Adobe Apps an, die im Datenstrom für Ihre Implementierung konfiguriert sind
1. Filtern Sie das Protokoll nach `adobe.target`
1. Wählen Sie einen Protokolleintrag mit dem Typ `com.adobe.target.trace`
1. Erweitern Sie die Details der Payload und zeigen Sie die Informationen unter `context > targetTrace`

![Anzeigen von Target-Traces mit Assurance](assets/target-trace-assurance.png){zoomable=&quot;yes&quot;}

## Netzwerkanforderung und -antwort untersuchen

Anfrage-Payload und Antwort des Platform Web SDK `sendEvent` -Aufrufe unterscheiden sich von at.js. Der nachstehende Entwurf soll Ihnen dabei helfen, die Struktur der Anfrage und Antwort zu verstehen, während Sie die Netzwerkaufrufe mit den Entwicklertools Ihres Browsers untersuchen.

### Payload der Inhaltsanforderung

![Target-spezifische Elemente der Platform Web SDK-Payload](assets/target-payload.png){zoomable=&quot;yes&quot;}

- Profil-, Entitäts- und andere Nicht-Mbox-Parameter werden im Ereignis-Array unter `data.__adobe.target`
- Entscheidungsbereiche befinden sich im Ereignisarray unter `query.personalization.decisionScopes`
- XDM-Daten, die nachgelagerten Mbox-Parametern zugeordnet werden, befinden sich im Ereignisarray unter `xdm`

### Inhalts-Antworttext

![Target-spezifische Elemente des Platform Web SDK-Antworttextes](assets/target-response.png){zoomable=&quot;yes&quot;}

- Das Platform Web SDK gibt Aktionen für alle Adobe Apps unter der `handle` Objekt
- Die `personalization:decisions` Aktion bedeutet eine Antwort von Target oder offer decisioning
- Zielvorschläge werden als Array dargestellt, wobei jeder eine eindeutige Vorschlagskennung mit dem Präfix `AT:`
- Entscheidungsbereich und Aktivitätsdetails befinden sich im Vorschlagsbereich
- Die Angebotsdetails finden Sie unter `items` Array unter `data`
- Antwort-Token befinden sich im `items` Array unter `meta`

### Payload des Vorschlags-Ereignisses

![Beispiel für Target-Vorschlagsereignis](assets/target-proposition-event.png){zoomable=&quot;yes&quot;}

- Target-spezifische SDK-Ereignisse sind entweder `decisioning.propositionDisplay` für eine Impression oder `decisioning.propositionInteract` für eine Interaktion, z. B. einen Klick
- Die Details des Vorschlagsereignisses befinden sich im &quot;events&quot;-Array unter `xdm._experience.decisioning`
- Die Vorschlagskennung des Anzeige- oder Interaktionsereignisses sollte mit der Vorschlagskennung des Inhalts übereinstimmen, die von Target zurückgegeben wird


Herzlichen Glückwunsch! Sie haben das Ende des Tutorials erreicht! Viel Glück bei der Migration Ihrer Adobe Target-Implementierung auf das Web SDK!

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
