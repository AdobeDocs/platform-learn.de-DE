---
title: Einrichten von Audience Manager mit Platform Web SDK
description: Erfahren Sie, wie Sie Adobe Audience Manager mithilfe der Platform Web SDK einrichten und die Implementierung mithilfe eines Cookie-Ziels überprüfen. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
solution: Data Collection, Audience Manager
jira: KT-15409
exl-id: 45db48e9-73cf-4a9c-88f4-b5872a8224d3
source-git-commit: 8602110d2b2ddc561e45f201e3bcce5e6a6f8261
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 4%

---

# Einrichten von Audience Manager mit Platform Web SDK

Erfahren Sie, wie Sie Adobe Audience Manager mit Adobe Experience Platform Web SDK einrichten und die Implementierung mit einem Cookie-Ziel validieren.

[Adobe Audience Manager](https://experienceleague.adobe.com/en/docs/audience-manager) ist die Adobe Experience Cloud-Lösung, die alles bietet, was erforderlich ist, um geschäftlich relevante Informationen über Site-Besucher zu sammeln, marktfähige Segmente zu erstellen und zielgruppengerechte Werbung und Inhalte für die richtige Zielgruppe bereitzustellen.

![Web-SDK und Adobe Audience Manager-Diagramm](assets/dc-websdk-aam.png)

## Lernziele

Am Ende dieser Lektion können Sie:

* Konfigurieren eines Datenstroms zum Aktivieren von Audience Manager
* Aktivieren eines Cookie-Ziels in Audience Manager
* Validieren der Audience Manager-Implementierung durch Bestätigen der Zielgruppen-Qualifizierung mit dem Adobe Experience Platform Debugger

## Voraussetzungen

Um diese Lektion abzuschließen, müssen Sie zunächst:

* Die vorherigen Lektionen in den Abschnitten Erstkonfiguration und Tags-Konfiguration dieses Tutorials absolvieren.
* Zugriff auf Adobe Audience Manager und die entsprechenden Berechtigungen zum Erstellen, Lesen und Schreiben von Eigenschaften, Segmenten und Zielen. Weitere Informationen finden Sie unter Rollenbasierte Zugriffssteuerung für [Audience Manager ](https://experienceleague.adobe.com/en/docs/audience-manager-learn/tutorials/setup-and-admin/user-management/setting-permissions-with-role-based-access-control).

## Konfigurieren des Datenstroms

Die Audience Manager-Implementierung mit Platform Web SDK unterscheidet sich von der Implementierung mit [Server-seitiger Weiterleitung (SSF)](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/server-side-forwarding/ssf). Die Server-seitige Weiterleitung übergibt Adobe Analytics-Anfragedaten an den Audience Manager. Bei einer Implementierung von Platform Web SDK werden XDM-Daten, die an das Platform-Edge Network gesendet werden, an den Audience Manager weitergeleitet. Audience Manager ist im Datenstrom aktiviert:

1. Zur [Datenerfassung](https://experience.adobe.com/#/data-collection){target="blank"} wechseln
1. Wählen Sie in der linken Navigation **[!UICONTROL Datenströme]**
1. Wählen Sie den zuvor erstellten `Luma Web SDK: Development Environment` aus

   ![Wählen Sie den Luma Web SDK-Datenstrom aus](assets/datastream-luma-web-sdk-development.png)

1. Wählen Sie **[!UICONTROL Service hinzufügen]**
   ![Fügen Sie einen Service zum Datenstrom hinzu](assets/aam-datastream-addService.png)
1. Wählen Sie **[!UICONTROL Adobe Audience Manager]** als **[!UICONTROL Service]**
1. Bestätigen Sie, dass **[!UICONTROL Cookie-Ziele aktiviert]** und **[!UICONTROL URL-Ziele]** sind
1. Wählen Sie **[!UICONTROL Speichern]**
   ![Bestätigen Sie die Einstellungen für den Audience Manager-Datenstrom und speichern Sie](assets/aam-datastream-save.png)

## Erstellen einer Datenquelle

Erstellen Sie anschließend ein [Daten-Source](https://experienceleague.adobe.com/en/docs/audience-manager/user-guide/features/data-sources/datasources-list-and-settings), ein grundlegendes Tool zum Organisieren von Daten in Audience Manager:

1. Zur [Audience Manager ](https://experience.adobe.com/#/audience-manager/)-Benutzeroberfläche
1. Wählen **[!UICONTROL Zielgruppendaten]** in der oberen Navigationsleiste aus.
1. Wählen Sie **[!UICONTROL Dropdown]** Menü „Datenquellen“ aus
1. Wählen Sie **[!UICONTROL Schaltfläche]** hinzufügen oben auf der Seite „Datenquellen“ aus

   ![Adobe Experience Platform Audience Manager-Datenquellen](assets/data-sources-list.jpg)

1. Geben Sie dem Data Source einen Anzeigenamen und eine Beschreibung. Bei der Ersteinrichtung können Sie diese `Platform Web SDK tutorial` benennen.
1. Legen Sie **[!UICONTROL ID-Typ]** auf **[!UICONTROL Cookie]** fest
1. Wählen **[!UICONTROL Abschnitt „Datenexportsteuerelemente]** die Option &quot;**[!UICONTROL Einschränkung]**

   ![Einrichten von Adobe Experience Platform Audience Manager Data Source](assets/data-source-details.png)

1. **[!UICONTROL Speichern]** der Daten-Source


## Erstellen einer Eigenschaft

Richten Sie nach dem Speichern der Daten-Source eine [Eigenschaft](https://experienceleague.adobe.com/en/docs/audience-manager/user-guide/features/traits/traits-overview) ein. Eigenschaften sind eine Kombination aus einem oder mehreren Signalen im Audience Manager. Erstellen Sie eine Eigenschaft für Homepage-Besucher.

>[!NOTE]
>
>Alle XDM-Daten werden an den -Audience Manager gesendet, wenn sie im Datenstrom aktiviert sind. Es kann jedoch 24 Stunden dauern, bis die Daten im Bericht „Nicht verwendete Signale“ verfügbar sind. Erstellen Sie explizite Eigenschaften für die XDM-Daten, die Sie sofort im Audience Manager verwenden möchten, wie in dieser Übung beschrieben.

1. Wählen Sie **[!UICONTROL Zielgruppendaten]** > **[!UICONTROL Eigenschaften]**
1. Wählen Sie **[!UICONTROL Neu hinzufügen]** > **[!UICONTROL Regelbasiert]** Eigenschaft aus

   ![Regelbasierte Eigenschaft des Adobe Experience Platform-Audience Managers ](assets/rule-based-trait.jpg)

1. Geben Sie Ihrem Merkmal einen Anzeigenamen und eine Beschreibung, `Luma homepage view`
1. Wählen Sie **[!UICONTROL Daten-Source]** aus, die Sie im vorherigen Abschnitt erstellt haben.
1. **[!UICONTROL Ordner auswählen]** in dem die Eigenschaft gespeichert werden soll, wird im Bereich rechts angezeigt. Sie können einen Ordner erstellen, indem Sie **das Symbol &quot;+&quot;** einem vorhandenen übergeordneten Ordner auswählen. Sie können diesen neuen Ordner `Platform Web SDK tutorial` benennen.
1. Erweitern Sie das **[!UICONTROL Eigenschaftsausdruck]**-Caret und wählen Sie **[!UICONTROL Ausdrucksgenerator]**. Sie müssen ein Schlüsselwertpaar angeben, das einen Homepage-Besuch bedeutet.
1. Öffnen Sie die [Luma-Homepage](https://luma.enablementadobe.com/content/luma/us/en.html) (der Ihrer Tag-Eigenschaft zugeordnet) und den **Adobe Experience Platform Debugger** und aktualisieren Sie die Seite.
1. Sehen Sie sich die Netzwerkanfragen und Ereignisdetails für Platform Web SDK an, um den Schlüssel und den Namenswert für die Homepage zu finden.
   ![XDM-Daten des Adobe Experience Platform-Audience Managers ](assets/xdm-keyvalue.jpg)
1. Kehren Sie zum Expression Builder in der Audience Manager-Benutzeroberfläche zurück und geben Sie den Schlüssel als **`web.webPageDetails.name`** und den Wert von **`content:luma:us:en`** ein. Dieser Schritt stellt sicher, dass Sie beim Laden der Homepage eine Eigenschaft auslösen.
1. **[!UICONTROL Speichern]** die Eigenschaft.


## Erstellen eines Segments

Die nächsten Schritte bestehen darin, ein **Segment** zu erstellen und diesem Segment Ihre neu definierte Eigenschaft zuzuweisen.

1. Wählen Sie **[!UICONTROL Zielgruppendaten]** in der oberen Navigationsleiste aus und klicken Sie auf **[!UICONTROL Segmente]**
1. Wählen **[!UICONTROL oben links auf]** Seite „Neu hinzufügen“ aus, um Segment Builder zu öffnen
1. Geben Sie Ihrem Segment einen Anzeigenamen und eine Beschreibung, z. B. `Platform Web SDK - Homepage visitors`
1. **[!UICONTROL Ordner auswählen]** in dem Ihr Segment im Bereich auf der rechten Seite gespeichert wird. Sie können einen Ordner erstellen, indem Sie **das Symbol &quot;+&quot;** einem vorhandenen übergeordneten Ordner auswählen. Sie können diesen neuen Ordner `Platform Web SDK tutorial` benennen.
1. Fügen Sie einen Integrations-Code hinzu, in diesem Fall eine zufällige Reihe von Zahlen.
1. Wählen Sie **[!UICONTROL Abschnitt Daten-Source]** die Option **[!UICONTROL Audience Manager]** und die zuvor erstellte Datenquelle aus
1. Erweitern Sie den Abschnitt **[!UICONTROL Eigenschaften]** und suchen Sie nach der von Ihnen erstellten Eigenschaft
1. Wählen Sie **[!UICONTROL Eigenschaft hinzufügen]** aus.
1. Klicken **[!UICONTROL unten]** der Seite auf „Speichern“

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/add-trait-segment.jpg)

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/saved-segment.jpg)

## Erstellen eines Ziels

Erstellen Sie anschließend ein **Cookie-basiertes Ziel** mithilfe des **Destination Builder**. Mit Destination Builder können Sie Cookies, URLs und Server-zu-Server-Ziele erstellen und verwalten.

1. Öffnen Sie den Destination Builder, indem Sie **[!UICONTROL Ziele]** im Menü **Zielgruppendaten** in der oberen Navigationsleiste auswählen
1. Wählen Sie **[!UICONTROL Ziel erstellen]**
1. Geben Sie einen Namen und eine Beschreibung ein `Platform Web SDK tutorial`
1. Wählen Sie als **[!UICONTROL Kategorie]** die Option **[!UICONTROL Benutzerdefiniert]**
1. Wählen Sie als **[!UICONTROL Typ]** &quot;**[!UICONTROL &quot;]**

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/destination-settings.jpg)

1. Öffnen Sie den **[!UICONTROL Konfiguration]**, um die Details zu Ihrem Cookie-Ziel einzugeben
1. Geben Sie Ihrem Cookie einen Anzeigenamen, `platform_web_sdk_tutorial`
1. Fügen Sie als **[!UICONTROL Cookie-Domain]** die Domain der Site hinzu, auf der Sie die Integration planen, für das Tutorial zur Eingabe der Luma-Domain `luma.enablementadobe.com`
1. Wählen Sie als Option **[!UICONTROL Publish-Daten an]** die Option **[!UICONTROL Nur ausgewählte Domains]**
1. Domain auswählen, falls noch nicht hinzugefügt
1. Wählen Sie als **[!UICONTROL Datenformat]** die Option **[!UICONTROL Einzelschlüssel]** und geben Sie Ihrem Cookie einen Schlüssel. Verwenden Sie für dieses Tutorial `segment` als Schlüsselwert.
1. Wählen Sie abschließend **[!UICONTROL Speichern]**, um die Details der Zielkonfiguration zu speichern.

   Abschnitt zur Konfiguration des ![Audience Manager-Ziels](assets/aam-destination-config-dw.png)

<!--
   ![Adobe Experience Platform Audience Manager Add Trait](assets/aam-destination-config.jpg)


   ![Adobe Experience Platform Audience Manager Add Trait](assets/cookie-destination-config.jpg)
-->

1. Verwenden Sie im Abschnitt **[!UICONTROL Segmentzuordnungen]** die Funktion **[!UICONTROL Suchen und Segmente hinzufügen]**, um nach Ihrer zuvor erstellten `Platform Web SDK - Homepage visitors` zu suchen, und wählen Sie **[!UICONTROL Hinzufügen]**.


1. Nachdem Sie Ihr Segment hinzugefügt haben, wird ein Popup geöffnet, in dem Sie einen erwarteten Wert für Ihr Cookie angeben müssen. Geben Sie für diese Übung den Wert „hpvisitor“ ein.

1. Wählen Sie **[!UICONTROL Speichern]**

1. Wählen Sie **[!UICONTROL Fertig]**
   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/luma-cookie-segment-dw.png)

Der Zeitraum für die Segmentzuordnung dauert einige Stunden, bis er aktiviert ist. Nach Abschluss des Vorgangs können Sie die Benutzeroberfläche des Audience Managers aktualisieren und sehen, dass die Liste **Zugeordnete Segmente** aktualisiert wurde.

## Segment validieren

Einige Stunden nach der ersten Erstellung des Segments können Sie überprüfen, ob es ordnungsgemäß funktioniert.

Bestätigen Sie zunächst, dass Sie sich für das Segment qualifizieren können

1. Öffnen Sie die [Startseite der Demo-Site von Luma](https://luma.enablementadobe.com/content/luma/us/en.html) mit der sie Ihrer Tag-Eigenschaft zugeordnet ist, um sich für Ihr neu erstelltes Segment zu qualifizieren.
1. Öffnen Sie die Registerkarte **Entwickler-Tools** > **Netzwerk** Ihres Browsers
1. Filtern Sie nach der Platform Web SDK-Anforderung, indem Sie `interact` als Textfilter verwenden
1. Wählen Sie einen Aufruf aus und öffnen Sie die **Vorschau**, um die Antwortdetails anzuzeigen
1. Erweitern Sie die **Payload**, um die erwarteten Cookie-Details anzuzeigen, wie zuvor in Audience Manager konfiguriert. In diesem Beispiel wird der erwartete Cookie-Name `platform_web_sdk_tutorial` angezeigt.

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/segment-validate-response.jpg)

1. Öffnen Sie die **Anwendung** und öffnen Sie **Cookies** über das Menü **Speicherung**.
1. Wählen Sie die **`https://luma.enablementadobe.com`** Domain aus und bestätigen Sie, dass Ihr Cookie ordnungsgemäß in der Liste geschrieben wurde

   ![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/validate-cookie.jpg)


Audience Manager Schließlich sollten Sie das Segment in der Segmentoberfläche öffnen und sicherstellen, dass **Segmentpopulationen** erhöht wurde:

![Adobe Experience Platform-Audience Manager - Eigenschaft hinzufügen](assets/segment-population.jpg)


Nachdem Sie nun diese Lektion abgeschlossen haben, sollten Sie sehen können, wie Platform Web SDK Daten an Audience Manager übergibt, und ein segmentspezifisches Erstanbieter-Cookie mit einem Cookie-Ziel setzen können.

[Weiter: ](setup-target.md)

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League-Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
