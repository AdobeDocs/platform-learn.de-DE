---
title: Konfigurieren eines Datenstroms für Implementierungen von Platform Mobile SDK
description: Erfahren Sie, wie Sie in Adobe Experience Platform einen Datenstrom erstellen können.
feature: Mobile SDK,Datastreams
jira: KT-14625
exl-id: 7b83f834-d1fb-45d1-8bcf-bc621f94725c
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 7%

---

# Erstellen eines Datenspeichers

Erfahren Sie, wie Sie in Adobe Experience Platform einen Datenstrom erstellen können.

Ein Datenstrom ist eine Server-seitige Konfiguration auf dem Platform-Edge Network. Der Datenstrom stellt sicher, dass eingehende Daten an das Platform-Edge Network ordnungsgemäß an Adobe Experience Cloud-Programme und -Services weitergeleitet werden. Weitere Informationen finden Sie in der [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de) oder in diesem [Video](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/configure-datastreams.html?lang=de).

![Architektur](assets/architecture.png)

## Voraussetzungen

Um einen Datenstrom zu erstellen, muss Ihre Organisation für diese Funktion in der Datenerfassungsoberfläche (früher [!UICONTROL Launch]) ausgestattet sein und Sie müssen über Benutzerberechtigungen zum Verwalten und Anzeigen von Datenströmen verfügen.

## Lernziele

In dieser Lektion erfahren Sie Folgendes:

* Wissen, wann ein Datenstrom verwendet werden soll.
* Erstellen eines Datenstroms.
* Konfigurieren eines Datenstroms.

## Erstellen eines Datenspeichers

Datenströme können in der Benutzeroberfläche [!UICONTROL Datenerfassung) mithilfe ] Konfigurations-Tools [!UICONTROL Datenstrom] erstellt werden. So erstellen Sie einen Datenstrom:

1. Stellen Sie sicher, dass Sie sich in der richtigen Experience Platform-Sandbox befinden, da Datenströme auf Sandbox-Ebene definiert sind.
1. Wählen **[!UICONTROL Datenströme]** in der linken Leiste aus.
1. Wählen Sie **[!UICONTROL Neuer Datenstrom]** aus.

   ![Datenströme - Startseite](assets/datastream-new.png)

1. Geben Sie einen **[!UICONTROL Namen]**, z. B. `Luma Mobile App`, und einen **[!UICONTROL Beschreibung]**, z. B. `Datastream for Luma Mobile App`, an.

   >[!NOTE]
   >
   >Letzte Erinnerung: Wenn Sie dieses Tutorial mit mehreren Personen in einer einzelnen Sandbox durchlaufen oder ein freigegebenes Konto verwenden, sollten Sie erwägen, eine Identifizierung als Teil Ihrer Namenskonventionen anzuhängen oder voranzustellen. Verwenden Sie beispielsweise anstelle von `Luma Mobile App Event Dataset` `Luma Mobile App Event Dataset - Joe Smith`. Siehe auch den Hinweis in [Übersicht](overview.md).

1. Wählen Sie das Schema, das Sie in der vorherigen Lektion erstellt haben, in der Liste **Ereignisschema** aus.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![neue Datenströme](assets/datastream-name.png)


## Dienste hinzufügen

Wenn Sie in diesem Tutorial die (optionalen) [Analytics](analytics.md)- und [Experience Platform](platform.md)-Lektionen durchlaufen, fügen Sie Ihrem Datenstrom Services hinzu, damit an Platform Edge Network gesendete Daten an diese Programme weitergeleitet werden.

<!--

### Adobe Analytics

1. Select **[!UICONTROL Add Service]**.

1. Add **[!UICONTROL Adobe Analytics]** from the [!UICONTROL Service] list, 

1. Enter the name of the report site that you want to use in **[!UICONTROL Report Suite ID]**.

1. Enable the service by switching **[!UICONTROL Enabled]** on.

1. Select **[!UICONTROL Save]**.

   ![Add Adobe Analytics as datastream service](assets/datastream-service-aa.png)


### Adobe Experience Platform

You might also want to enable the Adobe Experience Platform service. 

>[!IMPORTANT]
>
>You can only enable the Adobe Experience Platform service when having created an event dataset. If you don't already have an event dataset created, follow the instructions [here](platform.md).

1. Click ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add Service]** to add another service.

1. Select **[!UICONTROL Adobe Experience Platform]** from the [!UICONTROL Service] list.

1. Enable the service by switching **[!UICONTROL Enabled]** on.

1. Select the **[!UICONTROL Event Dataset]** that you created as part of the [Create a dataset](platform.md#create-a-dataset) instructions, for example **Luma Mobile App Event Dataset**

1. Select **[!UICONTROL Save]**.

   ![Add Adobe Experience Platform as a datastream service](assets/datastream-service-aep.png)
1. The final configuration should look something like this.
   
   ![datastream settings](assets/datastream-settings.png)

-->


>[!NOTE]
>
>Durch die Aktivierung der einzelnen Services, die Ihr Unternehmen verwendet, wird sichergestellt, dass die in der Mobile App erfassten Daten überall verwendet werden können. Weitere Informationen zu Datenstromeinstellungen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de).

Wenn Sie Platform Mobile SDK in Ihrer eigenen App implementieren, sollten Sie letztendlich drei Datenströme erstellen, die Ihren drei Tag-Umgebungen (Entwicklung, Staging und Produktion) zugeordnet werden können. Wenn Sie Platform Mobile SDK mit plattformbasierten Anwendungen wie Adobe Real-time Customer Data Platform oder Adobe Journey Optimizer verwenden, sollten Sie sicherstellen, dass Sie diese Datenströme in den entsprechenden Sandboxes erstellen.

>[!SUCCESS]
>
>Sie haben jetzt einen Datenstrom, der für den Rest des Tutorials verwendet werden kann.
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Konfigurieren einer Tag-Eigenschaft](configure-tags.md)**
