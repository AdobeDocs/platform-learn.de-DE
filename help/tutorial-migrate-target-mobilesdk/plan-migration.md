---
title: Planen der Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie mehr über die wichtigsten Unterschiede zwischen at.js und Platform Web SDK und wie Sie Ihren Migrationsaufwand planen können.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
source-git-commit: f3fd5f45412900dcb871bc0b346ce89108fa8913
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Migration planen

Der Aufwand für die Migration von der Target- zur Decisioning-Erweiterung hängt von der Komplexität Ihrer aktuellen Implementierung und der verwendeten Produktfunktionen ab.

Unabhängig davon, wie einfach oder komplex Ihre Implementierung ist, ist es wichtig, Ihren aktuellen Status vor der Migration vollständig zu verstehen. Dieser Leitfaden hilft Ihnen, die Komponenten Ihrer aktuellen Implementierung aufzuschlüsseln und einen überschaubaren Plan zur Migration der einzelnen Komponenten zu entwickeln.

Der Migrationsprozess umfasst die folgenden wichtigen Schritte:

1. Bewertung der aktuellen Implementierung und Festlegung eines Migrationsansatzes
1. Einrichten der Anfangskomponenten für die Verbindung mit dem Adobe Experience Platform-Edge Network
1. Aktualisieren Sie die grundlegende Implementierung, um die Target- und die Decisioning-Erweiterung zu ersetzen
1. Optimieren Sie die Implementierung von SDK Optimieren für Ihre spezifischen Anwendungsfälle. Dazu kann es gehören, zusätzliche Parameter zu übergeben, Antwort-Token zu verwenden und vieles mehr.
1. Aktualisieren von Objekten in der Target-Oberfläche, z. B. Profilskripte, Aktivitäten und Zielgruppendefinitionen
1. Validieren Sie die endgültige Implementierung, bevor Sie den Wechsel in Ihrer Produktionsumgebung vornehmen

## Hauptunterschiede zwischen der Target- und der Decisioning-Erweiterung

Bevor Sie mit dem Migrationsprozess beginnen, müssen Sie die Unterschiede zwischen der Target-Erweiterung und der Decisioning-Erweiterung verstehen.

### Operative Unterschiede

| | Target at.js 2.x | Platform Web-SDK |
|---|---|---|
| Prozess | Änderungen an einer Target-Implementierung können auf einen Prozess folgen, der im Vergleich zu anderen Programmen wie Analytics eine andere Kadenz oder andere QS-Anforderungen hat. | Bei Änderungen an einer Implementierung der Decisioning-Erweiterung sollten alle nachgelagerten Anwendungen berücksichtigt und der QA- und Veröffentlichungsprozess entsprechend angepasst werden. |
| Zusammenarbeit | Target-spezifische Daten können direkt in den Target-Aufrufen übergeben werden. Wenn die Target-Berichtsquelle Adobe Analytics ist, können Target-spezifische Daten auch an Adobe Analytics übergeben werden, wenn geeignete Tracking-Methoden in der Target-Erweiterung für die Anzeige von Target-Inhalten und die Interaktion aufgerufen werden. | In Decisioning-Erweiterungsaufrufen übergebene Daten können sowohl an Target als auch an Analytics weitergeleitet werden, wenn die Target-Berichtsquelle Adobe Analytics ist, Adobe Analytics im Daten-Stream aktiviert ist und geeignete Tracking-Methoden in der Decisioning-Erweiterung aufgerufen werden, wenn Target-Inhalte angezeigt werden und mit ihnen interagiert wird. |

### Technische Unterschiede

| | Target-Erweiterung | Decisioning-Erweiterung |
|---|---|---|
| Abhängigkeiten | Hängt nur von Mobile Core SDK ab | Hängt von Mobile Core und Edge Network SDK ab |
| Bibliotheksfunktion | Unterstützt nur das Abrufen von Inhalten aus Adobe Target | Unterstützung für das Abrufen von Inhalten von Adobe Target und Offer decisioning |
| Anfragen | Target-Aufrufe sind weitgehend unabhängig von anderen Netzwerkaufrufen | Target-Netzwerkaufrufe werden zusammen mit Netzwerkaufrufen für andere Edge-basierte Lösungen wie Messaging in Edge SDK in die Warteschlange gestellt und seriell ausgeführt. |
| Edge Network | Verwendet den Target-Serverwert oder das Adobe Experience Cloud-Edge Network mit dem Clientcode (clientcode.tt.omtrdc.net), die beide in der [Target-Konfiguration](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) in der Datenerfassungs-UI angegeben sind | Verwendet die Edge-Netzwerkdomäne, die in der Adobe Experience Platform-[Edge Network-Konfiguration ](https://developer.adobe.com/client-sdks/edge/edge-network/#configure-the-edge-network-extension-in-data-collection-ui) der Datenerfassungs-Benutzeroberfläche angegeben ist. |
| Allgemeine Terminologie | mbox, targetParameters | Entscheidungsumfang, Zuordnung (Android)/Wörterbuch (iOS) für Zielparameter |
| Standardinhalt | Ermöglicht die Übergabe Client-seitiger Standardinhalte in TargetRequest, die zurückgegeben wird, wenn der Netzwerkaufruf fehlschlägt oder zu einem Fehler führt. | Ermöglicht nicht die Übergabe Client-seitiger Standardinhalte. Gibt keinen Inhalt zurück, wenn der Netzwerkaufruf fehlschlägt oder zu einem Fehler führt. |
| Zielparameter | Ermöglicht die Übergabe globaler TargetParameters pro Anfrage und verschiedener TargetParameters pro Mbox | Ermöglicht die Übergabe globaler TargetParameters nur pro Anfrage |

Überprüfen Sie anschließend den detaillierten [Vergleich der Target- und der Decisioning-Erweiterung](detailed-comparison.md), um die technischen Unterschiede besser zu verstehen und Bereiche zu identifizieren, die einen zusätzlichen Fokus erfordern.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
