---
title: Daten aus Google Analytics in Adobe Experience Platform mit BigQuery Source Connector erfassen und analysieren - Daten aus BigQuery in Adobe Experience Platform laden
description: Daten aus Google Analytics in Adobe Experience Platform mit BigQuery Source Connector erfassen und analysieren - Daten aus BigQuery in Adobe Experience Platform laden
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 4%

---

# 4.2.4 Daten aus BigQuery in Adobe Experience Platform laden

## Ziele

- BigQuery-Daten einem XDM-Schema zuordnen
- BigQuery-Daten in Adobe Experience Platform laden
- Machen Sie sich mit der Benutzeroberfläche von BigQuery Source Connector vertraut

## Vorbereitung

Nach Übung 12.3 sollte diese Seite in Adobe Experience Platform geöffnet sein:

![demo](./images/datasets.png)

**Wenn Sie es geöffnet haben, fahren Sie mit Übung 12.4.1 fort.**

**Wenn Sie es nicht geöffnet haben, gehen Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform/home).**

Gehen Sie im linken Menü zu Quellen . Anschließend sehen Sie die Homepage **Quellen**. Klicken Sie im Menü **Quellen** auf **Datenbanken**.

![demo](./images/sourceshome.png)

Wählen Sie den Source Connector **Google BigQuery** aus und klicken Sie auf **+ Konfigurieren**.

![demo](./images/bq.png)

Daraufhin wird der Bildschirm zur Auswahl des Google BigQuery-Kontos angezeigt.

![demo](./images/0-c.png)

Wählen Sie Ihr Konto aus und klicken Sie auf **Weiter**.

![demo](./images/ex4/0-d.png)

Daraufhin wird die Ansicht **Daten hinzufügen** angezeigt.

![demo](./images/datasets.png)

## 4.2.4.1 BigQuery-Tabellenauswahl

Wählen Sie in der Ansicht **Daten hinzufügen** Ihren BigQuery-Datensatz aus.

![demo](./images/datasets.png)

Sie können jetzt eine Datenvorschau der Google Analytics in BigQuery sehen.

Klicken Sie auf **Weiter**.

![demo](./images/ex4/3.png)

## 4.2.4.2 XDM-Zuordnung

Jetzt sehen Sie Folgendes:

![demo](./images/xdm4a.png)

Jetzt müssen Sie entweder einen neuen Datensatz erstellen oder einen vorhandenen Datensatz auswählen, in den die Daten der Google Analytics geladen werden sollen. Für diese Übung wurden bereits ein Datensatz und ein Schema erstellt. Sie müssen kein neues Schema oder neuen Datensatz erstellen.

Wählen Sie **Vorhandenen Datensatz** aus. Öffnen Sie das Dropdown-Menü, um einen Datensatz auszuwählen. Suchen Sie nach dem Datensatz namens `Demo System - Event Dataset for BigQuery (Global v1.1)` und wählen Sie ihn aus. Klicken Sie auf **Weiter**.

![demo](./images/xdm6.png)

Scrollen Sie nach unten. Jetzt müssen Sie jedes **Source-Feld** von Google Analytics/BigQuery einem XDM **Target-Feld** zuordnen, und zwar Feld für Feld.

![demo](./images/xdm8.png)

Verwenden Sie die folgende Zuordnungstabelle für diese Übung.

| Quellfeld | Zielfeld |
| ----------------- |-------------| 
| **_id** | _id |
| **_id** | -Kanal._id |
| timeStamp | Zeitstempel |
| GA_ID | ``--aepTenantId--``.identification.core.gaid |
| customerID | ``--aepTenantId--``.identification.core.loyaltyId |
| Seite | web.webPageDetails.name |
| Gerät | device.type |
| Browser | environment.browserDetails.vendor |
| MarketingChannel | marketing.trackingCode |
| TrafficSource | channel.typeAtSource |
| TrafficMedium | channel.mediaType |
| TransactionID | commerce.order.payments.transactionID |
| Ecommerce_Action_Type | eventType |
| Seitenansichten | web.webPageDetails.pageViews.value |
| Unique_Purchases | commerce.purchases.value |
| product_detail_views | commerce.productViews.value |
| Adds_To_Cart | commerce.productListAdds.value |
| product_removes_from_cart | commerce.productListRemovals.value |
| Product_Checkouts | commerce.checkouts.value |

Überprüfen Sie nach dem Kopieren und Einfügen der oben genannten Zuordnung in die Adobe Experience Platform-Benutzeroberfläche, ob keine Fehler aufgrund von Tippfehlern oder Leerzeichen am Anfang/Ende auftreten.

Sie verfügen nun über eine **Zuordnung** wie die folgende:

![demo](./images/xdm34.png)

Die Quellfelder **GA_ID** und **customerID** werden in diesem XDM-Schema einer Kennung zugeordnet. Auf diese Weise können Sie Google Analytics-Daten (Web-/App-Verhaltensdaten) mit anderen Datensätzen wie Loyalität oder Callcenter-Daten anreichern.

Klicken Sie auf **Weiter**.

![demo](./images/ex4/38.png)

## 4.2.4.3 Verbindung und Datenerfassungszeitplanung

Die Registerkarte **Planung** wird nun angezeigt:

![demo](./images/xdm38a.png)

Auf der Registerkarte **Planung** können Sie eine Häufigkeit für den Datenerfassungsprozess für diese **Zuordnung** und Daten definieren.

Da Sie Demodaten in Google BigQuery verwenden, die nicht aktualisiert werden, müssen Sie in dieser Übung keinen Zeitplan festlegen. Sie müssen jedoch eine Auswahl treffen und um zu viele unnötige Datenerfassungsprozesse zu vermeiden, müssen Sie die Häufigkeit wie folgt festlegen:

- Häufigkeit: **Woche**
- Intervall: **200**

![demo](./images/ex4/39.png)

**Wichtig**: Stellen Sie sicher, dass Sie den Schalter **Aufstockung** aktivieren.

![demo](./images/ex4/39a.png)

Nicht zuletzt müssen Sie ein **delta** -Feld definieren.

![demo](./images/ex4/36.png)

Das Feld **delta** wird verwendet, um die Verbindung zu planen und nur neue Zeilen in Ihren BigQuery-Datensatz hochzuladen. Ein Delta-Feld ist normalerweise immer eine Zeitstempelspalte. Für zukünftige geplante Datenerfassungen werden daher nur die Zeilen mit einem neuen, aktuelleren Zeitstempel erfasst.

Wählen Sie **timeStamp** als Deltafeld aus.

![demo](./images/ex4/37.png)

Das hast du jetzt.

![demo](./images/xdm37a.png)

Klicken Sie auf **Weiter**.

![demo](./images/ex4/42.png)

## 4.2.4.4 Verbindung überprüfen und starten

In der Ansicht **Datensatzflussdetails** . Sie müssen Ihre Verbindung benennen, was Ihnen hilft, sie später zu finden.

Bitte verwenden Sie diese Namenskonvention:

| Feld | Benennung | Beispiel |
| ----------------- |-------------| -------------|
| Name des Datensatz-Flusses | DataFlow - ldap - BigQuery Website Interaction | DataFlow - vangeluw - BigQuery Website Interaction |
| Beschreibung | DataFlow - ldap - BigQuery Website Interaction | DataFlow - vangeluw - BigQuery Website Interaction |

![demo](./images/xdm44.png)

Klicken Sie auf **Weiter**.

![demo](./images/ex4/45.png)

Jetzt wird eine detaillierte Übersicht über Ihre Verbindung angezeigt. Stellen Sie sicher, dass alles korrekt ist, bevor Sie fortfahren, da einige Einstellungen danach nicht mehr geändert werden können, z. B. die XDM-Zuordnung.

![demo](./images/xdm46.png)

Klicken Sie auf **Fertigstellen**.

![demo](./images/ex4/finish.png)

Das Einrichten der Verbindung kann einige Zeit dauern. Daher sollten Sie sich keine Gedanken machen, wenn dies angezeigt wird:

![demo](./images/ex4/47.png)

Nachdem die Verbindung erstellt wurde, sehen Sie Folgendes:

![demo](./images/xdm48.png)

Sie können jetzt mit der nächsten Übung fortfahren, in der Sie mit Customer Journey Analytics mächtige Visualisierungen auf Google Analytics-Daten aufbauen.

Nächster Schritt: [4.2.5 Google Analytics-Daten mithilfe von Customer Journey Analytics analysieren](./ex5.md)

[Zurück zu Modul 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
