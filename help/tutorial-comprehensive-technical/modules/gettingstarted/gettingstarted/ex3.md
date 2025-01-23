---
title: Erste Schritte - Erstellen Ihres Datenstroms
description: Erste Schritte - Erstellen Ihres Datenstroms
kt: 5342
doc-type: tutorial
exl-id: b3e6f66d-fb7a-43ab-aedb-45141af76d3e
source-git-commit: 007e35504d19c332da39d90d65f34960aaa9c09b
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 1%

---

# Erstellen eines Datenstroms

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

![DSN](./images/launchprop.png)

Klicken Sie im linken Menü auf &quot;**[!UICONTROL &quot;]**. Nach der vorherigen Übung verfügen Sie jetzt über drei Datenerfassungseigenschaften: eine für das Web, eine für Mobilgeräte und eine für CX-Mobile-Apps.

![DSN](./images/launchprop1.png)

Diese Eigenschaften sind fast einsatzbereit. Bevor Sie jedoch mit der Datenerfassung mit diesen Eigenschaften beginnen können, müssen Sie einen Datenstrom einrichten. In einer späteren Übung im Datenerfassungsmodul erfahren Sie mehr darüber, was ein Datenstrom ist und was er bedeutet.

Führen Sie zunächst die folgenden Schritte aus.

## Erstellen eines Datenstroms für das Web

Klicken Sie **[!UICONTROL Datenströme]**.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration ](./images/edgeconfig1a.png)

Wählen Sie oben rechts im Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` werden soll.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration ](./images/edgeconfig1b.png)

Klicken Sie **[!UICONTROL Neuer Datenstrom]**.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration ](./images/edgeconfig1.png)

Geben **[!UICONTROL als]** und als optionale Beschreibung `--aepUserLdap-- - Demo System Datastream` ein. Wählen Sie **Zuordnungsschema** die Option **Demosystem - Ereignisschema für Website (Global v1.1)**. Klicken Sie auf **Speichern**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig2.png)

Sie werden es dann sehen. Klicken Sie **Service hinzufügen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig3.png)

Wählen Sie den Dienst **[!UICONTROL Adobe Experience Platform]** aus, wodurch zusätzliche Felder angezeigt werden. Sie werden es dann sehen.

Wählen Sie für den Ereignisdatensatz die Option **Demosystem - Ereignisdatensatz für die Website (Global v1.1)** und für den Profildatensatz die Option **Demosystem - Profildatensatz für die Website (Global v1.1)**. Klicken Sie auf **Speichern**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig4.png)

Das wirst du jetzt sehen.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig5.png)

Das war&#39;s fürs Erste. In [Modul 1](./../../../modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md)1 erfahren Sie mehr über Web SDK und darüber, wie Sie alle zugehörigen Funktionen konfigurieren können.

Klicken Sie im linken Menü auf &quot;**[!UICONTROL &quot;]**.

Filtern Sie die Suchergebnisse, um Ihre Datenerfassungseigenschaften anzuzeigen. Öffnen Sie die Eigenschaft für **Web** durch Klicken.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig10a.png)

Sie werden es dann sehen. Klicken Sie **Erweiterungen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig11.png)

Klicken Sie zunächst auf die Adobe Experience Platform Web SDK-Erweiterung und dann auf **Konfigurieren**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig12.png)

Sie werden es dann sehen. Sehen Sie sich das Menü **Datenströme** an und stellen Sie sicher, dass die richtige Sandbox ausgewählt ist, was in Ihrem Fall `--aepSandboxName--` werden sollte.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig12a.png)

Öffnen Sie das **Datenströme** und wählen Sie den zuvor erstellten Datenstrom aus.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig13.png)

Stellen Sie sicher, dass Sie Ihren **Datenstrom** in allen drei verschiedenen Umgebungen ausgewählt haben. Klicken Sie dann auf **Speichern**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig14.png)

Navigieren Sie **Veröffentlichungsfluss**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig15.png)

Klicken Sie auf **…** für **Main** und dann auf **Bearbeiten**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig16.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und anschließend auf **Für Entwicklung speichern und erstellen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17.png)

Ihre Änderungen werden jetzt veröffentlicht und sind in einigen Minuten bereit. Danach wird der grüne Punkt neben &quot;**&quot;**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17a.png)

## Erstellen eines Datenstroms für Mobilgeräte

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

Klicken Sie **[!UICONTROL Datenströme]**.

![Klicken Sie im linken Navigationsbereich auf das Datenstrom -Symbol](./images/edgeconfig1a.png)

Wählen Sie oben rechts im Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` werden soll.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration ](./images/edgeconfig1b.png)

Klicken Sie **[!UICONTROL Neuer Datenstrom]**.

![Klicken Sie im linken Navigationsbereich auf das Datenstrom -Symbol](./images/edgeconfig1.png)

Geben **[!UICONTROL als Anzeigename]** als optionale Beschreibung `--aepUserLdap-- - Demo System Datastream (Mobile)` ein. Wählen Sie **Zuordnungsschema** die Option **Demosystem - Ereignisschema für Mobile App (Global v1.1)**. Klicken Sie auf **Speichern**.

Klicken Sie auf **[!UICONTROL Speichern]**.

![Benennen Sie den Datenstrom und speichern Sie ihn](./images/edgeconfig2m.png)

Sie werden es dann sehen. Klicken Sie **Service hinzufügen**.

![Benennen Sie den Datenstrom und speichern Sie ihn](./images/edgeconfig3m.png)

Wählen Sie den Dienst **[!UICONTROL Adobe Experience Platform]** aus, wodurch zusätzliche Felder angezeigt werden. Sie werden es dann sehen.

Wählen Sie für den Ereignisdatensatz **Demosystem - Ereignisdatensatz für die Mobile App (Global v1.1)** und für den Profildatensatz **Demosystem - Profildatensatz für die Mobile App (Global v1.1)**. Klicken Sie auf **Speichern**.

![Benennen Sie die Datenstromkonfiguration und speichern Sie sie](./images/edgeconfig4m.png)

Sie werden es dann sehen.

![Benennen Sie die Datenstromkonfiguration und speichern Sie sie](./images/edgeconfig5m.png)

Ihr Datenstrom kann jetzt in Ihrer Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft für Mobilgeräte verwendet werden.

Navigieren Sie **Tags** und filtern Sie die Suchergebnisse, um Ihre Datenerfassungseigenschaften anzuzeigen. Öffnen Sie die Eigenschaft für **Mobile**, indem Sie darauf klicken.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig10am.png)

Sie werden es dann sehen. Klicken Sie **Erweiterungen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig11m.png)

Klicken Sie auf die Erweiterung **Adobe Experience PlatformEdge Network** und dann auf **Konfigurieren**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig12m.png)

Sie werden es dann sehen. Jetzt müssen Sie die richtige Sandbox und den richtigen Datenstrom auswählen, die Sie gerade konfiguriert haben. Die zu verwendende Sandbox wird `--aepSandboxName--` und der Datenstrom heißt `--aepUserLdap-- - Demo System Datastream (Mobile)`.

Für die **Edge Network-Domain** verwenden Sie die Standard-Domain.

Klicken Sie **Speichern**, um Ihre Änderungen zu speichern.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig13m.png)

Navigieren Sie **Veröffentlichungsfluss**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig15m.png)

Klicken Sie auf **…** neben **Main** und dann auf **Edit**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig16m.png)

Klicken Sie **Alle geänderten Ressourcen hinzufügen** und anschließend auf **Für Entwicklung speichern und erstellen**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17m.png)

Ihre Änderungen werden jetzt veröffentlicht und sind in einigen Minuten bereit. Danach wird der grüne Punkt neben &quot;**&quot;**.

![Benennen Sie die Edge-Konfiguration und speichern Sie](./images/edgeconfig17ma.png)

Nächster Schritt: [Verwenden der Website](./ex4.md)

[Zurück zu den ersten Schritten](./getting-started.md)

[Zurück zu „Alle Module“](./../../../overview.md)
