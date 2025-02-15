---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Client-seitige Web-Datenerfassung
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Client-seitige Web-Datenerfassung
kt: 5342
doc-type: tutorial
exl-id: dce7f1b5-72ca-41b2-9aa8-41c13ce25c82
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 1.1.4 Client-seitige Web-Datenerfassung

## Validieren der Daten in der Anfrage

### Installieren von Adobe Experience Platform Debugger

Experience Platform Debugger ist eine Erweiterung, die für Chrome- und Firefox-Browser verfügbar ist und Ihnen dabei hilft, die auf Ihren Web-Seiten implementierte Adobe-Technologie zu sehen. Installieren Sie die Version für Ihren bevorzugten Browser:

- [Firefox-Erweiterung](https://addons.mozilla.org/de/firefox/addon/adobe-experience-platform-dbg/)

- [Chrome-Erweiterung](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

Wenn Sie den Debugger noch nie verwendet haben - und dieser unterscheidet sich vom vorherigen Adobe Experience Cloud Debugger - sollten Sie sich dieses fünfminütige Übersichtsvideo ansehen:

>[!VIDEO](https://video.tv.adobe.com/v/32156?quality=12&learn=on&enablevpops)

Da Sie die Demo-Website im Inkognito-Modus laden werden, müssen Sie sicherstellen, dass der Experience Platform-Debugger auch im Inkognito-Modus verfügbar ist. Navigieren Sie dazu zu **chrome://extensions** in Ihrem Browser und öffnen Sie die Experience Platform Debugger-Erweiterung.

Stellen Sie sicher, dass diese beiden Einstellungen aktiviert sind:

- Entwicklermodus
- Inkognito zulassen

![EXP News Homepage](./images/ext1.png)

### Demo-Website öffnen

Navigieren Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf die 3 Punkte **…** in Ihrem Website-Projekt und dann auf **Ausführen**, um es zu öffnen.

![DSN](./images/web8.png)

Anschließend wird Ihre Demo-Website geöffnet. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](./../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browser-Fenster.

![DSN](./../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](./../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](./../../gettingstarted/gettingstarted/images/web6.png)

Ihre Website wird dann in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](./../../gettingstarted/gettingstarted/images/web7.png)

### Verwenden Sie den Experience Platform Debugger, um die Aufrufe an die Edge anzuzeigen

Stellen Sie sicher, dass die Demo-Website geöffnet ist und klicken Sie auf das Symbol der Experience Platform Debugger-Erweiterung .

![EXP News Homepage](./images/ext2.png)

Der Debugger wird geöffnet und zeigt die Details der Implementierung an, die in der Datenerfassungseigenschaft von Adobe Experience Platform erstellt wurde. Denken Sie daran, dass Sie die Erweiterung und die Regeln debuggen, die Sie gerade bearbeitet haben.

Klicken Sie oben rechts auf **[!UICONTROL Schaltfläche]** Anmelden“, um sich zu authentifizieren. Wenn Sie bereits eine Browser-Registerkarte mit der Datenerfassungsoberfläche von Adobe Experience Platform geöffnet haben, wird der Authentifizierungsschritt automatisch durchgeführt und Sie müssen Ihren Benutzernamen und Ihr Kennwort nicht erneut eingeben.

![AEP-Debugger](./images/validate2.png)

Sie werden dann im Debugger angemeldet.

![AEP-Debugger](./images/validate2ab.png)

Klicken Sie auf der Demo-Website auf die Schaltfläche Neu laden , um den Debugger mit dieser bestimmten Registerkarte zu verbinden.

![AEP-Debugger](./images/validate2a.png)

Bestätigen Sie, dass der Debugger **[!UICONTROL Mit Startseite verbunden]** ist, wie oben abgebildet, und klicken Sie dann auf das **[!UICONTROL Sperren]**-Symbol, um den Debugger für die Demo-Website zu sperren. Andernfalls wechselt der Debugger immer wieder, um die Implementierungsdetails der Browser-Registerkarte anzuzeigen, die im Fokus ist, was verwirrend sein kann. Sobald der Debugger gesperrt ist, ändert sich das Symbol in **Entsperren**.

![AEP-Debugger](./images/validate3.png)

Rufen Sie als Nächstes eine beliebige Seite der Demo-Website auf, z. B. die Kategorieseite **Pläne** .

![AEP Debugger AEP Web SDK-Erweiterung](./images/validate4.png)

Klicken Sie jetzt im linken Navigationsbereich auf ]**0}Experience Platform Web SDK, um die**[!UICONTROL  Netzwerkanfragen“ ]**.**[!UICONTROL 

Jede Anfrage enthält eine **[!UICONTROL Ereignis]**-Zeile.

![AEP Debugger AEP Web SDK-Erweiterung](./images/validate5.png)

Klicken, um eine Zeile **[!UICONTROL Ereignisse]** zu öffnen. Beachten Sie, wie Sie das **web.webpagedetails.pageViews**-Ereignis sowie andere native Variablen im XDM-Format **Web SDK ExperienceEvent** sehen können.

![Ereigniswert](./images/validate8.png)

Diese Arten von Anfragedetails sind auch auf der Registerkarte Netzwerk sichtbar. Filtern Sie nach Anfragen mit **interact**, um die von Web SDK gesendeten Anfragen zu finden. Alle Details der XDM-Payload finden Sie im Abschnitt Payload :

![Registerkarte „Netzwerk“](./images/validate9.png)

Nächster Schritt: [1.1.5 Implementieren von Adobe Analytics und Adobe Audience Manager](./ex5.md)

[Zurück zum Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zurück zu „Alle Module“](./../../../overview.md)
