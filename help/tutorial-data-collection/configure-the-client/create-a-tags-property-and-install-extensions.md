---
title: Erstellen einer Adobe Experience Platform-Tag-Eigenschaft und Installieren von Erweiterungen
description: Erstellen einer Adobe Experience Platform-Tag-Eigenschaft und Installieren von Erweiterungen
exl-id: d0fe82b5-a036-4e13-bae1-d1fee78d0084
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# Erstellen einer Adobe Experience Platform [!DNL Tags] Property- und Installationserweiterungen

Jetzt, da der On-Page-Code Daten und Ereignisse in die Datenschicht pusht, ist es für den Marketing-Experten an der Zeit, die Daten aus der Datenschicht zu lesen und an Adobe Experience Platform zu senden. Dazu sind normalerweise zwei JavaScript-Bibliotheken erforderlich:

* Adobe Client-Datenschicht: In vorherigen Schritten haben Sie ein Datenschichtarray erstellt und Objekte in dieses eingefügt. Um auf diese Daten zugreifen zu können, müssen Sie die JavaScript-Bibliothek der Adobe Client-Datenschicht laden. Diese Bibliothek bietet Benachrichtigungen zu Ereignissen und Datenschichtänderungen sowie einfachen Zugriff auf die Daten.
* Adobe Experience Platform Web SDK: Diese JavaScript-Bibliothek kommuniziert mit dem [Adobe Experience Platform Edge Network](https://business.adobe.com/products/experience-platform/experience-platform-edge-network.html). Das SDK verarbeitet u. a. Identität, Einverständnis, Datenerfassung, Personalisierung, Zielgruppen und mehr.

Sie können diese einzelnen Bibliotheken zwar auf Ihre Website laden und sie direkt verwenden, es wird jedoch empfohlen, [Adobe Experience Platform Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de). Mit Tags können Sie ein einzelnes Skript in Ihre HTML einbetten und die Tags-Benutzeroberfläche verwenden, um sowohl die Adobe Client-Datenschicht als auch das Adobe Experience Platform Web SDK bereitzustellen. Mit Tags können Sie unter anderem auch Regeln zum Senden von Daten erstellen. In diesem Tutorial werden Tags zu diesem Zweck verwendet. Es wird davon ausgegangen, dass Sie über grundlegende Kenntnisse der Funktionsweise von Tags verfügen.

## Erstellen einer Eigenschaft innerhalb von Tags

1. [Erstellen einer Eigenschaft in Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html#create-or-configure-a-property).

## Installieren der Adobe Client-Datenschichterweiterung

Installieren Sie die Adobe Client-Datenschichterweiterung:

1. Auswählen **[!UICONTROL Erweiterungen]** in der linken Navigationsleiste in der Tag-Eigenschaft, die Sie für dieses Tutorial verwenden.
1. Wählen Sie die **[!UICONTROL Katalog]** links oben und suchen Sie dann nach &quot;Datenschicht&quot;.
1. Sobald die Adobe Client-Datenschicht in den Ergebnissen angezeigt wird, klicken Sie auf **[!UICONTROL Installieren]** Schaltfläche. Es sollte ein Konfigurationsbildschirm angezeigt werden. Für dieses Tutorial müssen die Standardwerte nicht geändert werden.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Installation der Adobe Client-Datenschicht-Erweiterung](../assets/acdl-extension-installation.png)


## Adobe Experience Platform Web SDK-Erweiterung installieren

Installieren Sie anschließend die Adobe Experience Platform Web SDK-Erweiterung:

1. Suchen Sie nach der Erweiterung im Erweiterungskatalog und klicken Sie auf die entsprechende **[!UICONTROL Installieren]** Schaltfläche. Der Konfigurationsbildschirm sollte angezeigt werden:
   ![Installation der Adobe Experience Platform Web SDK-Erweiterung](../assets/web-sdk-extension-installation.png)
1. Im [!UICONTROL Datastream] auswählen, den zuvor erstellten Datastream. Ihnen werden dieselben Datastream-Umgebungen angezeigt, in denen Sie [Erstellen eines Datenspeichers](../configure-the-server/create-a-datastream.md).
   ![Datenspeicherauswahl](../assets/web-sdk-datastream-selection.png)
1. Suchen und deaktivieren Sie im Konfigurationsbildschirm **[!UICONTROL Aktivieren der Klickdatenerfassung]**. Standardmäßig verfolgt das SDK automatisch Links für Sie. In diesem Tutorial zeigen wir jedoch, wie Sie Ihre eigenen Link-Klicks mithilfe benutzerspezifischer Linkinformationen verfolgen können.
1. Klicken Sie auf **[!UICONTROL Speichern]** Schaltfläche zum Abschließen der Installation der Adobe Experience Platform Web SDK-Erweiterung.

>[!TIP]
>
>Die Datensatzumgebungen haben eine Beziehung zu Tags-Umgebungen. Nehmen Sie an, dass Sie die Installation der Adobe Experience Platform Web SDK-Erweiterung abgeschlossen haben, erstellen Sie eine Tag-Bibliothek mit der Erweiterung und veröffentlichen Sie die Bibliothek dann in einer Tags-Entwicklungsumgebung. Wenn die Tag-Bibliothek auf Ihre Web-Seite geladen wird und die Adobe Experience Platform Web SDK-Erweiterung eine Anfrage an Edge Network sendet, enthält die Erweiterung die [!UICONTROL Entwicklungsumgebung] datastream-Umgebungs-ID. Edge Network verwendet diese ID wiederum, um die Konfiguration der [!UICONTROL Entwicklungsumgebung] Datastream-Umgebung und Weiterleiten von Daten an die entsprechenden Adobe-Produkte.
>
>Derzeit gibt es nur eine Entwicklungs-Datastream-Umgebung, eine Staging-Datastream-Umgebung und eine Produktions-Datastream-Umgebung. Es ist möglich, mithilfe der Benutzeroberfläche von datastream mehrere Datastream-Entwicklungsumgebungen (eine für Sie und eine für Ihren Kollegen) zu erstellen. Wenn Sie über mehrere Entwicklungs-Datastream-Umgebungen verfügen, können Sie auswählen, welche Sie für diese Tag-Eigenschaft verwenden möchten.


Die entsprechenden Erweiterungen wurden installiert. Es ist Zeit, Regeln und Datenelemente zu erstellen.

[Weiter: ](create-rules-for-tracking-page-view-and-commerce-events.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
