---
title: Validieren von Target-Implementierungen mit dem Web SDK | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Aktivitäten validieren und eine Adobe Target-Implementierung mit dem Adobe Experience Platform Web SDK debuggen.
source-git-commit: 287ebcb275c4fca574dbd6cdf7e07ba4268bddb5
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 0%

---

# Validieren der Platform Web SDK-Implementierung

Nachdem Sie Ihre Target-Implementierung von at.js auf das Platform Web SDK migriert haben, müssen Sie vor dem Veröffentlichen von Änderungen auf Ihrer Produktions-Site überprüfen, ob alles ordnungsgemäß funktioniert. Adobe empfiehlt Folgendes, das auf dieser Seite ausführlich beschrieben wird:

* Führen Sie eine technische Validierung durch, um sicherzustellen, dass die grundlegenden Implementierungs- und Platform Web SDK-Anforderungen und -Antworten korrekt aussehen.
* Sicherstellen, dass Target-Aktivitäten ordnungsgemäß bereitgestellt und gerendert werden
* Überprüfen, ob die Berichterstellung ordnungsgemäß funktioniert
* Besuchen Sie Zielgruppen und Profilskripte erneut, um sicherzustellen, dass sie mit dem Platform Web SDK kompatibel sind.
* Sicherstellen, dass Integrationen mit Adobe- oder Drittanbieteranwendungen ordnungsgemäß funktionieren

Jede Target-Implementierung unterscheidet sich je nach verwendeter Site-Architektur und -Funktionen. Sie können die folgenden Tabellen als Ausgangspunkt verwenden und Elemente hinzufügen, die für Ihre Implementierung spezifisch sind. Die [Debugging-Seite](debugging.md) In diesem Tutorial werden die Tools vorgestellt, die Sie zur Unterstützung dieser Validierung verwenden können.

## Technische Validierung

| Validierungselement | Anmerkungen |
|---|---|
| Der at.js-Codeausschnitt zur Vorab-Ausblendung ist nicht mehr auf der Seite vorhanden | Das Platform Web SDK entfernt den Stil nicht automatisch mit ID `at-body-style`. Wenn Sie dieses alte Snippet auf der Seite belassen, werden ausgeblendete Inhalte angezeigt, bis der Timeout des Snippets erreicht ist. |
| Die at.js-Bibliothek ist nicht mehr auf der Seite vorhanden | Vergewissern Sie sich, dass in der Entwicklertools-Konsole Ihres Browsers kein Objekt &quot;adobe.target&quot;vorhanden ist. Die Verwendung von Platform Web SDK und at.js führt zu unbeabsichtigtem Rendering-Verhalten |
| Die erwarteten Parameter befinden sich in den XDM- und Datenobjekten der `sendEvent` Anfrage |  |
| Der Recommendations-Katalog wird erwartungsgemäß aktualisiert, wenn Seitenanforderungen zum Ausfüllen des Katalogs verwendet werden |  |
| Profilparameter wurden erfolgreich an Target übergeben | Anzeigen von Edge-Spuren im Debugger |
| Parameter, die XDM im Datastream-Mapper zugeordnet sind, werden korrekt an Target übergeben | Validieren mithilfe der Edge Trace-Funktion des Debuggers und/oder der Assurance |
| Target-Inhalte werden in der entsprechenden `sendEvent` Antworten | Erwartet bei `renderDecisions` ist auf `true` oder Bereiche angefordert werden und der Benutzer sich für eine bestimmte Target-Aktivität qualifiziert |
| A `decisioning.propositionDisplay` -Ereignis ausgelöst wird, nachdem VEC-basierte Aktivitäten gerendert wurden | Automatisch gerenderte und On-Demand-Aktivitäten werden voraussichtlich über separate Ereignisaufrufe verfügen |
| A `decisioning.propositionDisplay` -Ereignis ausgelöst wird, nachdem formularbasierte Aktivitäten gerendert wurden | Gilt nur für bestimmte Implementierungen. Erfordert benutzerdefinierten Code, um diesen Aufruf auszuführen. |
| A `decisioning.propositionDisplay` -Ereignis ausgelöst wird, wenn ein Angebot auf eine Änderung der SPA angewendet wird | Gilt nur für SPA Implementierungen |
| A `decisioning.propositionDisplay` -Ereignis wird NICHT ausgelöst, wenn eine SPA-Komponente für eine bestimmte Ansicht erneut gerendert wird | Gilt nur für SPA Implementierungen |
| A `decisioning.propsitionInteract` -Ereignis nach einer Aktivitätskonvertierung ausgelöst wird | Die von at.js migrierten benutzerdefinierten Konvertierungen &quot;Klicks auf ein Element&quot;und `trackEvent` oder `sendNotifications` werden voraussichtlich über separate Ereignisaufrufe verfügen |
| Antwort-Token werden im `sendEvent` Antwort und erwartete Werte | Antwort-Token sollten mit dem Web SDK normal funktionieren |
| ECIDs sind seitenübergreifend mit Web SDK und at.js konsistent | Gilt für seitenweise Migrationen. Es wird erwartet, dass Umleitungsangebote in diesen Arten von Migrationen nicht funktionieren. |


## Aktivitätsbereitstellung und -rendering

| Validierungselement | Anmerkungen |
|---|---|
| VEC-basierte Aktivitäten werden beim Laden der Seite ordnungsgemäß gerendert | Es ist am besten, sowohl benutzerspezifische Codeänderungen als auch grundlegende Änderungen zu überprüfen, wie z. B. das Neuanordnen von Elementen oder das Ersetzen von Text |
| VEC-basierte Aktivitäten werden bei Änderungen der SPA korrekt dargestellt | Gilt nur für SPA Implementierungen |
| Formularbasierte Aktivitäten werden ordnungsgemäß gerendert | Gilt nur für bestimmte Implementierungen. Für das Rendern von formularbasierten Aktivitäten ist ein benutzerdefinierter Code erforderlich, der mit at.js vergleichbar ist. |
| Aktivitäten, die Umleitungen verwenden, funktionieren ordnungsgemäß | Umleitungen werden unterstützt, wenn sowohl die Quell- als auch die Zielseite das Platform Web SDK verwenden. Eine Target-Umleitung von einer at.js-Seite zu einer Platform Web SDK-Seite oder umgekehrt wird nicht unterstützt. |
| Aktivitäten, die Remote-Angebote verwenden, funktionieren ordnungsgemäß | Nicht üblich, überprüfen Sie Ihren Target-Angebotsbestand auf Remote-Angebote. |
| Flackern wird entsprechend reduziert | Die Behandlung von Flackern ist optional. Stellen Sie jedoch sicher, dass alle von Ihnen vorhandenen Reduzierungstaktiken wie erwartet funktionieren, um eine optimale Seitenleistung und ein optimales Benutzererlebnis zu erzielen. |
| QA-Links funktionieren erwartungsgemäß | Wenn die URL nicht funktioniert, überprüfen Sie, ob web.webPageDetails.URL genau mit der URL im Browser übereinstimmt. |
| Alle gängigen Angebotstypen werden erwartungsgemäß gerendert |  |

## Reporting

| Validierungselement | Anmerkungen |
|---|---|
| Besucher werden VEC-basierten Aktivitäten zugeordnet | Es ist am besten, die Berichterstellung für Änderungen am Seitenladevorgang und SPA Änderungen der Ansicht zu validieren |
| Besucher werden formularbasierten Aktivitäten zugeordnet | Je nach verwendetem Rendering-Ansatz erfordert Ihre Implementierung möglicherweise benutzerdefinierten Code, um eine `decisioning.propositionDisplay` event |
| Standardmäßige Konversionsziele werden ordnungsgemäß erfasst | Gilt entweder für Target oder Analytics als Berichtsquelle |
| Bestellkonvertierungen und Details werden ordnungsgemäß erfasst | Überprüfen des Prüfberichts |
| Klick-Tracking-Konversionen werden ordnungsgemäß erfasst |  |
| Benutzerdefinierte Konversionsziele werden ordnungsgemäß erfasst | Beispielsweise werden Konversionsziele von at.js migriert `trackEvent` oder `sendNotifications` die häufig mit dem Ziel &quot;Angezeigte Mbox&quot;verwendet werden |

## Zielgruppen und Profilskripte

| Validierungselement | Anmerkungen |
|---|---|
| In Live-Aktivitäten verwendete Zielgruppen sind mit dem Platform Web SDK kompatibel | Zielgruppen, die die Komponente &quot;Benutzerdefiniert&quot;(Mbox-Parameter) verwenden, müssen aktualisiert werden und XDM-Attribute enthalten |
| Alle Profilskripte sind mit dem Platform Web SDK kompatibel. | Alle Profilskripte, die Mbox-Parameter verwenden, müssen aktualisiert werden, um XDM-Attribute einzuschließen |
| Rückgabe von Aktivitäten für Target-Zielgruppen | Am besten führen Sie eine durchgängige Validierung von Zielgruppen durch, die Sie ändern, um die Kompatibilität mit dem Platform Web SDK herzustellen |
| Profilskripte werden erwartungsgemäß ausgewertet | Anzeigen von Edge-Spuren im Debugger |

## Integrationen mit Adobe Apps

| Validierungselement | Anmerkungen |
|---|---|
| Aktivitäten werden für Experience Cloud-Zielgruppen zurückgegeben | Beispiel: ein aus Adobe Analytics veröffentlichtes Segment |
| Aktivitäten werden für Experience Platform-Zielgruppen zurückgegeben | Gilt nur, wenn Sie über eine Lizenz für eine Experience Platform-basierte Anwendung wie RTCDP verfügen |
| Aktivitäten werden für Audience Manager-Zielgruppen zurückgegeben | Beispiel: ein Segment, das auf dem Besuch einer bestimmten Seite basiert |
| Target-Aktivitätsdaten werden in Analysis Workspace angezeigt | Gilt für Aktivitäten, die Adobe Analytics als Berichtsquelle verwenden |

## Integrationen mit Drittanbieteranwendungen

| Validierungselement | Anmerkungen |
|---|---|
| Antwort-Token-Daten werden ordnungsgemäß an Drittanbieteranwendungen übergeben. | Die Integrationsansätze können variieren. Eine gängige Methode besteht jedoch darin, Target-Antwort-Token zu verwenden, um Aktivitäts- und Erlebnisinformationen an andere Analysetools wie Google Analytics zu übergeben. |
| Informationen von Drittanbietern werden als XDM- oder Profildaten übergeben. | Alle relevanten Informationen von Dritten sollten weitergegeben werden `sendEvent` Aufrufe an Target |

Nachdem Sie die obigen Validierungsschritte ausgeführt haben, können Sie sich darauf verlassen, dass die Platform Web SDK-Implementierung bereit für den Übergang zur Produktion ist.

Als Nächstes erfahren Sie, wie Sie [Fehlerbehebung bei einer Target-Implementierung mithilfe des Platform Web SDK](debugging.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).