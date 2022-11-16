---
title: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Implementieren von Adobe Target
description: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Implementieren von Adobe Target
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 4aee8ae2-38ca-49a3-8f1b-57713d16f5b5
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# 1.6 Adobe Target implementieren

## 1.6. Aktualisieren Sie Ihr Datastream für die Verwendung von Adobe Target

Wenn Sie vom Web SDK erfasste Daten an Adobe Target senden und eine Antwort von Adobe Target mit einem personalisierten Erlebnis für jeden Kunden erhalten möchten, führen Sie die folgenden Schritte aus.

Navigieren Sie zu [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) und gehen Sie zu **Datenspeicher**.

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxId--`. Öffnen Sie Ihren spezifischen Datastream mit dem Namen `--demoProfileLdap-- - Demo System Datastream`.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration .](./images/edgeconfig1b.png)

Dann wirst du das sehen. Um Adobe Target zu aktivieren, klicken Sie auf **+Dienst hinzufügen**.

![AEP Debugger](./images/aa2.png)

Dann wirst du das sehen. Wählen Sie den Dienst aus **Adobe Target**, nach dem Sie optional zusätzliche Informationen angeben können. Im Moment ist es nicht erforderlich, dies zu speichern. Klicken Sie daher auf **Abbrechen**.

![AEP Debugger](./images/at1.png)

Nächster Schritt: [1.7 XDM-Schema-Anforderungen in Adobe Experience Platform](./ex7.md)

[Zurück zu Modul 1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
