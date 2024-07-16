---
title: WebViews mit Platform Mobile SDK verarbeiten
description: Erfahren Sie, wie Sie die Datenerfassung mit WebViews in einer mobilen App durchführen.
jira: KT-14632
exl-id: 9b3c96fa-a1b8-49d2-83fc-ece390b9231c
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

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

Wenn Sie Daten aus dem nativen Teil der App und aus einer WebView innerhalb der App senden, generiert jede einzelne eine eigene Experience Cloud-ID (ECID), was zu getrennten Treffern und zu überhöhten Besuchs-/Besucherdaten führt. Weitere Informationen zur ECID finden Sie in der [ECID-Übersicht](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=en).

Um diese unerwünschte Situation zu beheben, ist es wichtig, die ECID des Benutzers aus dem nativen Teil Ihrer App an eine WebView zu übergeben, die Sie möglicherweise in Ihrer App verwenden möchten.

Die in WebView verwendete AEP Edge Identity-Erweiterung erfasst die aktuelle ECID und fügt sie zur URL hinzu, anstatt eine Anfrage für eine neue ID an Adobe zu senden. Die Implementierung verwendet diese ECID dann, um die URL anzufordern.

## Implementierung

Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Info]** > **[!DNL TermsOfServiceSheet]** und suchen Sie die Funktion `func loadUrl()` in der Klasse `final class SwiftUIWebViewModel: ObservableObject`. Fügen Sie den folgenden Aufruf zur Verarbeitung der Webansicht hinzu:

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

Die [`AEPEdgeIdentity.Identity.getUrlVariables`](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) -API richtet die Variablen für die URL ein, um alle relevanten Informationen wie ECID und mehr zu enthalten. Im Beispiel verwenden Sie eine lokale Datei, die gleichen Konzepte gelten jedoch für Remote-Seiten.

Weitere Informationen zur `Identity.getUrlVariables`-API finden Sie im Referenzhandbuch zur API für die [Identität für Edge Network-Erweiterung](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) .

## Überprüfen

So führen Sie den Code aus:

1. Lesen Sie den Abschnitt [Setup instructions](assurance.md#connecting-to-a-session) , um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Navigieren Sie zu den **[!UICONTROL Einstellungen]** in der App.
1. Tippen Sie auf die Schaltfläche **[!DNL View...]** , um die **[!DNL Terms of Use]** anzuzeigen.

   <img src="./assets/tou1.png" width="300" /> <img src="./assets/tou2.png" width="300" />

1. Suchen Sie in der Assurance-Benutzeroberfläche vom Anbieter **[!UICONTROL com.adobe.griffon.mobile]** nach dem Ereignis **[!UICONTROL Edge Identity Response URL Variables]** .
1. Wählen Sie das Ereignis aus und überprüfen Sie das Feld **[!UICONTROL urlvariable]** im Objekt **[!UICONTROL ACPExtensionEventData]** , um sicherzustellen, dass die folgenden Parameter in der URL vorhanden sind: `adobe_mc`, `mcmid` und `mcorgid`.

   ![Validierung der Webansicht](assets/webview-validation.png)

   Unten finden Sie ein Beispiel für ein `urvariables` -Feld:

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
>Die Besucherzuordnung über diese URL-Parameter wird im Platform Web SDK (Versionen 2.11.0 oder höher) und bei Verwendung von `VisitorAPI.js` unterstützt.


>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass Inhalte basierend auf einer URL in einer Webansicht angezeigt werden, wobei dieselbe ECID verwendet wird wie die bereits vom Adobe Experience Platform Mobile SDK ausgegebene ECID.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu künftigen Inhalten teilen möchten, teilen Sie diese auf diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Identität](identity.md)**
