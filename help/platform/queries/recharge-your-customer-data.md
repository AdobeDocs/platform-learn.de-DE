---
title: Erneutes Laden Ihrer Kundendaten für die Bereitstellung elektrisierter Erlebnisse
description: Erfahren Sie, wie Sie die Auswirkungen von Daten mit geringer Qualität verringern, die Zeit bis zur Wertschöpfung reduzieren und den ROI multiplizieren können, indem Sie dieselben Daten für eine Vielzahl von Anwendungsfällen verwenden.
role: Data Engineer, Data Architect, Developer
feature: Queries
kt: 10323
thumbnail: 342533.jpeg
exl-id: 30574cc5-66fa-4ab8-83ed-7af710294dbf
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 3%

---

# Erneutes Laden Ihrer Kundendaten für die Bereitstellung elektrisierter Erlebnisse

Omnichannel-Daten sind ein wichtiger Bestandteil zur Unterstützung umsetzbarer Kundenprofile, die von Marketing-Experten verwendet werden, um die Aktivierung zu orchestrieren und die resultierenden Journey zu messen. Unternehmen stehen jedoch vor Herausforderungen bei der Verwaltung der Qualität, des Umfangs und der Vielfalt dieser Daten. Sie erfordern optimierte Lösungen, um die Auswirkungen minderwertiger Daten zu verringern, die Zeit bis zur Wertschöpfung zu reduzieren und den ROI zu multiplizieren, indem für viele Anwendungsfälle dieselben Daten verwendet werden.

In diesem Video wird Folgendes untersucht:

* Adobe Experience Platform-Datenvorbereitungsfunktionen, die Sie nutzen können
* Steigerung des ROI aus Adobe Real-Time CDP, Adobe Journey Optimizer und Customer Journey Analytics

>[!VIDEO](https://video.tv.adobe.com/v/342533?quality=12&learn=on)

## SQL-Beispiel

```sql
INSERT INTO summit_adv_data_prep_dataset
SELECT STRUCT(
customerId AS crmCustomerId, struct(sku AS sku, price AS sku_price, abandonTS AS abandonTS) AS abandonBrowse) AS _pfreportingonprod
FROM
(SELECT
B.personKey.sourceID AS customerId,
A.productListItems[0].SKU AS sku,
max(A.timestamp) AS abandonTS,
max(C._pfreportingonprod.price) AS price
FROM summit_adobe_analytics_dataset A,profile_attribute_14adf268_2a20_4dee_bee6_a6b0e34616a9 B,summit_product_dataset C
WHERE A._experience.analytics.customDimensions.eVars.eVar1 = B.personKey.sourceID
AND A.productListItems[0].sku = C._pfreportingonprod.sku
AND A.web.webpagedetails.URL NOT LIKE '%orderconfirmation%'
AND timestamp > current_date - interval '4 day'
GROUP BY customerId,sku
order by price desc)D;
```

Weitere Informationen finden Sie unter [Dokumentation zu Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de).

>[!NOTE]
>
>Dieses Video ist ein Auszug aus der Adobe Summit-Sitzung 2020 *[Neuladen von Omnichannel-Daten für die Elektrifizierung von Erlebnissen](https://business.adobe.com/summit/2022/sessions/recharging-omnichannel-data-for-electrifying-exper-s409.html)*.
