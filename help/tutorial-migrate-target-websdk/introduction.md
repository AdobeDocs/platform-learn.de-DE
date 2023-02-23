---
title: Einführung | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie eine Adobe Target-Implementierung von at.js 2.x auf das Adobe Experience Platform Web SDK migrieren. Zu den Themen gehören das Laden der JavaScript-Bibliothek, das Senden von Parametern, Rendering-Aktivitäten und andere wichtige Hinweise.
last-substantial-update: 2023-02-23T00:00:00Z
source-git-commit: 4b695b4578f0e725fc3fe1e455aa4886b9cc0669
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 6%

---

# Migrieren von Target von at.js 2.x zum Platform Web SDK

In diesem Handbuch erfahren erfahrene Adobe Target-Implementierer, wie Sie eine at.js-Implementierung zum Adobe Experience Platform Web SDK migrieren.

Das Adobe Experience Platform Web SDK ist eine Client-seitige JavaScript-Bibliothek, die es Adobe Experience Cloud-Kunden ermöglicht, über das Adobe Experience Platform Edge Network mit Experience Cloud-Diensten zu interagieren. Diese neue Bibliothek kombiniert die Funktionen der separaten Adobe-Anwendungsbibliotheken in einem einfachen Paket, das die neuen Adobe Experience Platform-Funktionen in vollem Umfang nutzen kann.

## Wesentliche Vorteile

Zu den Vorteilen des Platform Web SDK im Vergleich zur eigenständigen at.js-Bibliothek gehören:

* Schnellere Freigabe von Zielgruppen aus [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=de)
* Integration von Target in Journey Optimizer zur Unterstützung [offer decisioning-Bereitstellung](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)
* Funktion zur Verwendung [Erstanbieter-IDs](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/generate-first-party-device-ids.html?lang=de) Generieren der ECID für die Besucheridentifizierung mit längerer Dauer
* Konsolidierung von Netzwerkaufrufen über Adobe Apps hinweg
* Geringerer Platzbedarf für verbesserte Metriken zur Seitengeschwindigkeit
* Eine engere Integration mit Adobe Analytics, die nicht auf die Zuordnung von Informationen aus separaten Netzwerkaufrufen angewiesen ist
* Zusätzliche Implementierungsflexibilität für Entwickler

Der größte Vorteil für Target-Kunden bei der Migration liegt wahrscheinlich in der Integration mit Real-time Customer Data Platform. Real-Time CDP bietet enorme Funktionen zur Zielgruppenbildung basierend auf der vollständigen Datenmenge, die in Experience Platform erfasst wird, und der Echtzeit-Kundenprofilfunktion. Ein integriertes Data Governance-Framework automatisiert die verantwortungsvolle Nutzung dieser Daten. Mit Customer AI können Sie mühelos Modelle für maschinelles Lernen verwenden, um Tendenz- und Abwanderungsmodelle zu erstellen, deren Ausgabe an Adobe Target zurückgegeben werden kann. Und schließlich können Kunden der optionalen Zusatzinformationen zu Gesundheitsfürsorge und Datenschutz- und Sicherheitsschild die Funktion zur Einwilligungsdurchsetzung nutzen, um die Zustimmungsvoreinstellungen einzelner Kunden einfach durchzusetzen. Das Platform Web SDK ist eine Voraussetzung für die Verwendung dieser RTCDP-Funktionen in Ihrem Webkanal.

## Lernziele

Am Ende dieses Tutorials können Sie:

* Unterschiede bei der Target-Implementierung zwischen at.js und dem Platform Web SDK
* Einrichten der anfänglichen Konfiguration für Target-Funktionen
* Aktualisieren der at.js-Bibliothek auf das Platform Web SDK
* Wiedergabe von formularbasierten und visuellen Experience Composer-Aktivitäten
* Übergeben von Parametern an Target
* Konversionsereignisse verfolgen
* Domänenübergreifende Unterstützung aktivieren
* Zielgruppen und Profilskripte aktualisieren
* Validieren der -Implementierung
* Versand von Target-Erlebnissen debuggen


## Voraussetzungen

Um dieses Tutorial abzuschließen, sollten Sie zunächst:

* Sie verfügen über ein technisches Verständnis Ihrer aktuellen Target at.js-Implementierung
* Vergewissern Sie sich, dass [Editor- oder Publisher-Rolle](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html#section_8C425E43E5DD4111BBFC734A2B7ABC80) für Ihre Target-Instanz verwenden, damit Sie selbst Beispiele versuchen können
* Erfahren Sie, wie Sie Aktivitäten in Adobe Target einrichten. Wenn Sie einen Auffrischungskurs benötigen, sind die folgenden Tutorials und Handbücher für diese Lektion hilfreich:
   * [Visual Experience Composer verwenden](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-visual-experience-composer.html)
   * [Verwenden des formularbasierten Experience Composer](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-form-based-experience-composer.html)
   * [Erstellen von Erlebnis-Targeting-Aktivitäten](https://experienceleague.adobe.com/docs/target-learn/tutorials/activities/create-experience-targeting-activities.html)

Sobald Sie bereit sind, besteht der erste Schritt zu einer erfolgreichen Migration darin, [Informationen zum Migrationsprozess](migration-overview.md) und Unterschiede zwischen at.js und Platform Web SDK.

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).