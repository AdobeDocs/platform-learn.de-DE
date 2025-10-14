---
title: Validieren von Target-Implementierungen mit Web SDK - Migrieren von Target von at.js 2.x zu Web SDK
description: Erfahren Sie, wie Sie Aktivitäten validieren und eine Adobe Target-Implementierung mithilfe der Adobe Experience Platform Web SDK debuggen.
exl-id: 09b4ebeb-fae9-470d-8ea9-f6e3c7d7da5e
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 0%

---

# Validieren der Implementierung von Platform Web SDK

Nachdem Sie Ihre Target-Implementierung von at.js zu Platform Web SDK migriert haben, müssen Sie überprüfen, ob alles ordnungsgemäß funktioniert, bevor Sie Änderungen an Ihrer Produktions-Site veröffentlichen. Adobe empfiehlt Folgendes. Ausführliche Informationen finden Sie auf dieser Seite:

* Führen Sie eine technische Validierung durch, um sicherzustellen, dass die grundlegende Implementierung und die Platform Web SDK-Anfragen und -Antworten korrekt aussehen
* Sicherstellen, dass Target-Aktivitäten ordnungsgemäß bereitgestellt und gerendert werden
* Überprüfen, ob das Reporting ordnungsgemäß funktioniert
* Gehen Sie zu Zielgruppen und Profilskripten zurück, um sicherzustellen, dass sie mit Platform Web SDK kompatibel sind
* Sicherstellen, dass Integrationen mit Adobe- oder Drittanbieterprogrammen ordnungsgemäß funktionieren

Jede Target-Implementierung unterscheidet sich je nach Site-Architektur und verwendeten Funktionen. Sie können die folgenden Tabellen als Ausgangspunkt verwenden und alle Elemente hinzufügen, die für Ihre Implementierung eindeutig sind. Auf [&#x200B; Seite „Debugging](debugging.md) dieses Tutorials werden Tools angezeigt, die Sie bei dieser Validierung verwenden können.

## Technische Validierung

| Validierungselement | Anmerkungen |
|---|---|
| Das Code-Fragment zum Vorab-Ausblenden von at.js ist auf der Seite nicht mehr vorhanden | Platform Web SDK entfernt den Stil mit der ID `at-body-style` nicht automatisch. Wenn Sie dieses alte Snippet auf der Seite belassen, wird der Inhalt ausgeblendet, bis das Snippet-Timeout erreicht ist. |
| Die at.js-Bibliothek ist nicht mehr auf der Seite vorhanden. | Vergewissern Sie sich, dass in der Entwicklertools-Konsole Ihres Browsers kein „adobe.target“-Objekt vorhanden ist. Das Einschließen von Platform Web SDK und at.js führt zu unbeabsichtigtem Rendering-Verhalten |
| Die erwarteten Parameter befinden sich im XDM und in den Datenobjekten der `sendEvent` | |
| Der Recommendations-Katalog wird erwartungsgemäß aktualisiert, wenn Seitenanfragen zum Ausfüllen des Katalogs verwendet werden | |
| Profilparameter wurden erfolgreich an Target übergeben | Anzeigen von Edge-Ablaufverfolgungen im Debugger |
| Parameter, die im Datenstrom-Mapper XDM zugeordnet sind, werden korrekt an Target übergeben | Validieren mithilfe der Edge-Trace-Funktion des Debuggers und/oder der Assurance |
| Zielinhalt wird in den entsprechenden `sendEvent` Antworten zurückgegeben | Wird erwartet, wenn `renderDecisions` Option auf `true` gesetzt oder Bereiche angefordert werden und der Benutzer für eine bestimmte Target-Aktivität qualifiziert ist |
| Ein `decisioning.propositionDisplay`-Ereignis wird ausgelöst, nachdem VEC-basierte Aktivitäten gerendert wurden | Für automatisch und bei Bedarf gerenderte Aktivitäten werden separate Ereignisaufrufe erwartet |
| Ein `decisioning.propositionDisplay`-Ereignis wird ausgelöst, nachdem formularbasierte Aktivitäten gerendert werden | Gilt nur für bestimmte Implementierungen. Erfordert benutzerdefinierten Code, um diesen Aufruf auszuführen. |
| Ein `decisioning.propositionDisplay` wird ausgelöst, wenn ein Angebot auf eine SPA-Ansichtsänderung angewendet wird | Nur für SPA-Implementierungen anwendbar |
| Ein `decisioning.propositionDisplay` wird NICHT ausgelöst, wenn eine SPA-Komponente für eine bestimmte Ansicht erneut gerendert wird | Nur für SPA-Implementierungen anwendbar |
| Nach einer Aktivitätskonvertierung wird ein `decisioning.propsitionInteract`-Ereignis ausgelöst | Für „Elementklick“ und benutzerdefinierte Konversionen, die aus at.js-`trackEvent` oder -`sendNotifications` migriert wurden, werden separate Ereignisaufrufe erwartet |
| Antwort-Token werden in der `sendEvent` Antwort zurückgegeben und haben erwartete Werte | Antwort-Token sollten mit Web SDK normal funktionieren |
| ECIDs sind auf allen Seiten mit Web SDK und at.js konsistent | Gilt für seitenweise Migrationen. Bei diesen Migrationstypen werden keine Umleitungsangebote erwartet. |


## Aktivitätsbereitstellung und -rendering

| Validierungselement | Anmerkungen |
|---|---|
| VEC-basierte Aktivitäten werden beim Laden der Seite korrekt dargestellt | Am besten überprüfen Sie sowohl Änderungen am benutzerdefinierten Code als auch grundlegende Änderungen wie das Neuanordnen von Elementen oder das Ersetzen von Text |
| VEC-basierte Aktivitäten werden bei SPA-Ansichtsänderungen korrekt dargestellt | Nur für SPA-Implementierungen anwendbar |
| Formularbasierte Aktivitäten werden ordnungsgemäß gerendert | Gilt nur für bestimmte Implementierungen. Für das Rendern von formularbasierten Aktivitäten ist benutzerdefinierter Code erforderlich, der at.js ähnelt. |
| Aktivitäten, die Umleitungen verwenden, funktionieren ordnungsgemäß | Umleitungen werden unterstützt, wenn sowohl die Quell- als auch die Zielseite Platform Web SDK verwenden. Eine Target-Umleitung von einer at.js-Seite zu einer Platform Web SDK-Seite oder umgekehrt wird nicht unterstützt. |
| Aktivitäten, die Remote-Angebote verwenden, funktionieren ordnungsgemäß | Nicht üblich. Prüfen Sie Ihren Target-Angebotsbestand auf Remote-Angebote. |
| Flackern wird entsprechend gemildert | Die Handhabung von Flackern ist optional, aber stellen Sie sicher, dass alle vorhandenen Korrekturtaktiken wie erwartet funktionieren, um eine optimale Seitenleistung und ein optimales Benutzererlebnis zu erzielen |
| QA-Links funktionieren erwartungsgemäß. | Wenn dies nicht funktioniert, überprüfen Sie, ob die Datei web.webPageDetails.URL genau mit der URL im Browser übereinstimmt. |
| Alle häufig verwendeten Angebotstypen werden wie erwartet gerendert |  |

## Reporting

| Validierungselement | Anmerkungen |
|---|---|
| Besucher werden VEC-basierten Aktivitäten zugeordnet | Am besten überprüfen Sie, ob das Reporting sowohl für Seitenladeänderungen als auch für Änderungen an der SPA-Ansicht erwartungsgemäß funktioniert |
| Besucher werden formularbasierten Aktivitäten zugeordnet | Je nach Rendering-Ansatz kann Ihre Implementierung benutzerdefinierten Code erfordern, um ein `decisioning.propositionDisplay` Ereignis auszuführen |
| Standard-Konversionsziele werden ordnungsgemäß erfasst | Gilt entweder für Target oder Analytics als Berichtsquelle |
| Auftragskonversionen und -details werden ordnungsgemäß erfasst | Überprüfen des Auditberichts |
| Klick-Tracking-Konversionen werden ordnungsgemäß erfasst |  |
| Benutzerdefinierte Konversionsziele werden ordnungsgemäß erfasst | Beispielsweise Konversionsziele, die aus at.js-`trackEvent` oder -`sendNotifications` migriert wurden und häufig mit dem Ziel „Angezeigte Mbox“ verwendet werden |

## Zielgruppen und Profilskripte

| Validierungselement | Anmerkungen |
|---|---|
| Zielgruppen, die in Live-Aktivitäten verwendet werden, sind mit Platform Web SDK kompatibel | Zielgruppen, die die Komponente „Benutzerdefiniert“ (Mbox-Parameter) verwenden, müssen aktualisiert werden, um XDM-Attribute einzuschließen |
| Alle Profilskripte sind mit Platform Web SDK kompatibel | Alle Profilskripte, die Mbox-Parameter verwenden, müssen aktualisiert werden, damit sie XDM-Attribute enthalten |
| Rückgabe von Aktivitäten für Target-Zielgruppen | Es wird empfohlen, eine End-to-End-Validierung für Zielgruppen durchzuführen, die Sie ändern, um sie mit Platform Web SDK kompatibel zu machen |
| Profilskripte werden erwartungsgemäß ausgewertet | Anzeigen von Edge-Ablaufverfolgungen im Debugger |

## Integrationen mit Adobe-Anwendungen

| Validierungselement | Anmerkungen |
|---|---|
| Rückgabe von Aktivitäten für Experience Cloud-Zielgruppen | Beispielsweise ein Segment, das aus Adobe Analytics veröffentlicht wurde |
| Rückgabe von Aktivitäten für Experience Platform-Zielgruppen | Gilt nur, wenn Sie über eine Lizenz für eine Experience Platform-basierte Anwendung wie RTCDP verfügen |
| Aktivitätenrückgabe für Audience Manager-Zielgruppen | Beispiel: ein Segment basierend auf dem Besuch einer bestimmten Seite |
| Target-Aktivitätsdaten werden in Analysis Workspace angezeigt | Gilt für Aktivitäten, die Adobe Analytics als Berichtsquelle verwenden |

## Integrationen mit Anwendungen von Drittanbietern

| Validierungselement | Anmerkungen |
|---|---|
| Daten des Antwort-Tokens werden ordnungsgemäß an Drittanbieterprogramme weitergeleitet | Integrationsansätze können variieren, aber eine gängige Methode ist die Verwendung von Target-Antwort-Token zur Weitergabe von Aktivitäts- und Erlebnisinformationen an andere Analytics-Tools wie Google Analytics |
| Informationen von Drittanbietern werden entweder als XDM- oder Profildaten weitergegeben | Alle relevanten Informationen von Dritten sollten bei `sendEvent` Aufrufen an Target weitergeleitet werden |

Nachdem Sie die oben genannten Validierungsschritte ausgeführt haben, können Sie sich darauf verlassen, dass die Platform Web SDK-Implementierung bereit für den Wechsel zur Produktionsumgebung ist.

Erfahren Sie als Nächstes, wie [&#x200B; eine Target-Implementierung mithilfe von Platform Web SDK &#x200B;](debugging.md).

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=de#M463) posten.
