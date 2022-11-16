---
title: Schema erstellen
description: Schema erstellen
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 25d77367-046d-46bd-9640-60fbcea263da
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 3%

---

# Schema erstellen

Wie in [Daten strukturieren](../structuring-your-data.md), müssen die an Adobe Experience Platform gesendeten Daten in XDM sein. Genauer gesagt müssen Ihre Daten mit einem _schema_. Ein Schema ist im Grunde eine Beschreibung dessen, wie die Daten aussehen sollen. Es beschreibt die Namen der Felder und wo sie sich in den Daten befinden sollen. Außerdem wird der Typ des Werts beschrieben, den jedes Feld aufweisen sollte (z. B. ein boolescher Wert, eine Zeichenfolge mit einer Länge von 12 Zeichen, ein Array von Zahlen).

Adobe Experience Platform bietet einige vordefinierte Bausteine, die als Feldergruppen bezeichnet werden und in der Branche häufig vorkommen. Für die Finanzdienstleistungsbranche gibt es beispielsweise Feldergruppen für Bilanztransfers und Kreditanträge. Für die Reise- und Gastgewerbe gibt es Feldergruppen für Flug- und Übernachtungsreservierungen.

Es wird empfohlen, bei der Erstellung Ihres Schemas nach Möglichkeit die integrierten Feldergruppen zu verwenden. Wir wissen auch, dass Sie möglicherweise Felder benötigen, die für Ihr eigenes Unternehmen spezifisch sind. Aus diesem Grund können Sie eigene benutzerdefinierte Feldergruppen erstellen, die in den von Ihnen erstellten Schemata verwendet werden.

Gehen wir durch die Erstellung eines Schemas für eine typische E-Commerce-Website.

Navigieren Sie zunächst zum [!UICONTROL Schemas] Ansicht in Adobe Experience Platform.

![Schemaansicht](../../../assets/implementation-strategy/schemas-view.png)

Auswählen [!UICONTROL Schema erstellen] in der oberen rechten Ecke. Ein Menü wird angezeigt. Auswählen [!UICONTROL XDM ExperienceEvent].

An dieser Stelle sollte ein Dialogfeld angezeigt werden, in dem Sie gefragt werden, welche Feldergruppen Sie Ihrem Schema hinzufügen möchten. Die erste Feldergruppe, die Sie auswählen sollten, ist die Feldergruppe mit dem Namen [!UICONTROL AEP Web SDK ExperienceEvent]. Diese Feldergruppe fügt eine Reihe von Feldern hinzu, die automatisch vom Adobe Experience Platform Web SDK erfasste Daten berücksichtigen.

![AEP Web SDK-Mixin](../../../assets/implementation-strategy/aep-web-sdk-mixin.png)

Da es sich bei der Website für dieses Tutorial um eine E-Commerce-Website handelt, sollten Sie auch die [!UICONTROL Commerce-Details] Feldergruppe. Mit dieser Gruppe können Sie typische Commerce-Daten senden, z. B. welche Produkte angezeigt, zum Warenkorb hinzugefügt und gekauft werden.

![Commerce-Details-Mixin](../../../assets/implementation-strategy/commerce-details-mixin.png)

Klicken Sie auf [!UICONTROL Feldergruppen hinzufügen] Schaltfläche oben rechts im Dialogfeld. An dieser Stelle sollte die Struktur Ihres Schemas angezeigt werden.

![Schema mit Mixins](../../../assets/implementation-strategy/schema-with-mixins.png)

Die Feldergruppen, die Sie hinzugefügt haben, werden auf der linken Seite aufgelistet. Bei Auswahl einer Feldergruppe werden die von dieser Feldergruppe bereitgestellten Felder auf der rechten Seite hervorgehoben. Nehmen Sie sich einen Moment Zeit, um die verfügbaren Felder zu erkunden.

Wählen Sie abschließend [!UICONTROL Unbenanntes Schema] Geben Sie links im Bildschirm einen Namen und eine Beschreibung rechts vom Bildschirm ein und klicken Sie auf [!UICONTROL Speichern].

![Schema mit Name und Beschreibung](../../../assets/implementation-strategy/schema-name-description.png)

Ihr Schema wurde erstellt. Als Nächstes erfahren wir, wie Sie einen Datensatz für Ihre Daten erstellen.

Weitere Informationen zum Erstellen von Schemas finden Sie unter [Erstellen eines Schemas (Benutzeroberfläche)](https://experienceleague.adobe.com/docs/experience-platform/xdm/tutorials/create-schema-ui.html?lang=de).
