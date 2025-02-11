---
title: Ersteinrichtung - Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie mehr über die wichtigen Grundelemente, die für Ihre Implementierung von Platform Web SDK erforderlich sind, und richten Sie sie ein
exl-id: dfc5abc8-0e79-454a-b1bb-6a42b1219771
source-git-commit: a928fb5c8e48e71984b75faf4eb397814caac6aa
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 5%

---

# Durchführen der erstmaligen Einrichtung der Datenerfassung

Die Migration von Target SDK zu Optimize SDK erfordert eine Ersteinrichtung, um die ordnungsgemäße Datenerfassung, Funktionen und Funktionen von Optimize SDK zu ermöglichen. Die folgenden Schritte müssen abgeschlossen werden, bevor Änderungen an der Website-Implementierung stattfinden:

- [Konfigurieren der entsprechenden Berechtigungen](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview#permissions){target="_blank"} in der Adobe Admin Console für die Datenerfassung
- [Konfigurieren eines XDM-](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-schema){target="_blank"}) zum Übergeben strukturierter Daten an die Edge Network
- [Konfigurieren des Schemas](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-your-schema){target="_blank"} um Adobe Target-Daten zu empfangen
- [Konfigurieren eines Identity-Namespace](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/app-implementation/identity#set-up-a-custom-identity-namespace){target="_blank"} für geräteübergreifende Personalisierung und mbox3rdPartyId-Funktionen
- [Erstellen eines Datenstroms](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-datastream){target="_blank"} um die Weiterleitung von Daten aus Edge Network zu ermöglichen
- [Konfigurieren des Datenstroms](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-datastream-configuration){target="_blank"} um die Weiterleitung von Daten an Adobe Target zu ermöglichen
- [Konfigurieren der Tag-Eigenschaft](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#install-adobe-journey-optimizer---decisioning-tags-extension){target="_blank"} für die Decisioning-Erweiterung

>[!BEGINTABS]

>[!TAB Decisioning-Erweiterung]

Bei Verwendung der Decisioning-Erweiterung installierte Tag-Erweiterungen:

1. Adobe Journey Optimizer - Decisioning
1. Adobe Experience Platform Edge Network
1. Core für Mobilgeräte
1. Profil
1. Einverständnis
1. Identität
1. AEP Assurance (optional, für das Debugging erforderlich)

![Tag-Erweiterungen bei Verwendung der Decisioning-Erweiterung installiert](assets/tag-extensions-decisioning.png)

>[!TAB Target-Erweiterung]

Bei Verwendung der Target-Erweiterung installierte Tag-Erweiterungen:

1. Adobe Target
1. Core für Mobilgeräte
1. Profil
1. Adobe Analytics (optional, erforderlich bei Verwendung von Adobe Analytics als Berichtsquelle für Adobe Target-Aktivitäten)

![Bei Verwendung der Target-Erweiterung installierte Tag-Erweiterungen](assets/tag-extensions-target.png)

>[!ENDTABS]

Erfahren Sie als Nächstes, wie [ Target-SDK ](replace-library.md).

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
