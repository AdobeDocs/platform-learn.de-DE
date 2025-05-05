---
title: Implementieren des Experience Cloud in Websites mit Tags
description: Die Implementierung des Experience Cloud in Websites mit Tags ist der perfekte Ausgangspunkt für Frontend-Entwickler oder technische Marketing-Experten, die lernen möchten, wie die Adobe Experience Cloud-Lösungen auf ihrer Website implementiert werden.
recommendations: catalog, noDisplay
exl-id: 1b95f0b2-3062-49d1-9b0b-e6824a54008f
source-git-commit: 2483409b52562e13a4f557fe5bdec75b5afb4716
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 37%

---

# Übersicht

_Implementieren des Experience Cloud in Websites mit Tags_ ist der perfekte Ausgangspunkt für Frontend-Entwickler oder technische Marketing-Experten, die lernen möchten, wie die Adobe Experience Cloud-Lösungen auf ihrer Website implementiert werden.

Jede Lektion enthält Anleitungen und grundlegende Informationen, die Ihnen die Implementierung von Experience Cloud und deren Vorteile näherbringen.  Innerhalb des Tutorials werden Ihnen Demosites bereitgestellt, anhand deren Sie die zugrunde liegenden Techniken in einer sicheren Umgebung erlernen können. Nach Abschluss dieses Tutorials sollten Sie bereit sein, alle Ihre Marketing-Lösungen über Tags auf Ihrer eigenen Website zu implementieren.

>[!INFO]
>
>In diesem Tutorial werden anwendungsspezifische Erweiterungen und Bibliotheken verwendet (AppMeasurement.js für Adobe Analytics, at.js für Adobe Target). Wenn Sie Adobe Experience Platform Web SDK implementieren möchten, lesen Sie das Tutorial [Implementieren von Adobe Experience Cloud mit Web SDK](/help/tutorial-web-sdk/overview.md) .


Nach Abschluss dieses Tutorials können Sie Folgendes:

* Erstellen einer Tag-Eigenschaft

* Installieren einer Tag-Eigenschaft auf einer Website

* die folgenden Adobe Experience Cloud-Lösungen hinzufügen:
   * **[Adobe Experience Platform Identity Service](id-service.md)**
   * **[Adobe Target](target.md)**
   * **[Adobe Analytics](analytics.md)**
   * **[Adobe Audience Manager](audience-manager.md)**

* Regeln und Datenelementen zum Senden von Daten an die Adobe-Lösungen erstellen

* Implementierung mit Adobe Experience Cloud Debugger überprüfen

* Publish verändert sich durch Entwicklungs-, Staging- und Produktionsumgebungen

>[!NOTE]
>
>Adobe Experience Platform Launch wird als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform integriert. In der Benutzeroberfläche wurden mehrere terminologische Änderungen eingeführt, die Sie bei der Verwendung dieses Inhalts beachten sollten:
>
> * Platform launch (Client-seitig) ist jetzt **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)**
> * Platform launch Server Side ist jetzt **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-Konfigurationen sind jetzt **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)**

>[!NOTE]
>
>Ähnliche Tutorials mit mehreren Lösungen stehen auch für [Web SDK](../tutorial-web-sdk/overview.md) und [Mobile SDK](../tutorial-mobile-sdk/overview.md) zur Verfügung.

## Voraussetzungen

In diesen Lektionen wird davon ausgegangen, dass Sie über eine Adobe ID und die erforderlichen Berechtigungen zum Ausführen der Übungen verfügen. Andernfalls müssen Sie sich an Ihren Experience Cloud-Administrator wenden, um Zugriff anzufordern.

* Für Tags müssen Sie über die Berechtigung zum Entwickeln, Genehmigen, Publish, Verwalten von Erweiterungen und Verwalten von Umgebungen verfügen. Weitere Informationen zu Tag-Benutzerberechtigungen finden Sie unter [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de).
* Für Adobe Analytics müssen Sie Ihren Trackingserver kennen und wissen, welche Report Suites Sie für dieses Tutorial verwenden.
* Für den Audience Manager müssen Sie Ihre Audience Manager-Subdomain kennen (auch als „Partnername“, „Partnerkennung“ oder „Partnersubdomain“ bezeichnet)

Es wird außerdem davon ausgegangen, dass Sie mit Frontend-Entwicklungssprachen wie HTML und JavaScript vertraut sind. Sie müssen kein Experte in diesen Sprachen sein, um den Unterricht abzuschließen, aber Sie werden mehr aus ihnen herausholen, wenn Sie Code bequem lesen und verstehen können.

## Über Tags

Die Tags-Funktion von Adobe Experience Platform umfasst die nächste Generation von Adobe-Verwaltungsfunktionen für Website-Tags und mobile SDK. Tags bietet Kunden eine einfache Möglichkeit, alle Analyse-, Marketing- und Werbelösungen bereitzustellen und zu verwalten, die für relevante Kundenerlebnisse erforderlich sind. Für Tags fallen keine zusätzlichen Kosten an. Launch steht jedem Adobe Experience Cloud-Kunden zur Verfügung.

Mit Tags für Websites können Sie alle JavaScript-Lösungen für Analyse-, Marketing- und Werbelösungen, die auf Ihren Desktop- und mobilen Sites verwendet werden, zentral verwalten. Wenn Sie beispielsweise Adobe Analytics bereitstellen, verwalten Tags die AppMeasurement-JavaScript-Bibliothek, füllen Variablen auf und lösen Anfragen aus.

Der Inhalt Ihres Containers wird minimiert, einschließlich Ihres benutzerspezifischen Codes. Alles ist modular. Wenn Sie ein Element nicht benötigen, ist es nicht in Ihrer Bibliothek enthalten. Das Ergebnis ist eine schnelle und kompakte Implementierung.

Tags ist auch eine Plattform, über die Drittanbieter Erweiterungen erstellen können, um die Bereitstellung ihrer Lösungen über Tags zu vereinfachen. Eine Erweiterung ist ein Codepaket (JavaScript, HTML und CSS), das die Tags-Oberfläche und die Client-Funktionalität erweitert. Sie können sich Tags wie ein Betriebssystem vorstellen, bei dem Erweiterungen die Programme sind, mit denen Sie Ihre Aufgaben erledigen.

## Informationen zu den Lektionen

In diesen Lektionen implementieren Sie Adobe Experience Cloud in eine simulierte Einzelhandelswebsite mit dem Namen „Luma“. Die [Site „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html) verfügt über einen umfangreichen Daten-Layer und Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Sie erstellen Ihre eigene Tag-Eigenschaft in Ihrem eigenen Experience Cloud-Unternehmen und ordnen sie mithilfe des Experience Cloud Debuggers unserer gehosteten Luma-Site zu.

[![Luma-Website](images/overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)

## Die richtigen Tools

1. Da Sie einige browserspezifische Erweiterungen verwenden werden, empfehlen wir, das Tutorial mit dem [Chrome-Webbrowser](https://www.google.com/chrome/) / abzuschließen
1. Fügen Sie die Erweiterung {0[&#128279;](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)Adobe Experience Platform Debugger} zu Ihrem Chrome-Browser hinzu
1. Kopieren Sie den HTML-Beispiel-Seiten-Code

   +++HTML-Beispiel-Seiten-Code

   ```html
   <!doctype html>
   <html lang="en">
   <head>
       <title>Tags: Sample HTML Page</title>
       <!--Preconnect and DNS-Prefetch to improve page load time. REPLACE "techmarketingdemos" WITH YOUR OWN AAM PARTNER ID, TARGET CLIENT CODE, AND ANALYTICS TRACKING SERVER-->
       <link rel="preconnect" href="//dpm.demdex.net">
       <link rel="preconnect" href="//fast.techmarketingdemos.demdex.net">
       <link rel="preconnect" href="//techmarketingdemos.demdex.net">
       <link rel="preconnect" href="//cm.everesttech.net">
       <link rel="preconnect" href="//techmarketingdemos.tt.omtrdc.net">
       <link rel="preconnect" href="//techmarketingdemos.sc.omtrdc.net">
       <link rel="dns-prefetch" href="//dpm.demdex.net">
       <link rel="dns-prefetch" href="//fast.techmarketingdemos.demdex.net">
       <link rel="dns-prefetch" href="//techmarketingdemos.demdex.net">
       <link rel="dns-prefetch" href="//cm.everesttech.net">
       <link rel="dns-prefetch" href="//techmarketingdemos.tt.omtrdc.net">
       <link rel="dns-prefetch" href="//techmarketingdemos.sc.omtrdc.net">
       <!--/Preconnect and DNS-Prefetch-->
       <!--Data Layer to enable rich data collection and targeting-->
       <script>
       var digitalData = {
           "page": {
               "pageInfo" : {
                   "pageName": "Home"
                   }
               }
       };
       </script>
       <!--/Data Layer-->
       <!--jQuery or other helper libraries-->
       <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
       <!--/jQuery-->
       <!--Tags Header Embed Code: REPLACE THE NEXT LINE WITH THE EMBED CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
       <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
       <!--/Tags Header Embed Code-->
   </head>
   <body>
       <h1>Tags: Sample HTML Page</h1>
       <p>This is a very simple page to demonstrate basic implementation concepts of Tags</p>
       <p>See <a href="https://docs.adobe.com/content/help/en/experience-cloud/implementing-in-websites-with-launch/index.html">Implementing the Experience Cloud in Websites with Tags</a> for the complete tutorial</p>
   </body>
   </html>
   ```

   +++

1. Installieren Sie einen Texteditor, in dem Sie Änderungen an der HTML-Beispielseite vornehmen können. (Wenn Sie keinen haben, sollten Sie [Brackets](https://brackets.io/) ausprobieren.)
1. Setzen Sie ein Lesezeichen für die [Site „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html).

>[!NOTE]
>
>Möglicherweise finden Sie es einfacher, dieses Tutorial abzuschließen, wenn die Luma-Site in Chrome geöffnet ist, während Sie dieses Tutorial lesen und die Schritte zur Datenerfassungs-Oberfläche in einem anderen Browser durchführen.

Los geht‘s!

[Weiter „Tag-Eigenschaft erstellen“ >](create-a-property.md)
