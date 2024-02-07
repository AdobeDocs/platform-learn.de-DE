---
title: Konfigurieren eines Datenstroms
description: Erfahren Sie, wie Sie einen Datastream aktivieren und Experience Cloud-Lösungen konfigurieren. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Web SDK,Datastreams
source-git-commit: ef3d374f800905c49cefba539c1ac16ee88c688b
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 5%

---

# Konfigurieren eines Datenstroms

Erfahren Sie, wie Sie einen Datastream aktivieren und Experience Cloud-Anwendungen konfigurieren.

Datastreams teilen dem Adobe Experience Platform Edge Network mit, wohin vom Platform Web SDK erfasste Daten gesendet werden sollen. In der Konfiguration der Datenspeicher aktivieren Sie Ihre Experience Cloud-Anwendungen, Ihr Experience Platform-Konto und die Ereignisweiterleitung. Siehe [Grundlagen zum Konfigurieren eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de) für detailliertere Informationen.


![Web SDK, Datenspeicher und Edge-Netzwerkdiagramm](assets/dc-websdk-datastreams.png)

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen eines Datenspeichers
* Erste Schritte mit Datastream-Überschreibungen

## Voraussetzungen

Bevor Sie Ihren Datastream konfigurieren, müssen Sie bereits die folgenden Lektionen abgeschlossen haben:

* [Schema konfigurieren](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)

## Erstellen eines Datenspeichers

Jetzt können Sie einen Datastream erstellen, um Platform Edge Network mitzuteilen, wohin die vom Web SDK erfassten Daten gesendet werden sollen.

**So erstellen Sie einen Datastream:**

1. Öffnen Sie die [Datenerfassungsoberfläche](https://launch.adobe.com/){target="_blank"}
1. Stellen Sie sicher, dass sich die richtige Sandbox befindet.

   >[!NOTE]
   >
   >Wenn Sie Platform-basierte Anwendungen wie Real-Time CDP oder Journey Optimizer nutzen, empfehlen wir für dieses Tutorial die Verwendung einer Entwicklungs-Sandbox. Wenn nicht, verwenden Sie die **[!UICONTROL Prod]** Sandbox.

1. Navigieren Sie zu **[!UICONTROL Datenspeicher]** in der linken Navigation
1. Auswählen **[!UICONTROL Neuer Datenspeicher]** auf der rechten Bildschirmseite.
1. Eingabe `Luma Web SDK: Development Environment` als **[!UICONTROL Name]**. Dieser Name wird später referenziert, wenn Sie die Web SDK-Erweiterung in Ihrer Tag-Eigenschaft konfigurieren.
1. Wählen Sie `Luma Web Event Data` als **[!UICONTROL Ereignisschema]**
1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Erstellen des Datastreams](assets/datastream-create-new-datastream.png)

Auf dem nächsten Bildschirm können Sie Dienste wie Adobe-Anwendungen zum Datastream hinzufügen. Sie werden jedoch zu diesem Zeitpunkt im Tutorial keine Dienste hinzufügen. Sie werden dies später im Unterricht tun [Experience Platform einrichten](setup-experience-platform.md), [Einrichten von Analytics](setup-analytics.md), [Einrichten von Audience Manager](setup-audience-manager.md), [Einrichten von Target](setup-target.md)oder [Ereignisweiterleitung](setup-event-forwarding.md).

>[!NOTE]
>
>Bei der Implementierung des Platform Web SDK auf Ihrer eigenen Website sollten Sie drei Datenspeicher erstellen, die Ihren drei Tag-Umgebungen (Entwicklung, Staging und Produktion) zugeordnet werden. Wenn Sie das Platform Web SDK mit Platform-basierten Anwendungen wie Adobe Real-time Customer Data Platform oder Adobe Journey Optimizer verwenden, sollten Sie sicherstellen, dass Sie diese Datenspeicher in den entsprechenden Platform-Sandboxes erstellen.

## Überschreiben eines Datastreams

Mit Datastream Overrides können Sie zusätzliche Konfigurationen für Ihre Datenspeicher definieren und dann Ihre Standardkonfiguration unter bestimmten Bedingungen aus Ihrer Implementierung überschreiben.


Die Außerkraftsetzung der Datastream-Konfiguration erfolgt in zwei Schritten:

1. Zunächst definieren Sie Ihre Datastream-Überschreibungen in der Datastream-Konfiguration. Dies muss pro Adobe-Anwendung erfolgen, die Sie überschreiben möchten.
1. Anschließend senden Sie die Überschreibungen entweder über eine Web SDK-Sendeereignisaktion oder eine Konfiguration in der Web SDK-Tag-Erweiterung an das Edge-Netzwerk.

Im [Einrichten von Adobe Analytics](setup-analytics.md) Lektion: Sie überschreiben die Report Suite für eine Seite mit der Ereignis-Aktion für das Senden des Platform Web SDK.

Siehe [Dokumentation zur Datastream-Konfiguration wird außer Kraft gesetzt](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overrides.html?lang=en) für detaillierte Anweisungen zum Überschreiben von Datenspeicherkonfigurationen.

Sie können jetzt die Platform Web SDK-Erweiterung in Ihrer Tag-Eigenschaft installieren!

[Weiter: ](install-web-sdk.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
