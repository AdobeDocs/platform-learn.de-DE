---
title: Verarbeiten von WebViews mit Platform Mobile SDK
description: Erfahren Sie, wie Sie die Datenerfassung mit WebViews in einer Mobile App handhaben.
jira: KT-14632
exl-id: 9b3c96fa-a1b8-49d2-83fc-ece390b9231c
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# Verarbeiten von WebViews

Erfahren Sie, wie Sie die Datenerfassung mit WebViews in einer Mobile App handhaben.

## Voraussetzungen

* App mit installierten und konfigurierten SDKs erfolgreich erstellt und ausgeführt.

## Lernziele

In dieser Lektion erfahren Sie Folgendes:

* Erfahren Sie, warum Sie WebViews in Ihrer App besonders berücksichtigen müssen.
* Den Code verstehen, der zum Verhindern von Tracking-Problemen erforderlich ist.

## Mögliche Tracking-Probleme

Wenn Sie Daten aus dem nativen Teil der App und von einer WebView innerhalb der App senden, generiert jede ihre eigene Experience Cloud-ID (ECID), was zu getrennten Treffern und überhöhten Besuchs-/Besucherdaten führt. Weitere Informationen zur ECID finden Sie in der [ECID-Übersicht](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=de).

Um diese unerwünschte Situation zu beheben, ist es wichtig, die ECID des Benutzers aus dem nativen Teil Ihrer App an eine WebView zu übergeben, die Sie möglicherweise in Ihrer App verwenden möchten.

Die in der WebView verwendete AEP Edge Identity-Erweiterung erfasst die aktuelle ECID und fügt sie zur URL hinzu, anstatt eine Anfrage für eine neue ID an Adobe zu senden. Die Implementierung verwendet dann diese ECID, um die URL anzufordern.

## Implementierung

Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Info]** > **[!DNL TermsOfServiceSheet]** und suchen Sie die `func loadUrl()` in der `final class SwiftUIWebViewModel: ObservableObject`. Fügen Sie den folgenden Aufruf hinzu, um die Web-Ansicht zu verarbeiten:

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

Die [`AEPEdgeIdentity.Identity.getUrlVariables`](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables)-API richtet die Variablen für die URL so ein, dass sie alle relevanten Informationen wie ECID und mehr enthalten. Im Beispiel verwenden Sie eine lokale Datei, aber für Remote-Seiten gelten dieselben Konzepte.

Weitere Informationen zur `Identity.getUrlVariables`-API finden Sie im [API-Referenzhandbuch für Erweiterungen von Identity for Edge Network ](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables).

## Überprüfen

So führen Sie den Code aus:

1. Lesen Sie den Abschnitt [Setup-Anweisungen](assurance.md#connecting-to-a-session), um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Navigieren Sie zu **[!UICONTROL Einstellungen]** in der App.
1. Tippen Sie auf die Schaltfläche **[!DNL View...]** , um die **[!DNL Terms of Use]** anzuzeigen.

   <img src="./assets/tou1.png" width="300" /> <img src="./assets/tou2.png" width="300" />

1. Suchen Sie in der Assurance-Benutzeroberfläche nach dem Ereignis **[!UICONTROL Edge Identity Response URL Variables]** vom Anbieter **[!UICONTROL com.adobe.griffon.mobile]**.
1. Wählen Sie das Ereignis aus und überprüfen Sie das **[!UICONTROL urlVariable]** im **[!UICONTROL ACPExtensionEventData]**-Objekt, um zu bestätigen, dass die folgenden Parameter in der URL vorhanden sind: `adobe_mc`, `mcmid` und `mcorgid`.

   ![WebView-Validierung](assets/webview-validation.png)

   Nachfolgend finden Sie ein Beispiel für ein `urvariables`:

   * Original (mit Escape-Zeichen)

     ```html
     adobe_mc=TS%3D1636526122%7CMCMID%3D79076670946787530005526183384271520749%7CMCORGID%3D7ABB3E6A5A7491460A495D61%40AdobeOrg
     ```

   * geschmückt

     ```html
     adobe_mc=TS=1636526122|MCMID=79076670946787530005526183384271520749|MCORGID=7ABB3E6A5A7491460A495D61@AdobeOrg
     ```

Leider ist das Debugging der Websitzung eingeschränkt. Beispielsweise können Sie den Adobe Experience Platform Debugger in Ihrem Browser nicht verwenden, um mit dem Debugging der Webansichtssitzung fortzufahren.

>[!NOTE]
>
>Die Zuordnung von Besuchern über diese URL-Parameter wird in Platform Web SDK (Version 2.11.0 oder höher) und bei Verwendung von `VisitorAPI.js` unterstützt.


>[!SUCCESS]
>
>Sie haben jetzt Ihre App so eingerichtet, dass Inhalte basierend auf einer URL in einer Webansicht mit derselben ECID angezeigt werden, die bereits von Adobe Experience Platform Mobile SDK ausgegeben wurde.
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796?profile.language=de)

Weiter: **[Identität](identity.md)**
