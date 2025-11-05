---
title: Automatisierung mithilfe von Connectoren
description: Automatisierung mithilfe von Connectoren
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 0b20ba91-28d4-4f4d-8abe-074f802c389e
source-git-commit: c9807ef0787f4390d12bc7285cfe71260aa3eabf
workflow-type: tm+mt
source-wordcount: '1991'
ht-degree: 1%

---

# 1.2.4 Automatisierung mithilfe von Connectoren

Sie verwenden jetzt die vordefinierten Connectoren in Workfront Fusion für Photoshop und verbinden die Firefly Text-2-Image-Anforderung und die Photoshop-Anforderungen in einem Szenario.

## 1.2.4.1 Variablen aktualisieren

Bevor Sie mit der Connector-Einrichtung fortfahren, müssen die folgenden Variablen zum Modul **Initialize Constants** hinzugefügt werden.

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

Gehen Sie zurück zu Ihrem ersten Knoten, wählen Sie **Konstanten initialisieren** und wählen Sie dann **Element hinzufügen** für jede dieser Variablen aus.

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

Ihr Bildschirm sollte wie folgt aussehen. Klicken Sie **OK**.

![WF Fusion](./images/wffusion68.png)

## 1.2.4.2 Aktivieren Ihres Szenarios mithilfe eines Webhooks

Bisher haben Sie Ihr Szenario zum Testen manuell ausgeführt. Aktualisieren wir nun Ihr Szenario mit einem Webhook, damit es von einer externen Umgebung aus aktiviert werden kann.

Wählen Sie **+** aus, suchen Sie nach **Webhook** und wählen Sie dann **Webhooks** aus.

![WF Fusion](./images/wffusion216.png)

Wählen Sie **Benutzerdefinierter Webhook** aus.

![WF Fusion](./images/wffusion217.png)

Ziehen Sie das **Benutzerdefinierter Webhook**-Modul an den Anfang Ihres Szenarios. Wählen Sie als Nächstes das **Uhr**-Symbol aus und ziehen Sie es auf das Modul **Benutzerdefinierter Webhook**.

![WF Fusion](./images/wffusion217a.png)

Sie sollten das dann sehen. Ziehen Sie als Nächstes den roten Punkt auf dem ersten Modul in Richtung des lilafarbenen Punkts auf dem zweiten Modul.

![WF Fusion](./images/wffusion217b.png)

Sie sollten das dann sehen. Klicken Sie anschließend auf das Modul **Benutzerdefinierter Webhook**.

![WF Fusion](./images/wffusion217c.png)

Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion218.png)

Legen Sie den **Webhook-Namen** auf `--aepUserLdap-- - Firefly + Photoshop Webhook` fest. Klicken Sie auf **Speichern**.

![WF Fusion](./images/wffusion219.png)

Ihre Webhook-URL ist jetzt verfügbar. Klicken Sie auf **Adresse in Zwischenablage kopieren**, um die URL zu kopieren.

![WF Fusion](./images/wffusion221.png)

Öffnen Sie Postman und fügen Sie einen neuen Ordner in der Sammlung **FF - Firefly Services Tech Insiders** hinzu.

![WF Fusion](./images/wffusion222.png)

Benennen Sie den Ordner `--aepUserLdap-- - Workfront Fusion`.

![WF Fusion](./images/wffusion223.png)

Wählen Sie in dem soeben erstellten Ordner die 3 Punkte **…** und dann **Anfrage hinzufügen**.

![WF Fusion](./images/wffusion224.png)

Legen Sie den **Methodentyp** auf **POST** fest und fügen Sie die URL Ihres Webhooks in die Adressleiste ein.

![WF Fusion](./images/wffusion225.png)

Sie müssen einen benutzerdefinierten Hauptteil senden, damit die Variablenelemente von einer externen Quelle für Ihr Workfront Fusion-Szenario bereitgestellt werden können.

Wechseln Sie zu **Textkörper** und wählen Sie **Roh** aus.

![WF Fusion](./images/wffusion226.png)

Fügen Sie den folgenden Text in den Textkörper Ihrer Anfrage ein. Wählen Sie **Senden** aus.

```json
{
    "psdTemplate": "citisignal-fiber.psd",
    "xlsFile": "placeholder",
    "prompt":"misty meadows",
    "cta": "Buy this now!",
    "button": "Click here to buy!"
}
```

![WF Fusion](./images/wffusion229.png)

Zurück in Workfront Fusion wird eine Meldung auf Ihrem benutzerdefinierten Webhook angezeigt, die lautet: **Erfolgreich ermittelt**.

![WF Fusion](./images/wffusion227.png)

## Adobe Firefly-Connector 1.2.4.3

Klicken Sie auf das Symbol **+** , um ein neues Modul hinzuzufügen.

![WF Fusion](./images/wffcff2.png)

Geben Sie den Suchbegriff `Adobe Firefly` ein und wählen Sie dann **Adobe Firefly**.

![WF Fusion](./images/wffcff2a.png)

Wählen Sie **Bild erstellen** aus.

![WF Fusion](./images/wffcff3.png)

Klicken Sie auf das **Adobe Firefly**-Modul, um es zu öffnen, und klicken Sie dann auf **Hinzufügen**, um eine neue Verbindung zu erstellen.

![WF Fusion](./images/wffcff5.png)

Füllen Sie die folgenden Felder aus:

- **Verbindungsname**: Verwenden Sie `--aepUserLdap-- - Firefly connection`.
- **Umgebung**: Verwenden Sie **Produktion**.
- **Type**: verwenden **Persönliches Konto**.
- **Client-ID**: Kopieren Sie die **Client-ID** aus Ihrem Adobe I/O-Projekt mit dem Namen `--aepUserLdap-- - One Adobe tutorial`.
- **Client-Geheimnis**: Kopieren Sie das **Client-Geheimnis** aus Ihrem Adobe I/O-Projekt mit dem Namen `--aepUserLdap-- - One Adobe tutorial`.

Die **Client-ID** und **Client-Geheimnis** Ihres Adobe I/O-Projekts finden Sie [hier](https://developer.adobe.com/console/projects.){target="_blank"}.

![WF Fusion](./images/wffc20.png)

Nachdem Sie alle Felder ausgefüllt haben, klicken Sie auf **Weiter**. Ihre Verbindung wird dann automatisch validiert.

![WF Fusion](./images/wffcff6.png)

Wählen Sie als Nächstes die Variable **Eingabeaufforderung** aus, die dem Szenario vom eingehenden **benutzerdefinierten Webhook“ bereitgestellt**.

![WF Fusion](./images/wffcff7.png)

Setzen Sie **Modellversion** **prompt** auf **image4 standard**. Klicken Sie auf **OK**.

![WF Fusion](./images/wffcff7b.png)

Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern, und klicken Sie dann auf **Einmal ausführen**, um Ihre Konfiguration zu testen.

![WF Fusion](./images/wffcff8.png)

Wechseln Sie zu Postman, überprüfen Sie die Eingabeaufforderung in Ihrer Anfrage und klicken Sie dann auf **Senden**.

![WF Fusion](./images/wffcff8a.png)

Nachdem Sie auf Senden geklickt haben, gehen Sie zurück zu Workfront Fusion und klicken Sie auf das Blasensymbol im Modul **Adobe Firefly**, um die Details zu überprüfen.

![WF Fusion](./images/wffcff9.png)

Navigieren Sie **AUSGABE** zu **Details** > **url**, um die URL des von **Adobe Firefly generierten Bildes** finden.

![WF Fusion](./images/wffcff10.png)

Kopieren Sie die URL und fügen Sie sie in Ihren Browser ein. Jetzt sollte ein Bild angezeigt werden, das die von der Postman-Anfrage gesendete Eingabeaufforderung darstellt, in diesem Fall **Misty Meadows**.

![WF Fusion](./images/wffcff11.png)

## 1.2.4.2 Ändern des Hintergrunds der PSD-Datei

Sie aktualisieren Ihr Szenario jetzt, um es durch die Verwendung von mehr vorkonfigurierten Connectoren intelligenter zu gestalten. Sie werden auch die Ausgabe von Firefly mit Photoshop verbinden, damit sich das Hintergrundbild der PSD-Datei dynamisch ändert, indem Sie die Ausgabe der Aktion &quot;Firefly-Bild generieren“ verwenden.

Sie sollten das dann sehen. Bewegen Sie als Nächstes den Mauszeiger über das Modul **Adobe Firefly** und klicken Sie auf das Symbol **+** .

![WF Fusion](./images/wffc15.png)

Geben Sie im Suchmenü `Photoshop` ein und klicken Sie dann auf die Aktion **Adobe Photoshop**.

![WF Fusion](./images/wffc16.png)

Wählen **PSD-Bearbeitungen anwenden**.

![WF Fusion](./images/wffc17.png)

Sie sollten das dann sehen. Klicken Sie **Hinzufügen**, um eine neue Verbindung zu Adobe Photoshop hinzuzufügen.

![WF Fusion](./images/wffc18.png)

Konfigurieren Sie Ihre Verbindung wie folgt:

- Verbindungstyp: **Adobe Photoshop (Server-zu-Server) auswählen**
- Verbindungsname: `--aepUserLdap-- - Adobe I/O` eingeben
- Client ID: Fügen Sie Ihre Client ID ein.
- Client-Geheimnis: Fügen Sie Ihr Client-Geheimnis ein.

Klicken Sie auf **Fortfahren**.

![WF Fusion](./images/wffc19.png)

Um Ihre **Client-ID** und Ihr **Client-Geheimnis** zu finden, navigieren Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"} und öffnen Sie Ihr Adobe I/O-Projekt mit dem Namen `--aepUserLdap-- One Adobe tutorial`. Wechseln Sie zu **OAuth Server-zu-Server**, um Ihre Client-ID und Ihr Client-Geheimnis zu finden. Kopieren Sie diese Werte und fügen Sie sie in die Verbindungseinrichtung in Workfront Fusion ein.

![WF Fusion](./images/wffc20.png)

Nachdem Sie auf **Weiter** geklickt haben, wird ein Popup-Fenster angezeigt, während Ihre Anmeldeinformationen überprüft werden. Sobald Sie fertig sind, sollten Sie dies sehen.

![WF Fusion](./images/wffc21.png)

Jetzt müssen Sie den Dateispeicherort der PSD-Datei eingeben, mit der Fusion arbeiten soll. Wählen **für** Speicher **die Option Azure** und geben Sie für **Dateispeicherort** `{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/{{1.AZURE_STORAGE_SAS_READ}}` ein. Platzieren Sie den Cursor neben die zweite `/`. Sehen Sie sich dann die verfügbaren Variablen an und scrollen Sie nach unten, um die Variable **psdTemplate** zu finden. Klicken Sie auf die Variable **psdTemplate**, um sie auszuwählen.

![WF Fusion](./images/wffc22.png)

Sie sollten das dann sehen.

![WF Fusion](./images/wffc23.png)

Scrollen Sie ganz nach unten, bis Sie „Ebenen **sehen**. Klicken Sie **Element hinzufügen**.

![WF Fusion](./images/wffc24.png)

Sie sollten das dann sehen. Jetzt müssen Sie den Namen der Ebene in Ihrer Photoshop PSD-Vorlage eingeben, die für den Hintergrund der Datei verwendet wird.

![WF Fusion](./images/wffc25.png)

In der Datei **citsignal-fiber.psd** finden Sie die Ebene, die für den Hintergrund verwendet wird. In diesem Beispiel erhält diese Ebene den Namen **2048x2048-background**.

![WF Fusion](./images/wffc26.png)

Fügen Sie den Namen **2048x2048-background** in das Dialogfeld &quot;Workfront Fusion“ ein.

![WF Fusion](./images/wffc27.png)

Scrollen Sie nach unten, bis Sie &quot;**&quot;**. Jetzt müssen Sie definieren, was in die Hintergrundebene eingefügt werden soll. In diesem Fall müssen Sie die Ausgabe des Moduls **Adobe Firefly** auswählen, das das dynamisch generierte Bild enthält.

Wählen **für** die Option **Extern** aus. Für **Dateispeicherort** müssen Sie die Variable `{{XX.details[].url}}` aus der Ausgabe des **Adobe Firefly**-Moduls kopieren und einfügen, aber Sie müssen **XX** in der Variablen durch die Sequenznummer des **Adobe Firefly**-Moduls ersetzen, die in diesem Beispiel **5** lautet.

![WF Fusion](./images/wffc28.png)

Scrollen Sie dann nach unten, bis Sie **Bearbeiten** sehen. Legen Sie **Bearbeiten** auf **Ja** und **Typ** auf **Layer** fest. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffc29.png)

Sie sollten das dann sehen. Als Nächstes müssen Sie die Ausgabe der Aktion definieren. Klicken Sie **Element hinzufügen** unter **Ausgaben**.

![WF Fusion](./images/wffc30.png)

Wählen Sie **Azure** für **Storage** aus, fügen Sie diesen `{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-replacedbg.psd{{1.AZURE_STORAGE_SAS_WRITE}}` unter **File Location** ein und wählen Sie **vnd.adobe.photoshop** unter **Type**. Klicken, um **Erweiterte Einstellungen anzeigen** zu aktivieren.

![WF Fusion](./images/wffc31.png)

Wählen **unter „Erweiterte**&quot; die Option **Ja**, um Dateien mit demselben Namen zu überschreiben.
Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffc32.png)

Sie sollten dann diese haben. Klicken Sie auf **OK**.

![WF Fusion](./images/wffc33.png)

Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern, und klicken Sie dann auf **Einmal ausführen**, um Ihre Konfiguration zu testen.

![WF Fusion](./images/wffc33a.png)

Wechseln Sie zu Postman, überprüfen Sie die Eingabeaufforderung in Ihrer Anfrage und klicken Sie dann auf **Senden**.

![WF Fusion](./images/wffcff8a.png)

Sie sollten das dann sehen. Klicken Sie auf den Kreis im Modul **Adobe Photoshop - PSD-Bearbeitungen anwenden**.

![WF Fusion](./images/wffc33b.png)

Sie können jetzt sehen, dass erfolgreich eine neue PSD-Datei generiert und in Ihrem Microsoft Azure-Speicherkonto gespeichert wurde.

![WF Fusion](./images/wffc33c.png)

## 1.2.4.3 Ändern der Textebenen einer PSD-Datei

Bewegen Sie als Nächstes den Mauszeiger über das Modul **Adobe Photoshop - PSD** Bearbeitungen anwenden und klicken Sie auf das Symbol **+** .

![WF Fusion](./images/wffc34.png)

**Adobe Photoshop**.

![WF Fusion](./images/wffc35.png)

Wählen Sie **Textebenen bearbeiten**.

![WF Fusion](./images/wffc36.png)

Sie sollten das dann sehen. Wählen Sie zunächst die zuvor bereits konfigurierte Adobe Photoshop-Verbindung aus, die `--aepUserLdap-- Adobe I/O` benannt werden soll.

![WF Fusion](./images/wffc37.png)

Wählen Sie für **Eingabedatei** die Option **Azure** für **Eingabedateispeicherung** und stellen Sie sicher, dass Sie die Ausgabe aus der vorherigen Anforderung **Adobe Photoshop - PSD-Bearbeitungen anwenden** auswählen, die Sie wie folgt definieren können: ``{{XX.data[].`_links`.renditions[].href}}`` (ersetzen Sie XX durch die Sequenznummer des vorherigen Moduls Adobe Photoshop - PSD-Bearbeitungen anwenden).

Klicken Sie anschließend auf **+Element hinzufügen** unter **Ebenen**, um mit dem Hinzufügen der Textebenen zu beginnen, die aktualisiert werden müssen.

![WF Fusion](./images/wffc37a.png)

Es sind zwei Änderungen vorzunehmen. Der CTA-Text und der Schaltflächentext in der Datei **Citisignal-fiber.psd** müssen aktualisiert werden.

Um die Ebenennamen zu finden, öffnen Sie die Datei &quot;**-fiber.psd**. In der Datei werden Sie feststellen, dass die Ebene, die die call to action enthält, **2048x2048-cta** heißt.

![WF Fusion](./images/wffc38.png)

In der Datei **citsignal-fiber.psd** werden Sie auch feststellen, dass die Ebene, die die call to action enthält, **2048x2048-button-text** heißt.

![WF Fusion](./images/wffc44.png)

Zunächst müssen Sie die Änderungen konfigurieren, die an der Ebene (2048x2048 **cta) vorgenommen** müssen. Geben Sie den Namen **2048x2048-cta** unter **Name** im Dialogfeld ein.

![WF Fusion](./images/wffc39.png)

Scrollen Sie nach unten, bis **Text** > **Inhalt** angezeigt wird. Wählen Sie die Variable **cta** aus der Webhook-Payload aus. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffc40.png)

Sie sollten das dann sehen. Klicken Sie auf **+Element hinzufügen** unter **Ebenen**, um mit dem Hinzufügen der nächsten Textebene zu beginnen, die aktualisiert werden muss.

![WF Fusion](./images/wffc40a.png)

Geben Sie den Namen **2048x2048-button-text** unter **Name** im Dialogfeld ein.

![WF Fusion](./images/wffc40b.png)

Scrollen Sie nach unten, bis **Text** > **Inhalt** angezeigt wird. Wählen Sie die Variable **Schaltfläche** aus der Webhook-Payload aus. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffc40c.png)

Sie sollten das dann sehen.

![WF Fusion](./images/wffc40d.png)

Scrollen Sie nach unten, bis Sie **Ausgabe** sehen. Wählen Sie **Speicher** die Option **Azure** aus. Geben Sie **Dateispeicherort** den folgenden Speicherort ein. Beachten Sie, dass dem Dateinamen die Variable `{{timestamp}}` hinzugefügt wurde. Dadurch wird sichergestellt, dass jede generierte Datei einen eindeutigen Namen hat. Legen Sie außerdem **Type** auf &quot;**.adobe.photoshop** fest.

`{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text-{{timestamp}}.psd{{1.AZURE_STORAGE_SAS_WRITE}}`

Legen Sie **Type** auf **vnd.adobe.photoshop** fest. Klicken Sie auf **OK**.

![WF Fusion](./images/wffc41.png)

Klicken Sie **Speichern**, um Ihre Änderungen zu speichern.

![WF Fusion](./images/wffc47.png)

## Webhook-Antwort 1.2.4.4

Nachdem Sie diese Änderungen auf Ihre Photoshop-Datei angewendet haben, müssen Sie jetzt eine „Webhook **Antwort“ konfigurieren** die an die Anwendung zurückgesendet wird, die dieses Szenario aktiviert hat.

Bewegen Sie den Mauszeiger über das Modul **Adobe Photoshop - Textebenen bearbeiten** klicken Sie auf das Symbol **+** .

![WF Fusion](./images/wffc48.png)

Suchen Sie nach `webhooks` und wählen Sie **Webhook**.

![WF Fusion](./images/wffc49.png)

Wählen Sie **Webhook-Antwort** aus.

![WF Fusion](./images/wffc50.png)

Sie sollten das dann sehen. Fügen Sie die folgende Payload in &quot;**&quot;**.

```json
{
    "newPsdTemplate": ""
}
```

![WF Fusion](./images/wffc51.png)

Kopieren Sie die Variable `{{XX.data[]._links.renditions[].href}}` und fügen Sie sie ein. Ersetzen **XX** durch die Sequenznummer des letzten **Adobe Photoshop -**-Moduls, in diesem Fall **7**.

![WF Fusion](./images/wffc52.png)

Aktivieren Sie das Kontrollkästchen für **Erweiterte Einstellungen anzeigen** und klicken Sie dann auf **Element hinzufügen**.

![WF Fusion](./images/wffc52b.png)

Geben Sie im Feld **Schlüssel** `Content-Type` ein. Geben Sie im Feld **Wert** `application/json` ein. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffc52a.png)

Sie sollten dann diese haben. Klicken Sie auf **OK**.

![WF Fusion](./images/wffc53.png)

Klicken Sie **Automatisch ausrichten**.

![WF Fusion](./images/wffc54.png)

Sie sollten das dann sehen. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern, und klicken Sie dann auf **Einmal ausführen**, um Ihr Szenario zu testen.

![WF Fusion](./images/wffc55.png)

Gehen Sie zurück zu Postman und klicken Sie auf **Senden**. Die hier verwendete Eingabeaufforderung lautet **Misty Meadows**.

![WF Fusion](./images/wffc56.png)

Anschließend wird das Szenario aktiviert und nach einiger Zeit wird in Postman eine Antwort angezeigt, die die URL der neu erstellten PSD-Datei enthält.

![WF Fusion](./images/wffc58.png)

Zur Erinnerung: Sobald das Szenario in Workfront Fusion ausgeführt wurde, können Sie Informationen zu den einzelnen Modulen anzeigen, indem Sie auf die Sprechblase über jedem Modul klicken.

![WF Fusion](./images/wffc59.png)

Mit Azure Storage Explorer können Sie dann die neu erstellte PSD-Datei suchen und öffnen, indem Sie in Azure Storage Explorer darauf doppelklicken.

![WF Fusion](./images/wffc60.png)

Ihre Datei sollte dann wie folgt aussehen, mit dem Hintergrund, der durch einen Hintergrund mit &quot;**Wiesen“ ersetzt**.

![WF Fusion](./images/wffc61.png)

Wenn Sie Ihr Szenario erneut ausführen und dann eine neue Anfrage aus Postman mit einer anderen Eingabeaufforderung senden, werden Sie sehen, wie einfach und wiederverwendbar Ihr Szenario geworden ist. In diesem Beispiel ist die neue Eingabeaufforderung (Sunny **)**.

![WF Fusion](./images/wffc62.png)

Und ein paar Minuten später wurde eine neue PSD-Datei mit neuem Hintergrund erstellt.

![WF Fusion](./images/wffc63.png)

## Nächste Schritte

Navigieren Sie zu [1.2.3 Frame.io und Workfront Fusion](./ex3.md){target="_blank"}

Zurück zur [Creative-Workflow-Automatisierung mit Workfront Fusion](./automation.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
