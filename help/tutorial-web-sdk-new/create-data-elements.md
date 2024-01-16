---
title: Erstellen von Datenelementen
description: Erfahren Sie, wie Sie ein XDM-Objekt erstellen und ihm Datenelemente in Tags zuordnen. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Tags
source-git-commit: f08866de1bd6ede50bda1e5f8db6dbd2951aa872
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 2%

---

# Erstellen von Datenelementen

Erfahren Sie, wie Sie die wichtigsten Datenelemente erstellen, die zum Erfassen von Daten mit dem Experience Platform Web SDK erforderlich sind. Erfassen Sie sowohl Inhalts- als auch Identitätsdaten auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html). Erfahren Sie, wie Sie das zuvor erstellte XDM-Schema zur Datenerfassung mit dem Platform Web SDK-Datenelementtyp Variable verwenden.

>[!NOTE]
>
> Zu Demonstrationszwecken bauen die Übungen in dieser Lektion auf dem Beispiel auf, das während der [Schema konfigurieren](configure-schemas.md) Schritt; Erstellen von Beispiel-XDM-Objekten, die angesehene Inhalte und Identitäten von Benutzern auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html).

>[!IMPORTANT]
>
>Die Daten für diese Lektion stammen aus dem `[!UICONTROL digitalData]` Datenschicht auf der Site &quot;Luma&quot;. Um die Datenschicht anzuzeigen, öffnen Sie Ihre Entwicklerkonsole und geben Sie in `[!UICONTROL digitalData]` , um die vollständige verfügbare Datenschicht anzuzeigen.![digitalData-Datenschicht](assets/data-element-data-layer.png)


Unabhängig vom Platform Web SDK müssen Sie weiterhin Datenelemente in Ihrer Tags-Eigenschaft erstellen, die Datenerfassungsvariablen Ihrer Website wie einer Datenschicht, einem HTML-Attribut oder anderen zugeordnet sind. Nachdem Sie diese Datenelemente erstellt haben, müssen Sie sie dem XDM-Schema zuordnen, das Sie während der [Schemas konfigurieren](configure-schemas.md) Lektion. Daher besteht das Erstellen von Datenelementen aus zwei Aktionen:

1. Zuordnen von Website-Variablen zu Datenelementen und
1. Zuordnen dieser Datenelemente zu einem XDM-Objekt

Bei Schritt 1 ordnen Sie Ihre Datenschicht Datenelementen weiterhin auf die aktuelle Weise zu, indem Sie einen der Datenelementtypen der Core-Tag-Erweiterung verwenden. Für Schritt 2 ist die Platform Web SDK-Erweiterung mit den folgenden Datenelementtypen verfügbar:

* Ereigniszusammenführungs-ID
* Identitätszuordnung
* Variable
* XDM-Objekt

Diese Lektion konzentriert sich auf den Datenelementtyp Variable . Sie erstellen ein Datenelement, um die Aktivität der Luma-Besucher basierend auf der verfügbaren Datenschicht auf der Site &quot;Luma&quot;zu erfassen. In der nächsten Lektion erfahren Sie mehr über Identity Map.

>[!NOTE]
>
> Die Datenelementtypen für Ereigniszusammenführungs-ID und XDM-Objektdaten werden selten für Edge-Fälle verwendet.

## Lernziele

Am Ende dieser Lektion können Sie:

* Verstehen verschiedener Ansätze zum Zuordnen einer Datenschicht zu XDM
* Erstellen von Datenelementen zum Erfassen von Inhaltsdaten
* Zuordnen von Datenelementen zu einem XDM-Objektdatenelement


## Voraussetzungen

Sie wissen, was eine Datenschicht ist, und kennen die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} und wissen, wie Datenelemente in Tags referenziert werden. Sie müssen die folgenden vorherigen Schritte im Tutorial ausgeführt haben.

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)

>[!IMPORTANT]
>
>Die [Experience Cloud ID-Diensterweiterung](https://exchange.adobe.com/experiencecloud.details.100160.adobe-experience-cloud-id-launch-extension.html) ist bei der Implementierung des Adobe Experience Platform Web SDK nicht erforderlich, da die ID-Dienst-Funktion in das Platform Web SDK integriert ist.

## Datenschichtansätze

Es gibt mehrere Möglichkeiten, Daten aus Ihrer Datenschicht mithilfe der Tagfunktion von Adobe Experience Platform XDM zuzuordnen. Im Folgenden finden Sie einige Vor- und Nachteile von drei verschiedenen Ansätzen:

* [Implementieren von XDM in der Datenschicht](create-data-elements.md#implement-xdm-in-the-data-layer)
* [Zuordnung zu XDM im Datastream](create-data-elements.md#map-to-xdm-in-the-datastream)
* [Zuordnung zu XDM in Tags](create-data-elements.md#map-data-layer-in-tags)

>[!NOTE]
>
>Die Beispiele in diesem Tutorial folgen dem Ansatz Zu XDM in Tags zuordnen .


### Implementieren von XDM in der Datenschicht

Bei diesem Ansatz wird das vollständig definierte XDM-Objekt als Struktur für Ihre Datenschicht verwendet. Anschließend ordnen Sie die gesamte Datenschicht einem XDM-Objektdatenelement in Adobe-Tags zu. Wenn Ihre Implementierung keinen Tag-Manager verwendet, ist dieser Ansatz möglicherweise optimal, da Sie Daten von Ihrer Anwendung direkt mit dem [XDM sendEvent, Befehl](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/tracking-events.html?lang=en#sending-xdm-data). Wenn Sie Adobe-Tags verwenden, können Sie ein benutzerdefiniertes Codedatenelement erstellen, das die gesamte Datenschicht als Pass-Through-JSON-Objekt an das XDM erfasst. Anschließend ordnen Sie die Pass-Through-JSON dem XDM-Objektfeld in der Aktion &quot;Ereignis senden&quot;zu.

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

* Überspringt Schritte zum Zuordnen einzelner Datenschichtvariablen zu XDM
* Kann schneller bereitgestellt werden, wenn Ihr Entwicklungsteam über das Tagging digitaler Verhaltensweisen verfügt

Nachteile

* Vollständige Abhängigkeit vom Entwicklungsteam und vom Entwicklungszyklus für die Aktualisierung der Daten an XDM
* Eingeschränkte Flexibilität, da XDM die exakte Payload von der Datenschicht erhält
* Es können keine integrierten Tags wie Scraping, Persistenz und Funktionen für schnelle Bereitstellungen verwendet werden
* Die Datenschicht kann nicht für Pixel von Drittanbietern verwendet werden
* Keine Transformation der Daten zwischen der Datenschicht und XDM

### Zuordnung zu XDM im Datastream

Bei diesem Ansatz werden Funktionen verwendet, die in die Datastream-Konfiguration integriert sind: [Datenvorbereitung für die Datenerfassung](https://experienceleague.adobe.com/docs/experience-platform/datastreams/data-prep.html) und überspringt die Zuordnung von Datenschichtvariablen zu XDM in Tags.

Vorteile

* Flexibel, da Sie einzelne Variablen XDM zuordnen können
* Fähigkeit [Neue Werte berechnen](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html?lang=de) oder [Datentypen transformieren](https://experienceleague.adobe.com/docs/experience-platform/data-prep/data-handling.html) aus einer Datenschicht, bevor sie an XDM gesendet wird
* Nutzen Sie eine [Zuordnungs-Benutzeroberfläche](https://experienceleague.adobe.com/docs/experience-platform/datastreams/data-prep.html#create-mapping) , um Felder in Ihren Quelldaten mit einer Point-and-Click-Benutzeroberfläche XDM zuzuordnen.

Nachteile

* Datenschichtvariablen können nicht als Datenelemente für clientseitige Drittanbieterpixel verwendet werden, sie können jedoch mit Adobe-Tags-Ereignisweiterleitung verwendet werden
* Die Scraping-Funktion der Tags-Funktion von Adobe Experience Platform kann nicht verwendet werden
* Die Wartungskomplexität erhöht sich bei der Zuordnung der Datenschicht sowohl in Tags als auch im Datenspeicher.

### Zuordnen der Datenschicht in Tags

Dieser Ansatz umfasst die Zuordnung einzelner Datenschichtvariablen ODER Datenschichtobjekte zu Datenelementen in Tags und schließlich zu XDM. Dies ist der traditionelle Ansatz für die Implementierung mithilfe eines Tag-Management-Systems.

Vorteile

* Der flexibelste Ansatz, da Sie einzelne Variablen steuern und Daten transformieren können, bevor sie in XDM gelangen
* Kann Adobe-Tags-Trigger und Scraping-Funktionen verwenden, um Daten an XDM zu übergeben
* Kann Datenelemente Client-seitigen Drittanbieterpixel zuordnen

Nachteile

* Die Implementierung kann länger dauern

>[!TIP]
>
> Google-Datenschicht
> 
> Wenn Ihr Unternehmen bereits Google Analytics verwendet und auf Ihrer Website über das herkömmliche Google dataLayer -Objekt verfügt, können Sie die [Google Data Layer-Erweiterung](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/google-data-layer/overview.html?lang=en) in Adobe-Tags. Dadurch können Sie Adobe-Technologie schneller bereitstellen, ohne Unterstützung von Ihrem IT-Team anfordern zu müssen. Die Zuordnung der Google-Datenschicht zu XDM würde dieselben Schritte wie oben ausführen.

>[!IMPORTANT]
>
>Wie bereits erwähnt, folgen die Beispiele in diesem Tutorial dem Ansatz Zu XDM in Tags zuordnen .

## Erstellen von Datenelementen zum Erfassen der Datenschicht

Bevor Sie das XDM-Objekt erstellen, erstellen Sie den folgenden Satz von Datenelementen für die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} Datenschicht:

1. Navigieren Sie zu **[!UICONTROL Datenelemente]** und wählen **[!UICONTROL Datenelement hinzufügen]** (oder **[!UICONTROL Neues Datenelement erstellen]** wenn in der Tag-Eigenschaft keine Datenelemente vorhanden sind)

   ![Datenelement erstellen](assets/data-element-create.jpg)

1. Benennen Sie das Datenelement `page.pageInfo.pageName`.
1. Verwenden Sie die **[!UICONTROL JavaScript-Variable]** **[!UICONTROL Datenelementtyp]** auf einen Wert in der Datenschicht von Luma verweisen: `digitalData.page.pageInfo.pageName`

1. Markieren Sie die Kästchen für **[!UICONTROL Kleinbuchstaben erzwingen Wert]** und **[!UICONTROL Text bereinigen]** zur Standardisierung der Groß-/Kleinschreibung und Entfernung von Fremdbereichen

1. Urlaub `None` als **[!UICONTROL Speicherdauer]** Einstellung, da dieser Wert auf jeder Seite unterschiedlich ist

1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Datenelement &quot;Seitenname&quot;](assets/data-element-pageName.jpg)

Erstellen Sie diese vier zusätzlichen Datenelemente wie folgt:

* **`page.pageInfo.server`**  zugeordnet zu
  `digitalData.page.pageInfo.server`

* **`page.pageInfo.hierarchie1`**  zugeordnet zu
  `digitalData.page.pageInfo.hierarchie1`

* **`user.profile.attributes.username`**  zugeordnet zu
  `digitalData.user.0.profile.0.attributes.username`

* **`user.profile.attributes.loggedIn`** zugeordnet zu
  `digitalData.user.0.profile.0.attributes.loggedIn`

* **`cart.orderId`** zugeordnet zu `digitalData.cart.orderId` (Sie verwenden dies während der [Einrichten von Analytics](setup-analytics.md) Lektion)


>[!CAUTION]
>
>Die [!UICONTROL JavaScript-Variable] Datenelementtyp behandelt Array-Referenzen als Punkte anstelle von Klammern. Referenzieren Sie daher das Datenelement &quot;Benutzername&quot;als `digitalData.user[0].profile[0].attributes.username` **funktioniert nicht**.

## Datenelement &quot;Variable&quot;erstellen

Nachdem Sie die Datenelemente erstellt haben, ordnen Sie sie dem XDM mithilfe der **[!UICONTROL Variable]** -Datenelement, das das für das XDM-Objekt verwendete Schema definiert. Dieses Objekt sollte mit dem XDM-Schema übereinstimmen, das Sie während der [Schema konfigurieren](configure-schemas.md) Lektion.

So erstellen Sie das Datenelement Variable :

1. Auswählen **[!UICONTROL Datenelement hinzufügen]**
1. Ihr Datenelement benennen `xdm.variable.content`. Es wird empfohlen, das XDM-spezifische Datenelement mit &quot;xdm&quot;zu versehen, um Ihre Tag-Eigenschaft besser zu organisieren
1. Wählen Sie die **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Erweiterung]**
1. Wählen Sie die **[!UICONTROL Variable]** als **[!UICONTROL Datenelementtyp]**
1. Auswählen der entsprechenden Experience Platform **[!UICONTROL Sandbox]**
1. Wählen Sie die entsprechende **[!UICONTROL Schema]** in diesem Fall `Luma Web Event Data`
1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Variablendatenelement](assets/analytics-tags-data-element-xdm-variable.png)

<!-- There are different ways to map data elements to XDM object fields. You can map individual data elements to individual XDM fields or map data elements to entire XDM objects as long as your data element matches the exact key-value pair schema present in the XDM object. In this lesson, you will capture content data by mapping to individual fields. You will learn how to [map a data element to an entire XDM object](setup-analytics.md#Map-an-entire-array-to-an-XDM-Object) in the [Setup Analytics](setup-analytics.md) lesson. 

Create an XDM object to capture content data:

1. In the left navigation, select **[!UICONTROL Data Elements]**
1. Select **[!UICONTROL Add Data Element]**
1. **[!UICONTROL Name]** the data element **`xdm.content`**
1. As the **[!UICONTROL Extension]** select `Adobe Experience Platform Web SDK`
1. As the **[!UICONTROL Data Element Type]** select `XDM object`
1. Select the Platform **[!UICONTROL Sandbox]** in which you created the XDM schema in during the [Configure an XDM Schema](configure-schemas.md) lesson, in this example `DEVELOPMENT Mobile and Web SDK Courses`
1. As the **[!UICONTROL Schema]**, select your `Luma Web Event Data` schema:

    ![XDM object](assets/data-element-xdm.content-fields.png)

    >[!NOTE]
    >
    >The sandbox corresponds to the Experience Platform sandbox in which you created the schema. There can be multiple sandboxes available in your Experience Platform instance, so make sure to select the right one. Always work in development first, then production.

1. Scroll down until you reach the **`web`** object
1. Select to open it

    ![Web Object](assets/data-element-pageviews-xdm-object.png)


1. Map the following web XDM variables to data elements

    * **`web.webPageDetials.name`** to `%page.pageInfo.pageName%`
    * **`web.webPageDetials.server`** to `%page.pageInfo.server%`
    * **`web.webPageDetials.siteSection`** to `%page.pageInfo.hierarchie1%`

    ![XDM object](assets/data-element-xdm.content.png)

1. Next, find the `identityMap` object in the schema and select it
 
1. Map to the `identityMap.loginID` data element

1. Select **[!UICONTROL Save]**

   ![Data Collection interface](assets/identity-dataElements-xdmContent-LumaSchema-identityMapSelect3.png)

-->

Am Ende dieser Schritte sollten die folgenden Datenelemente erstellt werden:

| Datenelemente der CORE-Erweiterung | Platform Web SDK-Datenelemente |
-----------------------------|-------------------------------
| `cart.orderId` | `xdm.variable.content` |
| `page.pageInfo.hierarchie1` | |
| `page.pageInfo.pageName` | |
| `page.pageInfo.server` | |
| `user.profile.attributes.loggedIn` | |
| `user.profile.attributes.username` | |


>[!TIP]
>
>In Zukunft [Tag-Regel erstellen](create-tag-rule.md) Lektion: Sie lernen, wie die **[!UICONTROL Variable]** Mit dem Datenelement können Sie mehrere Regeln in Tags stapeln, indem Sie die **[!UICONTROL Aktionstyp der Variablen aktualisieren]**. Anschließend können Sie das XDM-Objekt unabhängig mithilfe eines separaten **[!UICONTROL Aktionstyp &quot;Ereignis senden&quot;]**.

Wenn diese Datenelemente vorhanden sind, können Sie mit dem Senden von Daten an Platform Edge Network mit einer Tagregel beginnen. Erfahren Sie zunächst, wie Sie Identitäten mit dem Web SDK erfassen.

[Weiter: ](create-identities.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
