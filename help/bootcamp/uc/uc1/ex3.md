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

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

Gehen Sie im Menü auf der linken Seite zu **Zielgruppen**. Auf dieser Seite werden Dashboards mit wesentlichen Informationen zu **Zielgruppe** Leistung.

![Segmentierung](./images/menuseg.png)

Klicken Sie auf **Durchsuchen** um einen Überblick über alle vorhandenen Zielgruppen zu erhalten. Klicken Sie auf **+ Zielgruppe erstellen** -Schaltfläche, um mit der Erstellung einer neuen Audience zu beginnen.


![Segmentierung](./images/segmentationui.png)

Daraufhin wird ein Pop-IP angezeigt, das Sie fragt, ob Sie **&quot;Audience erstellen&quot;** oder **&#39;Regel erstellen&#39;**. Auswählen **&#39;Regel erstellen&#39;** um fortzufahren, klicken Sie auf **erstellen**.

![Segmentierung][def]

Sobald Sie sich im Audience Builder befinden, sehen Sie sofort die **Attribute** Menüoption und **Individuelles XDM-Profil** Referenz.


Da XDM die Sprache ist, die das Erlebnisgeschäft steuert, ist XDM auch die Grundlage für den Audience Builder. Alle Daten, die in Platform erfasst werden, sollten XDM zugeordnet werden. Daher werden alle Daten Teil desselben Datenmodells, unabhängig davon, woher diese Daten stammen. Dies bietet Ihnen einen großen Vorteil beim Erstellen von Zielgruppen, da Sie in dieser einzigen Benutzeroberfläche des Zielgruppen-Builders Daten aus verschiedenen Quellen im selben Workflow kombinieren können. In Audience Builder erstellte Zielgruppen können an Lösungen wie Adobe Target, Adobe Campaign oder einen beliebigen anderen Aktivierungskanal gesendet werden.

Jetzt müssen Sie eine Zielgruppe aller Kunden erstellen, die das Produkt angesehen haben **Real-Time CDP**.

Um diese Zielgruppe zu erstellen, müssen Sie ein Erlebnisereignis hinzufügen. Klicken Sie auf die Schaltfläche **Veranstaltungen** im **Felder** Menüleiste.

![Segmentierung](./images/findee.png)

Als Nächstes sehen Sie die oberste Ebene. **XDM ExperienceEvents** Knoten. Klicken Sie auf **XDM ExperienceEvent**.

![Segmentierung](./images/see.png)

Navigieren Sie zu **Produktlistenelemente**.

![Segmentierung](./images/plitems.png)

Auswählen **Name** und ziehen Sie die **Name** -Objekt aus dem linken Menü auf die Arbeitsfläche des Zielgruppen-Builders in die **Veranstaltungen** Abschnitt. Daraufhin sehen Sie Folgendes:

![Segmentierung](./images/eewebpdtlname.png)

Der Vergleichsparameter sollte **gleich** und im Eingabefeld **Realtime CDP**.

![Segmentierung](./images/pv.png)

Jedes Mal, wenn Sie ein Element zum Audience Builder hinzufügen, können Sie auf die **Schätzung aktualisieren** -Schaltfläche, um eine neue Schätzung der Population in Ihrer Audience zu erhalten.

![Segmentierung](./images/refreshest.png)

As **Auswertungsmethode** auswählen **Edge**.

![Segmentierung](./images/evedge.png)

Geben wir schließlich Ihrer Audience einen Namen und speichern Sie sie.

Verwenden Sie als Namenskonvention:

- `yourLastName - Interest in Real-Time CDP`

Klicken Sie dann auf die **Speichern und schließen** zum Speichern der Audience.

![Segmentierung](./images/segmentname.png)

Sie gelangen jetzt wieder zur Übersichtsseite der Zielgruppe, auf der Sie eine Beispielvorschau der Kundenprofile sehen, die für Ihre Zielgruppe geeignet sind.

![Segmentierung](./images/savedsegment.png)

Sie können jetzt mit der nächsten Übung fortfahren und Ihre Zielgruppe mit Adobe Target verwenden.

Nächster Schritt: [1.4 Aktion durchführen: Senden Sie Ihre Audience an Adobe Target](./ex4.md)

[Zurück zum Benutzerfluss 1](./uc1.md)

[Zu allen Modulen zurückkehren](../../overview.md)


[def]: ./images/segmentationpopup.png
