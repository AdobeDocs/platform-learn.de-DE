---
title: WebSDK-Implementierungen mit Experience Platform Assurance validieren
description: Erfahren Sie, wie Sie Ihre Platform Web SDK-Implementierung mit Adobe Experience Platform Assurance überprüfen. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Web SDK,Tags,Assurance
jira: KT-15406
exl-id: 31e381ea-fbaf-495f-a6e9-2ff6c0d36939
source-git-commit: 8602110d2b2ddc561e45f201e3bcce5e6a6f8261
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 3%

---

# WebSDK-Implementierungen mit Experience Platform Assurance validieren

Adobe Experience Platform Assurance ist eine Funktion, mit der Sie die Datenerfassung und Bereitstellung von Erlebnissen überprüfen, testen, simulieren und validieren können. Mehr dazu [Adobe Assurance](https://experienceleague.adobe.com/en/docs/experience-platform/assurance/home).


## Lernziele

Am Ende dieser Lektion können Sie:

* Starten einer Assurance-Sitzung
* Anzeigen von Anforderungen, die an und von Platform Edge Network gesendet werden

## Voraussetzungen

Sie kennen Datenerfassungs-Tags und die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} und die vorherigen Lektionen im Tutorial abgeschlossen haben:

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

1. Navigieren Sie zu [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) und verwenden Sie den Debugger zum [Ändern Sie die Tag-Eigenschaft auf der Site in Ihre eigene Entwicklungseigenschaft.](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)
1. In der linken Navigation von **[!UICONTROL Experience Platform Debugger]** select **[!UICONTROL Protokolle]**
1. Wählen Sie die **[!UICONTROL Edge]** und wählen Sie **[!UICONTROL Verbinden]**

   ![Edge Trace verbinden](assets/analytics-debugger-edgeTrace.png)
1. Wenn Edge Trace aktiviert ist, sehen Sie oben ein Symbol für einen ausgehenden Link. Wählen Sie das Symbol aus, um &quot;Versicherung&quot;zu öffnen.

   ![Starten einer Assurance-Sitzung](assets/validate-debugger-start-assurnance.png)

1. Eine neue Browser-Registerkarte wird mit der Assurance-Benutzeroberfläche geöffnet.

### Starten einer Zuverlässigkeitssitzung über die Assurance-Oberfläche

1. Öffnen Sie die [Datenerfassungsoberfläche](https://experience.adobe.com/#/data-collection/home){target="_blank"}
1. Wählen Sie im linken Navigationsbereich die Option Versicherung .
1. Sitzung erstellen
   ![Erstellen einer Zuverlässigkeitssitzung](assets/assurance-create-session.png)
1. Starten
1. Benennen Sie die Sitzung beispielsweise. `Luma Web SDK validation`
1. Als **[!UICONTROL Basis-URL]** enter `https://luma.enablementadobe.com/`
   ![Benennen der Assurance-Sitzung](assets/assurance-name-session.png)
1. Wählen Sie im nächsten Bildschirm **[!UICONTROL Link kopieren]**
1. Wählen Sie das Symbol aus, um den Link in die Zwischenablage zu kopieren
1. Fügen Sie die URL in Ihren Browser ein, wodurch die Luma-Website mit einem speziellen URL-Parameter geöffnet wird. `adb_validation_sessionid` und starten Sie die Sitzung
1. In der Assurance-Oberfläche sollte eine Meldung angezeigt werden, die angibt, dass Sie eine erfolgreiche Verbindung mit der Sitzung hergestellt haben. Außerdem sollten Ereignisse angezeigt werden, die in der Assurance-Oberfläche erfasst wurden.
   ![Die Bestätigungssitzung ist verbunden](assets/assurance-success.png)

## Überprüfen des aktuellen Status Ihrer Web SDK-Implementierung

Zu diesem Zeitpunkt Ihrer Implementierung sind nur begrenzte Informationen verfügbar. Ein Wert, den wir sehen können, ist Ihre Experience Cloud ID (ECID), die auf Platform Edge Network generiert wird:

1. Wählen Sie die Zeile mit dem Ereignis Adobe Response Handle aus.
1. Rechts wird ein Menü angezeigt. Wählen Sie die `+` neben `[!UICONTROL ACPExtensionEvent]`
1. Drilldown durch Auswahl von `[!UICONTROL payload > 0 > payload > 0 > namespace]`. Die unter der letzten `0` entspricht `ECID`. Sie wissen dies anhand des Wertes, der unter `namespace` Abgleich `ECID`

   ![Zuverlässigkeitsprüfung ECID](assets/validate-assurance-ecid.png)

   >[!CAUTION]
   >
   >Aufgrund der Breite Ihres Fensters wird möglicherweise ein abgeschnittener ECID-Wert angezeigt. Wählen Sie einfach die Griffleiste in der Benutzeroberfläche aus und ziehen Sie sie nach links, um die gesamte ECID anzuzeigen.

In zukünftigen Lektionen verwenden Sie Assurance, um vollständig verarbeitete Payloads zu validieren und eine Adobe-Anwendung zu erreichen, die in Ihrem Datastream aktiviert ist.

Da jetzt ein XDM-Objekt auf einer Seite ausgelöst wird und Sie wissen, wie Sie Ihre Datenerfassung überprüfen können, können Sie Experience Platform und die einzelnen Adobe-Anwendungen mithilfe des Platform Web SDK einrichten.

[Weiter: ](setup-experience-platform.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
