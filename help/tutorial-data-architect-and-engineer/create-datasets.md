---
title: Erstellen von Datensätzen
seo-title: Create datasets | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Erstellen von Datensätzen
description: In dieser Lektion erstellen Sie Datensätze, die Ihre Daten empfangen.
role: Data Architect, Data Engineer
feature: Data Management
jira: KT-4348
thumbnail: 4348-create-datasets.jpg
exl-id: 80227af7-4976-4fd2-b1d4-b26bc4626fa0
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 9%

---

# Erstellen von Datensätzen

<!--15min-->

In dieser Lektion erstellen Sie Datensätze, die Ihre Daten empfangen. Sie werden begeistert davon sein, dass dies die kürzeste Lektion im Tutorial ist!

Alle Daten, die erfolgreich in Adobe Experience Platform aufgenommen wurden, werden im Data Lake als Datensätze persistiert. Ein Datensatz ist ein Konstrukt zur Datenspeicherung und -verwaltung, in dem Daten (in der Regel) in einer Tabelle erfasst werden, die ein Schema (Spalten) und Felder (Zeilen) beinhaltet. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

**Datenarchitekten** müssen außerhalb dieses Tutorials Datensätze erstellen.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über Datensätze zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27269?learn=on)

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschluss dieser Lektion erforderlich sind.

<!--
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Erstellen von Datensätzen in der Benutzeroberfläche

In dieser Übung erstellen wir Datensätze in der Benutzeroberfläche. Beginnen wir mit den Treuedaten:

1. Navigieren Sie im linken Navigationsbereich der Platform-Benutzeroberfläche zu **[!UICONTROL Datensätze]** .
1. Wählen Sie die Schaltfläche **[!UICONTROL Datensatz erstellen]** aus
   ![Erstellen eines Datensatzes](assets/datasets-createDataset.png)

1. Wählen Sie im nächsten Bildschirm **Datensatz aus Schema erstellen** aus
1. Wählen Sie im nächsten Bildschirm Ihren `Luma Loyalty Schema` und dann die Schaltfläche **[!UICONTROL Weiter]** aus
   ![Wählen Sie den Datensatz aus](assets/datasets-selectSchema.png)

1. Benennen Sie den Datensatz mit `Luma Loyalty Dataset` und wählen Sie die Schaltfläche **[!UICONTROL Beenden]** aus.
   ![Benennen Sie den Datensatz](assets/datasets-nameDataset.png)
1. Wenn der Datensatz gespeichert wurde, gelangen Sie zu einem Bildschirm wie diesem:
   ![Datensatz erstellt](assets/datasets-created.png)

Das ist alles! Ich habe dir ja gesagt, dass das schnell sein wird. Erstellen Sie diese anderen Datensätze wie folgt:

1. `Luma Offline Purchase Events Dataset` für Ihre `Luma Offline Purchase Events Schema`
1. `Luma Web Events Dataset` für Ihre `Luma Web Events Schema`
1. `Luma Product Catalog Dataset` für Ihre `Luma Product Catalog Schema`


## Datensatz mit API erstellen

Erstellen Sie nun die `Luma CRM Dataset` mithilfe der API.

>[!NOTE]
>
>Wenn Sie die API-Übung überspringen und die `Luma CRM Dataset` in der Benutzeroberfläche erstellen möchten, ist dies in Ordnung. Benennen Sie ihn mit &quot;`Luma CRM Dataset`&quot;und verwenden Sie &quot;`Luma CRM Schema`&quot;.

### Abrufen der ID des Schemas, das im Datensatz verwendet werden soll

Zunächst müssen wir die `$id` des `Luma CRM Schema` abrufen:

1. Öffnen Sie [!DNL Postman]
1. Wenn Sie kein Zugriffstoken haben, öffnen Sie die Anfrage &quot;**[!DNL OAuth: Request Access Token]**&quot; und wählen Sie &quot;**Senden**&quot;, um ein neues Zugriffstoken anzufordern, wie Sie es in der [!DNL Postman]-Lektion getan haben.
1. Öffnen Sie die Anforderung **[!DNL Schema Registry API > Schemas > Retrieve a list of schemas within the specified container.]**
1. Wählen Sie die Schaltfläche **Senden** aus
1. Sie sollten eine 200-Antwort erhalten
1. Suchen Sie in der Antwort nach dem Element `Luma CRM Schema` und kopieren Sie den Wert `$id` .
   ![Kopieren Sie die $id](assets/dataset-crm-getSchemaId.png)

### Datensatz erstellen

Jetzt können Sie den Datensatz erstellen:

1. Laden Sie [Catalog Service API.postman_collection.json](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Catalog%20Service%20API.postman_collection.json) in Ihren Ordner `Luma Tutorial Assets` herunter.
1. Importieren der Sammlung in [!DNL Postman]
1. Wählen Sie die Anforderung **[!DNL Catalog Service API > Datasets > Create a new dataset.]** aus
1. Fügen Sie Folgendes als **Hauptteil** der Anforderung ein, ***ersetzt den ID-Wert durch Ihren eigenen***:

   ```json
   {
       "name": "Luma CRM Dataset",
   
       "schemaRef": {
           "id": "REPLACE_WITH_YOUR_OWN_ID",
           "contentType": "application/vnd.adobe.xed-full+json;version=1"
       },
       "fileDescription": {
           "persisted": true,
           "containerFormat": "parquet",
           "format": "parquet"
       }
   }
   ```

1. Wählen Sie die Schaltfläche **Senden** aus
1. Sie sollten eine 201 Erstellte Antwort mit der ID Ihres neuen Datensatzes erhalten!
   ![Datensatz, der mit der API erstellt wurde, Ihre benutzerdefinierte $id, die im Hauptteil verwendet wird](assets/datasets-crm-created.png)

>[!TIP]
>
> Häufige Probleme, die diese Anfrage verursachen, und mögliche Fehlerbehebungen:
>
> * `400: There was a problem retrieving xdm schema`. Stellen Sie sicher, dass Sie die ID im obigen Beispiel durch die ID Ihres eigenen `Luma CRM Schema` ersetzt haben.
> * No auth token: Führen Sie die Anfrage **OAuth: Request Access Token** aus, um ein neues Token zu generieren
> * `401: Not Authorized to PUT/POST/PATCH/DELETE for this path : /global/schemas/`: Aktualisieren Sie die Umgebungsvariable **CONTAINER_ID** von `global` auf `tenant`
> * `403: PALM Access Denied. POST access is denied for this resource from access control`: Überprüfen Sie Ihre Benutzerberechtigungen in der Admin Console


Sie können in der Benutzeroberfläche von Platform zum Bildschirm **[!UICONTROL Datensätze]** zurückkehren. Sie können die erfolgreiche Erstellung aller fünf Datensätze überprüfen.
![Fünf Datensätze abgeschlossen](assets/datasets-allComplete.png)


## Weitere Ressourcen

* [Datensatzdokumentation](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=de)
* Referenz für die [Datensatz-API (Teil des Catalog Service)](https://www.adobe.io/experience-platform-apis/references/catalog/#tag/Datasets)

Nachdem nun alle unsere Schemas, Identitäten und Datensätze vorhanden sind, können wir [sie für das Echtzeit-Kundenprofil aktivieren](enable-profiles.md).
