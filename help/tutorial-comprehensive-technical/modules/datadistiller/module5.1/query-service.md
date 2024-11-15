---
title: Abfrage-Service
description: Abfrage-Service
kt: 5342
doc-type: tutorial
exl-id: 6eb65de3-d0e8-49d4-a702-5c9d6a1952b7
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 1%

---

# 5.1 Query Service

**Autoren: [Marc Meewis](https://www.linkedin.com/in/marcmeewis/), [Wouter van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul erhalten Sie eine praktische Vorschau von Adobe Experience Platform Query Service. Mit Query Service können Sie Omnichannel-Abfragen für alle Adobe Experience Cloud-Anwendungsdaten durchführen, Daten aus Adobe Campaign, Analytics, Audience Manager, Target und Advertising Cloud sowie anderen in Adobe Experience Platform geladenen/eingefügten Kundendaten verbinden und analysieren.

Query Service ist ein Server-loses Tool. Es unterstützt SQL-Abfragen und Konnektivität von mehreren Client-Anwendungen über seine PostgreSQL-Kompatibilität.
Wir werden Daten verwenden, die mithilfe von Web Interaction Data oder Callcenter-Interaktionen in Kombination mit Daten aus dem Kundenloyalitätsbereich in die Plattform hochgeladen wurden.

## Lernziele

- Kennenlernen der Adobe Experience Platform-Benutzeroberfläche
- Verbindung zu Query Service herstellen und Ihre SQL-Abfragen ausführen
- Datensätze in Adobe Experience Platform erkunden
- Verbinden von Tableau oder Power BI mit dem Adobe Experience Platform Query Service , um Visualisierungen und Berichte zu erstellen

## Voraussetzungen

- Es wird empfohlen, mit SQL vertraut zu sein, dies ist jedoch nicht erforderlich.
- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Datensätze (im Labor verwendeter Datensatz, für Sie vorab geladen)
- PostgreSQL
- Tableau oder Microsoft Power BI Desktop
- **Laden Sie diese Assets herunter**:
   - [JSON - Beispieldaten: Website-Interaktionen](./../../../assets/json/ee.json)
   - [JSON - Beispieldaten: Interaktionen im Callcenter](./../../../assets/json/callcenter.json)
   - [JSON - Beispieldaten: Treueprogramm](./../../../assets/json/loyalty.json)

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben.

## Übungen

[5.1.0 Voraussetzungen](./ex0.md)

Sie müssen PSQL installieren, um die Abfragen in dieser Aktivierungsübung auszuführen. Je nach Betriebssystem müssen Sie Microsoft Power BI oder Tableau installieren. Windows-Benutzer können zwischen Power BI oder Tableau wählen. Mac-Benutzer sollten Tableau installieren.

[5.1.1 Erste Schritte](./ex1.md)

In dieser Übung werden Sie die Benutzeroberfläche von Adobe Experience Platform Query Service erkunden, sich über Datensätze informieren, Abfragen finden und schließlich eine Verbindung von PSQL einrichten.

[5.1.2 Query Service verwenden](./ex2.md)

In dieser Übung erfahren Sie mehr über die grundlegende Query Service-Syntax und Sie können die Attribute des XDM-Schemas in Ihrer Abfrage identifizieren.

[5.1.3 Abfragen, Abfragen, Abfragen ... und Abwanderungsanalyse](./ex3.md)

In dieser Übung werden Sie Abfragen durchführen, während Sie eine Abwanderungsanalyse durchführen, um mehr über die Adobe Defined Functions zu erfahren. Am Ende schreiben Sie eine Abfrage, um einen Datensatz für die Verwendung in Microsoft Power BI vorzubereiten.

[5.1.4 Datensatz aus einer Abfrage generieren](./ex4.md)

In dieser Übung generieren Sie einen Datensatz aus einer Abfrage, die in der vorherigen ausgeführt wurde, und verwenden diesen Datensatz in den nächsten Übungen.

[5.1.5 Query Service und Power BI](./ex5.md)

In dieser Übung verbinden Sie Power BI mit Adobe Experience Platform und Query Service, um Callcenter-Interaktionsanalysen durchzuführen.

[5.1.6 Query Service und Tableau](./ex6.md)

In dieser Übung verbinden Sie Tableau mit Adobe Experience Platform und Query Service, um Callcenter-Interaktionsanalysen durchzuführen.

[5.1.7 Query Service-API](./ex7.md)

In dieser Übung verwenden Sie die Query Service-API zum Verwalten von Abfragevorlagen und Abfrageplänen.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investieren, um alles über Adobe Experience Platform und seine Anwendungen zu erfahren. Wenn Sie Fragen haben, möchten Sie allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com** senden.

[Zu allen Modulen zurückkehren](../../../overview.md)
