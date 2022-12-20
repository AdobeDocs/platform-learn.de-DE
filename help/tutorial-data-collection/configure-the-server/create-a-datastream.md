---
title: Erstellen eines Datenspeichers
description: Erstellen eines Datenspeichers
exl-id: 4a33a7f3-8bd8-4d28-9ae4-a0609444485f
source-git-commit: cf0193e3aae4d6536c868f078f4773ee14e90408
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---

# Erstellen eines Datenspeichers

Die Daten, die Sie von Ihrer Website mit dem Platform Web SDK senden, erreichen eine Reihe von Adobe-Servern namens [Adobe Experience Platform Edge Network](https://business.adobe.com/products/experience-platform/experience-platform-edge-network.html). Dieses Netzwerk kann Ihre Daten an die [Adobe Experience Platform-Datensatz, den Sie zuvor erstellt haben](create-a-schema.md) und anderen Produkten in Adobe Experience Cloud. Diese Adobe-Produkte können auch mit Daten auf Ihre Webseite reagieren. Beispielsweise kann Edge Network Personalisierungsinhalte von Adobe Target zurückgeben.

Um zu konfigurieren, welche Adobe-Produkte das Edge Network Daten an und von übermittelt, müssen Sie einen Datastraam erstellen. Wenn Edge Network Daten von Ihrer Webseite erhält, prüft es den von Ihnen erstellten Datastrom, liest seine Konfiguration und leitet dann Daten an die entsprechenden Adobe-Produkte weiter.

![Produktkonfiguration für Datastream](../assets/datastream-diagram.png)

1. Um einen Datastream zu erstellen, müssen Sie zunächst zur Benutzeroberfläche &quot;Datenerfassung&quot;navigieren. Klicken Sie oben rechts in Platform auf das **[!UICONTROL Anwendungsauswahl]** und wählen Sie **[!UICONTROL Datenerfassung]** aus dem Dropdown-Menü.
   ![Datenerfassungsmenü](../assets/data-collection-menu.png)
1. Sobald die Datenerfassungs-Oberfläche angezeigt wird, wählen Sie **[!UICONTROL Datenspeicher]** in der linken Navigation und dann die **[!UICONTROL Neuer Datenspeicher]** in der oberen rechten Ecke.
1. Geben Sie einen Namen für den Datastream ein und wählen Sie [das zuvor von Ihnen erstellte Schema](create-a-schema.md) als **[!UICONTROL Ereignis-Datensatz]** und wählen Sie **[!UICONTROL Speichern]** (Das Mapping wird später behandelt).
   ![Name und Beschreibung des Datenspeichers](../assets/datastream-name-description.png)

## Dienst zu Datenspeicher hinzufügen

Im nächsten Bildschirm können Sie hinzufügen, welche Adobe-Produkte und -Dienste die von Ihrer Website gesendeten Daten erhalten sollen.

1. Wählen Sie die **[!UICONTROL Dienst hinzufügen]** Befehl. Aktivieren Sie in diesem Tutorial nur Adobe Experience Platform und wählen Sie [den zuvor erstellten Datensatz](create-a-dataset.md) und wählen Sie **[!UICONTROL Speichern]** in der oberen rechten Ecke. Ihr Datenspeicher wurde erstellt.
   ![Produktkonfiguration für Datastream](../assets/datastream-product-configuration.png)

## Datenspeicherumgebungen

Unternehmen haben normalerweise einen Promotionspfad für alle Website-Aktualisierungen. Jemand im Unternehmen (ein Marketing-Experte oder -Techniker, je nach Änderungen) testet seine Änderungen in einer Entwicklungsumgebung, die nur von dieser Person verwendet wird. Sobald sie mit den Änderungen vertraut sind, werden die Änderungen in eine Staging-Umgebung weitergeleitet, in der sie weitere Tests erhalten. Schließlich werden die Änderungen auf der Produktions-Website veröffentlicht, die Benutzer sehen. Datastreams unterstützen dieses Promotion-Muster.

Wenn Sie plattformbasierte Anwendungen wie Real-Time CDP, Journey Optimizer oder Customer Journey Analytics unterstützen, müssen zusätzliche Datenspeicher in den separaten Platform-Sandboxes erstellt werden, die diesen Umgebungen entsprechen.

Wenn Sie kein Platform-Kunde sind, können Sie mehrere Datenspeicher in einer Sandbox erstellen und die Funktion zum Kopieren von Datensätzen verwenden, um Einstellungen zu duplizieren.

Der Server ist nun vollständig für den Empfang von Daten von Ihrer Webseite konfiguriert.

[Weiter: ](../configure-the-client/whats-a-data-layer.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
