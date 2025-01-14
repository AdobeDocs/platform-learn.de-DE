---
title: Erste Schritte mit Firefly-Services
description: Erste Schritte mit Firefly-Services
kt: 5342
doc-type: tutorial
exl-id: 23ebf8b4-3f16-474c-afe1-520d88331417
source-git-commit: a0c16a47372d322a7931578adca30a246b537183
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 2%

---

# 1.2.2 Verwenden von Adobe-APIs in Workfront Fusion

## 1.2.2.1 Verwenden der Firefly-Text-zu-Bild-API mit Workfront Fusion

Bewegen Sie den Mauszeiger über den zweiten Knoten **Mehrere Variablen festlegen** und klicken Sie auf **+**, um ein weiteres Modul hinzuzufügen.

![WF Fusion](./images/wffusion48.png)

Suchen Sie nach **http** und wählen Sie dann **HTTP** aus.

![WF Fusion](./images/wffusion49.png)

Wählen Sie **Anfrage stellen** aus.

![WF Fusion](./images/wffusion50.png)

Wählen Sie diese Variablen aus:

- **URL**: `https://firefly-api.adobe.io/v3/images/generate`
- **Methode**: `POST`

Klicken Sie **Kopfzeile hinzufügen**.

![WF Fusion](./images/wffusion51.png)

Sie müssen die folgenden Kopfzeilen eingeben:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `x-api-key` | Ihre gespeicherte Variable für `CONST_client_id` |
| `Authorization` | `Bearer ` + Ihre gespeicherte Variable für `bearer_token` |
| `Content-Type` | `application/json` |
| `Accept` | `*/*` |

Geben Sie die Details für `x-api-key` ein. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion52.png)

Klicken Sie **Kopfzeile hinzufügen**.

![WF Fusion](./images/wffusion53.png)

Geben Sie die Details für `Authorization` ein. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion54.png)

Klicken Sie **Kopfzeile hinzufügen**. Geben Sie die Details für `Content-Type` ein. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion541.png)

Klicken Sie **Kopfzeile hinzufügen**. Geben Sie die Details für `Accept` ein. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion542.png)

Legen Sie **Body-Typ** auf **Raw** fest. Wählen **für &quot;**&quot; die Option **JSON (application/json)**.

![WF Fusion](./images/wffusion55.png)

Fügen Sie diese Payload in das Feld **Inhalt anfragen** ein.

```json
{
  "numVariations": 1,
  "size": {
    "width": 2048,
    "height": 2048
  },
  "prompt": "Horses in a field",
  "promptBiasingLocaleCode": "en-US"
}
```

Aktivieren Sie das Kontrollkästchen für **Antwort parsen**. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion56.png)

Klicken Sie **Einmal ausführen**.

![WF Fusion](./images/wffusion57.png)

Sobald Ihr Szenario ausgeführt wurde, sollten Sie dies sehen.

![WF Fusion](./images/wffusion58.png)

Auf die **klicken?** Symbol auf dem vierten Knoten, HTTP, um die Antwort anzuzeigen. In der Antwort sollte eine Bilddatei angezeigt werden.

![WF Fusion](./images/wffusion59.png)

Kopieren Sie die Bild-URL und öffnen Sie sie in einem Browser-Fenster. Sie sollten dann etwas wie das hier sehen:

![WF Fusion](./images/wffusion60.png)

Klicken Sie mit der rechten Maustaste auf **HTTP**-Objekt und benennen Sie es in **Firefly T2I** um.

![WF Fusion](./images/wffusion62.png)

Klicken Sie **Speichern**, um Ihre Änderungen zu speichern.

![WF Fusion](./images/wffusion61.png)

## 1.2.2.2 Verwenden der Photoshop-API mit Workfront Fusion

Klicken Sie auf das **Schraubenschlüssel**-Symbol zwischen den Knoten **Set Bearer Token** und **Firefly T2I**. Wählen Sie **Router hinzufügen**.

![WF Fusion](./images/wffusion63.png)

Klicken Sie mit der rechten Maustaste auf das **Firefly T2I**-Objekt und wählen Sie **Klonen**.

![WF Fusion](./images/wffusion64.png)

Ziehen Sie das geklonte Objekt in die Nähe des **Router**-Objekts, und es stellt automatisch eine Verbindung zum **Router** her. Sie sollten dann diese haben.

![WF Fusion](./images/wffusion65.png)

Sie verfügen jetzt über eine identische Kopie basierend auf der HTTP-Anfrage **Firefly T2I**. Einige der Einstellungen der **Firefly T2I**-HTTP-Anfrage entsprechen denen, die Sie für die Interaktion mit der **Photoshop-API** benötigen, was eine Zeitersparnis darstellt. Sie müssen jetzt nur die Variablen ändern, die nicht identisch sind, wie die Anfrage-URL und die Payload.

Ändern Sie die **URL** in `https://image.adobe.io/pie/psdService/text`.

![WF Fusion](./images/wffusion66.png)

Ersetzen Sie **Anfrageinhalt** durch die folgende Payload:

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/sevoi-psd.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "layers": [
      {
        "name": "2048x2048-button",
        "text": {
          "content": "Click here"
        }
      },
      {
        "name": "2048x2048-cta",
        "text": {
          "content": "Buy this stuff"
        }
      }
    ]
  },
  "outputs": [
    {
      "storage": "azure",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/sevoi-psd-changed-text.psd{{AZURE_STORAGE_SAS_WRITE}}",
      "type": "vnd.adobe.photoshop",
      "overwrite": true
    }
  ]
}
```

![WF Fusion](./images/wffusion67.png)

Damit dieser **Anfrageinhalt** ordnungsgemäß funktioniert, fehlen einige Variablen:

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

Gehen Sie zurück zu Ihrem ersten Knoten, klicken Sie auf **Konstanten initialisieren** und wählen Sie dann **Element hinzufügen** für jede dieser Variablen aus.

![WF Fusion](./images/wffusion69.png)

| Schlüssel | Beispielwert |
|:-------------:| :---------------:| 
| `AZURE_STORAGE_URL` | `https://vangeluw.blob.core.windows.net` |
| `AZURE_STORAGE_CONTAINER` | `vangeluw` |
| `AZURE_STORAGE_SAS_READ` | `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D` |
| `AZURE_STORAGE_SAS_WRITE` | `?sv=2023-01-03&st=2025-01-13T17%3A21%3A09Z&se=2025-01-14T17%3A21%3A09Z&sr=c&sp=racwl&sig=FD4m0YyyqUj%2B5T8YyTFJDi55RiTDC9xKtLTgW0CShps%3D` |

Sie können Ihre Variablen finden, indem Sie zurück zu Postman gehen und Ihre **Umgebungsvariablen** öffnen.

![Azure-Speicher](./../module1.1/images/az105.png)

Kopieren Sie diese Werte nach Workfront Fusion und fügen Sie für jede dieser vier Variablen ein neues Element hinzu.

Sie sollten dann diese haben. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion68.png)

Kehren Sie anschließend zur geklonten HTTP-Anfrage zurück, um den **Anfrageinhalt** zu aktualisieren. Diese schwarzen Variablen werden Sie im **Anfrageinhalt** bemerken, bei dem es sich um die Variablen handelt, die Sie aus Postman kopiert haben. Jetzt müssen Sie diese in die Variablen ändern, die Sie gerade in Workfront Fusion definiert haben. Ersetzen Sie jede Variable einzeln, indem Sie den schwarzen Text löschen und durch die richtige Variable ersetzen.

![WF Fusion](./images/wffusion70.png)

Im Abschnitt **Eingaben** sind drei Änderungen vorzunehmen.

![WF Fusion](./images/wffusion71.png)

Im Abschnitt **Ausgänge“ sind außerdem** Änderungen vorzunehmen. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion72.png)

Klicken Sie mit der rechten Maustaste auf den geklonten Knoten und wählen Sie **Umbenennen**. Ändern Sie den Namen in **Photoshop-Änderungstext**.

![WF Fusion](./images/wffusion73.png)

Sie sollten dann diese haben.

![WF Fusion](./images/wffusion74.png)

Nächster Schritt: [1.2.3 …](./ex3.md)

[Zurück zum Modul 1.2](./automation.md)

[Zurück zu „Alle Module“](./../../../overview.md)
