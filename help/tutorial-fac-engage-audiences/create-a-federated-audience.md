---
title: Erstellen einer Federated Audience
seo-title: Create a federated audience | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Erstellen einer Federated Audience
description: In dieser Übung erstellen wir eine Zielgruppe aus dem Snowflake Data Warehouse mithilfe der Federated Audience Composition.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
exl-id: a507cab5-dba9-4bf7-a043-d7c967e9e07d
source-git-commit: 41298ea7c79a5b540c546be93dcb14201ce27ce3
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---

# Erstellen einer Federated Audience

Als Nächstes führen wir Sie durch die Erstellung einer Zielgruppe aus dem Snowflake Data Warehouse mithilfe der Federated Audience-Komposition. Die Zielgruppe besteht aus SecurFinancial-Kunden, die eine Kreditwürdigkeit von 650 oder höher haben und derzeit keinen Kredit in ihrem SecurFinancial-Portfolio haben.

## Schritte

1. Klicken Sie **Portal „Kunde** > Zielgruppen“ auf die Registerkarte **Verknüpfte Kompositionen**.
2. Klicken Sie **Komposition erstellen**.

   ![create-zusammensetzung](assets/create-composition.png)

3. Beschriften Sie Ihre Komposition. In unserem Beispiel: `SecurFinancial Customers - No Loans, Good Credit`. Klicken Sie auf **Erstellen**.

4. Klicken Sie auf die Schaltfläche **+** auf der Arbeitsfläche und wählen Sie **Zielgruppe erstellen**. Die rechte Leiste wird angezeigt.

5. Klicken Sie **Schema auswählen** wählen Sie das entsprechende Schema aus und klicken Sie dann auf **Bestätigen**.

6. Klicken Sie auf **Fortfahren**. Klicken Sie im Fenster Query Builder auf die Schaltfläche **+** und dann auf **Benutzerdefinierte Bedingung**. Schreiben Sie die Bedingungen. In unserem Beispiel wird Folgendes verwendet:

   `CURRENTPRODUCTS does not contain loan`
   `AND`
   `CREDITSCORE greater than or equal to 650`
   `AND`
   `CONSENTSMARKETINGPREFERRED equal to email`

   *Die letzte Bedingung stellt sicher, dass Daten zu Marketing-Voreinstellungen verwendet werden, um Kunden zu segmentieren, die sich für E-Mail als bevorzugten Kommunikationskanal entschieden haben*.

   **Hinweis:** Beim Wertfeld wird zwischen Groß- und Kleinschreibung unterschieden.

   ![Query-Builder](assets/query-builder.png)

7. Klicken Sie auf die Schaltfläche **+** und dann auf **Audience speichern**. Beschriften Sie diesen Schritt. In unserem Beispiel beschriften wir sie mit `SecurFinancial Customers - No Loans, Good Credit`.

8. Fügen Sie die entsprechenden Zielgruppenzuordnungen hinzu. In diesem Beispiel:

   - **Source-Zielgruppenfeld:** EMAIL
   - **Source-Zielgruppenfeld:** CURRENTPRODUCTS
   - **Source-Zielgruppenfeld:** VORNAME

9. Wählen Sie die primäre Identität und den Namespace aus, die für Profile verwendet werden sollen. Dies sind die Identitäten und Felder, die für unsere Daten verwendet werden:

   - **Primäres Identitätsfeld:** Email
   - **Identity-Namespace:** E-Mail

10. Klicken Sie **Speichern** und anschließend auf **Starten**, um die Abfrage der Komposition auszuführen.

### ZUSAMMENFASSUNG

In diesem Beispiel wurden Produkt- und Bonitätsinformationen verwendet, um unsere Zielgruppe durch direkten Zugriff auf Unternehmensdaten aus Snowflake aufzubauen, ohne eine Kopie davon aus Adobe Experience Platform zu erstellen. Sobald das externe System die Abfrage verarbeitet, werden nur die relevanten E-Mail-, aktuellen Produkt- und Vornamenwerte zur nachgelagerten Aktivierung an die Zielgruppendefinition übergeben. Dies gilt für alle von RTCDP unterstützten Ziele.

Weitere Informationen zur Komposition von Audiences finden Sie unter [Experience League](https://experienceleague.adobe.com/de/docs/federated-audience-composition/using/compositions/create-composition/create-composition){target="_blank"}.

Nachdem wir nun unsere Federated Audience erstellt haben, [ wir sie einem S3-Ziel in Experience Platform ](map-federated-audience-to-s3.md).
