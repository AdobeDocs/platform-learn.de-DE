---
title: Offer decisioning - Testen Sie Ihre Entscheidung mithilfe der API.
description: Testen Ihrer Entscheidung mithilfe der API
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 1%

---

# 3.3.6 Entscheidung mithilfe der API testen

## 3.3.6.1 Arbeiten mit der Offer decisioning-API unter Verwendung von Postman

Laden Sie [diese Postman-Sammlung für Offer decisioning](./../../../assets/postman/postman_offer-decisioning.zip) auf Ihren Desktop herunter und dekomprimieren Sie sie. Dann haben Sie Folgendes:

![OD API](./images/unzip.png)

Sie haben diese Datei jetzt auf Ihrem Desktop:

- [!UICONTROL _Modul 14 - Decisioning Service.postman_collection.json]

In [Übung 2.1.3 - Postman-Authentifizierung für Adobe I/O](./../../../modules/rtcdp-b2c/module2.1/ex3.md) haben Sie Postman installiert. Sie müssen Postman erneut für diese Übung verwenden.

Öffnen Sie Postman. Klicken Sie auf **[!UICONTROL Importieren]**.

![Adobe I/O Neue Integration](./images/postmanui.png)

Klicken Sie auf **[!UICONTROL Dateien hochladen]**.

![Adobe I/O Neue Integration](./images/pm1.png)

Wählen Sie die Datei **[!UICONTROL _Module 14- Decisioning Service.postman_collection.json]** aus und klicken Sie auf **[!UICONTROL Open]**.

![Adobe I/O Neue Integration](./images/pm2.png)

Diese Sammlung ist dann in Postman verfügbar.

![Adobe I/O Neue Integration](./images/pm3.png)

Sie haben jetzt alles, was Sie in Postman benötigen, um über die APIs mit Adobe Experience Platform zu interagieren.

### 3.3.6.1.1 Listencontainer

Klicken Sie auf , um die Anforderung **[!UICONTROL GET - Listencontainer]** zu öffnen.

Unter **[!UICONTROL Parameter]** sehen Sie Folgendes:

- property: `_instance.parentName==aepenablementfy22`

In diesem Parameter ist **[!UICONTROL aepenablementfy22]** der Name der Sandbox, die in Adobe Experience Platform verwendet wird. Die Sandbox, die Sie verwenden sollten, ist `--aepSandboxName--`. Ersetzen Sie den Text **[!UICONTROL aepenablementfy22]** durch `--aepSandboxName--`.

Klicken Sie nach dem Ersetzen des Sandbox-Namens auf **[!UICONTROL Senden]**.

![OD API](./images/api2.png)

Dies ist die Antwort, die den Angebotscontainer für die von Ihnen angegebene Sandbox anzeigt. Kopieren Sie die **[!UICONTROL container instanceId]** wie unten angegeben und schreiben Sie sie in eine Textdatei auf Ihrem Computer. Sie müssen diese **[!UICONTROL container instanceId]** für die nächste Übung verwenden!

![OD API](./images/api3.png)

### 3.3.6.1.2 Listenplatzierungen

Klicken Sie auf , um die Anforderung **[!UICONTROL GET - Listenplatzierungen]** zu öffnen. Klicken Sie auf **[!UICONTROL Senden]**.

![OD API](./images/api4.png)

Jetzt werden alle verfügbaren Platzierungen in Ihrem Angebotscontainer angezeigt. Die Platzierungen, die Sie sehen, wurden in der Adobe Experience Platform-Benutzeroberfläche definiert, wie in [Übung 3.3.1.3](./ex1.md) dargestellt.

![OD API](./images/api5.png)

### 3.3.6.1.3 Regeln für Listenentscheidungen

Klicken Sie auf , um die Anforderung **[!UICONTROL GET - Entscheidungsregeln auflisten]** zu öffnen. Klicken Sie auf **[!UICONTROL Senden]**.

![OD API](./images/api6.png)

In der Antwort sehen Sie die Entscheidungsregeln, die Sie in der Adobe Experience Platform-Benutzeroberfläche definiert haben, wie in [Übung 3.3.1.4](./ex1.md) dargestellt.

![OD API](./images/api7.png)

### 3.3.6.1.4 Personalisierte Angebote auflisten

Klicken Sie auf , um die Anforderung **[!UICONTROL GET - Liste personalisierter Angebote]** zu öffnen. Klicken Sie auf **[!UICONTROL Senden]**.

![OD API](./images/api8.png)

In der Antwort sehen Sie die personalisierten Angebote, die Sie in der Adobe Experience Platform-Benutzeroberfläche unter [Übung 3.3.2.1](./ex2.md) definiert haben.

![OD API](./images/api9.png)

### 3.3.6.1.5 Fallback-Angebote auflisten

Klicken Sie auf , um die Anfrage **[!UICONTROL GET - Fallback-Angebote auflisten]** zu öffnen. Klicken Sie auf **[!UICONTROL Senden]**.

![OD API](./images/api10.png)

In der Antwort sehen Sie das Fallback-Angebot, das Sie in der Adobe Experience Platform-Benutzeroberfläche unter [Übung 3.3.2.2](./ex2.md) definiert haben.

![OD API](./images/api11.png)

### 3.3.6.1.6 Listen-Sammlungen

Klicken Sie auf , um die Anforderung **[!UICONTROL GET - Sammlungen auflisten]** zu öffnen.

![OD API](./images/api12.png)

In der Antwort sehen Sie die Sammlung, die Sie in der Adobe Experience Platform-Benutzeroberfläche unter [Übung 3.3.2.3](./ex2.md) definiert haben.

![OD API](./images/api13.png)

### 3.3.6.1.7 Detaillierte Angebote für das Kundenprofil abrufen

Klicken Sie auf , um die Anfrage **[!UICONTROL POST - Detaillierte Angebote für das Kundenprofil abrufen]** zu öffnen. Diese Anfrage ähnelt der vorherigen, gibt jedoch Details wie Bild-URLs, Text usw. zurück.

![OD API](./images/api23.png)

Für diese Anfrage müssen Sie, ähnlich wie bei der vorherigen Übung mit ähnlichen Anforderungen, die Werte für **[!UICONTROL xdm:placementId]** und **[!UICONTROL xdm:activityId]** angeben, um die spezifischen Angebotsdetails für einen Kunden abzurufen.

Das Feld **[!UICONTROL xdm:activityId]** muss ausgefüllt werden. Sie können dies wie unten beschrieben in der Adobe Experience Platform-Benutzeroberfläche abrufen.

![OD API](./images/activityid.png)

Das Feld **[!UICONTROL xdm:placementId]** muss ausgefüllt werden. Sie können dies wie unten beschrieben in der Adobe Experience Platform-Benutzeroberfläche abrufen. Im folgenden Beispiel sehen Sie die placementId für die Platzierung **[!UICONTROL Web - Image]**.

![OD API](./images/placementid.png)

Gehen Sie zu **[!UICONTROL Hauptteil]** und geben Sie die E-Mail-Adresse des Kunden ein, für den Sie ein Angebot anfordern möchten. Klicken Sie auf **[!UICONTROL Senden]**.

![OD API](./images/api24.png)

Schließlich sehen Sie das Ergebnis dessen, welche Art von personalisiertem Angebot und welche Assets diesem Kunden angezeigt werden müssen.

![OD API](./images/api25.png)

Du hast diese Übung jetzt abgeschlossen.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 3.3](./offer-decisioning.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
