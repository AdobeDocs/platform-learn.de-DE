---
title: WebSDK-Implementierungen mit Experience Platform Debugger validieren
description: Erfahren Sie, wie Sie Ihre Platform Web SDK-Implementierung mit Adobe Experience Platform Debugger validieren. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Web SDK,Tags,Debugger
exl-id: 150bb1b1-4523-4b44-bd4e-6cabc468fc04
source-git-commit: e2594d3b30897001ce6cb2f6908d75d0154015eb
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 6%

---

# WebSDK-Implementierungen mit Experience Platform Debugger validieren

Erfahren Sie, wie Sie Ihre Platform Web SDK-Implementierung mit Adobe Experience Platform Debugger validieren.

Der Experience Platform Debugger ist eine Erweiterung, die für Chrome- und Firefox-Browser verfügbar ist und Ihnen dabei hilft, die auf Ihren Webseiten implementierte Adobe-Technologie zu sehen. Laden Sie die Version für Ihren bevorzugten Browser herunter:

* [Firefox-Erweiterung](https://addons.mozilla.org/de/firefox/addon/adobe-experience-platform-dbg/)
* [Chrome-Erweiterung](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

Wenn Sie den Debugger noch nie verwendet haben und dieser sich vom älteren Adobe Experience Cloud Debugger unterscheidet, sollten Sie sich dieses fünfminütige Übersichtsvideo ansehen:

>[!VIDEO](https://video.tv.adobe.com/v/32156?learn=on)

In dieser Lektion verwenden Sie die [Adobe Experience Platform Debugger-Erweiterung](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) , um die Tag-Eigenschaft zu ersetzen, die auf der fest codiert ist. [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) mit Ihrer eigenen Eigenschaft.

Diese Technik wird als Umgebungswechsel bezeichnet und ist später hilfreich, wenn Sie mit Tags auf Ihrer eigenen Website arbeiten. Sie können Ihre Produktions-Website in Ihren Browser laden, jedoch mit Ihrem *development* Tagumgebung. Mit dieser Funktion können Sie sicher Änderungen an Tags vornehmen und überprüfen - unabhängig von Ihren normalen Codeversionen. Schließlich ist diese Trennung der Marketing-Tag-Versionen von Ihren normalen Codeversionen einer der Hauptgründe, warum Kunden Tags überhaupt verwenden!

## Lernziele

Am Ende dieser Lektion können Sie den Debugger für Folgendes verwenden:

* Alternative Tag-Bibliothek laden
* Überprüfen Sie, ob das XDM-Objekt Daten wie erwartet erfasst und sendet.

## Voraussetzungen

Sie kennen Datenerfassungs-Tags und die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} und haben die folgenden vorherigen Lektionen im Tutorial abgeschlossen:

* [Konfigurieren von Berechtigungen](configure-permissions.md)
* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)
* [Erstellen von Datenelementen](create-data-elements.md)
* [Tag-Regel erstellen](create-tag-rule.md)


## Alternative Tag-Bibliotheken mit Debugger laden

Dieses Tutorial verwendet eine öffentlich gehostete Version des [Demowebsite für Luma](https://luma.enablementadobe.com/content/luma/us/en.html). Öffnen Sie die Homepage und markieren Sie sie mit einem Lesezeichen.

![Startseite von Luma](assets/validate-luma-site.png)

Der Experience Platform Debugger verfügt über eine coole Funktion, mit der Sie eine vorhandene Tag-Bibliothek durch eine andere ersetzen können. Diese Technik ist für die Validierung nützlich und ermöglicht es uns, viele Implementierungsschritte in diesem Tutorial zu überspringen.

1. Stellen Sie sicher, dass die Site &quot;Luma&quot;geöffnet ist, und wählen Sie das Symbol für die Experience Platform Debugger-Erweiterung aus.
1. Der Debugger wird geöffnet und zeigt einige Details zur hartcodierten Implementierung an, die nicht mit diesem Tutorial in Zusammenhang steht (Sie müssen die Site &quot;Luma&quot;möglicherweise neu laden, nachdem Sie den Debugger geöffnet haben).
1. Vergewissern Sie sich, dass der Debugger &quot;**[!UICONTROL Verbunden mit Luma]**&quot;, wie unten dargestellt, und wählen Sie dann &quot;**[!UICONTROL lock]**&quot;, um den Debugger mit der Site &quot;Luma&quot;zu sperren.
1. Wählen Sie die **[!UICONTROL Anmelden]** und melden Sie sich mit Ihrer Adobe ID bei Adobe Experience Cloud an.
1. Gehen Sie jetzt zu **[!UICONTROL Experience Platform-Tags]** in der linken Navigation

   ![Debugger-Tag-Bildschirm](assets/validate-launch-screen.png)

1. Wählen Sie die **[!UICONTROL Konfiguration]** tab
1. Rechts neben dem Ort, an dem Sie die **[!UICONTROL Seiten-Einbettungscodes]**, öffnen Sie die **[!UICONTROL Aktionen]** und wählen Sie **[!UICONTROL Ersetzen]**

   ![Aktionen auswählen > Ersetzen](assets/validate-switch-environment.png)

1. Da Sie authentifiziert sind, ruft der Debugger Ihre verfügbaren Tag-Eigenschaften und -Umgebungen ab. Wählen Sie `Web SDK Course` property
1. Wählen Sie `Development` Umgebung
1. Wählen Sie die **[!UICONTROL Anwenden]** button

   ![Auswählen der alternativen Tag-Eigenschaft](assets/validate-switch-selection.png)

1. Die Luma-Website wird jetzt neu geladen _mit der Tag-Eigenschaft_.

   ![Tag-Eigenschaft ersetzt](assets/validate-switch-success.png)

Während Sie das Tutorial fortsetzen, verwenden Sie diese Methode, um die Site &quot;Luma&quot;Ihrer eigenen Tag-Eigenschaft zuzuordnen und Ihre Platform Web SDK-Implementierung zu validieren. Wenn Sie mit der Verwendung von Tags auf Ihrer Produktions-Website beginnen, können Sie dieselbe Methode verwenden, um Änderungen zu validieren.

## Überprüfen der Implementierung im Experience Platform Debugger

Sie können den Debugger verwenden, um Ihre Platform Web SDK-Implementierung zu validieren und die an Platform Edge Network gesendeten Daten anzuzeigen:

1. Navigieren Sie zu **[!UICONTROL Zusammenfassung]** in der linken Navigation, um die Details Ihrer Tag-Eigenschaft anzuzeigen

   ![Registerkarte „Zusammenfassung“](assets/validate-summary.png)

1. Gehen Sie jetzt zu **[!UICONTROL Experience Platform Web SDK]** in der linken Navigation, um die **[!UICONTROL Netzwerkanforderungen]**
1. Öffnen Sie die **[!UICONTROL events]** Zeile (keine Sorge, wenn dieser Screenshot mehr Anforderungen als Ihre anzeigt, enthält er Anforderungen aus zukünftigen Lektionen und Sie können ihn vorerst ignorieren)

   ![Adobe Experience Platform Web SDK-Anfrage](assets/validate-aep-screen.png)

1. Beachten Sie, dass die `web.webpagedetails.pageView` Ereignistyp, den wir in unserer [!UICONTROL Ereignis senden] und anderen nativen Variablen, die der `AEP Web SDK ExperienceEvent Mixin` format

   ![Ereignisdetails](assets/validate-event-pageViews.png)

1. Scrollen Sie nach unten zum `web` -Objekt, wählen Sie aus, um es zu öffnen und die `webPageDetails.name`, `webPageDetails.server`, und `webPageDetails.siteSection`. Sie sollten mit den entsprechenden digitalen Datenschichtvariablen auf der Homepage übereinstimmen.

   ![Registerkarte „Netzwerk“](assets/validate-xdm-content.png)

Sie können auch die Identitätszuordnungsdetails überprüfen:

1. Melden Sie auf der Site „Luma“ sich mit den folgenden Anmeldeinformationen an: `test@adobe.com`/`test`

1. Kehren Sie zur [Startseite „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html) zurück.

1. Öffnen Sie die **[!UICONTROL Experience Platform Web SDK]** im linken Navigationsbereich

   ![Web SDK in Debugger](assets/identity-debugger-websdk-dark.png)

1. Wählen Sie die **[!UICONTROL events]** Zeile zum Öffnen von Details in einem Popup-Fenster

   ![Web SDK in Debugger](assets/identity-deugger-websdk-event-dark.png)

1. Suchen Sie nach **identityMap** innerhalb des Popup-Fensters. Hier sollten Sie sehen `lumaCrmId` mit drei Schlüsseln von authenticatedState, id und primary:
   ![Web SDK in Debugger](assets/identity-deugger-websdk-event-lumaCrmId-dark.png)


## Validieren mit Browserdev-Tools

Diese Arten von Anforderungsdetails sind auch in den Webentwickler-Tools des Browsers sichtbar. **Netzwerk** Registerkarte (vorausgesetzt, die Website lädt Ihre Tag-Bibliothek).

1. Öffnen Sie die Webentwickler-Tools des Browsers. **Netzwerk** und laden Sie die Seite neu. Filtern von Aufrufen mit `/ee` Um den Aufruf zu finden, wählen Sie ihn aus und sehen Sie sich dann im **Kopfzeilen** und **Nutzlast** tab

   ![Registerkarte „Netzwerk“](assets/validate-dev-console.png)

1. Navigieren Sie zu **Reaktion** und beachten Sie, wie der ECID-Wert in der Antwort enthalten ist. Kopieren Sie diesen Wert, da Sie ihn verwenden werden, um die Profilinformationen in der nächsten Übung zu überprüfen.

   ![Registerkarte „Netzwerk“](assets/validate-dev-console-ecid.png)

   >[!NOTE]
   >
   >    Möglicherweise sehen Sie nicht die gleiche Anzahl von Nutzlastanfragen wie im Screenshot oben. Diese Diskrepanz liegt daran, dass zukünftige Lehren für [Einrichten von Target](setup-target.md) zum Zeitpunkt des Screenshots abgeschlossen wurden. Sie können diesen Unterschied vorerst ignorieren.

Da jetzt ein XDM-Objekt auf einer Seite ausgelöst wird und Sie wissen, wie Sie Ihre Datenerfassung überprüfen können, können Sie die einzelnen Adobe-Anwendungen mithilfe des Platform Web SDK einrichten.

[Weiter: ](setup-experience-platform.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
