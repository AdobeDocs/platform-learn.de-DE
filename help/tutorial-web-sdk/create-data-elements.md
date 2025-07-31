---
title: Erstellen von Datenelementen für Platform Web SDK
description: Erfahren Sie, wie Sie ein XDM-Objekt erstellen und ihm Datenelemente in Tags zuordnen. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Tags
jira: KT-15401
exl-id: d662ec46-de9b-44ba-974a-f81dfc842e68
source-git-commit: 7ccbaaf4db43921f07c971c485e1460a1a7f0334
workflow-type: tm+mt
source-wordcount: '1336'
ht-degree: 2%

---

# Datenelemente erstellen

Erfahren Sie, wie Sie Datenelemente in Tags für Inhalts-, Commerce- und Identitätsdaten auf der [Demo-Site von Luma](https://luma.enablementadobe.com/content/luma/us/en.html) erstellen. Füllen Sie dann Felder in Ihrem XDM-Schema mit dem Datenelementtyp Variable der Adobe Experience Platform Web SDK-Erweiterung aus.

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
>Die Daten für diese Lektion stammen aus der `[!UICONTROL digitalData]` Datenschicht auf der Luma-Site. Um die Datenschicht anzuzeigen, öffnen Sie die Entwicklerkonsole und geben Sie ein, `[!UICONTROL digitalData]` die vollständige verfügbare Datenschicht anzuzeigen.![digitalData-Datenschicht](assets/data-element-data-layer.png)


## Ansätze für Datenschichten

Es gibt mehrere Möglichkeiten, Daten aus Ihrer Datenschicht mithilfe der Tags-Funktion von Adobe Experience Platform XDM zuzuordnen. Im Folgenden finden Sie einige Vor- und Nachteile von drei verschiedenen Ansätzen. Es ist möglich, Ansätze zu kombinieren, falls gewünscht:

1. Implementieren von XDM in der Datenschicht
1. Zuordnen zu XDM in Tags
1. Zu XDM im Datenstrom zuordnen

>[!NOTE]
>
>Die Beispiele in diesem Tutorial folgen dem Ansatz Zu XDM in Tags zuordnen .


### Implementieren von XDM in der Datenschicht

Dieser Ansatz beinhaltet die Verwendung des vollständig definierten XDM-Objekts als Struktur für Ihre Datenschicht. Anschließend ordnen Sie die gesamte Datenschicht einem XDM-Objekt-Datenelement in Tags zu. Wenn Ihre Implementierung keinen Tag-Manager verwendet, kann dieser Ansatz ideal sein, da Sie mit dem Befehl „XDM sendEvent[ Daten direkt aus Ihrer Anwendung an XDM senden ](https://experienceleague.adobe.com/de/docs/experience-platform/edge/fundamentals/tracking-events#sending-xdm-data). Wenn Sie Tags verwenden, können Sie ein benutzerdefiniertes Code-Datenelement erstellen, das die gesamte Datenschicht als Passthrough-JSON-Objekt an das XDM erfasst. Anschließend ordnen Sie die Passthrough-JSON dem XDM-Objektfeld in der Aktion „Ereignis senden“ zu.

Im Folgenden finden Sie ein Beispiel dafür, wie die Datenschicht bei Verwendung des Adobe Client-Datenschichtformats aussehen würde:

+++XDM in Data Layer-Beispiel

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
* Die Verwendung der Datenschicht für Pixel von Drittanbietern ist schwieriger (Sie sollten diese Pixel jedoch möglicherweise in die [Ereignisweiterleitung“ ](setup-event-forwarding.md)!
* Keine Möglichkeit, die Daten zwischen der Datenschicht und XDM umzuwandeln

### Zuordnen der Datenschicht in Tags

Dieser Ansatz beinhaltet die Zuordnung einzelner Datenschichtvariablen ODER Datenschichtobjekte zu Datenelementen in Tags und schließlich zu XDM. Dies ist der herkömmliche Implementierungsansatz unter Verwendung eines Tag-Management-Systems.

#### Vorteile

* Der flexibelste Ansatz, da Sie einzelne Variablen steuern und Daten transformieren können, bevor sie an XDM gesendet werden
* Kann Adobe Tags-Trigger und Scraping-Funktionen verwenden, um Daten an XDM zu übergeben
* Kann Datenelemente Client-seitig Pixel von Drittanbietern zuordnen

#### Nachteile

* benötigt Zeit, um die Datenschicht als Datenelemente zu rekonstruieren


>[!TIP]
>
> Google-Datenschicht
> 
> Wenn Ihr Unternehmen bereits Google Analytics verwendet und das herkömmliche Google-Datenschichtobjekt auf Ihrer Website hat, können Sie die [Google-Datenschichterweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/client/google-data-layer/overview) in Tags verwenden. Dadurch können Sie Adobe-Technologie schneller bereitstellen, ohne den Support von Ihrem IT-Team anfordern zu müssen. Wenn Sie die Google-Datenschicht XDM zuordnen, gehen Sie wie oben beschrieben vor.

### Zu XDM im Datenstrom zuordnen

Dieser Ansatz verwendet Funktionen, die in die Datenstromkonfiguration integriert sind ([ für die Datenerfassung), ](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/data-prep) die Zuordnung von Datenschichtvariablen zu XDM in Tags übersprungen.

#### Vorteile

* Flexibel, da Sie einzelne Variablen XDM zuordnen können
* Möglichkeit [ „Berechnung neuer Werte](https://experienceleague.adobe.com/de/docs/experience-platform/data-prep/functions) oder [Umwandlung von Datentypen](https://experienceleague.adobe.com/de/docs/experience-platform/data-prep/data-handling) aus einer Datenschicht, bevor sie an XDM gesendet wird
* Nutzen Sie eine [Zuordnungs](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/data-prep#create-mapping)Benutzeroberfläche, um Felder in Ihren Quelldaten mithilfe einer Point-and-Click-Benutzeroberfläche XDM zuzuordnen

#### Nachteile

* Datenschichtvariablen können nicht als Datenelemente für Client-seitige Pixel von Drittanbietern verwendet werden, sie können jedoch bei der Ereignisweiterleitung verwendet werden
* Die Scraping-Funktion der Tags-Funktion von Adobe Experience Platform kann nicht verwendet werden
* Die Wartung ist komplexer, wenn die Zuordnung der Datenschicht sowohl in Tags als auch im Datenstrom erfolgt



>[!IMPORTANT]
>
>Wie bereits erwähnt, folgen die Beispiele in diesem Tutorial dem Ansatz Zu XDM in Tags zuordnen .

## Erstellen von Datenelementen zur Erfassung der Datenschicht

Bevor Sie das XDM-Objekt erstellen, erstellen Sie den folgenden Satz von Datenelementen für die Datenschicht [Demo-Site](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} von Luma:

1. Wechseln Sie zu **[!UICONTROL Datenelemente]** und wählen Sie **[!UICONTROL Datenelement hinzufügen]** (oder **[!UICONTROL Neues Datenelement erstellen]** wenn in der Tag-Eigenschaft keine Datenelemente vorhanden sind)

   ![Datenelement erstellen](assets/data-element-create.png)

1. Benennen Sie das Datenelement `page.pageInfo.pageName`.
1. Verwenden Sie den **[!UICONTROL JavaScript]** Variablen **[!UICONTROL Datenelementtyp,]** auf einen Wert in der Datenschicht von Luma zu verweisen: `digitalData.page.pageInfo.pageName`

1. Markieren Sie die Kästchen für **[!UICONTROL Kleinbuchstaben erzwingen]** und **[!UICONTROL Text bereinigen]**, um die Groß-/Kleinschreibung zu standardisieren und überflüssige Leerzeichen zu entfernen

1. Belassen Sie `None` als Einstellung **[!UICONTROL Speicherdauer]**, da dieser Wert auf jeder Seite anders ist

1. Wählen Sie **[!UICONTROL Speichern]**

   ![Datenelement „Seitenname“](assets/data-element-pageName.png)

Erstellen Sie diese zusätzlichen Datenelemente, indem Sie die gleichen Schritte ausführen:

* **`page.pageInfo.server`** zugeordnet zu
  `digitalData.page.pageInfo.server`

* **`page.pageInfo.hierarchie1`** zugeordnet zu
  `digitalData.page.pageInfo.hierarchie1`

* **`user.profile.attributes.username`** zugeordnet zu
  `digitalData.user.0.profile.0.attributes.username`

* **`user.profile.attributes.loggedIn`** zugeordnet zu
  `digitalData.user.0.profile.0.attributes.loggedIn`

* **`product.productInfo.sku`** zugeordnet zu `digitalData.product.0.productInfo.sku`
<!--digitalData.product.0.productInfo.sku
    ```javascript
    var cart = digitalData.product;
    var cartItem;
    cart.forEach(function(item){
    cartItem = item.productInfo.sku;
    });
    return cartItem;
    ```
    -->
* **`product.productInfo.title`** zugeordnet zu `digitalData.product.0.productInfo.title`
* **`cart.orderId`** zugeordnet zu `digitalData.cart.orderId`
<!--
    ```javascript
    var cart = digitalData.product;
    var cartItem;
    cart.forEach(function(item){
    cartItem = item.productInfo.title;
    });
    return cartItem;
    ```
    -->
* **`product.category`** Verwendung des **[!UICONTROL benutzerspezifischer Code]** **[!UICONTROL Datenelementtyps)]** folgenden benutzerdefinierten Code, um die Website-URL für die Kategorie der obersten Ebene zu analysieren:

  ```javascript
  var cat = location.pathname.split(/[/.]+/);
  if (cat[5] == 'products') {
     return (cat[6]);
  } else if (cat[5] != 'html') { 
     return (cat[5]);
  }
  ```

* **`cart.productInfo`** mit dem folgenden benutzerdefinierten Code:

  ```javascript
  var cart = digitalData.cart.cartEntries; 
  var cartItem = [];
  cart.forEach(function(item, index, array){
  cartItem.push({
  "SKU": item.sku
  });
  });
  return cartItem; 
  ```

* **`cart.productInfo.purchase`** mit dem folgenden benutzerdefinierten Code:

  ```javascript
  var cart = digitalData.cart.cartEntries; 
  var cartItem = [];
  cart.forEach(function(item, index, array){
  var qty = parseInt(item.qty);
  var price = parseInt(item.price);
  cartItem.push({
  "SKU": item.sku,
  "quantity": qty,
  "priceTotal": price
  });
  });
  return cartItem; 
  ```



>[!CAUTION]
>
>Der Datenelementtyp [!UICONTROL JavaScript] behandelt Array-Verweise als Punkte anstatt als Klammern, sodass das Verweisen auf das Datenelement Benutzername als `digitalData.user[0].profile[0].attributes.username`**nicht funktioniert**.

## Erstellen variabler Datenelemente für XDM und Datenobjekte

Die soeben erstellten Datenelemente werden zum Erstellen eines XDM-Objekts (für Platform-Programme) und eines Datenobjekts (für Analytics, Target und Audience Manager) verwendet. Diese Objekte haben ihre eigenen speziellen Datenelemente namens **[!UICONTROL Variable]** Datenelemente, die sehr einfach zu erstellen sind.

Um das Datenelement „Variable“ für XDM zu erstellen, binden Sie es an das Schema, das Sie in der Lektion [Konfigurieren eines Schemas“ erstellt ](configure-schemas.md):

1. Wählen Sie **[!UICONTROL Datenelement hinzufügen]**
1. Benennen Sie Ihr Datenelement `xdm.variable.content`. Es wird empfohlen, den XDM-spezifischen Datenelementen „xdm“ voranzustellen, um Ihre Tag-Eigenschaft besser zu organisieren
1. Wählen Sie **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Erweiterung]**
1. Wählen Sie **[!UICONTROL Variable]** als **[!UICONTROL Datenelementtyp]**
1. Wählen Sie **[!UICONTROL XDM]** als **[!UICONTROL Eigenschaft]**
1. Wählen Sie die **[!UICONTROL Sandbox]**, in der Sie das Schema erstellt haben
1. Wählen Sie das entsprechende **[!UICONTROL Schema]** aus, in diesem Fall `Luma Web Event Data`
1. Wählen Sie **[!UICONTROL Speichern]**

   ![Variablendatenelement für XDM](assets/analytics-tags-data-element-xdm-variable.png)

Erstellen Sie anschließend das Datenelement Variable für Ihr Datenobjekt:

1. Wählen Sie **[!UICONTROL Datenelement hinzufügen]**
1. Benennen Sie Ihr Datenelement `data.variable`. Es wird empfohlen, den für das Datenobjekt spezifischen Datenelementen das Präfix „data“ voranzustellen, um Ihre Tag-Eigenschaft besser zu organisieren
1. Wählen Sie **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Erweiterung]**
1. Wählen Sie **[!UICONTROL Variable]** als **[!UICONTROL Datenelementtyp]**
1. Wählen Sie **[!UICONTROL data]** als **[!UICONTROL property]**
1. Wählen Sie die Experience Cloud-Lösungen aus, die Sie im Rahmen dieses Tutorials implementieren möchten
1. Wählen Sie **[!UICONTROL Speichern]**

   ![Variables Datenelement für das Datenobjekt](assets/data-element-data-variable.png.png)


Am Ende dieser Schritte sollten die folgenden Datenelemente erstellt sein:

| Datenelemente der Haupterweiterung | Datenelemente der Platform Web SDK-Erweiterung |
-----------------------------|-------------------------------
| `cart.orderId` | `data.variable` |
| `cart.productInfo` | `xdm.variable.content` |
| `cart.productInfo.purchase` | |
| `page.pageInfo.hierarchie1` | |
| `page.pageInfo.pageName` | |
| `page.pageInfo.server` | |
| `product.category` | |
| `product.productInfo.sku` | |
| `product.productInfo.title` | |
| `user.profile.attributes.loggedIn` | |
| `user.profile.attributes.username` | |

>[!TIP]
>
>In einer zukünftigen Lektion [Erstellen von Tag](create-tag-rule.md)Regeln) erfahren Sie, wie Sie mit den **[!UICONTROL Variable]**-Datenelementen mehrere Regeln in Tags mithilfe des **[!UICONTROL Aktionstyps „Variable aktualisieren“]** können.

Wenn diese Datenelemente eingerichtet sind, können Sie mit einer Tag-Regel Daten an Platform Edge Network senden. Erfahren Sie jedoch zuerst mehr über das Erfassen von Identitäten mit Web SDK.

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996?profile.language=de)
