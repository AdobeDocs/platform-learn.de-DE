---
title: Zuordnen von mit Platform Mobile SDK erfassten Daten zu Adobe Analytics
description: Erfahren Sie, wie Sie Daten für Adobe Analytics in einer Mobile App erfassen und zuordnen.
solution: Data Collection,Experience Platform,Analytics
jira: KT-14636
exl-id: 406dc687-643f-4f7b-a8e7-9aad1d0d481d
source-git-commit: 7dfa14081e87489f908084e93722f67643fd5984
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 1%

---

# Erfassen und Zuordnen von Analytics-Daten

Erfahren Sie, wie Sie Mobile-Daten Adobe Analytics zuordnen.

Die [Ereignis](events.md)-Daten, die Sie in früheren Lektionen erfasst und an das Platform-Edge Network gesendet haben, werden an die in Ihrem Datenstrom konfigurierten Services weitergeleitet, einschließlich Adobe Analytics. Sie ordnen die Daten den richtigen Variablen in Ihrer Report Suite zu.

![Architektur](assets/architecture-aa.png)

## Voraussetzungen

* Grundlagen zum ExperienceEvent-Tracking.
* XDM-Daten in der Beispielanwendung wurden erfolgreich gesendet.
* Eine Adobe Analytics Report Suite , die Sie für diese Lektion verwenden können.

## Lernziele

In dieser Lektion erfahren Sie Folgendes:

* Konfigurieren Ihres Datenstroms mit dem Adobe Analytics-Service.
* Verstehen der automatischen Zuordnung von Analytics-Variablen.
* Richten Sie Verarbeitungsregeln ein, um XDM-Daten Analytics-Variablen zuzuordnen.

## Adobe Analytics-Datenstrom-Service hinzufügen

Um Ihre XDM-Daten aus dem Edge Network an Adobe Analytics zu senden, konfigurieren Sie den Adobe Analytics-Service für den Datenstrom, den Sie im Rahmen von &quot;[ erstellen“ ](create-datastream.md).

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche **[!UICONTROL Datenströme]** und Ihren Datenstrom aus.

1. Wählen Sie dann ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Service hinzufügen]** aus.

1. **[!UICONTROL Adobe Analytics]** aus der Liste [!UICONTROL Service] hinzufügen,

1. Geben Sie den Namen der Report Suite aus Adobe Analytics ein, die Sie in verwenden möchten **[!UICONTROL Report Suite-ID]**.

1. Aktivieren Sie den Service, indem Sie **[!UICONTROL Aktiviert]** einschalten.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Adobe Analytics als Datenstrom-Service hinzufügen](assets/datastream-service-aa.png)


## Automatische Zuordnung

Viele der XDM-Standardfelder werden automatisch Analytics-Variablen zugeordnet. Die vollständige Liste finden Sie [hier](https://experienceleague.adobe.com/docs/analytics/implementation/aep-edge/variable-mapping.html?lang=de).

### #1 - s.products

Ein gutes Beispiel ist die [Variable „products](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/products.html?lang=de) die nicht mit Verarbeitungsregeln ausgefüllt werden kann. Bei einer XDM-Implementierung übergeben Sie alle erforderlichen Daten in `productListItems` und die `s.products` werden automatisch über die Analytics-Zuordnung gefüllt.

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

Ergebnisse in:

```
s.products = ";5829;1;49.99,9841;3;30.00"
```

>[!NOTE]
>
>Wenn `productListItems[].SKU` und `productListItems[].name` beide Daten enthalten, wird der Wert in `productListItems[].SKU` verwendet. Weitere Informationen finden [ unter „Analytics-Variablenzuordnung in Adobe Edge Experience ](https://experienceleague.adobe.com/docs/analytics/implementation/aep-edge/variable-mapping.html?lang=de)&quot;.


### #2 - scAdd

Wenn Sie genau hinschauen, haben alle Ereignisse zwei Felder `value` (erforderlich) und `id` (optional). Das Feld `value` wird verwendet, um die Ereignisanzahl zu erhöhen. Das `id` Feld wird für die Serialisierung verwendet.

Dieses Objekt:

```swift
"commerce" : {
  "productListAdds" : {
    "value" : 1
  }
}
```

Ergebnisse in:

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

Ergebnisse in:

```
s.events = "scAdd:321435"
```

## Mit Assurance validieren

Mit der [Assurance ](assurance.md) Sie bestätigen, dass Sie ein Erlebnisereignis senden, die XDM-Daten korrekt sind und die Analytics-Zuordnung erwartungsgemäß erfolgt.

1. Lesen Sie den Abschnitt [Setup-Anweisungen](assurance.md#connecting-to-a-session), um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.

1. Senden Sie **[!UICONTROL Ereignis „productListAdds]** (fügen Sie dem Warenkorb ein Produkt hinzu).

1. Anzeigen des ExperienceEvent-Treffers.

   ![Analytics XDM-Treffer](assets/analytics-assurance-experiencevent.png)

1. Überprüfen Sie den XDM-Teil der JSON-Datei.

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

1. Überprüfen Sie das **[!UICONTROL analytics.mapping]** Ereignis.

   ![Analytics XDM-Treffer](assets/analytics-assurance-mapping.png)

Beachten Sie Folgendes in der Analytics-Zuordnung:

* **[!UICONTROL Ereignisse]** werden basierend auf `commerce.productListAdds` mit `scAdd` gefüllt.
* **[!UICONTROL pl]** (Variable „products„) werden basierend auf `productListItems` mit einem verketteten Wert gefüllt.
* Es gibt weitere interessante Informationen in diesem Ereignis, einschließlich aller Kontextdaten.


## Zuordnung mit Kontextdaten

An Analytics weitergeleitete XDM-Daten werden in [Kontextdaten](https://experienceleague.adobe.com/docs/mobile-services/ios/getting-started-ios/proc-rules.html?lang=de) einschließlich standardmäßiger und benutzerdefinierter Felder, konvertiert.

Der Kontextdatenschlüssel wird mit dieser Syntax erstellt:

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



Um diese XDM-Kontextdaten Ihren Analytics-Daten in Ihrer Report Suite zuzuordnen, haben Sie folgende Möglichkeiten:

### Verwenden einer Feldergruppe

* Fügen Sie die Feldergruppe **[!UICONTROL Adobe Analytics ExperienceEvent Full Extension]** zu Ihrem Schema hinzu.

  ![Analytics ExperienceEvent FullExtension-Feldergruppe](assets/schema-analytics-extension.png)

* Erstellen Sie XDM-Payloads in Ihrer App entsprechend der Adobe Analytics ExperienceEvent Full Extension-Feldergruppe, ähnlich dem, was Sie in der Lektion [Nachverfolgen von ](events.md)) oder
* Erstellen Sie Regeln in Ihrer Tags-Eigenschaft, die Regelaktionen verwenden, um Daten an die Feldergruppe Adobe Analytics ExperienceEvent Full Extension anzuhängen oder zu ändern. Weitere Informationen finden Sie unter [Anhängen von Daten an SDK-](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/) oder [Ändern von Daten in SDK-Ereignissen](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/).


### Merchandising-eVars

Wenn Sie [Merchandising-eVars](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/merchandising-evars.html?lang=de) in Ihrer Analytics-Einrichtung verwenden, um z. B. die Farbe von Produkten wie `&&products = ...;evar1=red;event10=50,...;evar1=blue;event10=60` zu erfassen, müssen Sie Ihre XDM-Payload, die Sie unter &quot;[ von Ereignisdaten“ definiert haben](events.md) erweitern, um diese Merchandising-Informationen zu erfassen.

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


### Verwenden von Verarbeitungsregeln

So könnte eine Verarbeitungsregel, die diese Daten verwendet, aussehen:

* Sie **[!UICONTROL Wert von]** (1) **[!UICONTROL App Screen Name (eVar2)]** (2) mit dem Wert von **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenName]** (3) überschreiben, wenn **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenName]** (4) **[!UICONTROL festgelegt]** (5).

* Sie **[!UICONTROL Ereignis festlegen]** (6) **[!UICONTROL Zur Wunschliste hinzufügen (Ereignis 3)]** (7) auf **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (8), wenn **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (9) **[!UICONTROL festgelegt ist]** (10).

![Analytics-Verarbeitungsregeln](assets/analytics-processing-rules.png)

>[!IMPORTANT]
>
>
>Einige der automatisch zugeordneten Variablen sind möglicherweise nicht für die Verwendung in Verarbeitungsregeln verfügbar.
>
>
>Wenn Sie eine Verarbeitungsregel zum ersten Mal zuordnen, zeigt die Benutzeroberfläche die Kontextdatenvariablen aus dem XDM-Objekt nicht an. Um dies zu beheben, wählen Sie einen beliebigen Wert aus, speichern Sie und kehren Sie zur Bearbeitung zurück. Alle XDM-Variablen sollten jetzt angezeigt werden.


Weitere Informationen zu Verarbeitungsregeln und Kontextdaten finden Sie [hier](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules.html?lang=de).

>[!TIP]
>
>Im Gegensatz zu vorherigen Mobile-App-Implementierungen gibt es keinen Unterschied zwischen einer Seiten-/Bildschirmansicht und anderen Ereignissen. Stattdessen können Sie die Metrik **[!UICONTROL Seitenansicht]** erhöhen, indem Sie die Dimension **[!UICONTROL Seitenname]** in einer Verarbeitungsregel festlegen. Da Sie das benutzerdefinierte `screenName` im Tutorial erfassen, wird dringend empfohlen, den Bildschirmnamen in einer Verarbeitungsregel **[!UICONTROL Seitenname]** zuzuordnen.

## Migration von der Analytics Mobile-Erweiterung

Wenn Sie Ihre Mobile App mit der [Adobe Analytics Mobile-Erweiterung entwickelt ](https://developer.adobe.com/client-sdks/solution/adobe-analytics/#add-analytics-to-your-application), haben Sie höchstwahrscheinlich [`MobileCore.trackAction`](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackaction)- und [`MobileCore.trackState`](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackstate)-API-Aufrufe verwendet.

Wenn Sie sich für die Migration entscheiden, um das empfohlene Edge Network zu verwenden, haben Sie Optionen:

* Implementieren Sie die Erweiterung [Edge Network ](configure-tags.md#extension-configuration) und verwenden Sie die [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#sendevent) APIs, wie in der Lektion [Nachverfolgen von Ereignisdaten“ ](events.md). Dieses Tutorial konzentriert sich auf diese Implementierung.
* Implementieren Sie die [Edge Bridge](https://developer.adobe.com/client-sdks/solution/adobe-analytics/migrate-to-edge-network/#implement-the-edge-bridge-extension)Erweiterung und verwenden Sie weiterhin Ihre [`MobileCore.trackAction`](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackaction) und [`MobileCore.trackState`](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackstate) API-Aufrufe. Weitere [ und ein separates Tutorial finden Sie unter ](https://developer.adobe.com/client-sdks/solution/adobe-analytics/migrate-to-edge-network/#implement-the-edge-bridge-extension)Implementieren der Edge Bridge-Erweiterung“.




>[!SUCCESS]
>
>Sie haben Ihre App so eingerichtet, dass Ihre XDM-Objekte von Experience Edge Adobe Analytics-Variablen zugeordnet werden, sodass der Adobe Analytics-Service in Ihrem Datenstrom aktiviert ist und gegebenenfalls Verarbeitungsregeln verwendet werden können.<br/> Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Daten an Experience Platform senden](platform.md)**
