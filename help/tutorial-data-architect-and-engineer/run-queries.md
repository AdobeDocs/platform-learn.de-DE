---
title: Abfragen ausführen
seo-title: Run queries | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Abfragen ausführen
description: In dieser Lektion erfahren Sie, wie Sie Abfragen einrichten, schreiben und ausführen, um die erfassten Daten zu validieren.
role: Data Architect, Data Engineer
feature: Queries
kt: 4348
thumbnail: 4348-run-queries.jpg
exl-id: a37531cb-96ad-4547-86af-84f7ed65f019
source-git-commit: cf0193e3aae4d6536c868f078f4773ee14e90408
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 5%

---

# Abfragen ausführen

<!-- 15 min-->
In dieser Lektion erfahren Sie, wie Sie Abfragen einrichten, schreiben und ausführen, um die erfassten Daten zu validieren.

Adobe Experience Platform Query Service hilft Ihnen, Ihre Daten zu verstehen, indem es Ihnen ermöglicht, SQL-Standard zur Abfrage von Daten in Platform zu verwenden. Mithilfe von Query Service können Sie einen beliebigen Datensatz in den Data Lake einbinden und die Abfrageergebnisse als neuen Datensatz erfassen, der für Berichte, maschinelles Lernen oder die Aufnahme in das Echtzeit-Kundenprofil verwendet werden kann.

**Datenarchitekten** und **Dateningenieure** müssen den Abfragedienst außerhalb dieses Tutorials verwenden.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Query Service zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/29795?quality=12&learn=on)

## Erforderliche Berechtigungen

Im [Berechtigungen konfigurieren](configure-permissions.md) Lektion erstellen Sie alle Zugriffssteuerungen, die zum Abschluss dieser Lektion erforderlich sind.

<!-- Settings > **[!UICONTROL Services]** > **[!UICONTROL Query Service]**
* Permission items Data Management > **[!UICONTROL View Datasets]** and  **[!UICONTROL Manage Datasets]**
* Permission item Sandboxes > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
-->

## Einfache Abfragen

Beginnen wir mit einigen einfachen Abfragen:

1. Navigieren Sie in der Benutzeroberfläche von Platform zu **Abfragen** in der linken Navigation
1. Wählen Sie die **Abfrage erstellen** Schaltfläche oben rechts, um ein Textfeld zum Ausführen und Ausführen von Abfragen zu öffnen
1. Geben Sie die folgende Abfrage in den Editor ein und drücken Sie Umschalt+Eingabetaste oder Umschalt+Zurück, um die Abfrage auszuführen.

   ```
   SHOW TABLES
   ```

1. Zeigt die Liste der verfügbaren Tabellen an

   ![TABELLENabfrage ANZEIGEN](assets/queries-showTables.png)


1. Versuchen Sie jetzt diese Abfrage, indem Sie `_techmarketingdemos` mit Ihrem eigenen Mandanten-Namespace, der, wenn Sie sich daran erinnern, in Ihren Schemas sichtbar ist.

   ```
   SELECT person.name.lastName,loyalty.tier
   FROM luma_loyalty_dataset
   WHERE loyalty.tier ='gold'
   ```

   ![Daten aus dem Treuedatensatz auswählen](assets/queries-loyaltySelect.png)

1. Wenn ein Fehler auftritt, werden im Abschnitt **[!UICONTROL Konsole]** Registerkarte, wie unten dargestellt
   ![Fehler in der Abfrage](assets/queries-error.png)

1. Mit Ihrer erfolgreichen Abfrage **[!UICONTROL Name]** it `Luma Gold Level Customers`
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**
   ![Abfrage speichern](assets/queries-loyaltySelect-save.png)


<!--SELECT COUNT(DISTINCT (_techmarketingdemos.systemIdentifier.loyaltyId)) FROM luma_loyalty_dataset 


SELECT _techmarketingdemos.systemIdentifier.loyaltyId, COUNT(_techmarketingdemos.systemIdentifier.loyaltyId)
FROM luma_loyalty_dataset 
GROUP BY _techmarketingdemos.systemIdentifier.loyaltyId
HAVING COUNT(_techmarketingdemos.systemIdentifier.loyaltyId) > 1;-->

## Zusätzliche Übungen

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

* [Dokumentation zu Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de)
* [Query Service-API-Referenz](https://www.adobe.io/experience-platform-apis/references/query-service/)

Und nun zur abschließenden praktischen Lektion: [Segmente erstellen](build-segments.md)!
