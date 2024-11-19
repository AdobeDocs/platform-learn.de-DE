---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Clientseitige Web-Datenerfassung
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Clientseitige Web-Datenerfassung
kt: 5342
doc-type: tutorial
exl-id: dce7f1b5-72ca-41b2-9aa8-41c13ce25c82
source-git-commit: 3a19e88e820c63294eff38bb8f699a9f690afcb9
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 1.1.4 Clientseitige Web-Datenerfassung

## Überprüfen der Daten in der Anforderung

### Installieren des Adobe Experience Platform Debuggers

Der Experience Platform Debugger ist eine Erweiterung für Chrome- und Firefox-Browser, die Ihnen dabei hilft, die auf Ihren Webseiten implementierte Adobe-Technologie zu sehen. Installieren Sie die Version für Ihren bevorzugten Browser:

- [Firefox-Erweiterung](https://addons.mozilla.org/de/firefox/addon/adobe-experience-platform-dbg/)

- [Chrome-Erweiterung](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

Wenn Sie den Debugger noch nie verwendet haben - und dieser von dem vorherigen Adobe Experience Cloud Debugger unterscheidet -, sollten Sie sich dieses fünfminütige Übersichtsvideo ansehen:

>[!VIDEO](https://video.tv.adobe.com/v/32156?quality=12&learn=on)

Da Sie die Demo-Website im Inkognito-Modus laden, müssen Sie sicherstellen, dass der Experience Platform Debugger auch im Inkognito-Modus verfügbar ist. Wechseln Sie dazu in Ihrem Browser zu **chrome://extensions** und öffnen Sie die Experience Platform Debugger-Erweiterung.

Stellen Sie sicher, dass diese beiden Einstellungen aktiviert sind:

- Entwicklermodus
- In Inkognito zulassen

![EXP News-Homepage](./images/ext1.png)

### Öffnen Sie die Demowebsite

Wechseln Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf die drei Punkte **..** im Website-Projekt und dann auf **Ausführen** , um es zu öffnen.

![DSN](./images/web8.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](./../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](./../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](./../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](./../../gettingstarted/gettingstarted/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](./../../gettingstarted/gettingstarted/images/web7.png)

### Verwenden Sie den Experience Platform Debugger, um die Aufrufe anzuzeigen, die an die Edge gesendet werden.

Stellen Sie sicher, dass die Demo-Website geöffnet ist, und klicken Sie auf das Symbol Experience Platform Debugger-Erweiterung .

![EXP News-Homepage](./images/ext2.png)

Der Debugger wird geöffnet und zeigt die Details der Implementierung an, die in Ihrer Adobe Experience Platform-Datenerfassungseigenschaft erstellt wurde. Denken Sie daran, dass Sie die Erweiterung und die Regeln debuggen, die Sie gerade bearbeitet haben.

Klicken Sie oben rechts auf die Schaltfläche **[!UICONTROL Anmelden]** , um sich zu authentifizieren. Wenn Sie bereits über die Benutzeroberfläche zur Datenerfassung von Adobe Experience Platform eine Browser-Registerkarte geöffnet haben, wird der Authentifizierungsschritt automatisch durchgeführt und Sie müssen Ihren Benutzernamen und Ihr Kennwort nicht erneut eingeben.

![AEP-Debugger](./images/validate2.png)

Sie werden dann im Debugger angemeldet sein.

![AEP-Debugger](./images/validate2ab.png)

Drücken Sie die Schaltfläche Neu laden auf Ihrer Demo-Website, um den Debugger mit dieser Registerkarte zu verbinden.

![AEP-Debugger](./images/validate2a.png)

Vergewissern Sie sich, dass der Debugger, wie oben dargestellt, &quot;**[!UICONTROL Verbindung zur Startseite&quot;]**&quot;ist, und klicken Sie dann auf das Symbol &quot;**[!UICONTROL Sperren]**&quot;, um den Debugger mit der Demowebsite zu sperren. Wenn Sie dies nicht tun, schaltet der Debugger weiter, um die Implementierungsdetails der Browser-Registerkarte anzuzeigen, die im Fokus ist, was verwirrend sein kann. Sobald der Debugger gesperrt ist, wird das Symbol in **Entsperren** geändert.

![AEP-Debugger](./images/validate3.png)

Navigieren Sie anschließend zu einer beliebigen Seite auf der Demowebsite, z. B. der Kategorieseite **Pläne** .

![AEP Debugger AEP Web SDK-Erweiterung](./images/validate4.png)

Klicken Sie nun im linken Navigationsbereich auf **[!UICONTROL Experience Platform Web SDK]** , um die **[!UICONTROL Netzwerkanforderungen]** anzuzeigen.

Jede Anforderung enthält eine Zeile **[!UICONTROL events]** .

![AEP Debugger AEP Web SDK-Erweiterung](./images/validate5.png)

Klicken Sie auf , um eine Zeile **[!UICONTROL events]** zu öffnen. Beachten Sie, wie Sie das Ereignis **web.webpageDetails.pageViews** sowie weitere native Variablen sehen können, die dem Format **Web SDK ExperienceEvent XDM** entsprechen.

![Ereigniswert](./images/validate8.png)

Diese Arten von Anforderungsdetails sind auch auf der Registerkarte &quot;Netzwerk&quot;sichtbar. Filtern Sie nach Anforderungen mit **interact** , um die vom Web SDK gesendeten Anforderungen zu finden. Alle Details der XDM-Payload finden Sie im Abschnitt Payload :

![Registerkarte &quot;Netzwerk&quot;](./images/validate9.png)

Nächster Schritt: [1.1.5 Adobe Analytics und Adobe Audience Manager implementieren](./ex5.md)

[Zurück zu Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
