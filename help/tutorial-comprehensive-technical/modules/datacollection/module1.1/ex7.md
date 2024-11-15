---
title: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - XDM-Schema-Anforderungen in Adobe Experience Platform
description: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - XDM-Schema-Anforderungen in Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 3fc4a1d6-4130-464e-98c0-5b9cac8051a0
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 1.1.7 XDM-Schema-Anforderungen in Adobe Experience Platform

Um sicherzustellen, dass Web SDK und legierte.js Daten in Adobe Experience Platform erfassen können, muss ein bestimmtes XDM-Mixin zum XDM-Schema in Adobe Experience Platform gehören.

Gehen Sie zu [https://experience.adobe.com/platform](https://experience.adobe.com/platform) und melden Sie sich an.

![AEP-Debugger](./images/exp1.png)

Wählen Sie nach der Anmeldung die entsprechende Sandbox aus, indem Sie in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **Produktions-Prod** klicken. Wählen Sie die Sandbox `--aepSandboxName--` aus.

Nachdem Sie Ihre Sandbox ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich jetzt in Ihrer Sandbox.

![AEP-Debugger](./images/exp2.png)

Wechseln Sie im linken Menü zu **Schemas** und öffnen Sie das Schema **Demo System - Event Schema for Website (Global v1.1)** .

![AEP-Debugger](./images/exp3.png)

In diesem Schema sehen Sie, dass die Feldergruppe **AEP Web SDK ExperienceEvent** hinzugefügt wurde. Diese Feldergruppe fügt alle minimal erforderlichen Felder zum Schema hinzu. Jedes Erlebnisereignisschema in Adobe Experience Platform, das vom Web SDK verwendet wird, erfordert immer, dass diese Feldergruppe Teil des Schemas ist.

![AEP-Debugger](./images/exp4.png)

In [Modul 1.2](./../module1.2/data-ingestion.md) erfahren Sie, wie Sie Schemas Feldergruppen hinzufügen.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
