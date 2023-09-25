---
title: Identitäts-Namespace konfigurieren
description: Erfahren Sie, wie Sie Identitäts-Namespaces für die Verwendung mit dem Adobe Experience Platform Web SDK konfigurieren. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Web SDK,Tags,Identities
exl-id: 7719dff4-6b30-4fa0-acae-7491c3208f15
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 13%

---

# Identitäts-Namespace konfigurieren

Erfahren Sie, wie Sie Identitäts-Namespaces für die Verwendung mit dem Adobe Experience Platform Web SDK konfigurieren.

Die [Adobe Experience Platform Identity-Dienst](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de) legt eine gemeinsame Besucher-ID für alle Adobe-Lösungen fest, um Experience Cloud-Funktionen wie die Zielgruppenfreigabe zwischen-Lösungen zu unterstützen. Sie können auch Ihre eigenen Kunden-IDs an den Dienst senden, um geräteübergreifendes Targeting und Integrationen mit anderen Systemen wie z. B. Ihrem CRM-System (Customer Relationship Management) zu ermöglichen.

Wenn Ihre Website bereits den Experience Cloud ID-Dienst auf Ihrer Website verwendet - entweder über die Besucher-API oder die Tag-Erweiterung des Experience Cloud ID-Diensts - und Sie ihn bei der Migration zum Adobe Experience Platform Web SDK weiterhin verwenden möchten, müssen Sie die neueste Version der Besucher-API oder die Tag-Erweiterung des Experience Cloud ID-Diensts verwenden. Siehe [ID-Migration](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/overview.html?lang=en) für weitere Informationen.

>[!NOTE]
>
> Zu Demonstrationszwecken können Sie bei den Übungen in dieser Lektion die Identitätsdetails eines fiktiven Kunden erfassen, der bei der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) mithilfe der Anmeldeinformationen, **user: test@adobe.com / password: test**. Sie können diese Schritte zwar verwenden, um eine andere Identität für Ihre eigenen Zwecke zu erstellen, aber um die Funktionen der Identity Map in der Datenerfassungsoberfläche kennenzulernen, sollten Sie zunächst die Beispielidentität erfassen.

## Lernziele

Am Ende dieser Lektion können Sie:

* Identitäts-Namespaces verstehen
* Erstellen eines benutzerdefinierten Identitäts-Namespace zum Erfassen einer internen CRM-ID


## Voraussetzungen

Sie müssen die vorherigen Lektionen bereits abgeschlossen haben:

* [Berechtigungen konfigurieren](configure-permissions.md)
* [Konfigurieren von Schemas](configure-schemas.md)

>[!IMPORTANT]
>
>Die [Experience Cloud ID-Erweiterung](https://exchange.adobe.com/experiencecloud.details.100160.adobe-experience-cloud-id-launch-extension.html) ist bei der Implementierung des Adobe Experience Platform Web SDK nicht erforderlich, da die JavaScript-Bibliothek des Web SDK die Funktion des Besucher-ID-Diensts enthält.

## Erstellen eines Identity-Namespace

In dieser Übung erstellen Sie einen Identitäts-Namespace für das benutzerdefinierte Identitätsfeld von Luma, `lumaCrmId`. Identity-Namespaces spielen eine entscheidende Rolle beim Erstellen von Echtzeit-Kundenprofilen, da zwei übereinstimmende Werte im selben Namespace es zwei Datenquellen ermöglichen, ein Identitätsdiagramm zu erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über die Identität in Adobe Experience Platform zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27841?learn=on)

Erstellen Sie nun einen Namespace für die Luma CRM-ID:

1. Öffnen Sie die [Datenerfassungsoberfläche](https://launch.adobe.com/){target="_blank"}
1. Wählen Sie die Sandbox aus, die Sie für das Tutorial verwenden

   >[!NOTE]
   >
   >Wenn Sie Platform-basierte Anwendungen wie Real-Time CDP verwenden, empfehlen wir für dieses Tutorial die Verwendung einer Entwicklungs-Sandbox. Wenn nicht, verwenden Sie die **[!UICONTROL Prod]** Sandbox.

1. Auswählen **[!UICONTROL Identitäten]** in der linken Navigation
1. Klicken Sie auf **[!UICONTROL Durchsuchen]**

   In der Hauptbenutzeroberfläche der Seite wird eine Liste von Identitäts-Namespaces angezeigt, die ihren Namen, Identitätssymbole, das letzte aktualisierte Datum und die Frage, ob es sich um standardmäßige oder benutzerdefinierte Namespaces handelt, enthalten. Die rechte Leiste enthält Informationen zur Stärke des Identitätsdiagramms.

1. Wählen Sie **[!UICONTROL Identity-Namespace erstellen]** aus

   ![Identitäten anzeigen](assets/configure-identities-screen.png)

1. Geben Sie Details wie folgt an und wählen Sie **[!UICONTROL Erstellen]**.

   | Feld | Wert |
   |---------------|-----------|
   | Anzeigename | Luma CRM ID |
   | Identitätssymbol | lumaCrmId |
   | Typ | Geräteübergreifende ID |


   ![Erstellen von Namespaces](assets/identities-create-namespace.png)


   Der Identitäts-Namespace wird im **[!UICONTROL Identitäten]** angezeigt.

   ![Erstellen von Namespaces](assets/configure-identities-namespace-lumaCrmId.png)


>[!INFO]
>
> Im [Erstellen von Datenelementen](create-data-elements.md) In dieser Lektion erfahren Sie, wie Sie diesen Namespace beim Senden von Identitäten an Platform Edge Network verwenden.

## Erstellen Sie den Identitäts-Namespace in Ihrer Produktions-Sandbox

Aufgrund einer aktuellen Einschränkung in der Web SDK-Erweiterung müssen auch Identitäts-Namespaces in der Produktions-Sandbox erstellt werden, um den Namespace zum Senden von Daten an eine Entwicklungs-Sandbox zu verwenden. Wenn Sie also eine Entwicklungs-Sandbox für dieses Tutorial verwendet haben, erstellen Sie auch die `Luma CRM ID` -Namespace in Ihrer Produktions-Sandbox.

## Weitere Ressourcen

* [Identitätsdienst-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de)
* [Identity Service-API](https://www.adobe.io/experience-platform-apis/references/identity-service/)

Nachdem Identitäten vorhanden sind, kann der Datastream konfiguriert werden.

[Weiter: ](configure-datastream.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
