---
title: Verfolgen von Ereignisdaten in mobilen Apps mit dem Platform Mobile SDK
description: Erfahren Sie, wie Sie Ereignisdaten in einer Mobile App verfolgen.
jira: KT-14631
exl-id: 4779cf80-c143-437b-8819-1ebc11a26852
source-git-commit: afb15c561179386e7846e8cd8963f67820af09f1
workflow-type: tm+mt
source-wordcount: '1328'
ht-degree: 0%

---

# Tracking von Ereignisdaten

Erfahren Sie, wie Sie Ereignisse in einer Mobile App verfolgen.

Die Edge Network-Erweiterung stellt eine API zum Senden von Erlebnisereignissen an Platform Edge Network bereit. Ein Erlebnisereignis ist ein Objekt, das Daten enthält, die der XDM ExperienceEvent-Schemadefinition entsprechen. Sie erfassen einfach, was Benutzer in Ihrer mobilen App tun. Sobald Daten von Platform Edge Network empfangen wurden, können sie an Anwendungen und Dienste weitergeleitet werden, die in Ihrem Datenspeicher konfiguriert sind, z. B. Adobe Analytics und Experience Platform. Weitere Informationen zu [Erlebnisereignissen](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) finden Sie in der Produktdokumentation.

## Voraussetzungen

* Alle Paketabhängigkeiten sind in Ihrem Xcode-Projekt vorhanden.
* Registrierte Erweiterungen in **[!UICONTROL AppDelegate]**.
* Die MobileCore-Erweiterung wurde für die Verwendung Ihrer Entwicklungsumgebung `appId` konfiguriert.
* Importierte SDKs
* Die App wurde erfolgreich erstellt und mit den oben genannten Änderungen ausgeführt.

## Lernziele

In dieser Lektion werden Sie

* Erfahren Sie, wie Sie XDM-Daten basierend auf einem Schema strukturieren.
* Senden Sie ein XDM-Ereignis basierend auf einer Standardfeldgruppe.
* Senden Sie ein XDM-Ereignis basierend auf einer benutzerdefinierten Feldergruppe.
* Senden Sie ein XDM-Kaufereignis.
* Überprüfen Sie mit Assurance.

## Erstellen eines Erlebnisereignisses

Die Adobe Experience Platform Edge-Erweiterung kann Ereignisse senden, die einem zuvor definierten XDM-Schema folgen, an das Adobe Experience Platform-Edge Network.

Der Prozess läuft so ab...

1. Identifizieren Sie die Mobile App-Interaktion, die Sie verfolgen möchten.

1. Überprüfen Sie Ihr Schema und identifizieren Sie das entsprechende Ereignis.

1. Überprüfen Sie Ihr Schema und identifizieren Sie alle zusätzlichen Felder, die zur Beschreibung des Ereignisses verwendet werden sollen.

1. Erstellen und füllen Sie das Datenobjekt.

1. Ereignis erstellen und senden.

1. Validieren Sie.


### Standardfeldgruppen

Für die Standardfeldgruppen sieht der Prozess wie folgt aus:

* Identifizieren Sie in Ihrem Schema die Ereignisse, die Sie erfassen möchten. In diesem Beispiel verfolgen Sie Commerce-Erlebnisereignisse, z. B. ein Produktansichtsereignis (**[!UICONTROL productViews]**).

  ![Produktansichtsschema](assets/datacollection-prodView-schema.png)

* Um ein Objekt zu erstellen, das die Erlebnisereignisdaten in Ihrer App enthält, verwenden Sie folgenden Code:

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

   * `eventType`: Beschreibt das Ereignis, das aufgetreten ist. Verwenden Sie nach Möglichkeit einen [bekannten Wert](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values).
   * `commerce.productViews.value`: der numerische oder boolesche Wert des Ereignisses. Wenn es sich um einen booleschen Wert (oder &quot;Zähler&quot;in Adobe Analytics) handelt, wird der Wert immer auf 1 gesetzt. Bei numerischen Ereignissen oder Währungsereignissen kann der Wert > 1 betragen.

* Identifizieren Sie in Ihrem Schema alle zusätzlichen Daten, die mit dem Ereignis zur Produktansicht für Commerce-Produkte verknüpft sind. Schließen Sie in diesem Beispiel **[!UICONTROL productListItems]** ein, das ein Standardsatz von Feldern ist, die mit jedem Commerce-bezogenen Ereignis verwendet werden:

  ![Schema der Produktlistenelemente](assets/datacollection-prodListItems-schema.png)
   * Beachten Sie, dass **[!UICONTROL productListItems]** ein Array ist, sodass mehrere Produkte bereitgestellt werden können.

* Um diese Daten hinzuzufügen, erweitern Sie Ihr `xdmData` -Objekt, um zusätzliche Daten einzuschließen:

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

* Sie können diese Datenstruktur nun verwenden, um eine `ExperienceEvent` zu erstellen:

  ```swift
  let productViewEvent = ExperienceEvent(xdm: xdmData)
  ```

* Senden Sie das Ereignis und die Daten mithilfe der `sendEvent` -API an Platform Edge Network:

  ```swift
  Edge.sendEvent(experienceEvent: productViewEvent)
  ```

Die API [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) ist das mobile SDK von AEP, das den API-Aufrufen [`MobileCore.trackAction`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackaction) und [`MobileCore.trackState`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackstate) entspricht. Weitere Informationen finden Sie unter [Migration von der mobilen Analytics-Erweiterung zum Adobe Experience Platform-Edge Network](https://developer.adobe.com/client-sdks/documentation/adobe-analytics/migrate-to-edge-network/) .

Sie werden diesen Code jetzt tatsächlich in Ihr Xcode-Projekt implementieren.
Sie haben verschiedene Commerce-produktbezogene Aktionen in Ihrer App und möchten Ereignisse basierend auf den vom Benutzer durchgeführten Aktionen senden:

* Ansicht: Tritt auf, wenn ein Benutzer ein bestimmtes Produkt anzeigt,
* Hinzufügen zum Warenkorb: wenn ein Benutzer auf <img src="assets/addtocart.png" width="20"/> in einem Produktdetailbildschirm,
* für später speichern: wenn ein Benutzer auf <img src="assets/saveforlater.png" width="15"/> in einem Produktdetailbildschirm,
* purchase: wenn ein Benutzer auf <img src="assets/purchase.png" width="20"/> in einem Produktdetailbildschirm angezeigt.

Um das Senden von Commerce-bezogenen Erlebnisereignissen wiederverwendbar zu machen, verwenden Sie eine dedizierte Funktion:

1. Navigieren Sie im Xcode-Projektnavigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** und fügen Sie der Funktion `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` Folgendes hinzu.

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

   * richtet die XDM-Payload mithilfe der Parameter aus der Funktion als Wörterbuch ein,
   * richtet mithilfe des Wörterbuchs ein Erlebnisereignis ein,
   * sendet das Erlebnisereignis mit der API [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) .

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!UICONTROL ProductView]** und fügen Sie verschiedene Aufrufe zur Funktion `sendCommerceExperienceEvent` hinzu:

   1. Beim Modifikator `.task` innerhalb des `ATTrackingManager.trackingAuthorizationStatus` -Schließens. Dieser Modifikator `.task` wird aufgerufen, wenn die Produktansicht initialisiert und angezeigt wird. Daher möchten Sie ein Produktansichtsereignis zu diesem bestimmten Zeitpunkt senden.

      ```swift
      // Send productViews commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productViews", product: product)
      ```

   1. Für jede der Schaltflächen (<img src="assets/saveforlater.png" width="15"/>, <img src="assets/addtocart.png" width="20"/> und <img src="assets/purchase.png" width="20"/>) Fügen Sie in der Symbolleiste den entsprechenden Aufruf innerhalb des `ATTrackingManager.trackingAuthorizationStatus == .authorized` -Schließens hinzu:

      1. Für <img src="assets/saveforlater.png" width="15"/>

         ```swift
         // Send saveForLater commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
         ```

      1. Für <img src="assets/addtocart.png" width="20"/>

         ```swift
         // Send productListAdds commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
         ```

      1. Für <img src="assets/purchase.png" width="20"/>

         ```swift
         // Send purchase commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
         ```

>[!TIP]
>
>Wenn Sie für Android™ entwickeln, verwenden Sie Map (`java.util.Map`) als grundlegende Schnittstelle, um Ihre XDM-Payload zu erstellen.


### Benutzerdefinierte Feldergruppen

Stellen Sie sich vor, Sie möchten Bildschirmansichten und Interaktionen in der App selbst verfolgen. Denken Sie daran, für diesen Ereignistyp eine benutzerdefinierte Feldergruppe definiert zu haben.

* Identifizieren Sie in Ihrem Schema die Ereignisse, die Sie erfassen möchten.
  ![App-Interaktionsschema](assets/datacollection-appInteraction-schema.png)

* Beginnen Sie mit der Erstellung Ihres Objekts.

  >[!NOTE]
  >
  >* Standardfeldgruppen beginnen immer im Objektstamm.
  >
  >* Benutzerdefinierte Feldergruppen beginnen immer unter einem Objekt, das für Ihre Experience Cloud-Organisation eindeutig ist, in diesem Beispiel `_techmarketingdemos` .

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


* Sie können diese Datenstruktur jetzt verwenden, um eine `ExperienceEvent` zu erstellen.

  ```swift
  let event = ExperienceEvent(xdm: xdmData)
  ```

* Senden Sie das Ereignis und die Daten an Platform Edge Network.

  ```swift
  Edge.sendEvent(experienceEvent: event)
  ```


Erneut lassen Sie diesen Code in Ihr Xcode-Projekt implementieren.

1. Zur Vereinfachung definieren Sie zwei Funktionen in **[!UICONTROL MobileSDK]**. Navigieren Sie im Xcode-Projektnavigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** .

   1. Eine für App-Interaktionen. Fügen Sie diesen Code zur Funktion `func sendAppInteractionEvent(actionName: String)` hinzu:

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

      * richtet die XDM-Nutzlast als Wörterbuch ein, indem der Parameter aus der Funktion verwendet wird,
      * richtet mithilfe des Wörterbuchs ein Erlebnisereignis ein,
      * sendet das Erlebnisereignis mit der API [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) .


   1. Und eine für die Bildschirmverfolgung. Fügen Sie diesen Code zur Funktion `func sendTrackScreenEvent(stateName: String) ` hinzu:

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

      * richtet die XDM-Nutzlast als Wörterbuch ein, indem der Parameter aus der Funktion verwendet wird,
      * richtet mithilfe des Wörterbuchs ein Erlebnisereignis ein,
      * sendet das Erlebnisereignis mit der API [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) .

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]**.

   1. Fügen Sie den folgenden hervorgehobenen Code zum Schließen der Anmelde-Schaltfläche hinzu:

      ```swift
      // Send app interaction event
      MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
      ```

   1. Fügen Sie den folgenden hervorgehobenen Code zum Modifikator `onAppear` hinzu:

      ```swift
      // Send track screen event
      MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: login")
      ```

## Validierung

1. Lesen Sie den Abschnitt [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) , um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.

   1. Verschieben Sie das Assurance-Symbol nach links.
   1. Wählen Sie **[!UICONTROL Home]** in der Registerkartenleiste aus und überprüfen Sie, ob auf dem Startbildschirm eine **[!UICONTROL ECID]**, eine **[!UICONTROL E-Mail]** und eine **[!UICONTROL CRM-ID]** angezeigt werden.
   1. Wählen Sie in der Registerkartenleiste **[!DNL Products]** aus.
   1. Wählen Sie ein Produkt.
   1. Auswählen <img src="assets/saveforlater.png" width="15"/>.
   1. Auswählen <img src="assets/addtocart.png" width="20"/>.
   1. Auswählen <img src="assets/purchase.png" width="15"/>.

      <img src="./assets/mobile-app-events-3.png" width="300">


1. Suchen Sie in der Assurance-Benutzeroberfläche vom Anbieter **[!UICONTROL com.adobe.edge.conductor]** nach den Ereignissen **[!UICONTROL hitReceived]** .
1. Wählen Sie das Ereignis aus und überprüfen Sie die XDM-Daten im Objekt **[!UICONTROL messages]** . Alternativ können Sie ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) **[!UICONTROL Roh-Ereignis kopieren]** verwenden und einen Text- oder Code-Editor Ihrer Voreinstellung verwenden, um das Ereignis einzufügen und zu untersuchen.

   ![Validierung der Datenerfassung](assets/datacollection-validation.png)


## Nächste Schritte

Sie sollten jetzt über alle Tools verfügen, um Ihrer App die Datenerfassung hinzuzufügen. Sie können mehr Informationen darüber hinzufügen, wie der Benutzer mit Ihren Produkten in der App interagiert, und Sie können der App weitere App-Interaktionen und Screentracking-Aufrufe hinzufügen:

* Implementieren Sie die App, indem Sie Bestellungen, Checkout, leeren Warenkorb und andere Funktionen hinzufügen und relevante Commerce-Erlebnisereignisse zu dieser Funktion hinzufügen.
* Wiederholen Sie den Aufruf von `sendAppInteractionEvent` mit dem entsprechenden Parameter, um andere App-Interaktionen des Benutzers zu verfolgen.
* Wiederholen Sie den Aufruf von `sendTrackScreenEvent` mit dem entsprechenden Parameter, um die vom Benutzer in der App angezeigten Bildschirme zu verfolgen.

>[!TIP]
>
>Weitere Beispiele finden Sie in der [fertigen App](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) .


## Senden von Ereignissen an Analytics und Platform

Nachdem Sie die Ereignisse erfasst und an Platform Edge Network gesendet haben, werden sie an die Anwendungen und Dienste gesendet, die in Ihrem [Datastream](create-datastream.md) konfiguriert sind. In späteren Lektionen ordnen Sie diese Daten [Adobe Analytics](analytics.md), [Adobe Experience Platform](platform.md) und anderen Adobe Experience Cloud-Lösungen wie [Adobe Target](target.md) und Adobe Journey Optimizer zu.

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass sie Commerce-, App-Interaktionen- und Bildschirmverfolgungsereignisse im Adobe Experience Platform-Edge Network und allen Diensten verfolgt, die Sie in Ihrem Datastream definiert haben.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu zukünftigen Inhalten haben möchten, teilen Sie diese in diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Verarbeiten von WebViews](web-views.md)**
