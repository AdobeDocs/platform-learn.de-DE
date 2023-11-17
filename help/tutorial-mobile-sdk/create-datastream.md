---
title: Konfigurieren eines Datenstroms
description: Erfahren Sie, wie Sie einen Datastream in Experience Platform erstellen.
feature: Mobile SDK,Datastreams
exl-id: 7b83f834-d1fb-45d1-8bcf-bc621f94725c
source-git-commit: 94ca4a238c241518219fb2e8d73f775836f86d86
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 8%

---

# Erstellen eines Datenspeichers

Erfahren Sie, wie Sie einen Datastream in Experience Platform erstellen.

>[!INFO]
>
> Dieses Tutorial wird Ende November 2023 mithilfe einer neuen Beispiel-Mobile-App durch ein neues Tutorial ersetzt.

Ein Datenspeicher ist eine serverseitige Konfiguration im Platform Edge Network.  Der Datastream stellt sicher, dass eingehende Daten an das Platform Edge Network ordnungsgemäß an Adobe Experience Cloud-Anwendungen und -Dienste weitergeleitet werden. Weitere Informationen finden Sie unter [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de) oder [Video](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/configure-datastreams.html?lang=de).

## Voraussetzungen

Um einen Datastream zu erstellen, muss Ihre Organisation für diese Funktion in der Datenerfassungsoberfläche (zuvor [!UICONTROL Launch]) und Sie müssen über Benutzerberechtigungen für [!UICONTROL Experience Platform] > [!UICONTROL Datenerfassung] > **[!UICONTROL Verwalten von Datenspeichern]** und **[!UICONTROL Anzeigen von Datenspeichern]**.

## Lernziele

In dieser Lektion werden Sie:

* Erfahren Sie, wann ein Datastream verwendet werden soll.
* Erstellen eines Datenspeichers.
* Konfigurieren eines Datenstroms.

## Erstellen eines Datenspeichers

Datenspeicher können im [!UICONTROL Datenerfassung] -Schnittstelle mithilfe der [!UICONTROL Datastream] Konfigurationstool. So erstellen Sie einen Datastream:

1. Vergewissern Sie sich, dass Sie sich in der richtigen Platform-Sandbox befinden.
1. Wählen Sie **[!UICONTROL Neuer Datenstrom]** aus.

   ![datastreams home](assets/mobile-datastream-new.png)

1. Geben Sie einen Namen an, beispielsweise `Luma App`.
1. Wählen Sie das Schema aus, das Sie in der vorherigen Lektion erstellt haben.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![neue Datenspeicher](assets/mobile-datastream-name.png)


## Dienste hinzufügen

Als Nächstes können Sie Ihre Experience Cloud-Dienste mit Ihrem Datastream verbinden. Wenn das Platform Mobile SDK Daten an Edge Network sendet, sendet der Datastream die Daten an diese Dienste:

1. Hinzufügen **[!UICONTROL Adobe Analytics]** und geben Sie eine Report Suite an.

1. Aktivieren **[!UICONTROL Adobe Audience Manager]** (optional).

1. Aktivieren **[!UICONTROL Adobe Experience Platform]** und stellen Sie **[!UICONTROL Datensatz]** (optional).
   * Wenn Sie noch keinen Datensatz erstellt haben, befolgen Sie die Anweisungen . [here](platform.md).

1. Die endgültige Konfiguration sollte ungefähr so aussehen:
   ![Datenspeichereinstellungen](assets/mobile-datastream-settings.png)


>[!NOTE]
>
>Durch die Aktivierung der einzelnen Dienste, die Ihr Unternehmen verwendet, stellen Sie sicher, dass in der App erfasste Daten überall verwendet werden können. Weitere Informationen zu Datastream-Einstellungen finden Sie in der Dokumentation . [here](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html#adobe-experience-platform-settings).

Bei der Implementierung des Platform Mobile SDK auf Ihrer eigenen Website sollten Sie drei Datenspeicher erstellen, die Ihren drei Tag-Umgebungen (Entwicklung, Staging und Produktion) zugeordnet werden. Wenn Sie Platform Mobile SDK mit Platform-basierten Anwendungen wie Adobe Real-time Customer Data Platform oder Adobe Journey Optimizer verwenden, sollten Sie sicherstellen, dass Sie diese Datenspeicher in den entsprechenden Platform-Sandboxes erstellen.

Weiter: **[Tags konfigurieren](configure-tags.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)
