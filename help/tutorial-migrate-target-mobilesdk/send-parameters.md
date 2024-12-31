---
title: Versandparameter - Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie, wie Sie Mbox-, Profil- und Entitätsparameter mithilfe von Experience Platform Web SDK an Adobe Target senden.
exl-id: 927d83f9-c019-4a6b-abef-21054ce0991b
source-git-commit: 348554b5a2d43d7a882e8259b39a57af13d41ff4
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Senden von Parametern an Target mithilfe der Adobe Journey Optimizer - Decisioning Mobile-Erweiterung

Target-Implementierungen unterscheiden sich je nach Website-Architektur, Geschäftsanforderungen und verwendeten Funktionen je nach Website. Bei den meisten Target-Implementierungen werden verschiedene Parameter für Kontextinformationen, Zielgruppen und Inhaltsempfehlungen übergeben.

Anhand einer einfachen Produktdetailseite und einer Bestellbestätigungsseite möchten wir die Unterschiede zwischen den Erweiterungen beim Übergeben von Parametern an Target demonstrieren.


| Beispiel für den Parameter „at.js“ | Platform Web SDK-Option | Anmerkungen |
| --- | --- | --- |
| `at_property` | K. A. | Eigenschafts-Token sind im [Datenstrom](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) konfiguriert und können im `sendEvent` nicht festgelegt werden. |
| `pageName` | `xdm.web.webPageDetails.name` | Alle Ziel-Mbox-Parameter müssen als Teil des `xdm` übergeben werden und einem Schema mit der XDM ExperienceEvent-Klasse entsprechen. Mbox-Parameter können nicht als Teil des `data` übergeben werden. |
| `profile.gender` | `data.__adobe.target.profile.gender` | Alle Zielprofilparameter müssen als Teil des `data` übergeben werden und das Präfix `profile.` aufweisen, damit sie entsprechend zugeordnet werden können. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Reservierter Parameter, der für die Zielkategorie-Affinitätsfunktion verwendet wird und als Teil des `data` übergeben werden muss. |
| `entity.id` | `data.__adobe.target.entity.id` <br>ODER<br> `xdm.productListItems[0].SKU` | Entitäts-IDs werden für Target Recommendations-Verhaltenszähler verwendet. Diese Entitäts-IDs können entweder als Teil des `data`-Objekts übergeben oder automatisch vom ersten Element im `xdm.productListItems`-Array zugeordnet werden, wenn Ihre Implementierung diese Feldergruppe verwendet. |
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | Entitätskategorie-IDs können als Teil des `data` übergeben werden. |
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | Benutzerdefinierte Entitätsparameter werden zum Aktualisieren des Recommendations-Produktkatalogs verwendet. Diese benutzerdefinierten Parameter müssen als Teil des `data` übergeben werden. |
| `cartIds` | `data.__adobe.target.cartIds` | Wird für die Warenkorb-basierten Empfehlungsalgorithmen von Target verwendet. |
| `excludedIds` | `data.__adobe.target.excludedIds` | Wird verwendet, um zu verhindern, dass bestimmte Entitäts-IDs in einem Recommendations-Design zurückgegeben werden. |
| `mbox3rdPartyId` | Wird im `xdm.identityMap` festgelegt | Wird zum Synchronisieren von Target-Profilen über Geräte und Kundenattribute hinweg verwendet. Der für die Kunden-ID zu verwendende Namespace muss in der [Target-Konfiguration des Datenstroms“ angegeben ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid.html). |
| `orderId` | `xdm.commerce.order.purchaseID` | Wird zur Identifizierung einer eindeutigen Reihenfolge für das Target-Konversions-Tracking verwendet. |
| `orderTotal` | `xdm.commerce.order.priceTotal` | Wird zum Tracking der Bestellsummen für Konversions- und Optimierungsziele von Target verwendet. |
| `productPurchasedId` | `data.__adobe.target.productPurchasedId` <br>ODER<br> `xdm.productListItems[0-n].SKU` | Wird für Target-Konversionsverfolgungs- und Recommendations-Algorithmen verwendet. Weitere Informationen finden Sie [ Abschnitt ](#entity-parameters)Entitätsparameter“. |
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Wird für das Aktivitätsziel [benutzerdefinierte Bewertung](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) verwendet. |

{style="table-layout:auto"}

## Benutzerdefinierte Parameter

Benutzerdefinierte Mbox-Parameter müssen als XDM oder mithilfe des Datenobjekts mit dem `sendEvent`-Befehl übergeben werden. Es ist wichtig sicherzustellen, dass das XDM-Schema alle Felder enthält, die für Ihre Target-Implementierung erforderlich sind.


## Profilparameter

Zielprofilparameter müssen übergeben werden…

## Entitätsparameter

Entitätsparameter werden verwendet, um Verhaltensdaten und zusätzliche Kataloginformationen für Target Recommendations zu übergeben. Alle [Entitätsparameter](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html) die von at.js unterstützt werden, werden auch von Platform Web SDK unterstützt. Ähnlich wie Profilparameter sollten alle Entitätsparameter unter dem `data.__adobe.target`-Objekt in der Payload des Platform Web SDK `sendEvent`-Befehls übergeben werden.

Entitätsparameter für ein bestimmtes Element müssen mit dem Präfix `entity.` versehen werden, um eine ordnungsgemäße Datenerfassung zu gewährleisten. Die reservierten `cartIds`- und `excludedIds`-Parameter für Recommendations-Algorithmen sollten nicht mit einem Präfix versehen werden und der Wert für jedes muss eine kommagetrennte Liste von Entitäts-IDs enthalten.



## Kaufparameter

Kaufparameter werden nach erfolgreicher Bestellung auf einer Auftragsbestätigungsseite weitergeleitet und für Konversions- und Optimierungsziele von Target verwendet. Bei einer Implementierung von Platform Mobile SDK unter Verwendung der Decisioning-Erweiterung werden diese Parameter und automatisch aus XDM-Daten zugeordnet, die als Teil der `commerce` Feldergruppe übergeben werden.


Kaufinformationen werden an Target übergeben, wenn die `commerce` Feldergruppe auf `1` gesetzt `purchases.value`. Die Auftrags-ID und die Bestellsumme werden automatisch aus dem `order` Objekt zugeordnet. Wenn das `productListItems`-Array vorhanden ist, werden die `SKU` Werte für die `productPurchasedId` verwendet.


## Kunden-ID (mbox3rdPartyId)

Target ermöglicht die Synchronisierung von Profilen über Geräte und Systeme hinweg mithilfe einer einzigen Kunden-ID.



Erfahren Sie als Nächstes, wie Sie [Target-Konversionsereignisse ](track-events.md) Platform Web SDK verfolgen.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
