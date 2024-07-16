---
title: Konfigurieren eines Datenspeichers für Platform Mobile SDK-Implementierungen
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

Ein Datastream ist eine serverseitige Konfiguration auf Platform Edge Network. Der Datastream stellt sicher, dass eingehende Daten an das Platform-Edge Network ordnungsgemäß an Adobe Experience Cloud-Anwendungen und -Dienste weitergeleitet werden. Weitere Informationen finden Sie in der [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de) oder in diesem [Video](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/configure-datastreams.html?lang=de) .

![Architektur](assets/architecture.png)

## Voraussetzungen

Um einen Datastream zu erstellen, muss Ihr Unternehmen für diese Funktion in der Datenerfassungsschnittstelle (früher [!UICONTROL Launch]) bereitgestellt werden und Sie müssen über Benutzerberechtigungen verfügen, um Datastraams zu verwalten und anzuzeigen.

## Lernziele

In dieser Lektion werden Sie:

* Erfahren Sie, wann ein Datastream verwendet werden soll.
* Erstellen Sie einen Datenspeicher.
* Konfigurieren Sie einen Datenspeicher.

## Erstellen eines Datenspeichers

Datenspeicher können in der Benutzeroberfläche [!UICONTROL Datenerfassung] mit dem Konfigurationstool [!UICONTROL Datastream] erstellt werden. So erstellen Sie einen Datastream:

1. Stellen Sie sicher, dass Sie sich in der richtigen Experience Platform-Sandbox befinden, da Datenspeicher auf Sandbox-Ebene definiert sind.
1. Wählen Sie in der linken Leiste **[!UICONTROL Datenspeicher]** aus.
1. Wählen Sie **[!UICONTROL Neuer Datenspeicher]** aus.

   ![datastreams home](assets/datastream-new.png)

1. Geben Sie einen **[!UICONTROL Namen]** an, z. B. `Luma Mobile App` und eine **[!UICONTROL Beschreibung]**, z. B. `Datastream for Luma Mobile App`.

   >[!NOTE]
   >
   >Letzte Erinnerung: Wenn Sie dieses Tutorial mit mehreren Personen in einer Sandbox durchlaufen oder ein freigegebenes Konto verwenden, sollten Sie erwägen, im Rahmen Ihrer Benennungskonventionen eine Identität anzuhängen oder vorzustellen. Verwenden Sie beispielsweise anstelle von `Luma Mobile App Event Dataset` `Luma Mobile App Event Dataset - Joe Smith`. Siehe auch den Hinweis unter [Überblick](overview.md).

1. Wählen Sie in der Liste **Ereignisschema** das Schema aus, das Sie in der vorherigen Lektion erstellt haben.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![neue Datastreams](assets/datastream-name.png)


## Dienste hinzufügen

Wenn Sie die Lektionen (optional) [Analytics](analytics.md) und [Experience Platform](platform.md) in diesem Tutorial durchlaufen, fügen Sie Dienste zu Ihrem Datastream hinzu, damit an Platform Edge Network gesendete Daten an diese Anwendungen weitergeleitet werden.

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
>Durch die Aktivierung der einzelnen Dienste, die Ihr Unternehmen verwendet, stellen Sie sicher, dass in der App erfasste Daten überall verwendet werden können. Weitere Informationen zu Datastream-Einstellungen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de).

Bei der Implementierung des Platform Mobile SDK in Ihrer eigenen App sollten Sie letztendlich drei Datenspeicher erstellen, die Ihren drei Tag-Umgebungen (Entwicklung, Staging und Produktion) zugeordnet werden. Wenn Sie Platform Mobile SDK mit Platform-basierten Anwendungen wie Adobe Real-time Customer Data Platform oder Adobe Journey Optimizer verwenden, sollten Sie diese Datenspeicher in den entsprechenden Sandboxes erstellen.

>[!SUCCESS]
>
>Sie verfügen jetzt über einen Datastream, der für den Rest des Tutorials verwendet werden kann.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu künftigen Inhalten teilen möchten, teilen Sie diese auf diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Konfigurieren einer Tag-Eigenschaft](configure-tags.md)**
