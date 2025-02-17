---
title: Erleben Sie Ihr Echtzeit-Kundenprofil in Aktion im Callcenter
description: Erleben Sie Ihr Echtzeit-Kundenprofil in Aktion im Callcenter
kt: 5342
doc-type: tutorial
exl-id: d3bd34a1-5577-4da7-a5a5-0f186b1a73c2
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 3%

---

# 2.1.5 Sehen Sie Ihr Echtzeit-Kundenprofil in Aktion im Callcenter

In dieser Übung besteht das Ziel darin, dass Sie die Kunden-Journey durchlaufen und sich wie ein echter Kunde verhalten.

Auf dieser Website haben wir Adobe Experience Platform implementiert. Jede Aktion wird als Erlebnisereignis betrachtet und in Echtzeit an Adobe Experience Platform gesendet, wodurch das Echtzeit-Kundenprofil hydriert wird.

In einer früheren Übung haben Sie als anonymer Kunde begonnen, der die Site durchsuchte, und nach einigen Schritten wurden Sie zu einem bekannten Kunden.

Wenn derselbe Kunde schließlich sein Telefon abnimmt und sein Callcenter anruft, ist es wichtig, dass die Informationen aus anderen Kanälen sofort verfügbar sind, damit das Callcenter-Erlebnis relevant und personalisiert sein kann.

## CX-App verwenden

Navigieren Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf die 3 Punkte **…** in Ihrem CX App-Projekt und klicken Sie dann auf **Bearbeiten**, um es zu öffnen.

![Demo](./images/cxapp3.png)

Navigieren Sie in Ihrem CX-App-Projekt zu **Integrationen**. Klicken Sie **Umgebung auswählen**.

![Demo](./images/cxapp3a.png)

Wählen Sie die Datenerfassungseigenschaft von Adobe Experience Platform aus, die in Erste Schritte erstellt wurde. Sie müssen die Eigenschaft auswählen, die **(cx-app)** im Namen enthält.

![Demo](./images/cxapp4.png)

Sie werden es dann sehen. Klicken Sie auf **Ausführen**.

![Demo](./images/cxapp4a.png)

Als Nächstes müssen Sie eine Ihrer Identitäten und den entsprechenden Namespace auswählen und auf das **Suchsymbol** klicken.

![Kundenprofil](./images/identities.png)

| Identität | Namespace |
|:-------------:| :---------------:|
| Experience Cloud-ID (ECID) | 79943948563923140522865572770524243489 |
| Experience Cloud-ID (ECID) | 70559351147248820114888181867542007989 |
| E-Mail-ID | woutervangeluwe+18112024-01@gmail.com |
| Mobiltelefonnummer-ID | +32473622044+18112024-01 |

![Demo](./images/19.png)

Sie sehen nun die Informationen, die idealerweise im Callcenter angezeigt werden, sodass die Callcenter-Agenten alle relevanten Informationen sofort bei einem Gespräch mit einem Kunden zur Verfügung haben.

![Demo](./images/20.png)

## Nächste Schritte

Wechseln Sie zu [Zusammenfassung und Vorteile](./summary.md){target="_blank"}

Zurück zum [Echtzeit-Kundenprofil](./real-time-customer-profile.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
