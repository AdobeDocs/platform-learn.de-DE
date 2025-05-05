---
title: Abfrage-Service - Voraussetzungen
description: Abfrage-Service - Voraussetzungen
kt: 5342
doc-type: tutorial
exl-id: e9e4d478-cb8d-42a9-87a3-319e5a8b8522
source-git-commit: 1e3a8d585503eddad4c642a3b13d2b5f7ddc9943
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# 2.1.1 Voraussetzungen

## Installieren des PSQL-Befehlszeilen-Dienstprogramms

Befolgen Sie die in der Adobe Experience Platform-Dokumentation beschriebenen Anweisungen, um den PSQL-Client zu installieren:
[PSQL-Installationshandbuch](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html?lang=de)

Nachdem Sie PSQL installiert haben, müssen Sie möglicherweise Ihren **PATH** aktualisieren, indem Sie den folgenden Befehl in einem Terminal-Fenster ausführen:

Für macOS (ersetzen Sie XX im folgenden Befehl durch die Versionsnummer von PSQL, die Sie installiert haben):

`export PATH=/Library/PostgreSQL/XX/bin:$PATH`

## Installieren von Power BI

Nur für Windows-Benutzer

[Installieren von Microsoft Power BI](https://experienceleague.adobe.com/docs/experience-platform/query/clients/power-bi.html?lang=de)

Installieren Sie unbedingt die exakte Version von **npgsql** wie im Dokument beschrieben. Andernfalls können Sie Power BI nicht mit dem Abfrage-Service von Adobe Experience Platform verbinden.

## Installieren von Tableau

Für Windows- oder Mac-Benutzer

[Installieren von Tableau Desktop](https://experienceleague.adobe.com/docs/experience-platform/query/clients/tableau.html?lang=de) gemäß der Dokumentation.

Tableau bietet Ihnen automatisch eine 14-tägige Testphase.

Wenn Sie Tableau über diese 14 Tage hinaus verwenden möchten, benötigen Sie einen Lizenzschlüssel.

## Nächste Schritte

Navigieren Sie zu [2.1.2 Erste Schritte](./ex2.md){target="_blank"}

Zurück zu [Abfrage-Service](./query-service.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
