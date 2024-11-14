---
title: Erste Schritte - Erstellen Ihres Datastreams
description: Erste Schritte - Erstellen Ihres Datastreams
kt: 5342
doc-type: tutorial
exl-id: b3e6f66d-fb7a-43ab-aedb-45141af76d3e
source-git-commit: 7f436f77ab6d7c625181304fd41be75c627c5b46
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 1%

---

# Erstellen Ihres Datenspeichers

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

![DSN](./images/launchprop.png)

Klicken Sie im linken Menü auf **[!UICONTROL Tags]**. Nach der vorherigen Übung verfügen Sie nun über zwei Datenerfassungseigenschaften: eine für Web und eine für Mobile.

![DSN](./images/launchprop1.png)

Diese Eigenschaften können fast verwendet werden. Bevor Sie mit der Datenerfassung mit diesen Eigenschaften beginnen können, müssen Sie jedoch einen Datastream einrichten. Weitere Informationen dazu, was ein Datastream ist und was es bedeutet, erhalten Sie in einer späteren Übung im Datenerfassungsmodul.

Befolgen Sie zunächst diese Schritte.

## Erstellen Ihres Datenspeichers für das Web

Klicken Sie auf **[!UICONTROL Datastreams]**.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1a.png)

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` lauten soll.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1b.png)

Klicken Sie auf **[!UICONTROL New Datastream]**.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1.png)

Geben Sie für den **[!UICONTROL Namen]** und für die optionale Beschreibung `--aepUserLdap-- - Demo System Datastream` ein. Wählen Sie für **Zuordnungsschema** **Demo-System - Ereignisschema für Website (Global v1.1)** aus. Klicken Sie auf **Speichern**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig2.png)

Dann wirst du das sehen. Klicken Sie auf **Dienst hinzufügen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig3.png)

Wählen Sie den Dienst **[!UICONTROL Adobe Experience Platform]** aus, der zusätzliche Felder verfügbar macht. Dann wirst du das sehen.

Wählen Sie für &quot;Ereignis-Datensatz&quot;die Option **Demo-System - Ereignis-Datensatz für Website (Global v1.1)** und wählen Sie für den Profildatensatz **Demo-System - Profildatensatz für Website (Global v1.1)**. Klicken Sie auf **Speichern**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig4.png)

Das wirst du jetzt sehen.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig5.png)

Das ist es vorerst. In [Modul 1.1](./../../../modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md) erfahren Sie mehr über das Web SDK und die Konfiguration aller seiner Funktionen.

Klicken Sie im linken Menü auf **[!UICONTROL Tags]**.

Filtern Sie die Suchergebnisse, um Ihre beiden Datenerfassungseigenschaften anzuzeigen. Öffnen Sie die Eigenschaft für **Web**, indem Sie darauf klicken.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig10a.png)

Dann wirst du das sehen. Klicken Sie auf **Erweiterungen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig11.png)

Klicken Sie zuerst auf die Adobe Experience Platform Web SDK-Erweiterung und dann auf **Konfigurieren**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig12.png)

Dann wirst du das sehen. Machen Sie sich mit dem Menü **Datastreams** vertraut und stellen Sie sicher, dass die richtige Sandbox ausgewählt ist, die in diesem Fall `--aepSandboxName--` sein sollte.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig12a.png)

Öffnen Sie das Dropdown-Menü **Datastreams** und wählen Sie den zuvor erstellten Datastream aus.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig13.png)

Stellen Sie sicher, dass Sie Ihren **Datastream** in allen drei verschiedenen Umgebungen ausgewählt haben. Klicken Sie dann auf **Speichern**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig14.png)

Wechseln Sie zu **Veröffentlichungsfluss**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig15.png)

Klicken Sie auf den **...** für **Main** und klicken Sie dann auf **Bearbeiten**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig16.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und dann auf **Speichern und für Entwicklung erstellen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17.png)

Ihre Änderungen werden jetzt veröffentlicht und sind in einigen Minuten fertig. Danach wird der grüne Punkt neben **Main** angezeigt.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17a.png)

## Erstellen Ihres Datenspeichers für Mobilgeräte

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

Klicken Sie auf **[!UICONTROL Datastreams]**.

![Klicken Sie auf das Datastraam-Symbol in der linken Navigation](./images/edgeconfig1a.png)

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` lauten soll.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1b.png)

Klicken Sie auf **[!UICONTROL New Datastream]**.

![Klicken Sie auf das Datastraam-Symbol in der linken Navigation](./images/edgeconfig1.png)

Geben Sie für den **[!UICONTROL Anzeigenamen]** und für die optionale Beschreibung `--aepUserLdap-- - Demo System Datastream (Mobile)` ein. Wählen Sie für **Zuordnungsschema** **Demo-System - Ereignisschema für mobile App (globale Version 1.1)** aus. Klicken Sie auf **Speichern**.

Klicken Sie auf **[!UICONTROL Speichern]**.

![Benennen Sie den Datastream und speichern Sie](./images/edgeconfig2m.png)

Dann wirst du das sehen. Klicken Sie auf **Dienst hinzufügen**.

![Benennen Sie den Datastream und speichern Sie](./images/edgeconfig3m.png)

Wählen Sie den Dienst **[!UICONTROL Adobe Experience Platform]** aus, der zusätzliche Felder verfügbar macht. Dann wirst du das sehen.

Wählen Sie für &quot;Ereignis-Datensatz&quot;die Option &quot;**Demo-System - Ereignis-Datensatz für mobile App (Global v1.1)**&quot;und wählen Sie für den Profildatensatz &quot;**Demo-System - Profildatensatz für mobile App (Global v1.1)**&quot;. Klicken Sie auf **Speichern**.

![Benennen Sie die Datastream-Konfiguration und speichern Sie](./images/edgeconfig4m.png)

Dann wirst du das sehen.

![Benennen Sie die Datastream-Konfiguration und speichern Sie](./images/edgeconfig5m.png)

Ihr Datastream kann jetzt in Ihrer Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft für Mobile verwendet werden.

Navigieren Sie zu **Tags** und filtern Sie die Suchergebnisse, um Ihre beiden Datenerfassungseigenschaften anzuzeigen. Öffnen Sie die Eigenschaft für **Mobile**, indem Sie darauf klicken.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig10am.png)

Dann wirst du das sehen. Klicken Sie auf **Erweiterungen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig11m.png)

Klicken Sie auf die Erweiterung **Adobe Experience Platform Edge Network** und dann auf **Konfigurieren**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig12m.png)

Dann wirst du das sehen. Jetzt müssen Sie die richtige Sandbox und den korrekt konfigurierten Datastream auswählen. Die zu verwendende Sandbox ist `--aepSandboxName--` und der Datastream heißt `--aepUserLdap-- - Demo System Datastream (Mobile)`.

Verwenden Sie für die **Edge Network-Domäne** die Standarddomäne.

Klicken Sie auf **Speichern** , um Ihre Änderungen zu speichern.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig13m.png)

Wechseln Sie zu **Veröffentlichungsfluss**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig15m.png)

Klicken Sie auf den **...** neben **Main** und klicken Sie dann auf **Bearbeiten**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig16m.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und dann auf **Für Entwicklung speichern und erstellen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17m.png)

Ihre Änderungen werden jetzt veröffentlicht und sind in einigen Minuten fertig. Danach wird der grüne Punkt neben **Main** angezeigt.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17ma.png)

Nächster Schritt: [Verwenden der Website](./ex4.md)

[Zurück zu den ersten Schritten](./getting-started.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
