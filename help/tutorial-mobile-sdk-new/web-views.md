---
title: WebViews verarbeiten
description: Erfahren Sie, wie Sie die Datenerfassung mit WebViews in einer mobilen App durchführen.
jira: KT-6987
hide: true
exl-id: 0c8818f7-39d3-496e-a835-2d85d50e50d6
source-git-commit: 4a12f8261cf1fb071bc70b6a04c34f6c16bcce64
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 1%

---

# WebViews verarbeiten

Erfahren Sie, wie Sie die Datenerfassung mit WebViews in einer mobilen App durchführen.

## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.

## Lernziele

In dieser Lektion werden Sie:

* Erfahren Sie, warum Sie WebViews in Ihrer App besonders berücksichtigen müssen.
* Machen Sie sich mit dem Code vertraut, der zur Vermeidung von Tracking-Problemen erforderlich ist.

## Potenzielle Tracking-Probleme

Wenn Sie Daten aus dem nativen Teil der App und aus einer WebView innerhalb der App senden, generiert jede einzelne eine eigene Experience Cloud-ID (ECID), was zu getrennten Treffern und zu überhöhten Besuchs-/Besucherdaten führt. Weitere Informationen über die ECID finden Sie im [ECID-Übersicht](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=en).

Um diese unerwünschte Situation zu beheben, ist es wichtig, die ECID des Benutzers aus dem nativen Teil Ihrer App an eine WebView zu übergeben, die Sie möglicherweise in Ihrer App verwenden möchten.

Die in WebView verwendete AEP Edge Identity-Erweiterung erfasst die aktuelle ECID und fügt sie zur URL hinzu, anstatt eine Anfrage für eine neue ID an Adobe zu senden. Die Implementierung verwendet diese ECID dann, um die URL anzufordern.

## Implementierung

Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Info]** > **[!DNL TermsOfServiceSheet]** und suchen Sie nach `func loadUrl()` -Funktion in `final class SwiftUIWebViewModel: ObservableObject` -Klasse. Fügen Sie den folgenden Aufruf zur Verarbeitung der Webansicht hinzu:

```swift
// Handle web view
AEPEdgeIdentity.Identity.getUrlVariables {(urlVariables, error) in
    if let error = error {
        print("Error with Webview", error)
        return;
    }
    
    if let urlVariables: String = urlVariables {
        urlString.append("?" + urlVariables)
        guard let url = URL(string: urlString) else {
            return
        }
        DispatchQueue.main.async {
            self.webView.load(URLRequest(url: url))
        }
    }
    Logger.aepMobileSDK.info("Successfully retrieved urlVariables for WebView, final URL: \(urlString)")
}
```

Die [`AEPEdgeIdentity.Identity.getUrlVariables`](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) Die API richtet die Variablen für die URL so ein, dass sie alle relevanten Informationen wie ECID und mehr enthalten. Im Beispiel verwenden Sie eine lokale Datei, die gleichen Konzepte gelten jedoch für Remote-Seiten.

Weitere Informationen zum `Identity.getUrlVariables` API im [Referenzhandbuch zur Identity für die Edge Network Extension-API](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables).

## Überprüfen

So führen Sie den Code aus:

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) -Abschnitt, um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Navigieren Sie zu **[!UICONTROL Einstellungen]** in der App
1. Tippen Sie auf **[!DNL View...]** -Schaltfläche zum Anzeigen **[!DNL Terms of Use]**.

   <img src="./assets/tou1.png" width="300" /> <img src="./assets/tou2.png" width="300" />

1. Suchen Sie in der Assurance-Benutzeroberfläche nach der **[!UICONTROL URL-Variablen für Edge-Identitätsantwort]** -Ereignis aus **[!UICONTROL com.adobe.griffon.mobile]** -Anbieter.
1. Wählen Sie das Ereignis aus und überprüfen Sie die **[!UICONTROL urlvariable]** im Feld **[!UICONTROL ACPExtensionEventData]** -Objekt, das bestätigt, dass die folgenden Parameter in der URL vorhanden sind: `adobe_mc`, `mcmid`, und `mcorgid`.

   ![Webseitenvalidierung](assets/webview-validation.png)

   Beispiel `urvariables` -Feld sehen Sie unten:

   * Original (mit Escapezeichen)

     ```html
     adobe_mc=TS%3D1636526122%7CMCMID%3D79076670946787530005526183384271520749%7CMCORGID%3D7ABB3E6A5A7491460A495D61%40AdobeOrg
     ```

   * Beautified

     ```html
     adobe_mc=TS=1636526122|MCMID=79076670946787530005526183384271520749|MCORGID=7ABB3E6A5A7491460A495D61@AdobeOrg
     ```

Leider ist das Debugging der Websitzung eingeschränkt. Beispielsweise können Sie den Adobe Experience Platform Debugger in Ihrem Browser nicht verwenden, um mit dem Debugging der Webansichtssitzung fortzufahren.

>[!NOTE]
>
>Die Besucherzuordnung über diese URL-Parameter wird im Platform Web SDK (Versionen 2.11.0 oder höher) und bei der Verwendung von unterstützt `VisitorAPI.js`.


>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass Inhalte basierend auf einer URL in einer Webansicht angezeigt werden, wobei dieselbe ECID verwendet wird wie die bereits vom Adobe Experience Platform Mobile SDK ausgegebene ECID.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Identität](identity.md)**
