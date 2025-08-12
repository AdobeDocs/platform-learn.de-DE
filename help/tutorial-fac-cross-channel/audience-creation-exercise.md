---
title: Erstellen einer Zielgruppe
seo-title: Create an audience | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Erstellen einer Zielgruppe
description: In dieser Lektion konfigurieren wir eine Verbindung zwischen Adobe Experience Platform und Ihrer Unternehmens-Data Warehouse, um die Federated Audience Composition zu aktivieren.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
hide: true
source-git-commit: b5611dccdba66d31f7dfcd96506e06d1bdd5fb3d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---


# Übung zur Zielgruppenerstellung

Diese Übung führt Sie durch die Erstellung einer Zielgruppe aus Ihrer Data Warehouse mithilfe der Federated-Audience-Komposition. Wir erstellen eine Zielgruppe, um SecurFinancial-Kunden zu qualifizieren, die eine Kreditwürdigkeit von 650 oder höher haben und derzeit kein Darlehen in ihrem SecurFinancial-Portfolio haben.

## Schritte

1. Klicken Sie **Portal „Kunde** > Zielgruppen“ auf die Registerkarte **Verknüpfte Kompositionen**.
2. Klicken Sie **Komposition erstellen**.

   ![create-zusammensetzung](assets/create-composition.png)

3. Beschriften Sie Ihre Komposition als `SecurFinancial Customers - No Loans, Good Credit`. Klicken Sie auf **Erstellen**.

4. Klicken Sie auf die Schaltfläche **+** auf der Arbeitsfläche und wählen Sie **Zielgruppe erstellen**. Die rechte Leiste sollte angezeigt werden.

5. Klicken Sie **Schema auswählen** und wählen Sie das Schema **FSI_CRM** aus und klicken Sie dann auf **Bestätigen**.

6. Klicken Sie auf **Fortfahren**. Klicken Sie im Fenster Query Builder auf die Schaltfläche **+** und dann auf **Benutzerdefinierte Bedingung**. Erstellen Sie die folgenden Bedingungen:

   `CURRENTPRODUCTS does not contain loan`
   `AND`
   `CREDITSCORE greater than or equal to 650`
   `AND`
   `CONSENTSMARKETINGPREFERRED equal to email`

   *Die letzte Bedingung stellt sicher, dass Daten zu Marketing-Voreinstellungen verwendet werden, um Kunden zu segmentieren, die sich für E-Mail als bevorzugten Kommunikationskanal entschieden haben*.

   **Hinweis:** Beim Wertfeld wird zwischen Groß- und Kleinschreibung unterschieden.

   Ihre Abfrage sollte nun wie folgt aussehen:

   ![Query-Builder](assets/query-builder.png)

7. Klicken Sie auf die Schaltfläche **+** und dann auf **Audience speichern**. Kennzeichnen Sie diesen Schritt als `SecurFinancial Customers - No Loans, Good Credit`. Verwenden Sie denselben Wert wie für die Zielgruppen-Kennzeichnung.

8. Fügen Sie die folgenden Zielgruppenzuordnungen hinzu:

   - **Source-Zielgruppenfeld:** EMAIL
   - **Source-Zielgruppenfeld:** CURRENTPRODUCTS
   - **Source-Zielgruppenfeld:** VORNAME

9. Wählen Sie die primäre Identität und den Namespace aus, die für Profile verwendet werden sollen:

   - **Primäres Identitätsfeld:** Email
   - **Identity-Namespace:** E-Mail

10. Klicken Sie auf **Speichern** und dann auf **Starten**, um die Abfrage der soeben erstellten Komposition auszuführen.

**Hinweis:** Wir haben Produkt- und Kreditinformationen verwendet, um unsere Zielgruppe zu erstellen, die keine sensiblen Daten wie z. B. die Kreditwürdigkeit zur Aktivierung auf nachgelagerte Plattformen verschoben hat.

Weitere Informationen zur Komposition von Audiences finden Sie unter [Experience League](https://experienceleague.adobe.com/de/docs/federated-audience-composition/using/compositions/create-composition/create-composition){target="_blank"}.

Nachdem wir nun unsere Federated Audience erstellt haben, fahren wir mit dem [Zuordnen zu einem S3-Konto](map-federated-audience-to-s3.md) fort.
