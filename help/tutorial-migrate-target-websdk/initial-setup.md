---
title: Ersteinrichtung - Migrieren von Target von at.js 2.x zu Web SDK
description: Erfahren Sie mehr über die wichtigen Grundelemente, die für Ihre Implementierung von Platform Web SDK erforderlich sind, und richten Sie sie ein
exl-id: dbf9683b-1cfc-474a-9c38-432cad4d1533
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Durchführen der erstmaligen Einrichtung der Datenerfassung

Für die Migration von at.js zu Platform Web SDK ist eine Ersteinrichtung erforderlich, um die ordnungsgemäße Datenerfassung, Funktionen und Funktionen von Platform Web SDK zu ermöglichen. Die folgenden Schritte aus dem [Implementierungs-Tutorial für Platform Web SDK](https://experienceleague.adobe.com/de/docs/platform-learn/implement-web-sdk/overview) müssen abgeschlossen werden, bevor Änderungen an der Website-Implementierung vorgenommen werden:

- [Konfigurieren der entsprechenden Berechtigungen](https://experienceleague.adobe.com/de/docs/platform-learn/implement-web-sdk/overview#prerequisites){target="_blank"} in der Adobe Admin Console für die Datenerfassung
- [Konfigurieren eines XDM-Schemas](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-schemas.html?lang=de){target="_blank"} zum Übergeben strukturierter Daten an das Edge Network
- [Konfigurieren eines Identity-Namespace](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-identities.html?lang=de){target="_blank"} für geräteübergreifende Personalisierung und mbox3rdPartyId-Funktionen
- [Erstellen eines Datenstroms](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-datastream.html?lang=de){target="_blank"} um die Weiterleitung von Daten aus dem Edge Network zu ermöglichen
- [Konfigurieren des Datenstroms](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html?lang=de#configure-the-datastream){target="_blank"} um die Weiterleitung von Daten an Adobe Target zu ermöglichen

>[!CAUTION]
>
>Denken Sie daran, dass diese Design-Aspekte über Target-, Analytics- und Audience Manager-Migrationen hinweg koordiniert werden sollten.

Sobald die Erstkonfiguration abgeschlossen ist, sollte die Target-Funktion mithilfe des Adobe Experience Platform-Edge Networks aktiviert werden.

Erfahren Sie als Nächstes, wie [&#x200B; die at.js-Bibliothek ersetzen und eine einfache Platform Web SDK-Implementierung einrichten](replace-library.md).

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=de#M463) posten.
