---
title: Erste Schritte mit Firefly-Services
description: Erste Schritte mit Firefly-Services
kt: 5342
doc-type: tutorial
exl-id: 1b7b2630-864f-4982-be5d-c46b760739c3
source-git-commit: 0fe4bbf6bcc80d4fa88bc30718a1de6621f93f17
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 0%

---

# 1.2.3 Prozessautomatisierung mit Workfront Fusion

Ihr Szenario sieht nun wie folgt aus:

![WF Fusion](./images/wffusion200.png)

## Iteration über mehrere Werte 1.2.3.1

Bisher haben Sie Text in einer Photoshop-Datei um einen statischen Wert geändert. Um Ihre Workflows zur Inhaltserstellung zu skalieren und zu automatisieren, müssen Sie eine Liste von Werten durchlaufen und diese Werte dynamisch in die Photoshop-Datei einfügen. In den nächsten Schritten fügen Sie hinzu, dass in Ihrem vorhandenen Szenario die Werte durchlaufen werden sollen.

Klicken Sie zwischen dem Knoten **Router** und dem Knoten **Photoshop Change Text** auf das Symbol **Schraubenschlüssel** und wählen Sie **Modul hinzufügen**.

![WF Fusion](./images/wffusion201.png)

Suchen Sie nach `flow` und wählen Sie **Flusssteuerung** aus.

![WF Fusion](./images/wffusion202.png)

Wählen Sie **Iterator** aus.

![WF Fusion](./images/wffusion203.png)

Sie sollten dann diese haben.

![WF Fusion](./images/wffusion204.png)

Es ist zwar möglich, Eingabedateien wie CSV-Dateien zu lesen, aber Sie müssen zunächst eine einfache Version einer CSV-Datei verwenden, indem Sie eine Textzeichenfolge definieren und diese Textdatei aufteilen.

Die Funktion **Aufspaltung** finden Sie, indem Sie auf das Symbol **T** klicken, wo alle verfügbaren Funktionen zum Bearbeiten von Textwerten angezeigt werden. Klicken Sie auf **Funktion** Aufspaltung“, und Sie sollten dies dann sehen.

![WF Fusion](./images/wffusion206.png)

Die Aufspaltungsfunktion erwartet ein Array von Werten vor dem Semikolon und erwartet, dass Sie das Trennzeichen nach dem Semikolon angeben. Für diesen Test sollten Sie ein einfaches Array mit zwei Feldern verwenden: **Jetzt kaufen** und **Hier klicken** und das zu verwendende Trennzeichen ist **,**.

Geben Sie dies in das Feld **Array** ein, indem Sie die derzeit leere Funktion **split** ersetzen: `{{split("Buy now, Click here "; ",")}}`. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion205.png)

Ihr Iterator ist jetzt konfiguriert, und wenn Sie Ihr Szenario jetzt ausführen würden, würde er es zweimal ausführen. Es gibt jedoch noch ein Problem, da Sie derzeit statische Werte in Ihrem **Photoshop-Änderungstext**-Knoten verwenden. Klicken Sie auf **Photoshop**&#x200B;Änderungstext, um für die Eingabe- und Ausgabefelder einige Variablen anstelle von statischen Werten hinzuzufügen.

![WF Fusion](./images/wffusion207.png)

Im **Inhalt anfragen** wird der Text angezeigt (**hier klicken**. Dieser Text muss durch die Werte aus Ihrem -Array ersetzt werden.

![WF Fusion](./images/wffusion208.png)

Löschen Sie den Text **Hier klicken** und ersetzen Sie ihn, indem Sie die Variable **Wert** im Knoten **Iterator** auswählen. Dadurch wird sichergestellt, dass der Text auf der Schaltfläche in Ihrem Photoshop-Dokument dynamisch aktualisiert wird.

![WF Fusion](./images/wffusion209.png)

Sie müssen auch den Dateinamen aktualisieren, der zum Schreiben der Datei in Ihr Azure-Speicherkonto verwendet wird. Wenn der Dateiname statisch ist, überschreibt jede neue Iteration einfach die vorherige Datei und als solche verlieren Sie die angepassten Dateien. Der aktuelle statische Dateiname lautet **sevoi-psd-changed-text.psd**, und Sie müssen ihn jetzt aktualisieren. Setzen Sie den Cursor hinter das Wort `text`.

![WF Fusion](./images/wffusion210.png)

Fügen Sie zunächst einen `-` mit Bindestrichen hinzu und wählen Sie dann den Wert **Bundle Order Position**. Dadurch wird sichergestellt, dass Workfront Fusion bei der ersten Iteration `-1` zum Dateinamen hinzufügt, bei der zweiten Iteration `-2`. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion211.png)

Speichern Sie Ihr Szenario und klicken Sie dann auf **Einmal ausführen**.

![WF Fusion](./images/wffusion212.png)

Sobald das Szenario ausgeführt wurde, kehren Sie zu Ihrem Azure Storage-Explorer zurück und aktualisieren Sie den Ordner . Anschließend sollten die beiden neu erstellten Dateien angezeigt werden.

![WF Fusion](./images/wffusion213.png)

Laden Sie jede Datei herunter und öffnen Sie sie. Sie sollten dann die verschiedenen Texte auf den Schaltflächen sehen. Dies ist die Datei `sevoi-psd-changed-text-1.psd`.

![WF Fusion](./images/wffusion214.png)

Dies ist die Datei `sevoi-psd-changed-text-2.psd`.

![WF Fusion](./images/wffusion215.png)

## 1.2.3.2 des aktiven Szenarios mithilfe eines Webhooks

Bisher haben Sie Ihr Szenario zum Testen manuell ausgeführt. Aktualisieren wir nun Ihr Szenario mit einem Webhook, damit es von einer externen Umgebung aus aktiviert werden kann.

Klicken Sie auf das Symbol **+**, suchen Sie nach **Webhook** und wählen Sie **Webhooks** aus.

![WF Fusion](./images/wffusion216.png)

Wählen Sie **Benutzerdefinierter Webhook** aus.

Ziehen Sie den Knoten **Benutzerdefinierter Webhook** und verbinden Sie ihn, sodass er eine Verbindung mit dem ersten Knoten auf der Arbeitsfläche herstellt, der **Initialisierungskonstanten“**.

![WF Fusion](./images/wffusion217.png)

Klicken Sie auf **Knoten** Benutzerdefinierter Webhook“. Klicken Sie dann auf **Hinzufügen**.

![WF Fusion](./images/wffusion218.png)

Legen Sie den **Webhook-Namen** auf `--aepUserLdap-- - Tutorial 1.2` fest.

![WF Fusion](./images/wffusion219.png)

Aktivieren Sie das Kontrollkästchen für **Anfrage-Header abrufen**. Klicken Sie auf **Speichern**.

![WF Fusion](./images/wffusion220.png)

Ihre Webhook-URL ist jetzt verfügbar. Kopieren Sie die URL.

![WF Fusion](./images/wffusion221.png)

Öffnen Sie Postman und fügen Sie einen neuen Ordner in der Sammlung **FF - Firefly Services Tech Insiders** hinzu.

![WF Fusion](./images/wffusion222.png)

Benennen Sie den Ordner `--aepUserLdap-- - Workfront Fusion`.

![WF Fusion](./images/wffusion223.png)

Klicken Sie in dem soeben erstellten Ordner auf die 3 Punkte **…** und wählen Sie **Anfrage hinzufügen**.

![WF Fusion](./images/wffusion224.png)

Legen Sie **Methodentyp** auf **POST fest** fügen Sie die URL Ihres Webhooks in die Adressleiste ein.

![WF Fusion](./images/wffusion225.png)

Sie müssen einen benutzerdefinierten Hauptteil senden, damit die Variablenelemente von einer externen Quelle für Ihr Workfront Fusion-Szenario bereitgestellt werden können. Wechseln Sie zu **Textkörper** und wählen Sie **Roh** aus.

![WF Fusion](./images/wffusion226.png)

Fügen Sie den folgenden Text in den Textkörper Ihrer Anfrage ein. Klicken Sie auf **Senden**.

```json
{
    "psdTemplate": "placeholder",
    "xlsFile": "placeholder"
}
```

![WF Fusion](./images/wffusion229.png)

Zurück zu Workfront Fusion. Im Webhook wird jetzt eine Meldung angezeigt, die lautet: **Erfolgreich ermittelt**.

![WF Fusion](./images/wffusion227.png)

Klicken Sie auf **Speichern** und dann auf **Einmal ausführen**. Ihr Szenario ist jetzt aktiv, wird aber erst ausgeführt, wenn Sie in Postman erneut **Senden** klicken.

![WF Fusion](./images/wffusion230.png)

Wechseln Sie zu Postman und klicken Sie erneut **Senden**.

![WF Fusion](./images/wffusion228.png)

Ihr Szenario wird dann erneut ausgeführt und die beiden Dateien werden wie zuvor erstellt.

![WF Fusion](./images/wffusion232.png)

Bevor Sie fortfahren, ändern Sie den Namen Ihrer Postman-Anfrage in `POST - Send Request to Workfront Fusion Webhook`.

![WF Fusion](./images/wffusion233.png)


Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zum Modul 1.2](./automation.md)

[Zurück zu „Alle Module“](./../../../overview.md)
