---
title: Identität
description: Erfahren Sie, wie Sie Identitätsdaten in einer Mobile App erfassen.
feature: Mobile SDK,Identities
exl-id: cbcd1708-29e6-4d74-be7a-f75c917ba2fa
source-git-commit: bc53cb5926f708408a42aa98a1d364c5125cb36d
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 4%

---

# Identität

Erfahren Sie, wie Sie Identitätsdaten in einer Mobile App erfassen.

>[!INFO]
>
> Dieses Tutorial wird Ende November 2023 mithilfe einer neuen Beispiel-Mobile-App durch ein neues Tutorial ersetzt.

Mit Adobe Experience Platform Identity Service erhalten Sie einen besseren Überblick über Ihre Kunden und deren Verhalten, indem Sie Identitäten zwischen Geräten und Systemen überbrücken und so effektive persönliche digitale Erlebnisse in Echtzeit bereitstellen. Identitätsfelder und Namespaces sind der Kleber, der verschiedene Datenquellen verbindet, um das 360-Grad-Echtzeit-Kundenprofil zu erstellen.

Weitere Informationen zum [Identitätserweiterung](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/) und [Identitätsdienst](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de) in der Dokumentation.

## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.

## Lernziele

In dieser Lektion werden Sie:

* Standardidentität aktualisieren
* Richten Sie eine benutzerdefinierte Identität ein.
* Aktualisieren Sie eine benutzerdefinierte Identität.
* Überprüfen Sie das Identitätsdiagramm.
* Abrufen von ECID und anderen Identitäten.

## Standardidentität aktualisieren

Aktualisieren Sie zunächst die Identitätszuordnung des Benutzers, wenn er sich anmeldet.

1. Navigieren Sie zu `Login.swift` wenn die Luma-App und die Funktion namens `loginButt`.

   In der Beispielanwendung &quot;Luma&quot;gibt es keine Überprüfung des Benutzernamens oder Kennworts. Sie tippen einfach auf die Schaltflächen, um sich anzumelden.

1. Erstellen Sie die `IdentityMap` und `IdentityItem`.

   ```swift
   let identityMap: IdentityMap = IdentityMap()
   let emailIdentity = IdentityItem(id: emailAddress, authenticatedState: AuthenticatedState.authenticated)
   ```

1. Fügen Sie die `IdentityItem` der `IdentityMap`

   ```swift
   identityMap.add(item:emailIdentity, withNamespace: "Email")
   ```

1. Aufruf `updateIdentities` , um die Daten an das Platform Edge Network zu senden.

   ```swift
   Identity.updateIdentities(with: identityMap)
   ```

>[!NOTE]
>
>Sie können mehrere Identitäten in einem einzelnen updateIdentities-Aufruf senden. Sie können auch zuvor gesendete Identitäten ändern.


## Einrichten eines benutzerdefinierten Identitäts-Namespace

Identity-Namespaces sind Komponenten von [Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de) , die als Indikatoren für den Kontext dienen, auf den sich eine Identität bezieht. Sie unterscheiden beispielsweise den Wert &quot;name@email.com&quot;als E-Mail-Adresse oder &quot;443522&quot;als numerische CRM-ID.

1. Wählen Sie in der Datenerfassungsoberfläche die Option **[!UICONTROL Identitäten]** über die Navigationsleiste auf der linken Schiene aus.
1. Wählen Sie **[!UICONTROL Identity-Namespace erstellen]** aus.
1. Stellen Sie eine **[!UICONTROL Anzeigename]** von `Luma CRM ID` und **[!UICONTROL Identitätssymbol]** Wert von `lumaCrmId`.
1. Auswählen **[!UICONTROL Geräteübergreifende ID]**.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.

![Identitäts-Namespace erstellen](assets/mobile-identity-create.png)

## Benutzerdefinierte Identität aktualisieren

Nachdem Sie eine benutzerdefinierte Identität erstellt haben, beginnen Sie mit der Erfassung, indem Sie die `updateIdentities` -Code, den Sie im vorherigen Schritt hinzugefügt haben. Erstellen Sie einfach ein IdentityItem und fügen Sie es der IdentityMap hinzu. So sollte der vollständige Codeblock aussehen:

```swift
//Hardcoded identity values
let emailAddress = "testuser@gmail.com"
let crmId = "112ca06ed53d3db37e4cea49cc45b71e"

// Create identity map
let identityMap: IdentityMap = IdentityMap()
// Add email (standard)
let emailIdentity = IdentityItem(id: emailAddress, authenticatedState: AuthenticatedState.authenticated)
identityMap.add(item:emailIdentity, withNamespace: "Email")
// Add lumaCrmId (custom)
let crmIdentity = IdentityItem(id: crmId, authenticatedState: AuthenticatedState.authenticated)
identityMap.add(item: crmIdentity, withNamespace: "lumaCrmId")
// Update
Identity.updateIdentities(with: identityMap)
```

## Identität entfernen

Sie können `removeIdentity` , um die Identität aus der gespeicherten clientseitigen IdentityMap zu entfernen. Die ID-Erweiterung sendet die Kennung nicht mehr an das Edge-Netzwerk. Die Verwendung dieser API entfernt die Kennung nicht aus dem serverseitigen Benutzerprofildiagramm oder Identitätsdiagramm.

Fügen Sie Folgendes hinzu: `removeIdentity` Code zur Abmelde-Schaltfläche anklicken `Account.swift`.

```swift
// Logout
let logout = UIAlertAction(title: "Logout", style: .destructive, handler: { (action) -> Void in
    isLoggedIn = false;
    ////Hardcoded identity values
    let emailAddress = "testuser@gmail.com"
    let crmId = "112ca06ed53d3db37e4cea49cc45b71e"
    // Adobe Experience Platform - Remove Identity
    Identity.removeIdentity(item: IdentityItem(id: emailAddress), withNamespace: "Email")
    Identity.removeIdentity(item: IdentityItem(id: crmId), withNamespace: "lumaCrmId")
})
```

>[!NOTE]
>In den obigen Beispielen `crmId` und `emailAddress` sind fest codiert, aber in einer realen App wären die Werte dynamisch.

## Validierung mit Versicherung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) und verbinden Sie Ihren Simulator oder Ihr Gerät mit Assurance.
1. Wählen Sie in der App unten rechts das Konto -Symbol aus.

   ![luma-App-Konto](assets/mobile-identity-login.png)
1. Wählen Sie die **Anmelden** Schaltfläche.
1. Sie erhalten die Möglichkeit, einen Benutzernamen und ein Passwort einzugeben. Beide sind optional und Sie können einfach **Anmelden**.

   ![Login einer App](assets/mobile-identity-login-final.png)
1. Suchen Sie in der Web-Benutzeroberfläche &quot;Assurance&quot;nach dem `Edge Identity Update Identities` -Ereignis aus `com.adobe.griffon.mobile` -Anbieter.
1. Wählen Sie das Ereignis aus und überprüfen Sie die Daten im `ACPExtensionEventData` -Objekt. Sie sollten die von Ihnen aktualisierten Identitäten sehen.
   ![Aktualisierung von Identitäten überprüfen](assets/mobile-identity-validate-assurance.png)

## Validieren mit Identitätsdiagramm

Nachdem Sie die Schritte im Abschnitt [Experience Platform-Lektion](platform.md), können Sie auch die Erfassung des Platzhalters im Identitätsdiagramm-Viewer für Plattformen bestätigen:

![Identitätsdiagramm überprüfen](assets/mobile-identity-validate.png)


Weiter: **[Profil](profile.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)