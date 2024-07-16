---
title: Validieren von Target-Implementierungen mit dem Web SDK | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Aktivitäten validieren und eine Adobe Target-Implementierung mit dem Adobe Experience Platform Web SDK debuggen.
exl-id: 09b4ebeb-fae9-470d-8ea9-f6e3c7d7da5e
source-git-commit: 4690d41f92c83fe17eda588538d397ae1fa28af0
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 0%

---

# Validieren der Platform Web SDK-Implementierung

Nachdem Sie Ihre Target-Implementierung von at.js auf das Platform Web SDK migriert haben, müssen Sie vor dem Veröffentlichen von Änderungen auf Ihrer Produktions-Site überprüfen, ob alles ordnungsgemäß funktioniert. Adobe empfiehlt Folgendes, das auf dieser Seite ausführlich beschrieben wird:

* Führen Sie eine technische Validierung durch, um sicherzustellen, dass die grundlegenden Implementierungs- und Platform Web SDK-Anforderungen und -Antworten korrekt aussehen.
* Sicherstellen, dass Target-Aktivitäten ordnungsgemäß bereitgestellt und gerendert werden
* Überprüfen, ob die Berichterstellung ordnungsgemäß funktioniert
* Besuchen Sie Zielgruppen und Profilskripte erneut, um sicherzustellen, dass sie mit dem Platform Web SDK kompatibel sind.
* Sicherstellen, dass Integrationen mit Adobe- oder Drittanbieteranwendungen ordnungsgemäß funktionieren

Jede Target-Implementierung unterscheidet sich je nach verwendeter Site-Architektur und -Funktionen. Sie können die folgenden Tabellen als Ausgangspunkt verwenden und Elemente hinzufügen, die für Ihre Implementierung spezifisch sind. Auf der [Debugging-Seite](debugging.md) dieses Tutorials finden Sie Tools, die Sie zur Unterstützung dieser Validierung verwenden können.

## Technische Validierung

| Validierungselement | Anmerkungen |
|---|---|
| Der at.js-Codeausschnitt zur Vorab-Ausblendung ist nicht mehr auf der Seite vorhanden | Das Platform Web SDK entfernt den Stil nicht automatisch mit der ID `at-body-style`. Wenn Sie dieses alte Snippet auf der Seite belassen, werden ausgeblendete Inhalte angezeigt, bis der Timeout des Snippets erreicht ist. |
| Die at.js-Bibliothek ist nicht mehr auf der Seite vorhanden | Vergewissern Sie sich, dass in der Entwicklertools-Konsole Ihres Browsers kein Objekt &quot;adobe.target&quot;vorhanden ist. Die Verwendung von Platform Web SDK und at.js führt zu unbeabsichtigtem Rendering-Verhalten |
| Erwartete Parameter befinden sich in den XDM- und Datenobjekten der `sendEvent`-Anfrage | |
| Der Recommendations-Katalog wird erwartungsgemäß aktualisiert, wenn Seitenanforderungen zum Ausfüllen des Katalogs verwendet werden | |
| Profilparameter wurden erfolgreich an Target übergeben | Anzeigen von Edge-Traces im Debugger |
| Parameter, die XDM im Datastream-Mapper zugeordnet sind, werden korrekt an Target übergeben | Validieren mit der Edge Trace-Funktion des Debuggers und/oder der Assurance |
| Target-Inhalte werden in den entsprechenden `sendEvent` -Antworten zurückgegeben | Wird erwartet, wenn die Option `renderDecisions` auf `true` gesetzt ist oder Bereiche angefordert werden und der Benutzer für eine bestimmte Target-Aktivität qualifiziert ist |
| Ein `decisioning.propositionDisplay` -Ereignis wird ausgelöst, nachdem VEC-basierte Aktivitäten gerendert wurden | Automatisch und On-Demand-Aktivitäten werden voraussichtlich über separate Ereignisaufrufe verfügen |
| Ein `decisioning.propositionDisplay` -Ereignis wird ausgelöst, nachdem formularbasierte Aktivitäten gerendert wurden | Gilt nur für bestimmte Implementierungen. Erfordert benutzerdefinierten Code, um diesen Aufruf auszuführen. |
| Ein `decisioning.propositionDisplay` -Ereignis wird ausgelöst, wenn ein Angebot auf eine Änderung der SPA angewendet wird | Gilt nur für SPA Implementierung |
| Ein `decisioning.propositionDisplay` -Ereignis wird NICHT ausgelöst, wenn eine SPA-Komponente für eine bestimmte Ansicht erneut gerendert wird | Gilt nur für SPA Implementierung |
| Ein `decisioning.propsitionInteract` -Ereignis wird nach einer Aktivitätskonvertierung ausgelöst | Es wird erwartet, dass die von at.js `trackEvent` oder `sendNotifications` migrierten benutzerdefinierten Konvertierungen &quot;Angeklicktes Element&quot;und &quot;Benutzerdefinierte Konversionen&quot;separate Ereignisaufrufe aufweisen |
| Antwort-Token werden in der Antwort `sendEvent` zurückgegeben und weisen erwartete Werte auf | Antwort-Token sollten mit dem Web SDK normal funktionieren |
| ECIDs sind seitenübergreifend mit Web SDK und at.js konsistent | Gilt für seitenweise Migrationen. Es wird erwartet, dass Umleitungsangebote in diesen Arten von Migrationen nicht funktionieren. |


## Aktivitätsbereitstellung und -rendering

| Validierungselement | Anmerkungen |
|---|---|
| VEC-basierte Aktivitäten werden beim Laden der Seite ordnungsgemäß dargestellt | Es ist am besten, sowohl benutzerspezifische Codeänderungen als auch grundlegende Änderungen zu überprüfen, wie z. B. das Neuanordnen von Elementen oder das Ersetzen von Text |
| VEC-basierte Aktivitäten werden bei Änderungen der SPA korrekt dargestellt | Gilt nur für SPA Implementierung |
| Formularbasierte Aktivitäten werden ordnungsgemäß gerendert | Gilt nur für bestimmte Implementierungen. Für das Rendern von formularbasierten Aktivitäten ist ein benutzerdefinierter Code erforderlich, der mit at.js vergleichbar ist. |
| Aktivitäten, die Umleitungen verwenden, funktionieren ordnungsgemäß | Umleitungen werden unterstützt, wenn sowohl die Quell- als auch die Zielseite das Platform Web SDK verwenden. Eine Target-Umleitung von einer at.js-Seite zu einer Platform Web SDK-Seite oder umgekehrt wird nicht unterstützt. |
| Aktivitäten, die Remote-Angebote verwenden, funktionieren ordnungsgemäß | Nicht üblich, überprüfen Sie Ihren Target-Angebotsbestand auf Remote-Angebote. |
| Flackern wird entsprechend reduziert | Die Behandlung von Flackern ist optional. Stellen Sie jedoch sicher, dass alle von Ihnen vorhandenen Reduzierungstaktiken wie erwartet funktionieren, um eine optimale Seitenleistung und ein optimales Benutzererlebnis zu erzielen. |
| QA-Links funktionieren erwartungsgemäß | Wenn die URL nicht funktioniert, überprüfen Sie, ob web.webPageDetails.URL genau mit der URL im Browser übereinstimmt |
| Alle gängigen Angebotstypen werden erwartungsgemäß gerendert |  |

## Reporting

| Validierungselement | Anmerkungen |
|---|---|
| Besucher werden VEC-basierten Aktivitäten zugeordnet | Es ist am besten, die Berichterstellung für Änderungen am Seitenladevorgang und SPA Änderungen der Ansicht zu validieren |
| Besucher werden formularbasierten Aktivitäten zugeordnet | Je nach verwendetem Rendering-Ansatz erfordert Ihre Implementierung möglicherweise benutzerdefinierten Code, um ein `decisioning.propositionDisplay` -Ereignis auszuführen |
| Standardmäßige Konversionsziele werden ordnungsgemäß erfasst | Gilt entweder für Target oder Analytics als Berichtsquelle |
| Bestellkonvertierungen und Details werden ordnungsgemäß erfasst | Überprüfen des Prüfberichts |
| Klick-Tracking-Konversionen werden ordnungsgemäß erfasst |  |
| Benutzerdefinierte Konversionsziele werden ordnungsgemäß erfasst | So werden z. B. Konversionsziele aus at.js `trackEvent` oder `sendNotifications` migriert, die häufig mit dem Ziel &quot;Angezeigte Mbox&quot;verwendet werden |

## Zielgruppen und Profilskripte

| Validierungselement | Anmerkungen |
|---|---|
| In Live-Aktivitäten verwendete Zielgruppen sind mit dem Platform Web SDK kompatibel | Zielgruppen, die die Komponente &quot;Benutzerdefiniert&quot;(Mbox-Parameter) verwenden, müssen aktualisiert werden und XDM-Attribute enthalten |
| Alle Profilskripte sind mit dem Platform Web SDK kompatibel. | Alle Profilskripte, die Mbox-Parameter verwenden, müssen aktualisiert werden, um XDM-Attribute einzuschließen |
| Rückgabe von Aktivitäten für Target-Zielgruppen | Am besten führen Sie eine durchgängige Validierung von Zielgruppen durch, die Sie ändern, um die Kompatibilität mit dem Platform Web SDK herzustellen. |
| Profilskripte werden erwartungsgemäß ausgewertet | Anzeigen von Edge-Traces im Debugger |

## Integrationen mit Adobe-Applikationen

| Validierungselement | Anmerkungen |
|---|---|
| Aktivitäten geben für Experience Cloud-Zielgruppen zurück | Beispiel: ein aus Adobe Analytics veröffentlichtes Segment |
| Aktivitäten geben für Experience Platform-Zielgruppen zurück | Gilt nur, wenn Sie über eine Lizenz für eine Experience Platform-basierte Anwendung wie RTCDP verfügen |
| Aktivitäten werden für Audience Manager-Zielgruppen zurückgegeben | Ein Segment, das auf dem Besuch einer bestimmten Seite basiert |
| Target-Aktivitätsdaten werden in Analysis Workspace angezeigt | Gilt für Aktivitäten, die Adobe Analytics als Berichtsquelle verwenden |

## Integrationen mit Drittanbieteranwendungen

| Validierungselement | Anmerkungen |
|---|---|
| Antwort-Token-Daten werden ordnungsgemäß an Drittanbieteranwendungen übergeben. | Die Integrationsansätze können variieren. Eine gängige Methode besteht jedoch darin, Target-Antwort-Token zu verwenden, um Aktivitäts- und Erlebnisinformationen an andere Analysetools wie Google Analytics weiterzugeben. |
| Informationen von Drittanbietern werden als XDM- oder Profildaten übergeben. | Alle relevanten Informationen von Drittanbietern sollten in `sendEvent` -Aufrufen an Target übergeben werden. |

Nachdem Sie die obigen Validierungsschritte ausgeführt haben, können Sie sich darauf verlassen, dass die Platform Web SDK-Implementierung bereit für den Übergang zur Produktion ist.

Als Nächstes erfahren Sie, wie Sie mit dem Platform Web SDK](debugging.md) eine Fehlerbehebung bei einer Target-Implementierung durchführen.[

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
