---
title: Planung - Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie, wie Sie Ihre Adobe Target-Implementierung von at.js 2.x auf Adobe Experience Platform Web SDK planen.
exl-id: 50eefe2d-ba20-45d5-8674-c4f5d035a9eb
source-git-commit: 348554b5a2d43d7a882e8259b39a57af13d41ff4
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Planen der Target-Migration zur Decisioning-Erweiterung

Bevor Sie in Ihrer Mobile App ein Upgrade von Target von der Target-Erweiterung auf die Decisioning-Erweiterung durchführen, sollten Sie Ihre aktuelle Implementierung bewerten.

## Bewertung der aktuellen Implementierung der Target-Erweiterung

Der erste Schritt für eine erfolgreiche Migration besteht darin, ein solides Verständnis Ihrer aktuellen Target-Erweiterungsimplementierung zu haben. Es gibt Funktionen und benutzerdefinierten Code, den Sie verwenden können und der aktualisiert werden muss. Berücksichtigen Sie bei der Bewertung Folgendes:

### Welche Funktionen werden unterstützt?

<!--Platform Web SDK is under continuous active development and features and enhancements are added regularly. As you evaluate your current at.js implementation, refer to the [supported use cases](https://github.com/orgs/adobe/projects/18/views/1) page for the latest information.-->

### Welche Funktionen nutzt ihr heute?

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


Überprüfen Sie anschließend den detaillierten [Vergleich der Target- und der Decisioning-Erweiterung](detailed-comparison.md), um die technischen Unterschiede besser zu verstehen und Bereiche zu identifizieren, die einen zusätzlichen Fokus erfordern.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
