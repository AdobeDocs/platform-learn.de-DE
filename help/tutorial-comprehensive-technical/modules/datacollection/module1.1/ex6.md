---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Implementieren von Adobe Target
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Implementieren von Adobe Target
kt: 5342
doc-type: tutorial
exl-id: 475e9a34-c80e-41e4-9660-61c79f26922d
source-git-commit: 1526661a80b4d551627dfca42a7e97c9498dd1f2
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---

# 1.1.6 Implementieren von Adobe Target

## Aktualisieren Ihres Datenstroms zur Verwendung von Adobe Target

Wenn Sie von Web SDK erfasste Daten an Adobe Target senden und von Adobe Target eine Antwort mit einem personalisierten Erlebnis für jeden Kunden erhalten möchten, führen Sie die folgenden Schritte aus.

Wechseln Sie zu [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) und dann zu **Datenströme**.

Wählen Sie oben rechts im Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` werden soll. Öffnen Sie Ihren spezifischen Datenstrom mit dem Namen `--aepUserLdap-- - Demo System Datastream`.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration ](./images/edgeconfig1b.png)

Sie werden es dann sehen. Um Adobe Target zu aktivieren, klicken Sie auf **Service hinzufügen**.

![AEP-Debugger](./images/aa2.png)

Sie werden es dann sehen. Wählen Sie den Dienst **Adobe Target** aus, nach dem Sie optional zusätzliche Informationen angeben können. Klicken Sie auf **Speichern**.

![AEP-Debugger](./images/at1.png)

Nächster Schritt: [1.1.7 XDM-Schemaanforderungen in Adobe Experience Platform](./ex7.md)

[Zurück zum Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zurück zu „Alle Module“](./../../../overview.md)
