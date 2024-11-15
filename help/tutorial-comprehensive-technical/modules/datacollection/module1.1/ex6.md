---
title: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Implementieren von Adobe Target
description: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Implementieren von Adobe Target
kt: 5342
doc-type: tutorial
exl-id: 475e9a34-c80e-41e4-9660-61c79f26922d
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# 1.1.6 Adobe Target implementieren

## 1.1.6.1 Datenspeicher für die Verwendung von Adobe Target aktualisieren

Wenn Sie vom Web SDK erfasste Daten an Adobe Target senden und eine Antwort von Adobe Target mit einem personalisierten Erlebnis für jeden Kunden erhalten möchten, führen Sie die folgenden Schritte aus.

Wechseln Sie zu [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) und gehen Sie zu **Datastreams**.

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` lauten soll. Öffnen Sie Ihren spezifischen Datastream mit dem Namen `--aepUserLdap-- - Demo System Datastream`.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1b.png)

Dann wirst du das sehen. Um Adobe Target zu aktivieren, klicken Sie auf **+Dienst hinzufügen**.

![AEP-Debugger](./images/aa2.png)

Dann wirst du das sehen. Wählen Sie den Dienst **Adobe Target** aus, nach dem Sie optional zusätzliche Informationen angeben können. Klicken Sie auf **Speichern**.

![AEP-Debugger](./images/at1.png)

Nächster Schritt: [1.1.7 XDM-Schema-Anforderungen in Adobe Experience Platform](./ex7.md)

[Zurück zu Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
