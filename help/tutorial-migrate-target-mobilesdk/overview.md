---
title: Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie, wie Sie Ihre Mobile-App-Implementierung von der Adobe Target zur Adobe Journey Optimizer - Decisioning-Erweiterung migrieren.
last-substantial-update: 2023-02-23T00:00:00Z
exl-id: 32363b95-b6ad-44af-a3b0-e1fbbbf5a8f1
source-git-commit: 485e79e3569052184475fbc49ab5f43cebcac9a6
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 3%

---

# Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung

Dieses Handbuch richtet sich an erfahrene Adobe Target-Implementierer, um zu erfahren, wie Sie bestehende Adobe Experience Platform Mobile SDK-Implementierungen von der Adobe Target-Erweiterung zur Adobe Journey Optimizer-Entscheidungserweiterung migrieren.

Adobe Experience Platform Mobile SDK ermöglicht die durchgängige Interaktion mit Ihren Mobile Apps. Die Target-Erweiterung baut auf der mobilen SDK auf, um Ihnen bei der Personalisierung von App-Erlebnissen mit Adobe Target zu helfen. Die Decisioning-Erweiterung ist ein neuerer Ansatz zur Implementierung von Adobe Target in Mobile Apps, der Adobe Experience Platform-Edge Network-Funktionen verwendet, die die Integration von Target in Platform-basierte Apps wie Real-Time CDP und Journey Optimizer erleichtern.

## Wesentliche Vorteile

Zu den Vorteilen der Decisioning-Erweiterung gehören unter anderem:

* Schnellere Freigabe von Zielgruppen aus [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=de)
* Integration von Target mit Journey Optimizer zur Unterstützung der [Offer decisioning-Bereitstellung](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)
* Eine engere Integration mit Adobe Analytics, die nicht auf der Zuordnung von Informationen aus separaten Netzwerkaufrufen beruht
* Zusätzliche Implementierungsflexibilität für Entwickler

Der wohl größte Vorteil der Migration für Target-Kunden liegt in der Integration mit Real-time Customer Data Platform. Real-Time CDP bietet umfangreiche Funktionen zur Zielgruppenbildung, die auf dem gesamten Spektrum der in Experience Platform aufgenommenen Daten und dessen Echtzeit-Kundenprofilfunktionen basieren. Ein integriertes Data Governance-Framework automatisiert die verantwortungsvolle Nutzung dieser Daten. Mit Kunden-KI können Sie mühelos maschinelle Lernmodelle verwenden, um Tendenz- und Abwanderungsmodelle zu erstellen, deren Ergebnisse an Adobe Target zurückgegeben werden können. Und schließlich können Kundinnen und Kunden der optionalen Add-ons für Healthcare und Privacy &amp; Security Shield die Funktion zur Durchsetzung von Einverständnissen verwenden, um die Einverständnisvoreinstellungen einzelner Kundinnen und Kunden einfach durchzusetzen. Platform Web SDK ist eine Voraussetzung für die Verwendung dieser Real-Time CDP-Funktionen in Ihrem Web-Kanal.

## Lernziele

Am Ende dieses Tutorials können Sie:

* Aufzählungszeichen 1
* Aufzählungszeichen 2


## Voraussetzungen

Um dieses Tutorial abzuschließen, sollten Sie zunächst:

* Aufzählungszeichen 1
* Aufzählungszeichen 2


>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
