---
title: Offer Decisioning - Testen Sie Ihre Entscheidung mit der -API
description: Testen der Entscheidung mithilfe der API
kt: 5342
doc-type: tutorial
exl-id: 52f90b9f-32ea-49c2-af5d-8742ca8b3b4e
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# 3.3.6 Testen Sie Ihre Entscheidung mit der API

## 3.3.6.1 Arbeiten mit der Offer Decisioning-API unter Verwendung von Postman

>[!IMPORTANT]
>
>Wenn Sie ein Adobe-Mitarbeiter sind, befolgen Sie bitte die Anweisungen hier zur Verwendung von [PostBuster](./../../../../modules/getting-started/gettingstarted/ex8.md).

Laden Sie [diese Postman-Sammlung für Offer Decisioning](./../../../../assets/postman/postman_offer-decisioning.zip) auf Ihren Desktop herunter und entpacken Sie sie. Sie erhalten dann Folgendes:

![OD-API](./images/unzip.png)

Sie haben nun diese Datei auf Ihrem Desktop:

- `_AJO- Decisioning Service.postman_collection.json`

In [Übung 2.1.3 - Postman-Authentifizierung für Adobe I/O](./../../../../modules/delivery-activation/rtcdp-b2c/rtcdpb2c-1/ex3.md) haben Sie Postman installiert. Für diese Übung müssen Sie Postman erneut verwenden.

Öffnen Sie Postman und importieren Sie die Datei `_AJO- Decisioning Service.postman_collection.json`. Diese Sammlung ist dann in Postman verfügbar.

![Neue Adobe I/O-Integration](./images/postmanui.png)

Jetzt verfügen Sie über alle Funktionen in Postman, die Sie benötigen, um über APIs mit Adobe Experience Platform zu interagieren.

Bevor Sie die folgenden APIs verwenden können, müssen Sie sich erneut mit der Sammlung **Adobe IO - OAuth authentifizieren,** Sie in Übung 2.1.3 konfiguriert haben.

![Neue Adobe I/O-Integration](./images/postmanui1.png)


### 3.3.6.2 Erhalten von Angeboten für das Kundenprofil

Klicken Sie, um die Anfrage **POST - Angebote für Kundenprofil abrufen** zu öffnen. Das erste, was aktualisiert werden muss, ist die **Header**-Variable für **x-sandbox-name**. Sie sollten sie auf `--aepSandboxName--` setzen.

![OD-API](./images/api23.png)

Für diese Anfrage gibt es eine Reihe von Feldern, die aktualisiert werden müssen. Wechseln Sie zu **Textkörper**.

- **xdm:placementId**
- **xdm:activityId**
- **xdm:id**
- **xdm:itemCount** (Ändern in einen Wert Ihrer Wahl)

![OD-API](./images/api24.png)

Das Feld **xdm:activityId** muss ausgefüllt werden. Sie können dies in der Adobe Experience Platform-Benutzeroberfläche abrufen, wie unten angegeben.

![OD-API](./images/activityid.png)

Das Feld **[!UICONTROL xdm:placementId]** muss ausgefüllt werden. Sie können dies in der Adobe Experience Platform-Benutzeroberfläche abrufen, wie unten angegeben. Im folgenden Beispiel sehen Sie die placementId für die Platzierung **[!UICONTROL Web - Bild]**.

![OD-API](./images/placementid.png)

Geben Sie für das Feld **xdm:id** die E-Mail-Adresse des Kundenprofils ein, für das Sie ein Angebot anfordern möchten. Nachdem alle Werte wie gewünscht festgelegt wurden, klicken Sie auf **[!UICONTROL Senden]**.

![OD-API](./images/api24a.png)

Schließlich sehen Sie das Ergebnis dessen, welche Art von personalisiertem Angebot und welche Assets diesem Kunden angezeigt werden müssen. In diesem Beispiel wurden 2 Elemente angefordert und wie zu sehen ist, wurden 2 personalisierte Angebote zurückgegeben. 1 Angebot für Apple Watch und ein weiteres Angebot für Galaxy Watch 7.

![OD-API](./images/api25.png)

Sie haben jetzt diese Übung abgeschlossen.

## Nächste Schritte

Wechseln Sie zu [Zusammenfassung und Vorteile](./summary.md){target="_blank"}

Zurück zu [Offer Decisioning](offer-decisioning.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
