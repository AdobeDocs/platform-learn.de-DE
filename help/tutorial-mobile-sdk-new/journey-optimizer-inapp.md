---
title: In-App-Nachrichten erstellen und senden
description: Erfahren Sie, wie Sie mit dem Platform Mobile SDK und Adobe Journey Optimizer In-App-Nachrichten erstellen und an eine Mobile App senden.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: In App
hide: true
source-git-commit: a2788110b1c43d24022672bb5ba0f36af66d962b
workflow-type: tm+mt
source-wordcount: '1547'
ht-degree: 6%

---

# In-App-Nachrichten erstellen und senden

Erfahren Sie, wie Sie In-App-Nachrichten für mobile Apps mit Experience Platform Mobile SDK und Journey Optimizer erstellen.

Mit Journey Optimizer können Sie Kampagnen erstellen, um In-App-Nachrichten an Zielgruppen zu senden. Kampagnen in Journey Optimizer werden verwendet, um einmalige Inhalte mithilfe verschiedener Kanäle an eine bestimmte Zielgruppe zu senden. Bei Kampagnen werden die Aktionen gleichzeitig ausgeführt, entweder sofort oder nach einem bestimmten Zeitplan. Bei der Verwendung von Journey (siehe [Journey Optimizer-Push-Benachrichtigungen](journey-optimizer-push.md) Lektion), werden Aktionen nacheinander ausgeführt.

![Architektur](assets/architecture-ajo.png)

Bevor Sie In-App-Nachrichten mit Journey Optimizer senden, müssen Sie sicherstellen, dass die richtigen Konfigurationen und Integrationen vorhanden sind. Informationen zum Datenfluss von In-App-Nachrichten in Journey Optimizer finden Sie unter [die Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/in-app/inapp-configuration.html?lang=en).

>[!NOTE]
>
>Diese Lektion ist optional und gilt nur für Journey Optimizer-Benutzer, die In-App-Nachrichten senden möchten.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.
* Richten Sie die App für Adobe Experience Platform ein.
* Zugriff auf Journey Optimizer und ausreichende Berechtigungen wie beschrieben [here](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configuration-message/push-config/push-configuration.html?lang=en). Außerdem benötigen Sie ausreichende Berechtigungen für die folgenden Journey Optimizer-Funktionen.
   * Verwalten von Kampagnen
* Bezahltes Apple-Entwicklerkonto mit ausreichendem Zugriff zum Erstellen von Zertifikaten, Kennungen und Schlüsseln.
* Physisches iOS-Gerät oder Simulator zum Testen.


## Lernziele

In dieser Lektion werden Sie

* Registrieren Sie die App-ID beim Apple Push Notification Service (APN).
* Erstellen Sie eine App-Oberfläche in AJO.
* Installieren und konfigurieren Sie die Journey Optimizer-Tag-Erweiterung.
* Aktualisieren Sie Ihre App, um die Journey Optimizer-Tag-Erweiterung zu registrieren.
* Validieren Sie die Einrichtung in &quot;Assurance&quot;.
* Definieren Sie Ihr eigenes Kampagnen- und In-App-Nachrichtenerlebnis in Journey Optimizer.
* Senden Sie Ihre eigene In-App-Nachricht aus der App heraus.

## Einrichten

>[!TIP]
>
>Wenn Sie Ihre Umgebung bereits als Teil der [Push-Nachrichten in Journey Optimizer](journey-optimizer-push.md) -Lektion verwenden, haben Sie möglicherweise bereits einige der Schritte in diesem Einrichtungsabschnitt ausgeführt.


### App-Oberfläche zur Datenerfassung hinzufügen

1. Aus dem [Datenerfassungsoberfläche](https://experience.adobe.com/data-collection/)auswählen **[!UICONTROL App-Oberflächen]** im linken Bereich.
1. Um eine Konfiguration zu erstellen, wählen Sie **[!UICONTROL App-Oberfläche erstellen]**.
   ![App-Oberfläche - Startseite](assets/push-app-surface.png)
1. Geben Sie einen **[!UICONTROL Name]** für die Konfiguration, beispielsweise `Luma App Tutorial`  .
1. Von **[!UICONTROL Konfiguration von Mobile Apps]** auswählen **[!UICONTROL Apple iOS]**.
1. Geben Sie die Bundle ID der Mobile App im Feld **[!UICONTROL App-ID (iOS Bundle ID)]** ein. Beispiel,  `com.adobe.luma.tutorial.swiftui`.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![App-Oberflächenkonfiguration](assets/push-app-surface-config.png)

### Aktualisierung der Konfiguration des Datenspeichers

Um sicherzustellen, dass Daten, die von Ihrer mobilen App an das Edge-Netzwerk gesendet werden, an Journey Optimizer weitergeleitet werden, aktualisieren Sie Ihre Experience Edge-Konfiguration .

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche die Option **[!UICONTROL Datenspeicher]** und wählen Sie Ihren Datastream aus, z. B. **[!DNL Luma Mobile App]**.
1. Auswählen ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) für **[!UICONTROL Experience Platform]** und wählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Bearbeiten]** aus dem Kontextmenü aus.
1. Im **[!UICONTROL Datenspeicher]** > ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) >  **[!UICONTROL Adobe Experience Platform]** Bildschirm, stellen Sie sicher **[!UICONTROL Adobe Journey Optimizer]** ausgewählt ist. Siehe [Adobe Experience Platform-Einstellungen](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=en#aep) für weitere Informationen.
1. Wählen Sie zum Speichern Ihrer Datastream-Konfiguration **[!UICONTROL Speichern]**.

   ![AEP-Datenspeicherkonfiguration](assets/datastream-aep-configuration.png)


### Journey Optimizer-Tag-Erweiterung installieren

Damit Ihre App mit Journey Optimizer verwendet werden kann, müssen Sie Ihre Tag-Eigenschaft aktualisieren.

1. Navigieren Sie zu **[!UICONTROL Tags]** > **[!UICONTROL Erweiterungen]** > **[!UICONTROL Katalog]**.
1. Öffnen Sie Ihre Eigenschaft, beispielsweise **[!DNL Luma Mobile App Tutorial]**.
1. Auswählen **[!UICONTROL Katalog]**.
1. Suchen Sie nach **[!UICONTROL Adobe Journey Optimizer]** -Erweiterung.
1. Installieren der Erweiterung.
1. Im **[!UICONTROL Installieren der Erweiterung]** dialog
   1. Wählen Sie beispielsweise eine Umgebung aus. **[!UICONTROL Entwicklung]**.
   1. Wählen Sie die **[!UICONTROL AJO Push Tracking Erlebnis-Datensatz]** Datensatz aus der **[!UICONTROL Ereignis-Datensatz]** Liste.
   1. Auswählen **[!UICONTROL In Bibliothek speichern und erstellen]**.
      ![Einstellungen der AJO-Erweiterung](assets/push-tags-ajo.png)

>[!NOTE]
>
>Wenn Sie nicht sehen `AJO Push Tracking Experience Event Dataset` als Option kontaktieren Sie den Kundendienst.
>

### Implementieren von Journey Optimizer in die App

Wie in den vorherigen Lektionen erläutert, bietet die Installation einer mobilen Tag-Erweiterung nur die Konfiguration. Als Nächstes müssen Sie das Messaging SDK installieren und registrieren. Wenn diese Schritte nicht klar sind, überprüfen Sie die [SDKs installieren](install-sdks.md) Abschnitt.

>[!NOTE]
>
>Wenn Sie die [SDKs installieren](install-sdks.md) -Abschnitt, ist das SDK bereits installiert und Sie können diesen Schritt überspringen.
>

1. Stellen Sie in Xcode sicher, dass [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios.git) wird zur Liste der Pakete in Package-Abhängigkeiten hinzugefügt. Siehe [Swift Package Manager](install-sdks.md#swift-package-manager).
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


## Validieren der Einrichtung mit Assurance

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) Abschnitt.
1. Installieren Sie die App auf Ihrem physischen Gerät oder auf dem Simulator.
1. Starten Sie die App mithilfe der durch die Versicherung generierten URL.
1. Wählen Sie in der Assurance-Benutzeroberfläche die Option **[!UICONTROL Konfigurieren]**.
   ![configure click](assets/push-validate-config.png)
1. Wählen Sie die ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) Schaltfläche neben **[!UICONTROL In-App-Nachrichten]**.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
   ![Speichern](assets/assurance-in-app-config.png)
1. Auswählen **[!UICONTROL In-App-Nachrichten]** über die linke Navigation.
1. Wählen Sie die **[!UICONTROL Validierung]** Registerkarte. Vergewissern Sie sich, dass keine Fehler auftreten.

   ![In-App-Validierung](assets/assurance-in-app-validate.png)


## Erstellen einer eigenen In-App-Nachricht

Um eine eigene In-App-Nachricht zu erstellen, müssen Sie eine Kampagne in Journey Optimizer definieren, in der eine In-App-Nachricht auf der Grundlage der Ereignisse Trigger wird. Diese Ereignisse können:

* an Adobe Experience Platform gesendete Daten,
* Core-Tracking-Ereignisse wie Aktionen oder Status oder Erfassung von PII-Daten über die generischen Mobile Core-APIs,
* Anwendungslebenszyklusereignisse wie Start, Installation, Aktualisierung, Schließen oder Absturz,
* Geolocation-Ereignisse, z. B. das Eintreten oder Beenden eines Zielpunkts.

In diesem Tutorial verwenden Sie die generischen und erweiterungsunabhängigen Mobile Core-APIs (siehe [Generische Mobile Core-APIs](https://developer.adobe.com/client-sdks/documentation/mobile-core/#mobile-core-generic-apis)), um die Ereignisverfolgung für Benutzerbildschirme, Aktionen und PII-Daten zu erleichtern. Von diesen APIs generierte Ereignisse werden in den SDK-Ereignis-Hub veröffentlicht und können von Erweiterungen verwendet werden. Der SDK-Ereignis-Hub bietet die Kerndatenstruktur, die mit allen Mobile SDK-Erweiterungen von AEP verknüpft ist, und verwaltet eine Liste registrierter Erweiterungen und interner Module, eine Liste registrierter Ereignis-Listener und eine freigegebene Statusdatenbank.
Der SDK-Ereignis-Hub veröffentlicht und empfängt Ereignisdaten von registrierten Erweiterungen, um die Integration mit Adobe- und Drittanbieterlösungen zu vereinfachen. Wenn beispielsweise die Optimize-Erweiterung installiert ist, werden alle Anforderungen und Interaktionen mit dem Journey Optimizer - Decision Management-Angebotsmodul vom Event Hub verarbeitet.

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche die Option **[!UICONTROL Kampagnen]** über die linke Leiste.
1. Auswählen **[!UICONTROL Kampagne erstellen]**.
1. Im **[!UICONTROL Kampagne erstellen]** screen:
   1. Auswählen **[!UICONTROL In-App-Nachricht]** und wählen Sie eine App-Oberfläche aus dem **[!UICONTROL Anwendungsoberfläche]** beispielsweise Liste **[!DNL Luma Mobile App]**.
   1. Wählen Sie **[!UICONTROL Erstellen]** aus
      ![Kampagneneigenschaften](assets/ajo-campaign-properties.png)
1. Gehen Sie im Bildschirm zur Kampagnendefinition zu **[!UICONTROL Eigenschaften]** eingeben, **[!UICONTROL Name]** beispielsweise für die Kampagne `Luma - In-App Messaging Campaign`und ein **[!UICONTROL Beschreibung]**, beispielsweise `In-app messaging campaign for Luma app`.
   ![Kampagnenname](assets/ajo-campaign-properties-name.png)
1. Nach unten scrollen zu **[!UICONTROL Aktion]** und wählen Sie **[!UICONTROL Inhalt bearbeiten]**.
1. Im **[!UICONTROL In-App-Nachricht]** screen:
   1. Auswählen **[!UICONTROL Modal]** als **[!UICONTROL Nachrichtenlayout]**.
   2. Eingabe `https://luma.enablementadobe.com/content/dam/luma/en/logos/Luma_Logo.png` für die **[!UICONTROL Medien-URL]**.
   3. Geben Sie einen **[!UICONTROL Kopfzeile]**, beispielsweise `Welcome to this Luma In-App Message` und geben Sie einen **[!UICONTROL body]**, beispielsweise `Triggered by pushing that button in the app...`.
   4. Eingabe **[!UICONTROL Verwerfen]** als **[!UICONTROL Schaltfläche 1 Text (primär)]**.
   5. Beachten Sie, wie die Vorschau aktualisiert wird.
   6. Auswählen **[!UICONTROL Aktivieren]**.
      ![In-App-Editor](assets/ajo-in-app-editor.png)
1. Im **[!UICONTROL Überprüfung zur Aktivierung (Luma - In-App Messaging Campaign)]** Bildschirm, auswählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) im **[!UICONTROL Zeitplan]** Kachel.
   ![Zeitplan überprüfen: Zeitplan auswählen](assets/ajo-review-select-schedule.png)
1. Zurück im **[!DNL Luma - In-App Messaging Campaign]** Bildschirm, auswählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Trigger bearbeiten]**.
1. Im **[!UICONTROL Trigger von In-App-Nachrichten]** konfigurieren Sie die Details der Verfolgungsaktion, mit der die In-App-Nachricht Trigger wird:
   1. Entfernen **[!UICONTROL Anwendungsstartereignis]** auswählen ![Schließen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Close_18_N.svg) .
   1. Verwendung ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Bedingung hinzufügen]** wiederholt , um die folgende Logik für **[!UICONTROL Meldung anzeigen, wenn]**.
   1. Klicken Sie auf **[!UICONTROL Fertig]**.
      ![Trigger-Logik](assets/ajo-trigger-logic.png)

   Sie haben eine Verfolgungsaktion definiert, bei der die Variable **[!UICONTROL Aktion]** gleich `in-app` und **[!UICONTROL Kontextdaten]** mit der Aktion ist ein Schlüsselwertpaar `"showMessage" : "true"`.

1. Zurück im **[!DNL Luma - In-App Messaging Campaign]** Bildschirm, auswählen **[!UICONTROL Aktivieren]**.
1. Im **[!UICONTROL Überprüfung zur Aktivierung (Luma - In-App Messaging Campaign)]** Bildschirm, auswählen **[!UICONTROL Aktivieren]**.
1. Sie sehen Ihre **[!DNL Luma - In-App Messaging Campaign]** mit Status **[!UICONTROL Live]** im **[!UICONTROL Kampagnen]** Liste.
   ![Liste der Kampagnen](assets/ajo-campaign-list.png)


## Trigger der In-App-Nachricht

Sie verfügen über alle nötigen Ressourcen, um eine In-App-Nachricht zu senden. Es bleibt jedoch die Möglichkeit, diese In-App-Nachricht in Ihrer App Trigger.

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** im Xcode-Projektnavigator. Suchen Sie die `func sendTrackAction(action: String, data: [String: Any]?)` und fügen Sie den folgenden Code hinzu, der die [`MobileCore.track`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackaction) -Funktion basierend auf den Parametern `action` und `data`.


   ```swift
   // Send trackAction event
   MobileCore.track(action: action, data: data)
   ```

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL ConfigView]** im Xcode-Projektnavigator. Suchen Sie den Code für die Schaltfläche In-App-Nachricht und fügen Sie den folgenden Code hinzu:

   ```swift
   // Setting parameters and calling function to send in-app message
   Task {
       AEPService.shared.sendTrackAction(action: "in-app", data: ["showMessage": "true"])
   }
   ```

## Validieren mit Ihrer App

1. Öffnen Sie Ihre App auf einem Gerät oder im Simulator.

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** Registerkarte.

1. Tippen **[!UICONTROL In-App-Nachricht]**. Die In-App-Nachricht wird in Ihrer App angezeigt.

   <img src="assets/ajo-in-app-message.png" width="300" />


## Validieren der Implementierung in Assurance

Sie können Ihre In-App-Nachrichten in der Assurance-Benutzeroberfläche validieren.

1. Auswählen **[!UICONTROL In-App-Nachrichten]**.
1. Auswählen **[!UICONTROL Ereignisliste]**.
1. Wählen Sie eine **[!UICONTROL Nachricht anzeigen]** eingeben.
1. Inspect das Rohereignis, insbesondere das `html`, das das vollständige Layout und den Inhalt der In-App-Nachricht enthält.
   ![In-App-Bestätigungsnachricht](assets/assurance-in-app-display-message.png)


## Nächste Schritte

Sie sollten jetzt über alle Tools verfügen, um gegebenenfalls In-App-Nachrichten hinzuzufügen.  Beispielsweise die Promotion von Produkten basierend auf bestimmten Interaktionen, die Sie in Ihrer App verfolgen.

>[!SUCCESS]
>
>Sie haben die App für In-App-Nachrichten aktiviert und eine In-App-Nachrichtenkampagne mit Journey Optimizer und der Journey Optimizer-Erweiterung für das Experience Platform Mobile SDK hinzugefügt.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Angebote mit Journey Optimizer anzeigen](journey-optimizer-offers.md)**
