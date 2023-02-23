---
title: Ersteinrichtung | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie mehr über und richten Sie die wichtigen grundlegenden Elemente ein, die für Ihre Implementierung des Platform Web SDK erforderlich sind.
source-git-commit: 287ebcb275c4fca574dbd6cdf7e07ba4268bddb5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---

# Führen Sie die erste Datenerfassung durch

Für die Migration von at.js zum Platform Web SDK ist eine Ersteinrichtung erforderlich, um die korrekte Datenerfassung, Funktionen und Funktionen des Platform Web SDK zu ermöglichen. Die folgenden Schritte aus dem [Tutorial zur Implementierung des Platform Web SDK](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=de) muss vor jeder Änderung der Website-Implementierung abgeschlossen sein:

- [Konfigurieren der entsprechenden Berechtigungen](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-permissions.html){target="_blank"} in der Adobe Admin Console zur Datenerfassung
- [Konfigurieren eines XDM-Schemas](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-schemas.html){target="_blank"} zur Übermittlung strukturierter Daten an das Edge-Netzwerk
- [Identitäts-Namespace konfigurieren](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-identities.html){target="_blank"} für geräteübergreifende Personalisierung und Mbox3rdPartyId-Funktionalität
- [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-datastream.html){target="_blank"} um die Weiterleitung von Daten aus Edge Network zu ermöglichen
- [Konfigurieren des Datenspeichers](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html#configure-the-datastream){target="_blank"} , um die Weiterleitung von Daten an Adobe Target zu ermöglichen

>[!CAUTION]
>
>Beachten Sie, dass diese Designaspekte über Target-, Analytics- und Audience Manager-Migrationen hinweg koordiniert werden sollten.

Nach Abschluss der ersten Konfiguration sollte die Target-Funktion mithilfe des Adobe Experience Platform Edge Network aktiviert werden.

Als Nächstes erfahren Sie, wie Sie [die at.js-Bibliothek ersetzen und eine grundlegende Platform Web SDK-Implementierung einrichten](replace-library.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
