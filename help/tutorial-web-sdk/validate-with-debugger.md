---
title: Validieren von Web SDK-Implementierungen mit Experience Platform Debugger
description: Erfahren Sie, wie Sie Ihre Platform Web SDK-Implementierung mit Adobe Experience Platform Debugger validieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Tags,Debugger
jira: KT-15405
exl-id: 150bb1b1-4523-4b44-bd4e-6cabc468fc04
source-git-commit: da65f13f95a6d1258655e8eebc76cf024221a610
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 2%

---

# Validieren von Web SDK-Implementierungen mit Experience Platform Debugger

Erfahren Sie, wie Sie Ihre Adobe Experience Platform Web SDK-Implementierung mit Adobe Experience Platform Debugger validieren.


Experience Platform Debugger ist eine [Chrome](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)Erweiterung, mit der Sie die in Ihren Web-Seiten implementierte Adobe-Technologie sehen können. Experience Platform Debugger und die Entwicklerkonsole Ihres Browsers sind die besten Möglichkeiten, die browserseitigen Aspekte Ihrer Web-SDK-Implementierung zu überprüfen und zu debuggen. Adobe Experience Platform Assurance, das in der nächsten Lektion behandelt wird, bietet die beste Ansicht der Daten, wenn sie in Platform Edge Network ein- und ausgehen.

![Validierungsdiagramm für Web SDK und Adobe Experience Platform](assets/dc-websdk-validation.png)


Wenn Sie den Debugger noch nie verwendet haben, sollten Sie sich dieses 5-minütige Übersichtsvideo ansehen:

>[!VIDEO](https://video.tv.adobe.com/v/32156?learn=on&enablevpops)

In dieser Lektion verwenden Sie die Erweiterung [Adobe Experience Platform Debugger](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) um die Tag-Eigenschaft, die auf der Demo-Website von [Luma“ hartcodiert &#x200B;](https://luma.enablementadobe.com), durch Ihre eigene Eigenschaft zu ersetzen.

Diese Technik wird als Umgebungsumschaltung bezeichnet und ist später hilfreich, wenn Sie auf Ihrer eigenen Website mit Tags arbeiten. Damit können Sie Ihre Produktions-Website in Ihren Browser laden, jedoch mit Ihrer *Entwicklungs-)*. Mit dieser Funktion können Sie Tag-Änderungen unabhängig von Ihren regulären Code-Versionen sicher vornehmen und validieren. Schließlich ist diese Trennung der Marketing-Tag-Versionen von Ihren regulären Code-Versionen einer der Hauptgründe, warum Kunden Tags überhaupt verwenden!

## Lernziele

Am Ende dieser Lektion können Sie den Debugger für folgende Aufgaben verwenden:

* Laden einer alternativen Tag-Bibliothek
* Überprüfen Sie, ob das Client-seitige XDM-Ereignis Daten wie erwartet erfasst und an Platform Edge Network sendet
* Aktivieren von Edge Trace, um Server-seitige Anforderungen anzuzeigen, die von Platform Edge Network gesendet werden

## Voraussetzungen

Sie sind mit Datenerfassungs-Tags und der [Demo-Website von Luma](https://luma.enablementadobe.com/){target="_blank"} vertraut und haben die vorherigen Lektionen im Tutorial abgeschlossen:

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Konfigurieren eines Identity-Namespace](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)
* [Datenelemente erstellen](create-data-elements.md)
* [Erfassen von Identitäten](create-identities.md)
* [Tag-Regeln erstellen](create-tag-rule.md)

## Laden alternativer Tag-Bibliotheken mit Debugger

Der Experience Platform-Debugger verfügt über eine coole Funktion, mit der Sie eine vorhandene Tag-Bibliothek durch eine andere ersetzen können. Diese Technik ist für die Validierung nützlich und ermöglicht es uns, viele Implementierungsschritte in diesem Tutorial zu überspringen.

1. Vergewissern Sie sich, dass Sie die [Demo-Website von Luma](https://luma.enablementadobe.com){target="_blank"} geöffnet haben, und wählen Sie das Symbol für die Experience Platform Debugger-Erweiterung aus
1. Der Debugger wird geöffnet und zeigt einige Details der hartcodierten Implementierung an (möglicherweise müssen Sie die Luma-Site nach dem Öffnen des Debuggers neu laden)
1. Vergewissern Sie sich, dass der Debugger **[!UICONTROL mit Luma verbunden]** ist, wie unten dargestellt, und wählen Sie dann das Symbol &quot;**[!UICONTROL lock]**&quot; aus, um den Debugger für die Luma-Site zu sperren.
1. Wählen Sie die Schaltfläche **[!UICONTROL Anmelden]**, melden Sie sich mit Ihrer Adobe-ID bei Adobe Experience Cloud an und wählen Sie Ihr Unternehmen aus.

   >[!TIP]
   >
   > Wenn der Debugger nach der Anmeldung Ihren Benutzernamen anstelle des Organisationsnamens anzeigt, melden Sie sich ab und versuchen Sie es erneut.


   ![Debugger-Tag-Bildschirm](assets/validate-launch-screen.png)

1. Navigieren Sie jetzt zu **[!UICONTROL Experience Platform Tags]** im linken Navigationsbereich
1. Wählen Sie die **[!UICONTROL Konfiguration]** aus
1. Öffnen Sie rechts neben der Stelle, an der die **[!UICONTROL Seiteneinbettungs-Codes]** angezeigt werden, das **[!UICONTROL Aktionen]** und wählen Sie **[!UICONTROL Ersetzen]**

   ![Wählen Sie Aktionen > Ersetzen](assets/validate-switch-environment.png)

1. Da Sie authentifiziert sind, ruft der Debugger Ihre verfügbaren Tag-Eigenschaften und Umgebungen ab. Eigenschaft auswählen
1. `Development` auswählen
   ![Wählen Sie die alternative Tag-Eigenschaft aus](assets/validate-switch-selection.png)

   >[!TIP]
   >
   > Wenn Sie Ihre Eigenschaft und Umgebung nicht über die Dropdown-Listen auswählen können, gehen Sie stattdessen zu [!UICONTROL Tags] > [!UICONTROL Umgebungen] > [!UICONTROL Entwicklung] > [!UICONTROL Installieren] und klicken Sie auf das Symbol, um den Einbettungs-Code zu kopieren und in den Debugger einzufügen:
   > ![Wählen Sie die alternative Tag-Eigenschaft aus](assets/validate-copy-embed-code.png)

1. Klicken Sie auf die **[!UICONTROL Apply]**-Schaltfläche

1. Die Luma-Website wird jetzt neu geladen _mit Ihrer eigenen Tag-Eigenschaft_.

   ![Tag-Eigenschaft ersetzt](assets/validate-switch-success.png)

Während Sie mit dem Tutorial fortfahren, verwenden Sie diese Methode, um die Luma-Site Ihrer eigenen Tag-Eigenschaft zuzuordnen, um Ihre Implementierung von Platform Web SDK zu validieren. Wenn Sie Tags auf Ihrer eigenen Website verwenden, können Sie dieselbe Methode zur Validierung von Entwicklungs-Tag-Bibliotheken auf Ihrer Produktions-Website verwenden.



## Validieren mit Debugger

### Überprüfen von Netzwerkanfragen und XDM

Sie können den Debugger verwenden, um Client-seitige Beacons zu validieren, die von Ihrer Platform Web SDK-Implementierung ausgelöst werden, um die an Platform Edge Network gesendeten Daten anzuzeigen:

1. Navigieren Sie **[!UICONTROL linken]** zu „Zusammenfassung“, um die Details Ihrer Tag-Eigenschaft anzuzeigen

   ![Registerkarte Zusammenfassung](assets/validate-summary.png)

1. Wechseln Sie jetzt zu **[!UICONTROL Experience Platform Web SDK]** im linken Navigationsbereich, um die **[!UICONTROL Netzwerkanfragen“ anzuzeigen]**
1. Öffnen Sie die **[!UICONTROL Ereignisse]** Zeile

   ![Adobe Experience Platform Web SDK-Anfrage](assets/validate-aep-screen.png)

1. Beachten Sie, wie Sie den `web.webPageDetails.pageView` Ereignistyp, den Sie in Ihrer Aktion [!UICONTROL Variable aktualisieren] angegeben haben, und andere vordefinierte Variablen sehen können, die der `AEP Web SDK ExperienceEvent` Feldergruppe entsprechen

   ![Ereignisdetails](assets/validate-event-pageViews.png)

1. Scrollen Sie nach unten zum `web`, wählen Sie es aus, um es zu öffnen, und überprüfen Sie die `webPageDetails.name`. Sie sollten mit den entsprechenden `adobeDataLayer` Datenschichtvariablen auf der Homepage übereinstimmen

>[!TIP]
>
> So zeigen Sie die `adobeDataLayer` Datenschicht auf der Homepage an und vergleichen sie:
>
> 1. Öffnen Sie auf der Luma-Homepage die Browser-Entwickler-Tools. Wählen Sie bei Chrome die Schaltfläche `F12` auf der Tastatur aus.
> 1. Wählen Sie die Registerkarte **[!UICONTROL Konsole]** aus
> 1. Geben Sie `adobeDataLayer` ein und wählen Sie `Enter` auf der Tastatur aus, um die Datenschichtwerte aufzurufen

![Registerkarte „Netzwerk“](assets/validate-xdm-content.png)

Validieren Sie die Ereignisse und Variablen, die auf den Produktseiten, auf der Warenkorbseite und auf der Bestellbestätigungsseite festgelegt sind.

### Identitätszuordnung validieren

Sie können auch die Details der Identitätszuordnung überprüfen:

1. Wählen Sie **[!DNL Sign In]** auf der [Luma-Website](https://luma.enablementadobe.com/){target=_blank}. Wählen Sie **[!DNL Create Account]** aus und erstellen Sie ein Konto mit den Anmeldedaten `test@test.com`/`test`

1. Verwenden Sie den **[!UICONTROL Jump to latest]** im Debugger, um schnell zum neuesten Web SDK-Ereignis zu wechseln (es ist die letzte Spalte). Wählen Sie die **[!UICONTROL Ereignisse]** aus, um das Modal „Details“ zu öffnen.

1. Suchen Sie im Modal nach **identityMap**. Hier sollten `lumaCrmId` mit drei Schlüsseln für „AuthenticatedState“, „ID“ und die primäre Bezeichnung angezeigt werden:
   ![Web SDK in Debugger](assets/identity-deugger-websdk-event-lumaCrmId-dark.png)

## Validieren mit Browser-Entwickler-Tools

Viele Web-Entwickler ziehen es möglicherweise vor, die Implementierung in den Entwickler-Tools ihres Browsers anzuzeigen. Dies ist besonders wichtig, da nicht alle Browser die Debugger-Erweiterung unterstützen. Aufgrund des flexiblen Frameworks stehen außerdem zusätzliche Implementierungsdetails zur Verfügung, die Sie einsehen können, z. B. Cookies und Antwortdetails.

### Prüfen von Netzwerkanfragen

Details zu Web SDK-Anfragen finden Sie auch auf der Registerkarte Web-Entwickler-Tools **Netzwerk** (vorausgesetzt, die Website lädt Ihre Tag-Bibliothek).

1. Öffnen Sie im Browser die Registerkarte Web-Entwickler-Tools **Netzwerk** und laden Sie die Seite neu. Filtern Sie nach Aufrufen mit `/ee`, um den Aufruf zu finden, ihn auszuwählen und dann auf der Registerkarte **Kopfzeilen** und auf der Registerkarte **Payload** zu suchen

   ![Registerkarte „Netzwerk“](assets/validate-dev-console.png)

1. Wechseln Sie zur Registerkarte **Vorschau** und beachten Sie, wie der ECID-Wert in der Netzwerkantwort enthalten ist.

   ![Registerkarte „Netzwerk“](assets/validate-dev-console-ecid.png)

   >[!NOTE]
   >
   > Der ECID-Wert ist in der Netzwerkantwort sichtbar. Sie ist nicht im `identityMap` Teil der Netzwerkanfrage enthalten und wird auch nicht in diesem Format in einem Cookie gespeichert.

### Cookies im Web SDK

Sehen wir uns einige der Cookies, die Web SDK im Browser setzt, an, während wir uns mit den Entwickler-Tools beschäftigen. Öffnen Sie Anwendung > Cookies > https://luma.enablementadobe.com

Es sollten mehrere Cookies angezeigt werden, die von Web SDK gesetzt werden:

* kndctr_[IMS_ORGID]_AdobeOrg_identity: speichert Daten zur ECID
* kndctr_[IMS_ORGID]_AdobeOrg_cluster: speichert den verwendeten Rechenzentrumsstandort, damit nachfolgende Netzwerkaufrufe an dieselben Edge-Server weitergeleitet werden
* AMCV_[IMS_ORGID]%40AdobeOrg: Dies ist das veraltete AMCV-Cookie, das von Pre-Web SDK Experience Cloud-Bibliotheken verwendet wird. Es wird festgelegt, weil die Standardeinstellung **[!UICONTROL Migrieren von ECID zu VisitorAPI zur Web SDK]** in der Adobe Experience Platform Web SDK Tags-Erweiterung ausgewählt wurde. Diese Einstellung muss aktiviert sein, wenn Sie Ihre Seiten von älteren Bibliotheken zu Web SDK migrieren. Sie kann jedoch deaktiviert werden, nachdem alle Ihre Seiten für eine bestimmte Zeit migriert wurden.

![Registerkarte „Cookies“](assets/debugger-cookies.png)

Wenn Sie diese Cookies löschen und die Seite neu laden, werden Sie möglicherweise feststellen, dass zusätzliche Drittanbieter-Cookies in der `.demdex.net` Domain gesetzt wurden. Diese sind festgelegt, weil wir die Standardeinstellung **[!UICONTROL Verwenden von Cookies von Drittanbietern]**: **[!UICONTROL Aktiviert]** in der Tags-Erweiterung von Adobe Experience Platform Web SDK beibehalten haben. Wenn Ihr Browser keine Third-Party-Cookies zulässt, werden diese beim Neuladen der Seite entfernt.

![Demdex-Cookies](assets/debugger-demdex-cookies.png)


### Lokaler Speicher von Luma

Die Demo-Website von Luma verwendet ausschließlich Client-seitige Technologien wie HTML, CSS und JavaScript. Es gibt keine Backend-Speichermechanismen außer der Experience Cloud-Implementierung, die vom Standardstatus der Website verwendet wird. Informationen wie Benutzernamen-Details werden nur lokal in Ihrem Browser mit localStorage gespeichert. Wenn Sie also diese Informationen löschen oder ein Inkognitor-Fenster verwenden, werden Sie feststellen, dass Sie möglicherweise ein zuvor erstelltes Testbenutzerkonto neu erstellen müssen.

![Lokaler Speicher](assets/debugger-local-storage.png)


Erfahren Sie als Nächstes, wie Sie diese Netzwerkanfragen validieren, wenn sie von Platform Edge Network mithilfe von Adobe Experience Platform Assurance empfangen und übertragen werden!

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
