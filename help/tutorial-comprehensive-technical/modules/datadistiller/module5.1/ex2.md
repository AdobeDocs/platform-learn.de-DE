---
title: Query Service - Verwendung des Query Service
description: Query Service - Verwendung des Query Service
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# 5.1.2 Query Service verwenden

## Ziel

- Suchen und Erkunden von Datensätzen
- Erfahren Sie, wie Sie in Ihren Abfragen Experience-Datenmodellobjekte und -attribute bearbeiten.

## Kontext

In diesem Abschnitt erfahren Sie, wie Sie mit PSQL Informationen zu den verfügbaren Datensätzen abrufen, wie Sie Abfragen für das Experience-Datenmodell (XDM) schreiben und Ihre ersten einfachen Berichtsabfragen mit den Datensätzen Query Service und Citi Signal schreiben können.

## 5.1.2.1 Grundlegende Abfragen

In diesem Abschnitt erfahren Sie mehr über die Methoden zum Abrufen von Informationen zu den verfügbaren Datensätzen und dazu, wie Daten mit einer Abfrage aus einem XDM-Datensatz ordnungsgemäß abgerufen werden.

Alle Datensätze, die wir Anfang 1 über Adobe Experience Platform erforscht haben, stehen auch als Tabellen über eine SQL-Schnittstelle zur Verfügung. Um diese Tabellen aufzulisten, können Sie den Befehl **Tabellen anzeigen;** verwenden.

Führen Sie **Tabellen anzeigen;** in Ihrer **PSQL-Befehlszeilenschnittstelle** aus. (Vergessen Sie nicht, Ihren Befehl mit einem Semikolon zu beenden).

Kopieren Sie den Befehl **show tables;** und fügen Sie ihn an der Eingabeaufforderung ein:

![command-quick-show-show-tables.png](./images/command-prompt-show-tables.png)

Das folgende Ergebnis wird angezeigt:

```text
aepenablementfy21:all=> show tables;
                            name                            |        dataSetId         |                            dataSet                             | description | resolved 
------------------------------------------------------------+--------------------------+----------------------------------------------------------------+-------------+----------
 demo_system_event_dataset_for_call_center_global_v1_1      | 5fd1a9dea30603194baeea43 | Demo System - Event Dataset for Call Center (Global v1.1)      |             | false
 demo_system_event_dataset_for_mobile_app_global_v1_1       | 5fd1a9de250e4f194bec84cd | Demo System - Event Dataset for Mobile App (Global v1.1)       |             | false
 demo_system_event_dataset_for_voice_assistants_global_v1_1 | 5fd1a9de49ee76194b85f73c | Demo System - Event Dataset for Voice Assistants (Global v1.1) |             | false
 demo_system_event_dataset_for_website_global_v1_1          | 5fd1a9dee3224d194cdfe786 | Demo System - Event Dataset for Website (Global v1.1)          |             | false
 demo_system_profile_dataset_for_loyalty_global_v1_1        | 5fd1a9de250e4f194bec84cc | Demo System - Profile Dataset for Loyalty (Global v1.1)        |             | false
 demo_system_profile_dataset_for_ml_predictions_global_v1_1 | 5fd1a9de241f58194b0cb117 | Demo System - Profile Dataset for ML Predictions (Global v1.1) |             | false
 demo_system_profile_dataset_for_mobile_app_global_v1_1     | 5fd1a9deddf353194a2e00b7 | Demo System - Profile Dataset for Mobile App (Global v1.1)     |             | false
 demo_system_profile_dataset_for_website_global_v1_1        | 5fd1a9de42a61c194dd7b810 | Demo System - Profile Dataset for Website (Global v1.1)        |             | false
 journey_step_events                                        | 5fd1a7f30268c5194bbb7e5e | Journey Step Events                                            |             | false
```

Drücken Sie am Doppelpunkt die Leertaste, um die nächste Seite des Ergebnissatzes anzuzeigen, oder geben Sie `q` ein, um zur Eingabeaufforderung zurückzukehren.

Jeder Datensatz in Platform verfügt über die zugehörige Tabelle Query Service . Die Tabelle eines Datensatzes finden Sie über die Datensatzschnittstelle:

![ui-dataset-tablename.png](./images/ui-dataset-tablename.png)

Die Tabelle `demo_system_event_dataset_for_website_global_v1_1` ist die Tabelle Query Service , die dem Datensatz `Demo System - Event Schema for Website (Global v1.1)` entspricht.

Um einige Informationen darüber abzufragen, wo ein Produkt angezeigt wurde, wählen wir die **geo** -Informationen aus.

Kopieren Sie die folgende Anweisung, fügen Sie sie an der Eingabeaufforderung in der Befehlszeilenschnittstelle **von** PSQL ein und drücken Sie die Eingabetaste:

```sql
select placecontext.geo
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

In Ihrem Abfrageergebnis werden Sie feststellen, dass Spalten im Experience-Datenmodell (XDM) komplexe Typen und nicht nur skalare Typen sein können. In der obigen Abfrage möchten wir geografische Standorte identifizieren, an denen **commerce.productViews** aufgetreten ist. Um eine **commerce.productViews** zu identifizieren, müssen wir mithilfe von **durch das XDM-Modell navigieren.** (Punkt).

```text
aepenablementfy21:all=> select placecontext.geo
aepenablementfy21:all-> from   demo_system_event_dataset_for_website_global_v1_1
aepenablementfy21:all-> where  eventType = 'commerce.productViews'
aepenablementfy21:all-> and placecontext.geo.countryCode <> ''
aepenablementfy21:all-> limit 1;
                  geo                   
----------------------------------------
 ("(57.4694803,-3.1269422)",Tullich,GB)
(1 row)
```

Beachten Sie, dass das Ergebnis eher ein flaches Objekt als ein einzelner Wert ist. Das Objekt **placecontext.geo** enthält vier Attribute: Schema, Land und Stadt. Wenn ein Objekt als Spalte deklariert wird, gibt es das gesamte Objekt als Zeichenfolge zurück. Das XDM-Schema ist möglicherweise komplexer als das, was Sie kennen, aber es ist sehr leistungsstark und wurde so konzipiert, dass es viele Lösungen, Kanäle und Anwendungsfälle unterstützt.

Um die einzelnen Eigenschaften eines Objekts auszuwählen, verwenden Sie den **.** (Punkt).

Kopieren Sie die unten stehende Anweisung und fügen Sie sie an der Eingabeaufforderung in Ihrer **PSQL-Befehlszeilenschnittstelle** ein:

```sql
select placecontext.geo._schema.longitude
      ,placecontext.geo._schema.latitude
      ,placecontext.geo.city
      ,placecontext.geo.countryCode
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

Das Ergebnis der obigen Abfrage sollte wie folgt aussehen:
Das Ergebnis ist jetzt ein Satz einfacher Werte:

```text
aepenablementfy21:all=> select placecontext.geo._schema.longitude
aepenablementfy21:all->       ,placecontext.geo._schema.latitude
aepenablementfy21:all->       ,placecontext.geo.city
aepenablementfy21:all->       ,placecontext.geo.countryCode
aepenablementfy21:all-> from   demo_system_event_dataset_for_website_global_v1_1
aepenablementfy21:all-> where  eventType = 'commerce.productViews'
aepenablementfy21:all-> and placecontext.geo.countryCode <> ''
aepenablementfy21:all-> limit 1;
 longitude  |  latitude  |  city   | countrycode 
------------+------------+---------+-------------
 -3.1269422 | 57.4694803 | Tullich | GB
(1 row)
```

Machen Sie sich keine Gedanken, es gibt eine einfache Möglichkeit, den Pfad zu einer bestimmten Eigenschaft zu erhalten. Im folgenden Teil erfahren Sie, wie Sie das machen.

Sie müssen eine Abfrage bearbeiten. Öffnen wir also zunächst einen Editor.

Unter Windows

Klicken Sie auf das Symbol **search** in der Windows-Symbolleiste, geben Sie **notepad** in das Feld **search** ein und klicken Sie auf das Ergebnis **notepad** :

![windows-start-notepad.png](./images/windows-start-notepad.png)

In Mac

Installieren Sie [Brackets](https://github.com/adobe/brackets/releases/download/release-1.14/Brackets.Release.1.14.dmg) oder verwenden Sie einen anderen Texteditor Ihrer Wahl, falls Sie ihn nicht installiert haben, und befolgen Sie die Anweisungen. Suchen Sie nach der Installation über die Spotlight-Suche von Mac nach **Brackets** und öffnen Sie sie.

Kopieren Sie die folgende Anweisung in Notizblock oder Klammern:

```sql
select your_attribute_path_here
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

Gehen Sie zurück zu Ihrer Adobe Experience Platform-Benutzeroberfläche (sollte in Ihrem Browser geöffnet sein) oder navigieren Sie zu [https://platform.adobe.com](https://platform.adobe.com).

Wählen Sie **Schemas** aus, geben Sie `Demo System - Event Schema for Website (Global v1.1)` in das Feld **Suche** ein und wählen Sie `Demo System - Event Schema for Website (Global v1.1) Schema` aus der Liste aus.

![browse-schema.png](./images/browse-schema.png)

Durchsuchen Sie das XDM-Modell für **Demo System - Event Schema for Website (Global v1.1)**, indem Sie auf ein Objekt klicken. Erweitern Sie die Struktur für **placecontext**, **geo** und **schema**. Wenn Sie das tatsächliche Attribut **longitude** auswählen, wird der vollständige Pfad im markierten roten Feld angezeigt. Um den Pfad des Attributs zu kopieren, klicken Sie auf das Symbol Pfad kopieren .

![explore-schema-for-path.png](./images/explore-schema-for-path.png)

Wechseln Sie zu Ihrem Notebook/Ihren Klammern und entfernen Sie **Ihr_Attribut_Pfad_hier** aus der ersten Zeile. Positionieren Sie den Cursor hinter **select** in der ersten Zeile und fügen Sie (STRG-V) ein.

Kopieren Sie die geänderte Anweisung aus Notizblock/Klammern, fügen Sie sie an der Eingabeaufforderung in Ihre **PSQL-Befehlszeilenschnittstelle** ein und drücken Sie die Eingabetaste.

Das Ergebnis sollte wie folgt aussehen:

```text
aepenablementfy21:all=> select placeContext.geo._schema.longitude
aepenablementfy21:all-> from   demo_system_event_dataset_for_website_global_v1_1
aepenablementfy21:all-> where  eventType = 'commerce.productViews'
aepenablementfy21:all-> and placecontext.geo.countryCode <> ''
aepenablementfy21:all-> limit 1;
 longitude  
------------
 -3.1269422
```

Nächster Schritt: [5.1.3 Abfragen, Abfragen, Abfragen.. und Abwanderungsanalyse](./ex3.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
