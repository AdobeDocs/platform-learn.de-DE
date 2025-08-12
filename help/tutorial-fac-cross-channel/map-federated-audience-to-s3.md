---
title: Zuordnen einer Federated Audience zu S3
seo-title: Map a federated audience to S3 | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Zuordnen einer Federated Audience zu S3
description: In dieser Lektion ordnen wir eine Federated Audience einem nachgelagerten Real-Time CDP-Ziel zu, um ein personalisiertes Offline-Erlebnis zu unterstützen.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
hide: true
source-git-commit: b5611dccdba66d31f7dfcd96506e06d1bdd5fb3d
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Verknüpfte Zielgruppe zu S3 zuordnen, um Zielgruppenattribute für die Anreicherung zu nutzen

In dieser Übung erfahren Sie, wie Sie Zielgruppenattribute in Ihrem Data Warehouse nutzen können, um das Erlebnis Ihrer Zielgruppe in nachgelagerten Aktivierungs-Workflows mit RTCDP-Zielen zu bereichern. Für SecurFinancial können diese Federated Attributes verwendet werden, um das Personalisierungserlebnis der Kunden-Zielgruppe offline zu verbessern. In diesem Beispiel ordnen wir die Federated Audience einem vorkonfigurierten Amazon S3-Ziel zu.

## Schritte

1. Navigieren Sie zum **Ziele**-Portal.

2. Klicken Sie auf die **3-Punkt**-Schaltfläche neben dem vorkonfigurierten Amazon S3-Ziel und dann auf **Zielgruppen aktivieren**.

   ![activate-audience](assets/activate-audiences.png)

3. Wählen Sie das **S3-Ziel** aus und klicken Sie dann auf **Weiter**.

   ![select-s3-destination](assets/select-s3-destination.png)

4. Wählen Sie die Zielgruppe **SecureFinancial Customers - Keine Kredite, Gute**.

   ![select-s3-audience](assets/select-s3-audience.png)

5. Lassen Sie im **Planung** alle Standardeinstellungen unverändert und klicken Sie auf **Weiter**.

6. Stellen Sie **Schritt** Zuordnung“ sicher, dass `xdm: personalEmail.address` enthalten ist und als **Deduplizierungsschlüssel)**. Klicken Sie dann auf **Weiter**:

   ![deduplizierungsschlüssel](assets/deduplication-key.png)

7. Im folgenden Zuordnungsschritt können Sie Anreicherungsattribute auswählen, die auf Zielgruppenfeld-Zuordnungen in der Federated-Audience-Komposition basieren. Klicken Sie auf **Stiftsymbol (Bearbeiten**, um die vorab ausgewählten Attribute anzuzeigen.

   ![edit-attributes](assets/edit-attributes.png)

   ![final-attributes](assets/final-attribution.png)

8. Überprüfen Sie Ihre Zielgruppenzuordnung und klicken Sie auf **Beenden**.

Wir sind bereit, mit dem &quot;[ einer Journey&quot; ](build-journey-federated-audience.md).
