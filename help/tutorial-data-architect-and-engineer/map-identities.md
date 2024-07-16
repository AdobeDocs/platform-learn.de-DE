---
title: Zuordnen von Identitäten
seo-title: Map identities | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Zuordnen von Identitäten
description: In dieser Lektion erstellen wir Identitäts-Namespaces und fügen unseren Schemas Identitätsfelder hinzu.
role: Data Architect
feature: Profiles
jira: KT-4348
thumbnail: 4348-map-identities.jpg
exl-id: e17ffabc-049c-42ff-bf0a-8cc31d665dfa
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 6%

---

# Zuordnen von Identitäten

<!-- 30 min-->

In dieser Lektion erstellen wir Identitäts-Namespaces und fügen unseren Schemas Identitätsfelder hinzu. Danach können wir auch die Schemabeziehungen aus der vorherigen Lektion abschließen.

Mit Adobe Experience Platform Identity Service erhalten Sie einen besseren Überblick über Ihre Kunden und deren Verhalten, indem Sie Identitäten zwischen Geräten und Systemen überbrücken und so effektive persönliche digitale Erlebnisse in Echtzeit bereitstellen. Identitätsfelder und Namespaces sind der Kleber, der verschiedene Datenquellen verbindet, um das 360-Grad-Echtzeit-Kundenprofil zu erstellen.

**Datenarchitekten** müssen Identitäten außerhalb dieses Tutorials zuordnen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über die Identität in Adobe Experience Platform zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27841?learn=on)

>[!NOTE]
>
>Identitätsfelder sind nur erforderlich, wenn Sie Echtzeit-Kundenprofile erstellen. Sie sind nicht erforderlich, wenn Sie nur Daten in den Daten-Pool aufnehmen.

<!--explain identity maps-->
<!--explain the strategy behind the identity selection, how these identities will join all the data together-->

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschluss dieser Lektion erforderlich sind.

<!--
* Permission items **[!UICONTROL Identity Management]** > **[!UICONTROL View Identity Namespaces]** and **[!UICONTROL Manage Identity Namespaces]**
* Permission item **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Identity-Namespace erstellen

In dieser Übung erstellen wir Identitäts-Namespaces für die benutzerdefinierten Identitätsfelder von Luma, `loyaltyId`, `crmId` und `productSku`. Identity-Namespaces spielen eine entscheidende Rolle beim Erstellen von Echtzeit-Kundenprofilen, da zwei übereinstimmende Werte im selben Namespace es zwei Datenquellen ermöglichen, ein Identitätsdiagramm zu erstellen.


### Erstellen von Namespaces in der Benutzeroberfläche

Erstellen wir zunächst einen Namespace für das Luma Loyalty-Schema:

1. Navigieren Sie in der Benutzeroberfläche von Platform im linken Navigationsbereich zu **[!UICONTROL Identitäten]** .
1. Sie werden feststellen, dass mehrere vordefinierte Identitäts-Namespaces verfügbar sind. Wählen Sie die Schaltfläche **[!UICONTROL Identitäts-Namespace erstellen]** aus
1. Geben Sie Details wie folgt an

   | Feld | Wert |
   |---------------|-----------|
   | Anzeigename | Luma Loyalty ID |
   | Identitätssymbol | lumaLoyaltyId |
   | Typ | Geräteübergreifend |

1. Wählen Sie **[!UICONTROL Erstellen]**

   ![Erstellen von Namespaces](assets/identity-createNamespace.png)

Richten Sie jetzt einen weiteren Namespace für das Luma Product Catalog-Schema mit den folgenden Details ein:

| Feld | Wert |
|---------------|-----------|
| Anzeigename | Luma Product SKU |
| Identitätssymbol | lumaProductSKU |
| Typ | Nicht personenbezogene Kennung |



## Erstellen eines Identitäts-Namespace mithilfe der API

Wir erstellen unseren CRM-Namespace per API.

>[!NOTE]
>
>Wenn Sie die API-Übungen überspringen möchten, können Sie den CRM-Namespace über die von Ihnen verwendete Benutzeroberflächenmethode mit den folgenden Details erstellen:
>
> 1. Verwenden Sie als **[!UICONTROL Anzeigenamen]** `Luma CRM Id`
> 1. Verwenden Sie als **[!UICONTROL Identitätssymbol]** `lumaCrmId`
> 1. Verwenden Sie als **[!UICONTROL Typ]** geräteübergreifend

Erstellen wir den Identitäts-Namespace `Luma CRM Id`:

1. Laden Sie [Identity Service.postman_collection.json](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Identity%20Service.postman_collection.json) in Ihren `Luma Tutorial Assets` -Ordner herunter
1. Importieren der Sammlung in [!DNL Postman]
1. Wenn Sie kein Zugriffstoken haben, öffnen Sie die Anfrage **[!DNL OAuth: Request Access Token]** und wählen Sie **Senden** aus, um ein neues Zugriffstoken anzufordern.
1. Wählen Sie die Anforderung **[!UICONTROL Identitätsdienst] > [!UICONTROL Identitäts-Namespace] > [!UICONTROL Neuen Identitäts-Namespace erstellen]** aus.
1. Fügen Sie Folgendes als [!DNL Body] der Anforderung ein:

   ```json
   {
       "name": "Luma CRM Id",
       "code": "lumaCrmId",
       "idType": "Cross_device"
   }
   ```

1. Drücken Sie die Schaltfläche **Senden** und Sie sollten eine Antwort vom Typ **200 OK** erhalten:

   ![Identity-Namespace](assets/identity-createUsingApi.png)

Wenn Sie zur Benutzeroberfläche zurückkehren, sollten Ihnen nun die drei neuen benutzerdefinierten Namespaces angezeigt werden:
![Identity-Namespace ](assets/identity-newIdentities.png)


## Identitätsfelder in Schemata beschriften

Nachdem wir nun unsere Namespaces haben, besteht der nächste Schritt darin, unsere Schemas zu aktualisieren, um unsere Identitätsfelder zu kennzeichnen.


### XDM-Felder für Primäre Identität beschriften

Für jedes mit dem Echtzeit-Kundenprofil verwendete Schema muss eine primäre Identität angegeben werden. Und jeder erfasste Datensatz muss einen Wert für dieses Feld haben.

Fügen wir eine primäre Identität zu `Luma Loyalty Schema` hinzu:

1. Öffnen Sie die `Luma Loyalty Schema`
1. Wählen Sie den `Luma Identity profile field group`
1. Wählen Sie das Feld `loyaltyId` aus
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Identität]** .
1. Aktivieren Sie auch das Kontrollkästchen **[!UICONTROL Primär Identity]** .
1. Wählen Sie den Namespace `Luma Loyalty Id` aus dem Dropdown-Menü **[!UICONTROL Identitäts-Namespaces]** aus
1. Wählen Sie **[!UICONTROL Anwenden]** aus.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Primäre Identität ](assets/identity-loyalty-primary.png)

Wiederholen Sie den Vorgang für ein anderes Schema:

1. Benennen Sie in `Luma CRM Schema` das Feld `crmId` mit dem Namespace `Luma CRM Id` als primäre Identität.
1. Benennen Sie in `Luma Offline Purchase Events Schema` das Feld `loyaltyId` mit dem Namespace `Luma Loyalty Id` als primäre Identität.
1. Benennen Sie in `Luma Product Catalog Schema` das Feld `productSku` mit dem Namespace `Luma Product SKU` als primäre Identität.

>[!NOTE]
>
>Mit dem Web SDK erfasste Daten stellen eine Ausnahme von der typischen Praxis dar, Identitätsfelder im Schema zu kennzeichnen. Das Web SDK verwendet die Identity Map, um Identitäten *auf der Implementierungsseite* zu beschriften, und so bestimmen wir die Identitäten für die `Luma Web Events Schema`, wenn wir das Web SDK auf der Luma-Website implementieren. In dieser späteren Lektion erfassen wir die Experience Cloud-Besucher-ID (ECID) als primäre ID und crmId als sekundäre ID.

Mit unserer Auswahl an primären Identitäten können Sie sehen, wie `Luma CRM Schema` eine Verbindung zum `Luma Offline Purchase Events Schema` herstellen kann, da beide `loyaltyId` als Kennung verwenden. Aber wie können wir unsere Offline-Käufe mit dem Online-Verhalten verbinden? Wie können wir die mit unserem Produktkatalog gekauften Produkte klassifizieren? Wir werden zusätzliche Identitätsfelder und Schemabeziehungen verwenden.

<!--use a visual-->

### XDM-Felder für Sekundäre Identität beschriften

Einem Schema können mehrere Identitätsfelder hinzugefügt werden. Nicht-primäre Identitäten werden häufig als sekundäre Identitäten bezeichnet. Um Offline-Käufe mit dem Online-Verhalten zu verbinden, fügen wir die crmId als sekundäre Kennung zu unseren `Luma Loyalty Schema` und später in unseren Web-Ereignisdaten hinzu. Aktualisieren wir die `Luma Loyalty Schema`:

1. Öffnen Sie die `Luma Loyalty Schema`
1. Wählen Sie `Luma Identity Profile Field group`
1. Feld `crmId` auswählen
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Identität]** .
1. Wählen Sie den Namespace `Luma CRM Id` aus dem Dropdown-Menü **[!UICONTROL Identitäts-Namespaces]** aus
1. Wählen Sie **[!UICONTROL Anwenden]** und dann die Schaltfläche **[!UICONTROL Speichern]** aus, um Ihre Änderungen zu speichern

   ![Sekundäre Identität](assets/identity-loyalty-secondaryId.png)

## Abschließen der Schemabeziehungen

Nachdem wir nun unsere Identitätsfelder beschriftet haben, können wir die Einrichtung der Schemabeziehungen zwischen dem Produktkatalog von Luma und den Ereignisschemata abschließen:

1. Öffnen Sie die `Luma Offline Purchase Events Schema`
1. Feldgruppe **[!UICONTROL Commerce-Details]** auswählen
1. Wählen Sie das Feld **[!UICONTROL productListItems]** > **[!UICONTROL SKU]** aus.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Beziehung]** .
1. Wählen Sie `Luma Product Catalog Schema` als **[!UICONTROL Referenzschema]** aus.
1. `Luma Product SKU` sollte automatisch als **[!UICONTROL Referenz-Identitäts-Namespace]** ausgefüllt werden
1. Wählen Sie **[!UICONTROL Anwenden]** aus.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Referenzfeld](assets/identity-offlinePurchase-relationship.png)

Wiederholen Sie diesen Vorgang, um eine Beziehung zwischen dem `Luma Web Events Schema` und dem `Luma Product Catalog Schema` zu erstellen.

Beachten Sie, dass nach dem Definieren der Beziehung diese sowohl im Abschnitt **[!UICONTROL Komposition]** als auch im Abschnitt **[!UICONTROL Struktur]** des Schema-Editors angezeigt wird.

![Visualisierung der Beziehung im Schema-Editor](assets/identity-webEvents-relationship.png)

<!--need to verify that the relationship schema works-->

## Weitere Ressourcen

* [Dokumentation zum Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de)
* [Identity Service-API](https://www.adobe.io/experience-platform-apis/references/identity-service/)

Nachdem unsere Identitäten nun vorhanden sind, können wir [unsere Datensätze erstellen](create-datasets.md)!
