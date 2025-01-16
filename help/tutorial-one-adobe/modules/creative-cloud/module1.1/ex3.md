---
title: Erste Schritte mit Firefly-Services
description: Erste Schritte mit Firefly-Services
kt: 5342
doc-type: tutorial
exl-id: 60eecc24-1713-4fec-9ffa-a3186db1a8ca
source-git-commit: 0fe4bbf6bcc80d4fa88bc30718a1de6621f93f17
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 1%

---

# 1.1.3 Adobe Firefly und Adobe Photoshop

## 1.1.3.1 Aktualisieren der Adobe I/O-Integration

Navigieren Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home).

![Neue Integration Adobe I/O](./images/iohome.png)

Navigieren Sie **Projekte** und klicken Sie, um das in der vorherigen Übung erstellte Projekt mit dem Namen `--aepUserLdap-- Firefly` zu öffnen.

![Azure-Speicher](./images/ps1.png)

Klicken Sie auf **+ Zum Projekt hinzufügen** dann auf **API**.

![Azure-Speicher](./images/ps2.png)

Wählen Sie **Creative Cloud** und klicken Sie auf **Photoshop - Firefly Services**. Klicken Sie auf **Weiter**.

![Azure-Speicher](./images/ps3.png)

Klicken Sie auf **Weiter**.

![Azure-Speicher](./images/ps4.png)

Als Nächstes müssen Sie ein Produktprofil auswählen, das definiert, welche Berechtigungen für diese Integration verfügbar sind.

Wählen Sie das Profil **Standardkonfiguration für Firefly-**) und **Standardkonfiguration für Creative Cloud-Automatisierungsdienste** aus.

Klicken Sie **Konfigurierte API speichern**.

![Azure-Speicher](./images/ps5.png)

Ihr Adobe I/O-Projekt wurde jetzt aktualisiert, um mit Photoshop- und Firefly-Services-APIs arbeiten zu können.

![Azure-Speicher](./images/ps6.png)

## Programmgesteuerte Interaktion 1.1.3.2 PSD-Dateien

Laden Sie die Datei Go to [Citisignal-fiber.psd](./../../../assets/ff/citisignal-fiber.psd) auf Ihren Desktop herunter.

Öffnen Sie die Datei **Citisignal-fiber.psd** in Photoshop. Sie sollten dann diese haben.

![Azure-Speicher](./images/ps7.png)

Im Bereich **Ebenen** sehen Sie, dass der Designer der Datei jeder Ebene einen eindeutigen Namen gegeben hat. Sie können die Ebeneninformationen anzeigen, indem Sie die PSD-Datei in Photoshop öffnen. Sie können dies aber auch programmgesteuert tun.

Senden wir Ihre erste API-Anfrage an Photoshop-APIs.

Weiter zu Postman. Bevor Sie API-Anfragen an Photoshop senden, müssen Sie sich beim Adobe I/O authentifizieren. Öffnen Sie die zuvor verwendete Anfrage mit dem Namen **POST - Zugriffstoken abrufen**.

Wechseln Sie zu **Parameter** und überprüfen Sie, ob der Parameter **Umfang** ordnungsgemäß festgelegt ist. Der **Wert** für **Umfang** sollte wie folgt aussehen:

`openid,session,AdobeID,read_organizations,additional_info.projectedProductContext, ff_apis, firefly_api`

Klicken Sie dann auf **Senden**.

![Azure-Speicher](./images/ps8.png)

Anschließend verfügen Sie über ein gültiges Zugriffstoken für die Interaktion mit Photoshop-APIs.

![Azure-Speicher](./images/ps9.png)

Als Nächstes begrüßen wir Photoshop-APIs, um zu testen, ob alle Berechtigungen und der Zugriff richtig festgelegt sind. Öffnen Sie in der Sammlung **Photoshop** die Anfrage mit dem Namen **Photoshop Hello (Test Auth.)**. Klicken Sie auf **Senden**.

![Azure-Speicher](./images/ps10.png)

Sie sollten dann diese Antwort erhalten: **Willkommen bei der Photoshop-API!**.

![Azure-Speicher](./images/ps11.png)

Als Nächstes müssen Sie die PSD-Datei **Citisignal-fiber.psd** in Ihr Speicherkonto hochladen, um programmatisch mit ihr zu interagieren. Sie könnten dies manuell tun, indem Sie es per Drag-and-Drop mit dem Azure Storage-Explorer in Ihren Container ziehen. Dieses Mal sollten Sie es jedoch über die API tun.

Öffnen Sie in Postman die Anfrage **PSD in Azure-Speicherkonto hochladen**. In der vorherigen Übung haben Sie diese Umgebungsvariablen in Postman konfiguriert, die Sie jetzt verwenden werden:

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

Wie Sie in der Anfrage **PSD in Azure-Speicherkonto hochladen** sehen können, ist die URL so konfiguriert, dass diese Variablen verwendet werden.

![Azure-Speicher](./images/ps12.png)

In **Body** sollten Sie jetzt die Datei &quot;**-fiber.psd“**.

![Azure-Speicher](./images/ps13.png)

Sie sollten dann diese haben. Klicken Sie auf **Senden**.

![Azure-Speicher](./images/ps14.png)

Sie sollten dann diese leere Antwort von Azure zurückerhalten, was bedeutet, dass Ihre Datei in Ihrem Container in Ihrem Azure-Speicherkonto gespeichert ist.

![Azure-Speicher](./images/ps15.png)

Wenn Sie Azure Storage Explorer verwenden, um einen Blick zu werfen, sehen Sie Ihre -Datei, nachdem Sie Ihren Ordner aktualisiert haben.

![Azure-Speicher](./images/ps16.png)

Als Nächstes müssen Sie die Manifestdatei Ihrer PSD-Datei abrufen. Öffnen Sie in Postman die Anfrage **Photoshop - PSD-Manifest abrufen**. Wechseln Sie zu **Textkörper**.

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

Klicken Sie auf **Senden**.

In der Antwort wird jetzt ein Link angezeigt. Da es manchmal einige Zeit dauern kann, bis Vorgänge in Photoshop abgeschlossen sind, stellt Photoshop eine Statusdatei als Antwort auf die meisten eingehenden Anfragen bereit. Um zu verstehen, was mit Ihrer Anfrage passiert, müssen Sie die Statusdatei lesen.

![Azure-Speicher](./images/ps17.png)

Um die Statusdatei zu lesen, öffnen Sie die Anfrage **Photoshop - Get PS Status**. Anschließend sehen Sie, dass diese Anfrage eine Variable als URL verwendet. Dies ist eine Variable, die von der vorherigen Anfrage festgelegt wurde, die Sie gesendet haben: **Photoshop - PSD-Manifest abrufen**. Variablen werden in den **Skripten** jeder Anfrage festgelegt.

Klicken Sie auf **Senden**.

![Azure-Speicher](./images/ps18.png)

Sie sollten das dann sehen. Derzeit ist der Status auf **Ausstehend** festgelegt, was bedeutet, dass der Prozess noch nicht abgeschlossen ist.

![Azure-Speicher](./images/ps19.png)

Sie können bei der Anfrage **Photoshop - PS-Status abrufen** noch einige Male auf Senden klicken, bis sich der Status auf &quot;**&quot;**. Dies kann einige Minuten dauern.

Wenn die Antwort verfügbar ist, wird eine JSON-Datei angezeigt, die Informationen zu allen Ebenen der PSD-Datei enthält. Dies sind nützliche Informationen, da Dinge wie der Ebenenname oder die Ebenenkennung hier zu sehen sind.

![Azure-Speicher](./images/ps20.png)

Suchen Sie beispielsweise nach dem `2048x2048-cta`. Sie sollten das dann sehen.

![Azure-Speicher](./images/ps21.png)

Als Nächstes müssen Sie jetzt den Text für den Aktionsaufruf mithilfe der APIs ändern. Öffnen Sie in Postman die Anfrage **Photoshop - Text ändern** und navigieren Sie zu **Hauptteil**.

Sie sollten das dann sehen. Sie können Folgendes sehen:

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

Die Ausgabedatei hat einen anderen Namen, da Sie die ursprüngliche Eingabedatei nicht überschreiben möchten.

Klicken Sie auf **Senden**.

![Azure-Speicher](./images/ps23.png)

Wie zuvor enthält die Antwort einen Link, der auf die Statusdatei verweist, die den Fortschritt verfolgt.

![Azure-Speicher](./images/ps22.png)

Um die Statusdatei zu lesen, öffnen Sie erneut die Anfrage **Photoshop - PS-** abrufen und klicken Sie auf **Senden**. Wenn der Status nicht sofort auf **Erfolgreich** festgelegt ist, warten Sie einige Sekunden und klicken Sie dann erneut auf **Senden**.

Sobald der Status auf **Erfolgreich** festgelegt wurde, sollte Folgendes angezeigt werden. Im `outputs[0]._links.renditions[0].href` Pfad sollte die URL der von Photoshop erstellten Ausgabedatei angezeigt werden, die den geänderten Text enthält.

Klicken Sie auf die URL, um die Ausgabedatei herunterzuladen.

![Azure-Speicher](./images/ps24.png)

Die Datei **Citisignal-fiber-changed-text.psd** wird dann auf Ihren Computer heruntergeladen und kann anschließend geöffnet werden. Anschließend sollten Sie sehen, dass der Platzhalter für den Aktionsaufruf durch den Text &quot;**jetzt abrufen!** ersetzt wurde.

![Azure-Speicher](./images/ps25.png)

Schließlich sehen Sie diese Datei dann auch in Ihrem Container mit dem Azure Storage-Explorer.

![Azure-Speicher](./images/ps26.png)

Sie haben jetzt diese Übung abgeschlossen.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zum Modul 1.1](./firefly-services.md)

[Zurück zu „Alle Module“](./../../../overview.md)
