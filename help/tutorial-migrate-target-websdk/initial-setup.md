---
title: Ersteinrichtung | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie mehr über und richten Sie die wichtigen grundlegenden Elemente ein, die für Ihre Implementierung des Platform Web SDK erforderlich sind
exl-id: dbf9683b-1cfc-474a-9c38-432cad4d1533
source-git-commit: 2182441d992aec0602d0955d78aa85407bd770c9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Führen Sie die erste Datenerfassung durch

Für die Migration von at.js zum Platform Web SDK ist eine Ersteinrichtung erforderlich, um die korrekte Datenerfassung, Funktionen und Funktionen des Platform Web SDK zu ermöglichen. Die folgenden Schritte aus dem Tutorial zur Implementierung des Platform Web SDK ](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=de) müssen abgeschlossen sein, bevor Änderungen an der Website-Implementierung vorgenommen werden:[

- [Konfigurieren der entsprechenden Berechtigungen](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview#prerequisites){target="_blank"} in Adobe Admin Console für die Datenerfassung
- [Konfigurieren eines XDM-Schemas](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-schemas.html){target="_blank"} für die Übergabe strukturierter Daten an das Edge Network
- [Konfigurieren eines Identitäts-Namespace](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-identities.html){target="_blank"} für geräteübergreifende Personalisierung und Mbox3rdPartyId-Funktionalität
- [Erstellen Sie einen Datastream](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-datastream.html){target="_blank"} , um die Weiterleitung von Daten aus Edge Network zu ermöglichen
- [Konfigurieren Sie den Datastream](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html#configure-the-datastream){target="_blank"}, um die Weiterleitung von Daten an Adobe Target zu ermöglichen

>[!CAUTION]
>
>Beachten Sie, dass diese Designaspekte über Target-, Analytics- und Audience Manager-Migrationen hinweg koordiniert werden sollten.

Nach Abschluss der ersten Konfiguration sollte die Target-Funktion mithilfe des Adobe Experience Platform-Edge Networks aktiviert werden.

Als Nächstes erfahren Sie, wie Sie [die at.js-Bibliothek ersetzen und eine grundlegende Platform Web SDK-Implementierung einrichten](replace-library.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
