---
title: Adobe Journey Optimizer - Konfigurieren einer Batch-basierten Journey
description: In diesem Abschnitt konfigurieren Sie eine Batch-E-Mail-Journey für den Versand eines Newsletters
kt: 5342
doc-type: tutorial
exl-id: 52b2e019-e408-4160-87b7-2aabd0f3c68f
source-git-commit: c531412a2c0a5c216f49560e01fb26b9b7e71869
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 8%

---

# 3.4.2 Konfigurieren einer Batch-basierten Newsletter-Journey

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox in eine andere zu wechseln, klicken Sie auf **PRODUCTION Prod (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel trägt die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

## 3.4.2.1 Newsletter-Journey erstellen

Im Folgenden erstellen Sie eine Batch-basierte Journey. Im Gegensatz zum ereignisbasierten Journey der vorherigen Übung, das auf eingehenden Erlebnisereignissen oder Zielgruppeneintritten oder -austritten beruht, um eine Journey für einen bestimmten Kunden Trigger, zielen Batch-basierte Journey-Dateien mit eindeutigen Inhalten wie Newslettern, einmaligen Werbeaktionen oder allgemeinen Informationen oder regelmäßig mit ähnlichen Inhalten ab, die regelmäßig gesendet werden, wie z. B. Geburtstagskampagnen und Erinnerungen.

Wechseln Sie im Menü zu **Journey** und klicken Sie auf **Journey erstellen**.

![Journey Optimizer](./images/oc43.png)

Auf der rechten Seite sehen Sie ein Formular, in dem Sie den Journey-Namen und die Beschreibung angeben müssen. Geben Sie die folgenden Werte ein:

- **Name**: `--aepUserLdap-- - Newsletter Journey`. Zum Beispiel: **vangeluw - Newsletter Journey**.
- **Beschreibung**: monatlicher Newsletter

Klicken Sie auf **OK**.

![Journey Optimizer](./images/batchj2.png)

Ziehen Sie **Orchestrierung** per Drag-and-Drop **Zielgruppe lesen** auf die Arbeitsfläche. Das bedeutet, dass die Journey nach der Veröffentlichung mit dem Abrufen der gesamten Zielgruppe beginnt, die dann zur Zielgruppe der Journey und Nachricht wird. Klicken Sie **Zielgruppe auswählen**.

![Journey Optimizer](./images/batchj3.png)

Suchen Sie im Popup **Zielgruppe wählen** nach Ihrem LDAP und wählen Sie die Zielgruppe aus, die Sie in [Modul 2.3 - Real-Time CDP - Eine Zielgruppe erstellen und ](./../../../modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md). `--aepUserLdap-- - Interest in Galaxy S24` erstellt haben. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/batchj5.png)

Klicken Sie auf **OK**.

![Journey Optimizer](./images/batchj6.png)

Suchen Sie im linken Menü den Abschnitt **Aktionen** und ziehen Sie per Drag-and-Drop eine **E-Mail**-Aktion auf die Arbeitsfläche.

![Journey Optimizer](./images/batchj7.png)

Legen Sie die **Kategorie** auf **Marketing** fest und wählen Sie eine E-Mail-Oberfläche aus, mit der Sie E-Mails senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **E-Mail**. Stellen Sie sicher, dass die Kontrollkästchen für **Klicks auf E-**) und **E-Mail-Öffnungen** beide aktiviert sind.

![ACOP](./images/journeyactions1eee.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

Jetzt seht ihr das. Klicken Sie auf **Textfeld** Betreffzeile“.

![Journey Optimizer](./images/batch4.png)

Geben Sie diesen Text in die Betreffzeile ein: `Luma Newsletter - your monthly update has arrived.`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/batch5.png)

Dann bist du wieder hier. Klicken Sie auf **E-Mail-Designer**, um mit der Erstellung des E-Mail-Inhalts zu beginnen.

![Journey Optimizer](./images/batch6.png)

Sie werden es dann sehen. Klicken Sie **HTML importieren**.

![Journey Optimizer](./images/batch7.png)

Im Popup-Bildschirm müssen Sie die HTML-Datei der E-Mail per Drag-and-Drop verschieben. Die HTML-Vorlage finden Sie [hier](./../../../assets/html/ajo-newsletter.html.zip). Laden Sie die ZIP-Datei mit der HTML-Vorlage auf Ihren lokalen Computer herunter und entpacken Sie sie auf Ihren Desktop.

![Journey Optimizer](./images/html1.png)

Ziehen Sie die Datei **ajo-newsletter.html** per Drag-and-Drop in Journey Optimizer. Klicken Sie **Importieren**.

![Journey Optimizer](./images/batch8.png)

Dieser E-Mail-Inhalt ist startbereit, da er alle erwarteten Personalisierungen, Bilder und Texte enthält. Nur der Platzhalter Angebot bleibt leer.

Möglicherweise erhalten Sie die folgende Fehlermeldung: **Fehler beim Abrufen von Assets**. Dies ist mit dem Bild in der E-Mail verknüpft.

![Journey Optimizer](./images/errorfetch.png)

Wenn Sie diesen Fehler erhalten, wählen Sie das Bild aus und klicken Sie auf die Schaltfläche **Bild bearbeiten**.

![Journey Optimizer](./images/errorfetch1.png)

Klicken Sie auf **Assets Essentials**, um zu Ihrer AEM Assets Essentials-Bibliothek zurückzukehren.

![Journey Optimizer](./images/errorfetch2.png)

Dann sehen Sie dieses Popup. Navigieren Sie zum Ordner **enable-assets** und wählen Sie das Bild **luma-newsletterContent.png** aus. Klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/errorfetch3.png)

Ihre Standard-Newsletter-E-Mail ist jetzt bereit. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/ready.png)

Kehren Sie zum Nachrichten-Dashboard zurück, indem Sie auf den **Pfeil** neben dem Betreffzeilentext in der oberen linken Ecke klicken.

![Journey Optimizer](./images/batch9.png)

Klicken Sie auf den Pfeil oben links, um zu Ihrem Journey zurückzukehren.

![Journey Optimizer](./images/oc79aeee.png)

Klicken Sie auf **OK**, um die E-Mail-Aktion zu schließen.

![Journey Optimizer](./images/oc79beee.png)

Ihre Newsletter-Journey ist jetzt zur Veröffentlichung bereit. Beachten Sie vorher den **Zeitplan**, in dem Sie diese Journey von einer einmaligen zu einer wiederkehrenden Kampagne wechseln können. Klicken Sie auf **Zeitplan**-Schaltfläche.

![Journey Optimizer](./images/batchj12.png)

Sie werden es dann sehen. Wählen Sie **Einmal** aus.

![Journey Optimizer](./images/sch1.png)

Wählen Sie innerhalb der nächsten Stunde ein Datum und eine Uhrzeit aus, um Ihren Journey zu testen. Klicken Sie auf **OK**.

>[!NOTE]
>
>Datum und Uhrzeit des Nachrichtenversands müssen innerhalb von mehr als einer Stunde liegen.

Klicken Sie auf **Veröffentlichen**.

![Journey Optimizer](./images/batchj13.png)

Klicken Sie erneut auf **** Publish.

![Journey Optimizer](./images/batchj14.png)

Ihre Standard-Newsletter-Journey ist jetzt veröffentlicht. Ihre Newsletter-E-Mail-Nachricht wird so gesendet, wie Sie es in Ihrem Zeitplan definiert haben, und Ihre Journey wird beendet, sobald die letzte E-Mail gesendet wurde.

![Journey Optimizer](./images/batchj14eee.png)

Du hast diese Übung beendet.

Nächster Schritt: [3.4.3 Personalisierung in einer E-Mail-Nachricht anwenden](./ex3.md)

[Zurück zum Modul 3.4](./journeyoptimizer.md)

[Zurück zu „Alle Module“](../../../overview.md)
