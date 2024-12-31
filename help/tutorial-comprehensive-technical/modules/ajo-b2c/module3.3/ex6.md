---
title: Offer decisioning - Testen Sie Ihre Entscheidung mithilfe der API.
description: Testen der Entscheidung mithilfe der API
kt: 5342
doc-type: tutorial
exl-id: 75515a3e-5df8-42ed-95dc-daae60ee9c72
source-git-commit: 348554b5a2d43d7a882e8259b39a57af13d41ff4
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 1%

---

# 3.3.6 Testen Sie Ihre Entscheidung mit der API

## 3.3.6.1 Arbeiten mit der Offer decisioning-API unter Verwendung von Postman

Laden Sie [diese Postman-Sammlung zum Offer decisioning](./../../../assets/postman/postman_offer-decisioning.zip) auf Ihren Desktop herunter und entpacken Sie sie. Sie erhalten dann Folgendes:

![OD-API](./images/unzip.png)

Sie haben nun diese Datei auf Ihrem Desktop:

- [!UICONTROL _Module 14- Decisioning Service.postman_collection.json]

In [Übung 2.1.3 - Postman-Authentifizierung auf Adobe I/O ](./../../../modules/rtcdp-b2c/module2.1/ex3.md) Sie Postman installiert. Für diese Übung müssen Sie Postman erneut verwenden.

Öffnen Sie Postman. Klicken Sie **[!UICONTROL Importieren]**.

![Neue Integration Adobe I/O](./images/postmanui.png)

Klicken Sie auf **[!UICONTROL Dateien]**.

![Neue Integration Adobe I/O](./images/pm1.png)

Wählen Sie die Datei **[!UICONTROL _Module 14- Decisioning Service.postman_collection.json]** klicken Sie auf **[!UICONTROL Öffnen]**.

![Neue Integration Adobe I/O](./images/pm2.png)

Diese Sammlung ist dann in Postman verfügbar.

![Neue Integration Adobe I/O](./images/pm3.png)

Jetzt verfügen Sie über alle Funktionen in Postman, die Sie benötigen, um über APIs mit Adobe Experience Platform zu interagieren.

### 3.3.6.1.1 Listencontainer

Klicken, um Anfrage **[!UICONTROL GET - Container auflisten]** zu öffnen.

Unter **[!UICONTROL Params]** wird Folgendes angezeigt:

- Eigenschaft: `_instance.parentName==aepenablementfy22`

In diesem Parameter **[!UICONTROL aepenablementfy22]** der Name der in Adobe Experience Platform verwendeten Sandbox. Die zu verwendende Sandbox ist `--aepSandboxName--`. Ersetzen Sie den Text **[!UICONTROL aepenablementfy22]** durch `--aepSandboxName--`.

Nachdem Sie den Sandbox-Namen ersetzt haben, klicken Sie auf **[!UICONTROL Senden]**.

![OD-API](./images/api2.png)

Dies ist die Antwort, die den Angebotscontainer für die angegebene Sandbox anzeigt. Kopieren Sie die **[!UICONTROL container-instanceId]** wie unten angegeben und schreiben Sie sie in einer Textdatei auf Ihrem Computer auf. Sie müssen diese **[!UICONTROL Container-Instanz-ID]** für die nächste Übung verwenden!

![OD-API](./images/api3.png)

### 3.3.6.1.2 Platzierungen auflisten

Klicken Sie, um die Anfrage **[!UICONTROL GET - Platzierungen auflisten]** öffnen. Klicken Sie auf **[!UICONTROL Senden]**.

![OD-API](./images/api4.png)

Sie sehen jetzt alle verfügbaren Platzierungen in Ihrem Angebotscontainer. Die Platzierungen, die Sie sehen, wurden in der Benutzeroberfläche von Adobe Experience Platform definiert, wie Sie in [3.3.1.3](./ex1.md) sehen konnten.

![OD-API](./images/api5.png)

### 3.3.6.1.3 Entscheidungsregeln auflisten

Klicken Sie, um die Anfrage **[!UICONTROL GET - Entscheidungsregeln auflisten zu]**. Klicken Sie auf **[!UICONTROL Senden]**.

![OD-API](./images/api6.png)

In der Antwort werden die Entscheidungsregeln angezeigt, die Sie in der Adobe Experience Platform-Benutzeroberfläche definiert haben, wie Sie in [3.3.1.4](./ex1.md) sehen konnten.

![OD-API](./images/api7.png)

### 3.3.6.1.4 Personalisierte Angebote auflisten

Klicken Sie, um die Anfrage **[!UICONTROL GET - Personalisierte Angebote auflisten]** öffnen. Klicken Sie auf **[!UICONTROL Senden]**.

![OD-API](./images/api8.png)

In der Antwort werden die personalisierten Angebote angezeigt, die Sie in der Adobe Experience Platform-Benutzeroberfläche unter [3.3.2.1](./ex2.md) definiert haben.

![OD-API](./images/api9.png)

### 3.3.6.1.5 Fallback-Angebote auflisten

Klicken, um Anfrage **[!UICONTROL GET - Fallback-Angebote auflisten]** zu öffnen. Klicken Sie auf **[!UICONTROL Senden]**.

![OD-API](./images/api10.png)

In der Antwort wird das Fallback-Angebot angezeigt, das Sie in der Adobe Experience Platform-Benutzeroberfläche in [3.3.2.2](./ex2.md) definiert haben.

![OD-API](./images/api11.png)

### 3.3.6.1.6 Auflisten von Sammlungen

Klicken, um Anfrage **[!UICONTROL GET - Sammlungen auflisten]** zu öffnen.

![OD-API](./images/api12.png)

In der Antwort wird die Sammlung angezeigt, die Sie in der Adobe Experience Platform-Benutzeroberfläche in &quot;[&quot; 3.3.2.3](./ex2.md).

![OD-API](./images/api13.png)

### 3.3.6.1.7 Detaillierte Angebote für Kundenprofil

Klicken Sie, um die Anfrage **[!UICONTROL POST - Detaillierte Angebote für Kundenprofil abrufen zu]**. Diese Anfrage ähnelt der vorherigen, gibt jedoch Details wie Bild-URLs, Text usw. zurück.

![OD-API](./images/api23.png)

Für diese Anfrage müssen Sie, ähnlich wie in der vorherigen Übung, die ähnliche Anforderungen hat, die Werte für **[!UICONTROL xdm:placementId]** und **[!UICONTROL xdm:activityId]** angeben, um die spezifischen Angebotsdetails für einen Kunden abzurufen.

Das Feld **[!UICONTROL xdm:activityId]** muss ausgefüllt werden. Sie können dies in der Adobe Experience Platform-Benutzeroberfläche abrufen, wie unten angegeben.

![OD-API](./images/activityid.png)

Das Feld **[!UICONTROL xdm:placementId]** muss ausgefüllt werden. Sie können dies in der Adobe Experience Platform-Benutzeroberfläche abrufen, wie unten angegeben. Im folgenden Beispiel sehen Sie die placementId für die Platzierung **[!UICONTROL Web - Bild]**.

![OD-API](./images/placementid.png)

Wechseln Sie **[!UICONTROL Textkörper]** und geben Sie die E-Mail-Adresse des Kunden ein, für den Sie ein Angebot anfordern möchten. Klicken Sie auf **[!UICONTROL Senden]**.

![OD-API](./images/api24.png)

Schließlich sehen Sie das Ergebnis dessen, welche Art von personalisiertem Angebot und welche Assets diesem Kunden angezeigt werden müssen.

![OD-API](./images/api25.png)

Sie haben jetzt diese Übung abgeschlossen.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zum Modul 3.3](./offer-decisioning.md)

[Zurück zu „Alle Module“](./../../../overview.md)
