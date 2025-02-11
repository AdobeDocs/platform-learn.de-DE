---
title: Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie, wie Sie Ihre Mobile-App-Implementierung von der Adobe Target zur Adobe Journey Optimizer - Decisioning-Erweiterung migrieren.
last-substantial-update: 2023-02-23T00:00:00Z
exl-id: 32363b95-b6ad-44af-a3b0-e1fbbbf5a8f1
source-git-commit: 314f0279ae445f970d78511d3e2907afb9307d67
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---

# Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung

Dieses Handbuch richtet sich an erfahrene Adobe Target-Implementierer, um zu erfahren, wie Sie bestehende Adobe Experience Platform Mobile SDK-Implementierungen von der Adobe Target-Erweiterung zur Adobe Journey Optimizer-Entscheidungserweiterung migrieren.

Adobe Experience Platform Mobile SDK ermöglicht die durchgängige Interaktion mit Ihren Mobile Apps. Die Target-Erweiterung baut auf der mobilen SDK auf, um Ihnen bei der Personalisierung von App-Erlebnissen mit Adobe Target zu helfen. Die Decisioning-Erweiterung ist ein neuerer Ansatz zur Implementierung von Adobe Target in Mobile Apps, der Adobe Experience Platform Edge Network-Funktionen verwendet, die die Integration von Target in Platform-basierte Apps wie Real-Time CDP und Journey Optimizer erleichtern.

![Abbildung der Verbindung von Mobile SDK mit Target über Edge Network mit der Decisioning-Erweiterung](assets/datacollection.png)

>[!INFO]
>
>Innerhalb des Adobe Experience Platform Mobile SDK-Ökosystems werden Erweiterungen durch SDKs implementiert, die in Ihre Anwendungen importiert werden, die unterschiedliche Namen haben können:
>
> * **Target SDK** implementiert die Erweiterung **Adobe Target**
> * **SDK optimieren** implementiert die Erweiterung **Adobe Journey Optimizer - Decisioning**


## Wesentliche Vorteile

Zu den Vorteilen der Adobe Journey Optimizer Decisioning-Erweiterung im Vergleich zur Target-Erweiterung gehören:

* Schnellere Freigabe von Zielgruppen aus [Real-Time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=de)
* Integration von Target mit Journey Optimizer zur Unterstützung der Bereitstellung von [Offer Decisioning](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)
* Eine engere Integration mit Adobe Analytics, die nicht auf der Zuordnung von Informationen aus separaten Netzwerkaufrufen beruht
* Zusätzliche Implementierungsflexibilität für Entwickler

Der wohl größte Vorteil der Migration für Target-Kunden liegt in der Integration mit Real-Time Customer Data Platform. Real-Time CDP bietet umfangreiche Funktionen zur Zielgruppenbildung, die auf dem gesamten Spektrum der in Experience Platform aufgenommenen Daten und dessen Echtzeit-Kundenprofilfunktionen basieren. Ein integriertes Data Governance-Framework automatisiert die verantwortungsvolle Nutzung dieser Daten. Mit Kunden-KI können Sie mühelos maschinelle Lernmodelle verwenden, um Tendenz- und Abwanderungsmodelle zu erstellen, deren Ergebnisse an Adobe Target zurückgegeben werden können. Und schließlich können Kundinnen und Kunden der optionalen Add-ons für Healthcare und Privacy &amp; Security Shield die Funktion zur Durchsetzung von Einverständnissen verwenden, um die Einverständnisvoreinstellungen einzelner Kundinnen und Kunden durchzusetzen. Platform Mobile SDK und die Decisioning-Erweiterung sind erforderlich, um diese Real-Time CDP-Funktionen in Ihrem mobilen Kanal verwenden zu können.

## Migrationsschritte

Der Aufwand für die Migration von der Target- zur Decisioning-Erweiterung hängt von der Komplexität Ihrer aktuellen Implementierung und der verwendeten Target-Funktionen ab.

Unabhängig davon, wie einfach oder komplex Ihre Implementierung ist, ist es wichtig, Ihren aktuellen Status vor der Migration vollständig zu verstehen. Dieser Leitfaden hilft Ihnen, die Komponenten Ihrer aktuellen Implementierung aufzuschlüsseln und einen überschaubaren Plan zur Migration der einzelnen Komponenten zu entwickeln.

Der Migrationsprozess umfasst die folgenden wichtigen Schritte:

1. Bewertung der aktuellen Implementierung
1. Einrichten der Anfangskomponenten für die Verbindung mit Adobe Experience Platform Edge Network
1. Aktualisieren Sie die grundlegende Implementierung, um die Target-Erweiterung durch die Decisioning-Erweiterung zu ersetzen
1. Optimieren Sie die Implementierung von SDK Optimieren für Ihre spezifischen Anwendungsfälle. Dazu kann es gehören, zusätzliche Parameter zu übergeben, Antwort-Token zu verwenden und vieles mehr.
1. Aktualisieren von Objekten in der Target-Oberfläche, z. B. Profilskripte, Aktivitäten und Zielgruppendefinitionen
1. Validieren Sie die endgültige Implementierung, bevor Sie den Wechsel in Ihrer Produktions-App vornehmen

>[!INFO]
>
>Innerhalb des Adobe Experience Platform Mobile SDK-Ökosystems werden Erweiterungen durch SDKs implementiert, die in Ihre Anwendungen importiert werden, die unterschiedliche Namen haben können:
>
> * **Target SDK** implementiert die Erweiterung **Adobe Target**
> * **SDK optimieren** implementiert die Erweiterung **Adobe Journey Optimizer - Decisioning**

Überprüfen Sie anschließend den detaillierten [Vergleich der Target- und der Decisioning-Erweiterung](comparison.md), um die technischen Unterschiede besser zu verstehen und Bereiche zu identifizieren, die einen zusätzlichen Fokus erfordern.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
