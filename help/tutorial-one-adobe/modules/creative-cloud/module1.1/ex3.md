---
title: Arbeiten mit Photoshop-APIs
description: Erfahren Sie, wie Sie mit den Photoshop-APIs und Firefly Services arbeiten
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 60eecc24-1713-4fec-9ffa-a3186db1a8ca
source-git-commit: 07c890d1f3e5dbcec5b3a81badb9a7147eed72db
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# 1.1.3 Arbeiten mit Photoshop-APIs

Erfahren Sie, wie Sie mit den Photoshop-APIs und Firefly Services arbeiten.

## Voraussetzungen für 1.1.3.1

Bevor Sie mit dieser Übung fortfahren, müssen Sie das Setup von [Ihr Adobe I/O-Projekt](./../../../modules/getting-started/gettingstarted/ex6.md) abgeschlossen haben. Außerdem müssen Sie eine Anwendung für die Interaktion mit APIs konfiguriert haben, z. B. [Postman](./../../../modules/getting-started/gettingstarted/ex7.md) oder [PostBuster](./../../../modules/getting-started/gettingstarted/ex8.md).

## 1.1.3.2 Adobe I/O - access_token

Wählen Sie in der Sammlung **Adobe IO - OAuth** die Anfrage mit dem Namen **POST - Zugriffstoken abrufen** und klicken Sie auf **Senden**. Die Antwort sollte ein neues &quot;**&quot;**.

![Postman](./images/ioauthresp.png){zoomable="yes"}

## Programmgesteuerte Interaktion von 1.1.3.3 mit einer PSD-Datei

Laden Sie [Citisignal-fiber.psd](./../../../assets/ff/citisignal-fiber.psd){target="_blank"} auf Ihren Desktop herunter.

Öffnen Sie **Citisignal-fiber.psd** in Photoshop.

![Azure-Speicher](./images/ps7.png){zoomable="yes"}

Im Bereich **Ebenen** hat der Designer der Datei jeder Ebene einen eindeutigen Namen gegeben. Sie können die Ebeneninformationen anzeigen, indem Sie die PSD-Datei in Photoshop öffnen. Sie können dies aber auch programmgesteuert tun.

Senden wir Ihre erste API-Anfrage an Photoshop-APIs.

### Photoshop-API - Hello World

Als Nächstes begrüßen wir Photoshop-APIs, um zu testen, ob alle Berechtigungen und der Zugriff richtig festgelegt sind.

1. Öffnen Sie in der Sammlung **Photoshop** die Anfrage **Photoshop Hello (Test Auth.)**. Wählen Sie **Senden** aus.

![Azure-Speicher](./images/ps10.png){zoomable="yes"}

Sie sollten die Antwort erhalten &quot;**zur Photoshop-API!**.

![Azure-Speicher](./images/ps11.png){zoomable="yes"}

Als Nächstes müssen Sie die PSD-Datei **Citisignal-fiber.psd** in Ihr -Speicherkonto hochladen, um programmatisch mit ihr zu interagieren. Sie können dies manuell tun, indem Sie es mit dem Azure Storage Explorer per Drag-and-Drop in Ihren Container ziehen. Diesmal sollten Sie es jedoch über die API tun.

### PSD in Azure hochladen

1. Öffnen Sie in Postman die Anfrage **PSD in Azure-Speicherkonto hochladen**. In der vorherigen Übung haben Sie diese Umgebungsvariablen in Postman konfiguriert, die Sie jetzt verwenden werden:

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

Wie Sie in der Anfrage **PSD in Azure-Speicherkonto hochladen** sehen können, ist die URL so konfiguriert, dass diese Variablen verwendet werden.

![Azure-Speicher](./images/ps12.png){zoomable="yes"}

1. Wählen **in &quot;**&quot; die Datei **citsignal-fiber.psd** aus.

![Azure-Speicher](./images/ps13.png){zoomable="yes"}

1. Ihr Bildschirm sollte wie folgt aussehen. Wählen Sie **Senden** aus.

![Azure-Speicher](./images/ps14.png){zoomable="yes"}

Sie sollten diese leere Antwort von Azure zurückerhalten, was bedeutet, dass Ihre Datei in Ihrem Container in Ihrem Azure-Speicherkonto gespeichert ist.

![Azure-Speicher](./images/ps15.png){zoomable="yes"}

Wenn Sie Azure Storage Explorer verwenden, um Ihre Datei zu überprüfen, müssen Sie Ihren Ordner aktualisieren.

![Azure-Speicher](./images/ps16.png){zoomable="yes"}

### Photoshop-API - Manifest abrufen

Als Nächstes müssen Sie die Manifestdatei Ihrer PSD-Datei abrufen.

1. Öffnen Sie in Postman die Anfrage **Photoshop - PSD-Manifest abrufen**. Wechseln Sie zu **Textkörper**.

Der Textkörper sollte wie folgt aussehen:

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "thumbnails": {
      "type": "image/jpeg"
    }
  }
}
```

1. Wählen Sie **Senden** aus.

In der Antwort wird jetzt ein Link angezeigt. Da es manchmal einige Zeit dauern kann, bis Vorgänge in Photoshop abgeschlossen sind, stellt Photoshop eine Statusdatei als Antwort auf die meisten eingehenden Anfragen bereit. Um zu verstehen, was mit Ihrer Anfrage passiert, müssen Sie die Statusdatei lesen.

![Azure-Speicher](./images/ps17.png){zoomable="yes"}

1. Um die Statusdatei zu lesen, öffnen Sie die Anfrage **Photoshop - Get PS Status**. Sie können sehen, dass diese Anfrage eine Variable als URL verwendet. Dies ist eine Variable, die von der vorherigen Anfrage festgelegt wurde, die Sie gesendet haben: **Photoshop - PSD-Manifest abrufen**. Variablen werden in den **Skripten** jeder Anfrage festgelegt. Wählen Sie **Senden** aus.

![Azure-Speicher](./images/ps18.png){zoomable="yes"}

Ihr Bildschirm sollte wie folgt aussehen. Derzeit ist der Status auf **Ausstehend** festgelegt, was bedeutet, dass der Prozess noch nicht abgeschlossen ist.

![Azure-Speicher](./images/ps19.png){zoomable="yes"}

1. Wählen Sie Mehrere Male senden auf **Photoshop - PS-Status abrufen**, bis sich der Status auf &quot;**&quot;**. Dies kann einige Minuten dauern.

Wenn die Antwort verfügbar ist, können Sie sehen, dass die JSON-Datei Informationen zu allen Ebenen der PSD-Datei enthält. Dies ist eine nützliche Information, da Dinge wie der Ebenenname oder die Ebenenkennung identifiziert werden können.

![Azure-Speicher](./images/ps20.png){zoomable="yes"}

Suchen Sie beispielsweise nach dem `2048x2048-cta`. Ihr Bildschirm sollte wie folgt aussehen:

![Azure-Speicher](./images/ps21.png){zoomable="yes"}

### Photoshop-API - Text ändern

Als Nächstes müssen Sie den Text für den Aktionsaufruf mithilfe der APIs ändern.

1. Öffnen Sie in Postman die Anfrage **Photoshop - Text ändern** und navigieren Sie zu **Hauptteil**.

Ihr Bildschirm sollte wie folgt aussehen:

- Zunächst wird eine Eingabedatei angegeben: `citisignal-fiber.psd`
- Zweitens wird die zu ändernde Ebene mit dem zu ändernden Text angegeben
- Drittens wird eine Ausgabedatei angegeben: `citisignal-fiber-changed-text.psd`

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "layers": [
      {
        "name": "2048x2048-cta",
        "text": {
          "content": "Get Fiber now!"
        }
      }
    ]
  },
  "outputs": [
    {
      "storage": "azure",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text.psd{{AZURE_STORAGE_SAS_WRITE}}",
      "type": "vnd.adobe.photoshop",
      "overwrite": true
    }
  ]
}
```

Die Ausgabedatei hat einen anderen Namen, da die ursprüngliche Eingabedatei nicht überschrieben werden soll.

1. Wählen Sie **Senden** aus.

![Azure-Speicher](./images/ps23.png){zoomable="yes"}

Wie zuvor enthält die Antwort einen Link, der auf die Statusdatei verweist, die den Fortschritt verfolgt.

![Azure-Speicher](./images/ps22.png){zoomable="yes"}

1. Um die Statusdatei zu lesen, öffnen Sie die Anfrage **Photoshop - PS-Status abrufen** und wählen Sie **Senden**. Wenn der Status nicht sofort auf **Erfolgreich** festgelegt ist, warten Sie einige Sekunden und wählen Sie dann erneut **Senden** aus.

1. Wählen Sie die URL aus, um die Ausgabedatei herunterzuladen.

![Azure-Speicher](./images/ps24.png){zoomable="yes"}

1. Öffnen Sie **citsignal-fiber-changed-text.psd** nach dem Herunterladen der Datei auf Ihren Computer. Der Platzhalter für den Aktionsaufruf wurde durch den Text „Jetzt Fibre **!** ersetzt.

![Azure-Speicher](./images/ps25.png){zoomable="yes"}

Diese Datei wird auch in Ihrem Container mit dem Azure Storage-Explorer angezeigt.

![Azure-Speicher](./images/ps26.png){zoomable="yes"}

## Nächste Schritte

Zur [Firefly Custom Models-API](./ex4.md){target="_blank"}

Zurück zu [Übersicht über Adobe Firefly Services](./firefly-services.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
