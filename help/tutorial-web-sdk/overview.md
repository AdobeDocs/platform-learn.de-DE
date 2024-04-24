---
title: Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK
description: Erfahren Sie, wie Sie Experience Cloud-Anwendungen mit dem Adobe Experience Platform Web SDK implementieren.
recommendations: catalog, noDisplay
exl-id: cf0ff74b-e81e-4f6d-ab7d-6c70e9b52d78
source-git-commit: 100a6a9ac8d580b68beb7811f99abcdc0ddefd1a
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 4%

---

# Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK

Erfahren Sie, wie Sie Experience Cloud-Anwendungen mit dem Adobe Experience Platform Web SDK implementieren.

Experience Platform Web SDK ist eine Client-seitige JavaScript-Bibliothek, die es Adobe Experience Cloud-Kunden ermöglicht, über das Adobe Experience Platform-Edge Network sowohl mit Adobe-Anwendungen als auch mit Drittanbieterdiensten zu interagieren. Siehe [Übersicht über das Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de) für detailliertere Informationen.

![Experience Platform Web SDK-Architektur](assets/dc-websdk.png)

Dieses Tutorial führt Sie durch die Implementierung des Platform Web SDK auf einer Beispiel-Einzelhandelswebsite mit dem Namen Luma. Die [Site &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) verfügt über eine umfangreiche Datenschicht und Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Für dieses Tutorial haben Sie folgende Möglichkeiten:

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
>Ein ähnliches Tutorial mit mehreren Lösungen steht für [Mobile SDK](../tutorial-mobile-sdk/overview.md).

## Voraussetzungen

Alle Experience Cloud-Kunden können das Platform Web SDK verwenden. Es ist nicht erforderlich, eine Platform-basierte Anwendung wie Real-time Customer Data Platform oder Journey Optimizer zu lizenzieren, um das Web SDK zu verwenden.

In diesen Lektionen wird davon ausgegangen, dass Sie über ein Adobe-Konto und die erforderlichen Berechtigungen zum Abschließen der Lektionen verfügen. Wenn nicht, müssen Sie sich an einen Experience Cloud-Administrator in Ihrem Unternehmen wenden, um Zugriff zu erhalten.

* Für **Datenerfassung**, müssen Sie über Folgendes verfügen:
   * **[!UICONTROL Plattformen]**—permission for **[!UICONTROL Web]** und, falls lizenziert, **[!UICONTROL Edge]**
   * **[!UICONTROL Eigenschaftsrechte]**—permission to **[!UICONTROL Genehmigen]**, **[!UICONTROL Entwickeln]**, **[!UICONTROL Eigenschaft bearbeiten]**, **[!UICONTROL Verwalten von Umgebungen]**, **[!UICONTROL Verwalten von Erweiterungen]**, und **[!UICONTROL Veröffentlichen]**,
   * **[!UICONTROL Unternehmensrechte]**—permission to **[!UICONTROL Eigenschaften verwalten]**

     Weitere Informationen zu Berechtigungen für Tags finden Sie unter [die Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de).

* Für **Experience Platform**, müssen Sie über Folgendes verfügen:

   * Zugriff auf **Standardproduktion**, **&quot;Prod&quot;** Sandbox.
   * Zugriff auf **[!UICONTROL Verwalten von Schemas]** und **[!UICONTROL Anzeigen von Schemas]** under **[!UICONTROL Datenmodellierung]**.
   * Zugriff auf **[!UICONTROL Verwalten von Identitäts-Namespaces]** und **[!UICONTROL Anzeigen von Identitäts-Namespaces]** under **[!UICONTROL Identity Management]**.
   * Zugriff auf **[!UICONTROL Verwalten von Datenspeichern]** und **[!UICONTROL Anzeigen von Datenspeichern]** under **[!UICONTROL Datenerfassung]**.
   * Wenn Sie Kunde einer Platform-basierten Anwendung sind und die [Experience Platform einrichten](setup-experience-platform.md) Lektion sollten Sie auch:
      * Zugriff auf einen **development** Sandbox.
      * Alle Berechtigungselemente unter **[!UICONTROL Data Management]**, und **[!UICONTROL Profilverwaltung]**:

     Die erforderlichen Funktionen sollten für alle Experience Cloud-Kunden verfügbar sein, auch wenn Sie keine plattformbasierte Anwendung wie Real-Time CDP verwenden.

     Weitere Informationen zur Zugriffskontrolle auf Platform finden Sie unter [die Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html?lang=de).

* Für das optionale **Adobe Analytics** Lektion, müssen Sie [Administratorzugriff auf Report Suite-Einstellungen, Verarbeitungsregeln und Analysis Workspace](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

* Für das optionale **Adobe Target** Lektion, müssen Sie [Bearbeiter oder Genehmiger](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html#section_8C425E43E5DD4111BBFC734A2B7ABC80) Zugriff.

* Für das optionale **Audience Manager** -Lektion erstellen, lesen und schreiben Sie Eigenschaften, Segmente und Ziele. Weitere Informationen finden Sie im Tutorial zu [Rollenbasierte Zugriffssteuerung des Audience Managers](https://experienceleague.adobe.com/docs/audience-manager-learn/tutorials/setup-and-admin/user-management/setting-permissions-with-role-based-access-control.html?lang=en).


>[!NOTE]
>
>Es wird davon ausgegangen, dass Sie mit Frontend-Entwicklungssprachen wie HTML und JavaScript vertraut sind. Sie müssen kein Experte für diese Sprachen sein, aber Sie erhalten mehr aus diesem Tutorial, wenn Sie Code lesen und verstehen können.

## Updates

* 24. April 2024: Größere Aktualisierung, einschließlich Hinzufügen der Variablen &quot;Set Variable/Update Variable&quot;, Aufspaltung von Personalisierungs- und Analyseanforderungen, Journey Optimizer-Lektionen

## Laden der Website Luma

Laden Sie die [Luma-Website](https://luma.enablementadobe.com/content/luma/us/en.html){target="blank"} in einem separaten Browser-Tab und mit einem Lesezeichen versehen, damit Sie es bei Bedarf während des Tutorials einfach laden können. Sie benötigen keinen zusätzlichen Zugriff auf Luma, außer dass Sie unsere gehostete Produktions-Site laden können.

[![Luma-Website](assets/old-overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html){target="blank"}

Los geht‘s!

[Weiter: ](configure-schemas.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
