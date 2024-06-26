---
title: Push-Benachrichtigungen mit dem Platform Mobile SDK erstellen und senden
description: Erfahren Sie, wie Sie mit dem Platform Mobile SDK und Adobe Journey Optimizer Push-Benachrichtigungen für eine Mobile App erstellen.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: Push
jira: KT-14638
exl-id: e8e920d5-fd36-48b7-9185-a34231c0d336
source-git-commit: e316f881372a387b82f8af27f7f0ea032a99be99
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 1%

---

# Erstellen und Versenden von Push-Benachrichtigungen

Erfahren Sie, wie Sie Push-Benachrichtigungen für mobile Apps mit dem Experience Platform Mobile SDK und Journey Optimizer erstellen.

Mit Journey Optimizer können Sie Journey erstellen und Nachrichten an Zielgruppen senden. Bevor Sie Push-Benachrichtigungen mit Journey Optimizer senden, müssen Sie sicherstellen, dass die richtigen Konfigurationen und Integrationen vorhanden sind. Informationen zum Datenfluss von Push-Benachrichtigungen in Journey Optimizer finden Sie im Abschnitt [Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/push/push-config/push-gs.html).

![Architektur](assets/architecture-ajo.png)

>[!NOTE]
>
>Diese Lektion ist optional und gilt nur für Journey Optimizer-Benutzer, die Push-Benachrichtigungen versenden möchten.


## Voraussetzungen

* Die App wurde erfolgreich erstellt und mit installierten und konfigurierten SDKs ausgeführt.
* Richten Sie die App für Adobe Experience Platform ein.
* Zugriff auf Journey Optimizer und ausreichende Berechtigungen wie beschrieben [here](https://experienceleague.adobe.com/docs/journey-optimizer/using/push/push-config/push-configuration.html?lang=en). Außerdem benötigen Sie ausreichende Berechtigungen für die folgenden Journey Optimizer-Funktionen.
   * Erstellen Sie eine App-Oberfläche.
   * Erstellen Sie eine Journey.
   * Erstellen Sie eine Nachricht.
   * Erstellen Sie Nachrichtenvorgaben.
* **Bezahltes Apple-Entwicklerkonto** mit ausreichend Zugriff zum Erstellen von Zertifikaten, Kennungen und Schlüsseln.
* Physisches iOS-Gerät oder Simulator zum Testen.

## Lernziele

In dieser Lektion werden Sie

* Registrieren Sie die App-ID beim Apple Push Notification Service (APNs).
* Erstellen Sie eine App-Oberfläche in Journey Optimizer.
* Aktualisieren Sie Ihr Schema, um Push-Nachrichtenfelder einzuschließen.
* Installieren und konfigurieren Sie die Journey Optimizer-Tag-Erweiterung.
* Aktualisieren Sie Ihre App, um die Journey Optimizer-Tag-Erweiterung zu registrieren.
* Validieren Sie die Einrichtung in &quot;Assurance&quot;.
* Testnachricht aus Assurance senden
* Definieren Sie Ihr eigenes Push-Benachrichtigungsereignis, Ihre eigene Journey und Ihr eigenes Erlebnis in Journey Optimizer.
* Senden Sie Ihre eigene Push-Benachrichtigung aus der App heraus.


## Einrichten

>[!TIP]
>
>Wenn Sie Ihre Umgebung bereits als Teil der [In-App-Nachrichten in Journey Optimizer](journey-optimizer-inapp.md) -Lektion verwenden, haben Sie möglicherweise bereits einige der Schritte in diesem Einrichtungsabschnitt ausgeführt.

### App-ID mit APNS registrieren

Die folgenden Schritte sind nicht Adobe Experience Cloud-spezifisch und dienen als Orientierung für die Konfiguration von APNs.

#### Privaten Schlüssel erstellen

1. Navigieren Sie im Apple-Entwicklerportal zu **[!UICONTROL Schlüssel]**.
1. Um einen Schlüssel zu erstellen, wählen Sie **[!UICONTROL +]**.
   ![neuen Schlüssel erstellen](assets/mobile-push-apple-dev-new-key.png)

1. Stellen Sie eine **[!UICONTROL Schlüsselname]**.
1. Wählen Sie die **[!UICONTROL Apple Push Notification Service] (APNs)** aktivieren.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
   ![Neuen Schlüssel konfigurieren](assets/mobile-push-apple-dev-config-key.png)
1. Überprüfen Sie die Konfiguration und wählen Sie **[!UICONTROL registrieren]**.
1. Laden Sie die `.p8` privater Schlüssel. Sie wird später in dieser Lektion in der App Surface-Konfiguration verwendet.
1. Beachten Sie die **[!UICONTROL Schlüssel-ID]**. Sie wird in der App Surface-Konfiguration verwendet.
1. Beachten Sie die **[!UICONTROL Team-ID]**. Sie wird in der App Surface-Konfiguration verwendet.
   ![Wichtigste Details](assets/push-apple-dev-key-details.png)

Weitere Dokumentationen können [hier finden](https://help.apple.com/developer-account/#/devcdfbb56a3).

#### App-Oberfläche zur Datenerfassung hinzufügen

1. Aus dem [Datenerfassungsoberfläche](https://experience.adobe.com/data-collection/)auswählen **[!UICONTROL App-Oberflächen]** im linken Bereich.
1. Um eine Konfiguration zu erstellen, wählen Sie **[!UICONTROL App-Oberfläche erstellen]**.
   ![App-Oberfläche - Startseite](assets/push-app-surface.png)
1. Geben Sie einen **[!UICONTROL Name]** für die Konfiguration, beispielsweise `Luma App Tutorial`  .
1. Von **[!UICONTROL Konfiguration von Mobile Apps]** auswählen **[!UICONTROL Apple iOS]**.
1. Geben Sie die Paket-ID der mobilen App in die **[!UICONTROL App-ID (iOS Bundle ID)]** -Feld. Beispiel:  `com.adobe.luma.tutorial.swiftui`.
1. Schalten Sie die **[!UICONTROL Push-Anmeldedaten]** Schalten Sie um, um Ihre Anmeldedaten hinzuzufügen.
1. Ziehen und ablegen `.p8` **Authentifizierungsschlüssel für Apple-Push-Benachrichtigungen** -Datei.
1. Stellen Sie die **[!UICONTROL Schlüssel-ID]**, eine 10-stellige Zeichenfolge, die bei der Erstellung von `p8` Authentifizierungsschlüssel. Sie finden sie unter der **[!UICONTROL Schlüssel]** im **Zertifikate, Kennungen und Profile** auf den Apple Developer Portal-Seiten. Siehe auch [Privaten Schlüssel erstellen](#create-a-private-key).
1. Geben Sie die **[!UICONTROL Team ID]** an. Die Team-ID ist ein Wert, der unter der **Mitgliedschaft** oder oben auf der Apple Developer Portal-Seite. Siehe auch [Privaten Schlüssel erstellen](#create-a-private-key).
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![App-Oberflächenkonfiguration](assets/push-app-surface-config.png)

### Aktualisierung der Konfiguration des Datenspeichers

Um sicherzustellen, dass Daten, die von Ihrer mobilen App an das Edge-Netzwerk gesendet werden, an Journey Optimizer weitergeleitet werden, aktualisieren Sie Ihre Experience Edge-Konfiguration .

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche die Option **[!UICONTROL Datenspeicher]** und wählen Sie Ihren Datastream aus, z. B. **[!DNL Luma Mobile App]**.
1. Auswählen ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) für **[!UICONTROL Experience Platform]** und wählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Bearbeiten]** aus dem Kontextmenü aus.
1. Im **[!UICONTROL Datenspeicher]** > ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) >  **[!UICONTROL Adobe Experience Platform]** screen:

   1. Wenn noch nicht ausgewählt, wählen Sie **[!UICONTROL AJO Push Profile DataSet]** von **[!UICONTROL Profildatensatz]**. Dieser Profildatensatz ist bei Verwendung der `MobileCore.setPushIdentifier` API-Aufruf (siehe [Geräte-Token für Push-Benachrichtigungen registrieren](#register-device-token-for-push-notifications)), die sicherstellt, dass die eindeutige Kennung für Push-Benachrichtigungen (auch Push-Kennung genannt) als Teil des Benutzerprofils gespeichert wird.

   1. **[!UICONTROL Adobe Journey Optimizer]** ausgewählt ist. Siehe [Adobe Experience Platform-Einstellungen](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=en#aep) für weitere Informationen.

   1. Wählen Sie zum Speichern Ihrer Datastream-Konfiguration **[!UICONTROL Speichern]**.

   ![AEP-Datenspeicherkonfiguration](assets/datastream-aep-configuration.png)



### Journey Optimizer-Tag-Erweiterung installieren

Damit Ihre App mit Journey Optimizer verwendet werden kann, müssen Sie Ihre Tag-Eigenschaft aktualisieren.

1. Navigieren Sie zu **[!UICONTROL Tags]** > **[!UICONTROL Erweiterungen]** > **[!UICONTROL Katalog]**,
1. Öffnen Sie Ihre Eigenschaft, beispielsweise **[!DNL Luma Mobile App Tutorial]**.
1. Auswählen **[!UICONTROL Katalog]**.
1. Suchen Sie nach **[!UICONTROL Adobe Journey Optimizer]** -Erweiterung.
1. Installieren Sie die -Erweiterung.
1. Im **[!UICONTROL Installieren der Erweiterung]** dialog
   1. Wählen Sie beispielsweise eine Umgebung aus. **[!UICONTROL Entwicklung]**.
   1. Wählen Sie die **[!UICONTROL AJO Push Tracking Erlebnis-Datensatz]** Datensatz aus der **[!UICONTROL Ereignis-Datensatz]** Liste.
   1. Auswählen **[!UICONTROL In Bibliothek speichern und erstellen]**.
      ![Einstellungen der AJO-Erweiterung](assets/push-tags-ajo.png)

>[!NOTE]
>
>Wenn Sie nicht sehen **[!UICONTROL AJO Push Tracking Erlebnis-Datensatz]** als Option kontaktieren Sie den Kundendienst.
>

## Validieren der Einrichtung mit Assurance

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) -Abschnitt, um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Wählen Sie in der Assurance-Benutzeroberfläche die Option **[!UICONTROL Konfigurieren]**.
   ![configure click](assets/push-validate-config.png)
1. Auswählen ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) neben **[!UICONTROL Push Debug]**.
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
1. Die Test-Push-Benachrichtigung sollte in Ihrer App angezeigt werden.

   <img src="assets/luma-app-push.png" width="300" />


## Signing

Zum Senden von Push-Benachrichtigungen und **erfordert ein gebührenpflichtiges Apple-Entwicklerkonto**.

So aktualisieren Sie die Signatur für Ihre App:

1. Rufen Sie Ihre App in Xcode auf.
1. Auswählen **[!DNL Luma]** im Projekt-Navigator.
1. Wählen Sie die **[!DNL Luma]** Zielgruppe.
1. Wählen Sie die **Signieren und Funktionen** Registerkarte.
1. Konfigurieren **[!UICONTROL Automatische Verwaltungssignatur]**, **[!UICONTROL Team]**, und **[!UICONTROL Bundle-Kennung]** oder verwenden Sie Ihre spezifischen Apple-Entwicklungsbereitstellungsdetails.

   >[!IMPORTANT]
   >
   >Stellen Sie sicher, dass Sie eine _eindeutig_ Bundle-ID und ersetzen Sie `com.adobe.luma.tutorial.swiftui` Bundle-Kennung, da jede Bundle-ID eindeutig sein muss. In der Regel verwenden Sie ein Reverse-DNS-Format für Bundle-ID-Zeichenfolgen, z. B. `com.organization.brand.uniqueidentifier`. Die abgeschlossene Version dieses Tutorials verwendet beispielsweise `com.adobe.luma.tutorial.swiftui`.


   ![Xcode-Signaturfunktionen](assets/xcode-signing-capabilities.png){zoomable=&quot;yes&quot;}


## Hinzufügen von Push-Benachrichtigungsfunktionen zu Ihrer App

>[!IMPORTANT]
>
>Um Push-Benachrichtigungen in eine iOS-App zu implementieren und zu testen, benötigen Sie eine **bezahlt** Apple-Entwicklerkonto. Wenn Sie kein gebührenpflichtiges Apple-Entwicklerkonto haben, können Sie den Rest dieser Lektion überspringen.

1. Wählen Sie in Xcode **[!DNL Luma]** aus dem **[!UICONTROL ZIELE]** Liste, wählen Sie die **[!UICONTROL Signieren und Funktionen]** auswählen, wählen Sie die **[!UICONTROL + Funktion]** Schaltfläche und wählen Sie **[!UICONTROL Push-Benachrichtigungen]**. Dadurch kann Ihre App Push-Benachrichtigungen empfangen.

1. Als Nächstes müssen Sie der App eine Benachrichtigungserweiterung hinzufügen. Gehen Sie zurück zu **[!DNL General]** und wählen Sie die **[!UICONTROL +]** -Symbol unten im **[!UICONTROL ZIELE]** Abschnitt.

1. Sie werden aufgefordert, die Vorlage für Ihr neues Ziel auszuwählen. Auswählen **[!UICONTROL Erweiterung für Benachrichtigungsdienst]** und wählen Sie **[!UICONTROL Nächste]**.

1. Verwenden Sie im nächsten Fenster `NotificationExtension` als Namen der Erweiterung verwenden und auf die **[!UICONTROL Beenden]** Schaltfläche.

Sie sollten Ihrer App jetzt eine Push-Benachrichtigungs-Erweiterung hinzufügen, ähnlich dem unten stehenden Bildschirm.

![Erweiterung &quot;Pusen nofitications&quot;](assets/xcode-signing-capabilities-pushnotifications.png)


## Implementieren von Journey Optimizer in die App

Wie in den vorherigen Lektionen erläutert, bietet die Installation einer mobilen Tag-Erweiterung nur die Konfiguration. Als Nächstes müssen Sie das Messaging SDK installieren und registrieren. Wenn diese Schritte nicht klar sind, überprüfen Sie die [SDKs installieren](install-sdks.md) Abschnitt.

>[!NOTE]
>
>Wenn Sie die [SDKs installieren](install-sdks.md) -Abschnitt, ist das SDK bereits installiert und Sie können diesen Schritt überspringen.
>

1. Stellen Sie in Xcode sicher, dass [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios) wird zur Liste der Pakete in Package-Abhängigkeiten hinzugefügt. Siehe [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** im Xcode-Projektnavigator.
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

## Geräte-Token für Push-Benachrichtigungen registrieren

1. Fügen Sie die [`MobileCore.setPushIdentifier`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#setpushidentifier) API für die `func application(_ application: UIApplication, didRegisterForRemoteNotificationsWithDeviceToken deviceToken: Data)` -Funktion.

   ```swift
   // Send push token to Mobile SDK
   MobileCore.setPushIdentifier(deviceToken)
   ```

   Diese Funktion ruft das Geräte-Token ab, das für das Gerät eindeutig ist, auf dem die App installiert ist. Legt dann das Token für den Push-Benachrichtigungsversand mithilfe der von Ihnen eingerichteten Konfiguration fest, die sich auf den Push-Benachrichtigungsdienst (APNs) von Apple stützt.

>[!IMPORTANT]
>
>Die `MobileCore.updateConfigurationWith(configDict: ["messaging.useSandbox": true])` bestimmt, ob Push-Benachrichtigungen zum Senden von Push-Benachrichtigungen eine APN-Sandbox oder einen Produktionsserver verwenden. Stellen Sie beim Testen Ihrer App im Simulator oder auf einem Gerät sicher, dass die `messaging.useSandbox` auf `true` sodass Sie Push-Benachrichtigungen erhalten. Stellen Sie beim Bereitstellen Ihrer App für die Produktion zum Testen mit Apple Testflight sicher, dass Sie `messaging.useSandbox` nach `false` ansonsten kann Ihre Produktions-App keine Push-Benachrichtigungen empfangen.


## Erstellen einer eigenen Push-Benachrichtigung

Um eine eigene Push-Benachrichtigung zu erstellen, müssen Sie in Journey Optimizer ein Ereignis definieren, das einen Journey Trigger, der die Push-Benachrichtigung sendet.

### Schema aktualisieren

Sie werden einen neuen Ereignistyp definieren, der noch nicht als Teil der Liste der in Ihrem Schema definierten Ereignisse verfügbar ist. Sie verwenden diesen Ereignistyp später beim Auslösen von Push-Benachrichtigungen.

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche die Option **[!UICONTROL Schemas]** über die linke Leiste.
1. Auswählen **[!UICONTROL Durchsuchen]** in der Symbolleiste.
1. Wählen Sie beispielsweise Ihr Schema aus. **[!DNL Luma Mobile App Event Schema]** , um es zu öffnen.
1. Im Schema-Editor:
   1. Wählen Sie die **[!UICONTROL eventType]** -Feld.
   1. Im **[!UICONTROL Feldeigenschaften]** nach unten scrollen, um die Liste der möglichen Werte für den Ereignistyp anzuzeigen. Auswählen **[!UICONTROL Zeile hinzufügen]** und fügen Sie `application.test` als **[!UICONTROL WERT]** und `[!UICONTROL Test event for push notification]` als `DISPLAY NAME`.
   1. Wählen Sie **[!UICONTROL Anwenden]** aus.
   1. Wählen Sie **[!UICONTROL Speichern]** aus.
      ![Wert zu Ereignistypen hinzufügen](assets/ajo-update-schema-eventtype-enum.png)

### Ereignis definieren

Ereignisse in Journey Optimizer ermöglichen den einheitlichen Trigger Ihrer Journey, Nachrichten, z. B. Push-Benachrichtigungen, zu senden. Siehe [Über Ereignisse](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configure-journeys/events-journeys/about-events.html?lang=en) für weitere Informationen.

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche die Option **[!UICONTROL Konfigurationen]** über die linke Leiste.

1. Im **[!UICONTROL Dashboard]** Bildschirm, wählen Sie **[!UICONTROL Verwalten]** im **[!UICONTROL Veranstaltungen]** Kachel.

1. Im **[!UICONTROL Veranstaltungen]** Bildschirm, auswählen **[!UICONTROL Ereignis erstellen]**.

1. Im **[!UICONTROL Ereignis-Ereignis bearbeiten1]** -Bereich:

   1. Eingabe `LumaTestEvent` als **[!UICONTROL Name]** des Ereignisses.
   1. Stellen Sie eine **[!UICONTROL Beschreibung]**, beispielsweise `Test event to trigger push notifications in Luma app`.

   1. Wählen Sie das Erlebnisereignisschema der Mobile App aus, das Sie zuvor in [Erstellen eines XDM-Schemas](create-schema.md) aus dem **[!UICONTROL Schema]** beispielsweise Liste **[!DNL Luma Mobile App Event Schema v.1]**.
   1. Auswählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) neben dem **[!UICONTROL Felder]** Liste.

      ![Ereignis bearbeiten Schritt 1](assets/ajo-edit-event1.png)

      Im **[!UICONTROL Felder]** müssen Sie sicherstellen, dass die folgenden Felder ausgewählt sind (über den Standardfeldern, die immer ausgewählt sind (**[!UICONTROL _id]**, **[!UICONTROL id]**, und **[!UICONTROL timestamp]**). Mithilfe der Dropdown-Liste können Sie zwischen **[!UICONTROL Ausgewählt]**, **[!UICONTROL Alle]** und **[!UICONTROL Primär]** oder verwenden Sie ![Suche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) -Feld.

      * **[!UICONTROL App identifiziert (id)]**,
      * **[!UICONTROL Ereignistyp (eventType)]**,
      * **[!UICONTROL Primär (primary)]**.

      ![Ereignisfelder bearbeiten](assets/ajo-event-fields.png)

      Wählen Sie anschließend **[!UICONTROL Ok]**.

   1. Auswählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) neben dem **[!UICONTROL Ereignis-ID-Bedingung]** -Feld.

      1. Im **[!UICONTROL Ereignis-ID-Bedingung hinzufügen]** Dialogfeld, ziehen und ablegen **[!UICONTROL Ereignistyp (eventType)]** auf **[!UICONTROL Element hierher ziehen und ablegen]**.
      1. Scrollen Sie im Popover-Fenster zum unteren Rand und wählen Sie **[!UICONTROL application.test]** (Dies ist der Ereignistyp, den Sie zuvor zur Liste der Ereignistypen im Rahmen von [Schema aktualisieren](#update-your-schema)). Scrollen Sie dann nach oben und wählen Sie **[!UICONTROL Ok]**.
      1. Auswählen **[!UICONTROL Ok]** , um die Bedingung zu speichern.
         ![Ereignisbedingung bearbeiten](assets/ajo-edit-condition.png)

   1. Auswählen **[!UICONTROL ECID (ECID)]** aus dem **[!UICONTROL Namespace]** Liste. Automatisch die **[!UICONTROL Profilkennung]** -Feld mit **[!UICONTROL Die ID des ersten Elements des ECID-Schlüssels für die Map identityMap]**.
   1. Wählen Sie **[!UICONTROL Speichern]** aus.
      ![Ereignis bearbeiten Schritt 2](assets/ajo-edit-event2.png)

Sie haben soeben eine Ereigniskonfiguration erstellt, die auf dem Erlebnisereignisschema der Mobile App basiert, das Sie im Rahmen dieses Tutorials zuvor erstellt haben. Diese Ereigniskonfiguration filtert eingehende Erlebnisereignisse nach Ihrem spezifischen Ereignistyp (`application.test`), sodass nur Ereignisse mit diesem bestimmten Typ, die von Ihrer mobilen App aus initiiert werden, die im nächsten Schritt von Ihnen erstellte Journey Trigger werden. In einem realen Szenario möchten Sie möglicherweise Push-Benachrichtigungen von einem externen Dienst versenden. Dabei gelten jedoch die gleichen Konzepte: Von der externen Anwendung senden Sie ein Erlebnisereignis an Experience Platform, das spezifische Felder aufweist, auf die Sie Bedingungen anwenden können, bevor diese Ereignisse Trigger einer Journey werden.

### Journey erstellen

Als Nächstes erstellen Sie die Journey, die beim Empfang des entsprechenden Ereignisses den Versand der Push-Benachrichtigung an den Trigger sendet.

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche die Option **[!UICONTROL Journey]** über die linke Leiste.
1. Auswählen **[!UICONTROL Journey erstellen]**.
1. Im **[!UICONTROL Journey-Eigenschaften]** Bereich:

   1. Geben Sie einen **[!UICONTROL Name]** für die Journey, beispielsweise `Luma - Test Push Notification Journey`.
   1. Geben Sie einen **[!UICONTROL Beschreibung]** für die Journey, beispielsweise `Journey for test push notifications in Luma mobile app`.
   1. Sichern **[!UICONTROL Wiedereintritt erlauben]** ausgewählt und festgelegt ist **[!UICONTROL Wartezeit beim erneuten Eintritt]** nach **[!UICONTROL 30]** **[!UICONTROL Sekunden]**.
   1. Klicken Sie auf **[!UICONTROL OK]**.
      ![Journey-Eigenschaften](assets/ajo-journey-properties.png)

1. Zurück auf der Journey-Arbeitsfläche, aus dem **[!UICONTROL EREIGNISSE]**, ziehen Sie Ihre ![Ereignis](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Globe_18_N.svg) **[!DNL LumaTestEvent]** auf der Arbeitsfläche, auf der sie angezeigt wird **[!UICONTROL Wählen Sie ein Eintrittsereignis oder die Aktivität Audience lesen aus]**.

   * Im **[!UICONTROL Ereignisse: LumaTestEvent]** Bereich, geben Sie eine **[!UICONTROL Titel]**, beispielsweise `Luma Test Event`.

1. Aus dem **[!UICONTROL AKTIONEN]** Dropdown, per Drag &amp; Drop ![Push](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PushNotification_18_N.svg) **[!UICONTROL Push]** auf ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) im rechten **[!DNL LumaTestEvent]** -Aktivität. Im **[!UICONTROL Aktionen: Push]** -Bereich:

   1. Stellen Sie eine **[!UICONTROL Titel]**, beispielsweise `Luma Test Push Notification`, stellen Sie eine **[!UICONTROL Beschreibung]**, beispielsweise `Test push notification for Luma mobile app`auswählen **[!UICONTROL Transactional]** aus dem **[!UICONTROL Kategorie]** Liste und Auswahl **[!DNL Luma]** aus dem **[!UICONTROL Push-Oberfläche]**.
   1. Auswählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Inhalt bearbeiten]** , um die eigentliche Push-Benachrichtigung zu bearbeiten.
      ![Push-Eigenschaften](assets/ajo-push-properties.png)

      Im **[!UICONTROL Push-Benachrichtigung]** editor:

      1. Geben Sie einen **[!UICONTROL Titel]**, beispielsweise `Luma Test Push Notification` und geben Sie einen **[!UICONTROL body]**, beispielsweise `Test push notification for Luma mobile app`.
      1. Optional können Sie einen Link zu einem Bild (.png oder .jpg) in **[!UICONTROL Medien hinzufügen]**. Wenn Sie dies tun, wird das Bild Teil der Push-Benachrichtigung sein.
      1. Um den Editor zu speichern und zu verlassen, wählen Sie ![Chevron links](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronLeft_18_N.svg).
         ![Push-Editor](assets/ajo-push-editor.png)

   1. Um die Definition der Push-Benachrichtigung zu speichern und abzuschließen, wählen Sie **[!UICONTROL Ok]**.

1. Ihre Journey sollte wie unten dargestellt aussehen. Auswählen **[!UICONTROL Veröffentlichen]** , um Ihre Journey zu veröffentlichen und zu aktivieren.
   ![Abgeschlossene Journey](assets/ajo-journey-finished.png)


## Trigger der Push-Benachrichtigung

Sie verfügen über alle nötigen Bestandteile, um eine Push-Benachrichtigung zu versenden. Was bleibt, ist, wie diese Push-Benachrichtigung Trigger wird. Im Wesentlichen ist dies dasselbe wie zuvor: Senden Sie einfach ein Erlebnisereignis mit der richtigen Payload (wie in [Veranstaltungen](events.md)).

Diesmal wird das Erlebnisereignis, das Sie senden möchten, nicht zum Erstellen eines einfachen XDM-Wörterbuchs erstellt. Sie werden eine `struct` , die eine Push-Benachrichtigungs-Payload darstellen. Die Definition eines dedizierten Datentyps ist eine alternative Methode zur Implementierung der Erstellung von Erlebnisereignis-Payloads in Ihrer Anwendung.

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL Modell]** > **[!UICONTROL XDM]** > **[!UICONTROL TestPushPayload]** im Xcode-Projektnavigator und überprüfen Sie den Code.

   ```swift
   import Foundation
   
   // MARK: - TestPush
   struct TestPushPayload: Codable {
      let application: Application
      let eventType: String
   }
   
   // MARK: - Application
   struct Application: Codable {
      let id: String
   }
   ```

   Der Code stellt die folgende einfache Payload dar, die Sie an den Trigger Ihrer Test-Push-Benachrichtigung senden werden Journey

   ```json
   {
      "eventType": string,
      "application" : [
          "id": string
      ]
   }
   ```

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** im Xcode Project-Navigator und fügen Sie den folgenden Code zu `func sendTestPushEvent(applicationId: String, eventType: String)`:

   ```swift
   // Create payload and send experience event
   Task {
       let testPushPayload = TestPushPayload(
           application: Application(
               id: applicationId
           ),
           eventType: eventType
       )
       // send the final experience event
       await sendExperienceEvent(
           xdm: testPushPayload.asDictionary() ?? [:]
       )
   }
   ```

   Dieser Code erstellt eine `testPushPayload` -Instanz mit den Parametern, die der Funktion (`applicationId` und `eventType`) und anschließend -Aufrufe `sendExperienceEvent` beim Konvertieren der Payload in ein Wörterbuch. Dieser Code berücksichtigt diesmal auch die asynchronen Aspekte des Aufrufs des Adobe Experience Platform-SDK, indem das Swift-Parallelitätsmodell verwendet wird, das auf `await` und `async`.

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL ConfigView]** im Xcode-Projektnavigator. Fügen Sie in der Definition der Push-Benachrichtigungsschaltfläche den folgenden Code hinzu, um die Payload des Erlebnisereignisses für Push-Benachrichtigungen zu senden, die bei jedem Tippen auf diese Schaltfläche auf Ihre Journey Trigger werden.

   ```swift
   // Setting parameters and calling function to send push notification
   Task {
       let eventType = testPushEventType
       let applicationId = Bundle.main.bundleIdentifier ?? "No bundle id found"
       await MobileSDK.shared.sendTestPushEvent(applicationId: applicationId, eventType: eventType)
   }
   ```


## Validieren mit Ihrer App

1. Erstellen Sie die App im Simulator oder auf einem physischen Gerät aus Xcode neu und führen Sie sie mithilfe von ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** Registerkarte.

1. Tippen **[!UICONTROL Push-Benachrichtigung]**. Die Push-Benachrichtigung wird in Ihrer App angezeigt.

   <img src="assets/ajo-test-push.png" width="300" />


## Nächste Schritte

Sie sollten jetzt über alle Tools verfügen, um Push-Benachrichtigungen in Ihrer App zu verarbeiten. Sie können beispielsweise eine Journey in Journey Optimizer erstellen, die eine Willkommens-Push-Benachrichtigung sendet, wenn sich ein Anwender der App anmeldet. Oder eine Push-Benachrichtigung zur Bestätigung, wenn ein Benutzer ein Produkt in der App kauft. Oder gibt den Geofence eines Standorts ein (wie Sie in der [Orte](places.md) Lektion).

>[!SUCCESS]
>
>Sie haben die App jetzt für Push-Benachrichtigungen mit Journey Optimizer und der Journey Optimizer-Erweiterung für das Experience Platform Mobile SDK aktiviert.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[In-App-Nachrichten erstellen und senden](journey-optimizer-inapp.md)**
