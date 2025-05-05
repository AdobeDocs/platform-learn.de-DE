---
title: Laden Sie Ihre Kundendaten auf, um elektrisierende Erlebnisse bereitzustellen
description: Erfahren Sie, wie Sie die Auswirkungen von Daten niedriger Qualität mindern, die Time-to-Value verkürzen und den ROI multiplizieren können, indem Sie dieselben Daten für eine Vielzahl von Anwendungsfällen verwenden.
feature: Queries
role: Data Engineer, Data Architect, Developer
level: Beginner
jira: KT-10323
thumbnail: 342533.jpeg
exl-id: 30574cc5-66fa-4ab8-83ed-7af710294dbf
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Laden Sie Ihre Kundendaten auf, um elektrisierende Erlebnisse bereitzustellen

Omni-Channel-Daten sind eine wichtige Komponente für umsetzbare Kundenprofile, die von Marketing-Experten verwendet werden, um die Aktivierung zu orchestrieren und die resultierenden Kunden-Journey zu messen. Unternehmen stehen jedoch vor der Herausforderung, die Qualität, den Umfang und die Vielfalt dieser Daten zu verwalten. Sie erfordern optimierte Lösungen, um die Auswirkungen qualitativ minderwertiger Daten zu minimieren, die Time-to-Value zu verkürzen und den ROI zu vervielfachen, indem dieselben Daten für eine Vielzahl von Anwendungsfällen verwendet werden.
Weitere Informationen finden Sie in der [Dokumentation zum Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de).

In diesem Video wird Folgendes untersucht:

* Adobe Experience Platform-Datenvorbereitungsfunktionen, die Sie nutzen können
* Steigern des ROI von Adobe Real-Time CDP, Adobe Journey Optimizer und Customer Journey Analytics

>[!VIDEO](https://video.tv.adobe.com/v/3454955?learn=on&enablevpops&captions=ger)

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

>[!NOTE]
>
>Dieses Video ist ein Auszug aus der Adobe Summit 2020-Sitzung *[Aufladen von Omnichannel-Daten zur Elektrifizierung von Erlebnissen](https://business.adobe.com/summit/2022/sessions/recharging-omnichannel-data-for-electrifying-exper-s409.html)*.
