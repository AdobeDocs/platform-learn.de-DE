---
title: Events
description: Erfahren Sie, wie Sie Ereignisdaten in einer Mobile App erfassen.
hide: true
hidefromtoc: true
source-git-commit: ca83bbb571dc10804adcac446e2dba4fda5a2f1d
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

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

  ```swift {highlight="2-8"}
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

* Identifizieren Sie in Ihrem Schema alle zusätzlichen Daten, die mit dem Ereignis zur Produktansicht für Commerce-Produkte verknüpft sind. Fügen Sie in diesem Beispiel `productListItems` Hierbei handelt es sich um einen Standardsatz von Feldern, die mit Commerce-bezogenen Ereignissen verwendet werden:

  ![Schema der Produktlistenelemente](assets/datacollection-prodListItems-schema.png)
   * Beachten Sie Folgendes: `productListItems` ist ein Array, sodass mehrere Produkte bereitgestellt werden können.

* Um diese Daten hinzuzufügen, erweitern Sie Ihre `xdmData` -Objekt, um zusätzliche Daten einzuschließen:

```swift {highlight="9-16"}
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

* Anschließend erstellen Sie mithilfe der Datenstruktur eine `ExperienceEvent`:

  ```swift
  let productViewEvent = ExperienceEvent(xdm: xdmData)
  ```

* Senden Sie das Ereignis und die Daten mithilfe der sendEvent-API an Platform Edge Network:

  ```swift
  Edge.sendEvent(experienceEvent: productViewEvent)
  ```

Lassen Sie uns nun diesen Code in Ihr Xcode-Projekt implementieren.
Sie haben in Ihrer App unterschiedliche Aktionen im Zusammenhang mit Commerce-Produkten (Ansicht, Hinzufügen zum Warenkorb, Speichern zum späteren Kauf) und möchten Ereignisse basierend auf diesen Aktionen senden, die vom Benutzer ausgeführt werden.

1. Gehen Sie wie folgt vor, um Erlebnisereignisse zu strukturieren: `MobileSDK`und fügen Sie Folgendes zum `sendCommerceExperienceEvent` -Funktion. Diese Funktion akzeptiert das Commerce-Erlebnis-Ereignis und das Produkt als Parameter:

   ```swift {highlight="2-22"}
   func sendCommerceExperienceEvent(commerceEventType: String, product: Product) {
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
   }
   ```

1. In `ProductView` Fügen Sie verschiedene Aufrufe zu `sendCommerceExperienceEvent` Funktion:

   1. Im `.task` -Modifikator im `ATTrackingManager.trackingAuthorizationStatus` Schließung. Die `.task` -Modifikator wird aufgerufen, wenn die Produktansicht initialisiert und angezeigt wird. Daher möchten Sie zu diesem bestimmten Zeitpunkt ein Produktansichtsereignis senden.

      ```swift {highlight="4-5"}
      .task {
          if ATTrackingManager.trackingAuthorizationStatus == .authorized {
               // Send commerce experience event
              MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productView", product: product)
          }
      }
      ```

   1. Fügen Sie für jede der Schaltflächen (In späteren Versionen gespeichert, Zu Warenkorb hinzufügen und Kauf) in der Symbolleiste, die in der Produktansicht verfügbar ist, den entsprechenden Aufruf hinzu.

      * Für Speichern für später/Hinzufügen zur Wunschliste:

        ```swift {highlight="5-6"}
        Button {
            Task {
                if ATTrackingManager.trackingAuthorizationStatus == .authorized {
                // Send saveForLater commerce experience event
                    MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
                }
            }
            showSaveForLaterDialog.toggle()
        } label: {
            Label("", systemImage: "heart")
        }
        .alert(isPresented: $showSaveForLaterDialog, content: {
            Alert(title: Text( "Saved for later"), message: Text("The selected item is saved to your wishlist…"))
        })
        ```

      * Zum Hinzufügen zum Warenkorb:

        ```swift {highlight="5-6"}
        Button {
            Task {
                if ATTrackingManager.trackingAuthorizationStatus == .authorized {
                    // Send productListAdds commerce experience event
                    MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
                }
            }
            showAddToCartDialog.toggle()
        } label: {
                Label("", systemImage: "cart.badge.plus")
        }
        alert(isPresented: $showAddToCartDialog, content: {
            Alert(title: Text( "Added to basket"), message: Text("The selected item is added to your basket…"))
        })
        ```

      * Für Kauf:

        ```swift {highlight="5-6"}
        Button {
            Task {
                if ATTrackingManager.trackingAuthorizationStatus == .authorized {
                    // Send purchase commerce experience event
                    MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
                }
            }
            showPurchaseDialog.toggle()
        } label: {
            Label("", systemImage: "creditcard")
        }
        .alert(isPresented: $showPurchaseDialog, content: {
            Alert(title: Text( "Purchases"), message: Text("The selected item is purchased…"))
        })
        ```

### Benutzerdefinierte Feldergruppen

Stellen Sie sich vor, Sie möchten Bildschirmansichten und Interaktionen in der App selbst verfolgen. Denken Sie daran, für diesen Ereignistyp eine benutzerdefinierte Feldergruppe definiert zu haben.

* Identifizieren Sie in Ihrem Schema die Ereignisse, die Sie erfassen möchten.
  ![App-Interaktionsschema](assets/datacollection-appInteraction-schema.png)

* Beginnen Sie mit der Erstellung Ihres Objekts.

  >[!NOTE]
  >
  >  Standardfeldgruppen beginnen immer im Objektstamm.
  >
  >  Benutzerdefinierte Feldergruppen beginnen immer unter einem Objekt, das für Ihre Experience Cloud-Organisation eindeutig ist. `_techmarketingdemos` in diesem Beispiel.

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


* Erstellen Sie dann die Datenstruktur, um eine `ExperienceEvent`.

  ```swift
  let event = ExperienceEvent(xdm: xdmData)
  ```

* Senden Sie das Ereignis und die Daten an Platform Edge Network.

  ```swift
  Edge.sendEvent(experienceEvent: event)
  ```


Erneut lassen Sie diesen Code in Ihr Xcode-Projekt implementieren.

1. Zur Vereinfachung definieren Sie zwei Funktionen in `MobileSDK`.

   Eine für App-Interaktionen. Fügen Sie den hervorgehobenen Code zum `sendAppInteractionEvent(actionName)` -Funktion in **[!UICONTROL MobileSDK]**:

   ```swift {highlight="2-16"}
   func sendAppInteractionEvent(actionName: String) {
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
   }
   ```

   Und eine für die Bildschirmverfolgung. Fügen Sie den markierten Code hinzu. `sendTrackScreenEvent(stateName)` -Funktion in **[!UICONTROL MobileSDK]**:

   ```swift {highlight="2-17"}
   func sendTrackScreenEvent(stateName: String) {
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
   }
   ```

1. Navigieren Sie zu **[!UICONTROL LoginSheet]**.

   * Fügen Sie den folgenden hervorgehobenen Code zum Schließen der Anmelde-Schaltfläche hinzu:

     ```swift {highlight="3"}
     Button("Login") {                               
        // Send app interaction event
        MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
        dismiss()
     }
     .disabled(currentEmailId.isValidEmail == false)
     .buttonStyle(.bordered)
     ```

   * Fügen Sie den folgenden hervorgehobenen Code zu `onAppear` modifier:

     ```swift {highlight="13"}
     .onAppear {
        Task {
            if currentEmailId == "testUser@gmail.com" || currentEmailId.isValidEmail == false {
                // still allow to log in
                disableLogin = false
            }
            else {
                disableLogin = true
            }
        }
        // Send track screen event
        MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: login")
     }
     ```

### Validierung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) und verbinden Sie Ihren Simulator oder Ihr Gerät mit Assurance.
1. Führen Sie die App aus, um sich anzumelden und mit einem Produkt zu interagieren.

   1. Verschieben Sie das Symbol &quot;Versicherung&quot;nach links.
   1. Auswählen **[!UICONTROL Startseite]** in der Symbolleiste.
   1. Wählen Sie die **[!UICONTROL Anmelden]** -Schaltfläche, um das Login-Blatt zu öffnen.
   1. Wählen Sie die **[!UICONTROL A|]** -Schaltfläche, um eine zufällige E-Mail- und Kunden-ID einzufügen.
   1. Auswählen **[!UICONTROL Anmelden]**.
   1. Auswählen **[!UICONTROL Produkte]** in der Symbolleiste.
   1. Wählen Sie ein Produkt.
   1. Auswählen **[!UICONTROL Später speichern]**.
   1. Auswählen **[!UICONTROL Zum Warenkorb hinzufügen]**.
   1. Auswählen **[!UICONTROL Kauf]**.

      <img src="./assets/mobile-app-events-1.png" width="200"> <img src="./assets/mobile-app-events-2.png" width="200"> <img src="./assets/mobile-app-events-3.png" width="200">


1. Suchen Sie nach **[!UICONTROL hitReceived]** -Ereignisse aus **[!UICONTROL com.adobe.edge.konductor]** -Anbieter.
1. Wählen Sie das Ereignis aus und überprüfen Sie die XDM-Daten im **[!UICONTROL messages]** -Objekt.
   ![Datenerfassungsprüfung](assets/datacollection-validation.png)


### Implementieren in die Luma-App

Sie sollten jetzt über alle Tools verfügen, um die Datenerfassung zur Luma-App hinzuzufügen. Sie können mehr Informationen dazu hinzufügen, wie Ihr Benutzer mit Ihren Produkten interagiert, und Sie können Ihrer App weitere App-Interaktionen und Screentracking-Aufrufe hinzufügen:

* Implementieren Sie die App, indem Sie Bestellungen, Checkout, leeren Warenkorb und andere Funktionen hinzufügen und dieser Funktion relevante Commerce-Erlebnisereignisse hinzufügen.
* Wiederholen Sie den Aufruf von `sendAppInteractionEvent` mit dem entsprechenden Parameter, um andere App-Interaktionen in der App durch den Benutzer zu verfolgen.
* Wiederholen Sie den Aufruf von `sendTrackScreenEvent` mit dem entsprechenden Parameter, um jeden vom Benutzer in der App angezeigten Bildschirm zu verfolgen.

>[!TIP]
>
>Überprüfen Sie die [voll implementierte App](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) für weitere Beispiele.


## Senden von Ereignissen an Analytics und Platform

Nachdem Sie die Ereignisse erfasst und an das Platform Edge Network gesendet haben, werden sie an die in Ihrer [datastream](create-datastream.md). In späteren Lektionen ordnen Sie diese Daten zu [Adobe Analytics](analytics.md) und [Adobe Experience Platform](platform.md).

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass sie Commerce-, App-Interaktionen- und Bildschirmverfolgungsereignisse im Adobe Experience Platform Edge Network und allen in Ihrem Datastream definierten Diensten verfolgt.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[WebViews](web-views.md)**
