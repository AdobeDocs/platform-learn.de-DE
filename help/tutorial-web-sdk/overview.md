---
title: Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK
description: Erfahren Sie, wie Sie Experience Cloud-Programme mit dem Adobe Experience Platform Web SDK implementieren.
recommendations: catalog, noDisplay
exl-id: cf0ff74b-e81e-4f6d-ab7d-6c70e9b52d78
source-git-commit: cf0193e3aae4d6536c868f078f4773ee14e90408
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 26%

---

# Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK

Erfahren Sie, wie Sie Experience Cloud-Programme mit dem Adobe Experience Platform Web SDK implementieren.

Experience Platform Web SDK ist eine Client-seitige JavaScript-Bibliothek, mit der Adobe Experience Cloud-Kunden über das Adobe Experience Platform Edge Network sowohl mit Adobe Apps als auch mit Drittanbieterdiensten interagieren können. Siehe [Übersicht über das Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de) für detailliertere Informationen.

Dieses Tutorial führt Sie durch die Implementierung des Platform Web SDK auf einer Beispiel-Einzelhandelswebsite mit dem Namen Luma. Die [](https://luma.enablementadobe.com/content/luma/us/en.html)Luma-Website verfügt über eine umfangreiche Datenschicht und Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Nach Abschluss dieses Tutorials sollten Sie bereit sein, mit der Implementierung all Ihrer Marketing-Lösungen über das Platform Web SDK auf Ihrer eigenen Website zu beginnen.

[![Website „Luma“](assets/old-overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)


## Lernziele

Nach Abschluss des Tutorials können Sie:

* Konfigurieren von Datenströmen

* Erstellen von XDM-Schemata

* Fügen Sie die folgenden Adobe Experience Cloud-Anwendungen hinzu:
   * **[Adobe Experience Platform](setup-experience-platform.md)** (und auf Platform aufbauende Anwendungen wie Adobe Real-time Customer Data Platform, Adobe Journey Optimizer und Adobe Customer Journey Analytics)
   * **[Adobe Analytics](setup-analytics.md)**
   * **[Adobe Audience Manager](setup-audience-manager.md)**
   * **[Adobe Target](setup-target.md)**

* Erstellen von Tag-Regeln und XDM-Objektdatenelementen zum Senden von Daten an Adobe Apps

* Validieren der Implementierung mit dem Adobe Experience Platform Debugger

* Erfassen der Benutzerzustimmung

* Weiterleiten von Daten an Dritte mit Ereignisweiterleitung

>[!NOTE]
>
>Ein ähnliches Tutorial mit mehreren Lösungen steht für [Mobile SDK](../tutorial-mobile-sdk/overview.md).

## Voraussetzungen

Alle Experience Cloud-Kunden können das Platform Web SDK verwenden. Es ist nicht erforderlich, eine Platform-basierte Anwendung wie Real-time Customer Data Platform oder Journey Optimizer zu lizenzieren, um das Web SDK zu verwenden.

In diesen Lektionen wird davon ausgegangen, dass Sie über ein Adobe-Konto und die [erforderliche Berechtigungen](configure-permissions.md) um die Lektionen abzuschließen. Wenn nicht, müssen Sie sich an Ihren Experience Cloud-Administrator wenden, um Zugriff anzufordern.

Es wird außerdem davon ausgegangen, dass Sie mit Frontend-Entwicklungssprachen wie HTML und JavaScript vertraut sind. Sie müssen kein Experte für diese Sprachen sein, aber Sie erhalten mehr aus diesem Tutorial, wenn Sie Code lesen und verstehen können.

Los geht‘s!

[Weiter: ](configure-permissions.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
