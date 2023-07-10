---
title: Analytics-Zuordnung
description: Erfahren Sie, wie Sie Daten für Adobe Analytics in einer App erfassen.
solution: Data Collection,Experience Platform,Analytics
exl-id: 406dc687-643f-4f7b-a8e7-9aad1d0d481d
source-git-commit: adbe8f4476340abddebbf9231e3dde44ba328063
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# Analytics-Zuordnung

Erfahren Sie, wie Sie mobile Daten Adobe Analytics zuordnen.

Die [event](events.md) Daten, die Sie in früheren Lektionen gesammelt und an Platform Edge Network gesendet haben, werden an die in Ihrem Datastream konfigurierten Dienste weitergeleitet, einschließlich Adobe Analytics. Sie müssen die Daten nur den korrekten Variablen in Ihrer Report Suite zuordnen.

## Voraussetzungen

* Grundlegendes zum ExperienceEvent-Tracking.
* Erfolgreiches Senden von XDM-Daten in Ihrer Beispielanwendung.
* Für Adobe Analytics konfigurierter Datenspeicher

## Lernziele

In dieser Lektion werden Sie:

* Verstehen Sie die automatische Zuordnung von Analytics-Variablen.
* Richten Sie Verarbeitungsregeln ein, um XDM-Daten Analytics-Variablen zuzuordnen.

## Automatische Zuordnung

Viele der Standard-XDM-Felder werden automatisch Analytics-Variablen zugeordnet. Die vollständige Liste finden Sie [hier](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/adobe-analytics/automatically-mapped-vars.html?lang=en).

### Beispiel 1: s.products

Ein gutes Beispiel dafür ist die [Produktvariable](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/products.html?lang=en) die nicht mit Verarbeitungsregeln aufgefüllt werden können. Bei einer XDM-Implementierung werden alle erforderlichen Daten in productListItems und s.products automatisch über die Analytics-Zuordnung ausgefüllt.

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

Dies würde Folgendes zur Folge haben:

```
s.products = ";Yoga Mat;1;49.99,;Water Bottle,3,30.00"
```

>[!NOTE]
>
>Aktuell `productListItems[N].SKU` wird von der automatischen Zuordnung ignoriert.

### Beispiel 2 - scAdd

Wenn Sie genau hinsehen, haben alle Ereignisse zwei Felder `value` (erforderlich) und `id` (optional). Die `value` -Feld wird verwendet, um die Ereignisanzahl zu erhöhen. Die `id` -Feld wird für die Serialisierung verwendet.

Dieses Objekt:

```swift
"commerce" : {
  "productListAdds" : {
    "value" : 1
  }
}
```

Dies würde Folgendes zur Folge haben:

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

Dies würde Folgendes zur Folge haben:

```
s.events = "scAdd:321435"
```

## Validierung mit Versicherung

Verwenden der [Tool zur Qualitätssicherung](assurance.md) Sie können bestätigen, dass Sie ein ExperienceEvent senden, dass die XDM-Daten korrekt sind und die Analytics-Zuordnung erwartungsgemäß erfolgt. Beispiel:

1. Senden Sie ein productListAdds-Ereignis.

   ```swift
   var xdmData: [String: Any] = [
     "eventType": "commerce.productListAdds",
     "commerce": [
       "productListAdds": [
         "value": 1
       ]
     ],
     "productListItems": [
       [
         "name": "neve studio dance jacket - (blue)",
         "SKU": "test-sku",
         "priceTotal": 69
       ]
     ]
   ]
   let addToCartEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: addToCartEvent)
   ```

1. Anzeigen des ExperienceEvent-Treffers.

   ![xdm-Treffer von analytics](assets/mobile-analytics-assurance-xdm.png)

1. Überprüfen Sie den XDM-Teil der JSON.

   ```json
     "xdm" : {
       "productListItems" : [ {
         "priceTotal" : 69,
         "SKU" : "test-sku",
         "name" : "neve studio dance jacket - (blue)"
       } ],
       "timestamp" : "2021-10-22T22:03:37Z",
       "commerce" : {
         "productListAdds" : {
           "value" : 1
         }
       },
       "eventType" : "commerce.productListAdds",
       //...
     }
   ```

1. Überprüfen Sie die `analytics.mapping` -Ereignis.

   ![xdm-Treffer von analytics](assets/mobile-analytics-assurance-mapping.png)

Beachten Sie Folgendes in der Analytics-Zuordnung:

* &quot;events&quot;wurde mit &quot;scAdd&quot;gefüllt, basierend auf `commerce.productListAdds`.
* &quot;pl&quot;(Produktvariable) mit einem verketteten Wert gefüllt wurde, der auf `productListItems`.
* Es gibt weitere interessante Informationen in diesem Ereignis, einschließlich aller Kontextdaten.


## Zuordnung mit Kontextdaten

An Analytics weitergeleitete XDM-Daten werden in [Kontextdaten](https://experienceleague.adobe.com/docs/mobile-services/ios/getting-started-ios/proc-rules.html?lang=en) einschließlich sowohl standardmäßiger als auch benutzerdefinierter Felder.

Der Kontextdatenschlüssel wird nach dieser Syntax konstruiert:

```
a.x.[xdm path]
```

Beispiel:

```
//Standard Field
a.x.commerce.saveforlaters.value

//Custom Field
a.x._techmarketingdemos.appinformationa.appstatedetails.screenname
```

>[!NOTE]
>
>Benutzerdefinierte Felder werden unter Ihrer Experience Cloud-Organisationskennung platziert.
>
>&quot;_techmarketingdemos&quot;wird durch den eindeutigen Wert Ihrer Organisation ersetzt.

So könnte eine Verarbeitungsregel, die diese Daten verwendet, aussehen:

![Analytics-Verarbeitungsregeln](assets/mobile-analytics-processing-rules.png)

>[!IMPORTANT]
>
>
>Einige der automatisch zugeordneten Variablen stehen möglicherweise nicht zur Verwendung in Verarbeitungsregeln zur Verfügung.
>
>
>Wenn Sie eine Verarbeitungsregel zum ersten Mal zuordnen, zeigt die Benutzeroberfläche die Kontextdatenvariablen aus dem XDM-Objekt nicht an. Um das Problem zu beheben, bei dem ein beliebiger Wert ausgewählt wurde, speichern Sie und kehren Sie zur Bearbeitung zurück. Alle XDM-Variablen sollten jetzt angezeigt werden.


Weitere Informationen zu Verarbeitungsregeln und Kontextdaten finden Sie [here](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules.html?lang=en).

>[!TIP]
>
>Im Gegensatz zu früheren Implementierungen mobiler Apps gibt es keine Unterscheidung zwischen Seiten-/Bildschirmansichten und anderen Ereignissen. Stattdessen können Sie die **[!UICONTROL Seitenansicht]** Metrik durch Festlegen der **[!UICONTROL Seitenname]** -Dimension in einer Verarbeitungsregel. Da Sie die benutzerdefinierte `screenName` im Tutorial wird dringend empfohlen, dies der **[!UICONTROL Seitenname]** in einer Verarbeitungsregel.


Weiter: **[Experience Platform](platform.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)