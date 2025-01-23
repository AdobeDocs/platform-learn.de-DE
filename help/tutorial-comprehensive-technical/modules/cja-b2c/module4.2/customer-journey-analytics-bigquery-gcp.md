---
title: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector
description: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector
kt: 5342
doc-type: tutorial
exl-id: b078d003-da25-44c5-b000-77e3b3188fb6
source-git-commit: bd46be455f88007174f7e6be9a1ce5f508edc09b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# 4.2 Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector

In diesem Modul richten Sie Ihre eigene Instanz von Google Cloud Platform ein, laden Beispieldaten in Google Cloud Platform und verwenden dann den BigQuery Source Connector , um diese Daten von Google Cloud Platform in Adobe Experience Platform aufzunehmen. Zum Schluss verwenden Sie Customer Journey Analytics zur Visualisierung dieser Daten.

Source-Connectoren in Adobe Experience Platform erleichtern den Prozess der Datenübernahme in Adobe Experience Platform. Google BigQuery ist einer der bereits verfügbaren Connectoren. Dank Adobe Experience Platform und dem BigQuery Source Connector können wir jetzt Google Analytics-Daten in Customer Journey Analytics in Analysis Workspace einbringen.

Darüber hinaus können wir diese Google Analytics-Daten anreichern, indem wir sie mit anderen Datenquellen wie CRM, Callcenter oder Treuedaten innerhalb von Customer Journey Analytics verbinden.

## Lernziele

- Machen Sie sich mit der Google Cloud-Plattform und der BigQuery-Benutzeroberfläche vertraut
- Aufnehmen von Google Analytics-Daten in Adobe Experience Platform
- Customer Journey Analytics zur Analyse der Google Analytics-Daten verwenden
- Anreicherung von Google Analytics-Daten mit Offline-Daten

## Voraussetzungen

- Eine gewisse Vertrautheit mit Customer Journey Analytics ist vorzuziehen, aber nicht erforderlich
- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf Customer Journey Analytics
- Zugriff auf Google Cloud Platform und Google BigQuery
- **Diese Assets herunterladen**:
   - [JSON - Beispieldaten: Treueprogramm-Daten](./../../../assets/json/bqLoyalty.json)

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben

## Übungen

[4.2.1 Verwenden der Google Cloud Platform](./ex1.md)

Beginnen Sie mit der Verwendung Ihrer Google Cloud Platform-Umgebung.

[4.2.2 Erstellen Sie Ihre erste Abfrage in BigQuery](./ex2.md)

Erfahren Sie, wie Sie mit BigQuery die Daten für das Laden in Platform vorbereiten.

[4.2.3 Verbinden von GCP und BigQuery mit Adobe Experience Platform](./ex3.md)

Erfahren Sie, wie Sie den Quell-Connector in Adobe Experience Platform einrichten.

[4.2.4 Laden von Daten aus BigQuery in Adobe Experience Platform](./ex4.md)

Erfahren Sie, wie Sie den BigQuery-Quell-Connector in Adobe Experience Platform konfigurieren, um Ihre Google Analytics-Daten aufzunehmen.

[4.2.5 Analysieren von Google Analytics-Daten mit Customer Journey Analytics](./ex5.md)

Erfahren Sie, wie Sie Google Analytics-Daten in Customer Journey Analytics analysieren und mit Treuedaten kombinieren können.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Überblick über die Vorteile.

![Tech Insiders](./../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um alles über Adobe Experience Platform und seine Programme zu erfahren. Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.

[Zurück zu „Alle Module“](../../../overview.md)
