---
title: Migrieren - Migrieren der Adobe Target-Implementierung in Ihrer Mobile App zur Offer Decisioning- und Target-Erweiterung
description: Erfahren Sie mehr über die wichtigsten Unterschiede zwischen at.js und Platform Web SDK und wie Sie Ihren Migrationsaufwand planen können.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Migration planen

Der Aufwand für die Migration von der Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung hängt von der Komplexität Ihrer aktuellen Implementierung und der verwendeten Target-Funktionen ab.

Unabhängig davon, wie einfach oder komplex Ihre Implementierung ist, ist es wichtig, Ihren aktuellen Status vor der Migration vollständig zu verstehen. Dieser Leitfaden hilft Ihnen, die Komponenten Ihrer aktuellen Implementierung aufzuschlüsseln und einen überschaubaren Plan zur Migration der einzelnen Komponenten zu entwickeln.

Der Migrationsprozess umfasst die folgenden wichtigen Schritte:

1. Bewertung der aktuellen Implementierung und Festlegung eines Migrationsansatzes
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


Überprüfen Sie anschließend den detaillierten [Vergleich der Target-Erweiterung mit der Offer Decisioning- und Target](detailed-comparison.md), um sich ein besseres Verständnis der technischen Unterschiede zu verschaffen und Bereiche zu ermitteln, die zusätzliche Aufmerksamkeit erfordern.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484?profile.language=de#M625) posten.
