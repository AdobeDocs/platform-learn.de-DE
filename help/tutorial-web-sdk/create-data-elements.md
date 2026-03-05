---
title: Erstellen von Datenelementen für Platform Web SDK
description: Erfahren Sie, wie Sie ein XDM-Objekt erstellen und ihm Datenelemente in Tags zuordnen. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Tags
jira: KT-15401
exl-id: d662ec46-de9b-44ba-974a-f81dfc842e68
source-git-commit: da65f13f95a6d1258655e8eebc76cf024221a610
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 2%

---

# Datenelemente erstellen

Erfahren Sie, wie Sie Datenelemente in Tags für Inhalts-, Commerce- und Identitätsdaten auf der [Demo-Website von Luma](https://luma.enablementadobe.com) erstellen. Füllen Sie dann Felder in Ihrem XDM-Schema aus.



## Lernziele

Am Ende dieser Lektion können Sie:

* Verstehen der verschiedenen Ansätze zum Zuordnen einer Datenschicht zu XDM
* Erstellen von Datenelementen zur Datenerfassung
* Zuordnen von Datenelementen zu einem XDM-Objekt


## Voraussetzungen

Sie wissen, was eine Datenschicht ist, und haben die vorherigen Lektionen im Tutorial abgeschlossen:

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Konfigurieren eines Identity-Namespace](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)


>[!IMPORTANT]
>
>Die Daten für diese Lektion stammen aus der `[!UICONTROL adobeDataLayer]` Datenschicht auf der [Luma-Site](https://luma.enablementadobe.com). Um die Datenschicht anzuzeigen, öffnen Sie die Entwicklerkonsole und geben Sie ein, `[!UICONTROL adobeDataLayer]` die vollständige verfügbare Datenschicht anzuzeigen.![adobeDataLayer-Datenschicht](assets/data-element-data-layer-new.png)


## Ansätze für Datenschichten

Es gibt mehrere Möglichkeiten, Daten aus Ihrer Datenschicht mithilfe der Tags-Funktion von Adobe Experience Platform XDM zuzuordnen. Im Folgenden finden Sie einige Vor- und Nachteile von drei verschiedenen Ansätzen. Es ist möglich, Ansätze zu kombinieren, falls gewünscht:

1. Implementieren von XDM in der Datenschicht
1. Zuordnen zu XDM in Tags
1. Zu XDM im Datenstrom zuordnen

>[!NOTE]
>
>Die Beispiele in diesem Tutorial folgen dem Ansatz Zu XDM in Tags zuordnen .


### Implementieren von XDM in der Datenschicht

Bei diesem Ansatz implementieren Webentwickler ein vollständig definiertes XDM-Objekt als Struktur für die Datenschicht. Anschließend ordnen Sie einfach die gesamte Datenschicht einem XDM-Objekt in Tags zu. Wenn Ihre Implementierung keinen Tag-Manager verwendet, kann dieser Ansatz ideal sein, da Sie mit dem Befehl „XDM sendEvent[ Daten direkt aus Ihrer Anwendung an XDM senden ](https://experienceleague.adobe.com/en/docs/experience-platform/edge/fundamentals/tracking-events#sending-xdm-data). Wenn Sie Tags verwenden, können Sie ein benutzerdefiniertes Code-Datenelement erstellen, das die gesamte Datenschicht als Passthrough-JSON-Objekt an das XDM erfasst. Anschließend ordnen Sie die Passthrough-JSON dem XDM-Objektfeld in der Aktion „Ereignis senden“ zu.

Im Folgenden finden Sie ein Beispiel dafür, wie die Datenschicht bei Verwendung des Adobe Client-Datenschichtformats aussehen würde:

+++Beispiel für XDM in Data Layer

```JSON
window.adobeDataLayer.push({
"eventType": "web.webPageDetails.pageViews",
"web":{
         "webInteraction":{
            "linkClicks":{
               "id":"",
               "value":""
            },
            "URL":"",
            "name":"",
            "region":"",
            "type":""
         },
         "webPageDetails":{
            "pageViews":{
               "id":"",
               "value":"1"
            },
            "URL":"https://luma.enablementadobe.com/",
            "isErrorPage":"",
            "isHomePage":"",
            "name":"luma:home",
            "server":"enablementadobe.com",
            "siteSection":"home",
            "viewName":""
         },
         "webReferrer":{
            "URL":"",
            "type":""
         }
      }
});
```

+++

Vorteile

* Beseitigt zusätzliche Schritte, um Datenschichtvariablen XDM zuzuordnen
* Die Bereitstellung kann schneller erfolgen, wenn Ihrem Web-Entwicklungs-Team auch das Tagging digitalen Verhaltens gehört

Nachteile

* Vollständige Abhängigkeit vom Entwicklungsteam und vom Entwicklungszyklus zur Aktualisierung der an XDM gesendeten Daten
* Eingeschränkte Flexibilität, da XDM die genaue Payload von der Datenschicht erhält
* Integrierte Tags-Funktionen wie Scraping, Persistenz und Funktionen für schnelle Bereitstellungen können nicht verwendet werden.
* Die Verwendung der Datenschicht für Pixel von Drittanbietern ist schwieriger (Sie sollten diese Pixel jedoch möglicherweise in die [Ereignisweiterleitung](setup-event-forwarding.md) verschieben).
* Keine Möglichkeit, die Daten zwischen der Datenschicht und XDM umzuwandeln

### Zuordnen zu XDM in Tags

Dieser Ansatz beinhaltet die Zuordnung einzelner Datenschichtvariablen zu Datenelementen in Tags und schließlich zu XDM. Dies ist der herkömmliche Implementierungsansatz unter Verwendung eines Tag-Management-Systems.

#### Vorteile

* Der flexibelste Ansatz, da Sie einzelne Variablen steuern und Daten transformieren können, bevor sie an XDM gesendet werden
* Kann Adobe Tags-Trigger und Scraping-Funktionen verwenden, um Daten an XDM zu übergeben
* Kann Datenelemente Client-seitig Pixel von Drittanbietern zuordnen

#### Nachteile

* Dauert seine Zeit, um die Datenschicht als Tags-Datenelemente zu rekonstruieren


>[!IMPORTANT]
>
>Wie bereits erwähnt, folgen die Beispiele in diesem Tutorial dem Ansatz Zu XDM in Tags zuordnen .

### Zu XDM im Datenstrom zuordnen

Dieser Ansatz verwendet Funktionen, die in die Datenstromkonfiguration integriert sind ([ für die Datenerfassung), ](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/data-prep) die Zuordnung von Datenschichtvariablen zu XDM in Tags übersprungen.

#### Vorteile

* Flexible Zuordnung einzelner Variablen zu XDM in einer Point-and-Click-Benutzeroberfläche
* Möglichkeit [ „Berechnung neuer Werte](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/functions) oder [Umwandlung von Datentypen](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/data-handling) aus einer Datenschicht, bevor sie an XDM gesendet wird

#### Nachteile

* Datenschichtvariablen können nicht als Datenelemente für Client-seitige Pixel von Drittanbietern verwendet werden, sie können jedoch bei der Ereignisweiterleitung verwendet werden
* Die Scraping-Funktion kann in Tags nicht verwendet werden
* Die Wartung ist komplexer, wenn die Zuordnung der Datenschicht sowohl in Tags als auch im Datenstrom erfolgt


>[!TIP]
>
> Google-Datenschicht
> 
> Wenn Ihr Unternehmen bereits Google Analytics verwendet und das herkömmliche Google-Datenschichtobjekt auf Ihrer Website hat, können Sie die [Google-Datenschichterweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/google-data-layer/overview) in Tags verwenden. Dadurch können Sie Adobe-Technologie schneller bereitstellen, ohne den Support von Ihrem IT-Team anfordern zu müssen. Wenn Sie die Google-Datenschicht XDM zuordnen, gehen Sie wie oben beschrieben vor.


## Erstellen von Datenelementen zur Erfassung der Datenschicht

Bevor Sie XDM-Felder ausfüllen, erfassen Sie zunächst die Datenpunkte, die Sie als Tag-Datenelemente benötigen:

1. Wechseln Sie zu **[!UICONTROL Datenelemente]** und wählen Sie **[!UICONTROL Datenelement hinzufügen]** (oder **[!UICONTROL Neues Datenelement erstellen]** wenn in der Tag-Eigenschaft keine Datenelemente vorhanden sind)

   ![Datenelement erstellen](assets/data-element-create.png)

1. Benennen Sie das Datenelement `Page Name`.
1. Verwenden Sie den **[!UICONTROL JavaScript]** Variablen **[!UICONTROL Datenelementtyp,]** auf den Wert in der Datenschicht von Luma zu verweisen: `adobeDataLayer.0.page.name`

1. Markieren Sie die Kästchen für **[!UICONTROL Kleinbuchstaben erzwingen]** und **[!UICONTROL Text bereinigen]**, um die Groß-/Kleinschreibung zu standardisieren und überflüssige Leerzeichen zu entfernen

1. Belassen Sie `None` als Einstellung **[!UICONTROL Speicherdauer]**, da dieser Wert auf jeder Seite anders ist

1. Wählen Sie **[!UICONTROL Speichern]**

   ![Datenelement „Seitenname“](assets/data-element-pageName.png)

Erstellen Sie diese zusätzlichen Datenelemente, indem Sie die gleichen Schritte ausführen:

* **`User Id`** zugeordnet zu
  `adobeDataLayer.0.user.id`

* **`User Logged In`** zugeordnet zu
  `adobeDataLayer.0.user.loggedIn`

* **`Ecommerce Product Id`** zugeordnet zu `adobeDataLayer.0.ecommerce.detail.products.0.id`
* **`Ecommerce Product Name`** zugeordnet zu `adobeDataLayer.0.ecommerce.detail.products.0.name`
* **`Ecommerce Purchase Id`** zugeordnet zu `adobeDataLayer.0.ecommerce.purchase.actionField.id`
* **`Ecommerce Product Category`** mit dem **[!UICONTROL Benutzerdefinierter Code]** **[!UICONTROL Datenelementtyp]** und dem folgenden benutzerdefinierten Code:

  ```javascript
  return adobeDataLayer[0].ecommerce.detail.products[0].category+":"+adobeDataLayer[0].ecommerce.detail.products[0].subcategory;
  ```

* **`Ecommerce Cart Products`** mit dem folgenden benutzerdefinierten Code:

  ```javascript
  const cartProducts = adobeDataLayer
  .flatMap(evt => Array.isArray(evt?.ecommerce?.cart?.items) ? evt.ecommerce.cart.items : [])
  .filter(item => item && item.id && item.name && item.brand)
  .map(({ id, name, brand }) => ({ id, name, brand }));
  
  return cartProducts;
  ```

* **`Ecommerce Purchase Products`** mit dem folgenden benutzerdefinierten Code:

  ```javascript
  const purchaseEvent = adobeDataLayer.find(e => e.event === "purchase");
  
  const currencyCode = purchaseEvent?.ecommerce?.currencyCode ?? "USD";
  
  const purchasedProducts = (purchaseEvent?.ecommerce?.purchase?.products || []).map(p => {
     const unitPrice = parseFloat(String(p.price).replace(/[^0-9.-]/g, "")) || 0;
     const qty = Number(p.quantity) || 0;
  
     return {
     SKU: p.id,                       // id -> SKU
     name: p.name,                    // name -> name
     quantity: qty,                   // quantity -> quantity
     priceTotal: unitPrice * qty,     // price -> priceTotal (unit price × quantity)
     currencyCode                     // "USD" -> currencyCode (from ecommerce.currencyCode)
     };
  });
  
  return(purchasedProducts);
  ```


>[!CAUTION]
>
>Der Datenelementtyp [!UICONTROL JavaScript] behandelt Array-Verweise als Punkte anstatt als Klammern, sodass das Verweisen auf das Datenelement Benutzername als `adobeDataLayer[0].page.name`**nicht funktioniert**.

## Erstellen variabler Datenelemente für XDM und Datenobjekte

Die soeben erstellten Datenelemente werden zum Erstellen eines XDM-Objekts (für Platform-Programme) und eines Datenobjekts (für Analytics, Target und Audience Manager) verwendet. Diese Objekte haben ihre eigenen speziellen Datenelemente namens **[!UICONTROL Variable]** Datenelemente, die sehr einfach zu erstellen sind.

Um das Datenelement „Variable“ für XDM zu erstellen, binden Sie es an das Schema, das Sie in der Lektion [Konfigurieren eines Schemas“ erstellt ](configure-schemas.md):

1. Wählen Sie **[!UICONTROL Datenelement hinzufügen]**
1. Benennen Sie Ihr Datenelement `XDM Variable`. Es wird empfohlen, den XDM-spezifischen Datenelementen „XDM“ voranzustellen, um Ihre Tag-Eigenschaft besser zu organisieren
1. Wählen Sie **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Erweiterung]**
1. Wählen Sie **[!UICONTROL Variable]** als **[!UICONTROL Datenelementtyp]**
1. Wählen Sie **[!UICONTROL XDM]** als **[!UICONTROL Eigenschaft]**
1. Wählen Sie die **[!UICONTROL Sandbox]**, in der Sie das Schema erstellt haben
1. Wählen Sie das entsprechende **[!UICONTROL Schema]** aus, in diesem Fall `Luma Web Event Data`
1. Wählen Sie **[!UICONTROL Speichern]**

   ![Variablendatenelement für XDM](assets/analytics-tags-data-element-xdm-variable.png)

Erstellen Sie anschließend das Datenelement Variable für Ihr Datenobjekt:

1. Wählen Sie **[!UICONTROL Datenelement hinzufügen]**
1. Benennen Sie Ihr Datenelement `Data Variable`.
1. Wählen Sie **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Erweiterung]**
1. Wählen Sie **[!UICONTROL Variable]** als **[!UICONTROL Datenelementtyp]**
1. Wählen Sie **[!UICONTROL data]** als **[!UICONTROL property]**
1. Wählen Sie die Experience Cloud-Lösungen aus, die Sie im Rahmen dieses Tutorials implementieren möchten
1. Wählen Sie **[!UICONTROL Speichern]**

   ![Variables Datenelement für das Datenobjekt](assets/data-element-data-variable.png)


Am Ende dieser Schritte sollten die folgenden Datenelemente erstellt sein:

| Datenelemente der Haupterweiterung | Datenelemente der Platform Web SDK-Erweiterung |
-----------------------------|-------------------------------
| `Ecommerce Cart Products` | `Data Variable` |
| `Ecommerce Product Category` | `XDM Variable` |
| `Ecommerce Product Id` | |
| `Ecommerce Product Name` | |
| `Ecommerce Purchase Id` | |
| `Ecommerce Purchase Products` | |
| `Page Name` | |
| `User Id` | |
| `User Logged In` | |

Wenn diese Datenelemente eingerichtet sind, können Sie mit einer Tag-Regel Daten an Platform Edge Network senden. Erfahren Sie jedoch zuerst mehr über das Erfassen von Identitäten mit Web SDK.

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
