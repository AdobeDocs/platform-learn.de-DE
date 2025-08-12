---
title: Experience Platform-Zielgruppen mit Federated Data anreichern
seo-title: Enrich Experience Platform audiences with federated data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Experience Platform-Zielgruppen mit Federated Data anreichern
description: In dieser Lektion reichern wir eine Experience Platform-Zielgruppe mit Federated Data an.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-enrich-audience-with-federated-data.jpg
hide: true
source-git-commit: b5611dccdba66d31f7dfcd96506e06d1bdd5fb3d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 4%

---


# Experience Platform-Zielgruppen mit Federated Data anreichern

Die Federated Audience-Komposition ermöglicht es Ihnen, bestehende Audiences in Adobe Experience Platform (AEP) anzureichern, indem Sie zusammengestellte Audience-Daten verwenden, die aus dem Enterprise Data Warehouse verbunden wurden. Diese Daten werden nicht in Adobe Experience Platform-Kundenprofilen beibehalten.

## Anreicherung einer föderierten Zielgruppenkomposition

Es gibt zwei primäre Methoden, um eine Federated-Audience-Komposition anzureichern.

### &#x200B;1. Lesen einer AEP-Zielgruppe in einer Federated Composition

In diesem ersten Beispiel verwenden wir die Zielgruppe **SecurFinancial Loan Application Page Visitor**, die im Profil-Service von AEP gespeichert ist, um unsere Verbundzusammensetzung zu starten. Wir werden die Zielgruppe mithilfe von Federated Data in Snowflake anreichern, um die Vorabgenehmigung auf der Grundlage von Kreditwürdigkeit und Darlehensaktivität zu bestimmen.

![federated-zusammensetzung-example](assets/snowflake-preapproval.png)

1. **Zuordnen der AEP**-Zielgruppe zum Ziel „Federated Audience Composition“.
2. **Erstellen Sie Ihre** mit der zugeordneten Zielgruppe als „Zielgruppe lesen“.
3. **Abstimmung der Identitäten** in der gelesenen Zielgruppe, um sie mit Federated Data zu verbinden.

![federated-method-1-1](assets/federated-method-1-1.png)

![federated-method-1-2](assets/federated-method-1-2.png)

### &#x200B;2. Anreichern einer Experience Platform-Zielgruppenregel mit einer Federated Audience

Im zweiten Beispiel verwenden wir die Federated Audience, die mit der Kreditwürdigkeit und der Darlehensaktivität abgefragt wird, um die verhaltensbezogene Zielgruppe der Web-Seitenbesucher des Darlehensantrags anzureichern.

Wenn wir diese Zielgruppe auf der Edge bewerten, können wir die vorab genehmigten Seitenbesucher des Darlehensantrags sofort mit personalisierten Angeboten auf der Website erneut ansprechen.

![edge-audience-enrich](assets/edge-audience-enrich.png)

1. **Speichern und Starten** Ihrer Federated-Audience-Komposition. Sobald die Komposition ausgeführt wurde, wird Ihre verbundene Zielgruppe im Zielgruppen-Portal angezeigt.
2. **Erstellen einer Zielgruppenregel** Verwenden von Profilattributen und Erlebnisereignissen aus dem Profil-Service, einschließlich der verbundenen Zielgruppe.

Lassen Sie uns dies mit einer „Zusammenfassung [ Erkenntnisse und endgültigen Schlussfolgerungen“ ](conclusion.md).
