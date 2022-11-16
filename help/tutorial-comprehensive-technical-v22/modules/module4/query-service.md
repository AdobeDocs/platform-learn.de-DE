---
title: Query Service
description: Query Service
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 74943e52-8a7e-4db7-9407-7deeab008fa7
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 2%

---

# 4. Query Service

**Autoren: [Marc Meewis](https://www.linkedin.com/in/marcmeewis/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul erhalten Sie eine praktische Vorschau von Adobe Experience Platform Query Service. Mit Query Service können Sie Omnichannel-Abfragen für alle Adobe Experience Cloud-Anwendungsdaten durchführen, Daten aus Adobe Campaign, Analytics, Audience Manager, Target und Advertising Cloud sowie anderen in Adobe Experience Platform geladenen/eingefügten Kundendaten verbinden und analysieren.

Query Service ist ein Server-loses Tool. Es unterstützt SQL-Abfragen und Konnektivität von mehreren Client-Anwendungen über seine PostgreSQL-Kompatibilität.
Wir werden Daten verwenden, die mithilfe von Web Interaction Data oder Callcenter-Interaktionen in Kombination mit Daten aus dem Kundenloyalitätsbereich in die Plattform hochgeladen wurden.

## Lernziele

- Kennenlernen der Adobe Experience Platform-Benutzeroberfläche
- Stellen Sie eine Verbindung zu Query Service her und führen Sie Ihre SQL-Abfragen aus.
- Datensätze in Adobe Experience Platform erkunden
- Verbinden von Tableau oder Power BI mit dem Adobe Experience Platform Query Service , um Visualisierungen und Berichte zu erstellen

## Voraussetzungen

- Es wird empfohlen, mit SQL vertraut zu sein, dies ist jedoch nicht erforderlich
- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Datensätze (im Labor verwendeter Datensatz, für Sie vorab geladen)
- PostgreSQL
- Tableau oder Microsoft Power BI Desktop
- **Herunterladen dieser Assets**:
   - [JSON - Beispieldaten: Website-Interaktionen](./../../assets/json/ee.json)
   - [JSON - Beispieldaten: Interaktionen im Callcenter](./../../assets/json/callcenter.json)
   - [JSON - Beispieldaten: Treue](./../../assets/json/loyalty.json)

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem7.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--module7sandbox--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[4.0 Voraussetzungen](./ex0.md)

Sie müssen PSQL installieren, um die Abfragen in dieser Aktivierungsübung auszuführen. Je nach Betriebssystem müssen Sie Microsoft Power BI oder Tableau installieren. Windows-Benutzer können zwischen Power BI oder Tableau wählen. Mac-Benutzer sollten Tableau installieren.

[4.1 Erste Schritte](./ex1.md)

In dieser Übung werden Sie die Benutzeroberfläche von Adobe Experience Platform Query Service erkunden, sich über Datensätze informieren, Abfragen finden und schließlich eine Verbindung von PSQL einrichten.

[4.2 Query Service verwenden](./ex2.md)

In dieser Übung erfahren Sie mehr über die grundlegende Query Service-Syntax und Sie können die Attribute des XDM-Schemas in Ihrer Abfrage identifizieren.

[4.3 Abfragen, Abfragen, Abfragen.. und Abwanderungsanalyse](./ex3.md)

In dieser Übung werden Sie Abfragen durchführen, während Sie eine Abwanderungsanalyse durchführen, um mehr über die Adobe Definierte Funktionen zu erfahren. Am Ende schreiben Sie eine Abfrage, um einen Datensatz für die Verwendung in Microsoft Power BI vorzubereiten.

[4.4 Datensatz aus einer Abfrage generieren](./ex4.md)

In dieser Übung generieren Sie einen Datensatz aus einer Abfrage, die in der vorherigen ausgeführt wurde, und verwenden diesen Datensatz in den nächsten Übungen.

[4.5 Query Service und Power BI](./ex5.md)

In dieser Übung verbinden Sie Power BI mit Adobe Experience Platform und Query Service, um Callcenter-Interaktionsanalysen durchzuführen.

[4.6 Query Service und Tableau](./ex6.md)

In dieser Übung verbinden Sie Tableau mit Adobe Experience Platform und Query Service, um Callcenter-Interaktionsanalysen durchzuführen.

[4.7 Query Service-API](./ex7.md)

In dieser Übung verwenden Sie die Query Service-API zum Verwalten von Abfragevorlagen und Abfrageplänen.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
