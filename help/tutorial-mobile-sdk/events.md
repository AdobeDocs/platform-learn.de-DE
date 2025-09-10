---
title: Nachverfolgen von Ereignisdaten in Mobile Apps mit der Experience Platform Mobile SDK
description: Erfahren Sie, wie Sie Ereignisdaten in einer Mobile App verfolgen.
jira: KT-14631
exl-id: 4779cf80-c143-437b-8819-1ebc11a26852
source-git-commit: 7e7c7600457b361c2ba9616c067b9fe33fd70c5c
workflow-type: tm+mt
source-wordcount: '1678'
ht-degree: 2%

---

# Verfolgen von Ereignisdaten

Erfahren Sie, wie Sie Ereignisse in einer Mobile App verfolgen.

Die Edge Network-Erweiterung bietet eine API zum Senden von Erlebnisereignissen an Platform Edge Network. Ein Erlebnisereignis ist ein Objekt, das Daten enthält, die der Schemadefinition von XDM ExperienceEvent entsprechen. Einfach ausgedrückt, erfassen diese Ereignisse, was Menschen in Ihrer App tun. Nachdem Platform Edge Network Daten erhalten hat, können diese Daten an Programme und Services weitergeleitet werden, die in Ihrem Datenstrom konfiguriert sind, z. B. Adobe Analytics und Experience Platform. Weitere Informationen zu [Erlebnisereignissen](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) finden Sie in der Produktdokumentation.

## Voraussetzungen

* Alle Paketabhängigkeiten werden in Ihrem Xcode-Projekt konfiguriert.
* Registrierte Erweiterungen in **[!UICONTROL AppDelegate]**.
* MobileCore-Erweiterung zur Verwendung Ihrer `appId` konfiguriert.
* SDKs importiert.
* Die App mit den oben genannten Änderungen wurde erfolgreich erstellt und ausgeführt.

## Lernziele

In dieser Lektion werden Sie

* Erfahren Sie, wie Sie XDM-Daten basierend auf einem Schema strukturieren.
* Senden Sie ein XDM-Ereignis basierend auf einer Standardfeldgruppe.
* Senden Sie ein XDM-Ereignis basierend auf einer benutzerdefinierten Feldergruppe.
* Senden Sie ein XDM-Kaufereignis.
* Validieren mit Assurance.

## Erstellen eines Erlebnisereignisses

Die Adobe Experience Platform Edge-Erweiterung kann Ereignisse, die einem zuvor definierten XDM-Schema folgen, an Adobe Experience Platform Edge Network senden.

Der Prozess läuft so ab…

1. Identifizieren Sie die Mobile-App-Interaktion, die Sie verfolgen möchten.

1. Prüfen Sie Ihr Schema und ermitteln Sie das entsprechende Ereignis.

1. Prüfen Sie Ihr Schema und identifizieren Sie alle zusätzlichen Felder, die zur Beschreibung des Ereignisses verwendet werden sollten.

1. Erstellen und Auffüllen des Datenobjekts.

1. Ereignis erstellen und senden.

1. Validieren.


### Standardfeldgruppen

Für die Standardfeldgruppen sieht der Prozess wie folgt aus:

* Identifizieren Sie in Ihrem Schema die Ereignisse, die Sie erfassen möchten. In diesem Beispiel verfolgen Sie Commerce-Erlebnisereignisse, z. B. ein Produktansichtsereignis **[!UICONTROL productViews]**.

  ![Produktansichtsschema](assets/datacollection-prodView-schema.png){zoomable="yes"}

* Um ein -Objekt zu erstellen, das die Erlebnisereignisdaten in Ihrer App enthält, verwenden Sie Code wie den folgenden:

>[!BEGINTABS]

>[!TAB iOS]

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

In diesem Code:

* `eventType`: Beschreibt das aufgetretene Ereignis. Verwenden Sie nach Möglichkeit einen [bekannten ](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values)&quot;.

* `commerce.productViews.value`: Der numerische oder boolesche Wert des Ereignisses. Wenn es sich um einen booleschen Wert (oder „Zähler“ in Adobe Analytics) handelt, wird der Wert immer auf 1 festgelegt. Wenn es sich um ein numerisches oder ein Währungsereignis handelt, kann der Wert > 1 sein.

>[!TAB Android]

```kotlin
val xdmData = mapOf(
    "eventType" to "commerce.productViews",
    "commerce" to mapOf(
        "productViews" to mapOf(
        "value": 1
        )
    )
)
```

In diesem Code:

* `eventType`: Beschreibt das aufgetretene Ereignis. Verwenden Sie nach Möglichkeit einen [bekannten ](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values)&quot;.

* `commerce.productViews.value`: Der numerische oder boolesche Wert des Ereignisses. Wenn es sich um einen booleschen Wert (oder „Zähler“ in Adobe Analytics) handelt, wird der Wert immer auf 1 festgelegt. Wenn es sich um ein numerisches oder ein Währungsereignis handelt, kann der Wert > 1 sein.

>[!ENDTABS]


* Identifizieren Sie in Ihrem Schema alle zusätzlichen Daten, die mit dem Commerce-Produktansichtsereignis verknüpft sind. In diesem Beispiel schließen Sie **[!UICONTROL productListItems]** ein. Dies ist ein Standardsatz von Feldern, die mit jedem Commerce-bezogenen Ereignis verwendet werden:

  ![Schema für Produktlistenelemente](assets/datacollection-prodListItems-schema.png){zoomable="yes"}
   * Beachten Sie **[!UICONTROL dass „productListItems]** ein Array ist, sodass mehrere Produkte bereitgestellt werden können.

* Um diese Daten hinzuzufügen, erweitern Sie Ihr `xdmData`-Objekt, um zusätzliche Daten einzuschließen:

>[!BEGINTABS]

>[!TAB iOS]

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

>[!TAB Android]

```kotlin
val xdmData = mapOf(
    "eventType" to "commerce.productViews",
    "commerce" to mapOf(
        "productViews" to mapOf(
        "value": 1
        )
    ),
    "productListItems" to mapOf(
        "name": productName,
        "SKU": sku,
        "priceTotal", priceString,
        "quantity", 1
    )
)
```

>[!ENDTABS]

* Sie können jetzt diese Datenstruktur verwenden, um eine `ExperienceEvent` zu erstellen:

>[!BEGINTABS]

>[!TAB iOS]

```swift
let productViewEvent = ExperienceEvent(xdm: xdmData)
```

>[!TAB Android]

```kotlin
val productViewEvent = ExperienceEvent.Builder().setXdmSchema(xdmData).build()
```

>[!ENDTABS]

* und senden Sie das Ereignis und die Daten mithilfe der `sendEvent`-API an Platform Edge Network:

>[!BEGINTABS]

>[!TAB iOS]

```swift
Edge.sendEvent(experienceEvent: productViewEvent)
```

>[!TAB Android]

```kotlin
Edge.sendEvent(productViewEvent, null)
```

>[!ENDTABS]


Die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent)-API entspricht der AEP Mobile SDK den [`MobileCore.trackAction`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackaction)- und [`MobileCore.trackState`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackstate)-API-Aufrufen. Weitere [ finden Sie unter „Migrieren von der Analytics Mobile-Erweiterung ](https://developer.adobe.com/client-sdks/documentation/adobe-analytics/migrate-to-edge-network/) Adobe Experience Platform Edge Network&quot;.

Sie werden diesen Code jetzt in Ihrem Projekt implementieren.
Sie haben verschiedene Commerce-produktbezogene Aktionen in Ihrer App und möchten Ereignisse senden, die auf diesen Aktionen basieren und vom Benutzer ausgeführt werden:

* Ansicht: Tritt auf, wenn ein Benutzer ein bestimmtes Produkt anzeigt,
* Zum Warenkorb hinzufügen: Wenn ein Benutzer tippt <img src="assets/addtocart.png" width="20" /> in einem Produktdetailbildschirm,
* Für später speichern: Wenn ein Benutzer tippt <img src="assets/saveforlater.png" width="15" /> / <img src="assets/heart.png" width="25" /> in einem Produktdetailbildschirm,
* Kauf: Wenn ein Benutzer auf tippt In einem Produktdetailbildschirm <img src="assets/purchase.png" width="20" />.

Um den wiederverwendbaren Versand von Commerce-bezogenen Erlebnisereignissen zu implementieren, verwenden Sie eine dedizierte Funktion:

>[!BEGINTABS]

>[!TAB iOS]

1. Navigieren Sie im Xcode-Projekt-**[!DNL Luma]** zu **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL >]** MobileSDK) und fügen Sie Folgendes zur `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` hinzu.

   ```swift
   // Set up a data dictionary, create an experience event and send the event.
   let xdmData: [String: Any] = [
       "eventType": "commerce." + commerceEventType,
       "commerce": [
           commerceEventType: [
               "value": 1
           ]
       ],
       "productListItems": [
           [
               "name": product.name,
               "priceTotal": product.price,
               "SKU": product.sku
           ]
       ]
   ]
   
   let commerceExperienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: commerceExperienceEvent)
   ```

   Diese Funktion akzeptiert den Ereignistyp und das Produkt des Commerce-Erlebnisses als Parameter und

   * richtet die XDM-Payload mithilfe der Parameter aus der -Funktion als Wörterbuch ein,
   * ein Erlebnisereignis mithilfe des Wörterbuchs einrichtet,
   * sendet das Erlebnisereignis über die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent)-API.

1. Navigieren Sie im Xcode-Projekt-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!UICONTROL ProductView]** und fügen Sie verschiedene Aufrufe an die `sendCommerceExperienceEvent` Funktion hinzu:

   1. Am Modifikator `.task` innerhalb des `ATTrackingManager.trackingAuthorizationStatus`. Dieser `.task` wird aufgerufen, wenn die Produktansicht initialisiert und angezeigt wird. Daher möchten Sie zu diesem Zeitpunkt ein Produktansichtsereignis senden.

      ```swift
      // Send productViews commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productViews", product: product)
      ```

   1. Für jede Schaltfläche (<img src="assets/saveforlater.png" width="15" />, <img src="assets/addtocart.png" width="20" /> und <img src="assets/purchase.png" width="20" />) Fügen Sie in der Symbolleiste den entsprechenden Aufruf innerhalb des `ATTrackingManager.trackingAuthorizationStatus == .authorized` hinzu:

      1. für <img src="assets/saveforlater.png" width="15" />

         ```swift
         // Send saveForLater commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
         ```

      1. für <img src="assets/addtocart.png" width="20" />

         ```swift
         // Send productListAdds commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
         ```

      1. für <img src="assets/purchase.png" width="20" />

         ```swift
         // Send purchase commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
         ```

>[!TAB Android]

1. Navigieren Sie im Android Studio-Navigator zu **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]** und fügen Sie Folgendes zur `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` hinzu.

   ```kotlin
   // Set up a data map, create an experience event and send the event.
   val xdmData = mapOf(
       "eventType" to "commerce.$commerceEventType",
       "commerce" to mapOf(commerceEventType to mapOf("value" to 1)),
       "productListItems" to listOf(
           mapOf(
               "name" to product.name,
               "priceTotal" to product.price,
               "SKU" to product.sku
           )
       )
   )
   val commerceExperienceEvent = ExperienceEvent.Builder().setXdmSchema(xdmData).build()
   Edge.sendEvent(commerceExperienceEvent, null)
   ```

   Diese Funktion akzeptiert den Ereignistyp und das Produkt des Commerce-Erlebnisses als Parameter und

   * richtet die XDM-Payload mithilfe der Parameter aus der -Funktion als Zuordnung ein,
   * ein Erlebnisereignis mithilfe der Zuordnung einrichtet,
   * sendet das Erlebnisereignis über die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent)-API.

1. Android Navigieren Sie im **[!UICONTROL Studio-Navigator zu app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.]** > **[!UICONTROL views]** > **[!UICONTROL ProductView.kt]** und fügen Sie der `sendCommerceExperienceEvent` verschiedene Aufrufe hinzu:

   1. Bei der `LaunchedEffect(Unit)` zusammensetzbaren Funktion möchten Sie ein Produktansichtsereignis zum Zeitpunkt der Anzeige eines Produkts senden.

      ```kotlin
      // Send productViews commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent("productViews", product)
      ```

   1. Für jede Schaltfläche (<img src="assets/heart.png" width="25" />, <img src="assets/addtocart.png" width="20" /> und <img src="assets/purchase.png" width="20" />) Fügen Sie in der Symbolleiste den entsprechenden Aufruf im `scope.launch` des `if (MobileSDK.shared.trackingEnabled == TrackingStatus.AUTHORIZED)  statement` hinzu:

      1. für <img src="assets/heart.png" width="25" />

         ```kotlin
         // Send saveForLater commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent("saveForLaters", product)
         ```

      1. für <img src="assets/addtocart.png" width="20" />

         ```kotlin
         // Send productListAdds commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent("productListAdds", product)
         ```

      1. für <img src="assets/purchase.png" width="20" />

         ```kotlin
         // Send purchase commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent("purchases", product)
         ```

>[!ENDTABS]

>[!TIP]
>
>Wenn Sie eine Entwicklung für Android™ durchführen, verwenden Sie Map (`java.util.Map`) als grundlegende Schnittstelle zum Erstellen Ihrer XDM-Payload.


### Benutzerdefinierte Feldergruppen

Angenommen, Sie möchten Bildschirmansichten und Interaktionen in der App selbst verfolgen. Denken Sie daran, dass Sie eine benutzerdefinierte Feldergruppe für diesen Ereignistyp definiert haben.

* Identifizieren Sie in Ihrem Schema die Ereignisse, die Sie erfassen möchten.
  ![App-Interaktionsschema](assets/datacollection-appInteraction-schema.png){zoomable="yes"}

* Beginnen Sie mit dem Aufbau Ihres -Objekts.

  >[!NOTE]
  >
  >* Standardfeldgruppen beginnen immer im Objektstamm.
  >
  >* Benutzerdefinierte Feldergruppen beginnen immer unter einem Objekt, das für Ihre Experience Cloud-Organisation eindeutig ist, `_techmarketingdemos` in diesem Beispiel.

* Für das Ereignis „App Interaction“ würden Sie ein -Objekt wie das folgende erstellen:

>[!BEGINTABS]

>[!TAB iOS]

```swift
let xdmData: [String: Any] = [
    "eventType": "application.interaction",
    "_techmarketingdemos": [
    "appInformation": [
        "appInteraction": [
            "name": "login",
            "appAction": [
                "value": 1
                ]
            ]
        ]
    ]
]
```

>[!TAB Android]

```kotlin
val xdmData = mapOf(
    "eventType" to "application.interaction",
    "_techmarketingdemos" to mapOf(
        "appInformation" to mapOf(
            "appInteraction" to mapOf(
                "name" to "login",
                "appAction" to mapOf("value" to 1)
            )
        )
    )
)
```

>[!ENDTABS]

* Für das Bildschirm-Tracking-Ereignis würden Sie ein Objekt wie das folgende erstellen:

>[!BEGINTABS]

>[!TAB iOS]

```swift
var xdmData: [String: Any] = [
    "eventType": "application.scene",
    "_techmarketingdemos": [
        "appInformation": [
            "appStateDetails": [
                "screenType": "App",
                "screenName": "luma: content: ios: us: en: login",
                "screenView": [
                    "value": 1
                ]
            ]
        ] 
    ]
]
```

>[!TAB Android]

```kotlin
val xdmData = mapOf(
    "eventType" to "application.scene",
    tenant.value to mapOf(
        "appInformation" to mapOf(
            "appStateDetails" to mapOf(
                "screenType" to "App",
                "screenName" to stateName,
                "screenView" to mapOf("value" to 1)
            )
        )
    )
)
```

>[!ENDTABS]



* Sie können diese Datenstruktur jetzt verwenden, um eine `ExperienceEvent` zu erstellen.

>[!BEGINTABS]

>[!TAB iOS]

```swift
let event = ExperienceEvent(xdm: xdmData)
```

>[!TAB Android]

```kotlin
val event = ExperienceEvent(xdmData)
```

>[!ENDTABS]


* Senden Sie das Ereignis und die Daten an Platform Edge Network.

>[!BEGINTABS]

>[!TAB iOS]

```swift
Edge.sendEvent(experienceEvent: event)
```

>[!TAB Android]

```kotlin
Edge.sendEvent(event, null)
```

>[!ENDTABS]

Implementieren Sie diesen Code erneut in Ihrem Projekt.

>[!BEGINTABS]

>[!TAB iOS]

1. Zur Vereinfachung definieren Sie zwei Funktionen in **[!UICONTROL MobileSDK]**. Navigieren Sie in Ihrem Xcode-Projekt **[!DNL Luma]** Navigator zu **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL >]** MobileSDK.

   * Eines für App-Interaktionen. Fügen Sie den folgenden Code zur `func sendAppInteractionEvent(actionName: String)` hinzu:

     ```swift
     // Set up a data dictionary, create an experience event and send the event.
     let xdmData: [String: Any] = [
         "eventType": "application.interaction",
         tenant : [
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
     let appInteractionEvent = ExperienceEvent(xdm: xdmData)
     Edge.sendEvent(experienceEvent: appInteractionEvent)
     ```

     Diese Funktion verwendet den Aktionsnamen als Parameter und

      * richtet die XDM-Payload mithilfe des Parameters aus der -Funktion als Wörterbuch ein,
      * ein Erlebnisereignis mithilfe des Wörterbuchs einrichtet,
      * sendet das Erlebnisereignis über die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent)-API.


   * Und einen für Bildschirmverfolgung. Fügen Sie den folgenden Code zur `func sendTrackScreenEvent(stateName: String) ` hinzu:

     ```swift
     // Set up a data dictionary, create an experience event and send the event.
     let xdmData: [String: Any] = [
         "eventType": "application.scene",
         tenant : [
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
     ]
     let trackScreenEvent = ExperienceEvent(xdm: xdmData)
     Edge.sendEvent(experienceEvent: trackScreenEvent)
     ```

     Diese Funktion verwendet den Statusnamen als Parameter und

      * richtet die XDM-Payload mithilfe des Parameters aus der -Funktion als Wörterbuch ein,
      * ein Erlebnisereignis mithilfe des Wörterbuchs einrichtet,
      * sendet das Erlebnisereignis über die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent)-API.

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]**.

   1. Fügen Sie den folgenden hervorgehobenen Code zum Schließen der Schaltfläche „Anmelden“ hinzu:

      ```swift
      // Send app interaction event
      MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
      ```

   1. Fügen Sie den folgenden hervorgehobenen Code zu `onAppear` Modifikator hinzu:

      ```swift
      // Send track screen event
      MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: login")
      ```

>[!TAB Android]

1. Zur Vereinfachung definieren Sie zwei Funktionen in **[!UICONTROL MobileSDK]**. Android Navigieren Sie in Ihrem Android **[!UICONTROL -Navigator zu {]**}![ChevronDown ](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** models **[!UICONTROL >]** MobileSDK **[!UICONTROL .]**

   * Eines für App-Interaktionen. Fügen Sie den folgenden Code zur `fun sendAppInteractionEvent(actionName: String)` hinzu:

     ```kotlin
     // Set up a data map, create an experience event and send the event.
     val xdmData = mapOf(
         "eventType" to "application.interaction",
         tenant.value to mapOf(
             "appInformation" to mapOf(
                 "appInteraction" to mapOf(
                     "name" to actionName,
                     "appAction" to mapOf("value" to 1)
                 )
             )
         )
     )
     val appInteractionEvent = ExperienceEvent.Builder().setXdmSchema(xdmData).build()
     Edge.sendEvent(appInteractionEvent, null)
     ```

     Diese Funktion verwendet den Aktionsnamen als Parameter und

      * richtet die XDM-Payload mithilfe des Parameters aus der -Funktion als Zuordnung ein,
      * ein Erlebnisereignis mithilfe der Zuordnung einrichtet,
      * sendet das Erlebnisereignis über die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent)-API.


   * Und einen für Bildschirmverfolgung. Fügen Sie den folgenden Code zur `fun sendTrackScreenEvent(stateName: String)` hinzu:

     ```kotlin
     // Set up a data map, create an experience event and send the event.
     val xdmData = mapOf(
         "eventType" to "application.scene",
         tenant.value to mapOf(
             "appInformation" to mapOf(
                 "appStateDetails" to mapOf(
                     "screenType" to "App",
                     "screenName" to stateName,
                     "screenView" to mapOf("value" to 1)
                 )
             )
         )
     )
     val trackScreenEvent = ExperienceEvent.Builder().setXdmSchema(xdmData).build()
     Edge.sendEvent(trackScreenEvent, null)
     ```

     Diese Funktion verwendet den Statusnamen als Parameter und

      * richtet die XDM-Payload mithilfe des Parameters aus der -Funktion als Zuordnung ein,
      * ein Erlebnisereignis mithilfe der Zuordnung einrichtet,
      * sendet das Erlebnisereignis über die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent)-API.

1. Navigieren Sie zu **[!UICONTROL Android]** ![ChevronDown ](/help/assets/icons/ChevronDown.svg)**[!DNL app]**>**[!DNL kotlin+java]**>**[!DNL com.adobe.luma.tutorial.android]**>**[!UICONTROL &#x200B; views &#x200B;]**>**[!UICONTROL &#x200B; LoginSheet.kt &#x200B;]**

   1. Fügen Sie den folgenden hervorgehobenen Code zum Ereignis **[!UICONTROL Button]** **[!UICONTROL onClick]** hinzu:

      ```kotlin
      // Send app interaction event
      MobileSDK.shared.sendAppInteractionEvent("login")
      ```

   1. Fügen Sie den folgenden hervorgehobenen Code zur zusammensetzbaren Funktion `LaunchedEffect(Unit)` hinzu:

      ```kotlin
      // Send track screen event
      MobileSDK.shared.sendTrackScreenEvent("luma: content: android: us: en: login")
      ```

>[!ENDTABS]



## Validierung

1. Lesen Sie den Abschnitt [Setup-Anweisungen](assurance.md#connecting-to-a-session), um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.

   1. Verschieben Sie das Assurance-Symbol nach links.
   1. Wählen Sie **[!UICONTROL Startseite]** in der Registerkartenleiste aus und vergewissern Sie sich, dass **[!UICONTROL ECID]**, **[!UICONTROL E-Mail]** und **[!UICONTROL CRM ID]** auf dem Startbildschirm angezeigt werden.
   1. Wählen Sie **[!DNL Products]** in der Registerkartenleiste aus.
   1. Produkt auswählen.
   1. Auswählen <img src="assets/saveforlater.png" width="15" /> (iOS) oder <img src="assets/heart.png" width="25" /> (Android).
   1. Auswählen <img src="assets/addtocart.png" width="20" />.
   1. Auswählen <img src="assets/purchase.png" width="15" />.

>[!BEGINTABS]

>[!TAB iOS]

<img src="./assets/mobile-app-events-3.png" width="300">

>[!TAB Android]

<img src="./assets/mobile-app-events-3-android.png" width="278">

>[!ENDTABS]

1. Suchen Sie in der Assurance-Benutzeroberfläche nach den **[!UICONTROL hitReceived]**-Ereignissen des Anbieters **[!UICONTROL com.adobe.edge.]**.
1. Wählen Sie das Ereignis aus und überprüfen Sie die XDM-Daten im **[!UICONTROL messages]**-Objekt. Alternativ können Sie ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) **[!UICONTROL Rohereignis kopieren]** verwenden und einen Text- oder Code-Editor Ihrer Wahl verwenden, um das Ereignis einzufügen und zu überprüfen.

   ![Validierung der Datenerfassung](assets/datacollection-validation.png){zoomable="yes"}


## Nächste Schritte

Sie sollten jetzt über alle Tools verfügen, um mit dem Hinzufügen der Datenerfassung zu Ihrer App zu beginnen. Sie können die Interaktion der Benutzenden mit Ihren Produkten in der App intelligenter gestalten und der App weitere Interaktionen und Bildschirm-Tracking-Aufrufe hinzufügen:

* Implementieren Sie die Bestellung, den Checkout, den leeren Warenkorb und andere Funktionen in der App und fügen Sie dieser Funktion relevante Commerce-Erlebnisereignisse hinzu.
* Wiederholen Sie den Aufruf von `sendAppInteractionEvent` mit dem entsprechenden Parameter, um andere App-Interaktionen des Benutzers zu verfolgen.
* Wiederholen Sie den Aufruf von `sendTrackScreenEvent` mit dem entsprechenden Parameter, um die vom Benutzer in der App angezeigten Bildschirme zu verfolgen.

>[!TIP]
>
>Sehen Sie sich die [fertige App](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) an, um weitere Beispiele zu erhalten.


## Senden von Ereignissen an Analytics und Platform

Nachdem Sie nun die Ereignisse erfasst und an Platform Edge Network gesendet haben, werden sie an die Programme und Services gesendet, die in Ihrem [Datenstrom“ konfiguriert ](create-datastream.md). In späteren Lektionen ordnen Sie diese Daten [Adobe Analytics](analytics.md), [Adobe Experience Platform](platform.md) und anderen Adobe Experience Cloud-Lösungen (wie [Adobe Target](target.md) und Adobe Journey Optimizer) zu.

>[!SUCCESS]
>
>Sie haben jetzt Ihre App so eingerichtet, dass Commerce-, App-Interaktions- und Bildschirm-Tracking-Ereignisse über die Adobe Experience Platform Edge Network verfolgt werden. Und für alle -Services, die Sie in Ihrem Datenstrom definiert haben.
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[WebViews behandeln](web-views.md)**
