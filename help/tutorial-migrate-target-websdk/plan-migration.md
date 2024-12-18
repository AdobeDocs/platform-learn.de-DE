---
title: Planung - Migration von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie für Ihre Adobe Target-Implementierung von at.js 2.x auf das Adobe Experience Platform Web SDK planen.
exl-id: 0e8f9cde-f361-4f69-886d-aad3074cd9b2
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 1%

---

# Migration von at.js zum Platform Web SDK planen

Bevor Sie auf Ihre Site ein Upgrade auf das Platform Web SDK durchführen, sollten Sie Ihre aktuelle Implementierung bewerten.

## Aktuelle at.js-Implementierung bewerten

Der erste Schritt zu einer erfolgreichen Migration besteht darin, ein solides Verständnis Ihrer aktuellen at.js-Target-Implementierung zu haben. Es gibt Funktionen, Funktionen und benutzerdefinierten Code, die Sie verwenden können und die aktualisiert werden müssen. Beachten Sie Folgendes bei der Beurteilung:

### Welche Funktionen werden unterstützt?

Das Platform Web SDK befindet sich in kontinuierlicher aktiver Entwicklung und es werden regelmäßig Funktionen und Verbesserungen hinzugefügt. Aktuelle Informationen zur at.js-Implementierung finden Sie auf der Seite [Unterstützte Anwendungsbeispiele](https://github.com/orgs/adobe/projects/18/views/1) .

### Welche Funktionen verwenden Sie heute?

Platform Web SDK ist eine neue Bibliothek, die alle Adobe-Lösungen für die Websites in einem einzigen SDK zusammenfasst. Dies ermöglicht eine engere Integration und ermöglicht neue Funktionen, die speziell für Adobe Experience Platform geeignet sind. Das bedeutet jedoch auch, dass at.js-Funktionen nicht abwärtskompatibel mit dem Platform Web SDK sind. Beachten Sie bei der Bewertung Ihrer aktuellen Implementierung Folgendes:

- &quot;at.js&quot;-Funktionen wie `getOffer()` und `applyOffer()`
- Änderungen an den globalen Einstellungen von Target
- Integration in Adobe Analytics
- Verwendung eines Flackerminderungsskripts
- Verwenden von Antwort-Token
- Verwendung von Mbox-, Profil- und Entitätsparametern
- Benutzerspezifischer Code für Ihre Implementierung

### Welchen Migrationsansatz wählen Sie?

Nachdem Sie Ihre at.js-Implementierung erneut besucht haben, müssen Sie einen Migrationsansatz festlegen. Es gibt zwei Optionen:

- Migrieren Sie alle Adobe-Anwendungen gleichzeitig auf der gesamten Site.
- Auf Seitenbasis migrieren

Da das Platform Web SDK mehrere Adobe-Anwendungen kombiniert und ermöglicht, müssen Sie die Target-Migration anderer Adobe-Anwendungen wie Analytics und Audience Manager koordinieren. Alle Adobe-Bibliotheken auf einer bestimmten Seite sollten gleichzeitig migriert werden. Eine gemischte Implementierung des Platform Web SDK für Target und AppMeasurement für Analytics auf einer bestimmten Seite wird nicht unterstützt. Es wird jedoch eine gemischte Implementierung über verschiedene Seiten hinweg unterstützt, z. B. das Platform Web SDK auf Seite A und at.js mit AppMeasurement auf Seite B.

Bei der Migration sollten Sie planen, den Prozess Ihres Unternehmens zum Testen und Freigeben von neuem Code zu befolgen und Dinge wie Entwicklungs-, QA- und Staging-Umgebungen zu verwenden, bevor Sie die Veröffentlichung in der Produktion durchführen.

>[!CAUTION]
>
>Umleitungsangebote werden bei seitenweisen Migrationen nicht unterstützt, wenn die Umleitung von einer Seite mit einer Bibliothek zu einer Seite mit einer anderen Bibliothek erfolgt


Lesen Sie als Nächstes den detaillierten [Vergleich von at.js mit dem Platform Web SDK](detailed-comparison.md) , um ein besseres Verständnis der technischen Unterschiede zu erhalten und Bereiche zu identifizieren, die zusätzlichen Fokus erfordern.

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
