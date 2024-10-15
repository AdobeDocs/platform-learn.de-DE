---
title: Aktualisierung von Zielgruppen und Profilskripten - Migration von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Adobe Target-Zielgruppen und Profilskripte aktualisieren können, um die Kompatibilität mit dem Experience Platform Web SDK zu gewährleisten.
source-git-commit: 009548969b88d1bfa6eac23f65b1ca2144f27c34
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Aktualisierung von Target-Zielgruppen und Profilskripten für die Platform Web SDK-Kompatibilität


## Zielgruppen anpassen


Weitere Informationen und Best Practices finden Sie in der entsprechenden Dokumentation zu [Profilskripten](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/profile-parameters.html).

## Parameter-Token für dynamischen Inhalt aktualisieren



Wenn Sie nach der Migration Anpassungen vornehmen möchten, um die neuen XDM-Mbox-Parameternamen zu berücksichtigen, stellen Sie sicher, dass Sie alle betroffenen Aktivitäten während des Migrationsereignisses anhalten, um Aktivitätsanzeigefehler für Besucher zu vermeiden.

Als Nächstes erfahren Sie, wie Sie [die Target-Implementierung validieren](validate.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Optimierungserweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
