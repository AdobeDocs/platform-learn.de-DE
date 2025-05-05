---
title: Abfrage-Service - Voraussetzungen
description: Abfrage-Service - Voraussetzungen
kt: 5342
doc-type: tutorial
exl-id: b8a404d1-7796-46e3-b245-553acdc753ae
source-git-commit: d9d9a38c1e160950ae755e352a54667c8a7b30f7
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# 5.1.1 Voraussetzungen

## Installieren des PSQL-Befehlszeilen-Dienstprogramms

Befolgen Sie die in der Adobe Experience Platform-Dokumentation beschriebenen Anweisungen, um den PSQL-Client zu installieren:
[PSQL-Installationshandbuch](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html?lang=de)

Nachdem Sie PSQL installiert haben, müssen Sie möglicherweise Ihren **PATH** aktualisieren, indem Sie den folgenden Befehl in einem Terminal-Fenster ausführen:

Für macOS (ersetzen Sie XX im folgenden Befehl durch die Versionsnummer von PSQL, die Sie installiert haben):

`export PATH=/Library/PostgreSQL/XX/bin:$PATH`

## Power BI installieren

Nur für Windows-Benutzer

[Microsoft-Power BI installieren](https://experienceleague.adobe.com/docs/experience-platform/query/clients/power-bi.html?lang=de)

Installieren Sie unbedingt die exakte Version von **npgsql** wie im Dokument beschrieben. Andernfalls können Sie keinen Power BI mit dem Abfrage-Service von Adobe Experience Platform verbinden.

## Installieren von Tableau

Für Windows- oder Mac-Benutzer

[Installieren von Tableau Desktop](https://experienceleague.adobe.com/docs/experience-platform/query/clients/tableau.html?lang=de) gemäß der Dokumentation.

Tableau bietet Ihnen automatisch eine 14-tägige Testphase.

Wenn Sie Tableau über diese 14 Tage hinaus verwenden möchten, benötigen Sie einen Lizenzschlüssel.

Nächster Schritt: [5.1.2 Erste Schritte](./ex2.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zurück zu „Alle Module“](../../../overview.md)
