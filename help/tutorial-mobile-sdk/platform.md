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
ht-degree: 5%

---

# Daten an Experience Platform senden

Erfahren Sie, wie Sie Mobile-App-Daten an Adobe Experience Platform senden.

Diese optionale Lektion gilt für alle Kunden von Real-time Customer Data Platform (Real-Time CDP), Journey Optimizer und Customer Journey Analytics. Experience Platform, die Grundlage von Experience Cloud-Produkten, ist ein offenes System, das alle Ihre Daten (Adobe und Nicht-Adobe) in robuste Kundenprofile umwandelt. Diese Kundenprofile werden in Echtzeit aktualisiert und verwenden KI-gesteuerte Einblicke, um Ihnen dabei zu helfen, auf allen Kanälen die richtigen Erlebnisse bereitzustellen.

Die [Ereignis](events.md), [Lebenszyklus](lifecycle-data.md) und [Identität](identity.md)-Daten, die Sie in früheren Lektionen erfasst und an Platform Edge Network gesendet haben, werden an die in Ihrem Datenstrom konfigurierten Services weitergeleitet, einschließlich Adobe Experience Platform.

![Architektur](assets/architecture-aep.png)


## Voraussetzungen

Für Ihr Unternehmen müssen Berechtigungen bereitgestellt und für Adobe Experience Platform gewährt werden.

Wenn Sie keinen Zugriff haben, können Sie [diese Lektion überspringen](install-sdks.md).

## Lernziele

In dieser Lektion erfahren Sie Folgendes:

* Erstellen Sie einen Experience Platform-Datensatz.
* Konfigurieren Sie Ihren Datenstrom, um Daten an Experience Platform weiterzuleiten.
* Validieren von Daten im Datensatz.
* Aktivieren Sie Ihr Schema und Ihren Datensatz für das Echtzeit-Kundenprofil.
* Validieren von Daten im Echtzeit-Kundenprofil.
* Validieren von Daten im Identitätsdiagramm.


## Erstellen eines Datensatzes

Alle Daten, die erfolgreich in Adobe Experience Platform aufgenommen werden, bleiben als Datensätze im Data Lake erhalten. Ein Datensatz ist ein Konstrukt zur Datenspeicherung und -verwaltung (in der Regel eine Tabelle), die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben. Weitere Informationen finden [ in der ](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=de).

1. Navigieren Sie zur Experience Platform-Benutzeroberfläche, indem Sie sie oben rechts ![ Menü Apps ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg)Apps) auswählen.


1. Wählen **[!UICONTROL Datensätze]** im linken Navigationsmenü aus.

1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Datensatz erstellen]** aus.

1. Wählen Sie **[!UICONTROL Datensatz aus Schema erstellen]** aus.
   ![Datensatz - Startseite](assets/dataset-create.png)

1. Suchen Sie nach Ihrem Schema. Zum Beispiel mit `Luma Mobile` im Suchfeld.
1. Wählen Sie Ihr Schema aus, zum Beispiel **[!DNL Luma Mobile App Event Schema]**.

1. Klicken Sie auf **[!UICONTROL Weiter]**.
   ![Datensatz konfigurieren](assets/dataset-configure.png)

1. Geben Sie **[!UICONTROL Name]** ein, z. B. `Luma Mobile App Events Dataset` und eine **[!UICONTROL Beschreibung]**.

1. Wählen Sie **[!UICONTROL Beenden]** aus.
   ![Datensatz-Ende](assets/dataset-finish.png)


## Adobe Experience Platform-Datenstrom-Service hinzufügen

Um Ihre XDM-Daten aus dem Edge Network an Adobe Experience Platform zu senden, fügen Sie den Adobe Experience Platform-Service zu dem Datenstrom hinzu, den Sie im Rahmen von &quot;[ erstellen“ ](create-datastream.md).

>[!IMPORTANT]
>
>Sie können den Adobe Experience Platform-Service nur aktivieren, wenn Sie einen Ereignisdatensatz erstellt haben.

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche **[!UICONTROL Datenströme]** und Ihren Datenstrom aus.

1. Wählen Sie dann ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Service hinzufügen]** aus.

1. Wählen Sie **[!UICONTROL Adobe Experience Platform]** in der Liste [!UICONTROL Service] aus.

1. Aktivieren Sie den Service, indem Sie **[!UICONTROL Aktiviert]** einschalten.

1. Wählen Sie den **[!UICONTROL Ereignis-Datensatz]** aus, den Sie zuvor erstellt haben, z. B. **[!DNL Luma Mobile App Event Dataset]**.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Adobe Experience Platform als Datenstrom-Service hinzufügen](assets/datastream-service-aep.png)
1. Die endgültige Konfiguration sollte in etwa so aussehen.

   ![Datenstromeinstellungen](assets/datastream-settings.png)


## Validieren von Daten im Datensatz

Nachdem Sie nun einen Datensatz erstellt und Ihren Datenstrom aktualisiert haben, um Daten an Experience Platform zu senden, werden alle an Platform Edge Network gesendeten XDM-Daten an Platform weitergeleitet und landen im Datensatz.

Öffnen Sie die App und navigieren Sie zu Bildschirmen, auf denen Sie Ereignisse verfolgen. Sie können auch Trigger-Lebenszyklusmetriken erstellen.

Öffnen Sie Ihren Datensatz in der Platform-Benutzeroberfläche. Die Daten sollten in Stapeln an den Datensatz ankommen. Die Daten werden in der Regel alle 15 Minuten in Microbatches eintreffen, sodass Ihre Daten möglicherweise nicht sofort angezeigt werden.

![Validieren von Data Landing Platform-Datensatz-Batches](assets/platform-dataset-batches.png)

Sie sollten auch in der Lage sein, Beispieldatensätze und -felder mithilfe der Funktion **[!UICONTROL Vorschau des Datensatzes]** anzuzeigen:
![Validieren des an den Platform-Datensatz gesendeten Lebenszyklus](assets/lifecycle-platform-dataset.png)

Ein robusteres Tool zur Datenvalidierung ist der [Abfrage-Service](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=de) von Platform.

## Echtzeit-Kundenprofil aktivieren

Mit dem Echtzeit-Kundenprofil von Experience Platform können Sie eine ganzheitliche Sicht auf jeden einzelnen Kunden erstellen, indem Sie Daten aus verschiedenen Kanälen, einschließlich Online-, Offline-, CRM- und Drittanbieterdaten, kombinieren. Mit dem Profil können Sie Ihre unterschiedlichen Kundendaten in einer zentralen Sicht zusammenführen, die eine aussagekräftige, im Zeitverlauf gezeichnete Darstellung jeder Kundeninteraktion bietet.

### Aktivieren des Schemas

1. Öffnen Sie Ihr Schema, z. B. **[!DNL Luma Mobile App Event Schema]**.
1. Aktivieren Sie **[!UICONTROL Profil]**.
1. Wählen Sie **[!UICONTROL Daten für dieses Schema enthalten eine primäre Identität im identityMap -Feld.Im Dialogfeld]**.
1. **[!UICONTROL Speichern]** des Schemas.

   ![Aktivieren des Schemas für das Profil](assets/platform-profile-schema.png)

### Aktivieren des Datensatzes

1. Öffnen Sie den Datensatz, z. B. **[!DNL Luma Mobile App Event Dataset]**.
1. Aktivieren Sie **[!UICONTROL Profil]**.

   ![Aktivieren des Datensatzes für Profil](assets/platform-profile-dataset.png)

### Validieren von Daten im Profil

Öffnen Sie die App und navigieren Sie zu Bildschirmen, auf denen Sie Ereignisse verfolgen, z. B.: Melden Sie sich bei der Luma-App an und tätigen Sie einen Kauf.

Verwenden Sie Assurance, um eine der in der identityMap übergebenen Identitäten (E-Mail, lumaCrmId oder ECID) zu finden, z. B. die CRM-ID.

![Identitätswert erfassen](assets/platform-identity.png)

In der Platform-Oberfläche

1. Navigieren Sie zu **[!UICONTROL Profile]** und wählen Sie **[!UICONTROL Durchsuchen]** in der oberen Leiste aus.
1. Geben Sie die soeben erfassten Identitätsdetails an, z. B. `Luma CRM ID` für **[!UICONTROL Identity-Namespace]** und den Wert, den Sie für **[!UICONTROL Identitätswert]** kopiert haben. Wählen Sie dann **[!UICONTROL Ansicht]** aus.
1. Um Details anzuzeigen, wählen Sie das Profil aus.

![Identitätswert nachschlagen](assets/platform-profile-lookup.png)

Auf dem Bildschirm **[!UICONTROL Detail]** können Sie grundlegende Informationen über den Benutzer sehen, einschließlich der **[!UICONTROL **&#x200B; verknüpften Identitäten &#x200B;**]**:
![Profildetails](assets/platform-profile-details.png)

Auf der **[!UICONTROL Ereignisse]** können Sie die Ereignisse sehen, die von Ihrer Mobile-App-Implementierung für diesen Benutzer erfasst wurden:

![Profilereignisse](assets/platform-profile-events.png)


Vom Bildschirm mit den Profildetails:

1. Um das Identitätsdiagramm anzuzeigen, klicken Sie auf den Link oder navigieren Sie **[!UICONTROL Identitäten]** und wählen Sie dann **[!UICONTROL Identitätsdiagramm]** aus der oberen Leiste aus.
1. Um den Identitätswert nachzuschlagen, geben Sie `Luma CRM ID` als **[!UICONTROL Identity-Namespace]** und den kopierten Wert als **[!UICONTROL Identitätswert]** an. Wählen Sie dann **[!UICONTROL Ansicht]** aus.

   Diese Visualisierung zeigt Ihnen alle Identitäten, die in einem Profil miteinander verknüpft sind, und deren Herkunft. Im Folgenden finden Sie ein Beispiel für ein Identitätsdiagramm, das aus den Daten besteht, die im Rahmen des Absolvierens sowohl dieses Tutorials zu Mobile SDK (Data Source 2) als auch des Tutorials zu [Web SDK](https://experienceleague.adobe.com/de/docs/platform-learn/implement-web-sdk/overview) (Data Source 1) erfasst wurden:

   ![Identitätswert erfassen](assets/platform-profile-identitygraph.png)


## Nächste Schritte

Marketing-Experten und Analytiker können noch viel mehr mit den im Experience Platform erfassten Daten anfangen, einschließlich ihrer Analyse im Customer Journey Analytics und der Erstellung von Segmenten in Real-time Customer Data Platform. Du hast einen guten Start!


>[!SUCCESS]
>
>Sie haben jetzt Ihre App so eingerichtet, dass Daten nicht nur an das Edge Network, sondern auch an Adobe Experience Platform gesendet werden.<br>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796?profile.language=de).

Weiter: **[Push-Benachrichtigungen erstellen und senden](journey-optimizer-push.md)**
