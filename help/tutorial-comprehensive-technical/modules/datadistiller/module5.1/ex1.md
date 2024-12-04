---
title: Query Service - Voraussetzungen
description: Query Service - Voraussetzungen
kt: 5342
doc-type: tutorial
exl-id: b8a404d1-7796-46e3-b245-553acdc753ae
source-git-commit: d9d9a38c1e160950ae755e352a54667c8a7b30f7
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# 5.1.1 Voraussetzungen

## PSQL-Befehlszeilendienstprogramm installieren

Befolgen Sie die Anweisungen in der Adobe Experience Platform-Dokumentation, um den psql-Client zu installieren:
[PSQL-Installationsanleitung](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html)

Nachdem Sie PSQL installiert haben, müssen Sie möglicherweise Ihren **PATH** aktualisieren, indem Sie den folgenden Befehl in einem Terminal-Fenster ausführen:

Für macOS (ersetzen Sie XX im folgenden Befehl durch die Versionsnummer von PSQL, die Sie installiert haben):

`export PATH=/Library/PostgreSQL/XX/bin:$PATH`

## Installieren von Power BI

Nur für Windows-Benutzer

[Installieren von Microsoft Power BI](https://experienceleague.adobe.com/docs/experience-platform/query/clients/power-bi.html)

Stellen Sie sicher, dass Sie die exakte Version von **npgsql** installieren, wie im Dokument erwähnt, da Sie sonst nicht in der Lage sind, Power BI mit Adobe Experience Platform Query Service zu verbinden.

## Installieren von Tableau

Für Windows- oder Mac-Benutzer

[Installieren Sie Tableau Desktop](https://experienceleague.adobe.com/docs/experience-platform/query/clients/tableau.html) gemäß der Dokumentation.

Tableau gibt Ihnen automatisch eine 14-tägige Testphase.

Wenn Sie Tableau über diese 14 Tage hinaus verwenden möchten, benötigen Sie einen Lizenzschlüssel.

Nächster Schritt: [5.1.2 Erste Schritte](./ex2.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
