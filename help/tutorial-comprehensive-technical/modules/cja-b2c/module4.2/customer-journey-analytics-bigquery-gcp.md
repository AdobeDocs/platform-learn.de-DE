---
title: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector
description: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector
kt: 5342
doc-type: tutorial
source-git-commit: f19f6b4a44a34af3c9545eb7f8735ef6ccf5d6c7
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 4.2 Daten aus Google Analytics in Adobe Experience Platform mit BigQuery Source Connector erfassen und analysieren

**Autoren: [Victor de la Iglesia](https://www.linkedin.com/in/victordelaiglesia/), [Wouter van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul richten Sie Ihre eigene Instanz von Google Cloud Platform ein, laden Beispieldaten in Google Cloud Platform und verwenden dann den BigQuery Source Connector, um diese Daten von Google Cloud Platform in Adobe Experience Platform aufzunehmen. Schließlich verwenden Sie Customer Journey Analytics, um diese Daten zu visualisieren.

Source-Connectoren in Adobe Experience Platform erleichtern die Datenübernahme in Adobe Experience Platform. Google BigQuery ist einer der bereits verfügbaren Connectoren. Dank Adobe Experience Platform und dem BigQuery Source Connector können wir jetzt Google Analytics-Daten in Analysis Workspace in Customer Journey Analytics importieren.

Darüber hinaus können wir diese Daten von Google Analytics anreichern, indem wir sie mit anderen Datenquellen wie CRM-, Callcenter- oder Loyalitätsdaten innerhalb von Customer Journey Analytics verbinden.

## Lernziele

- Kennenlernen der Google Cloud-Plattform und der BigQuery-Benutzeroberfläche
- Daten aus Google Analytics in Adobe Experience Platform erfassen
- Customer Journey Analytics zur Analyse von Google Analytics-Daten verwenden
- Anreicherung von Google Analytics-Daten mit Offline-Daten

## Voraussetzungen

- Eine gewisse Vertrautheit mit Customer Journey Analytics wird empfohlen, ist jedoch nicht erforderlich
- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf Customer Journey Analytics
- Zugriff auf Google Cloud Platform und Google BigQuery
- **Laden Sie diese Assets herunter**:
   - [JSON - Beispieldaten: Loyalitätsdaten](./../../../assets/json/bqLoyalty.json)

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [0.1 - Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben.

## Übungen

[4.2.1 Google Cloud Platform-Konto erstellen](./ex1.md)

Erstellen Sie Ihr Google Cloud Platform-Konto.

[4.2.2 Erste Abfrage in BigQuery erstellen](./ex2.md)

Erfahren Sie, wie Sie BigQuery verwenden, um die Daten für das Laden in Platform vorzubereiten.

[4.2.3 GCP und BigQuery mit Adobe Experience Platform verbinden](./ex3.md)

Erfahren Sie, wie Sie den Quell-Connector in Adobe Experience Platform einrichten.

[4.2.4 Daten aus BigQuery in Adobe Experience Platform laden](./ex4.md)

Erfahren Sie, wie Sie den Quell-Connector BigQuery in Adobe Experience Platform für die Aufnahme Ihrer Google Analytics-Daten konfigurieren.

[4.2.5 Google Analytics-Daten mithilfe von Customer Journey Analytics analysieren](./ex5.md)

Erfahren Sie, wie Sie Google Analytics-Daten in Customer Journey Analytics analysieren und mit Loyalitätsdaten kombinieren können.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investieren, um alles über Adobe Experience Platform und seine Anwendungen zu erfahren. Wenn Sie Fragen haben, möchten Sie allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com** senden.

[Zu allen Modulen zurückkehren](../../../overview.md)
