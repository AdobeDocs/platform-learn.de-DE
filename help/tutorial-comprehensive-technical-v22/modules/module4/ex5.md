---
title: Query Service - Datensatz mit Power BI durchsuchen
description: Query Service - Datensatz mit Power BI durchsuchen
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 0f9e6719-056b-4858-8c86-04b3beaa950e
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 4.5 Query Service und Power BI

Öffnen Sie Microsoft Power BI Desktop.

![start-power-bi.png](./images/start-power-bi.png)

Klicken **Daten abrufen**.

![power-bi-get-data.png](./images/power-bi-get-data.png)

Suchen Sie nach **postgres** (1), wählen Sie **Postgres** 2) aus der Liste und **Verbinden** Absatz 3.

![power-bi-connect-progress.png](./images/power-bi-connect-progress.png)

Navigieren Sie zu Adobe Experience Platform, um **Abfragen** und **Anmeldeinformationen**.

![query-service-credentials.png](./images/query-service-credentials.png)

Aus dem **Anmeldeinformationen** Seite in Adobe Experience Platform, kopieren Sie die **Host** und fügen Sie sie in **Server** und kopieren Sie das **Datenbank** und fügen Sie sie in **Datenbank** in PowerBI und klicken Sie dann auf OK (2).

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Port **:80** am Ende des Serverwerts, da der Query Service derzeit nicht den standardmäßigen PostgreSQL-Port 5432 verwendet.

![power-bi-connect-server.png](./images/power-bi-connect-server.png)

Geben Sie im nächsten Dialogfeld den Benutzernamen und das Kennwort mit Ihrem Benutzernamen und Kennwort ein, die Sie im **Anmeldeinformationen** von Abfragen in Adobe Experience Platform.

![query-service-credentials.png](./images/query-service-credentials.png)

Legen Sie im Dialogfeld Navigator Ihre **LDAP** im Suchfeld (1), um Ihre CTAS-Datensätze zu finden und das Kontrollkästchen neben jedem Datensatz zu aktivieren (2). Klicken Sie dann auf Laden (3).

![power-bi-load-churn-data.png](./images/power-bi-load-churn-data.png)

Stellen Sie sicher, dass **Bericht** Registerkarte (1) ausgewählt ist.

![power-bi-report-tab.png](./images/power-bi-report-tab.png)

Wählen Sie die Karte (1) aus und vergrößern Sie die Karte (2), nachdem sie der Berichtsarbeitsfläche hinzugefügt wurde.

![power-bi-select-map.png](./images/power-bi-select-map.png)

Als Nächstes müssen die Kennzahlen und Dimensionen definiert werden. Ziehen Sie dazu Felder aus dem **fields** auf die entsprechenden Platzhalter (unter **Visualisierungen**) wie unten angegeben:

![power-bi-drag-lat-lon.png](./images/power-bi-drag-lat-lon.png)

Als Maßnahme verwenden wir die Anzahl der **customerId**. Ziehen Sie die **crmid** aus dem **fields** in die **Größe** Platzhalter:

![power-bi-drag-crmid.png](./images/power-bi-drag-crmid.png)

Abschließend noch einige Schritte **callTopic** Analyse, ziehen wir die **callTopic** zum **Filter auf Seitenebene** Platzhalter (Sie müssen ggf. im **Visualisierungen** Abschnitt);

![power-bi-drag-calltopic.png](./images/power-bi-drag-calltopic.png)

Auswählen/Aufheben der Auswahl **callTopics** Untersuchung:

![power-bi-report-select-calltopic.png](./images/power-bi-report-select-calltopic.png)

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [4.7 Query Service-API](./ex7.md)

[Zurück zu Modul 4](./query-service.md)

[Zu allen Modulen zurückkehren](../../overview.md)
