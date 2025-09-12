---
title: Erfassen von Profildaten mit Platform Mobile SDK
description: Erfahren Sie, wie Sie Profildaten in einer Mobile App erfassen.
jira: KT-14634
exl-id: 97717611-04d9-45e3-a443-ea220a13b57c
source-git-commit: 4a0fa85c76c00fd505118692ea4b6cbe410f5839
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 1%

---

# Erfassen von Profildaten

Erfahren Sie, wie Sie Profildaten in einer Mobile App erfassen.

Sie können die Profilerweiterung verwenden, um Attribute über Ihre Benutzerin oder Ihren Benutzer auf dem Client zu speichern. Diese Informationen können später zum Targeting und zur Personalisierung von Nachrichten in Online- oder Offline-Szenarien verwendet werden, ohne dass eine Verbindung zu einem Server hergestellt werden muss, um eine optimale Leistung zu erzielen.

Die Profilerweiterung verwaltet das Client-seitige Vorgangsprofil (CSOP), bietet eine Möglichkeit, auf APIs zu reagieren, aktualisiert Benutzerprofilattribute und gibt die Benutzerprofilattribute als generiertes Ereignis für den Rest des Systems frei.

Die Profildaten werden von anderen Erweiterungen verwendet, um profilbezogene Aktionen durchzuführen. Ein Beispiel hierfür ist die Erweiterung Regel-Engine , die die Profildaten verwendet und Regeln auf der Grundlage der Profildaten ausführt. Weitere Informationen zur [Profilerweiterung](https://developer.adobe.com/client-sdks/documentation/profile/) finden Sie in der Dokumentation

>[!IMPORTANT]
>
>Die in dieser Lektion beschriebene Profilfunktion ist getrennt von der Echtzeit-Kundenprofilfunktion in Adobe Experience Platform und plattformbasierten Anwendungen.


## Voraussetzungen

* App mit installierten und konfigurierten SDKs erfolgreich erstellt und ausgeführt.

## Lernziele

In dieser Lektion erfahren Sie Folgendes:

* Benutzerattribute festlegen oder aktualisieren.
* Abrufen von Benutzerattributen.


## Benutzerattribute festlegen und aktualisieren

Für Targeting und Personalisierung in der App ist es hilfreich, schnell zu wissen, ob ein Benutzer in der Vergangenheit oder kürzlich einen Kauf getätigt hat. Richten wir das in der Luma-App ein.

>[!BEGINTABS]

>[!TAB iOS]

1. Navigieren Sie im Xcode-Projekt-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!DNL MobileSDK]** und suchen Sie nach der `func updateUserAttribute(attributeName: String, attributeValue: String)`. Fügen Sie den folgenden Code hinzu:

   ```swift
   // Create a profile map, add attributes to the map and update profile using the map
   var profileMap = [String: Any]()
   profileMap[attributeName] = attributeValue
   UserProfile.updateUserAttributes(attributeDict: profileMap)
   ```

   Dieser Code:

   1. Ein leeres Wörterbuch mit dem Namen `profileMap` wird eingerichtet.

   1. Fügt dem Wörterbuch ein Element mithilfe von `attributeName` (z. B. `isPaidUser`) und `attributeValue` (z. B. `yes`) hinzu.

   1. Verwendet das `profileMap` als Wert für den `attributeDict` des [`UserProfile.updateUserAttributes`](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattributes)-API-Aufrufs.

1. Navigieren Sie im Xcode-Projekt-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!DNL ProductView]** und suchen Sie den Aufruf an `updateUserAttributes` (im Code für die Schaltfläche Bestellungen ![Kreditkarte](/help/assets/icons/CreditCard.svg)). Fügen Sie den folgenden Code hinzu:

   ```swift
   // Update attributes
   MobileSDK.shared.updateUserAttribute(attributeName: "isPaidUser", attributeValue: "yes")
   ```

>[!TAB Android]

1. Android Navigieren Sie im Android Studio-Navigator zu **&#x200B;**![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]** und suchen Sie nach der `func updateUserAttribute(attributeName: String, attributeValue: String)`. Fügen Sie den folgenden Code hinzu:

   ```kotlin
   // Create a profile map, add attributes to the map and update profile using the map
   val profileMap = mapOf(attributeName to attributeValue)
   UserProfile.updateUserAttributes(profileMap)
   ```

   Dieser Code:

   1. Richtet eine leere Zuordnung mit dem Namen `profileMap` ein.

   1. Fügt der Zuordnung ein Element mithilfe von `attributeName` (zum Beispiel `isPaidUser`) und `attributeValue` (zum Beispiel `yes`) hinzu.

   1. Verwendet die `profileMap` Zuordnung als Wert zum `attributeDict` des [`UserProfile.updateUserAttributes`](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattributes)-API-Aufrufs.

1. Navigieren Sie zu **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** > **[!UICONTROL views]** > **[!UICONTROL ProductView.kt]** und suchen Sie den Aufruf an `updateUserAttributes` (im Code für die Schaltfläche ![CreditCard](/help/assets/icons/CreditCard.svg)). Fügen Sie den folgenden Code hinzu:

   ```kotlin
   // Update attributes
   MobileSDK.shared.updateUserAttribute("isPaidUser", "yes")
   ```

>[!ENDTABS]

## Benutzerattribute abrufen

Nachdem Sie das Attribut eines Benutzers aktualisiert haben, ist es für andere Adobe-SDKs verfügbar, Sie können jedoch auch Attribute explizit abrufen, damit sich Ihre App wie gewünscht verhält.

>[!BEGINTABS]

>[!TAB iOS]

1. Navigieren Sie im Xcode-Projekt-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!DNL HomeView]** und suchen Sie den `.onAppear`. Fügen Sie den folgenden Code hinzu:

   ```swift
   // Get attributes
   UserProfile.getUserAttributes(attributeNames: ["isPaidUser"]) { attributes, error in
       if attributes?.count ?? 0 > 0 {
           if attributes?["isPaidUser"] as? String == "yes" {
               showBadgeForUser = true
           }
           else {
               showBadgeForUser = false
           }
       }
   }
   ```

   Dieser Code:

   1. Ruft die [`UserProfile.getUserAttributes`](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes)-API mit dem `isPaidUser` Attributnamen als einzelnes Element im `attributeNames`-Array auf.
   1. Sucht dann nach dem Wert des `isPaidUser` Attributs und platziert `yes` oben rechts in der Symbolleiste ein Badge ![ das Symbol UserCheckedOut](/help/assets/icons/UserCheckedOut.svg).

>[!TAB Android]

1. Navigieren Sie im Android **[!UICONTROL -Projektnavigator zu]** Android![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.androi]** > **[!DNL views]** > **[!DNL HomeView.kt]** und suchen Sie nach dem `.onAppear`. Fügen Sie den folgenden Code hinzu:

   ```kotlin
   // Get attributes
   UserProfile.getUserAttributes(listOf("isPaidUser")) { attributes ->
       showBadgeForUser = attributes?.get("isPaidUser") == "yes"
   }
   ```

   Dieser Code:

   1. Ruft die [`UserProfile.getUserAttributes`](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes)-API mit dem `isPaidUser` Attributnamen als einzelnes Element im `attributeNames`-Array auf.
   1. Prüft dann auf den Wert des `isPaidUser`. Wenn `yes`, ersetzt der Code das Personensymbol durch ein Badge-Symbol in der Symbolleiste oben rechts.

>[!ENDTABS]

Weitere Informationen finden Sie [API](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes)Referenz.

## Mit Assurance validieren

1. Lesen Sie den Abschnitt [Setup-Anweisungen](assurance.md#connecting-to-a-session), um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Führen Sie die App aus, um sich anzumelden und mit einem Produkt zu interagieren.

>[!BEGINTABS]

>[!TAB iOS]

1. Wählen Sie **[!UICONTROL Startseite]** in der Registerkartenleiste aus.
1. Verschieben Sie das Assurance-Symbol nach links.
1. Um die Anmeldungsseite zu öffnen, klicken Sie auf die Schaltfläche ![Benutzer](/help/assets/icons/User.svg).

   <img src="./assets/mobile-app-events-1.png" width="300">

1. Um eine zufällige E-Mail und Kunden-ID einzufügen, klicken Sie auf die Schaltfläche > .
1. Wählen Sie **[!UICONTROL Anmelden]** aus.

   <img src="./assets/mobile-app-events-2.png" width="300">

1. Wählen Sie **[!DNL Products]** in der Registerkartenleiste aus.
1. Ein Produkt auswählen.
1. Wählen Sie ![Herz](/help/assets/icons/Heart.svg) aus.
1. Wählen Sie ![Warenkorb](/help/assets/icons/ShoppingCart.svg) aus.
1. Wählen Sie ![Kreditkarte](/help/assets/icons/CreditCard.svg) aus.

   <img src="./assets/mobile-app-events-3.png" width="300">

1. Kehren Sie zum Bildschirm **[!UICONTROL Startseite]** zurück. Sie sollten sehen, dass ein Abzeichen hinzugefügt wurde ![UserCheckedOut](/help/assets/icons/UserCheckedOut.svg).

   <img src="./assets/personbadges.png" width="300">


>[!TAB Android]

1. Wählen Sie **[!UICONTROL Startseite]** in der Registerkartenleiste aus.
1. Verschieben Sie das Assurance-Symbol nach links.
1. Um die Anmeldungsseite zu öffnen, klicken Sie auf die Schaltfläche ![Benutzer](/help/assets/icons/User.svg).

   <img src="./assets/mobile-app-events-1-android.png" width="300">

1. Um eine zufällige E-Mail und Kunden-ID einzufügen, wählen Sie **[!UICONTROL Zufällige E-Mail generieren]** aus.
1. Wählen Sie **[!UICONTROL Anmelden]** aus.

   <img src="./assets/mobile-app-events-2-android.png" width="300">

1. Wählen Sie **[!DNL Products]** in der Registerkartenleiste aus.
1. Ein Produkt auswählen.
1. Wählen Sie ![ThumbUp](/help/assets/icons/ThumbUp.svg)
1. Wählen Sie ![Warenkorb](/help/assets/icons/ShoppingCart.svg) aus.
1. Wählen Sie ![Kreditkarte](/help/assets/icons/CreditCard.svg) aus.

   <img src="./assets/mobile-app-events-3-android.png" width="300">

1. Kehren Sie zum Bildschirm **[!UICONTROL Startseite]** zurück. Sie sollten sehen, dass das Personensymbol aktualisiert wird.

   <img src="./assets/personbadges-android.png" width="300">

>[!ENDTABS]


In der Assurance-Benutzeroberfläche sollten die Ereignisse **[!UICONTROL UserProfileUpdate]** und **[!UICONTROL getUserAttributes]** mit dem aktualisierten `profileMap` angezeigt werden.

![Profil validieren](assets/profile-validate.png){zoomable="yes"}

>[!SUCCESS]
>
>Sie haben jetzt Ihre App so eingerichtet, dass Attribute von Profilen in der Edge Network und (wenn eingerichtet) in Adobe Experience Platform aktualisiert werden.
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796?profile.language=de).

Weiter: **[Verwenden Sie Orte](places.md)**
