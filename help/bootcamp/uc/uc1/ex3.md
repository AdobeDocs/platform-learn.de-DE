---
title: Bootcamp - Echtzeit-Kundenprofil - Segment erstellen - Benutzeroberfläche
description: Bootcamp - Echtzeit-Kundenprofil - Segment erstellen - Benutzeroberfläche
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Segments
exl-id: 37d4a5e8-e2bc-4c8c-a74f-09f74ea79962
source-git-commit: ee5c0af17c12f1d90774a3a4150c9788e2368e39
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 3%

---

# 1.3 Segment erstellen - Benutzeroberfläche

In dieser Übung erstellen Sie ein Segment, indem Sie den Segmentaufbau von Adobe Experience Platform verwenden.

## Geschichte

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

Gehen Sie im Menü auf der linken Seite zu **Segmente**. Auf dieser Seite sehen Sie eine Übersicht über alle vorhandenen Segmente. Klicken Sie auf **+ Segment erstellen** -Schaltfläche, um mit der Erstellung eines neuen Segments zu beginnen.

![Segmentierung](./images/menuseg.png)

Sobald Sie sich im neuen Segment-Builder befinden, wird Ihnen sofort die **Attribute** Menüoption und **XDM Individual Profile** Referenz.

![Segmentierung](./images/segmentationui.png)

Da XDM die Sprache ist, die das Erlebnisgeschäft steuert, ist XDM auch die Grundlage für den Segment-Builder. Alle Daten, die in Platform erfasst werden, sollten XDM zugeordnet werden. Daher werden alle Daten Teil desselben Datenmodells, unabhängig davon, woher diese Daten stammen. Dies bietet Ihnen beim Erstellen von Segmenten einen großen Vorteil. So können Sie in dieser einzigen Segment Builder-Benutzeroberfläche Daten aus jedem beliebigen Ursprung im selben Workflow kombinieren. In Segment Builder erstellte Segmente können zur Aktivierung an Lösungen wie Adobe Target, Adobe Campaign und Adobe Audience Manager gesendet werden.

Jetzt müssen Sie ein Segment aller Kunden erstellen, die das Produkt angesehen haben **Real-Time CDP**.

Um dieses Segment zu erstellen, müssen Sie ein Erlebnisereignis hinzufügen. Klicken Sie auf die Schaltfläche **Veranstaltungen** im **Felder** Menüleiste.

![Segmentierung](./images/findee.png)

Als Nächstes sehen Sie die oberste Ebene. **XDM ExperienceEvents** Knoten. Klicken Sie auf **XDM ExperienceEvent**.

![Segmentierung](./images/see.png)

Navigieren Sie zu **Produktlistenelemente**.

![Segmentierung](./images/plitems.png)

Auswählen **Name** und ziehen Sie die **Name** -Objekt aus dem linken Menü auf die Arbeitsfläche des Segmentaufbaus in der **Veranstaltungen** Abschnitt. Daraufhin sehen Sie Folgendes:

![Segmentierung](./images/eewebpdtlname.png)

Der Vergleichsparameter sollte **gleich** und geben Sie im Eingabefeld **Echtzeit-Kundendatenplattform**.

![Segmentierung](./images/pv.png)

Jedes Mal, wenn Sie ein Element zum Segment Builder hinzufügen, können Sie auf die **Schätzung aktualisieren** -Schaltfläche, um eine neue Schätzung der Population in Ihrem Segment zu erhalten.

![Segmentierung](./images/refreshest.png)

As **Auswertungsmethode** auswählen **Edge**.

![Segmentierung](./images/evedge.png)

Geben wir schließlich Ihrem Segment einen Namen und speichern es.

Verwenden Sie als Namenskonvention:

- `yourLastName - Interest in Real-Time CDP`

Klicken Sie dann auf die **Speichern und schließen** zum Speichern des Segments.

![Segmentierung](./images/segmentname.png)

Sie werden jetzt wieder zur Segmentübersichtsseite zurückgeführt, auf der eine Beispielvorschau der Kundenprofile angezeigt wird, die für Ihr Segment qualifiziert sind.

![Segmentierung](./images/savedsegment.png)

Sie können jetzt mit der nächsten Übung fortfahren und Ihr Segment mit Adobe Target verwenden.

Nächster Schritt: [1.4 Maßnahmen ergreifen: Senden Ihres Segments an Adobe Target](./ex4.md)

[Zurück zum Benutzerfluss 1](./uc1.md)

[Zu allen Modulen zurückkehren](../../overview.md)
