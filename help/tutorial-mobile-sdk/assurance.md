---
title: Einrichten der Sicherheit
description: Erfahren Sie, wie Sie die Assurance-Erweiterung in eine mobile App implementieren.
exl-id: e15774b2-2f52-400f-9313-bb4338a88918
source-git-commit: 7df759ec0ea248ee91ae673e3468ffa3f6cc5be5
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 3%

---

# Assurance

Erfahren Sie, wie Sie Adobe Experience Platform Assurance in einer Mobile App einrichten.

Assurance, formell als Project Griffon bekannt, soll Ihnen dabei helfen, zu untersuchen, zu testen, zu simulieren und zu überprüfen, wie Sie Daten erfassen oder Erlebnisse in Ihrer mobilen App bereitstellen.

Mithilfe von &quot;Assurance&quot;können Sie unformatierte SDK-Ereignisse überprüfen, die vom Adobe Experience Platform Mobile SDK generiert wurden. Alle vom SDK erfassten Ereignisse stehen zur Überprüfung zur Verfügung. SDK-Ereignisse werden in einer Listenansicht geladen, sortiert nach Zeit. Jedes Ereignis verfügt über eine detaillierte Ansicht, die weitere Details enthält. Zusätzliche Ansichten zum Durchsuchen von SDK-Konfigurationen, Datenelementen, freigegebenen Status und SDK-Erweiterungsversionen werden ebenfalls bereitgestellt. Weitere Informationen zum [Sicherheit](https://aep-sdks.gitbook.io/docs/foundation-extensions/adobe-experience-platform-assurance) in der Produktdokumentation.


## Voraussetzungen

* Die Beispielanwendung wurde erfolgreich erstellt und mit installierten und konfigurierten SDKs ausgeführt.

## Lernziele

In dieser Lektion werden Sie:

* Vergewissern Sie sich, dass Ihr Unternehmen Zugriff hat (und fordern Sie ihn an, falls nicht möglich).
* Richten Sie Ihre Basis-URL ein.
* Fügen Sie erforderlichen iOS-spezifischen Code hinzu.
* Stellen Sie eine Verbindung zu einer Sitzung her.

## Zugriff bestätigen

Vergewissern Sie sich, dass Ihr Unternehmen Zugriff auf die Zertifizierung hat, indem Sie die folgenden Schritte ausführen:

1. Besuch [https://experience.adobe.com/#/assurance](https://experience.adobe.com/griffon){target="_blank"}
1. Melden Sie sich mit Ihren Adobe ID-Anmeldedaten für das Experience Cloud an.
1. Wenn Sie zur **[!UICONTROL Sitzungen]** angezeigt, haben Sie Zugriff. Wenn Sie zur Beta-Zugriffsseite gelangen, wählen Sie **[!UICONTROL registrieren]**.

## Implementierung

Neben der allgemeinen [SDK-Installation](install-sdks.md) Wenn Sie in der vorherigen Lektion abgeschlossen haben, erfordert iOS auch die folgende Ergänzung. Fügen Sie der Datei `AppDelegate.swift` den folgenden Code hinzu:

```swift
func application(_ app: UIApplication, open url: URL, options: [UIApplication.OpenURLOptionsKey: Any] = [:]) -> Bool {
    Assurance.startSession(url: url)
    return true
}
```

Das für dieses Tutorial bereitgestellte Beispiel-Luma verwendet iOS 12.0. Verwenden Sie die Variable `UISceneDelegate's scene(_:openURLContexts:)` wie folgt:

```swift
func scene(_ scene: UIScene, openURLContexts URLContexts: Set<UIOpenURLContext>) {
    // Called when the app in background is opened with a deep link.
    if let deepLinkURL = URLContexts.first?.url {
        Assurance.startSession(url: deepLinkURL)
    }
}
```

Weitere Informationen finden Sie [hier](https://aep-sdks.gitbook.io/docs/foundation-extensions/adobe-experience-platform-assurance#implement-aep-assurance-session-start-apis-ios-only){target="_blank"}.

## Einrichten einer Basis-URL

1. Öffnen Sie XCode und wählen Sie den Projektnamen aus.
1. Navigieren Sie zum **Info** Registerkarte.
1. Scrollen Sie nach unten zu **URL-Typen** und wählen Sie die **+** -Schaltfläche, um eine neue hinzuzufügen.
1. Satz **Kennung** und **URL-Schemata** auf &quot;lumadeeplink&quot;.
1. Erstellen Sie die App und führen Sie sie aus.

![Sicherungs-URL](assets/mobile-assurance-url-type.png)

Weitere Informationen zu URL-Schemata in iOS finden Sie unter [Dokumentation zu Apple](https://developer.apple.com/documentation/xcode/defining-a-custom-url-scheme-for-your-app){target="_blank"}.

Die Sicherung funktioniert durch Öffnen einer URL, entweder über einen Browser oder QR-Code, diese URL beginnt mit der Basis-URL, die die App öffnet und zusätzliche Parameter enthält. Diese eindeutigen Parameter werden verwendet, um die Sitzung zu verbinden.

## Herstellen einer Verbindung zu einer Sitzung

1. Navigieren Sie zum [Assurance-Benutzeroberfläche](https://experience.adobe.com/griffon){target="_blank"}.
1. Auswählen **[!UICONTROL Sitzung erstellen]**.
1. Bereitstellung **[!UICONTROL Sitzungsname]** wie `Luma App QA` und **[!UICONTROL Basis-URL]** `lumadeeplink://default`
1. Klicken Sie auf **[!UICONTROL Weiter]**.
   ![Sicherheitssitzung erstellen](assets/mobile-assurance-create-session.png)
1. **[!UICONTROL QR-Code scannen]** wenn Sie ein physisches Gerät verwenden. Wenn Sie den Simulator verwenden, dann **[!UICONTROL Link kopieren]** und öffnen Sie es mit Safari im Simulator.
   ![Zuverlässigkeitsqa-Code](assets/mobile-assurance-qr-code.png)
1. Wenn die App geladen wird, erhalten Sie eine modale Aufforderung, Ihre PIN aus dem vorherigen Schritt einzugeben.
   ![Sicherungs-Node](assets/mobile-assurance-enter-pin.png)
1. Wenn die Verbindung erfolgreich hergestellt wurde, werden Ereignisse in der Web-Benutzeroberfläche &quot;Assurance&quot;und ein unverankertes Assurance-Symbol in der App angezeigt.
   * Symbol &quot;Versicherung&quot;unverankert.
      ![Zuverlässigkeitsmodal](assets/mobile-assurance-modal.png)
   * Experience Cloud-Ereignisse, die in der Web-Benutzeroberfläche auftreten.
      ![Zuverlässigkeitsereignisse](assets/mobile-assurance-events.png)

Wenn Sie auf Herausforderungen stoßen, lesen Sie bitte die [technisch](https://aep-sdks.gitbook.io/docs/foundation-extensions/adobe-experience-platform-assurance){target="_blank"} and [general documentation](https://aep-sdks.gitbook.io/docs/beta/project-griffon){target="_blank"}.

Weiter: **[Einverständnis](consent.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)
