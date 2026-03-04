---
title: Erfassen von Identitäten für Platform Web SDK
description: Erfahren Sie, wie Sie Identitäten in XDM erfassen und das Datenelement „Identity Map“ verwenden können, um Benutzer-IDs zu erfassen. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK, Tags, Identities
jira: KT-15402
exl-id: 7ca32dc8-dd86-48e0-8931-692bcbb2f446
source-git-commit: d15ce3b51424dba51b5b621b6d92eff85edd5b27
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 3%

---

# Erfassen von Identitäten

Erfahren Sie, wie Sie Identitäten mit Adobe Experience Platform Web SDK erfassen. Erfassen Sie sowohl nicht authentifizierte als auch authentifizierte Identitätsdaten auf der [Demo-Site von Luma](https://luma.enablementadobe.com). Erfahren Sie, wie Sie die zuvor erstellten Datenelemente zum Erfassen authentifizierter Daten mit einem Platform Web SDK-Datenelementtyp namens Identitätszuordnung verwenden.

Diese Lektion konzentriert sich auf das Identitätszuordnungs-Datenelement, das mit der Adobe Experience Platform Web SDK-Tag-Erweiterung verfügbar ist. Sie ordnen Datenelemente, die eine authentifizierte Benutzer-ID und einen Authentifizierungsstatus enthalten, XDM zu.



## Lernziele

Am Ende dieser Lektion können Sie:

* Verstehen der Beziehung zwischen Experience Cloud ID (ECID) und First-Party-Geräte-ID (FPID)
* Verstehen Sie den Unterschied zwischen nicht authentifizierten und authentifizierten IDs
* Erstellen eines Identitätszuordnungs-Datenelements

## Voraussetzungen

Sie haben ein Verständnis davon, was eine Datenschicht ist, kennen die [Luma-Demo-Site](https://luma.enablementadobe.com){target="_blank"} Datenschicht und wissen, wie Sie in Tags auf Datenelemente verweisen. Sie müssen die vorherigen Lektionen im Tutorial abgeschlossen haben:

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Konfigurieren eines Identity-Namespace](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)
* [Datenelemente erstellen](create-data-elements.md)


## Experience Cloud ID

Die [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid) ist ein freigegebener Identity-Namespace, der in Adobe Experience Platform- und Adobe Experience Cloud-Anwendungen verwendet wird. ECID bildet die Grundlage für die Kundenidentität und ist die Standardidentität für digitale Eigenschaften. ECID ist die ideale Kennung zum Tracking nicht authentifizierten Benutzerverhaltens, da es immer vorhanden ist.

<!-- FYI I commented this out because it was breaking the build - Jack
>[!TIP]
>
> When you use the Experience Platform Web SDK to set up Adobe applications on your digital properties, the ECID is generated at the Adobe Edge server level. As such, ECID is not viewable on the client-side network request payload. You can view the ECID by seeing the Preview tab of the network request, or by using the [Adobe Experience Platform Debugger Edge Trace](set-up-analytics.md#experience-cloud-id-validation).
>![View ECID](assets/validate-dev-console-ecid.png)
-->

Erfahren Sie mehr darüber, wie [ECIDs mit Platform Web SDK verfolgt werden](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/overview).

ECIDs werden mithilfe einer Kombination aus Erstanbieter-Cookies und Platform Edge Network festgelegt. Standardmäßig werden die Erstanbieter-Identitäts-Cookies Client-seitig von der Web-SDK gesetzt. Um Browser-Einschränkungen hinsichtlich der Cookie-Lebensdauer zu berücksichtigen, können Sie stattdessen eigene Erstanbieter-Identitäts-Cookies Server-seitig setzen. Diese Identitäts-Cookies werden als First-Party-Geräte-IDs (FPIDs) bezeichnet.

>[!IMPORTANT]
>
>Die [Experience Cloud ID Service-Erweiterung](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) wird bei der Implementierung von Adobe Experience Platform Web SDK nicht benötigt, da die ID-Service-Funktionalität in Platform Web SDK integriert ist.

## First-Party-Geräte-ID (FPID)

FPIDs sind Erstanbieter-Cookies _Sie setzen sie mithilfe Ihrer eigenen Webserver_ die Adobe dann verwendet, um die ECID zu erstellen, anstatt das Erstanbieter-Cookie zu verwenden, das von der Web-SDK gesetzt wird. Während die Browser-Unterstützung variieren kann, sind Erstanbieter-Cookies tendenziell haltbarer, wenn sie von einem Server festgelegt werden, der einen DNS-A-Eintrag (für IPv4) oder einen AAAA-Eintrag (für IPv6) nutzt, im Gegensatz dazu, wenn sie durch einen DNS-CNAME- oder JavaScript-Code festgelegt werden.

Sobald ein FPID-Cookie gesetzt wurde, kann sein Wert abgerufen und bei der Erfassung von Ereignisdaten an Adobe gesendet werden. Die erfassten FPIDs werden als Seeds verwendet, um ECIDs auf Platform Edge Network zu generieren, die weiterhin die Standardkennungen in Adobe Experience Cloud-Programmen sind.

Obwohl FPIDs in diesem Tutorial nicht verwendet werden, wird empfohlen, FPIDs in Ihrer eigenen Web SDK-Implementierung zu verwenden. Weitere Informationen zu [Erstanbieter-Geräte-IDs“ finden Sie in der Platform Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/first-party-device-ids)

>[!CAUTION]
>
> FPID ist eine alternative Möglichkeit, die ECID mithilfe eines von Ihren Webservern gesetzten Cookies zu generieren. Er wird nicht zur Identifizierung authentifizierter Benutzer verwendet.

## Authentifizierte ID

Wie bereits erwähnt, wird allen Besuchern Ihrer digitalen Objekte bei der Verwendung von Platform Web SDK von Adobe eine ECID zugewiesen. ECID ist die Standardidentität zum Tracking von nicht authentifiziertem digitalem Verhalten.

Sie können auch eine authentifizierte Benutzer-ID senden, damit Platform [Identitätsdiagramme) erstellen ](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/identities/understanding-identity-and-identity-graphs) Target seine [Drittanbieter-ID](https://experienceleague.adobe.com/en/docs/target/using/audiences/visitor-profiles/3rd-party-id) festlegen kann. Das Festlegen der authentifizierten ID erfolgt mithilfe des Datenelementtyps [!UICONTROL Identitätszuordnung].

So erstellen Sie [!UICONTROL  Datenelement ]Identitätszuordnung“:

1. Wechseln Sie zu **[!UICONTROL Datenelemente]** und wählen Sie **[!UICONTROL Datenelement hinzufügen]**

1. **[!UICONTROL Name]** das Datenelement `Identity Map`

1. Wählen Sie als **[!UICONTROL Erweiterung]** die Option `Adobe Experience Platform Web SDK`

1. Wählen Sie als **[!UICONTROL Datenelementtyp]** die Option `Identity map`

1. Wählen **[!UICONTROL als]** den `lumaCrmId` Namespace aus, der in der Lektion [Konfigurieren von Identitäten](configure-identities.md) erstellt wurde. Wenn er nicht im Dropdown-Menü angezeigt wird, geben Sie ihn ein.

1. Wählen Sie als **[!UICONTROL ID]** das `User Id` Datenelement aus, das in der Lektion [Datenelemente erstellen](create-data-elements.md#create-data-elements-to-capture-the-data-layer) erstellt wurde.

1. Wählen Sie als **[!UICONTROL Authentifizierungsstatus]** die Option **[!UICONTROL Authentifiziert]**
1. **[!UICONTROL Primär]**

1. Wählen Sie **[!UICONTROL Speichern]**

   ![Datenerfassungsschnittstelle](assets/identity-id-namespace.png)

>[!IMPORTANT]
>
> Adobe empfiehlt, Identitäten, die eine Person darstellen, wie `Luma CRM Id`, als [!UICONTROL primäre] Identität zu senden.
>
> Wenn die Identitätszuordnung die Personenkennung enthält (z. B. `Luma CRM Id`), wird die Personenkennung zur [!UICONTROL primären] Identität. Andernfalls wird `ECID` zur [!UICONTROL primären] Identität.
>
> Darüber hinaus empfiehlt Adobe für Kundinnen und Kunden von Platform-Anwendungen die Implementierung [Regeln zur Identitätsdiagramm-Verknüpfung](https://experienceleague.adobe.com/de/docs/platform-learn/tutorials/identities/graph-linking-rules/overview), um das Ausblenden von Diagrammen zu verhindern.

>[!NOTE]
>
> Sie müssen keine Maßnahmen ergreifen, um die ECID in einer Web SDK-Implementierung zu erfassen. Er wird automatisch erfasst.


Am Ende dieser Schritte sollten die folgenden Datenelemente erstellt sein:

| Datenelemente der Haupterweiterung | Datenelemente der Platform Web SDK-Erweiterung |
-----------------------------|-------------------------------
| `Ecommerce Cart Products` | `Data Variable` |
| `Ecommerce Product Category` | `Identity Map` |
| `Ecommerce Product Id` | `XDM Variable` |
| `Ecommerce Product Name` | |
| `Ecommerce Purchase Id` | |
| `Ecommerce Purchase Products` |  |
| `Page Name` | |
| `User Id` | |
| `User Logged In` | |

Wenn diese Datenelemente eingerichtet sind, können Sie beginnen, Daten an Platform Edge Network zu senden, indem Sie eine Regel in Tags erstellen.

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
