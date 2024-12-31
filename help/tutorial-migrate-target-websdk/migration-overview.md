---
title: Migrationsübersicht - Migrieren von Target aus at.js 2.x nach Web SDK
description: Erfahren Sie mehr über die wichtigsten Unterschiede zwischen at.js und Platform Web SDK und wie Sie Ihren Migrationsaufwand planen können.
exl-id: a8ed78e4-c8c2-4505-b4b5-e5d508f5ed87
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 1%

---

# Übersicht über die Migration von at.js zu Platform Web SDK

Der Aufwand für die Migration von at.js zu Platform Web SDK hängt von der Komplexität Ihrer aktuellen Implementierung und der verwendeten Produktfunktionen ab.

Unabhängig davon, wie einfach oder komplex Ihre Implementierung ist, ist es wichtig, Ihren aktuellen Status vor der Migration vollständig zu verstehen. Dieser Leitfaden hilft Ihnen, die Komponenten Ihrer aktuellen Implementierung aufzuschlüsseln und einen überschaubaren Plan zur Migration der einzelnen Komponenten zu entwickeln.

Der Migrationsprozess umfasst die folgenden wichtigen Schritte:

1. Bewertung der aktuellen Implementierung und Festlegung eines Migrationsansatzes
1. Einrichten der Anfangskomponenten für die Verbindung mit dem Adobe Experience Platform-Edge Network
1. Aktualisieren Sie die grundlegende Implementierung, um at.js durch Platform Web SDK zu ersetzen.
1. Verbessern Sie die Implementierung von Platform Web SDK für Ihre spezifischen Anwendungsfälle. Dazu kann es gehören, zusätzliche Parameter zu übergeben, Änderungen an der Ansicht der Single Page App (SPA) zu berücksichtigen, Antwort-Token zu verwenden und vieles mehr.
1. Aktualisieren von Objekten in der Target-Oberfläche, z. B. Profilskripte, Aktivitäten und Zielgruppendefinitionen
1. Validieren Sie die endgültige Implementierung, bevor Sie den Wechsel in Ihrer Produktionsumgebung vornehmen

## Hauptunterschiede zwischen at.js und Platform Web SDK

Bevor Sie mit dem Migrationsprozess beginnen, müssen Sie die Unterschiede zwischen at.js und Platform Web SDK verstehen.

### Operative Unterschiede

Die Platform Web SDK kombiniert die Funktionalität mehrerer Adobe-Anwendungen in einer einzigen Bibliothek. Dieser einheitliche Ansatz bedeutet, dass Sie teamübergreifende Verantwortlichkeiten und Prozesse in Betracht ziehen sollten, um eine ordnungsgemäße Implementierung sicherzustellen.

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Eigentümerschaft | Die at.js-Bibliothek ist unabhängig von anderen Anwendungsbibliotheken. Anpassungen und Eigentümerschaft dieser unterschiedlichen Bibliotheken können an verschiedene Teams in der Organisation angepasst werden. | Die Platform Web SDK-Bibliothek und die übergebenen Daten werden für alle Adobe-Anwendungen vereinheitlicht. Die Eigentümerschaft der Platform Web SDK-Implementierung sollte die Stakeholder aller nachgelagerten Anwendungen repräsentieren. |
| Wartung | Separate Teams können an Implementierungsverbesserungen für jede Adobe-Anwendung arbeiten, z. B. Target und Analytics. | Idealerweise sollte ein einzelnes Team für Verbesserungen verantwortlich sein, die sich auf die Implementierung von Platform Web SDK auswirken. |
| Prozess | Änderungen an einer Target-Implementierung können auf einen Prozess folgen, der im Vergleich zu anderen Programmen wie Analytics eine andere Kadenz oder andere QS-Anforderungen hat. | Bei Änderungen an einer Platform Web SDK-Implementierung sollten alle nachgelagerten Anwendungen berücksichtigt und der QA- und Veröffentlichungsprozess entsprechend angepasst werden. |
| Zusammenarbeit | Target-spezifische Daten können direkt in den Target-Aufrufen übergeben werden. Je nach Implementierung können zusätzliche Target-Aufrufe auftreten. Dies hat keine direkten Auswirkungen auf die Daten von Adobe Analytics, und die Koordinierung mit dem Analytics-Team ist nicht so wichtig. | Daten, die in Platform Web SDK-Aufrufen übergeben werden, können sowohl an Target als auch an Analytics weitergeleitet werden. Um sicherzustellen, dass sich Änderungen nicht negativ auf ein bestimmtes Programm auswirken, ist eine Koordinierung zwischen den Teams erforderlich. |

### Technische Unterschiede

Die Platform Web SDK ist keine Weiterentwicklung der Target at.js-Bibliothek. Dies ist ein neuer und einheitlicher Ansatz zur Implementierung aller Adobe-Anwendungen für den Web-Kanal. Es gibt mehrere technische Unterschiede, die zu beachten sind.

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Bibliotheksfunktion | Target-Funktion, bereitgestellt von at.js. Integrationen mit anderen Programmen von Visitor.js und AppMeasurement.js | Funktionalität für alle Adobe-Anwendungen, die von einer einzigen Platform Web SDK-Bibliothek bereitgestellt werden: alloy.js |
| Performance | at.js ist eine von mehreren Bibliotheken, die für eine ordnungsgemäße programmübergreifende Integration geladen werden müssen. Dies führt zu einer kürzeren als der optimalen Ladezeit. | Platform Web SDK ist eine einzelne, einfache Bibliothek, die mehrere programmspezifische Bibliotheken überflüssig macht, was zu einer besseren Seitenladeleistung führt. |
| Anfragen | Separate Aufrufe für jede Adobe-Anwendung. Target-Aufrufe sind weitgehend unabhängig von anderen Netzwerkaufrufen. | Ein Aufruf für alle Adobe-Anwendungen. Änderungen an den in diesen Aufrufen übergebenen Daten können sich auf mehrere nachgelagerte Anwendungen auswirken. |
| Ladereihenfolge | Für eine ordnungsgemäße Integration in andere Adobe-Anwendungen ist eine bestimmte Lastreihenfolge von Bibliotheken und Netzwerkaufrufen erforderlich. | Die ordnungsgemäße Integration beruht nicht auf dem Zusammenfügen von Daten aus unterschiedlichen anwendungsspezifischen Netzwerkaufrufen. Daher ist die Ladereihenfolge nicht von Belang. |
| Edge Network | Verwendet das Adobe Experience Cloud-Edge Network (tt.omtrdc.net), optional mit einem Target-spezifischen CNAME. | Verwendet das Adobe Experience Platform-Edge Network (edge.adobedc.net), optional mit einem einzigen CNAME. |
| Allgemeine Terminologie | at.js-Benennung: <br> - `mbox` <br> - `pageLoad` Ereignis (globale Mbox) <br> - `offer` | Platform Web SDK Entsprechung: <br> - `decisionScope` <br> - `__view__` decisionScope <br> - `proposition` |

### Videoüberblick

Das folgende Video bietet einen Überblick über das Adobe Experience Platform Web SDK- und Adobe Experience Platform-Edge Network.

>[!VIDEO](https://video.tv.adobe.com/v/34141/?learn=on)

Nachdem Sie nun die allgemeinen Unterschiede zwischen at.js und Platform Web SDK kennen, können Sie [die Migration planen](plan-migration.md).

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
