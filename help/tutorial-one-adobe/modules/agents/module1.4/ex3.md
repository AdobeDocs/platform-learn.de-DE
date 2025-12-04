---
title: Implementieren von Brand Concierge mithilfe von Datenerfassungs-Tags
description: Implementieren von Brand Concierge mithilfe von Datenerfassungs-Tags
kt: 5342
doc-type: tutorial
source-git-commit: 3704abb57e9fa64c2ff6d6914b6da8b46a5f44aa
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 6%

---

# 1.4.3 Implementieren von Brand Concierge mithilfe von Datenerfassungs-Tags

>[!IMPORTANT]
>
>An dieser Übung wird gearbeitet und sie ist noch nicht abgeschlossen.

## Datenerfassungs-Tags-Eigenschaft

Brand Concierge muss Daten an Adobe Experience Platform senden. Dazu muss Web SDK (oder alloy.js) auf Ihrer Website bereitgestellt werden.

Um dies zu ermöglichen, müssen Sie jetzt eine Datenerfassungs-Tags-Eigenschaft erstellen.

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Öffnen Sie **Datenerfassung**.

![Brand Concierge](./images/aep101.png)

Klicken Sie auf **Neue Eigenschaft**.

![Brand Concierge](./images/aep102.png)

Geben Sie den Namen `--aepUserLdap-- - CitiSignal Website + Brand Concierge` und auch die Domain Ihrer Website ein.

Klicken Sie auf **Speichern**.

![Brand Concierge](./images/aep103.png)

Suchen Sie nach Ihrer Eigenschaft und öffnen Sie sie dann.

![Brand Concierge](./images/aep104.png)

Navigieren Sie zu **Erweiterungen** und dann zu **Katalog**.

![Brand Concierge](./images/aep105.png)

Suchen Sie nach `web sdk` und klicken Sie dann auf die Erweiterung **Adobe Experience Platform Web SDK**. Klicken Sie auf **Installieren**.

![Brand Concierge](./images/aep106.png)

Sie sollten das dann sehen. Die Details für Ihren Datenstrom müssen Sie hier nur angeben. Scrollen Sie dazu ein wenig nach unten.

![Brand Concierge](./images/aep107.png)

Wählen Sie für alle drei Umgebungen **Produktion**, **Staging** und **Entwicklung** Folgendes aus:

- **Sandbox**: `--aepUserLdap-- - bc`
- **Datenstrom**: `--aepUserLdap-- - Brand Concierge`

Klicken Sie **Speichern**.

![Brand Concierge](./images/aep108.png)

Sie sollten das dann sehen. Navigieren Sie zu **Regeln**.

![Brand Concierge](./images/aep108a.png)

Klicken Sie auf **Neue Regel erstellen**.

![Brand Concierge](./images/aep109.png)

Geben Sie den Namen ein: `Homepage`. Klicken Sie dann auf **+ Hinzufügen** unter **EREIGNISSE**.

![Brand Concierge](./images/aep110.png)

Wählen Sie die folgenden Optionen aus:

- **Erweiterung**: **Core**
- **Ereignistyp**: **Bibliothek geladen (Seitenanfang)**

Klicken Sie auf **Änderungen beibehalten**.

![Brand Concierge](./images/aep111.png)

Sie sollten das dann sehen. Klicken Sie auf **+ Hinzufügen** unter **BEDINGUNGEN**.

![Brand Concierge](./images/aep112.png)

Wählen Sie die folgenden Optionen aus:

- **Logiktyp**: **normal**
- **Erweiterung**: **Core**
- **Bedingungstyp**: **Pfad ohne Abfragezeichenfolge**
- **Pfad ist gleich …**: Geben Sie Ihre Website-Domain ein, in diesem Fall `https://vangeluw.adobedemosystem.com/`

Klicken Sie auf **Änderungen beibehalten**.

![Brand Concierge](./images/aep113.png)

Sie sollten das dann sehen. Klicken Sie auf **+ Hinzufügen** unter **AKTIONEN**.

![Brand Concierge](./images/aep114.png)

Wählen Sie die folgenden Optionen aus:

- **Erweiterung**: **Core**
- **Aktionstyp**: **Benutzerdefinierter Code**
- **language**: **JavaScript**

Klicken Sie **Editor öffnen**.

![Brand Concierge](./images/aep115.png)

Fügen Sie den folgenden Code ein:

```javascript
window["alloy"]("sendEvent", {
        conversation: {fetchConversationalExperience: true}
    }).then(result=> {
        console.log("Conversation experience fetched", result);
        window["alloy"]("bootstrapConversationalExperience", {
            selector: "#brand-concierge-mount",
						// src: "main.js",
            src: "https://experience-stage.adobe.net/solutions/experience-platform-brand-concierge-web-agent/static-assets/main.js",
            stylingConfigurations: window.styleConfiguration,
						stickySession: true
        })
    });
```

Klicken Sie auf **Speichern**.

![Brand Concierge](./images/aep116.png)

Sie sollten das dann sehen. Klicken Sie auf **Änderungen beibehalten**.

![Brand Concierge](./images/aep117.png)

Sie sollten das dann sehen. Klicken Sie auf **Speichern**.

![Brand Concierge](./images/aep118.png)

Navigieren Sie **Veröffentlichungsfluss**. Klicken Sie **Bibliothek hinzufügen**.

![Brand Concierge](./images/aep119.png)

Geben Sie den Namen ein: `Dev`, wählen Sie **Entwicklung (Entwicklung)** für die Umgebung aus und klicken Sie dann auf **Alle geänderten Ressourcen hinzufügen**.

Klicken Sie auf **Speichern und Build zur Entwicklung erstellen**.

![Brand Concierge](./images/aep120.png)

Nach einigen Minuten wird Ihre Bibliothek erstellt. Warten Sie, bis der **grüne Punkt** neben &quot;**&quot;**. Navigieren Sie dann zu **Umgebungen**.

![Brand Concierge](./images/aep121.png)

Klicken Sie auf das **Installieren**-Symbol für die Umgebung **Entwicklung**.

![Brand Concierge](./images/aep122.png)

Sie sollten das dann sehen. Klicken Sie auf **Kopieren**, um den Pfad Ihrer Bibliothek zu kopieren. Sie müssen dies auf Ihrer Website implementieren.

Der Bibliothekspfad sollte wie folgt aussehen:
`<script src="https://assets.adobedtm.com/XXXXXXX/XXXXXXXX/launch-XXXXXXXXX-development.min.js" async></script>`

![Brand Concierge](./images/aep123.png)

Zurück zu [Brand Concierge](./brandconcierge.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}