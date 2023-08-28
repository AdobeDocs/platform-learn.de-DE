---
title: In-App-Nachrichten in Adobe Journey Optimizer
description: Erfahren Sie, wie Sie In-App-Nachrichten mit dem Platform Mobile SDK und Adobe Journey Optimizer für eine mobile App erstellen.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
hide: true
source-git-commit: 35b38e7491a3751d21afe4a7b998e5dc2292ba27
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 2%

---

# In-App-Nachrichten in Adobe Journey Optimizer

Erfahren Sie, wie Sie In-App-Nachrichten für mobile Apps mit Platform Mobile SDK und Adobe Journey Optimizer erstellen.

Mit Journey Optimizer können Sie Ihre Journey erstellen und In-App-Nachrichten an Zielgruppen senden. Bevor Sie In-App-Nachrichten mit Journey Optimizer senden, müssen Sie sicherstellen, dass die richtigen Konfigurationen und Integrationen vorhanden sind. Informationen zum Datenfluss von In-App-Nachrichten in Adobe Journey Optimizer finden Sie unter [die Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/in-app/inapp-configuration.html?lang=en).

>[!NOTE]
>
>Diese Lektion ist optional und gilt nur für Adobe Journey Optimizer-Benutzer, die In-App-Nachrichten senden möchten.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.
* Zugriff auf Adobe Journey Optimizer und ausreichende Berechtigungen wie beschrieben [here](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configuration-message/push-config/push-configuration.html?lang=en). Außerdem benötigen Sie ausreichende Berechtigungen für die folgenden Adobe Journey Optimizer-Funktionen.
   * Verwalten Sie eine Kampagne.
* Bezahltes Apple-Entwicklerkonto mit ausreichendem Zugriff zum Erstellen von Zertifikaten, Kennungen und Schlüsseln.
* Physisches iOS-Gerät oder Simulator zum Testen.
* [Registrierte App-ID mit Apple Push Notification Service](journey-optimizer-push.md#register-app-id-with-apn)
* [App-Push-Anmeldedaten zur Datenerfassung hinzugefügt](journey-optimizer-push.md#add-your-app-push-credentials-in-data-collection)
* [Installierte Adobe Journey Optimizer Tags-Erweiterung](journey-optimizer-push.md#install-adobe-journey-optimizer-tags-extension)
* [Implementierte Adobe Journey Optimizer in der App](journey-optimizer-push.md#implement-adobe-journey-optimizer-in-the-app)


## Lernziele

In dieser Lektion werden Sie

* Registrieren Sie die App-ID beim Apple Push Notification Service (APN).
* Erstellen Sie eine **[!UICONTROL App-Oberfläche]** in AJO.
* Aktualisieren Sie Ihre **[!UICONTROL schema]** , um Push-Nachrichten einzuschließen.
* Installieren und konfigurieren Sie die **[!UICONTROL Adobe Journey Optimizer]** Tag-Erweiterung.
* Aktualisieren Sie Ihre App, um die AJO-Tag-Erweiterung einzuschließen.
* Validieren Sie die Einrichtung in &quot;Assurance&quot;.
* Definieren Sie Ihr eigenes Kampagnen- und In-App-Nachrichtenerlebnis in Journey Optimizer.
* Senden Sie Ihre eigene In-App-Nachricht aus der App heraus.


## Validierung mit Versicherung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) Abschnitt.
1. Installieren Sie die App auf Ihrem physischen Gerät oder auf dem Simulator.
1. Starten Sie die App mithilfe der durch die Versicherung generierten URL.
1. Wählen Sie in der Assurance-Benutzeroberfläche die Option **[!UICONTROL Konfigurieren]**.
   ![configure click](assets/push-validate-config.png)
1. Wählen Sie die ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) Schaltfläche neben **[!UICONTROL In-App-Nachrichten]**.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
   ![Speichern](assets/assurance-in-app-config.png)
1. Auswählen **[!UICONTROL In-App-Nachrichten]** über die linke Navigation.
1. Wählen Sie die **[!UICONTROL Validierung]** Registerkarte.
1. Vergewissern Sie sich, dass keine Fehler auftreten.
   ![In-App-Validierung](assets/assurance-in-app-validate.png)


## Erstellen einer eigenen In-App-Nachricht

Um eine eigene In-App-Nachricht zu erstellen, müssen Sie eine Kampagne in Journey Optimizer definieren, in der eine In-App-Nachricht auf der Grundlage der Ereignisse Trigger wird. Diese Ereignisse können:

* an Adobe Experience Platform gesendete Daten,
* Core-Tracking-Ereignisse wie Aktionen oder Status oder Erfassung von PII-Daten über die generischen Mobile Core-APIs,
* Anwendungslebenszyklusereignisse wie Start, Installation, Aktualisierung, Schließen oder Absturz,
* Geolocation-Ereignisse, z. B. das Eintreten oder Beenden eines Zielpunkts.

In diesem Tutorial verwenden Sie die generischen und erweiterungsunabhängigen Mobile Core-APIs, um die Ereignisverfolgung für Benutzerbildschirme, Aktionen und PII-Daten zu erleichtern. Von diesen APIs generierte Ereignisse werden in den SDK-Ereignis-Hub veröffentlicht und können von Erweiterungen verwendet werden. Wenn beispielsweise die Analytics-Erweiterung installiert ist, werden alle Benutzeraktionen und App Screens-Ereignisdaten an die entsprechenden Analytics-Reporting-Endpunkte gesendet.

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche die Option **[!UICONTROL Kampagnen]** über die linke Leiste.
1. Auswählen **[!UICONTROL Kampagne erstellen]**.
1. Im **[!UICONTROL Kampagne erstellen]** screen:
   1. Auswählen **[!UICONTROL In-App-Nachricht]** und wählen **[!UICONTROL Luma Mobile App]** aus dem **[!UICONTROL Anwendungsoberfläche]** Liste.
   1. Wählen Sie **[!UICONTROL Erstellen]** aus
      ![Kampagneneigenschaften](assets/ajo-campaign-properties.png)
1. Gehen Sie im Bildschirm zur Kampagnendefinition zu **[!UICONTROL Eigenschaften]** eingeben, **[!UICONTROL Name]** beispielsweise für die Kampagne `Luma - In-App Messaging Campaign`und ein **[!UICONTROL Beschreibung]**, beispielsweise `In-app messaging campaign for Luma app`.
   ![Kampagnenname](assets/ajo-campaign-properties-name.png)
1. Nach unten scrollen zu **[!UICONTROL Aktion]** und wählen Sie **[!UICONTROL Inhalt bearbeiten]**.
1. Im **[!UICONTROL In-App-Nachricht]** screen:
   1. Auswählen **[!UICONTROL Modal]** als **[!UICONTROL Nachrichtenlayout]**.
   2. Eingabe `https://luma.enablementadobe.com/content/dam/luma/en/logos/Luma_Logo.png` für **[!UICONTROL Medien-URL]**.
   3. Geben Sie einen **[!UICONTROL Kopfzeile]**, beispielsweise `Welcome to this Luma In-App Message` und geben Sie einen **[!UICONTROL body]**, beispielsweise `Triggered by pushing that button in the app...`.
   4. Eingabe **[!UICONTROL Verwerfen]** als **[!UICONTROL Schaltfläche 1 Text (primär)]**.
   5. Beachten Sie, wie die Vorschau aktualisiert wird.
   6. Auswählen **[!UICONTROL Aktivieren]**.
      ![In-App-Editor](assets/ajo-in-app-editor.png)
1. Im **[!UICONTROL Überprüfung zur Aktivierung (Luma - In-App Messaging Campaign)]** Bildschirm, auswählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) im **[!UICONTROL Zeitplan]** Kachel.
   ![Zeitplan überprüfen: Zeitplan auswählen](assets/ajo-review-select-schedule.png)
1. Zurück im **[!UICONTROL Luma - In-App-Nachrichtenkampagne]** Bildschirm, auswählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Trigger bearbeiten]**.
1. Im **[!UICONTROL Trigger von In-App-Nachrichten]** konfigurieren Sie die Details der Verfolgungsaktion, mit der die In-App-Nachricht Trigger wird:
   1. Entfernen **[!UICONTROL Anwendungsstartereignis]** auswählen ![Schließen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Close_18_N.svg) .
   1. Verwendung ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Bedingung hinzufügen]** wiederholt , um die folgende Logik für **[!UICONTROL Meldung anzeigen, wenn]**.
   1. Klicken Sie auf **[!UICONTROL Fertig]**.
      ![Trigger-Logik](assets/ajo-trigger-logic.png)

   Sie haben eine Verfolgungsaktion definiert, bei der die Variable **[!UICONTROL Aktion]** gleich `in-app` und **[!UICONTROL Kontextdaten]** mit der Aktion ist ein Schlüsselwertpaar `"showMessage" : "true"`.

1. Zurück im **[!UICONTROL Luma - In-App-Nachrichtenkampagne]** Bildschirm, auswählen **[!UICONTROL Aktivieren]**.
1. Im **[!UICONTROL Überprüfung zur Aktivierung (Luma - In-App Messaging Campaign)]** Bildschirm, auswählen **[!UICONTROL Aktivieren]**.
1. Sie sehen Ihre **[!UICONTROL Luma - In-App-Nachrichtenkampagne]** mit Status **[!UICONTROL Live]** im **[!UICONTROL Kampagnen]** Liste.
   ![Liste der Kampagnen](assets/ajo-campaign-list.png)


## In-App-Nachricht auslösen

Sie verfügen über alle nötigen Ressourcen, um eine In-App-Nachricht zu senden. Es bleibt nur noch, wie Sie diese In-App-Nachricht in Ihren Code Trigger haben.

1. Navigieren Sie zu Luma > Luma > Utils > MobileSDK im Xcode-Projekt-Navigator und suchen Sie nach der `func sendTrackAction(action: String, data: [String: Any]?)` und fügen Sie den folgenden Code hinzu, der die `MobileCore.track` -Funktion basierend auf den Parametern `action` und `data`.


   ```swift
   // send trackAction event
   MobileCore.track(action: action, data: data)
   ```

1. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Ansichten]** > **[!UICONTROL Allgemein]** > **[!UICONTROL ConfigView]** im Xcode-Projektnavigator. Suchen Sie den Code für die Schaltfläche In-App-Nachricht und fügen Sie den folgenden Code hinzu:

   ```swift
   Task {
       AEPService.shared.sendTrackAction(action: "in-app", data: ["showMessage": "true"])
   }
   ```

## Validieren mit Ihrer App

1. Öffnen Sie Ihre App auf einem Gerät oder im Simulator.

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** Registerkarte.

1. Tippen **[!UICONTROL In-App-Nachricht]**. Die In-App-Nachricht wird in Ihrer App angezeigt.

   <img src="assets/ajo-in-app-message.png" width="300" />


## Validierung in Assurance

Sie können Ihre In-App-Nachrichten in der Assurance-Benutzeroberfläche validieren.

1. Auswählen **[!UICONTROL In-App-Nachrichten]**.
1. Auswählen **[!UICONTROL Ereignisliste]**.
1. Wählen Sie eine **[!UICONTROL Nachricht anzeigen]** eingeben.
1. Inspect das Rohereignis, insbesondere das `html`, das das vollständige Layout und den Inhalt der In-App-Nachricht enthält.
   ![In-App-Bestätigungsnachricht](assets/assurance-in-app-display-message.png)


## Implementieren in Ihre App

Sie sollten jetzt über alle Tools verfügen, um gegebenenfalls Push-Benachrichtigungen zur Luma-App hinzuzufügen. Beispielsweise beim Einladen des Benutzers bei der Anmeldung bei der App oder beim Annähern an eine bestimmte Geolocation.

>[!SUCCESS]
>
>Sie haben die App jetzt für In-App-Nachrichten aktiviert und eine In-App-Nachrichtenkampagne mit Adobe Journey Optimizer und der Adobe Journey Optimizer-Erweiterung für das Adobe Experience Platform Mobile SDK hinzugefügt.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Angebote mit Journey Optimizer anzeigen](journey-optimizer-offers.md)**
