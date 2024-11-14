---
title: Mit dem Platform Mobile SDK erfasste Daten Adobe Analytics zuordnen
description: Erfahren Sie, wie Sie Daten für Adobe Analytics in einer App erfassen und zuordnen können.
solution: Data Collection,Experience Platform,Analytics
jira: KT-14636
exl-id: 406dc687-643f-4f7b-a8e7-9aad1d0d481d
source-git-commit: 7dfa14081e87489f908084e93722f67643fd5984
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 1%

---

# Analytics-Daten erfassen und zuordnen

Erfahren Sie, wie Sie mobile Daten Adobe Analytics zuordnen.

Die [event](events.md) -Daten, die Sie in früheren Lektionen erfasst und an Platform Edge Network gesendet haben, werden an die in Ihrem Datastream konfigurierten Dienste weitergeleitet, einschließlich Adobe Analytics. Sie ordnen die Daten den korrekten Variablen in Ihrer Report Suite zu.

![Architektur](assets/architecture-aa.png)

## Voraussetzungen

* Grundlegendes zum ExperienceEvent-Tracking.
* Erfolgreiches Senden von XDM-Daten in Ihrer Beispielanwendung.
* Eine Adobe Analytics Report Suite, die Sie für diese Lektion verwenden können.

## Lernziele

In dieser Lektion werden Sie:

* Konfigurieren Sie Ihren Datenspeicher mit dem Adobe Analytics-Dienst.
* Verstehen Sie die automatische Zuordnung von Analytics-Variablen.
* Richten Sie Verarbeitungsregeln ein, um XDM-Daten Analytics-Variablen zuzuordnen.

## Hinzufügen des Adobe Analytics-Datenspeicherdiensts

Um Ihre XDM-Daten vom Edge Network an Adobe Analytics zu senden, konfigurieren Sie den Adobe Analytics-Dienst für den Datastream, den Sie im Rahmen von [Erstellen eines Datenspeichers](create-datastream.md) eingerichtet haben.

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche **[!UICONTROL Datastreams]** und Ihren Datenspeicher aus.

1. Wählen Sie dann ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add Service]** aus.

1. Fügen Sie **[!UICONTROL Adobe Analytics]** aus der Liste [!UICONTROL Service] hinzu,

1. Geben Sie den Namen der Report Suite aus Adobe Analytics ein, die Sie in **[!UICONTROL Report Suite-ID]** verwenden möchten.

1. Aktivieren Sie den Dienst, indem Sie **[!UICONTROL Aktiviert]** aktivieren.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Hinzufügen von Adobe Analytics als Datastraam-Dienst](assets/datastream-service-aa.png)


## Automatische Zuordnung

Viele der Standard-XDM-Felder werden automatisch Analytics-Variablen zugeordnet. Die vollständige Liste finden Sie [hier](https://experienceleague.adobe.com/docs/analytics/implementation/aep-edge/variable-mapping.html?lang=en).

### Beispiel 1: s.products

Ein gutes Beispiel ist die Variable [products](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/products.html?lang=en) , die nicht mit Verarbeitungsregeln aufgefüllt werden kann. Bei einer XDM-Implementierung werden alle erforderlichen Daten in `productListItems` und `s.products` automatisch über die Analytics-Zuordnung ausgefüllt.

Dieses Objekt:

```swift
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
```

führt zu:

```
s.products = ";5829;1;49.99,9841;3;30.00"
```

>[!NOTE]
>
>Wenn `productListItems[].SKU` und `productListItems[].name` beide Daten enthalten, wird der Wert in `productListItems[].SKU` verwendet. Weitere Informationen finden Sie unter [Analytics-Variablenzuordnung in Adobe Experience Edge](https://experienceleague.adobe.com/docs/analytics/implementation/aep-edge/variable-mapping.html?lang=en) .


### Beispiel 2 - scAdd

Wenn Sie genau hinsehen, haben alle Ereignisse zwei Felder: `value` (erforderlich) und `id` (optional). Das Feld `value` wird verwendet, um die Ereignisanzahl zu erhöhen. Das Feld `id` wird für die Serialisierung verwendet.

Dieses Objekt:

```swift
"commerce" : {
  "productListAdds" : {
    "value" : 1
  }
}
```

führt zu:

```
s.events = "scAdd"
```

Dieses Objekt:

```swift
"commerce" : {
  "productListAdds" : {
    "value" : 1,
    "id": "321435"
  }
}
```

führt zu:

```
s.events = "scAdd:321435"
```

## Mit Assurance validieren

Mit dem [Assurance](assurance.md) können Sie bestätigen, dass Sie ein Erlebnisereignis senden, die XDM-Daten korrekt sind und die Analytics-Zuordnung erwartungsgemäß erfolgt.

1. Lesen Sie den Abschnitt [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) , um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.

1. Senden Sie ein **[!UICONTROL productListAdds]** -Ereignis (fügen Sie Ihrem Warenkorb ein Produkt hinzu).

1. Anzeigen des ExperienceEvent-Treffers.

   ![analytics xdm hit](assets/analytics-assurance-experiencevent.png)

1. Überprüfen Sie den XDM-Teil der JSON.

   ```json
   "xdm" : {
     "productListItems" : [ {
       "SKU" : "LLWS05.1-XS",
       "name" : "Desiree Fitness Tee",
       "priceTotal" : 24
     } ],
   "timestamp" : "2023-08-04T12:53:37.662Z",
   "eventType" : "commerce.productListAdds",
   "commerce" : {
     "productListAdds" : {
       "value" : 1
     }
   }
   // ...
   ```

1. Überprüfen Sie das Ereignis **[!UICONTROL analytics.mapping]** .

   ![analytics xdm hit](assets/analytics-assurance-mapping.png)

Beachten Sie Folgendes in der Analytics-Zuordnung:

* **[!UICONTROL events]** werden mit `scAdd` basierend auf `commerce.productListAdds` aufgefüllt.
* **[!UICONTROL pl]** (Variable &quot;products&quot;) wird mit einem verketteten Wert gefüllt, der auf `productListItems` basiert.
* Es gibt weitere interessante Informationen in diesem Ereignis, einschließlich aller Kontextdaten.


## Zuordnung mit Kontextdaten

An Analytics weitergeleitete XDM-Daten werden in [Kontextdaten](https://experienceleague.adobe.com/docs/mobile-services/ios/getting-started-ios/proc-rules.html?lang=en) konvertiert, die sowohl standardmäßige als auch benutzerdefinierte Felder enthalten.

Der Kontextdatenschlüssel wird nach dieser Syntax konstruiert:

```
a.x.[xdm path]
```

z. B.:

```
// Standard Field
a.x.commerce.saveforlaters.value

// Custom Field
a.x._techmarketingdemos.appinformation.appstatedetails.screenname
```

>[!NOTE]
>
>Benutzerdefinierte Felder werden unter Ihrer Experience Cloud-Organisationskennung platziert.
>
>`_techmarketingdemos` wird durch den eindeutigen Wert Ihrer Organisation ersetzt.



Um diese XDM-Kontextdaten Ihren Analytics-Daten in Ihrer Report Suite zuzuordnen, können Sie:

### Feldgruppe verwenden

* Fügen Sie Ihrem Schema die Feldergruppe **[!UICONTROL Adobe Analytics ExperienceEvent Full Extension]** hinzu.

  ![Analytics ExperienceEvent FullExtension-Feldergruppe](assets/schema-analytics-extension.png)

* Erstellen Sie XDM-Payloads in Ihrer App entsprechend der Feldergruppe &quot;Adobe Analytics ExperienceEvent Full Extension&quot;, ähnlich wie in der Lektion [Ereignisdaten verfolgen](events.md) beschrieben, oder
* Erstellen Sie Regeln in Ihrer Tags-Eigenschaft, die Regelaktionen zum Anhängen oder Ändern von Daten an die Feldergruppe &quot;Adobe Analytics ExperienceEvent Full Extension&quot;verwenden. Weitere Informationen finden Sie unter [Daten an SDK-Ereignisse anhängen](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/) oder [Daten in SDK-Ereignissen ändern](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/).


### Merchandising-eVars

Wenn Sie [Merchandising-eVars](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/merchandising-evars.html?lang=en) in Ihrem Analytics-Setup verwenden, z. B. um die Farbe von Produkten zu erfassen, z. B. `&&products = ...;evar1=red;event10=50,...;evar1=blue;event10=60`, müssen Sie Ihre XDM-Payload erweitern, die Sie in [Tracking von Ereignisdaten](events.md) definiert haben, um diese Merchandising-Informationen zu erfassen.

* In JSON:

  ```json
  {
    "productListItems": [
        {
            "SKU": "LLWS05.1-XS",
            "name": "Desiree Fitness Tee",
            "priceTotal": 24,
            "_experience": {
                "analytics": {
                    "events1to100": {
                        "event10": {
                            "value": 50
                        }
                    },
                    "customDimensions": {
                        "eVars": {
                            "eVar1": "red",
                        }
                    }
                }
            }
        }
    ],
    "eventType": "commerce.productListAdds",
    "commerce": {
        "productListAdds": {
            "value": 1
        }
    }
  }
  ```

* Im Code:

  ```swift
  var xdmData: [String: Any] = [
    "productListItems": [
      [
        "name":  productName,
        "SKU": sku,
        "priceTotal": priceString,
        "_experience" : [
          "analytics": [
            "events1to100": [
              "event10": [
                "value:": value
              ]
            ],
            "customDimensions": [
              "eVars": [
                "eVar1": color
              ]
            ]
          ]
        ]
      ]
    ],
    "eventType": "commerce.productViews",
    "commerce": [
      "productViews": [
        "value": 1
      ]
    ]
  ]
  ```


### Verarbeitungsregeln verwenden

So könnte eine Verarbeitungsregel, die diese Daten verwendet, aussehen:

* Sie **[!UICONTROL überschreiben den Wert]** (1) **[!UICONTROL App Screen Name (eVar 2)]** (2) mit dem Wert **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenname]** (3), wenn **[!UICONTROL a.x_techmarketingdemo.appinformation.appstatedetails.screenname]**} (4) **[!UICONTROL ist festgelegt]** (5).

* Sie **[!UICONTROL Legen Sie event]** (6) **[!UICONTROL Add to Wishlist (Event 3)]** (7) auf **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (8) fest, wenn **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (9) **[!UICONTROL auf]** (10) gesetzt ist.

![Analytics-Verarbeitungsregeln](assets/analytics-processing-rules.png)

>[!IMPORTANT]
>
>
>Einige der automatisch zugeordneten Variablen stehen möglicherweise nicht zur Verwendung in Verarbeitungsregeln zur Verfügung.
>
>
>Wenn Sie eine Verarbeitungsregel zum ersten Mal zuordnen, zeigt die Schnittstelle die Kontextdatenvariablen aus dem XDM-Objekt nicht an. Um das Problem zu beheben, bei dem ein beliebiger Wert ausgewählt wurde, speichern Sie und kehren Sie zur Bearbeitung zurück. Alle XDM-Variablen sollten jetzt angezeigt werden.


Weitere Informationen zu Verarbeitungsregeln und Kontextdaten finden Sie [hier](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules.html?lang=en).

>[!TIP]
>
>Im Gegensatz zu früheren Implementierungen mobiler Apps gibt es keine Unterscheidung zwischen Seiten-/Bildschirmansichten und anderen Ereignissen. Stattdessen können Sie die Metrik **[!UICONTROL Seitenansicht]** erhöhen, indem Sie in einer Verarbeitungsregel die Dimension **[!UICONTROL Seitenname]** festlegen. Da Sie das benutzerdefinierte Feld `screenName` im Tutorial erfassen, wird dringend empfohlen, den Bildschirmnamen in einer Verarbeitungsregel **[!UICONTROL Seitennamen]** zuzuordnen.

## Migration von der mobilen Analytics-Erweiterung

Wenn Sie Ihre Mobile App mit der mobilen Erweiterung [Adobe Analytics ](https://developer.adobe.com/client-sdks/solution/adobe-analytics/#add-analytics-to-your-application) entwickelt haben, haben Sie höchstwahrscheinlich [`MobileCore.trackAction`](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackaction) und [`MobileCore.trackState`](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackstate) API-Aufrufe verwendet.

Wenn Sie sich für eine Migration zur Verwendung des empfohlenen Edge Networks entscheiden, haben Sie folgende Optionen:

* Implementieren Sie die [Edge Network-Erweiterung](configure-tags.md#extension-configuration) und verwenden Sie die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#sendevent)-APIs, wie in der Lektion zum [Tracking von Ereignisdaten](events.md) dargestellt. Dieses Tutorial konzentriert sich auf diese Implementierung.
* Implementieren Sie die Erweiterung [Edge Bridge](https://developer.adobe.com/client-sdks/solution/adobe-analytics/migrate-to-edge-network/#implement-the-edge-bridge-extension) und verwenden Sie weiterhin Ihre API-Aufrufe [`MobileCore.trackAction`](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackaction) und [`MobileCore.trackState`](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackstate). Weitere Informationen und ein separates Tutorial finden Sie unter [Implementieren der Edge Bridge-Erweiterung](https://developer.adobe.com/client-sdks/solution/adobe-analytics/migrate-to-edge-network/#implement-the-edge-bridge-extension) .




>[!SUCCESS]
>
>Sie haben Ihre App eingerichtet, um Ihre Experience Edge-XDM-Objekte Adobe Analytics-Variablen zuzuordnen, die den Adobe Analytics-Dienst in Ihrem Datenspeicher ermöglichen, und gegebenenfalls Verarbeitungsregeln verwenden.<br/> Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu zukünftigen Inhalten haben möchten, teilen Sie diese in diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Daten an Experience Platform senden](platform.md)**
