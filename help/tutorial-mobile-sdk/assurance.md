---
title: Einrichten von Assurance für Platform Mobile SDK-Implementierungen
description: Erfahren Sie, wie Sie die Assurance-Erweiterung in eine mobile App implementieren.
feature: Mobile SDK,Assurance
jira: KT-14628
exl-id: e15774b2-2f52-400f-9313-bb4338a88918
source-git-commit: 576f85eda6e5888b9eafa15a705a99c3a70fed07
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 1%

---

# Einrichten der Sicherheit

Erfahren Sie, wie Sie Adobe Experience Platform Assurance in einer Mobile App einrichten.

Assurance, formell als Project Griffon bekannt, soll Ihnen dabei helfen, zu untersuchen, zu testen, zu simulieren und zu überprüfen, wie Sie Daten erfassen oder Erlebnisse in Ihrer mobilen App bereitstellen.

Mithilfe von &quot;Assurance&quot;können Sie unformatierte SDK-Ereignisse überprüfen, die vom Adobe Experience Platform Mobile SDK generiert wurden. Alle vom SDK erfassten Ereignisse stehen zur Überprüfung zur Verfügung. SDK-Ereignisse werden in einer Listenansicht geladen, sortiert nach Zeit. Jedes Ereignis verfügt über eine detaillierte Ansicht, die weitere Details enthält. Zusätzliche Ansichten zum Durchsuchen von SDK-Konfigurationen, Datenelementen, freigegebenen Status und SDK-Erweiterungsversionen werden ebenfalls bereitgestellt. Weitere Informationen zur [Zuverlässigkeit](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html?lang=de) finden Sie in der Produktdokumentation.


## Voraussetzungen

* Richten Sie die App erfolgreich mit installierten und konfigurierten SDKs ein.

## Lernziele

In dieser Lektion werden Sie:

* Vergewissern Sie sich, dass Ihr Unternehmen Zugriff hat (und fordern Sie ihn an, falls nicht möglich).
* Richten Sie Ihre Basis-URL ein.
* Fügen Sie erforderlichen iOS-spezifischen Code hinzu.
* Stellen Sie eine Verbindung zu einer Sitzung her.

## Zugriff bestätigen

Vergewissern Sie sich, dass Ihr Unternehmen Zugriff auf die Zertifizierung hat. Als Benutzer sollten Sie zum Profil für Adobe Experience Platform hinzugefügt werden. Weitere Informationen finden Sie unter [Benutzerzugriff](https://experienceleague.adobe.com/docs/experience-platform/assurance/user-access.html?lang=en) im Zuverlässigkeitshandbuch.

## Implementierung

Zusätzlich zur allgemeinen [SDK-Installation](install-sdks.md), die Sie in der vorherigen Lektion abgeschlossen haben, erfordert iOS auch die folgende Ergänzung, um die Assurance-Sitzung für Ihre App zu starten.

1. Navigieren Sie im Projektnavigator Ihres Xcode zu **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL SceneDelegate]** .

1. Fügen Sie folgenden Code zu `func scene(_ scene: UIScene, openURLContexts URLContexts: Set<UIOpenURLContext>` hinzu:

   ```swift
   // Called when the app in background is opened with a deep link.
   if let deepLinkURL = URLContexts.first?.url {
       // Start the Assurance session
       Assurance.startSession(url: deepLinkURL)
   }
   ```

   Dieser Code startet eine Sicherheitssitzung, wenn sich die App im Hintergrund befindet und über einen Deep-Link geöffnet wird.

Weitere Informationen finden Sie [hier](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/api-reference/){target="_blank"}.



## Bundle-Kennung definieren

Sie müssen eine eindeutige Bundle-ID für Ihre App angeben.

1. Öffnen Sie das Projekt in Xcode.
1. Wählen Sie im Projektnavigator **[!DNL Luma]** aus.
1. Wählen Sie das Ziel **[!DNL Luma]** aus.
1. Wählen Sie die Registerkarte **Signing &amp; Capabilities** aus.
1. Definieren Sie eine **[!UICONTROL Bundle-Kennung]**.

   >[!IMPORTANT]
   >
   >Stellen Sie sicher, dass Sie eine _eindeutige_ Bundle-ID verwenden und die `com.adobe.luma.tutorial.swiftui` -Bundle-ID ersetzen, da jede Bundle-ID eindeutig sein muss. Normalerweise verwenden Sie ein Reverse-DNS-Format für Bundle-ID-Zeichenfolgen, z. B. `com.organization.brand.uniqueidentifier`. Die abgeschlossene Version dieses Tutorials verwendet beispielsweise `com.adobe.luma.tutorial.swiftui`.


   ![Xcode-Signaturfunktionen](assets/xcode-signing-capabilities.png){zoomable="yes"}


## Einrichten einer Basis-URL

1. Wechseln Sie zu Ihrem Projekt in Xcode.
1. Wählen Sie im Projektnavigator **[!DNL Luma]** aus.
1. Wählen Sie das Ziel **[!DNL Luma]** aus.
1. Wählen Sie die Registerkarte **Info** aus.
1. Um eine Basis-URL hinzuzufügen, scrollen Sie nach unten zu **URL-Typen** und wählen Sie die Schaltfläche **+** aus.
1. Setzen Sie **Kennung** auf die Bundle-Kennung Ihrer Wahl und legen Sie ein **URL-Schema** Ihrer Wahl fest.

   ![Sicherungs-URL](assets/assurance-url-type.png)

   >[!IMPORTANT]
   >
   >Stellen Sie sicher, dass Sie eine _eindeutige_ Bundle-ID verwenden und die `com.adobe.luma.tutorial.swiftui` -Bundle-ID ersetzen, da jede Bundle-ID eindeutig sein muss. Normalerweise verwenden Sie ein Reverse-DNS-Format für Bundle-ID-Zeichenfolgen, z. B. `com.organization.brand.uniqueidentifier`. Sie können dieselbe Bundle-Kennung verwenden, die Sie unter [Bundle-ID definieren](#define-bundle-identifier) verwendet haben.<br/>Verwenden Sie auf ähnliche Weise ein eindeutiges URL-Schema und ersetzen Sie das bereits bereitgestellte `lumatutorialswiftui` durch Ihr eindeutiges URL-Schema.

Weitere Informationen zu URL-Schemata in iOS finden Sie in der Dokumentation zu [Apple](https://developer.apple.com/documentation/xcode/defining-a-custom-url-scheme-for-your-app){target="_blank"} .

Assurance funktioniert durch Öffnen einer URL, entweder über einen Browser oder QR-Code. Diese URL beginnt mit der Basis-URL, die die App öffnet und zusätzliche Parameter enthält. Diese eindeutigen Parameter werden verwendet, um die Sitzung zu verbinden.


## Herstellen einer Verbindung zu einer Sitzung

In Xcode:

1. Erstellen Sie die App im Simulator oder auf einem physischen Gerät aus Xcode neu und führen Sie sie mit ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg) aus.

   >[!TIP]
   >
   >Optional können Sie Ihren Build &quot;bereinigen&quot;, insbesondere wenn unerwartete Ergebnisse angezeigt werden. Wählen Sie dazu **[!UICONTROL Ordner bereinigen...]** aus dem Menü Xcode **[!UICONTROL Produkt]** aus.


1. Wählen Sie im Dialogfeld **[!UICONTROL Zulassen, dass &quot;Luma App&quot;Ihre Position verwendet&quot;]** die Option **[!UICONTROL Während Verwendung der App zulassen]**.

   <img src="assets/geolocation-permissions.png" width="300">

1. Wählen Sie im Dialogfeld **[!UICONTROL &quot;Luma App&quot;Möchten Sie Benachrichtigungen senden]** die Option **[!UICONTROL Zulassen]**.

   <img src="assets/notification-permissions.png" width="300">

1. Wählen Sie **[!UICONTROL Fortfahren...]** aus, damit die App Ihre Aktivität verfolgen kann.

   <img src="assets/tracking-continue.png" width="300">

1. Wählen Sie im Dialogfeld **[!UICONTROL Zulassen, dass &quot;Luma App&quot;Ihre Aktivität über die Apps und Websites anderer Unternehmen hinweg verfolgt]**, die Option **[!UICONTROL Zulassen]** aus.

   <img src="assets/tracking-allow.png" width="300">


In Ihrem Browser:

1. Rufen Sie die Benutzeroberfläche für die Datenerfassung auf.
1. Wählen Sie in der linken Leiste die Option **[!UICONTROL Versicherung]** aus.
1. Wählen Sie **[!UICONTROL Sitzung erstellen]** aus.
1. Wählen Sie **[!UICONTROL Start]** aus.
1. Geben Sie einen **[!UICONTROL Sitzungsnamen]** wie `Luma Mobile App Session` und die **[!UICONTROL Basis-URL]** an, bei denen es sich um die URL-Schemas handelt, die Sie in Xcode eingegeben haben, gefolgt von `://` Beispiel: `lumatutorialswiftui://`
1. Klicken Sie auf **[!UICONTROL Weiter]**.
   ![assurance create session](assets/assurance-create-session.png)
1. Im modalen Dialogfeld **[!UICONTROL Neue Sitzung erstellen]** :

   Wenn Sie ein physisches Gerät verwenden:

   * Wählen Sie **[!UICONTROL QR-Code scannen]** aus. Um die App zu öffnen, verwenden Sie die Kamera auf Ihrem physischen Gerät, um den QR-Code zu scannen, und tippen Sie auf den Link.

     ![assurance qa code](assets/assurance-qr-code.png)

   Wenn Sie einen Simulator verwenden:

   1. Wählen Sie **[!UICONTROL Link kopieren]** aus.
   1. Kopieren Sie den Deep-Link mit ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) und verwenden Sie den Deep-Link, um die App mit Safari im Simulator zu öffnen.
      ![Link zum Kopieren der Garantie](assets/assurance-copy-link.png)

1. Wenn die App geladen wird, wird Ihnen ein modales Dialogfeld angezeigt, in dem Sie aufgefordert werden, die in Schritt 7 dargestellte PIN einzugeben.

   <img src="assets/assurance-enter-pin.png" width="300">

   Geben Sie die PIN ein und wählen Sie **[!UICONTROL Verbinden]** aus.


1. Wenn die Verbindung erfolgreich hergestellt wurde, sehen Sie Folgendes:
   * Ein Zuverlässigkeitssymbol, das über der App angezeigt wird.

     <img src="assets/assurance-modal.png" width="300">

   * Experience Cloud-Updates in der Assurance-Benutzeroberfläche, die Folgendes zeigen:

      1. Erlebnisereignisse aus der App.
      1. Details eines ausgewählten Ereignisses.
      1. Gerät und Timeline.

         ![Zuverlässigkeitsereignisse](assets/assurance-events.png)

Wenn Sie auf Herausforderungen stoßen, lesen Sie die [technischen](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/){target="_blank"} und die [allgemeinen Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html?lang=de){target="_blank"}.


## Überprüfen von Erweiterungen

So überprüfen Sie, ob Ihre App die aktuellsten Erweiterungen verwendet:

1. Wählen Sie **[!UICONTROL Konfigurieren]** aus.

1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) für ![123](https://spectrum.adobe.com/static/icons/workflow_18/Smock_123_18_N.svg) **[!UICONTROL Erweiterungsversionen]**.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Konfigurieren von Erweiterungsversionen](assets/assurance-configure-extension-versions.png)

1. Wählen Sie ![123](https://spectrum.adobe.com/static/icons/workflow_18/Smock_123_18_N.svg) **[!UICONTROL Erweiterungsversionen]** aus, um einen Überblick über die neuesten verfügbaren Erweiterungen und die in Ihrer Version der App verwendeten Erweiterungen anzuzeigen.

   ![Erweiterungsversionen](assets/assurance-extension-versions.png)

1. Um Ihre Erweiterungsversionen zu aktualisieren (z. B. **[!UICONTROL Messaging]** und **[!UICONTROL Optimize]**), wählen Sie das Paket (Erweiterung) aus **[!UICONTROL Paketabhängigkeiten]** (z. B. **[!UICONTROL APMessaging]**) und wählen Sie im Kontextmenü die Option **[!UICONTROL Paket aktualisieren]** aus. Xcode aktualisiert die Paketabhängigkeiten.


>[!NOTE]
>
>Nachdem Sie Ihre Erweiterungen (Pakete) in Xcode aktualisiert haben, schließen und löschen Sie die aktuelle Sitzung und wiederholen Sie alle Schritte aus [Herstellen einer Verbindung zu einer Sitzung](#connecting-to-a-session) und [Überprüfen von Erweiterungen](#verify-extensions), um sicherzustellen, dass die Zuverlässigkeitsberichte die richtigen Erweiterungen in einer neuen Zuverlässigkeitssitzung enthalten.





>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass sie für den Rest des Tutorials Assurance verwendet.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu künftigen Inhalten teilen möchten, teilen Sie diese auf diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.


Weiter: **[Einverständnis implementieren](consent.md)**
