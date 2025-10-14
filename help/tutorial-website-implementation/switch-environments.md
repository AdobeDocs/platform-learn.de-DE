---
title: Wechseln von Tag-Umgebungen mit dem Adobe Experience Cloud Debugger
description: Erfahren Sie, wie Sie mit dem -Experience Cloud Debugger verschiedene Tag-Einbettungs-Codes laden können. Diese Lektion ist Teil des Tutorials Implementieren von Experience Cloud in Websites .
exl-id: 29972a00-e5e0-4fe0-a71c-c2ca106938be
source-git-commit: 2483409b52562e13a4f557fe5bdec75b5afb4716
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 24%

---

# Wechseln von Tag-Umgebungen mit dem Experience Cloud Debugger

In dieser Lektion verwenden Sie die Erweiterung [Adobe Experience Platform Debugger &#x200B;](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) um die Tag-Eigenschaft auf der Demo-Site [Luma“ hartcodiert &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html) Ihre eigene Eigenschaft zu ersetzen.

Diese Technik wird als Umgebungsumschaltung bezeichnet und ist später hilfreich, wenn Sie auf Ihrer eigenen Website mit Tags arbeiten. Sie können Ihre Produktions-Website in Ihrem Browser laden, jedoch mit Ihrer *Entwicklungs-)*. Auf diese Weise können Sie Tag-Änderungen unabhängig von Ihren regulären Code-Versionen sicher vornehmen und validieren.  Schließlich ist diese Trennung der Marketing-Tag-Versionen von Ihren regulären Code-Versionen einer der Hauptgründe, warum Kunden Tags überhaupt verwenden!

>[!NOTE]
>
>Adobe Experience Platform Launch wird als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform integriert. In der Benutzeroberfläche wurden mehrere terminologische Änderungen eingeführt, die Sie bei der Verwendung dieses Inhalts beachten sollten:
>
> * Platform launch (Client-seitig) ist jetzt **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)**
> * Platform launch Server Side ist jetzt **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de)**
> * Edge-Konfigurationen sind jetzt **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)**

## Lernziele

Am Ende dieser Lektion können Sie:

* Verwenden des Debuggers zum Laden einer alternativen Tag-Umgebung
* Verwenden Sie den Debugger, um zu überprüfen, ob Sie eine alternative Tag-Umgebung geladen haben

## Abrufen der URL Ihrer Entwicklungsumgebung

1. Öffnen Sie in Ihrer Tag-Eigenschaft die `Environments`

1. Klicken Sie in **[!UICONTROL Zeile]** Entwicklung“ auf das Symbol „Installieren![, &#x200B;](images/launch-installIcon.png) das Modal zu öffnen

1. Klicken Sie auf das Kopiersymbol ![Kopiersymbol](images/launch-copyIcon.png), um den Einbettungscode in die Zwischenablage zu kopieren.

1. Klicken Sie auf **[!UICONTROL Schließen]**, um das Modal zu schließen

   ![Installationssymbol](images/launch-copyInstallCode.png)

## Ersetzen Sie die Tag-URL auf der Demo-Site von Luma

1. Öffnen Sie die [Demosite „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html) in Ihrem Chrome-Browser.

1. Öffnen Sie die Erweiterung [Experience Platform Debugger](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) indem Sie auf das Symbol ![Debugger-Symbol](images/icon-debugger.png) klicken

   ![Klicken Sie auf das Debugger-Symbol](images/switchEnvironments-openDebugger.png)

1. Beachten Sie, dass die aktuell implementierte Tag-Eigenschaft auf der Registerkarte Zusammenfassung angezeigt wird

   ![Die Tag-Umgebung wird im Debugger angezeigt](images/switchEnvironments-debuggerOnWeRetail-prod.png)

1. Navigieren Sie zur Registerkarte „Tools“.
1. Scrollen Sie zum Abschnitt **[!UICONTROL Launch-Einbettungs-Code ersetzen]**
1. Stellen Sie sicher, dass die Registerkarte Chrome mit der Luma-Site hinter dem Debugger im Fokus ist (nicht die Registerkarte mit diesem Tutorial oder die Registerkarte mit der Datenerfassungsoberfläche).  Fügen Sie den Einbettungscode aus der Zwischenablage in das Eingabefeld ein.
1. Schalten Sie die Funktion „Apply across luma.enablementadobe.com“ ein, damit alle Seiten auf der Luma-Site Ihrer Tag-Eigenschaft zugeordnet werden
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![Die Tag-Umgebung wird im Debugger angezeigt](images/switchEnvironments-debugger-save.png)

1. Laden Sie die Site „Luma“ neu und überprüfen Sie die Registerkarte „Zusammenfassung“ des Debuggers. Im Launch-Abschnitt sollte angezeigt werden, dass Ihre Entwicklungseigenschaft verwendet wird. Vergewissern Sie sich, dass der Name der Eigenschaft richtig ist und dass die Umgebung die Bezeichnung „Entwicklung“ aufweist.

   ![Die Tag-Umgebung wird im Debugger angezeigt](images/switchEnvironments-debuggerOnWeRetail.png)

>[!NOTE]
>
>Der Debugger speichert diese Konfiguration und ersetzt die Tag-Einbettungs-Codes, wenn Sie zur Luma-Site zurückkehren. Dies hat keine Auswirkungen auf andere Sites, die Sie auf anderen Registerkarten besuchen. Um zu verhindern, dass der Debugger den Einbettungs-Code ersetzt, klicken Sie auf die Schaltfläche **[!UICONTROL Entfernen]** neben dem Einbettungs-Code auf der Registerkarte Tools des Debuggers.

Während Sie mit dem Tutorial fortfahren, verwenden Sie diese Methode, um die Luma-Site Ihrer eigenen Tag-Eigenschaft zuzuordnen, um Ihre Tag-Implementierung zu validieren. Wenn Sie mit der Verwendung von Tags auf Ihrer Produktions-Website beginnen, können Sie dieselbe Technik verwenden, um Änderungen zu validieren.

[Weiter &quot;Adobe Experience Platform Identity Service hinzufügen“ >](id-service.md)
