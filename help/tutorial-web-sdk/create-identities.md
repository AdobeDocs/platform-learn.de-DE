---
title: Erstellen von Identitäten für das Platform Web SDK
description: Erfahren Sie, wie Sie Identitäten in XDM erstellen und das Datenelement "Identity Map"zum Erfassen von Benutzer-IDs verwenden. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK, Tags, Identities
jira: KT-15402
exl-id: 7ca32dc8-dd86-48e0-8931-692bcbb2f446
source-git-commit: a8431137e0551d1135763138da3ca262cb4bc4ee
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 3%

---

# Erstellen von Identitäten

Erfahren Sie, wie Sie Identitäten mit Adobe Experience Platform Web SDK erfassen. Erfassen Sie sowohl nicht authentifizierte als auch authentifizierte Identitätsdaten auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html). Erfahren Sie, wie Sie die zuvor erstellten Datenelemente zum Erfassen authentifizierter Daten mit einem Platform Web SDK-Datenelementtyp namens Identity Map verwenden.

Diese Lektion konzentriert sich auf das Datenelement &quot;Identitätszuordnung&quot;, das mit der Adobe Experience Platform Web SDK-Tag-Erweiterung verfügbar ist. Sie ordnen Datenelemente mit einer authentifizierten Benutzer-ID und Authentifizierungsstatus XDM zu.

## Lernziele

Am Ende dieser Lektion können Sie:

* Grundlegendes zur Beziehung zwischen Experience Cloud ID (ECID) und Erstanbieter Device ID (FPID)
* den Unterschied zwischen nicht authentifizierten und authentifizierten IDs verstehen
* Erstellen eines Identitätszuordnungs-Datenelements

## Voraussetzungen

Sie wissen, was eine Datenschicht ist, kennen die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"}-Datenschicht und wissen, wie Datenelemente in Tags referenziert werden. Sie müssen die vorherigen Lektionen im Tutorial abgeschlossen haben:

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)
* [Erstellen von Datenelementen](create-data-elements.md)


## Experience Cloud ID

Die [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid) ist ein freigegebener Identitäts-Namespace, der in Adobe Experience Platform- und Adobe Experience Cloud-Anwendungen verwendet wird. ECID bildet die Grundlage für die Kundenidentität und ist die Standardidentität für digitale Eigenschaften. ECID ist die ideale ID zum Verfolgen von nicht authentifiziertem Benutzerverhalten, da es immer vorhanden ist.

<!-- FYI I commented this out because it was breaking the build - Jack
>[!TIP]
>
> When you use the Experience Platform Web SDK to set up Adobe applications on your digital properties, the ECID is generated at the Adobe Edge server level. As such, ECID is not viewable on the client-side network request payload. You can view the ECID by seeing the Preview tab of the network request, or by using the [Adobe Experience Platform Debugger Edge Trace](set-up-analytics.md#experience-cloud-id-validation).
>![View ECID](assets/validate-dev-console-ecid.png)
-->

Erfahren Sie mehr darüber, wie [ECIDs mit dem Platform Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/overview) verfolgt werden.

ECIDs werden anhand einer Kombination aus Erstanbieter-Cookies und Platform Edge Network festgelegt. Standardmäßig werden die Erstanbieter-Identitäts-Cookies vom Web SDK Client-seitig gesetzt. Um Browserbeschränkungen für Cookie-Lebenszyklen zu berücksichtigen, können Sie stattdessen Ihre eigenen Erstanbieter-Identitäts-Cookies serverseitig festlegen. Diese Identitäts-Cookies werden als Erstanbieter-Geräte-IDs (FPIDs) bezeichnet.

>[!IMPORTANT]
>
>Die Erweiterung [Experience Cloud ID-Dienst](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) ist bei der Implementierung des Adobe Experience Platform Web SDK nicht erforderlich, da die Funktionalität des ID-Diensts in das Platform Web SDK integriert ist.

## Erstanbieter-Geräte-ID (FPID)

FPIDs sind Erstanbieter-Cookies _, die Sie mithilfe Ihrer eigenen Webserver_ festlegen und die Adobe dann zur Erstellung der ECID verwendet, anstatt das vom Web SDK festgelegte Erstanbieter-Cookie zu verwenden. Auch wenn die Browserunterstützung variieren kann, sind Erstanbieter-Cookies meist haltbarer, wenn sie von einem Server gesetzt werden, der einen DNS-A-Datensatz (für IPv4) oder einen AAAA-Datensatz (für IPv6) nutzt, im Gegensatz zu einem DNS-CNAME oder JavaScript-Code.

Sobald ein FPID-Cookie gesetzt ist, kann der zugehörige Wert abgerufen und an Adobe gesendet werden, während Ereignisdaten erfasst werden. Erfasste FPIDs werden als Samen verwendet, um ECIDs in Platform Edge Network zu generieren, die weiterhin die Standardkennungen in Adobe Experience Cloud-Anwendungen sind.

Auch wenn FPIDs in diesem Tutorial nicht verwendet werden, sollten Sie FPIDs in Ihrer eigenen Web SDK-Implementierung verwenden. Weitere Informationen zu [Erstanbieter-Geräte-IDs im Platform Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/first-party-device-ids)

>[!CAUTION]
>
> FPID ist eine alternative Methode zur Generierung der ECID mithilfe eines von Ihren Webservern gesetzten Cookies. Sie wird nicht zur Identifizierung authentifizierter Benutzer verwendet.

## Authentifizierte ID

Wie oben erwähnt, wird allen Besuchern Ihrer digitalen Eigenschaften bei Verwendung des Platform Web SDK eine ECID von Adobe zugewiesen. ECID ist die Standardidentität zum Verfolgen nicht authentifizierter digitaler Verhaltensweisen.

Sie können auch eine authentifizierte Benutzer-ID senden, damit Platform [Identitätsdiagramme](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/identities/understanding-identity-and-identity-graphs) erstellen kann und Target seine [Drittanbieter-ID](https://experienceleague.adobe.com/en/docs/target/using/audiences/visitor-profiles/3rd-party-id) festlegen kann. Das Festlegen der authentifizierten ID erfolgt mithilfe des Datenelementtyps [!UICONTROL Identitätszuordnung] .

Erstellen des Datenelements [!UICONTROL Identity Map] :

1. Navigieren Sie zu **[!UICONTROL Datenelemente]** und wählen Sie **[!UICONTROL Datenelement hinzufügen]** aus.

1. **[!UICONTROL Name]** das Datenelement `identityMap.loginID`

1. Wählen Sie als **[!UICONTROL Erweiterung]** `Adobe Experience Platform Web SDK` aus.

1. Wählen Sie als **[!UICONTROL Datenelementtyp]** `Identity map` aus.

1. Dadurch wird ein Bildschirmbereich rechts neben der **[!UICONTROL Datenerfassungsoberfläche]** angezeigt, in dem Sie die Identität konfigurieren können:

   ![Datenerfassungsschnittstelle](assets/identity-identityMap-setup.png)

1. Wählen Sie als **[!UICONTROL Namespace]** den Namespace `lumaCrmId` aus, den Sie zuvor in der Lektion [Identitäten konfigurieren](configure-identities.md) erstellt haben. Wenn es nicht in der Dropdown-Liste angezeigt wird, geben Sie es in ein.

1. Nachdem der **[!UICONTROL Namespace]** ausgewählt wurde, muss eine ID festgelegt werden. Wählen Sie das zuvor in der Lektion [Datenelemente erstellen](create-data-elements.md#create-data-elements-to-capture-the-data-layer) erstellte Datenelement `user.profile.attributes.username` aus, das eine ID erfasst, wenn Benutzer bei der Site &quot;Luma&quot;angemeldet sind.

   <!--  >[!TIP]
    >
    >You can verify the **[!UICONTROL Luma CRM ID]** is collected in a data element on the web property by going to the [Luma Demo site](https://luma.enablementadobe.com/content/luma/us/en.html), logging in, [switching the tag environment](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tag-property) to your own, and typing `_satellite.getVar("user.profile.attributes.username")` in the web browser developer console.
    >
    >   ![Data Element  ID ](assets/identity-data-element-customer-id.png)
    -->

1. Wählen Sie als **[!UICONTROL Authentifizierungsstatus]** **[!UICONTROL Authentifiziert]** aus.
1. Wählen Sie **[!UICONTROL Primär]**

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Datenerfassungsschnittstelle](assets/identity-id-namespace.png)

>[!TIP]
>
> Adobe empfiehlt das Senden von Identitäten, die eine Person repräsentieren, z. B. `Luma CRM Id`, als die [!UICONTROL primäre] Identität.
>
> Wenn die Identitätszuordnung die Personenkennung enthält (z. B. `Luma CRM Id`), wird die Personenkennung zur [!UICONTROL primären] Identität. Andernfalls wird `ECID` zur Identität [!UICONTROL primary].




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

Am Ende dieser Schritte sollten die folgenden Datenelemente erstellt werden:

| Datenelemente der Haupterweiterung | Datenelemente der Platform Web SDK-Erweiterung |
-----------------------------|-------------------------------
| `cart.orderId` | `data.variable` |
| `cart.productInfo` | `identityMap.loginID` |
| `cart.productInfo.purchase` | `xdm.variable.content` |
| `page.pageInfo.hierarchie1` | |
| `page.pageInfo.pageName` | |
| `page.pageInfo.server` | |
| `product.category` | |
| `product.productInfo.sku` | |
| `product.productInfo.title` | |
| `user.profile.attributes.loggedIn` | |
| `user.profile.attributes.username` | |

Wenn diese Datenelemente vorhanden sind, können Sie mit dem Senden von Daten an Platform Edge Network beginnen, indem Sie eine Regel in Tags erstellen.

[Weiter: ](create-tag-rule.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
