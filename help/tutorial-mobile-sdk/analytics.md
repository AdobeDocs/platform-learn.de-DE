---
title: Mit dem Platform Mobile SDK erfasste Daten Adobe Analytics zuordnen
description: Erfahren Sie, wie Sie Daten für Adobe Analytics in einer App erfassen und zuordnen können.
solution: Data Collection,Experience Platform,Analytics
exl-id: 406dc687-643f-4f7b-a8e7-9aad1d0d481d
source-git-commit: 29b9771d81395676547b93ab3a1475a6a69c763f
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 2%

---

# Analytics-Daten erfassen und zuordnen

Erfahren Sie, wie Sie mobile Daten Adobe Analytics zuordnen.

Die [event](events.md) Daten, die Sie in früheren Lektionen gesammelt und an Platform Edge Network gesendet haben, werden an die in Ihrem Datastream konfigurierten Dienste weitergeleitet, einschließlich Adobe Analytics. Sie ordnen die Daten den korrekten Variablen in Ihrer Report Suite zu.

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

Um Ihre XDM-Daten vom Edge-Netzwerk an Adobe Analytics zu senden, konfigurieren Sie den Adobe Analytics-Dienst für den Datastraam, den Sie im Rahmen von [Erstellen eines Datenspeichers](create-datastream.md).

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche die Option **[!UICONTROL Datenspeicher]** und Ihrem Datastream.

1. Wählen Sie anschließend ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Dienst hinzufügen]**.

1. Hinzufügen **[!UICONTROL Adobe Analytics]** aus dem [!UICONTROL Dienst] Liste,

1. Geben Sie den Namen der Report Suite aus Adobe Analytics ein, die Sie in **[!UICONTROL Report Suite-ID]**.

1. Aktivieren Sie den Dienst, indem Sie **[!UICONTROL Aktiviert]** auf.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Hinzufügen von Adobe Analytics als Datenspeicherdienst](assets/datastream-service-aa.png)


## Automatische Zuordnung

Viele der Standard-XDM-Felder werden automatisch Analytics-Variablen zugeordnet. Die vollständige Liste finden Sie [hier](https://experienceleague.adobe.com/docs/analytics/implementation/aep-edge/variable-mapping.html?lang=en).

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
>Wenn `productListItems[].SKU` und `productListItems[].name` beide Daten enthalten, wird der Wert in `productListItems[].SKU` verwendet. Siehe [Analytics-Variablenzuordnung in Adobe Experience Edge](https://experienceleague.adobe.com/docs/analytics/implementation/aep-edge/variable-mapping.html?lang=en) für weitere Informationen.


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

Verwenden der [Assurance](assurance.md) Sie können bestätigen, dass Sie ein Erlebnisereignis senden, dass die XDM-Daten korrekt sind und die Analytics-Zuordnung erwartungsgemäß erfolgt.

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) -Abschnitt, um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.

1. Senden Sie eine **[!UICONTROL productListAdds]** -Ereignis (fügen Sie Ihrem Warenkorb ein Produkt hinzu).

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

### Feldgruppe verwenden

* Fügen Sie die **[!UICONTROL Adobe Analytics ExperienceEvent Full Extension]** Feldergruppe in Ihr Schema ein.

  ![Feldergruppe &quot;Analytics ExperienceEvent FullExtension&quot;](assets/schema-analytics-extension.png)

* Erstellen Sie XDM-Payloads in Ihrer App entsprechend der Feldergruppe &quot;Adobe Analytics ExperienceEvent Full Extension&quot;, ähnlich wie bei den Schritten im [Tracking von Ereignisdaten](events.md) Lektion oder
* Erstellen Sie Regeln in Ihrer Tags-Eigenschaft, die Regelaktionen zum Anhängen oder Ändern von Daten an die Feldergruppe &quot;Adobe Analytics ExperienceEvent Full Extension&quot;verwenden. Weitere Informationen finden Sie unter [Daten an SDK-Ereignisse anhängen](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/) oder [Daten in SDK-Ereignissen ändern](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/).


### Verarbeitungsregeln verwenden

So könnte eine Verarbeitungsregel, die diese Daten verwendet, aussehen:

* You **[!UICONTROL Wert von überschreiben]** Absatz 1 **[!UICONTROL App-Bildschirmname (eVar2)]** 2) mit dem Wert **[!UICONTROL a.x_techmarketingdemo.appinformation.appstatedetails.screename]** 3. wenn **[!UICONTROL a.x_techmarketingdemo.appinformation.appstatedetails.screename]** Absatz 4 **[!UICONTROL festgelegt ist]** Absatz 5.

* You **[!UICONTROL Ereignis festlegen]** Absatz 6 **[!UICONTROL Zu Wunschliste hinzufügen (Ereignis 3)]** 7 bis **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** 8, wenn **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** 9. **[!UICONTROL festgelegt ist]** 10.

![Analytics-Verarbeitungsregeln](assets/analytics-processing-rules.png)

>[!IMPORTANT]
>
>
>Einige der automatisch zugeordneten Variablen stehen möglicherweise nicht zur Verwendung in Verarbeitungsregeln zur Verfügung.
>
>
>Wenn Sie eine Verarbeitungsregel zum ersten Mal zuordnen, zeigt die Schnittstelle die Kontextdatenvariablen aus dem XDM-Objekt nicht an. Um das Problem zu beheben, bei dem ein beliebiger Wert ausgewählt wurde, speichern Sie und kehren Sie zur Bearbeitung zurück. Alle XDM-Variablen sollten jetzt angezeigt werden.


Weitere Informationen zu Verarbeitungsregeln und Kontextdaten finden Sie [here](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules.html?lang=en).

>[!TIP]
>
>Im Gegensatz zu früheren Implementierungen mobiler Apps gibt es keine Unterscheidung zwischen Seiten-/Bildschirmansichten und anderen Ereignissen. Stattdessen können Sie die **[!UICONTROL Seitenansicht]** Metrik durch Festlegen der **[!UICONTROL Seitenname]** -Dimension in einer Verarbeitungsregel. Da Sie die benutzerdefinierte `screenName` im Tutorial wird dringend empfohlen, den Namen des Bildschirms **[!UICONTROL Seitenname]** in einer Verarbeitungsregel.


>[!SUCCESS]
>
>Sie haben Ihre App eingerichtet, um Ihre Experience Edge XDM-Objekte Adobe Analytics-Variablen zuzuordnen, die den Adobe Analytics-Dienst in Ihrem Datenspeicher ermöglichen, und gegebenenfalls Verarbeitungsregeln verwenden.<br/> Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Daten an Experience Platform senden](platform.md)**
