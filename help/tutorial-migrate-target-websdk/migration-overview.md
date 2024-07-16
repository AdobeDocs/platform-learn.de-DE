---
title: Migrationsübersicht | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie mehr über die wichtigsten Unterschiede zwischen at.js und dem Platform Web SDK und wie Sie Ihren Migrationsaufwand planen.
exl-id: a8ed78e4-c8c2-4505-b4b5-e5d508f5ed87
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 1%

---

# Übersicht über die Migration von &quot;at.js&quot;zu Platform Web SDK

Der Aufwand für die Migration von at.js zum Platform Web SDK hängt von der Komplexität Ihrer aktuellen Implementierung und den verwendeten Produktfunktionen ab.

Unabhängig davon, wie einfach oder komplex Ihre Implementierung ist, ist es wichtig, den aktuellen Status vor der Migration vollständig zu verstehen. Dieses Handbuch hilft Ihnen dabei, die Komponenten Ihrer aktuellen Implementierung aufzuschlüsseln und einen verwaltbaren Plan für die Migration der einzelnen Elemente zu entwickeln.

Der Migrationsprozess umfasst die folgenden wichtigen Schritte:

1. Ihre aktuelle Implementierung bewerten und einen Migrationsansatz festlegen
1. Einrichten der Anfangskomponenten für die Verbindung mit dem Adobe Experience Platform-Edge Network
1. Aktualisieren der Basisimplementierung, um at.js durch das Platform Web SDK zu ersetzen
1. Verbessern Sie die Implementierung des Platform Web SDK für Ihre spezifischen Anwendungsfälle. Dies kann die Übergabe zusätzlicher Parameter, die Berücksichtigung von Änderungen an der Einzelseiten-App (SPA), die Verwendung von Antwort-Token und mehr umfassen.
1. Aktualisieren von Objekten in der Target-Oberfläche, z. B. Profilskripten, Aktivitäten und Zielgruppendefinitionen
1. Validieren Sie die endgültige Implementierung, bevor Sie den Wechsel in Ihrer Produktionsumgebung vornehmen.

## Wichtige Unterschiede zwischen at.js und Platform Web SDK

Bevor Sie mit dem Migrationsprozess beginnen, müssen Sie die Unterschiede zwischen at.js und dem Platform Web SDK kennen.

### Betriebsunterschiede

Das Platform Web SDK kombiniert die Funktionalität mehrerer Adobe-Anwendungen in einer Bibliothek. Dieser einheitliche Ansatz bedeutet, dass Sie die Verantwortung und Prozesse der Teams für eine gesunde Implementierung in Betracht ziehen sollten.

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Eigentümerschaft | Die at.js-Bibliothek ist unabhängig von anderen Anwendungsbibliotheken. Anpassungen und das Eigentum an diesen unterschiedlichen Bibliotheken können sich an verschiedenen Teams in der Organisation ausrichten. | Die Platform Web SDK-Bibliothek und die übergebenen Daten sind für alle Adobe-Anwendungen vereinheitlicht. Die Eigentümerschaft der Platform Web SDK-Implementierung sollte die Stakeholder aller nachgelagerten Anwendungen repräsentieren. |
| Wartung | Separate Teams können an Implementierungsverbesserungen für jede Adobe-Anwendung arbeiten, z. B. Target und Analytics. | Idealerweise sollte ein einzelnes Team für Verbesserungen verantwortlich sein, die sich auf die Implementierung des Platform Web SDK auswirken. |
| Prozess | Änderungen an einer Target-Implementierung folgen möglicherweise einem Prozess, der im Vergleich zu anderen Anwendungen wie Analytics andere Cadence- oder QA-Anforderungen aufweist. | Änderungen an einer Platform Web SDK-Implementierung sollten alle nachgelagerten Anwendungen berücksichtigen und der QA- und Veröffentlichungsprozess sollte entsprechend angepasst werden. |
| Zusammenarbeit | Target-spezifische Daten können direkt in den Target-Aufrufen übergeben werden. Abhängig von der Implementierung können zusätzliche Target-Aufrufe auftreten. Dies hat keine direkten Auswirkungen auf Adobe Analytics-Daten, und die Koordinierung mit dem Analyseteam ist nicht so wichtig. | Daten, die in Platform Web SDK-Aufrufen übergeben werden, können sowohl an Target als auch an Analytics weitergeleitet werden. Eine Koordinierung zwischen Teams ist erforderlich, um sicherzustellen, dass Änderungen keine negativen Auswirkungen auf eine bestimmte Anwendung haben. |

### Technische Unterschiede

Das Platform Web SDK ist keine Weiterentwicklung der Target at.js-Bibliothek. Es handelt sich um einen neuen und einheitlichen Ansatz für die Implementierung aller Adobe-Anwendungen für den Webkanal. Es gibt mehrere technische Unterschiede, die Sie kennen sollten.

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Bibliotheksfunktionen | Von at.js bereitgestellte Target-Funktionen. Integrationen mit anderen von Visitor.js und AppMeasurement.js bereitgestellten Anwendungen | Funktionen für alle Adobe-Anwendungen, die von einer einzigen Platform Web SDK-Bibliothek bereitgestellt werden: &quot;legate.js&quot; |
| Performance | at.js ist eine von mehreren Bibliotheken, die für eine ordnungsgemäße anwendungsübergreifende Integration geladen werden müssen. Dies führt zu weniger als der optimalen Ladezeit. | Das Platform Web SDK ist eine einfache Bibliothek, die die Notwendigkeit mehrerer anwendungsspezifischer Bibliotheken beseitigt, was zu einer besseren Seitenladeleistung führt. |
| Anfragen | Separate Aufrufe für jede Adobe-Anwendung. Target-Aufrufe sind weitgehend unabhängig von anderen Netzwerkaufrufen. | Ein Einzelaufruf für alle Adobe-Anwendungen. Änderungen an den in diesen Aufrufen übergebenen Daten können sich auf mehrere nachgelagerte Anwendungen auswirken. |
| Auftrag laden | Eine ordnungsgemäße Integration mit anderen Adobe-Applikationen erfordert eine bestimmte Ladereihenfolge von Bibliotheken und Netzwerkaufrufen. | Eine ordnungsgemäße Integration beruht nicht auf der Zuordnung von Daten aus unterschiedlichen anwendungsspezifischen Netzwerkaufrufen. Daher ist die Ladereihenfolge kein Problem. |
| Edge Network | Verwendet das Adobe Experience Cloud-Edge Network (tt.omtrdc.net), optional mit einem für Target spezifischen CNAME. | Verwendet das Adobe Experience Platform-Edge Network (edge.adobedc.net), optional mit einem einzigen CNAME. |
| Grundlegende Terminologie | &quot;at.js&quot;-Benennung: <br> - `mbox` <br> - `pageLoad` Ereignis (globale Mbox) <br> - `offer` | Platform Web SDK-Entsprechung: <br> - `decisionScope` <br> - `__view__` decisionScope <br> - `proposition` |

### Videoüberblick

Das folgende Video bietet einen Überblick über das Adobe Experience Platform Web SDK und Adobe Experience Platform-Edge Network.

>[!VIDEO](https://video.tv.adobe.com/v/34141/?learn=on)

Nachdem Sie nun die allgemeinen Unterschiede zwischen at.js und dem Platform Web SDK kennen, können Sie die Migration [planen](plan-migration.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
