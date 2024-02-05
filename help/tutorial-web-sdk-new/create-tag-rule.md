---
title: Erstellen von Tag-Regeln
description: Erfahren Sie, wie Sie mit Ihrem XDM-Objekt mithilfe einer Tag-Regel ein Ereignis an das Platform Edge Network senden. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Tags
source-git-commit: 367789cfb0800fee7d020303629f57112e52464f
workflow-type: tm+mt
source-wordcount: '2005'
ht-degree: 1%

---

# Erstellen von Tag-Regeln

Erfahren Sie, wie Sie mithilfe von Tag-Regeln Ereignisse mit Ihrem XDM-Objekt an das Platform Edge Network senden. Eine Tag-Regel ist eine Kombination aus Ereignissen, Bedingungen und Aktionen, die die Tag-Eigenschaft anweist, etwas zu tun.

>[!NOTE]
>
> Zu Demonstrationszwecken bauen die Übungen in dieser Lektion auf dem Beispiel auf, das während der [Erstellen von Identitäten](create-identities.md) Schritt; Senden einer XDM-Ereignisaktion zum Erfassen von Inhalten und Identitäten von Benutzern auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html).


## Lernziele

Am Ende dieser Lektion können Sie:

* Verwenden einer Benennungskonvention zum Verwalten von Regeln innerhalb von Tags
* Senden eines XDM-Ereignisses mithilfe der Aktionstypen &quot;Variable aktualisieren&quot;und &quot;Ereignis senden&quot;in einer Tag-Regel
* Veröffentlichen einer Tag-Regel in einer Entwicklungsbibliothek


## Voraussetzungen

Sie kennen Datenerfassungs-Tags und die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html)und Sie müssen die folgenden vorherigen Lektionen im Tutorial abgeschlossen haben:

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)
* [Erstellen von Datenelementen](create-data-elements.md)
* [Erstellen von Identitäten](create-identities.md)

## Benennungskonventionen

Um Regeln in Tags besser zu verwalten, wird empfohlen, eine standardmäßige Namenskonvention zu befolgen. In diesem Tutorial wird eine dreiteilige Namenskonvention verwendet:

* [**location**] - [**event**] - [**Tool**] (**Sequenz**)

wo;

1. **location** ist die Seite oder die Seiten auf der Site, auf der die Regel ausgelöst wird.
1. **event** ist der Trigger für die Regel
1. **Tool** ist die spezifische(n) Anwendung(en), die im Aktionsschritt für diese Regel verwendet wird/werden.
1. **Sequenz** ist die Reihenfolge, in der die Regel im Verhältnis zu anderen Regeln ausgelöst werden soll
<!-- minor update -->

## Erstellen von Tag-Regeln

In -Tags werden Regeln verwendet, um unter verschiedenen Bedingungen Aktionen (Aufrufe auslösen) auszuführen. Die Platform Web SDK-Tag-Erweiterung umfasst zwei Aktionen, die in dieser Lektion verwendet werden:

* **[!UICONTROL Variable aktualisieren]** ordnet Datenelemente XDM-Feldern zu
* **[!UICONTROL Ereignis senden]** sendet das XDM-Objekt an das Experience Platform Edge Network

Zuerst definieren wir eine Regel mit der **[!UICONTROL Variable aktualisieren]** -Aktion, die eine &quot;globale Konfiguration&quot;von XDM-Feldern definiert, die wir auf jeder Seite der Site senden möchten (z. B. den Seitennamen).

Anschließend können wir zusätzliche Regeln mit der **[!UICONTROL Variable aktualisieren]** -Aktion, die die globalen XDM-Felder durch zusätzliche Felder ergänzt, die nur unter bestimmten Bedingungen verfügbar sind (z. B. Hinzufügen von Produktdetails zu Produktseiten).

Schließlich verwenden wir eine andere Regel mit der **[!UICONTROL Ereignis senden]** -Aktion, die das vollständige XDM-Objekt an Adobe Experience Platform Edge Network sendet.


### Aktualisieren von Variablenregeln

#### Globale Felder

So erstellen Sie eine Tag-Regel für die globalen XDM-Felder:

1. Öffnen Sie die Tag-Eigenschaft, die Sie für dieses Tutorial verwenden

1. Navigieren Sie zu **[!UICONTROL Regeln]** in der linken Navigation

1. Wählen Sie die **[!UICONTROL Neue Regel erstellen]** button

   ![Regel erstellen](assets/rules-create.png)

1. Geben Sie einen Namen für die Regel ein `all pages global content variables - library loaded - AA (order 1)`.

1. Im **[!UICONTROL Veranstaltungen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

   ![Benennen Sie die Regel und fügen Sie ein Ereignis hinzu](assets/rule-name-new.png)

1. Verwenden Sie die **[!UICONTROL Haupterweiterung]** und wählen `Page Bottom` als **[!UICONTROL Ereignistyp]**

1. Unter dem **[!UICONTROL Name]** Feld, nennen Sie es `Core - Page Bottom - order 1`. Auf diese Weise können Sie den Trigger mit einem aussagekräftigen Namen beschreiben.

1. Auswählen **[!UICONTROL Erweitert]** Dropdown und `1` in **[!UICONTROL Bestellung]**

   >[!NOTE]
   >
   > Je höher die Zahl, die Sie eingeben, desto später wird die Gesamtzahl der Vorgänge Trigger.

1. Auswählen **[!UICONTROL Änderungen beibehalten]** zum Hauptregelbildschirm zurückzukehren
   ![Seitenende auswählen, Trigger](assets/create-tag-rule-trigger-bottom.png)

1. Im **[!UICONTROL Aktionen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

1. Als **[!UICONTROL Erweiterung]** auswählen **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als **[!UICONTROL Aktionstyp]** auswählen **[!UICONTROL Variable aktualisieren]**

1. Als **[!UICONTROL Datenelement]**, wählen Sie die `xdm.variable.content` die Sie in der [Erstellen von Datenelementen](create-data-elements.md) Lektion

   ![Variablenschema aktualisieren](assets/create-rule-update-variable.png)

Jetzt zuordnen [!UICONTROL Datenelemente] der [!UICONTROL schema] verwendet von Ihrem XDM-Objekt.

>[!NOTE]
> 
> Sie können einzelnen Eigenschaften oder ganzen Objekten zuordnen. In diesem Beispiel ordnen Sie einzelne Eigenschaften zu.


1. Scrollen Sie nach unten, bis Sie zum **`web`** Objekt

1. Auswahl zum Öffnen

1. Ordnen Sie die folgenden Datenelemente den entsprechenden `web` XDM-Variablen

   * **`web.webPageDetials.name`** in `%page.pageInfo.pageName%`
   * **`web.webPageDetials.server`** in `%page.pageInfo.server%`
   * **`web.webPageDetials.siteSection`** in `%page.pageInfo.hierarchie1%`

1. Stellen Sie `web.webPageDetials.pageViews.value` auf `1` ein.

   ![Variableninhalt aktualisieren](assets/create-rule-xdm-variable-content.png)

1. Suchen Sie als Nächstes die `identityMap` -Objekt im Schema und wählen Sie es aus

1. Zuordnung zu `identityMap.loginID` Datenelement

   ![Variable-Identitätszuordnung aktualisieren](assets/create-rule-variable-identityMap.png)

1. Suchen Sie anschließend das Feld eventType und wählen Sie es aus

1. Wert eingeben `web.webpagedetails.pageViews`

   >[!WARNING]
   >
   > Mit diesem Dropdown-Menü wird die **`xdm.eventType`** im XDM-Objekt. Sie können in dieses Feld zwar auch Freiform-Beschriftungen eingeben, es wird jedoch dringend empfohlen, **nicht** da sie negative Auswirkungen auf Platform hat.

   >[!TIP]
   >
   > So verstehen Sie, welche Werte im `eventType` -Feld, müssen Sie zur Schemaseite gehen und die `eventType` -Feld, um die vorgeschlagenen Werte in der rechten Leiste anzuzeigen.

   >[!TIP]
   >
   > Während `web.webPageDetials.pageViews.value` nor `eventType` auf `web.webpagedetails.pageViews` erforderlich sind, damit Adobe Analytics ein Beacon als Seitenansicht verarbeiten kann, ist es nützlich, eine Standardmethode zur Anzeige einer Seitenansicht für andere nachgelagerte Anwendungen zu verwenden.

   ![Variable-Identitätszuordnung aktualisieren](assets/create-tag-rule-eventType.png)


1. Auswählen **[!UICONTROL Änderungen beibehalten]** und dann **[!UICONTROL Speichern]** die Regel im nächsten Bildschirm, um die Erstellung der Regel abzuschließen


#### Anreicherung des XDM-Objekts mithilfe zusätzlicher Regeln mit der Aktion &quot;Variable aktualisieren&quot;

Sie können **[!UICONTROL Variable aktualisieren]**  in mehreren sequenzierten Regeln, um das XDM-Objekt anzureichern, bevor es an gesendet wird [!UICONTROL Platform Edge Network].

>[!TIP]
>
>Die Regelreihenfolge bestimmt, welche Regel beim Auslösen eines Ereignisses zuerst ausgeführt wird. Wenn zwei Regeln denselben Ereignistyp aufweisen, wird zuerst die Regel mit der niedrigsten Nummer ausgeführt.
> 
>![rule-order](assets/set-up-analytics-sequencing.png)

##### Felder für Produktseiten

Beginnen Sie mit der Verfolgung der Produktansichten auf der Produktdetailseite von Luma:

1. Auswählen **[!UICONTROL Regel hinzufügen]**
1. Benennen Sie ihn  [!UICONTROL `ecommerce - pdp library loaded - AA (order 20)`]
1. Wählen Sie die ![+ Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) unter Ereignis zum Hinzufügen eines neuen Triggers
1. under **[!UICONTROL Erweiterung]** auswählen **[!UICONTROL Core]**
1. under **[!UICONTROL Ereignistyp]** auswählen **[!UICONTROL Seitenende]**
1. Benennen Sie ihn `Core - Page Bottom - order 20`
1. Zum Öffnen auswählen **[!UICONTROL Erweiterte Optionen]**, Typ in `20`. Dadurch wird sichergestellt, dass die Regel nach dem `all pages global content variables - library loaded - AA (order 1)` , das die globalen Inhaltsvariablen festlegt, jedoch vor dem `all pages send event - library loaded - AA (order 50)` sendet das XDM-Ereignis.

   ![Analytics-XDM-Regeln](assets/set-up-analytics-pdp.png)

1. under **[!UICONTROL Bedingungen]**, wählen Sie **[!UICONTROL Hinzufügen]**
1. Urlaub **[!UICONTROL Logiktyp]** as **[!UICONTROL Normal]**
1. Urlaub **[!UICONTROL Erweiterungen]** as **[!UICONTROL Core]**
1. Auswählen **[!UICONTROL Bedingungstyp]** as **[!UICONTROL Pfad ohne Abfragezeichenfolge]**
1. Aktivieren Sie rechts die Option **[!UICONTROL Regex]** Umschalten
1. under **[!UICONTROL path equals]** set `/products/`. Auf der Demosite &quot;Luma&quot;wird sichergestellt, dass die Regel nur Trigger auf Produktseiten enthält.
1. Auswählen **[!UICONTROL Änderungen beibehalten]**

   ![Analytics-XDM-Regeln](assets/set-up-analytics-product-condition.png)

1. under **[!UICONTROL Aktionen]** select **[!UICONTROL Hinzufügen]**
1. Auswählen **[!UICONTROL Adobe Experience Platform Web SDK]** Erweiterung
1. Auswählen **[!UICONTROL Aktionstyp]** as **[!UICONTROL Variable aktualisieren]**
1. Scrollen Sie nach unten zum `commerce` -Objekt ein und wählen Sie aus, um es zu öffnen.
1. Öffnen Sie die **[!UICONTROL productViews]** -Objekt und -set **[!UICONTROL value]** nach `1`

   ![Einrichten der Produktansicht](assets/set-up-analytics-prodView.png)

   >[!TIP]
   >
   >Wenn Sie commerce.productViews.value=1 in XDM festlegen, wird dies automatisch dem `prodView` -Ereignis in Analytics


1. Scrollen Sie nach unten zu und wählen Sie `productListItems` array
1. Auswählen **[!UICONTROL Bereitstellen einzelner Elemente]**
1. Auswählen **[!UICONTROL Element hinzufügen]**

   ![Festlegen des Produktansichtsereignisses](assets/set-up-analytics-xdm-individual.png)

   >[!CAUTION]
   >
   >Die **`productListItems`** ist `array` -Datentyp, sodass erwartet wird, dass Daten als Sammlung von Elementen eingehen. Aufgrund der Datenschichtstruktur der Demosite &quot;Luma&quot;und da es nur möglich ist, ein Produkt gleichzeitig auf der Site &quot;Luma&quot;anzuzeigen, fügen Sie Elemente einzeln hinzu. Bei der Implementierung auf Ihrer eigenen Website können Sie je nach Datenschichtstruktur möglicherweise ein ganzes Array bereitstellen.

1. Zum Öffnen auswählen **[!UICONTROL Posten 1]**
1. Zuordnung von **`productListItems.item1.SKU`** nach `%product.productInfo.sku%`

   ![Produkt-SKU XDM-Objektvariable](assets/set-up-analytics-sku.png)

1. Suchen `eventType` und legen Sie `commerce.productViews`

1. Auswählen **[!UICONTROL Änderungen beibehalten]**

1. Auswählen **[!UICONTROL Speichern]** zum Speichern der Regel




### Felder im Warenkorb

Sie können das gesamte Array einem XDM-Objekt zuordnen, vorausgesetzt, das Array entspricht dem Format des XDM-Schemas. Das Datenelement des benutzerspezifischen Codes `cart.productInfo` Sie haben frühere Schleifen durch `digitalData.cart.cartEntries` Datenschichtobjekt auf Luma und übersetzt es in das erforderliche Format der `productListItems` -Objekt des XDM-Schemas.

Sehen Sie sich dazu den unten stehenden Vergleich der Datenschicht der Site &quot;Luma&quot;(links) mit dem übersetzten Datenelement (rechts) an:

![XDM-Objekt-Array-Format](assets/data-element-xdm-array.png)

Das Datenelement mit dem `productListItems` Struktur (Hinweis, sollte übereinstimmen).

>[!IMPORTANT]
>
>Beachten Sie, wie numerische Variablen übersetzt werden, wobei Zeichenfolgenwerte in der Datenschicht wie `price` und `qty` in Zahlen im Datenelement umformatiert. Diese Formatanforderungen sind für die Datenintegrität in Platform wichtig und werden während der [Schemas konfigurieren](configure-schemas.md) Schritt. Im Beispiel **[!UICONTROL quantity]** verwendet die **[!UICONTROL Ganzzahl]** Datentyp.
> ![XDM-Schema-Datentyp](assets/set-up-analytics-quantity-integer.png)

Zuordnen unseres Arrays zum XDM-Objekt


1. Eine neue Regel mit dem Namen `ecommerce - cart library loaded - AA (order 20)`
1. Wählen Sie die ![+ Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) unter Ereignis zum Hinzufügen eines neuen Triggers
1. under **[!UICONTROL Erweiterung]** auswählen **[!UICONTROL Core]**
1. under **[!UICONTROL Ereignistyp]** auswählen **[!UICONTROL Seitenende]**
1. Benennen Sie ihn `Core - Page Bottom - order 20`
1. Zum Öffnen auswählen **[!UICONTROL Erweiterte Optionen]**, Typ in `20`
1. Auswählen **[!UICONTROL Änderungen beibehalten]**

   ![Analytics-XDM-Regeln](assets/set-up-analytics-cart-sequence.png)

1. under **[!UICONTROL Bedingungen]**, wählen Sie **[!UICONTROL Hinzufügen]**
1. Urlaub **[!UICONTROL Logiktyp]** as **[!UICONTROL Normal]**
1. Urlaub **[!UICONTROL Erweiterungen]** as **[!UICONTROL Core]**
1. Auswählen **[!UICONTROL Bedingungstyp]** as **[!UICONTROL Pfad ohne Abfragezeichenfolge]**
1. rechts: **nicht** aktivieren die **[!UICONTROL Regex]** Umschalten
1. under **[!UICONTROL path equals]** set `/content/luma/us/en/user/cart.html`. Auf der Demosite &quot;Luma&quot;wird sichergestellt, dass die Regel nur Trigger auf der Warenkorbseite enthält.
1. Auswählen **[!UICONTROL Änderungen beibehalten]**

   ![Analytics-XDM-Regeln](assets/set-up-analytics-cart-condition.png)

1. under **[!UICONTROL Aktionen]** select **[!UICONTROL Hinzufügen]**
1. Auswählen **[!UICONTROL Adobe Experience Platform Web SDK]** Erweiterung
1. Auswählen **[!UICONTROL Aktionstyp]** as **[!UICONTROL Variable aktualisieren]**
1. Scrollen Sie nach unten zum `commerce` -Objekt ein und wählen Sie aus, um es zu öffnen.
1. Öffnen Sie die **[!UICONTROL productListViews]** -Objekt und -set **[!UICONTROL value]** nach `1`

   ![Einrichten der Produktansicht](assets/set-up-analytics-cart-view.png)

   >[!TIP]
   >
   >Wenn Sie commerce.productListViews.value=1 in XDM festlegen, wird dies automatisch dem `scView` -Ereignis in Analytics



1. Scrollen Sie nach unten zu und wählen Sie **[!UICONTROL productListItems]** array

1. Auswählen **[!UICONTROL Gesamtes Array bereitstellen]**

1. Zuordnung zu **`cart.productInfo`** Datenelement

1. Auswählen `eventType` und auf `commerce.productListViews`

1. Auswählen **[!UICONTROL Änderungen beibehalten]**

1. Auswählen **[!UICONTROL Speichern]** zum Speichern der Regel

Erstellen Sie zwei weitere Regeln für Checkout und Kauf nach demselben Muster mit den folgenden Unterschieden:

**Regelname**: `ecommerce - checkout library loaded - AA (order 20)`

* **[!UICONTROL Bedingung]**: /content/luma/us/en/user/checkout.html
* Stellen Sie `eventType` auf `commerce.checkouts` ein.
* Satz **XDM-Commerce-Ereignis**: commerce.checkout.value to `1`

  >[!TIP]
  >
  >Dies entspricht der Einstellung `scCheckout` -Ereignis in Analytics

**Regelname**: `ecommerce - purchase library loaded - AA (order 20)`

* **[!UICONTROL Bedingung]**: /content/luma/us/en/user/checkout/order/thank-you.html
* Stellen Sie `eventType` auf `commerce.purchases` ein.
* Satz **XDM-Commerce-Ereignis**: commerce.purchases.value to `1`

  >[!TIP]
  >
  >Dies entspricht der Einstellung `purchase` -Ereignis in Analytics

Es gibt zusätzliche Schritte zum Erfassen aller erforderlichen `purchase` Ereignisvariablen:

1. Öffnen **[!UICONTROL commerce]** Objekt
1. Öffnen Sie die **[!UICONTROL bestellen]** Objekt
1. Zuordnung **[!UICONTROL purchaseID]** der `cart.orderId` Datenelement
1. Satz **[!UICONTROL currencyCode]** zum hartcodierten Wert `USD`

   ![Festlegen der purchaseID für Analytics](assets/set-up-analytics-purchase.png)

   >[!TIP]
   >
   >Dies entspricht der Einstellung `s.purchaseID` und `s.currencyCode` Variablen in Analytics


1. Scrollen Sie nach unten zu und wählen Sie **[!UICONTROL productListItems]** array
1. Auswählen **[!UICONTROL Gesamtes Array bereitstellen]**
1. Zuordnung zu **`cart.productInfo.purchase`** Datenelement
1. Wählen Sie **[!UICONTROL Speichern]** aus

Wenn Sie fertig sind, sollten die folgenden Regeln erstellt werden.

![Analytics-XDM-Regeln](assets/set-up-analytics-rules.png)


### Ereignis senden

Nachdem Sie die Variablen festgelegt haben, können Sie die zweite Regel erstellen, um das XDM-Objekt mit dem **[!UICONTROL Ereignis senden]** Aktionstyp.

1. Wählen Sie rechts Folgendes aus: **[!UICONTROL Regel hinzufügen]** zum Erstellen einer weiteren Regel

1. Geben Sie einen Namen für die Regel ein `all pages send event - library loaded - AA (order 50)`.

1. Im **[!UICONTROL Veranstaltungen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

1. Verwenden Sie die **[!UICONTROL Haupterweiterung]** und wählen `Page Bottom` als **[!UICONTROL Ereignistyp]**

1. Unter dem **[!UICONTROL Name]** Feld, nennen Sie es `Core - Page Bottom - order 50`. Auf diese Weise können Sie den Trigger mit einem aussagekräftigen Namen beschreiben.

1. Auswählen **[!UICONTROL Erweitert]** Dropdown und `50` in **[!UICONTROL Bestellung]**. Dadurch wird sichergestellt, dass die zweite Regel Trigger nach der ersten Regel, die Sie auf Trigger als `1`.

1. Auswählen **[!UICONTROL Änderungen beibehalten]** zum Hauptregelbildschirm zurückzukehren
   ![Seitenende auswählen, Trigger](assets/create-tag-rule-trigger-bottom-send.png)

1. Im **[!UICONTROL Aktionen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

1. Als **[!UICONTROL Erweiterung]** auswählen  **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als  **[!UICONTROL Aktionstyp]** auswählen  **[!UICONTROL Ereignis senden]**

1. Als **[!UICONTROL XDM]**, wählen Sie die `xdm.variable.content` Datenelement, das in der vorherigen Lektion erstellt wurde

1. Auswählen **[!UICONTROL Änderungen beibehalten]** zum Hauptregelbildschirm zurückzukehren

   ![Hinzufügen der Aktion &quot;Ereignis senden&quot;](assets/create-rule-send-event-action.png)
1. Auswählen **[!UICONTROL Speichern]** zum Speichern der Regel

   ![Speichern der Regel](assets/create-rule-save-rule.png)

## Regel in einer Bibliothek veröffentlichen

Veröffentlichen Sie dann die Regel in Ihrer Entwicklungsumgebung, damit Sie überprüfen können, ob sie funktioniert.

So erstellen Sie eine Bibliothek:

1. Navigieren Sie zu **[!UICONTROL Veröffentlichungsfluss]** in der linken Navigation

1. Auswählen **[!UICONTROL Bibliothek hinzufügen]**

   ![Bibliothek hinzufügen](assets/rule-publish-library.png)
1. Für **[!UICONTROL Name]**, eingeben `Luma Web SDK Tutorial`
1. Für **[!UICONTROL Umgebung]** auswählen `Development`
1. Auswählen  **[!UICONTROL Alle geänderten Ressourcen hinzufügen]**

   >[!NOTE]
   >
   >    Zusätzlich zur Adobe Experience Platform Web SDK-Erweiterung und der `all pages global content variables - library loaded - AA (order 50)` -Regel sehen Sie die Tag-Komponenten, die in vorherigen Lektionen erstellt wurden. Die Haupterweiterung enthält das grundlegende JavaScript, das für alle Web-Tag-Eigenschaften erforderlich ist.

1. Auswählen **[!UICONTROL Speichern und erstellen für Entwicklung]**

   ![Erstellen und Erstellen der Bibliothek](assets/create-tag-rule-library-changes.png)

Die Erstellung der Bibliothek kann einige Minuten dauern. Wenn sie abgeschlossen ist, wird links neben dem Bibliotheksnamen ein grüner Punkt angezeigt:

![Build-Abschluss](assets/create-rule-development-success.png)

Wie Sie auf der [!UICONTROL Veröffentlichungsfluss] -Bildschirm gibt es viel mehr im Veröffentlichungsprozess, was über den Rahmen dieses Tutorials hinausgeht. In diesem Tutorial wird nur eine einzige Bibliothek in Ihrer Entwicklungsumgebung verwendet.

Jetzt können Sie die Daten in der Anfrage mithilfe des Adobe Experience Platform Debuggers überprüfen.

[Nächste ](validate-with-debugger.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
