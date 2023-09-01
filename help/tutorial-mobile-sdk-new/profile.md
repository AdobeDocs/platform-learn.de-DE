---
title: Profil
description: Erfahren Sie, wie Sie Profildaten in einer Mobile App erfassen.
hide: true
source-git-commit: c31dd74cf8ff9c0856b29e82d9c8be2ad027df4a
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 5%

---

# Profil

Erfahren Sie, wie Sie Profildaten in einer Mobile App erfassen.

Sie können die Profil-Erweiterung verwenden, um Attribute über Ihren Benutzer auf dem Client zu speichern. Diese Informationen können später verwendet werden, um Nachrichten in Online- oder Offline-Szenarien auszuwählen und zu personalisieren, ohne dass für eine optimale Leistung eine Verbindung zu einem Server hergestellt werden muss. Die Profil-Erweiterung verwaltet das clientseitige Aktionsprofil (CSOP), bietet eine Möglichkeit, auf APIs zu reagieren, aktualisiert Benutzerprofilattribute und gibt die Benutzerprofilattribute für den Rest des Systems als generiertes Ereignis frei.

Die Profildaten werden von anderen Erweiterungen verwendet, um profilbezogene Aktionen durchzuführen. Ein Beispiel ist die Regel-Engine-Erweiterung, die die Profildaten nutzt und Regeln basierend auf den Profildaten ausführt. Weitere Informationen zum [Profilerweiterung](https://developer.adobe.com/client-sdks/documentation/profile/) in der Dokumentation

>[!IMPORTANT]
>
>Die in dieser Lektion beschriebene Profilfunktion unterscheidet sich von der Funktionalität des Echtzeit-Kundenprofils in Adobe Experience Platform und Platform-basierten Anwendungen.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.
* Profil-SDK importiert.

  ```swift
  import AEPUserProfile
  ```

## Lernziele

In dieser Lektion werden Sie:

* Festlegen oder Aktualisieren von Benutzerattributen.
* Abrufen von Benutzerattributen.


## Benutzerattribute festlegen und aktualisieren

Für Targeting und/oder Personalisierung wäre es hilfreich, schnell zu wissen, ob ein Benutzer zuvor in der App gekauft hat. Legen wir das in der Luma-App fest.

1. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Utils]** >  **[!UICONTROL MobileSDK]** im Xcode-Projektnavigator und suchen Sie die `func updateUserAttribute(attributeName: String, attributeValue: String)` -Funktion. Fügen Sie den folgenden Code hinzu:

   ```swift
   // Create a profile map
   var profileMap = [String: Any]()
   // Add attributes to profile map
   profileMap[attributeName] = attributeValue
   // Use profile map to update user attributes
   UserProfile.updateUserAttributes(attributeDict: profileMap)
   ```

   Dieser Code:

   1. Richtet ein leeres Wörterbuch ein mit dem Namen `profileMap`.

   1. Fügt dem Wörterbuch ein Element hinzu mit `attributeName` (Beispiel `isPaidUser`) und `attributeValue` (Beispiel `yes`).

   1. Verwendet die `profileMap` Wörterbuch als Wert für `attributeDict` Parameter der `UserProfile.updateUserAttributes` API-Aufruf.

1. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Ansichten]** > **[!UICONTROL Produkte]** > **[!UICONTROL ProductView]** im Xcode-Projektnavigator und suchen Sie den Aufruf an `updateUserAttributes` (im Code für die Käufe) <img src="assets/purchase.png" width="15" /> Schaltfläche):

   ```swift
   // Update attributes
   MobileSDK.shared.updateUserAttributes(attributeName: "isPaidUser", attributeValue: "yes")
   ```

Weitere Dokumentationen finden Sie [here](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattribute).

## Abrufen von Benutzerattributen

Nachdem Sie das -Attribut eines Benutzers aktualisiert haben, ist es für andere Adobe-SDKs verfügbar, Sie können aber auch Attribute explizit abrufen.

1. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Ansichten]** > Allgemein > **[!UICONTROL HomeView]** im Xcode-Projektnavigator und suchen Sie die `.onAppear` -Modifikator. Fügen Sie den folgenden Code hinzu:

   ```swift
   // Get attributes
   UserProfile.getUserAttributes(attributeNames: ["isPaidUser"]) { attributes, error in
       if attributes?["isPaidUser"] as! String == "yes" {
           showBadgeForUser = true
       }
       else {
           showBadgeForUser = false
       }
   }
   ```

   Dieser Code:

   1. Ruft die `UserProfile.getUserAttributes` Schließung mit `iPaidUser` Attributname als einzelnes Element im `attributeNames` Array.
   1. Prüft dann den Wert der `isPaidUser` Attribut und Zeitpunkt `yes`, platziert einen Badge auf der <img src="assets/paiduser.png" width="20" /> in der Symbolleiste oben rechts.

Weitere Dokumentationen finden Sie [here](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes).

## Validierung mit Versicherung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) Abschnitt.
1. Installieren Sie das Programm.
1. Starten Sie die App mithilfe der durch die Versicherung generierten URL.
1. Führen Sie die App aus, um sich anzumelden und mit einem Produkt zu interagieren.

   1. Verschieben Sie das Symbol &quot;Versicherung&quot;nach links.
   1. Auswählen **[!UICONTROL Startseite]** in der Symbolleiste.
   1. Um das Anmeldeblatt zu öffnen, wählen Sie die <img src="assets/login.png" width="15" /> Schaltfläche.
   1. Um eine zufällige E-Mail- und Kunden-ID einzufügen, wählen Sie die <img src="assets/insert.png" width="15" /> Schaltfläche .
   1. Auswählen **[!UICONTROL Anmelden]**.
   1. Auswählen **[!UICONTROL Produkte]** in der Symbolleiste.
   1. Wählen Sie ein Produkt aus.
   1. Auswählen <img src="assets/saveforlater.png" width="15" />.
   1. Auswählen <img src="assets/addtocart.png" width="20" />.
   1. Auswählen <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-1.png" width="200"> <img src="./assets/mobile-app-events-2.png" width="200"> <img src="./assets/mobile-app-events-3.png" width="200">
   1. Zurück zu **[!UICONTROL Startseite]** angezeigt. Es sollte ein Abzeichen hinzugefügt werden <img src="assets/person-badge-icon.png" width="15" />.

      <img src="./assets/personbadges.png" width="200">



1. In der Assurance-Benutzeroberfläche sollte eine **[!UICONTROL UserProfileUpdate]** und **[!UICONTROL getUserAttributes]** Ereignisse mit aktualisierter `profileMap` -Wert.
   ![Profil validieren](assets/profile-validate.png)

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass Profilattribute im Edge-Netzwerk und (falls eingerichtet) mit Adobe Experience Platform aktualisiert werden.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Geolocation-Dienste verwenden](places.md)**
