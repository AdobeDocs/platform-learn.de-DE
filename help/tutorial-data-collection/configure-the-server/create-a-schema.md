---
title: Schema erstellen
description: Schema erstellen
exl-id: 0256b358-0c2c-4c59-ab23-5fe0d38880d6
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 3%

---

# Schema erstellen

Wie in [Daten strukturieren](../structuring-your-data.md), müssen die an Adobe Experience Platform gesendeten Daten in XDM sein. Genauer gesagt müssen Ihre Daten mit einem _schema_. Ein Schema ist im Grunde eine Beschreibung dessen, wie die Daten aussehen sollen. Es beschreibt die Namen der Felder und wo sie sich in den Daten befinden sollen. Außerdem wird der Typ des Werts beschrieben, den jedes Feld aufweisen sollte (z. B. ein boolescher Wert, eine Zeichenfolge mit einer Länge von 12 Zeichen, ein Array von Zahlen).

Adobe Experience Platform bietet einige vordefinierte Bausteine, die als Feldergruppen bezeichnet werden und in der Branche häufig vorkommen. Für die Finanzdienstleistungsbranche gibt es beispielsweise Feldergruppen für Bilanztransfers und Kreditanträge. Für die Reise- und Gastgewerbe gibt es Feldergruppen für Flug- und Übernachtungsreservierungen.

Es wird empfohlen, bei der Erstellung Ihres Schemas nach Möglichkeit die integrierten Feldergruppen zu verwenden. Wir wissen auch, dass Sie möglicherweise Felder benötigen, die für Ihr eigenes Unternehmen spezifisch sind. Aus diesem Grund können Sie eigene benutzerdefinierte Feldergruppen erstellen, die in den von Ihnen erstellten Schemata verwendet werden.

Gehen wir durch die Erstellung eines Schemas für eine typische E-Commerce-Website.

1. Auswählen **[!UICONTROL Schemas]** under [!UICONTROL Data Management] über das Menü links in der Adobe Experience Platform-Benutzeroberfläche.
1. Auswählen **[!UICONTROL Schema erstellen]** in der oberen rechten Ecke und **[!UICONTROL XDM ExperienceEvent]** aus dem Dropdown-Menü.

Sie befinden sich jetzt auf der Arbeitsfläche des Schemas-Builders.
![Schemaansicht](../assets/schemas-view.png)

## Klicken Sie auf Feldergruppen hinzufügen

1. Im **[!UICONTROL Feldergruppen]** auf der linken Seite des **[!UICONTROL Struktur]** Bereich, wählen Sie die **[!UICONTROL + Hinzufügen]** Link. An dieser Stelle wird ein Modal angezeigt, in dem die Feldergruppen ausgewählt werden, die zum Schema hinzugefügt werden sollen.
1. Wählen Sie zuerst die Feldergruppe mit dem Namen **[!UICONTROL AEP Web SDK ExperienceEvent]**. Diese Feldergruppe fügt eine Reihe von Feldern hinzu, die automatisch vom Adobe Experience Platform Web SDK erfasste Daten berücksichtigen.
   ![AEP Web SDK-Mixin](../assets/aep-web-sdk-mixin.png)
1. Da es sich bei der Website für dieses Tutorial um eine E-Commerce-Website handelt, wählen Sie als Nächstes die **[!UICONTROL Commerce-Details]** Feldergruppe. Mit dieser Feldergruppe können Sie typische Commerce-Daten senden, z. B. welche Produkte angezeigt, zum Warenkorb hinzugefügt und gekauft werden.
1. Wählen Sie die **[!UICONTROL Feldergruppen hinzufügen]** Schaltfläche oben rechts im Dialogfeld.
   ![Commerce-Details-Mixin](../assets/commerce-details-mixin.png)
1. An dieser Stelle sollte die Struktur Ihres Schemas angezeigt werden.
   ![Schema mit Mixins](../assets/schema-with-mixins.png)

## Schema speichern

1. Geben Sie einen Namen und eine Beschreibung rechts vom Bildschirm ein und wählen Sie **[!UICONTROL Speichern]**.
   ![Schema mit Name und Beschreibung](../assets/schema-name-description.png)

Ihr Schema wurde erstellt. Als Nächstes erfahren wir, wie Sie einen Datensatz zum Speichern Ihrer Daten erstellen.

Weitere Informationen zum Erstellen von Schemas finden Sie unter [Erstellen von Schemata](/help/platform/schemas/create-schemas.md).

[Weiter: ](create-a-dataset.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
