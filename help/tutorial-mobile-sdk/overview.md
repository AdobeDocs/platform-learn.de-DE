---
title: Tutorial zur Implementierung von Adobe Experience Cloud in Apps - Überblick
description: Erfahren Sie, wie Sie die mobilen Adobe Experience Cloud-Anwendungen implementieren. Dieses Tutorial führt Sie durch eine Implementierung von Experience Cloud-Anwendungen in einer Swift-Beispielanwendung.
recommendations: noDisplay,catalog
last-substantial-update: 2023-11-29T00:00:00Z
exl-id: daff4214-d515-4fad-a224-f7589b685b55
source-git-commit: 0d5914ee0e63719c0439f02a5aa2a1e1c1d11a2f
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 3%

---

# Tutorial zur Implementierung von Adobe Experience Cloud in Apps

Erfahren Sie, wie Sie Adobe Experience Cloud-Programme mit dem Adobe Experience Platform Mobile SDK in Ihrer Mobile App implementieren.

Experience Platform Mobile SDK ist ein Client-seitiges SDK, mit dem Adobe Experience Cloud-Kunden über das Adobe Experience Platform-Edge Network sowohl mit Adobe-Anwendungen als auch mit Drittanbieterdiensten interagieren können. Weitere Informationen finden Sie in der Dokumentation zum Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) .[

![Architektur](assets/architecture.png)


Dieses Tutorial führt Sie durch die Implementierung des Platform Mobile SDK in einer Beispiel-Einzelhandelsanwendung namens Luma. Die [Luma-App](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) verfügt über Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Nach Abschluss dieses Tutorials sollten Sie bereit sein, mit der Implementierung all Ihrer Marketing-Lösungen über das Experience Platform Mobile SDK in Ihre eigenen mobilen Apps zu beginnen.

Die Lektionen sind für iOS konzipiert und in Swift/SwiftUI geschrieben, aber viele der Konzepte gelten auch für Android™.

Nach Abschluss dieses Tutorials können Sie:

* Erstellen Sie ein Schema mit standardmäßigen und benutzerdefinierten Feldergruppen.
* Richten Sie einen Datenspeicher ein.
* Konfigurieren Sie eine mobile Tag-Eigenschaft.
* Einrichten eines Experience Platform-Datensatzes (optional).
* Installieren und implementieren Sie Tag-Erweiterungen in einer App.
* Übergeben Sie die Experience Cloud-Parameter ordnungsgemäß an eine [webview](web-views.md).
* Validieren Sie die Implementierung mit [Adobe Experience Platform Assurance](assurance.md).
* Fügen Sie die folgenden Adobe Experience Cloud-Anwendungen/Erweiterungen hinzu:
   * [Adobe Experience Platform Edge (XDM)](events.md)
   * [Erfassung der Lebenszyklusdaten](lifecycle-data.md)
   * [Einverständnis](consent.md)
   * [Identität](identity.md)
   * [Profil](profile.md)
   * [Places](places.md)
   * [Analytics](analytics.md)
   * [Experience Platform](platform.md)
   * [Push-Nachrichten mit Journey Optimizer](journey-optimizer-push.md)
   * [In-App-Messaging mit Journey Optimizer](journey-optimizer-inapp.md)
   * [Entscheidungsverwaltung mit Journey Optimizer](journey-optimizer-offers.md)
   * [Target](target.md)


>[!NOTE]
>
>Ein ähnliches Tutorial mit mehreren Lösungen ist für [Web SDK](../tutorial-web-sdk/overview.md) verfügbar.

## Voraussetzungen

In diesen Lektionen wird davon ausgegangen, dass Sie über eine Adobe ID und die erforderlichen Berechtigungen auf Benutzerebene zum Abschließen der Übungen verfügen. Wenn nicht, sollten Sie sich an Ihren Adobe-Administrator wenden, um Zugriff anzufordern.

* In der Datenerfassung müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Plattformen]**—Berechtigungselement **[!UICONTROL Mobil]**
   * **[!UICONTROL Eigenschaftsrechte]** - Berechtigungselemente für **[!UICONTROL Entwickeln]**, **[!UICONTROL Genehmigen]**, **[!UICONTROL Publish]**, **[!UICONTROL Erweiterungen verwalten]** und **[!UICONTROL Umgebungen verwalten]**.
   * **[!UICONTROL Firmenrechte]** - Berechtigungselemente zu **[!UICONTROL Eigenschaften verwalten]** und, wenn Sie die optionale Lektion zur Push-Benachrichtigung abschließen, **[!UICONTROL App-Konfigurationen verwalten]**

     Weitere Informationen zu Tag-Berechtigungen finden Sie unter [Benutzerberechtigungen für Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de){target="_blank"} in der Produktdokumentation.
* Unter Experience Platform müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Datenmodellierung]** - Berechtigungselemente zum Verwalten und Anzeigen von Schemas.
   * **[!UICONTROL Identity Management]**: Berechtigungselemente zum Verwalten und Anzeigen von Identitäts-Namespaces.
   * **[!UICONTROL Datenerfassung]**: Berechtigungselemente zum Verwalten und Anzeigen von Datenspeichern.

   * Wenn Sie Kunde einer Platform-basierten Anwendung wie Real-Time CDP, Journey Optimizer oder Customer Journey Analytics sind und die entsprechenden Lektionen ausführen, sollten Sie auch Folgendes haben:
      * **[!UICONTROL Datenverwaltung]** - Berechtigungselemente zum Verwalten und Anzeigen von Datensätzen.
      * Eine Entwicklungs- **Sandbox** , die Sie für dieses Tutorial verwenden können.

   * Für die Journey Optimizer-Lektionen benötigen Sie Berechtigungen zum Konfigurieren des **Push-Benachrichtigungsdiensts** und zum Erstellen einer **App-Oberfläche**, einer **Journey**, einer **Nachricht** und einer **Nachrichtenvorgabe**. Für die Entscheidungsverwaltung benötigen Sie die entsprechenden Berechtigungen, um **Angebote verwalten** und **Entscheidungen** zu können, wie in [hier](https://experienceleague.adobe.com/docs/journey-optimizer/using/access-control/privacy/high-low-permissions.html?lang=en#decisions-permissions) beschrieben.

* Für Adobe Analytics müssen Sie wissen, welche **Report Suites** Sie zum Abschluss dieses Tutorials verwenden können.

* Für Adobe Target müssen Sie über die Berechtigung zum Erstellen und Aktivieren von Aktivitäten verfügen.


>[!NOTE]
>
>Im Rahmen dieses Tutorials erstellen Sie Schemas, Datensätze, Identitäten usw. Wenn mehrere Personen dieses Tutorial in einer Sandbox durchlaufen, sollten Sie beim Erstellen dieser Objekte erwägen, eine Identifizierung als Teil Ihrer Benennungskonventionen anzuhängen oder voranzustellen. Fügen Sie beispielsweise ` - <your name or initials>` zum Namen des Objekts hinzu, das Sie erstellen sollen.

## Versionsverlauf

* 29. November 2023: Umfassende Überarbeitung mit einer neuen Beispielanwendung und neuen Lektionen für In-App-Nachrichten, Entscheidungsmanagement und Adobe Target.
* 9. März 2022: Erste Veröffentlichung

## Herunterladen der Luma-App

Zwei Versionen der Beispiel-App können heruntergeladen werden. Beide Versionen können von [Github](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) heruntergeladen/geklont werden. Es gibt zwei Ordner:


1. [Start](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: ein Projekt ohne Code oder Platzhaltercode für den Großteil des Experience Platform Mobile SDK-Codes, den Sie zum Abschließen der praktischen Übungen in diesem Tutorial benötigen.
1. [Beenden](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: eine Version mit der vollständigen Implementierung als Referenz.

>[!NOTE]
>
>Sie verwenden iOS als Plattform, [!DNL Swift] als Programmiersprache, [!DNL SwiftUI] als UI-Framework und [!DNL Xcode] als integrierte Entwicklungsumgebung (IDE). Viele der erläuterten Implementierungskonzepte sind jedoch für andere Entwicklungsplattformen ähnlich. Viele haben dieses Tutorial bereits erfolgreich abgeschlossen, ohne dass zuvor ein iOS/Swift(UI)-Erlebnis vorhanden war. Sie müssen kein Experte sein, um die Lektionen abzuschließen, aber Sie erhalten mehr aus den Lektionen, wenn Sie Code bequem lesen und verstehen können.


Sie können die fertige, produktionierte Version des Programms von der App Store herunterladen.

[![Download](assets/download-app.svg)](https://apps.apple.com/us/app/luma-app/id6466588487)


Los geht‘s!

>[!SUCCESS]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu zukünftigen Inhalten haben möchten, teilen Sie diese in diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Erstellen eines XDM-Schemas](create-schema.md)**
