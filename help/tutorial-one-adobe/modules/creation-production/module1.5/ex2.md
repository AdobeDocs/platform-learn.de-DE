---
title: Validierungen mit Frame.io
description: Validierungen mit Frame.io
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
source-git-commit: 96711c78cecdce13e2e2fd6e5a43e0815f59e079
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---

# 1.5.2 Genehmigungen mit Frame.io

>[!NOTE]
>
> Der folgende Screenshot zeigt, wie eine bestimmte Umgebung verwendet wird. Wenn Sie dieses Tutorial durchlaufen, hat Ihre Umgebung höchstwahrscheinlich einen anderen Namen. Wenn Sie sich für dieses Tutorial angemeldet haben, wurden Ihnen die zu verwendenden Umgebungsdetails zur Verfügung gestellt. Befolgen Sie bitte diese Anweisungen.

Um den Genehmigungs-Workflow in Frame.io durchlaufen zu können, benötigen Sie ein Asset. In dieser Übung erstellen Sie zunächst dieses Asset selbst mit Adobe Firefly und Adobe Express. Sobald Sie das Asset haben, laden Sie es in Frame.io hoch und genehmigen es schließlich.

## 1.5.2.1 Erstellen von Assets mit Adobe Firefly Services und Adobe Express

Navigieren Sie zu [https://firefly.adobe.com/](https://firefly.adobe.com/){target="_blank"}. Geben Sie den `a neon rabbit running very fast through space` ein und klicken Sie auf **Generieren**.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset1.png)

Anschließend werden mehrere Bilder generiert. Wählen Sie das Bild aus, das Ihnen am besten gefällt, klicken Sie auf das Symbol **Freigeben** auf dem Bild und wählen Sie dann **In Adobe Express öffnen**.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset2.png)

Anschließend wird das soeben generierte Bild in Adobe Express zur Bearbeitung verfügbar. Jetzt müssen Sie das CitiSignal-Logo auf dem Bild hinzufügen. Navigieren Sie dazu zu **Marken**.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset3.png)

Anschließend sollte eine CitiSignal-Markenvorlage angezeigt werden. die in GenStudio for Performance Marketing erstellt wurden, erscheinen in Adobe Express. Klicken Sie, um eine Markenvorlage auszuwählen, deren Name `CitiSignal` enthält.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset4.png)

Gehen Sie zu **Logos** und klicken Sie auf das **weiß** Citisignal-Logo, um es auf dem Bild abzulegen.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset5.png)

Positionieren Sie das CitiSignal-Logo oben auf Ihrem Bild, nicht zu weit von der Mitte entfernt.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset6.png)

Navigieren Sie zu **Text**.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset6a.png)

Klicken Sie **Text hinzufügen**.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset6b.png)

Geben Sie die `Timetravel now!` ein, ändern Sie die Schriftfarbe und Schriftgröße, legen Sie den Text auf **Fett** fest, sodass Sie ein Bild wie dieses haben.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset6c.png)

Klicken Sie anschließend auf **Freigeben**.

![GSPeM](./../../workflow-planning/module1.2/images/gsasset7.png)

Klicken Sie auf **… Alle**.

![Frame.io](./images/frameioasset1.png)

Scrollen Sie nach unten und wählen Sie **Herunterladen** aus.

![Frame.io](./images/frameioasset2.png)

Klicken Sie **Herunterladen**.

![Frame.io](./images/frameioasset3.png)

Anschließend haben Sie Ihr Asset auf Ihrem lokalen Computer.

![Frame.io](./images/frameioasset4.png)

## 1.5.2.2 Genehmigen des Assets in Frame.io

Navigieren Sie zu [https://next.frame.io/](https://next.frame.io/). Stellen Sie sicher, dass Sie bei der `--aepImsOrgName--` der Umgebung angemeldet sind.

![Frame.io](./images/frameio1.png)

Falls Sie nicht in der rechten Umgebung angemeldet sind, klicken Sie auf das Logo in der linken unteren Ecke und wählen Sie die gewünschte Umgebung aus.

![Frame.io](./images/frameio2.png)

Gehen Sie zu Ihrem Arbeitsbereich, der `--aepUserLdap--` heißen sollte, und öffnen Sie dann den Ordner **CitiSignal**. Klicken Sie auf das Symbol **+** und wählen Sie dann **Neuer Ordner** aus.

![Frame.io](./images/frameioappr1.png)

Benennen Sie den Ordner `--aepUserLdap-- - Approvals`. Doppelklicken Sie auf den Ordner, um ihn zu öffnen.

![Frame.io](./images/frameioappr2.png)

Sie laden nun die in der vorherigen Übung erstellte Datei in diesen Ordner hoch. Klicken Sie **Hochladen**.

![Frame.io](./images/frameioappr3.png)

Wählen Sie die Datei aus und klicken Sie auf **Öffnen**.

![Frame.io](./images/frameioappr4.png)

Sie sollten dann diese haben. Doppelklicken Sie auf die Datei, um sie zu öffnen.

![Frame.io](./images/frameioappr5.png)

Aktivieren Sie das Symbol, um einen verankerten Kommentar zu hinterlassen.

![Frame.io](./images/frameioappr6.png)

Geben Sie einen Kommentar ein, z. B. `Change CTA to "Get on board now!"`. Klicken Sie auf das **Senden**-Symbol, um Ihren Kommentar zu teilen.

![Frame.io](./images/frameioappr7.png)

Sie sollten dann diese haben. Navigieren Sie zu **Felder**.

![Frame.io](./images/frameioappr8.png)

Ändern Sie im Feld **Status** den Status in **Überprüfung erforderlich**.

![Frame.io](./images/frameioappr9.png)

Sie sollten dann diese haben. Navigieren Sie zurück zum Ordner, indem Sie auf den Pfeil klicken, um zurückzukehren.

![Frame.io](./images/frameioappr10.png)

Klicken Sie auf die drei Punkte **…** und wählen Sie **Umbenennen**.

![Frame.io](./images/frameioappr11.png)

Ändern Sie den Dateinamen in `version1.png`.

![Frame.io](./images/frameioappr12.png)

## 1.5.2.3 Vornehmen von Design-Änderungen in Adobe Express

Wechseln Sie zu [https://new.express.adobe.com/your-stuff/files](https://new.express.adobe.com/your-stuff/files) und öffnen Sie das zuvor erstellte Bild erneut.

![WF](./../../workflow-planning/module1.2/images/wfp25a.png)

Ändern Sie den CTA-Text in `Get On Board Now!`.

![WF](./../../workflow-planning/module1.2/images/wfp25b.png)

Klicken Sie auf **Freigeben** und wählen Sie dann **Herunterladen** aus.

![WF](./images/frameioasset5.png)

Klicken Sie **Herunterladen**.

![WF](./images/frameioasset6.png)

Anschließend wird ein neues Bild auf den lokalen Computer heruntergeladen. Benennen Sie die Datei in `version2.png` um.

![WF](./images/frameioasset7.png)

## 1.5.2.4 Version2 in Frame.io genehmigen

Klicken Sie in Ihrem Ordner in Frame.io auf das Symbol **+** und wählen Sie **Asset hochladen**.

![Frame.io](./images/frameioappr13.png)

Wählen Sie die Datei **version2.png** aus und klicken Sie auf **Öffnen**.

![Frame.io](./images/frameioappr14.png)

Ziehen Sie als Nächstes die Datei **version2.png** auf die Datei **version1.png**. Diese Aktion aktiviert das Stapeln von Versionen in Frame.io.

![Frame.io](./images/frameioappr15.png)

Sie sollten das dann sehen.

![Frame.io](./images/frameioappr16.png)

Klicken Sie auf die 3 Punkte **…** auf dem Bild und wählen Sie dann **Versionen vergleichen**.

![Frame.io](./images/frameioappr17.png)

Sie sollten dann diese Vergleichsansicht sehen, die beide Versionen der Datei anzeigt. Navigieren Sie zu **Felder**.

![Frame.io](./images/frameioappr18.png)

Ändern Sie das Feld **Status** in **Genehmigt**.

![Frame.io](./images/frameioappr19.png)

Sie sollten dann diese haben. Klicken Sie auf das Pfeilsymbol, um zur Ordneransicht zurückzukehren.

![Frame.io](./images/frameioappr20.png)

Klicken Sie auf die 3 Punkte **…** und wählen **Herunterladen**, falls Sie diese Datei in einem anderen Programm verwenden möchten.

![Frame.io](./images/frameioappr21.png)

## Nächste Schritte

[1.5.3 Frame.io und Premiere Pro](./ex3.md){target="_blank"}

Gehen Sie zurück zu [Optimieren Sie Ihren Workflow mit Frame.io](./frameio.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
