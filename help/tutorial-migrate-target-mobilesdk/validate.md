---
title: Validieren und Fehlerbehebung bei der Implementierung der Decisioning-Erweiterung
description: Erfahren Sie, wie Sie eine Adobe Target Mobile-Implementierung mithilfe der Decisioning-Erweiterung validieren und Fehler beheben können.
exl-id: edc6e25a-58d7-4145-97c3-bf48e980914f
source-git-commit: a4fe85580776e5d84f6deaf3c0224f0513ba8415
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Validieren und Fehlerbehebung bei der Implementierung der Decisioning-Erweiterung

Nachdem Sie Ihre Target-Implementierung von der Target-Erweiterung zur Decisioning-Erweiterung migriert haben, müssen Sie überprüfen, ob alles ordnungsgemäß funktioniert, bevor Sie Änderungen an Ihrer Produktions-App veröffentlichen. Adobe empfiehlt Folgendes. Ausführliche Informationen finden Sie auf dieser Seite:

* Führen Sie eine technische Validierung durch, um sicherzustellen, dass die Basisimplementierung und die SDK-Anfragen und -Antworten von Platform Mobile korrekt aussehen
* Sicherstellen, dass Target-Aktivitäten ordnungsgemäß bereitgestellt und gerendert werden
* Überprüfen, ob das Reporting ordnungsgemäß funktioniert
* Gehen Sie zu Zielgruppen und Profilskripten zurück, um sicherzustellen, dass sie mit Platform Mobile SDK und der Erweiterung Optimime kompatibel sind
* Sicherstellen, dass Integrationen mit Adobe oder Anwendungen von Drittanbietern ordnungsgemäß funktionieren

Jede Target-Implementierung unterscheidet sich je nach Site-Architektur und verwendeten Funktionen. Sie können die folgenden Tabellen als Ausgangspunkt verwenden und alle Elemente hinzufügen, die für Ihre Implementierung eindeutig sind.

## Technische Validierung und Fehlerbehebung

Die technische Validierung und Fehlerbehebung mit Platform Mobile SDK und der Decisioning-Erweiterung wurde mit Assurance erheblich verbessert. Auf den folgenden Dokumentationsseiten erfahren Sie mehr über dieses wichtige Tool:

* [Einrichten von Decisioning-Plug-ins in Assurance](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/assurance-setup/){target=_blank}

* [Validieren und Optimieren der SDK-Einrichtung](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/optimize-configuration-view/){target=_blank}

* [Prüfen Sie Anfragen und simulieren Sie verschiedene Erlebnisse](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/review-simulate/){target=_blank}

Nachdem Sie die oben genannten Validierungsschritte ausgeführt haben, können Sie sich darauf verlassen, dass die SDK-Implementierung von Platform Mobile mit der Decisioning-Erweiterung bereit für den Wechsel zur Produktionsumgebung ist.

Herzlichen Glückwunsch, Sie haben das Ende des Tutorials erreicht! Viel Glück bei der Migration Ihrer Adobe Target-Implementierung zur Decisioning-Erweiterung!

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
