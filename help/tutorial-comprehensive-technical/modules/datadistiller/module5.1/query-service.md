---
title: Abfrage-Service
description: Abfrage-Service
kt: 5342
doc-type: tutorial
exl-id: 6eb65de3-d0e8-49d4-a702-5c9d6a1952b7
source-git-commit: bd46be455f88007174f7e6be9a1ce5f508edc09b
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 1%

---

# 5.1 Abfrage-Service

In diesem Modul erhalten Sie eine praktische Vorschau des Abfrage-Service von Adobe Experience Platform. Mit Query Service können Sie Omni-Channel-Abfragen für alle Daten der Adobe Experience Cloud-Anwendung durchführen, Daten aus Adobe Campaign, Analytics, Audience Manager, Target und Advertising Cloud verbinden und analysieren und weitere Kundendaten in Adobe Experience Platform laden/einfügen.

Query Service ist ein Server-loses Tool. Es unterstützt SQL-Abfragen und Konnektivität von mehreren Client-Anwendungen durch seine PostgreSQL-Kompatibilität.
Wir verwenden Daten, die entweder mithilfe von Web Interaction-Daten oder mithilfe von Callcenter-Interaktionen in Kombination mit in Platform hochgeladenen Kundenloyalitätsdaten in Platform eingespeist wurden.

## Lernziele

- Machen Sie sich mit der Benutzeroberfläche von Adobe Experience Platform vertraut
- Verbinden mit dem Abfrage-Service und Ausführen von SQL-Abfragen
- Erkunden von Datensätzen in Adobe Experience Platform
- Verbinden von Tableau oder Power BI mit dem Adobe Experience Platform Query Service, um Visualisierungen und Berichte zu erstellen

## Voraussetzungen

- Eine gewisse Vertrautheit mit SQL wird bevorzugt, ist aber nicht erforderlich
- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Datensätze (im Labor verwendeter Datensatz, für Sie vorgeladen)
- PostgreSQL
- Tableau oder Microsoft Power BI Desktop
- **Diese Assets herunterladen**:
   - [JSON - Beispieldaten: Website-Interaktionen](./../../../assets/json/ee.json)
   - [JSON - Beispieldaten: Interaktionen mit Callcentern](./../../../assets/json/callcenter.json)
   - [JSON - Beispieldaten: Treue](./../../../assets/json/loyalty.json)

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben

## Übungen

[5.1.1 Voraussetzungen](./ex1.md)

Sie müssen PSQL installieren, um die Abfragen in dieser Aktivierungsübung auszuführen. Abhängig von Ihrem Betriebssystem müssen Sie Microsoft Power BI oder Tableau installieren. Windows-Anwender können zwischen Power BI oder Tableau wählen. Mac-Benutzer sollten Tableau installieren.

[5.1.2 Erste Schritte](./ex2.md)

In dieser Übung erfahren Sie mehr über die Benutzeroberfläche des Adobe Experience Platform-Abfrage-Service, lernen Datensätze kennen, finden Ihre Abfragen und richten schließlich eine Verbindung über PSQL ein.

[5.1.3 Verwenden des Abfrage-Service](./ex3.md)

In dieser Übung lernen Sie die grundlegende Syntax des Abfrage-Service kennen und können die Attribute des XDM-Schemas in Ihrer Abfrage identifizieren.

[5.1.4 Abfragen, Abfragen… und Abwanderungsanalyse](./ex4.md)

In dieser Übung werden Sie Abfragen durchführen, um mehr über die Adobe-definierten Funktionen zu erfahren, während Sie eine Abwanderungsanalyse durchführen. Am Ende dieses Vorgangs schreiben Sie eine Abfrage, um einen Datensatz für die Verwendung im Microsoft-Power BI vorzubereiten.

[5.1.5 Generieren eines Datensatzes aus einer Abfrage](./ex5.md)

In dieser Übung generieren Sie einen Datensatz aus einer in der vorherigen Übung ausgeführten Abfrage und verwenden diesen Datensatz in den nächsten Übungen.

[5.1.6 Abfrage-Service und Power BI](./ex6.md)

In dieser Übung verbinden Sie Power BI mit Adobe Experience Platform und Query Service, um eine Callcenter-Interaktionsanalyse durchzuführen.

[5.1.7 Query Service und Tableau](./ex7.md)

In dieser Übung verbinden Sie Tableau mit Adobe Experience Platform und Query Service, um eine Callcenter-Interaktionsanalyse durchzuführen.

[5.1.8 Abfrage-Service-API](./ex8.md)

In dieser Übung verwenden Sie die Abfrage-Service-API, um Abfragevorlagen und Abfragezeitpläne zu verwalten.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Überblick über die Vorteile.

![Tech Insiders](./../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um alles über Adobe Experience Platform und seine Programme zu erfahren. Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.

[Zurück zu „Alle Module“](../../../overview.md)
