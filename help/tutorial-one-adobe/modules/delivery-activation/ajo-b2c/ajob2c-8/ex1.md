---
title: Einrichten der Grundlage für relationale Daten
description: Einrichten der Grundlage für relationale Daten
kt: 5342
doc-type: tutorial
exl-id: 532e5f2c-971f-488f-bef4-3a8141408cc8
source-git-commit: bf3bebfa3bd79829da5352e950aed3f4ef5bf6d1
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 21%

---

# 3.8.1 Einrichten der Grundlage für relationale Daten

Melden Sie sich unter [https://experience.adobe.com](https://experience.adobe.com) bei Adobe Journey Optimizer an. Auf **Journey Optimizer**.

![AJO OC](./images/aechome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`.

![AJO OC](./images/ajohome.png)

## 3.8.1.1 Einrichtung relationaler Schemata

Ein relationales Schema ist die formale Definition des modellbasierten Datenmodells.

Es gibt an:

- Den Satz von Tabellen
- Die Spalten der einzelnen Tabellen
- Die Einschränkungen
- Die Beziehungen zwischen Tabellen

Beim Organisieren von Schemata oder Tabellen in einem modellbasierten Datenmodell geht es um die Strukturierung Ihrer Daten in verschiedenen Tabellen. Stellen Sie sicher, dass in jeder Tabelle ein Entitäts-/Schematyp gespeichert ist.

Bei der Aufnahme von Daten in zur Verwendung mit Adobe Journey Optimizer Orchestered Campaign stehen die folgenden Quellen zur Verfügung:

- Amazon S3
- Google Cloud Storage
- SFTP
- Snowflake
- Google BigQuery
- Data Landing Zone
- Azure Databricks
- Hochladen einer lokalen Datei

Der erste Schritt in dieser Übung ist die Konfiguration Ihrer relationalen XDM-Schemata. Scrollen Sie im linken Menü nach unten zu **Daten-Management** und wählen Sie **Schemata** aus. Klicken Sie auf **+ Schema erstellen**.

![AJO OC](./images/ajoocdata1.png)

Wählen Sie **Relational** aus.

![AJO OC](./images/ajoocdata2.png)

Wählen Sie **DDL-Datei hochladen** und klicken Sie dann auf **Dateien auswählen**.

![AJO OC](./images/ajoocdata3.png)

Nachdem Ihre relationalen XDM-Schemata konfiguriert und Daten aufgenommen wurden, können Sie in der nächsten Übung beginnen, diese Daten zur Erstellung Ihrer orchestrierten Kampagne zu verwenden.

## 3.8.1.2 Datenaufnahme


## Nächste Schritte

Navigieren Sie zu [Erstellen einer orchestrierten Kampagne](./ex2.md){target="_blank"}

Zurück zu [Adobe Journey Optimizer: Kampagnen](./ajocampaigns.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
