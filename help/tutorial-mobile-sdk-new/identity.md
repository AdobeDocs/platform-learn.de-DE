---
title: Identität
description: Erfahren Sie, wie Sie Identitätsdaten in einer Mobile App erfassen.
feature: Mobile SDK,Identities
hide: true
hidefromtoc: true
source-git-commit: ca83bbb571dc10804adcac446e2dba4fda5a2f1d
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 7%

---

# Identität

Erfahren Sie, wie Sie Identitätsdaten in einer Mobile App erfassen.

Mit Adobe Experience Platform Identity Service erhalten Sie einen besseren Überblick über Ihre Kunden und deren Verhalten, indem Sie Identitäten zwischen Geräten und Systemen überbrücken und so effektive persönliche digitale Erlebnisse in Echtzeit bereitstellen. Identitätsfelder und Namespaces sind der Kleber, der verschiedene Datenquellen verbindet, um das 360-Grad-Echtzeit-Kundenprofil zu erstellen.

Weitere Informationen zum [Identitätserweiterung](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/) und [Identitätsdienst](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de) in der Dokumentation.

## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.

## Lernziele

In dieser Lektion werden Sie:

* Richten Sie einen benutzerdefinierten Identitäts-Namespace ein.
* Identitäten aktualisieren.
* Überprüfen Sie das Identitätsdiagramm.
* Abrufen von ECID und anderen Identitäten.


## Einrichten eines benutzerdefinierten Identitäts-Namespace

Identity-Namespaces sind Komponenten von [Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de) , die als Indikatoren für den Kontext dienen, auf den sich eine Identität bezieht. Sie identifizieren beispielsweise den Wert `name@email.com` als E-Mail-Adresse oder `443522` als numerische CRM-ID.

1. Wählen Sie in der Datenerfassungsoberfläche die Option **[!UICONTROL Identitäten]** über die Navigationsleiste auf der linken Schiene aus.
1. Wählen Sie **[!UICONTROL Identity-Namespace erstellen]** aus.
1. Stellen Sie eine **[!UICONTROL Anzeigename]** von `Luma CRM ID` und **[!UICONTROL Identitätssymbol]** Wert von `lumaCRMId`.
1. Auswählen **[!UICONTROL Geräteübergreifende ID]**.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   ![Identitäts-Namespace erstellen](assets/identity-create.png)




## Identitäten aktualisieren

Sie möchten sowohl die Standardidentität (E-Mail) als auch die benutzerdefinierte Identität (Luma CRM ID) aktualisieren, wenn sich der Benutzer bei der App anmeldet.

1. Navigieren Sie zu **[!UICONTROL LoginSheet]** (in **[!UICONTROL Ansichten]** > **[!UICONTROL Allgemein]**) in das Xcode Luma-App-Projekt ein und suchen Sie den -Aufruf an `updateIdentities`:

   ```swift {highlight="3,4"}
   Button("Login") {
       // call updaeIdentities
       MobileSDK.shared.updateIdentities(emailAddress: currentEmailId, crmId: currentCRMId)
   
       // Send app interaction event
       MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
       dismiss()
   }
   .disabled(currentEmailId.isValidEmail == false)
   .buttonStyle(.bordered)
   ```

1. Navigieren Sie zum `updateIdentities` Funktionsimplementierung in **[!UICONTROL MobileSDK]** (in **[!UICONTROL Utils]**) im Xcode Luma-App-Projekt. Fügen Sie der Funktion den folgenden hervorgehobenen Code hinzu.

   ```swift {highlight="2-12"}
   func updateIdentities(emailAddress: String, crmId: String) {
       let identityMap: IdentityMap = IdentityMap()
       // Add identity items
       let emailIdentity = IdentityItem(id: emailAddress, authenticatedState: AuthenticatedState.authenticated)
       let crmIdentity = IdentityItem(id: crmId, authenticatedState: AuthenticatedState.authenticated)
       identityMap.add(item:emailIdentity, withNamespace: "Email")
       identityMap.add(item: crmIdentity, withNamespace: "lumaCRMId")
   
       // Update identities
       Identity.updateIdentities(with: identityMap)
   }
   ```

   Dieser Code:

   1. Erstellt eine leere `IdentityMap` -Objekt.

      ```swift
      let identityMap: IdentityMap = IdentityMap()
      ```

   1. Einrichten `IdentityItem` Objekte für E-Mail- und CRM-ID.

      ```swift
      let emailIdentity = IdentityItem(id: emailAddress, authenticatedState: AuthenticatedState.authenticated)
      let crmIdentity = IdentityItem(id: crmId, authenticatedState: AuthenticatedState.authenticated)
      ```

   1. Fügt diese hinzu `IdentityItem` -Objekte `IdentityMap` -Objekt.

      ```swift
      identityMap.add(item:emailIdentity, withNamespace: "Email")
      identityMap.add(item: crmIdentity, withNamespace: "lumaCRMId")
      ```

   1. Sendet die `IdentityItem` -Objekt als Teil der `Identity.updateIdentities` API-Aufruf an das Edge-Netzwerk.

      ```swift
      Identity.updateIdentities(with: identityMap) 
      ```


>[!NOTE]
>
>Sie können mehrere Identitäten in einer `updateIdentities` aufrufen. Sie können auch zuvor gesendete Identitäten ändern.


## Identität entfernen

Sie können `removeIdentity` , um die Identität aus der gespeicherten clientseitigen IdentityMap zu entfernen. Die ID-Erweiterung sendet die Kennung nicht mehr an das Edge-Netzwerk. Die Verwendung dieser API entfernt die Kennung nicht aus dem serverseitigen Benutzerprofildiagramm oder Identitätsdiagramm.

1. Navigieren Sie zu **[!UICONTROL LoginSheet]** (in **[!UICONTROL Ansichten]** > **[!UICONTROL Allgemein]**) in das Xcode Luma-App-Projekt ein und suchen Sie den -Aufruf an `removeIdentities`:

   ```swift {highlight="3"}
   Button("Logout", role: .destructive) {
       // call removeIdentities
       MobileSDK.shared.removeIdentities(emailAddress: currentEmailId, crmId: currentCRMId)
       dismiss()                   
   }
   .buttonStyle(.bordered)
   ```

1. Fügen Sie den folgenden Code zum `removeIdentities` -Funktion in `MobileSDK`:

   ```swift {highlight="2-8"}
   func removeIdentities(emailAddress: String, crmId: String) {
       Identity.removeIdentity(item: IdentityItem(id: emailAddress), withNamespace: "Email")
       Identity.removeIdentity(item: IdentityItem(id: crmId), withNamespace: "lumaCRMId")
       // reset email and CRM Id to their defaults
       currentEmailId = "testUser@gmail.com"
       currentCRMId = "112ca06ed53d3db37e4cea49cc45b71e"
   }
   ```


## Validierung mit Versicherung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) und verbinden Sie Ihren Simulator oder Ihr Gerät mit Assurance.
1. In der Luma-App
   1. Wählen Sie die **[!UICONTROL Startseite]** Registerkarte.
   1. Wählen Sie die **[!UICONTROL Anmelden]** rechts oben.
   1. Geben Sie eine E-Mail-Adresse und eine CRM-ID an oder
   1. Wählen Sie A| aus, um nach dem Zufallsprinzip eine **[!UICONTROL Email]** und **[!UICONTROL CRM-ID]**.
   1. Auswählen **[!UICONTROL Anmelden]**.

      <img src="./assets/identity1.png" width="300"> <img src="./assets/identity2.png" width="300">


1. Suchen Sie in der Web-Benutzeroberfläche &quot;Assurance&quot;nach dem **[!UICONTROL Identitäten für Edge-Identitätsaktualisierungen]**Ereignis aus dem **[!UICONTROL com.adobe.griffon.mobile]** -Anbieter.
1. Wählen Sie das Ereignis aus und überprüfen Sie die Daten im **[!UICONTROL ACPExtensionEventData]** -Objekt. Sie sollten die von Ihnen aktualisierten Identitäten sehen.
   ![Aktualisierung von Identitäten überprüfen](assets/identity-validate-assurance.png)

## Validieren mit Identitätsdiagramm

Nachdem Sie die Schritte im Abschnitt [Experience Platform-Lektion](platform.md), können Sie die Erfassung des Platzhalters im Identitätsdiagramm-Viewer für Plattformen bestätigen:

1. Auswählen **[!UICONTROL Identitäten]** in der Datenerfassungs-Benutzeroberfläche.
1. Auswählen **[!UICONTROL Identitätsdiagramm]** aus der oberen Leiste.
1. Eingabe `Luma CRM ID` als **[!UICONTROL Identitäts-Namespace]** und Ihrer CRM-ID (z. B. `24e620e255734d8489820e74f357b5c8`) als **[!UICONTROL Identitätswert]**.
1. Sie sehen die **[!UICONTROL Identitäten]** aufgelistet.

   ![Identitätsdiagramm überprüfen](assets/identity-validate-graph.png)


>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass Identitäten im Edge-Netzwerk und (falls eingerichtet) mit Adobe Experience Platform aktualisiert werden.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Profil](profile.md)**
