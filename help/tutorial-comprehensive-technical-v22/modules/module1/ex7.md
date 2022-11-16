---
title: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - XDM-Schema-Anforderungen in Adobe Experience Platform
description: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - XDM-Schema-Anforderungen in Adobe Experience Platform
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 8e17129c-633d-45bd-aa70-78cc3d3a2108
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 1.7 XDM-Schema-Anforderungen in Adobe Experience Platform

Um sicherzustellen, dass Web SDK und legierte.js Daten in Adobe Experience Platform erfassen können, muss ein bestimmtes XDM-Mixin zum XDM-Schema in Adobe Experience Platform gehören.

Navigieren Sie zu [https://experience.adobe.com/platform](https://experience.adobe.com/platform) und melden Sie sich an.

![AEP Debugger](./images/exp1.png)

Wählen Sie nach der Anmeldung die entsprechende Sandbox aus, indem Sie auf den Text klicken **Produktionsprodukt** in der blauen Zeile auf Ihrem Bildschirm. Sandbox auswählen `--aepSandboxId--`.

Nachdem Sie Ihre Sandbox ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich jetzt in Ihrer Sandbox.

![AEP Debugger](./images/exp2.png)

Gehen Sie im linken Menü zu **Schemas** und öffnen Sie die **Demosystem - Ereignisschema für Website (Global v1.1)** Schema.

![AEP Debugger](./images/exp3.png)

Auf diesem Schema sehen Sie, dass die Feldergruppe **ExperienceEvent-Mixin für das AEP Web SDK** wurde hinzugefügt. Diese Feldergruppe fügt alle minimal erforderlichen Felder zum Schema hinzu. Jedes Erlebnisereignisschema in Adobe Experience Platform, das vom Web SDK verwendet wird, erfordert immer, dass diese Feldergruppe Teil des Schemas ist.

![AEP Debugger](./images/exp4.png)

In [Modul 2](./../module2/data-ingestion.md) Sie erfahren, wie Sie Schemas Feldergruppen hinzufügen.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
