---
title: Ersteinrichtung - Migrieren der Adobe Target-Implementierung in Ihrer Mobile App zur Offer Decisioning- und Target-Erweiterung
description: Erfahren Sie mehr über die wichtigen Grundelemente, die für Ihre Implementierung von Platform Web SDK erforderlich sind, und richten Sie sie ein
exl-id: dfc5abc8-0e79-454a-b1bb-6a42b1219771
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 6%

---

# Durchführen der erstmaligen Einrichtung der Datenerfassung

Die Migration von Target SDK zu Optimize SDK erfordert eine Ersteinrichtung, um die ordnungsgemäße Datenerfassung, Funktionen und Funktionen von Optimize SDK zu ermöglichen. Die folgenden Schritte müssen abgeschlossen sein, bevor Änderungen an der Implementierung von Mobile Apps vorgenommen werden:

- [Konfigurieren der entsprechenden Berechtigungen](https://experienceleague.adobe.com/de/docs/platform-learn/implement-web-sdk/overview#permissions){target="_blank"} in der Adobe Admin Console für die Datenerfassung
- [Konfigurieren eines XDM-](https://experienceleague.adobe.com/de/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-schema){target="_blank"}) zum Übergeben strukturierter Daten an die Edge Network
- [Konfigurieren des Schemas](https://experienceleague.adobe.com/de/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-your-schema){target="_blank"} um Adobe Target-Daten zu empfangen
- [Konfigurieren eines Identity-Namespace](https://experienceleague.adobe.com/de/docs/platform-learn/implement-mobile-sdk/app-implementation/identity#set-up-a-custom-identity-namespace){target="_blank"} für geräteübergreifende Personalisierung und mbox3rdPartyId-Funktionen
- [Erstellen eines Datenstroms](https://experienceleague.adobe.com/de/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-datastream){target="_blank"} um die Weiterleitung von Daten aus Edge Network zu ermöglichen
- [Konfigurieren des Datenstroms](https://experienceleague.adobe.com/de/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-datastream-configuration){target="_blank"} um die Weiterleitung von Daten an Adobe Target zu ermöglichen
- [Konfigurieren der Tag-Eigenschaft](https://experienceleague.adobe.com/de/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#install-adobe-journey-optimizer---decisioning-tags-extension){target="_blank"} für Offer Decisioning und die Target-Erweiterung

## Erweiterungskonfiguration

>[!BEGINTABS]

>[!TAB Offer Decisioning- und Target-Erweiterung]

Bei Verwendung der Offer Decisioning- und Target-Erweiterung installierte Tag-Erweiterungen:

1. Offer Decisioning und Target
1. Adobe Experience Platform Edge Network
1. Core für Mobilgeräte
1. Profil
1. Einverständnis
1. Identität
1. AEP Assurance (optional, für das Debugging erforderlich)

![Bei Verwendung der Offer Decisioning- und Target-Erweiterung installierte Tag-Erweiterungen](assets/tag-extensions-decisioning.png)

>[!TAB Target-Erweiterung]

Bei Verwendung der Target-Erweiterung installierte Tag-Erweiterungen:

1. Adobe Target
1. Core für Mobilgeräte
1. Profil
1. Adobe Analytics (optional, erforderlich bei Verwendung von Adobe Analytics als Berichtsquelle für Adobe Target-Aktivitäten)

![Bei Verwendung der Target-Erweiterung installierte Tag-Erweiterungen](assets/tag-extensions-target.png)

>[!ENDTABS]

## Datenstromkonfiguration

Die Target-Erweiterung verfügt über [konfigurierbare Einstellungen](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) die mit der Entscheidungs[Erweiterung im Datenstrom konfiguriert &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#adobe-experience-platform-data-collection-setup).

| Target-Erweiterung | Offer Decisioning- und Target-Erweiterung | Anmerkungen |
| --- | --- | --- | 
| Clientcode | k. A. | Wird automatisch vom Edge mithilfe der IMS-Organisationsdetails festgelegt |
| Umgebungs-ID | Zielumgebungs-ID | Im Datenstrom konfiguriert |
| Workspace-Zieleigenschaft | Eigenschafts-Token | Im Datenstrom konfiguriert |
| Timeout | Timeout | Konfigurierbar in der Offer Decisioning- und Target-Erweiterung sowie in der SDK optimieren . Die standardmäßige maximale Wartezeit beträgt 10 Sekunden. |
| Serverdomäne | Edge Network-Domain | In der Adobe Experience Platform Edge Network-Erweiterung festgelegt |

Erfahren Sie als Nächstes, wie [&#x200B; Target-SDK &#x200B;](replace-sdk.md).

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484?profile.language=de#M625) posten.
