---
title: Konfigurieren eines Datenstroms
description: Erfahren Sie, wie Sie einen Datastream in Experience Platform erstellen.
feature: Mobile SDK,Datastreams
hide: true
source-git-commit: 56323387deae4a977a6410f9b69db951be37059f
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 10%

---


# Erstellen eines Datenspeichers

Erfahren Sie, wie Sie einen Datastream in Experience Platform erstellen.

Ein Datenspeicher ist eine serverseitige Konfiguration im Platform Edge Network. Der Datastream stellt sicher, dass eingehende Daten an das Platform Edge Network ordnungsgemäß an Adobe Experience Cloud-Anwendungen und -Dienste weitergeleitet werden. Weitere Informationen finden Sie unter [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de) oder [Video](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/configure-datastreams.html?lang=de).

## Voraussetzungen

Um einen Datastream zu erstellen, muss Ihre Organisation für diese Funktion in der Datenerfassungsoberfläche (zuvor [!UICONTROL Launch]) und Sie müssen über Benutzerberechtigungen verfügen, um Datenspeicher zu verwalten und anzuzeigen.

## Lernziele

In dieser Lektion werden Sie:

* Erfahren Sie, wann ein Datastream verwendet werden soll.
* Erstellen eines Datenspeichers.
* Konfigurieren eines Datenstroms.

## Erstellen eines Datenspeichers

Datenspeicher können im [!UICONTROL Datenerfassung] -Schnittstelle mithilfe der [!UICONTROL Datastream] Konfigurationstool. So erstellen Sie einen Datastream:

1. Stellen Sie sicher, dass Sie sich in der richtigen Experience Platform-Sandbox befinden, da Datastreams auf Sandbox-Ebene definiert sind.
1. Auswählen **[!UICONTROL Datenspeicher]** in der linken Leiste.
1. Wählen Sie **[!UICONTROL Neuer Datenstrom]** aus.

   ![datastreams home](assets/datastream-new.png)

1. Stellen Sie eine **[!UICONTROL Name]**, beispielsweise `Luma Mobile App` und **[!UICONTROL Beschreibung]**, beispielsweise `Datastream for Luma Mobile App`.
1. Wählen Sie das Schema aus, das Sie in der vorherigen Lektion aus dem **Veranstaltungsschema** eine Liste.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![neue Datenspeicher](assets/datastream-name.png)


## Dienste hinzufügen

Als Nächstes verbinden Sie Ihre Experience Cloud-Dienste mit Ihrem Datastream. Wenn das Platform Mobile SDK Daten an Edge Network sendet, sendet der Datastream die Daten an diese Dienste:

### Adobe Analytics

1. Wählen Sie **[!UICONTROL Service hinzufügen]** aus.

1. Hinzufügen **[!UICONTROL Adobe Analytics]** aus dem [!UICONTROL Dienst] Liste,

1. Geben Sie den Namen der Report Suite ein, die Sie in **[!UICONTROL Report Suite-ID]**.

1. Aktivieren Sie den Dienst, indem Sie **[!UICONTROL Aktiviert]** auf.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Hinzufügen von Adobe Analytics als Datastream-Dienst](assets/datastream-service-aa.png)


### Adobe Experience Platform

Möglicherweise möchten Sie auch den Adobe Experience Platform-Dienst aktivieren.

>[!IMPORTANT]
>
>Sie können den Adobe Experience Platform-Dienst nur aktivieren, wenn Sie einen Ereignisdatensatz erstellt haben. Wenn Sie noch keinen Ereignis-Datensatz erstellt haben, befolgen Sie die Anweisungen . [here](platform.md).

1. Klicks ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Dienst hinzufügen]** , um einen weiteren Dienst hinzuzufügen.

1. Wählen Sie **[!UICONTROL Adobe Experience Platform]** in der Liste [!UICONTROL Service] aus.

1. Aktivieren Sie den Dienst, indem Sie **[!UICONTROL Aktiviert]** auf.

1. Wählen Sie die **[!UICONTROL Ereignis-Datensatz]** die Sie im Rahmen der [Datensatz erstellen](platform.md#create-a-dataset) Anweisungen, beispielsweise **Ereignis-Datensatz für Luma Mobile App**

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Hinzufügen von Adobe Experience Platform als Datastraam-Dienst](assets/datastream-service-aep.png)
1. Die endgültige Konfiguration sollte ungefähr so aussehen:

   ![Datenspeichereinstellungen](assets/datastream-settings.png)


>[!NOTE]
>
>Durch die Aktivierung der einzelnen Dienste, die Ihr Unternehmen verwendet, stellen Sie sicher, dass in der App erfasste Daten überall verwendet werden können. Weitere Informationen zu den Datastream-Einstellungen finden Sie in der Dokumentation . [here](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html#adobe-experience-platform-settings).

Bei der Implementierung des Platform Mobile SDK in Ihrer eigenen App sollten Sie letztendlich drei Datenspeicher erstellen, die Ihren drei Tag-Umgebungen (Entwicklung, Staging und Produktion) zugeordnet werden. Wenn Sie Platform Mobile SDK mit Platform-basierten Anwendungen wie Adobe Real-time Customer Data Platform oder Adobe Journey Optimizer verwenden, sollten Sie diese Datenspeicher in den entsprechenden Sandboxes erstellen.

>[!SUCCESS]
>
>Sie verfügen jetzt über einen Datastream, der für den Rest des Tutorials verwendet werden kann.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Tags konfigurieren](configure-tags.md)**
