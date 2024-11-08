---
title: Adobe Journey Optimizer - Konfigurieren einer Batch-basierten Journey
description: In diesem Abschnitt konfigurieren Sie eine Batch-E-Mail-Journey, um einen Newsletter zu versenden
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 8%

---

# 3.4.2 Batch-basierte Newsletter-Journey konfigurieren

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der Ansicht **Home** Ihrer Sandbox `--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

## 3.4.2.1 Newsletter-Journey erstellen

Jetzt erstellen Sie eine Batch-basierte Journey. Im Gegensatz zur ereignisbasierten Journey der vorherigen Übung, bei der eingehende Erlebnisereignisse oder Segmenteinträge oder -ausstiege zum Trigger einer Journey für einen bestimmten Kunden verwendet werden, richten sich Batch-basierte Journey ein ganzes Segment einmal mit eindeutigen Inhalten wie Newslettern, einmaligen Promotions oder allgemeinen Informationen oder regelmäßig mit ähnlichen Inhalten, die regelmäßig gesendet werden, z. B. Geburtstagskampagnen und Erinnerungen.

Wechseln Sie im Menü zu **Journey** und klicken Sie auf **Journey erstellen**.

![Journey Optimizer](./images/oc43.png)

Auf der rechten Seite sehen Sie ein Formular, in dem Sie den Journey-Namen und die Beschreibung angeben müssen. Geben Sie die folgenden Werte ein:

- **Name**: `--aepUserLdap-- - Newsletter Journey`. Beispiel: **vangeluw - Newsletter-Journey**.
- **Beschreibung**: Monatlicher Newsletter

Klicken Sie auf **OK**.

![Journey Optimizer](./images/batchj2.png)

Ziehen Sie unter **Orchestrierung** **Segment lesen** auf die Arbeitsfläche. Das bedeutet, dass die Journey nach der Veröffentlichung mit dem Abrufen der gesamten Segmentzielgruppe beginnt, die dann zur Zielgruppe der Journey und Nachricht wird. Klicken Sie auf **Segment auswählen**.

![Journey Optimizer](./images/batchj3.png)

Suchen Sie im Popup **Segment auswählen** nach Ihrem ldap und wählen Sie das Segment aus, das Sie in [Modul 2.3 - Echtzeit-Kundendatenplattform - Erstellen eines Segments erstellt haben. Nehmen Sie die Aktion](./../../../modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md) mit dem Namen `--aepUserLdap-- - Interest in PROTEUS FITNESS JACKSHIRT` vor. Beispiel: vangeluw - Interesse an PROTEUS FITNESS JACKSHIRT. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/batchj5.png)

Klicken Sie auf **OK**.

![Journey Optimizer](./images/batchj6.png)

Suchen Sie im linken Menü den Abschnitt **Aktionen** und ziehen Sie eine Aktion vom Typ **E-Mail** auf die Arbeitsfläche.

![Journey Optimizer](./images/batchj7.png)

Setzen Sie die **Kategorie** auf **Marketing** und wählen Sie eine E-Mail-Oberfläche aus, über die Sie E-Mails senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **E-Mail**. Stellen Sie sicher, dass die Kontrollkästchen für **Klicks auf E-Mail** und **E-Mail-Öffnungen** aktiviert sind.

![ACOP](./images/journeyactions1eee.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

Das sehen Sie jetzt. Klicken Sie auf das Textfeld **Betreff**.

![Journey Optimizer](./images/batch4.png)

Geben Sie diesen Text für die Betreffzeile ein: `Luma Newsletter - your monthly update has arrived.`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/batch5.png)

Du wirst dann wieder hier sein. Klicken Sie auf **E-Mail-Designer** , um mit der Erstellung des E-Mail-Inhalts zu beginnen.

![Journey Optimizer](./images/batch6.png)

Dann wirst du das sehen. Klicken Sie auf **HTML importieren**.

![Journey Optimizer](./images/batch7.png)

Im Popup-Bildschirm müssen Sie die HTML-Datei der E-Mail per Drag-and-Drop verschieben. Die HTML-Vorlage [finden Sie hier](./../../../assets/html/ajo-newsletter.html.zip). Laden Sie die ZIP-Datei mit der HTML-Vorlage auf Ihren lokalen Computer herunter und dekomprimieren Sie sie auf Ihrem Desktop.

![Journey Optimizer](./images/html1.png)

Ziehen Sie die Datei **ajo-newsletter.html** in den Arbeitsbereich, um sie in Journey Optimizer hochzuladen. Klicken Sie auf **Importieren**.

![Journey Optimizer](./images/batch8.png)

Dieser E-Mail-Inhalt ist einsatzbereit, da er die erwartete Personalisierung, Bilder und Text aufweist. Leer bleibt nur der Angebots-Platzhalter.

Möglicherweise erhalten Sie eine Fehlermeldung: **Fehler beim Versuch, Assets abzurufen**. Dies ist mit dem Bild in der E-Mail verknüpft.

![Journey Optimizer](./images/errorfetch.png)

Wenn dieser Fehler auftritt, wählen Sie das Bild aus und klicken Sie auf die Schaltfläche **Bild bearbeiten** .

![Journey Optimizer](./images/errorfetch1.png)

Klicken Sie auf **Assets Essentials** , um zur AEM Assets Essentials-Bibliothek zurückzukehren.

![Journey Optimizer](./images/errorfetch2.png)

Dann sehen Sie dieses Popup. Navigieren Sie zum Ordner **enable-assets** und wählen Sie das Bild **luma-newsletterContent.png** aus. Klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/errorfetch3.png)

Ihre einfache Newsletter-E-Mail ist jetzt bereit. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/ready.png)

Gehen Sie zurück zum Nachrichten-Dashboard, indem Sie in der oberen linken Ecke auf den Pfeil **11} neben dem Betreffzeilentext klicken.**

![Journey Optimizer](./images/batch9.png)

Klicken Sie auf den Pfeil oben links, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/oc79aeee.png)

Klicken Sie auf **OK** , um Ihre E-Mail-Aktion zu schließen.

![Journey Optimizer](./images/oc79beee.png)

Ihre Newsletter-Journey kann jetzt veröffentlicht werden. Beachten Sie zunächst den Abschnitt **Planung** , in dem Sie diese Journey von einer einmaligen zu einer wiederkehrenden Kampagne wechseln können. Klicken Sie auf die Schaltfläche **Zeitplan** .

![Journey Optimizer](./images/batchj12.png)

Dann wirst du das sehen. Wählen Sie **Einmal** aus.

![Journey Optimizer](./images/sch1.png)

Wählen Sie Datum und Uhrzeit innerhalb der nächsten Stunde aus, damit Sie Ihre Journey testen können. Klicken Sie auf **OK**.

>[!NOTE]
>
>Datum und Uhrzeit des Nachrichtenversands müssen innerhalb von mehr als einer Stunde liegen.

Klicken Sie auf **Veröffentlichen**.

![Journey Optimizer](./images/batchj13.png)

Klicken Sie erneut auf **Publish**.

![Journey Optimizer](./images/batchj14.png)

Ihre grundlegende Newsletter-Journey ist jetzt veröffentlicht. Ihre Newsletter-E-Mail-Nachricht wird wie in Ihrem Zeitplan definiert gesendet und Ihre Journey wird beendet, sobald die letzte E-Mail gesendet wurde.

![Journey Optimizer](./images/batchj14eee.png)

Du hast diese Übung beendet.

Nächster Schritt: [3.4.3 Personalisierung in einer E-Mail-Nachricht anwenden](./ex3.md)

[Zurück zu Modul 3.4](./journeyoptimizer.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
