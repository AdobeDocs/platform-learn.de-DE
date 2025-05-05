---
title: Verwenden von Adobe-APIs in Workfront Fusion
description: Erfahren Sie, wie Sie Adobe-APIs in Workfront Fusion verwenden
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 23ebf8b4-3f16-474c-afe1-520d88331417
source-git-commit: 603e48e0453911177823fe7ceb340f8ca801c5e1
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 0%

---

# 1.2.2 Verwenden von Adobe-APIs in Workfront Fusion

Erfahren Sie, wie Sie Adobe-APIs in Workfront Fusion verwenden.

## Verwenden 1.2.2.1 Firefly Text-to-Image-API mit Workfront Fusion

Bewegen Sie den Mauszeiger über den zweiten **mehrere Variablen festlegen**-Knoten und wählen Sie **+** aus, um ein weiteres Modul hinzuzufügen.

![WF Fusion](./images/wffusion48.png)

Suchen Sie nach **http** und wählen Sie **HTTP** aus.

![WF Fusion](./images/wffusion49.png)

Wählen Sie **Anfrage stellen** aus.

![WF Fusion](./images/wffusion50.png)

Wählen Sie diese Variablen aus:

- **URL**: `https://firefly-api.adobe.io/v3/images/generate`
- **Methode**: `POST`

Wählen Sie **hinzufügen einer Kopfzeile** aus.

![WF Fusion](./images/wffusion51.png)

Geben Sie die folgenden Kopfzeilen ein:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `x-api-key` | Ihre gespeicherte Variable für `CONST_client_id` |
| `Authorization` | `Bearer ` + Ihre gespeicherte Variable für `bearer_token` |
| `Content-Type` | `application/json` |
| `Accept` | `*/*` |

Geben Sie die Details für `x-api-key` ein. Wählen Sie **Hinzufügen** aus.

![WF Fusion](./images/wffusion52.png)

Wählen Sie **Kopfzeile hinzufügen**.

![WF Fusion](./images/wffusion53.png)

Geben Sie die Details für `Authorization` ein. Wählen Sie **Hinzufügen** aus.

![WF Fusion](./images/wffusion54.png)

Wählen Sie **Kopfzeile hinzufügen**. Geben Sie die Details für `Content-Type` ein. Wählen Sie **Hinzufügen** aus.

![WF Fusion](./images/wffusion541.png)

Wählen Sie **Kopfzeile hinzufügen**. Geben Sie die Details für `Accept` ein. Wählen Sie **Hinzufügen** aus.

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

Aktivieren Sie das Kontrollkästchen für **Antwort analysieren**. Klicken Sie **OK**.

![WF Fusion](./images/wffusion56.png)

Wählen Sie **Einmal ausführen** aus.

![WF Fusion](./images/wffusion57.png)

Ihr Bildschirm sollte wie folgt aussehen.

![WF Fusion](./images/wffusion58.png)

Wählen Sie das **Symbol ?,** auf dem vierten Knoten, HTTP, um die Antwort anzuzeigen. In der Antwort sollte ein Grafikdatei angezeigt werden.

![WF Fusion](./images/wffusion59.png)

Kopie das Bild URL und öffnen Sie es in einem Browser-Fenster. Ihr Bildschirm sollte liken diesem aussehen:

![WF Fusion](./images/wffusion60.png)

Klicken Sie mit der rechten Maustaste **HTTP** und benennen Sie in **Firefly T2I** um.

![WF Fusion](./images/wffusion62.png)

Wählen Sie **Speichern** aus, um die Änderungen zu speichern.

![WF Fusion](./images/wffusion61.png)

## 1.2.2.2 Verwenden Photoshop-API mit Workfront Fusion

Wählen Sie **wrench** zwischen den Knoten **Set Bearer Token** und **Firefly T2I**. Wählen Sie **Router hinzufügen**.

![WF Fusion](./images/wffusion63.png)

Klicken Sie mit der rechten Maustaste auf das **Firefly T2I**-Objekt und wählen Sie **Klonen**.

![WF Fusion](./images/wffusion64.png)

Ziehen Sie das geklonte Objekt in die Nähe des **Router**-Objekts - es stellt automatisch eine Verbindung zum **her**. Ihr Bildschirm sollte wie folgt aussehen:

![WF Fusion](./images/wffusion65.png)

Sie verfügen jetzt über eine identische Kopie basierend auf der **Firefly T2I**-HTTP-Anfrage. Einige der Einstellungen der **Firefly T2I**-HTTP-Anfrage ähneln denen, die Sie für die Interaktion mit der **Photoshop-API** benötigen, was eine Zeitersparnis darstellt. Jetzt müssen Sie nur noch die Variablen ändern, die nicht identisch sind, wie die Anfrage-URL und die Payload.

Ändern Sie die **URL** in `https://image.adobe.io/pie/psdService/text`.

![WF Fusion](./images/wffusion66.png)

Ersetzen **Anfrageinhalt** durch die folgende Payload:

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
          "name": "2048x2048-button-text",
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
        "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text.psd{{AZURE_STORAGE_SAS_WRITE}}",
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

Gehen Sie zurück zu Ihrem ersten Knoten, wählen Sie **Konstanten initialisieren** und wählen Sie dann **Element hinzufügen** für jede dieser Variablen aus.

![WF Fusion](./images/wffusion69.png)

| Schlüssel | Beispiel Wert |
|:-------------:| :---------------:| 
| `AZURE_STORAGE_URL` | `https://vangeluw.blob.core.windows.net` |
| `AZURE_STORAGE_CONTAINER` | `vangeluw` |
| `AZURE_STORAGE_SAS_READ` | `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D` |
| `AZURE_STORAGE_SAS_WRITE` | `?sv=2023-01-03&st=2025-01-13T17%3A21%3A09Z&se=2025-01-14T17%3A21%3A09Z&sr=c&sp=racwl&sig=FD4m0YyyqUj%2B5T8YyTFJDi55RiTDC9xKtLTgW0CShps%3D` |

Sie können Ihre Variablen suchen, indem Sie zu Postman zurückkehren und Ihren **Umgebung Variablen** öffnen.

![Azure Storage](./../module1.1/images/az105.png)

Kopie diese Werte an Workfront Fusion weiter, und fügen Sie für jede dieser 4 Variablen ein neues Element hinzu.

Ihr Bildschirm sollte liken diesem aussehen. Klicken Sie **OK**.

![WF Fusion](./images/wffusion68.png)

Kehren Sie anschließend zur geklonten HTTP-Anfrage zurück, um den **Anfrageinhalt** zu aktualisieren. Beachten Sie die schwarzen Variablen im **Anfrageinhalt**. Dies sind die Variablen, die Sie aus Postman kopiert haben. Sie müssen zu den Variablen wechseln, die Sie gerade in Workfront Fusion definiert haben. Ersetzen Sie jede Variable einzeln, indem Sie den schwarzen Text löschen und durch die richtige Variable ersetzen.

![WF Fusion](./images/wffusion70.png)

Nehmen Sie diese 3 Änderungen im Abschnitt **Eingaben** vor. Klicken Sie **OK**.

![WF Fusion](./images/wffusion71.png)

Nehmen Sie diese 3 Änderungen im Abschnitt **Ausgänge** vor. Klicken Sie **OK**.

![WF Fusion](./images/wffusion72.png)

Klicken Sie mit der rechten Maustaste auf den geklonten Knoten und wählen Sie **Umbenennen**. Ändern Sie den Namen in **Photoshop-Änderungstext**.

![WF Fusion](./images/wffusion73.png)

Ihr Bildschirm sollte wie folgt aussehen:

![WF Fusion](./images/wffusion74.png)

Wählen Sie **Einmal ausführen** aus.

![WF Fusion](./images/wffusion75.png)

Wählen Sie das **search**-Symbol im Knoten **Photoshop-** aus, um die Antwort anzuzeigen. Sie sollten über eine Antwort verfügen, die wie folgt aussieht, mit einem Link zu einer Statusdatei.

![WF Fusion](./images/wffusion76.png)

Deaktivieren Sie vor dem Fortsetzen der Photoshop-API-Interaktionen die Route zum **Firefly T2I**-Knoten, um nicht benötigte API-Aufrufe an diesen API-Endpunkt zu senden. Wählen Sie das **Schraubenschlüssel**-Symbol aus und wählen Sie dann **Route deaktivieren**.

![WF Fusion](./images/wffusion77.png)

Ihr Bildschirm sollte wie folgt aussehen:

![WF Fusion](./images/wffusion78.png)

Fügen Sie als Nächstes einen weiteren Knoten **Mehrere Variablen festlegen** hinzu.

![WF Fusion](./images/wffusion79.png)

Platzieren Sie sie nach dem Knoten **Photoshop-**:

![WF Fusion](./images/wffusion80.png)

Wählen Sie die **Festlegen mehreren Variablen** Knoten und wählen Sie Element hinzufügen **aus**. Wählen Sie den Variable Wert aus der Antwort des vorherigen Anfrage aus.

| Variablenname | Variablenwert |
|:-------------:| :---------------:| 
| `psdStatusUrl` | `data > _links > self > href` |

Wählen Sie **Hinzufügen** aus.

![WF Fusion](./images/wffusion81.png)

Klicken Sie **OK**.

![WF Fusion](./images/wffusion82.png)

Klicken Sie mit der rechten Maustaste auf das **Photoshop ändern Text** Knoten und wählen Sie Klonen **aus**.

![WF Fusion](./images/wffusion83.png)

Ziehen Sie die geklonte HTTP-Anfrage hinter die Festlegen mehreren Variablen **, die** Sie soeben erstellt Knoten.

![WF Fusion](./images/wffusion83.png)

Klicken Sie mit der rechten Maustaste auf die geklonte HTTP-Anfrage, wählen Sie **Umbenennen** und ändern Sie den Namen in **Photoshop-Prüfungsstatus**.

![WF Fusion](./images/wffusion84.png)

Wählen Sie aus, um die HTTP-Anfrage zu öffnen. Ändern Sie die URL so, dass sie auf die Variable verweist, die Sie im vorherigen Schritt erstellt haben, und setzen Sie **Methode** auf **GET**.

![WF Fusion](./images/wffusion85.png)

Entfernen Sie den **Hauptteil**, indem Sie die leere Option auswählen.

![WF Fusion](./images/wffusion86.png)

Klicken Sie **OK**.

![WF Fusion](./images/wffusion87.png)

Wählen Sie **Einmal ausführen** aus.

![WF Fusion](./images/wffusion88.png)

Eine Antwort, die das Feld **status** mit dem Status **running“**. Photoshop braucht einige Sekunden, um den Vorgang abzuschließen.

![WF Fusion](./images/wffusion89.png)

Da Sie nun wissen, dass die Antwort etwas mehr Zeit benötigt, um abgeschlossen zu werden, kann es eine gute Idee sein, vor dieser HTTP-Anfrage einen Timer hinzuzufügen, damit sie nicht sofort ausgeführt wird.

Wählen Sie den Knoten **Tools** und dann **Sleep** aus.

![WF Fusion](./images/wffusion90.png)

Positionieren Sie den **Sleep**-Knoten zwischen **Mehrere Variablen festlegen** und **Photoshop-**. Festlegen die **Verzögerung** auf **5** Sekunden. Klicken Sie **OK**.

![WF Fusion](./images/wffusion91.png)

Ihr Bildschirm sollte liken diesem aussehen. Die Herausforderung bei der folgenden Konfiguration besteht darin, dass 5 Sekunden Wartezeit ausreichen können, aber vielleicht nicht ausreichen. In Wirklichkeit wäre es besser, eine intelligentere Lösung zu haben, liken eine... while-Schleife, die den Status alle 5 Sekunden überprüft, **bis der Status erfolgreich ist**. Sie können also eine solche Taktik in den nächsten Schritten implementieren.

![WF Fusion](./images/wffusion92.png)

Wählen Sie das **Schraubenschlüssel**-Symbol zwischen **Mehrere Variablen festlegen** und **Schlaf** aus. Wählen Sie **Modul hinzufügen** aus.

![WF Fusion](./images/wffusion93.png)

Suchen Sie nach `flow` und wählen Sie **Flusssteuerung** aus.

![WF Fusion](./images/wffusion94.png)

Wählen Sie **Repeater** aus.

![WF Fusion](./images/wffusion95.png)

Setzen Sie **repeat** auf **20**. Klicken Sie **OK**.

![WF Fusion](./images/wffusion96.png)

Wählen Sie als Nächstes **+** auf der **Photoshop-** aus, um ein weiteres Modul hinzuzufügen.

![WF Fusion](./images/wffusion97.png)

Search für **den Fluss** und wählen Sie **&quot;Fluss Control**&quot;.

![WF Fusion](./images/wffusion98.png)

Wählen Sie **Array Aggregator** aus.

![WF Fusion](./images/wffusion99.png)

**Festlegen Quelle Modul** an Repeater **&#x200B;**. Wählen Sie **OK**.

![WF Fusion](./images/wffusion100.png)

Ihr Bildschirm sollte liken diesem aussehen:

![WF Fusion](./images/wffusion101.png)

Wählen Sie das **Schraubenschlüsselsymbol** aus und wählen Sie hinzufügen **eine Modul**.

![WF Fusion](./images/wffusion102.png)

Suchen Sie nach **tools** und wählen Sie **Tools** aus.

![WF Fusion](./images/wffusion103.png)

Wählen Sie **Mehrere Variablen abrufen**.

![WF Fusion](./images/wffusion104.png)

Wählen Sie **+ Element hinzufügen** und setzen Sie **Variablenname** auf `done`.

![WF Fusion](./images/wffusion105.png)

Wählen Sie **OK**.

![WF Fusion](./images/wffusion106.png)

Wählen Sie den Knoten **Mehrere Variablen festlegen** den Sie zuvor konfiguriert haben. Um die Variable zu initialisieren **Done** müssen Sie sie hier auf `false` setzen. Wählen Sie **+ Element hinzufügen**.

![WF Fusion](./images/wffusion107.png)

`done` für den **Variablennamen** verwenden

Zum Festlegen des Status ist ein boolescher Wert erforderlich. Um den booleschen Wert zu finden, wählen Sie **gear** und dann aus `false`. Wählen Sie **hinzufügen**.

![WF Fusion](./images/wffusion108.png)

Wählen Sie **OK**.

![WF Fusion](./images/wffusion109.png)

Wählen Sie als Nächstes das **Schraubenschlüssel**-Symbol nach dem **Abrufen mehrerer**&quot;, den Sie konfiguriert haben.

![WF Fusion](./images/wffusion110.png)

Wählen Sie **Filter einrichten** aus. Jetzt müssen Sie den Wert der Variablen (**)**. Wenn dieser Wert auf **false** gesetzt ist, muss der nächste Teil der Schleife ausgeführt werden. Wenn der Wert auf **true** festgelegt ist, bedeutet dies, dass der Prozess bereits erfolgreich abgeschlossen wurde, sodass es nicht erforderlich ist, mit dem nächsten Teil der Schleife fortzufahren.

![WF Fusion](./images/wffusion111.png)

Verwenden Sie für die Bezeichnung **Sind wir fertig?**. Legen Sie die **Bedingung** mithilfe der bereits vorhandenen Variable **Done** fest. Der Operator sollte auf **Gleich** festgelegt werden und der Wert sollte die boolesche Variable `false` sein. Klicken Sie **OK**.

![WF Fusion](./images/wffusion112.png)

Nehmen Sie als Nächstes etwas Platz zwischen den Knoten **Photoshop-** und **Array-Aggregator**. Klicken Sie dann auf das Symbol **Schraubenschlüssel** und wählen Sie **Router hinzufügen** aus. Dies liegt daran, dass es nach der Überprüfung des Status der Photoshop-Datei zwei Pfade geben sollte. Wenn der Status `succeeded` ist, sollte die Variable **done** auf `true` gesetzt werden. Wenn der Status nicht gleich `succeeded` ist, sollte die Schleife fortgesetzt werden. Der Router ermöglicht es, dies zu überprüfen und einzustellen.

![WF Fusion](./images/wffusion113.png)

Klicken Sie nach dem Hinzufügen des Routers auf das Symbol **Schraubenschlüssel** und wählen Sie **Filter einrichten** aus.

![WF Fusion](./images/wffusion114.png)

Verwenden Sie für die Bezeichnung **Wir sind fertig**. Festlegen die **Bedingung**, die die Antwort aus dem **Photoshop Überprüfen Sie Status** Knoten verwenden, indem Sie das Resposne-Feld **data.outputs.status**&#x200B;[] wählen, sollte der Operator auf **Gleich und der Wert auf gesetzt** werden`succeeded`. Klicken Sie **OK**.

![WF Fusion](./images/wffusion115.png)

Wählen Sie Weiter das leere Knoten mit dem Fragezeichen aus und suchen Sie nach **Werkzeugen**. Wählen Sie dann Werkzeuge **aus**.

![WF Fusion](./images/wffusion116.png)

Wählen Sie **Mehrere Variablen festlegen** aus.

![WF Fusion](./images/wffusion117.png)

Wenn diese Verzweigung des Routers verwendet wird, bedeutet dies, dass der Status der Photoshop Dateierstellung erfolgreich abgeschlossen wurde. Das bedeutet, dass die... while-Schleife muss den Status in Photoshop nicht mehr mehr überprüfen, daher sollten Sie die Variable `done` auf `true`festlegen.

Verwenden Sie für den **Variable** Namen .`done`

Für den **Variable Wert** sollten Sie den booleschen Wert `true`verwenden. Wählen Sie das **Zahnradsymbol** und dann aus `true`. Wählen Sie **hinzufügen**.

![WF Fusion](./images/wffusion118.png)

Wählen Sie **OK**.

![WF Fusion](./images/wffusion119.png)

Klicken Sie Weiter rechten Maustaste auf die **Festlegen mehrere Variablen**, Knoten Sie gerade erstellt haben, und wählen Sie Klonen **aus**.

![WF Fusion](./images/wffusion120.png)

Ziehen Sie das geklonte Knoten so, dass es mit dem **Array Aggregator** verbunden wird. Klicken Sie dann mit der rechten Maustaste auf die Knoten, wählen Sie Umbenennen **und ändern Sie** den Namen in `Placeholder End`.

![WF Fusion](./images/wffusion122.png)

Entfernen die vorhandene Variable und wählen Sie + hinzufügen Element **aus**. Verwenden Sie für den **Variable** Namen , verwenden Sie `end` `placeholder`für den **Variable Wert**. Wählen Sie **hinzufügen** und dann OK **aus**.

![WF Fusion](./images/wffusion123.png)

Wählen Sie **Speichern** aus, um Ihr Szenario zu speichern. Wählen Sie Weiter einmal ausführen **aus**.

![WF Fusion](./images/wffusion124.png)

Ihr Szenario wird ausgeführt und sollte erfolgreich Beenden. Beachten Sie, dass... while-Schleife, die Sie konfiguriert haben, funktioniert einwandfrei. In der folgenden Ausführung können Sie sehen, dass der **Repeater** 20 Mal ausgeführt wurde, basierend auf der Blase im **Werkzeuge > Get multiple variables** Knoten. Nach diesem Knoten haben Sie einen Filter konfiguriert, der den Status überprüft, und nur wenn der Status nicht gleich **erfolgreich** war, wurden die nächsten Knoten ausgeführt. In diesem Durchgang wurde das Teil nach dem Filter nur einmal ausgeführt, da der Status bereits **ersten Durchgang** erfolgreich“ war.

![WF Fusion](./images/wffusion125.png)

Sie können den Erstellungsstatus Ihrer neuen Photoshop-Datei überprüfen, indem Sie auf die Schaltfläche für die **HTTP-Anfrage zur** des Photoshops klicken und nach unten zum Feld **status** bohren.

![WF Fusion](./images/wffusion126.png)

Sie haben jetzt die Basisversion eines wiederholbaren Szenarios konfiguriert, das eine Reihe von Schritten automatisiert. In der nächsten Übung werden Sie dies durchlaufen, indem Sie Komplexität hinzufügen.

## Nächste Schritte

OK zur [Prozessautomatisierung mit Workfront Fusion](./ex3.md){target="_blank"}

Zurück zur [Creative-Workflow-Automatisierung mit Workfront Fusion](./automation.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
