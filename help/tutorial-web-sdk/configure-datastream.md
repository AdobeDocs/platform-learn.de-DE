---
title: Konfigurieren eines Datenstroms
description: Erfahren Sie, wie Sie einen Datastream aktivieren und Experience Cloud-Lösungen konfigurieren. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Web SDK,Tags,Datastreams
exl-id: ca28374a-9fe0-44de-a7ac-0aa046712515
source-git-commit: 15bc08bdbdcb19f5b086267a6d94615cbfe1bac7
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 6%

---

# Konfigurieren eines Datenstroms


>[!CAUTION]
>
>Wir gehen davon aus, dass am Dienstag, dem 23. April 2024, wichtige Änderungen an diesem Tutorial veröffentlicht werden. Danach ändern sich viele Übungen und Sie müssen das Tutorial möglicherweise von Anfang an neu starten, um alle Lektionen abzuschließen.

Erfahren Sie, wie Sie einen Datastream aktivieren und Experience Cloud-Lösungen konfigurieren.

Datastreams teilen Adobe Experience Platform Edge Network mit, wohin vom Platform Web SDK erfasste Daten gesendet werden sollen. In der Konfiguration der Datenspeicher aktivieren Sie Ihre Experience Cloud-Anwendungen, Ihr Experience Platform-Konto und die Ereignisweiterleitung. Siehe [Grundlagen zum Konfigurieren eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=de) für detailliertere Informationen.

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen eines Datenspeichers
* Experience Cloud-Apps aktivieren
* Experience Platform aktivieren

## Voraussetzungen

Bevor Sie Ihren Datastream konfigurieren, müssen Sie bereits die folgenden Lektionen abgeschlossen haben:

* [Berechtigungen konfigurieren](configure-permissions.md)
* [Schema konfigurieren](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)

## Erstellen eines Datenspeichers

Jetzt können Sie einen Datastream erstellen, um Platform Edge Network mitzuteilen, wohin vom Web SDK erfasste Daten gesendet werden sollen.

**So erstellen Sie einen Datastream:**

1. Öffnen Sie die [Datenerfassungsoberfläche](https://launch.adobe.com/){target="_blank"}
1. Stellen Sie sicher, dass sich die richtige Sandbox befindet.

   >[!NOTE]
   >
   >Wenn Sie Platform-basierte Anwendungen wie Real-Time CDP verwenden, empfehlen wir für dieses Tutorial die Verwendung einer Entwicklungs-Sandbox. Wenn nicht, verwenden Sie die **[!UICONTROL Prod]** Sandbox.

1. Navigieren Sie zu **[!UICONTROL Datenspeicher]** in der linken Navigation
1. Auswählen **[!UICONTROL Neuer Datenspeicher]** auf der rechten Bildschirmseite.
1. Eingabe `Luma Web SDK` als **[!UICONTROL Name]**. Dieser Name wird später referenziert, wenn Sie die Web SDK-Erweiterung in Ihrer Tag-Eigenschaft konfigurieren.
1. Wählen Sie `Luma Web Event Data` als **[!UICONTROL Ereignisschema]**
1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Erstellen des Datastreams](assets/datastream-create-datastream.png)

   >[!AVAILABILITY]
   >
   >Die Zuordnungsfunktion wird in dieses Tutorial zu einem späteren Zeitpunkt einbezogen.




Auf dem nächsten Bildschirm können Sie Dienste wie Adobe-Anwendungen zum Datastream hinzufügen. Sie werden jedoch zu diesem Zeitpunkt im Tutorial keine Dienste hinzufügen. Sie werden dies später im Unterricht tun [Experience Platform einrichten](setup-experience-platform.md), [Einrichten von Analytics](setup-analytics.md), [Einrichten von Audience Manager](setup-audience-manager.md), [Einrichten von Target](setup-target.md)oder [Ereignisweiterleitung](setup-event-forwarding.md).

>[!NOTE]
>
>Bei der Implementierung des Platform Web SDK auf Ihrer eigenen Website sollten Sie drei Datenspeicher erstellen, die Ihren drei Tag-Umgebungen (Entwicklung, Staging und Produktion) zugeordnet werden. Wenn Sie das Platform Web SDK mit Platform-basierten Anwendungen wie Adobe Real-time Customer Data Platform oder Adobe Journey Optimizer verwenden, sollten Sie sicherstellen, dass Sie diese Datenspeicher in den entsprechenden Platform-Sandboxes erstellen.

Sie können jetzt die Platform Web SDK-Erweiterung in Ihrer Tag-Eigenschaft installieren!

[Weiter: ](install-web-sdk.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
