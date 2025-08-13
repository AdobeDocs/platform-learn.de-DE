---
title: Experience Platform-Zielgruppen mit Federated Data anreichern
seo-title: Enrich Experience Platform audiences with federated data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Experience Platform-Zielgruppen mit Federated Data anreichern
description: In dieser visuellen Übung wird eine Experience Platform-Zielgruppe mit Federated Data angereichert.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-enrich-audience-with-federated-data.jpg
exl-id: 3f6aa121-0dbd-4ad9-b136-d1455eed03ca
source-git-commit: 3de9721332379f9fd3dd45768ba2ca2308e09357
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 7%

---

# Experience Platform-Zielgruppen mit Federated Data anreichern

Die Federated Audience-Komposition ermöglicht es Ihnen, bestehende Audiences in Adobe Experience Platform (AEP) anzureichern, indem Sie zusammengestellte Audience-Daten verwenden, die aus dem Enterprise Data Warehouse verbunden wurden. Diese Daten werden nicht in Adobe Experience Platform-Kundenprofilen beibehalten.

## Lesen einer AEP-Zielgruppe in einer Federated Composition

In dieser visuellen Übung verwenden wir die Zielgruppe **SecurFinancial Loan Application Page Visitor**, die im Profil-Service von AEP gespeichert ist, um unsere Verbundzusammensetzung zu starten. Sie verwendet die Federated Data in Snowflake, um die Vorabgenehmigung auf der Grundlage von Kreditwürdigkeit und Darlehensaktivität zu bestimmen.

![federated-zusammensetzung-example](assets/snowflake-preapproval.png)

### Schritte

1. **Zuordnen der AEP**-Zielgruppe zum Ziel „Federated Audience Composition“.
2. **Erstellen Sie Ihre** mit der zugeordneten Zielgruppe als „Zielgruppe lesen“.
3. **Abstimmung der Identitäten** in der gelesenen Zielgruppe, um sie mit Federated Data zu verbinden.

![federated-method-1-1](assets/federated-method-1-1.png)

![federated-method-1-2](assets/federated-method-1-2.png)

Wir werden uns ein weiteres Beispiel für die Verwendung von Federated Data ansehen[ um eine „In-the-Moment“-Personalisierung zu ](drive-in-the-moment-personalization.md)!
