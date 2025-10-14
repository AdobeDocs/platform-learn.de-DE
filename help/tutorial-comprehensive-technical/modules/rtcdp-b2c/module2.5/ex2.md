---
title: 'Adobe Experience Platform-Datenerfassung und Server-seitige Echtzeit-Weiterleitung : Aktualisieren Sie Ihren Datenstrom, um Daten für Ihre Adobe Experience Platform-Datenerfassungsserver-Eigenschaft verfügbar zu machen'
description: Aktualisieren Sie Ihren Datenstrom, um Daten für Ihre Adobe Experience Platform-Datenerfassungsserver-Eigenschaft verfügbar zu machen.
kt: 5342
doc-type: tutorial
exl-id: 7b5b598e-e54c-4f0f-b260-d643600ee6ca
source-git-commit: 6485bfa1c75c43bb569f77c478a273ace24a61d4
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 1%

---

# 2.5.2 Aktualisieren Sie Ihren Datenstrom, um Daten für Ihre Adobe Experience Platform-Datenerfassungsserver-Eigenschaft verfügbar zu machen

## Aktualisieren des Datenstroms

In [Erste Schritte](./../../gettingstarted/gettingstarted/ex2.md) haben Sie Ihren eigenen **[!UICONTROL Datenstrom]** erstellt. Sie haben dann den Namen `--aepUserLdap-- - Demo System Datastream` verwendet.

In dieser Übung müssen Sie diesen **[!UICONTROL Datenstrom) so konfigurieren]** dass er mit Ihrer **Datenerfassungs-Server-Eigenschaft)**.

Navigieren Sie dazu zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Sie werden es dann sehen. Klicken Sie im linken Menü auf **[!UICONTROL Datenströme]**.

Wählen Sie oben rechts im Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` werden soll.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration &#x200B;](./images/edgeconfig1b.png)

Suchen Sie nach Ihrem **[!UICONTROL Datenstrom]**, der `--aepUserLdap-- - Demo System Datastream` heißt. Klicken Sie auf **[!UICONTROL Datenstrom]**, um ihn zu öffnen.

![WebSDK](./images/websdk0.png)

Sie werden es dann sehen. Klicken Sie auf **[!UICONTROL + Service hinzufügen]**.

![WebSDK](./images/websdk3.png)

Wählen Sie den Service **Ereignisweiterleitung** aus. Dadurch werden zwei zusätzliche Einstellungen angezeigt. Wählen Sie die in der vorherigen Übung erstellte Ereignisweiterleitungseigenschaft mit dem Namen `--aepUserLdap-- - Demo System (DD/MM/YYYY) (Edge)` aus. Wählen Sie dann **Entwicklung** unter **Umgebung** aus. Klicken Sie auf **Speichern**.

![WebSDK](./images/websdk4.png)

Ihr Datenstrom wurde jetzt aktualisiert und ist einsatzbereit.

![WebSDK](./images/websdk8a.png)

Ihr Datenstrom ist jetzt für die Arbeit mit Ihrem **[!DNL Event Forwarding property]** bereit.

Nächster Schritt: [2.5.3 Erstellen und konfigurieren Sie einen benutzerdefinierten Webhook](./ex3.md)

[Zurück zum Modul 2.5](./aep-data-collection-ssf.md)

[Zurück zu „Alle Module“](./../../../overview.md)
