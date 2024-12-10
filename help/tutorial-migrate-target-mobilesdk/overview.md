---
title: Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie, wie Sie Ihre Mobile-App-Implementierung von der Adobe Target in die Adobe Journey Optimizer - Decisioning-Erweiterung migrieren.
last-substantial-update: 2023-02-23T00:00:00Z
exl-id: 32363b95-b6ad-44af-a3b0-e1fbbbf5a8f1
source-git-commit: 485e79e3569052184475fbc49ab5f43cebcac9a6
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 3%

---

# Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung

In diesem Handbuch erfahren erfahrene Adobe Target-Implementierer, wie Sie vorhandene Adobe Experience Platform Mobile SDK-Implementierungen von der Adobe Target-Erweiterung in die Adobe Journey Optimizer - Decisioning-Erweiterung migrieren.

Adobe Experience Platform Mobile SDK ermöglicht die durchgängige Interaktion mit Ihren mobilen Anwendungen. Die Target-Erweiterung baut auf dem Mobile SDK auf, um Sie bei der Personalisierung von App-Erlebnissen mit Adobe Target zu unterstützen. Die Decisioning-Erweiterung ist ein neuerer Ansatz zur Implementierung von Adobe Target in Apps, die Adobe Experience Platform Edge Network-Funktionen verwenden, die die Integration von Target in plattformbasierte Apps wie Real-Time CDP und Journey Optimizer unterstützen.

## Wesentliche Vorteile

Zu den Vorteilen der Decisioning-Erweiterung zählen:

* Schnellere Freigabe von Zielgruppen aus [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=de)
* Integration von Target in Journey Optimizer zur Unterstützung der [Offer decisioning-Bereitstellung](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)
* Eine engere Integration mit Adobe Analytics, bei der keine Informationen aus separaten Netzwerkaufrufen zugeordnet werden müssen
* Zusätzliche Implementierungsflexibilität für Entwickler

Der größte Vorteil für Target-Kunden bei der Migration liegt wahrscheinlich in der Integration mit Real-time Customer Data Platform. Real-Time CDP bietet umfangreiche Funktionen zum Erstellen von Zielgruppen, die auf der vollständigen Datenmenge von Experience Platform und der Echtzeit-Kundenprofilfunktion basieren. Ein integriertes Data Governance-Framework automatisiert die verantwortungsvolle Nutzung dieser Daten. Mit Customer AI können Sie mühelos Modelle für maschinelles Lernen verwenden, um Tendenzmodelle und Abwanderungsmodelle zu erstellen, deren Ausgabe an Adobe Target zurückgegeben werden kann. Und schließlich können Kunden der optionalen Zusatzinformationen zu Gesundheitsfürsorge und Datenschutz- und Sicherheitsschild die Funktion zur Einwilligungsdurchsetzung nutzen, um die Zustimmungsvoreinstellungen einzelner Kunden einfach durchzusetzen. Das Platform Web SDK ist eine Voraussetzung für die Verwendung dieser Real-Time CDP-Funktionen in Ihrem Webkanal.

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
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Decisioning-Erweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
