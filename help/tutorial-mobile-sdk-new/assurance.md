---
title: Einrichten der Sicherheit
description: Erfahren Sie, wie Sie die Assurance-Erweiterung in eine mobile App implementieren.
feature: Mobile SDK,Assurance
hide: true
source-git-commit: b3cf168fc9b20ea78df0f8863a6395e9a45ed832
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 5%

---

# Assurance

Erfahren Sie, wie Sie Adobe Experience Platform Assurance in einer Mobile App einrichten.

Assurance, formell als Project Griffon bekannt, soll Ihnen dabei helfen, zu untersuchen, zu testen, zu simulieren und zu überprüfen, wie Sie Daten erfassen oder Erlebnisse in Ihrer mobilen App bereitstellen.

Mithilfe von &quot;Assurance&quot;können Sie unformatierte SDK-Ereignisse überprüfen, die vom Adobe Experience Platform Mobile SDK generiert wurden. Alle vom SDK erfassten Ereignisse stehen zur Überprüfung zur Verfügung. SDK-Ereignisse werden in einer Listenansicht geladen, sortiert nach Zeit. Jedes Ereignis verfügt über eine detaillierte Ansicht, die weitere Details enthält. Zusätzliche Ansichten zum Durchsuchen von SDK-Konfigurationen, Datenelementen, freigegebenen Status und SDK-Erweiterungsversionen werden ebenfalls bereitgestellt. Weitere Informationen zum [Assurance](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html?lang=de) in der Produktdokumentation.


## Voraussetzungen

* Richten Sie die App erfolgreich mit installierten und konfigurierten SDKs ein.

## Lernziele

In dieser Lektion werden Sie:

* Vergewissern Sie sich, dass Ihr Unternehmen Zugriff hat (und fordern Sie ihn an, falls nicht möglich).
* Richten Sie Ihre Basis-URL ein.
* Fügen Sie erforderlichen iOS-spezifischen Code hinzu.
* Stellen Sie eine Verbindung zu einer Sitzung her.

## Zugriff bestätigen

Vergewissern Sie sich, dass Ihr Unternehmen Zugriff auf die Zertifizierung hat. Als Benutzer sollten Sie zum Profil für Adobe Experience Platform hinzugefügt werden. Siehe [Benutzerzugriff](https://experienceleague.adobe.com/docs/experience-platform/assurance/user-access.html?lang=en) im Zuverlässigkeitshandbuch für weitere Informationen.

## Implementierung

Neben der allgemeinen [SDK-Installation](install-sdks.md)Wenn Sie in der vorherigen Lektion abgeschlossen haben, erfordert iOS auch den folgenden Zusatz, um die Assurance-Sitzung für Ihre App zu starten.

1. Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL SceneDelegate]** im Projektnavigator Ihres Xcode-Codes ein.

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

## Signing

Bevor Sie die Anwendung zum ersten Mal in Xcode ausführen, müssen Sie die Signatur aktualisieren.

1. Öffnen Sie das Projekt  in Xcode.
1. Auswählen **[!UICONTROL Luma]** im Projekt-Navigator.
1. Wählen Sie die **[!UICONTROL Luma]** Zielgruppe.
1. Wählen Sie die **Signieren und Funktionen** Registerkarte.
1. Konfigurieren **[!UICONTROL Automatische Verwaltungssignatur]**, **[!UICONTROL Team]**, und **[!UICONTROL Bundle-Kennung]** oder verwenden Sie Ihre spezifischen Apple-Entwicklungsbereitstellungsdetails.

   ![Xcode-Signaturfunktionen](assets/xcode-signing-capabilities.png){zoomable=&quot;yes&quot;}

## Einrichten einer Basis-URL

1. Wechseln Sie zu Ihrem Projekt in Xcode.
1. Auswählen **[!UICONTROL Luma]** im Projekt-Navigator.
1. Wählen Sie die **[!UICONTROL Luma]** Zielgruppe.
1. Wählen Sie die **Info** Registerkarte.
1. Um eine Basis-URL hinzuzufügen, scrollen Sie nach unten zu **URL-Typen** und wählen Sie die **+** Schaltfläche.
1. Satz **Kennung** zur Bundle-ID, die Sie in der [Signing](#signing) (Beispiel `com.adobe.luma.tutorial.swiftui`) und legen Sie eine **URL-Schemata**, beispielsweise `lumatutorialswiftui`.

   ![Sicherungs-URL](assets/assurance-url-type.png)

Weitere Informationen zu URL-Schemata in iOS finden Sie unter [Dokumentation zu Apple](https://developer.apple.com/documentation/xcode/defining-a-custom-url-scheme-for-your-app){target="_blank"}.

Assurance funktioniert durch Öffnen einer URL, entweder über einen Browser oder QR-Code. Diese URL beginnt mit der Basis-URL, die die App öffnet und zusätzliche Parameter enthält. Diese eindeutigen Parameter werden verwendet, um die Sitzung zu verbinden.


## Herstellen einer Verbindung zu einer Sitzung

1. Führen Sie die Anwendung im Simulator oder auf einem angeschlossenen physischen Gerät aus.
1. Auswählen **[!UICONTROL Assurance]** über die linke Leiste in der Datenerfassungs-Benutzeroberfläche.
1. Auswählen **[!UICONTROL Sitzung erstellen]**.
1. Auswählen **[!UICONTROL Starten]**.
1. Stellen Sie eine **[!UICONTROL Sitzungsname]** wie `Luma Mobile App Session` und **[!UICONTROL Basis-URL]**; dies sind die URL-Schemas, die Sie in Xcode eingegeben haben, gefolgt von `://`. Beispiel: `lumatutorialswiftui://`.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
   ![Sicherheitssitzung erstellen](assets/assurance-create-session.png)
1. Im **[!UICONTROL Neue Sitzung erstellen]** modaler Dialog:

   Wenn Sie ein physisches Gerät verwenden:

   * Auswählen **[!UICONTROL QR-Code scannen]**. Verwenden Sie Ihre Kamera auf Ihrem physischen Gerät, um den QR-Code zu scannen, und tippen Sie auf den Link, um die App zu öffnen.

     ![Zuverlässigkeitsqa-Code](assets/assurance-qr-code.png)

   Wenn Sie einen Simulator verwenden:

   1. Auswählen **[!UICONTROL Link kopieren]**.
   1. Kopieren Sie den Deep-Link mit ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)  und verwenden Sie den Deep-Link, um die App mit Safari im Simulator zu öffnen.
      ![Link zum Kopieren der Assets](assets/assurance-copy-link.png)

1. Wenn die App geladen wird, wird Ihnen ein modales Dialogfeld angezeigt, in dem Sie aufgefordert werden, die in Schritt 7 dargestellte PIN einzugeben.

   <img src="assets/assurance-enter-pin.png" width="300">

   Geben Sie die PIN ein und wählen Sie **[!UICONTROL Verbinden]**.


1. Wenn die Verbindung erfolgreich hergestellt wurde, sehen Sie Folgendes:
   * Ein Zuverlässigkeitssymbol, das über der App angezeigt wird.

     <img src="assets/assurance-modal.png" width="300">

   * Experience Cloud-Updates in der Assurance-Benutzeroberfläche, die Folgendes zeigen:

      1. Erlebnisereignisse aus der App.
      1. Details eines ausgewählten Ereignisses.
      1. Gerät und Timeline.

         ![Zuverlässigkeitsereignisse](assets/assurance-events.png)

Wenn Sie auf Herausforderungen stoßen, lesen Sie bitte die [technisch](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/){target="_blank"} and [general documentation](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html?lang=de){target="_blank"}.

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass sie für den Rest des Tutorials Assurance verwendet.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)


Weiter: **[Einverständnis](consent.md)**
