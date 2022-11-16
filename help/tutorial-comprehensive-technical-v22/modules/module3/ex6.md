---
title: Anzeigen Ihres Echtzeit-Kundenprofils in Aktion im Callcenter
description: Anzeigen Ihres Echtzeit-Kundenprofils in Aktion im Callcenter
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 457347ca-1ce5-4699-bd30-735abdc7b450
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 4%

---

# 3.6 Echtzeit-Kundenprofil in Aktion im Callcenter anzeigen

In dieser Übung ist es das Ziel, Sie durch die Journey zu führen und wie ein echter Kunde zu handeln.

Auf dieser Website haben wir Adobe Experience Platform implementiert. Jede Aktion wird als Erlebnisereignis betrachtet und in Echtzeit an Adobe Experience Platform gesendet, wodurch das Echtzeit-Kundenprofil verbessert wird.

In einer früheren Übung haben Sie als anonymer Kunde begonnen, der die Site besuchte, und nach einigen Schritten wurden Sie zu einem bekannten Kunden.

Wenn derselbe Kunde schließlich sein Telefon abruft und Ihr Callcenter anruft, ist es wichtig, dass die Informationen aus anderen Kanälen sofort verfügbar sind, damit das Callcenter-Erlebnis relevant und personalisiert werden kann.

## 3.6.1 Verwenden der CX-App

Im Rahmen unseres Demo-Systems haben wir eine CX-App-Vorlage erstellt, die zur Simulation einer Callcenter-Umgebung verwendet werden kann. Führen Sie diese Schritte aus, um ein solches CX-App-Projekt zu erstellen.

Navigieren Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Klicken **Neues Projekt**.

Anschließend sehen Sie Ihr CX-App-Projekt. Klicken Sie auf das Projekt, um es zu öffnen.

![Demo](./images/cxapp3.png)

Wechseln Sie in Ihrem CX-App-Projekt zu **Integrationen**. Wählen Sie die Adobe Experience Platform-Datenerfassungseigenschaft aus, die in Modul 0 erstellt wurde. Sie müssen die Eigenschaft auswählen, die **(Aktivierung)** im Namen. Klicken Sie dann auf **Ausführen**.

![Demo](./images/cxapp4.png)

Dann wirst du das sehen.

![Demo](./images/cxapp5.png)

Im Bedienfeld &quot;Profil-Viewer&quot;können Sie die folgenden Kombinationen von IDs und Namespaces sehen:

![Kundenprofil](./images/identities.png)

| Identität | Namespace |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID) | 12507560687324495704459439363261812234 |
| Email ID | woutervangeluwe+06022022-01@gmail.com |
| Mobiltelefonnummer | +32473622044+06022022-01 |

Wenn der Kunde Ihr Callcenter anruft, kann die Telefonnummer zur Identifizierung des Kunden verwendet werden. In dieser Übung verwenden Sie also die Telefonnummer, um das Kundenprofil in der CX-App abzurufen.

Auswählen **Telefonnummer** in das Dropdown-Menü ein und geben Sie die Telefonnummer ein, die Sie auf der Website verwendet haben. Treffer **Eingabe**.

![Demo](./images/19.png)

Sie sehen nun die Informationen, die idealerweise im Callcenter angezeigt werden würden, sodass die Angestellten des Call-Centers alle relevanten Informationen sofort beim Kontakt mit einem Kunden zur Verfügung haben.

![Demo](./images/20.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 3](./real-time-customer-profile.md)

[Zu allen Modulen zurückkehren](../../overview.md)
