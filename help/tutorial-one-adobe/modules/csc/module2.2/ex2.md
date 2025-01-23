---
title: Proofing mit Workfront
description: Proofing mit Workfront
kt: 5342
doc-type: tutorial
source-git-commit: 246bb91496104818f357848f41b79523b7771638
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 2.2.2 Proofing mit Workfront

## 2.2.2.1 Erstellen eines neuen Genehmigungsflusses

Navigieren Sie zu [https://experienceplatform.my.workfront.com/](https://experienceplatform.my.workfront.com/){target="_blank"}.

Klicken Sie auf das 9-Punkte **Hamburger**-Symbol und wählen Sie **Proofing**.

![WF](./images/wfp1.png)

Gehen Sie zu **Workflows**, klicken Sie auf **+ Neu** und wählen Sie dann **Neue Vorlage**.

![WF](./images/wfp2.png)

Legen Sie den **Vorlagennamen** auf `--aepUserLdap-- - Approval Workflow` fest und legen Sie den **Vorlagenbesitzer** auf sich selbst fest.

![WF](./images/wfp3.png)

Scrollen Sie nach unten und fügen Sie unter **Schritte** > **Schritt 1** den Inhalt **Wouter Van Geluwe** mit dem **Rolle** des **Validierungsverantwortlichen und Genehmigenden** hinzu.

Klicken Sie auf **Erstellen**.

![WF](./images/wfp4.png)

Ihr einfacher Genehmigungs-Workflow kann jetzt verwendet werden.

![WF](./images/wfp5.png)

## 2.2.2.2 Neues Projekt erstellen

Klicken Sie auf der Workfront-Startseite auf **Neu** auf der Registerkarte **Meine Projekte** . Wählen Sie **Leeres Projekt** aus.

![WF](./images/wfp6.png)

Sie sollten das dann sehen. Ändern Sie den Namen in `--aepUserLdap-- - CitiSignal Fiber Launch`.

![WF](./images/wfp6a.png)

Ihr Projekt ist jetzt erstellt.

![WF](./images/wfp7.png)

## 2.2.2.3 Neue Aufgabe erstellen

Geben Sie den folgenden Namen für Ihre Aufgabe ein: **Erstellen von Assets für Fibre-**-Kampagnen. Klicken Sie **Aufgabe erstellen**.

![WF](./images/wfp8.png)

Sie sollten das dann sehen.

![WF](./images/wfp9.png)

## 2.2.2.4 Ein neues Dokument zu Ihrer Aufgabe hinzufügen, durchlaufen Sie den Genehmigungsfluss

Klicken Sie auf **+ Neu hinzufügen** wählen Sie dann **Dokument** aus.

![WF](./images/wfp10.png)

Laden Sie [diese Datei](./images/2048x2048.png) auf Ihren Desktop herunter.

![WF](./images/2048x2048.png){width="50px" align="left"}

Wählen Sie die Datei **2048x2048.png** aus und klicken Sie auf **Öffnen**.

![WF](./images/wfp12.png)

Sie sollten dann diese haben. Klicken Sie **Korrekturabzug erstellen** und wählen Sie dann **Erweiterter Korrekturabzug**.

![WF](./images/wfp13.png)

Wählen Sie im Fenster **Neuer Korrekturabzug** die zuvor erstellte Workflow-Vorlage aus, die `--aepuserLdap-- - Approval Workflow` benannt werden soll. Klicken Sie **Korrekturabzug erstellen**.

![WF](./images/wfp14.png)

Dann sind Sie wieder bei Ihrer Aufgabe. Klicken Sie auf die **Zuweisen zu** und wählen Sie **Mir zuweisen** aus.

![WF](./images/wfp15.png)

Klicken Sie auf **Speichern**.

![WF](./images/wfp16.png)

Klicken Sie **Bearbeiten**.

![WF](./images/wfp17.png)

Klicken Sie **Korrekturabzug öffnen**

![WF](./images/wfp18.png)

Sie können den Korrekturabzug jetzt überprüfen. Wählen Sie **Kommentar hinzufügen** aus, um eine Anmerkung hinzuzufügen, für die das Dokument geändert werden muss.

![WF](./images/wfp19.png)

Geben Sie Ihren Kommentar ein und klicken Sie auf **Posten**. Klicken Sie auf **Schließen**.

![WF](./images/wfp20.png)

Als Nächstes müssen Sie Ihre Rolle von &quot;**&quot; in &quot;** und **&quot;**. Gehen Sie dazu zurück zu Ihrer Aufgabe und klicken Sie auf **Proofing-Workflow**.

![WF](./images/wfp21.png)

Ändern Sie Ihre Rolle von **Prüfer** in **Prüfer und Genehmiger**.

![WF](./images/wfp22.png)

Kehren Sie zu Ihrer Aufgabe zurück und öffnen Sie den Korrekturabzug erneut. Jetzt sehen Sie eine neue Schaltfläche **Entscheidung treffen**. Klicken Sie darauf.

![WF](./images/wfp23.png)

Wählen Sie **Änderungen erforderlich** und klicken Sie auf **Entscheidung treffen**.

![WF](./images/wfp24.png)

Dann solltest du wieder hier sein. Sie müssen jetzt ein zweites Bild hochladen, das die angegebenen Kommentare berücksichtigt.

![WF](./images/wfp25.png)

Laden Sie [diese Datei](./images/2048x2048_buynow.png) auf Ihren Desktop herunter.

![diese Datei](./images/2048x2048_buynow.png){width="50px" align="left"}

Wählen Sie in Ihrer Aufgabenansicht die alte Bilddatei aus, die nicht genehmigt wurde. Klicken Sie dann auf **+ Neu hinzufügen** wählen Sie **Version** und dann **Dokument** aus.

![WF](./images/wfp26.png)

Wählen Sie die Datei **2048x2048_buynow.png** und klicken Sie auf **Öffnen**.

![WF](./images/wfp27.png)

Sie sollten dann diese haben. Klicken Sie **Korrekturabzug erstellen** und wählen Sie dann erneut **Erweiterter** aus.

![WF](./images/wfp28.png)

Sie werden es dann sehen. Die **Workflow-Vorlage** ist jetzt vorausgewählt, da Workfront davon ausgeht, dass der vorherige Genehmigungs-Workflow weiterhin gültig ist. Klicken Sie **Korrekturabzug erstellen**.

![WF](./images/wfp29.png)

Wählen Sie **Korrekturabzug öffnen** aus.

![WF](./images/wfp30.png)

Sie können nun zwei Versionen der Datei nebeneinander sehen.

![WF](./images/wfp31.png)

Klicken Sie **Entscheidung treffen**, wählen Sie **Genehmigt** und klicken Sie erneut **Entscheidung treffen**.

![WF](./images/wfp32.png)

Schließen Sie die Testversand-Vorschau.

![WF](./images/wfp33.png)

Sie werden dann mit einem genehmigten Asset wieder in Ihrer Aufgabenansicht angezeigt. Dieses Asset muss jetzt für AEM Assets freigegeben werden.

![WF](./images/wfp34.png)

Klicken Sie auf das **Freigabe** Pfeilsymbol und wählen Sie Ihre AEM Assets-Integration aus, die `--aepUserLdap-- - Citi Signal AEM` benannt werden soll.

![WF](./images/wfp35.png)

Doppelklicken Sie auf den zuvor erstellten Ordner, der `--aepUserLdap-- - Workfront Assets` benannt werden soll.

![WF](./images/wfp36.png)

Klicken Sie **Ordner auswählen**.

![WF](./images/wfp37.png)

Nach 1-2 Minuten wird Ihr Dokument jetzt in AEM Assets veröffentlicht. Neben Ihrem Dokumentnamen wird ein AEM-Symbol angezeigt.

![WF](./images/wfp37a.png)

Klicken Sie **Zusammenfassung öffnen**.

![WF](./images/wfp38.png)

Navigieren Sie **Metadaten**, Sie sollten Folgendes sehen:

![WF](./images/wfp39.png)

Gehen Sie zu **Übersicht** und klicken Sie auf **+ Hinzufügen** um eine Beschreibung hinzuzufügen.

![WF](./images/wfp40.png)

Geben Sie Ihre Beschreibung ein. Ihre Korrekturabzugs- und Dokumenteneinstellungen sind jetzt abgeschlossen.

![WF](./images/wfp41.png)

## 2.2.2.5 Datei in AEM Assets anzeigen

Wechseln Sie zu Ihrem Ordner in AEM Assets, der `--aepUserLdap - Workfront Assets` heißt.

![WF](./images/wfppaem1.png)

Klicken Sie auf die drei Punkte unter Ihrem Bild und wählen Sie dann **Details**.

![WF](./images/wfppaem2.png)

Anschließend sehen Sie das zuvor erstellte Metadatenformular mit den Werten, die automatisch durch die Integration zwischen Workfront und AEM Assets ausgefüllt wurden.

![WF](./images/wfppaem3.png)

[Zurück zum Modul 2.2](./workfront.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
