---
title: Erstellen von Datenelementen
description: Erfahren Sie, wie Sie ein XDM-Objekt erstellen und ihm Datenelemente in Tags zuordnen. Diese Lektion ist Teil des Tutorials Adobe Experience Cloud mit Web SDK implementieren .
feature: Tags
exl-id: d662ec46-de9b-44ba-974a-f81dfc842e68
source-git-commit: 28333d3079f586996cd6b6933831ffd9f3caacd1
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 6%

---

# Erstellen von Datenelementen

Erfahren Sie, wie Sie die wichtigsten Datenelemente erstellen, die zum Erfassen von Daten mit dem Experience Platform Web SDK erforderlich sind. Erfassen Sie sowohl Inhalts- als auch Identitätsdaten auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html). Erfahren Sie, wie Sie das zuvor erstellte XDM-Schema zur Datenerfassung mit dem Platform Web SDK mithilfe eines neuen Datenelementtyps namens XDM Object verwenden.

>[!NOTE]
>
> Zu Demonstrationszwecken bauen die Übungen in dieser Lektion auf dem Beispiel auf, das während der [Schema konfigurieren](configure-schemas.md) Schritt; Erstellen von Beispiel-XDM-Objekten, die angesehene Inhalte und Identitäten von Benutzern auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html).

>[!IMPORTANT]
>
>Die Daten für diese Lektion stammen aus dem `[!UICONTROL digitalData]` Datenschicht auf der Site &quot;Luma&quot;. Um die Datenschicht anzuzeigen, öffnen Sie Ihre Entwicklerkonsole und geben Sie in `[!UICONTROL digitalData]` um die vollständige verfügbare Datenschicht anzuzeigen.![digitalData-Datenschicht](assets/data-element-data-layer.png)


Unabhängig vom Platform Web SDK müssen Sie weiterhin Datenelemente in Ihrer Tag-Eigenschaft erstellen, die Datenerfassungsvariablen Ihrer Website wie einer Datenschicht, einem HTML-Attribut oder anderen zugeordnet sind. Nachdem Sie diese Datenelemente erstellt haben, müssen Sie sie dem XDM-Schema zuordnen, das Sie während der [Schemas konfigurieren](configure-schemas.md) Lektion. Zu diesem Zweck stellt die Platform Web SDK-Erweiterung einen neuen Datenelementtyp namens XDM-Objekt bereit. Daher besteht das Erstellen von Datenelementen aus zwei Aktionen:

1. Zuordnen von Website-Variablen zu Datenelementen und
1. Zuordnen dieser Datenelemente zu einem XDM-Objekt

Bei Schritt 1 ordnen Sie Ihre Datenschicht Datenelementen weiterhin auf die aktuelle Weise zu, indem Sie einen der Datenelementtypen der Core-Tag-Erweiterung verwenden. Für Schritt 2 erstellt die Platform Web SDK-Erweiterung eine Reihe neuer Datenelementtypen, die zuvor nicht verfügbar waren:

* Ereigniszusammenführungs-ID
* Identitätszuordnung
* XDM-Objekt

Diese Lektion konzentriert sich auf Datenelementtypen von XDM-Objekten und Identitätszuordnungen. Sie erstellen XDM-Objekte, um die Aktivität und den Authentifizierungsstatus von Luma-Besuchern zu erfassen.

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen von Datenelementen zum Erfassen von Inhalten und ID-Daten für die Benutzeranmeldung
* Erstellen eines Identitätszuordnungs-Datenelements
* Zuordnen von Datenelementen zu einem XDM-Objektdatenelement


## Voraussetzungen

Sie wissen, was eine Datenschicht ist, und kennen die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} und wissen, wie Datenelemente in Tags referenziert werden. Sie müssen die folgenden vorherigen Schritte im Tutorial ausgeführt haben

* [Berechtigungen konfigurieren](configure-permissions.md)
* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)

>[!IMPORTANT]
>
>Die [Experience Cloud ID-Diensterweiterung](https://exchange.adobe.com/experiencecloud.details.100160.adobe-experience-cloud-id-launch-extension.html) ist bei der Implementierung des Adobe Experience Platform Web SDK nicht erforderlich, da die ID-Dienst-Funktion in das Platform Web SDK integriert ist.

## Erstellen von Datenelementen zum Erfassen der Datenschicht

Bevor Sie mit der Erstellung des XDM-Objekts beginnen, erstellen Sie den folgenden Satz von Datenelementen, die dem [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} Datenschicht:

1. Navigieren Sie zu **[!UICONTROL Datenelemente]** und wählen Sie **[!UICONTROL Datenelement hinzufügen]** (oder **[!UICONTROL Neues Datenelement erstellen]** wenn in der Tag-Eigenschaft keine Datenelemente vorhanden sind)

   ![Datenelement erstellen](assets/data-element-create.jpg)

1. Benennen Sie das Datenelement `page.pageInfo.pageName`.
1. Verwenden Sie die **[!UICONTROL JavaScript-Variable]** **[!UICONTROL Datenelementtyp]** , um auf einen Wert in der Datenschicht von Luma zu verweisen: `digitalData.page.pageInfo.pageName`

1. Markieren Sie die Kästchen für **[!UICONTROL Wert in Kleinbuchstaben erzwingen]** und **[!UICONTROL Text bereinigen]**, um die Groß-/Kleinschreibung zu standardisieren und unnötige Leerzeichen zu entfernen

1. Urlaub `None` als **[!UICONTROL Speicherdauer]** Einstellung, da dieser Wert auf jeder Seite unterschiedlich ist

1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Datenelement &quot;Seitenname&quot;](assets/data-element-pageName.jpg)

Führen Sie dieselben Schritte aus, um diese vier zusätzlichen Datenelemente zu erstellen:

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

## Identitätszuordnungs-Datenelement erstellen

Als Nächstes können Sie das Datenelement &quot;Identity Map&quot;erstellen:

1. Navigieren Sie zu **[!UICONTROL Datenelemente]** und wählen Sie **[!UICONTROL Datenelement hinzufügen]**

1. **[!UICONTROL Name]** das Datenelement `identityMap.loginID`

1. Als **[!UICONTROL Erweiterung]** auswählen `Adobe Experience Platform Web SDK`

1. Als **[!UICONTROL Datenelementtyp]** auswählen `Identity map`

1. Dadurch wird ein Bildschirmbereich rechts neben dem **[!UICONTROL Datenerfassungsoberfläche]** für die Konfiguration der Identität:

   ![Datenerfassungsoberfläche](assets/identity-identityMap-setup.png)

1. Als  **[!UICONTROL Namespace]**, wählen Sie die `Luma CRM Id` Namespace, den Sie zuvor in der [Identitäten konfigurieren](configure-identities.md) Lektion.

   >[!NOTE]
   >
   >    Wenn Sie Ihre `Luma CRM Id` -Namespace verwenden, überprüfen Sie, ob Sie ihn auch in Ihrer standardmäßigen Produktions-Sandbox erstellt haben. Derzeit werden im Dropdown-Menü Namespace nur Namespaces angezeigt, die in der standardmäßigen Produktions-Sandbox erstellt wurden.

1. Nach dem **[!UICONTROL Namespace]** ausgewählt ist, muss eine ID festgelegt werden. Wählen Sie die `user.profile.attributes.username` -Datenelement, das zuvor in dieser Lektion erstellt wurde und eine ID erfasst, wenn Benutzer bei der Site &quot;Luma&quot;angemeldet sind.

<!--  >[!TIP]
   >
   >You can verify the **[!UICONTROL Luma CRM ID]** is collected in a data element on the web property by going to the [Luma Demo site](https://luma.enablementadobe.com/content/luma/us/en.html), logging in, [switching the tag environment](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tag-property) to your own, and typing `_satellite.getVar("user.profile.attributes.username")` in the web browser developer console.
   >
   >   ![Data Element  ID ](assets/identity-data-element-customer-id.png)
-->

1. Als **[!UICONTROL Authentifizierter Status]** auswählen **[!UICONTROL Authentifiziert]**
1. Auswählen **[!UICONTROL Primär]**

1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Datenerfassungsoberfläche](assets/identity-id-namespace.png)

>[!TIP]
>
> Adobe empfiehlt, Identitäten zu senden, die eine Person repräsentieren, z. B. `Luma CRM Id`als [!UICONTROL primary] Identität.




<!--
1. Once the data element is configured in **[!UICONTROL Data Collection interface]**, it can be tested on the Luma web property like any other Data Element. Enter the following script in the browser developer console
   
   
   ```
   _satellite.getVar('identityMap.loginID')
   ```  

   ![Data Collection interface](assets/identity-consoleIdentityDataElement.png)
   
   >[!NOTE]
   >
   >ECID identifier will NOT populate in the Data Element, as this is configured already with Platform Web SDK.   
-->

## Zuordnen von Datenelementen zu XDM-Objekten

Alle von Ihnen erstellten Datenelemente müssen einem XDM-Objekt zugeordnet sein. Dieses Objekt sollte mit dem XDM-Schema übereinstimmen, das Sie während der [Schema konfigurieren](configure-schemas.md) Lektion.

Es gibt verschiedene Möglichkeiten, Datenelemente XDM-Objektfeldern zuzuordnen. Sie können einzelne Datenelemente einzelnen XDM-Feldern zuordnen oder Datenelemente ganzen XDM-Objekten zuordnen, sofern Ihr Datenelement mit dem exakten Schlüssel-Wert-Paar-Schema im XDM-Objekt übereinstimmt. In dieser Lektion erfassen Sie Inhaltsdaten, indem Sie sie einzelnen Feldern zuordnen. Sie werden lernen, [Zuordnen eines Datenelements zu einem ganzen XDM-Objekt](setup-analytics.md#Map-an-entire-array-to-an-XDM-Object) im [Einrichten von Analytics](setup-analytics.md) Lektion.

Erstellen Sie ein XDM-Objekt zum Erfassen von Inhaltsdaten:

1. Wählen Sie im linken Navigationsbereich die Option **[!UICONTROL Datenelemente]**
1. Wählen Sie **[!UICONTROL Datenelement hinzufügen]** aus
1. **** Benennen Sie das Datenelement . **`xdm.content`**
1. Als **[!UICONTROL Erweiterung]** select `Adobe Experience Platform Web SDK`
1. Als **[!UICONTROL Datenelementtyp]** select `XDM object`
1. Plattform auswählen **[!UICONTROL Sandbox]** in dem Sie das XDM-Schema während der [Konfigurieren eines XDM-Schemas](configure-schemas.md) Lektion in diesem Beispiel `DEVELOPMENT Mobile and Web SDK Courses`
1. Als **[!UICONTROL Schema]**, wählen Sie `Luma Web Event Data` schema:

   ![XDM-Objekt](assets/data-element-xdm.content-fields.png)

   >[!NOTE]
   >
   >Die Sandbox entspricht der Experience Platformen-Sandbox, in der Sie das Schema erstellt haben. In Ihrer Experience Platform-Instanz können mehrere Sandboxes verfügbar sein. Stellen Sie daher sicher, dass Sie die richtige Sandbox auswählen. Arbeiten Sie immer zuerst in der Entwicklung, dann in der Produktion.

1. Scrollen Sie nach unten, bis Sie zum **`web`** Objekt
1. Auswahl zum Öffnen

   ![Webobjekt](assets/data-element-pageviews-xdm-object.png)


1. Ordnen Sie die folgenden Web-XDM-Variablen Datenelementen zu

   * **`web.webPageDetials.name`** in `%page.pageInfo.pageName%`
   * **`web.webPageDetials.server`** in `%page.pageInfo.server%`
   * **`web.webPageDetials.siteSection`** in `%page.pageInfo.hierarchie1%`

   ![XDM-Objekt](assets/data-element-xdm.content.png)

1. Suchen Sie als Nächstes die `identityMap` -Objekt im Schema und wählen Sie es aus

1. Zuordnung zu `identityMap.loginID` Datenelement

1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Datenerfassungsoberfläche](assets/identity-dataElements-xdmContent-LumaSchema-identityMapSelect3.png)




Am Ende dieser Schritte sollten die folgenden Datenelemente erstellt werden:

| Datenelemente der CORE-Erweiterung | Platform Web SDK-Datenelemente |
-----------------------------|-------------------------------
| `cart.orderId` | `identityMap.loginID` |
| `page.pageInfo.hierarchie1` | `xdm.content` |
| `page.pageInfo.pageName` | |
| `page.pageInfo.server` | |
| `user.profile.attributes.loggedIn` | |
| `user.profile.attributes.username` | |

Wenn diese Datenelemente vorhanden sind, können Sie mit dem Senden von Daten an Platform Edge Network über das XDM-Objekt beginnen, indem Sie eine Regel in Tags erstellen.

[Weiter: ](create-tag-rule.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
