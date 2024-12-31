---
title: Planung - Migrieren von Target von at.js 2.x zu Web SDK
description: Erfahren Sie, wie Sie Ihre Adobe Target-Implementierung von at.js 2.x auf Adobe Experience Platform Web SDK planen.
exl-id: 0e8f9cde-f361-4f69-886d-aad3074cd9b2
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 1%

---

# Planen der Migration von at.js zu Platform Web SDK

Bevor Sie auf Ihrer Site ein Upgrade auf Platform Web SDK durchführen, sollten Sie Ihre aktuelle Implementierung bewerten.

## Bewertung der aktuellen at.js-Implementierung

Der erste Schritt für eine erfolgreiche Migration besteht darin, Ihre aktuelle at.js-Target-Implementierung genau zu verstehen. Es gibt Funktionen und benutzerdefinierten Code, den Sie verwenden können und der aktualisiert werden muss. Berücksichtigen Sie bei der Bewertung Folgendes:

### Welche Funktionen werden unterstützt?

Platform Web SDK wird ständig weiterentwickelt und regelmäßig Funktionen und Erweiterungen hinzugefügt. Wenn Sie Ihre aktuelle at.js-Implementierung bewerten, finden Sie auf der Seite [Unterstützte Anwendungsfälle](https://github.com/orgs/adobe/projects/18/views/1) die neuesten Informationen.

### Welche Funktionen nutzt ihr heute?

Platform Web SDK ist eine neue Bibliothek, die alle Adobe-Lösungen für die Websites in einer einzigen SDK zusammenfasst. Dies ermöglicht eine engere Integration und neue, für Adobe Experience Platform einzigartige Funktionen. Das bedeutet jedoch auch, dass at.js-Funktionen nicht abwärtskompatibel mit Platform Web SDK sind. Beachten Sie bei der Bewertung Ihrer aktuellen Implementierung Folgendes:

- at.js-Funktionen wie `getOffer()` und `applyOffer()`
- Änderungen an den globalen Einstellungen von Target
- Integration in Adobe Analytics
- Verwendung eines Flimmerschutzskripts
- Verwendung von Antwort-Token
- Verwendung von Mbox-, Profil- und Entitätsparametern
- Benutzerdefinierter Code, der für Ihre Implementierung eindeutig ist

### Welchen Migrationsansatz wählen Sie?

Nachdem Sie Ihre at.js-Implementierung überarbeitet haben, müssen Sie einen Migrationsansatz festlegen. Es gibt zwei Möglichkeiten:

- Alle Adobe-Anwendungen gleichzeitig über die gesamte Website migrieren
- Seite für Seite migrieren

Da Platform Web SDK mehrere Adobe-Anwendungen kombiniert und ermöglicht, müssen Sie die Target-Migration anderer Adobe-Anwendungen wie Analytics und Audience Manager koordinieren. Alle Adobe-Bibliotheken auf einer bestimmten Seite sollten gleichzeitig migriert werden. Eine gemischte Implementierung von Platform Web SDK for Target und AppMeasurement for Analytics auf einer bestimmten Seite wird nicht unterstützt. Es wird jedoch eine gemischte Implementierung über verschiedene Seiten hinweg unterstützt, z. B. Platform Web SDK auf Seite A und at.js mit AppMeasurement auf Seite B.

Bei der Migration sollten Sie planen, den Prozess Ihres Unternehmens zum Testen und Freigeben von neuem Code zu befolgen und Dinge wie Entwicklung, QS und Staging-Umgebungen zu verwenden, bevor Sie die Veröffentlichung in der Produktion durchführen.

>[!CAUTION]
>
>Umleitungsangebote werden bei seitenweisen Migrationen nicht unterstützt, wenn von einer Seite mit einer Bibliothek zu einer Seite mit einer anderen Bibliothek umgeleitet wird


Überprüfen Sie anschließend den detaillierten [Vergleich von at.js mit Platform Web SDK](detailed-comparison.md), um ein besseres Verständnis der technischen Unterschiede zu erhalten und Bereiche zu ermitteln, die zusätzliche Aufmerksamkeit erfordern.

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
