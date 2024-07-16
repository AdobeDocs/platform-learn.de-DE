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
source-wordcount: '905'
ht-degree: 1%

---

# Erstellen von Segmenten

<!-- 30 min-->
In dieser Lektion erstellen wir einige Segmente basierend auf den Profildaten, die wir in den vorherigen Lektionen erfasst haben.

Sobald Sie über Echtzeit-Kundenprofile verfügen, können Sie Segmente von Einzelanwendern erstellen, die ähnliche Eigenschaften aufweisen und möglicherweise ähnlich auf Marketing-Strategien reagieren. Die Bausteine dieser Segmente sind die XDM-Felder, die Sie zuvor erstellt haben.

**Datenarchitekten** müssen außerhalb dieses Tutorials Segmente erstellen und ihre Kollegen bei dieser Aufgabe unterstützen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über das Erstellen von Segmenten zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27254?learn=on)


## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschluss dieser Lektion erforderlich sind, insbesondere:

* Berechtigungselemente **[!UICONTROL Profilverwaltung]** > **[!UICONTROL Segmente verwalten]**, **[!UICONTROL Segmente anzeigen]** und **[!UICONTROL Zielgruppensegment exportieren]**
* Berechtigungselemente **[!UICONTROL Profilverwaltung]** > **[!UICONTROL Profile anzeigen]** und **[!UICONTROL Profile verwalten]**
* Berechtigungselement **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* Benutzerrollenzugriff auf das `Luma Tutorial Platform` -Produktprofil
* Entwicklerrollenzugriff auf das `Luma Tutorial Platform` -Produktprofil (für API)

## Basissegment erstellen

Erstellen wir ein einfaches Segment für Kunden von Treueprogrammen mit einem Gold- oder Platinstatus

1. Navigieren Sie in der Benutzeroberfläche von Platform im linken Navigationsbereich zu **[!UICONTROL Segmente]** .
1. Wählen Sie die Schaltfläche **[!UICONTROL Segment erstellen]** aus
1. Auf der linken Seite des Schema Builders befinden sich drei Registerkarten für Attribute (Datensatzdaten), Ereignisse (Zeitreihendaten) und Zielgruppen
1. Wählen Sie das Zahnradsymbol aus, um zu sehen, wie der Segment Builder standardmäßig nur die Felder mit Daten anzeigt und es Ihnen ermöglicht, die Zusammenführungsrichtlinie zu ändern
1. Navigieren Sie auf der Registerkarte &quot;Attribute&quot;zum Ordner **XDM Individual Profile > Loyalty** (Sie können auch nach &quot;loyalty&quot;suchen).
1. Ziehen Sie &quot;`Tier`&quot;aus dem Menü &quot;Attributfelder&quot;in die Arbeitsfläche des Segmentaufbaus
1. Wählen Sie `Tier` gleich `Gold` oder `Platinum`
1. Wählen Sie **[!UICONTROL Schätzung aktualisieren]** aus, um zu sehen, wie viele Profile für Ihr Segment qualifiziert sind.
1. Geben Sie als **[!UICONTROL Name]** `Luma customers with level Gold or Above` ein.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
   ![Segment](assets/segment-goldOrAbove.png)

<!--## Build a sequential segment-->

## Dynamisches Segment erstellen

In dieser Übung erstellen wir ein Segment für Kunden, die dasselbe Produkt innerhalb von 30 Tagen zweimal gekauft haben. Mit dynamischen Segmenten können Sie Ihre Segmentierung skalieren, indem Sie Felder als Variablen verwenden.

1. Navigieren Sie im linken Navigationsbereich zu **[!UICONTROL Segmente]** .
1. Wählen Sie die Schaltfläche **[!UICONTROL Segment erstellen]** aus
1. Wählen Sie die Registerkarte **[!UICONTROL Ereignisse]** aus
1. Filtern der Liste nach `purchases`
1. Ziehen Sie den Ereignistyp **[!UICONTROL Einkäufe]** zweimal separat auf die Arbeitsfläche __
1. Wählen Sie das Uhrensymbol zwischen den beiden Ereignissen **[!UICONTROL Einkäufe]** aus und wählen Sie &quot;innerhalb von 30 Tagen&quot;.
1. Bestätigen Sie, dass Ihre Segmentdefinition an dieser Stelle &quot;**&quot;Einschließlich Zielgruppe, die mindestens 1 Kaufereignis aufweist und innerhalb von 30 Tagen mindestens 1 Kaufereignis aufweist&quot;**
   ![Zwei Käufe innerhalb von 30 Tagen](assets/segment-twoPurchases.png)
1. Ändern Sie jetzt den Ereignisfilter auf `sku`
1. Ziehen Sie das SKU-Feld zum zweiten Kaufereignis
   ![Zwei Käufe innerhalb von 30 Tagen mit SKU](assets/segment-twoPurchases-addSku.png)
1. Löschen Sie jetzt den Ereignisfilter
1. Im Abschnitt **[!UICONTROL Variablen durchsuchen]** sollten Sie sehen, dass es Ordner für die beiden Kaufereignisse gibt. Klicken Sie auf , um **[!UICONTROL Einkäufe 1]** zu durchsuchen.\
   ![Zwei Käufe innerhalb von 30 Tagen mit SKU, durchsuchen Sie den ersten Kauf](assets/segment-twoPurchases-browsePurchaseOne.png)
1. Führen Sie einen Drilldown in den Ordner **[!UICONTROL Produktlistenelemente]** durch, wählen Sie das Feld **[!UICONTROL SKU]** aus und ziehen Sie es rechts vom Operanden **[!UICONTROL gleich]** . Wenn Sie den Mauszeiger über den Bereich bewegen, legen Sie ihn im Abschnitt &quot;Hinzufügen zum Vergleichen von Operanden&quot;ab
1. Benennen Sie Ihr Segment `Bought same product within 30 days`
1. Vergewissern Sie sich, dass Ihre Zielgruppendefinition &quot;**&quot;Zielgruppe einschließen, die mindestens 1 Kaufereignis aufweist und innerhalb von 30 Tagen mindestens 1 Kaufereignis aufweist, bei dem ((SKU entspricht Verkauf1 SKU))&quot;**
1. Wählen Sie die Schaltfläche **[!UICONTROL Speichern]** aus

   ![Gab dasselbe Produkt in den letzten 30 Tagen im Segment](assets/segment-boughtSameProduct.png)

## Mehrere Entitätssegmente erstellen

Denken Sie daran, wie wir die Beziehung zwischen `Luma Offline Purchase Events Schema` und `Luma Product Catalog Schema` in früheren Lektionen erstellt haben. Wir haben dies getan, damit wir die Beziehung in unserem Schema mithilfe der Segmentierung mehrerer Entitäten verwenden konnten.

Mit der erweiterten Segmentierungsfunktion für mehrere Entitäten können Sie Segmente mit mehreren XDM-Klassen erstellen, um Ihre Schemas zu erweitern. Daher kann der Segment Builder auf zusätzliche Felder zugreifen, als wären sie nativ im Profildatenspeicher

Sie erstellen das nächste Segment, indem Sie die von Ihnen erstellte Beziehung zwischen Ihrem `Luma Product Catalog Schema` und Ihrem `Luma Offline Purchase Events Schema` anwenden.

1. Navigieren Sie im linken Navigationsbereich zu **[!UICONTROL Segmente]** .
1. Wählen Sie die Schaltfläche **[!UICONTROL Segment erstellen]** aus
1. Wählen Sie die Registerkarte **[!UICONTROL Ereignisse]** aus
1. Filtern der Liste nach `purchases`
1. Ziehen Sie den Ereignistyp **[!UICONTROL Einkäufe]** auf die Arbeitsfläche
1. Wählen Sie das Cursor-Dropdown-Menü über dem Ereignis aus und wählen Sie **[!UICONTROL in den letzten 30 Tagen]**
1. Filtern Sie die Liste **[!UICONTROL Ereignisse]** in `category` und ziehen Sie dann das Feld **[!UICONTROL Produktkategorie]** auf **[!UICONTROL Einkäufe]**
1. Ändern Sie den Operator in **[!UICONTROL beginnt mit]** und geben Sie `men` in das Textfeld ein.
1. Geben Sie als **[!UICONTROL Name]** `Purchased a Men's product in the last 30 days` ein.
1. Audience definition bestätigen `(Include audience who have at least 1 Purchases event where ((Product Category starts with men)) ) and occurs in last 30 day(s)`
1. Wählen Sie die Schaltfläche **[!UICONTROL Speichern]** aus

   ![Gab dasselbe Produkt in den letzten 30 Tagen im Segment](assets/segment-purchasedMens.png)

## Batch- und Streaming-Segmentierung

Klicken Sie im linken Navigationsbereich auf **[!UICONTROL Segmente]** und überprüfen Sie die drei Segmente:

* Zwei unserer Segmente sind Batch-Segmente und eines ist ein Streaming-Segment.
* Die Plattform nutzt nach Möglichkeit Streaming-Segmentierung, um den Kunden für ein Segment zu qualifizieren, sobald er die Kriterien erfüllt. Wenn Segmentdefinitionen für das Streaming zu komplex sind, werden sie automatisch in Batch konvertiert. In diesem Fall wurde für die beiden Segmente standardmäßig ein Batch-Vorgang verwendet, da das Lookback-Fenster der Kaufereignisse länger als sieben Tage war. Eine vollständige und aktuelle Liste der Streaming-Einschränkungen finden Sie in der [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/streaming-segmentation.html?lang=de).
* Die Batch-Aufträge werden nach einem täglichen Zeitplan ausgeführt, der umgeschaltet werden kann.

![Gab dasselbe Produkt in den letzten 30 Tagen im Segment](assets/segment-review.png)

## Weitere Ressourcen

* [Dokumentation zum Segmentierungsdienst](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Referenz zur Segmentation Service-API](https://www.adobe.io/experience-platform-apis/references/segmentation/)

Die Segmentierung, insbesondere beim Aktivieren von Segmenten, hat noch einiges zu tun. Diese Themen werden in einem anderen Tutorial behandelt.

Du hast es durch alle Übungen geschafft! Fahren Sie mit der [Schlussfolgerung](conclusion.md) fort.
