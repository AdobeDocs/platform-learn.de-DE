---
title: Sendeparameter - Migrieren der Adobe Target-Implementierung in Ihrer Mobile App zur Adobe Journey Optimizer - Decisioning-Erweiterung
description: Erfahren Sie, wie Sie Mbox-, Profil- und Entitätsparameter mithilfe von Experience Platform Web SDK an Adobe Target senden.
exl-id: 927d83f9-c019-4a6b-abef-21054ce0991b
source-git-commit: 2ebad2014d4c29a50af82328735258958893b42c
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 1%

---

# Senden von Parametern an Target mithilfe der Decisioning-Erweiterung

Target-Implementierungen unterscheiden sich je nach Mobile App-Architektur, Geschäftsanforderungen und verwendeten Funktionen. Bei den meisten Target-Implementierungen werden verschiedene Parameter für Kontextinformationen, Zielgruppen und Inhaltsempfehlungen übergeben.

Bei der Target-Erweiterung wurden alle Target-Parameter mithilfe der `TargetParameters`-Funktion übergeben.

Mit der Decisioning-Erweiterung:

* Parameter, die für mehrere Adobe-Programme vorgesehen sind, können im XDM-Objekt übergeben werden
* Parameter, die nur für Target bestimmt sind, können im `data.__adobe.target` übergeben werden


>[!IMPORTANT]
>
> Mit der Decisioning-Erweiterung gelten Parameter, die in einer Anfrage gesendet werden, für alle Bereiche in der Anfrage. Wenn Sie für verschiedene Bereiche unterschiedliche Parameter festlegen müssen, müssen Sie zusätzliche Anfragen stellen.

## Benutzerdefinierte Parameter

Benutzerdefinierte Mbox-Parameter sind die einfachste Möglichkeit, Daten an Target zu übergeben, und können in den `xdm` oder `data.__adobe.target` Objekten übergeben werden.

## Profilparameter

Profilparameter speichern Daten für einen längeren Zeitraum im Zielprofil des Benutzers und müssen im `data.__adobe.target` Objekt übergeben werden.

## Entitätsparameter

[Entitätsparameter](https://experienceleague.adobe.com/en/docs/target/using/recommendations/entities/entity-attributes) werden verwendet, um Verhaltensdaten und zusätzliche Kataloginformationen für Target Recommendations zu übergeben. Ähnlich wie Profilparameter sollten die meisten Entitätsparameter unter dem `data.__adobe.target` Objekt übergeben werden. Die einzige Ausnahme ist, dass das `xdm.productListItems`-Array vorhanden ist, dann wird der erste `SKU` als `entity.id` verwendet.

Entitätsparameter für ein bestimmtes Element müssen mit dem Präfix `entity.` versehen werden, um eine ordnungsgemäße Datenerfassung zu gewährleisten. Die reservierten `cartIds`- und `excludedIds`-Parameter für Recommendations-Algorithmen sollten nicht mit einem Präfix versehen werden und der Wert für jedes muss eine kommagetrennte Liste von Entitäts-IDs enthalten.

## Kaufparameter

Kaufparameter werden nach erfolgreicher Bestellung auf einer Auftragsbestätigungsseite weitergeleitet und für Konversions- und Optimierungsziele von Target verwendet. Bei einer Implementierung von Platform Mobile SDK unter Verwendung der Decisioning-Erweiterung werden diese Parameter und automatisch aus XDM-Daten zugeordnet, die als Teil der `commerce` Feldergruppe übergeben werden.

Kaufinformationen werden an Target übergeben, wenn die `commerce` Feldergruppe auf `1` gesetzt `purchases.value`. Die Auftrags-ID und die Bestellsumme werden automatisch aus dem `order` Objekt zugeordnet. Wenn das `productListItems`-Array vorhanden ist, werden die `SKU` Werte für die `productPurchasedId` verwendet.

Wenn Sie keine `commerce` Felder im `xdm` Objekt übergeben, können Sie die Bestelldetails mithilfe der Felder `data.__adobe.target.orderId`, `data.__adobe.target.orderTotal` und `data.__adobe.target.productPurchasedId` an Target übergeben.

## Kunden-ID (mbox3rdPartyId)

Target ermöglicht die Synchronisierung von Profilen über Geräte und Systeme hinweg mithilfe einer einzigen Kunden-ID. Diese Kunden-ID sollte im `identityMap` Feld des XDM-Objekts übergeben und dem Feld „Target Third-Party-ID“ im Datenstrom zugeordnet werden.

## Tabelle

| Beispiel für den Parameter „at.js“ | Platform Web SDK-Option | Anmerkungen |
| --- | --- | --- |
| `at_property` | K. A. | Eigenschafts-Token sind im [Datenstrom](https://experienceleague.adobe.com/en/docs/experience-platform/edge/datastreams/configure#target) konfiguriert und können im `sendEvent` nicht festgelegt werden. |
| `pageName` | `xdm.web.webPageDetails.name` oder <br> `data.__adobe.target.pageName` | Mbox-Zielparameter können entweder als Teil des `xdm` oder als Teil des `data.__adobe.target` übergeben werden. |
| `profile.gender` | `data.__adobe.target.profile.gender` | Alle Zielprofilparameter müssen als Teil des `data` übergeben werden und das Präfix `profile.` aufweisen, damit sie entsprechend zugeordnet werden können. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Reservierter Parameter, der für die Zielkategorie-Affinitätsfunktion verwendet wird und als Teil des `data` übergeben werden muss. |
| `entity.id` | `data.__adobe.target.entity.id` <br>ODER<br> `xdm.productListItems[0].SKU` | Entitäts-IDs werden für Target Recommendations-Verhaltenszähler verwendet. Diese Entitäts-IDs können entweder als Teil des `data`-Objekts übergeben oder automatisch vom ersten Element im `xdm.productListItems`-Array zugeordnet werden, wenn Ihre Implementierung diese Feldergruppe verwendet. |
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | Entitätskategorie-IDs können als Teil des `data` übergeben werden. |
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | Benutzerdefinierte Entitätsparameter werden zum Aktualisieren des Recommendations-Produktkatalogs verwendet. Diese benutzerdefinierten Parameter müssen als Teil des `data` übergeben werden. |
| `cartIds` | `data.__adobe.target.cartIds` | Wird für die Warenkorb-basierten Empfehlungsalgorithmen von Target verwendet. |
| `excludedIds` | `data.__adobe.target.excludedIds` | Wird verwendet, um zu verhindern, dass bestimmte Entitäts-IDs in einem Recommendations-Design zurückgegeben werden. |
| `mbox3rdPartyId` | Wird im `xdm.identityMap` festgelegt | Wird zum Synchronisieren von Target-Profilen über Geräte und Kundenattribute hinweg verwendet. Der für die Kunden-ID zu verwendende Namespace muss in der [Target-Konfiguration des Datenstroms“ angegeben ](https://experienceleague.adobe.com/en/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid). |
| `orderId` | `xdm.commerce.order.purchaseID`<br> (wenn `commerce.purchases.value` auf `1` gesetzt ist)<br> oder<br> `data.__adobe.target.orderId` | Wird zur Identifizierung einer eindeutigen Reihenfolge für das Target-Konversions-Tracking verwendet. |
| `orderTotal` | `xdm.commerce.order.priceTotal`<br> (wenn `commerce.purchases.value` auf `1` gesetzt ist)<br> oder<br> `data.__adobe.target.orderTotal` | Wird zum Tracking der Bestellsummen für Konversions- und Optimierungsziele von Target verwendet. |
| `productPurchasedId` | `xdm.productListItems[0-n].SKU`<br> (wenn `commerce.purchases.value` auf `1` gesetzt ist) <br>ODER<br> `data.__adobe.target.productPurchasedId` | Wird für Target-Konversionsverfolgungs- und Recommendations-Algorithmen verwendet. |
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Wird für das Aktivitätsziel [benutzerdefinierte Bewertung](https://experienceleague.adobe.com/en/docs/target/using/activities/success-metrics/capture-score) verwendet. |

{style="table-layout:auto"}


## Beispiele für die Übergabe von Parametern

Verwenden wir ein einfaches Beispiel, um die Unterschiede zwischen den Erweiterungen beim Übergeben von Parametern an Target zu veranschaulichen.

### Android

>[!BEGINTABS]

>[!TAB SDK optimieren]

```Java
final Map<String, Object> data = new HashMap<>();
final Map<String, String> targetParameters = new HashMap<>();
 
// Mbox parameters
targetParameters.put("status", "platinum");
 
// Profile parameters - prefix with profile.
targetParameters.put("profile.gender", "male");
 
// Product parameters
targetParameters.put("productId", "pId1");
targetParameters.put("categoryId", "cId1");
 
// Order parameters
targetParameters.put("orderId", "id1");
targetParameters.put("orderTotal", "1.0");
targetParameters.put("purchasedProductIds", "ppId1");
 
data.put("__adobe", new HashMap<String, Object>() {
  {
    put("target", targetParameters);
  }
});
 
// Target location (or mbox)
final DecisionScope decisionScope = DecisionScope("myTargetLocation")
 
final List<DecisionScope> decisionScopes = new ArrayList<>();
decisionScopes.add(decisionScope);
 
Optimize.updatePropositions(decisionScopes, null, data);
```

>[!TAB Target SDK]

```Java
Map<String, String> mboxParameters = new HashMap<String, String>();
mboxParameters1.put("status", "platinum");
 
Map<String, String> profileParameters = new HashMap<String, String>();
profileParameters1.put("gender", "male");
 
List<String> purchasedProductIds = new ArrayList<String>();
purchasedProductIds.add("ppId1");
TargetOrder targetOrder = new TargetOrder("id1", 1.0, purchasedProductIds);
 
TargetProduct targetProduct = new TargetProduct("pId1", "cId1");
 
TargetParameters targetParameters = new TargetParameters.Builder()
                                    .parameters(mboxParameters)
                                    .profileParameters(profileParameters)
                                    .product(targetProduct)
                                    .order(targetOrder)
                                    .build();
```

>[!ENDTABS]

### iOS

>[!BEGINTABS]

>[!TAB SDK optimieren]

```Swift
var data: [String: Any] = [:]
var targetParameters: [String: String] = [:]
 
// Mbox parameters
targetParameters["status"] = "platinum"
 
// Profile parameters - prefix with profile.
targetParameters["profile.gender"] = "make"
 
// Product parameters
targetParameters["productId"] = "pId1"
targetParameters["categoryId"] = "cId1"
 
// Add order parameters
targetParameters["orderId"] = "id1"
targetParameters["orderTotal"] = "1.0"
targetParameters["purchasedProductIds"] = "ppId1"
 
data["__adobe"] = [
  "target": targetParameters
]
 
// Target location (or mbox)
let decisionScope = DecisionScope(name: "myTargetLocation")
Optimize.updatePropositions(for: [decisionScope] withXdm: nil andData: data)
```

>[!TAB Target SDK]

```Swift
let mboxParameters = [
                        "status": "platinum"
                     ]
 
let profileParameters = [
                            "gender": "male"
                        ]
 
let order = TargetOrder(id: "id1", total: 1.0, purchasedProductIds: ["ppId1"])
 
let product = TargetProduct(productId: "pId1", categoryId: "cId1")
 
let targetParameters = TargetParameters(parameters: mboxParameters, profileParameters: profileParameters, order: order, product: product))
```


>[!ENDTABS]






Erfahren Sie als Nächstes, wie Sie [Target-Konversionsereignisse ](track-events.md) Platform Web SDK verfolgen.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625) posten.
