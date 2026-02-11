---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - XDM-Schemaanforderungen in Adobe Experience Platform
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - XDM-Schemaanforderungen in Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 124c9c54-27f1-4784-9a5c-2c9d8ba620d5
source-git-commit: 23816907de778cbe3b9708f4a7273bdcb8e86d5c
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# 1.1.7 XDM-Schemaanforderungen in Adobe Experience Platform

Um sicherzustellen, dass Web SDK Daten in Adobe Experience Platform aufnehmen kann, muss ein bestimmtes XDM-Mixin Teil des XDM-Schemas in Adobe Experience Platform sein.

Wechseln Sie zu [https://experience.adobe.com/platform](https://experience.adobe.com/platform) und melden Sie sich an.

![AEP Debugger](./images/exp1.png)

Wählen Sie nach der Anmeldung die entsprechende Sandbox aus, indem Sie auf den Text **Produktions-**) in der blauen Zeile oben auf dem Bildschirm klicken. Wählen Sie die Sandbox-`--aepSandboxName--` aus.

Nachdem Sie Ihre Sandbox ausgewählt haben, ändert sich der Bildschirm, und Sie befinden sich nun in Ihrer Sandbox.

![AEP Debugger](./images/exp2.png)

Wechseln Sie im linken Menü zu **Schemata** und öffnen Sie das Schema **Demosystem - Ereignisschema für Website (Global v1.1** .

![AEP Debugger](./images/exp3.png)

In diesem Schema sehen Sie, dass die Feldergruppe **AEP Web SDK ExperienceEvent** hinzugefügt wurde. Diese Feldergruppe fügt alle minimal erforderlichen Felder zum Schema hinzu. Für jedes Erlebnisereignisschema in Adobe Experience Platform, das von Web SDK verwendet wird, muss diese Feldergruppe immer Teil des Schemas sein.

![AEP Debugger](./images/exp4.png)

In [Modul 1.2 Datenaufnahme](./../dc1.2/data-ingestion.md) erfahren Sie, wie Sie Feldergruppen zu Schemata hinzufügen.

Nächster Schritt:

## Nächste Schritte

Kehren Sie zurück zu [Einrichtung der Adobe Experience Platform-Datenerfassung und der Tag-Erweiterung „Web SDK&quot;](./data-ingestion-launch-web-sdk.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
