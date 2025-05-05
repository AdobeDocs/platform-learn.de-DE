---
title: Erfassen von Profildaten mit Platform Mobile SDK
description: Erfahren Sie, wie Sie Profildaten in einer Mobile App erfassen.
jira: KT-14634
exl-id: 97717611-04d9-45e3-a443-ea220a13b57c
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 1%

---

# Erfassen von Profildaten

Erfahren Sie, wie Sie Profildaten in einer Mobile App erfassen.

Sie können die Profilerweiterung verwenden, um Attribute über Ihre Benutzerin oder Ihren Benutzer auf dem Client zu speichern. Diese Informationen können später zum Targeting und zur Personalisierung von Nachrichten in Online- oder Offline-Szenarien verwendet werden, ohne dass eine Verbindung zu einem Server hergestellt werden muss, um eine optimale Leistung zu erzielen. Die Profilerweiterung verwaltet das Client-seitige Vorgangsprofil (CSOP), bietet eine Möglichkeit, auf APIs zu reagieren, aktualisiert Benutzerprofilattribute und gibt die Benutzerprofilattribute als generiertes Ereignis für den Rest des Systems frei.

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

Es wäre hilfreich, wenn Sie beim Targeting und/oder der Personalisierung in der App schnell feststellen würden, ob ein Benutzer in der Vergangenheit oder kürzlich einen Kauf getätigt hat. Richten wir das in der Luma-App ein.

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

1. Navigieren Sie im Xcode-Projekt-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!DNL ProductView]** und suchen Sie den Aufruf an `updateUserAttributes` (im Code für die Bestellungen) <img src="assets/purchase.png" width="15" />). Fügen Sie den folgenden Code hinzu:

   ```swift
   // Update attributes
   MobileSDK.shared.updateUserAttribute(attributeName: "isPaidUser", attributeValue: "yes")
   ```


## Benutzerattribute abrufen

Nachdem Sie das Attribut eines Benutzers aktualisiert haben, ist es für andere Adobe-SDKs verfügbar, Sie können aber auch Attribute explizit abrufen, damit sich Ihre App wie gewünscht verhält.

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
   1. Prüft dann auf den Wert des `isPaidUser` Attributs und platziert `yes` ein Badge auf dem <img src="assets/paiduser.png" width="20" /> oben rechts in der Symbolleiste.

Weitere Dokumentationen finden Sie [hier](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes).

## Mit Assurance validieren

1. Lesen Sie den Abschnitt [Setup-Anweisungen](assurance.md#connecting-to-a-session), um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Führen Sie die App aus, um sich anzumelden und mit einem Produkt zu interagieren.

   1. Verschieben Sie das Assurance-Symbol nach links.
   1. Wählen Sie **[!UICONTROL Startseite]** in der Registerkartenleiste aus.
   1. Um die Anmeldeseite zu öffnen, wählen Sie die <img src="assets/login.png" width="15" />.

      <img src="./assets/mobile-app-events-1.png" width="300">

   1. Um eine zufällige E-Mail und Kunden-ID einzufügen, wählen Sie die Schaltfläche <img src="assets/insert.png" width="15" /> .
   1. Wählen Sie **[!UICONTROL Anmelden]** aus.

      <img src="./assets/mobile-app-events-2.png" width="300">

   1. Wählen Sie **[!DNL Products]** in der Registerkartenleiste aus.
   1. Ein Produkt auswählen.
   1. Auswählen <img src="assets/saveforlater.png" width="15" />.
   1. Auswählen <img src="assets/addtocart.png" width="20" />.
   1. Auswählen <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-3.png" width="300">

   1. Kehren Sie zum Bildschirm **[!UICONTROL Startseite]** zurück. Sie sollten sehen, dass ein Abzeichen hinzugefügt wurde <img src="assets/person-badge-icon.png" width="15" />.

      <img src="./assets/personbadges.png" width="300">



1. In der Assurance-Benutzeroberfläche sollten die Ereignisse **[!UICONTROL UserProfileUpdate]** und **[!UICONTROL getUserAttributes]** mit dem aktualisierten `profileMap` angezeigt werden.
   ![Profil validieren](assets/profile-validate.png)

>[!SUCCESS]
>
>Sie haben jetzt Ihre App so eingerichtet, dass Attribute von Profilen im Edge Network und (wenn eingerichtet) mit Adobe Experience Platform aktualisiert werden.
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796?profile.language=de).

Weiter: **[Verwenden Sie Orte](places.md)**
