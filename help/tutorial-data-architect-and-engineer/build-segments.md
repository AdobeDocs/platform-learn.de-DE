---
title: Erstellen von Segmenten
seo-title: Build segments | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Erstellen von Segmenten
description: In dieser Lektion erstellen wir einige Segmente auf der Grundlage der Profildaten, die wir in den vorherigen Lektionen aufgenommen haben.
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
In dieser Lektion erstellen wir einige Segmente basierend auf den Profildaten, die wir in den vorherigen Lektionen aufgenommen haben.

Sobald Sie über Echtzeit-Kundenprofile verfügen, können Sie Segmente von Einzelpersonen erstellen, die ähnliche Eigenschaften aufweisen und möglicherweise ähnlich auf Marketing-Strategien reagieren. Die Bausteine dieser Segmente sind die XDM-Felder, die Sie zuvor erstellt haben.

**Datenarchitekten** müssen außerhalb dieses Tutorials Segmente erstellen und ihre Kollegen bei dieser Aufgabe unterstützen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über das Erstellen von Segmenten zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27254?learn=on)


## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Durchführen dieser Lektion erforderlich sind, insbesondere:

* Berechtigungselemente **[!UICONTROL Profilverwaltung]** > **[!UICONTROL Segmente verwalten]**, **[!UICONTROL Segmente anzeigen]** und **[!UICONTROL Zielgruppensegment exportieren]**
* Berechtigungselemente **[!UICONTROL Profilverwaltung]** > **[!UICONTROL Profile anzeigen]** und **[!UICONTROL Profile verwalten]**
* Berechtigungselement **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* Benutzerrollenzugriff auf das `Luma Tutorial Platform` Produktprofil
* Zugriff auf das Produktprofil &quot;`Luma Tutorial Platform`&quot; mit Entwicklerrolle (für API)

## Erstellen eines Basissegments

Erstellen wir ein einfaches Segment für Kundinnen und Kunden des Treueprogramms mit einem Gold- oder Platin-Status

1. Navigieren Sie in der Platform-Benutzeroberfläche **[!UICONTROL linken]** zu „Segmente“
1. Klicken Sie auf **[!UICONTROL Schaltfläche]** Segment erstellen“
1. Auf der linken Seite des Schema Builders befinden sich drei Registerkarten für Attribute (Datensatzdaten), Ereignisse (Zeitreihendaten) und Zielgruppen
1. Wählen Sie das Zahnradsymbol aus, um zu beachten, dass Segment Builder standardmäßig nur Felder mit Daten anzeigt und Ihnen das Ändern der Zusammenführungsrichtlinie ermöglicht
1. Navigieren Sie auf der Registerkarte „Attribute **zum Ordner „Individuelles XDM-Profil > Treue** (Sie können auch nach „Treue“ suchen)
1. Ziehen Sie per Drag-and-Drop `Tier` aus dem Menü Attributfelder auf die Arbeitsfläche des Segment Builders
1. Wählen Sie `Tier` ist gleich `Gold` oder `Platinum`
1. Wählen Sie **[!UICONTROL Schätzung aktualisieren]**, um anzuzeigen, wie viele Profile für Ihr Segment qualifiziert sind
1. Geben Sie als **[!UICONTROL Name]** `Luma customers with level Gold or Above`
1. Wählen Sie **[!UICONTROL Speichern]**
   ![Segment](assets/segment-goldOrAbove.png)

<!--## Build a sequential segment-->

## Dynamisches Segment erstellen

In dieser Übung erstellen wir ein Segment für Kunden, die dasselbe Produkt zweimal innerhalb von 30 Tagen gekauft haben. Dynamische Segmente ermöglichen es Ihnen, Ihre Segmentierung mithilfe von Feldern als Variablen zu skalieren.

1. Navigieren Sie **[!UICONTROL linken]** zu „Segmente“
1. Klicken Sie auf **[!UICONTROL Schaltfläche]** Segment erstellen“
1. Wählen Sie die **[!UICONTROL Ereignisse]** aus
1. Liste nach `purchases` filtern
1. Ziehen Sie **[!UICONTROL Ereignistyp]** Bestellungen“ zweimal _die Arbeitsfläche_
1. Wählen Sie das Uhrensymbol zwischen den beiden **[!UICONTROL Käufe]** und wählen Sie „Innerhalb von 30 Tagen“ aus.
1. Bestätigen Sie, dass in Ihrer Segmentdefinition an dieser Stelle **steht: „Zielgruppe einschließen, die mindestens 1 Kaufereignis haben und dann innerhalb von 30 Tagen mindestens 1 Kaufereignis haben“**
   ![Zwei Käufe innerhalb von 30 Tagen](assets/segment-twoPurchases.png)
1. Ändern Sie nun den Ereignisfilter in `sku`
1. Ziehen Sie das Feld SKU zum zweiten Kaufereignis.
   ![Zwei Käufe innerhalb von 30 Tagen mit SKU](assets/segment-twoPurchases-addSku.png)
1. Löschen Sie jetzt den Ereignisfilter
1. Im Abschnitt **[!UICONTROL Variablen durchsuchen]** sollten Sie sehen, dass es Ordner für die beiden Kaufereignisse gibt. Klicken, um zu **[!UICONTROL Bestellungen 1]**\
   ![Zwei Käufe innerhalb von 30 Tagen mit SKU, durchsuchen Sie den ersten Kauf](assets/segment-twoPurchases-browsePurchaseOne.png)
1. Drilldown in den Ordner **[!UICONTROL Produktlistenelemente]** durchführen, das Feld **[!UICONTROL SKU]** auswählen und es rechts neben den **[!UICONTROL Gleich]** ziehen. Wenn Sie den Mauszeiger über den Bereich bewegen, legen Sie ihn im Abschnitt „Zum Vergleichen hinzufügen“ ab
1. Benennen des Segments `Bought same product within 30 days`
1. Vergewissern Sie sich, dass Ihre Zielgruppendefinition **lautet: „Zielgruppe einschließen, die mindestens 1 Kaufereignis haben und dann innerhalb von 30 Tagen mindestens 1 Kaufereignis haben, bei dem (SKU gleich Einkäufe1 SKU))“**
1. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Habe das gleiche Produkt in den letzten 30 Tagen gekauft](assets/segment-boughtSameProduct.png)

## Segment mit mehreren Entitäten erstellen

Erinnern Sie sich, wie wir die Beziehung zwischen dem `Luma Offline Purchase Events Schema` und dem `Luma Product Catalog Schema` in früheren Lektionen erstellt haben? Wir haben dies getan, damit wir die Beziehung in unserem Schema verwenden konnten, wobei die Segmentierung mehrerer Entitäten verwendet wurde.

Mit der erweiterten Segmentierungsfunktion für mehrere Entitäten können Sie Segmente mithilfe mehrerer XDM-Klassen erstellen, um Ihre Schemata zu erweitern. Daher kann Segment Builder auf zusätzliche Felder zugreifen, als ob sie nativ im Profildatenspeicher enthalten wären

Sie erstellen das nächste Segment, indem Sie die Beziehung anwenden, die Sie zwischen Ihrer `Luma Product Catalog Schema` und Ihrer `Luma Offline Purchase Events Schema` erstellt haben.

1. Navigieren Sie **[!UICONTROL linken]** zu „Segmente“
1. Klicken Sie auf **[!UICONTROL Schaltfläche]** Segment erstellen“
1. Wählen Sie die **[!UICONTROL Ereignisse]** aus
1. Liste nach `purchases` filtern
1. Ziehen Sie **[!UICONTROL Ereignistyp]** Bestellungen“ auf die Arbeitsfläche
1. Wählen Sie das Uhren-Dropdown-Menü über dem Ereignis aus und wählen Sie **[!UICONTROL in den letzten 30 Tagen]**
1. Filtern Sie die **[!UICONTROL Ereignisse]**-Liste nach `category` und ziehen Sie dann das Feld **[!UICONTROL Produktkategorie]** auf **[!UICONTROL Bestellungen]**
1. Ändern Sie den Operator in **[!UICONTROL beginnt mit]** und geben Sie `men` in das Textfeld ein
1. Geben Sie als **[!UICONTROL Name]** `Purchased a Men's product in the last 30 days`
1. Bestätigen der Zielgruppendefinition `(Include audience who have at least 1 Purchases event where ((Product Category starts with men)) ) and occurs in last 30 day(s)`
1. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Habe das gleiche Produkt in den letzten 30 Tagen gekauft](assets/segment-purchasedMens.png)

## Batch- und Streaming-Segmentation

Klicken Sie **[!UICONTROL linken Navigationsbereich auf]** Segmente“. Sehen wir uns nun unsere drei Segmente an:

* Zwei unserer Segmente sind Batch-Segmente und eines ist ein Streaming-Segment.
* Platform verwendet standardmäßig die Streaming-Segmentierung, sofern dies möglich ist. Dadurch wird der Kunde für ein Segment qualifiziert, sobald er die Kriterien erfüllt. Wenn Segmentdefinitionen für Streaming zu komplex sind, werden sie automatisch in Batch konvertiert. In diesem Fall sind die beiden Segmente standardmäßig im Batch-Modus, da das Lookback-Fenster der Kaufereignisse länger als sieben Tage dauerte. Eine vollständige und aktuelle Liste der Streaming-Einschränkungen finden Sie unter [Dokumentation](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/streaming-segmentation).
* Die Batch-Vorgänge werden nach einem täglichen Zeitplan ausgeführt, der deaktiviert werden kann.

![Habe das gleiche Produkt in den letzten 30 Tagen gekauft](assets/segment-review.png)

## Weitere Ressourcen

* [Dokumentation zum Segmentierungs-Service](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=de)
* [Segmentation Service-API-Referenz](https://www.adobe.io/experience-platform-apis/references/segmentation/)

Die Segmentierung ist komplexer, insbesondere beim Aktivieren von Segmenten. Diese Themen werden in einem anderen Tutorial behandelt.

Du hast es durch alle Übungen geschafft! Bitte fahren Sie mit der [Schlussfolgerung](conclusion.md) fort.
