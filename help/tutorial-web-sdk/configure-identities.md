---
title: Identitäts-Namespace konfigurieren
description: Erfahren Sie, wie Sie Identitäts-Namespaces für die Verwendung mit dem Adobe Experience Platform Web SDK konfigurieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Identities
jira: KT-15400
exl-id: 7719dff4-6b30-4fa0-acae-7491c3208f15
source-git-commit: 1a4f2e3813a6db4bef77753525c8a7d40692a4b2
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 12%

---

# Identitäts-Namespace konfigurieren

Erfahren Sie, wie Sie Identity-Namespaces für die Verwendung mit dem Adobe Experience Platform Web SDK konfigurieren.

Der [Adobe Experience Cloud Identity-Dienst](https://experienceleague.adobe.com/de/docs/id-service/using/home) legt eine allgemeine Besucher-ID (ECID) für SDK-basierte Adobe-Anwendungen fest, um Experience Cloud-Funktionen wie die Zielgruppenfreigabe zwischen-Anwendungen zu unterstützen. Sie können auch Ihre eigenen Kunden-IDs an den Dienst senden, um geräteübergreifendes Targeting und Integrationen mit anderen Systemen wie z. B. Ihrem CRM-System (Customer Relationship Management) zu ermöglichen.

Der [Adobe Experience Platform Identity-Dienst](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) (ja, es gibt zwei!) verwendet die ECIDs und Kunden-IDs zum Generieren von Identitätsdiagrammen, sodass Sie Attribute und Verhaltensweisen mit Echtzeit-Kundenprofilen zusammenführen können.

>[!NOTE]
>
>Ein benutzerdefinierter Identitäts-Namespace ist _nicht erforderlich_ , um Adobe Analytics, Adobe Target oder Adobe Audience Manager mit dem Web SDK zu implementieren (authentifizierte Identitäten können im `data` -Objekt anstelle des `xdm` -Objekts übergeben werden, wie Sie später sehen werden). Identitäts-Namespaces sind für plattformnative Anwendungen wie Journey Optimizer, Real-time Customer Data Platform und Customer Journey Analytics erforderlich. Sie können sich zwar entscheiden, keinen Identitäts-Namespace in Ihrer eigenen Implementierung zu verwenden, doch wird dies im Rahmen dieses Tutorials erwartet.

>[!NOTE]
>
> Zu Demonstrationszwecken lassen Sie die Übungen in dieser Lektion die Identitätsdetails eines fiktiven Kunden erfassen, der sich mit den Anmeldedaten **Benutzer: `test@adobe.com` / Passwort: test** bei der [Luma Demo Site](https://luma.enablementadobe.com/content/luma/us/en.html) angemeldet hat.

## Lernziele

Am Ende dieser Lektion können Sie:

* Identitäts-Namespaces verstehen
* Erstellen eines benutzerdefinierten Identitäts-Namespace zum Erfassen einer internen CRM-ID


## Voraussetzungen

Sie müssen die vorherigen Lektionen bereits abgeschlossen haben:

* [Konfigurieren von Schemas](configure-schemas.md)

>[!IMPORTANT]
>
>Die [Experience Cloud ID-Erweiterung](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) ist bei der Implementierung des Adobe Experience Platform Web SDK nicht erforderlich, da die Web SDK JavaScript-Bibliothek die Funktion des Besucher-ID-Diensts enthält.
>
> Wenn Ihre Website bereits den Experience Cloud ID-Dienst auf Ihrer Website verwendet - entweder über die Besucher-API oder die Tag-Erweiterung des Experience Cloud ID-Diensts - und Sie ihn bei der Migration zum Adobe Experience Platform Web SDK weiterhin verwenden möchten, müssen Sie die neueste Version der Besucher-API oder die Tag-Erweiterung des Experience Cloud ID-Diensts verwenden. Weitere Informationen finden Sie unter [ID-Migration](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/overview) .

## Erstellen eines Identitäts-Namespace

In dieser Übung erstellen Sie einen Identitäts-Namespace für das benutzerdefinierte Identitätsfeld von Luma, `lumaCrmId`. Identity-Namespaces spielen eine entscheidende Rolle beim Erstellen von Echtzeit-Kundenprofilen, da zwei übereinstimmende Werte im selben Namespace es zwei Datenquellen ermöglichen, ein Identitätsdiagramm zu erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über die Identität in Adobe Experience Platform zu erfahren:

>[!VIDEO](https://video.tv.adobe.com/v/27841?learn=on)

Erstellen Sie nun einen Namespace für die Luma CRM-ID:

1. Öffnen Sie die [Datenerfassungsschnittstelle](https://launch.adobe.com/){target="_blank"} .
1. Wählen Sie die Sandbox aus, die Sie für das Tutorial verwenden

   >[!NOTE]
   >
   >Wenn Sie Platform-basierte Anwendungen wie Real-Time CDP oder Journey Optimizer nutzen, empfehlen wir für dieses Tutorial die Verwendung einer Entwicklungs-Sandbox. Ist dies nicht der Fall, verwenden Sie die Sandbox **[!UICONTROL Prod]** .

1. Wählen Sie **[!UICONTROL Identitäten]** im linken Navigationsbereich aus.
1. Auswählen **[!UICONTROL Durchsuchen]**

   In der Hauptbenutzeroberfläche der Seite wird eine Liste von Identitäts-Namespaces angezeigt, die ihren Namen, Identitätssymbole, das letzte aktualisierte Datum und die Frage, ob es sich um standardmäßige oder benutzerdefinierte Namespaces handelt, enthalten. Die rechte Leiste enthält Informationen zur Stärke des Identitätsdiagramms ].[!UICONTROL 

1. Wählen Sie **[!UICONTROL Identitäts-Namespace erstellen]**

   ![Identitäten anzeigen](assets/configure-identities-screen.png)

1. Geben Sie die Details wie folgt an und wählen Sie **[!UICONTROL Erstellen]** aus.

   | Feld | Wert |
   |---------------|-----------|
   | Anzeigename | Luma CRM ID |
   | Identitätssymbol | lumaCrmId |
   | Typ | Individuelle geräteübergreifende ID |


   ![Erstellen von Namespaces](assets/identities-create-namespace.png)


   Der Identitäts-Namespace wird im Bildschirm **[!UICONTROL Identitäten]** angezeigt.

   ![Erstellen von Namespaces](assets/configure-identities-namespace-lumaCrmId.png)


>[!NOTE]
>
> In der Lektion [Identitäten erstellen](create-identities.md) erfahren Sie, wie Sie diesen Namespace beim Senden von Identitäten an Platform Edge Network verwenden.

Nachdem Identitäten vorhanden sind, kann der Datastream konfiguriert werden.

[Weiter: ](configure-datastream.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
