---
title: Prozessautomatisierung mit Workfront Fusion
description: Erfahren Sie, wie Sie die Automatisierung mit Workfront Fusion verarbeiten
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 1b7b2630-864f-4982-be5d-c46b760739c3
source-git-commit: 603e48e0453911177823fe7ceb340f8ca801c5e1
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# 1.2.3 Prozessautomatisierung mit Workfront Fusion

Erfahren Sie, wie Sie die Prozessautomatisierung mit Workfront Fusion durchführen.

## Iteration über mehrere Werte 1.2.3.1

Ihr Szenario sollte wie folgt aussehen:

![WF Fusion](./images/wffusion200.png)

Bisher haben Sie Text in einer Photoshop-Datei um einen statischen Wert geändert. Um Ihre Workflows zur Inhaltserstellung zu skalieren und zu automatisieren, müssen Sie eine Liste von Werten durchlaufen und diese Werte dynamisch in die Photoshop-Datei einfügen. In den nächsten Schritten fügen Sie hinzu, dass in Ihrem vorhandenen Szenario die Werte durchlaufen werden sollen.

Wählen Sie zwischen dem **Router**-Knoten und dem **Photoshop Change Text**-Knoten das Symbol **Schraubenschlüssel** aus und klicken Sie auf **Modul hinzufügen**.

![WF Fusion](./images/wffusion201.png)

Suchen Sie nach `flow` und wählen Sie **Flusssteuerung** aus.

![WF Fusion](./images/wffusion202.png)

Wählen Sie **Iterator** aus.

![WF Fusion](./images/wffusion203.png)

Ihr Bildschirm sollte wie folgt aussehen:

![WF Fusion](./images/wffusion204.png)

Es ist zwar möglich, Eingabedateien wie CSV-Dateien zu lesen, aber Sie müssen zunächst eine einfache Version einer CSV-Datei verwenden, indem Sie eine Textzeichenfolge definieren und diese Textdatei aufteilen.

Sie finden die Funktion **Aufspaltung** durch Auswahl des Symbols **T**, über das Sie alle verfügbaren Funktionen zum Bearbeiten von Textwerten sehen. Wählen Sie die **Aufspaltung**-Funktion aus, dann sollte dies angezeigt werden.

![WF Fusion](./images/wffusion206.png)

Die Aufspaltungsfunktion erwartet ein Array von Werten vor dem Semikolon und erwartet, dass Sie das Trennzeichen nach dem Semikolon angeben. Für diesen Test sollten Sie ein einfaches Array mit zwei Feldern verwenden: **Jetzt kaufen** und **Hier klicken** und das zu verwendende Trennzeichen ist **,**.

Geben Sie dies in das Feld **Array** ein, indem Sie die derzeit leere Funktion **split** ersetzen: `{{split("Buy now, Click here "; ",")}}`. Klicken Sie **OK**.

![WF Fusion](./images/wffusion205.png)

Wählen Sie **Photoshop-** aus, um für die Eingabe- und Ausgabefelder einige Variablen anstelle statischer Werte hinzuzufügen.

![WF Fusion](./images/wffusion207.png)

In **Inhalt anfragen** ist der Text **Hier klicken**. Dieser Text muss durch die Werte aus Ihrem -Array ersetzt werden.

![WF Fusion](./images/wffusion208.png)

Löschen Sie den Text **Hier klicken** und ersetzen Sie ihn, indem Sie die Variable **Wert** im Knoten **Iterator** auswählen. Dadurch wird sichergestellt, dass der Text auf der Schaltfläche in Ihrem Photoshop-Dokument dynamisch aktualisiert wird.

![WF Fusion](./images/wffusion209.png)

Sie müssen auch den Dateinamen aktualisieren, der zum Schreiben der Datei in Ihr Azure-Speicherkonto verwendet wird. Wenn der Dateiname statisch ist, überschreibt jede neue Iteration einfach die vorherige Datei und verliert daher die angepassten Dateien. Der aktuelle statische Dateiname lautet **Citisignal-Fibre-Changed-Text.psd**, und Sie müssen ihn jetzt aktualisieren.

Setzen Sie den Cursor hinter das Wort `text`.

![WF Fusion](./images/wffusion210.png)

Fügen Sie zunächst einen `-` mit Bindestrichen hinzu und wählen Sie dann den Wert **Bundle Order Position**. Dadurch wird sichergestellt, dass Workfront Fusion bei der ersten Iteration `-1` zum Dateinamen hinzufügt, bei der zweiten Iteration `-2`. Klicken Sie **OK**.

![WF Fusion](./images/wffusion211.png)

Speichern Sie das Szenario und wählen Sie **Einmal ausführen**.

![WF Fusion](./images/wffusion212.png)

Sobald das Szenario ausgeführt wurde, kehren Sie zu Ihrem Azure Storage-Explorer zurück und aktualisieren Sie den Ordner . Anschließend sollten die beiden neu erstellten Dateien angezeigt werden.

![WF Fusion](./images/wffusion213.png)

Laden Sie jede Datei herunter und öffnen Sie sie. Sie sollten verschiedene Texte auf den Schaltflächen. Dies ist die Datei `citisignal-fiber-changed-text-1.psd`.

![WF Fusion](./images/wffusion214.png)

Dies ist die Datei `citisignal-fiber-changed-text-2.psd`.

![WF Fusion](./images/wffusion215.png)

## 1.2.3.2 Aktivieren Ihres Szenarios mithilfe eines Webhooks

Bisher haben Sie Ihr Szenario zum Testen manuell ausgeführt. Aktualisieren wir nun Ihr Szenario mit einem Webhook, damit es von einer externen Umgebung aus aktiviert werden kann.

Wählen Sie **+** aus, suchen Sie nach **Webhook** und wählen Sie dann **Webhooks** aus.

![WF Fusion](./images/wffusion216.png)

Wählen Sie **Benutzerdefinierter Webhook** aus.

Ziehen Sie den Knoten **Benutzerdefinierter Webhook** und verbinden Sie ihn, sodass er eine Verbindung mit dem ersten Knoten auf der Arbeitsfläche herstellt, der **Initialisierungskonstanten“**.

![WF Fusion](./images/wffusion217.png)

Wählen Sie den Knoten **Benutzerdefinierter Webhook** aus. Wählen Sie dann **Hinzufügen** aus.

![WF Fusion](./images/wffusion218.png)

Legen Sie **Webhook-Name** auf `--aepUserLdap-- - Tutorial 1.2` fest.

![WF Fusion](./images/wffusion219.png)

Aktivieren Sie das Kontrollkästchen für **GET-Anfrage-Header**. Wählen Sie **Speichern** aus.

![WF Fusion](./images/wffusion220.png)

Ihre Webhook-URL ist jetzt verfügbar. Kopieren Sie die URL.

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
	"psdTemplate": "placeholder",
	"xlsFile": "placeholder"
}
```

![WF Fusion](./images/wffusion229.png)

Zurück in Workfront Fusion wird eine Meldung auf Ihrem benutzerdefinierten Webhook angezeigt, die lautet: **Erfolgreich ermittelt**.

![WF Fusion](./images/wffusion227.png)

Wählen Sie **Speichern** und dann **Einmal ausführen** aus. Ihr Szenario ist jetzt aktiv, wird aber erst ausgeführt, wenn Sie in Postman erneut **Senden** auswählen.

![WF Fusion](./images/wffusion230.png)

Wählen Sie in Postman **Senden** erneut aus.

![WF Fusion](./images/wffusion228.png)

Ihr Szenario wird erneut ausgeführt und erstellt die zwei Dateien genau wie zuvor.

![WF Fusion](./images/wffusion232.png)

Ändern Sie den Namen Ihrer Postman-Anfrage in `POST - Send Request to Workfront Fusion Webhook`.

![WF Fusion](./images/wffusion233.png)

Jetzt müssen Sie mit der Verwendung der Variablen **psdTemplate** beginnen. Anstatt den Speicherort der Eingabedatei im Knoten **Photoshop-Änderungstext** hartcodiert zu haben, verwenden Sie die eingehende Variable aus der Postman-Anfrage.

Öffnen Sie den Knoten **Photoshop**&#x200B;Änderungstext/ und wechseln Sie zu **Inhalt anfordern**. Wählen Sie den hartcodierten Dateinamen **citsignal-fiber.psd** unter **inputs** und löschen Sie ihn.

![WF Fusion](./images/wffusion234.png)

Wählen Sie die Variable **psdTemplate** aus. Wählen Sie **OK** und speichern Sie dann Ihr Szenario.

![WF Fusion](./images/wffusion235.png)

Wählen Sie **EIN** aus, um Ihr Szenario zu aktivieren. Ihr Szenario wird jetzt ununterbrochen ausgeführt.

![WF Fusion](./images/wffusion236.png)

Geben Sie zurück in Postman den Dateinamen `citisignal-fiber.psd` als Wert für die Variable **psdTemplate** ein und wählen Sie erneut **Senden** aus, um Ihr Szenario erneut auszuführen.

![WF Fusion](./images/wffusion237.png)

Indem Sie die PSD-Vorlage als Variable angeben, die von einem externen System bereitgestellt wird, haben Sie jetzt ein wiederverwendbares Szenario erstellt.

Jetzt haben Sie diese Übung abgeschlossen.

## Nächste Schritte

Wechseln Sie zur Automatisierung von [1.2.4 mithilfe von Connectoren](./ex4.md){target="_blank"}

Zurück zur [Creative-Workflow-Automatisierung mit Workfront Fusion](./automation.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
