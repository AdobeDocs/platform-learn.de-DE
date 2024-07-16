---
title: WebSDK-Implementierungen mit Experience Platform Assurance validieren
description: Erfahren Sie, wie Sie Ihre Platform Web SDK-Implementierung mit Adobe Experience Platform Assurance validieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Tags,Assurance
jira: KT-15406
exl-id: 31e381ea-fbaf-495f-a6e9-2ff6c0d36939
source-git-commit: a8431137e0551d1135763138da3ca262cb4bc4ee
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 7%

---

# WebSDK-Implementierungen mit Experience Platform Assurance validieren

Adobe Experience Platform Assurance ist eine Funktion, mit der Sie die Datenerfassung und Bereitstellung von Erlebnissen überprüfen, testen, simulieren und validieren können. Lesen Sie mehr über [Adobe Assurance](https://experienceleague.adobe.com/en/docs/experience-platform/assurance/home).


## Lernziele

Am Ende dieser Lektion können Sie:

* Starten einer Assurance-Sitzung
* Anzeigen von Anforderungen, die an und von Platform Edge Network gesendet werden

## Voraussetzungen

Sie sind mit Datenerfassungs-Tags und der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} vertraut und haben die vorherigen Lektionen im Tutorial abgeschlossen:

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)
* [Erstellen von Datenelementen](create-data-elements.md)
* [Erstellen von Identitäten](create-identities.md)
* [Tag-Regel erstellen](create-tag-rule.md)
* [Validieren mit Debugger](validate-with-debugger.md)


## Starten und Anzeigen einer Assurance-Sitzung

Es gibt mehrere Möglichkeiten, eine Zuverlässigkeitssitzung zu starten.

### Starten einer Zuverlässigkeitssitzung im Debugger

Jedes Mal, wenn Sie Edge Trace in Adobe Experience Platform Debugger aktivieren, wird eine Zuverlässigkeitssitzung im Hintergrund gestartet.

Überprüfen Sie, wie wir dies in der Debugger-Lektion durchgeführt haben:

1. Wechseln Sie zur Demosite &quot;[Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html)&quot;und verwenden Sie den Debugger, um die Tag-Eigenschaft auf der Site in Ihre eigene Entwicklungseigenschaft zu ändern. ](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)[
1. Wählen Sie im linken Navigationsbereich von **[!UICONTROL Experience Platform Debugger]** **[!UICONTROL Protokolle]** aus.
1. Wählen Sie die Registerkarte **[!UICONTROL Edge]** und dann **[!UICONTROL Verbinden]** aus.

   ![Verbinden von Edge Trace](assets/analytics-debugger-edgeTrace.png)
1. Wenn Edge Trace aktiviert ist, sehen Sie oben ein Symbol für einen ausgehenden Link. Wählen Sie das Symbol aus, um &quot;Versicherung&quot;zu öffnen.

   ![Beginn der Zuverlässigkeitssitzung](assets/validate-debugger-start-assurnance.png)

1. Eine neue Browser-Registerkarte wird mit der Assurance-Benutzeroberfläche geöffnet.

### Starten einer Zuverlässigkeitssitzung über die Assurance-Oberfläche

1. Öffnen Sie die [Datenerfassungsschnittstelle](https://experience.adobe.com/#/data-collection/home){target="_blank"} .
1. Wählen Sie im linken Navigationsbereich die Option Versicherung .
1. Sitzung erstellen
   ![Erstellen einer Zuverlässigkeitssitzung](assets/assurance-create-session.png)
1. Starten
1. Geben Sie der Sitzung einen Namen, z. B. `Luma Web SDK validation`
1. Geben Sie als **[!UICONTROL Basis-URL]** `https://luma.enablementadobe.com/` ein.
   ![Benennen der Zuverlässigkeitssitzung](assets/assurance-name-session.png)
1. Wählen Sie im nächsten Bildschirm **[!UICONTROL Link kopieren]** aus.
1. Wählen Sie das Symbol aus, um den Link in die Zwischenablage zu kopieren
1. Fügen Sie die URL in Ihren Browser ein, wodurch die Luma-Website mit einem speziellen URL-Parameter `adb_validation_sessionid` geöffnet und die Sitzung gestartet wird.
1. In der Assurance-Oberfläche sollte eine Meldung angezeigt werden, die angibt, dass Sie eine erfolgreiche Verbindung mit der Sitzung hergestellt haben. Außerdem sollten Ereignisse angezeigt werden, die in der Assurance-Oberfläche erfasst wurden.
   ![Die Zuverlässigkeitssitzung ist verbunden](assets/assurance-success.png)

## Überprüfen des aktuellen Status Ihrer Web SDK-Implementierung

Zu diesem Zeitpunkt Ihrer Implementierung sind nur begrenzte Informationen verfügbar. Ein Wert, den wir sehen können, ist Ihre Experience Cloud ID (ECID), die auf Platform Edge Network generiert wird:

1. Wählen Sie die Zeile mit dem Ereignis `Alloy Response Handle` aus.
1. Rechts wird ein Menü angezeigt. Wählen Sie das `+`-Zeichen neben `[!UICONTROL ACPExtensionEventData]` aus.
1. Führen Sie einen Drilldown durch, indem Sie `[!UICONTROL payload > 0 > payload > 0 > namespace]` auswählen. Die unter dem letzten `0` angezeigte ID entspricht dem `ECID`. Sie wissen das an dem Wert, der unter `namespace` angezeigt wird, der `ECID` entspricht

   ![Assurance validate ECID](assets/validate-assurance-ecid.png)

   >[!CAUTION]
   >
   >Aufgrund der Breite Ihres Fensters wird möglicherweise ein abgeschnittener ECID-Wert angezeigt. Wählen Sie einfach die Griffleiste in der Benutzeroberfläche aus und ziehen Sie sie nach links, um die gesamte ECID anzuzeigen.

In zukünftigen Lektionen verwenden Sie Assurance, um vollständig verarbeitete Payloads zu validieren und eine Adobe-Anwendung zu erreichen, die in Ihrem Datastream aktiviert ist.

Da jetzt ein XDM-Objekt auf einer Seite ausgelöst wird und Sie wissen, wie Sie Ihre Datenerfassung überprüfen können, können Sie Experience Platform und die einzelnen Adobe-Anwendungen mithilfe des Platform Web SDK einrichten.

[Weiter: ](setup-experience-platform.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
