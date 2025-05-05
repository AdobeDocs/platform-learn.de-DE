---
title: Migrieren von Target aus at.js 2.x nach Web SDK
description: Erfahren Sie, wie Sie eine Adobe Target-Implementierung von at.js 2.x zu Adobe Experience Platform Web SDK migrieren. Zu den Themen gehören das Laden der JavaScript-Bibliothek, das Senden von Parametern, Rendering-Aktivitäten und andere bemerkenswerte Hinweise.
last-substantial-update: 2023-02-23T00:00:00Z
exl-id: c8920fde-ad6b-4f2d-a35f-ce865b35bba0
source-git-commit: e0359d1bade01f79d0f7aff6a6e69f3e4d0c3b62
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 5%

---

# Migrieren von Target aus at.js 2.x nach Platform Web SDK

Dieses Handbuch richtet sich an erfahrene Adobe Target-Implementierer, um zu erfahren, wie Sie eine at.js-Implementierung zu Adobe Experience Platform Web SDK migrieren.

Adobe Experience Platform Web SDK ist eine Client-seitige JavaScript-Bibliothek, die es Adobe Experience Cloud-Kunden ermöglicht, über Adobe Experience Platform Edge Network mit Experience Cloud-Services zu interagieren. Diese neue Bibliothek kombiniert die Funktionen der separaten Adobe-Anwendungsbibliotheken in einem einzigen, schlanken Paket, das die neuen Adobe Experience Platform-Funktionen in vollem Umfang nutzen kann.


>[!NOTE]
>
>Ähnliche Migrations-Tutorials sind verfügbar für:
>
> * [Adobe Analytics](../tutorial-migrate-analytics-websdk/migration-to-websdk-overview.md)
> * [Adobe Audience Manager](https://experienceleague.adobe.com/de/docs/audience-manager/user-guide/migrate-to-web-sdk/appmeasurement-to-web-sdk)

>[!CAUTION]
>
> Da Platform Web SDK mehrere Adobe-Programme unterstützt, sollten alle Adobe-Bibliotheken auf einer bestimmten Seite gleichzeitig migriert werden. Beispielsweise wird eine gemischte Implementierung von Web SDK for Target und AppMeasurement for Analytics auf einer Einzelseite _nicht unterstützt_. Es wird jedoch eine gemischte Implementierung über verschiedene Seiten hinweg unterstützt, z. B. Web SDK auf Seite A und at.js mit AppMeasurement auf Seite B.



## Wichtigste Vorteile

Zu den Vorteilen von Platform Web SDK im Vergleich zur eigenständigen at.js-Bibliothek gehören unter anderem:

* Schnellere Freigabe von Zielgruppen aus [Real-Time Customer Data Platform](https://experienceleague.adobe.com/de/docs/platform-learn/tutorials/destinations/target/next-hit-personalization)
* Integration von Target mit Journey Optimizer zur Unterstützung der Bereitstellung von [Offer Decisioning](https://experienceleague.adobe.com/de/docs/target/using/integrate/ajo/offer-decision)
* Möglichkeit zur Verwendung [Erstanbieter-IDs](https://experienceleague.adobe.com/de/docs/platform-learn/data-collection/edge-network/generate-first-party-device-ids) zum Generieren der ECID für eine längere Besucheridentifizierung
* Geringerer Platzbedarf für verbesserte Metriken zur Seitengeschwindigkeit
* Zusätzliche Implementierungsflexibilität für Entwickler

Der wohl größte Vorteil der Migration für Target-Kunden liegt in der Integration mit Real-Time Customer Data Platform. Real-Time CDP bietet umfangreiche Funktionen zur Zielgruppenbildung, die auf dem gesamten Spektrum der in Experience Platform aufgenommenen Daten und dessen Echtzeit-Kundenprofilfunktionen basieren. Ein integriertes Data Governance-Framework automatisiert die verantwortungsvolle Nutzung dieser Daten. Mit Kunden-KI können Sie mühelos maschinelle Lernmodelle verwenden, um Tendenz- und Abwanderungsmodelle zu erstellen, deren Ergebnisse an Adobe Target zurückgegeben werden können. Und schließlich können Kundinnen und Kunden der optionalen Add-ons für Healthcare und Privacy &amp; Security Shield die Funktion zur Durchsetzung von Einverständnissen verwenden, um die Einverständnisvoreinstellungen einzelner Kundinnen und Kunden einfach durchzusetzen. Platform Web SDK ist eine Voraussetzung für die Verwendung dieser Real-Time CDP-Funktionen in Ihrem Web-Kanal.

## Lernziele

Am Ende dieses Tutorials können Sie:

* Machen Sie sich mit den Target-Implementierungsunterschieden zwischen at.js und Platform Web SDK vertraut
* Einrichten der Erstkonfiguration für die Target-Funktion
* Aktualisieren der at.js-Bibliothek auf Platform Web SDK
* Rendern von formularbasierten und visuellen Experience Composer-Aktivitäten
* Übergeben von Parametern an Target
* Konversionsereignisse verfolgen
* Domain-übergreifende Unterstützung aktivieren
* Aktualisieren von Audiences und Profilskripten
* Validieren der -Implementierung
* Debugging der Target-Erlebnisbereitstellung


## Voraussetzungen

Um dieses Tutorial abzuschließen, sollten Sie zunächst:

* Über technische Kenntnisse Ihrer aktuellen Target-at.js-Implementierung verfügen
* Stellen Sie sicher, dass Sie [Editor- oder Publisher-Rolle](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html?lang=de#section_8C425E43E5DD4111BBFC734A2B7ABC80) für Ihre Zielinstanz haben, damit Sie Beispiele selbst versuchen können
* Wissen, wie Sie Aktivitäten in Adobe Target einrichten. Wenn Sie eine Auffrischung benötigen, sind die folgenden Tutorials und Handbücher für diese Lektion hilfreich:
   * [Visual Experience Composer verwenden](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-visual-experience-composer.html?lang=de)
   * [Verwenden des formularbasierten Experience Composers](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-form-based-experience-composer.html?lang=de)
   * [Erstellen von Experience Targeting-Aktivitäten](https://experienceleague.adobe.com/docs/target-learn/tutorials/activities/create-experience-targeting-activities.html?lang=de)

Wenn Sie bereit sind, besteht der erste Schritt für eine erfolgreiche Migration darin, [mehr über den Migrationsprozess zu erfahren](migration-overview.md) und darüber, wie sich at.js und Platform Web SDK unterscheiden.

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=de#M463) posten.
