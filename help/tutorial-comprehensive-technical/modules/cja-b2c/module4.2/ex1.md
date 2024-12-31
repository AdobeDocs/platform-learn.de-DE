---
title: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Erstellen Sie Ihr Google Cloud Platform-Konto
description: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Erstellen Sie Ihr Google Cloud Platform-Konto
kt: 5342
doc-type: tutorial
exl-id: 6dbfb5a3-adc2-4818-8f79-bbb00e56fbdf
source-git-commit: 348554b5a2d43d7a882e8259b39a57af13d41ff4
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 1%

---

# 4.2.1 Erstellen eines Google Cloud Platform-Kontos

## Ziele

- Erstellen Ihres Google Cloud Platform-Kontos
- Machen Sie sich mit der Google Cloud Platform-Konsole vertraut
- Erstellen und Vorbereiten des BigQuery-Projekts

## 4.2.1.1 Warum Google BigQuery mit Adobe Experience Platform verbinden, um Google Analytics-Daten zu erhalten

Google Cloud Platform (GCP) ist eine Suite öffentlicher Cloud-Computing-Services, die von Google angeboten wird. Die Google Cloud-Plattform umfasst eine Reihe gehosteter Services für die Rechen-, Speicher- und Anwendungsentwicklung, die auf Google-Hardware ausgeführt werden.

BigQuery ist einer dieser Services und ist immer in Google Analytics 360 enthalten. Google Analytics-Daten werden häufig aufgenommen, wenn wir versuchen, Daten direkt daraus abzurufen (z. B. API). Deshalb enthält Google BigQuery, um nicht abgetastete Daten zu erhalten, sodass Marken erweiterte Analysen mithilfe von SQL durchführen und von der Leistungsfähigkeit von GCP profitieren können.

Google Analytics-Daten werden täglich über einen Batch-Mechanismus in BigQuery geladen. Daher ist es nicht sinnvoll, diese GCP/BigQuery-Integration für Anwendungsfälle der Echtzeit-Personalisierung und -Aktivierung zu verwenden.

Wenn eine Marke Anwendungsfälle für die Personalisierung in Echtzeit bereitstellen möchte, die auf Daten von Google Analytics basieren, kann sie diese Daten auf der Website mit Google Tag Manager erfassen und dann in Echtzeit an Adobe Experience Platform streamen.

Der GCP/BigQuery Source Connector sollte verwendet werden, um…

- Verfolgen Sie das gesamte Kundenverhalten auf der Website und laden Sie diese Daten in Adobe Experience Platform für Anwendungsfälle für Analyse, Datenwissenschaft und Personalisierung, die keine Echtzeit-Aktivierung erfordern.
- Laden Sie historische Google Analytics-Daten in Adobe Experience Platform, ebenfalls für Anwendungsfälle zur Analyse und Datenwissenschaft

## 4.2.1.2 Google-Konto erstellen

Um ein Google Cloud Platform-Konto zu erhalten, benötigen Sie ein Google-Konto.

## 4.2.1.3 Aktivieren Ihres Google Cloud Platform-Kontos

Nachdem Sie nun über Ihr Google-Konto verfügen, können Sie eine Google Cloud Platform-Umgebung erstellen. Navigieren Sie dazu zu [https://console.cloud.google.com/](https://console.cloud.google.com/).

Akzeptieren Sie auf der nächsten Seite die Nutzungsbedingungen.

![demo](./images/ex1/1.png)

Klicken Sie anschließend auf **Projekt auswählen**.

![demo](./images/ex1/2.png)

Klicken Sie auf **NEUES PROJEKT**.

![demo](./images/ex1/createproject.png)

Benennen Sie Ihr Projekt nach dieser Namenskonvention:

| Konvention | Beispiel |
| ----------------- |-------------| 
| `--aepUserLdap---googlecloud` | delaigle-googlecloud |

![demo](./images/ex1/3.png)

Klicken Sie auf **Erstellen**.

![demo](./images/ex1/3-1.png)

Warten Sie, bis die Benachrichtigung oben rechts im Bildschirm anzeigt, dass die Erstellung abgeschlossen ist. Klicken Sie dann auf **Projekt anzeigen**.

![demo](./images/ex1/4.png)

Navigieren Sie dann oben im Bildschirm zur Suchleiste und geben Sie „BigQuery **ein**. Das erste Ergebnis auswählen.

![demo](./images/ex1/7.png)

Sie werden dann zur BigQuery-Konsole weitergeleitet und Sie sehen eine Popup-Meldung.

**Klicken Sie auf Fertig**.

![demo](./images/ex1/5.png)

Ziel dieses Moduls ist es, Daten von Google Analytics in Adobe Experience Platform zu übertragen. Dazu benötigen wir zunächst Platzhalterdaten in einem Google Analytics-Datensatz.

Klicken Sie **linken Menü auf** Daten hinzufügen“, gefolgt von einem Klick auf **Öffentliche Datensätze erkunden**.

![demo](./images/ex1/18.png)

Daraufhin wird dieses Fenster angezeigt:

![demo](./images/ex1/19.png)

Geben Sie in der Suchleiste den Suchbegriff **Google Analytics** Beispiel“ ein und wählen Sie das erste Ergebnis aus.

![demo](./images/ex1/20.png)

Daraufhin wird der folgende Bildschirm mit einer Beschreibung des Datensatzes angezeigt. Klicken Sie auf **DATENSATZ ANZEIGEN**.

![demo](./images/ex1/21.png)

Sie werden dann zu BigQuery weitergeleitet, wo Sie diesen Datensatz **bigquery-public-data** unter **Explorer** sehen.

![demo](./images/ex1/22a.png)

In **Explorer** sollten jetzt mehrere Tabellen angezeigt werden. Erkunden Sie sie einfach. Gehe zu `google_analytics_sample`.

![demo](./images/ex1/22.png)

Klicken, um die `ga_sessions` zu öffnen.

![demo](./images/ex1/23.png)

Bevor Sie mit der nächsten Übung fortfahren, notieren Sie sich folgende Dinge in einer separaten Textdatei auf Ihrem Computer:

| Anmeldedaten | Benennung | Beispiel |
| ----------------- |-------------| -------------|
| Projektname | `--aepUserLdap---googlecloud` | vangeluw-googlecloud |
| Projekt-ID | random | compose-task-306413 |

Sie können Ihren Projektnamen und Ihre Projekt-ID finden, indem Sie auf **Projektname** in der oberen Menüleiste klicken:

![demo](./images/ex1/projectMenu.png)

Auf der rechten Seite sehen Sie dann Ihre Projekt-ID:

![demo](./images/ex1/projetcselection.png)

Sie können jetzt zu Übung 12.2 wechseln, in der Sie sich die Hände schmutzig machen, indem Sie Daten von Google Analytics abfragen.

Nächster Schritt: [4.2.2 Erstellen Sie Ihre erste Abfrage in BigQuery](./ex2.md)

[Zurück zum Modul 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Zurück zu „Alle Module“](./../../../overview.md)
