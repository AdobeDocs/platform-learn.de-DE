---
title: Zuordnen einer Federated Audience zu S3
seo-title: Map a federated audience to S3 | Engage with Audiences from your Data Warehouse using Federated Audience Composition
breadcrumb-title: Zuordnen einer Federated Audience zu S3
description: In dieser Übung ordnen wir eine zusammengeführte Zielgruppe einem nachgelagerten Real-Time CDP-Ziel zu, um ein personalisiertes Offline-Erlebnis zu unterstützen.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
exl-id: a47b8f7b-7bd0-43a0-bc58-8b57d331b444
source-git-commit: dd5f594a54a9cab8ef78d36d2cf15a9b5f2b682a
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Verknüpfte Zielgruppe zu S3 zuordnen, um Zielgruppenattribute für die Anreicherung zu nutzen

Sie können Zielgruppenattribute in Ihrem Data Warehouse nutzen, um das Erlebnis Ihrer Zielgruppe in nachgelagerten Aktivierungs-Workflows mit RTCDP-Zielen zu bereichern. Für SecurFinancial können diese Federated Attributes verwendet werden, um das Personalisierungserlebnis der Kunden-Zielgruppe offline zu verbessern. Nachfolgend wird die Federated Audience einem vorkonfigurierten Amazon S3-Ziel zugeordnet.

## Schritte

1. Navigieren Sie zum **Ziele**-Portal.

2. Klicken Sie auf die **3-Punkt**-Schaltfläche neben dem vorkonfigurierten Amazon S3-Ziel und dann auf **Zielgruppen aktivieren**.

   ![activate-audience](assets/activate-audiences.png)

3. Wählen Sie das **S3-Ziel** aus und klicken Sie dann auf **Weiter**.

   ![select-s3-destination](assets/select-s3-destination.png)

4. Wählen Sie die entsprechende Zielgruppe aus. In unserem Beispiel: **SecureFinancial Customers - Keine Kredite, gute**, Zielgruppe.

   ![select-s3-audience](assets/select-s3-audience.png)

5. Verwenden **im Abschnitt** die Standardeinstellungen und klicken Sie auf **Weiter**.

6. Wählen Sie **Schritt** Zuordnung“ den Deduplizierungsschlüssel aus. In unserem Beispiel wird `xdm: personalEmail.address` als **Deduplizierungsschlüssel“**. Klicken Sie dann auf **Weiter**:

   ![deduplizierungsschlüssel](assets/deduplication-key.png)

7. Wählen Sie im Zuordnungsschritt Anreicherungsattribute basierend auf Zielgruppenfeld-Zuordnungen in der Federated-Audience-Komposition aus. Klicken Sie auf **Stiftsymbol (Bearbeiten**, um die vorab ausgewählten Attribute anzuzeigen.

   ![edit-attributes](assets/edit-attributes.png)

   ![final-attributes](assets/final-attribution.png)

8. Überprüfen Sie Ihre Zielgruppenzuordnung und klicken Sie auf **Beenden**.

>[**!SUMMARY**]
>
> Wir haben erfolgreich eine Zielgruppe erstellt und sie mit Leichtigkeit für ein S3-Ziel aktiviert. Die benutzerfreundliche Oberfläche ermöglicht es Marketing-Teams, Zielgruppen schnell zu erstellen und zu aktivieren, ohne die zugrunde liegenden Daten zu verschieben.

Jetzt bauen wir [eine Journey](build-journey-federated-audience.md).
