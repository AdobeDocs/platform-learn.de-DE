---
title: Adobe Experience Platform-Datenerfassung und serverseitige Weiterleitung in Echtzeit - Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Adobe Experience Platform-Datenerfassungsservereigenschaft verfügbar zu machen.
description: Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Adobe Experience Platform-Datenerfassungsservereigenschaft verfügbar zu machen.
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 1%

---

# 2.5.2 Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Adobe Experience Platform-Datenerfassungsservereigenschaft verfügbar zu machen.

## 2.5.2.1 Datenspeicher aktualisieren

In [Übung 0.2](./../../gettingstarted/gettingstarted/ex2.md) haben Sie Ihren eigenen **[!UICONTROL Datastream]** erstellt. Dann haben Sie den Namen `--demoProfileLdap-- - Demo System Datastream` verwendet.

In dieser Übung müssen Sie diesen **[!UICONTROL Datastream]** so konfigurieren, dass er mit Ihrem **[!DNL Data Collection Server property]** funktioniert.

Gehen Sie dazu zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Dann wirst du das sehen. Klicken Sie im linken Menü auf **[!UICONTROL Datastreams]**.

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxId--` lauten soll.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1b.png)

Suchen Sie nach Ihrem **[!UICONTROL Datastream]** mit dem Namen `--demoProfileLdap-- - Demo System Datastream`. Klicken Sie auf Ihren **[!UICONTROL Datastream]**, um ihn zu öffnen.

![WebSDK](./images/websdk0.png)

Dann wirst du das sehen. Klicken Sie auf **[!UICONTROL + Service hinzufügen]**.

![WebSDK](./images/websdk3.png)

Wählen Sie den Dienst **Ereignisweiterleitung** aus. Dadurch werden Ihnen zwei zusätzliche Einstellungen angezeigt. Wählen Sie Ihre Eigenschaft für die Ereignisweiterleitung aus, die Sie in der vorherigen Übung erstellt haben und die den Namen `--demoProfileLdap-- - Demo System (DD/MM/YYYY) (Edge)` trägt. Wählen Sie dann **Entwicklung** unter **Umgebung** aus. Klicken Sie auf **Speichern**.

![WebSDK](./images/websdk4.png)

Ihr Datastream wurde aktualisiert und kann jetzt verwendet werden.

![WebSDK](./images/websdk8a.png)

Ihr Datastream kann jetzt mit Ihrem **[!DNL Event Forwarding property]** verwendet werden.

Nächster Schritt: [2.5.3 Benutzerdefinierten Webhook erstellen und konfigurieren](./ex3.md)

[Zurück zu Modul 2.5](./aep-data-collection-ssf.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
