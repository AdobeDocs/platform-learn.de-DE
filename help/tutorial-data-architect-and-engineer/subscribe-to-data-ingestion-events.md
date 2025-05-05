---
title: Abonnieren von Datenerfassungsereignissen
seo-title: Subscribe to data ingestion events | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Abonnieren von Datenerfassungsereignissen
description: In dieser Lektion abonnieren Sie Datenerfassungsereignisse, indem Sie einen Webhook mit dem Adobe Developer Console und ein Online-Webhook-Entwicklungs-Tool einrichten. Sie verwenden diese Ereignisse, um den Status Ihrer Datenaufnahmevorgänge in den nachfolgenden Lektionen zu überwachen.
role: Data Engineer
feature: Data Management
jira: KT-4348
thumbnail: 4348-subscribe-to-data-ingestion-events.jpg
exl-id: f4b90832-4415-476f-b496-2f079b4fcbbc
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 4%

---

# Abonnieren von Datenerfassungsereignissen

<!--25min-->

In dieser Lektion abonnieren Sie Datenerfassungsereignisse, indem Sie einen Webhook mit dem Adobe Developer Console und ein Online-Webhook-Entwicklungs-Tool einrichten. Sie verwenden diese Ereignisse, um den Status Ihrer Datenaufnahmevorgänge in den nachfolgenden Lektionen zu überwachen.

**Dateningenieure** können Datenaufnahmeereignisse außerhalb dieses Tutorials abonnieren.
**Datenarchitekten** _können diese Lektion_ überspringen und zur Lektion [Batch-Aufnahme“ ](ingest-batch-data.md).

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Durchführen dieser Lektion erforderlich sind, insbesondere:

<!--* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

>[!IMPORTANT]
>
> Diese Benachrichtigungen, die durch die Datenerfassungsereignisse ausgelöst werden, gelten für _alle Ihre Sandboxes_ und nicht nur für Ihre `Luma Tutorial`. Möglicherweise werden in Ihrem Konto auch Benachrichtigungen angezeigt, die von anderen Datenerfassungsereignissen stammen.


## Webhook einrichten

In dieser Übung erstellen wir einen Webhook mit einem Online-Tool namens webhook.site (Sie können auch ein anderes Webhook-Entwicklungs-Tool verwenden, das Sie bevorzugen):

1. Öffnen Sie in einer anderen Browser-Registerkarte die Website [https://webhook.site/](https://webhook.site/)
1. Ihnen wird eine eindeutige URL zugewiesen, die Sie mit einem Lesezeichen versehen sollten, wenn Sie später in den Lektionen zur Datenaufnahme zu ihr zurückkehren:

   ![Webhook.site](assets/ioevents-webhook-home.png)
1. Wählen Sie die **Bearbeiten** in der oberen Navigationsleiste aus
1. Geben Sie als Antworttext `$request.query.challenge$` ein. Die Adobe I/O-Ereignis-Benachrichtigungen, die wir später in dieser Lektion einrichten, senden eine Abfrage an den Webhook und erfordern, dass er im Antworttext enthalten ist.
1. Klicken Sie auf **Speichern**.

   ![Bearbeiten der Antwort](assets/ioevents-webhook-editResponse.png)

## Einrichten

1. Öffnen Sie in einer anderen Browser-Registerkarte die [Adobe Developer Console](https://console.adobe.io/)
1. `Luma Tutorial API Project` öffnen
1. Klicken Sie auf **[!UICONTROL Schaltfläche „Zum Projekt hinzufügen]** und wählen Sie dann **[!UICONTROL Ereignis]**

   ![Ereignis hinzufügen](assets/ioevents-addEvents.png)
1. Filtern Sie die Liste durch Auswahl von **[!UICONTROL Experience Platform]**
1. Wählen Sie **[!UICONTROL Platform-Benachrichtigungen]**
1. Klicken Sie auf **[!UICONTROL Weiter]**-Schaltfläche
   ![Hinzufügen der Benachrichtigungen](assets/ioevents-addNotifications.png)
1. Alle Ereignisse auswählen
1. Klicken Sie auf **[!UICONTROL Weiter]**-Schaltfläche
   ![Abonnements auswählen](assets/ioevents-addSubscriptions.png)
1. Klicken Sie im nächsten Bildschirm zum Konfigurieren der Anmeldeinformationen erneut auf **[!UICONTROL Weiter]**.
   ![Überspringen des Berechtigungsbildschirms](assets/ioevents-clickNext.png)
1. Geben Sie als **[!UICONTROL Name der Ereignisregistrierung]** `Platform notifications` ein
1. Scrollen Sie nach unten und wählen Sie aus, um den Abschnitt **[!UICONTROL Webhook]** zu öffnen
1. Fügen Sie als **[!UICONTROL Webhook-URL]** den Wert aus dem Feld **Ihre eindeutige URL** von webhook.site ein
1. Klicken Sie auf **[!UICONTROL Schaltfläche „Konfigurierte Ereignisse speichern]**
   ![Ereignisse speichern](assets/ioevents-addWebhook.png)
1. Warten Sie, bis die Konfiguration gespeichert wurde. Ihr `Platform notifications`-Ereignis ist aktiv mit Ihren Webhook-Details und keinen Fehlermeldungen
   ![Konfiguration gespeichert](assets/ioevents-webhookConfigured.png)
1. Wechseln Sie zurück zur Registerkarte Webhook.site , und Sie sollten die erste Anforderung für den Webhook sehen, die aus der Validierung Ihrer Developer Console-Konfiguration resultiert:
   ![Erste Anfrage in webhook.site](assets/ioevents-webhook-firstRequest.png)

So ist es vorerst. In den nächsten Lektionen erfahren Sie mehr über diese Benachrichtigungen, wenn Sie Daten aufnehmen.

## Weitere Ressourcen

* [Webhook.site](https://webhook.site/)
* [Dokumentation zu Datenerfassungsbenachrichtigungen](https://experienceleague.adobe.com/docs/experience-platform/ingestion/quality/subscribe-events.html?lang=de)
* [Erste Schritte mit der Dokumentation zu Adobe I/O Events](https://www.adobe.io/apis/experienceplatform/events/docs.html)

Ok, fangen wir endlich an [Daten aufzunehmen](ingest-batch-data.md)!
