---
title: Events
description: Erfahren Sie, wie Sie Ereignisdaten in einer Mobile App erfassen.
hide: true
source-git-commit: e119e2bdce524c834cdaf43ed9eb9d26948b0ac6
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 1%

---

# Events

Erfahren Sie, wie Sie Ereignisse in einer Mobile App verfolgen.

Die Edge Network-Erweiterung stellt eine API zum Senden von Erlebnisereignissen an Platform Edge Network bereit. Ein Erlebnisereignis ist ein Objekt, das Daten enthält, die der XDM ExperienceEvent-Schemadefinition entsprechen. Sie erfassen einfach, was Benutzer in Ihrer mobilen App tun. Sobald Daten vom Platform Edge Network empfangen wurden, können sie an Anwendungen und Dienste weitergeleitet werden, die in Ihrem Datenspeicher konfiguriert sind, z. B. Adobe Analytics und Experience Platform. Weitere Informationen zum [Erlebnisereignisse](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) in der Produktdokumentation.

## Voraussetzungen

* Alle Paketabhängigkeiten sind im Xcode-Projekt vorhanden.
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


### Standardfeldgruppen

Für die Standardfeldgruppen sieht der Prozess wie folgt aus:

* Identifizieren Sie in Ihrem Schema die Ereignisse, die Sie erfassen möchten. In diesem Beispiel verfolgen Sie Commerce-Erlebnisereignisse, z. B. eine Produktansicht (**[!UICONTROL productViews]**).

  ![Produktansichtsschema](assets/datacollection-prodView-schema.png)

* Um ein Objekt zu erstellen, das die Erlebnisereignisdaten in Ihrer App enthält, verwenden Sie folgenden Code:

  ```swift
  var xdmData: [String: Any] = [
      "eventType": "commerce.productViews",
      "commerce": [
          "productViews": [
            "id": sku,
            "value": 1
          ]
      ]
  ]
  ```

   * `eventType`: Beschreibt das aufgetretene Ereignis und verwendet eine [bekannter Wert](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values) nach Möglichkeit.
   * `commerce.productViews.id`: ein string -Wert, der die SKU des Produkts darstellt.
   * `commerce.productViews.value`: Geben Sie den numerischen Wert des Ereignisses an. Wenn es sich um einen booleschen Wert (oder &quot;Zähler&quot;in Adobe Analytics) handelt, wird der Wert immer auf 1 gesetzt. Bei numerischen Ereignissen oder Währungsereignissen kann der Wert > 1 betragen.

* Identifizieren Sie in Ihrem Schema alle zusätzlichen Daten, die mit dem Ereignis zur Produktansicht für Commerce-Produkte verknüpft sind. Fügen Sie in diesem Beispiel **[!UICONTROL productListItem]** Hierbei handelt es sich um einen Standardsatz von Feldern, die mit Commerce-bezogenen Ereignissen verwendet werden:

  ![Schema der Produktlistenelemente](assets/datacollection-prodListItems-schema.png)
   * Beachten Sie Folgendes: **[!UICONTROL productListItems]** ist ein Array, sodass mehrere Produkte bereitgestellt werden können.

* Um diese Daten hinzuzufügen, erweitern Sie Ihre `xdmData` -Objekt, um zusätzliche Daten einzuschließen:

```swift
var xdmData: [String: Any] = [
    "eventType": "commerce.productViews",
        "commerce": [
        "productViews": [
            "id": sku,
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

* Sie können diese Datenstruktur jetzt verwenden, um eine `ExperienceEvent`:

  ```swift
  let productViewEvent = ExperienceEvent(xdm: xdmData)
  ```

* Senden Sie das Ereignis und die Daten mithilfe des `sendEvent` API:

  ```swift
  Edge.sendEvent(experienceEvent: productViewEvent)
  ```

Sie werden diesen Code jetzt tatsächlich in Ihr Xcode-Projekt implementieren.
Sie haben unterschiedliche Aktionen im Zusammenhang mit Commerce-Produkten in Ihrer App und möchten Ereignisse basierend auf diesen Aktionen senden, die vom Benutzer ausgeführt werden:

* Ansicht: Tritt auf, wenn Benutzer ein bestimmtes Produkt anzeigen;
* Zum Warenkorb hinzufügen: wenn Benutzer tippt <img src="assets/addtocart.png" width="20" /> in einem Produktdetailbildschirm,
* für später speichern: Benutzer tippt auf <img src="assets/saveforlater.png" width="15" /> im Produktdetailbildschirm,
* Käufer: Benutzer tippt auf die <img src="assets/purchase.png" width="20" /> im Produktdetailbildschirm.

So strukturieren Sie das Senden von Erlebnisereignissen:

1. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Utils]** > **[!UICONTROL MobileSDK]** im Xcode-Projekt-Navigator und fügen Sie Folgendes zum `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` -Funktion. Diese Funktion akzeptiert das Commerce-Erlebnis-Ereignis und das Produkt als Parameter:

   ```swift
   let xdmData: [String: Any] = [
       "eventType": "commerce." + commerceEventType,
       "commerce": [
           commerceEventType: [
               "id": product.sku,
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
   
   Logger.viewCycle.info("About to send commerce experience event of type  \(commerceEventType)..."
   let commerceExperienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: commerceExperienceEvent)
   ```

1. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Ansichten]** > **[!UICONTROL Produkte]** > **[!UICONTROL ProductView]** und fügen Sie verschiedene Aufrufe zu `sendCommerceExperienceEvent` Funktion:

   1. Im `.task` -Modifikator innerhalb der `ATTrackingManager.trackingAuthorizationStatus` Schließung. Diese `.task` -Modifikator wird aufgerufen, wenn die Produktansicht initialisiert und angezeigt wird. Daher möchten Sie zu diesem bestimmten Zeitpunkt ein Produktansichtsereignis senden.

      ```swift
      // Send commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productView", product: product)
      ```

   1. Für jede der Schaltflächen (<img src="assets/saveforlater.png" width="15" />, <img src="assets/addtocart.png" width="20" /> und <img src="assets/purchase.png" width="20" />) in der Symbolleiste den entsprechenden Aufruf innerhalb der `ATTrackingManager.trackingAuthorizationStatus == .authorized` Stilllegung:

      1. Für <img src="assets/saveforlater.png" width="15" />

         ```swift
         // Send saveForLater commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
         ```

      1. Für <img src="assets/addtocart.png" width="20" />

         ```swift
         // Send productListAdds commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
         ```

      1. Für <img src="assets/purchase.png" width="20" />

         ```swift
         // Send purchase commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
         ```

### Benutzerdefinierte Feldergruppen

Stellen Sie sich vor, Sie möchten Bildschirmansichten und Interaktionen in der App selbst verfolgen. Denken Sie daran, für diesen Ereignistyp eine benutzerdefinierte Feldergruppe definiert zu haben.

* Identifizieren Sie in Ihrem Schema die Ereignisse, die Sie erfassen möchten.
  ![App-Interaktionsschema](assets/datacollection-appInteraction-schema.png)

* Beginnen Sie mit der Erstellung Ihres Objekts.

  >[!NOTE]
  >
  >* Standardfeldgruppen beginnen immer im Objektstamm.
  >
  >* Benutzerdefinierte Feldergruppen beginnen immer unter einem Objekt, das für Ihre Experience Cloud-Organisation eindeutig ist. `_techmarketingdemos` in diesem Beispiel.

  Für das App-Interaktionsereignis erstellen Sie ein Objekt wie:

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

  Für das Screeningereignis erstellen Sie ein Objekt wie:

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


* Sie können diese Datenstruktur jetzt verwenden, um eine `ExperienceEvent`.

  ```swift
  let event = ExperienceEvent(xdm: xdmData)
  ```

* Senden Sie das Ereignis und die Daten an Platform Edge Network.

  ```swift
  Edge.sendEvent(experienceEvent: event)
  ```


Erneut lassen Sie diesen Code in Ihr Xcode-Projekt implementieren.

1. Zur Vereinfachung definieren Sie zwei Funktionen in **[!UICONTROL MobileSDK]**. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Utils]** > **[!UICONTROL MobileSDK]** in Ihrem Xcode-Projektnavigator.

   1. Eine für App-Interaktionen. Fügen Sie diesen Code zum `func sendAppInteractionEvent(actionName: String)` Funktion:

      ```swift
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

   1. Und eine für die Bildschirmverfolgung. Fügen Sie diesen Code zum `func sendTrackScreenEvent(stateName: String) ` Funktion:

      ```swift
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

1. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Ansichten]** > **[!UICONTROL Allgemein]** > **[!UICONTROL LoginSheet]**.

   1. Fügen Sie den folgenden hervorgehobenen Code zum Schließen der Anmelde-Schaltfläche hinzu:

      ```swift
      // Send app interaction event
      MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
      dismiss()
      ```

   1. Fügen Sie den folgenden hervorgehobenen Code zu `onAppear` modifier:

      ```swift
      // Send track screen event
      MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: login")
      ```

### Validierung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) und verbinden Sie Ihren Simulator oder Ihr Gerät mit Assurance.
1. Führen Sie die App aus, um sich anzumelden und mit einem Produkt zu interagieren.

   1. Verschieben Sie das Symbol &quot;Versicherung&quot;nach links.
   1. Auswählen **[!UICONTROL Startseite]** in der Symbolleiste.
   1. Wählen Sie die <img src="assets/login.png" width="15" /> -Schaltfläche, um das Login-Blatt zu öffnen.
   1. Wählen Sie die <img src="assets/insert.png" width="15" /> -Schaltfläche, um eine zufällige E-Mail- und Kunden-ID einzufügen.
   1. Auswählen **[!UICONTROL Anmelden]**.
   1. Auswählen **[!UICONTROL Produkte]** in der Symbolleiste.
   1. Wählen Sie ein Produkt.
   1. Auswählen <img src="assets/saveforlater.png" width="15" />.
   1. Auswählen <img src="assets/addtocart.png" width="20" />.
   1. Auswählen <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-1.png" width="200"> <img src="./assets/mobile-app-events-2.png" width="200"> <img src="./assets/mobile-app-events-3.png" width="200">


1. Suchen Sie in der Assurance-Benutzeroberfläche nach der **[!UICONTROL hitReceived]** -Ereignisse aus **[!UICONTROL com.adobe.edge.konductor]** -Anbieter.
1. Wählen Sie das Ereignis aus und überprüfen Sie die XDM-Daten im **[!UICONTROL messages]** -Objekt.
   ![Datenerfassungsprüfung](assets/datacollection-validation.png)


### Implementieren in die Luma-App

Sie sollten jetzt über alle Tools verfügen, um die Datenerfassung zur Luma-App hinzuzufügen. Sie können mehr Informationen dazu hinzufügen, wie Ihr Benutzer mit Ihren Produkten interagiert, und Sie können Ihrer App weitere App-Interaktionen und Screentracking-Aufrufe hinzufügen:

* Implementieren Sie die App, indem Sie Bestellungen, Checkout, leeren Warenkorb und andere Funktionen hinzufügen und dieser Funktion relevante Commerce-Erlebnisereignisse hinzufügen.
* Wiederholen Sie den Aufruf von `sendAppInteractionEvent` mit dem entsprechenden Parameter, um andere App-Interaktionen des Benutzers zu verfolgen.
* Wiederholen Sie den Aufruf von `sendTrackScreenEvent` mit dem entsprechenden Parameter zur Verfolgung der Bildschirme, die vom Benutzer in der App angezeigt wurden.

>[!TIP]
>
>Überprüfen Sie die [voll implementierte App](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) für weitere Beispiele.


## Senden von Ereignissen an Analytics und Platform

Nachdem Sie die Ereignisse erfasst und an das Platform Edge Network gesendet haben, werden sie an die in Ihrer [datastream](create-datastream.md). In späteren Lektionen ordnen Sie diese Daten zu [Adobe Analytics](analytics.md) und [Adobe Experience Platform](platform.md).

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass sie Commerce-, App-Interaktionen- und Bildschirmverfolgungsereignisse im Adobe Experience Platform Edge Network und allen in Ihrem Datastream definierten Diensten verfolgt.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[WebViews](web-views.md)**
