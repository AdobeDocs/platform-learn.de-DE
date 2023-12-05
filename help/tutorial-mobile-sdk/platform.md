---
title: Senden von Daten an Experience Platform mit Platform Mobile SDK
description: Erfahren Sie, wie Sie Daten an Experience Platform senden.
solution: Data Collection,Experience Platform
feature: Mobile SDK,Data Ingestion
jira: KT-14637
exl-id: fdd2c90e-8246-4d75-a6db-df3ef31946c4
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 6%

---

# Daten an Experience Platform senden

Erfahren Sie, wie Sie App-Daten an Adobe Experience Platform senden.

Diese optionale Lektion ist für alle Kunden von Real-time Customer Data Platform (Real-Time CDP), Journey Optimizer und Customer Journey Analytics relevant. Experience Platform, die Grundlage von Experience Cloud-Produkten, ist ein offenes System, das all Ihre Daten (Adobe und Nicht-Adobe) in robuste Kundenprofile umwandelt. Diese Kundenprofile werden in Echtzeit aktualisiert und verwenden KI-gestützte Einblicke, um Ihnen bei der Bereitstellung der richtigen Erlebnisse für alle Kanäle zu helfen.

Die [event](events.md), [Lebenszyklus](lifecycle-data.md), und [identity](identity.md) Daten, die Sie in früheren Lektionen gesammelt und an Platform Edge Network gesendet haben, werden an die in Ihrem Datastream konfigurierten Dienste weitergeleitet, einschließlich Adobe Experience Platform.

![Architektur](assets/architecture-aep.png)


## Voraussetzungen

Ihr Unternehmen muss freigeschaltet und Berechtigungen für Adobe Experience Platform gewährt werden.

Wenn Sie keinen Zugriff haben, können Sie [Diese Lektion überspringen](install-sdks.md).

## Lernziele

In dieser Lektion werden Sie:

* Erstellen Sie einen Experience Platform-Datensatz.
* Konfigurieren Sie Ihren Datenspeicher, um Daten an Experience Platform weiterzuleiten.
* Validieren Sie Daten im Datensatz.
* Aktivieren Sie Ihr Schema und Ihren Datensatz für das Echtzeit-Kundenprofil.
* Daten im Echtzeit-Kundenprofil validieren
* Validieren Sie Daten im Identitätsdiagramm.


## Erstellen eines Datensatzes

Alle Daten, die erfolgreich in Adobe Experience Platform aufgenommen wurden, werden im Data Lake als Datensätze persistiert. Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung (normalerweise eine Tabelle), die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben. Siehe [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=de) für Informationen.

1. Navigieren Sie zur Experience Platform-Benutzeroberfläche, indem Sie sie aus den Apps auswählen ![Apps](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) Menü oben rechts.


1. Auswählen **[!UICONTROL Datensätze]** aus dem linken Navigationsmenü.

1. Auswählen ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Datensatz erstellen]**.

1. Wählen Sie **[!UICONTROL Datensatz aus Schema erstellen]** aus.
   ![Datensatz-Homepage](assets/dataset-create.png)

1. Suchen Sie nach Ihrem Schema. zum Beispiel mit `Luma Mobile` im Suchfeld.
1. Wählen Sie beispielsweise Ihr Schema aus. **[!DNL Luma Mobile App Event Schema]**.

1. Klicken Sie auf **[!UICONTROL Weiter]**.
   ![Datensatzkonfiguration](assets/dataset-configure.png)

1. Stellen Sie eine **[!UICONTROL Name]**, beispielsweise `Luma Mobile App Events Dataset` und **[!UICONTROL Beschreibung]**.

1. Wählen Sie **[!UICONTROL Beenden]** aus.
   ![Datensatzfertigstellung](assets/dataset-finish.png)


## Hinzufügen des Adobe Experience Platform-Datenspeicherdiensts

Um Ihre XDM-Daten aus dem Edge-Netzwerk an Adobe Experience Platform zu senden, fügen Sie den Adobe Experience Platform-Dienst zum -Datastream hinzu, den Sie als Teil von [Erstellen eines Datenspeichers](create-datastream.md).

>[!IMPORTANT]
>
>Sie können den Adobe Experience Platform-Dienst nur aktivieren, wenn Sie einen Ereignisdatensatz erstellt haben.

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche die Option **[!UICONTROL Datenspeicher]** und Ihrem Datastream.

1. Wählen Sie anschließend ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Dienst hinzufügen]**.

1. Wählen Sie **[!UICONTROL Adobe Experience Platform]** in der Liste [!UICONTROL Service] aus.

1. Aktivieren Sie den Dienst, indem Sie **[!UICONTROL Aktiviert]** auf.

1. Wählen Sie die **[!UICONTROL Ereignis-Datensatz]** , die Sie zuvor erstellt haben, z. B. **[!DNL Luma Mobile App Event Dataset]**.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Hinzufügen von Adobe Experience Platform als Datenspeicherdienst](assets/datastream-service-aep.png)
1. Die endgültige Konfiguration sollte ungefähr so aussehen:

   ![Datenspeichereinstellungen](assets/datastream-settings.png)


## Daten im Datensatz validieren

Nachdem Sie nun einen Datensatz erstellt und Ihren Datastream aktualisiert haben, um Daten an Experience Platform zu senden, werden alle an Platform Edge Network gesendeten XDM-Daten an Platform weitergeleitet und landen im Datensatz.

Öffnen Sie die App und navigieren Sie zu Bildschirmen, auf denen Sie Ereignisse verfolgen. Sie können auch Trigger-Lebenszyklusmetriken verwenden.

Öffnen Sie Ihren Datensatz in der Platform-Oberfläche. Sie sollten die Daten sehen, die in Batches zum Datensatz eingehen. Die Daten werden in der Regel alle 15 Minuten in Mikrostapeln empfangen, sodass Ihre Daten möglicherweise nicht sofort angezeigt werden.

![Dateneinstiegs-Datensatz-Batches der Platform validieren](assets/platform-dataset-batches.png)

Sie sollten auch Beispieldatensätze und -felder mit der **[!UICONTROL Datensatz-Vorschau]** Funktion:
![Lebenszyklus überprüfen, der an Platform-Datensatz gesendet wird](assets/lifecycle-platform-dataset.png)

Ein robusteres Tool für die Validierung von Daten ist das [Abfragedienst](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=de).

## Echtzeit-Kundenprofil aktivieren

Mit Experience Platform Echtzeit-Kundenprofil können Sie eine ganzheitliche Ansicht jedes einzelnen Kunden erstellen, in der Daten aus mehreren Kanälen kombiniert werden, einschließlich Online-, Offline-, CRM- und Drittanbieter-Daten. Mit dem Profil können Sie Ihre unterschiedlichen Kundendaten in einer zentralen Sicht zusammenführen, die eine aussagekräftige, im Zeitverlauf gezeichnete Darstellung jeder Kundeninteraktion bietet.

### Aktivieren des Schemas

1. Öffnen Sie beispielsweise Ihr Schema. **[!DNL Luma Mobile App Event Schema]**.
1. Aktivieren **[!UICONTROL Profil]**.
1. Auswählen **[!UICONTROL Daten für dieses Schema enthalten eine primäre Identität im Feld identityMap .]** im Dialogfeld.
1. **[!UICONTROL Speichern]** das Schema.

   ![Aktivieren des Schemas für das Profil](assets/platform-profile-schema.png)

### Aktivieren des Datensatzes

1. Öffnen Sie beispielsweise Ihren Datensatz. **[!DNL Luma Mobile App Event Dataset]**.
1. Aktivieren **[!UICONTROL Profil]**.

   ![Datensatz für Profil aktivieren](assets/platform-profile-dataset.png)

### Daten im Profil überprüfen

Öffnen Sie die App und navigieren Sie zu Bildschirmen, auf denen Sie Ereignisse verfolgen, z. B.: Melden Sie sich bei der Luma-App an und tätigen Sie einen Kauf.

Verwenden Sie Assurance, um eine der Identitäten zu finden, die in der identityMap (E-Mail, lumaCrmId oder ECID) übergeben werden, z. B. die CRM-ID.

![Identitätswert abrufen](assets/platform-identity.png)

In der Platform-Benutzeroberfläche

1. Navigieren Sie zu **[!UICONTROL Profile]** und wählen Sie **[!UICONTROL Durchsuchen]** aus der oberen Leiste.
1. Geben Sie die Identitätsdetails an, die Sie gerade erfasst haben, beispielsweise `Luma CRM ID` für **[!UICONTROL Identitäts-Namespace]** und dem Wert, für den Sie kopiert haben **[!UICONTROL Identitätswert]**. Wählen Sie anschließend **[!UICONTROL Ansicht]**.
1. Um Details anzuzeigen, wählen Sie das Profil aus.

![Identitätswert nachschlagen](assets/platform-profile-lookup.png)

Im **[!UICONTROL Detail]** -Bildschirm sehen Sie grundlegende Informationen zum Benutzer, einschließlich der **[!UICONTROL ** verknüpfte Identitäten **]**:
![Profildetails](assets/platform-profile-details.png)

Im **[!UICONTROL Veranstaltungen]** können Sie die Ereignisse sehen, die von Ihrer Mobile-App-Implementierung für diesen Benutzer erfasst wurden:

![Profilereignisse](assets/platform-profile-events.png)


Auf dem Bildschirm mit den Profildetails:

1. Klicken Sie auf den Link oder navigieren Sie zu **[!UICONTROL Identitäten]**, wählen Sie **[!UICONTROL Identitätsdiagramm]** aus der oberen Leiste.
1. Um den Identitätswert nachzuschlagen, geben Sie `Luma CRM ID` als **[!UICONTROL Identitäts-Namespace]** und der kopierte Wert als **[!UICONTROL Identitätswert]**. Wählen Sie anschließend **[!UICONTROL Ansicht]**.

   Diese Visualisierung zeigt Ihnen alle Identitäten, die in einem Profil verknüpft sind, und deren Ursprung. Im Folgenden finden Sie ein Beispiel für ein Identitätsdiagramm, das aus Daten erstellt wurde, die aus dem Abschluss dieses Mobile SDK-Tutorials (Datenquelle 2) und der [Web SDK-Tutorial](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=de) (Datenquelle 1):

   ![Identitätswert abrufen](assets/platform-profile-identitygraph.png)


## Nächste Schritte

Marketingexperten und Analytics können viel mehr mit in Experience Platform erfassten Daten tun, z. B. mit der Analyse in Customer Journey Analytics und dem Erstellen von Segmenten in Real-time Customer Data Platform. Du hast einen guten Anfang gemacht!


>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass Daten nicht nur an das Edge-Netzwerk, sondern auch an Adobe Experience Platform gesendet werden.<br>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Push-Benachrichtigungen erstellen und senden](journey-optimizer-push.md)**
