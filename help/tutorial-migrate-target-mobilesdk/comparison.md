---
title: Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung
description: Erfahren Sie mehr über die Unterschiede zwischen der Target-Erweiterung und der Decisioning-Erweiterung, einschließlich Funktionen, Einstellungen und Datenfluss.
exl-id: 6c854049-4126-45cf-8b2b-683cf29549f3
source-git-commit: 2ebad2014d4c29a50af82328735258958893b42c
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 3%

---

# Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung

Die Adobe Journey Optimizer - Decisioning-Erweiterung unterscheidet sich von der Adobe Target-Erweiterung für Mobile Apps. Die folgenden Tabellen dienen als Referenz bei der Bewertung von Bereichen Ihrer Implementierung, auf die Sie sich während des Migrationsprozesses möglicherweise konzentrieren müssen.

Nachdem Sie die folgenden Informationen durchgelesen und Ihre aktuelle Implementierung der technischen Target-Erweiterung bewertet haben, sollten Sie Folgendes verstehen:

- Welche Target-Funktionen von Adobe Journey Optimizer unterstützt werden - Decisioning
- Welche Adobe Target-Erweiterungsfunktionen über Adobe Journey Optimizer verfügen - Entscheidungsäquivalente
- Anwenden von Target-Einstellungen mit Adobe Journey Optimizer - Decisioning
- Fluss der Daten mithilfe der Adobe Journey Optimizer - Decisioning-Erweiterung

## Operative Unterschiede

| | Target-Erweiterung | Decisioning-Erweiterung |
|---|---|---|
| Prozess | Änderungen an einer Target-Implementierung können auf einen Prozess folgen, der im Vergleich zu anderen Programmen wie Analytics eine andere Kadenz oder andere QS-Anforderungen hat. | Bei Änderungen an einer Implementierung der Decisioning-Erweiterung sollten alle nachgelagerten Anwendungen berücksichtigt und der QA- und Veröffentlichungsprozess entsprechend angepasst werden. |
| Zusammenarbeit | Target-spezifische Daten können direkt in den Target-Aufrufen übergeben werden. Wenn die Target-Berichtsquelle Adobe Analytics (A4T) ist, können Target-spezifische Daten auch an Adobe Analytics übergeben werden, wenn geeignete Tracking-Methoden in der Target-Erweiterung für die Anzeige von Target-Inhalten und die Interaktion aufgerufen werden. | Daten, die in den Decisioning-Erweiterungsaufrufen übergeben werden, können sowohl an Target als auch an Analytics weitergeleitet werden, wenn die Target-Berichtsquelle Adobe Analytics (A4T) ist, Adobe Analytics im Daten-Stream aktiviert ist und geeignete Tracking-Methoden in der Decisioning-Erweiterung aufgerufen werden, wenn Target-Inhalte angezeigt werden und mit ihnen interagiert wird. |

## Grundlegende Unterschiede

| | Target-Erweiterung | Decisioning-Erweiterung |
|---|---|---|
| Abhängigkeiten | Hängt nur von Mobile Core SDK ab | Hängt von Mobile Core und Edge Network SDK ab |
| Bibliotheksfunktion | Unterstützt nur das Abrufen von Inhalten aus Adobe Target | Unterstützung für das Abrufen von Inhalten aus Adobe Target und Offer Decisioning |
| Anfragen | Target-Aufrufe sind weitgehend unabhängig von anderen Netzwerkaufrufen | Target-Netzwerkaufrufe werden zusammen mit Netzwerkaufrufen für andere Edge-basierte Lösungen wie Messaging in Edge SDK in die Warteschlange gestellt und seriell ausgeführt. |
| Edge Network | Verwendet den Target-Serverwert oder die Adobe Experience Cloud Edge Network mit dem Clientcode (clientcode.tt.omtrdc.net), die beide in der [Target-Konfiguration](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) in der Datenerfassungs-UI angegeben sind | Verwendet die Edge-Netzwerkdomäne, die in der Konfiguration von Adobe Experience Platform [Edge Network ](https://developer.adobe.com/client-sdks/edge/edge-network/#configure-the-edge-network-extension-in-data-collection-ui) der Datenerfassungs-Benutzeroberfläche angegeben ist. |
| Allgemeine Terminologie | mbox, targetParameters | Entscheidungsumfang, Zuordnung (Android)/Wörterbuch (iOS) für Zielparameter |
| Standardinhalt | Ermöglicht die Übergabe Client-seitiger Standardinhalte in TargetRequest, die zurückgegeben wird, wenn der Netzwerkaufruf fehlschlägt oder zu einem Fehler führt. | Ermöglicht nicht die Übergabe Client-seitiger Standardinhalte. Gibt keinen Inhalt zurück, wenn der Netzwerkaufruf fehlschlägt oder zu einem Fehler führt. |
| Zielparameter | Ermöglicht die Übergabe globaler TargetParameters pro Anfrage und verschiedener TargetParameters pro Mbox | Ermöglicht die Übergabe globaler TargetParameters nur pro Anfrage |



## Funktionsvergleich

| Funktion | Target-Erweiterung | Decisioning-Erweiterung (Target über Edge) |
|---|---|---|
| Vorheriger Abrufmodus | Unterstützt | Unterstützt |
| Ausführungsmodus | Unterstützt | Nicht unterstützt |
| Benutzerdefinierte Parameter | Unterstützt | Unterstützt* |
| Profilparameter | Unterstützt | Unterstützt* |
| Entitätsparameter | Unterstützt | Unterstützt* |
| Zielgruppen | Unterstützt | Unterstützt |
| Real-Time CDP-Zielgruppen | Nicht unterstützt | Unterstützt |
| Real-Time CDP-Attribute | Nicht unterstützt | Unterstützt |
| Lebenszyklusmetriken | Unterstützt | Unterstützt durch Datenerfassungsregeln |
| thirdPartyId (mbox3rdPartyId) | Unterstützt | Unterstützt über Identity Map und Target Third-Party-ID-Namespace im Datenstrom |
| Benachrichtigungen (Anzeige, Klick) | Unterstützt | Unterstützt |
| Antwort-Token | Unterstützt | Unterstützt |
| Mobile-Vorschau (QA-Modus) | Unterstützt | Eingeschränkter Support mit Assurance |

>[!IMPORTANT]
>
> \* Die in einer Anfrage gesendeten Parameter gelten für alle Bereiche in der Anfrage. Wenn Sie für verschiedene Bereiche unterschiedliche Parameter festlegen müssen, müssen Sie zusätzliche Anfragen stellen.



## Bemerkenswerte Hinweise

>[!NOTE]
>
>Behalten Sie die Konfiguration und die Einstellungen für Target-Erweiterungs-Tags bei, auch nachdem Sie Ihren App-Code zur Decisioning-Erweiterung migriert haben. Dadurch wird sichergestellt, dass Target auch für Kunden funktioniert, die die App noch nicht auf die neue Version aktualisiert haben.
>
>Wenn Sie die Analytics for Target-Integration (A4T) verwenden, müssen Sie auch Ihre Analytics-Implementierung mit der Edge Bridge-Erweiterung migrieren, während Sie gleichzeitig Ihre Target-Implementierung in die Decisioning-Erweiterung migrieren.





>[!IMPORTANT]
>
> Behalten Sie die Einstellungen der Target-Erweiterung bei, auch nachdem Sie Ihren App-Code zur Decisioning-Erweiterung migriert haben. Dadurch wird sichergestellt, dass Target auch weiterhin für Benutzende funktioniert, die ihre App noch nicht aktualisiert haben.

## Systemdiagramm der Decisioning-Erweiterung

Das folgende Diagramm soll Ihnen dabei helfen, den Datenfluss mithilfe der Adobe Journey Optimizer - Decisioning-Erweiterung zu verstehen.

![Adobe Target Edge Decisioning mit Client-seitigem Mobile SDK](assets/diagram.png)


>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484?profile.language=de#M625) posten.
