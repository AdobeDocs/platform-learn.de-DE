---
title: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Erstellen eines Google Cloud Platform-Kontos
description: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Erstellen eines Google Cloud Platform-Kontos
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 1%

---

# 4.2.1 Google Cloud Platform-Konto erstellen

## Ziele

- Erstellen Ihres Google Cloud Platform-Kontos
- Kennenlernen von Google Cloud Platform Console
- Erstellen und Vorbereiten Ihres BigQuery-Projekts

## 4.2.1.1 Warum Google BigQuery mit Adobe Experience Platform verbinden, um Google Analytics-Daten zu erhalten

Google Cloud Platform (GCP) ist eine Suite öffentlicher Cloud-Computing-Dienste, die von Google angeboten werden. Die Google Cloud-Plattform umfasst eine Reihe gehosteter Dienste für die Computer-, Speicher- und Anwendungsentwicklung, die auf Google-Hardware ausgeführt werden.

BigQuery ist einer dieser Dienste und wird immer in Google Analytics 360 integriert. Google Analytics-Daten werden häufig gesampelt, wenn wir versuchen, Daten direkt daraus zu erhalten (z. B. API). Daher beinhaltet Google BigQuery, um nicht gesampelte Daten zu erhalten, sodass Marken erweiterte Analysen mit SQL durchführen und von der Leistungsfähigkeit von GCP profitieren können.

Google Analytics-Daten werden täglich mit einem Batch-Mechanismus in BigQuery geladen. Daher ist es nicht sinnvoll, diese GCP/BigQuery-Integration für die Echtzeit-Personalisierung und -Aktivierung zu verwenden.

Wenn eine Marke auf Grundlage von Google Analytics-Daten Echtzeit-Personalisierungsanwendungsfälle bereitstellen möchte, kann sie diese Daten auf der Website mit Google Tag Manager erfassen und dann in Echtzeit an Adobe Experience Platform streamen.

Der GCP/BigQuery Source Connector sollte für ...

- verfolgen Sie das gesamte Kundenverhalten auf der Website und laden Sie diese Daten zur Analyse, Datenwissenschaft und Personalisierung in Adobe Experience Platform, für die keine Echtzeit-Aktivierung erforderlich ist.
- Laden Sie Google Analytics historische Daten in Adobe Experience Platform, erneut für Analysen und Anwendungsfälle in der Datenwissenschaft.

## 4.2.1.2 Google-Konto erstellen

Um ein Google Cloud Platform-Konto zu erhalten, benötigen Sie ein Google-Konto.

## 4.2.1.3 Google Cloud Platform-Konto aktivieren

Nachdem Sie über Ihr Google-Konto verfügen, können Sie eine Google Cloud Platform-Umgebung erstellen. Gehen Sie dazu zu [https://console.cloud.google.com/](https://console.cloud.google.com/).

Akzeptieren Sie auf der nächsten Seite die Geschäftsbedingungen.

![demo](./images/ex1/1.png)

Klicken Sie anschließend auf **Projekt auswählen**.

![demo](./images/ex1/2.png)

Klicken Sie auf **NEUES PROJEKT**.

![demo](./images/ex1/createproject.png)

Benennen Sie Ihr Projekt nach dieser Benennungsregel:

| Übereinkommen | Beispiel |
| ----------------- |-------------| 
| `--demoProfileLdap---googlecloud` | delaigle-googlecloud |

![demo](./images/ex1/3.png)

Klicken Sie auf **Erstellen**.

![demo](./images/ex1/3-1.png)

Warten Sie, bis die Benachrichtigung oben rechts im Bildschirm angezeigt wird, dass die Erstellung abgeschlossen ist. Klicken Sie dann auf **Projekt anzeigen**.

![demo](./images/ex1/4.png)

Navigieren Sie dann zur Suchleiste am oberen Bildschirmrand und geben Sie **BigQuery** ein. Wählen Sie das erste Ergebnis aus.

![demo](./images/ex1/7.png)

Sie werden dann zur BigQuery-Konsole weitergeleitet und Sie werden eine Popup-Meldung sehen.

**Klicken Sie auf Fertig**.

![demo](./images/ex1/5.png)

Ziel dieses Moduls ist es, Google Analytics-Daten in Adobe Experience Platform zu übertragen. Dazu benötigen wir Platzhalterdaten in einem Datensatz der Google Analytics.

Klicken Sie im linken Seitenmenü auf **Daten hinzufügen** und anschließend auf **Öffentliche Datensätze durchsuchen**.

![demo](./images/ex1/18.png)

Dann sehen Sie dieses Fenster:

![demo](./images/ex1/19.png)

Geben Sie den Suchbegriff **Google Analytics-Beispiel** in die Suchleiste ein und wählen Sie das erste Ergebnis aus.

![demo](./images/ex1/20.png)

Der folgende Bildschirm mit einer Beschreibung des Datensatzes wird angezeigt. Klicken Sie auf **DATENSATZ ANZEIGEN**.

![demo](./images/ex1/21.png)

Sie werden dann zu BigQuery weitergeleitet, wo dieser **bigquery-public-data** -Datensatz unter **Explorer** angezeigt wird.

![demo](./images/ex1/22a.png)

In **Explorer** sollte jetzt eine Reihe von Tabellen angezeigt werden. Entdecken Sie sie gerne. Wechseln Sie zu &quot;`google_analytics_sample`&quot;.

![demo](./images/ex1/22.png)

Klicken Sie auf , um die Tabelle `ga_sessions` zu öffnen.

![demo](./images/ex1/23.png)

Bevor Sie mit der nächsten Übung fortfahren, schreiben Sie bitte die folgenden Dinge in eine separate Textdatei auf Ihrem Computer:

| Anmeldedaten | Benennung | Beispiel |
| ----------------- |-------------| -------------|
| Projektname | `--demoProfileLdap---googlecloud` | vangeluw-googlecloud |
| Projekt-ID | random | created-task-306413 |

Sie finden Ihren Projektnamen und Ihre Projekt-ID, indem Sie in der oberen Menüleiste auf Ihren **Projektnamen** klicken:

![demo](./images/ex1/projectMenu.png)

Anschließend sehen Sie Ihre Projekt-ID auf der rechten Seite:

![demo](./images/ex1/projetcselection.png)

Sie können jetzt zu Übung 12.2 wechseln, wo Sie Ihre Hände schmutzig machen, indem Sie Google Analytics-Daten abfragen.

Nächster Schritt: [4.2.2 Erstellen Sie Ihre erste Abfrage in BigQuery](./ex2.md)

[Zurück zu Modul 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
