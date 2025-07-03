---
title: Experience Decisioning - Experience Decisioning 101
description: Experience Decisioning - Experience Decisioning 101
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
source-git-commit: 13d790855601fa6f36c1afa0f2d5faad5fc07eb0
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 1%

---

# 3.7.1 Experience Decisioning 101

## 3.7.1.1 Terminologie

Um Experience Decisioning besser zu verstehen, empfehlen wir Ihnen dringend, die [Übersicht“ über ](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=de) Funktionsweise von Offer Decisioning Application Service mit Adobe Experience Platform zu lesen.

Bei der Arbeit mit Offer Decisioning müssen Sie die folgenden Konzepte verstehen:

| Begriff | Erklärung |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Angebot** | Ein Angebot ist eine Marketing-Nachricht, der ggf. Regeln zugeordnet sind, die angeben, wer sich zum Anzeigen des Angebots eignet. Ein Angebot hat den Status Entwurf, Genehmigt oder Archiviert. |
| **Platzierung** | Die Kombination aus Standort (oder Kanaltyp) und Kontext (oder Inhaltstyp), in dem ein Angebot für einen Endbenutzer angezeigt wird. Im Grunde handelt es sich um eine Kombination aus Text, HTML, Bild, JSON in mobilen, Web-, Social-, Instant Messaging- und nicht digitalen Kanälen. |
| **Regel** | Die Logik, die die Eignung von Endbenutzenden für ein Angebot definiert und steuert. |
| **Personalisiertes Angebot** | Eine anpassbare Marketing-Nachricht, die auf Eignungsregeln und Einschränkungen basiert. |
| **Fallback-Angebot** | Das Standardangebot, das angezeigt wird, wenn ein Endbenutzer für keines der Angebote in der verwendeten Sammlung geeignet ist. |
| **Begrenzung** | Wird in einer Angebotsdefinition verwendet, um festzulegen, wie oft ein Angebot insgesamt und für eine bestimmte Benutzerin oder einen bestimmten Benutzer unterbreitet werden kann. |
| **Priorität** | Ebene, um den Prioritätsrang aus einem Ergebnissatz von Angeboten zu bestimmen. |
| **Sammlung** | Wird zum Filtern einer Untergruppe von Angeboten aus der personalisierten Angebotsliste verwendet, um den Offer-Decisioning-Prozess zu beschleunigen. |
| **Entscheidung** | Eine Kombination aus einer Reihe von Angeboten, Platzierungen und Profilen, für die der Marketer möchte, dass die Entscheidungs-Engine das beste Angebot bereitstellt. |
| **AEM Assets Essentials** | Ein universelles und zentralisiertes Erlebnis zum Speichern, Suchen und Auswählen von Assets in Adobe Experience Cloud-Lösungen und Adobe Experience Platform. |

{style="table-layout:auto"}

## 3.7.1.2 Experience Decisioning

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![exD](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![exD](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

In der nächsten Übung konfigurieren Sie Ihre eigenen Angebote und Entscheidungen.

## Nächste Schritte

Navigieren Sie zu [3.7.2 Konfigurieren Sie Ihre Angebote und Entscheidungen](./ex2.md){target="_blank"}

Zurück zu [Experience Decisioning](ajo-decisioning.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
