---
title: Hinzufügen des Einbettungs-Codes
description: Erfahren Sie, wie Sie die Einbettungs-Codes Ihrer Tag-Eigenschaft abrufen und in Ihrer Website implementieren können. Diese Lektion ist Teil des Tutorials Implementieren von Experience Cloud in Websites .
exl-id: a2959553-2d6a-4c94-a7df-f62b720fd230
source-git-commit: 1fc027db2232c8c56de99d12b719ec10275b590a
workflow-type: tm+mt
source-wordcount: '1069'
ht-degree: 43%

---

# Hinzufügen des Einbettungs-Codes

In dieser Lektion implementieren Sie den asynchronen Einbettungs-Code der Entwicklungsumgebung Ihrer Tag-Eigenschaft. Auf dem Weg lernen Sie zwei Hauptkonzepte von Tags kennen: Umgebungen und Einbettungs-Codes.


>[!WARNING]
>
> Die in diesem Tutorial verwendete Luma-Website wird voraussichtlich in der Woche vom 16. Februar 2026 ersetzt. Die im Rahmen dieses Tutorials durchgeführten Arbeiten sind möglicherweise nicht auf die neue Website anwendbar.

>[!NOTE]
>
>Adobe Experience Platform Launch wird als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform integriert. In der Benutzeroberfläche wurden mehrere terminologische Änderungen eingeführt, die Sie bei der Verwendung dieses Inhalts beachten sollten:
>
> * Platform Launch (Client-seitig) ist jetzt **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)**
> * Platform Launch Server Side ist jetzt **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-Konfigurationen sind jetzt **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de)**

## Lernziele

Am Ende dieser Lektion können Sie:

* Abrufen des Einbettungs-Codes für die Tag-Eigenschaft
* den Unterschied zwischen einer Entwicklungs-, Staging- und Produktionsumgebung erläutern
* Hinzufügen eines Tag-Einbettungs-Codes zu einem HTML-Dokument
* Erklären Sie die optimale Position des Tag-Einbettungs-Codes in Bezug auf anderen Code im `<head>` eines HTML-Dokuments

## Kopieren des Einbettungs-Codes

Der Einbettungs-Code ist ein `<script>`-Tag, das Sie auf Ihren Web-Seiten einfügen, um die in Tags erstellte Logik zu laden und auszuführen. Wenn Sie die Bibliothek asynchron laden, lädt der Browser weiterhin die Seite, ruft die Tag-Bibliothek ab und führt sie parallel aus. In diesem Fall ist nur ein Einbettungs-Code vorhanden, den Sie in den `<head>` einfügen. (Wenn Tags synchron bereitgestellt werden, gibt es zwei Einbettungs-Codes, einen, den Sie in die `<head>` einfügen, und einen anderen, den Sie vor die `</body>` stellen.)

Klicken Sie im Eigenschaftenübersichtsbildschirm im linken Navigationsbereich auf **[!UICONTROL Umgebungen]**, um zur Seite „Umgebungen“ zu gelangen. Beachten Sie, dass die Entwicklungs-, Staging- und Produktionsumgebungen für Sie erstellt wurden.

![Klicken Sie auf „Umgebungen“ in der oberen Navigationsleiste](images/launch-environments.png)

Diese Umgebungen entsprechen den typischen Phasen im Prozess der Code-Entwicklung und -Veröffentlichung. Der Code wird zuerst von einem Entwickler in einer Entwicklungsumgebung geschrieben. Wenn sie ihre Arbeit abgeschlossen haben, senden sie den Code an eine Staging-Umgebung, in der QA- und andere Teams ihn überprüfen können. Sobald die QA und andere Teams zufrieden sind, wird der Code dann in der Produktionsumgebung veröffentlicht. Dies ist die öffentlich zugängliche Umgebung, die Besucher beim Aufrufen Ihrer Website nutzen.

Tags ermöglichen zusätzliche Entwicklungsumgebungen, was in großen Organisationen nützlich ist, in denen mehrere Entwickler gleichzeitig an verschiedenen Projekten arbeiten.

Dies sind die einzigen Umgebungen, die wir zum Abschluss des Tutorials benötigen. Umgebungen ermöglichen es Ihnen, verschiedene funktionierende Versionen Ihrer Tag-Bibliotheken unter verschiedenen URLs zu hosten, sodass Sie neue Funktionen sicher hinzufügen und sie den richtigen Benutzern (z. B. Entwicklern, QA-Technikern, der Öffentlichkeit usw.) zur richtigen Zeit zur Verfügung stellen können.

Kopieren wir nun den Einbettungs-Code:

1. Klicken Sie in **[!UICONTROL Zeile]** Entwicklung“ auf das Symbol „Installieren![ (](images/launch-installIcon.png)), um das Modal zu öffnen.

1. Beachten Sie, dass Tags standardmäßig auf die asynchronen Einbettungs-Codes gesetzt werden

1. Klicken Sie auf das Kopiersymbol ![Kopiersymbol](images/launch-copyIcon.png), um den Einbettungs-Code in die Zwischenablage zu kopieren.

1. Klicken Sie auf **[!UICONTROL Schließen]**, um das Modal zu schließen.

   ![Installationssymbol](images/launch-copyInstallCode.png)

## Implementieren des Einbettungs-Codes im `<head>` der HTML-Beispielseite

Der Einbettungs-Code sollte im `<head>`-Element aller HTML-Seiten implementiert werden, die die Eigenschaft gemeinsam nutzen werden. Möglicherweise verfügen Sie über eine oder mehrere Vorlagendateien, die die `<head>` auf der gesamten Site global steuern. Dies macht das Hinzufügen von Tags zu einem unkomplizierten Prozess.

Falls noch nicht geschehen, kopieren Sie den Beispiel-HTML-Seiten-Code und fügen Sie ihn in einen Code-Editor ein. [Brackets](https://brackets.io/) ist ein kostenloser Open-Source-Editor, falls Sie einen benötigen.

+++HTML-Seiten-Code als Beispiel

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

Ersetzen Sie den vorhandenen Einbettungs-Code in Zeile 34 (oder den umliegenden Zeilen) durch den Code in der Zwischenablage und speichern Sie die Seite. Öffnen Sie die Seite jetzt in einem Webbrowser. Wenn Sie die Seite mit dem `file://`-Protokoll laden, müssen Sie in Ihrem Code-Editor „https:“ am Anfang der Einbettungscode-URL hinzufügen). Die Zeilen 33 bis 36 Ihrer Beispielseite sollten etwa wie folgt aussehen:

```html
    <!--Tags Header Embed Code: REPLACE LINE 39 WITH THE EMBED CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="https://assets.adobedtm.com/launch-ENa21cfed3f06f4ddf9690de8077b39e81-development.min.js" async></script>
    <!--/Tags Header Embed Code-->
```

Öffnen Sie die Entwicklertools Ihres Webbrowsers und rufen Sie die Registerkarte „Netzwerk“ auf. An dieser Stelle sollte ein 404-Fehler für die Tag-Umgebungs-URL angezeigt werden:
![404-Fehler](images/samplepage-404.png)

Der 404-Fehler wird erwartet, da Sie noch keine Bibliothek in dieser Tags-Umgebung erstellt haben. Hierzu kommen wir in der nächsten Lektion. Wenn anstelle eines 404-Fehlers die Meldung „Fehlgeschlagen“ angezeigt wird, haben Sie wahrscheinlich vergessen, das `https://`-Protokoll im Einbettungs-Code hinzuzufügen. Sie müssen das `https://`-Protokoll nur angeben, wenn Sie die Beispielseite mit dem `file://`-Protokoll laden. Nehmen Sie die Änderung vor und laden Sie die Seite neu, bis der 404-Fehler angezeigt wird.

## Best Practices für die Implementierung von Tags

Sehen wir uns einige der Best Practices für die Implementierung von Tags an, die auf der Beispielseite demonstriert werden:

* **Datenschicht**:

   * Es *dringend*, auf Ihrer Site eine Datenschicht zu erstellen, die alle Attribute enthält, die zum Ausfüllen von Variablen in Analytics, Target und anderen Marketing-Lösungen erforderlich sind. Diese Beispielseite enthält nur eine sehr einfache Datenschicht. Eine echte Datenschicht kann viele weitere Details über Seite, Besucher, Warenkorbdetails usw. enthalten. Weitere Informationen zu Datenschichten finden Sie in [Customer Experience Digital Data Layer 1.0](https://www.w3.org/2013/12/ceddl-201312.pdf).

   * Definieren Sie Ihre Datenschicht vor dem Tag-Einbettungs-Code, um zu maximieren, was Sie mit Experience Cloud-Lösungen tun können.

* **JavaScript Helper-Bibliotheken**: Wenn Sie bereits eine Bibliothek wie JQuery im `<head>` Ihrer Seiten implementiert haben, laden Sie sie vor Tags, um ihre Syntax in Tags und Target zu nutzen

* **HTML5-Doctype**: Der HTML5-Doctype ist für Target erforderlich.

* **Vorabladen und DNS-Vorabruf**: Verwenden Sie diese Funktionen, um die Seitenladezeit zu optimieren. Siehe auch: [/https://w3c.github.io/resource-hints/](https://w3c.github.io/resource-hints/)

* **pre-hiding Snippet for asynchronous Target implementation**: Sie erfahren mehr darüber in der Target-Lektion, aber wenn Target über asynchrone Tag-Einbettungs-Codes bereitgestellt wird, sollten Sie ein pre-hiding Snippet auf Ihren Seiten vor den Tag-Einbettungs-Codes hartcodieren, um das Flackern von Inhalten zu verwalten

Im Folgenden finden Sie eine Zusammenfassung dieser Best Practices in der empfohlenen Reihenfolge. Beachten Sie, dass es einige Platzhalter für kontospezifische Details gibt:

```html
<!doctype html>
<html lang="en">
<head>
    <title>Basic Demo</title>
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
    <!--prehiding snippet for Adobe Target with asynchronous tags deployment-->
    <script>
        (function(g,b,d,f){(function(a,c,d){if(a){var e=b.createElement("style");e.id=c;e.innerHTML=d;a.appendChild(e)}})(b.getElementsByTagName("head")[0],"at-body-style",d);setTimeout(function(){var a=b.getElementsByTagName("head")[0];if(a){var c=b.getElementById("at-body-style");c&&a.removeChild(c)}},f)})(window,document,"body {opacity: 0 !important}",3E3);
    </script>
    <!--/prehiding snippet for Adobe Target with asynchronous tags deployment-->
    <!--Tags Header Embed Code: REPLACE LINE 39 WITH THE INSTALL CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
    <!--/Tags Header Embed Code-->
</head>
<body>
    <h1>Tags Basic Demo</h1>
    <p>This is a very simple page to demonstrate basic concepts of tags</p>
</body>
</html>
```

Jetzt wissen Sie, wie Sie den Tag-Einbettungs-Code zu Ihrer Site hinzufügen!

[Weiter: „Hinzufügen eines Datenelements, einer Regel und einer Bibliothek“ >](add-data-elements-rules.md)
