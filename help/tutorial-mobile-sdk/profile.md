---
title: Erfassen von Profildaten mit dem Platform Mobile SDK
description: Erfahren Sie, wie Sie Profildaten in einer Mobile App erfassen.
jira: KT-14634
exl-id: 97717611-04d9-45e3-a443-ea220a13b57c
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 1%

---

# Profildaten erfassen

Erfahren Sie, wie Sie Profildaten in einer Mobile App erfassen.

Sie können die Profil-Erweiterung verwenden, um Attribute über Ihren Benutzer auf dem Client zu speichern. Diese Informationen können später verwendet werden, um Nachrichten in Online- oder Offline-Szenarien auszuwählen und zu personalisieren, ohne dass für eine optimale Leistung eine Verbindung zu einem Server hergestellt werden muss. Die Profil-Erweiterung verwaltet das clientseitige Aktionsprofil (CSOP), bietet eine Möglichkeit, auf APIs zu reagieren, aktualisiert Benutzerprofilattribute und gibt die Benutzerprofilattribute für den Rest des Systems als generiertes Ereignis frei.

Die Profildaten werden von anderen Erweiterungen verwendet, um profilbezogene Aktionen durchzuführen. Ein Beispiel ist die Regel-Engine-Erweiterung, die die Profildaten nutzt und Regeln basierend auf den Profildaten ausführt. Weitere Informationen zur [Profil-Erweiterung](https://developer.adobe.com/client-sdks/documentation/profile/) finden Sie in der Dokumentation .

>[!IMPORTANT]
>
>Die in dieser Lektion beschriebene Profilfunktion unterscheidet sich von der Funktionalität des Echtzeit-Kundenprofils in Adobe Experience Platform und Platform-basierten Anwendungen.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.

## Lernziele

In dieser Lektion werden Sie:

* Festlegen oder Aktualisieren von Benutzerattributen.
* Abrufen von Benutzerattributen.


## Benutzerattribute festlegen und aktualisieren

Es wäre hilfreich für Targeting und/oder Personalisierung in der App, schnell zu erkennen, ob ein Benutzer in der Vergangenheit oder vor Kurzem einen Kauf getätigt hat. Legen wir das in der Luma-App fest.

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!DNL MobileSDK]** und suchen Sie die Funktion `func updateUserAttribute(attributeName: String, attributeValue: String)` . Fügen Sie den folgenden Code hinzu:

   ```swift
   // Create a profile map, add attributes to the map and update profile using the map
   var profileMap = [String: Any]()
   profileMap[attributeName] = attributeValue
   UserProfile.updateUserAttributes(attributeDict: profileMap)
   ```

   Dieser Code:

   1. Richtet ein leeres Wörterbuch mit dem Namen `profileMap` ein.

   1. Fügt ein Element zum Wörterbuch mit `attributeName` (z. B. `isPaidUser`) und `attributeValue` (z. B. `yes`) hinzu.

   1. Verwendet das Wörterbuch `profileMap` als Wert für den Parameter `attributeDict` des API-Aufrufs [`UserProfile.updateUserAttributes`](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattributes).

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!DNL ProductView]** und suchen Sie den Aufruf zu `updateUserAttributes` (innerhalb des Codes für die Käufe). Schaltfläche <img src="assets/purchase.png" width="15" /> ). Fügen Sie den folgenden Code hinzu:

   ```swift
   // Update attributes
   MobileSDK.shared.updateUserAttribute(attributeName: "isPaidUser", attributeValue: "yes")
   ```


## Abrufen von Benutzerattributen

Nachdem Sie das -Attribut eines Benutzers aktualisiert haben, ist es für andere Adobe-SDKs verfügbar, Sie können aber auch Attribute explizit abrufen, damit sich Ihre App wie gewünscht verhält.

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!DNL HomeView]** und suchen Sie den Modifikator `.onAppear` . Fügen Sie den folgenden Code hinzu:

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

   1. Ruft die [`UserProfile.getUserAttributes`](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes) -API mit dem Attributnamen `isPaidUser` als einzelnes Element im Array `attributeNames` auf.
   1. Prüft dann den Wert des `isPaidUser` -Attributs und platziert beim `yes` ein Zeichen auf der <img src="assets/paiduser.png" width="20" /> in der Symbolleiste oben rechts.

Zusätzliche Dokumentation finden Sie [hier](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes).

## Mit Assurance validieren

1. Lesen Sie den Abschnitt [Setup instructions](assurance.md#connecting-to-a-session) , um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Führen Sie die App aus, um sich anzumelden und mit einem Produkt zu interagieren.

   1. Verschieben Sie das Symbol &quot;Versicherung&quot;nach links.
   1. Wählen Sie in der Registerkartenleiste **[!UICONTROL Home]** aus.
   1. Um das Anmeldeblatt zu öffnen, wählen Sie die Schaltfläche <img src="assets/login.png" width="15" />.

      <img src="./assets/mobile-app-events-1.png" width="300">

   1. Um eine zufällige E-Mail- und Kunden-ID einzufügen, wählen Sie die Schaltfläche <img src="assets/insert.png" width="15" /> .
   1. Wählen Sie **[!UICONTROL Anmelden]** aus.

      <img src="./assets/mobile-app-events-2.png" width="300">

   1. Wählen Sie in der Registerkartenleiste **[!DNL Products]** aus.
   1. Wählen Sie ein Produkt aus.
   1. Auswählen <img src="assets/saveforlater.png" width="15" />.
   1. Auswählen <img src="assets/addtocart.png" width="20" />.
   1. Auswählen <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-3.png" width="300">

   1. Kehren Sie zurück zum Bildschirm **[!UICONTROL Home]** zurück. Sie sollten sehen, dass ein Badge hinzugefügt wurde <img src="assets/person-badge-icon.png" width="15" />.

      <img src="./assets/personbadges.png" width="300">



1. In der Assurance-Benutzeroberfläche sollten die Ereignisse **[!UICONTROL UserProfileUpdate]** und **[!UICONTROL getUserAttributes]** mit dem aktualisierten Wert `profileMap` angezeigt werden.
   ![validate profile](assets/profile-validate.png)

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass Profilattribute im Edge Network und (falls eingerichtet) mit Adobe Experience Platform aktualisiert werden.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu zukünftigen Inhalten haben möchten, teilen Sie diese in diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Orte verwenden](places.md)**
