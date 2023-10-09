---
title: Tracking von Ereignisdaten
description: Erfahren Sie, wie Sie Ereignisdaten in einer Mobile App verfolgen.
hide: true
exl-id: b926480b-b431-4db8-835c-fa1db6436a93
source-git-commit: d7410a19e142d233a6c6597de92f112b961f5ad6
workflow-type: tm+mt
source-wordcount: '1390'
ht-degree: 4%

---

# Tracking von Ereignisdaten

Erfahren Sie, wie Sie Ereignisse in einer Mobile App verfolgen.

Die Edge Network-Erweiterung stellt eine API zum Senden von Erlebnisereignissen an Platform Edge Network bereit. Ein Erlebnisereignis ist ein Objekt, das Daten enthält, die der XDM ExperienceEvent-Schemadefinition entsprechen. Sie erfassen einfach, was Benutzer in Ihrer mobilen App tun. Sobald Daten vom Platform Edge Network empfangen wurden, können sie an Anwendungen und Dienste weitergeleitet werden, die in Ihrem Datenspeicher konfiguriert sind, z. B. Adobe Analytics und Experience Platform. Weitere Informationen zum [Erlebnisereignisse](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) in der Produktdokumentation.

## Voraussetzungen

* Alle Paketabhängigkeiten sind in Ihrem Xcode-Projekt vorhanden.
* Registrierte Erweiterungen in **[!UICONTROL AppDelegate]**.
* Konfigurierte MobileCore-Erweiterung zur Verwendung Ihrer Entwicklung `appId`.
* Importierte SDKs
* Die App wurde erfolgreich erstellt und mit den oben genannten Änderungen ausgeführt.

## Lernziele

In dieser Lektion werden Sie

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
            "value": 1
          ]
      ]
  ]
  ```

   * `eventType`: Beschreibt das aufgetretene Ereignis und verwendet eine [bekannter Wert](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values) nach Möglichkeit.
   * `commerce.productViews.value`: der numerische oder boolesche Wert des Ereignisses. Wenn es sich um einen booleschen Wert (oder &quot;Zähler&quot;in Adobe Analytics) handelt, wird der Wert immer auf 1 gesetzt. Bei numerischen Ereignissen oder Währungsereignissen kann der Wert > 1 betragen.

* Identifizieren Sie in Ihrem Schema alle zusätzlichen Daten, die mit dem Ereignis zur Produktansicht für Commerce-Produkte verknüpft sind. Fügen Sie in diesem Beispiel **[!UICONTROL productListItems]** Dies ist ein Standardsatz von Feldern, die mit jedem Commerce-bezogenen Ereignis verwendet werden:

  ![Schema der Produktlistenelemente](assets/datacollection-prodListItems-schema.png)
   * Beachten Sie Folgendes: **[!UICONTROL productListItems]** ist ein Array, sodass mehrere Produkte bereitgestellt werden können.

* Um diese Daten hinzuzufügen, erweitern Sie Ihre `xdmData` -Objekt, um zusätzliche Daten einzuschließen:

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

* Sie können diese Datenstruktur jetzt verwenden, um eine `ExperienceEvent`:

  ```swift
  let productViewEvent = ExperienceEvent(xdm: xdmData)
  ```

* Senden Sie das Ereignis und die Daten mithilfe des `sendEvent` API:

  ```swift
  Edge.sendEvent(experienceEvent: productViewEvent)
  ```

Die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) Die API entspricht dem AEP Mobile SDK . [`MobileCore.trackAction`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackaction) und [`MobileCore.trackState`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackstate) API-Aufrufe. Siehe [Migration von der mobilen Analytics-Erweiterung zu Adobe Experience Platform Edge Network](https://developer.adobe.com/client-sdks/documentation/adobe-analytics/migrate-to-edge-network/) für weitere Informationen.

Sie werden diesen Code jetzt tatsächlich in Ihr Xcode-Projekt implementieren.
Sie haben verschiedene Commerce-produktbezogene Aktionen in Ihrer App und möchten Ereignisse basierend auf den vom Benutzer durchgeführten Aktionen senden:

* Ansicht: Tritt auf, wenn ein Benutzer ein bestimmtes Produkt anzeigt,
* Hinzufügen zum Warenkorb: wenn ein Benutzer auf <img src="assets/addtocart.png" width="20" /> in einem Produktdetailbildschirm,
* für später speichern: wenn ein Benutzer auf <img src="assets/saveforlater.png" width="15" /> in einem Produktdetailbildschirm,
* purchase: wenn ein Benutzer auf <img src="assets/purchase.png" width="20" /> in einem Produktdetailbildschirm.

Um das Senden von Commerce-bezogenen Erlebnisereignissen wiederverwendbar zu machen, verwenden Sie eine dedizierte Funktion:

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** im Xcode-Projekt-Navigator und fügen Sie Folgendes zum `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` -Funktion.

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
   * sendet das Erlebnisereignis mit der [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!UICONTROL ProductView]** im Xcode-Projektnavigator und fügen Sie verschiedene Aufrufe zum `sendCommerceExperienceEvent` Funktion:

   1. Im `.task` -Modifikator innerhalb der `ATTrackingManager.trackingAuthorizationStatus` Schließung. Diese `.task` -Modifikator wird aufgerufen, wenn die Produktansicht initialisiert und angezeigt wird. Daher möchten Sie zu diesem bestimmten Zeitpunkt ein Produktansichtsereignis senden.

      ```swift
      // Send productViews commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productViews", product: product)
      ```

   1. Für jede der Schaltflächen (<img src="assets/saveforlater.png" width="15" />, <img src="assets/addtocart.png" width="20" /> und <img src="assets/purchase.png" width="20" />) in der Symbolleiste den entsprechenden Aufruf innerhalb der `ATTrackingManager.trackingAuthorizationStatus == .authorized` Stilllegung:

      1. Für <img src="assets/saveforlater.png" width="15" />

         ```swift
         // Send saveForLaters commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
         ```

      1. Für <img src="assets/addtocart.png" width="20" />

         ```swift
         // Send productListAdds commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
         ```

      1. Für <img src="assets/purchase.png" width="20" />

         ```swift
         // Send purchases commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
         ```

>[!TIP]
>
>Wenn Sie sich für Android entwickeln, verwenden Sie Map (`java.util.Map`) als grundlegende Schnittstelle zum Erstellen Ihrer XDM-Payload.


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

1. Zur Vereinfachung definieren Sie zwei Funktionen in **[!UICONTROL MobileSDK]**. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in Ihrem Xcode-Projektnavigator.

   1. Eine für App-Interaktionen. Fügen Sie diesen Code zum `func sendAppInteractionEvent(actionName: String)` Funktion:

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
      * sendet das Erlebnisereignis mit der [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.


   1. Und eine für die Bildschirmverfolgung. Fügen Sie diesen Code zum `func sendTrackScreenEvent(stateName: String) ` Funktion:

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
      * sendet das Erlebnisereignis mit der [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]**.

   1. Fügen Sie den folgenden hervorgehobenen Code zum Schließen der Anmelde-Schaltfläche hinzu:

      ```swift
      // Send app interaction event
      MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
      ```

   1. Fügen Sie den folgenden hervorgehobenen Code zu `onAppear` modifier:

      ```swift
      // Send track screen event
      MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: login")
      ```

## Validierung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) -Abschnitt, um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.

   1. Verschieben Sie das Symbol &quot;Versicherung&quot;nach links.
   1. Auswählen **[!UICONTROL Startseite]** in der Registerkartenleiste und überprüfen Sie, ob eine **[!UICONTROL ECID]**, **[!UICONTROL Email]** und **[!UICONTROL CRM-ID]** im Startbildschirm.
   1. Auswählen **[!DNL Products]** in der Symbolleiste.
   1. Wählen Sie ein Produkt.
   1. Auswählen <img src="assets/saveforlater.png" width="15" />.
   1. Auswählen <img src="assets/addtocart.png" width="20" />.
   1. Auswählen <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-3.png" width="300">


1. Suchen Sie in der Assurance-Benutzeroberfläche nach der **[!UICONTROL hitReceived]** -Ereignisse aus **[!UICONTROL com.adobe.edge.konductor]** -Anbieter.
1. Wählen Sie das Ereignis aus und überprüfen Sie die XDM-Daten im **[!UICONTROL messages]** -Objekt. Alternativ können Sie ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) **[!UICONTROL Rohereignis kopieren]** und verwenden Sie einen Text- oder Code-Editor Ihrer Voreinstellung, um das Ereignis einzufügen und zu untersuchen.

   ![Datenerfassungsprüfung](assets/datacollection-validation.png)


## Nächste Schritte

Sie sollten jetzt über alle Tools verfügen, um Ihrer App die Datenerfassung hinzuzufügen. Sie können mehr Informationen darüber hinzufügen, wie der Benutzer mit Ihren Produkten in der App interagiert, und Sie können der App weitere App-Interaktionen und Screentracking-Aufrufe hinzufügen:

* Implementieren Sie die App, indem Sie Bestellungen, Checkout, leeren Warenkorb und andere Funktionen hinzufügen und relevante Commerce-Erlebnisereignisse zu dieser Funktion hinzufügen.
* Wiederholen Sie den Aufruf von `sendAppInteractionEvent` mit dem entsprechenden Parameter, um andere App-Interaktionen des Benutzers zu verfolgen.
* Wiederholen Sie den Aufruf von `sendTrackScreenEvent` mit dem entsprechenden Parameter zur Verfolgung der Bildschirme, die vom Benutzer in der App angezeigt wurden.

>[!TIP]
>
>Überprüfen Sie die [fertige App](https://git.corp.adobe.com/rmaur/Luma) für weitere Beispiele.


## Senden von Ereignissen an Analytics und Platform

Nachdem Sie die Ereignisse erfasst und an das Platform Edge Network gesendet haben, werden sie an die in Ihrer [datastream](create-datastream.md). In späteren Lektionen ordnen Sie diese Daten zu [Adobe Analytics](analytics.md), [Adobe Experience Platform](platform.md) und anderen Adobe Experience Cloud-Lösungen wie [Adobe Target](target.md) und Adobe Journey Optimizer.

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass sie Commerce-, App-Interaktionen- und Bildschirmverfolgungsereignisse im Adobe Experience Platform Edge Network und allen in Ihrem Datastream definierten Diensten verfolgt.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[WebViews verarbeiten](web-views.md)**
