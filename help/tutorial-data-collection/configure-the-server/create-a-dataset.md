---
title: Erstellen eines Datensatzes
description: Erstellen eines Datensatzes
exl-id: 19a60087-2f78-4510-b127-b1007a6b7a56
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 2%

---

# Erstellen eines Datensatzes

Zusätzlich zur Beschreibung der Daten, die Sie an Adobe Experience Platform senden, benötigen Sie eine Stelle, an der die Daten beibehalten werden. In Adobe Experience Platform werden diese Behälter, in die Sie Daten einfügen können, als Datensätze bezeichnet.

>[!NOTE]
>
>Datensätze sind nicht erforderlich, wenn Sie zum Senden von Daten an Adobe Analytics, Adobe Target und Adobe Audience Manager nur Platform Web SDK verwenden oder die Ereignisweiterleitung verwenden. Wenn Sie für diese Zwecke nur Web SDK verwenden, können Sie diese Seite des Tutorials überspringen.

1. Auswählen **[!UICONTROL Datensätze]** under [!UICONTROL Data Management] über das Menü links in Adobe Experience Platform.
1. Wählen Sie als Nächstes die **[!UICONTROL Datensatz erstellen]** in der oberen rechten Ecke.
   ![Ansicht &quot;Datensätze&quot;](../assets/datasets-view.png)

## Datensatz aus Schema erstellen

1. Aus dem [!UICONTROL Workflow] -Benutzeroberfläche die erste Kachel auswählen, **[!UICONTROL Datensatz aus Schema erstellen]**.
1. Suchen Sie nach [das zuvor von Ihnen erstellte Schema](create-a-schema.md) und wählen Sie sie aus.
   ![Schemaauswahl](../assets/schema-selection.png)
1. Auswählen **[!UICONTROL Nächste]** und geben Sie einen Namen und eine Beschreibung ein.
   ![Datensatzname und Beschreibung](../assets/dataset-name-description.png)
1. Auswählen **[!UICONTROL Beenden]**. Ihr Datensatz wurde erstellt und kann Daten empfangen.

Wenn Sie Daten in einen Datensatz senden, überprüft Adobe Experience Platform, ob die Daten, die Sie in den Datensatz einfügen möchten, mit dem angewendeten Schema übereinstimmen. Wenn die Daten nicht mit dem Schema übereinstimmen, werden die Daten zurückgewiesen und nicht in den Datensatz eingefügt. Infolge dieses Validierungsschritts können Verbraucher des Datensatzes (Adobe-Produkte, Drittanbieter oder Ihr eigenes Unternehmen) ein gewisses Maß an Sicherheit in Bezug auf die Struktur und Sauberkeit der Daten des Datensatzes haben.

Weitere Informationen zum Erstellen von Datensätzen finden Sie unter [Erstellen von Datensätzen und Erfassen von Daten](/help/platform/data-ingestion/create-datasets-and-ingest-data.md).

[Weiter: ](create-a-datastream.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)

