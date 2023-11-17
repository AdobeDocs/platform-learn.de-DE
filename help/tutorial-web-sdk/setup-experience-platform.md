---
title: Streamen von Daten an Adobe Experience Platform mit dem Web SDK
description: Erfahren Sie, wie Sie Webdaten mit dem Web SDK an Adobe Experience Platform streamen. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
exl-id: 4d749ffa-e1c0-4498-9b12-12949807b369
source-git-commit: 4a12f8261cf1fb071bc70b6a04c34f6c16bcce64
workflow-type: tm+mt
source-wordcount: '1605'
ht-degree: 11%

---

# Streamen von Daten an Experience Platform mit dem Web SDK

Erfahren Sie, wie Sie Webdaten mit dem Platform Web SDK an Adobe Experience Platform streamen.

Experience Platform ist das Rückgrat aller neuen Experience Cloud-Applikationen wie Adobe Real-time Customer Data Platform, Adobe Customer Journey Analytics und Adobe Journey Optimizer. Diese Anwendungen sind so konzipiert, dass sie das Platform Web SDK als optimale Methode zur Webdatenerfassung verwenden.

Experience Platform verwendet dasselbe XDM-Schema, das Sie zuvor erstellt haben, um Ereignisdaten von der Luma-Website zu erfassen. Wenn diese Daten an Platform Edge Network gesendet werden, kann die Datastream-Konfiguration sie an Experience Platform weiterleiten.

## Lernziele

Am Ende dieser Lektion können Sie:

* Datensatz in Adobe Experience Platform erstellen
* Konfigurieren des Datenspeichers zum Senden von Web SDK-Daten an Adobe Experience Platform
* Streaming-Webdaten für Echtzeit-Kundenprofil aktivieren
* Überprüfen, ob die Daten sowohl im Platform-Datensatz als auch im Echtzeit-Kundenprofil gelandet sind

## Voraussetzungen

Sie sollten die folgenden Lektionen bereits abgeschlossen haben:

* Die **Erstkonfiguration** Lektionen:
   * [Konfigurieren von Berechtigungen](configure-permissions.md)
   * [Konfigurieren eines XDM-Schemas](configure-schemas.md)
   * [Konfigurieren eines Datenstroms](configure-datastream.md)
   * [Identitäts-Namespace konfigurieren](configure-identities.md)

* Die **Tag-Konfiguration** Lektionen:
   * [Installieren der Web SDK-Erweiterung](install-web-sdk.md)
   * [Erstellen von Datenelementen](create-data-elements.md)
   * [Erstellen von Tag-Regeln](create-tag-rule.md)


## Erstellen eines Datensatzes

Alle Daten, die erfolgreich in Adobe Experience Platform aufgenommen wurden, werden im Data Lake als Datensätze persistiert. A [Datensatz](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=en) ist ein Speicher- und Verwaltungskonstrukt für eine Sammlung von Daten, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

In dieser Übung erstellen Sie einen Datensatz, um Inhalte und E-Commerce-Details für die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html).

>[!WARNING]
>
>Sie müssen die `Luma Web Event Data` Schema, wie in der vorherigen Lektion beschrieben, [Konfigurieren eines XDM-Schemas](configure-schemas.md).


1. Navigieren Sie zu [Experience Platform-Oberfläche](https://experience.adobe.com/platform/)
1. Bestätigen, dass Sie sich in der Entwicklungs-Sandbox befinden, die Sie für dieses Tutorial verwenden
1. Öffnen **[!UICONTROL Datensätze]** über die linke Navigation
1. Wählen Sie **[!UICONTROL Erstellen eines Datensatzes]** aus

   ![Erstellen eines Schemas](assets/experience-platform-create-dataset.png)

1. Wählen Sie die **[!UICONTROL Datensatz aus Schema erstellen]** option

   ![Datensatz aus Schema erstellen](assets/experience-platform-create-dataset-schema.png)

1. Wählen Sie die `Luma Web Event Data` Schema, das im [frühere Lektion](configure-schemas.md) und wählen Sie **[!UICONTROL Nächste]**

   ![Datensatz, Schema auswählen](assets/experience-platform-create-dataset-schema-selection.png)

1. Stellen Sie eine **[!UICONTROL Name]** und optional **[!UICONTROL Beschreibung]** für den Datensatz. Verwenden Sie für diese Übung `Luma Web Event Data`, wählen Sie **[!UICONTROL Beenden]**

   ![Datensatzname ](assets/experience-platform-create-dataset-schema-name.png)

Ein Datensatz ist jetzt so konfiguriert, dass Daten aus Ihrer Platform Web SDK-Implementierung erfasst werden.

## Konfigurieren des Datenspeichers

Jetzt können Sie Ihre [!UICONTROL datastream] zum Senden von Daten an [!UICONTROL Adobe Experience Platform]. Der Datastream ist die Verknüpfung zwischen Ihrer Tag-Eigenschaft, dem Platform Edge Network und dem Experience Platform-Datensatz.

1. Öffnen Sie die [Datenerfassung](https://experience.adobe.com/#/data-collection){target="blank"} Benutzeroberfläche
1. Auswählen **[!UICONTROL Datenspeicher]** über die linke Navigation
1. Öffnen Sie den von Ihnen im Abschnitt [Konfigurieren eines Datenspeichers](configure-datastream.md) Lektion, `Luma Web SDK`

   ![Wählen Sie den Datenspeicher des Luma Web SDK aus.](assets/datastream-luma-web-sdk.png)

1. Wählen Sie **[!UICONTROL Service hinzufügen]** aus
   ![Hinzufügen eines Dienstes zum Datastream](assets/experience-platform-addService.png)
1. Auswählen **[!UICONTROL Adobe Experience Platform]** als **[!UICONTROL Dienst]**
1. Auswählen `Luma Web Event Data` als **[!UICONTROL Ereignis-Datensatz]**

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Datenspeicherkonfiguration](assets/experience-platform-datastream-config.png)

Während Sie Traffic in der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) Ihrer Tag-Eigenschaft zugeordnet sind, füllen die Daten den Datensatz in Experience Platform!

## Datensatz validieren

Dieser Schritt ist wichtig, um sicherzustellen, dass die Daten im Datensatz gelandet sind. Es gibt zwei Aspekte bei der Validierung von Daten, die an den Datensatz gesendet werden.

* Validieren mit [!UICONTROL Experience Platform Debugger]
* Validieren mit [!UICONTROL Vorschau eines Datensatzes anzeigen]
* Validieren mit [!UICONTROL Query Service]

### Experience Platform Debugger

Diese Schritte entsprechen mehr oder weniger den Schritten in der [Debugger-Lektion](validate-with-debugger.md). Da Daten jedoch erst nach der Aktivierung im Datastream an Platform gesendet werden, müssen Sie weitere Beispieldaten generieren:

1. Öffnen Sie die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) und wählen Sie die [!UICONTROL Experience Platform Debugger] Erweiterungssymbol

1. Konfigurieren des Debuggers für die Zuordnung der Tag-Eigenschaft zu *Ihre* Entwicklungsumgebung, wie im Abschnitt [Validieren mit Debugger](validate-with-debugger.md) Lektion

   ![Ihre Launch-Entwicklungsumgebung im Debugger angezeigt](assets/experience-platform-debugger-dev.png)

1. Melden Sie auf der Site „Luma“ sich mit den folgenden Anmeldeinformationen an: `test@adobe.com`/`test`

1. Kehren Sie zur [Startseite „Luma“](https://luma.enablementadobe.com/content/luma/us/en.html) zurück.

1. Wählen Sie im vom Debugger angezeigten Platform Web SDK-Netzwerk-Beacon die Zeile &quot;Ereignisse&quot;aus, um Details in einem Popup-Fenster zu erweitern.

   ![Web SDK in Debugger](assets/experience-platform-debugger-dev-eventType.png)

1. Suchen Sie im Popup nach der &quot;identityMap&quot;. Hier sollten Sie lumaCrmId mit drei Schlüsseln von authenticatedState, id und primary sehen.
   ![Web SDK in Debugger](assets/experience-platform-debugger-dev-idMap.png)

Jetzt sollten Daten in die `Luma Web Event Data` Datensatz und bereit für die Validierung des Datensatzes in der Vorschau.

### Vorschau des Datensatzes anzeigen

Um zu bestätigen, dass die Daten im Data Lake von Platform gelandet sind, können Sie schnell mithilfe der **[!UICONTROL Datensatz-Vorschau]** Funktion. Web SDK-Daten werden in Mikro-Batches an den Data Lake gesendet und in der Platform-Oberfläche regelmäßig aktualisiert. Es kann 10-15 Minuten dauern, bis die von Ihnen generierten Daten angezeigt werden.

1. Im [Experience Platform](https://experience.adobe.com/platform/) Benutzeroberfläche, wählen Sie **[!UICONTROL Datensätze]** im linken Navigationsbereich, um die **[!UICONTROL Datensätze]** Dashboard.

   Das Dashboard listet alle verfügbaren Datensätze für Ihre Organisation auf. Zu jedem aufgelisteten Datensatz werden Details angezeigt, einschließlich seines Namens, des Schemas, dem der Datensatz entspricht, und des Status des letzten Erfassungslaufs.

1. Wählen Sie `Luma Web Event Data` Datensatz, um seine **[!UICONTROL Datensatzaktivität]** angezeigt.

   ![Dataset-Luma-Webereignis](assets/experience-platform-dataset-validation-lumaSDK.png)

   Der Aktivitätsbildschirm enthält ein Diagramm, das die Rate der konsumierten Nachrichten sowie eine Liste erfolgreicher und fehlgeschlagener Batches visualisiert.

1. Aus dem **[!UICONTROL Datensatzaktivität]** Bildschirm, auswählen **[!UICONTROL Datensatz-Vorschau]** in der oberen rechten Ecke des Bildschirms eine Vorschau von bis zu 100 Datenzeilen anzeigen. Wenn der Datensatz leer ist, wird der Vorschau-Link deaktiviert.

   ![Datensatzvorschau](assets/experience-platform-dataset-preview.png)

   Im Vorschaufenster wird rechts für den Datensatz die hierarchische Ansicht des Schemas angezeigt.

   ![Datensatzvorschau 1](assets/experience-platform-dataset-preview-1.png)

>[!INFO]
>
>Der Abfragedienst von Adobe Experience Platform ist eine zuverlässigere Methode zur Überprüfung von Daten im See, überschreitet jedoch den Rahmen dieses Tutorials. Weitere Informationen finden Sie unter [Daten durchsuchen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=de) im Abschnitt Platform-Tutorials .


## Datensatz und Schema für Echtzeit-Kundenprofil aktivieren

Der nächste Schritt besteht darin, den Datensatz und das Schema für das Echtzeit-Kundenprofil zu aktivieren. Das Daten-Streaming vom Web SDK ist eine von vielen Datenquellen, die in Platform fließen. Sie möchten Ihre Web-Daten mit anderen Datenquellen verbinden, um 360-Grad-Kundenprofile zu erstellen. Weitere Informationen zum Echtzeit-Kundenprofil finden Sie in diesem kurzen Video:

>[!VIDEO](https://video.tv.adobe.com/v/27251?learn=on&captions=eng)

>[!CAUTION]
>
>Wenn Sie mit Ihrer eigenen Website und Ihren eigenen Daten arbeiten, empfehlen wir eine zuverlässigere Validierung der Daten, bevor Sie sie für das Echtzeit-Kundenprofil aktivieren.


**So aktivieren Sie den Datensatz:**

1. Öffnen Sie den von Ihnen erstellten Datensatz, `Luma Web Event Data`

1. Wählen Sie die **[!UICONTROL Profil-Umschalter]** zum Aktivieren

   ![Profil-Umschalter](assets/setup-experience-platform-profile.png)

1. Bestätigen, dass Sie **[!UICONTROL Aktivieren]** den Datensatz

   ![Profil aktivieren - Umschalten](assets/setup-experience-platform-profile-enable.png)

**So aktivieren Sie das Schema:**

1. Öffnen Sie das von Ihnen erstellte Schema, `Luma Web Event Data`

1. Wählen Sie die **[!UICONTROL Profil-Umschalter]** zum Aktivieren

   ![Profil-Umschalter](assets/setup-experience-platform-profile-schema.png)

1. Auswählen **[!UICONTROL Daten für dieses Schema enthalten eine primäre Identität im Feld identityMap .]**

   >[!IMPORTANT]
   >
   >    Primäre Identitäten sind in jedem Datensatz erforderlich, der an das Echtzeit-Kundenprofil gesendet wird. Normalerweise werden Identitätsfelder innerhalb des Schemas beschriftet. Bei der Verwendung von Identitätszuordnungen sind die Identitätsfelder jedoch nicht im Schema sichtbar. In diesem Dialogfeld wird bestätigt, dass Sie eine primäre Identität im Hinterkopf haben und diese beim Senden Ihrer Daten in einer Identitätszuordnung angeben. Wie Sie wissen, verwendet das Web SDK eine Identitätszuordnung und die Experience Cloud ID (ECID) ist die primäre Standardidentität.


1. Auswählen **[!UICONTROL Aktivieren]**

   ![Profil aktivieren - Umschalten](assets/setup-experience-platform-profile-schema-enable.png)

1. Auswählen **[!UICONTROL Speichern]** Speichern des aktualisierten Schemas

Jetzt ist das Schema auch für das Profil aktiviert.

>[!IMPORTANT]
>
>    Nachdem ein Schema für Profil aktiviert wurde, kann es nicht mehr deaktiviert oder gelöscht werden. Außerdem können Felder nach diesem Punkt nicht mehr aus dem Schema entfernt werden. Diese Implikationen sollten Sie später bei der Arbeit mit Ihren eigenen Daten in Ihrer Produktionsumgebung berücksichtigen. Sie sollten in diesem Tutorial eine Entwicklungs-Sandbox verwenden, die jederzeit gelöscht werden kann.
>
>   
> Wir empfehlen, beim Arbeiten mit Ihren eigenen Daten die folgenden Schritte auszuführen:
> 
> * Erfassen Sie zunächst einige Daten in Ihren Datensätzen.
> * Beheben Sie alle Probleme, die während des Datenerfassungsprozesses auftreten (z. B. bei der Datenvalidierung oder bei der Zuordnung).
> * Datensätze und Schemata für Profile aktivieren
> * Erneutes Erfassen der Daten


### Profil überprüfen

Sie können in der Benutzeroberfläche von Platform (oder Journey Optimizer) nach einem Kundenprofil suchen, um zu bestätigen, dass die Daten im Echtzeit-Kundenprofil gelandet sind. Wie der Name schon sagt, werden Profile in Echtzeit ausgefüllt, sodass es keine Verzögerung gibt, wie es bei der Validierung von Daten im Datensatz der Fall war.

Zunächst müssen Sie weitere Beispieldaten generieren. Wiederholen Sie die Schritte aus dieser Lektion, um sich bei der Website Luma anzumelden, wenn sie Ihrer Tag-Eigenschaft zugeordnet ist. Inspect die Platform Web SDK-Anforderung, um sicherzustellen, dass Daten mit dem `lumaCRMId`.

1. Im [Experience Platform](https://experience.adobe.com/platform/) Benutzeroberfläche, wählen Sie **[!UICONTROL Profile]** im linken Navigationsbereich

1. Als **[!UICONTROL Identitäts-Namespace]** use `lumaCRMId`
1. Kopieren und Einfügen des Werts des `lumaCRMId` hat den Aufruf übergeben, den Sie im Experience Platform Debugger überprüft haben (wahrscheinlich `112ca06ed53d3db37e4cea49cc45b71e`).

   ![Profil](assets/experience-platform-validate-dataset-profile.png)

1. Wenn im Profil ein gültiger Wert für `lumaCRMId`, wird in der Konsole eine Profil-ID eingetragen:

   ![Profil](assets/experience-platform-validate-dataset-profile-set.png)

1. Klicken Sie in die [!UICONTROL Profil-ID] und [!UICONTROL Kundenprofil] -Konsole gefüllt. Hier können Sie alle Identitäten sehen, die mit dem `lumaCRMId`, beispielsweise die `ECID`:

   ![Kundenprofil](assets/experience-platform-validate-dataset-custProfile.png)

Sie haben jetzt das Platform Web SDK für Experience Platform (und Real-Time CDP) aktiviert! Und Customer Journey Analytics! Und Journey Optimizer!)!


[Weiter: ](setup-analytics.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)