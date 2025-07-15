---
title: Ihre Mobile App von der Adobe Target zur Offer Decisioning- und Target-Erweiterung migrieren
description: Erfahren Sie, wie Sie Ihre Mobile-App-Implementierung von der Adobe Target zur Offer Decisioning- und Target-Erweiterung migrieren
last-substantial-update: 2023-02-23T00:00:00Z
exl-id: 32363b95-b6ad-44af-a3b0-e1fbbbf5a8f1
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 1%

---

# Ihre Mobile App von der Adobe Target zur Offer Decisioning- und Target-Erweiterung migrieren

Dieses Handbuch richtet sich an erfahrene Adobe Target-Implementierer, um zu erfahren, wie Sie bestehende mobile Adobe Experience Platform-SDK-Implementierungen von der Adobe Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung migrieren.

Adobe Experience Platform Mobile SDK ermöglicht die durchgängige Interaktion mit Ihren Mobile Apps. Die Target-Erweiterung baut auf der mobilen SDK auf, um Ihnen bei der Personalisierung von App-Erlebnissen mit Adobe Target zu helfen. Die Offer Decisioning- und Target-Erweiterung ist ein neuerer Ansatz zur Implementierung von Adobe Target in Mobile Apps, der Adobe Experience Platform Edge Network-Funktionen nutzt, die die Integration von Target in Platform-basierte Apps wie Real-Time CDP und Journey Optimizer erleichtern.

![Abbildung der mobilen SDK, die über Edge Network mit der Offer Decisioning- und Target-Erweiterung eine Verbindung zu Target herstellt](assets/datacollection.png)

## Wichtigste Vorteile

Zu den Vorteilen der Adobe Journey Optimizer Offer Decisioning- und Target-Erweiterung im Vergleich zur Target-Erweiterung gehören:

* Schnellere Freigabe von Zielgruppen aus [Real-Time Customer Data Platform](https://experienceleague.adobe.com/de/docs/platform-learn/tutorials/destinations/target/next-hit-personalization)
* Integration von Target mit Journey Optimizer zur Unterstützung der Bereitstellung von [Offer Decisioning](https://experienceleague.adobe.com/de/docs/target/using/integrate/ajo/offer-decision)
* Eine engere Integration mit Adobe Analytics, die nicht auf der Zuordnung von Informationen aus separaten Netzwerkaufrufen beruht
* Zusätzliche Implementierungsflexibilität für Entwickler

Der wohl größte Vorteil der Migration für Target-Kunden liegt in der Integration mit Real-Time Customer Data Platform. Real-Time CDP bietet umfangreiche Funktionen zur Zielgruppenbildung, die auf dem gesamten Spektrum der in Experience Platform aufgenommenen Daten und dessen Echtzeit-Kundenprofilfunktionen basieren. Ein integriertes Data Governance-Framework automatisiert die verantwortungsvolle Nutzung dieser Daten. Mit Kunden-KI können Sie mühelos maschinelle Lernmodelle verwenden, um Tendenz- und Abwanderungsmodelle zu erstellen, deren Ergebnisse an Adobe Target zurückgegeben werden können. Und schließlich können Kundinnen und Kunden der optionalen Add-ons für Healthcare und Privacy &amp; Security Shield die Funktion zur Durchsetzung von Einverständnissen verwenden, um die Einverständnisvoreinstellungen einzelner Kundinnen und Kunden durchzusetzen. Platform Mobile SDK und die Offer Decisioning- und Target-Erweiterung sind eine Voraussetzung für die Verwendung dieser Real-Time CDP-Funktionen in Ihrem mobilen Kanal.

## Migrationsschritte

Der Aufwand für die Migration von der Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung hängt von der Komplexität Ihrer aktuellen Implementierung und der verwendeten Target-Funktionen ab.

Unabhängig davon, wie einfach oder komplex Ihre Implementierung ist, ist es wichtig, Ihren aktuellen Status vor der Migration vollständig zu verstehen. Dieser Leitfaden hilft Ihnen, die Komponenten Ihrer aktuellen Implementierung aufzuschlüsseln und einen überschaubaren Plan zur Migration der einzelnen Komponenten zu entwickeln.

Der Migrationsprozess umfasst die folgenden wichtigen Schritte:

1. Bewertung Ihrer aktuellen Implementierung, einschließlich:
   1. Alle verwendeten Target SDK-APIs
   1. Änderungen an den globalen Einstellungen von Target
   1. Integration in Adobe Analytics
   1. Verwendung von Mbox-, Profil- und Entitätsparametern
   1. Verwendung von Profilskripten und Audiences
   1. Benutzerdefinierter Code, der für Ihre Implementierung eindeutig ist
1. Einrichten der Anfangskomponenten für die Verbindung mit Adobe Experience Platform Edge Network
1. Aktualisieren Sie die grundlegende Implementierung, um die Target-Erweiterung durch die Offer Decisioning- und Target-Erweiterung zu ersetzen
1. Optimieren Sie die Implementierung von SDK Optimieren für Ihre spezifischen Anwendungsfälle. Dazu kann es gehören, zusätzliche Parameter zu übergeben, Antwort-Token zu verwenden und vieles mehr.
1. Aktualisieren von Objekten in der Target-Oberfläche, z. B. Profilskripte, Aktivitäten und Zielgruppendefinitionen
1. Validieren Sie die endgültige Implementierung, bevor Sie den Wechsel in Ihrer Produktions-App vornehmen


>[!INFO]
>
>Innerhalb des Adobe Experience Platform Mobile SDK-Ökosystems werden Erweiterungen durch SDKs implementiert, die in Ihre Anwendungen importiert werden, die unterschiedliche Namen haben können:
>
> * **Target SDK** implementiert die Erweiterung **Adobe Target**
> * **SDK optimieren** implementiert die Erweiterung **Offer Decisioning und Target**

Überprüfen Sie anschließend den detaillierten [Vergleich der Target-Erweiterung mit der Offer Decisioning- und Target](comparison.md), um sich ein besseres Verständnis der technischen Unterschiede zu verschaffen und Bereiche zu ermitteln, die zusätzliche Aufmerksamkeit erfordern.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484?profile.language=de#M625) posten.
