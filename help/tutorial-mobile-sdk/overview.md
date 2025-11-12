---
title: Tutorial zur Implementierung von Adobe Experience Cloud in Mobile Apps
description: Erfahren Sie, wie Sie die Mobile Apps von Adobe Experience Cloud implementieren. Dieses Tutorial führt Sie durch eine Implementierung von Experience Cloud-Programmen in einer Swift- oder Android-Beispielanwendung.
recommendations: noDisplay,catalog
last-substantial-update: 2023-11-29T00:00:00Z
exl-id: daff4214-d515-4fad-a224-f7589b685b55
source-git-commit: 342bb7efbe868622c4bc08e02568bce948fed61c
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 1%

---

# Tutorial zur Implementierung von Adobe Experience Cloud in Mobile Apps

Erfahren Sie, wie Sie Adobe Experience Cloud-Anwendungen mit Adobe Experience Platform Mobile SDK in Ihrer Mobile App implementieren.

Experience Platform Mobile SDK ist eine Client-seitige SDK, die es Kunden von Adobe Experience Cloud ermöglicht, sowohl mit Adobe-Anwendungen als auch mit Drittanbieter-Services über Adobe Experience Platform Edge Network zu interagieren. Weitere Informationen finden Sie in der Dokumentation [ Adobe Experience Platform Mobile SDK .](https://developer.adobe.com/client-sdks/home/)

![Architektur](assets/architecture.png){zoomable="yes"}


Dieses Tutorial führt Sie durch die Implementierung von Platform Mobile SDK in einer Beispielanwendung namens Luma. Die Luma-App verfügt über Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Nachdem Sie dieses Tutorial abgeschlossen haben, sollten Sie bereit sein, alle Ihre Marketing-Lösungen über Experience Platform Mobile SDK in Ihren eigenen Mobile Apps zu implementieren.

Die Unterrichtsstunden sind für Folgendes ausgelegt:

* iOS unter Verwendung der Programmiersprache Swift und des SwiftUI-Frameworks.
* Android unter Verwendung der Programmiersprache Kotlin und Java und des JetPack Compose-Frameworks.

Nach Abschluss dieses Tutorials haben Sie folgende Möglichkeiten:

* Erstellen Sie ein Schema mit standardmäßigen und benutzerdefinierten Feldergruppen.
* Richten Sie einen Datenstrom ein.
* Konfigurieren Sie eine mobile Tag-Eigenschaft.
* Einrichten eines Experience Platform-Datensatzes (optional).
* Installieren und Implementieren von Tag-Erweiterungen in einer App.
* Richtige Übergabe der Experience Cloud-Parameter an eine [WebView](web-views.md).
* Validieren Sie die Implementierung mithilfe von [Adobe Experience Platform Assurance](assurance.md).
* Fügen Sie die folgenden Adobe Experience Cloud-Programme oder -Erweiterungen hinzu:
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
   * [Ziel](target.md)


>[!NOTE]
>
>Ein ähnliches Tutorial mit mehreren Lösungen ist für [Web SDK](../tutorial-web-sdk/overview.md) verfügbar.

## Berechtigungen

In diesen Lektionen wird davon ausgegangen, dass Sie über eine Adobe-ID und die erforderlichen Berechtigungen auf Benutzerebene verfügen, um die Übungen abzuschließen. Wenn nicht, wenden Sie sich an Ihren Adobe-Administrator, um Zugriff anzufordern.

* Bei der Datenerfassung müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Plattformen]** - Berechtigungselement **[!UICONTROL Mobile]**
   * **[!UICONTROL Eigenschaftsrechte]** - Berechtigungselemente für **[!UICONTROL Entwickeln]**, **[!UICONTROL Genehmigen]**, **[!UICONTROL Veröffentlichen]**, **[!UICONTROL Erweiterungen verwalten]** und **[!UICONTROL Umgebungen verwalten]**.
   * **[!UICONTROL Unternehmensrechte]** - Berechtigungselemente für **[!UICONTROL Eigenschaften verwalten]**

     Weitere Informationen zu Tag-Berechtigungen finden Sie unter [Benutzerberechtigungen für Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/admin/user-permissions){target="_blank"} in der Produktdokumentation.
* In Experience Platform müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Datenmodellierung]** - Berechtigungselemente zum Verwalten und Anzeigen von Schemas.
   * **[!UICONTROL Identity Management]** - Berechtigungselemente zum Verwalten und Anzeigen von Identity-Namespaces.
   * **[!UICONTROL Datenerfassung]** - Berechtigungselemente zum Verwalten und Anzeigen von Datenströmen.

   * Wenn Sie Kunde eines plattformbasierten Programms wie Real-Time CDP, Journey Optimizer oder Customer Journey Analytics sind und planen, die entsprechenden Lektionen durchzuführen, sollten Sie auch über Folgendes verfügen:
      * **[!UICONTROL Daten-]**: Berechtigungselemente zum Verwalten und Anzeigen von Datensätzen.
      * Eine Entwicklungs **Sandbox** die Sie für dieses Tutorial verwenden können.

   * Für die Journey Optimizer-Lektionen benötigen Sie Berechtigungen zum Konfigurieren des **Push-Benachrichtigungs-**) und zum Erstellen einer **Programmoberfläche** einer **Journey**, einer **Nachricht** und **Nachrichtenvoreinstellungen**. Darüber hinaus benötigen Sie für das Entscheidungs-Management die entsprechenden Berechtigungen zum **Verwalten von Angeboten** und **Entscheidungen**, wie unter [Berechtigungsebenen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/access-control/high-low-permissions) beschrieben.

* Für Adobe Analytics müssen Sie wissen, welche **Report Suites** Sie verwenden können, um dieses Tutorial abzuschließen.

* Für Adobe Target benötigen Sie die Berechtigung zum Erstellen und Aktivieren von Aktivitäten.


>[!NOTE]
>
>Im Rahmen dieses Tutorials erstellen Sie Schemata, Datensätze, Identitäten usw. Wenn mehrere Personen dieses Tutorial in einer einzelnen Sandbox durchlaufen, sollten Sie beim Erstellen dieser Objekte erwägen, eine Kennung als Teil Ihrer Namenskonventionen anzuhängen oder voranzustellen. Fügen Sie beispielsweise ` - <your name or initials>` zum Namen des Objekts hinzu, das Sie erstellen sollen.

## Versionsverlauf

* &#x200B;9. September 2025:
   * Android-Version der App mit zugehörigen Anweisungen.
   * Aktualisierungen für Änderungen an der Programmoberfläche und der Kampagnenfunktion in Journey Optimizer.
* &#x200B;29. November 2023: Umfangreiche Überarbeitung mit neuer Beispiel-App und neuen Lektionen für In-App-Messaging, Entscheidungs-Management und Adobe Target.
* &#x200B;9. März 2022: Erste Veröffentlichung

## Herunterladen der Luma-App

>[!BEGINTABS]

>[!TAB iOS]

Zwei Versionen der Beispiel-App stehen zum Download zur Verfügung. Beide Versionen können von (GitHub[ heruntergeladen/geklont ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App). Es gibt zwei Ordner:

1. [Start](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: Ein Projekt ohne Code oder mit Platzhaltercode für den Großteil des Experience Platform Mobile SDK-Codes, den Sie verwenden müssen, um die praktischen Übungen in diesem Tutorial abzuschließen.
1. [Beenden](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: eine Version mit der vollständigen Implementierung als Referenz.

Sie verwenden iOS als Plattform, [!DNL Swift] als Programmiersprache, [!DNL SwiftUI] als UI-Framework und [!DNL Xcode] als integrierte Entwicklungsumgebung (IDE). Viele der erläuterten Implementierungskonzepte sind jedoch für andere Entwicklungsplattformen ähnlich. Viele haben dieses Tutorial bereits mit wenig oder gar keiner Erfahrung in der iOS- und Swift(UI)-Entwicklung erfolgreich abgeschlossen. Sie müssen kein Experte sein, um die Lektionen zu vervollständigen, aber Sie erhalten mehr aus den Lektionen, wenn Sie Code bequem lesen und verstehen können.

Sie können die endgültige produktbezogene Version der App von der App Store herunterladen.

[![Herunterladen](assets/download-app.svg)](https://apps.apple.com/us/app/luma-app/id6466588487)

>[!TAB Android]

Zwei Versionen der Beispiel-App stehen zum Download zur Verfügung. Beide Versionen können von (GitHub[ heruntergeladen oder geklont ](https://github.com/adobe/Luma-Android). Es gibt zwei Ordner:

1. [Start](https://github.com/adobe/Luma-Android){target="_blank"}: Ein Projekt ohne Code oder mit Platzhaltercode für den Großteil des Experience Platform Mobile SDK-Codes, den Sie verwenden müssen, um die praktischen Übungen in diesem Tutorial abzuschließen.
1. [Beenden](https://github.com/adobe/Luma-Android){target="_blank"}: eine Version mit der vollständigen Implementierung als Referenz.

Sie verwenden Android als Plattform, [!DNL Kotlin]+[!DNL Java] als Programmiersprache, [!DNL JetPack Compose] als UI-Framework und [!DNL Android Studio] als integrierte Entwicklungsumgebung (IDE). Viele der erläuterten Implementierungskonzepte sind jedoch für andere Entwicklungsplattformen ähnlich. Viele haben dieses Tutorial bereits mit wenig bis gar keiner Erfahrung in Android / Kotlin+Java / JetPack Compose erfolgreich abgeschlossen. Sie müssen kein Experte sein, um die Lektionen zu vervollständigen, aber Sie erhalten mehr aus den Lektionen, wenn Sie Code bequem lesen und verstehen können.

Wenn Sie es vorziehen, können [ aus Google Play an einem Test für eine produktbezogene Version ](https://play.google.com/apps/internaltest/4700642199234438150) App teilnehmen.


>[!ENDTABS]

Los geht‘s!

>[!SUCCESS]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Erstellen eines XDM-Schemas](create-schema.md)**
