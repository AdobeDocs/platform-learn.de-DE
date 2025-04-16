---
title: Automatisierung mithilfe von Connectoren
description: Automatisierung mithilfe von Connectoren
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 0b20ba91-28d4-4f4d-8abe-074f802c389e
source-git-commit: 003c0ff26183acbafbe745276bde6f90d5adef34
workflow-type: tm+mt
source-wordcount: '1722'
ht-degree: 1%

---

# 1.2.4 Automatisierung mithilfe von Connectoren

Sie verwenden jetzt die vordefinierten Connectoren in Workfront Fusion für Photoshop und verbinden die Firefly Text-2-Image-Anforderung und die Photoshop-Anforderungen in einem Szenario.

## 1.2.4.1 Duplizieren und Vorbereiten des Szenarios

Gehen Sie im linken Menü zu **Szenarien** und wählen Sie Ihre `--aepUserLdap--` aus. Anschließend sollte das zuvor erstellte Szenario mit dem Namen `--aepUSerLdap-- - Adobe I/O Authentication` angezeigt werden.

![WF Fusion](./images/wffc1.png)

Klicken Sie auf den Pfeil, um das Dropdown-Menü zu öffnen, und wählen Sie **Klonen**.

![WF Fusion](./images/wffc2.png)

Legen Sie **Name** des geklonten Szenarios auf `--aepUserLdap-- - Firefly + Photoshop` fest und wählen Sie das entsprechende **Target-Team**. Klicken Sie **Hinzufügen**, um einen neuen Webhook hinzuzufügen.

![WF Fusion](./images/wffc3.png)

Legen Sie den **Webhook-Namen** auf `--aepUserLdap-- - Firefly + Photoshop Webhook` fest. Klicken Sie auf **Speichern**.

![WF Fusion](./images/wffc4.png)

Sie sollten das dann sehen. Klicken Sie auf **Speichern**.

![WF Fusion](./images/wffc5.png)

Sie sollten das dann sehen. Klicken Sie auf **Knoten** Webhook“.

![WF Fusion](./images/wffc6.png)

Klicken Sie **Adresse in Zwischenablage kopieren** und dann auf **Datenstruktur neu bestimmen**.

![WF Fusion](./images/wffc7.png)

Öffnen Sie Postman. Fügen Sie eine neue Anfrage in demselben Ordner hinzu, den Sie zuvor verwendet haben.

![WF Fusion](./images/wffc9.png)

Stellen Sie sicher, dass die folgenden Einstellungen angewendet werden:

- Name der Anfrage: `POST - Send Request to Workfront Fusion Webhook Firefly + Photoshop`
- Anfragetyp: `POST`
- Anfrage-URL: Fügen Sie die URL ein, die Sie aus dem Webhook Ihres Workfront Fusion-Szenarios kopiert haben.

Wechseln Sie zu **body** und setzen Sie **body type** auf **raw** - **JSON**. Fügen Sie die folgende Payload in den **Hauptteil** ein.

```json
{
    "psdTemplate": "citisignal-fiber.psd",
    "xlsFile": "placeholder",
    "prompt":"misty meadows",
    "cta": "Buy this now!",
    "button": "Click here to buy!"
}
```

Diese neue Payload stellt sicher, dass alle Variableninformationen von außerhalb des Szenarios bereitgestellt werden, anstatt im Szenario hartcodiert zu werden. In einem Unternehmensszenario muss ein Szenario wiederverwendbar definiert werden, was bedeutet, dass eine Reihe von Variablen als Eingabevariablen bereitgestellt werden müssen, anstatt sie im Szenario hartcodiert zu haben.

Sie sollten dann diese haben. Klicken Sie auf **Senden**.

![WF Fusion](./images/wffc10.png)

Der Workfront Fusion-Webhook wartet noch auf Eingabe.

![WF Fusion](./images/wffc11.png)

Nachdem Sie auf **Senden** geklickt haben, sollte die Nachricht in **Erfolgreich ermittelt** geändert werden. Klicken Sie auf **OK**.

![WF Fusion](./images/wffc12.png)

## 1.2.4.2 Firefly T2I-Knoten aktualisieren

Klicken Sie auf den Knoten **Firefly T2I**. Sie sollten das dann sehen. Die Eingabeaufforderung in dieser Anfrage war zuvor hartcodiert **Pferde in einem Feld**. Sie entfernen nun diesen hartcodierten Text und ersetzen ihn durch ein Feld aus dem Webhook.

![WF Fusion](./images/wffcfft2i1.png)

Entfernen Sie den Text **Pferde in einem Feld** und ersetzen Sie ihn durch die Variable **prompt** die unter den **Webhook**-Variablen zu finden ist. Klicken Sie auf **OK**, um die Änderungen zu speichern.

![WF Fusion](./images/wffcfft2i2.png)

## 1.2.4.2 Ändern des Hintergrunds der PSD-Datei

Sie aktualisieren Ihr Szenario jetzt, um es durch die Verwendung von vorkonfigurierten Connectoren intelligenter zu gestalten. Sie werden auch die Ausgabe von Firefly mit Photoshop verbinden, damit sich das Hintergrundbild der PSD-Datei dynamisch ändert, indem Sie die Ausgabe der Aktion &quot;Firefly-Bild generieren“ verwenden.

In der vorherigen Übung hatten Sie die Route **Firefly T2I** deaktiviert. Sie sollten das jetzt rückgängig machen. Klicken Sie auf **stop**, um die Route wieder zu aktivieren.

![WF Fusion](./images/wffc13.png)

Sie werden dann sehen, dass das **Stopp**-Symbol verschwindet. Klicken Sie als Nächstes auf **Schraubenschlüssel**-Symbol auf der anderen Route zur Konfiguration der vorherigen Übung und wählen Sie **Route deaktivieren** aus.

![WF Fusion](./images/wffc14.png)

Sie sollten das dann sehen. Bewegen Sie als Nächstes den Mauszeiger über den Knoten **Firefly T2I** und klicken Sie auf das Symbol **+** .

![WF Fusion](./images/wffc15.png)

Geben Sie im Menü Suche den Befehl `Photoshop`und klicken Sie dann auf die Aktion **Adobe Photoshop**.

![WF Fusion](./images/wffc16.png)

Wählen **PSD-Bearbeitungen anwenden**.

![WF Fusion](./images/wffc17.png)

Sie sollten das dann sehen. Klicken Sie **Hinzufügen**, um eine neue Verbindung zu Adobe Photoshop hinzuzufügen.

![WF Fusion](./images/wffc18.png)

Konfigurieren Sie Ihre Verbindung wie folgt:

- Verbindungstyp: **Adobe Photoshop (Server-zu-Server) auswählen**
- Verbindungsname: `--aepUserLdap-- - Adobe IO` eingeben
- Client ID: Fügen Sie Ihre Client ID ein.
- Client-Geheimnis: Fügen Sie Ihr Client-Geheimnis ein.

Klicken Sie auf **Weiter**.

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

Scrollen Sie nach unten, bis Sie &quot;**&quot;**. Jetzt müssen Sie definieren, was in die Hintergrundebene eingefügt werden soll. In diesem Fall müssen Sie die Ausgabe des Firefly T2I-Objekts auswählen, das das dynamisch generierte Bild enthält.

Wählen **für** die Option **Extern** aus. Suchen Sie für **Dateispeicherort** die Variable `data.outputs[].image.url` in der Ausgabe der **Firefly T2I**-Anfrage und suchen Sie sie.

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

## 1.2.4.3 Ändern der Textebenen einer PSD-Datei

### Aktionsaufruf-Text

Bewegen Sie als Nächstes den Mauszeiger über den Knoten **Adobe Photoshop - PSD** Bearbeitungen anwenden und klicken Sie auf das Symbol **+** .

![WF Fusion](./images/wffc34.png)

**Adobe Photoshop**.

![WF Fusion](./images/wffc35.png)

Wählen Sie **Textebenen bearbeiten**.

![WF Fusion](./images/wffc36.png)

Sie sollten das dann sehen. Wählen Sie zunächst die zuvor bereits konfigurierte Adobe Photoshop-Verbindung aus, die `--aepUserLdap-- Adobe IO` benannt werden soll.

Jetzt müssen Sie den Speicherort der **Eingabedatei** definieren, die die Ausgabe des vorherigen Schritts ist, und unter **Ebenen** müssen Sie den **Namen** der Textebene eingeben, die Sie ändern möchten.

![WF Fusion](./images/wffc37.png)

Wählen Sie für **Eingabedatei** die Option **Azure** für **Eingabedateispeicherung** und stellen Sie sicher, dass Sie die Ausgabe aus der vorherigen Anforderung **Adobe Photoshop - PSD-Bearbeitungen anwenden** auswählen, die Sie hier übernehmen können: `data[]._links.renditions[].href`

![WF Fusion](./images/wffc37a.png)

Öffnen Sie die Datei **citsignal-fiber.psd**. In der Datei werden Sie feststellen, dass die Ebene, die den Aktionsaufruf enthält, **2048x2048-cta** heißt.

![WF Fusion](./images/wffc38.png)

Geben Sie den Namen **2048x2048-cta** unter **Name** im Dialogfeld ein.

![WF Fusion](./images/wffc39.png)

Scrollen Sie nach unten, bis **Text** > **Inhalt** angezeigt wird. Wählen Sie die Variable **cta** aus der Webhook-Payload aus.

![WF Fusion](./images/wffc40.png)

Scrollen Sie nach unten, bis Sie **Ausgabe** sehen. Wählen Sie **Speicher** die Option **Azure** aus. Geben Sie **Dateispeicherort** den folgenden Speicherort ein. Beachten Sie, dass dem Dateinamen die Variable `{{timestamp}}` hinzugefügt wurde. Dadurch wird sichergestellt, dass jede generierte Datei einen eindeutigen Namen hat. Legen Sie außerdem **Type** auf &quot;**.adobe.photoshop** fest. Klicken Sie auf **OK**.

`{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text-{{timestamp}}.psd{{1.AZURE_STORAGE_SAS_WRITE}}`

![WF Fusion](./images/wffc41.png)

### Schaltflächentext

Klicken Sie mit der rechten Maustaste auf den soeben erstellten Knoten und wählen Sie **Klonen**. Dadurch wird ein zweites ähnliches Objekt erstellt.

![WF Fusion](./images/wffc42.png)

Sie sollten das dann sehen. Wählen Sie zunächst die zuvor bereits konfigurierte Adobe Photoshop-Verbindung aus, die `--aepUserLdap-- Adobe IO` benannt werden soll.

Jetzt müssen Sie den Speicherort der **Eingabedatei** definieren, die die Ausgabe des vorherigen Schritts ist, und unter **Ebenen** müssen Sie den **Namen** der Textebene eingeben, die Sie ändern möchten.

![WF Fusion](./images/wffc43.png)

Wählen Sie für **Eingabedatei** die Option **Azure** für **Eingabedateispeicherung** und stellen Sie sicher, dass Sie die Ausgabe aus der vorherigen Anforderung **Adobe Photoshop - Textebenen bearbeiten** auswählen, die Sie hier verwenden können: `data[]._links.renditions[].href`

Öffnen Sie die Datei **citsignal-fiber.psd**. In der Datei werden Sie feststellen, dass die Ebene, die den Aktionsaufruf enthält, **2048x2048-button-text** heißt.

![WF Fusion](./images/wffc44.png)

Geben Sie den Namen **2048x2048-cta** unter **Name** im Dialogfeld ein.

![WF Fusion](./images/wffc43.png)

Scrollen Sie nach unten, bis **Text** > **Inhalt** angezeigt wird. Wählen Sie die Variable **cta** aus der Webhook-Payload aus.

![WF Fusion](./images/wffc45.png)

Scrollen Sie nach unten, bis Sie **Ausgabe** sehen. Wählen Sie **Speicher** die Option **Azure** aus. Geben Sie **Dateispeicherort** den folgenden Speicherort ein. Beachten Sie, dass dem Dateinamen die Variable `{{timestamp}}` hinzugefügt wurde. Dadurch wird sichergestellt, dass jede generierte Datei einen eindeutigen Namen hat. Legen Sie außerdem **Type** auf &quot;**.adobe.photoshop** fest. Klicken Sie auf **OK**.

`{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text-{{timestamp}}.psd{{1.AZURE_STORAGE_SAS_WRITE}}`

![WF Fusion](./images/wffc46.png)

Klicken Sie **Speichern**, um Ihre Änderungen zu speichern.

![WF Fusion](./images/wffc47.png)

## Webhook-Antwort 1.2.4.4

Nachdem Sie diese Änderungen auf Ihre Photoshop-Datei angewendet haben, müssen Sie jetzt eine „Webhook **Antwort“ konfigurieren** die an die Anwendung zurückgesendet wird, die dieses Szenario aktiviert hat.

Bewegen Sie den Mauszeiger über den Knoten **Adobe Photoshop - Textebenen bearbeiten** klicken Sie auf das Symbol **+** .

![WF Fusion](./images/wffc48.png)

Suchen Sie nach **Webhook** und wählen Sie **Webhook** aus.

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

Wählen Sie den Pfad `data[]._links.renditions[].href` aus der Ausgabe der vorherigen Anfrage aus. Aktivieren Sie das Kontrollkästchen für **Erweiterte Einstellungen anzeigen** und klicken Sie dann auf **Element hinzufügen**.

![WF Fusion](./images/wffc52.png)

Geben Sie im Feld **Schlüssel** `Content-Type` ein. Geben Sie im Feld **Wert** `application/json` ein. Klicken Sie auf **Speichern**.

![WF Fusion](./images/wffc52a.png)

Sie sollten dann diese haben. Klicken Sie auf **OK**.

![WF Fusion](./images/wffc53.png)

Klicken Sie **Automatisch ausrichten**.

![WF Fusion](./images/wffc54.png)

Sie sollten das dann sehen. Klicken Sie **Einmal ausführen**.

![WF Fusion](./images/wffc55.png)

Gehen Sie zurück zu Postman und klicken Sie auf **Senden**. Die hier verwendete Eingabeaufforderung lautet **Misty Meadows**.

![WF Fusion](./images/wffc56.png)

Anschließend wird das Szenario aktiviert und nach einiger Zeit wird in Postman eine Antwort angezeigt, die die URL der neu erstellten PSD-Datei enthält.

![WF Fusion](./images/wffc58.png)

Zur Erinnerung: Sobald das Szenario in Workfront Fusion ausgeführt wurde, können Sie Informationen zu den einzelnen Knoten anzeigen, indem Sie auf die Sprechblase über jedem Knoten klicken.

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

Navigieren Sie zu [1.2.5 Frame.io und Workfront Fusion](./ex5.md){target="_blank"}

Zurück zur [Creative-Workflow-Automatisierung mit Workfront Fusion](./automation.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
