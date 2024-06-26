---
title: Implementieren der Zustimmung für Platform Mobile SDK-Implementierungen
description: Erfahren Sie, wie Sie die Zustimmung in eine Mobile App implementieren.
feature: Mobile SDK,Consent
jira: KT-14629
exl-id: 08042569-e16e-4ed9-9b5a-864d8b7f0216
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Implementieren der Zustimmung

Erfahren Sie, wie Sie die Zustimmung in eine Mobile App implementieren.

Die mobile Adobe Experience Platform-Erweiterung &quot;Einverständnis&quot;ermöglicht die Erfassung von Zustimmungsvoreinstellungen von Ihrer mobilen App bei Verwendung des Adobe Experience Platform Mobile SDK und der Edge Network-Erweiterung. Weitere Informationen zum [Zustimmungserweiterung](https://developer.adobe.com/client-sdks/documentation/consent-for-edge-network/) in der Dokumentation.

## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.

## Lernziele

In dieser Lektion werden Sie:

* Fordern Sie den Benutzer zur Zustimmung auf.
* Aktualisieren Sie die Erweiterung basierend auf der Benutzerantwort.
* Erfahren Sie, wie Sie den aktuellen Status der Zustimmung erhalten.

## Einverständnisersuchen

Wenn Sie das Tutorial von Anfang an befolgt haben, erinnern Sie sich möglicherweise daran, dass Sie die standardmäßige Zustimmung in der Erweiterung &quot;Einverständnis&quot;auf **[!UICONTROL Ausstehend - Queue-Ereignisse, die auftreten, bevor der Benutzer Zustimmungseinstellungen bereitstellt.]**

Um mit der Datenerfassung zu beginnen, müssen Sie die Zustimmung des Benutzers einholen. In einer realen App möchten Sie die Best Practices für die Zustimmung für Ihre Region konsultieren. In diesem Tutorial erhalten Sie das Einverständnis des Benutzers, indem Sie ihn einfach mit einem Warnhinweis anfordern:

1. Sie möchten den Benutzer nur einmal um Zustimmung bitten. Dazu können Sie die Mobile SDK-Zustimmung mit der erforderlichen Autorisierung für das Tracking mit Apple kombinieren [App Tracking Transparency Framework](https://developer.apple.com/documentation/apptrackingtransparency). In dieser App gehen Sie davon aus, dass Benutzer, wenn sie die Verfolgung zulassen, der Erfassung von Ereignissen zustimmen.

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** im Xcode-Projektnavigator.

   Fügen Sie diesen Code zum `updateConsent` -Funktion.

   ```swift
   // Update consent
   let collectConsent = ["collect": ["val": value]]
   let currentConsents = ["consents": collectConsent]
   Consent.update(with: currentConsents)
   MobileCore.updateConfigurationWith(configDict: currentConsents)
   ```

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL DisclaimerView]** im Projektnavigator von Xcode, der die Ansicht ist, die nach der ersten Installation oder Neuinstallation der Anwendung und dem ersten Starten der App angezeigt wird. Der Benutzer wird aufgefordert, das Tracking pro Apple zu autorisieren. [App Tracking Transparency Framework](https://developer.apple.com/documentation/apptrackingtransparency). Wenn der Benutzer autorisiert, aktualisieren Sie auch die Zustimmung.

   Fügen Sie den folgenden Code zum `ATTrackingManager.requestTrackingAuthorization { status in` Schließung.

   ```swift
   // Add consent based on authorization
   if status == .authorized {
      // Set consent to yes
      MobileSDK.shared.updateConsent(value: "y")
   }
   else {
      // Set consent to yes
      MobileSDK.shared.updateConsent(value: "n")
   }
   ```

## Aktuellen Zustimmungsstatus abrufen

Die mobile Erweiterung &quot;Einverständnis&quot;unterdrückt/sticht/ermöglicht das Tracking basierend auf dem aktuellen Zustimmungswert automatisch. Sie können auch selbst auf den aktuellen Zustimmungsstatus zugreifen:

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** im Projektnavigator von Xcode.

   Fügen Sie den folgenden Code zum `getConsents` Funktion:

   ```swift
   // Get consents
   Consent.getConsents { consents, error in
      guard error == nil, let consents = consents else { return }
      guard let jsonData = try? JSONSerialization.data(withJSONObject: consents, options: .prettyPrinted) else { return }
      guard let jsonStr = String(data: jsonData, encoding: .utf8) else { return }
      Logger.aepMobileSDK.info("Consent getConsents: \(jsonStr)")
   }
   ```

2. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL HomeView]** im Projektnavigator von Xcode.

   Fügen Sie den folgenden Code zum `.task` modifier:

   ```swift
   // Ask status of consents
   MobileSDK.shared.getConsents()   
   ```

Im obigen Beispiel protokollieren Sie einfach den Zustimmungsstatus in Xcode in der Konsole. In einem realen Szenario können Sie damit ändern, welche Menüs oder Optionen dem Benutzer angezeigt werden.

## Validierung mit Versicherung

1. Löschen Sie die Anwendung von Ihrem Gerät oder Simulator, um das Tracking und die Zustimmung ordnungsgemäß zurückzusetzen und zu initialisieren.
1. Um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden, lesen Sie die Informationen unter [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) Abschnitt.
1. Beim Verschieben der App von **[!UICONTROL Startseite]** Bildschirm zu **[!UICONTROL Produkte]** Bildschirm und zurück zu **[!UICONTROL Startseite]** angezeigt wird, sollte ein **[!UICONTROL Zustimmungsantwort abrufen]** -Ereignis in der Assurance-Benutzeroberfläche.
   ![Validieren der Zustimmung](assets/consent-update.png)


>[!SUCCESS]
>
>Sie haben Ihre App jetzt aktiviert, um den Benutzer beim ersten Start nach der Installation (oder Neuinstallation) aufzufordern, die Verwendung des Adobe Experience Platform Mobile SDK zu genehmigen.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Lebenszyklusdaten erfassen](lifecycle-data.md)**
