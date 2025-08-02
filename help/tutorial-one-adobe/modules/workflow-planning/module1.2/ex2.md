---
title: Proofing mit Workfront
description: Proofing mit Workfront
kt: 5342
doc-type: tutorial
exl-id: 5feb9486-bdb4-4d59-941c-09fc2e38163b
source-git-commit: 19291afe2d8101fead734fa20212a3db76369522
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---

# 1.2.2 Proofing mit Workfront

>[!IMPORTANT]
>
>Wenn Sie zuvor ein AEM CS-Programm mit einer AEM Assets CS-Umgebung konfiguriert haben, kann es sein, dass Ihre AEM CS-Sandbox in den Ruhezustand versetzt wurde. Da der Ruhezustand einer solchen Sandbox 10-15 Minuten dauert, ist es ratsam, den Ruhezustand jetzt zu beenden, damit Sie nicht zu einem späteren Zeitpunkt warten müssen.

## 1.2.2.1 Erstellen eines neuen Genehmigungsflusses

Zurück zu **Adobe Workfront**. Klicken Sie auf **Menü** und wählen Sie **Proofing** aus.

![WF](./images/wfp1.png)

Gehen Sie zu **Workflows**, klicken Sie auf **+ Neu** und wählen Sie dann **Neue Vorlage**.

![WF](./images/wfp2.png)

Legen Sie den **Vorlagennamen** auf `--aepUserLdap-- - Approval Workflow` fest und legen Sie den **Vorlagenbesitzer** auf sich selbst fest.

![WF](./images/wfp3.png)

Scrollen Sie nach unten und fügen Sie sich unter **Schritte** > **Schritt 1** mit der **Rolle** von **Prüfer und Genehmiger** hinzu.

Klicken Sie auf **Erstellen**.

![WF](./images/wfp4.png)

Ihr einfacher Genehmigungs-Workflow kann jetzt verwendet werden.

![WF](./images/wfp5.png)

## 1.2.2.2 Neues Projekt erstellen

Öffnen Sie das **Menü** und navigieren Sie zu **Programme**.

![WF](./images/wfp6a.png)

Klicken Sie auf , um das zuvor erstellte Programm mit dem Namen `--aepUserLdap-- CitiSignal Fiber Launch` anzuzeigen.

>[!NOTE]
>
>Sie haben im Rahmen der Übung zu [Workfront Planning](./../module1.1/ex1.md) mit der von Ihnen erstellten und ausgeführten Automatisierung ein Programm erstellt. Wenn ihr das noch nicht getan habt, könnt ihr die Anleitung dort finden.

![WF](./images/wfp6b.png)

Navigieren Sie in Ihrem Programm zu **Projekte**. Klicken Sie auf **+ Neues Projekt** und wählen Sie dann **Neues Projekt** aus.

![WF](./images/wfp6.png)

Sie sollten das dann sehen. Ändern Sie den Namen in `--aepUserLdap-- - CitiSignal Fiber Launch`.

![WF](./images/wfp6c.png)

Gehen Sie zu **Projektdetails**. Klicken Sie auf **+** unter **Beschreibung**.

![WF](./images/wfp6d.png)

Legen Sie die Beschreibung auf `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.` fest

Klicken Sie **Änderungen speichern**.

![WF](./images/wfp6e.png)

Ihr Projekt ist jetzt erstellt.

![WF](./images/wfp7.png)

## 1.2.2.3 Neue Aufgabe erstellen

Navigieren Sie zu **Aufgaben** und klicken Sie auf **+ Neue Aufgabe**.

![WF](./images/wfp7a.png)

Geben Sie diesen Namen für Ihre Aufgabe ein: `Create assets for Fiber campaign`.

Legen Sie das Feld **Beschreibung** wie folgt fest: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Klicken Sie **Aufgabe erstellen**.

![WF](./images/wfp8.png)

Sie sollten das dann sehen.

![WF](./images/wfp9.png)

Fügen Sie in der Spalte **Zuweisung** Ihren eigenen Namen hinzu.

![WF](./images/wfp9a.png)

Die Aufgabe wird dann Ihnen zugewiesen.

![WF](./images/wfp9b.png)

## 1.2.2.4 Ein neues Dokument zu Ihrer Aufgabe hinzufügen, durchlaufen Sie den Genehmigungsfluss

Klicken Sie auf das Workfront **-Logo von**, um zur Übersichtsseite zurückzukehren. Anschließend sollte das soeben erstellte Projekt in der Übersicht angezeigt werden. Klicken Sie auf das Projekt, um es zu öffnen.

![WF](./images/wfp9c.png)

Klicken **in &quot;**&quot;, um die Aufgabe zu öffnen.

![WF](./images/wfp9d.png)

Navigieren Sie zu **Dokumente**. Klicken Sie auf **+ Neu hinzufügen** wählen Sie dann **Dokument** aus.

![WF](./images/wfp10.png)

Laden Sie [diese Datei](./images/2048x2048.png) auf Ihren Desktop herunter.

![WF](./images/2048x2048.png){width="50px" align="left"}

Wählen Sie die Datei **2048x2048.png** aus und klicken Sie auf **Öffnen**.

![WF](./images/wfp12.png)

Sie sollten dann diese haben. Bewegen Sie den Mauszeiger über das hochgeladene Dokument. Klicken Sie **Korrekturabzug erstellen** und wählen Sie dann **Erweiterter Korrekturabzug**.

![WF](./images/wfp13.png)

Wählen Sie im Fenster **Neuer Korrekturabzug** die Option **Automatisiert** und wählen Sie dann die zuvor erstellte Workflow-Vorlage aus, die `--aepUserLdap-- - Approval Workflow` benannt werden soll. Klicken Sie **Korrekturabzug erstellen**.

![WF](./images/wfp14.png)

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

Gehen Sie zurück zu Ihrer **Aufgabe** und dem **Dokument**. Sie müssen jetzt ein zweites Bild hochladen, das die angegebenen Kommentare berücksichtigt.

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

Klicken Sie auf **Aufgabenname**, um zur Aufgabenübersicht zurückzukehren.

![WF](./images/wfp33.png)

Sie werden dann mit einem genehmigten Asset wieder in Ihrer Aufgabenansicht angezeigt. Dieses Asset muss jetzt für AEM Assets freigegeben werden.

![WF](./images/wfp34.png)

Wählen Sie das genehmigte Dokument aus. Klicken Sie auf das **Freigabe** Pfeilsymbol und wählen Sie Ihre AEM Assets-Integration aus, die `--aepUserLdap-- - CitiSignal AEM` benannt werden soll.

![WF](./images/wfp35.png)

Doppelklicken Sie auf den zuvor erstellten Ordner, der `--aepUserLdap-- - CitiSignal Fiber Launch Assets` benannt werden soll.

![WF](./images/wfp36.png)

Klicken Sie **Ordner auswählen**.

![WF](./images/wfp37.png)

Nach 1-2 Minuten wird Ihr Dokument jetzt in AEM Assets veröffentlicht. Neben Ihrem Dokumentnamen wird ein AEM-Symbol angezeigt.

![WF](./images/wfp37a.png)

## 1.2.2.5 Datei in AEM Assets anzeigen

Navigieren Sie zu Ihrem Ordner in AEM Assets CS mit dem Namen `--aepUserLdap-- - CitiSignal Fiber Launch Assets`.

![WF](./images/wfppaem1.png)

Wählen Sie das Bild aus und klicken Sie auf **Details**.

![WF](./images/wfppaem2.png)

Anschließend sehen Sie das zuvor erstellte Metadatenformular mit den Werten, die automatisch durch die Integration zwischen Workfront und AEM Assets ausgefüllt wurden.

![WF](./images/wfppaem3.png)

Zurück zu [Workflow-Verwaltung mit Adobe Workfront](./workfront.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
