---
title: Planung - Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie, wie Sie für Ihre Adobe Target-Implementierung von at.js 2.x auf das Adobe Experience Platform Web SDK planen.
source-git-commit: afbc8248ad81a5d9080a4fdba1167e09bbf3b33d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Planen der Target-Migration zur Decisioning-Erweiterung

Bevor Sie Target von der Target-Erweiterung auf die Decisioning-Erweiterung in Ihrer mobilen App aktualisieren, sollten Sie Ihre aktuelle Implementierung bewerten.

## Bewertung der aktuellen Target-Erweiterungsimplementierung

Der erste Schritt zu einer erfolgreichen Migration besteht darin, ein solides Verständnis Ihrer aktuellen Target-Erweiterungsimplementierung zu haben. Es gibt Funktionen, Funktionen und benutzerdefinierten Code, die Sie verwenden können und die aktualisiert werden müssen. Beachten Sie Folgendes bei der Beurteilung:

### Welche Funktionen werden unterstützt?

<!--Platform Web SDK is under continuous active development and features and enhancements are added regularly. As you evaluate your current at.js implementation, refer to the [supported use cases](https://github.com/orgs/adobe/projects/18/views/1) page for the latest information.-->

### Welche Funktionen verwenden Sie heute?

<!--Platform Web SDK is a new library that consolidates all Adobe solutions for the websites into a single SDK. This enables tighter integration and enables new capabilities unique to Adobe Experience Platform. However, this also means at.js functions are not backwards compatible with Platform Web SDK. As you evaluate your current implementation, make note of the following:

- at.js functions such as `getOffer()` and `applyOffer()`
- Modifications to Target's global settings
- Integration with Adobe Analytics
- Use of a flicker mitigation script
- Use of response tokens
- Use of mbox, profile, and entity parameters
- Custom code unique to your implementation-->

### Welchen Migrationsansatz wählen Sie?

<!--Once you have revisited your at.js implementation, you need to determine a migration approach. There are two options:

- Migrate all Adobe applications at once across the entire site
- Migrate on a page-by-page basis

Because Platform Web SDK combines and enables multiple Adobe applications, you must coordinate the Target migration of other Adobe applications like Analytics and Audience Manager. All Adobe libraries on a given page should be migrated at the same time. A mixed implementation of Platform Web SDK for Target and AppMeasurement for Analytics on a particular page is not supported. However, a mixed implementation across different pages is supported, for example Platform Web SDK on page A, and at.js with AppMeasurement on page B.

As you migrate, you should plan on following your company's process for testing and releasing new code and use things like development, qa, and staging environments before you release to production.-->

<!--
>[!CAUTION]
>
>Redirect offers are not supported in page-by-page migrations if redirecting from a page with one library to a page with a different library
-->


Überprüfen Sie als Nächstes den detaillierten [Vergleich der Target-Erweiterung und der Decisioning-Erweiterung](detailed-comparison.md), um ein besseres Verständnis der technischen Unterschiede zu erhalten und Bereiche zu identifizieren, die zusätzlichen Fokus erfordern.

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Decisioning-Erweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
