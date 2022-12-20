---
title: Zuordnen von Identitäten
seo-title: Map identities | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Zuordnen von Identitäten
description: In dieser Lektion erstellen wir Identitäts-Namespaces und fügen unseren Schemas Identitätsfelder hinzu.
role: Data Architect
feature: Profiles
kt: 4348
thumbnail: 4348-map-identities.jpg
exl-id: e17ffabc-049c-42ff-bf0a-8cc31d665dfa
source-git-commit: cf0193e3aae4d6536c868f078f4773ee14e90408
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 4%

---

# Zuordnen von Identitäten

<!-- 30 min-->

In dieser Lektion erstellen wir Identitäts-Namespaces und fügen unseren Schemas Identitätsfelder hinzu. Danach können wir auch die Schemabeziehungen aus der vorherigen Lektion abschließen.

Mit Adobe Experience Platform Identity Service erhalten Sie einen besseren Überblick über Ihre Kunden und deren Verhalten, indem Sie Identitäten zwischen Geräten und Systemen überbrücken und so effektive persönliche digitale Erlebnisse in Echtzeit bereitstellen. Identitätsfelder und Namespaces sind der Kleber, der verschiedene Datenquellen verbindet, um das 360-Grad-Echtzeit-Kundenprofil zu erstellen.

**Datenarchitekten** muss Identitäten außerhalb dieses Tutorials zuordnen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über die Identität in Adobe Experience Platform zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27841?quality=12&learn=on)

>[!NOTE]
>
>Identitätsfelder sind nur erforderlich, wenn Sie Echtzeit-Kundenprofile erstellen. Sie sind nicht erforderlich, wenn Sie nur Daten in den Daten-Pool aufnehmen.

<!--explain identity maps-->
<!--explain the strategy behind the identity selection, how these identities will join all the data together-->

## Erforderliche Berechtigungen

Im [Berechtigungen konfigurieren](configure-permissions.md) Lektion erstellen Sie alle Zugriffssteuerungen, die zum Abschluss dieser Lektion erforderlich sind.

<!--
* Permission items **[!UICONTROL Identity Management]** > **[!UICONTROL View Identity Namespaces]** and **[!UICONTROL Manage Identity Namespaces]**
* Permission item **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Identity-Namespace erstellen

In dieser Übung erstellen wir Identitäts-Namespaces für die benutzerdefinierten Identitätsfelder von Luma, `loyaltyId`, `crmId`und `productSku`. Identitäts-Namespaces spielen eine entscheidende Rolle beim Erstellen von Echtzeit-Kundenprofilen, da zwei übereinstimmende Werte im selben Namespace es zwei Datenquellen ermöglichen, ein Identitätsdiagramm zu erstellen.


### Erstellen von Namespaces in der Benutzeroberfläche

Erstellen wir zunächst einen Namespace für das Luma Loyalty-Schema:

1. Navigieren Sie in der Benutzeroberfläche von Platform zu **[!UICONTROL Identitäten]** in der linken Navigation
1. Sie werden feststellen, dass mehrere vordefinierte Identitäts-Namespaces verfügbar sind. Wählen Sie die **[!UICONTROL Identitäts-Namespace erstellen]** button
1. Geben Sie Details wie folgt an

   | Feld | Wert |
   |---------------|-----------|
   | Anzeigename | Luma Loyalty ID |
   | Identitätssymbol | lumaLoyaltyId |
   | Typ | Geräteübergreifend |

1. Wählen Sie **[!UICONTROL Erstellen]** aus

   ![Erstellen von Namespaces](assets/identity-createNamespace.png)

Richten Sie jetzt einen weiteren Namespace für das Luma Product Catalog-Schema mit den folgenden Details ein:

| Feld | Wert |
|---------------|-----------|
| Anzeigename | Luma Product SKU |
| Identitätssymbol | lumaProductSKU |
| Typ | Personenidentifizierung |



## Erstellen eines Identitäts-Namespace mithilfe der API

Wir erstellen unseren CRM-Namespace per API.

>[!NOTE]
>
>Wenn Sie die API-Übungen überspringen möchten, können Sie den CRM-Namespace über die von Ihnen verwendete Benutzeroberflächenmethode mit den folgenden Details erstellen:
>
> 1. Als **[!UICONTROL Anzeigename]**, verwenden `Luma CRM Id`
> 1. Als **[!UICONTROL Identitätssymbol]**, verwenden `lumaCrmId`
> 1. Als **[!UICONTROL Typ]**, verwenden Sie geräteübergreifend


Erstellen wir den Identity-Namespace `Luma CRM Id`:

1. Download [Identity Service.postman_collection.json](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Identity%20Service.postman_collection.json) auf `Luma Tutorial Assets` Ordner
1. Importieren Sie die Sammlung in [!DNL Postman]
1. Wenn Sie in den letzten 24 Stunden keine Anfrage gestellt haben, sind Ihre Autorisierungstoken wahrscheinlich abgelaufen. Anfrage öffnen **[!DNL Adobe I/O Access Token Generation > Local Signing (Non-production use-only) > IMS: JWT Generate + Auth via User Token]** und wählen Sie **Senden** , um neue JWT- und Zugriffstoken anzufordern.
1. Anforderung auswählen **[!UICONTROL Identity Service] > [!UICONTROL Identitäts-Namespace] > [!UICONTROL Neuen Identitäts-Namespace erstellen].**
1. Fügen Sie Folgendes als [!DNL Body] des Antrags:

   ```json
   {
       "name": "Luma CRM Id",
       "code": "lumaCrmId",
       "idType": "Cross_device"
   }
   ```

1. Drücken Sie die **Senden** und Sie sollten eine **200 OK** Antwort:

   ![Identity-Namespace](assets/identity-createUsingApi.png)

Wenn Sie zur Benutzeroberfläche zurückkehren, sollten Ihnen nun die drei neuen benutzerdefinierten Namespaces angezeigt werden:
![Identitäts-Namespace ](assets/identity-newIdentities.png)


## Identitätsfelder in Schemata beschriften

Nachdem wir nun unsere Namespaces haben, besteht der nächste Schritt darin, unsere Schemas zu aktualisieren, um unsere Identitätsfelder zu kennzeichnen.


### XDM-Felder für Primäre Identität beschriften

Für jedes mit dem Echtzeit-Kundenprofil verwendete Schema muss eine primäre Identität angegeben werden. Und jeder erfasste Datensatz muss einen Wert für dieses Feld haben.

Fügen wir eine primäre Identität zur `Luma Loyalty Schema`:

1. Öffnen Sie die `Luma Loyalty Schema`
1. Wählen Sie die `Luma Identity profile field group`
1. Wählen Sie die `loyaltyId` field
1. Überprüfen Sie die **[!UICONTROL Identität]** box
1. Überprüfen Sie die **[!UICONTROL Primäre Identität]** auch
1. Wählen Sie die `Luma Loyalty Id` Namespace aus **[!UICONTROL Identitäts-Namespaces]** Dropdown
1. Auswählen **[!UICONTROL Anwenden]**
1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Primäre Identität ](assets/identity-loyalty-primary.png)

Wiederholen Sie den Vorgang für ein anderes Schema:

1. Im `Luma CRM Schema`, die Bezeichnung `crmId` als primäre Identität mithilfe der `Luma CRM Id` namespace
1. Im `Luma Offline Purchase Events Schema`, die Bezeichnung `loyaltyId` als primäre Identität mithilfe der `Luma Loyalty Id` namespace
1. Im `Luma Product Catalog Schema`, die Bezeichnung `productSku` als primäre Identität mithilfe der `Luma Product SKU` namespace

>[!NOTE]
>
>Mit dem Web SDK erfasste Daten stellen eine Ausnahme von der typischen Praxis dar, Identitätsfelder im Schema zu kennzeichnen. Web SDK verwendet die Identity Map zur Beschriftung von Identitäten *auf der Implementierungsseite* und so werden wir die Identitäten für die `Luma Web Events Schema` wenn wir das Web SDK auf der Luma-Website implementieren. In dieser späteren Lektion erfassen wir die Experience Cloud-Besucher-ID (ECID) als primäre ID und crmId als sekundäre ID.

Mit unserer Auswahl an primären Identitäten ist es klar zu sehen, wie `Luma CRM Schema` kann eine Verbindung zum `Luma Offline Purchase Events Schema` da beide `loyaltyId` als Kennung. Aber wie können wir unsere Offline-Käufe mit dem Online-Verhalten verbinden? Wie können wir die mit unserem Produktkatalog gekauften Produkte klassifizieren? Wir werden zusätzliche Identitätsfelder und Schemabeziehungen verwenden.

<!--use a visual-->

### XDM-Felder für Sekundäre Identität beschriften

Einem Schema können mehrere Identitätsfelder hinzugefügt werden. Nicht-primäre Identitäten werden häufig als sekundäre Identitäten bezeichnet. Um Offline-Käufe mit dem Online-Verhalten zu verbinden, fügen wir die crmId als sekundäre Kennung zu unserem `Luma Loyalty Schema` und später in unseren Web-Ereignisdaten. Aktualisieren wir die `Luma Loyalty Schema`:

1. Öffnen Sie die `Luma Loyalty Schema`
1. Auswählen `Luma Identity Profile Field group`
1. Auswählen `crmId` field
1. Überprüfen Sie die **[!UICONTROL Identität]** box
1. Wählen Sie die `Luma CRM Id` Namespace aus **[!UICONTROL Identitäts-Namespaces]** Dropdown
1. Auswählen **[!UICONTROL Anwenden]** und wählen Sie dann die **[!UICONTROL Speichern]** Schaltfläche zum Speichern Ihrer Änderungen

   ![Sekundäre Identität](assets/identity-loyalty-secondaryId.png)

## Abschließen der Schemabeziehungen

Nachdem wir nun unsere Identitätsfelder beschriftet haben, können wir die Einrichtung der Schemabeziehungen zwischen dem Produktkatalog von Luma und den Ereignisschemata abschließen:

1. Öffnen Sie die `Luma Offline Purchase Events Schema`
1. Auswählen **[!UICONTROL Commerce-Details]** Feldergruppe
1. Auswählen **[!UICONTROL productListItems]** > **[!UICONTROL SKU]** field
1. Überprüfen Sie die **[!UICONTROL Beziehung]** box
1. Auswählen `Luma Product Catalog Schema` als **[!UICONTROL Referenzschema]**
1. `Luma Product SKU` sollte automatisch mit **[!UICONTROL Referenz-Identitäts-Namespace]**
1. Auswählen **[!UICONTROL Anwenden]**
1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Referenzfeld](assets/identity-offlinePurchase-relationship.png)

Wiederholen Sie diesen Vorgang, um eine Beziehung zwischen dem `Luma Web Events Schema` und `Luma Product Catalog Schema`.

Beachten Sie, dass nach der Definition der Beziehung diese in beiden **[!UICONTROL Komposition]** und **[!UICONTROL Struktur]** Abschnitt des Schema-Editors.

![Beziehungsvisualisierung im Schema-Editor](assets/identity-webEvents-relationship.png)

<!--need to verify that the relationship schema works-->

## Weitere Ressourcen

* [Identitätsdienst-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de)
* [Identity Service-API](https://www.adobe.io/experience-platform-apis/references/identity-service/)

Nachdem unsere Identitäten nun existieren, können wir [Erstellen unserer Datensätze](create-datasets.md)!
