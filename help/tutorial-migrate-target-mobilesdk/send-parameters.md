---
title: Parameter senden - Migration von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie mit dem Experience Platform Web SDK Mbox-, Profil- und Entitätsparameter an Adobe Target senden.
source-git-commit: 009548969b88d1bfa6eac23f65b1ca2144f27c34
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# Senden von Parametern an Target mithilfe des Platform Web SDK

Target-Implementierungen unterscheiden sich je nach Website-Architektur, Geschäftsanforderungen und verwendeten Funktionen. Die meisten Target-Implementierungen umfassen die Übergabe verschiedener Parameter für Kontextinformationen, Zielgruppen und Inhaltsempfehlungen.

Verwenden wir eine einfache Produktdetailseite und eine Bestellbestätigungsseite, um die Unterschiede zwischen den Erweiterungen bei der Übergabe von Parametern an Target zu demonstrieren.


| Beispiel für einen at.js-Parameter | Platform Web SDK-Option | Anmerkungen |
| --- | --- | --- |
| `at_property` | K. A. | Eigenschafts-Token werden im [Datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) konfiguriert und können nicht im `sendEvent` -Aufruf festgelegt werden. |
| `pageName` | `xdm.web.webPageDetails.name` | Alle Target-Mbox-Parameter müssen als Teil des `xdm` -Objekts übergeben und mit der XDM ExperienceEvent-Klasse einem Schema entsprechen. Mbox-Parameter können nicht als Teil des `data` -Objekts übergeben werden. |
| `profile.gender` | `data.__adobe.target.profile.gender` | Alle Target-Profilparameter müssen als Teil des `data` -Objekts übergeben und mit dem Präfix `profile.` versehen werden, damit sie korrekt zugeordnet werden können. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Reservierter Parameter, der für die Kategorieaffinitätsfunktion von Target verwendet wird und als Teil des Objekts `data` übergeben werden muss. |
| `entity.id` | `data.__adobe.target.entity.id` <br>ODER<br> `xdm.productListItems[0].SKU` | Entitäts-IDs werden für Target Recommendations-Verhaltenszähler verwendet. Diese Entitäts-IDs können entweder als Teil des `data` -Objekts übergeben oder automatisch vom ersten Element im `xdm.productListItems` -Array zugeordnet werden, wenn Ihre Implementierung diese Feldergruppe verwendet. |
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | Entitätskategorie-IDs können als Teil des `data` -Objekts übergeben werden. |
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | Benutzerdefinierte Entitätsparameter werden zum Aktualisieren des Recommendations-Produktkatalogs verwendet. Diese benutzerdefinierten Parameter müssen als Teil des `data` -Objekts übergeben werden. |
| `cartIds` | `data.__adobe.target.cartIds` | Wird für die auf dem Warenkorb basierenden Empfehlungsalgorithmen von Target verwendet. |
| `excludedIds` | `data.__adobe.target.excludedIds` | Wird verwendet, um zu verhindern, dass bestimmte Entitäts-IDs in einem Empfehlungsentwurf zurückgegeben werden. |
| `mbox3rdPartyId` | Im `xdm.identityMap` -Objekt festlegen | Wird zum Synchronisieren von Target-Profilen über Geräte und Kundenattribute hinweg verwendet. Der Namespace, der für die Kunden-ID verwendet werden soll, muss in der [Target-Konfiguration des Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid.html) angegeben werden. |
| `orderId` | `xdm.commerce.order.purchaseID` | Wird zur Identifizierung einer eindeutigen Bestellung für das Target-Konversions-Tracking verwendet. |
| `orderTotal` | `xdm.commerce.order.priceTotal` | Wird zur Verfolgung von Bestellsummen für Target-Konversions- und Optimierungsziele verwendet. |
| `productPurchasedId` | `data.__adobe.target.productPurchasedId` <br>ODER<br> `xdm.productListItems[0-n].SKU` | Wird für Target-Konversions-Tracking und Empfehlungsalgorithmen verwendet. Weitere Informationen finden Sie im Abschnitt [Entitätsparameter](#entity-parameters) unten. |
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Wird für das Aktivitätsziel [benutzerdefiniertes Scoring](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) verwendet. |

{style="table-layout:auto"}

## Benutzerdefinierte Parameter

Benutzerdefinierte Mbox-Parameter müssen als XDM oder mithilfe des Datenobjekts mit dem Befehl `sendEvent` übergeben werden. Es ist wichtig sicherzustellen, dass das XDM-Schema alle Felder enthält, die für Ihre Target-Implementierung erforderlich sind.


## Profilparameter

Target-Profilparameter müssen übergeben werden...

## Entitätsparameter

Entitätsparameter werden verwendet, um Verhaltensdaten und zusätzliche Kataloginformationen für Target Recommendations zu übergeben. Alle von at.js unterstützten [Entitätsparameter](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html) werden ebenfalls vom Platform Web SDK unterstützt. Ähnlich wie Profilparameter sollten alle Entitätsparameter unter dem Objekt `data.__adobe.target` in der Befehlsnutzlast des Platform Web SDK `sendEvent` übergeben werden.

Entitätsparameter für ein bestimmtes Element müssen mit dem Präfix &quot;`entity.`&quot;versehen werden, um eine korrekte Datenerfassung zu ermöglichen. Die reservierten Parameter `cartIds` und `excludedIds` für Empfehlungsalgorithmen dürfen nicht mit dem Präfix versehen werden und der Wert für jede Variable muss eine kommagetrennte Liste von Entitäts-IDs enthalten.



## Kaufparameter

Kaufparameter werden nach einer erfolgreichen Bestellung auf einer Bestellbestätigungsseite übergeben und für Target-Konversions- und Optimierungsziele verwendet. Bei einer Platform Mobile SDK-Implementierung mit der Optimize-Erweiterung werden diese Parameter und automatisch aus XDM-Daten zugeordnet, die als Teil der `commerce` -Feldergruppe übergeben werden.


Kaufinformationen werden an Target übergeben, wenn für die Feldergruppe `commerce` der Wert `purchases.value` auf `1` festgelegt ist. Die Bestell-ID und die Bestellsumme werden automatisch vom `order` -Objekt zugeordnet. Wenn das Array `productListItems` vorhanden ist, werden die Werte `SKU` für `productPurchasedId` verwendet.


## Kunden-ID (mbox3rdPartyId)

Target ermöglicht die Profilsynchronisierung über Geräte und Systeme hinweg mithilfe einer einzelnen Kunden-ID.



Als Nächstes erfahren Sie, wie Sie mit dem Platform Web SDK [Target-Konversionsereignisse verfolgen](track-events.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Optimierungserweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
