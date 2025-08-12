---
title: Data Warehouse-Verbindung
seo-title: Configure a Data Warehouse connection | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Data Warehouse-Verbindung
description: In dieser Lektion konfigurieren wir eine Verbindung zwischen Adobe Experience Platform und Ihrer Unternehmens-Data Warehouse, um die Federated Audience Composition zu aktivieren.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-configure-a-data-warehouse-connection.jpg
hide: true
source-git-commit: fcfadca95c12d0123cfb221e44909f7e0fa8abab
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 2%

---


# Data Warehouse-Verbindung

In dieser Lektion konfigurieren wir eine Verbindung zwischen Adobe Experience Platform und Ihrer Unternehmens-Data Warehouse, um die Federated Audience Composition zu aktivieren. Auf diese Weise können Sie Daten ohne Replikation direkt aus unterstützten Warehouses abfragen. Zusätzlich erstellen wir Schemata und Datenmodelle basierend auf den Data Warehouse-Tabellen.

Für dieses Labor verbinden wir uns mit einem Snowflake-Konto. Die Federated Audience-Komposition unterstützt eine wachsende Liste von Cloud-Warehouse-Verbindungen. Siehe die [aktualisierte Liste der Integrationen](https://experienceleague.adobe.com/de/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"}.


## Schritte

1. Navigieren Sie zum Abschnitt **FEDERATED DATA** in der linken Leiste.
2. Klicken Sie **Link „Federated**&quot; auf die Schaltfläche **Federated Database hinzufügen**.
3. Fügen Sie einen Namen hinzu und wählen Sie **Snowflake**.
4. Füllen Sie die Details aus, klicken Sie auf die Schaltfläche **Verbindung testen** und dann auf die Schaltfläche **Funktionen bereitstellen**.

   ![snowflake-connection-setup](assets/snowflake-connection-setup.png)

   ![snowflake-connection-setup-step2](assets/snowflake-connection-setup-step2.png)

   ![snowflake-connection-setup-step3](assets/snowflake-connection-setup-step3.png)

## Schema erstellen

Gehen Sie wie folgt vor, um Schemas in Federated Audience Composition zu erstellen:

1. Klicken Sie **Abschnitt „FEDERATED DATA** auf **Modelle**.
2. Durchsuchen Sie die **Schema** und klicken Sie auf die Schaltfläche **Schema erstellen**.
3. Wählen Sie Ihre Quelldatenbank in der Liste aus und klicken Sie auf die Registerkarte **Tabellen hinzufügen**.
4. Folgende Tabellen auswählen:
   - FSI_CRM
   - FSI_CRM_CONSENT_PREFERENCE

   ![create-schema](assets/create-schema.png)

   ![select-table](assets/select-table.png)

Überprüfen Sie nach Auswahl der Tabellen die Spalten der einzelnen Tabellen und wählen Sie Ihren Primärschlüssel aus. Für diese Übung wählen wir **E-MAIL** als Primärschlüssel in beiden Tabellen aus.

![create-schema](assets/create-schema.png)

![create-schema-step2](assets/create-schema-step2.png)

## Vorschau von Daten in einem Schema

Um eine Vorschau der Daten in der Tabelle anzuzeigen, die durch Ihr Schema dargestellt wird, navigieren Sie zur Registerkarte **Daten** .

Klicken Sie auf den **Berechnen**, um eine Vorschau der Gesamtzahl der Datensätze anzuzeigen.

![preview-data-in-schema](assets/preview-data-in-schema.png)

## Erstellen eines Datenmodells

Mit Datenmodellen können Sie eine Relation zwischen Tabellen erstellen. Die Relation kann zwischen Tabellen in derselben Datenbank (z. B. in Snowflake) oder zwischen Tabellen in verschiedenen Datenbanken (z. B. zwischen einer Tabelle in Snowflake und einer Tabelle in Amazon Redshift) erstellt werden.

Gehen Sie wie folgt vor, um ein Datenmodell in Federated Audience Composition zu erstellen:

1. Klicken Sie im **FEDERATED DATA**-Abschnitt auf **Modelle** und anschließend auf **Datenmodell**.
2. Klicken Sie auf **Schaltfläche „Datenmodell erstellen**.
3. Geben Sie einen Namen für Ihr Datenmodell an.
4. Klicken Sie auf **Schemata hinzufügen** und wählen Sie **FSI_CRM** und **FSI_CRM_CONSENT_PREFERENCE** Schemata aus.
5. Erstellen Sie eine Verknüpfung zwischen diesen Tabellen, indem Sie auf **Verknüpfungen erstellen** klicken.

Wählen Sie beim Erstellen eines Links die entsprechende Kardinalität:

- **1-N**: Eine Entität in der Quelltabelle kann mit mehreren Entitäten in der Zieltabelle in Beziehung stehen, aber eine Entität in der Zieltabelle kann nur maximal mit einer Entität in der Quelltabelle in Beziehung stehen.
- **N-1**: Eine Entität in der Zieltabelle kann mit mehreren Entitäten in der Quelltabelle in Beziehung stehen, aber eine Entität in der Quelltabelle kann mit höchstens einer Entität in der Zieltabelle in Beziehung stehen.
- **1-1**: Eine Entität in der Quelltabelle kann maximal mit einer Entität in der Zieltabelle in Beziehung stehen.

Im Folgenden finden Sie eine Vorschau des Links, der für die Laborübungen erstellt wurde. Die Relation ermöglicht eine Verknüpfung zwischen der CRM- und der Einverständnistabelle unter Verwendung des Primärschlüssels **E-Mail**, um eine Verknüpfung durchzuführen.

![preview-data-model](assets/preview-data-model.png)

Jetzt sind wir bereit, &quot;[ und Zielgruppe“ ](audience-creation-exercise.md).
