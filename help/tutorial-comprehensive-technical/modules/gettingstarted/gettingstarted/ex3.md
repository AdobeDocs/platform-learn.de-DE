---
title: Erste Schritte - Erstellen Ihres Datastreams
description: Erste Schritte - Erstellen Ihres Datastreams
kt: 5342
doc-type: tutorial
source-git-commit: 7d2f5f842559b2d6d9f115f3993268a4b36a0fe0
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 1%

---

# 0.3 Datenspeicher erstellen

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Nach der vorherigen Übung verfügen Sie nun über zwei Datenerfassungseigenschaften: eine für Web und eine für Mobile.

![DSN](./images/launchprop.png)

Diese Eigenschaften können fast verwendet werden. Bevor Sie mit der Datenerfassung mit diesen Eigenschaften beginnen können, müssen Sie jedoch einen Datastream einrichten. Sie erhalten weitere Informationen über das Konzept, was ein Datastream ist und was es in Übung 1.2 bedeutet.

Befolgen Sie zunächst diese Schritte.

## 0.3.1 Erstellen Ihres Datenspeichers für Web

Klicken Sie auf **[!UICONTROL Datastreams]** oder **[!UICONTROL Datastreams (Beta)]**.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1a.png)

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxId--` lauten soll.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1b.png)

Klicken Sie auf **[!UICONTROL New Datastream]**.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1.png)

Geben Sie für den **[!UICONTROL Anzeigenamen]** und für die optionale Beschreibung `--demoProfileLdap-- - Demo System Datastream` ein. Wählen Sie für das Ereignisschema **Demo-System - Ereignisschema für Website (Global v1.1)** aus. Klicken Sie auf **Speichern**.

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

Klicken Sie in der Adobe Experience Platform Web SDK-Erweiterung auf **Konfigurieren**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig12.png)

Dann wirst du das sehen. Für **Datastreams** sehen Sie derzeit einen Platzhalterwert, der auf 1 gesetzt ist. Sie müssen jetzt auf das Optionsfeld **Aus Liste auswählen** klicken. Wählen Sie in der Dropdown-Liste den zuvor erstellten Datastream aus.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig13.png)

Stellen Sie sicher, dass Sie Ihren **Datastream** ausgewählt haben. TIPP: Sie können die Ergebnisse im Dropdown-Menü einfach filtern, indem Sie Ihren `--demoProfileLdap--` eingeben.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig14.png)

Scrollen Sie nach unten, bis **Datenerfassung** angezeigt wird. Stellen Sie sicher, dass das Kontrollkästchen für **Klick-Datenerfassung aktivieren** nicht aktiviert ist. Klicken Sie auf **Speichern** , um Ihre Änderungen zu speichern.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig14a.png)

Wechseln Sie zu **Veröffentlichungsfluss**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig15.png)

Klicken Sie auf den **...** für **Main** und klicken Sie dann auf **Bearbeiten**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig16.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und dann auf **Speichern und für Entwicklung erstellen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17.png)

Ihre Änderungen werden jetzt veröffentlicht und sind in einigen Minuten fertig.

## 0.3.2 Datenspeicher für Mobilgeräte erstellen

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

Klicken Sie auf **[!UICONTROL Datastreams]** oder **[!UICONTROL Datastreams (Beta)]**.

![Klicken Sie auf das Datastraam-Symbol in der linken Navigation](./images/edgeconfig1a.png)

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxId--` lauten soll.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1b.png)

Klicken Sie auf **[!UICONTROL New Datastream]**.

![Klicken Sie auf das Datastraam-Symbol in der linken Navigation](./images/edgeconfig1.png)

Geben Sie für den **[!UICONTROL Anzeigenamen]** und für die optionale Beschreibung `--demoProfileLdap-- - Demo System Datastream (Mobile)` ein. Wählen Sie für das Ereignisschema **Demo-System - Ereignisschema für mobile App (globale Version 1.1)** aus. Klicken Sie auf **Speichern**.

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

Klicken Sie in der Erweiterung **Adobe Experience Platform Edge Network** auf **Konfigurieren**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig12m.png)

Dann wirst du das sehen. Jetzt müssen Sie die richtige Sandbox und den korrekt konfigurierten Datastream auswählen. Die zu verwendende Sandbox ist `--aepSandboxId--` und der Datastream heißt `--demoProfileLdap-- - Demo System Datastream (Mobile)`.

Verwenden Sie für die **Edge Network-Domäne** die Standarddomäne **edge.adobedc.net**.

Klicken Sie auf **Speichern** , um Ihre Änderungen zu speichern.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig13m.png)

Wechseln Sie zu **Veröffentlichungsfluss**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig15m.png)

Klicken Sie auf den **...** neben **Main** und klicken Sie dann auf **Bearbeiten**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig16m.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und dann auf **Für Entwicklung speichern und erstellen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17m.png)

Ihre Änderungen werden jetzt veröffentlicht und sind in einigen Minuten fertig.

Nächster Schritt: [0.4 Website verwenden](./ex4.md)

[Zurück zu Modul 0](./getting-started.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)