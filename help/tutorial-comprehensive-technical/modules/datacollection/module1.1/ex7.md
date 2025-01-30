---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - XDM-Schemaanforderungen in Adobe Experience Platform
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - XDM-Schemaanforderungen in Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 3fc4a1d6-4130-464e-98c0-5b9cac8051a0
source-git-commit: 1526661a80b4d551627dfca42a7e97c9498dd1f2
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# 1.1.7 XDM-Schemaanforderungen in Adobe Experience Platform

Um sicherzustellen, dass Web SDK Daten in Adobe Experience Platform aufnehmen kann, muss ein bestimmtes XDM-Mixin Teil des XDM-Schemas in Adobe Experience Platform sein.

Wechseln Sie zu [https://experience.adobe.com/platform](https://experience.adobe.com/platform) und melden Sie sich an.

![AEP-Debugger](./images/exp1.png)

Wählen Sie nach der Anmeldung die entsprechende Sandbox aus, indem Sie auf den Text **Produktions-**) in der blauen Zeile oben auf dem Bildschirm klicken. Wählen Sie die Sandbox-`--aepSandboxName--` aus.

Nachdem Sie Ihre Sandbox ausgewählt haben, ändert sich der Bildschirm, und Sie befinden sich nun in Ihrer Sandbox.

![AEP-Debugger](./images/exp2.png)

Wechseln Sie im linken Menü zu **Schemata** und öffnen Sie das Schema **Demosystem - Ereignisschema für Website (Global v1.1** .

![AEP-Debugger](./images/exp3.png)

In diesem Schema sehen Sie, dass die Feldergruppe **AEP Web SDK ExperienceEvent** hinzugefügt wurde. Diese Feldergruppe fügt alle minimal erforderlichen Felder zum Schema hinzu. Für jedes Erlebnisereignisschema in Adobe Experience Platform, das von Web SDK verwendet wird, muss diese Feldergruppe immer Teil des Schemas sein.

![AEP-Debugger](./images/exp4.png)

In [Modul 1](./../module1.2/data-ingestion.md)2 erfahren Sie, wie Sie Feldergruppen zu Schemata hinzufügen.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zum Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zurück zu „Alle Module“](./../../../overview.md)
