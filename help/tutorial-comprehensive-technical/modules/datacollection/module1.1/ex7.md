---
title: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - XDM-Schema-Anforderungen in Adobe Experience Platform
description: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - XDM-Schema-Anforderungen in Adobe Experience Platform
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '241'
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

Auf diesem Schema sehen Sie, dass die Feldergruppe **AEP Web SDK ExperienceEvent Mixin** hinzugefügt wurde. Diese Feldergruppe fügt alle minimal erforderlichen Felder zum Schema hinzu. Jedes Erlebnisereignisschema in Adobe Experience Platform, das vom Web SDK verwendet wird, erfordert immer, dass diese Feldergruppe Teil des Schemas ist.

![AEP-Debugger](./images/exp4.png)

In [Modul 1.2](./../module1.2/data-ingestion.md) erfahren Sie, wie Sie Schemas Feldergruppen hinzufügen.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
