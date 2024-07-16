---
title: Wechseln von Tag-Umgebungen mit dem Adobe Experience Cloud Debugger
description: Erfahren Sie, wie Sie mit dem Experience Cloud Debugger verschiedene Tag-Einbettungscodes laden können. Diese Lektion ist Teil des Tutorials zum Implementieren des Experience Cloud in Websites .
exl-id: 29972a00-e5e0-4fe0-a71c-c2ca106938be
source-git-commit: 2483409b52562e13a4f557fe5bdec75b5afb4716
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 24%

---

# Tag-Umgebungen mit dem Experience Cloud Debugger wechseln

In dieser Lektion verwenden Sie die [Adobe Experience Platform Debugger-Erweiterung](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob), um die auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) hartcodierte Tag-Eigenschaft durch Ihre eigene Eigenschaft zu ersetzen.

Diese Technik wird als Umgebungswechsel bezeichnet und ist später hilfreich, wenn Sie mit Tags auf Ihrer eigenen Website arbeiten. Sie können Ihre Produktionswebsite in Ihren Browser laden, jedoch mit Ihrer *Entwicklungs-* -Tag-Umgebung. Auf diese Weise können Sie sicher Änderungen an Tags vornehmen und überprüfen - unabhängig von Ihren normalen Codeversionen.  Schließlich ist diese Trennung der Marketing-Tag-Versionen von Ihren normalen Codeversionen einer der Hauptgründe, warum Kunden Tags überhaupt verwenden!

>[!NOTE]
>
>Adobe Experience Platform Launch wird als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform integriert. In der Benutzeroberfläche wurden verschiedene terminologische Änderungen eingeführt, die Sie bei der Verwendung dieses Inhalts beachten sollten:
>
> * Platform launch (Client-seitig) ist jetzt **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)**
> * Platform launch Server Side ist jetzt **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-Konfigurationen sind jetzt **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)**

## Lernziele

Am Ende dieser Lektion können Sie:

* Debugger verwenden, um eine alternative Tag-Umgebung zu laden
* Überprüfen Sie mit dem Debugger, ob Sie eine alternative Tag-Umgebung geladen haben.

## Abrufen der URL Ihrer Entwicklungsumgebung

1. Öffnen Sie in der Tag-Eigenschaft die Seite `Environments` .

1. Klicken Sie in der Zeile **[!UICONTROL Entwicklung]** auf das Installationssymbol ![Installationssymbol](images/launch-installIcon.png) , um das Modal zu öffnen.

1. Klicken Sie auf das Kopiersymbol ![Kopiersymbol](images/launch-copyIcon.png), um den Einbettungscode in die Zwischenablage zu kopieren.

1. Klicken Sie auf **[!UICONTROL Schließen]** , um das Modal zu schließen.

   ![Installationssymbol](images/launch-copyInstallCode.png)

## Tag-URL auf der Demosite &quot;Luma&quot;ersetzen

1. Öffnen Sie die [Demosite „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html) in Ihrem Chrome-Browser.

1. Öffnen Sie die Erweiterung [Experience Platform Debugger ](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob), indem Sie auf das Symbol ![Debugger-Symbol](images/icon-debugger.png) klicken.

   ![Klicken Sie auf das Debugger-Symbol](images/switchEnvironments-openDebugger.png)

1. Beachten Sie, dass die derzeit implementierte Tag-Eigenschaft auf der Registerkarte &quot;Zusammenfassung&quot;angezeigt wird.

   ![Tag-Umgebung, die im Debugger angezeigt wird](images/switchEnvironments-debuggerOnWeRetail-prod.png)

1. Navigieren Sie zur Registerkarte „Tools“.
1. Scrollen Sie zum Abschnitt **[!UICONTROL Ersetzen des eingebetteten Launch-Codes]**.
1. Stellen Sie sicher, dass die Registerkarte Chrome mit der Site &quot;Luma&quot;hinter dem Debugger im Fokus ist (nicht die Registerkarte mit diesem Tutorial oder der Registerkarte mit der Oberfläche zur Datenerfassung ).  Fügen Sie den Einbettungscode aus der Zwischenablage in das Eingabefeld ein.
1. Schalten Sie die Funktion &quot;Anwenden über luma.enablementadobe.com&quot;ein, damit alle Seiten auf der Site &quot;Luma&quot;Ihrer Tag-Eigenschaft zugeordnet werden.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]** .

   ![Tag-Umgebung, die im Debugger angezeigt wird](images/switchEnvironments-debugger-save.png)

1. Laden Sie die Site „Luma“ neu und überprüfen Sie die Registerkarte „Zusammenfassung“ des Debuggers. Im Launch-Abschnitt sollte angezeigt werden, dass Ihre Entwicklungseigenschaft verwendet wird. Vergewissern Sie sich, dass der Name der Eigenschaft richtig ist und dass die Umgebung die Bezeichnung „Entwicklung“ aufweist.

   ![Tag-Umgebung, die im Debugger angezeigt wird](images/switchEnvironments-debuggerOnWeRetail.png)

>[!NOTE]
>
>Der Debugger speichert diese Konfiguration und ersetzt die Tag-Einbettungscodes, sobald Sie zur Site &quot;Luma&quot;zurückkehren. Dies hat keine Auswirkungen auf andere Sites, die Sie auf anderen Registerkarten besuchen. Um zu verhindern, dass der Debugger den Einbettungscode ersetzt, klicken Sie auf der Registerkarte &quot;Tools&quot;des Debuggers neben dem Einbettungscode auf die Schaltfläche **[!UICONTROL Entfernen]** .

Während Sie das Tutorial fortsetzen, verwenden Sie diese Methode, um die Site &quot;Luma&quot;Ihrer eigenen Tag-Eigenschaft zuzuordnen und Ihre Tag-Implementierung zu validieren. Wenn Sie mit der Verwendung von Tags auf Ihrer Produktions-Website beginnen, können Sie dieselbe Methode verwenden, um Änderungen zu validieren.

[Weiter mit &quot;Hinzufügen des Adobe Experience Platform Identity-Diensts&quot;>](id-service.md)
