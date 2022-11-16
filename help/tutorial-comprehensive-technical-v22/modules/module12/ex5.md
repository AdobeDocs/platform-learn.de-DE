---
title: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Analysieren von Google Analytics-Daten mithilfe von Customer Journey Analytics
description: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Analysieren von Google Analytics-Daten mithilfe von Customer Journey Analytics
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 600bd26a-aa5a-413a-8221-8e6e74ad6259
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '3325'
ht-degree: 3%

---

# 12.5 Google Analytics-Daten mithilfe von Customer Journey Analytics analysieren

## Ziele

- BigQuery-Datensatz mit Customer Journey Analytics (CJA) verbinden
- Verbinden Sie Google Analytics mit Treuedaten und schließen Sie sie an.
- Kennenlernen der CJA-Benutzeroberfläche

## 12.5.1 Verbindung erstellen

Navigieren Sie zu [analytics.adobe.com](https://analytics.adobe.com) , um auf Customer Journey Analytics zuzugreifen.

![Demo](./images/1a.png)

Gehen Sie auf der Customer Journey Analytics-Homepage zu **Verbindungen**.

![Demo](./images/conn1.png)

Hier sehen Sie alle Verbindungen, die zwischen CJA und Platform hergestellt wurden. Diese Verbindungen haben dasselbe Ziel wie Report Suites in Adobe Analytics. Die Erfassung der Daten ist jedoch völlig anders. Alle Daten stammen aus Adobe Experience Platform-Datensätzen.

![Demo](./images/2.png)

Klicken Sie auf **Neue Verbindung erstellen**.

![Demo](./images/conn3.png)

Sie werden dann die **Verbindung erstellen** Benutzeroberfläche.

![Demo](./images/5.png)

Zunächst müssen Sie die richtige Sandbox auswählen, die verwendet werden soll. Wählen Sie im Sandbox-Menü Ihre Sandbox aus, die `--aepSandboxId--`. In diesem Beispiel lautet die zu verwendende Sandbox **AEP-Aktivierung FY21**.

![Demo](./images/cjasb.png)

Nach Auswahl Ihrer Sandbox werden die verfügbaren Datensätze aktualisiert.

![Demo](./images/cjasb1.png)

Im linken Menü können Sie alle verfügbaren Adobe Experience Platform-Datensätze sehen. Suche nach dem Datensatz `Demo System - Event Dataset for BigQuery (Global v1.1)`. Klicken **+** , um den Datensatz zu dieser Verbindung hinzuzufügen.

![Demo](./images/6.png)

Nach dem Hinzufügen wird der Datensatz in der Verbindung angezeigt.

Sie müssen nun die **Personen-ID**. Stellen Sie sicher, dass **loyaltyId** als Personen-ID ausgewählt ist.

![Demo](./images/8.png)

Jetzt ergänzen Sie die Google Analytics-Website-Interaktionsdaten mit einem anderen Adobe Experience Platform-Datensatz.

Suche nach dem Datensatz `Demo System - Profile Dataset for Loyalty (Global v1.1)` und fügen Sie ihn dieser Verbindung hinzu.

![Demo](./images/10.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/10a.png)

Um beide Datensätze zusammenzuführen, müssen Sie eine **Personen-ID** die denselben ID-Typ enthält. Der Datensatz `Demo System - Profile Dataset for Loyalty (Global v1.1)` verwendet die **loyaltyId** als Personen-ID, die denselben ID-Typ wie die `Demo System - Event Dataset for BigQuery (Global v1.1)`, der auch die **loyaltyId** als Personen-ID.

![Demo](./images/12.png)

Klicken Sie auf **Weiter**.

![Demo](./images/14.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/15.png)

Hier müssen Sie Ihrer Verbindung einen Namen geben.

Bitte verwenden Sie diese Namenskonvention: `ldap - GA + Loyalty Data Connection`.

Beispiel: `vangeluw - GA + Loyalty Data Connection`

Bitte aktivieren Sie vor dem Fertigstellen auch **Automatisch ab heute alle neuen Daten für alle Datensätze in dieser Verbindung importieren.** wie in der Abbildung unten dargestellt.

![Demo](./images/16.png)

Dadurch wird alle 60 Minuten ein Datenfluss von Adobe Experience Platform nach CJA gestartet, bei großen Datenmengen kann es jedoch bis zu 24 Stunden dauern.

Sie müssen auch historische Daten aufstocken. Aktivieren Sie daher das Kontrollkästchen für **Alle vorhandenen Daten importieren** und wählen Sie **weniger als 1 Million** under **Durchschnittliche Anzahl der täglichen Ereignisse**.

![Demo](./images/17.png)

Nachdem Sie die **Verbindung** Es kann einige Stunden dauern, bis Ihre Daten in Customer Journey Analytics verfügbar sind.

Klicken **Speichern** und gehen Sie zur nächsten Übung.

![Demo](./images/cjasave.png)

Ihre Verbindung wird dann in der Liste der verfügbaren Verbindungen angezeigt.

![Demo](./images/18.png)

## 12.5.2 Datenansicht erstellen

Nachdem die Verbindung hergestellt wurde, können Sie jetzt Fortschritte bei der Beeinflussung der Visualisierung erzielen. Ein Unterschied zwischen Adobe Analytics und CJA besteht darin, dass CJA eine Datenansicht benötigt, um die Daten vor der Visualisierung zu bereinigen und vorzubereiten.

Eine Datenansicht ähnelt dem Konzept von Virtual Report Suites in Adobe Analytics, wo Sie kontextbezogene Besuchsdefinitionen, Filtervorgänge und auch die Art und Weise definieren, wie die Komponenten aufgerufen werden.

Sie benötigen mindestens eine Datenansicht pro Verbindung. Für einige Anwendungsfälle ist es jedoch großartig, mehrere Datenansichten für dieselbe Verbindung zu haben, um verschiedenen Teams unterschiedliche Einblicke zu geben.

Wenn Sie möchten, dass Ihr Unternehmen datengesteuert wird, sollten Sie anpassen, wie Daten in den einzelnen Teams angezeigt werden. Beispiele:

- UX-Metriken nur für das UX-Design-Team
- Verwenden Sie für Google Analytics dieselben Namen für KPIs und Metriken wie für Customer Journey Analytics, damit das Digital Analytics-Team nur 1 Sprache sprechen kann.
- Datenansicht gefiltert, um z. B. Daten nur für 1 Markt, 1 Marke oder nur für Mobilgeräte anzuzeigen.

Im **Verbindungen** aktivieren Sie das Kontrollkästchen vor der soeben erstellten Verbindung.

![Demo](./images/exta.png)

Jetzt klicken **Datenansicht erstellen**.

![Demo](./images/extb.png)

Sie werden zum **Datenansicht erstellen** Arbeitsablauf.

![Demo](./images/extc.png)

Sie können jetzt die grundlegenden Definitionen für Ihre Datenansicht konfigurieren. Dinge wie Zeitzone, Sitzungs-Timeout oder die Datenansichtsfilterung (der Segmentierungsteil ähnelt Virtual Report Suites in Adobe Analytics).

Die **Verbindung** die Sie in der vorherigen Übung erstellt haben, ist bereits ausgewählt. Ihre Verbindung heißt `ldap - GA + Loyalty Data Connection`.

![Demo](./images/ext5.png)

Geben Sie Ihrer Datenansicht als Nächstes einen Namen, der dieser Namenskonvention entspricht: `ldap - GA + Loyalty Data View`.

Geben Sie für die Beschreibung denselben Wert ein: `ldap - GA + Loyalty Data View`.

Vor der Analyse oder Visualisierung müssen wir eine Datenansicht mit allen Feldern, Dimensionen und Metriken und ihren Attributionseinstellungen erstellen.

| Feld | Namenskonvention | Beispiel |
| ----------------- |-------------|-------------|  
| Verbindung benennen | ldap - GA- und Loyalitätsdatenansicht | vangeluw - GA + Loyalty Data View |
| Beschreibung | ldap - GA- und Loyalitätsdatenansicht | vangeluw - GA + Loyalty Data View |

![Demo](./images/22.png)

Klicken **Speichern und fortfahren**.

![Demo](./images/23.png)

Sie können Ihrer Datenansicht jetzt Komponenten hinzufügen. Wie Sie sehen können, werden einige Metriken und Dimensionen automatisch hinzugefügt.

![Demo](./images/24.png)

Fügen Sie der Datenansicht die folgenden Komponenten hinzu:

| Name der Komponente | Typ der Komponente | Komponentenpfad |
| -----------------|-----------------|-----------------|
| usw | Dimension | _experienceplatform.loyaltyDetails.level |
| Punkte | Metrik | _experienceplatform.loyaltyDetails.points |
| commerce.checkouts.value | Metrik | commerce.checkouts.value |
| commerce.productListRemovals.value | Metrik | commerce.productListRemovals.value |
| commerce.productListAdds | Metrik | commerce.productListAdds |
| commerce.productViews.value | Metrik | commerce.productViews.value |
| commerce.purchases.value | Metrik | commerce.purchases.value |
| web.webPageDetails.pageViews | Metrik | web.webPageDetails.pageViews |
| Transaction ID | Dimension | commerce.order.payments.transactionID |
| channel.mediaType | Dimension | channel.mediaType |
| channel.typeAtSource | Dimension | channel.typeAtSource |
| Trackingcode | Dimension | marketing.trackingCode |
| gaid | Dimension | _experienceplatform.identification.core.gaid |
| web.webPageDetails.name | Dimension | web.webPageDetails.name |
| Ereignistyp | Dimension | eventType |
| Anbieter | Dimension | environment.browserDetails.vendor |
| Kennung | Dimension | _id |
| Zeitstempel | Dimension | timestamp |
| Typ | Dimension | device.type |
| loyaltyId | Dimension | _experiencePlatform.identification.core.loyaltyId |

Dann haben Sie Folgendes:

![Demo](./images/25.png)

Als Nächstes müssen Sie den Anzeigenamen einiger der oben genannten Metriken und Dimensionen ändern, damit Sie sie bei der Erstellung Ihrer Analyse einfach verwenden können. Wählen Sie dazu die Metrik oder Dimension aus und aktualisieren Sie die **Name** wie in der unten stehenden Abbildung angegeben.

![Demo](./images/25a.png)

| Ursprünglicher Komponentenname | Anzeigename |
| -----------------|-----------------|
| usw | Treuestufe |
| Punkte | Treuepunkte |
| commerce.checkouts.value | Checkouts |
| commerce.productListRemovals.value | Entnahme aus Warenkorb |
| commerce.productListAdds | Hinzufügungen zum Warenkorb |
| commerce.productViews.value | Produktansichten |
| commerce.purchases.value | Käufe |
| web.webPageDetails.pageViews | Page Views |
| channel.mediaType | Traffic-Medium |
| channel.typeAtSource | Traffic-Quelle |
| Trackingcode | Marketing-Kanal |
| gaid | Google Analytics-ID |
| Name | Seitentitel |
| Anbieter | Browser |
| Typ | Device Type |
| loyaltyId | Treueprogramm-ID |

Sie haben dann etwas wie das:

![Demo](./images/25b.png)

Als Nächstes müssen Sie einige Änderungen am Personen- und Sitzungskontext für einige dieser Komponenten vornehmen, indem Sie die **Attributionseinstellungen**.

![Demo](./images/25c.png)

Ändern Sie die **Attributionseinstellungen** für die folgenden Komponenten:

| Komponente |
| -----------------|
| Traffic-Quelle |
| Marketing-Kanal |
| Browser |
| Traffic-Medium |
| Gerätetyp |
| Google Analytics-ID |
| Treueprogramm-ID |
| Treuestufe |
| Treuepunkte |

Wählen Sie dazu die Komponente aus und klicken Sie auf **Verwenden eines benutzerdefinierten Attributionsmodells** und legen Sie die **Modell** nach **Letztkontakt** und die **Ablauf** nach **Person (Berichtsfenster)**. Wiederholen Sie diesen Vorgang für alle oben genannten Komponenten.

![Demo](./images/27a.png)

Nachdem Sie die Änderungen an den Attributionseinstellungen für alle oben genannten Komponenten vorgenommen haben, sollten Sie diese Ansicht haben:

![Demo](./images/27.png)

Ihre Datenansicht ist jetzt konfiguriert. Klicken Sie auf **Speichern**.

![Demo](./images/30.png)

Jetzt können Sie Google Analytics-Daten in Adobe Analytics Analysis Workspace analysieren. Lasst uns zur nächsten Übung übergehen.

## 12.5.3 Projekt erstellen

Gehen Sie im Customer Journey Analytics zu **Projekte**.

![Demo](./images/pro1.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/pro2.png)

Erstellen eines Projekts durch Klicken auf **Neues Projekt erstellen**.

![Demo](./images/pro3.png)

Sie haben jetzt ein leeres Projekt:

![Demo](./images/pro4.png)

Speichern Sie zunächst Ihr Projekt und geben Sie ihm einen Namen. Sie können den folgenden Befehl zum Speichern verwenden:

| BS | Kurzschnitt |
| ----------------- |-------------| 
| Windows | Kontrolle + S |
| Mac | Befehl + S |

Dieses Popup wird angezeigt:

![Demo](./images/prsave.png)

Bitte verwenden Sie diese Namenskonvention:

| Name | Beschreibung |
| ----------------- |-------------| 
| ldap - GA + Loyalitätsarbeitsbereich | ldap - GA + Loyalitätsarbeitsbereich |

Klicken Sie anschließend auf **Projekt speichern**.

![Demo](./images/prsave2.png)

Wählen Sie dann in der oberen rechten Ecke des Bildschirms die korrekte Datenansicht aus. Dies ist die Datenansicht, die Sie in der vorherigen Übung mit der Namenskonvention erstellt haben. `ldap - GA + Loyalty Data View`. In diesem Beispiel lautet die auszuwählende Datenansicht . `ldap - GA + Loyalty Data View`.

![Demo](./images/prdvlist.png)

![Demo](./images/prdv.png)

### 12.5.3.1 Freiformtabellen

Freiformtabellen funktionieren mehr oder weniger als Pivot-Tabellen in Excel. Sie wählen etwas aus der linken Leiste aus, ziehen es in die Freiform und erhalten einen Tabellenbericht.

Freiformtabellen sind fast grenzenlos. Sie können (fast) alles tun, was im Vergleich zu Google Analytics so viel Wert bringt (da dieses Tool einige Analyseeinschränkungen aufweist). Dies ist einer der Gründe, warum Google Analytics-Daten in ein anderes Analysetool geladen werden.

Sehen Sie sich zwei Beispiele an, in denen Sie SQL, BigQuery und einige Zeit benötigen, um einfache Fragen zu beantworten, die in der Google Analytics-Benutzeroberfläche oder Google Data Studio nicht möglich sind:

- Wie viele Personen gelangen zum Checkout aus dem Safari-Browser, aufgeteilt nach Marketing-Kanälen? Beachten Sie, dass die Checkout-Metrik vom Safari-Browser gefiltert wird. Die Variable Browser = Safari wurde einfach per Drag-and-Drop auf die Checkout-Spalte verschoben.

- Als Analytiker kann ich sehen, dass der Social Marketing-Kanal geringe Konversionen aufweist. Ich verwende die Letztkontakt-Attribution als Standard, aber was ist mit Erstkontakt? Wenn Sie den Mauszeiger über eine Metrik bewegen, werden die Metrikeinstellungen angezeigt. Dort kann ich das gewünschte Attributionsmodell auswählen. Sie können die Attribution in GA (nicht in Data Studio) als eigenständige Aktivität durchführen, aber Sie können keine anderen Metriken oder Dimensionen haben, die nicht mit der Attributionsanalyse in derselben Tabelle in Verbindung stehen.

Beantworten wir diese Fragen und weitere Fragen mit Analysis Workspace in CJA.

Wählen Sie zunächst den richtigen Datumsbereich (**Letzte 53 volle Wochen**) auf der rechten Seite des Bedienfelds.

![Demo](./images/pro11.png)

Klicken Sie anschließend auf **Anwenden** , um den Datumsbereich anzuwenden. Merken Sie sich diesen Schritt für die nächsten Übungen.

![Demo](./images/apply.png)

>[!NOTE]
>
>Wenn Sie die **Datenverbindung** und **Datenansicht** Sie müssen vielleicht ein paar Stunden warten. CJA benötigt etwas Zeit, um historische Daten aufzustocken, wenn eine große Menge an Datensätzen vorhanden ist.

Ziehen wir einige Dimensionen und Metriken per Drag-and-Drop in den Arbeitsbereich, um die Marketing-Kanäle zu analysieren. Verwenden Sie zuerst die Dimension **Marketingkanal** und ziehen Sie sie per Drag-and-Drop auf die Arbeitsfläche des **Freiformtabelle**. (Klicken Sie auf **Alle anzeigen** falls Sie die Metrik nicht sofort im Menü Metriken sehen)

![Demo](./images/pro14.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/pro14a.png)

Als Nächstes müssen Sie die Metriken zur Freiformtabelle hinzufügen. Sie sollten diese Metriken hinzufügen: **Personen**, **Sitzungen**, **Produktansichten**, **Checkouts**, **Käufe**, **Konversionsrate** (Berechnete Metrik).

Bevor Sie dies tun können, müssen Sie die berechnete Metrik erstellen **Konversionsrate**. Klicken Sie dazu auf die Schaltfläche **+** Symbol neben Metriken:

![Demo](./images/procalc1.png)

Verwenden Sie als Namen für die berechnete Metrik . **Konversionsrate**. Ziehen Sie dann die Metriken **purchase** und **Sitzungen** auf die Arbeitsfläche. Satz **Format** nach **Prozent** und **Dezimalstellen** nach **2**. Klicken Sie abschließend auf **Speichern**.

![Demo](./images/procalc2.png)

Als Nächstes verwenden Sie alle diese Metriken im **Freiformtabelle**, ziehen Sie sie einzeln auf die **Freiformtabelle**. Siehe Beispiel unten.

![Demo](./images/pro16.png)

Am Ende steht eine Tabelle wie diese:

![Demo](./images/pro16a.png)

Wie oben erwähnt, **Freiformtabellen** geben Ihnen die Freiheit, die Sie für eine tiefgehende Tauchanalyse benötigen. Sie können beispielsweise eine beliebige andere Dimension auswählen, um eine bestimmte Metrik in der Tabelle aufzuschlüsseln.

Navigieren Sie beispielsweise zu Dimensionen, suchen Sie nach und wählen Sie die **Browser** -Variable.

![Demo](./images/new1.png)

Daraufhin wird eine Übersicht der für diese Dimension verfügbaren Werte angezeigt.

![Demo](./images/new2.png)

Dimension auswählen **Safari** und ziehen Sie sie per Drag-and-Drop auf eine Metrik, z. B. **Checkouts**. Daraufhin sehen Sie Folgendes:

![Demo](./images/new3.png)

Dabei haben Sie nur eine potenzielle Frage beantwortet, die Sie hatten: Wie viele Personen gelangen mit Safari zur Checkout-Seite, aufgeteilt nach Marketing-Kanal?

Antworten wir jetzt auf die Frage Attribution .

Suchen Sie die **Kauf** Metrik in der Tabelle.

![Demo](./images/pro20.png)

Bewegen Sie den Mauszeiger über die Metrik und eine **Einstellungen** wird angezeigt. Klicken Sie darauf.

![Demo](./images/pro21.png)

Daraufhin wird ein Kontextmenü angezeigt. Aktivieren Sie das Kontrollkästchen für **Nicht standardmäßiges Attributionsmodell**.

![Demo](./images/pro22.png)

Im Popup-Fenster können Sie die Attributionsmodelle und das Lookback-Fenster einfach ändern (was mit SQL sehr komplex ist).

![Demo](./images/pro23.png)

Auswählen **Erstkontakt** als Ihr Attributionsmodell.

![Demo](./images/pro24.png)

Auswählen **Person** für das Lookback-Fenster.

![Demo](./images/pro25.png)

Jetzt klicken **Anwenden**.

![Demo](./images/pro26.png)

Sie können jetzt sehen, dass das Attributionsmodell für diese bestimmte Metrik jetzt Erstkontakt ist.

![Demo](./images/pro27.png)

Sie können beliebig viele Aufschlüsselungen ohne Einschränkungen für Variablentypen, Segmente, Dimensionen oder Datumsbereiche durchführen.

Noch wichtiger ist die Möglichkeit, beliebige Datensätze aus Adobe Experience Platform zu verknüpfen, um die digitalen Verhaltensdaten von Google Analytics anzureichern. Zum Beispiel Offline-, Callcenter-, Treueprogramm- oder CRM-Daten.

Um diese Funktion zu demonstrieren, konfigurieren wir Ihre erste Aufschlüsselung, die Offline-Daten mit Online-Daten kombiniert. Dimension auswählen **Treuestufe** und ziehen Sie sie per Drag &amp; Drop auf eine beliebige **Marketingkanal**, beispielsweise **Organische Suche**:

![Demo](./images/pro28.png)

Analysieren wir als Nächstes, welche **Gerätetyp** wird von Kunden verwendet, die mithilfe von **Organische Suche** mit **Treuestufe** , **Bronze**. Nehmen Sie die Dimension **Gerätetyp** und ziehen Sie es per Drag &amp; Drop auf **Bronze**. Daraufhin sehen Sie Folgendes:

![Demo](./images/pro29.png)

Sie können sehen, dass für Ihre erste Aufschlüsselung die Treuestufe verwendet wird. Diese Dimension stammt aus einem anderen Datensatz und aus einem anderen Schema als dem, das Sie für den BigQuery-Connector verwendet haben. Die Personen-ID **loyaltyID** (Demosystem - Ereignisschema für BigQuery (Global v1.1) und **loyaltyID** (Demosystem - Profilschema für Treueprogramm (Global v1.1)) stimmen überein. Daher können Sie Erlebnisereignisse von Google Analytics mit Profildaten aus dem Treueschema kombinieren.

Wir können die Zeilen weiterhin mit Segmenten oder bestimmten Datumsbereichen teilen (um möglicherweise bestimmte Fernsehkampagnen widerzuspiegeln), um Fragen an den Customer Journey Analytics zu stellen und die Antworten unterwegs zu erhalten.

Das gleiche Endergebnis mit SQL und dann einem Visualisierungs-Tool eines Drittanbieters zu erzielen, ist eine große Herausforderung. Besonders wenn Sie Fragen stellen und versuchen, die Antworten sofort zu bekommen. Customer Journey Analytics hat diese Herausforderung nicht und ermöglicht es Data Analysten, die Daten flexibel und in Echtzeit abzufragen.

## 12.5.3.2 Trichteranalyse oder Fallout-Analyse

Trichter eignen sich hervorragend, um die wichtigsten Schritte einer Journey zu verstehen. Diese Schritte können auch aus Offline-Interaktionen (z. B. vom Callcenter) stammen und dann mit digitalen Touchpoints im selben Trichter kombiniert werden.

Customer Journey Analytics ermöglicht Ihnen dies und vieles mehr. Wenn Sie sich an Modul 13 erinnern, können wir mit der rechten Maustaste klicken und Dinge wie:

- Analysieren, wohin die Benutzer nach einem Fallout-Schritt navigieren
- Erstellen eines Segments von einem beliebigen Punkt im Trichter
- Anzeigen des Trends in einer Liniendiagramm-Visualisierung


Sehen wir uns eine andere Möglichkeit an: Wie steht es um meinen Kunden-Journey-Trichter in diesem Monat im Vergleich zum Vormonat? Was ist mit Mobile vs Desktop?

Nachfolgend werden zwei Bedienfelder erstellt:

- Trichteranalyse (Januar)
- Trichteranalyse (Februar)

Sie werden sehen, dass wir einen Trichter über verschiedene Zeiträume (Januar und Februar) vergleichen, aufgeteilt nach Gerätetyp.

Diese Art von Analyse ist in der Google Analytics-Benutzeroberfläche nicht möglich oder sehr eingeschränkt. Customer Journey Analytics erhöht also die von Google Analytics erfassten Daten um einen weiteren wertvollen Faktor.

So erstellen Sie Ihre erste Fallout-Visualisierung. Schließen Sie das aktuelle Bedienfeld, um mit einem neuen zu beginnen.

Sehen Sie sich die rechte Seite des Bedienfelds an und klicken Sie auf den Pfeil, um es zu schließen.

![Demo](./images/pro33.png)

Klicken Sie anschließend auf **+** , um ein neues Bedienfeld zu erstellen.

![Demo](./images/pro35.png)

Wählen Sie nun die **Fallout** Visualisierung.

![Demo](./images/pro36.png)

Angenommen, Sie möchten wissen, was mit Ihrem Haupt-E-Commerce-Trichter passiert: Startseite > Interne Suche > Produktdetails > Checkout > Kauf.

Beginnen wir mit dem Hinzufügen neuer Schritte zum Trichter. Öffnen Sie dazu die **Seitenname** Dimension.

![Demo](./images/pro37.png)

Daraufhin werden alle verfügbaren Seiten angezeigt, die besucht wurden.

![Demo](./images/pro38.png)

Drag &amp; Drop **Startseite** zum ersten Schritt.

![Demo](./images/pro39.png)

Verwenden Sie als zweiten Schritt die **Suchergebnisse speichern**

![Demo](./images/pro40.png)

Jetzt müssen Sie einige E-Commerce-Aktionen hinzufügen. Suchen Sie in den Dimensionen nach der Dimension **Ereignistyp** Dimension. Klicken Sie auf , um die Dimension zu öffnen.

![Demo](./images/pro41.png)

Auswählen **product_detail_views** und ziehen Sie es in den nächsten Schritt.

![Demo](./images/pro43.png)

Auswählen **Product_Checkouts** und ziehen Sie es in den nächsten Schritt.

![Demo](./images/pro44.png)

Ändern Sie die Größe Ihrer Fallout-Visualisierung.

![Demo](./images/pro45.png)

Ihre Fallout-Visualisierung ist jetzt bereit.

Um die Einblicke zu analysieren und zu dokumentieren, ist es immer eine gute Idee, **Text** Visualisierung. So fügen Sie eine **Text** Visualisierung, klicken Sie auf die **Diagramm** im linken Menü, um alle verfügbaren Visualisierungen anzuzeigen. Ziehen Sie dann die **Text** Visualisierung auf der Arbeitsfläche. Ändern Sie die Größe und verschieben Sie sie so, dass sie wie unten dargestellt aussieht.

![Demo](./images/pro48.png)

Ändern Sie die Größe erneut, um sie an das Dashboard anzupassen:

![Demo](./images/pro49.png)

Fallouts-Visualisierungen ermöglichen auch Aufschlüsselungen. Verwenden Sie die **Gerätetyp** -Dimension durch Öffnen und Ziehen einiger der Werte einzeln in die Visualisierung:

![Demo](./images/pro50.png)

Sie erhalten eine erweiterte Visualisierung:

![Demo](./images/pro51.png)

Customer Journey Analytics ermöglicht Ihnen dies und vieles mehr. Durch Rechtsklick auf eine beliebige Stelle im Fallout...

- Analysieren, wohin die Benutzer von einem Fallout-Schritt gehen
- Erstellen eines Segments von einem beliebigen Punkt im Trichter
- Trend für jeden Schritt in einer Linienvisualisierung erstellen
- Vergleichen Sie alle Trichter visuell mit verschiedenen Zeiträumen.

Führen Sie beispielsweise einen Rechtsklick in einen beliebigen Schritt des Fallout aus, um einige dieser Analyseoptionen anzuzeigen.

![Demo](./images/pro52.png)

## 12.5.3.3 Flussanalyse und Visualisierung

Wenn Sie die erweiterte Flussanalyse mit Google Analytics durchführen möchten, müssen Sie SQL verwenden, um die Daten zu extrahieren, und dann eine Drittanbieterlösung für den Visualisierungsteil verwenden. Customer Journey Analytics wird dabei helfen.

In diesem Schritt konfigurieren Sie eine Flussanalyse, um diese Frage zu beantworten: Welche Hauptbeitragskanäle vor einer bestimmten Landingpage genutzt werden?  Mit zwei Drag-and-Drop-Vorgängen und einem Klick als Analytiker können Sie den Fluss des Benutzers zur Landingpage mit den beiden letzten Touches der Marketing-Kanäle erkennen.

Andere Fragen, die Customer Journey Analytics beantworten kann:

- Was ist die Hauptkombination von Kanälen vor einer bestimmten Landingpage?
- Was veranlasst einen Benutzer, die Sitzung zu beenden, wenn er zum Product_Checkout gelangt? Wo liegen die vorherigen Schritte?

Beginnen wir mit einem leeren Bedienfeld, um diese Fragen zu beantworten. Schließen Sie das aktuelle Bedienfeld und klicken Sie auf **+**.

![Demo](./images/pro53.png)

Wählen Sie nun die **Fluss** Visualisierung.

![Demo](./images/pro54.png)

Erstellen wir nun eine kanalübergreifende Analyse des Marketingkanalflusses mit mehreren Pfaden. Ziehen Sie die **Marketingkanal** Dimension auf **Einstiegs-Dimensionen** Bereich.

![Demo](./images/pro55.png)

Sie können nun die ersten Einstiegspfade sehen:

![Demo](./images/pro56.png)

Klicken Sie auf den ersten Pfad, um einen Drilldown durchzuführen.

![Demo](./images/pro58.png)

Jetzt wird der nächste Pfad (Marketingkanal) angezeigt.

![Demo](./images/pro59.png)

Machen wir einen dritten Drilldown. Klicken Sie auf die erste Option im neuen Pfad, **Verweis**.

![Demo](./images/pro60.png)

Die Visualisierung sollte nun wie folgt dargestellt werden:

![Demo](./images/pro61.png)

Komplizieren wir die Dinge! Angenommen, Sie möchten analysieren, was die Landingpage nach zwei Marketingpfaden war? Dazu können Sie eine sekundäre Dimension verwenden, um den letzten Pfad zu ändern. Suchen Sie die **Seitenname** und ziehen Sie sie wie folgt in den Arbeitsbereich:

![Demo](./images/pro62n.png)

Jetzt sehen Sie Folgendes:

![Demo](./images/pro63n.png)

Lasst uns eine andere Flussanalyse durchführen. Diesmal analysieren Sie, was nach einem bestimmten Ausstiegspunkt passiert ist. Andere Analytics-Lösungen erfordern die Verwendung von SQL/ETL und wiederum ein Visualisierungstool von Drittanbietern, um dasselbe zu erreichen.

Neue Funktionen **Flussvisualisierung** zum Bereich hinzu.

![Demo](./images/pro64.png)

Dann haben Sie Folgendes:

![Demo](./images/pro64a.png)

Dimension suchen **Ereignistyp** und ziehen Sie sie per Drag-and-Drop in die **Ausstiegsdimension** Bereich.

![Demo](./images/pro65.png)

Jetzt können Sie sehen, **Ereignistyp**-Pfade haben Kunden zum Ausstieg geführt.

![Demo](./images/pro66.png)

Lassen Sie uns untersuchen, was vor dem Beenden der Kasse-Aktion passiert ist. Klicken Sie auf **Product_Checkouts** path:

![Demo](./images/pro67.png)

Ein neuer Aktionspfad wird mit einigen Daten angezeigt, die nicht aufschlussreich sind.

![Demo](./images/pro68.png)

Lasst uns weiter analysieren! Dimension durchsuchen **Seitenname** und ziehen Sie sie in den neuen generierten Pfad.

![Demo](./images/pro69.png)

Sie haben jetzt eine erweiterte Flussanalyse in Minutenschnelle durchgeführt. Sie können auf die verschiedenen Pfade klicken, um zu sehen, wie sie sich vom Ausstieg zu den vorherigen Schritten verbinden.

![Demo](./images/pro70.png)

Sie verfügen jetzt über ein leistungsstarkes Kit, um Trichter zu analysieren und Pfade des Kundenverhaltens über digitale, aber auch Offline-Touchpoints zu untersuchen.

Vergiss nicht, deine Änderungen zu speichern!

## 12.5.4 Projekt freigeben

>[!IMPORTANT]
>
>Der folgende Inhalt ist als FYI gedacht - Sie tun dies **NOT** müssen Ihr Projekt für andere freigeben.

FYI - Sie können dieses Projekt mit Kollegen teilen, um zusammenzuarbeiten oder Geschäftsfragen gemeinsam zu analysieren.

![Demo](./images/pro99.png)

![Demo](./images/pro100.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 12](./customer-journey-analytics-bigquery-gcp.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
