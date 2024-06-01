---
title: Erstellen von Datenelementen für das Platform Web SDK
description: Erfahren Sie, wie Sie ein XDM-Objekt erstellen und ihm Datenelemente in Tags zuordnen. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Tags
jira: KT-15401
exl-id: d662ec46-de9b-44ba-974a-f81dfc842e68
source-git-commit: a8431137e0551d1135763138da3ca262cb4bc4ee
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 2%

---

# Erstellen von Datenelementen

Erfahren Sie, wie Sie Datenelemente in Tags für Inhalts-, Commerce- und Identitätsdaten in der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html). Füllen Sie dann die Felder in Ihrem XDM-Schema mit dem Datenelementtyp der Adobe Experience Platform Web SDK-Erweiterung Variable aus.

## Lernziele

Am Ende dieser Lektion können Sie:

* Verstehen verschiedener Ansätze zum Zuordnen einer Datenschicht zu XDM
* Erstellen von Datenelementen zur Datenerfassung
* Zuordnen von Datenelementen zu einem XDM-Objekt


## Voraussetzungen

Sie wissen, was eine Datenschicht ist, und haben die vorherigen Lektionen im Tutorial abgeschlossen:

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)


>[!IMPORTANT]
>
>Die Daten für diese Lektion stammen aus dem `[!UICONTROL digitalData]` Datenschicht auf der Site &quot;Luma&quot;. Um die Datenschicht anzuzeigen, öffnen Sie Ihre Entwicklerkonsole und geben Sie in `[!UICONTROL digitalData]` , um die vollständige verfügbare Datenschicht anzuzeigen.![digitalData-Datenschicht](assets/data-element-data-layer.png)


## Datenschichtansätze

Es gibt mehrere Möglichkeiten, Daten aus Ihrer Datenschicht mithilfe der Tagfunktion von Adobe Experience Platform XDM zuzuordnen. Im Folgenden finden Sie einige Vor- und Nachteile von drei verschiedenen Ansätzen. Bei Bedarf können Ansätze kombiniert werden:

1. Implementieren von XDM in der Datenschicht
1. Zuordnung zu XDM in Tags
1. Zuordnung zu XDM im Datastream

>[!NOTE]
>
>Die Beispiele in diesem Tutorial folgen dem Ansatz Zu XDM in Tags zuordnen .


### Implementieren von XDM in der Datenschicht

Bei diesem Ansatz wird das vollständig definierte XDM-Objekt als Struktur für Ihre Datenschicht verwendet. Anschließend ordnen Sie die gesamte Datenschicht einem XDM-Objektdatenelement in Tags zu. Wenn Ihre Implementierung keinen Tag-Manager verwendet, ist dieser Ansatz möglicherweise optimal, da Sie Daten von Ihrer Anwendung direkt mit dem [XDM sendEvent, Befehl](https://experienceleague.adobe.com/en/docs/experience-platform/edge/fundamentals/tracking-events#sending-xdm-data). Wenn Sie Tags verwenden, können Sie ein benutzerdefiniertes Code-Datenelement erstellen, das die gesamte Datenschicht als Pass-Through-JSON-Objekt an das XDM erfasst. Anschließend ordnen Sie die Pass-Through-JSON dem XDM-Objektfeld in der Aktion &quot;Ereignis senden&quot;zu.

Im Folgenden finden Sie ein Beispiel dafür, wie die Datenschicht mit dem Adobe Client-Datenschichtformat aussehen würde:

+++XDM im Beispiel einer Datenschicht

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

* Beseitigt zusätzliche Schritte, die auf Datenschichtvariablen in XDM beschränkt sind
* Die Bereitstellung kann schneller erfolgen, wenn Ihr Webentwicklungsteam auch Eigentümer des Tagging-digitalen Verhaltens ist

Nachteile

* Vollständige Abhängigkeit vom Entwicklungsteam und vom Entwicklungszyklus für die Aktualisierung der Daten an XDM
* Eingeschränkte Flexibilität, da XDM die exakte Payload von der Datenschicht erhält
* Es können keine integrierten Tags-Funktionen wie Scraping, Persistenz, Funktionen für schnelle Bereitstellungen verwendet werden
* Die Verwendung der Datenschicht für Pixel von Drittanbietern ist schwieriger (Sie sollten diese Pixel jedoch verschieben in [Ereignisweiterleitung](setup-event-forwarding.md)!
* Keine Transformation der Daten zwischen der Datenschicht und XDM

### Zuordnen der Datenschicht in Tags

Dieser Ansatz umfasst die Zuordnung einzelner Datenschichtvariablen ODER Datenschichtobjekte zu Datenelementen in Tags und schließlich zu XDM. Dies ist der traditionelle Ansatz für die Implementierung mithilfe eines Tag-Management-Systems.

#### Vorteile

* Der flexibelste Ansatz, da Sie einzelne Variablen steuern und Daten transformieren können, bevor sie in XDM gelangen
* Kann Adobe-Tags-Trigger und Scraping-Funktionen verwenden, um Daten an XDM zu übergeben
* Kann Datenelemente Client-seitigen Drittanbieterpixel zuordnen

#### Nachteile

* Zeit zum Rekonstruieren der Datenschicht als Datenelemente


>[!TIP]
>
> Google-Datenschicht
> 
> Wenn Ihr Unternehmen bereits Google Analytics verwendet und auf Ihrer Website über das herkömmliche Google dataLayer -Objekt verfügt, können Sie die [Google Data Layer-Erweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/google-data-layer/overview) in Tags. Dadurch können Sie Adobe-Technologie schneller bereitstellen, ohne Unterstützung von Ihrem IT-Team anfordern zu müssen. Die Zuordnung der Google-Datenschicht zu XDM würde dieselben Schritte wie oben ausführen.

### Zuordnung zu XDM im Datastream

Bei diesem Ansatz werden Funktionen verwendet, die in die Datastream-Konfiguration integriert sind: [Datenvorbereitung für die Datenerfassung](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/data-prep) und überspringt die Zuordnung von Datenschichtvariablen zu XDM in Tags.

#### Vorteile

* Flexibel, da Sie einzelne Variablen XDM zuordnen können
* Fähigkeit [Neue Werte berechnen](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/functions) oder [Datentypen transformieren](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/data-handling) aus einer Datenschicht, bevor sie an XDM gesendet wird
* Nutzen Sie eine [Zuordnungs-Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/data-prep#create-mapping) , um Felder in Ihren Quelldaten mit einer Point-and-Click-Benutzeroberfläche XDM zuzuordnen.

#### Nachteile

* Datenschichtvariablen können nicht als Datenelemente für clientseitige Drittanbieterpixel verwendet werden, können aber mit der Ereignisweiterleitung verwendet werden
* Die Scraping-Funktion der Tags-Funktion von Adobe Experience Platform kann nicht verwendet werden
* Die Wartungskomplexität erhöht sich bei der Zuordnung der Datenschicht sowohl in Tags als auch im Datenspeicher.



>[!IMPORTANT]
>
>Wie bereits erwähnt, folgen die Beispiele in diesem Tutorial dem Ansatz Zu XDM in Tags zuordnen .

## Erstellen von Datenelementen zum Erfassen der Datenschicht

Bevor Sie das XDM-Objekt erstellen, erstellen Sie den folgenden Satz von Datenelementen für die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} Datenschicht:

1. Navigieren Sie zu **[!UICONTROL Datenelemente]** und wählen **[!UICONTROL Datenelement hinzufügen]** (oder **[!UICONTROL Neues Datenelement erstellen]** wenn in der Tag-Eigenschaft keine Datenelemente vorhanden sind)

   ![Datenelement erstellen](assets/data-element-create.png)

1. Benennen Sie das Datenelement `page.pageInfo.pageName`.
1. Verwenden Sie die **[!UICONTROL JavaScript-Variable]** **[!UICONTROL Datenelementtyp]** auf einen Wert in der Datenschicht von Luma verweisen: `digitalData.page.pageInfo.pageName`

1. Markieren Sie die Kästchen für **[!UICONTROL Kleinbuchstaben erzwingen Wert]** und **[!UICONTROL Text bereinigen]** zur Standardisierung der Groß-/Kleinschreibung und Entfernung von Fremdbereichen

1. Urlaub `None` als **[!UICONTROL Speicherdauer]** Einstellung, da dieser Wert auf jeder Seite unterschiedlich ist

1. Auswählen **[!UICONTROL Speichern]**

   ![Datenelement &quot;Seitenname&quot;](assets/data-element-pageName.png)

Erstellen Sie diese zusätzlichen Datenelemente wie folgt:

* **`page.pageInfo.server`**  zugeordnet zu
  `digitalData.page.pageInfo.server`

* **`page.pageInfo.hierarchie1`**  zugeordnet zu
  `digitalData.page.pageInfo.hierarchie1`

* **`user.profile.attributes.username`**  zugeordnet zu
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
* **`product.category`** mithilfe der **[!UICONTROL Benutzerspezifischer Code]** **[!UICONTROL Datenelementtyp]** und den folgenden benutzerspezifischen Code, um die Site-URL für die Kategorie der obersten Ebene zu analysieren:

  ```javascript
  var cat = location.pathname.split(/[/.]+/);
  if (cat[5] == 'products') {
     return (cat[6]);
  } else if (cat[5] != 'html') { 
     return (cat[5]);
  }
  ```

* **`cart.productInfo`** unter Verwendung des folgenden benutzerspezifischen Codes:

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

* **`cart.productInfo.purchase`** unter Verwendung des folgenden benutzerspezifischen Codes:

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
>Die [!UICONTROL JavaScript-Variable] Datenelementtyp behandelt Array-Referenzen als Punkte anstelle von Klammern. Referenzieren Sie daher das Datenelement &quot;Benutzername&quot;als `digitalData.user[0].profile[0].attributes.username` **funktioniert nicht**.

## Erstellen von Variablendatenelementen für XDM- und Datenobjekte

Die soeben erstellten Datenelemente werden zum Erstellen eines XDM-Objekts (für Platform-Anwendungen) und eines Datenobjekts (für Analytics, Target und Audience Manager) verwendet. Diese Objekte verfügen über eigene spezielle Datenelemente, die **[!UICONTROL Variable]** Datenelemente, die sehr einfach zu erstellen sind.

Um das Datenelement &quot;Variable&quot;für XDM zu erstellen, verknüpfen Sie es mit dem Schema, das Sie im [Schema konfigurieren](configure-schemas.md) Lektion:

1. Auswählen **[!UICONTROL Datenelement hinzufügen]**
1. Ihr Datenelement benennen `xdm.variable.content`. Es wird empfohlen, das XDM-spezifische Datenelement mit &quot;xdm&quot;zu versehen, um Ihre Tag-Eigenschaft besser zu organisieren
1. Wählen Sie die **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Erweiterung]**
1. Wählen Sie die **[!UICONTROL Variable]** als **[!UICONTROL Datenelementtyp]**
1. Auswählen **[!UICONTROL XDM]** als **[!UICONTROL property]**
1. Wählen Sie die **[!UICONTROL Sandbox]** in dem Sie das Schema erstellt haben
1. Wählen Sie die entsprechende **[!UICONTROL Schema]** in diesem Fall `Luma Web Event Data`
1. Auswählen **[!UICONTROL Speichern]**

   ![Variablendatenelement für XDM](assets/analytics-tags-data-element-xdm-variable.png)

Erstellen Sie anschließend das Datenelement Variable für Ihr Datenobjekt:

1. Auswählen **[!UICONTROL Datenelement hinzufügen]**
1. Ihr Datenelement benennen `data.variable`. Es wird empfohlen, den Datenelementen, die spezifisch für das Datenobjekt sind, das Präfix &quot;data&quot;zu verwenden, um Ihre Tag-Eigenschaft besser zu organisieren.
1. Wählen Sie die **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Erweiterung]**
1. Wählen Sie die **[!UICONTROL Variable]** als **[!UICONTROL Datenelementtyp]**
1. Auswählen **[!UICONTROL data]** als **[!UICONTROL property]**
1. Wählen Sie die Experience Cloud-Lösungen aus, die Sie im Rahmen dieses Tutorials implementieren möchten
1. Auswählen **[!UICONTROL Speichern]**

   ![Variablendatenelement für Datenobjekt](assets/data-element-data-variable.png.png)


Am Ende dieser Schritte sollten die folgenden Datenelemente erstellt werden:

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
>In Zukunft [Erstellen von Tag-Regeln](create-tag-rule.md) Lektion: Sie lernen, wie die **[!UICONTROL Variable]** Datenelemente ermöglichen es Ihnen, mehrere Regeln in Tags mithilfe der **[!UICONTROL Aktionstyp der Variablen aktualisieren]**.

Wenn diese Datenelemente vorhanden sind, können Sie mit dem Senden von Daten an Platform Edge Network mit einer Tagregel beginnen. Erfahren Sie zunächst, wie Sie Identitäten mit dem Web SDK erfassen.

[Weiter: ](create-identities.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
