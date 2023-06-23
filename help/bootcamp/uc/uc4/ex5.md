---
title: Bootcamp - Customer Journey Analytics - Visualisierung mit Customer Journey Analytics
description: Bootcamp - Customer Journey Analytics - Visualisierung mit Customer Journey Analytics
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 051b5b91-56c4-414e-a4c4-74aa67219551
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '1497'
ht-degree: 2%

---

# 4.5 Visualisierung mit Customer Journey Analytics

## Ziele

- Grundlegendes zur Benutzeroberfläche von Analysis Workspace
- Lernen Sie einige Funktionen kennen, die Analysis Workspace so anders machen.
- Erfahren Sie, wie Sie mit Analysis Workspace in CJA analysieren.

## Kontext

In dieser Übung verwenden Sie Analysis Workspace in CJA, um Produktansichten, Produkttribute, Abwanderungen usw. zu analysieren.

Verwenden wir das Projekt, das Sie in [4.4 Datenvorbereitung in Analysis Workspace](./ex4.md), also gehen Sie zu [https://analytics.adobe.com](https://analytics.adobe.com).

![Demo](./images/prohome.png)

Öffnen Sie Ihr Projekt `yourLastName - Omnichannel Analysis`.

Mit geöffnetem Projekt und Datenansicht `CJA Bootcamp - Omnichannel Data View` ausgewählt haben, können Sie mit der Erstellung Ihrer ersten Visualisierungen beginnen.

![Demo](./images/prodataView1.png)

## Wie viele Produktansichten haben wir täglich?

Zunächst müssen wir die richtigen Daten für die Analyse der Daten auswählen. Gehen Sie auf der rechten Seite der Arbeitsfläche zum Kalender -Dropdown. Klicken Sie darauf und wählen Sie den entsprechenden Datumsbereich aus.

>[!IMPORTANT]
>
>Die neuesten verfügbaren Daten wurden am 9.19.2022 erfasst. Bitte wählen Sie einen Datumsbereich aus, der dieses Datum enthält.

![Demo](./images/pro1.png)

Suchen Sie im Menü links (Komponentenbereich) die berechnete Metrik **Produktansichten**. Wählen Sie sie aus und ziehen Sie sie per Drag-and-Drop in die Arbeitsfläche oben rechts in der Freiformtabelle.

![Demo](./images/pro2.png)

Automatisch die Dimension **Tag** wird hinzugefügt, um Ihre erste Tabelle zu erstellen. Jetzt können Sie sehen, wie Ihre Frage direkt beantwortet wird.

![Demo](./images/pro3.png)

Klicken Sie anschließend mit der rechten Maustaste auf die Metrikzusammenfassung.

![Demo](./images/pro4.png)

Klicken Sie auf **Visualisieren** und wählen Sie **Linie** als Visualisierung.

![Demo](./images/pro5.png)

Sie sehen Ihre Produktansichten nach Tag.

![Demo](./images/pro6.png)

Sie können den Zeitrahmen von Tag zu Tag ändern, indem Sie auf **Einstellungen** innerhalb der Visualisierung.

![Demo](./images/pro7.png)

Klicken Sie auf den Punkt neben **Linie** nach **Datenquelle verwalten**.

![Demo](./images/pro7a.png)

Klicken Sie anschließend auf **Auswahl sperren** und wählen Sie **Ausgewählte Elemente** , um diese Visualisierung so zu sperren, dass immer eine Zeitleiste von Produktansichten angezeigt wird.

![Demo](./images/pro7b.png)

## Die vier beliebtesten Produkte

Welche Produkte werden am häufigsten angezeigt?

Vergessen Sie nicht, das Projekt ab und zu zu zu speichern.

| BS | Kurzschnitt |
| ----------------- |-------------| 
| Windows | Kontrolle + S |
| Mac | Befehl + S |

Beginnen wir damit, die vier am häufigsten angezeigten Produkte zu finden. Suchen Sie im Menü links die **Produktname** - Dimension.

![Demo](./images/pro8.png)

Jetzt ziehen und ablegen **Produktname** , um **Tag** Dimension:

Dies ist das Ergebnis

![Demo](./images/pro10a.png)

Versuchen Sie als Nächstes, eines der Produkte nach Markenname aufzuschlüsseln. Suchen Sie nach **brandName** und ziehen Sie es unter den ersten Produktnamen.

![Demo](./images/pro13.png)

Erstellen Sie anschließend eine Aufschlüsselung anhand der Treuestufe. Suchen Sie nach **Treuestufe** und ziehen Sie es unter den Markennamen.

![Demo](./images/pro15.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/pro15a.png)

Schließlich können Sie weitere Visualisierungen hinzufügen. Suchen Sie auf der linken Seite unter &quot;Visualisierungen&quot;nach `Donut`. Nehmen Sie `Donut`, ziehen Sie sie per Drag-and-Drop auf die Arbeitsfläche unter **Linie** Visualisierung.

![Demo](./images/pro18.png)

Wählen Sie als Nächstes in der Tabelle die 3 **Treuestufe**  Zeilen aus der Aufschlüsselung, die wir unter **Google Pixel XL 32 GB Black Smartphone** > **Citi Signal**. Halten Sie bei Auswahl der drei Zeilen die **STRG** (unter Windows) oder **Befehl** Schaltfläche (in Mac).

![Demo](./images/pro20.png)

Das Ringdiagramm wird sich ändern:

![Demo](./images/pro21.png)

Sie können das Design sogar so anpassen, dass es lesbarer ist, indem Sie beide **Linie** und **Ringdiagramm** Gravieren Sie ein wenig kleiner, damit sie nebeneinander platziert werden können:

![Demo](./images/pro22.png)

Klicken Sie auf den Punkt neben **Ringdiagramm** nach **Datenquelle verwalten**.
Klicken Sie anschließend auf **Auswahl sperren** , um diese Visualisierung so zu sperren, dass immer eine Zeitleiste von Produktansichten angezeigt wird.

![Demo](./images/pro22b.png)

Weitere Informationen zu Visualisierungen mit Analysis Workspace finden Sie hier:

- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html?lang=de](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html?lang=de)
- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html)

## Produkt-Interaktionstrichter, vom Anzeigen bis zum Kauf

Es gibt viele Möglichkeiten, diese Frage zu lösen. Eine davon besteht darin, den Interaktionstyp &quot;Produkt&quot;zu verwenden und ihn in einer Freiformtabelle zu verwenden. Eine andere Möglichkeit besteht darin, eine **Fallout-Visualisierung**. Verwenden wir die letzte, die wir gleichzeitig visualisieren und analysieren möchten.

Schließen Sie das aktuelle Bedienfeld, das wir haben, indem Sie hier klicken:

![Demo](./images/pro23.png)

Fügen Sie jetzt ein neues leeres Bedienfeld hinzu, indem Sie auf **+ Leeres Bedienfeld hinzufügen**.

![Demo](./images/pro24.png)

Klicken Sie auf die Visualisierung **Fallout**.

![Demo](./images/pro25.png)

Wählen Sie denselben Datumsbereich wie in der vorherigen Übung aus.

![Demo](./images/pro1.png)

Dann wirst du das sehen.

![Demo](./images/prodatefa.png)

Dimension suchen **Ereignistyp** unter den Komponenten auf der linken Seite:

![Demo](./images/pro26.png)

Klicken Sie auf den Pfeil, um die Dimension zu öffnen:

![Demo](./images/pro27.png)

Es werden alle verfügbaren Ereignistypen angezeigt.

![Demo](./images/pro28.png)

Element auswählen **commerce.productViews** und ziehen Sie sie per Drag-and-Drop auf **Touchpoint hinzufügen** -Feld in **Fallout-Visualisierung**.

![Demo](./images/pro29.png)

Dasselbe gilt für **commerce.productListAdds** und **commerce.purchases** und legen Sie sie auf **Touchpoint hinzufügen** -Feld in **Fallout-Visualisierung**. Ihre Visualisierung sieht nun wie folgt aus:

![Demo](./images/props1.png)

Du kannst hier vieles tun. Beispiele: Vergleich im Zeitverlauf, Vergleich jedes Schritts nach Gerät oder Vergleich nach Treue. Wenn wir jedoch interessante Dinge analysieren möchten, z. B. warum Kunden nach dem Hinzufügen eines Artikels zum Warenkorb keinen Kauf tätigen, können wir das beste Tool in CJA verwenden: Rechtsklick.

Rechtsklick auf den Touchpoint **commerce.productListAdds**. Klicken Sie anschließend auf **Aufschlüsselungs-Fallout an diesem Touchpoint**.

![Demo](./images/pro32.png)

Es wird eine neue Freiformtabelle erstellt, in der analysiert wird, was die Personen getan haben, wenn sie nichts gekauft haben.

![Demo](./images/pro33.png)

Ändern Sie die **Ereignistyp** von **Seitenname** in der neuen Freiformtabelle, um zu sehen, welche Seiten sie anstelle der Kaufbestätigungsseite besuchen.

![Demo](./images/pro34.png)

## Was machen Personen auf der Site, bevor sie die Seite &quot;Abbrechen&quot;aufrufen?

Auch hier gibt es viele Möglichkeiten, diese Analyse durchzuführen. Verwenden wir die Flussanalyse, um den Erkundungsteil zu starten.

Schließen Sie das aktuelle Bedienfeld, indem Sie hier klicken:

![Demo](./images/pro0.png)

Fügen Sie jetzt ein neues leeres Bedienfeld hinzu, indem Sie auf **+ Leeres Bedienfeld hinzufügen**.

![Demo](./images/pro0a.png)

Klicken Sie auf die Visualisierung **Fluss**.

![Demo](./images/pro35.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/pro351.png)

Wählen Sie denselben Datumsbereich wie in der vorherigen Übung aus.

![Demo](./images/pro1.png)

Dimension suchen **Seitenname** unter den Komponenten auf der linken Seite:

![Demo](./images/pro36.png)

Klicken Sie auf den Pfeil, um die Dimension zu öffnen:

![Demo](./images/pro37.png)

Sie finden alle angezeigten Seiten. Suchen Sie den Seitennamen: **Dienst abbrechen**.
Drag &amp; Drop **Dienst abbrechen** in die Flussvisualisierung des mittleren Felds ein:

![Demo](./images/pro38.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/pro40.png)

Analysieren wir nun, ob Kunden, die die **Dienst abbrechen** auf der Website auch Callcenter genannt, und was das Ergebnis war.

Gehen Sie unter den Dimensionen zurück und suchen Sie dann nach **Interaktionstyp aufrufen**.
Drag &amp; Drop **Interaktionstyp aufrufen** , um die erste Interaktion auf der rechten Seite innerhalb der **Flussvisualisierung**.

![Demo](./images/pro43.png)

Jetzt sehen Sie das Supportticket der Kunden, die das Callcenter nach dem Besuch der **Dienst abbrechen** Seite.

![Demo](./images/pro44.png)

Suchen Sie als Nächstes unter den Dimensionen nach **Rufempfindlichkeit**.  Ziehen Sie es per Drag-and-Drop in den Arbeitsbereich, um die erste Interaktion auf der rechten Seite im **Flussvisualisierung**.

![Demo](./images/pro46.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/flow.png)

Wie Sie sehen können, haben wir mithilfe der Flussvisualisierung eine Omnichannel-Analyse durchgeführt. Dadurch haben wir herausgefunden, dass einige Kunden, die daran gedacht haben, ihren Dienst abzubrechen, ein positives Gefühl hatten, nachdem sie das Callcenter angerufen hatten. Haben wir vielleicht mit einer Beförderung ihre Meinung geändert?


## Wie funktionieren Kunden mit einem positiven Callcenter-Kontakt mit den wichtigsten KPIs?

Segmentieren wir zunächst die Daten, um nur Benutzer mit **positive** -Aufrufe. In CJA werden Segmente als Filter bezeichnet. Navigieren Sie zu Filtern im Komponentenbereich (links) und klicken Sie auf **+**.

![Demo](./images/pro58.png)

Benennen Sie den Filter im Filter-Builder.

| Name | Beschreibung |
| ----------------- |-------------| 
| Rufempfindlichkeit - positiv | Rufempfindlichkeit - positiv |

![Demo](./images/pro47.png)

Suchen Sie unter den Komponenten (innerhalb des Filteraufbaus) nach **Rufempfindlichkeit** und ziehen Sie sie per Drag-and-Drop in die Filtergenerator-Definition.

![Demo](./images/pro48.png)

Jetzt auswählen **positive** als Wert für den Filter.

![Demo](./images/pro49.png)

Ändern des Perimeter **Person** Ebene.

![Demo](./images/pro50.png)

Klicken Sie abschließend einfach auf **Speichern**.

![Demo](./images/pro51.png)

Du wirst dann wieder hier sein. Wenn noch nicht geschehen, schließen Sie das vorherige Bedienfeld.

![Demo](./images/pro0c.png)

Fügen Sie jetzt ein neues leeres Bedienfeld hinzu, indem Sie auf **+ Leeres Bedienfeld hinzufügen**.

![Demo](./images/pro24c.png)

Wählen Sie denselben Datumsbereich wie in der vorherigen Übung aus.

![Demo](./images/pro1.png)

Klicken Sie auf **Freiformtabelle**.

![Demo](./images/pro52.png)

Ziehen Sie nun den soeben erstellten Filter in den Arbeitsbereich.

![Demo](./images/pro53.png)

Zeit zum Hinzufügen einiger Metriken. Beginnen mit **Produktansichten**. Ziehen Sie die Freiformtabelle in den Arbeitsbereich. Sie können auch die **Veranstaltungen** Metrik.

![Demo](./images/pro54.png)

Dasselbe gilt für **Personen**,  **Zum Warenkorb hinzufügen** und **Käufe**. Du wirst am Ende einen Tisch wie diesen haben.

![Demo](./images/pro55.png)

Dank der ersten Flussanalyse kam eine neue Frage in den Sinn. Also haben wir beschlossen, diese Tabelle zu erstellen und einige KPIs mit einem Segment zu vergleichen, um diese Frage zu beantworten. Wie Sie sehen können, ist die Zeit für Einblicke viel schneller als die Verwendung von SQL oder andere BI-Lösungen.

## Customer Journey Analytics- und Analysis Workspace-Neukodifizierung

Wie Sie in diesem Labor erfahren haben, ordnet Analysis Workspace Daten aus allen Kanälen zu, um die vollständige Journey zu analysieren. Beachten Sie außerdem, dass Sie Daten in denselben Arbeitsbereich bringen können, der nicht mit dem Journey verbunden ist.
Es kann sehr nützlich sein, getrennte Daten in Ihre Analyse aufzunehmen, um dem Journey Kontext zu geben. Einige Beispiele sind NPS-Daten, Umfragen, Facebook Ads-Ereignisse oder Offline-Interaktionen (nicht identifiziert).

Nächster Schritt: [4.6 Von Einblicken zu Aktionen](./ex6.md)

[Zurück zum Benutzerfluss 4](./uc4.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
