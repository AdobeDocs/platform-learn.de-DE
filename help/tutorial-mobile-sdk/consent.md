---
title: Einverständnis
description: Erfahren Sie, wie Sie die Zustimmung in eine Mobile App implementieren.
exl-id: 08042569-e16e-4ed9-9b5a-864d8b7f0216
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 3%

---

# Einverständnis

Erfahren Sie, wie Sie die Zustimmung in eine Mobile App implementieren.

Die mobile Adobe Experience Platform-Erweiterung &quot;Einverständnis&quot;ermöglicht die Erfassung von Zustimmungsvoreinstellungen von Ihrer mobilen App bei Verwendung des Adobe Experience Platform Mobile SDK und der Edge Network-Erweiterung. Weitere Informationen zum [Zustimmungserweiterung](https://aep-sdks.gitbook.io/docs/foundation-extensions/consent-for-edge-network), in der Dokumentation.

## Voraussetzungen

* Erfolgreiche Erstellung und Ausführung der App mit installierten und konfigurierten SDKs.

## Lernziele

In dieser Lektion werden Sie:

* Fordern Sie den Benutzer zur Zustimmung auf.
* Aktualisieren Sie die Erweiterung basierend auf der Benutzerantwort.
* Erfahren Sie, wie Sie den aktuellen Status der Zustimmung erhalten.

## Einverständnisersuchen

Wenn Sie das Tutorial von Anfang an befolgt haben, werden Sie sich daran erinnern, das **[!UICONTROL Standardmäßige Zustimmungsstufe]** auf &quot;Ausstehend&quot;. Um mit der Datenerfassung zu beginnen, müssen Sie die Zustimmung des Benutzers einholen. In diesem Tutorial erhalten Sie das Einverständnis, indem Sie einfach mit einem Warnhinweis fragen. In einer echten App möchten Sie die Best Practices für die Einwilligung für Ihre Region konsultieren.

1. Sie möchten den Benutzer nur einmal fragen. Eine einfache Möglichkeit, dies zu verwalten, besteht darin, einfach `UserDefaults`.
1. Navigieren Sie zu `Home.swift`.
1. Fügen Sie den folgenden Code zu `viewDidLoad()`.

   ```swift
   let defaults = UserDefaults.standard
   let consentKey = "askForConsentYet"
   let hidePopUp = defaults.bool(forKey: consentKey)
   ```

1. Wenn der Benutzer den Warnhinweis noch nie gesehen hat, zeigen Sie ihn an und aktualisieren Sie die Einwilligung je nach Antwort. Fügen Sie den folgenden Code zu `viewDidLoad()`.

   ```swift
   if(hidePopUp == false){
       //Consent Alert
       let alert = UIAlertController(title: "Allow Data Collection?", message: "Selecting Yes will begin data collection", preferredStyle: .alert)
       alert.addAction(UIAlertAction(title: "Yes", style: .default, handler: { action in
           //Update Consent -> "yes"
           let collectConsent = ["collect": ["val": "y"]]
           let currentConsents = ["consents": collectConsent]
           Consent.update(with: currentConsents)
           defaults.set(true, forKey: consentKey)
       }))
       alert.addAction(UIAlertAction(title: "No", style: .cancel, handler: { action in
           //Update Consent -> "no"
           let collectConsent = ["collect": ["val": "n"]]
           let currentConsents = ["consents": collectConsent]
           Consent.update(with: currentConsents)
           defaults.set(true, forKey: consentKey)
       }))
       self.present(alert, animated: true)
   }
   ```


## Aktuellen Zustimmungsstatus abrufen

Die mobile Erweiterung &quot;Einverständnis&quot;unterdrückt/unterdrückt/lässt/lässt das Tracking basierend auf dem aktuellen Zustimmungswert. Sie können auch selbst auf den aktuellen Zustimmungsstatus zugreifen:

1. Navigieren Sie zu `Home.swift`.
1. Fügen Sie den folgenden Code zu `viewDidLoad()`.

```swift
Consent.getConsents{ consents, error in
    guard error == nil, let consents = consents else { return }
    guard let jsonData = try? JSONSerialization.data(withJSONObject: consents, options: .prettyPrinted) else { return }
    guard let jsonStr = String(data: jsonData, encoding: .utf8) else { return }
    print("Consent getConsents: ",jsonStr)
}
```

Im obigen Beispiel drucken Sie einfach den Zustimmungsstatus in die Konsole. In einem realen Szenario können Sie damit ändern, welche Menüs oder Optionen dem Benutzer angezeigt werden.

## Validierung mit Versicherung

1. Überprüfen Sie die [Sicherheit](assurance.md) Lektion.
1. Installieren Sie das Programm.
1. Starten Sie die App mithilfe der durch die Versicherung generierten URL.
1. Wenn Sie den obigen Code korrekt hinzugefügt haben, werden Sie aufgefordert, die Zustimmung zu erteilen. Auswählen **Ja**.
   ![Popup für Einwilligung](assets/mobile-consent-validate.png)
1. Sie sollten eine **[!UICONTROL Zustimmungsvoreinstellungen aktualisiert]** -Ereignis in der Assurance-Benutzeroberfläche.
   ![Validieren der Zustimmung](assets/mobile-consent-update.png)

Weiter: **[Lebenszyklusdaten erfassen](lifecycle-data.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)