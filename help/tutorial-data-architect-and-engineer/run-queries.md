---
title: Abfragen ausführen
seo-title: Run queries | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Abfragen ausführen
description: In dieser Lektion erfahren Sie, wie Sie Abfragen einrichten, schreiben und ausführen, um die aufgenommenen Daten zu validieren.
role: Data Architect, Data Engineer
feature: Queries
jira: KT-4348
thumbnail: 4348-run-queries.jpg
exl-id: a37531cb-96ad-4547-86af-84f7ed65f019
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---

# Abfragen ausführen

<!-- 15 min-->
In dieser Lektion erfahren Sie, wie Sie Abfragen einrichten, schreiben und ausführen, um die aufgenommenen Daten zu validieren.

Der Abfrage-Service von Adobe Experience Platform hilft Ihnen, Ihre Daten zu verstehen, indem er die Verwendung von Standard-SQL zur Abfrage von Daten in Platform ermöglicht. Mit Query Service können Sie einen beliebigen Datensatz in den Data Lake einbinden und die Abfrageergebnisse als neuen Datensatz erfassen, der beim Reporting, für das maschinelle Lernen oder zur Aufnahme in das Echtzeit-Kundenprofil verwendet werden kann.

**Datenarchitekten** und **Dateningenieure** müssen den Abfrage-Service außerhalb dieses Tutorials verwenden.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über den Abfrage-Service zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/29795?learn=on)

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschließen dieser Lektion erforderlich sind.

<!-- Settings > **[!UICONTROL Services]** > **[!UICONTROL Query Service]**
* Permission items Data Management > **[!UICONTROL View Datasets]** and  **[!UICONTROL Manage Datasets]**
* Permission item Sandboxes > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
-->

## Einfache Abfragen

Beginnen wir mit einigen einfachen Abfragen:

1. Wechseln Sie in der Platform-Benutzeroberfläche **linken Navigationsbereich** Abfragen“
1. Klicken Sie auf **Schaltfläche Abfrage erstellen** oben rechts, um ein Textfeld zum Ausführen und Ausführen von Abfragen zu öffnen
1. Geben Sie die folgende Abfrage im Editor ein und drücken Sie Umschalt+Eingabe oder Umschalt+Zurückgeben , um die Abfrage auszuführen.

   ```
   SHOW TABLES
   ```

1. Zeigt die Liste der verfügbaren Tabellen an

   ![TABELLENABFRAGE ANZEIGEN](assets/queries-showTables.png)


1. Versuchen Sie nun diese Abfrage und ersetzen Sie `_techmarketingdemos` durch Ihren eigenen Mandanten-Namespace, der, wenn Sie sich erinnern, in Ihren Schemata sichtbar ist.

   ```
   SELECT person.name.lastName,loyalty.tier
   FROM luma_loyalty_dataset
   WHERE loyalty.tier ='gold'
   ```

   ![SELECT-Daten aus dem Treueprogramm-Datensatz](assets/queries-loyaltySelect.png)

1. Wenn ein Fehler auftritt, werden detaillierte Meldungen auf der Registerkarte **[!UICONTROL Konsole]** angezeigt, wie unten dargestellt
   ![Fehler in der Abfrage](assets/queries-error.png)

1. Bei Ihrer erfolgreichen Abfrage **[!UICONTROL Name]** sie `Luma Gold Level Customers`
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Speichern der Abfrage](assets/queries-loyaltySelect-save.png)


<!--SELECT COUNT(DISTINCT (_techmarketingdemos.systemIdentifier.loyaltyId)) FROM luma_loyalty_dataset 


SELECT _techmarketingdemos.systemIdentifier.loyaltyId, COUNT(_techmarketingdemos.systemIdentifier.loyaltyId)
FROM luma_loyalty_dataset 
GROUP BY _techmarketingdemos.systemIdentifier.loyaltyId
HAVING COUNT(_techmarketingdemos.systemIdentifier.loyaltyId) > 1;-->

## Weitere Übungen

Weitere Query Service-Übungen werden dem Tutorial zu einem späteren Zeitpunkt hinzugefügt.
<!--
## Join Datasets

In this exercise, we will join two datasets `Luma Loyalty Dataset` and `Luma Offline Purchase` to get list of gold customers who have spend over $500 dollars in one purchase.

1. Create a new query
1. Copy and paste following query in query editor and execute, again replacing `_techmarketingdemos` with your own tenant namespace
    
    ```
    SELECT DISTINCT lopd.commerce.order.purchaseID as PurchaseId ,
        lld.person.name.firstName as LastName ,
        lld.person.name.lastName as LastName ,
        lopd.personalEmail.address as email,
        lopd.commerce.order.priceTotal as Total

    FROM luma_loyalty_dataset lld
    JOIN luma_offline_purchase_event_dataset lopd
    ON lopd._techmarketingdemos.systemIdentifier.loyaltyId = lld._techmarketingdemos.systemIdentifier.loyaltyId

    WHERE lld._techmarketingdemos.loyalty.level ='gold' AND lopd.commerce.order.priceTotal >500;
    ```

1. You should get list of Gold Customers who have spend over $500 in single purchase.

## Output datasets

1. Select on Output Dataset button
1. Provide name and description to the dataset
1. Save.
1. Go to **Datasets** under **Data Management** to find new dataset created.

-->
<!--Add content for Adobe Defined Functions-->

## Weitere Ressourcen

* [Dokumentation zum Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de)
* [Abfrage-Service-API-Referenz](https://www.adobe.io/experience-platform-apis/references/query-service/)

Und jetzt zur letzten praktischen Lektion: [Erstellen von Segmenten](build-segments.md)!
