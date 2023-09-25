---
title: Erstellen von Segmenten
seo-title: Build segments | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Erstellen von Segmenten
description: In dieser Lektion erstellen wir einige Segmente basierend auf den Profildaten, die wir in den vorherigen Lektionen erfasst haben.
role: Data Architect
feature: Data Governance
jira: KT-4348
thumbnail: 4348-build-segments.jpg
exl-id: cd05e814-1ea7-48ba-adf6-1a71504c623e
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 3%

---

# Erstellen von Segmenten

<!-- 30 min-->
In dieser Lektion erstellen wir einige Segmente basierend auf den Profildaten, die wir in den vorherigen Lektionen erfasst haben.

Sobald Sie über Echtzeit-Kundenprofile verfügen, können Sie Segmente von Einzelanwendern erstellen, die ähnliche Eigenschaften aufweisen und möglicherweise ähnlich auf Marketing-Strategien reagieren. Die Bausteine dieser Segmente sind die XDM-Felder, die Sie zuvor erstellt haben.

**Datenarchitekten** müssen Segmente außerhalb dieses Tutorials erstellen und ihre Kollegen bei dieser Aufgabe unterstützen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über das Erstellen von Segmenten zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27254?learn=on)


## Erforderliche Berechtigungen

Im [Berechtigungen konfigurieren](configure-permissions.md) Lektion: Sie richten alle Zugriffskontrollen ein, die zum Abschluss dieser Lektion erforderlich sind, insbesondere:

* Berechtigungselemente **[!UICONTROL Profilverwaltung]** > **[!UICONTROL Segmente verwalten]**, **[!UICONTROL Segmente anzeigen]**, und **[!UICONTROL Zielgruppensegment exportieren]**
* Berechtigungselemente **[!UICONTROL Profilverwaltung]** > **[!UICONTROL Anzeigen von Profilen]**, und **[!UICONTROL Profile verwalten]**
* Berechtigungselement **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* Benutzerrollenzugriff auf die `Luma Tutorial Platform` Produktprofil
* Entwicklerrollenzugriff auf die `Luma Tutorial Platform` Produktprofil (für API)

## Basissegment erstellen

Erstellen wir ein einfaches Segment für Kunden von Treueprogrammen mit einem Gold- oder Platinstatus

1. Navigieren Sie in der Benutzeroberfläche von Platform zu **[!UICONTROL Segmente]** in der linken Navigation
1. Wählen Sie die **[!UICONTROL Segment erstellen]** button
1. Auf der linken Seite des Schema Builders befinden sich drei Registerkarten für Attribute (Datensatzdaten), Ereignisse (Zeitreihendaten) und Zielgruppen
1. Wählen Sie das Zahnradsymbol aus, um zu sehen, wie der Segment Builder standardmäßig nur die Felder mit Daten anzeigt und es Ihnen ermöglicht, die Zusammenführungsrichtlinie zu ändern
1. Navigieren Sie auf der Registerkarte &quot;Attribute&quot;zum **XDM Individual Profile > Loyalität** Ordner (Sie können auch nach &quot;loyalty&quot;suchen)
1. Drag &amp; Drop, `Tier` aus dem Menü &quot;Attributfelder&quot;zur Arbeitsfläche des Segmentaufbaus
1. Auswählen `Tier` gleich `Gold` oder `Platinum`
1. Auswählen **[!UICONTROL Schätzung aktualisieren]** um zu sehen, wie viele Profile für Ihr Segment qualifiziert sind
1. Als **[!UICONTROL Name]**, eingeben `Luma customers with level Gold or Above`
1. Wählen Sie **[!UICONTROL Speichern]** aus
   ![Segment](assets/segment-goldOrAbove.png)

<!--## Build a sequential segment-->

## Dynamisches Segment erstellen

In dieser Übung erstellen wir ein Segment für Kunden, die dasselbe Produkt innerhalb von 30 Tagen zweimal gekauft haben. Mit dynamischen Segmenten können Sie Ihre Segmentierung skalieren, indem Sie Felder als Variablen verwenden.

1. Navigieren Sie zu **[!UICONTROL Segmente]** in der linken Navigation
1. Wählen Sie die **[!UICONTROL Segment erstellen]** button
1. Wählen Sie die **[!UICONTROL Veranstaltungen]** tab
1. Filtern der Liste nach `purchases`
1. Ziehen Sie die **[!UICONTROL Käufe]** Ereignistyp auf der Arbeitsfläche _zwei separate_
1. Wählen Sie das Uhrensymbol zwischen den beiden **[!UICONTROL Käufe]** Ereignisse und wählen Sie &quot;innerhalb von 30 Tagen&quot;aus.
1. Bestätigen Sie, dass Ihre Segmentdefinition an dieser Stelle wie folgt lautet: **&quot;Schließen Sie Zielgruppe ein, die mindestens 1 Kaufereignis hat und dann innerhalb von 30 Tagen mindestens 1 Kaufereignis hat.&quot;**
   ![Zwei Käufe innerhalb von 30 Tagen](assets/segment-twoPurchases.png)
1. Ändern Sie jetzt den Ereignisfilter in `sku`
1. Ziehen Sie das SKU-Feld zum zweiten Kaufereignis
   ![Zwei Käufe innerhalb von 30 Tagen mit SKU](assets/segment-twoPurchases-addSku.png)
1. Löschen Sie jetzt den Ereignisfilter
1. Sie sollten in der **[!UICONTROL Variablen durchsuchen]** -Abschnitt gibt es Ordner für die beiden Kaufereignisse. Klicken Sie auf . **[!UICONTROL Einkäufe 1]**\
   ![Zwei Käufe innerhalb von 30 Tagen mit SKU, durchsuchen Sie den ersten Kauf](assets/segment-twoPurchases-browsePurchaseOne.png)
1. Drilldown in die **[!UICONTROL Produktlistenelemente]** Ordner, wählen Sie die **[!UICONTROL SKU]** und ziehen Sie es rechts neben **[!UICONTROL gleich]** Operand. Wenn Sie den Mauszeiger über den Bereich bewegen, legen Sie ihn im Abschnitt &quot;Hinzufügen zum Vergleichen von Operanden&quot;ab
1. Benennen Sie Ihr Segment `Bought same product within 30 days`
1. Überprüfen Sie, ob Ihre Zielgruppendefinition **&quot;Schließen Sie Zielgruppe ein, die mindestens 1 Kaufereignis hat und dann innerhalb von 30 Tagen mindestens 1 Kaufereignis hat, bei dem ((SKU = Purchases1 SKU))&quot;**
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![In den letzten 30 Tagen im Segment gekauft](assets/segment-boughtSameProduct.png)

## Mehrere Entitätssegmente erstellen

Denken Sie daran, wie wir die Beziehung zwischen `Luma Offline Purchase Events Schema` und `Luma Product Catalog Schema` in früheren Lektionen? Wir haben dies getan, damit wir die Beziehung in unserem Schema mithilfe der Segmentierung mehrerer Entitäten verwenden konnten.

Mit der erweiterten Segmentierungsfunktion für mehrere Entitäten können Sie Segmente mit mehreren XDM-Klassen erstellen, um Ihre Schemas zu erweitern. Daher kann der Segment Builder auf zusätzliche Felder zugreifen, als wären sie nativ im Profildatenspeicher

Sie erstellen das nächste Segment, indem Sie die Beziehung anwenden, die Sie zwischen Ihrem `Luma Product Catalog Schema` und `Luma Offline Purchase Events Schema`.

1. Navigieren Sie zu **[!UICONTROL Segmente]** in der linken Navigation
1. Wählen Sie die **[!UICONTROL Segment erstellen]** button
1. Wählen Sie die **[!UICONTROL Veranstaltungen]** tab
1. Filtern der Liste nach `purchases`
1. Ziehen Sie die **[!UICONTROL Käufe]** Ereignistyp auf der Arbeitsfläche
1. Wählen Sie das Dropdown-Menü &quot;Uhr&quot;über dem Ereignis aus und wählen Sie **[!UICONTROL in den letzten 30 Tagen]**
1. Filtern Sie die **[!UICONTROL Veranstaltungen]** Liste zu `category` und ziehen Sie dann die **[!UICONTROL Produktkategorie]** Feld auf **[!UICONTROL Käufe]**
1. Ändern Sie den Operator in **[!UICONTROL beginnt mit]** und eingeben `men` in das Textfeld
1. Als **[!UICONTROL Name]**, eingeben `Purchased a Men's product in the last 30 days`
1. Zielgruppendefinition bestätigen `(Include audience who have at least 1 Purchases event where ((Product Category starts with men)) ) and occurs in last 30 day(s)`
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![In den letzten 30 Tagen im Segment gekauft](assets/segment-purchasedMens.png)

## Batch- und Streaming-Segmentierung

Klicken Sie auf **[!UICONTROL Segmente]** im linken Navigationsbereich und lassen Sie uns einen Moment Zeit nehmen, um unsere drei Segmente zu überprüfen:

* Zwei unserer Segmente sind Batch-Segmente und eines ist ein Streaming-Segment.
* Die Plattform nutzt nach Möglichkeit Streaming-Segmentierung, um den Kunden für ein Segment zu qualifizieren, sobald er die Kriterien erfüllt. Wenn Segmentdefinitionen für das Streaming zu komplex sind, werden sie automatisch in Batch konvertiert. In diesem Fall wurde für die beiden Segmente standardmäßig ein Batch-Vorgang verwendet, da das Lookback-Fenster der Kaufereignisse länger als sieben Tage war. Eine vollständige und aktuelle Liste der Streaming-Einschränkungen finden Sie unter [die Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/streaming-segmentation.html).
* Die Batch-Aufträge werden nach einem täglichen Zeitplan ausgeführt, der umgeschaltet werden kann.

![In den letzten 30 Tagen im Segment gekauft](assets/segment-review.png)

## Weitere Ressourcen

* [Dokumentation zum Segmentierungsdienst](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Referenz zur Segmentierungsdienst-API](https://www.adobe.io/experience-platform-apis/references/segmentation/)

Die Segmentierung, insbesondere beim Aktivieren von Segmenten, hat noch einiges zu tun. Diese Themen werden in einem anderen Tutorial behandelt.

Du hast es durch alle Übungen geschafft! Fahren Sie mit dem [Schlussfolgerung](conclusion.md).
