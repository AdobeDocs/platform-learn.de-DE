---
title: Events
description: Erfahren Sie, wie Sie Ereignisdaten in einer Mobile App erfassen.
exl-id: 4779cf80-c143-437b-8819-1ebc11a26852
source-git-commit: bc53cb5926f708408a42aa98a1d364c5125cb36d
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 1%

---

# Events

Erfahren Sie, wie Sie Ereignisse in einer Mobile App verfolgen.

>[!INFO]
>
> Dieses Tutorial wird Ende November 2023 mithilfe einer neuen Beispiel-Mobile-App durch ein neues Tutorial ersetzt.

Die Edge Network-Erweiterung stellt eine API zum Senden von Erlebnisereignissen an Platform Edge Network bereit. Ein Erlebnisereignis ist ein Objekt, das Daten enthält, die der XDM ExperienceEvent-Schemadefinition entsprechen. Sie erfassen einfach, was Benutzer in Ihrer mobilen App tun. Sobald Daten vom Platform Edge Network empfangen wurden, können sie an Anwendungen und Dienste weitergeleitet werden, die in Ihrem Datenspeicher konfiguriert sind, z. B. Adobe Analytics und Experience Platform. Weitere Informationen zum [Erlebnisereignisse](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) in der Produktdokumentation.

## Voraussetzungen

* PodFile mit den erforderlichen SDKs aktualisiert.
* Registrierte Erweiterungen in AppDelegate.
* MobileCore für die Verwendung Ihrer Entwicklungs-AppId konfiguriert.
* Importierte SDKs
* App wurde erfolgreich erstellt und mit den oben genannten Änderungen ausgeführt.

## Lernziele

In dieser Lektion werden Sie:

* Erfahren Sie, wie Sie XDM-Daten basierend auf einem Schema strukturieren.
* Senden Sie ein XDM-Ereignis basierend auf einer Standardfeldgruppe.
* Senden Sie ein XDM-Ereignis basierend auf einer benutzerdefinierten Feldergruppe.
* Senden Sie ein XDM-Kaufereignis.
* Validieren mit Assurance.

## Erstellen eines Erlebnisereignisses

Die Adobe Experience Platform Edge-Erweiterung kann Ereignisse senden, die einem zuvor definierten XDM-Schema folgen, an Adobe Experience Platform Edge Network.

Der Prozess läuft so ab...

1. Identifizieren Sie die Mobile App-Interaktion, die Sie verfolgen möchten.

1. Überprüfen Sie Ihr Schema und identifizieren Sie das entsprechende Ereignis.

1. Überprüfen Sie Ihr Schema und identifizieren Sie alle zusätzlichen Felder, die zur Beschreibung des Ereignisses verwendet werden sollen.

1. Erstellen und füllen Sie das Datenobjekt.

1. Ereignis erstellen und senden.

1. Überprüfen.

Sehen wir uns ein paar Beispiele an.

### Beispiel 1: Standardfeldgruppen

Überprüfen Sie das folgende Beispiel, ohne zu versuchen, es in die Beispielanwendung zu implementieren:

1. Identifizieren Sie in Ihrem Schema das Ereignis, das Sie erfassen möchten. In diesem Beispiel verfolgen wir eine Produktansicht.
   ![Produktansichtsschema](assets/mobile-datacollection-prodView-schema.png)

1. Beginnen Sie mit der Erstellung Ihres -Objekts:

   ```swift
   var xdmData: [String: Any] = [
       "eventType": "commerce.productViews",
       "commerce": [
           "productViews": [
           "value": 1
           ]
       ]
   ]
   ```

   * eventType: Beschreibt das aufgetretene Ereignis und verwendet eine [bekannter Wert](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values) nach Möglichkeit.
   * commerce.productViews.value: Geben Sie den numerischen Wert des Ereignisses an. Wenn es sich um einen booleschen Wert (oder &quot;Zähler&quot;in Adobe Analytics) handelt, ist der Wert immer 1. Bei numerischen Ereignissen oder Währungsereignissen kann der Wert > 1 betragen.

1. Identifizieren Sie in Ihrem Schema alle zusätzlichen Daten, die mit dem Ereignis verknüpft sind. Fügen Sie in diesem Beispiel `productListItems` Dies ist ein Standardsatz von Feldern, die mit Commerce-bezogenen Ereignissen verwendet werden:
   ![Schema der Produktlistenelemente](assets/mobile-datacollection-prodListItems-schema.png)
   * Beachten Sie Folgendes: `productListItems` ist ein Array, sodass mehrere Produkte bereitgestellt werden können.

1. Erweitern Sie Ihr xdmData -Objekt, um zusätzliche Daten einzuschließen:

   ```swift
   var xdmData: [String: Any] = [
       "eventType": "commerce.productViews",
           "commerce": [
           "productViews": [
               "value": 1
           ]
       ],
       "productListItems": [
           [
               "name":  productName,
               "SKU": sku,
               "priceTotal": priceString,
               "quantity": 1
           ]
       ]
   ]
   ```

1. Verwenden Sie die Datenstruktur, um eine `ExperienceEvent`:

   ```swift
   let productViewEvent = ExperienceEvent(xdm: xdmData)
   ```

1. Senden Sie das Ereignis und die Daten an das Platform Edge Network:

   ```swift
   Edge.sendEvent(experienceEvent: productViewEvent)
   ```

### Beispiel 2: Benutzerdefinierte Feldergruppen

Überprüfen Sie das folgende Beispiel, ohne zu versuchen, es in die Beispielanwendung zu implementieren:

1. Identifizieren Sie in Ihrem Schema das Ereignis, das Sie erfassen möchten. In diesem Beispiel verfolgen Sie eine &quot;App-Interaktion&quot;, die aus einem App-Aktionsereignis und -Namen besteht.
   ![App-Interaktionsschema](assets/mobile-datacollection-appInteraction-schema.png)

1. Beginnen Sie mit der Erstellung Ihres Objekts.

   >[!NOTE]
   >
   >  Standardfeldgruppen beginnen immer im Objektstamm.
   >
   >  Benutzerdefinierte Feldergruppen beginnen immer unter einem Objekt, das für Ihre Experience Cloud-Organisation eindeutig ist, in diesem Beispiel &quot;_techmarketingdemos&quot;.

   ```swift
   var xdmData: [String: Any] = [
   "_techmarketingdemos": [
       "appInformation": [
           "appInteraction": [
               "name": actionName,
               "appAction": [
                   "value": 1
                   ]
               ]
           ]
       ]
   ]
   ```

   Oder alternativ ...

   ```swift
   var xdmData: [String: Any] = [:]
   xdmData["_techmarketingdemos"] = [
       "appInformation": [
           "appInteraction": [
               "name": actionName,
               "appAction": [
                   "value": 1
               ]
           ]
       ]
   ]
   ```

1. Verwenden Sie die Datenstruktur, um eine `ExperienceEvent`.

   ```swift
   let appInteractionEvent = ExperienceEvent(xdm: xdmData)
   ```

1. Senden Sie das Ereignis und die Daten an Platform Edge Network.

   ```swift
   Edge.sendEvent(experienceEvent: appInteractionEvent)
   ```

### Hinzufügen des Bildschirmansichts-Trackings zur Luma-App

Die obigen Beispiele haben hoffentlich den Gedankenprozess beim Erstellen eines XDM-Datenobjekts erläutert. Als Nächstes fügen wir das Tracking der Bildschirmansichten in der Luma-App hinzu.

1. Navigieren Sie zu `Home.swift`.
1. Fügen Sie den folgenden Code zu `viewDidAppear(...)` hinzu.

   ```swift
           let stateName = "luma: content: ios: us: en: home"
           var xdmData: [String: Any] = [:]
           //Page View
           xdmData["_techmarketingdemos"] = [
               "appInformation": [
                   "appStateDetails": [
                       "screenType": "App",
                       "screenName": stateName,
                       "screenView": [
                           "value": 1
                       ]
                   ]
               ]
           ]
           let experienceEvent = ExperienceEvent(xdm: xdmData)
           Edge.sendEvent(experienceEvent: experienceEvent)
   ```

1. Wiederholen Sie diese Schritte für jeden Bildschirm im Programm und aktualisieren Sie `stateName` wie du gehst.



### Validierung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) und verbinden Sie Ihren Simulator oder Ihr Gerät mit Assurance.
1. Führen Sie die Aktion aus und suchen Sie nach der `hitReceived` -Ereignis aus `com.adobe.edge.konductor` -Anbieter.
1. Wählen Sie das Ereignis aus und überprüfen Sie die XDM-Daten im `messages` -Objekt.
   ![Datenerfassungsprüfung](assets/mobile-datacollection-validation.png)

### Beispiel 3: Kauf

In diesem Beispiel wird davon ausgegangen, dass der Benutzer den folgenden Kauf erfolgreich getätigt hat:

* Produkt Nr. 1 - Yoga Mat.
   * $ 49.99 x1
   * SKU: 5829
* Produkt Nr. 2 - Wasserflasche
   * $10.00 x3
   * SKU: 9841
* Bestellsumme: 79,99 USD
* Eindeutige Bestell-ID: 298234720
* Zahlungsart: Visa-Kreditkarte
* Unique Payment Transaction Id: 847361

#### Schema

Im Folgenden finden Sie die zu verwendenden Schemafelder:

* eventType: &quot;commerce.purchases&quot;
* commerce.purchases
* commerce.order
* productsListItems
* _techmarketingdemos.appStateDetails (benutzerdefiniert)

>[!TIP]
>
>Benutzerdefinierte Feldergruppen werden immer unter Ihrer Experience Cloud-Organisationskennung platziert.
>
>&quot;_techmarketingdemos&quot;wird durch den eindeutigen Wert Ihrer Organisation ersetzt.

![Kaufschema](assets/mobile-datacollection-purchase-schema.png)


#### Code

So erstellen und senden Sie das XDM-Objekt in der App.

```swift
let stateName = "luma: content: ios: us: en: orderconfirmation"
let currencyCode = "USD"
let orderTotal = "79.99"
let paymentType = "Visa Credit Card"
let orderId = "298234720"
let paymentTransactionId = "847361"
var xdmData: [String: Any] = [
  "eventType": "commerce.purchases",
  "commerce": [
    "purchases": [
      "value": 1
    ],
    "order": [
      "currencyCode": currencyCode,
      "priceTotal": orderTotal,
      "purchaseID": orderId,
      "purchaseOrderNumber": orderId,
      "payments": [ //Assuming only 1 payment type is used
        [
          "currencyCode": currencyCode,
          "paymentAmount": orderTotal,
          "paymentType": paymentType,
          "transactionID": paymentTransactionId
        ]
      ]
    ]
  ],
  "productListItems": [
      [
          "name":  "Yoga Mat",
          "SKU": "5829",
          "priceTotal": "49.99",
          "quantity": 1
      ],
      [
        "name":  "Water Bottle",
        "SKU": "9841",
        "priceTotal": "30.00",
        "quantity": 3
      ]
  ]
]

//Custom field group
xdmData["_techmarketingdemos"] = [
  "appInformation": [
    "appStateDetails": [
      "screenType": "App",
      "screenName": stateName,
      "screenView": [
        "value": 1
      ]
    ]
  ]
]
let experienceEvent = ExperienceEvent(xdm: xdmData)
Edge.sendEvent(experienceEvent: experienceEvent)
```

>[!NOTE]
>
>Aus Gründen der Klarheit sind alle Werte hartcodiert. In einer realen Situation würden die Werte dynamisch ausgefüllt.


### Implementieren in die Luma-App

Sie sollten über alle Tools verfügen, um mit dem Hinzufügen der Datenerfassung zur Beispielanwendung &quot;Luma&quot;zu beginnen. Im Folgenden finden Sie eine Liste der hypothetischen Tracking-Anforderungen, die Sie erfüllen können.

* Verfolgen Sie die einzelnen Bildschirmansichten.
   * Schemafelder: screenType, screenName, screenView
* Verfolgen Sie nicht kommerzielle Aktionen.
   * Schemafelder: appInteraction.name, appAction
* Commerce-Aktionen:
   * Produktseite: productViews
   * Zum Warenkorb hinzufügen: productListAdds
   * Aus Warenkorb entfernen: productListRemovals
   * Checkout starten: Checkouts
   * Warenkorb anzeigen: productListViews
   * Zu Wunschliste hinzufügen: saveForLaters
   * Kauf: Einkäufe, Bestellung

>[!TIP]
>
>Überprüfen Sie die [voll implementierte App](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) für weitere Beispiele.

### Validierung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) und verbinden Sie Ihren Simulator oder Ihr Gerät mit Assurance.

1. Führen Sie die Aktion aus und suchen Sie nach der `hitReceived` -Ereignis aus `com.adobe.edge.konductor` -Anbieter.

1. Wählen Sie das Ereignis aus und überprüfen Sie die XDM-Daten im `messages` -Objekt.
   ![Datenerfassungsprüfung](assets/mobile-datacollection-validation.png)

## Senden von Ereignissen an Analytics und Platform

Nachdem Sie die Ereignisse erfasst und an das Platform Edge Network gesendet haben, werden sie an die in Ihrer [datastream](create-datastream.md). In späteren Lektionen ordnen Sie diese Daten zu [Adobe Analytics](analytics.md) und [Adobe Experience Platform](platform.md).

Weiter: **[WebViews](web-views.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)