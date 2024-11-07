---
title: Query Service - Datensatz mit Power BI durchsuchen
description: Query Service - Datensatz mit Power BI durchsuchen
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 5.1.5 Query Service und Power BI

Öffnen Sie Microsoft Power BI Desktop.

![start-power-bi.png](./images/start-power-bi.png)

Klicken Sie auf **Daten abrufen**.

![power-bi-get-data.png](./images/power-bi-get-data.png)

Suchen Sie nach **postgres** (1), wählen Sie **Postgres** (2) aus der Liste und **Connect** (3).

![power-bi-connect-progress.png](./images/power-bi-connect-progress.png)

Wechseln Sie zu Adobe Experience Platform, zu **Abfragen** und zu **Anmeldeinformationen**.

![query-service-credentials.png](./images/query-service-credentials.png)

Kopieren Sie auf der Seite **Anmeldedaten** in Adobe Experience Platform den **Host** und fügen Sie ihn in das Feld **Server** ein. Kopieren Sie dann die **Datenbank**, fügen Sie sie in das Feld **Datenbank** in Power BI ein und klicken Sie dann auf OK (2).

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie Port **:80** am Ende des Serverwerts einschließen, da der Query Service derzeit nicht den standardmäßigen PostgreSQL-Port 5432 verwendet.

![power-bi-connect-server.png](./images/power-bi-connect-server.png)

Füllen Sie im nächsten Dialogfeld den Benutzernamen und das Kennwort mit Ihrem Benutzernamen und Kennwort aus, die in den **Anmeldedaten** der Abfragen in Adobe Experience Platform zu finden sind.

![query-service-credentials.png](./images/query-service-credentials.png)

Setzen Sie im Dialogfeld Navigator Ihren **LDAP** in das Suchfeld (1), um Ihre CTAS-Datensätze zu finden, und aktivieren Sie das Kontrollkästchen neben jedem (2). Klicken Sie dann auf Laden (3).

![power-bi-load-churn-data.png](./images/power-bi-load-churn-data.png)

Stellen Sie sicher, dass die Registerkarte &quot;**Bericht**&quot;(1) ausgewählt ist.

![power-bi-report-tab.png](./images/power-bi-report-tab.png)

Wählen Sie die Karte (1) aus und vergrößern Sie die Karte (2), nachdem sie der Berichtsarbeitsfläche hinzugefügt wurde.

![power-bi-select-map.png](./images/power-bi-select-map.png)

Als Nächstes müssen wir die Kennzahlen und Dimensionen definieren. Ziehen Sie dazu Felder aus dem Abschnitt **Felder** auf die entsprechenden Platzhalter (unter **Visualisierungen**), wie unten angegeben:

![power-bi-drag-lat-lon.png](./images/power-bi-drag-lat-lon.png)

Als Maßstab verwenden wir eine Anzahl von **customerId**. Ziehen Sie das Feld **crmid** aus dem Abschnitt **fields** in den Platzhalter **size** :

![power-bi-drag-crmid.png](./images/power-bi-drag-crmid.png)

Um schließlich einige Analysen von **callTopic** durchzuführen, ziehen wir das Feld **callTopic** auf den Platzhalter **Filter auf Seitenebene** (möglicherweise müssen Sie im Abschnitt **Visualisierungen** einen Bildlauf durchführen).

![power-bi-drag-calltopic.png](./images/power-bi-drag-calltopic.png)

Auswählen/Aufheben der Auswahl von **callTopics** zur Untersuchung:

![power-bi-report-select-calltopic.png](./images/power-bi-report-select-calltopic.png)

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [5.1.7 Query Service API](./ex7.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
