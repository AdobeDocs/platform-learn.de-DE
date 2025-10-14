---
title: Zielgruppen mit Warehouse-Daten anreichern
seo-title: Enrich Audiences with warehouse data | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Zielgruppen mit Warehouse-Daten anreichern
description: In dieser Übung wird eine Experience Platform-Zielgruppe mit Warehouse-Daten angereichert.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-enrich-audience-with-federated-data.jpg
exl-id: 3f6aa121-0dbd-4ad9-b136-d1455eed03ca
source-git-commit: 7e2f7bbb392eba51c0d6b9ccc8224c2081a01c7c
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 7%

---

# Zielgruppen mit Warehouse-Daten anreichern

Die Federated Audience-Komposition ermöglicht es Ihnen, bestehende Audiences in Adobe Experience Platform (AEP) anzureichern, indem Sie zusammengestellte Audience-Daten verwenden, die aus dem Enterprise Data Warehouse verbunden wurden. Diese Daten werden nicht in Adobe Experience Platform-Kundenprofilen beibehalten.

## Lesen einer Audience in einer Federated Composition

In dieser Übung verwenden wir die Zielgruppe **SecurFinancial Loan Application Page Visitor**, die im Profil-Service von Experience Platform gespeichert ist, um unsere Verbundzusammensetzung zu starten. Sie verwendet die Federated Data in Snowflake, um die Vorabgenehmigung auf der Grundlage von Kreditwürdigkeit und Darlehensaktivität zu bestimmen.

![federated-zusammensetzung-example](assets/snowflake-preapproval.png)

### Schritte

1. **Zuordnen der AEP**-Zielgruppe zum Ziel „Federated Audience Composition“.
2. **Erstellen Sie Ihre** mit der zugeordneten Zielgruppe als „Zielgruppe lesen“.
3. **Abstimmung der Identitäten** in der gelesenen Zielgruppe, um sie mit Federated Data zu verbinden.

![federated-method-1-1](assets/federated-method-1-1.png)

![federated-method-1-2](assets/federated-method-1-2.png)

Wir werden uns ein weiteres Beispiel für die Verwendung von Federated Data ansehen[&#x200B; um eine „In-the-Moment“-Personalisierung bereitzustellen](deliver-in-the-moment-personalization.md)!
