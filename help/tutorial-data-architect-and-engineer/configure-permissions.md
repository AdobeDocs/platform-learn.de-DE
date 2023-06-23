---
title: Berechtigungen konfigurieren
seo-title: Configure permissions | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Berechtigungen konfigurieren
description: In dieser Lektion konfigurieren Sie Adobe Experience Platform-Benutzerberechtigungen anhand der Admin Console der Adobe.
role: Data Architect, Data Engineer
feature: Access Control
jira: KT-4348
thumbnail: 4348-configure-permissions.jpg
exl-id: ca01f99e-f10c-4bf0-bef2-b011ac29a565
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 4%

---

# Berechtigungen konfigurieren

<!--30min-->

In dieser Lektion konfigurieren Sie Adobe Experience Platform-Benutzerberechtigungen mithilfe von [!DNL Adobe's Admin Console] und [!UICONTROL Berechtigungen] in der Platform-Oberfläche angezeigt.

Die Zugriffskontrolle ist eine wichtige Datenschutzfunktion in Experience Platform. Wir empfehlen, die Berechtigungen auf das für die Ausführung der Arbeitsaufgaben erforderliche Minimum zu beschränken. Siehe [Dokumentation zur Zugriffssteuerung](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html) für weitere Informationen.

Datenarchitekten und Dateningenieure sind leistungsstarke Benutzer von Adobe Experience Platform und Sie benötigen viele Berechtigungen, um dieses Tutorial und später in Ihrer täglichen Arbeit abzuschließen. Datenarchitekten sind wahrscheinlich an der Verwaltung von *andere Platform-Benutzer* in ihrem Unternehmen, z. B. Marketingexperten, Analysten und Datenwissenschaftler. Überlegen Sie sich, wie Sie diese Funktionen verwenden können, um andere Benutzer in Ihrem Unternehmen zu verwalten.

**Datenarchitekten** häufig Berechtigungen für andere Benutzer außerhalb dieses Tutorials konfigurieren.

>[!IMPORTANT]
>
>Ein Systemadministrator von Adobe Experience Cloud-Produkten muss einige der Schritte in dieser Lektion ausführen, die in den Abschnittsüberschriften beschrieben wird. Wenn Sie kein Systemadministrator sind, wenden Sie sich an einen Mitarbeiter in Ihrem Unternehmen und bitten Sie ihn, diese Aufgaben auszuführen. Es gibt auch eine Aufgabe, die sie während der [Einrichten von Developer Console und Postman](set-up-developer-console-and-postman.md) Lektion.

## Über die Admin Console

Die [!DNL Admin Console] ist die Benutzeroberfläche, über die der Benutzerzugriff auf alle Adobe Experience Cloud-Produkte verwaltet wird. Für den Zugriff auf Platform müssen Benutzer oder der Admin Console hinzugefügt werden. Anschließend werden alle detaillierten Berechtigungselemente im Bildschirm &quot;Berechtigungen&quot;von Adobe Experience Platform verwaltet.


Im Folgenden finden Sie eine kurze Zusammenfassung der Rollen, die für Platform vorhanden sind:

* **Benutzer** eines Produktprofils kann Aufgaben in der Benutzeroberfläche von Platform entsprechend den im Produktprofil zugewiesenen Berechtigungen ausführen.
* **Entwickler** kann API-Anmeldeinformationen und -Projekte in der Adobe Developer-Konsole erstellen, um mit der Verwendung der Experience Platform API zu beginnen
* **Produktadministratoren** Sie können Benutzer und Entwickler zum Adobe Experience Platform-Produkt in der Adobe Admin Console hinzufügen und granularen Benutzerzugriff im Bildschirm &quot;Berechtigungen&quot;der Platform-Oberfläche verwalten.
* **Systemadministratoren** kann Produktadministratoren hinzufügen und im Wesentlichen alle Berechtigungen für alle Adobe Experience Cloud-Produkte verwalten.

## Hinzufügen von Benutzern und Entwicklern zum `AEP-Default-All-Users` Produktprofil (erfordert einen Systemadministrator oder einen Produktadministrator)

In dieser Übung fügen Sie als Systemadministrator oder Produktadministrator Sie als Benutzer und Entwickler zum Adobe Experience Platform-Produkt von Adobe Admin Console hinzu.

>[!NOTE]
>
>Wenn Sie ein Systemadministrator sind, der einen Kollegen unterstützt, der dieses Tutorial durchführt, sollten Sie erwägen, Ihren Kollegen als *Produktadministrator* für Adobe Experience Platform. Als Produktadministrator können sie diese Schritte selbst durchführen und in Zukunft andere Experience Platform-Benutzer verwalten.

So fügen Sie den Tutorial-Teilnehmer als [!UICONTROL Benutzer] und [!UICONTROL Entwickler]:

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com)
1. Auswählen **[!UICONTROL Produkte]** in der oberen Navigation
1. Auswählen **Adobe Experience Platform**
   ![Adobe Experience Platform auswählen](assets/adminconsole-experiencePlatform.png)
1. Möglicherweise haben Sie in Ihrer Experience Platform-Instanz bereits mehrere Profile. Wählen Sie die `AEP-Default-All-Users` profile
   ![Neues Profil hinzufügen](assets/adminconsole-newProfile.png)

1. Navigieren Sie zu **[!UICONTROL Benutzer]** tab
1. Wählen Sie die **[!UICONTROL Benutzer hinzufügen]** button
   ![Benutzer hinzufügen](assets/adminconsole-addUser.png)
1. Schließen Sie den Workflow ab, um den Tutorial-Teilnehmer als Benutzer zum Produktprofil hinzuzufügen.

1. Navigieren Sie zu **[!UICONTROL Entwickler]** tab
1. Wählen Sie die **[!UICONTROL Entwickler hinzufügen]** button
   ![Benutzer hinzufügen](assets/adminconsole-addDeveloper.png)
1. Schließen Sie den Workflow ab, um den Tutorial-Teilnehmer als Entwickler zum Produktprofil hinzuzufügen.


## Eine Rolle in Adobe Experience Platform hinzufügen (Systemadministrator oder Produktadministrator erforderlich)

Die detaillierten Berechtigungen für die Experience Platform werden im Bildschirm &quot;Berechtigungen&quot;der Platform-Benutzeroberfläche verwaltet. Nur System- und Produktadministratoren haben Zugriff auf diesen Bildschirm. Wenn Sie also keine Administratorrechte haben, benötigen Sie Hilfe von jemandem, der dies tut.

Berechtigungen werden in Rollen verwaltet. Erstellen Sie eine Rolle für das Tutorial:

1. Anmelden [Adobe Experience Platform](https://platform.adobe.com)
1. Auswählen **[!UICONTROL Berechtigungen]** in der linken Navigation, die Sie zum [!UICONTROL Rollen] Bildschirm
1. Auswählen **[!UICONTROL Rolle erstellen]**

   ![Rollen in Experience Platform erstellen](assets/permissions-addRole.png)
1. Benennen Sie die Rolle. `Luma Tutorial Platform` (Fügen Sie am Ende den Namen des Tutorial-Teilnehmers hinzu, wenn mehrere Personen aus Ihrem Unternehmen dieses Tutorial absolvieren) und wählen Sie **[!UICONTROL Bestätigen]**

   ![Rollen in Experience Platform erstellen](assets/permissions-nameRole.png)


1. Fügen Sie alle Berechtigungselemente für die folgenden Ressourcen hinzu, indem Sie  **[!UICONTROL +]** und **[!UICONTROL Alle hinzufügen]**:

   1. Datenmodellierung
   1. Data Management
   1. Profilverwaltung
   1. Identitäts-Management
   1. Sandbox-Verwaltung
   1. Abfrage-Service
   1. Datenerfassung
   1. Data Governance
   1. Dashboards
   1. Warnhinweise

      ![Berechtigungselemente hinzufügen](assets/permissions-addPermissionItems.png)

1. Fügen Sie unter Datenerfassung die Berechtigungselemente Quellen verwalten und Quellen anzeigen hinzu.

1. Nachdem Sie alle Berechtigungselemente hinzugefügt haben, klicken Sie auf die Schaltfläche Speichern .
   ![Berechtigungselemente speichern](assets/permissions-savePermissions.png)

Sie werden nach dem [Sandbox erstellen](create-a-sandbox.md) und [Einrichten von Developer Console und Postman](set-up-developer-console-and-postman.md) Unterricht.

## Erstellen eines Datenerfassungs-Produktprofils (erfordert einen Systemadministrator oder einen Produktadministrator)

In dieser Übung erstellen Sie oder ein Systemadministrator in Ihrem Unternehmen ein Produktprofil für die Datenerfassung (ehemals Adobe Experience Platform Launch) und fügen Sie Sie als Produktprofiladministrator hinzu.

>[!NOTE]
>
>Wenn Sie ein Systemadministrator sind, der einen Kollegen bei diesem Tutorial unterstützt, sollten Sie sie als *Produktadministrator* für die Datenerfassung. Als Produkt-Administrator können sie diese Schritte selbst durchführen und in Zukunft andere Benutzer der Datenerfassung verwalten.

So erstellen Sie das Produktprofil:

1. Im [!DNL Adobe Admin Console] Wechseln Sie zum Adobe Experience Platform-Datenerfassungsprodukt.
1. Fügen Sie ein neues Profil mit dem Namen `Luma Tutorial Data Collection` (Fügen Sie am Ende den Namen des Tutorial-Teilnehmers hinzu, wenn mehrere Personen aus Ihrem Unternehmen dieses Tutorial absolvieren)
1. Deaktivieren Sie die **[!UICONTROL Eigenschaften]** > **[!UICONTROL Automatisch einschließen]** Einstellung
1. Weisen Sie zu diesem Zeitpunkt keine Eigenschaften oder Berechtigungen zu
1. Fügen Sie den Tutorial-Teilnehmer als Administrator dieses Profils hinzu.

Nachdem Sie diese Schritte ausgeführt haben, sollten Sie sehen, dass die `Luma Tutorial Data Collection` Profil mit einem Administrator eingerichtet.
![Erstelltes Datenerfassungsprofil](assets/adminconsole-dc-profileCreated.png)

## Konfigurieren des Datenerfassungs-Produktprofils

Jetzt, da Sie Administrator der `Luma Tutorial Data Collection` Produktprofil können Sie die Berechtigungen und Rollen konfigurieren, die Sie zum Abschluss des Tutorials benötigen.

### Hinzufügen von Berechtigungen

Nun fügen Sie dem Profil die einzelnen Berechtigungselemente hinzu:

1. Im [Adobe Admin Console](https://adminconsole.adobe.com), gehen Sie zu **[!UICONTROL Produkte]** > **[!UICONTROL Datenerfassung]**
1. Öffnen Sie die `Luma Tutorial Data Collection` profile
1. Navigieren Sie zu **[!UICONTROL Berechtigungen]** tab
1. Öffnen **[!UICONTROL Plattformen]**
1. Stellen Sie sicher, dass alle verfügbaren Plattformen ausgewählt sind (je nach Lizenz werden Ihnen möglicherweise unterschiedliche Optionen angezeigt)
1. **[!UICONTROL Speichern]** Sie die Änderungen
   ![Plattformen hinzufügen](assets/adminconsole-launch-addPlatforms.png)
1. Öffnen **[!UICONTROL Eigenschaften]**
1. Stellen Sie sicher, dass **[!UICONTROL Automatisch einschließen]** -Umschalter ist aus, sodass Sie keinen Zugriff auf Eigenschaften haben (wir fügen später eine hinzu)
1. **[!UICONTROL Speichern]** Sie die Änderungen
   ![Eigenschaften entfernen](assets/adminconsole-launch-removeProperties.png)
1. Öffnen **[!UICONTROL Eigenschaftsrechte]**
1. Auswählen **[!UICONTROL Alle hinzufügen]** , um alle Eigenschaftsberechtigungen hinzuzufügen
1. **[!UICONTROL Speichern Sie]**
   ![Eigenschaften entfernen](assets/adminconsole-launch-addPropertyRights.png)
1. Öffnen **[!UICONTROL Unternehmensrechte]**
1. Hinzufügen **[!UICONTROL Eigenschaften verwalten]**
1. Wählen Sie **[!UICONTROL Speichern]** aus
   ![Eigenschaften entfernen](assets/adminconsole-launch-companyRights.png)


### Fügen Sie sich selbst als Benutzer hinzu

Fügen Sie sich jetzt als Benutzer dem Datenerfassungsprofil hinzu:

1. Navigieren Sie zu **[!UICONTROL Benutzer]** tab
1. Wählen Sie die **[!UICONTROL Benutzer hinzufügen]** button
   ![Benutzer hinzufügen](assets/adminconsole-launch-addUser.png)
1. Schließen Sie den Workflow ab, um sich selbst als Benutzer zum Produktprofil hinzuzufügen.

Sie müssen sich nicht selbst als Entwickler für die Datenerfassung hinzufügen.

Jetzt verfügen Sie über fast alle Berechtigungen, die zum Abschließen des Tutorials erforderlich sind. Es gibt nur noch zwei weitere Stärken, die Sie im [!DNL Adobe Admin Console], einschließlich eines nach Ihnen [Sandbox erstellen](create-a-sandbox.md)!
