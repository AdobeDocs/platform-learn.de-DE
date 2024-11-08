---
title: Query Service - Power BI/Tableau
description: Query Service - Power BI/Tableau
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 5.1.4 Datensatz aus einer Abfrage generieren

## Ziel

Erfahren Sie, wie Sie Datensätze aus Abfrageergebnissen generieren.
Microsoft Power BI Desktop/Tableau direkt mit Query Service verbinden
Erstellen eines Berichts in Microsoft Power BI Desktop/Tableau Desktop

## Lektionskontext

Eine Befehlszeilenschnittstelle zur Abfrage von Daten ist aufregend, aber nicht gut vorhanden. In dieser Lektion führen wir Sie durch einen empfohlenen Arbeitsablauf für die Verwendung von Microsoft Power BI Desktop/Tableau direkt im Query Service, um visuelle Berichte für Ihre Stakeholder zu erstellen.

## 5.1.4.1 Datensatz aus einer SQL-Abfrage erstellen

Die Komplexität Ihrer Abfrage wirkt sich darauf aus, wie lange es dauert, bis der Query Service Ergebnisse zurückgibt. Bei Abfragen direkt über die Befehlszeile oder andere Lösungen wie Microsoft Power BI/Tableau wird der Abfragedienst mit einem 5-minütigen Timeout (600 Sekunden) konfiguriert. In bestimmten Fällen werden diese Lösungen mit kürzeren Timeouts konfiguriert. Um größere Abfragen auszuführen und die Zeit, die zum Zurückgeben von Ergebnissen benötigt wird, vorab zu laden, bieten wir eine Funktion zum Generieren eines Datensatzes aus den Abfrageergebnissen an. Diese Funktion nutzt die SQL-Standardfunktion, die als Tabelle als Auswahl erstellen (CTAS) bezeichnet wird. Sie ist in der Platform-Benutzeroberfläche in der Abfrageliste verfügbar und kann auch direkt über die Befehlszeile mit PSQL ausgeführt werden.

Im vorherigen Schritt haben Sie **Ihren Namen** durch Ihren eigenen ldap ersetzt, bevor Sie ihn in PSQL ausführen.

```sql
select /* enter your name */
       e.--aepTenantId--.identification.core.ecid as ecid,
       e.placeContext.geo.city as city,
       e.placeContext.geo._schema.latitude latitude,
       e.placeContext.geo._schema.longitude longitude,
       e.placeContext.geo.countryCode as countrycode,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callFeeling as callFeeling,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callTopic as callTopic,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callContractCancelled as contractCancelled,
       l.--aepTenantId--.loyaltyDetails.level as loyaltystatus,
       l.--aepTenantId--.loyaltyDetails.points as loyaltypoints,
       l.--aepTenantId--.identification.core.loyaltyId as crmid
from   demo_system_event_dataset_for_website_global_v1_1 e
      ,demo_system_event_dataset_for_call_center_global_v1_1 c
      ,demo_system_profile_dataset_for_loyalty_global_v1_1 l
where  e.--aepTenantId--.demoEnvironment.brandName IN ('Luma Telco', 'Citi Signal')
and    e.web.webPageDetails.name in ('Cancel Service', 'Call Start')
and    e.--aepTenantId--.identification.core.ecid = c.--aepTenantId--.identification.core.ecid
and    l.--aepTenantId--.identification.core.ecid = e.--aepTenantId--.identification.core.ecid;
```

Navigieren Sie zur Adobe Experience Platform-Benutzeroberfläche - [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

Sie suchen in der Adobe Experience Platform-Abfrage-Benutzeroberfläche nach Ihrer ausgeführten Anweisung, indem Sie Ihren ldap in das Suchfeld eingeben:

Wählen Sie **Abfragen**, gehen Sie zu **Protokoll** und geben Sie Ihren ldap in das Suchfeld ein.

![search-query-for-ctas.png](./images/search-query-for-ctas.png)

Wählen Sie Ihre Abfrage aus und klicken Sie auf **Ausgabedatensatz**.

![search-query-for-ctas.png](./images/search-query-for-ctasa.png)

Geben Sie `--aepUserLdap-- Callcenter Interaction Analysis` als Namen und Beschreibung für den Datensatz ein und drücken Sie die Schaltfläche **Abfrage ausführen** .

![create-ctas-dataset.png](./images/create-ctas-dataset.png)

Daher wird eine neue Abfrage mit dem Status **Gesendet** angezeigt.

![ctas-query-sent.png](./images/ctas-query-submitted.png)

Nach Abschluss wird ein neuer Eintrag für **Datensatz erstellt** angezeigt (Sie müssen die Seite möglicherweise aktualisieren).

![ctas-dataset-created.png](./images/ctas-dataset-created.png)

Sobald Ihr Datensatz erstellt wurde (was 5-10 Minuten dauern kann), können Sie die Übung fortsetzen.

Nächster Schritt - Option A: [5.1.5 Query Service und Power BI](./ex5.md)

Nächster Schritt - Option B: [5.1.6 Query Service and Tableau](./ex6.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
