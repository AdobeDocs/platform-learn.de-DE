---
title: Erste Schritte - Adobe I/O
description: Erste Schritte - Adobe I/O
kt: 5342
doc-type: tutorial
exl-id: 00f17d4f-a2c8-4e8e-a1ff-556037a60629
source-git-commit: 3b6ae4bb4eb2d9f189438dddc461bb0f2a0a9aac
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 3%

---

# Konfigurieren des Adobe I/O-Projekts

## Erstellen eines Adobe I/O-Projekts

In dieser Übung wird Adobe I/O verwendet, um verschiedene Adobe-Endpunkte abzufragen. Führen Sie diese Schritte aus, um Adobe I/O einzurichten.

Navigieren Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"}.

![Neue Adobe I/O-Integration](./images/iohome.png){zoomable="yes"}

Achten Sie darauf, dass Sie die richtige Instanz in der oberen rechten Ecke Ihres Bildschirms auswählen. Ihre Instanz ist `--aepImsOrgName--`.

>[!NOTE]
>
> Der folgende Screenshot zeigt, wie eine bestimmte Organisation ausgewählt wird. Wenn Sie dieses Tutorial durchlaufen, hat Ihre Organisation höchstwahrscheinlich einen anderen Namen. Wenn Sie sich für dieses Tutorial angemeldet haben, wurden Ihnen die zu verwendenden Umgebungsdetails zur Verfügung gestellt. Befolgen Sie bitte diese Anweisungen.

Wählen Sie anschließend **Neues Projekt erstellen**.

![Neue Adobe I/O-Integration](./images/iocomp.png){zoomable="yes"}

### Firefly Services-API

Sie sollten das dann sehen. Wählen Sie **+ Zu Projekt hinzufügen** und dann **API**.

![Neue Adobe I/O-Integration](./images/adobe_io_access_api.png){zoomable="yes"}

Ihr Bildschirm sollte wie folgt aussehen.

![Neue Adobe I/O-Integration](./images/api1.png){zoomable="yes"}

Wählen Sie **Creative Cloud** und **Firefly - Firefly Services** aus und klicken Sie dann auf **Weiter**.

![Neue Adobe I/O-Integration](./images/api3.png){zoomable="yes"}

Geben Sie einen Namen für Ihre Berechtigung ein: `--aepUserLdap-- - One Adobe OAuth credential` und wählen Sie **Weiter**.

![Neue Adobe I/O-Integration](./images/api4.png){zoomable="yes"}

Wählen Sie das Standardprofil **Standardkonfiguration für Firefly Services** und anschließend **Konfigurierte API speichern** aus.

![Neue Adobe I/O-Integration](./images/api9.png){zoomable="yes"}

Sie sollten das dann sehen.

![Neue Adobe I/O-Integration](./images/api10.png){zoomable="yes"}

### Photoshop Services-API

Wählen Sie **+ Zu Projekt hinzufügen** dann **API** aus.

![Azure-Speicher](./images/ps2.png){zoomable="yes"}

Wählen Sie **Creative Cloud** und dann **Photoshop - Firefly Services**. Klicken Sie auf **Weiter**.

![Azure-Speicher](./images/ps3.png){zoomable="yes"}

Klicken Sie auf **Weiter**.

![Azure-Speicher](./images/ps4.png){zoomable="yes"}

Als Nächstes müssen Sie ein Produktprofil auswählen, das definiert, welche Berechtigungen für diese Integration verfügbar sind.

Wählen Sie **Standardkonfiguration für Firefly Services** und **Standardkonfiguration für Creative Cloud-Automatisierungsdienste** aus.

Wählen Sie **Konfigurierte API speichern**.

![Azure-Speicher](./images/ps5.png){zoomable="yes"}

Sie sollten das dann sehen.

![Neue Adobe I/O-Integration](./images/ps7.png){zoomable="yes"}

### Adobe Experience Platform-API

Wählen Sie **+ Zu Projekt hinzufügen** dann **API** aus.

![Azure-Speicher](./images/aep1.png){zoomable="yes"}

Wählen Sie **Adobe Experience** und **Experience Platform API**. Klicken Sie auf **Weiter**.

![Azure-Speicher](./images/aep2.png){zoomable="yes"}

Klicken Sie auf **Weiter**.

![Azure-Speicher](./images/aep3.png){zoomable="yes"}

Als Nächstes müssen Sie ein Produktprofil auswählen, das definiert, welche Berechtigungen für diese Integration verfügbar sind.

Wählen Sie **Adobe Experience Platform - Alle Benutzer - PROD** aus.

>[!NOTE]
>
>Der Name des Produktprofils für AEP hängt davon ab, wie die Umgebung konfiguriert wurde. Wenn das oben genannte Produktprofil nicht angezeigt wird, verfügen Sie möglicherweise über ein Produktprofil mit dem Namen **Standardzugriff auf alle Produktionssysteme**. Wenn Sie sich nicht sicher sind, welches ausgewählt werden soll, wenden Sie sich an Ihren AEP-Systemadministrator.

Wählen Sie **Konfigurierte API speichern**.

![Azure-Speicher](./images/aep4.png){zoomable="yes"}

Sie sollten das dann sehen.

![Neue Adobe I/O-Integration](./images/aep5.png){zoomable="yes"}

### Projektname

Klicken Sie auf Ihren Projektnamen.

![Neue Adobe I/O-Integration](./images/api13.png){zoomable="yes"}

Wählen Sie **Projekt bearbeiten** aus.

![Neue Adobe I/O-Integration](./images/api14.png){zoomable="yes"}

Geben Sie einen Anzeigenamen für Ihre Integration ein: `--aepUserLdap-- One Adobe tutorial` und wählen Sie **Speichern**.

![Neue Adobe I/O-Integration](./images/api15.png){zoomable="yes"}

Die Einrichtung Ihres Adobe I/O-Projekts ist jetzt abgeschlossen.

![Neue Adobe I/O-Integration](./images/api16.png){zoomable="yes"}

## Nächste Schritte

Navigieren Sie zu [Option 1: Postman-Setup](./ex7.md){target="_blank"}

Gehen Sie zu [Option 2: PostBuster-Einrichtung](./ex8.md){target="_blank"}

Zurück zu [Erste Schritte](./getting-started.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
