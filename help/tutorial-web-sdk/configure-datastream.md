---
title: Konfigurieren eines Datenspeichers für das Platform Web SDK
description: Erfahren Sie, wie Sie einen Datastream aktivieren und Experience Cloud-Lösungen konfigurieren. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Web SDK,Datastreams
jira: KT-15399
exl-id: 20f770d1-eb0f-41a9-b451-4069a0a91fc4
source-git-commit: 8602110d2b2ddc561e45f201e3bcce5e6a6f8261
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 4%

---

# Konfigurieren eines Datenstroms

Erfahren Sie, wie Sie einen Datastream für das Adobe Experience Platform Web SDK konfigurieren.

[Datenspeicher](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview) teilen Adobe Experience Platform Edge Network mit, wohin vom Platform Web SDK erfasste Daten gesendet werden sollen. In der Konfiguration der Datenspeicher aktivieren Sie Ihre Experience Cloud-Anwendungen, Ihr Experience Platform-Konto und die Ereignisweiterleitung.

![Web SDK, Datenspeicher und Edge Network-Diagramm](assets/dc-websdk-datastreams.png)

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen eines Datenspeichers
* Erste Schritte mit Datastream-Überschreibungen

## Voraussetzungen

Bevor Sie Ihren Datastream konfigurieren, müssen Sie bereits die folgenden Lektionen abgeschlossen haben:

* [Schema konfigurieren](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)

## Erstellen eines Datenspeichers

Jetzt können Sie einen Datastream erstellen, um Platform Edge Network mitzuteilen, wohin vom Web SDK erfasste Daten gesendet werden sollen.

**So erstellen Sie einen Datastream:**

1. Öffnen Sie die [Datenerfassungsoberfläche](https://launch.adobe.com/){target="_blank"}
1. Vergewissern Sie sich, dass Sie sich in der richtigen Sandbox befinden

   >[!NOTE]
   >
   >Wenn Sie Platform-basierte Anwendungen wie Real-Time CDP oder Journey Optimizer nutzen, empfehlen wir für dieses Tutorial die Verwendung einer Entwicklungs-Sandbox. Wenn nicht, verwenden Sie die **[!UICONTROL Prod]** Sandbox.

1. Navigieren Sie zu **[!UICONTROL Datenspeicher]** in der linken Navigation
1. Auswählen **[!UICONTROL Neuer Datenspeicher]**
1. Eingabe `Luma Web SDK: Development Environment` als **[!UICONTROL Name]**. Dieser Name wird später referenziert, wenn Sie die Web SDK-Erweiterung in Ihrer Tag-Eigenschaft konfigurieren.
1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Erstellen des Datastreams](assets/datastream-create-new-datastream.png)

   >[!NOTE]
   >
   >Sie müssen nur ein Schema auswählen, wenn Sie die [Datenvorbereitung für die Datenerfassung](/help/data-collection/edge/data-prep.md) Funktion.

Auf dem nächsten Bildschirm können Sie Dienste wie Adobe-Anwendungen zum Datastream hinzufügen. Sie werden jedoch zu diesem Zeitpunkt im Tutorial keine Dienste hinzufügen. Sie werden dies später im Unterricht tun [Experience Platform einrichten](setup-experience-platform.md), [Einrichten von Analytics](setup-analytics.md), [Einrichten von Audience Manager](setup-audience-manager.md), [Einrichten von Target](setup-target.md)oder [Ereignisweiterleitung](setup-event-forwarding.md).

>[!NOTE]
>
>Bei der Implementierung des Platform Web SDK auf Ihrer eigenen Website sollten Sie drei Datenspeicher erstellen, die Ihren drei Tag-Umgebungen (Entwicklung, Staging und Produktion) zugeordnet werden. Wenn Sie das Platform Web SDK mit Platform-basierten Anwendungen wie Adobe Real-time Customer Data Platform oder Adobe Journey Optimizer verwenden, sollten Sie sicherstellen, dass Sie diese Datenspeicher in den entsprechenden Platform-Sandboxes erstellen.

## Überschreiben eines Datastreams

[Datenspeicherüberschreibungen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overrides) ermöglichen es Ihnen, zusätzliche Konfigurationen für Ihren Datenspeicher zu definieren und dann Ihre Standardkonfiguration unter bestimmten Bedingungen zu überschreiben.

Die Außerkraftsetzung der Datastream-Konfiguration erfolgt in zwei Schritten:

1. Zunächst definieren Sie in der Konfiguration des Datastream-Dienstes Überschreibungen von Datastream. Sie können beispielsweise alternative Analytics Report Suites, Target-Arbeitsbereiche oder Platform-Datensätze definieren, die als Überschreibungen verwendet werden sollen.
1. Anschließend senden Sie die Überschreibungen entweder mit einer Web SDK-Sendeereignisaktion oder durch eine Konfiguration in der Web SDK-Tag-Erweiterung an das Edge Network.

Im [Einrichten von Adobe Analytics](setup-analytics.md) -Lektion verwenden, überschreiben Sie die Report Suite für eine Seite mit der Ereignis-Aktion für das Senden des Platform Web SDK.

Sie können jetzt die Platform Web SDK-Erweiterung in Ihrer Tag-Eigenschaft installieren!

[Weiter: ](install-web-sdk.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
