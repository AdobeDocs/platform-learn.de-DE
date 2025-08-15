---
title: Bereitstellen von Personalisierung „im Moment“ mit Edge Network
seo-title: Deliver "in-the moment" personalization using Edge Network | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Bereitstellen von Personalisierung „im Moment“ mit Edge Network
description: In dieser Übung wird die verbundene Zielgruppe auf der Edge für das sofortige Retargeting „im Moment“ ausgewertet.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-drive-in-the-moment-personalization.jpg
exl-id: 20bfafb1-1d1b-48d8-84eb-97d4c9e03b76
source-git-commit: 93b787112134919444150974c7149dc10c2d0ca6
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# Bereitstellen von Personalisierung „im Moment“ mit Edge Network

Die Federated Audience-Komposition ermöglicht es Ihnen, bestehende Audiences in Adobe Experience Platform (AEP) anzureichern, indem Sie zusammengestellte Audience-Daten verwenden, die aus dem Enterprise Data Warehouse verbunden wurden. Diese Daten werden nicht in Adobe Experience Platform gespeichert, aber Sie können die Funktionen [Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/overview){target="_blank"} verwenden, um diese Daten direkt an Ihr Data Warehouse zu senden.

In dieser Übung verwenden wir eine verbundene Zielgruppe, die mit der Kreditwürdigkeit und der Darlehensaktivität abgefragt wird, um die verhaltensbezogene Zielgruppe der Web-Seitenbesucher des Darlehensantrags anzureichern.

Durch die Auswertung dieser Zielgruppe auf der Edge sprechen wir die zuvor genehmigten Kreditantragsseiten-Besucher sofort mit personalisierten Angeboten auf der Website erneut an.

![edge-audience-enrich](assets/edge-audience-enrich.png)

## Schritte

1. **Speichern und Starten** Ihrer Federated-Audience-Komposition. Sobald die Komposition ausgeführt wurde, wird die verbundene Zielgruppe im Zielgruppen-Portal angezeigt.
2. **Erstellen einer Zielgruppenregel** Verwenden von Profilattributen und Erlebnisereignissen aus dem Profil-Service, einschließlich der verbundenen Zielgruppe.

Lassen Sie uns dies mit einer „Zusammenfassung [ Erkenntnisse und endgültigen Schlussfolgerungen“ ](conclusion.md).
