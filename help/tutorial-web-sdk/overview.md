---
title: Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK
description: Erfahren Sie, wie Sie Experience Cloud-Programme mit Adobe Experience Platform Web SDK implementieren.
recommendations: catalog, noDisplay
exl-id: cf0ff74b-e81e-4f6d-ab7d-6c70e9b52d78
source-git-commit: 8602110d2b2ddc561e45f201e3bcce5e6a6f8261
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 7%

---

# Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK

Erfahren Sie, wie Sie Experience Cloud-Programme mit Adobe Experience Platform Web SDK implementieren. 

Experience Platform Web SDK ist eine Client-seitige JavaScript-Bibliothek, mit der Adobe Experience Cloud-Kunden über das Adobe Experience Platform-Edge Network sowohl mit Adobe-Anwendungen als auch mit Drittanbieterdiensten interagieren können. Weitere Informationen finden Sie unter [Übersicht über das Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge/home) .

![Experience Platform Web SDK-Architektur](assets/dc-websdk.png)

Dieses Tutorial führt Sie durch die Implementierung des Platform Web SDK auf einer Beispiel-Einzelhandelswebsite mit dem Namen Luma. Die [Site &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) verfügt über einen Rich-Data-Layer und Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Für dieses Tutorial haben Sie folgende Möglichkeiten:

* Erstellen Sie Ihre eigene Tag-Eigenschaft in Ihrem eigenen Konto mit einer Platform Web SDK-Implementierung für die Luma-Website.
* Konfigurieren Sie alle Datenerfassungsfunktionen für Web SDK-Implementierungen wie Datenspeicher, Schemas und Identitäts-Namespaces.
* Fügen Sie die folgenden Adobe Experience Cloud-Anwendungen hinzu:
   * **[Adobe Experience Platform](setup-experience-platform.md)** (und auf Platform aufbauende Anwendungen wie Adobe Real-time Customer Data Platform, Adobe Journey Optimizer und Adobe Customer Journey Analytics)
   * **[Adobe Analytics](setup-analytics.md)**
   * **[Adobe Audience Manager](setup-audience-manager.md)**
   * **[Adobe Target](setup-target.md)**
* Implementieren Sie die Ereignisweiterleitung, um die vom Web SDK erfassten Daten an Nicht-Adobe-Ziele zu senden.
* Validieren Sie Ihre eigene Platform Web SDK-Implementierung mithilfe von Experience Platform Debugger und Assurance.

Nach Abschluss dieses Tutorials sollten Sie bereit sein, mit der Implementierung all Ihrer Marketing-Anwendungen über das Platform Web SDK auf Ihrer eigenen Website zu beginnen!


>[!NOTE]
>
>Ein ähnliches Tutorial mit mehreren Lösungen ist für [Mobile SDK](../tutorial-mobile-sdk/overview.md) verfügbar.

## Voraussetzungen

Alle Experience Cloud-Kunden können das Platform Web SDK verwenden. Es ist nicht erforderlich, eine Platform-basierte Anwendung wie Real-time Customer Data Platform oder Journey Optimizer zu lizenzieren, um das Web SDK zu verwenden.

In diesen Lektionen wird davon ausgegangen, dass Sie über ein Adobe-Konto und die erforderlichen Berechtigungen zum Abschließen der Lektionen verfügen. Wenn nicht, müssen Sie sich an einen Experience Cloud-Administrator in Ihrem Unternehmen wenden, um Zugriff zu erhalten.

* Für die **Datenerfassung** müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Plattformen]**—Berechtigung für **[!UICONTROL Web]** und, falls lizenziert, **[!UICONTROL Edge]**
   * **[!UICONTROL Eigenschaftsrechte]** - Berechtigung für **[!UICONTROL Genehmigen]**, **[!UICONTROL Entwickeln]**, **[!UICONTROL Eigenschaft bearbeiten]**, **[!UICONTROL Umgebungen verwalten]**, **[!UICONTROL Erweiterungen verwalten]** und **[!UICONTROL Publish]**;
   * **[!UICONTROL Unternehmensrechte]** - Berechtigung für **[!UICONTROL Eigenschaften verwalten]**

     Weitere Informationen zu Tag-Berechtigungen finden Sie in der [Dokumentation](https://experienceleague.adobe.com/en/docs/experience-platform/tags/admin/user-permissions).

* Für **Experience Platform** müssen Sie über Folgendes verfügen:

   * Zugriff auf die Sandbox **default production**, **&quot;Prod&quot;**.
   * Zugriff auf **[!UICONTROL Schemas verwalten]** und **[!UICONTROL Schemas anzeigen]** unter **[!UICONTROL Datenmodellierung]**.
   * Zugriff auf **[!UICONTROL Identitäts-Namespaces verwalten]** und **[!UICONTROL Identitäts-Namespaces anzeigen]** unter **[!UICONTROL Identity Management]**.
   * Zugriff auf **[!UICONTROL Datenspeicher verwalten]** und **[!UICONTROL Datenspeicher anzeigen]** unter **[!UICONTROL Datenerfassung]**.
   * Wenn Sie ein Kunde einer plattformbasierten Anwendung sind und die Lektion zum Einrichten von Experience Platform](setup-experience-platform.md) abschließen, sollten Sie außerdem über Folgendes verfügen:[
      * Zugriff auf eine Sandbox vom Typ **development**.
      * Alle Berechtigungselemente unter **[!UICONTROL Datenverwaltung]** und **[!UICONTROL Profilverwaltung]**:

     Die erforderlichen Funktionen sollten für alle Experience Cloud-Kunden verfügbar sein, auch wenn Sie keine plattformbasierte Anwendung wie Real-Time CDP verwenden.

     Weitere Informationen zur Zugriffskontrolle auf Platform finden Sie in der [Dokumentation](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home).

* Für die optionale Lektion **Adobe Analytics** müssen Sie über [Administratorzugriff auf Report Suite-Einstellungen, Verarbeitungsregeln und Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-console/home) verfügen.

* Für die optionale Lektion **Adobe Target** müssen Sie über den Zugriff [Bearbeiter oder Genehmiger](https://experienceleague.adobe.com/en/docs/target/using/administer/manage-users/enterprise/properties-overview#section_8C425E43E5DD4111BBFC734A2B7ABC80) verfügen.

* Für die optionale Lektion **Audience Manager** müssen Sie Zugriff haben, um Eigenschaften, Segmente und Ziele erstellen, lesen und schreiben zu können. Weiterführende Informationen finden Sie im Tutorial zur rollenbasierten Zugriffskontrolle des Audience Managers [.](https://experienceleague.adobe.com/en/docs/audience-manager-learn/tutorials/setup-and-admin/user-management/setting-permissions-with-role-based-access-control)


>[!NOTE]
>
>Es wird davon ausgegangen, dass Sie mit Frontend-Entwicklungssprachen wie HTML und JavaScript vertraut sind. Sie müssen kein Experte für diese Sprachen sein, aber Sie erhalten mehr aus diesem Tutorial, wenn Sie Code lesen und verstehen können.

## Updates

* 24. April 2024: Wichtige Updates, einschließlich Hinzufügen der Variablen &quot;Set Variable/Update Variable&quot;, Aufspaltung von Personalisierungs- und Analyseanforderungen, Journey Optimizer-Lektionen

## Laden der Website Luma

Laden Sie die [Luma-Website](https://luma.enablementadobe.com/content/luma/us/en.html){target="blank"} in eine separate Browser-Registerkarte und markieren Sie sie mit einem Lesezeichen, damit Sie sie bei Bedarf während des Tutorials einfach laden können. Sie benötigen keinen zusätzlichen Zugriff auf Luma, außer dass Sie unsere gehostete Produktions-Site laden können.

[![Luma-Website](assets/old-overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html){target="blank"}

Los geht‘s!

[Weiter: ](configure-schemas.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
