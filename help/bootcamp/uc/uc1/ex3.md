---
title: Bootcamp - Echtzeit-Kundenprofil - Erstellen einer Zielgruppe - Benutzeroberfläche
description: Bootcamp - Echtzeit-Kundenprofil - Erstellen einer Zielgruppe - Benutzeroberfläche
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Audiences
exl-id: 37d4a5e8-e2bc-4c8c-a74f-09f74ea79962
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---

# 1.3 Erstellen einer Zielgruppe - Benutzeroberfläche

In dieser Übung erstellen Sie eine Zielgruppe, indem Sie Adobe Experience Platforms Audience Builder verwenden.

## Geschichte

Wechseln Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende [!UICONTROL Sandbox] ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

Navigieren Sie im Menü auf der linken Seite zu **Zielgruppen**. Auf dieser Seite werden Dashboards mit wesentlichen Informationen zur Leistung von **Zielgruppe** angezeigt.

![Segmentierung](./images/menuseg.png)

Klicken Sie auf **Durchsuchen** , um eine Übersicht über alle vorhandenen Zielgruppen anzuzeigen. Klicken Sie auf die Schaltfläche **+ Audience erstellen** , um mit der Erstellung einer neuen Audience zu beginnen.


![Segmentierung](./images/segmentationui.png)

Daraufhin wird ein Pop-IP angezeigt, das Sie fragt, ob Sie **&#39;Audience erstellen&#39;** oder **&#39;Regel erstellen&#39;** verwenden möchten. Wählen Sie **&#39;Build rule&#39;** aus, um fortzufahren, und klicken Sie auf **create**.

![Segmentierung][def]

Sobald Sie sich im Audience Builder befinden, sehen Sie sofort die Menüoption **Attribute** und den Verweis auf **XDM Individual Profile** .


Da XDM die Sprache ist, die das Erlebnisgeschäft steuert, ist XDM auch die Grundlage für den Audience Builder. Alle Daten, die in Platform erfasst werden, sollten XDM zugeordnet werden. Daher werden alle Daten Teil desselben Datenmodells, unabhängig davon, woher diese Daten stammen. Dies bietet Ihnen einen großen Vorteil beim Erstellen von Zielgruppen, da Sie in dieser einzigen Benutzeroberfläche des Zielgruppen-Builders Daten aus verschiedenen Quellen im selben Workflow kombinieren können. In Audience Builder erstellte Zielgruppen können an Lösungen wie Adobe Target, Adobe Campaign oder einen beliebigen anderen Aktivierungskanal gesendet werden.

Jetzt müssen Sie eine Zielgruppe aller Kunden erstellen, die das Produkt **Real-Time CDP** angesehen haben.

Um diese Zielgruppe zu erstellen, müssen Sie ein Erlebnisereignis hinzufügen. Sie können alle Erlebnisereignisse finden, indem Sie in der Menüleiste **Felder** auf das Symbol **Ereignisse** klicken.

![Segmentierung](./images/findee.png)

Als Nächstes sehen Sie den Knoten **XDM ExperienceEvents** der obersten Ebene. Klicken Sie auf **XDM ExperienceEvent**.

![Segmentierung](./images/see.png)

Wechseln Sie zu **Produktlistenelemente**.

![Segmentierung](./images/plitems.png)

Wählen Sie **Name** aus und ziehen Sie das Objekt **Name** aus dem linken Menü auf die Arbeitsfläche des Zielgruppen-Builders und legen Sie es in den Abschnitt **Ereignisse**. Daraufhin sehen Sie Folgendes:

![Segmentierung](./images/eewebpdtlname.png)

Der Vergleichsparameter sollte **gleich** sein und im Eingabefeld **Echtzeit-Kundendatenplattform** eingeben.

![Segmentierung](./images/pv.png)

Jedes Mal, wenn Sie ein Element zum Audience Builder hinzufügen, können Sie auf die Schaltfläche **Schätzung aktualisieren** klicken, um eine neue Schätzung der Population in Ihrer Audience zu erhalten.

![Segmentierung](./images/refreshest.png)

Wählen Sie als **Auswertungsmethode** **Edge** aus.

![Segmentierung](./images/evedge.png)

Geben wir schließlich Ihrer Audience einen Namen und speichern Sie sie.

Verwenden Sie als Namenskonvention:

- `yourLastName - Interest in Real-Time CDP`

Klicken Sie dann auf die Schaltfläche **Speichern und schließen** , um Ihre Audience zu speichern.

![Segmentierung](./images/segmentname.png)

Sie gelangen jetzt wieder zur Übersichtsseite der Zielgruppe, auf der Sie eine Beispielvorschau der Kundenprofile sehen, die für Ihre Zielgruppe geeignet sind.

![Segmentierung](./images/savedsegment.png)

Sie können jetzt mit der nächsten Übung fortfahren und Ihre Zielgruppe mit Adobe Target verwenden.

Nächster Schritt: [1.4 Aktion ausführen: Senden Sie Ihre Audience an Adobe Target](./ex4.md)

[Zurück zum Benutzerfluss 1](./uc1.md)

[Zu allen Modulen zurückkehren](../../overview.md)


[def]: ./images/segmentationpopup.png
