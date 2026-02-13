---
title: Erste Schritte mit benutzerdefinierten Workflows in Firefly
description: Erste Schritte mit benutzerdefinierten Workflows in Firefly
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 7d9ad7ec-7744-4ba6-9c11-c434e6cdef09
source-git-commit: 5fe2f1c413f54dd1e3c67d78460d7f2a84248005
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 4%

---

# 1.7.1 Erste Schritte mit benutzerdefinierten Workflows in Firefly

[!BADGE Beta]

+++Beta-Details
Durch die Verwendung der Beta für benutzerdefinierte Firefly-Workflows erkennen Sie hiermit an, dass die Beta ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt wird. Adobe ist nicht verpflichtet, die Beta zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Es wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung solcher Beta und/oder Begleitmaterialien zu verlassen. Die Beta gilt als vertrauliche Information von Adobe.  Jedes „Feedback“ (Informationen zur Beta-Version, insbesondere Probleme oder Mängel, auf die Sie bei der Verwendung der Beta-Version stoßen, Vorschläge, Verbesserungen und Empfehlungen), das sie Adobe geben, wird hiermit Adobe zugewiesen, einschließlich aller Rechte, Titel und Interessen an diesem Feedback.

+++

Navigieren Sie zu [https://firefly.adobe.com](https://firefly.adobe.com). Klicken Sie auf das Profilsymbol oben rechts und vergewissern Sie sich, dass Sie die richtige Instanz ausgewählt haben, die `--aepImsOrgName--` werden soll.

Wechseln Sie zu **Produktion**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw1.png)

Sie sollten das dann sehen. Klicken Sie **Workflow erstellen (Betaversion)**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw2.png)

## 1.7.1.1 Hintergrund entfernen

Um sich mit benutzerdefinierten Firefly-Workflows vertraut zu machen, implementieren Sie jetzt einen grundlegenden Anwendungsfall, der sich darauf konzentriert, den Hintergrund eines bestimmten Bildes zu entfernen.

Ändern Sie den Namen Ihres Workflows in `vangeluw - remove background`.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw3.png)

Öffnen Sie das **Bild**

![Benutzerdefinierte Firefly-Workflows](./images/ffcw4.png)

Wählen Sie **Hintergrund entfernen** und ziehen Sie diesen Knoten per Drag-and-Drop auf die Arbeitsfläche.

Sie müssen jetzt einen Eingabebildknoten und einen Ausgabebildknoten mit dem **Hintergrund entfernen** verbinden.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw5.png)

Scrollen Sie nach oben und gehen Sie zu **Eingabe und Ausgabe**. Klicken Sie auf den **Eingabebilder** und ziehen Sie ihn auf die Arbeitsfläche.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw6.png)

Sie sollten dann diese haben. Verbinden Sie den Knoten **Eingabebilder** mit dem Knoten **Hintergrund entfernen**, indem Sie den Mauszeiger über den blauen Punkt neben **Bild** auf dem Knoten **Eingabebilder** bewegen und eine Linie auf den blauen Punkt neben **Eingabebild** auf dem Knoten **Hintergrund entfernen** ziehen.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw7.png)

Sie sollten dann diese haben. Klicken Sie anschließend auf den Knoten **Ausgabebilder** und ziehen Sie ihn auf die Arbeitsfläche.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw8.png)

Sie sollten dann diese haben. Verbinden Sie den Knoten **Hintergrund entfernen** mit dem Knoten **Ausgabebilder**, indem Sie den Mauszeiger über den blauen Punkt neben **Ausgabebild** auf dem Knoten **Hintergrund entfernen** bewegen und eine Linie auf den blauen Punkt neben **Image** auf dem Knoten **Ausgabebilder** ziehen.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw9.png)

Sie sollten dann diese haben.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw10.png)

Ihr einfacher Workflow kann jetzt getestet werden. Laden Sie das Bild [phone.png](./assets/phone.png) auf Ihren Desktop.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw11.png)

Kehren Sie zu Ihrem Workflow zurück. Klicken Sie auf **Bereich (Drag-and** Drop) des Knotens **Eingabebilder**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw11a.png)

Wählen Sie die Datei **phone.png** aus. Klicken Sie auf **Öffnen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw12.png)

Sie sollten das dann sehen. Klicken Sie auf **Ausführen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw13.png)

Nach 1-2 Minuten sollten Sie dieses Ergebnis sehen.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw14.png)

## 1.7.1.2 Hintergrund + Zuschnitt entfernen

Sie sollten jetzt einen **Zuschneiden**-Knoten zur Arbeitsfläche hinzufügen. Gehen Sie im Menü zu **Bild** und scrollen Sie nach unten, um **Zuschneiden** zu finden. Ziehen Sie es auf die Arbeitsfläche.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw15.png)

Positionieren Sie **Knoten** Zuschneiden) zwischen dem Knoten **Hintergrund entfernen** und dem Knoten **Ausgabebild**.

Sie müssen jetzt die Verbindung zwischen dem Knoten **Hintergrund entfernen** und dem Knoten **Ausgabebild** entfernen. Doppelklicken Sie dazu auf die Linie zwischen den beiden Knoten.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw16.png)

Sie sollten dann diese haben. Verbinden Sie den Knoten **Hintergrund entfernen** mit dem Knoten **Zuschneiden** und verbinden Sie dann den Knoten **Zuschneiden** mit dem Knoten **Ausgabebild**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw17.png)

Aktivieren Sie das Kontrollkästchen für **Automatisches Zuschneiden**. Anschließend können Sie Ihren Workflow testen, indem Sie auf **Ausführen** klicken.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw18.png)

Nach 1-2 Minuten sollten Sie dies sehen, wodurch jetzt ein Bild mit einer anderen Auflösung angezeigt wird.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw19.png)

## 1.7.1.3 Hintergrund entfernen + Zuschneiden + zusammengesetztes Bild

Wählen Sie im Menü unter **Bild** den Knoten **Verbund-Bilder (2D)** aus und ziehen Sie ihn auf die Arbeitsfläche.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw20.png)

Fügen Sie eine zweite Verbindung zum Knoten **Zuschneiden** hinzu, indem Sie den blauen Punkt neben **Zugeschnittenes Bild** mit dem blauen Punkt neben **Eingabebild** auf dem Knoten **Composite Images (2D)** verbinden.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw21.png)

Wählen Sie im Menü unter **Eingabe und Ausgabe** einen **Eingabetext**-Knoten aus und ziehen Sie ihn auf die Arbeitsfläche.

Verbinden Sie den grünen Punkt neben **Text** im Knoten **Eingabetext** mit dem grünen Punkt neben **Prompt** im Knoten **Composite Images (2D)**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw22.png)

Sie sollten dann diese haben. Geben Sie die folgende Eingabeaufforderung im Knoten **Text eingeben** ein.

`magazine quality photo of a phone on a red pedestal with a pink background surrounded by origami style pink paper hearts`

Wählen Sie im Menü unter **Eingabe und Ausgabe** den Knoten **Ausgabebilder** und ziehen Sie ihn auf die Arbeitsfläche.

Verbinden Sie den blauen Punkt neben **zusammengesetztes Bild** im Knoten **zusammengesetzte Bilder (2D)** mit dem blauen Punkt neben **Eingabebild** im Knoten **Ausgabebild**.

Klicken Sie auf **Ausführen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw23.png)

Nach ein paar Minuten sollten Sie so etwas sehen, das Ihr Originalbild in einer Komposition basierend auf der Eingabeaufforderung in einer bestimmten Auflösung zeigt.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw24.png)

## 1.7.1.4 Hintergrund entfernen + Zuschneiden + zusammengesetztes Bild + Video generieren

Gehen Sie im Menü zu **Video**. Wählen Sie den Knoten **Video generieren** und ziehen Sie ihn auf die Arbeitsfläche.

Verbinden Sie den blauen Punkt neben **zusammengesetztes Bild** des Knotens **zusammengesetzte Bilder (2D)** mit dem blauen Punkt neben **Eingabebild** des Knotens **Video generieren**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw25.png)

Gehen Sie im Menü zu **Eingabe und Ausgabe**. Wählen Sie den Knoten **Eingabetext** aus und ziehen Sie ihn auf die Arbeitsfläche.

Verbinden Sie den grünen Punkt neben **Text** im Knoten **Eingabetext** mit dem grünen Punkt neben **Prompt** des Knotens **Video generieren**.

Geben Sie die `background hearts fluttering` im Knoten **Text eingeben** ein.

Gehen Sie im Menü zu **Eingabe und Ausgabe**. Wählen Sie den Knoten **Video ausgeben** und ziehen Sie ihn auf die Arbeitsfläche.

Verbinden Sie den violetten Punkt neben **Videoausgabe** des Knotens **Video generieren** mit dem violetten Punkt neben **Video** auf dem Knoten **Video**.

Klicken Sie auf **Ausführen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw26.png)

Nach ein paar Videos sollten Sie dies sehen, in dem ein Video basierend auf der Kombination aus dem bereitgestellten Bild und der Eingabeaufforderung angezeigt wird.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw27.png)

## 1.7.1.5

Sie haben dies nun für 1 Bild gemacht. Diesen Workflow können wir nun verwenden, allerdings für mehrere Bilder.

Laden Sie diese Bilder auf Ihren Desktop herunter:

- [watch.jpg](./assets/watch.jpg)
- [airpods.jpg](./assets/airpods.jpg)

![Benutzerdefinierte Firefly-Workflows](./images/ffcw28.png)

Gehen Sie in Ihrem Workflow zurück zum ersten Knoten **Eingabebilder**. Entfernt das aktuell ausgewählte Bild.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw29.png)

Klicken Sie auf den **Drag &amp; Drop** Bereich.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw30.png)

Wählen Sie die drei Bilder aus, die Sie heruntergeladen haben. Klicken Sie auf **Öffnen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw31.png)

Sie sollten das dann sehen. Klicken Sie auf **Ausführen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw32.png)

Nach einigen Minuten sollten Sie eine ähnliche Ausgabe sehen, wobei 3 Bilder und 3 Videos generiert werden.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw33.png)

## 1.7.1.5 Store in AEM Assets CS

In dieser Übung speichern Sie die Assets, die im Rahmen Ihres benutzerdefinierten Workflows in AEM Assets CS erstellt werden.

Zunächst sollten Sie einen neuen Ordner in Ihrer AEM Assets CS-Umgebung erstellen.

Navigieren Sie dazu zu [https://experience.adobe.com](https://experience.adobe.com). Klicken, um **Experience Manager Assets zu**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw50.png)

Wählen Sie Ihre AEM Assets CS-Umgebung aus, die `--aepUserLdap-- - CitiSignal AEM + ACCS` benannt werden soll.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw51.png)

Wechseln Sie zu **Assets** und klicken Sie auf **Ordner erstellen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw52.png)

Geben Sie den Namen ein: `--aepUserLdap-- - Firefly Custom Workflows`. Klicken Sie auf **Erstellen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw53.png)

Gehen Sie zurück zu Ihrem benutzerdefinierten Workflow und gehen Sie zum Knoten **Ausgabebilder**. Klicken Sie auf **Standard** und wählen Sie dann **AEM Assets** aus.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw57.png)

Daraufhin sollte dieses Popup angezeigt werden. Wählen Sie Ihr AEM Assets CS-Repository und dann den soeben erstellten Ordner aus, der folgenden Namen haben soll: `--aepUserLdap-- - Firefly Custom Workflows`. Klicken Sie auf **Auswählen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw54.png)

Wechseln Sie zum Knoten **Output Video**. Klicken Sie auf **Standard** und wählen Sie dann **AEM Assets** aus.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw55.png)

Daraufhin sollte dieses Popup angezeigt werden. Wählen Sie Ihr AEM Assets CS-Repository und dann den soeben erstellten Ordner aus, der folgenden Namen haben soll: `--aepUserLdap-- - Firefly Custom Workflows`. Klicken Sie auf **Auswählen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw56.png)

Sie sollten dann diese haben. Klicken Sie auf **Ausführen**.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw56a.png)

Nach einigen Minuten sollten die erstellten Assets im Ordner in AEM Assets CS verfügbar werden.

![Benutzerdefinierte Firefly-Workflows](./images/ffcw58.png)

## Nächste Schritte

Zurück zu [Workflow Builder](./workflowbuilder.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
