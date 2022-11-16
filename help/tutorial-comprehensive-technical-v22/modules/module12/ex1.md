---
title: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Erstellen Sie Ihr Google Cloud Platform-Konto
description: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Erstellen Sie Ihr Google Cloud Platform-Konto
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 632ff2fe-ae56-4481-b281-c11224b18639
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 2%

---

# 12.1 Google Cloud Platform-Konto erstellen

## Ziele

- Erstellen Ihres Google Cloud Platform-Kontos
- Kennenlernen von Google Cloud Platform Console
- Erstellen und Vorbereiten Ihres BigQuery-Projekts

## 12.1.1 Warum Google BigQuery mit Adobe Experience Platform verbinden, um Google Analytics-Daten zu erhalten

Google Cloud Platform (GCP) ist eine Suite öffentlicher Cloud-Computing-Dienste, die von Google angeboten werden. Die Google Cloud-Plattform umfasst eine Reihe gehosteter Dienste für die Computer-, Speicher- und Anwendungsentwicklung, die auf Google-Hardware ausgeführt werden.

BigQuery ist einer dieser Dienste und wird immer in Google Analytics 360 eingeschlossen. Google Analytics-Daten werden häufig gesampelt, wenn wir versuchen, Daten direkt daraus zu erhalten (z. B. API). Daher beinhaltet Google BigQuery, um nicht gesampelte Daten zu erhalten, sodass Marken erweiterte Analysen mit SQL durchführen und von der Leistungsfähigkeit von GCP profitieren können.

Google Analytics-Daten werden täglich mit einem Batch-Mechanismus in BigQuery geladen. Daher ist es nicht sinnvoll, diese GCP/BigQuery-Integration für die Echtzeit-Personalisierung und -Aktivierung zu verwenden.

Wenn eine Marke auf der Grundlage von Google Analytics-Daten Echtzeit-Personalisierungsanwendungsfälle bereitstellen möchte, kann sie diese Daten auf der Website mit Google Tag Manager erfassen und sie dann in Echtzeit an Adobe Experience Platform streamen.

Der GCP/BigQuery Source Connector sollte für ...

- verfolgen Sie das gesamte Kundenverhalten auf der Website und laden Sie diese Daten zur Analyse, Datenwissenschaft und Personalisierung in Adobe Experience Platform, für die keine Echtzeit-Aktivierung erforderlich ist.
- Laden von Google Analytics historische Daten in Adobe Experience Platform, erneut für Analysen und Anwendungsfälle in der Datenwissenschaft

## 12.1.2 Google-Konto erstellen

Um ein Google Cloud Platform-Konto zu erhalten, benötigen Sie ein Google-Konto.

## 12.1.3 Google Cloud Platform-Konto aktivieren

Nachdem Sie über Ihr Google-Konto verfügen, können Sie eine Google Cloud Platform-Umgebung erstellen. Gehen Sie dazu zu [https://console.cloud.google.com/](https://console.cloud.google.com/).

Akzeptieren Sie auf der nächsten Seite die Geschäftsbedingungen.

![Demo](./images/ex1/1.png)

Klicken Sie anschließend auf **Projekt auswählen**.

![Demo](./images/ex1/2.png)

Klicken Sie auf **NEUES PROJEKT**.

![Demo](./images/ex1/createproject.png)

Benennen Sie Ihr Projekt nach dieser Benennungsregel:

| Übereinkommen | Beispiel |
| ----------------- |-------------| 
| `--demoProfileLdap---googlecloud` | delaigle-googlecloud |

![Demo](./images/ex1/3.png)

Klicken Sie auf **Erstellen**.

![Demo](./images/ex1/3-1.png)

Warten Sie, bis die Benachrichtigung oben rechts im Bildschirm angezeigt wird, dass die Erstellung abgeschlossen ist. Klicken Sie dann auf **Projekt anzeigen**.

![Demo](./images/ex1/4.png)

Navigieren Sie dann zur Suchleiste am oberen Bildschirmrand und geben Sie **BigQuery**. Wählen Sie das erste Ergebnis aus.

![Demo](./images/ex1/7.png)

Sie werden dann zur BigQuery-Konsole weitergeleitet und Sie werden eine Popup-Meldung sehen.

**Klicken Sie auf Fertig**.

![Demo](./images/ex1/5.png)

Ziel dieses Moduls ist es, Google Analytics-Daten in Adobe Experience Platform zu übertragen. Dazu benötigen wir Platzhalterdaten in einem Google Analytics-Datensatz, damit wir beginnen können.

Klicken Sie auf **Daten hinzufügen** im Menü links, gefolgt von einem Klick auf **Öffentliche Datensätze durchsuchen**.

![Demo](./images/ex1/18.png)

Dann sehen Sie dieses Fenster:

![Demo](./images/ex1/19.png)

Suchbegriff eingeben **Google Analytics-Beispiel** in der Suchleiste und wählen Sie das erste Ergebnis aus.

![Demo](./images/ex1/20.png)

Der folgende Bildschirm mit einer Beschreibung des Datensatzes wird angezeigt. Klicken Sie auf **DATENSATZ ANZEIGEN**.

![Demo](./images/ex1/21.png)

Sie werden dann zu BigQuery weitergeleitet, wo Sie dies sehen werden **bigquery-public-data** Datensatz unter **Explorer**.

![Demo](./images/ex1/22a.png)

In **Explorer** angezeigt, sollten nun eine Reihe von Tabellen angezeigt werden. Entdecken Sie sie gerne. Öffnen von `google_analytics_sample`.

![Demo](./images/ex1/22.png)

Klicken, um die Tabelle zu öffnen `ga_sessions`.

![Demo](./images/ex1/23.png)

Bevor Sie mit der nächsten Übung fortfahren, schreiben Sie bitte die folgenden Dinge in eine separate Textdatei auf Ihrem Computer:

| Anmeldedaten | Namenskonvention | Beispiel |
| ----------------- |-------------| -------------|
| Projektname | `--demoProfileLdap---googlecloud` | vangeluw-googlecloud |
| Projekt-ID | random | created-task-306413 |

Sie können Ihren Projektnamen und Ihre Projekt-ID finden, indem Sie auf Ihre **Projektname** in der oberen Menüleiste:

![Demo](./images/ex1/projectMenu.png)

Anschließend sehen Sie Ihre Projekt-ID auf der rechten Seite:

![Demo](./images/ex1/projetcselection.png)

Sie können jetzt zu Übung 12.2 wechseln, wo Sie Ihre Hände schmutzig machen, indem Sie Google Analytics-Daten abfragen.

Nächster Schritt: [12.2 Erste Abfrage in BigQuery erstellen](./ex2.md)

[Zurück zu Modul 12](./customer-journey-analytics-bigquery-gcp.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
