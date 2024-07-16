---
title: Identitätsdaten in einer Mobile App mit Mobile SDK erfassen
description: Erfahren Sie, wie Sie Identitätsdaten in einer Mobile App erfassen.
feature: Mobile SDK,Identities
jira: KT-14633
exl-id: cbcd1708-29e6-4d74-be7a-f75c917ba2fa
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 1%

---

# Identitätsdaten erfassen

Erfahren Sie, wie Sie Identitätsdaten in einer Mobile App erfassen.

Mit Adobe Experience Platform Identity Service erhalten Sie einen besseren Überblick über Ihre Kunden und deren Verhalten, indem Sie Identitäten zwischen Geräten und Systemen überbrücken und so effektive persönliche digitale Erlebnisse in Echtzeit bereitstellen. Identitätsfelder und Namespaces sind der Kleber, der verschiedene Datenquellen verbindet, um das 360-Grad-Echtzeit-Kundenprofil zu erstellen.

Weitere Informationen zur [Identitätserweiterung](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/) und zum [Identitätsdienst](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de) finden Sie in der Dokumentation.

## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.

## Lernziele

In dieser Lektion werden Sie:

* Richten Sie einen benutzerdefinierten Identitäts-Namespace ein.
* Identitäten aktualisieren.
* Überprüfen Sie das Identitätsdiagramm.
* Abrufen von ECID und anderen Identitäten.


## Einrichten eines benutzerdefinierten Identitäts-Namespace

Identitäts-Namespaces sind Komponenten von [Identitätsdienst](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de) , die als Indikatoren für den Kontext dienen, auf den sich eine Identität bezieht. Sie unterscheiden beispielsweise den Wert `name@email.com` als E-Mail-Adresse oder `443522` als numerische CRM-ID.

>[!NOTE]
>
>Das Mobile SDK generiert eine eindeutige Identität in seinem eigenen Namespace namens Experience Cloud ID (ECID), wenn die App installiert wird. Diese ECID wird im persistenten Speicher auf dem Mobilgerät gespeichert und bei jedem Treffer gesendet. Die ECID wird entfernt, wenn der Benutzer die App deinstalliert oder den globalen Datenschutzstatus des Mobile SDK auf &quot;Opt-out&quot;setzt. In der Beispielanwendung &quot;Luma&quot;sollten Sie die App entfernen und neu installieren, um ein neues Profil mit einer eigenen eindeutigen ECID zu erstellen.


So erstellen Sie einen neuen Identitäts-Namespace:

1. Wählen Sie in der Datenerfassungs-Oberfläche im Navigationsbereich auf der linken Schiene die Option **[!UICONTROL Identitäten]** aus.
1. Wählen Sie **[!UICONTROL Identity-Namespace erstellen]** aus.
1. Geben Sie den **[!UICONTROL Anzeigenamen]** von `Luma CRM ID` und den Wert **[!UICONTROL Identitätssymbol]** von `lumaCRMId` an.
1. Wählen Sie **[!UICONTROL Geräteübergreifende ID]** aus.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   ![Identitäts-Namespace erstellen](assets/identity-create.png)




## Identitäten aktualisieren

Sie möchten sowohl die Standardidentität (E-Mail) als auch die benutzerdefinierte Identität (Luma CRM ID) aktualisieren, wenn sich der Benutzer bei der App anmeldet.

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** und suchen Sie nach der Implementierung der Funktion `func updateIdentities(emailAddress: String, crmId: String)` . Fügen Sie der Funktion den folgenden Code hinzu.

   ```swift
   // Set up identity map, add identities to map and update identities
   let identityMap: IdentityMap = IdentityMap()
   
   let emailIdentity = IdentityItem(id: emailAddress, authenticatedState: AuthenticatedState.authenticated)
   let crmIdentity = IdentityItem(id: crmId, authenticatedState: AuthenticatedState.authenticated)
   identityMap.add(item:emailIdentity, withNamespace: "Email")
   identityMap.add(item: crmIdentity, withNamespace: "lumaCRMId")
   
   Identity.updateIdentities(with: identityMap)
   ```

   Dieser Code:

   1. Erstellt ein leeres `IdentityMap` -Objekt.

      ```swift
      let identityMap: IdentityMap = IdentityMap()
      ```

   1. Richtet `IdentityItem` -Objekte für E-Mail und CRM-ID ein.

      ```swift
      let emailIdentity = IdentityItem(id: emailAddress, authenticatedState: AuthenticatedState.authenticated)
      let crmIdentity = IdentityItem(id: crmId, authenticatedState: AuthenticatedState.authenticated)
      ```

   1. Fügt diese `IdentityItem` -Objekte zum Objekt `IdentityMap` hinzu.

      ```swift
      identityMap.add(item:emailIdentity, withNamespace: "Email")
      identityMap.add(item: crmIdentity, withNamespace: "lumaCRMId")
      ```

   1. Sendet das Objekt `IdentityItem` als Teil des API-Aufrufs `Identity.updateIdentities` an das Edge Network.

      ```swift
      Identity.updateIdentities(with: identityMap) 
      ```

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]** und suchen Sie nach dem Code, der ausgeführt werden soll, wenn Sie die Schaltfläche **[!UICONTROL Anmelden]** auswählen. Fügen Sie den folgenden Code hinzu:

   ```swift
   // Update identities
   MobileSDK.shared.updateIdentities(emailAddress: currentEmailId, crmId: currentCRMId)                             
   ```


>[!NOTE]
>
>Sie können mehrere Identitäten in einem einzelnen `updateIdentities` -Aufruf senden. Sie können auch zuvor gesendete Identitäten ändern.


## Identität entfernen

Sie können die API [`Identity.removeIdentity`](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#removeidentity) verwenden, um die Identität aus der gespeicherten clientseitigen Identitätszuordnung zu entfernen. Die ID-Erweiterung stoppt das Senden der Kennung an das Edge Network. Die Verwendung dieser API entfernt die Kennung nicht aus dem serverseitigen Identitätsdiagramm. Weitere Informationen zu Identitätsdiagrammen finden Sie unter [Identitätsdiagramme anzeigen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/view-identity-graphs.html?lang=en) .

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** und fügen Sie den folgenden Code zur Funktion `func removeIdentities(emailAddress: String, crmId: String)` hinzu:

   ```swift
   // Remove identities and reset email and CRM Id to their defaults
   Identity.removeIdentity(item: IdentityItem(id: emailAddress), withNamespace: "Email")
   Identity.removeIdentity(item: IdentityItem(id: crmId), withNamespace: "lumaCRMId")
   currentEmailId = "testUser@gmail.com"
   currentCRMId = "112ca06ed53d3db37e4cea49cc45b71e"
   ```

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]** und suchen Sie nach dem Code, der ausgeführt werden soll, wenn Sie die Schaltfläche **[!UICONTROL Logout]** auswählen. Fügen Sie den folgenden Code hinzu:

   ```swift
   // Remove identities
   MobileSDK.shared.removeIdentities(emailAddress: currentEmailId, crmId: currentCRMId)                  
   ```


## Mit Assurance validieren

1. Lesen Sie den Abschnitt [Setup instructions](assurance.md#connecting-to-a-session) , um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. In der Luma-App
   1. Wählen Sie die Registerkarte **[!UICONTROL Home]** aus und verschieben Sie das Symbol &quot;Versicherung&quot;nach links.
   1. Wählen Sie die Symbol &quot;<img src="assets/login.png" width="15" />&quot;oben rechts.

      <img src="./assets/identity1.png" width="300">

   1. Geben Sie eine E-Mail-Adresse und eine CRM-ID an oder
   1. Auswählen <img src="assets/insert.png" width="15" /> , um nach dem Zufallsprinzip eine **[!UICONTROL E-Mail]** und eine **[!UICONTROL CRM-ID]** zu generieren.
   1. Wählen Sie **[!UICONTROL Anmelden]** aus.

      <img src="./assets/identity2.png" width="300">


1. Suchen Sie in der Assurance-Web-Oberfläche nach dem Ereignis **[!UICONTROL Edge Identity Update Identities]** vom Anbieter **[!UICONTROL com.adobe.griffon.mobile]** .
1. Wählen Sie das Ereignis aus und überprüfen Sie die Daten im Objekt **[!UICONTROL ACPExtensionEventData]** . Sie sollten die von Ihnen aktualisierten Identitäten sehen.
   ![validate identities update](assets/identity-validate-assurance.png)

## Validieren mit Identitätsdiagramm

Nachdem Sie die Schritte in der Experience Platform-Lektion ](platform.md) ausgeführt haben, können Sie die Identitätserfassung im Viewer für Identitätsdiagramme für Plattformen bestätigen:[

1. Wählen Sie **[!UICONTROL Identitäten]** in der Datenerfassungs-Benutzeroberfläche aus.
1. Wählen Sie in der oberen Leiste **[!UICONTROL Identitätsdiagramm]** aus.
1. Geben Sie `Luma CRM ID` als **[!UICONTROL Identitäts-Namespace]** und Ihre CRM-ID (z. B. `24e620e255734d8489820e74f357b5c8`) als **[!UICONTROL Identitätswert]** ein.
1. Sie sehen die **[!UICONTROL Identitäten]** aufgelistet.

   ![Identitätsdiagramm validieren](assets/identity-validate-graph.png)

>[!INFO]
>
>In der App gibt es keinen Code zum Zurücksetzen der ECID. Das bedeutet, dass Sie die ECID nur zurücksetzen (und effektiv ein neues Profil mit einer neuen ECID erstellen) können, indem Sie die Anwendung deinstallieren und neu installieren. Informationen zum Implementieren des Zurücksetzens von Kennungen finden Sie in den API-Aufrufen [`Identity.resetIdentities`](https://developer.adobe.com/client-sdks/documentation/mobile-core/identity/api-reference/#resetidentities) und [`MobileCore.resetIdentities`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#resetidentities) . Beachten Sie jedoch bei Verwendung einer Push-Benachrichtigungs-ID (siehe [Push-Benachrichtigungen senden](journey-optimizer-push.md)), dass diese Kennung zu einer weiteren &quot;Sticky&quot;-Profilkennung auf dem Gerät wird.


>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass Identitäten im Edge Network und (falls eingerichtet) mit Adobe Experience Platform aktualisiert werden.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu künftigen Inhalten teilen möchten, teilen Sie diese auf diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Profildaten erfassen](profile.md)**
