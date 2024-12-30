---
title: Abfrage-Service - Erkunden des Datensatzes mit Power BI
description: Abfrage-Service - Erkunden des Datensatzes mit Power BI
kt: 5342
doc-type: tutorial
exl-id: c27abd0e-e563-4702-a243-1aec84ce6116
source-git-commit: f843c50af04d744a7d769f320b5b55a5e6d25ffd
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 5.1.6 Abfrage-Service und Power BI

Öffnen Sie Microsoft Power BI Desktop.

![start-power-bi.png](./images/startpowerbi.png)

Klicken Sie **Daten abrufen**.

![power-bi-get-data.png](./images/powerbigetdata.png)

Suchen Sie nach **postgres** (1), wählen Sie **Postgres** (2) aus der Liste aus und **Verbinden** (3).

![power-bi-connect-progress.png](./images/powerbiconnectprogress.png)

Wechseln Sie zu Adobe Experience Platform, zu **Abfragen** und zu **Anmeldeinformationen**.

![query-service-credentials.png](./images/queryservicecredentials.png)

Kopieren Sie auf der Seite **Anmeldeinformationen** in Adobe Experience Platform den **Host**, fügen Sie ihn in das Feld **Server** ein, kopieren Sie den **Database** und fügen Sie ihn in das Feld **Database** in PowerBI ein. Klicken Sie dann auf OK (2).

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie Port **:80** am Ende des Server-Werts einschließen, da der Abfrage-Service derzeit nicht den standardmäßigen PostgreSQL-Port 5432 verwendet.

![power-bi-connect-server.png](./images/powerbiconnectserver.png)

Füllen Sie im nächsten Dialogfeld den Benutzernamen und das Kennwort mit Ihrem Benutzernamen und Kennwort aus den **Anmeldeinformationen** von Abfragen in Adobe Experience Platform.

![query-service-credentials.png](./images/queryservicecredentials.png)

Legen Sie im Navigator-Dialogfeld Ihren **LDAP** in das Suchfeld (1), um Ihre CTAS-Datensätze zu finden, und aktivieren Sie das Kontrollkästchen neben jedem (2). Klicken Sie anschließend auf Laden (3).

![power-bi-load-churn-data.png](./images/powerbiloadchurndata.png)

Stellen Sie sicher **dass die Registerkarte** Bericht) (1) ausgewählt ist.

![power-bi-report-tab.png](./images/powerbireporttab.png)

Wählen Sie die Zuordnung (1) aus und vergrößern Sie nach dem Hinzufügen zur Reporting-Arbeitsfläche die Zuordnung (2).

![power-bi-select-map.png](./images/powerbiselectmap.png)

Als Nächstes müssen wir die Kennzahlen und Dimensionen definieren. Ziehen Sie dazu Felder aus dem Abschnitt **Felder** auf die entsprechenden Platzhalter (unter **Visualisierungen**), wie unten angegeben:

![power-bi-drag-lat-lon.png](./images/powerbidraglatlon.png)

Als Kennzahl verwenden wir die Anzahl **customerId**. Ziehen Sie das Feld **crmid** aus dem Abschnitt **fields** in den **Size**-Platzhalter:

![power-bi-drag-crmid.png](./images/powerbidragcrmid.png)

Ziehen wir zum Schluss **callTopic**-Analyse das Feld **callTopic** auf den Platzhalter **Filter auf Seitenebene** (Sie müssen möglicherweise im Abschnitt **Visualisierungen** scrollen);

![power-bi-drag-calltopic.png](./images/powerbidragcalltopic.png)

Wählen/deaktivieren Sie **callTopics** zur Untersuchung aus:

![power-bi-report-select-calltopic.png](./images/powerbireportselectcalltopic.png)

Sie haben jetzt diese Übung beendet.

Nächster Schritt: [5.1.8 Query Service API](./ex8.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zurück zu „Alle Module“](../../../overview.md)
