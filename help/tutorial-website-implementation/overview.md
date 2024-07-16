---
title: Experience Cloud in Websites mit Tags implementieren
description: Die Implementierung der Experience Cloud in Websites mit Tags ist der perfekte Ausgangspunkt für Frontend-Entwickler oder technische Marketingexperten, die lernen möchten, wie die Adobe Experience Cloud-Lösungen auf ihrer Website implementiert werden.
recommendations: catalog, noDisplay
exl-id: 1b95f0b2-3062-49d1-9b0b-e6824a54008f
source-git-commit: 2483409b52562e13a4f557fe5bdec75b5afb4716
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 37%

---

# Übersicht

_Die Implementierung der Experience Cloud in Websites mit Tags_ ist der perfekte Ausgangspunkt für Frontend-Entwickler oder technische Marketingexperten, die lernen möchten, wie die Adobe Experience Cloud-Lösungen auf ihrer Website implementiert werden.

Jede Lektion enthält Anleitungen und grundlegende Informationen, die Ihnen die Implementierung von Experience Cloud und deren Vorteile näherbringen.  Innerhalb des Tutorials werden Ihnen Demosites bereitgestellt, anhand deren Sie die zugrunde liegenden Techniken in einer sicheren Umgebung erlernen können. Nach Abschluss dieses Tutorials sollten Sie bereit sein, mit der Implementierung all Ihrer Marketing-Lösungen über Tags auf Ihrer eigenen Website zu beginnen.

>[!INFO]
>
>In diesem Tutorial werden anwendungsspezifische Erweiterungen und Bibliotheken verwendet (AppMeasurement.js für Adobe Analytics, at.js für Adobe Target). Wenn Sie Adobe Experience Platform Web SDK implementieren möchten, lesen Sie das Tutorial [Adobe Experience Cloud mit Web SDK implementieren](/help/tutorial-web-sdk/overview.md) .


Nach Abschluss dieses Tutorials können Sie Folgendes:

* Tag-Eigenschaft erstellen

* Installieren einer Tag-Eigenschaft auf einer Website

* die folgenden Adobe Experience Cloud-Lösungen hinzufügen:
   * **[Adobe Experience Platform Identity-Dienst](id-service.md)**
   * **[Adobe Target](target.md)**
   * **[Adobe Analytics](analytics.md)**
   * **[Adobe Audience Manager](audience-manager.md)**

* Regeln und Datenelementen zum Senden von Daten an die Adobe-Lösungen erstellen

* Implementierung mit Adobe Experience Cloud Debugger überprüfen

* Publish-Änderungen durch Entwicklungs-, Staging- und Produktionsumgebungen

>[!NOTE]
>
>Adobe Experience Platform Launch wird als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform integriert. In der Benutzeroberfläche wurden verschiedene terminologische Änderungen eingeführt, die Sie bei der Verwendung dieses Inhalts beachten sollten:
>
> * Platform launch (Client-seitig) ist jetzt **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)**
> * Platform launch Server Side ist jetzt **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-Konfigurationen sind jetzt **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)**

>[!NOTE]
>
>Ähnliche Tutorials mit mehreren Lösungen stehen auch für [Web SDK](../tutorial-web-sdk/overview.md) und [Mobile SDK](../tutorial-mobile-sdk/overview.md) zur Verfügung.

## Voraussetzungen

In diesen Lektionen wird davon ausgegangen, dass Sie über eine Adobe ID und die erforderlichen Berechtigungen zum Ausführen der Übungen verfügen. Andernfalls müssen Sie sich an Ihren Experience Cloud-Administrator wenden, um Zugriff anzufordern.

* Für Tags müssen Sie über die Berechtigungen &quot;Entwickeln&quot;, &quot;Genehmigen&quot;, &quot;Publish&quot;, &quot;Erweiterungen verwalten&quot;und &quot;Umgebungen verwalten&quot;verfügen. Weitere Informationen zu Tag-Benutzerberechtigungen finden Sie in der [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de).
* Für Adobe Analytics müssen Sie Ihren Trackingserver kennen und wissen, welche Report Suites Sie für dieses Tutorial verwenden.
* Audience Manager: Sie müssen Ihre Audience Manager-Subdomäne kennen (auch als &quot;Partnername&quot;, &quot;Partner-ID&quot;oder &quot;Partner-Subdomäne&quot;bezeichnet).

Es wird außerdem davon ausgegangen, dass Sie mit Frontend-Entwicklungssprachen wie HTML und JavaScript vertraut sind. Sie müssen kein Experte in diesen Sprachen sein, um die Lektionen abzuschließen, aber Sie werden mehr daraus lernen, wenn Sie Code bequem lesen und verstehen können.

## Über Tags

Die Tag-Funktion von Adobe Experience Platform ist die nächste Generation der Website-Tag- und mobilen SDK-Verwaltungsfunktionen von Adobe. Mit Tags erhalten Kunden eine einfache Möglichkeit, alle Analyse-, Marketing- und Werbelösungen bereitzustellen und zu verwalten, die zur Unterstützung entsprechender Kundenerlebnisse erforderlich sind. Für Tags fallen keine zusätzlichen Gebühren an. Launch steht jedem Adobe Experience Cloud-Kunden zur Verfügung.

Mit Tags für Websites können Sie alle JavaScript zentral verwalten, die mit Analyse-, Marketing- und Werbelösungen verbunden sind, die auf Ihren Desktop- und mobilen Sites verwendet werden. Wenn Sie beispielsweise Adobe Analytics bereitstellen, verwalten Tags die AppMeasurement JavaScript-Bibliothek, füllen Variablen aus und lösen Anfragen aus.

Der Inhalt Ihres Containers wird minimiert, einschließlich Ihres benutzerspezifischen Codes. Alles ist modular. Wenn Sie ein Element nicht benötigen, ist es nicht in Ihrer Bibliothek enthalten. Das Ergebnis ist eine schnelle und kompakte Implementierung.

Tags sind außerdem eine Plattform, mit der Drittanbieter Erweiterungen erstellen können, um die Bereitstellung ihrer Lösungen über Tags zu vereinfachen. Eine Erweiterung ist ein Codepaket (JavaScript, HTML und CSS), das die Tag-Oberfläche und die Client-Funktionalität erweitert. Sie können sich Tags als Betriebssystem vorstellen, und Erweiterungen sind die Apps, mit denen Sie Ihre Aufgaben erledigen.

## Informationen zu den Lektionen

In diesen Lektionen implementieren Sie Adobe Experience Cloud in eine simulierte Einzelhandelswebsite mit dem Namen „Luma“. Die [Site „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html) verfügt über einen umfangreichen Daten-Layer und Funktionen, mit denen Sie eine realistische Implementierung erstellen können. Sie erstellen Ihre eigene Tag-Eigenschaft in Ihrer eigenen Experience Cloud-Organisation und ordnen sie mithilfe des Experience Cloud Debuggers unserer gehosteten Site &quot;Luma&quot;zu.

[![Luma-Website](images/overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)

## Die richtigen Tools

1. Da Sie einige browserspezifische Erweiterungen verwenden werden, empfehlen wir, das Tutorial mit dem [Chrome-Webbrowser](https://www.google.com/chrome/) / abzuschließen
1. Hinzufügen der Erweiterung [Adobe Experience Platform Debugger](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) zum Chrome-Browser
1. HTML-Beispielseitencode kopieren

   +++HTML-Seitencode

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
>Möglicherweise ist es einfacher, dieses Tutorial mit der in Chrome geöffneten Site &quot;Luma&quot;abzuschließen, während Sie dieses Tutorial lesen und die Schritte der Datenerfassungsoberfläche in einem anderen Browser ausführen.

Los geht‘s!

[Weiter mit &quot;Erstellen einer Tag-Eigenschaft&quot;>](create-a-property.md)
