---
title: Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK
description: 'Erfahren Sie, wie Sie Experience Cloud-Programme mit Adobe Experience Platform Web SDK implementieren. '
recommendations: catalog, noDisplay
exl-id: cf0ff74b-e81e-4f6d-ab7d-6c70e9b52d78
source-git-commit: 1fc027db2232c8c56de99d12b719ec10275b590a
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 7%

---

# Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK

Erfahren Sie, wie Sie Experience Cloud-Programme mit Adobe Experience Platform Web SDK implementieren. 

Experience Platform Web SDK ist eine Client-seitige JavaScript-Bibliothek, die es Kunden von Adobe Experience Cloud ermöglicht, sowohl mit Adobe-Anwendungen als auch mit Drittanbieter-Services über Adobe Experience Platform Edge Network zu interagieren. Adobe Experience Platform Weitere Informationen finden Sie unter [Übersicht über &#x200B;](https://experienceleague.adobe.com/de/docs/experience-platform/edge/home) Web SDK.

![Architektur von Experience Platform Web SDK](assets/dc-websdk.png)

Dieses Tutorial führt Sie durch die Implementierung von Platform Web SDK auf einer Beispiel-Website für den Einzelhandel namens Luma. Die [Luma-Site](https://luma.enablementadobe.com/content/luma/us/en.html) verfügt über eine umfangreiche Datenschicht und Funktionen, mit denen Sie eine realistische Implementierung erstellen können. In diesem Tutorial haben Sie folgende Möglichkeiten:

* Erstellen Sie Ihre eigene Tag-Eigenschaft in Ihrem eigenen Konto mit einer Platform Web SDK-Implementierung für die Luma-Website.
* Konfigurieren Sie alle Datenerfassungsfunktionen für Web-SDK-Implementierungen wie Datenströme, Schemata und Identity-Namespaces.
* Fügen Sie die folgenden Adobe Experience Cloud-Programme hinzu:
   * **[Adobe Experience Platform](setup-experience-platform.md)** (und auf Platform aufbauende Anwendungen wie Adobe Real-Time Customer Data Platform, Adobe Journey Optimizer und Adobe Customer Journey Analytics)
   * **[Adobe Analytics](setup-analytics.md)**
   * **[Adobe Audience Manager](setup-audience-manager.md)**
   * **[Adobe Target](setup-target.md)**
* Implementieren Sie die Ereignisweiterleitung, um die von Web SDK erfassten Daten an Ziele zu senden, die nicht mit Adobe verbunden sind.
* Validieren Sie Ihre eigene Implementierung von Platform Web SDK mit Experience Platform Debugger und Assurance.

Nach Abschluss dieses Tutorials sollten Sie bereit sein, alle Ihre Marketing-Programme über Platform Web SDK auf Ihrer eigenen Website zu implementieren!


>[!NOTE]
>
>Ein ähnliches Tutorial mit mehreren Lösungen ist für [Mobile SDK](../tutorial-mobile-sdk/overview.md) verfügbar.

## Voraussetzungen

Alle Experience Cloud-Kunden können Platform Web SDK verwenden. Es ist nicht erforderlich, eine plattformbasierte Anwendung wie Real-Time Customer Data Platform oder Journey Optimizer für die Verwendung von Web SDK zu lizenzieren.

In diesen Lektionen wird davon ausgegangen, dass Sie über ein Adobe-Konto und die erforderlichen Berechtigungen zum Abschließen der Lektionen verfügen. Andernfalls müssen Sie sich an einen Experience Cloud-Administrator in Ihrem Unternehmen wenden, um Zugriff zu erhalten.

* Für **Datenerfassung** müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Plattformen]** - Berechtigung für **[!UICONTROL Web]** und, falls lizenziert, **[!UICONTROL Edge]**
   * **[!UICONTROL Eigenschaftsrechte]** - Berechtigung zum **[!UICONTROL Genehmigen]**, **[!UICONTROL Entwickeln]**, **[!UICONTROL Eigenschaft bearbeiten]**, **[!UICONTROL Umgebungen verwalten]**, **[!UICONTROL Erweiterungen]** und **[!UICONTROL Veröffentlichen]**,
   * **[!UICONTROL Unternehmensrechte]** - Berechtigung zum **[!UICONTROL Verwalten von Eigenschaften]**

     Weitere Informationen zu Tag-Berechtigungen finden Sie unter [Dokumentation](https://experienceleague.adobe.com/de/docs/experience-platform/tags/admin/user-permissions).

* Für **Experience Platform** ist Folgendes erforderlich:

   * Zugriff auf die Sandbox **Standardproduktion**, **„Produktion“**.
   * Zugriff auf **[!UICONTROL Schemata verwalten]** und **[!UICONTROL Schemata anzeigen]** unter **[!UICONTROL Datenmodellierung]**.
   * Zugriff auf **[!UICONTROL Identity-Namespaces verwalten]** und **[!UICONTROL Identity-Namespaces]** **[!UICONTROL Identity Management]**.
   * Zugriff auf **[!UICONTROL Datenströme verwalten]** und **[!UICONTROL Datenströme anzeigen]** unter **[!UICONTROL Datenerfassung]**.
   * Wenn Sie Kunde einer Platform-basierten Anwendung sind und die Lektion [Einrichten von Experience Platform](setup-experience-platform.md) abschließen, sollten Sie auch über Folgendes verfügen:
      * Zugriff auf eine **Entwicklungs**-Sandbox.
      * Alle Berechtigungselemente unter **[!UICONTROL Datenverwaltung]** und **[!UICONTROL Profilverwaltung]**:

     Die erforderlichen Funktionen sollten für alle Experience Cloud-Kunden verfügbar sein, auch wenn Sie nicht Kunde einer plattformbasierten Anwendung wie Real-Time CDP sind.

     Weitere Informationen zur Platform-Zugriffssteuerung finden Sie unter [Dokumentation](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home).

* Für die optionale Lektion **Adobe Analytics** benötigen Sie [Administratorzugriff auf Report Suite-Einstellungen, Verarbeitungsregeln und Analysis Workspace](https://experienceleague.adobe.com/de/docs/analytics/admin/admin-console/home)

* Für die optionale Lektion **Adobe Target** benötigen Sie [Editor- oder &#x200B;](https://experienceleague.adobe.com/de/docs/target/using/administer/manage-users/enterprise/properties-overview#section_8C425E43E5DD4111BBFC734A2B7ABC80)).

* Für die optionale Lektion **Audience Manager** benötigen Sie Zugriff zum Erstellen, Lesen und Schreiben von Eigenschaften, Segmenten und Zielen. Weitere Informationen finden Sie im Tutorial zur rollenbasierten Zugriffssteuerung in Audience Manager[.](https://experienceleague.adobe.com/de/docs/audience-manager-learn/tutorials/setup-and-admin/user-management/setting-permissions-with-role-based-access-control)


>[!NOTE]
>
>Es wird davon ausgegangen, dass Sie mit Frontend-Entwicklungssprachen wie HTML und JavaScript vertraut sind. Sie müssen kein Experte in diesen Sprachen sein, aber Sie erhalten mehr aus diesem Tutorial, wenn Sie Code lesen und verstehen können.

## Updates

* &#x200B;24. April 2024: Wichtige Updates, einschließlich des Hinzufügens von „Variable festlegen“/„Variable aktualisieren“, Aufspaltungs-Personalisierungs- und Analytics-Anfragen, Journey Optimizer-Lektionen

## Laden der Luma-Website


>[!WARNING]
>
> Die in diesem Tutorial verwendete Luma-Website wird voraussichtlich in der Woche vom 16. Februar 2026 ersetzt. Die im Rahmen dieses Tutorials durchgeführten Arbeiten sind möglicherweise nicht auf die neue Website anwendbar.

Laden Sie die [Luma-Website](https://luma.enablementadobe.com/content/luma/us/en.html){target="blank"} in eine separate Browser-Registerkarte und setzen Sie ein Lesezeichen dafür, damit Sie sie während des Tutorials bei Bedarf einfach laden können. Sie benötigen keinen zusätzlichen Zugriff auf Luma, außer dass Sie unsere gehostete Produktions-Site laden können.

[![Luma-Website](assets/old-overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html){target="blank"}

Los geht‘s!

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996?profile.language=de)
