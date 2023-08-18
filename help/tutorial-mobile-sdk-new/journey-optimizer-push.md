---
title: Push-Nachrichten in Adobe Journey Optimizer
description: Erfahren Sie, wie Sie mit dem Platform Mobile SDK und Adobe Journey Optimizer Push-Nachrichten für eine Mobile App erstellen.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: Push
hide: true
hidefromtoc: true
source-git-commit: ca83bbb571dc10804adcac446e2dba4fda5a2f1d
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 4%

---

# Push-Nachrichten in Adobe Journey Optimizer

Erfahren Sie, wie Sie mit dem Platform Mobile SDK und Adobe Journey Optimizer Push-Nachrichten für mobile Apps erstellen.

Mit Journey Optimizer können Sie Ihre Journey erstellen und Nachrichten an Zielgruppen senden. Bevor Sie Push-Benachrichtigungen mit Journey Optimizer senden, müssen Sie sicherstellen, dass die richtigen Konfigurationen und Integrationen vorhanden sind. Informationen zum Datenfluss von Push-Benachrichtigungen in Adobe Journey Optimizer finden Sie unter [die Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configuration-message/push-config/push-gs.html).

>[!NOTE]
>
>Diese Lektion ist optional und gilt nur für Adobe Journey Optimizer-Benutzer, die Push-Nachrichten senden möchten.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.
* Zugriff auf Adobe Journey Optimizer und ausreichende Berechtigungen wie beschrieben [here](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configuration-message/push-config/push-configuration.html?lang=en). Außerdem benötigen Sie ausreichende Berechtigungen für die folgenden Adobe Journey Optimizer-Funktionen.
   * Erstellen Sie eine App-Oberfläche.
   * Erstellen einer Journey
   * Erstellen einer Nachricht.
   * Erstellen von Nachrichtenvoreinstellungen.
* Bezahltes Apple-Entwicklerkonto mit ausreichendem Zugriff zum Erstellen von Zertifikaten, Kennungen und Schlüsseln.
* Physisches iOS-Gerät zum Testen.

## Lernziele

In dieser Lektion werden Sie:

* Registrieren Sie die App-ID beim Apple Push Notification Service (APN).
* Erstellen Sie eine **[!UICONTROL App-Oberfläche]** in AJO.
* Aktualisieren Sie Ihre **[!UICONTROL schema]** , um Push-Nachrichten einzuschließen.
* Installieren und konfigurieren Sie die **[!UICONTROL Adobe Journey Optimizer]** Tag-Erweiterung.
* Aktualisieren Sie Ihre App, um die AJO-Tag-Erweiterung einzuschließen.
* Validieren Sie die Einrichtung in &quot;Assurance&quot;.
* Senden Sie eine Testnachricht.


## App-ID mit APN registrieren

Die folgenden Schritte sind nicht Adobe Experience Cloud-spezifisch und sollen Sie durch die APN-Konfiguration führen.

### Privaten Schlüssel erstellen

1. Navigieren Sie im Apple-Entwicklerportal zu **[!UICONTROL Schlüssel]**.
1. Um einen Schlüssel zu erstellen, wählen Sie **[!UICONTROL +]**.
   ![neuen Schlüssel erstellen](assets/mobile-push-apple-dev-new-key.png)

1. Stellen Sie eine **[!UICONTROL Schlüsselname]**.
1. Wählen Sie die **[!UICONTROL APN]** aktivieren.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
   ![Neuen Schlüssel konfigurieren](assets/mobile-push-apple-dev-config-key.png)
1. Überprüfen Sie die Konfiguration und wählen Sie **[!UICONTROL registrieren]**.
1. Laden Sie die `.p8` privater Schlüssel. Sie wird in der App Surface-Konfiguration verwendet.
1. Beachten Sie die [!UICONTROL Schlüssel-ID]. Sie wird in der App Surface-Konfiguration verwendet.
1. Beachten Sie die [!UICONTROL Team-ID]. Sie wird in der App Surface-Konfiguration verwendet.
   ![Wichtigste Details](assets/push-apple-dev-key-details.png)

Weitere Dokumentationen können [hier finden](https://help.apple.com/developer-account/#/devcdfbb56a3).

## App-Push-Anmeldedaten zur Datenerfassung hinzufügen

1. Aus dem [Datenerfassungsoberfläche](https://experience.adobe.com/data-collection/)auswählen **[!UICONTROL App-Oberflächen]** im linken Bereich.
1. Um eine Konfiguration zu erstellen, wählen Sie **[!UICONTROL Erstellen von App-Oberflächen]**.
   ![App-Oberfläche - Startseite](assets/push-app-surface.png)
1. Geben Sie einen **[!UICONTROL Name]** für die Konfiguration, beispielsweise `Luma App Tutorial`  .
1. Wählen Sie in der Konfiguration der Mobile App die Option **[!UICONTROL Apple iOS]**.
1. Geben Sie die Bundle ID der Mobile App im Feld App-ID (iOS Bundle ID) ein. Wenn Sie zusammen mit der Luma-App folgen, lautet der Wert `com.adobe.luma.tutorial.swiftui`.
1. Schalten Sie die **[!UICONTROL Push-Anmeldedaten]** -Schaltfläche, um Ihre Anmeldedaten hinzuzufügen.
1. Ziehen und ablegen `.p8` **Authentifizierungsschlüssel für Apple-Push-Benachrichtigungen** -Datei.
1. Stellen Sie die **[!UICONTROL Schlüssel-ID]**, eine 10-stellige Zeichenfolge, die bei der Erstellung von `p8` Authentifizierungsschlüssel. Sie finden sie unter **[!UICONTROL Schlüssel]** Registerkarte in **Zertifikate, Kennungen und Profile** auf den Apple Developer Portal-Seiten.
1. Geben Sie die **[!UICONTROL Team ID]** an. Die Team-ID ist ein Wert, der unter der **Mitgliedschaft** oder oben auf den Apple Developer Portal-Seiten.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![App-Oberflächenkonfiguration](assets/push-app-surface-config.png)

## Adobe Journey Optimizer-Tag-Erweiterung installieren

1. Navigieren Sie zu **[!UICONTROL Tags]** > **[!UICONTROL Erweiterungen]** > **[!UICONTROL Katalog]**,
1. Öffnen Sie Ihre Eigenschaft, beispielsweise **[!UICONTROL Luma Mobile App-Tutorial]**.
1. Auswählen **[!UICONTROL Katalog]**.
1. Suchen Sie nach **[!UICONTROL Adobe Journey Optimizer]** -Erweiterung.
1. Installieren der Erweiterung.
1. Im **[!UICONTROL Installieren der Erweiterung]** dialog
   1. Wählen Sie beispielsweise eine Umgebung aus. **[!UICONTROL Entwicklung]**.
   1. Wählen Sie die **[!UICONTROL AJO Push Tracking Erlebnis-Datensatz]** Datensatz aus der **[!UICONTROL Ereignis-Datensatz]** Dropdown-Liste.
      ![Einstellungen der AJO-Erweiterung](assets/push-tags-ajo.png)
   1. Auswählen **[!UICONTROL In Bibliothek speichern und erstellen]**.

>[!NOTE]
>
>Wenn Sie nicht sehen `AJO Push Tracking Experience Event Dataset` als Option kontaktieren Sie den Kundendienst.
>

## Implementieren von Adobe Journey Optimizer in die App

Wie in den vorherigen Lektionen erläutert, bietet die Installation einer mobilen Tag-Erweiterung nur die Konfiguration. Als Nächstes müssen Sie das Messaging SDK installieren und registrieren. Wenn diese Schritte nicht klar sind, überprüfen Sie die [SDKs installieren](install-sdks.md) Abschnitt.

>[!NOTE]
>
>Wenn Sie die [SDKs installieren](install-sdks.md) -Abschnitt, ist das SDK bereits installiert und Sie können zu Schritt 7 überspringen.
>

1. Stellen Sie in Xcode sicher, dass [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios.git) wird zur Liste der Pakete in Package-Abhängigkeiten hinzugefügt. Siehe [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Öffnen Sie Xcode und navigieren Sie zu **[!UICONTROL AppDelegate]**.
1. Sichern `AEPMessaging` ist Teil Ihrer Importliste.

   `import AEPMessaging`

1. Sichern `Messaging.self` ist Teil des Arrays von Erweiterungen, die Sie registrieren.

   ```swift
   let extensions = [
       AEPIdentity.Identity.self,
       Lifecycle.self,
       Signal.self,
       Edge.self,
       AEPEdgeIdentity.Identity.self,
       Consent.self,
       UserProfile.self,
       Places.self,
       Messaging.self,
       Optimize.self,
       Assurance.self
   ]
   ```

1. Fügen Sie die `MobileCore.setPushIdentifier` der `application(_, didRegisterForRemoteNotificationsWithDeviceToken)` -Funktion.

   ```swift {highlight="7"}
   func application(_ application: UIApplication, didRegisterForRemoteNotificationsWithDeviceToken deviceToken: Data) {
       // Required to log the token
       let tokenParts = deviceToken.map { data in String(format: "%02.2hhx", data) }
       let token = tokenParts.joined()
       Logger.notifications.info("didRegisterForRemoteNotificationsWithDeviceToken - device token: \(token)")
   
       // Send push token to Experience Platform
       MobileCore.setPushIdentifier(deviceToken)
       currentDeviceToken = token
   }
   ```

   Diese Funktion ruft das Geräte-Token ab, das dem Gerät eindeutig ist, auf dem die App installiert ist, und sendet das Token zur Push-Nachrichtenbereitstellung an Adobe Apple.

## Validieren durch Senden einer Test-Push-Nachricht

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) Abschnitt.
1. Installieren Sie die App auf Ihrem physischen Gerät oder auf dem Simulator.
1. Starten Sie die App mithilfe der durch die Versicherung generierten URL.
1. Wählen Sie in der Assurance-Benutzeroberfläche die Option **[!UICONTROL Konfigurieren]**.
   ![configure click](assets/push-validate-config.png)
1. Wählen Sie die ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) Schaltfläche neben **[!UICONTROL Push Debug]**.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
   ![Speichern](assets/push-validate-save.png)
1. Auswählen **[!UICONTROL Push Debug]** über die linke Navigation.
1. Wählen Sie die **[!UICONTROL Einrichtung überprüfen]** Registerkarte.
1. Wählen Sie Ihr Gerät aus der **[!UICONTROL Client]** Liste.
1. Vergewissern Sie sich, dass keine Fehler auftreten.
   ![validate](assets/push-validate-confirm.png)
1. Wählen Sie die **[!UICONTROL Test-Push senden]** Registerkarte.
1. (optional) Ändern Sie die Standarddetails für **[!UICONTROL Titel]** und **[!UICONTROL body]**
1. Auswählen ![Fehler](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bug_18_N.svg) **[!UICONTROL Push-Benachrichtigung zum Testversand senden]**.
1. Überprüfen Sie die **[!UICONTROL Testergebnisse]**.
1. Sie sollten die Push-Benachrichtigung in Ihrer App sehen.

   <img src="assets/luma-app-push.png" width="300" />


>[!SUCCESS]
>
>Sie haben die App jetzt für Push-Benachrichtigungen mit der Adobe Journey Optimizer-Erweiterung für das Adobe Experience Platform Mobile SDK aktiviert.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Schlussfolgerung und nächste Schritte](conclusion.md)**
