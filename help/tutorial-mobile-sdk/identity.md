---
title: Erfassen von Identitätsdaten in einer Mobile App mit Mobile SDK
description: Erfahren Sie, wie Sie Identitätsdaten in einer Mobile App erfassen.
feature: Mobile SDK,Identities
jira: KT-14633
exl-id: cbcd1708-29e6-4d74-be7a-f75c917ba2fa
source-git-commit: d73f9b3eafb327783d6bfacaf4d57cf8881479f7
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 1%

---

# Erfassen von Identitätsdaten

Erfahren Sie, wie Sie Identitätsdaten in einer Mobile App erfassen.

Adobe Experience Platform Identity Service hilft Ihnen, sich einen besseren Überblick über Ihre Kunden und deren Verhalten zu verschaffen, indem Identitäten geräte- und systemübergreifend zusammengeführt werden. So können Sie in Echtzeit für eindrucksvolle persönliche digitale Erlebnisse sorgen. Identitätsfelder und Namespaces verbinden verschiedene Datenquellen miteinander, um das 360-Grad-Echtzeit-Kundenprofil zu erstellen.

Weitere Informationen zur [Identity-Erweiterung](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/) und zum [Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de) finden Sie in der Dokumentation.

## Voraussetzungen

* App mit installierten und konfigurierten SDKs erfolgreich erstellt und ausgeführt.

## Lernziele

In dieser Lektion erfahren Sie Folgendes:

* Richten Sie einen benutzerdefinierten Identity-Namespace ein.
* Aktualisieren von Identitäten.
* Validieren des Identitätsdiagramms.
* Abrufen von ECID und anderen Identitäten.


## Einrichten eines benutzerdefinierten Identity-Namespace

Identity-Namespaces sind Komponenten von [Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de) die als Indikatoren für den Kontext dienen, auf den sich eine Identität bezieht. Sie identifizieren beispielsweise den Wert `name@email.com` als E-Mail-Adresse oder `443522` als numerische CRM-ID.

>[!NOTE]
>
>Die Mobile SDK generiert eine eindeutige Identität in einem eigenen Namespace, der als Experience Cloud ID (ECID) bezeichnet wird, wenn die App installiert wird. Diese ECID wird im permanenten Speicher auf dem Mobilgerät gespeichert und bei jedem Treffer gesendet. Die ECID wird entfernt, wenn Benutzende die App deinstallieren oder den globalen Datenschutzstatus von Mobile SDK auf „Opt-out“ setzen. In der Beispiel-Luma-App sollten Sie die App entfernen und erneut installieren, um ein neues Profil mit einer eigenen eindeutigen ECID zu erstellen.


So erstellen Sie einen neuen Identity-Namespace:

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche **[!UICONTROL Identitäten]** in der linken Navigationsleiste aus.
1. Wählen Sie **[!UICONTROL Identity-Namespace erstellen]** aus.
1. Geben Sie einen **[!UICONTROL Anzeigenamen]** von `Luma CRM ID` und den Wert **[!UICONTROL Identitätssymbol]** von `lumaCRMId` an.
1. Wählen Sie **[!UICONTROL Geräteübergreifende ID]** aus.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   ![Identity-Namespace erstellen](assets/identity-create.png)




## Aktualisieren von Identitäten

Sie möchten sowohl die Standardidentität (E-Mail) als auch die benutzerdefinierte Identität (Luma CRM ID) aktualisieren, wenn sich der Benutzer bei der App anmeldet.

1. Navigieren Sie im Xcode-Projekt-]**zu **[!DNL Luma]**>**[!DNL Luma]**>**[!DNL Utils]**>**[!UICONTROL  MobileSDK) und suchen Sie nach der Implementierung der `func updateIdentities(emailAddress: String, crmId: String)`. Fügen Sie der Funktion den folgenden Code hinzu.

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

   1. Erstellt ein leeres `IdentityMap`.

      ```swift
      let identityMap: IdentityMap = IdentityMap()
      ```

   1. Richtet `IdentityItem` Objekte für E-Mail und CRM-ID ein.

      ```swift
      let emailIdentity = IdentityItem(id: emailAddress, authenticatedState: AuthenticatedState.authenticated)
      let crmIdentity = IdentityItem(id: crmId, authenticatedState: AuthenticatedState.authenticated)
      ```

   1. Fügt dem `IdentityMap`-Objekt diese `IdentityItem`-Objekte hinzu.

      ```swift
      identityMap.add(item:emailIdentity, withNamespace: "Email")
      identityMap.add(item: crmIdentity, withNamespace: "lumaCRMId")
      ```

   1. Sendet das `IdentityItem` als Teil des `Identity.updateIdentities`-API-Aufrufs an die Edge Network.

      ```swift
      Identity.updateIdentities(with: identityMap) 
      ```

1. Navigieren Sie im Xcode-Projekt-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]** und suchen Sie den Code, der ausgeführt werden soll, wenn Sie die Schaltfläche **[!UICONTROL Login]** auswählen. Fügen Sie den folgenden Code hinzu:

   ```swift
   // Update identities
   MobileSDK.shared.updateIdentities(emailAddress: currentEmailId, crmId: currentCRMId)                             
   ```


>[!NOTE]
>
>Sie können mehrere Identitäten in einem einzigen `updateIdentities`-Aufruf senden. Sie können auch zuvor gesendete Identitäten ändern.


## Entfernen einer Identität

Sie können die [`Identity.removeIdentity`](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#removeidentity)-API verwenden, um die Identität aus der gespeicherten Client-seitigen Identitätszuordnung zu entfernen. Die Identity-Erweiterung sendet die Kennung nicht mehr an die Edge Network. Bei Verwendung dieser API wird die Kennung nicht aus dem serverseitigen Identitätsdiagramm entfernt. Weitere [ zu Identitätsdiagrammen finden Sie ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/view-identity-graphs.html?lang=en) „Anzeigen von Identitätsdiagrammen“.

1. Navigieren Sie im Xcode-Projekt-]**zu **[!DNL Luma]**>**[!DNL Luma]**>**[!DNL Utils]**>**[!UICONTROL  MobileSDK) und fügen Sie den folgenden Code zur `func removeIdentities(emailAddress: String, crmId: String)` hinzu:

   ```swift
   // Remove identities and reset email and CRM Id to their defaults
   Identity.removeIdentity(item: IdentityItem(id: emailAddress), withNamespace: "Email")
   Identity.removeIdentity(item: IdentityItem(id: crmId), withNamespace: "lumaCRMId")
   currentEmailId = "testUser@gmail.com"
   currentCRMId = "b642b4217b34b1e8d3bd915fc65c4452"
   ```

1. Navigieren Sie im Xcode-Projekt-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]** und suchen Sie den Code, der ausgeführt werden soll, wenn Sie die Schaltfläche **[!UICONTROL Abmelden]** auswählen. Fügen Sie den folgenden Code hinzu:

   ```swift
   // Remove identities
   MobileSDK.shared.removeIdentities(emailAddress: currentEmailId, crmId: currentCRMId)                  
   ```


## Mit Assurance validieren

1. Lesen Sie den Abschnitt [Setup-Anweisungen](assurance.md#connecting-to-a-session), um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. In der Luma-App
   1. Wählen Sie die **[!UICONTROL Startseite]** und verschieben Sie das Assurance-Symbol nach links.
   1. Wählen Sie die <img src="assets/login.png" width="15" /> oben rechts.

      <img src="./assets/identity1.png" width="300">

   1. Geben Sie eine E-Mail-Adresse und eine CRM-ID an oder
   1. Auswählen <img src="assets/insert.png" width="15" /> nach dem Zufallsprinzip eine **[!UICONTROL E-Mail]** und **[!UICONTROL CRM ID]** zu generieren.
   1. Wählen Sie **[!UICONTROL Anmelden]** aus.

      <img src="./assets/identity2.png" width="300">


1. Suchen Sie in der Assurance-Web-Oberfläche nach dem Ereignis **[!UICONTROL Edge Identity Update]** Identities **[!UICONTROL vom Anbieter com.adobe.griffon.mobile]**.
1. Wählen Sie das Ereignis aus und überprüfen Sie die Daten im **[!UICONTROL ACPExextensionEventData]**-Objekt. Die aktualisierten Identitäten sollten angezeigt werden.
   ![Aktualisierung von Identitäten validieren](assets/identity-validate-assurance.png)

## Mit Identitätsdiagramm validieren

Nachdem Sie die Schritte in der [Experience Platform-Lektion](platform.md) abgeschlossen haben, können Sie die Identitätserfassung in der Identitätsdiagramm-Anzeige von Platform bestätigen:

1. Wählen **[!UICONTROL Identitäten]** in der Datenerfassungs-Benutzeroberfläche aus.
1. Wählen Sie **[!UICONTROL Identitätsdiagramm]** in der oberen Leiste aus.
1. Geben Sie `Luma CRM ID` als **[!UICONTROL Identity-Namespace]** und Ihre CRM-ID (z. B. `24e620e255734d8489820e74f357b5c8`) als **[!UICONTROL Identitätswert]** ein.
1. Sie sehen die **[!UICONTROL Identitäten]** aufgelistet.

   ![Identitätsdiagramm validieren](assets/identity-validate-graph.png)

>[!INFO]
>
>Es gibt keinen Code in der App, um die ECID zurückzusetzen. Das bedeutet, dass Sie die ECID nur durch eine Deinstallation und eine Neuinstallation der Anwendung zurücksetzen (und effektiv ein neues Profil mit einer neuen ECID erstellen) können. Informationen zum Implementieren des Zurücksetzens von Kennungen finden Sie in den [`Identity.resetIdentities`](https://developer.adobe.com/client-sdks/documentation/mobile-core/identity/api-reference/#resetidentities) und [`MobileCore.resetIdentities`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#resetidentities) API-Aufrufen. Beachten Sie jedoch, dass bei Verwendung einer Push-Benachrichtigungs-ID (siehe [Senden von Push-Benachrichtigungen](journey-optimizer-push.md)) diese Kennung zu einer weiteren „Sticky“-Profilkennung auf dem Gerät wird.


>[!SUCCESS]
>
>Sie haben jetzt Ihre App so eingerichtet, dass Identitäten in der Edge Network und (wenn eingerichtet) in Adobe Experience Platform aktualisiert werden.
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Erfassen von Profildaten](profile.md)**
