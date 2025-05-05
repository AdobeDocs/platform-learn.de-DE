---
title: Publish - Ihre Tag-Eigenschaft
description: Erfahren Sie, wie Sie Ihre Tag-Eigenschaft aus der Entwicklungsumgebung in der Staging- und Produktionsumgebung veröffentlichen. Diese Lektion ist Teil des Tutorials Implementieren von Experience Cloud in Websites .
exl-id: dec70472-cecc-4630-b68e-723798f17a56
source-git-commit: e2594d3b30897001ce6cb2f6908d75d0154015eb
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 58%

---

# Publish - Ihre Tag-Eigenschaft

Nachdem Sie nun einige wichtige Adobe Experience Cloud-Lösungen in Ihrer Entwicklungsumgebung implementiert haben, ist es Zeit, den Veröffentlichungs-Workflow kennenzulernen.

>[!NOTE]
>
>Adobe Experience Platform Launch wird als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform integriert. In der Benutzeroberfläche wurden mehrere terminologische Änderungen eingeführt, die Sie bei der Verwendung dieses Inhalts beachten sollten:
>
> * Platform launch (Client-seitig) ist jetzt **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)**
> * Platform launch Server Side ist jetzt **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de)**
> * Edge-Konfigurationen sind jetzt **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)**

## Lernziele

Am Ende dieser Lektion können Sie:

1. eine Entwicklungsbibliothek in der Staging-Umgebung veröffentlichen
1. Ihrer Produktionswebsite mithilfe des Debuggers eine Staging-Bibliothek zuordnen
1. eine Staging-Bibliothek in der Produktionsumgebung veröffentlichen

## Veröffentlichung im Staging

Nachdem Sie Ihre Bibliothek in der Entwicklungsumgebung erstellt und überprüft haben, ist es Zeit, sie in der Staging-Umgebung zu veröffentlichen.

1. Navigieren Sie zur Seite **[!UICONTROL Publishing-Ablauf]**.

1. Öffnen Sie das Dropdown-Menü neben Ihrer Bibliothek und wählen Sie **[!UICONTROL Zur Genehmigung einreichen]**

   ![Einreichen zur Genehmigung](images/publishing-submitForApproval.png)

1. Klicken Sie im **[!UICONTROL auf]** Senden“:

   ![Klicken Sie im Modal auf „Absenden“](images/publishing-submit.png)

1. Ihre Bibliothek wird jetzt in der Spalte [!UICONTROL Gesendet] in einem nicht erstellten Status angezeigt:

1. Öffnen Sie das Dropdown-Menü und wählen Sie **[!UICONTROL Für Staging erstellen]**:

   ![Build für das Staging](images/publishing-buildForStaging.png)

1. Sobald das grüne Symbol zu sehen ist, kann die Bibliothek in der Staging-Umgebung als Vorschau angezeigt werden.

In einem realen Szenario würde nun Ihr QA-Team die Änderungen in der Staging-Bibliothek validieren. Hierzu kann Ihr Team den Debugger verwenden.

**Überprüfen der Änderungen in der Staging-Bibliothek**

1. Öffnen Sie in Ihrer Tag-Eigenschaft die Seite [!UICONTROL Umgebungen]

1. Klicken Sie in der Zeile [!UICONTROL Staging] auf das Installationssymbol ![Installationssymbol](images/launch-installIcon.png), um das Modal zu öffnen.

   ![Wechseln Sie zur Seite „Umgebungen“ und klicken Sie, um das Modal zu öffnen](images/publishing-getStagingCode.png)

1. Klicken Sie auf das Kopiersymbol ![Kopiersymbol](images/launch-copyIcon.png), um den Einbettungscode in die Zwischenablage zu kopieren.

1. Klicken Sie auf **[!UICONTROL Schließen]**, um das Modal zu schließen

   ![Installationssymbol](images/publishing-copyStagingCode.png)

1. Öffnen Sie die [Demosite „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html) in Ihrem Chrome-Browser.

1. Öffnen Sie die Erweiterung [Experience Platform Debugger](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) indem Sie auf das Symbol ![Debugger-Symbol](images/icon-debugger.png) klicken

   ![Klicken Sie auf das Debugger-Symbol](images/switchEnvironments-openDebugger.png)

1. Navigieren Sie zur Registerkarte „Tools“.

1. Fügen Sie im Abschnitt **[!UICONTROL Adobe-Launch > Launch-Einbettungs-Code ersetzen]** den Einbettungs-Code für das Staging in die Zwischenablage ein
1. Schalten Sie den **[!UICONTROL Apply across luma.enablementadobe.com]** ein

1. Klicken Sie auf das Diskettensymbol, um zu speichern.

   ![Die Tag-Umgebung wird im Debugger angezeigt](images/switchEnvironments-debugger-save.png)

1. Laden Sie die Registerkarte „Zusammenfassung“ des Debuggers neu und überprüfen Sie diese. Im Abschnitt Launch sollte nun Ihre Staging-Eigenschaft implementiert sein und Ihren Eigenschaftsnamen anzeigen (d. h. „Tags-Tutorial“ oder den Namen Ihrer Eigenschaft)!

   ![Die Tag-Umgebung wird im Debugger angezeigt](images/publishing-debugger-staging.png)

Sobald Ihr QA-Team die Änderungen in der Staging-Umgebung überprüft und bestätigt hat, können Sie sie in der Produktion veröffentlichen.

## Veröffentlichung in der Produktion

1. Navigieren Sie zur Seite [!UICONTROL Veröffentlichung].

1. Klicken Sie im Dropdown-Menü auf **[!UICONTROL Für Veröffentlichung genehmigen]**:

   ![Zur Veröffentlichung genehmigen](images/publishing-approveForPublishing.png)

1. Klicken Sie **[!UICONTROL Dialogfeld auf]** Genehmigen“:

   ![Klicken Sie auf „Genehmigen“](images/publishing-approve.png)

1. Die Bibliothek wird jetzt in der Spalte [!UICONTROL Genehmigt] im nicht erstellten Status (gelber Punkt) angezeigt:

1. Öffnen Sie das Dropdown-Menü und wählen Sie **[!UICONTROL Erstellen und Publish in Produktion]**:

   ![Klicken Sie auf „Erstellen und in Produktion veröffentlichen“](images/publishing-buildAndPublishToProduction.png)

1. Klicken Sie im Dialogfeld auf **&#x200B;**&#x200B;Publish:

   ![Klicken Sie auf Veröffentlichen](images/publishing-publish.png)

1. Die Bibliothek wird nun in der Spalte [!UICONTROL Veröffentlicht] angezeigt:

   ![Veröffentlicht](images/publishing-published.png)

Das ist alles! Sie haben das Tutorial abgeschlossen und Ihre erste Eigenschaft in Tags veröffentlicht!
