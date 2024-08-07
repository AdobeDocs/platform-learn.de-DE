---
title: Echtzeit-Kundenprofile aktivieren
seo-title: Enable Real-Time Customer Profiles | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Echtzeit-Kundenprofile aktivieren
description: In dieser Lektion aktivieren Sie Ihre Schemas und Datensätze für das Echtzeit-Kundenprofil.
role: Data Architect
feature: Profiles
jira: KT-4348
thumbnail: 4348-enable-profiles.jpg
exl-id: b05f1af1-a599-42f2-8546-77453a578b92
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 2%

---

# Echtzeit-Kundenprofile aktivieren

<!-- 15min-->
In dieser Lektion aktivieren Sie Ihre Schemas und Datensätze für das Echtzeit-Kundenprofil.

Okay, ich habe gelogen, als ich sagte, dass die Lektion zu Datensätzen die kürzeste Lektion in diesem Tutorial war - diese sollte noch weniger Zeit in Anspruch nehmen! Alles, was du tun wirst, ist ein Haufen Umschalter zu werfen. Aber was passiert, wenn Sie diese Umschalter drehen, ist _wirklich_ wichtig, also wollte ich ihm eine ganze Seite widmen.

Mit dem Echtzeit-Kundenprofil können Sie eine ganzheitliche Ansicht jedes einzelnen Kunden anzeigen, die Daten aus mehreren Kanälen kombiniert, einschließlich Online-, Offline-, CRM- und Drittanbieter-Daten. Mit dem Profil können Sie Ihre unterschiedlichen Kundendaten in einer zentralen Sicht zusammenführen, die eine aussagekräftige, im Zeitverlauf gezeichnete Darstellung jeder Kundeninteraktion bietet.

So erstaunlich das alles auch klingt, Sie müssen nicht *all Ihre Daten* für das Profil aktivieren. Tatsächlich sollten Sie nur die Daten aktivieren, die Sie für Aktivierungs-Anwendungsfälle benötigen. Aktivieren Sie Daten, die Sie für Marketing-Anwendungsfälle, Callcenter-Integrationen usw. verwenden möchten, wo Sie schnellen Zugriff auf ein robustes Kundenprofil benötigen. Wenn Sie Daten nur zur Analyse hochladen, sollte sie wahrscheinlich nicht für das Profil aktiviert werden.

Es gibt wichtige [Limits für Echtzeit-Kundenprofil-Daten](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en), die Sie bei der Entscheidung darüber überprüfen sollten, welche Ihrer eigenen Daten Sie für das Profil aktivieren sollten.

<!--is this accurate. Are there other considerations to point out? -->

**Datenarchitekten** müssen das Echtzeit-Kundenprofil außerhalb dieses Tutorials aktivieren.

Bevor Sie mit den Übungen beginnen, sehen Sie sich dieses kurze Video an, um mehr über das Echtzeit-Kundenprofil zu erfahren:
>[!VIDEO](https://video.tv.adobe.com/v/27251?learn=on)

## Erforderliche Berechtigungen

In der Lektion [Berechtigungen konfigurieren](configure-permissions.md) richten Sie alle Zugriffssteuerungen ein, die zum Abschluss dieser Lektion erforderlich sind.


<!--* Permission items **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Aktivieren von Schemata für das Echtzeit-Kundenprofil über die Benutzeroberfläche von Platform

Beginnen wir mit der einfachen Aufgabe, ein Schema zu aktivieren:

1. Öffnen Sie in der Platform-Benutzeroberfläche das **Luma Loyalty-Schema**
1. In **[!UICONTROL Schemaeigenschaften]** können Sie den Schalter **Profil** umschalten
1. Klicken Sie im Bestätigungsmodal auf die Schaltfläche **[!UICONTROL Aktivieren]** , um zu bestätigen
1. Wählen Sie die Schaltfläche **[!UICONTROL Speichern]** aus, um Ihre Änderungen zu speichern

   >[!IMPORTANT]
   >
   >Nachdem ein Schema für Profil aktiviert wurde, kann es nicht mehr deaktiviert oder gelöscht werden. Außerdem können Felder nach diesem Punkt nicht mehr aus dem Schema entfernt werden. Diese Implikationen sollten Sie später bei der Arbeit mit Ihren eigenen Daten in Ihrer Produktionsumgebung berücksichtigen. Sie sollten in diesem Tutorial eine Entwicklungs-Sandbox verwenden, die jederzeit gelöscht werden kann.
   >
   >In der kontrollierten Umgebung dieses Tutorials aktivieren Sie Ihre Schemas und Datensätze für das Profil, _vor der Aufnahme von Daten_. Wir empfehlen, beim Arbeiten mit Ihren eigenen Daten die folgenden Schritte auszuführen:
   >
   > 1. Erfassen Sie zunächst einige Daten in Ihren Datensätzen.
   > 1. Beheben Sie alle Probleme, die während des Datenerfassungsprozesses auftreten (z. B. bei der Datenvalidierung oder bei der Zuordnung).
   > 1. Datensätze und Schemata für Profile aktivieren
   > 1. Daten erneut verwenden


   ![Profil-Umschalter](assets/profile-loyalty-enableSchema.png)

Einfach richtig? Wiederholen Sie die obigen Schritte für dieses andere Schema:

1. Luma-Produktkatalog-Schema
1. Luma-Offline-Kaufereignisschema
1. Luma Web Events Schema (aktivieren Sie im Bestätigungs-Modal das Kontrollkästchen &quot;Daten für dieses Schema enthalten eine primäre Identität im Feld identityMap .&quot;)

## Aktivieren von Schemata für das Echtzeit-Kundenprofil mithilfe der Platform-API

Jetzt ist es an der Zeit, die `Luma CRM Schema` mit der API zu aktivieren. Wenn Sie diese Übung überspringen und sie einfach in der Benutzeroberfläche aktivieren möchten, fahren Sie sofort fort.

### Abrufen der meta:altId des Schemas

Zunächst rufen wir die `meta:altId` des `Luma CRM Schema` ab:

1. Öffnen Sie [!DNL Postman]
1. Wenn Sie kein Zugriffstoken haben, öffnen Sie die Anfrage &quot;**[!DNL OAuth: Request Access Token]**&quot; und wählen Sie &quot;**Senden**&quot;, um ein neues Zugriffstoken anzufordern, wie Sie es in der [!DNL Postman]-Lektion getan haben.
1. Öffnen Sie die Anforderung **[!DNL Schema Registry API > Schemas > Retrieve a list of schemas within the specified container.]**
1. Wählen Sie die Schaltfläche **Senden** aus
1. Sie sollten eine 200-Antwort erhalten
1. Suchen Sie in der Antwort nach dem Element `Luma CRM Schema` und kopieren Sie den Wert `meta:altId` .
   ![Kopieren Sie die meta:altIid](assets/profile-crm-getMetaAltId.png)

### Aktivieren des Schemas

Nachdem wir nun über die meta:altId des Schemas verfügen, können wir sie für das Profil aktivieren:

1. Öffnen Sie die Anforderung **[!DNL Schema Registry API > Schemas > Update one or more attributes of a custom schema specified by ID.]**
1. Fügen Sie in den **Parameter** Ihren `meta:altId` -Wert als `SCHEMA_ID`-Parameterwert ein.
1. Fügen Sie auf der Registerkarte **Hauptteil** den folgenden Code ein

   ```json
   [{
       "op": "add",
       "path": "/meta:immutableTags",
       "value": ["union"]
   }]
   ```

1. Wählen Sie die Schaltfläche **Senden** aus
1. Sie sollten eine 200-Antwort erhalten

   ![Aktivieren Sie das CRM-Schema für das Profil mit Ihrer benutzerdefinierten meta:altIid, die als Parameter &quot;SCHEMA_ID&quot;verwendet wird](assets/profile-crm-enableProfile.png)

Sie sollten in der Benutzeroberfläche sehen können, dass alle fünf Schemas für Profil aktiviert sind (möglicherweise müssen Sie UMSCHALT-Neu laden, um zu sehen, dass `Luma CRM Schema` aktiviert ist):
![Alle Schemas aktiviert](assets/profile-allSchemasEnabled.png)


## Aktivieren von Datensätzen für Echtzeit-Kundenprofil über die Benutzeroberfläche von Platform

Die Datensätze müssen auch für Profil aktiviert werden, und der Prozess ist noch einfacher:

1. Öffnen Sie in der Benutzeroberfläche von Platform den `Luma Loyalty Dataset`
1. Wechsel zum Schalter **[!UICONTROL Profil]**
1. Klicken Sie im Bestätigungsmodal auf die Schaltfläche **[!UICONTROL Aktivieren]** , um zu bestätigen

   ![ Profil-Umschalter](assets/profile-loyalty-enableDataset.png)

Wiederholen Sie die obigen Schritte für diese anderen Datensätze:

1. Luma-Produktkatalog-Datensatz
1. Datensatz mit Offline-Kaufereignissen für Luma
1. Datensatz mit Luma-Webereignissen

>[!NOTE]
>
>Im Gegensatz zu Schemas können Sie Datensätze aus dem Profil deaktivieren, jedoch bleiben alle zuvor erfassten Daten im Profil.

## Datensätze für Echtzeit-Kundenprofil mithilfe der Platform-API aktivieren

Jetzt aktivieren Sie einen Datensatz für Profil mithilfe der API. Auch wenn Sie es über die Benutzeroberfläche mit der oben genannten Methode aktivieren möchten, ist das in Ordnung.

### ID des Datensatzes abrufen

Zunächst müssen wir die `id` des `Luma CRM Dataset` abrufen:

1. Öffnen Sie [!DNL Postman]
1. Wenn Sie kein Zugriffstoken haben, öffnen Sie die Anfrage &quot;**[!DNL OAuth: Request Access Token]**&quot; und wählen Sie &quot;**Senden**&quot;, um ein neues Zugriffstoken anzufordern, wie Sie es in der [!DNL Postman]-Lektion getan haben.
1. Öffnen Sie die Anforderung **[!DNL Catalog Service API > Datasets > Retrieve a list of datasets.]**
1. Wählen Sie die Schaltfläche **Senden** aus
1. Sie sollten eine 200-Antwort erhalten
1. Suchen Sie in der Antwort nach dem Element `Luma CRM Dataset` und kopieren Sie die ID:
   ![Kopieren Sie die ID](assets/profile-crm-copyDatasetId.png)

### Aktivieren des Datensatzes

Nachdem wir nun die ID des Datensatzes haben, können wir ihn für das Profil aktivieren:

1. Öffnen Sie die Anforderung **[!DNL Catalog Service API > Datasets > Update one or more attributes of a dataset specified by ID.]**
1. Aktualisieren Sie in den **Parameter** den Wert `DATASET_ID` auf Ihren eigenen
1. Fügen Sie auf der Registerkarte **Hauptteil** den folgenden Code ein. Beachten Sie, dass es sich bei den ersten beiden Werten um bereits vorhandene Tags handelt, die in der vorherigen Antwort sichtbar sind. Sie müssen zusätzlich zu den beiden neuen Tags, die wir hinzufügen, im Text enthalten sein:

   ```json
   {
       "tags":{
           "adobe/pqs/table":["luma_crm_dataset"],
           "adobe/siphon/table/format":["parquet"],
           "unifiedProfile":["enabled:true"],
           "unifiedIdentity":["enabled:true"]
           }
   }
   ```

1. Wählen Sie die Schaltfläche **Senden** aus
1. Sie sollten eine 200-Antwort erhalten

   ![Aktivieren Sie den CRM-Datensatz für das Profil und stellen Sie sicher, dass Sie Ihre benutzerdefinierte Datensatz-ID als Parameter &quot;DATASET_ID&quot;verwenden.](assets/profile-crm-enableDataset.png)

Sie können auch bestätigen, dass in der Benutzeroberfläche der Datensatz aktiviert angezeigt wird:
![Bestätigen](assets/profile-crm-confirmEnabled.png)

>[!IMPORTANT]
>
> Wenn Sie Daten erfassen, bevor Sie das Schema und den Datensatz für das Profil aktivieren, müssen Sie diese Daten anschließend erneut erfassen.

## Weitere Ressourcen

* [Dokumentation zum Echtzeit-Kundenprofil](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=de)
* [Referenz zur Echtzeit-Kundenprofil-API](https://www.adobe.io/experience-platform-apis/references/profile/)


**Dateningenieure** sollten die Lektion [Abonnieren von Datenerfassungsereignissen](subscribe-to-data-ingestion-events.md) fortsetzen.
**Datenarchitekten** _können_ überspringen und zur [Batch-Erfassungsstunde](ingest-batch-data.md) wechseln.
