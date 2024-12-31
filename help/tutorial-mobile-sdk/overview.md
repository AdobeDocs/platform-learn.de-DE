---
title: Tutorial-Übersicht zur Implementierung von Adobe Experience Cloud in Mobile Apps
description: Erfahren Sie, wie Sie die Mobile Apps von Adobe Experience Cloud implementieren. Dieses Tutorial führt Sie durch eine Implementierung von Experience Cloud-Anwendungen in einer Swift-Beispiel-App.
recommendations: noDisplay,catalog
last-substantial-update: 2023-11-29T00:00:00Z
exl-id: daff4214-d515-4fad-a224-f7589b685b55
source-git-commit: 0d5914ee0e63719c0439f02a5aa2a1e1c1d11a2f
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 3%

---

# Tutorial zur Implementierung von Adobe Experience Cloud in Mobile Apps

Erfahren Sie, wie Sie Adobe Experience Cloud-Programme mit dem Adobe Experience Platform Mobile SDK in Ihrer Mobile App implementieren.

Experience Platform Mobile SDK ist eine Client-seitige SDK, die es Kunden von Adobe Experience Cloud ermöglicht, über das Adobe Experience Platform-Edge Network sowohl mit Adobe-Anwendungen als auch mit Drittanbieter-Services zu interagieren. Weitere Informationen finden Sie in der Dokumentation ](https://developer.adobe.com/client-sdks/home/) Adobe Experience Platform Mobile SDK .[

![Architektur](assets/architecture.png)


Dieses Tutorial führt Sie durch die Implementierung von Platform Mobile SDK in einer Beispiel-App für den Einzelhandel namens Luma. Die [Luma-App](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) verfügt über Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Nach Abschluss dieses Tutorials sollten Sie bereit sein, alle Ihre Marketing-Lösungen über Experience Platform Mobile SDK in Ihren eigenen Mobile Apps zu implementieren.

Die Lektionen sind für iOS konzipiert und in Swift/SwiftUI geschrieben, aber viele der Konzepte gelten auch für Android™.

Nach Abschluss dieses Tutorials haben Sie folgende Möglichkeiten:

* Erstellen Sie ein Schema mit standardmäßigen und benutzerdefinierten Feldergruppen.
* Richten Sie einen Datenstrom ein.
* Konfigurieren Sie eine mobile Tag-Eigenschaft.
* Einrichten eines Experience Platform-Datensatzes (optional).
* Installieren und Implementieren von Tag-Erweiterungen in einer App.
* Experience Cloud-Parameter korrekt an eine [WebView](web-views.md) übergeben.
* Validieren Sie die Implementierung mithilfe von [Adobe Experience Platform Assurance](assurance.md).
* Fügen Sie die folgenden Adobe Experience Cloud-Programme/-Erweiterungen hinzu:
   * [Adobe Experience Platform Edge (XDM)](events.md)
   * [Lebenszyklus-Datenerfassung](lifecycle-data.md)
   * [Einverständnis](consent.md)
   * [Identität](identity.md)
   * [Profil](profile.md)
   * [Places](places.md)
   * [Analytics](analytics.md)
   * [Experience Platform](platform.md)
   * [Push-Messaging mit Journey Optimizer](journey-optimizer-push.md)
   * [In-App-Messaging mit Journey Optimizer](journey-optimizer-inapp.md)
   * [Entscheidungs-Management mit Journey Optimizer](journey-optimizer-offers.md)
   * [Target](target.md)


>[!NOTE]
>
>Ein ähnliches Tutorial mit mehreren Lösungen ist für [Web SDK](../tutorial-web-sdk/overview.md) verfügbar.

## Voraussetzungen

In diesen Lektionen wird davon ausgegangen, dass Sie über eine Adobe-ID und die erforderlichen Berechtigungen auf Benutzerebene verfügen, um die Übungen abzuschließen. Andernfalls sollten Sie sich an Ihren Adobe-Administrator wenden, um den Zugriff anzufordern.

* Bei der Datenerfassung müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Plattformen]** - Berechtigungselement **[!UICONTROL Mobile]**
   * **[!UICONTROL Eigenschaftsrechte]** - Berechtigungselemente für **[!UICONTROL Entwickeln]**, **[!UICONTROL Genehmigen]**, **[!UICONTROL Publish]**, **[!UICONTROL Erweiterungen verwalten]** und **[!UICONTROL Umgebungen verwalten]**.
   * **[!UICONTROL Unternehmensrechte]** - Berechtigungselemente für **[!UICONTROL Eigenschaften verwalten]** und, falls Sie die optionale Lektion für Push-Messaging abgeschlossen haben, **[!UICONTROL App-Konfigurationen verwalten]**

     Weitere Informationen zu Tag-Berechtigungen finden Sie unter [Benutzerberechtigungen für Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de){target="_blank"} in der Produktdokumentation.
* Beim Experience Platform müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Datenmodellierung]** - Berechtigungselemente zum Verwalten und Anzeigen von Schemas.
   * **[!UICONTROL Identity Management]** - Berechtigungselemente zum Verwalten und Anzeigen von Identity-Namespaces.
   * **[!UICONTROL Datenerfassung]** - Berechtigungselemente zum Verwalten und Anzeigen von Datenströmen.

   * Wenn Sie Kunde eines plattformbasierten Programms wie Real-Time CDP, Journey Optimizer oder Customer Journey Analytics sind und die entsprechenden Lektionen erledigen, sollten Sie auch über Folgendes verfügen:
      * **[!UICONTROL Daten-]**: Berechtigungselemente zum Verwalten und Anzeigen von Datensätzen.
      * Eine Entwicklungs **Sandbox** die Sie für dieses Tutorial verwenden können.

   * Für die Journey Optimizer-Lektionen benötigen Sie Berechtigungen zum Konfigurieren des **Push-Benachrichtigungs-**) und zum Erstellen einer **Programmoberfläche** einer **Journey**, einer **Nachricht** und **Nachrichtenvoreinstellungen**. Für das Entscheidungs-Management benötigen Sie die entsprechenden Berechtigungen zum **Verwalten von Angeboten** und **Entscheidungen** wie [hier beschrieben](https://experienceleague.adobe.com/docs/journey-optimizer/using/access-control/privacy/high-low-permissions.html?lang=en#decisions-permissions).

* Für Adobe Analytics müssen Sie wissen, welche **Report Suites** Sie verwenden können, um dieses Tutorial abzuschließen.

* Für Adobe Target benötigen Sie die Berechtigung zum Erstellen und Aktivieren von Aktivitäten.


>[!NOTE]
>
>Im Rahmen dieses Tutorials erstellen Sie Schemata, Datensätze, Identitäten usw. Wenn mehrere Personen dieses Tutorial in einer einzelnen Sandbox durchlaufen, sollten Sie beim Erstellen dieser Objekte erwägen, eine Kennung als Teil Ihrer Namenskonventionen anzuhängen oder voranzustellen. Fügen Sie beispielsweise ` - <your name or initials>` zum Namen des Objekts hinzu, das Sie erstellen sollen.

## Versionsverlauf

* 29. November 2023: Umfangreiche Überarbeitung mit neuer Beispiel-App und neuen Lektionen für In-App-Messaging, Entscheidungs-Management und Adobe Target.
* 9. März 2022: Erste Veröffentlichung

## Herunterladen der Luma-App

Zwei Versionen der Beispiel-App stehen zum Download zur Verfügung. Beide Versionen können von (GitHub[ heruntergeladen/geklont ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App). Sie finden zwei Ordner:


1. [Start](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: Ein Projekt ohne Code oder mit Platzhaltercode für den Großteil des Experience Platform Mobile SDK-Codes, den Sie verwenden müssen, um die praktischen Übungen in diesem Tutorial abzuschließen.
1. [Beenden](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: eine Version mit der vollständigen Implementierung als Referenz.

>[!NOTE]
>
>Sie verwenden iOS als Plattform, [!DNL Swift] als Programmiersprache, [!DNL SwiftUI] als UI-Framework und [!DNL Xcode] als integrierte Entwicklungsumgebung (IDE). Viele der erläuterten Implementierungskonzepte sind jedoch für andere Entwicklungsplattformen ähnlich. Viele haben dieses Tutorial bereits mit wenig oder gar keiner Erfahrung mit iOS/Swift(UI) erfolgreich abgeschlossen. Sie müssen kein Experte sein, um die Lektionen zu vervollständigen, aber Sie erhalten mehr aus den Lektionen, wenn Sie Code bequem lesen und verstehen können.


Sie können die endgültige produktbezogene Version der App von der App Store herunterladen.

[![Herunterladen](assets/download-app.svg)](https://apps.apple.com/us/app/luma-app/id6466588487)


Los geht‘s!

>[!SUCCESS]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Erstellen eines XDM-Schemas](create-schema.md)**
