---
title: Daten Analytics-Daten zuordnen
description: Erfahren Sie, wie Sie Daten für Adobe Analytics in einer App erfassen und zuordnen können.
solution: Data Collection,Experience Platform,Analytics
hide: true
source-git-commit: 5f178f4bd30f78dff3243b3f5bd2f9d11c308045
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 2%

---

# Analytics-Daten erfassen und zuordnen

Erfahren Sie, wie Sie mobile Daten Adobe Analytics zuordnen.

Die [event](events.md) Daten, die Sie in früheren Lektionen gesammelt und an Platform Edge Network gesendet haben, werden an die in Ihrem Datastream konfigurierten Dienste weitergeleitet, einschließlich Adobe Analytics. Sie ordnen die Daten den korrekten Variablen in Ihrer Report Suite zu.

![Architektur](assets/architecture-aa.png)

## Voraussetzungen

* Grundlegendes zum ExperienceEvent-Tracking.
* Erfolgreiches Senden von XDM-Daten in Ihrer Beispielanwendung.
* Für Adobe Analytics konfigurierter Datenspeicher

## Lernziele

In dieser Lektion werden Sie:

* Konfigurieren Sie Ihren Datenspeicher mit dem Adobe Analytics-Dienst.
* Verstehen Sie die automatische Zuordnung von Analytics-Variablen.
* Richten Sie Verarbeitungsregeln ein, um XDM-Daten Analytics-Variablen zuzuordnen.

## Hinzufügen des Adobe Analytics-Datenspeicherdiensts

Um Ihre XDM-Daten vom Edge-Netzwerk an Adobe Analytics zu senden, konfigurieren Sie den Adobe Analytics-Dienst für den Datastraam, den Sie im Rahmen von [Erstellen eines Datenspeichers](create-datastream.md).

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche die Option **[!UICONTROL Datenspeicher]** und Ihrem Datastream.

1. Wählen Sie anschließend ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Dienst hinzufügen]**.

1. Hinzufügen **[!UICONTROL Adobe Analytics]** aus dem [!UICONTROL Dienst] Liste,

1. Geben Sie den Namen der Report Suite aus Adobe Analytics ein, die Sie in **[!UICONTROL Report Suite-ID]**.

1. Aktivieren Sie den Dienst, indem Sie **[!UICONTROL Aktiviert]** auf.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Hinzufügen von Adobe Analytics als Datenspeicherdienst](assets/datastream-service-aa.png)


## Automatische Zuordnung

Viele der Standard-XDM-Felder werden automatisch Analytics-Variablen zugeordnet. Die vollständige Liste finden Sie [hier](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/adobe-analytics/automatically-mapped-vars.html?lang=en).

### Beispiel 1: s.products

Ein gutes Beispiel dafür ist die [Produktvariable](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/products.html?lang=en) die nicht mit Verarbeitungsregeln aufgefüllt werden können. Mit einer XDM-Implementierung übergeben Sie alle erforderlichen Daten in `productListItems` und `s.products` werden automatisch über die Analytics-Zuordnung ausgefüllt.

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

## Validierung mit Versicherung

Verwenden der [Assurance](assurance.md) Sie können bestätigen, dass Sie ein Erlebnisereignis senden, dass die XDM-Daten korrekt sind und die Analytics-Zuordnung erwartungsgemäß erfolgt. Beispiel:

1. Senden Sie ein productListAdds-Ereignis.

1. Anzeigen des ExperienceEvent-Treffers.

   ![xdm-Treffer von analytics](assets/analytics-assurance-experiencevent.png)

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
       "id" : "LLWS05.1-XS",
       "value" : 1
     }
   }
   // ...
   ```

1. Überprüfen Sie die **[!UICONTROL analytics.mapping]** -Ereignis.

   ![xdm-Treffer von analytics](assets/analytics-assurance-mapping.png)

Beachten Sie Folgendes in der Analytics-Zuordnung:

* **[!UICONTROL events]** mit `scAdd` basierend auf `commerce.productListAdds`.
* **[!UICONTROL pl]** (Produktvariable) mit einem verketteten Wert gefüllt werden, der auf `productListItems`.
* Es gibt weitere interessante Informationen in diesem Ereignis, einschließlich aller Kontextdaten.


## Zuordnung mit Kontextdaten

An Analytics weitergeleitete XDM-Daten werden in [Kontextdaten](https://experienceleague.adobe.com/docs/mobile-services/ios/getting-started-ios/proc-rules.html?lang=en) einschließlich sowohl standardmäßiger als auch benutzerdefinierter Felder.

Der Kontextdatenschlüssel wird nach dieser Syntax konstruiert:

```
a.x.[xdm path]
```

Beispiel:

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
>`_techmarketingdemos` durch den eindeutigen Wert Ihrer Organisation ersetzt.

Um diese XDM-Kontextdaten Ihren Analytics-Daten in Ihrer Report Suite zuzuordnen, können Sie:

* Fügen Sie die **[!UICONTROL Adobe Analytics ExperienceEvent Full Extension]** Feldergruppe in Ihr Schema ein.

  ![Feldergruppe &quot;Analytics ExperienceEvent FullExtension&quot;](assets/schema-analytics-extension.png)
* Erstellen Sie Regeln in Ihrer Tags-Eigenschaft, um die Kontextdaten den Feldern in der Feldergruppe Adobe Analytics ExperienceEvent Full Extension zuzuordnen. Zum Beispiel map `_techmarketingdemo.appinformation.appstatedetails.screenname` nach `_experience.analytics.customDimensions.eVars.eVar2`.

<!-- Old processing rules section
Here is what a processing rule using this data might look like:

* You **[!UICONTROL Overwrite value of]** (1) **[!UICONTROL App Screen Name (eVar2)]** (2) with the value of **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenname]** (3) if **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenname]** (4) **[!UICONTROL is set]** (5).

* You **[!UICONTROL Set event]** (6) **[!UICONTROL Add to Wishlist (Event 3)]** (7) to **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (8) if **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (9) **[!UICONTROL is set]** (10).

![analytics processing rules](assets/analytics-processing-rules.png)

>[!IMPORTANT]
>
>
>Some of the automatically mapped variables may not be available for use in processing rules.
>
>
>The first time you map to a processing rule, the interface does not show you the context data variables from the XDM object. To fix that select any value, Save, and come back to edit. All XDM variables should now appear.


Additional information about processing rules and context data can be found [here](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules.html?lang=en).

>[!TIP]
>
>Unlike previous mobile app implementations, there is no distinction between a page / screen views and other events. Instead you can increment the **[!UICONTROL Page View]** metric by setting the **[!UICONTROL Page Name]** dimension in a processing rule. Since you are collecting the custom `screenName` field in the tutorial, it is highly recommended to map screen name to **[!UICONTROL Page Name]** in a processing rule.

-->

>[!SUCCESS]
>
>Sie haben Ihre App eingerichtet, um Ihre Experience Edge XDM-Objekte Adobe Analytics-Variablen zuzuordnen, die den Adobe Analytics-Dienst in Ihrem Datenspeicher ermöglichen, und gegebenenfalls Verarbeitungsregeln verwenden.<br/> Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Daten an Experience Platform senden](platform.md)**
