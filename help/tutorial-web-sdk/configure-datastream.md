---
title: Konfigurieren eines Datenstroms für Platform Web SDK
description: Erfahren Sie, wie Sie einen Datenstrom aktivieren und Experience Cloud-Lösungen konfigurieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Datastreams
jira: KT-15399
exl-id: 20f770d1-eb0f-41a9-b451-4069a0a91fc4
source-git-commit: a8431137e0551d1135763138da3ca262cb4bc4ee
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 9%

---

# Konfigurieren eines Datenstroms

Erfahren Sie, wie Sie einen Datastrom für das Adobe Experience Platform Web SDK konfigurieren.

[Datenströme](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/overview) teilen dem Adobe Experience Platform-Edge Network mit, wohin die von Platform Web SDK erfassten Daten gesendet werden sollen. In der Datenstromkonfiguration aktivieren Sie Ihre Experience Cloud-Anwendungen, Ihr Experience Platform-Konto und die Ereignisweiterleitung.

![Web-SDK, Datenströme und Edge Network-Diagramm](assets/dc-websdk-datastreams.png)

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen eines Datenspeichers
* Erste Schritte mit Datenstrom-Überschreibungen

## Voraussetzungen

Bevor Sie Ihren Datenstrom konfigurieren, müssen Sie die folgenden Lektionen bereits abgeschlossen haben:

* [Konfigurieren eines Schemas](configure-schemas.md)
* [Konfigurieren eines Identity-Namespace](configure-identities.md)

## Erstellen eines Datenspeichers

Jetzt können Sie einen Datenstrom erstellen, um Platform Edge Network mitzuteilen, wohin die von Web SDK erfassten Daten gesendet werden sollen.

**So erstellen Sie einen Datenstrom:**

1. Öffnen Sie die [Datenerfassungsschnittstelle](https://launch.adobe.com/){target="_blank"}
1. Stellen Sie sicher, dass Sie sich in der richtigen Sandbox befinden

   >[!NOTE]
   >
   >Wenn Sie Kunde eines plattformbasierten Programms wie Real-Time CDP oder Journey Optimizer sind, empfehlen wir, für dieses Tutorial eine Entwicklungs-Sandbox zu verwenden. Andernfalls verwenden Sie die **[!UICONTROL Prod]**-Sandbox.

1. Navigieren Sie **[!UICONTROL linken Navigationsbereich zu]** Datenströme“
1. Wählen Sie **[!UICONTROL Neuer Datenstrom]**
1. Geben Sie `Luma Web SDK: Development Environment` als **[!UICONTROL Name]** ein. Auf diesen Namen wird später verwiesen, wenn Sie die Web-SDK-Erweiterung in Ihrer Tag-Eigenschaft konfigurieren.
1. Wählen Sie **[!UICONTROL Speichern]**

   ![Erstellen des Datenstroms](assets/datastream-create-new-datastream.png)

   >[!NOTE]
   >
   >Sie müssen kein Schema auswählen. Eine Schemaauswahl ist nur erforderlich, wenn Sie die Funktion [Datenvorbereitung für die Datenerfassung](/help/data-collection/edge/data-prep.md) verwenden.

Auf dem nächsten Bildschirm können Sie dem Datenstrom Services wie Adobe-Anwendungen hinzufügen, Sie werden jedoch derzeit keine Services hinzufügen. Sie werden dies später im Abschnitt Lektionen [Einrichten von Experience Platform](setup-experience-platform.md), [Einrichten von Analytics](setup-analytics.md), [Einrichten von Audience Manager](setup-audience-manager.md), [Einrichten von Target](setup-target.md) oder [Ereignisweiterleitung](setup-event-forwarding.md).

>[!NOTE]
>
>Wenn Sie Platform Web SDK auf Ihrer eigenen Website implementieren, sollten Sie drei Datenströme erstellen, die Ihren drei Tag-Umgebungen (Entwicklung, Staging und Produktion) zugeordnet werden können. Wenn Sie Platform Web SDK mit plattformbasierten Anwendungen wie Adobe Real-time Customer Data Platform oder Adobe Journey Optimizer verwenden, sollten Sie sicherstellen, dass Sie diese Datenströme in den entsprechenden Platform-Sandboxes erstellen.

## Überschreiben eines Datenstroms

[Datenstromüberschreibungen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overrides) ermöglichen es Ihnen, zusätzliche Konfigurationen für Ihren Datenstrom zu definieren und dann Ihre Standardkonfiguration unter bestimmten Bedingungen zu überschreiben.

Die Überschreibung der Datenstromkonfiguration ist ein zweistufiger Prozess:

1. Zunächst definieren Sie Datenstrom-Überschreibungen in der Datenstrom-Service-Konfiguration. Sie können beispielsweise alternative Analytics-Report Suites, Target-Arbeitsbereiche oder Platform-Datensätze definieren, die als Überschreibungen verwendet werden sollen.
1. Anschließend senden Sie die Überschreibungen entweder mit einer Web SDK-Sendeereignisaktion oder durch eine Konfiguration in der Web SDK-Tag-Erweiterung an das Edge Network.

In der Lektion [Einrichten von Adobe Analytics](setup-analytics.md) überschreiben Sie die Report Suite für eine Seite mithilfe der Sendeereignisaktion von Platform Web SDK.

Jetzt können Sie die Platform Web SDK-Erweiterung in Ihrer Tag-Eigenschaft installieren!

[Weiter: ](install-web-sdk.md)

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League-Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
