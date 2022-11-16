---
title: Veröffentlichen der Tag-Eigenschaft
description: Erfahren Sie, wie Sie Ihre Tag-Eigenschaft aus der Entwicklungsumgebung in den Staging- und Produktionsumgebungen veröffentlichen. Diese Lektion ist Teil des Tutorials zum Implementieren des Experience Cloud in Websites .
exl-id: dec70472-cecc-4630-b68e-723798f17a56
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 72%

---

# Veröffentlichen der Tag-Eigenschaft

Nachdem Sie nun einige wichtige Adobe Experience Cloud-Lösungen in Ihrer Entwicklungsumgebung implementiert haben, ist es Zeit, den Veröffentlichungs-Workflow kennenzulernen.

>[!NOTE]
>
>Adobe Experience Platform Launch wird als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform integriert. In der Benutzeroberfläche wurden verschiedene terminologische Änderungen eingeführt, die Sie bei der Verwendung dieses Inhalts beachten sollten:
>
> * platform launch (Client-seitig) ist jetzt **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)**
> * platform launch Server Side ist jetzt **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-Konfigurationen sind jetzt verfügbar **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)**


## Lernziele

Am Ende dieser Lektion können Sie:

1. eine Entwicklungsbibliothek in der Staging-Umgebung veröffentlichen
1. Ihrer Produktionswebsite mithilfe des Debuggers eine Staging-Bibliothek zuordnen
1. eine Staging-Bibliothek in der Produktionsumgebung veröffentlichen

## Veröffentlichung im Staging

Nachdem Sie Ihre Bibliothek in der Entwicklungsumgebung erstellt und überprüft haben, ist es Zeit, sie in der Staging-Umgebung zu veröffentlichen.

1. Navigieren Sie zu **[!UICONTROL Veröffentlichungsfluss]** page

1. Öffnen Sie das Dropdown-Menü neben Ihrer Bibliothek und wählen Sie **[!UICONTROL Zur Genehmigung übermitteln]** aus.

   ![Einreichen zur Genehmigung](images/publishing-submitForApproval.png)

1. Klicken Sie im Dialogfeld auf die Schaltfläche **[!UICONTROL Absenden]**:

   ![Klicken Sie im Modal auf „Absenden“](images/publishing-submit.png)

1. Ihre Bibliothek wird jetzt in der Spalte [!UICONTROL Gesendet] in einem nicht erstellten Status angezeigt:

1. Öffnen Sie das Dropdown-Menü und wählen Sie **[!UICONTROL Build für das Staging]** aus:

   ![Build für das Staging](images/publishing-buildForStaging.png)

1. Sobald das grüne Symbol zu sehen ist, kann die Bibliothek in der Staging-Umgebung als Vorschau angezeigt werden.

In einem realen Szenario würde nun Ihr QA-Team die Änderungen in der Staging-Bibliothek validieren. Hierzu kann Ihr Team den Debugger verwenden.

**Überprüfen der Änderungen in der Staging-Bibliothek**

1. Öffnen Sie in der Tag-Eigenschaft die [!UICONTROL Umgebungen] page

1. Klicken Sie in der Zeile [!UICONTROL Staging] auf das Installationssymbol ![Installationssymbol](images/launch-installIcon.png), um das Modal zu öffnen.

   ![Wechseln Sie zur Seite „Umgebungen“ und klicken Sie, um das Modal zu öffnen](images/publishing-getStagingCode.png)

1. Klicken Sie auf das Kopiersymbol ![Kopiersymbol](images/launch-copyIcon.png), um den Einbettungscode in die Zwischenablage zu kopieren.

1. Klicken Sie auf **[!UICONTROL Schließen]**, um das Modal zu schließen.

   ![Installationssymbol](images/publishing-copyStagingCode.png)

1. Öffnen Sie die [Demosite „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html) in Ihrem Chrome-Browser.

1. Öffnen Sie die [Erweiterung Experience Cloud Debugger](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj), indem Sie auf das Symbol ![Debugger](images/icon-debugger.png) klicken.

   ![Klicken Sie auf das Debugger-Symbol](images/switchEnvironments-openDebugger.png)

1. Navigieren Sie zur Registerkarte „Tools“.

1. Im **[!UICONTROL Adobe Launch > Launch-Einbettungscode ersetzen]** Einfügen des Einbettungscodes für die Staging-Umgebung in die Zwischenablage
1. Aktivieren Sie die **[!UICONTROL Anwenden auf luma.enablementadobe.com]** switch

1. Klicken Sie auf das Diskettensymbol, um zu speichern.

   ![Tag-Umgebung im Debugger angezeigt](images/switchEnvironments-debugger-save.png)

1. Laden Sie die Registerkarte „Zusammenfassung“ des Debuggers neu und überprüfen Sie diese. Im Abschnitt &quot;Launch&quot;sollte nun angezeigt werden, dass Ihre Staging-Eigenschaft implementiert ist und Ihren Eigenschaftsnamen (d. h. &quot;Tags-Tutorial&quot;oder was auch immer Sie Ihre Eigenschaft genannt haben)!

   ![Tag-Umgebung im Debugger angezeigt](images/publishing-debugger-staging.png)

Sobald Ihr QA-Team die Änderungen in der Staging-Umgebung überprüft und bestätigt hat, können Sie sie in der Produktion veröffentlichen.

## Veröffentlichung in der Produktion

1. Navigieren Sie zur Seite [!UICONTROL Veröffentlichung].

1. Klicken Sie im Dropdown-Menü auf **[!UICONTROL Zur Veröffentlichung genehmigen]**:

   ![Zur Veröffentlichung genehmigen](images/publishing-approveForPublishing.png)

1. Klicken Sie im Dialogfeld auf die Schaltfläche **[!UICONTROL Genehmigen]**:

   ![Klicken Sie auf „Genehmigen“](images/publishing-approve.png)

1. Die Bibliothek wird jetzt in der Spalte [!UICONTROL Genehmigt] im nicht erstellten Status (gelber Punkt) angezeigt:

1. Öffnen Sie das Dropdown-Menü und wählen Sie **[!UICONTROL Erstellen und in Produktion veröffentlichen]** aus:

   ![Klicken Sie auf „Erstellen und in Produktion veröffentlichen“](images/publishing-buildAndPublishToProduction.png)

1. Klicken Sie im Dialogfeld auf **[!UICONTROL Veröffentlichen]**:

   ![Klicken Sie auf Veröffentlichen](images/publishing-publish.png)

1. Die Bibliothek wird nun in der Spalte [!UICONTROL Veröffentlicht] angezeigt:

   ![Veröffentlicht](images/publishing-published.png)

Das ist alles! Sie haben das Tutorial abgeschlossen und Ihre erste Eigenschaft in Tags veröffentlicht!
