---
title: Query Service - Verwendung des Query Service
description: Query Service - Verwendung des Query Service
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
exl-id: 31c14a9b-cb62-48ab-815c-caa6e832794f
source-git-commit: d9d9a38c1e160950ae755e352a54667c8a7b30f7
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# 5.1.3 Query Service verwenden

## Ziel

- Suchen und Erkunden von Datensätzen
- Erfahren Sie, wie Sie in Ihren Abfragen Experience-Datenmodellobjekte und -attribute bearbeiten.

## Kontext

In diesem Abschnitt erfahren Sie, wie Sie mit PSQL Informationen zu den verfügbaren Datensätzen abrufen, wie Sie Abfragen für das Experience-Datenmodell (XDM) schreiben und Ihre ersten einfachen Berichtsabfragen mit den Datensätzen Query Service und Citi Signal schreiben können.

## Grundlegende Abfragen

In diesem Abschnitt erfahren Sie mehr über die Methoden zum Abrufen von Informationen zu den verfügbaren Datensätzen und dazu, wie Daten mit einer Abfrage aus einem XDM-Datensatz ordnungsgemäß abgerufen werden.

Alle Datensätze, die wir Anfang 1 über Adobe Experience Platform erforscht haben, stehen auch als Tabellen über eine SQL-Schnittstelle zur Verfügung. Um diese Tabellen aufzulisten, können Sie den Befehl **Tabellen anzeigen;** verwenden.

Führen Sie `show tables;` in Ihrer **PSQL-Befehlszeilenschnittstelle** aus. (Vergessen Sie nicht, Ihren Befehl mit einem Semikolon zu beenden).

Kopieren Sie den Befehl `show tables;` und fügen Sie ihn an der Eingabeaufforderung ein:

![command-quick-show-show-tables.png](./images/commandpromptshowtables.png)

Das folgende Ergebnis wird angezeigt:

```text
tech-insiders:all=> show tables;
                               name                               |                                                  dataSetId                                                   |                                       dataSet                                        | description |        labels        
------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+-------------+----------------------
 ajo_bcc_feedback_event_dataset                                   | 672a07cb7728e82aefa1ec56                                                                                     | AJO BCC Feedback Event Dataset                                                       |             | 
 ajo_classification_dataset                                       | 672a07cab55b0d2aef6f9626                                                                                     | AJO Classification Dataset                                                           |             | 
 ajo_consent_service_dataset                                      | 672a07c80fd5fd2aee4155ca                                                                                     | AJO Consent Service Dataset                                                          |             | 'PROFILE'
 ajo_email_tracking_experience_event_dataset                      | 672a07c926d57d2aef020230                                                                                     | AJO Email Tracking Experience Event Dataset                  :
                               name                               |                                                  dataSetId                                                   |                                       dataSet                                        | description |        labels        
------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+-------------+----------------------
 ajo_bcc_feedback_event_dataset                                   | 672a07cb7728e82aefa1ec56                                                                                     | AJO BCC Feedback Event Dataset                                                       |             | 
 ajo_classification_dataset                                       | 672a07cab55b0d2aef6f9626                                                                                     | AJO Classification Dataset                                                           |             | 
 ajo_consent_service_dataset                                      | 672a07c80fd5fd2aee4155ca                                                                                     | AJO Consent Service Dataset                                                          |             | 'PROFILE'
 ajo_email_tracking_experience_event_dataset                      | 672a07c926d57d2aef020230                                                                                     | AJO Email Tracking Experience Event Dataset   
```

Drücken Sie am Doppelpunkt die Leertaste, um die nächste Seite des Ergebnissatzes anzuzeigen, oder geben Sie `q` ein, um zur Eingabeaufforderung zurückzukehren.

Jeder Datensatz in AEP verfügt über die zugehörige Tabelle Query Service . Die Tabelle eines Datensatzes finden Sie über die Benutzeroberfläche &quot;Datensätze&quot;:

![ui-dataset-tablename.png](./images/uidatasettablename.png)

Die Tabelle `demo_system_event_dataset_for_website_global_v1_1` ist die Tabelle Query Service , die dem Datensatz `Demo System - Event Schema for Website (Global v1.1)` entspricht.

Um einige Informationen darüber abzufragen, wo ein Produkt angezeigt wurde, wählen wir die **geo** -Informationen aus.

Kopieren Sie die unten stehende Abfrage, fügen Sie sie an der Eingabeaufforderung in die Befehlszeilenschnittstelle **von** PSQL ein und drücken Sie die Eingabetaste:

```sql
select placecontext.geo
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

In Ihrem Abfrageergebnis werden Sie feststellen, dass Spalten im Experience-Datenmodell (XDM) komplexe Typen und nicht nur skalare Typen sein können. In der obigen Abfrage möchten wir geografische Standorte identifizieren, an denen **commerce.productViews** aufgetreten ist. Um eine **commerce.productViews** zu identifizieren, müssen wir mithilfe von **durch das XDM-Modell navigieren.** (Punkt).

```text
tech-insiders:all=> select placecontext.geo
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
                 geo                  
--------------------------------------
 ("(51.59119,-1.407848)",Charlton,GB)
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
tech-insiders:all=> select placecontext.geo._schema.longitude
      ,placecontext.geo._schema.latitude
      ,placecontext.geo.city
      ,placecontext.geo.countryCode
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
 longitude | latitude |   city   | countrycode 
-----------+----------+----------+-------------
 -1.407848 | 51.59119 | Charlton | GB
(1 row)
```

Machen Sie sich keine Gedanken, es gibt eine einfache Möglichkeit, den Pfad zu einer bestimmten Eigenschaft zu erhalten. Im folgenden Teil erfahren Sie, wie Sie das machen.

Sie müssen eine Abfrage bearbeiten. Öffnen wir also zunächst einen Editor.

Unter Windows: Verwenden Sie **Notepad**

Auf Mac: Installieren Sie eine beliebige Text Editor-App und öffnen Sie sie.

Kopieren Sie die folgende Anweisung in Ihren Texteditor:

```sql
select your_attribute_path_here
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

Gehen Sie zurück zu Ihrer Adobe Experience Platform-Benutzeroberfläche (sollte in Ihrem Browser geöffnet sein) oder navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform).

Wählen Sie **Schemas** aus, geben Sie `Demo System - Event Schema for Website` in das Feld **Suche** ein und klicken Sie auf , um das Schema `Demo System - Event Schema for Website (Global v1.1) Schema` zu öffnen.

![browse-schema.png](./images/browseschema.png)

Durchsuchen Sie das XDM-Modell für **Demo System - Event Schema for Website (Global v1.1)**, indem Sie auf ein Objekt klicken. Erweitern Sie die Struktur für **placecontext**, **geo** und **schema**. Wenn Sie das tatsächliche Attribut **longitude** auswählen, wird der vollständige Pfad im markierten roten Feld angezeigt. Um den Pfad des Attributs zu kopieren, klicken Sie auf das Symbol Pfad kopieren .

![explore-schema-for-path.png](./images/exploreschemaforpath.png)

Wechseln Sie zu Ihrem Notebook/Ihren Klammern und entfernen Sie **Ihr_Attribut_Pfad_hier** aus der ersten Zeile. Positionieren Sie den Cursor hinter **select** in der ersten Zeile und fügen Sie (STRG-V) ein.

![explore-schema-for-path.png](./images/exploreschemaforpath1.png)

Kopieren Sie die geänderte Anweisung, fügen Sie sie an der Eingabeaufforderung in der Befehlszeilenschnittstelle **von** PSQL ein und drücken Sie die Eingabetaste.

Das Ergebnis sollte wie folgt aussehen:

```text
tech-insiders:all=> select placeContext.geo._schema.longitude
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
 longitude 
-----------
 -1.407848
(1 row)
```

Nächster Schritt: [5.1.4 Abfragen, Abfragen, Abfragen.. und Abwanderungsanalyse](./ex4.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
