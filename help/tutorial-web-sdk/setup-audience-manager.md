---
title: Einrichten von Audience Manager mit dem Platform Web SDK
description: Erfahren Sie, wie Sie Adobe Audience Manager mit dem Platform Web SDK einrichten und die Implementierung mit einem Cookie-Ziel validieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
solution: Data Collection, Audience Manager
jira: KT-15409
exl-id: 45db48e9-73cf-4a9c-88f4-b5872a8224d3
source-git-commit: 8602110d2b2ddc561e45f201e3bcce5e6a6f8261
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 4%

---

# Einrichten von Audience Manager mit dem Platform Web SDK

Erfahren Sie, wie Sie Adobe Audience Manager mit Adobe Experience Platform Web SDK einrichten und die Implementierung mit einem Cookie-Ziel validieren.

[Adobe Audience Manager](https://experienceleague.adobe.com/en/docs/audience-manager) ist die Adobe Experience Cloud-Lösung, die alles bietet, was erforderlich ist, um geschäftlich relevante Informationen über Site-Besucher zu sammeln, vermarktbare Segmente zu erstellen und zielgruppengerechte Werbung und Inhalte für die richtige Zielgruppe bereitzustellen.

![Web SDK- und Adobe Audience Manager-Diagramm](assets/dc-websdk-aam.png)

## Lernziele

Am Ende dieser Lektion können Sie:

* Konfigurieren eines Datenspeichers zum Aktivieren von Audience Manager
* Aktivieren eines Cookie-Ziels in Audience Manager
* Validieren der Audience Manager-Implementierung durch Bestätigung der Zielgruppenqualifizierung mit Adobe Experience Platform Debugger

## Voraussetzungen

Um diese Lektion abzuschließen, müssen Sie zunächst:

* Schließen Sie die früheren Lektionen in den Abschnitten Erstkonfiguration und Tags-Konfiguration dieses Tutorials ab.
* Sie haben Zugriff auf Adobe Audience Manager und die entsprechenden Berechtigungen zum Erstellen, Lesen und Schreiben von Eigenschaften, Segmenten und Zielen. Weitere Informationen finden Sie unter [rollenbasierte Zugriffskontrolle des Audience Managers](https://experienceleague.adobe.com/en/docs/audience-manager-learn/tutorials/setup-and-admin/user-management/setting-permissions-with-role-based-access-control).

## Konfigurieren des Datenspeichers

Die Implementierung des Audience Managers mit dem Platform Web SDK unterscheidet sich von der Implementierung mit [serverseitiger Weiterleitung (SSF)](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/server-side-forwarding/ssf). Die serverseitige Weiterleitung übergibt Adobe Analytics-Anfragedaten an Audience Manager. Eine Platform Web SDK-Implementierung übergibt XDM-Daten, die an Platform Edge Network gesendet werden, an Audience Manager. Audience Manager ist im Datastream aktiviert:

1. Wechseln Sie zur Oberfläche [Datenerfassung](https://experience.adobe.com/#/data-collection){target="blank"} .
1. Wählen Sie im linken Navigationsbereich **[!UICONTROL Datastreams]** aus.
1. Wählen Sie den zuvor erstellten `Luma Web SDK: Development Environment`-Datastream aus.

   ![Wählen Sie den Luma Web SDK-Datenspeicher aus](assets/datastream-luma-web-sdk-development.png)

1. Wählen Sie **[!UICONTROL Dienst hinzufügen]** aus
   ![Hinzufügen eines Dienstes zum Datastream](assets/aam-datastream-addService.png)
1. Wählen Sie **[!UICONTROL Adobe Audience Manager]** als **[!UICONTROL Dienst]** aus.
1. Bestätigen Sie, dass **[!UICONTROL Cookie-Ziele aktiviert]** und **[!UICONTROL URL-Ziele aktiviert]** ausgewählt sind.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
   ![Bestätigen Sie die Audience Manager-Datastream-Einstellungen und speichern Sie](assets/aam-datastream-save.png)

## Erstellen einer Datenquelle

Erstellen Sie anschließend eine [Daten-Source](https://experienceleague.adobe.com/en/docs/audience-manager/user-guide/features/data-sources/datasources-list-and-settings), ein grundlegendes Tool für die Organisation von Daten in Audience Manager:

1. Navigieren Sie zur Benutzeroberfläche [Audience Manager](https://experience.adobe.com/#/audience-manager/) .
1. Wählen Sie **[!UICONTROL Zielgruppendaten]** aus der oberen Navigation aus.
1. Wählen Sie **[!UICONTROL Data Sources]** aus dem Dropdown-Menü aus
1. Wählen Sie oben auf der Seite &quot;Data Sources&quot;die Schaltfläche **[!UICONTROL Neu hinzufügen]** aus.

   ![Adobe Experience Platform Audience Manager Data Sources](assets/data-sources-list.jpg)

1. Benennen und beschreiben Sie die Data Source. Bei der Ersteinrichtung können Sie diesen `Platform Web SDK tutorial` nennen.
1. Setzen Sie **[!UICONTROL ID-Typ]** auf **[!UICONTROL Cookie]**
1. Wählen Sie im Abschnitt **[!UICONTROL Datenexportkontrollen]** die Option **[!UICONTROL Keine Einschränkung]** aus.

   ![Einrichten von Adobe Experience Platform Audience Manager Data Source](assets/data-source-details.png)

1. **[!UICONTROL Speichern]** der Daten-Source


## Erstellen einer Eigenschaft

Nachdem die Data Source gespeichert wurde, richten Sie eine [Eigenschaft](https://experienceleague.adobe.com/en/docs/audience-manager/user-guide/features/traits/traits-overview) ein. Eigenschaften sind eine Kombination aus einem oder mehreren Signalen in Audience Manager. Erstellen Sie eine Eigenschaft für Besucher der Homepage.

>[!NOTE]
>
>Alle XDM-Daten werden an Audience Manager gesendet, wenn sie im Datastream aktiviert sind. Die Daten können jedoch 24 Stunden dauern, bis sie im Bericht Nicht verwendete Signale verfügbar sind. Erstellen Sie explizite Eigenschaften für die XDM-Daten, die Sie sofort in Audience Manager verwenden möchten, wie in dieser Übung beschrieben.

1. Wählen Sie **[!UICONTROL Zielgruppendaten]** > **[!UICONTROL Eigenschaften]** aus.
1. Wählen Sie **[!UICONTROL Neue Eigenschaft hinzufügen]** > **[!UICONTROL regelbasierte Eigenschaft]** aus.

   ![Regelbasierte Eigenschaft des Adobe Experience Platform-Audience Managers](assets/rule-based-trait.jpg)

1. Geben Sie Ihrer Eigenschaft einen Anzeigenamen und eine Beschreibung, `Luma homepage view`
1. Wählen Sie die **[!UICONTROL Daten-Source]** aus, die Sie im vorherigen Abschnitt erstellt haben.
1. **[!UICONTROL Wählen Sie einen Ordner]** aus, in dem Ihre Eigenschaft im Bereich rechts gespeichert werden soll. Sie können einen Ordner erstellen, indem Sie **auf das Plussymbol** neben einem vorhandenen übergeordneten Ordner klicken. Sie können diesen neuen Ordner &quot;`Platform Web SDK tutorial`&quot; nennen.
1. Erweitern Sie das Caret **[!UICONTROL Eigenschaftsausdruck]** und wählen Sie **[!UICONTROL Ausdrucksgenerator]**. Sie müssen ein Schlüsselwertpaar bereitstellen, das einen Homepage-Besuch angibt.
1. Öffnen Sie die Homepage [Luma](https://luma.enablementadobe.com/content/luma/us/en.html) (die Ihrer Tag-Eigenschaft zugeordnet ist) und den Adobe Experience Platform Debugger **3} und aktualisieren Sie die Seite.**
1. Sehen Sie sich die Netzwerkanforderungen und Ereignisdetails für das Platform Web SDK an, um den Schlüssel- und Namenswert für die Homepage zu finden.
   ![Adobe Experience Platform Audience Manager XDM Data](assets/xdm-keyvalue.jpg)
1. Kehren Sie in der Audience Manager-Benutzeroberfläche zum Ausdrucksgenerator zurück und geben Sie den Schlüssel als **`web.webPageDetails.name`** und den Wert **`content:luma:us:en`** ein. Dieser Schritt stellt sicher, dass Sie beim Laden der Startseite eine Eigenschaft auslösen.
1. **[!UICONTROL Speichern]** Sie die Eigenschaft.


## Erstellen eines Segments

Die nächsten Schritte sind das Erstellen eines **Segments** und das Zuweisen Ihrer neu definierten Eigenschaft zu diesem Segment.

1. Wählen Sie **[!UICONTROL Zielgruppendaten]** in der oberen Navigation und dann **[!UICONTROL Segmente]** aus.
1. Wählen Sie oben links auf der Seite **[!UICONTROL Neu hinzufügen]** aus, um den Segment Builder zu öffnen.
1. Geben Sie Ihrem Segment einen Anzeigenamen und eine Beschreibung, z. B. `Platform Web SDK - Homepage visitors`
1. **[!UICONTROL Wählen Sie einen Ordner]** aus, in dem Ihr Segment im rechten Bereich gespeichert ist. Sie können einen Ordner erstellen, indem Sie **auf das Plussymbol** neben einem vorhandenen übergeordneten Ordner klicken. Sie können diesen neuen Ordner &quot;`Platform Web SDK tutorial`&quot; nennen.
1. Fügen Sie einen Integrationscode hinzu, bei dem es sich in diesem Fall um einen zufälligen Satz von Zahlen handelt.
1. Wählen Sie im Bereich **[!UICONTROL Data Source]** die Option **[!UICONTROL Audience Manager]** und die zuvor erstellte Datenquelle
1. Erweitern Sie den Abschnitt **[!UICONTROL Eigenschaften]** und suchen Sie nach der von Ihnen erstellten Eigenschaft.
1. Wählen Sie **[!UICONTROL Eigenschaft hinzufügen]** aus.
1. Wählen Sie **[!UICONTROL Speichern]** unten auf der Seite aus.

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/add-trait-segment.jpg)

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/saved-segment.jpg)

## Erstellen eines Ziels

Als Nächstes erstellen Sie ein **Cookie-basiertes Ziel** mit dem **Ziel-Builder**. Mit dem Destination Builder können Sie Cookie-, URL- und Server-zu-Server-Ziele erstellen und verwalten.

1. Öffnen Sie den Destination Builder, indem Sie im Menü **Zielgruppendaten** in der oberen Navigation die Option **[!UICONTROL Ziele]** auswählen
1. Wählen Sie **[!UICONTROL Ziel erstellen]** aus
1. Geben Sie einen Namen und eine Beschreibung ein, `Platform Web SDK tutorial`
1. Wählen Sie als **[!UICONTROL Kategorie]** **[!UICONTROL Benutzerdefiniert]** aus.
1. Wählen Sie als **[!UICONTROL Typ]** **[!UICONTROL Cookie]** aus.

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/destination-settings.jpg)

1. Öffnen Sie den Abschnitt **[!UICONTROL Konfiguration]** , um Details zu Ihrem Cookie-Ziel einzugeben.
1. Geben Sie Ihrem Cookie einen Anzeigenamen, `platform_web_sdk_tutorial`
1. Fügen Sie als **[!UICONTROL Cookie-Domäne]** die Domäne der Site hinzu, für die Sie die Integration planen. Geben Sie für die Tutorial-Eingabe die Domäne &quot;Luma&quot;ein, `luma.enablementadobe.com`
1. Wählen Sie als Option **[!UICONTROL Publish data to]** die Option **[!UICONTROL Nur die ausgewählten Domänen]** aus.
1. Domain auswählen, falls noch nicht hinzugefügt
1. Wählen Sie als **[!UICONTROL Datenformat]** **[!UICONTROL Einzelschlüssel]** aus und geben Sie Ihrem Cookie einen Schlüssel. Verwenden Sie für dieses Tutorial `segment` als Schlüsselwert.
1. Wählen Sie abschließend **[!UICONTROL Speichern]** aus, um die Details der Zielkonfiguration zu speichern.

   ![Audience Manager-Zielkonfiguration, Abschnitt](assets/aam-destination-config-dw.png)

<!--
   ![Adobe Experience Platform Audience Manager Add Trait](assets/aam-destination-config.jpg)


   ![Adobe Experience Platform Audience Manager Add Trait](assets/cookie-destination-config.jpg)
-->

1. Verwenden Sie im Abschnitt **[!UICONTROL Segmentzuordnungen]** die Funktion **[!UICONTROL Suchen und Segmente hinzufügen]** , um nach Ihrem zuvor erstellten `Platform Web SDK - Homepage visitors` zu suchen, und wählen Sie **[!UICONTROL Hinzufügen]** aus.


1. Nachdem Sie Ihr Segment hinzugefügt haben, wird ein Popup geöffnet, in dem Sie einen erwarteten Wert für Ihr Cookie angeben müssen. Geben Sie für diese Übung den Wert &quot;hpvisitor&quot;ein.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

1. Wählen Sie **[!UICONTROL Fertig]** aus
   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/luma-cookie-segment-dw.png)

Für den Zeitraum der Segmentzuordnung müssen einige Stunden aktiviert werden. Nach Abschluss können Sie die Audience Manager-Oberfläche aktualisieren und sehen, dass die Liste **Zugeordnete** aktualisiert wurde.

## Validieren des Segments

Einige Stunden nach der ersten Erstellung des Segments können Sie überprüfen, ob es ordnungsgemäß funktioniert.

Bestätigen Sie zunächst, dass Sie sich für das Segment qualifizieren können.

1. Öffnen Sie die Demosite &quot;[Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html)&quot;, wobei sie Ihrer Tag-Eigenschaft zugeordnet ist, um sich für Ihr neu erstelltes Segment zu qualifizieren.
1. Öffnen Sie die Registerkarte **Entwicklertools** > **Netzwerk** Ihres Browsers.
1. Filtern nach der Platform Web SDK-Anforderung mit `interact` als Textfilter
1. Wählen Sie einen Aufruf aus und öffnen Sie die Registerkarte **Vorschau** , um die Antwortdetails anzuzeigen
1. Erweitern Sie die **Payload** , um die erwarteten Cookie-Details anzuzeigen, wie zuvor in Audience Manager konfiguriert. In diesem Beispiel wird der erwartete Cookie-Name `platform_web_sdk_tutorial` angezeigt.

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/segment-validate-response.jpg)

1. Öffnen Sie die Registerkarte **Anwendung** und öffnen Sie **Cookies** im Menü **Speicherung** .
1. Wählen Sie die Domäne **`https://luma.enablementadobe.com`** aus und vergewissern Sie sich, dass Ihr Cookie in der Liste richtig geschrieben ist.

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/validate-cookie.jpg)


Schließlich sollten Sie das Segment in der Audience Manager-Oberfläche öffnen und sicherstellen, dass die **Segmentpopulationen** inkrementiert wurde:

![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/segment-population.jpg)


Nachdem Sie diese Lektion abgeschlossen haben, sollten Sie sehen können, wie das Platform Web SDK Daten an Audience Manager übergibt, und ein segmentspezifisches Erstanbieter-Cookie mit einem Cookie-Ziel setzen können.

[Weiter: ](setup-target.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
