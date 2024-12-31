---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Edge Network, Datenströme und Server-seitige Datenerfassung
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Edge Network, Datenströme und Server-seitige Datenerfassung
kt: 5342
doc-type: tutorial
exl-id: e97d40b5-616d-439c-9d6b-eaa4ebf5acb0
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# 1.1.2 Edge Network, Datenströme und Server-seitige Datenerfassung

## Kontext

In dieser Übung erstellen Sie einen **Datenstrom**. Ein **Datenstrom** teilt den Adobe Edge-Servern mit, wohin die Daten gesendet werden sollen, nachdem sie von Web SDK erfasst wurden. Möchten Sie beispielsweise die Daten an Adobe Experience Platform senden? Adobe Analytics? Adobe Audience Manager? Adobe Target?

Datenströme werden immer in der Datenerfassungs-Benutzeroberfläche von Adobe Experience Platform verwaltet und sind für die Datenerfassung von Adobe Experience Platform mit Web SDK von entscheidender Bedeutung. Selbst wenn Sie Web SDK mit einer Nicht-Adobe-Tag-Management-Lösung implementieren, müssen Sie weiterhin Ihren Datenstrom in der Benutzeroberfläche der Datenerfassung von Adobe Experience Platform erstellen.

In der nächsten Übung implementieren Sie die Web-SDK im Browser. Dann wird Ihnen klarer werden, wie die erfassten Daten aussehen. Vorerst teilen wir dem Datenstrom lediglich mit, wohin er die Daten weiterleiten soll.

## Erstellen eines Datenstroms

In [Erste Schritte](./../../../modules/gettingstarted/gettingstarted/ex2.md) haben Sie bereits einen Datenstrom erstellt, aber wir haben die Hintergründe und den Grund für die Verwendung des Datenstroms nicht besprochen.

Ein Datenstrom teilt den Adobe Edge-Servern mit, wohin sie die Daten senden sollen, nachdem sie von der Web-SDK erfasst wurden. Möchten Sie beispielsweise die Daten an Adobe Experience Platform senden? Adobe Analytics? Adobe Audience Manager? Adobe Target? Datenströme werden in der Datenerfassungs-Benutzeroberfläche von Adobe Experience Platform verwaltet und sind für die Datenerfassung mit Web SDK von entscheidender Bedeutung, unabhängig davon, ob Sie Web SDK über die Datenerfassung von Adobe Experience Platform implementieren oder nicht.

Überprüfen wir Ihren **[!UICONTROL Datenstrom]**:

Navigieren Sie zu [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/).

Klicken Sie **[!UICONTROL linken Menü auf]** Datenströme“.

![Klicken Sie im linken Navigationsbereich auf das Datenstrom -Symbol](./images/edgeconfig1.png)

Öffnen Sie Ihren Datenstrom mit dem Namen `--aepUserLdap-- - Demo System Datastream`.

![Benennen Sie den Datenstrom und speichern Sie ihn](./images/edgeconfig2.png)

Anschließend werden die Details Ihres Datenstroms angezeigt.

![Benennen Sie den Datenstrom und speichern Sie ihn](./images/edgecfg1.png)

Klicken Sie auf **…** neben **Adobe Experience Platform** und klicken Sie auf **Bearbeiten**.

![Benennen Sie den Datenstrom und speichern Sie ihn](./images/edgecfg1a.png)

Sie werden es dann sehen. Derzeit haben Sie nur Adobe Experience Platform aktiviert. Ihre Konfiguration sieht in etwa wie folgt aus: (Je nach Umgebung und Adobe Experience Platform-Instanz kann der Sandbox-Name anders lauten.)

![Benennen Sie den Datenstrom und speichern Sie ihn](./images/edgecfg2.png)

Die folgenden Felder sollten folgendermaßen interpretiert werden:

Für diesen Datenstrom…

- Alle erfassten Daten werden in der `--aepSandboxName--` Sandbox in Adobe Experience Platform gespeichert
- Alle Erlebnisereignisdaten werden standardmäßig im Datensatz erfasst **Demosystem - Ereignisdatensatz für die Website (Global v1.1)**
- Alle Profildaten werden standardmäßig im Datensatz erfasst **Demosystem - Profildatensatz für Website (Global v1.1)** (die native Aufnahme von Profildaten in Web SDK wird derzeit von Web SDK noch nicht unterstützt)
- Wenn Sie den Anwendungsdienst **Offer decisioning** für diesen Datenstrom verwenden möchten, müssen Sie das Kontrollkästchen für das Offer decisioning aktivieren. (Dies ist Teil von [Modul 3.3](./../../../modules/ajo-b2c/module3.3/offer-decisioning.md))
- **Edge-**: ist standardmäßig aktiviert, d. h., dass qualifizierte Zielgruppen bei der Aufnahme von eingehendem Traffic am Edge ausgewertet werden
- Wenn Sie die **Personalization-Ziele** verwenden möchten, müssen Sie das Kontrollkästchen für Personalization-Ziele aktivieren.
- 
   - Wenn Sie die Funktionen von **Adobe Journey Optimizer** in diesem Datenstrom verwenden möchten, müssen Sie das Kontrollkästchen für Adobe Journey Optimizer aktivieren.


Für Ihren Datenstrom ist derzeit keine andere Konfiguration erforderlich.

Nächster Schritt: [1.1.3 Einführung in die Datenerfassung in Adobe Experience Platform](./ex3.md)

[Zurück zum Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zurück zu „Alle Module“](./../../../overview.md)
