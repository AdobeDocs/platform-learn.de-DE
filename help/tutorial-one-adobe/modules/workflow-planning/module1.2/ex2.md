---
title: Proofing mit Workfront
description: Proofing mit Workfront
kt: 5342
doc-type: tutorial
exl-id: 5feb9486-bdb4-4d59-941c-09fc2e38163b
source-git-commit: 919bfdb5f047669f670482695edfa7820e0aad93
workflow-type: tm+mt
source-wordcount: '1293'
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

Scrollen Sie nach unten und ändern Sie unter **Schritte** > **Schritt 1** die Rolle **Korrekturabzugsersteller** in **Prüfende und genehmigende Person**. Sie können auch jede andere Person hinzufügen. Fügen Sie sich beispielsweise selbst hinzu, indem Sie Ihre Benutzerin bzw. Ihren Benutzer auswählen und die **Rolle** von **Prüfende und genehmigende Person** festlegen.

Klicken Sie auf **Erstellen**.

![WF](./images/wfp4.png)

Ihr einfacher Genehmigungs-Workflow kann jetzt verwendet werden.

![WF](./images/wfp5.png)

## 1.2.2.2 Workfront Blueprint aktivieren

Im nächsten Schritt erstellen Sie ein neues Projekt mithilfe einer Vorlage. Adobe Workfront stellt eine Reihe verfügbarer Blueprints bereit, die nur aktiviert werden müssen.

Für den Anwendungsfall von CitiSignal ist die Blueprint **Integrierte Kampagnenausführung** zu verwenden.

Um diese Blueprint zu installieren, öffnen Sie das Menü und wählen Sie **Blueprints**.

![WF](./images/blueprint1.png)

Wählen Sie den Filter **Marketing** und scrollen Sie dann nach unten, um den Blueprint **Integrierte Kampagnenausführung** zu finden. Klicken Sie auf **Installieren**.

![WF](./images/blueprint2.png)

Klicken Sie auf **Fortfahren**.

![WF](./images/blueprint3.png)

Klicken Sie **Unverändert installieren…**.

![WF](./images/blueprint4.png)

Sie sollten das dann sehen. Die Installation kann einige Minuten dauern.

![WF](./images/blueprint5.png)

Nach einigen Minuten wird die Blueprint installiert.

![WF](./images/blueprint6.png)

## 1.2.2.3 Neues Projekt erstellen

Öffnen Sie das **Menü** und navigieren Sie zu **Programme**.

![WF](./images/wfp6a.png)

Klicken Sie auf , um das zuvor erstellte Programm mit dem Namen `--aepUserLdap-- CitiSignal Fiber Launch` anzuzeigen.

>[!NOTE]
>
>Sie haben im Rahmen der Übung zu [Workfront Planning](./../module1.1/ex1.md) mit der von Ihnen erstellten und ausgeführten Automatisierung ein Programm erstellt. Wenn ihr das noch nicht getan habt, könnt ihr die Anleitung dort finden.

![WF](./images/wfp6b.png)

Navigieren Sie in Ihrem Programm zu **Projekte**. Klicken Sie auf **+ Neues Projekt** und wählen Sie dann **Neues Projekt aus Vorlage**.

![WF](./images/wfp6.png)

Wählen Sie die Vorlage **Integrierte Kampagnenausführung** und klicken Sie auf **Vorlage verwenden**.

![WF](./images/wfp6g.png)

Sie sollten das dann sehen. Ändern Sie den Namen in `--aepUserLdap-- - CitiSignal Fiber Launch Winter 2026` und klicken Sie auf **Projekt erstellen**.

![WF](./images/wfp6c.png)

Ihr Projekt ist jetzt erstellt. Gehen Sie zu **Projektdetails**.

![WF](./images/wfp6h.png)

Gehen Sie zu **Projektdetails**. Klicken Sie, um den aktuellen Text unter **Beschreibung** auszuwählen.

![WF](./images/wfp6d.png)

Legen Sie die Beschreibung auf `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.` fest

Klicken Sie **Änderungen speichern**.

![WF](./images/wfp6e.png)

Ihr Projekt kann jetzt verwendet werden.

![WF](./images/wfp7.png)

Die Aufgaben und Abhängigkeiten im Projekt wurden auf der Grundlage der von Ihnen ausgewählten Vorlage erstellt und als festgelegt. Projektbesitzer. Der Status des Projekts wurde auf &quot;**&quot;**. Sie können den Status des Projekts ändern, indem Sie einen anderen Wert in der Liste auswählen.

![WF](./images/wfp7z.png)

## 1.2.2.4 Neue Aufgabe erstellen

Bewegen Sie den Mauszeiger über die Aufgabe **Beginnen Sie mit dem Erstellen von Design** Vorlagen und klicken Sie auf die 3 Punkte **…**.

![WF](./images/wfp7a.png)

Wählen Sie die Option **Aufgabe unten einfügen**.

![WF](./images/wfp7x.png)

Geben Sie diesen Namen für Ihre Aufgabe ein: `Create layout using approved assets and copy`.

Legen Sie das Feld **Arbeitsaufträge** auf die Rolle **Designer** fest.
Legen Sie das Feld **Dauer** auf **5 Tage** fest.
Setzen Sie den Vorgänger des Feldes auf **9**.
Geben Sie ein Datum für die Felder **Start am** und **Fällig am** ein.

Klicken Sie auf eine andere Stelle im Bildschirm, um die neue Aufgabe zu speichern.

![WF](./images/wfp8.png)

Sie sollten das dann sehen. Klicken Sie auf die Aufgabe, um sie zu öffnen.

![WF](./images/wfp9.png)

Gehen Sie zu **Aufgabendetails** und legen Sie das Feld **Beschreibung** auf: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Klicken Sie **Änderungen speichern**.

![WF](./images/wfp9a.png)

Sie sollten das dann sehen. Klicken Sie auf das **Projekt**, um zu Ihrem Projekt zurückzukehren.

![WF](./images/wfp9b.png)

Wechseln Sie in **Projekt** Ansicht zu **Workload-Balancer**.

![WF](./images/wfpwlb1.png)

Klicken Sie **Massenzuweisungen**.

![WF](./images/wfpwlb2.png)

Wählen Sie die **Rollenzuweisung** von **Designer** und klicken Sie dann auf das Feld **Zu zuweisender Benutzer**. Dadurch werden alle Benutzenden angezeigt, die in Ihrer Workfront-Instanz über eine **Designer**-Rolle verfügen. Wählen Sie in diesem Fall die fiktive Benutzerin **Melissa Jenkins**.

![WF](./images/wfpwlb3.png)

Klicken Sie **Zuweisen**. Der ausgewählte Benutzer wird nun den Aufgaben im Projekt zugewiesen, die mit der Rolle **Designer** verknüpft sind.

![WF](./images/wfpwlb4.png)

Die Aufgaben sind jetzt zugewiesen. Klicken Sie auf **Aufgaben**, um zur Übersichtsseite **Aufgaben** zurückzukehren.

![WF](./images/wfpwlb5.png)

Klicken Sie auf die erstellte Aufgabe mit dem Namen .
**Erstellen eines Layouts mit genehmigten Assets und Kopieren**.

![WF](./images/wfpwlb6.png)

Sie werden nun im Rahmen dieser Übung mit der Arbeit an dieser Aufgabe beginnen. Sie können sehen, dass Melissa Jenkins im Moment mit dieser Aufgabe betraut ist. Um dies für sich selbst zu ändern, klicken Sie auf das Feld **Arbeitsaufträge** und wählen Sie **Mir zuweisen** aus.

![WF](./images/wfpwlb7.png)

Klicken Sie auf **Speichern**.

![WF](./images/wfpwlb8.png)

Klicken Sie **Bearbeiten**.

![WF](./images/wfpwlb9.png)

Sie sollten das dann sehen.

![WF](./images/wfpwlb10.png)

Im Rahmen dieser Aufgabe müssen Sie ein neues Bild erstellen und es dann als Dokument in Workfront hochladen. Sie erstellen dieses Asset jetzt selbst mit Adobe Express.

## 1.2.2.5 Ein neues Dokument zu Ihrem Projekt hinzufügen und den Genehmigungsfluss starten

Für diese Übung müssen Sie dieses Asset herunterladen und verwenden: [timetravelnow.png](./images/timetravelnow.png)

![WF](./images/timetravelnow.png)

Kehren Sie zum Bildschirm **Projektdetails** zurück. Navigieren Sie zu **Dokumente**. Klicken Sie auf **+ Neu hinzufügen** wählen Sie dann **Dokument** aus.

![WF](./images/wfp10.png)

Klicken, um die `timetravelnow.png` auszuwählen. Klicken Sie auf **Öffnen**.

![WF](./images/wfp10a.png)

Sie sollten dann diese haben.

![WF](./images/wfp10b.png)

Bewegen Sie den Mauszeiger über das hochgeladene Dokument. Klicken Sie **Korrekturabzug erstellen** und wählen Sie dann **Erweiterter Korrekturabzug**.

![WF](./images/wfp13.png)

Wählen Sie im Fenster **Neuer Korrekturabzug** die Option **Automatisiert** und wählen Sie dann die zuvor erstellte Workflow-Vorlage aus, die `--aepUserLdap-- - Approval Workflow` benannt werden soll. Klicken Sie **Korrekturabzug erstellen**.

![WF](./images/wfp14.png)

Klicken Sie **Korrekturabzug öffnen**

![WF](./images/wfp18.png)

Sie können den Korrekturabzug jetzt überprüfen. Wählen Sie **Kommentar hinzufügen** aus, um eine Anmerkung hinzuzufügen, für die das Dokument geändert werden muss.

![WF](./images/wfp19.png)

Geben Sie Ihren Kommentar ein und klicken Sie auf **Posten**. Klicken Sie anschließend auf **Entscheidung treffen**.

![WF](./images/wfp20.png)

Wählen Sie **Änderungen erforderlich** und klicken Sie auf **Entscheidung treffen**.

![WF](./images/wfp24.png)

Gehen Sie zurück zu Ihrer **Aufgabe** und dem **Dokument**. Dort wird auch der Text **Änderungen erforderlich** angezeigt.

![WF](./images/wfp25.png)

Jetzt müssen Sie Design-Änderungen vornehmen, was Sie in Adobe Express tun werden.

## 1.2.2.6 Neue Version des Dokuments zu Ihrer Aufgabe hinzufügen

Für diese Übung müssen Sie dieses Asset herunterladen und verwenden: [getonboard.png](./images/getonboard.png)

![WF](./images/getonboard.png)

Wählen Sie in Ihrer Aufgabenansicht in Adobe Workfront die alte Bilddatei aus, die nicht genehmigt wurde. Klicken Sie dann auf **+ Neu hinzufügen**, wählen Sie **Version** und wählen Sie dann Ihr AEM Assets CS-Repository aus, das `--aepUserLdap-- - CitiSignal` benannt werden soll.

![WF](./images/wfp26.png)

Navigieren Sie zur `--aepUserLdap-- CitiSignal Fiber Campaign` und wählen Sie die `CitiSignal - Neon Rabit - Get On Board Now!.png` aus. Klicken Sie auf **Auswählen**.

![WF](./images/wfp26a.png)

Sie sollten dann diese haben. Klicken Sie **Korrekturabzug erstellen** und wählen Sie dann erneut **Erweiterter** aus.

![WF](./images/wfp28.png)

Sie werden es dann sehen. Die **Workflow-Vorlage** ist jetzt vorausgewählt, da Workfront davon ausgeht, dass der vorherige Genehmigungs-Workflow weiterhin gültig ist. Klicken Sie **Korrekturabzug erstellen**.

![WF](./images/wfp29.png)

Wählen Sie **Korrekturabzug öffnen** aus.

![WF](./images/wfp30.png)

Sie können nun zwei Versionen der Datei nebeneinander sehen. Klicken Sie auf die **Korrekturabzüge vergleichen**.

![WF](./images/wfp31.png)

Anschließend sollten beide Versionen des Bildes nebeneinander angezeigt werden. Klicken Sie **Entscheidung treffen**.

![WF](./images/wfp32.png)

Wählen Sie **Genehmigt** und klicken Sie erneut **Entscheidung**.

![WF](./images/wfp32a.png)

Schließen Sie die Ansicht **Korrekturabzüge vergleichen**, indem Sie die linke Version des Bildes schließen. Klicken Sie auf **Aufgabenname**, um zur Aufgabenübersicht zurückzukehren.

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

Klicken Sie **Als erledigt markieren**, um diese Aufgabe abzuschließen.

![WF](./images/wfp37b.png)

Sie sollten das dann sehen.

![WF](./images/wfp37c.png)

## 1.2.2.7 Datei in AEM Assets anzeigen

Navigieren Sie zu Ihrem Ordner in AEM Assets CS mit dem Namen `--aepUserLdap-- - CitiSignal Fiber Launch Assets`.

![WF](./images/wfppaem1.png)

Wählen Sie das Bild aus und klicken Sie auf **Details**.

![WF](./images/wfppaem2.png)

Anschließend sehen Sie das zuvor erstellte Metadatenformular mit den Werten, die automatisch durch die Integration zwischen Workfront und AEM Assets ausgefüllt wurden.

![WF](./images/wfppaem3.png)

Zurück zu [Workflow-Verwaltung mit Adobe Workfront](./workfront.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
