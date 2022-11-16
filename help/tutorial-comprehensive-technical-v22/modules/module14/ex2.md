---
title: Adobe Experience Platform-Datenerfassung und serverseitige Weiterleitung in Echtzeit - Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Adobe Experience Platform-Datenerfassungsservereigenschaft verfügbar zu machen.
description: Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Adobe Experience Platform-Datenerfassungsservereigenschaft verfügbar zu machen.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 0c42350c-c38a-410e-bdab-41aff6024f81
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 14.2 Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Adobe Experience Platform-Datenerfassungsservereigenschaft verfügbar zu machen.

## 14.2.1 Datenspeicher aktualisieren

In [Übung 0.2](./../../modules/module0/ex2.md), haben Sie eine eigene **[!UICONTROL Datastream]**. Sie haben dann den Namen `--demoProfileLdap-- - Demo System Datastream`.

In dieser Übung müssen Sie Folgendes konfigurieren: **[!UICONTROL Datastream]** , um **[!DNL Data Collection Server property]**.

Gehen Sie dazu zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Dann wirst du das sehen. Klicken Sie im linken Menü auf **[!UICONTROL Datenspeicher]**.

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxId--`.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration .](./images/edgeconfig1b.png)

Suchen Sie nach Ihrer **[!UICONTROL Datastream]**, der `--demoProfileLdap-- - Demo System Datastream`. Klicken Sie auf **[!UICONTROL Datastream]** um es zu öffnen.

![WebSDK](./images/websdk0.png)

Dann wirst du das sehen. Klicken **[!UICONTROL + Dienst hinzufügen]**.

![WebSDK](./images/websdk3.png)

Wählen Sie den Dienst aus **Ereignisweiterleitung**. Dadurch werden Ihnen zwei zusätzliche Einstellungen angezeigt. Wählen Sie die Ereignisweiterleitungseigenschaft aus, die Sie in der vorherigen Übung erstellt haben und die den Namen hat `--demoProfileLdap-- - Demo System (DD/MM/YYYY) (Edge)`. Wählen Sie anschließend **Entwicklung** under **Umgebung**. Klicken Sie auf **Speichern**.

![WebSDK](./images/websdk4.png)

Ihr Datastream wurde aktualisiert und kann jetzt verwendet werden.

![WebSDK](./images/websdk8a.png)

Ihr Datastream kann jetzt mit Ihrem **[!DNL Event Forwarding property]**.

Nächster Schritt: [14.3 Benutzerdefinierten Webhook erstellen und konfigurieren](./ex3.md)

[Zurück zu Modul 14](./aep-data-collection-ssf.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
