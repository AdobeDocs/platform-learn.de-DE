---
title: Foundation - Echtzeit-Kundenprofil - Erstellen eines Segments - Benutzeroberfläche
description: Foundation - Echtzeit-Kundenprofil - Erstellen eines Segments - Benutzeroberfläche
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 2462addc-6123-44e6-991c-0e5c21256448
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 3%

---

# 3.4 Segment erstellen - Benutzeroberfläche

In dieser Übung erstellen Sie ein Segment, indem Sie den Segmentaufbau von Adobe Experience Platform verwenden.

## Geschichte

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](../module2/images/sb1.png)

Gehen Sie im Menü auf der linken Seite zu **Segmente**. Auf dieser Seite sehen Sie eine Übersicht über alle vorhandenen Segmente. Klicken Sie auf **+ Segment erstellen** -Schaltfläche, um mit der Erstellung eines neuen Segments zu beginnen.

![Segmentierung](./images/menuseg.png)

Sobald Sie sich im neuen Segment-Builder befinden, wird Ihnen sofort die **Attribute** Menüoption und **XDM Individual Profile** Referenz.

![Segmentierung](./images/segmentationui.png)

Da XDM die Sprache ist, die das Erlebnisgeschäft steuert, ist XDM auch die Grundlage für den Segment-Builder. Alle Daten, die in Platform erfasst werden, sollten XDM zugeordnet werden. Daher werden alle Daten Teil desselben Datenmodells, unabhängig davon, woher diese Daten stammen. Dies bietet Ihnen beim Erstellen von Segmenten einen großen Vorteil. So können Sie in dieser einzigen Segment Builder-Benutzeroberfläche Daten aus jedem beliebigen Ursprung im selben Workflow kombinieren. In Segment Builder erstellte Segmente können zur Aktivierung an Lösungen wie Adobe Target, Adobe Campaign und Adobe Audience Manager gesendet werden.

Erstellen wir ein Segment, das alle **male** -Kunden.

Um zum Geschlechterattribut zu gelangen, müssen Sie XDM verstehen und kennen.

Geschlecht ist ein Attribut von Person, das unter Attribute zu finden ist. Um dorthin zu gelangen, klicken Sie auf **XDM Individual Profile**. Dann wirst du das sehen. Aus dem **XDM Individual Profile** auswählen **Person**.

![Segmentierung](./images/person.png)

Dann wirst du das sehen. In **Person**, können Sie die **Geschlecht** -Attribut. Ziehen Sie das Attribut Geschlecht in den Segment Builder.

![Segmentierung](./images/gender.png)

Jetzt können Sie aus den vorausgefüllten Optionen das spezifische Geschlecht auswählen. In diesem Fall wählen wir **Männlich**.

![Segmentierung](./images/genderselection.png)

Nach Auswahl **Männlich** können Sie eine Schätzung der Segmentpopulation erhalten, indem Sie die **Schätzung aktualisieren** Schaltfläche. Dies ist für einen Business-Anwender sehr hilfreich, damit er die Auswirkungen bestimmter Attribute auf die resultierende Segmentgröße sehen kann.

![Segmentierung](./images/segmentpreview.png)

Daraufhin wird eine Schätzung wie die folgende angezeigt:

![Segmentierung](./images/segmentpreviewest.png)

Als Nächstes sollten Sie Ihr Segment etwas verfeinern. Sie müssen ein Segment aller männlichen Kunden erstellen, die das Produkt angesehen haben **Proteus Fitness Jackshirt (Orange)**.

Um dieses Segment zu erstellen, müssen Sie ein Erlebnisereignis hinzufügen. Klicken Sie auf die Schaltfläche **Veranstaltungen** im **Felder** Menüleiste.

![Segmentierung](./images/findee.png)

Als Nächstes sehen Sie die oberste Ebene. **XDM ExperienceEvents** Knoten. Klicken Sie auf **XDM ExperienceEvent**.

![Segmentierung](./images/see.png)

Navigieren Sie zu **Produktlistenelemente**.

![Segmentierung](./images/plitems.png)

Auswählen **Name** und ziehen Sie die **Name** -Objekt aus dem linken Menü auf die Arbeitsfläche des Segmentaufbaus in der **Veranstaltungen** Abschnitt.

![Segmentierung](./images/eeweb.png)

Daraufhin sehen Sie Folgendes:

![Segmentierung](./images/eewebpdtlname.png)

Der Vergleichsparameter sollte **gleich** und geben Sie im Eingabefeld **MONTANA WIND JACKET**.

![Segmentierung](./images/pv.png)

Jedes Mal, wenn Sie ein Element zum Segment Builder hinzufügen, können Sie auf die **Schätzung aktualisieren** -Schaltfläche, um eine neue Schätzung der Population in Ihrem Segment zu erhalten.

Bisher haben Sie nur die Benutzeroberfläche zum Erstellen Ihres Segments verwendet, aber es gibt auch eine Code-Option zum Erstellen eines Segments.

Beim Erstellen eines Segments stellen Sie tatsächlich eine PQL-Abfrage (Profile Query Language) zusammen. Um den PQL-Code zu visualisieren, können Sie auf die **Codeansicht** Umschalter in der oberen rechten Ecke des Segment-Builders.

![Segmentierung](./images/codeview.png)

Jetzt können Sie die vollständige PQL-Anweisung sehen:

```sql
person.gender in ["male"] and CHAIN(xEvent, timestamp, [C0: WHAT(productListItems.exists(name.equals("MONTANA WIND JACKET", false)))])
```

Sie können auch eine Vorschau der Kundenprofile anzeigen, die Teil dieses Segments sind, indem Sie auf **Profile anzeigen**.

![Segmentierung](./images/previewprofiles.png)

![Segmentierung](./images/previewprofilesdtl.png)

Geben wir schließlich Ihrem Segment einen Namen und speichern es.

Verwenden Sie als Namenskonvention:

- `--demoProfileLdap-- - Male customers with interest in Montana Wind Jacket`

![Segmentierung](./images/segmentname.png)

Klicken Sie dann auf die **Speichern und schließen** zum Speichern Ihres Segments, woraufhin Sie zur Übersichtsseite Segment zurückgeleitet werden.

![Segmentierung](./images/savedsegment.png)

Sie können jetzt mit der nächsten Übung fortfahren und ein Segment über die API erstellen.

Nächster Schritt: [3.5 Segment erstellen - API](./ex5.md)

[Zurück zu Modul 3](./real-time-customer-profile.md)

[Zu allen Modulen zurückkehren](../../overview.md)
