---
title: Konfigurieren eines Identity-Namespace
description: Erfahren Sie, wie Sie Identity-Namespaces konfigurieren, die mit Adobe Experience Platform Web SDK verwendet werden sollen. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Identities
jira: KT-15400
exl-id: 7719dff4-6b30-4fa0-acae-7491c3208f15
source-git-commit: d73f9b3eafb327783d6bfacaf4d57cf8881479f7
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 12%

---

# Konfigurieren eines Identity-Namespace

Erfahren Sie, wie Sie Identity-Namespaces für die Verwendung mit dem Adobe Experience Platform Web SDK konfigurieren.

Der [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/de/docs/id-service/using/home) legt eine gemeinsame Besucher-ID (die ECID) für alle SDK-basierten Adobe-Anwendungen fest, um Experience Cloud-Funktionen wie die gemeinsame Nutzung von Audiences zwischen Programmen zu unterstützen. Sie können auch eigene Kunden-IDs an den Service senden, um geräteübergreifendes Targeting und Integrationen mit anderen Systemen zu ermöglichen, z. B. Ihrem CRM-System (Customer Relationship Management).

Der [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home) (ja, es gibt zwei!) verwendet die ECIDs und Kunden-IDs, um Identitätsdiagramme zu generieren, sodass Sie Attribute und Verhaltensweisen in Echtzeit-Kundenprofilen zusammenführen können.

>[!NOTE]
>
>Ein benutzerdefinierter Identity-Namespace ist _nicht erforderlich_ um Adobe Analytics, Adobe Target oder Adobe Audience Manager mit Web SDK zu implementieren (authentifizierte Identitäten können im `data`-Objekt anstelle des `xdm`-Objekts übergeben werden, wie Sie später sehen werden). Identity-Namespaces sind für plattformnative Programme wie Journey Optimizer, Real-Time Customer Data Platform und Customer Journey Analytics erforderlich. Sie können sich zwar dafür entscheiden, in Ihrer eigenen Implementierung keinen Identity-Namespace zu verwenden, dies wird jedoch im Rahmen dieses Tutorials erwartet.

>[!NOTE]
>
> Zu Demonstrationszwecken werden in den Übungen in dieser Lektion die Identitätsdetails eines fiktiven Kunden erfasst, der bei der Demo-Site [Luma“ angemeldet ](https://luma.enablementadobe.com/content/luma/us/en.html), und zwar mithilfe der Anmeldeinformationen **Benutzer: `test@test.com` / Kennwort: test**.

## Lernziele

Am Ende dieser Lektion können Sie:

* Identity-Namespaces verstehen
* Erstellen eines benutzerdefinierten Identity-Namespace zur Erfassung einer internen CRM-ID


## Voraussetzungen

Sie müssen die vorherigen Lektionen bereits abgeschlossen haben:

* [Konfigurieren von Schemata](configure-schemas.md)

>[!IMPORTANT]
>
>Die [Experience Cloud ID-Erweiterung](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) wird bei der Implementierung von Adobe Experience Platform Web SDK nicht benötigt, da die Web SDK JavaScript-Bibliothek die Funktionalität des Besucher-ID-Diensts enthält.
>
> Wenn Ihre Website bereits den Experience Cloud ID-Service auf Ihrer Website verwendet - entweder über die Visitor-API oder die Tag-Erweiterung des Experience Cloud ID-Service - und Sie ihn während der Migration zu Adobe Experience Platform Web SDK weiterhin verwenden möchten, müssen Sie die neueste Version der Visitor-API oder die Tag-Erweiterung des Experience Cloud ID-Service verwenden. Siehe [ID-Migration](https://experienceleague.adobe.com/de/docs/experience-platform/edge/identity/overview) für weitere Informationen.

## Erstellen eines Identity-Namespace

In dieser Übung erstellen Sie einen Identity-Namespace für das benutzerdefinierte Identitätsfeld von Luma, `lumaCrmId`. Identity-Namespaces spielen eine entscheidende Rolle beim Erstellen von Echtzeit-Kundenprofilen, da zwei übereinstimmende Werte im selben Namespace es zwei Datenquellen ermöglichen, ein Identitätsdiagramm zu erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Identitäten in Adobe Experience Platform zu erfahren:

>[!VIDEO](https://video.tv.adobe.com/v/3422772?learn=on&enablevpops&captions=ger)

Erstellen Sie jetzt einen Namespace für die Luma CRM-ID:

1. Öffnen Sie die [Datenerfassungsschnittstelle](https://experience.adobe.com/data-collection/){target="_blank"}
1. Wählen Sie die für das Tutorial verwendete Sandbox aus

   >[!NOTE]
   >
   >Wenn Sie Kunde eines plattformbasierten Programms wie Real-Time CDP oder Journey Optimizer sind, empfehlen wir, für dieses Tutorial eine Entwicklungs-Sandbox zu verwenden. Andernfalls verwenden Sie die **[!UICONTROL Prod]**-Sandbox.

1. Wählen **[!UICONTROL Identitäten]** im linken Navigationsbereich aus
1. Wählen Sie **[!UICONTROL Durchsuchen]** aus

   In der Hauptbenutzeroberfläche der Seite wird eine Liste mit Identitäts-Namespaces angezeigt, die Namen, Identitätssymbole, das Datum der letzten Aktualisierung und Informationen darüber enthalten, ob es sich um standardmäßige oder benutzerdefinierte Namespaces handelt. Die rechte Leiste enthält Informationen zur [!UICONTROL Stärke des Identitätsdiagramms].

1. Wählen Sie **[!UICONTROL Identity-Namespace erstellen]**

   ![Anzeigen von Identitäten](assets/configure-identities-screen.png)

1. Geben Sie die Details wie folgt an und wählen Sie **[!UICONTROL Erstellen]**.

   | Feld | Wert |
   |---------------|-----------|
   | Anzeigename | Luma CRM ID |
   | Identitätssymbol | lumaCrmId |
   | Typ | Individuelle geräteübergreifende ID |


   ![Erstellen von Namespaces](assets/identities-create-namespace.png)


   Der Identity-Namespace wird im Bildschirm **[!UICONTROL Identitäten]** angezeigt.

   ![Erstellen von Namespaces](assets/configure-identities-namespace-lumaCrmId.png)


>[!NOTE]
>
> In der Lektion [Identitäten erstellen](create-identities.md) erfahren Sie, wie Sie diesen Namespace verwenden, wenn Sie Identitäten an Platform Edge Network senden.

Nachdem Identitäten eingerichtet sind, kann der Datenstrom konfiguriert werden.

[Weiter: ](configure-datastream.md)

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996?profile.language=de)
