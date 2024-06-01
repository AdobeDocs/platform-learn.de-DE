---
title: Einrichten von Adobe Analytics mithilfe des Experience Platform Web SDK
description: Erfahren Sie, wie Sie Adobe Analytics mit dem Experience Platform Web SDK einrichten. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
solution: Data Collection, Analytics
jira: KT-15408
exl-id: de86b936-0a47-4ade-8ca7-834c6ed0f041
source-git-commit: a8431137e0551d1135763138da3ca262cb4bc4ee
workflow-type: tm+mt
source-wordcount: '2865'
ht-degree: 1%

---

# Einrichten von Adobe Analytics mit dem Adobe Experience Platform Web SDK

Erfahren Sie, wie Sie Adobe Analytics mit [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/en/docs/platform-learn/data-collection/web-sdk/overview)erstellen Tag-Regeln, um Daten an Adobe Analytics zu senden, und überprüfen, ob Analytics Daten erwartungsgemäß erfasst.

[Adobe Analytics](https://experienceleague.adobe.com/de/docs/analytics) ist eine branchenführende Anwendung, mit der Sie Ihre Kunden besser verstehen und Ihr Geschäft mit Customer Intelligence steuern können.

![Diagramm Web SDK zu Adobe Analytics](assets/dc-websdk-aa.png)

## Lernziele

Am Ende dieser Lektion können Sie:

* Konfigurieren eines Datenspeichers zur Aktivierung von Adobe Analytics
* Ermitteln, welche Standard-XDM-Felder automatisch Analytics-Variablen zugeordnet werden
* Analytics-Variablen im Datenobjekt festlegen
* Senden von Daten an eine andere Report Suite durch Überschreiben des Datastreams
* Validieren von Adobe Analytics-Variablen mithilfe von Debugger und Assurance

## Voraussetzungen

Um diese Lektion abzuschließen, müssen Sie zunächst:

* Machen Sie sich mit Adobe Analytics vertraut und haben Sie Zugriff auf diese.

* Sie verfügen über mindestens eine Report Suite-ID für Tests/Entwicklung. Wenn Sie nicht über eine Report Suite für Tests/Entwicklung verfügen, die Sie für dieses Tutorial verwenden können, [erstellen Sie bitte eine](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/t-create-a-report-suite).

* Schließen Sie die früheren Lektionen in den Abschnitten Erstkonfiguration und Tags-Konfiguration dieses Tutorials ab.

## Konfigurieren des Datenspeichers

Das Platform Web SDK sendet Daten von Ihrer Website an Platform Edge Network. Ihr Datastream teilt dann Platform Edge Network mit, an welche Adobe Analytics Report Suites Ihre Daten gesendet werden sollen.

1. Navigieren Sie zu [Datenerfassung](https://experience.adobe.com/#/data-collection){target="blank"} Benutzeroberfläche
1. Wählen Sie im linken Navigationsbereich die Option **[!UICONTROL Datenspeicher]**
1. Wählen Sie die zuvor erstellte `Luma Web SDK: Development Environment` datastream

   ![Wählen Sie den Datenspeicher des Luma Web SDK aus.](assets/datastream-luma-web-sdk-development.png)

1. Auswählen **[!UICONTROL Dienst hinzufügen]**
   ![Hinzufügen eines Dienstes zum Datastream](assets/datastream-analytics-addService.png)
1. Auswählen **[!UICONTROL Adobe Analytics]** als **[!UICONTROL Dienst]**
1. Geben Sie die **[!UICONTROL Report Suite-ID]** Ihrer Entwicklungs-Report Suite
1. Auswählen **[!UICONTROL Speichern]**

   ![Analyse zum Speichern von Datensätzen](assets/datastream-add-analytics.png)

   >[!TIP]
   >
   >Hinzufügen weiterer Report Suites durch Auswahl von **[!UICONTROL Report Suite hinzufügen]** entspricht Multi-Suite-Tagging.

>[!WARNING]
>
>In diesem Tutorial konfigurieren Sie nur die Adobe Analytics Report Suite für Ihre Entwicklungsumgebung. Wenn Sie Datenspeicher für Ihre eigene Website erstellen, sollten Sie zusätzliche Datenspeicher und Report Suites für Ihre Staging- und Produktionsumgebungen erstellen.

## Analytics-Variablen festlegen

Es gibt mehrere Möglichkeiten, Analytics-Variablen in einer Web SDK-Implementierung festzulegen:

1. Automatische Zuordnung von XDM-Feldern zu Analytics-Variablen (automatisch).
1. Festlegen von Feldern in der `data` -Objekt (empfohlen).
1. Ordnen Sie XDM-Felder Analytics-Variablen in Analytics-Verarbeitungsregeln zu (nicht mehr empfohlen).
1. Ordnen Sie Analytics-Variablen direkt im XDM-Schema zu (nicht mehr empfohlen).

Ab Mai 2024 müssen Sie kein XDM-Schema mehr erstellen, um Adobe Analytics mit dem Platform Web SDK zu implementieren. Die `data` -Objekt (und der `data.variable` Datenelement, das Sie im [Erstellen von Datenelementen](create-data-elements.md) Lektion) verwendet werden, um alle benutzerdefinierten Analytics-Variablen festzulegen. Das Festlegen dieser Variablen im Datenobjekt ist für bestehende Analytics-Kunden bekannt, effizienter als die Verwendung der Benutzeroberfläche für Verarbeitungsregeln und verhindert, dass unnötige Daten in Echtzeit-Kundenprofilen Platz nehmen (wichtig bei Real-time Customer Data Platform oder Journey Optimizer).

### Automatisch zugeordnete Felder

Viele XDM-Felder werden automatisch Analytics-Variablen zugeordnet. Die aktuellste Liste der Zuordnungen finden Sie unter [Analytics-Variablenzuordnung in Adobe Experience Edge](https://experienceleague.adobe.com/en/docs/experience-platform/edge/data-collection/adobe-analytics/automatically-mapped-vars).

Dies tritt auf, wenn _auch wenn Sie kein benutzerdefiniertes Schema definiert haben_. Experience Platform Web SDK erfasst automatisch einige Daten und sendet sie als XDM-Felder an Platform Edge Network. Beispielsweise liest das Web SDK die aktuelle Seiten-URL und sendet sie als XDM-Feld `web.webPageDetails.URL`. Dieses Feld wird an Adobe Analytics weitergeleitet und füllt automatisch die Seiten-URL-Berichte in Adobe Analytics.

Wenn Sie das Web SDK für Adobe Analytics mit einem XDM-Schema implementieren, wie in diesem Tutorial beschrieben, weisen einige der XDM-Felder, die Sie benutzerdefiniert implementiert haben, automatisch Analytics-Variablen zu, wie in dieser Tabelle beschrieben:

| Automatisch zugeordnete Variablen von XDM zu Analytics | Adobe Analytics-Variable |
|-------|---------|
| `identitymap.ecid.[0].id` | mid |
| `web.webPageDetails.name` | s.pageName |
| `web.webPageDetails.server` | s.server |
| `web.webPageDetails.siteSection` | s.channel |
| `commerce.productViews.value` | prodView |
| `commerce.productListViews.value` | scView |
| `commerce.checkouts.value` | scCheckout |
| `commerce.purchases.value` | Kauf |
| `commerce.order.currencyCode` | s.currencyCode |
| `commerce.order.purchaseID` | s.purchaseID |
| `productListItems[].SKU` | s.products=;product name;;; (primary - siehe Hinweis unten) |
| `productListItems[].name` | s.products=;product name;;; (Fallback - siehe Hinweis unten) |
| `productListItems[].quantity` | s.products=;;Produktmenge;; |
| `productListItems[].priceTotal` | s.product=;;;Produktpreis; |

Die einzelnen Abschnitte der Analytics-Produktzeichenfolge werden durch verschiedene XDM-Variablen unter der `productListItems` -Objekt.

>[!NOTE]
>
>Am 18. August 2022 `productListItems[].SKU` hat Priorität für die Zuordnung zum Produktnamen in der Variablen s.products .
>Der auf `productListItems[].name` nur dann dem Produktnamen zugeordnet wird, wenn `productListItems[].SKU` existiert nicht. Andernfalls ist sie nicht zugeordnet und in Kontextdaten verfügbar.
>Setzen Sie keine leere Zeichenfolge oder null auf `productListItems[].SKU`. Dies hat den unerwünschten Effekt, dass die Zuordnung zum Produktnamen in der Variablen s.products vorgenommen wird.


### Festlegen von Variablen im Datenobjekt

Aber was ist mit eVars, Props und Ereignissen? Festlegen von Variablen in `data` -Objekt ist die empfohlene Methode zum Festlegen dieser Analytics-Variablen mit dem Web SDK. Durch das Festlegen von Variablen im Datenobjekt können auch alle automatisch zugeordneten Variablen überschrieben werden.

Zunächst einmal, was ist das `data` Objekt? In jedem Web SDK-Ereignis können Sie zwei Objekte mit benutzerdefinierten Daten senden, die `xdm` und dem `data` -Objekt. Beide werden an Platform Edge Network gesendet, jedoch nur die `xdm` -Objekt an den Experience Platform-Datensatz gesendet. Eigenschaften in `data` -Objekt kann auf der Edge-Seite `xdm` -Felder, die die Funktion &quot;Datenvorbereitung für Datenerfassung&quot;verwenden, andernfalls jedoch nicht an Experience Platform gesendet werden. Dadurch ist es ideal, Daten an Anwendungen wie Analytics zu senden, die nativ nicht auf Experience Platform basieren.

Im Folgenden finden Sie die beiden Objekte in einem allgemeinen Web SDK-Aufruf:

![Daten- und xdm-Objekte](assets/analytics-data-object-intro.png)

Adobe Analytics ist so konfiguriert, dass es nach Eigenschaften im `data.__adobe.analytics` -Objekt und verwenden Sie sie für Analytics-Variablen.

Nun sehen wir, wie das funktioniert. Setzen wir uns `eVar1` und `prop1` mit unserem Seitennamen und sehen Sie, wie XDM-mapped-Wert überschrieben werden kann.

1. Tag-Regel öffnen `all pages - library loaded - set global variables - 1`
1. Hinzufügen neuer **[!UICONTROL Aktion]**
1. Auswählen **[!UICONTROL Adobe Experience Platform Web SDK]** Erweiterung
1. Auswählen **[!UICONTROL Aktionstyp]** as **[!UICONTROL Variable aktualisieren]**
1. Auswählen `data.variable` als **[!UICONTROL Datenelement]**
1. Wählen Sie die **[!UICONTROL analytics]** Objekt
1. Satz `eVar1` als `page.pageInfo.pageName` Datenelement
1. Satz `prop1` zum Kopieren des Werts von `eVar1`
1. So testen Sie das Überschreiben von XDM-zugeordneten Werten in der **[!UICONTROL Zusätzliche Eigenschaft]** -Abschnitt Seitennamen als statischen Wert festlegen `test`
1. Regel speichern


Jetzt müssen wir das Datenobjekt in unsere Versandereignisregel einbeziehen.

1. Tag-Regel öffnen `all pages - library loaded - send event - 50`
1. Öffnen Sie die **[!UICONTROL Ereignis senden]** action
1. Auswählen `data.variable` als **[!UICONTROL Daten]**
1. Auswählen **[!UICONTROL Änderungen beibehalten]**
1. Auswählen **[!UICONTROL Speichern]**



<!--


### Map to Analytics variables with processing rules

All fields in the XDM schema become available to Adobe Analytics as Context Data Variables with the following prefix `a.x.`. For example, `a.x.web.webinteraction.region`

In this exercise, you map one XDM variable to a prop. Follow these same steps for any custom mapping that you must do for any `eVar`, `prop`, `event`, or variable accessible via Processing Rules.

1. Go to the Analytics interface
1. Go to [!UICONTROL Admin] > [!UICONTROL Admin Tools] > [!UICONTROL Report Suites ]
1. Select the dev/test report suite that you are using for the tutorial > [!UICONTROL Edit Settings] > [!UICONTROL General] > [!UICONTROL Processing Rules]

    ![Analytics Purchase](assets/analytics-process-rules.png)   

1. Create a rule to **[!UICONTROL Overwrite value of]** `[!UICONTROL Product SKU (prop1)]` to `a.x.productlistitems.0.sku`. Remember to add a note about why you are creating the rule and name your rule title. Select **[!UICONTROL Save]**

    ![Analytics Purchase](assets/analytics-set-processing-rule.png)   

    >[!IMPORTANT]
    >
    >The first time you map to a processing rule, the UI does not show you the context data variables from the XDM object. To fix that select any value, Save, and come back to edit. All XDM variables should now appear.

### Map to Analytics variables using the Adobe Analytics field group

An alternative to processing rules is to map to Analytics variables in the XDM schema using the `Adobe Analytics ExperienceEvent Template` field group. This approach has gained popularity because many users find it simpler than configuring processing rules, however, by increasing the size of the XDM payload it could in turn increase the profile size in other applications like Real-Time CDP.

To add the `Adobe Analytics ExperienceEvent Template` field group to your schema:

1. Open the [Data Collection](https://experience.adobe.com/#/data-collection){target="blank"} interface
1. Select **[!UICONTROL Schemas]** from the left navigation
1. Make sure you are in the sandbox you are using from the tutorial
1. Open your `Luma Web Event Data` schema
1. In the **[!UICONTROL Field Groups]** section, select **[!UICONTROL Add]**
1. Find the `Adobe Analytics ExperienceEvent Template` field group and add it to your schema


Now, set a merchandising eVar in the product string. With the `Adobe Analytics ExperienceEvent Template` field group, you are able to map variables to merchandising eVars or events within the product string. This is also known as setting **Product Syntax Merchandising**. 

1. Go back to your tag property

1. Open the rule `ecommerce - library loaded - set product details variables - 20`

1. Open the **[!UICONTROL Set Variable]** action

1. Select to open `_experience > analytics > customDimensions > eVars > eVar1`

1. Set the **[!UICONTROL Value]** to `%product.productInfo.title%`

1. Select **[!UICONTROL Keep Changes]**

    ![Product SKU XDM object Variable](assets/set-up-analytics-product-merchandising.png)

1. Select **[!UICONTROL Save]** to save the rule

As you just saw, basically all of the Analytics variables can be set in the `Adobe Analytics ExperienceEvent Template` field group.

>[!NOTE]
>
> Notice the `_experience` object under `productListItems` > `Item 1`. Setting any variable under this [!UICONTROL object] sets Product Syntax eVars or Events.

-->

## Daten an eine andere Report Suite senden

Möglicherweise möchten Sie ändern, an welche Adobe Analytics Report Suite-Daten gesendet werden, wenn sich Besucher auf bestimmten Seiten befinden. Dies erfordert eine Konfiguration sowohl im Datastream als auch in einer Regel.

### Konfigurieren des Datenspeichers für eine Report Suite-Überschreibung

So konfigurieren Sie die Einstellung zum Überschreiben der Adobe Analytics Report Suite im Datastream:

1. Datenspeicher öffnen
1. Bearbeiten Sie die **[!UICONTROL Adobe Analytics]** Konfiguration durch Öffnen der ![more](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Menü und anschließend **[!UICONTROL Bearbeiten]**

   ![Datastream überschreiben](assets/datastream-edit-analytics.png)

1. Auswählen **[!UICONTROL Erweiterte Optionen]** zum Öffnen **[!UICONTROL Report Suite - Überschreibungen]**

1. Wählen Sie die Report Suites aus, die Sie überschreiben möchten. In diesem Fall `Web SDK Course Dev` und `Web SDK Course Stg`

1. Auswählen **[!UICONTROL Speichern]**

   ![Datastream überschreiben](assets/analytics-datastreams-edit-adobe-analytics-configurations-report-suites.png)


### Konfigurieren einer Regel für eine Report Suite-Überschreibung

Erstellen wir eine Regel, um einen zusätzlichen Seitenansichtsaufruf an eine andere Report Suite zu senden. Verwenden Sie die Funktion zur Außerkraftsetzung des Datenspeichers, um die Report Suite für eine Seite mithilfe der Variablen **[!UICONTROL Ereignis senden]** Aktion.

1. Neue Regel erstellen, sie benennen `homepage - library loaded - AA report suite override - 51`

1. Wählen Sie das Pluszeichen unter **[!UICONTROL Ereignis]** , um einen neuen Trigger hinzuzufügen

1. under **[!UICONTROL Erweiterung]** auswählen **[!UICONTROL Core]**

1. under **[!UICONTROL Ereignistyp]** auswählen **[!UICONTROL Bibliothek geladen (Seitenanfang)]**

1. Zum Öffnen auswählen **[!UICONTROL Erweiterte Optionen]**, Typ in `51`. Dadurch wird sichergestellt, dass die Regel nach dem `all pages - library loaded - send event - 50` , das das Grundlinien-XDM mit der **[!UICONTROL Variable aktualisieren]** Aktionstyp.
1. Auswählen **[!UICONTROL Änderungen beibehalten]**

   ![Analytics Report Suite - Überschreibung](assets/set-up-analytics-rs-override.png)

1. under **[!UICONTROL Bedingungen]**, wählen Sie **[!UICONTROL Hinzufügen]**

1. Urlaub **[!UICONTROL Logiktyp]** as **[!UICONTROL Normal]**

1. Urlaub **[!UICONTROL Erweiterungen]** as **[!UICONTROL Core]**

1. Auswählen **[!UICONTROL Bedingungstyp]** as **[!UICONTROL Pfad ohne Abfragezeichenfolge]**

1. Lassen Sie rechts die **[!UICONTROL Regex]** Umschalten deaktiviert

1. under **[!UICONTROL path equals]** set `/content/luma/us/en.html`. Auf der Demosite &quot;Luma&quot;wird sichergestellt, dass die Regel nur Trigger auf der Startseite enthält.

1. Auswählen **[!UICONTROL Änderungen beibehalten]**

   ![Bedingung für die Überschreibung der Analytics-Report Suite](assets/set-up-analytics-override-condition.png)

1. under **[!UICONTROL Aktionen]** select **[!UICONTROL Hinzufügen]**

1. Als **[!UICONTROL Erweiterung]** auswählen **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als **[!UICONTROL Aktionstyp]** auswählen **[!UICONTROL Ereignis senden]**

1. Als **[!UICONTROL XDM-Daten]**, wählen Sie die `xdm.variable.content` Datenelement, das Sie im [Erstellen von Datenelementen](create-data-elements.md) Lektion

1. Als **[!UICONTROL Daten]**, wählen Sie die `data.variable` Datenelement, das Sie im [Erstellen von Datenelementen](create-data-elements.md) Lektion

   ![Überschreiben des Analytics-Datastreams](assets/set-up-analytics-datastream-override-1.png)

1. Scrollen Sie nach unten zum **[!UICONTROL Überschreibungen von Datenspeicherkonfigurationen]** Abschnitt

1. Lassen Sie die **[!UICONTROL Entwicklung]** ausgewählt ist.

   >[!TIP]
   >
   >    Diese Registerkarte bestimmt, in welcher Tagumgebung das Außerkraftsetzen erfolgt. Für diese Übung geben Sie nur die Entwicklungsumgebung an. Denken Sie jedoch daran, dies auch in der **[!UICONTROL Produktion]** Umgebung.

1. Wählen Sie die **[!UICONTROL Sandbox]** Sie für das Tutorial verwenden
1. Wählen Sie die **[!UICONTROL Datastream]** in diesem Fall `Luma Web SDK: Development Environment`

1. under **[!UICONTROL Report Suites]** wählen Sie die Report Suite aus, für die Sie die Site überschreiben möchten. In diesem Fall `tmd-websdk-course-stg`.

1. Auswählen **[!UICONTROL Änderungen beibehalten]**

1. und **[!UICONTROL Speichern]** Ihre Regel

   ![Überschreiben des Analytics-Datastreams](assets/analytics-tags-report-suite-override.png)


## Erstellen der Entwicklungsumgebung

Fügen Sie Ihre aktualisierten Regeln zu Ihren `Luma Web SDK Tutorial` -Tag-Bibliothek und erstellen Sie Ihre Entwicklungsumgebung neu.

Herzlichen Glückwunsch! Der nächste Schritt besteht darin, Ihre Adobe Analytics-Implementierung über das Experience Platform Web SDK zu validieren.

## Adobe Analytics mit Debugger überprüfen

Erfahren Sie, wie Sie mit der Funktion &quot;Edge Trace&quot;des Experience Platform Debuggers überprüfen, ob Adobe Analytics die ECID, Seitenansichten, die Produktzeichenfolge und E-Commerce-Ereignisse erfasst.

Im [Debugger](validate-with-debugger.md) In der Lektion haben Sie erfahren, wie Sie die clientseitige XDM-Anforderung mit dem Platform Debugger und der Browser-Entwicklerkonsole überprüfen, die dem Debugging einer `AppMeasurement.js` Analytics-Implementierung. Sie haben auch erfahren, wie Sie serverseitige Anfragen für Platform Edge Network, die an Adobe-Anwendungen gesendet werden, validieren und wie Sie eine vollständig verarbeitete Payload mithilfe von Assurance anzeigen.

Um zu überprüfen, ob Analytics Daten ordnungsgemäß über das Experience Platform Web SDK erfasst, müssen Sie zwei Schritte weiter gehen:

1. Validieren Sie mithilfe der Edge Trace-Funktion des Experience Platform-Debuggers, wie Daten vom XDM-Objekt im Platform-Edge Network verarbeitet werden.
1. Überprüfen der vollständigen Verarbeitung von Daten durch Analytics mithilfe von Adobe Experience Platform Assurance

### Experience Cloud ID-Überprüfung

1. Navigieren Sie zu [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"}
1. Wählen Sie die Anmelde-Schaltfläche oben rechts aus und verwenden Sie die Anmeldeinformationen u: test@adobe.com p: test to authentication
1. Öffnen Sie den Experience Platform Debugger und [Ändern Sie die Tag-Eigenschaft auf der Site in Ihre eigene Entwicklungseigenschaft.](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)


1. Um den Edge Trace zu aktivieren, gehen Sie zum Experience Platform Debugger und wählen Sie im linken Navigationsmenü die Option **[!UICONTROL Protokolle]** und wählen Sie dann die **[!UICONTROL Edge]** und wählen Sie **[!UICONTROL Verbinden]**

   ![Edge Trace verbinden](assets/analytics-debugger-edgeTrace.png)

1. Es ist vorerst leer

   ![Connected Edge Trace](assets/analytics-debugger-edge-connected.png)

1. Aktualisieren Sie die Seite &quot;Luma&quot;und aktivieren Sie Experience Platform Debugger erneut. Sie sollten sehen, dass Daten vorliegen. Die Zeile beginnt mit **[!UICONTROL Automatische Zuordnung von Analytics]** ist das Adobe Analytics-Beacon
1. Wählen Sie aus, um beide `[!UICONTROL mappedQueryParams]` Dropdown und das zweite Dropdown-Menü zur Ansicht von Analytics-Variablen

   ![Analytics-Beacon Edge Trace](assets/analytics-debugger-edge-analytics.png)

   >[!TIP]
   >
   >Das zweite Dropdown-Menü entspricht der Analytics Report Suite-ID, an die Sie Daten senden. Sie sollte mit Ihrer eigenen Report Suite übereinstimmen, nicht mit der im Screenshot.

1. Scrollen Sie nach unten, um `[!UICONTROL c.a.x.identitymap.ecid.[0].id]`. Es handelt sich dabei um eine Kontextdatenvariable, die ECID erfasst
1. Scrollen Sie nach unten, bis Analytics angezeigt wird. `[!UICONTROL mid]` -Variable. Beide IDs stimmen mit der Experience Cloud-ID Ihres Geräts überein.
1. Auf der Site &quot;Luma&quot;:

   ![Analytics-ECID](assets/analytics-debugger-ecid.png)

   >[!NOTE]
   >
   >Da Sie angemeldet sind, nehmen Sie sich einen Moment Zeit, um die authentifizierte ID zu validieren `112ca06ed53d3db37e4cea49cc45b71e` für den Benutzer **`test@adobe.com`** wird auch im `[!UICONTROL c.a.x.identitymap.lumacrmid.[0].id]`

### Überprüfung der Report Suite-Überschreibung

Oben haben Sie eine Datastream-Überschreibung für die [Startseite von Luma](https://luma.enablementadobe.com/content/luma/us/en.html).  Überprüfen dieser Konfiguration

1. Suchen nach einer Zeile mit **[!UICONTROL Datastream-Konfiguration nach Anwendung der Außerkraftsetzung]**. Hier finden Sie die primäre Report Suite und die zusätzlichen Report Suites, die für die Report Suite-Überschreibung konfiguriert wurden.

   ![Überprüfung der Analytics-Report Suite-Liste außer Kraft setzen](assets/aep-debugger-datastream-override.png)

1. Scrollen Sie nach unten zu der Zeile, beginnend mit **[!UICONTROL Automatische Zuordnung von Analytics]**  und überprüfen Sie, dass `[!UICONTROL reportSuiteIds]` zeigt die Report Suite an, die Sie in Ihren Überschreibungskonfigurationen angegeben haben

   ![Überprüfung von Analytics Report Suite-Aufrufen außer Kraft setzen](assets/aep-debugger-analytics-report-suite-override.png)

### Überprüfung der Inhaltsseitenansichten

Rufen Sie eine Produktseite auf, z. B. [Didi Sport Watch-Produktseite](https://luma.enablementadobe.com/content/luma/us/en/products/gear/watches/didi-sport-watch.html#24-WG02).  Überprüfen Sie, ob die Seitenansichten des Inhalts von Analytics erfasst werden.

1. Suchen nach `[!UICONTROL c.a.x.web.webpagedetails.pageviews.value]=1`.
1. Scrollen Sie nach unten, um die `[!UICONTROL gn]` -Variable. Dies ist die dynamische Analytics-Syntax für die `[!UICONTROL s.pageName]` -Variable. Sie erfasst den Seitennamen aus der Datenschicht.

   ![Analytics-Produktzeichenfolge](assets/analytics-debugger-edge-page-view.png)

### Validierung von Produktzeichenfolgen und E-Commerce-Ereignissen

Da Sie sich bereits auf einer Produktseite befinden, verwendet diese Übung weiterhin denselben Edge Trace, um Produktdaten zu überprüfen, die von Analytics erfasst werden. Sowohl die Produktzeichenfolge als auch die E-Commerce-Ereignisse werden Analytics automatisch XDM-Variablen zugeordnet. Solange Sie dem entsprechenden `productListItem` XDM-Variable während [Konfigurieren eines XDM-Schemas für Adobe Analytics](setup-analytics.md#configure-an-xdm-schema-for-adobe-analytics), übernimmt das Platform-Edge Network die Zuordnung der Daten zu den entsprechenden Analysevariablen.

**Überprüfen Sie zunächst, ob die `Product String` festgelegt ist**

1. Suchen nach `[!UICONTROL c.a.x.productlistitems.][0].[!UICONTROL sku]`. Die Variable erfasst den Datenelementwert, den Sie der Variablen `productListItems.item1.sku` früher in dieser Lektion
1. Suchen Sie auch nach `[!UICONTROL c.a.x.productlistitems.][0].[!UICONTROL _experience.analytics.customdimensions.evars.evar1]`. Die Variable erfasst den Datenelementwert, dem Sie zugeordnet sind `productListItems.item1._experience.analytics.customdimensions.evars.evar1`
1. Scrollen Sie nach unten, um die `[!UICONTROL pl]` -Variable. Dies ist die dynamische Syntax der Analytics-Variablen mit der Produktzeichenfolge .
1. Beachten Sie, dass der Produktname aus der Datenschicht dem `[!UICONTROL c.a.x.productlistitems.][0].[!UICONTROL sku]` und `[!UICONTROL product]` -Parameter der Produktzeichenfolge.  Darüber hinaus wird der Produktname aus der Datenschicht der Merchandising-evar1 in der Produktzeichenfolge zugeordnet.

   ![Analytics-Produktzeichenfolge](assets/analytics-debugger-prodstring.png)

   Die Edge Trace-Behandlung `commerce` Ereignisse geringfügig anders als `productList` Dimensionen. Es wird keine Kontextdatenvariable angezeigt, die auf die gleiche Weise zugeordnet ist wie der Produktname, der `[!UICONTROL c.a.x.productlistitem.[0].name]` höher. Stattdessen zeigt Edge Trace die endgültige automatische Ereigniszuordnung in Analytics an `event` -Variable. Das Platform-Edge Network ordnet es entsprechend zu, solange Sie dem entsprechenden XDM-Element zuordnen `commerce` Variable während [Konfiguration des Schemas für Adobe Analytics](setup-analytics.md#configure-an-xdm-schema-for-adobe-analytics); in diesem Fall die `commerce.productViews.value=1`.

1. Scrollen Sie im Experience Platform Debugger-Fenster nach unten zum `[!UICONTROL events]` festgelegt ist, wird `[!UICONTROL prodView]`

1. Hinweis `[!UICONTROL c.a.x.eventType]` auf `commerce.productViews` da Sie sich auf einer Produktseite befinden.

   >[!TIP]
   >
   > Die `ecommerce - pdp library loaded - AA (order 20)` -Regel überschreibt den Wert von `eventType` festgelegt durch `all pages global content variables - library loaded - AA (order 1)` -Regel, da sie später in der Sequenz auf &quot;Trigger&quot;festgelegt ist.


   ![Analytics-Produktansicht](assets/analytics-debugger-prodView.png)

**Überprüfen, ob die restlichen E-Commerce-Ereignisse und Produktzeichenfolgen für Analytics festgelegt sind**

1. Hinzufügen [Didi Sport Watch](https://luma.enablementadobe.com/content/luma/us/en/products/gear/watches/didi-sport-watch.html#24-WG02) in den Warenkorb
1. Navigieren Sie zu [Einkaufswagenseite](https://luma.enablementadobe.com/content/luma/us/en/user/cart.html), aktivieren Sie Edge Trace für

   * `eventType` auf `commerce.productListViews`
   * `[!UICONTROL events: "scView"]`, und
   * die Produktzeichenfolge festgelegt ist

   ![Analytics-Warenkorbansicht](assets/analytics-debugger-cartView.png)

1. Fahren Sie mit dem Checkout fort und suchen Sie nach Edge Trace für

   * `eventType` auf `commerce.checkouts`
   * `[!UICONTROL events: "scCheckout"]`, und
   * die Produktzeichenfolge festgelegt ist

   ![Analytics-Checkout](assets/analytics-debugger-checkout.png)

1. Füllen Sie nur die **Vorname** und **Nachname** Felder im Versandformular und wählen Sie **Weiter**. Wählen Sie auf der nächsten Seite **Bestellung platzieren**
1. Überprüfen Sie auf der Bestätigungsseite Edge Trace auf

   * `eventType` auf `commerce.purchases`
   * Kaufereignis festgelegt `[!UICONTROL events: "purchase"]`
   * Währungscode-Variable festgelegt `[!UICONTROL cc: "USD"]`
   * Kauf-ID festgelegt in `[!UICONTROL pi]`
   * Produktzeichenfolge `[!UICONTROL pl]` Festlegen von Produktname, Menge und Preis

   ![Analytics-Kauf](assets/analytics-debugger-purchase.png)



## Validieren von Adobe Analytics mithilfe von Assurance

Mit Adobe Experience Platform Assurance können Sie die Datenerfassung und die Bereitstellung von Erlebnissen auf Ihrer Website und in Ihrer mobilen Anwendung überprüfen, testen, simulieren und validieren.

In der vorherigen Übung haben Sie überprüft, ob Adobe Analytics die ECID, Seitenansichten, die Produktzeichenfolge und E-Commerce-Ereignisse mit der Edge Trace-Funktion des Experience Platform Debuggers erfasst.  Als Nächstes validieren Sie dieselben Ereignisse mit Adobe Experience Platform Assurance, einer alternativen Schnittstelle für den Zugriff auf dieselben Daten in Edge Trace.

Wie Sie in der [Assurance](validate-with-assurance.md) Lektion, es gibt mehrere Möglichkeiten, eine Zuverlässigkeitssitzung zu initiieren. Da Sie bereits einen Adobe Experience Platform Debugger geöffnet haben, bei dem eine Edge Trace-Sitzung von der letzten Übung aus initiiert wurde, empfehlen wir, über den Debugger auf &quot;Assurance&quot;zuzugreifen:
![Assemblierung durch Adobe Experience Platform-Datenerfassung](assets/assurance-open-aep-debugger.png)

Innerhalb der **[!UICONTROL &quot;Web SDK-Tutorial 3&quot;]** Sitzungseintrag **[!UICONTROL &quot;hitdebugger&quot;]** in die Ereignissuchleiste, um die Ergebnisse nach den nach der Verarbeitung in Adobe Analytics verarbeiteten Daten zu filtern.
![Assurance Adobe Analytics - Nachbearbeitete Daten](assets/assurance-hitdebugger.png)

### Experience Cloud ID-Überprüfung

Um zu überprüfen, ob Adobe Analytics die ECID erfasst, wählen Sie ein Beacon aus und öffnen Sie die Payload.  Der Anbieter für dieses Beacon sollte **[!UICONTROL com.adobe.analytics.hitdebugger]**
![Adobe Analytics-Validierung mit Assurance](assets/assurance-hitdebugger-payload.png)

Scrollen Sie dann nach unten zu **[!UICONTROL mcvisId]** , um zu überprüfen, ob die ECID korrekt erfasst wurde
![Experience Cloud ID-Validierung mit Assurance](assets/assurance-hitdebugger-mcvisId.png)

### Überprüfung der Inhaltsseitenansichten

Überprüfen Sie mit demselben Beacon, ob die Seitenansichten des Inhalts der richtigen Adobe Analytics-Variablen zugeordnet sind.
Nach unten scrollen zu **[!UICONTROL pageName]** , um zu überprüfen, dass die `Page Name` korrekt erfasst wurde
![Validierung von Seitennamen mit Assurance](assets/assurance-hitdebugger-content-pagename.png)

### Validierung von Produktzeichenfolgen und E-Commerce-Ereignissen

Nach denselben Validierungsanwendungsfällen, die bei der obigen Validierung mit dem Experience Platform Debugger verwendet werden, verwenden Sie dasselbe Beacon zur Validierung der `Ecommerce Events` und `Product String`.

1. Suchen Sie nach Payload , wobei die **[!UICONTROL events]** contain `prodView`
   ![Product String-Validierung mit Assurance](assets/assurance-hitdebugger-prodView-event.png)
1. Nach unten scrollen zu **[!UICONTROL product-string]** validieren Sie die `Product String`.
   * Beachten Sie die `Product SKU` und `Merchandizing eVar1`.
1. Scrollen Sie weiter nach unten und überprüfen Sie, ob `prop1`, die Sie mithilfe der Verarbeitungsregeln im vorherigen Abschnitt konfiguriert haben, enthält die `Product SKU`\
   ![Produktzeichenfolge mit Merchandising-Variablenvalidierung mit Garantie](assets/assurance-hitdebugger-prodView-productString-merchVar.png)

Überprüfen Sie weiterhin Ihre Implementierung, indem Sie sich die Warenkorb-, Checkout- und Kaufereignisse ansehen.

1. Suchen Sie nach Payload , wobei die **[!UICONTROL events]** contain `scView` und validieren Sie die Produktzeichenfolge.
   ![Product String-Validierung mit Assurance](assets/assurance-hitdebugger-scView-event.png)
1. Suchen Sie nach Payload , wobei die **[!UICONTROL events]** contain `scCheckout` und validieren Sie die Produktzeichenfolge.
   ![Product String-Validierung mit Assurance](assets/assurance-hitdebugger-scView-event.png)
1. Suchen Sie nach Payload , wobei die **[!UICONTROL events]** contain `purchase`
   ![Product String-Validierung mit Assurance](assets/assurance-hitdebugger-purchase-event.png)
1. Bei der Validierung der `purchase` -Ereignis, beachten Sie, dass die `Product String` sollte enthalten `Product SKU`, `Product Quantity` , und `Product Total Price`.
1. Darüber hinaus gilt für die `purchase` überprüfen, ob die `purchase-id` und/oder `purchaseId` festgelegt sind


Herzlichen Glückwunsch! Du hast es getan! Dies ist das Ende der Lektion und jetzt können Sie Adobe Analytics mit dem Platform Web SDK für Ihre eigene Website implementieren.

[Weiter: ](setup-audience-manager.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
