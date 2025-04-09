---
title: Zuordnen von Identitäten
seo-title: Map identities | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Zuordnen von Identitäten
description: In dieser Lektion erstellen wir Identitäts-Namespaces und fügen unseren Schemata Identitätsfelder hinzu.
role: Data Architect
feature: Profiles
jira: KT-4348
thumbnail: 4348-map-identities.jpg
exl-id: e17ffabc-049c-42ff-bf0a-8cc31d665dfa
source-git-commit: 73645b8b088cfdfe6f256c187b3c510dcc2386fc
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 6%

---

# Zuordnen von Identitäten

<!-- 30 min-->

In dieser Lektion erstellen wir Identitäts-Namespaces und fügen unseren Schemata Identitätsfelder hinzu. Danach können wir auch die Schemabeziehungen aus der vorherigen Lektion abschließen.

Adobe Experience Platform Identity Service hilft Ihnen, sich einen besseren Überblick über Ihre Kunden und deren Verhalten zu verschaffen, indem Identitäten geräte- und systemübergreifend zusammengeführt werden. So können Sie in Echtzeit für eindrucksvolle persönliche digitale Erlebnisse sorgen. Identitätsfelder und Namespaces verbinden verschiedene Datenquellen miteinander, um das 360-Grad-Echtzeit-Kundenprofil zu erstellen.

**Datenarchitekten** müssen Identitäten außerhalb dieses Tutorials zuordnen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Identitäten in Adobe Experience Platform zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27841?learn=on&enablevpops)

>[!NOTE]
>
>Identitätsfelder sind nur erforderlich, wenn Sie Echtzeit-Kundenprofile erstellen. Sie sind nicht erforderlich, wenn Sie nur Daten in den Data Lake aufnehmen.

<!--explain identity maps-->
<!--explain the strategy behind the identity selection, how these identities will join all the data together-->

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschließen dieser Lektion erforderlich sind.

<!--
* Permission items **[!UICONTROL Identity Management]** > **[!UICONTROL View Identity Namespaces]** and **[!UICONTROL Manage Identity Namespaces]**
* Permission item **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Identity-Namespace erstellen

In dieser Übung erstellen wir Identity-Namespaces für die benutzerdefinierten Identitätsfelder, `loyaltyId`, `crmId` und `productSku` von Luma. Identity-Namespaces spielen eine entscheidende Rolle beim Erstellen von Echtzeit-Kundenprofilen, da zwei übereinstimmende Werte im selben Namespace es zwei Datenquellen ermöglichen, ein Identitätsdiagramm zu erstellen.


### Erstellen von Namespaces in der Benutzeroberfläche

Erstellen wir zunächst einen Namespace für das Luma-Treueschema:

1. Wechseln Sie in der Platform-Benutzeroberfläche **[!UICONTROL linken]** zu „Identitäten“
1. Sie werden feststellen, dass mehrere vordefinierte Identity-Namespaces verfügbar sind. Klicken Sie auf **[!UICONTROL Schaltfläche Identity-Namespace]** .
1. Geben Sie Details wie folgt an

   | Feld | Wert |
   |---------------|-----------|
   | Anzeigename | Luma-Treue-ID |
   | Identitätssymbol | lumaLoyaltyId |
   | Typ | Geräteübergreifend |

1. Wählen Sie **[!UICONTROL Erstellen]**

   ![Erstellen von Namespaces](assets/identity-createNamespace.png)

Richten Sie jetzt einen anderen Namespace für das Luma-Produktkatalogschema mit den folgenden Details ein:

| Feld | Wert |
|---------------|-----------|
| Anzeigename | Luma-Produkt-SKU |
| Identitätssymbol | lumaProductSKU |
| Typ | Nicht personenbezogene Kennung |



## Erstellen von Identity-Namespaces mit API

Wir erstellen unseren CRM-Namespace über die API.

>[!NOTE]
>
>Wenn Sie die API-Übungen überspringen möchten, können Sie den CRM-Namespace mithilfe der von Ihnen verwendeten Benutzeroberflächenmethode mit den folgenden Details erstellen:
>
> 1. Verwenden Sie als **[!UICONTROL Anzeigename]** die `Luma CRM Id`
> 1. Verwenden Sie als **[!UICONTROL Identitätssymbol]** die `lumaCrmId`
> 1. Verwenden Sie **[!UICONTROL Typ]** die Option Geräteübergreifend

Erstellen wir die Identity-Namespace-`Luma CRM Id`:

1. Laden Sie [Identity Service.postman_collection.json](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Identity%20Service.postman_collection.json) in Ihren `Luma Tutorial Assets` Ordner herunter
1. Importieren der Sammlung in [!DNL Postman]
1. Wenn Sie kein Zugriffs-Token haben, öffnen Sie die Anfrage-**[!DNL OAuth: Request Access Token]** und wählen Sie **Senden** aus, um ein neues Zugriffs-Token anzufordern.
1. Wählen Sie die Anfrage **[!UICONTROL Identity Service] > [!UICONTROL Identity-Namespace] > [!UICONTROL Neuen Identity-Namespace erstellen].**
1. Fügen Sie Folgendes als [!DNL Body] der Anfrage ein:

   ```json
   {
       "name": "Luma CRM Id",
       "code": "lumaCrmId",
       "idType": "Cross_device"
   }
   ```

1. Drücken Sie die **Senden**-Taste, und Sie sollten eine **200 OK**-Antwort erhalten:

   ![Identity-Namespace](assets/identity-createUsingApi.png)

Wenn Sie zur Benutzeroberfläche zurückkehren, sollten jetzt Ihre drei neuen benutzerdefinierten Namespaces angezeigt werden:
![Identity-Namespace-](assets/identity-newIdentities.png)


## Kennzeichnen von Identitätsfeldern in Schemata

Nachdem wir nun über unsere Namespaces verfügen, besteht der nächste Schritt darin, unsere Schemata zu aktualisieren, um unsere Identitätsfelder zu kennzeichnen.


### Kennzeichnen von XDM-Feldern für Primäre Identitäten

Für jedes Schema, das mit dem Echtzeit-Kundenprofil verwendet wird, muss eine primäre Identität angegeben werden. Jeder aufgenommene Datensatz muss einen Wert für dieses Feld enthalten.

Fügen wir dem `Luma Loyalty Schema` eine primäre Identität hinzu:

1. `Luma Loyalty Schema` öffnen
1. `Luma Identity profile field group` auswählen
1. `loyaltyId` auswählen
1. Aktivieren Sie das **[!UICONTROL Identität]**.
1. Aktivieren Sie auch das Kontrollkästchen {]**}Primäre Identität**[!UICONTROL 
1. Wählen Sie den `Luma Loyalty Id`-Namespace aus **[!UICONTROL Dropdown-Liste]** Identity-Namespaces“ aus
1. Wählen Sie **[!UICONTROL Übernehmen]**
1. Wählen Sie **[!UICONTROL Speichern]**

   ![Primäre ](assets/identity-loyalty-primary.png)

Wiederholen Sie den Vorgang für einige Ihrer anderen Schemata:

1. Beschriften Sie in der `Luma CRM Schema` das `crmId` Feld mithilfe des `Luma CRM Id` Namespace als primäre Identität
1. Beschriften Sie in der `Luma Offline Purchase Events Schema` das `loyaltyId` Feld mithilfe des `Luma Loyalty Id` Namespace als primäre Identität
1. Beschriften Sie in der `Luma Product Catalog Schema` das `productSku` Feld mithilfe des `Luma Product SKU` Namespace als primäre Identität

>[!NOTE]
>
>Mit Web SDK erfasste Daten bilden eine Ausnahme von der üblichen Praxis der Kennzeichnung von Identitätsfeldern im Schema. Web SDK verwendet die Identitätszuordnung , um Identitäten *implementierungsseitig) zu kennzeichnen* und so bestimmen wir die Identitäten für die `Luma Web Events Schema`, wenn wir Web SDK auf der Luma-Website implementieren. In dieser Lektion erfassen wir die Experience Cloud-Besucher-ID (ECID) als primäre ID und die crmId als sekundäre ID.

Mit unserer Auswahl primärer Identitäten ist klar zu sehen, wie `Luma Loyalty Schema` eine Verbindung zur `Luma Offline Purchase Events Schema` herstellen können, da beide LoyaltyId als Kennung verwenden. Aber wie kann das CRM eine Verbindung zu Offline-Kaufereignissen herstellen? Wie können wir unsere Offline-Käufe mit dem Online-Verhalten verbinden? Und wie können wir die mit unserem Produktkatalog gekauften Produkte einordnen? Wir verwenden zusätzliche Identitätsfelder und Schemabeziehungen.

<!--use a visual-->

### Kennzeichnen von XDM-Feldern für Sekundäre Identitäten

Einem Schema können mehrere Identitätsfelder hinzugefügt werden. Nicht-primäre Identitäten werden oft als sekundäre Identitäten bezeichnet. Um Offline-Käufe mit dem Online-Verhalten zu verbinden, fügen wir die crmId als sekundäre Kennung zu unserem `Luma Loyalty Schema` und später in unseren Web-Ereignisdaten hinzu. Aktualisieren wir die `Luma Loyalty Schema`:

1. `Luma Loyalty Schema` öffnen
1. `Luma Identity Profile Field group` auswählen
1. `crmId` auswählen
1. Aktivieren Sie das **[!UICONTROL Identität]**.
1. Wählen Sie den `Luma CRM Id`-Namespace aus **[!UICONTROL Dropdown-Liste]** Identity-Namespaces“ aus
1. Klicken Sie **[!UICONTROL Übernehmen]** und klicken Sie dann auf die Schaltfläche **[!UICONTROL Speichern]**, um Ihre Änderungen zu speichern

   ![Sekundäre Identität](assets/identity-loyalty-secondaryId.png)

## Vervollständigen der Schemabeziehungen

Nachdem wir nun unsere Identitätsfelder gekennzeichnet haben, können wir die Einrichtung der Schemabeziehungen zwischen dem Produktkatalog von Luma und den Ereignisschemata abschließen:

1. `Luma Offline Purchase Events Schema` öffnen
1. **[!UICONTROL Commerce-Details]**-Feldergruppe auswählen
1. Wählen Sie **[!UICONTROL Feld]** productListItems **[!UICONTROL > SKU]** aus
1. Markieren Sie das **[!UICONTROL Beziehung]**
1. Wählen Sie `Luma Product Catalog Schema` als **[!UICONTROL Referenzschema]**
1. `Luma Product SKU` sollten automatisch als (Referenz **[!UICONTROL Identity-Namespace)]**
1. Wählen Sie **[!UICONTROL Übernehmen]**
1. Wählen Sie **[!UICONTROL Speichern]**

   ![Referenzfeld](assets/identity-offlinePurchase-relationship.png)

Wiederholen Sie diesen Vorgang, um eine Beziehung zwischen dem `Luma Web Events Schema` und dem `Luma Product Catalog Schema` zu erstellen.

Beachten Sie, dass nach der Definition der Beziehung dies sowohl im Abschnitt **[!UICONTROL Komposition]** als auch **[!UICONTROL Struktur]** des Schema-Editors angezeigt wird.

![Beziehungsvisualisierung im Schema-Editor](assets/identity-webEvents-relationship.png)

<!--need to verify that the relationship schema works-->

## Weitere Ressourcen

* [Identity Service-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de)
* [Identity Service-API](https://www.adobe.io/experience-platform-apis/references/identity-service/)

Jetzt, da unsere Identitäten vorhanden sind, können wir [unsere Datensätze erstellen](create-datasets.md)!
