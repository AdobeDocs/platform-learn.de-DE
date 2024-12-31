---
title: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Laden von Daten aus BigQuery in Adobe Experience Platform
description: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Laden von Daten aus BigQuery in Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 793b35c6-761f-4b0a-b0bc-3eab93c82162
source-git-commit: 348554b5a2d43d7a882e8259b39a57af13d41ff4
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 4%

---

# 4.2.4 Laden von Daten aus BigQuery in Adobe Experience Platform

## Ziele

- BigQuery-Daten einem XDM-Schema zuordnen
- BigQuery-Daten in Adobe Experience Platform laden
- Machen Sie sich mit der Benutzeroberfläche des BigQuery Source-Connectors vertraut

## Bevor Sie beginnen

Nach Übung 12.3 sollte diese Seite in Adobe Experience Platform geöffnet sein:

![demo](./images/datasets.png)

**Wenn Sie es geöffnet haben, setzen Sie die Übung 12.4.1 fort.**

**Wenn es nicht geöffnet ist, navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform/home).**

Navigieren Sie im linken Menü zu Quellen . Anschließend wird die Homepage **Quellen** angezeigt. Klicken Sie **Menü** Quellen“ auf **Datenbanken**.

![demo](./images/sourceshome.png)

Wählen Sie den **Google BigQuery** Source Connector aus und klicken Sie auf **+ Konfigurieren**.

![demo](./images/bq.png)

Daraufhin wird der Auswahlbildschirm für das Google BigQuery-Konto angezeigt.

![demo](./images/0-c.png)

Wählen Sie Ihr Konto aus und klicken Sie auf **Weiter**.

![demo](./images/ex4/0-d.png)

Anschließend wird die Ansicht **Daten hinzufügen** angezeigt.

![demo](./images/datasets.png)

## 4.2.4.1 BigQuery-Tabellenauswahl

Wählen Sie in **Ansicht** Daten hinzufügen“ Ihren BigQuery-Datensatz aus.

![demo](./images/datasets.png)

Sie können jetzt eine Beispieldatenvorschau der Google Analytics-Daten in BigQuery sehen.

Klicken Sie auf **Weiter**.

![demo](./images/ex4/3.png)

## XDM-Zuordnung 4.2.4.2

Sie sehen dies jetzt:

![demo](./images/xdm4a.png)

Jetzt müssen Sie entweder einen neuen Datensatz erstellen oder einen vorhandenen Datensatz auswählen, in den die Google Analytics-Daten geladen werden. Für diese Übung wurden bereits ein Datensatz und ein Schema erstellt. Sie müssen kein neues Schema oder keinen neuen Datensatz erstellen.

Wählen Sie **Vorhandener Datensatz** aus. Öffnen Sie das Dropdown-Menü, um einen Datensatz auszuwählen. Suchen Sie nach dem Datensatz mit dem Namen `Demo System - Event Dataset for BigQuery (Global v1.1)` und wählen Sie ihn aus. Klicken Sie auf **Weiter**.

![demo](./images/xdm6.png)

Scroll down. Jetzt müssen Sie jedes **Source-Feld** von Google Analytics/BigQuery einem XDM-**Target-Feld** Feld für Feld zuordnen.

![demo](./images/xdm8.png)

Verwenden Sie die folgende Zuordnungstabelle für diese Übung.

| Quellfeld | Zielfeld |
| ----------------- |-------------| 
| **_id** | _id |
| **_id** | Kanal._id |
| Zeitstempel | Zeitstempel |
| GA_ID | ``--aepTenantId--``.identification.core.gaid |
| customerID | ``--aepTenantId--``.identification.core.loyaltyId |
| Seite | web.webPageDetails.name |
| Gerät | device.type |
| Browser | environment.browserDetails.vendor |
| Marketing-Kanal | marketing.trackingCode |
| Traffic-Herkunft | channel.typeAtSource |
| Verkehrsmittel | channel.mediaType |
| TransactionID | commerce.order.payments.transactionID |
| ecommerce_action_type | eventType |
| Seitenansichten | web.webPageDetails.pageViews.value |
| Unique_Purchases | commerce.purchases.value |
| product_detail_views | commerce.productViews.value |
| ADDS_TO_CART | commerce.productListAdds.value |
| product_removes_from_cart | commerce.productListRemovals.value |
| product_checkouts | commerce.checkouts.value |

Nachdem Sie die obige Zuordnung kopiert und in die Adobe Experience Platform-Benutzeroberfläche eingefügt haben, überprüfen Sie, ob Fehler aufgrund von Tippfehlern oder führenden/nachfolgenden Leerzeichen angezeigt werden.

Sie haben jetzt eine **Zuordnung** wie diese:

![demo](./images/xdm34.png)

Die Quellfelder **GA_ID** und **customerID** werden einer Kennung in diesem XDM-Schema zugeordnet. Auf diese Weise können Sie Google Analytics-Daten (Web-/App-Verhaltensdaten) mit anderen Datensätzen wie Treue- oder Callcenter-Daten anreichern.

Klicken Sie auf **Weiter**.

![demo](./images/ex4/38.png)

## 4.2.4.3 der Verbindung und Planung der Datenaufnahme

Daraufhin wird die Registerkarte **Planung** angezeigt:

![demo](./images/xdm38a.png)

Auf der Registerkarte **Planung** können Sie eine Häufigkeit für den Datenaufnahmeprozess für diese (**)** Daten definieren.

Da Sie Demodaten in Google BigQuery verwenden, die nicht aktualisiert werden, besteht keine echte Notwendigkeit, in dieser Übung einen Zeitplan festzulegen. Sie müssen etwas auswählen, und um zu viele unnötige Datenaufnahmen zu vermeiden, müssen Sie die Häufigkeit wie folgt festlegen:

- Häufigkeit: **Woche**
- Intervall: **200**

![demo](./images/ex4/39.png)

**Wichtig**: Stellen Sie sicher, dass Sie den Umschalter **Aufstockung** aktivieren.

![demo](./images/ex4/39a.png)

Zu guter Letzt müssen Sie ein Feld **delta** definieren.

![demo](./images/ex4/36.png)

Das **delta**-Feld wird verwendet, um die Verbindung zu planen und nur neue Zeilen hochzuladen, die in Ihren BigQuery-Datensatz gelangen. Ein Delta-Feld ist normalerweise immer eine Zeitstempelspalte. Für zukünftige geplante Datenerfassungen werden also nur die Zeilen mit einem neuen, neueren Zeitstempel aufgenommen.

Wählen Sie **timeStamp** als Delta-Feld aus.

![demo](./images/ex4/37.png)

Jetzt hast du das.

![demo](./images/xdm37a.png)

Klicken Sie auf **Weiter**.

![demo](./images/ex4/42.png)

## Verbindung 4.2.4.4 und starten

In der **Datensatzflussdetails** Ansicht. Sie müssen Ihre Verbindung benennen, damit Sie sie später finden können.

Bitte diese Namenskonvention verwenden:

| Feld | Benennung | Beispiel |
| ----------------- |-------------| -------------|
| Name des Datensatz-Flusses | DataFlow - LDAP - BigQuery Website Interaction | Datenfluss - vangeluw - BigQuery Website Interaction |
| Beschreibung | DataFlow - LDAP - BigQuery Website Interaction | Datenfluss - vangeluw - BigQuery Website Interaction |

![demo](./images/xdm44.png)

Klicken Sie auf **Weiter**.

![demo](./images/ex4/45.png)

Jetzt sehen Sie einen detaillierten Überblick über Ihre Verbindung. Stellen Sie sicher, dass alles korrekt ist, bevor Sie fortfahren, da einige Einstellungen anschließend nicht mehr geändert werden können, z. B. die XDM-Zuordnung.

![demo](./images/xdm46.png)

Klicken Sie auf **Fertigstellen**.

![demo](./images/ex4/finish.png)

Die Einrichtung der Verbindung kann einige Zeit in Anspruch nehmen. Seien Sie also unbesorgt, wenn Sie dies sehen:

![demo](./images/ex4/47.png)

Nachdem die Verbindung erstellt wurde, wird Folgendes angezeigt:

![demo](./images/xdm48.png)

Sie können jetzt mit der nächsten Übung fortfahren, in der Sie Customer Journey Analytics verwenden werden, um leistungsstarke Visualisierungen auf den Daten von Google Analytics zu erstellen.

Nächster Schritt: [4.2.5 Analysieren von Google Analytics-Daten mit Customer Journey Analytics](./ex5.md)

[Zurück zum Modul 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Zurück zu „Alle Module“](./../../../overview.md)
