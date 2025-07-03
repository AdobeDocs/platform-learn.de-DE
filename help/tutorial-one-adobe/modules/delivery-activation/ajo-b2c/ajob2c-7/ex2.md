---
title: Offer Decisioning - Konfigurieren von Angeboten und Entscheidungs-ID
description: Offer Decisioning - Konfigurieren von Angeboten und Entscheidungs-ID
kt: 5342
doc-type: tutorial
source-git-commit: 13d790855601fa6f36c1afa0f2d5faad5fc07eb0
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 13%

---

# 3.7.2 Angebote und Entscheidungen konfigurieren

## 3.7.2.1 Personalisierte Angebote erstellen

In dieser Übung erstellen Sie vier **personalisierte Angebote**. Im Folgenden finden Sie die Details, die bei der Erstellung dieser Angebote zu berücksichtigen sind:

| Name | Datumsbereich | Bild-Link für E-Mail | Bildlink für Web | Text | Priorität | Eignung | Sprache | Begrenzungsfrequenz | Bildname |
|-----|------------|----------------------|--------------------|------|:--------:|--------------|:-------:|:-------:|:-------:|
| `--aepUserLdap-- - AirPods Max` | Heute - 1 Monat später | https://bit.ly/4a9RJ5d | Aus Assets Library auswählen | `{{ profile.person.name.firstName }}, 10% discount on AirPods Max` | 25 | Alle - Weibliche Kunden | Englisch (USA) | 3 | Apple AirPods Max - Weiblich.jpg |
| `--aepUserLdap-- - Galaxy S24` | Heute - 1 Monat später | https://bit.ly/3W8yuDv | Aus Assets Library auswählen | `{{ profile.person.name.firstName }}, 5% discount on Galaxy S24` | 15 | Alle - Weibliche Kunden | Englisch (USA) | 3 | Galaxy S24 - Weiblich.jpg |
| `--aepUserLdap-- - Apple Watch` | Heute - 1 Monat später | https://bit.ly/4fGwfxX | https://bit.ly/4fGwfxX | `{{ profile.person.name.firstName }}, 10% discount on Apple Watch` | 25 | Alle - Männliche Kunden | Englisch (USA) | 3 | Apple Watch - Male.jpg |
| `--aepUserLdap-- - Galaxy Watch 7` | Heute - 1 Monat später | https://bit.ly/4gTrkeo | Aus Assets Library auswählen | `{{ profile.person.name.firstName }}, 5% discount on Galaxy Watch 7` | 15 | Alle - Männliche Kunden | Englisch (USA) | 3 | Galaxy Watch7 - Männlich.jpg |

{style="table-layout:auto"}

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## Nächste Schritte

Wechseln Sie zum [3.7.3 Web SDK-Setup für Experience Decisioning](./ex3.md){target="_blank"}

Zurück zu [Experience Decisioning](ajo-decisioning.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
