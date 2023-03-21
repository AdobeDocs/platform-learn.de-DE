---
title: Bootcamp - Journey Optimizer Erstellen Ihrer Journey- und E-Mail-Nachricht
description: Bootcamp - Journey Optimizer Erstellen Ihrer Journey- und E-Mail-Nachricht
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 138a70fa-fe50-4585-b47f-150db4770c3d
source-git-commit: f018e3aae714879de0cccb3a47b1f2242b57abc1
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 5%

---

# 2.3 Journey und E-Mail-Nachricht erstellen

In dieser Übung konfigurieren Sie die Journey, die ausgelöst werden muss, wenn jemand ein Konto auf der Demowebsite erstellt.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `Bootcamp`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **Prod** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **Bootcamp**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 2.3.1 Journey erstellen

Klicken Sie im linken Menü auf **Journeys**. Klicken Sie anschließend auf **Journey erstellen** , um eine neue Journey zu erstellen.

![ACOP](./images/createjourney.png)

Dann sehen Sie einen leeren Journey-Bildschirm.

![ACOP](./images/journeyempty.png)

In der vorherigen Übung haben Sie eine neue **Ereignis**. Sie haben es wie folgt benannt: `yourLastNameAccountCreationEvent` und ersetzt `yourLastName` mit Ihrem Nachnamen. Dies war das Ergebnis der Ereigniserstellung:

![ACOP](./images/eventdone.png)

Jetzt müssen Sie dieses Ereignis als Beginn dieser Journey nehmen. Gehen Sie dazu zur linken Seite des Bildschirms und suchen Sie in der Ereignisliste nach Ihrem Ereignis.

![ACOP](./images/eventlist.png)

Wählen Sie das Ereignis aus, ziehen Sie es auf die Journey-Arbeitsfläche und legen Sie es ab. Ihre Journey sieht nun wie folgt aus:

![ACOP](./images/journeyevent.png)

Als zweiten Schritt im Journey müssen Sie eine kurze **Warten** Schritt. Navigieren Sie zur linken Seite Ihres Bildschirms, um die **Orchestrierung** zu finden. Sie verwenden Profilattribute und müssen sicherstellen, dass sie in das Echtzeit-Kundenprofil eingetragen sind.

![ACOP](./images/journeywait.png)

Ihre Journey sieht jetzt so aus. Auf der rechten Bildschirmseite müssen Sie die Wartezeit konfigurieren. Setzen Sie es auf 1 Minute. Dadurch wird ausreichend Zeit für die Profilattribute zur Verfügung stehen, nachdem das Ereignis ausgelöst wurde.

![ACOP](./images/journeywait1.png)

Klicken **Ok** , um Ihre Änderungen zu speichern.

Als dritten Schritt im Journey müssen Sie eine **Email** Aktion. Navigieren Sie zur linken Seite Ihres Bildschirms, um **Aktionen**, wählen Sie die **Email** -Aktion und ziehen Sie sie dann per Drag-and-Drop auf den zweiten Knoten im Journey. Das sehen Sie jetzt.

![ACOP](./images/journeyactions.png)

Legen Sie die **Kategorie** nach **Marketing** und wählen Sie eine E-Mail-Oberfläche aus, über die Sie E-Mails versenden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **Email**. Stellen Sie sicher, dass die Kontrollkästchen für **Klicks auf E-Mail** und **E-Mail-Öffnungen** beide aktiviert sind.

![ACOP](./images/journeyactions1.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

## 2.3.2 Nachricht erstellen

Um Ihre Nachricht zu erstellen, klicken Sie auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

Das sehen Sie jetzt.

![ACOP](./images/journeyactions3.png)

Klicken Sie auf **Betreff** Textfeld.

![Journey Optimizer](./images/msg5.png)

Beginnen Sie im Textbereich mit dem Schreiben **Hi**

![Journey Optimizer](./images/msg6.png)

Die Betreffzeile ist noch nicht fertig. Als Nächstes müssen Sie das Personalisierungstoken für das Feld einfügen **Vorname** die unter `profile.person.name.firstName`. Scrollen Sie im linken Menü nach unten, um die **Person** und klicken Sie auf den Pfeil, um eine Ebene tiefer zu gehen.

![Journey Optimizer](./images/msg7.png)

Suchen Sie nun die **Vollständiger Name** und klicken Sie auf den Pfeil, um eine Ebene tiefer zu gehen.

![Journey Optimizer](./images/msg8.png)

Suchen Sie abschließend die **Vorname** und klicken Sie auf **+** daneben unterschreiben. Daraufhin wird das Personalisierungstoken im Textfeld angezeigt.

![Journey Optimizer](./images/msg9.png)

Fügen Sie als Nächstes den Text hinzu **, danke für die Anmeldung!**. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg10.png)

Du wirst dann wieder hier sein. Klicken **Email Designer** um den Inhalt der E-Mail zu erstellen.

![Journey Optimizer](./images/msg11.png)

Im nächsten Bildschirm werden Sie mit 3 verschiedenen Methoden aufgefordert, den Inhalt der E-Mail bereitzustellen:

- **Design von Grund auf neu**: Beginnen Sie mit einer leeren Arbeitsfläche und verwenden Sie den WYSIWYG-Editor, um Struktur- und Inhaltskomponenten per Drag-and-Drop zu verschieben, um den Inhalt der E-Mail visuell zu erstellen.
- **Eigene Code**: Erstellen Sie eine eigene E-Mail-Vorlage durch Codierung mithilfe von HTML
- **HTML importieren**: Importieren Sie eine vorhandene HTML-Vorlage, die Sie bearbeiten können.

Klicken **HTML importieren**. Alternativ können Sie auf **Gespeicherte Vorlagen** und wählen Sie die Vorlage aus **Bootcamp - E-Mail-Vorlage**.

![Journey Optimizer](./images/msg12.png)

Wenn Sie **HTML importieren** können Sie jetzt die Datei per Drag-and-Drop verschieben **mailtemplatebootcamp.html** herunterladen [here](../../assets/html/mailtemplatebootcamp.html.zip). Wählen Sie Importieren.

![Journey Optimizer](./images/msg13.png)

Anschließend wird Ihnen diese Standard-E-Mail-Vorlage angezeigt:

![Journey Optimizer](./images/msg14.png)

Personalisieren wir die E-Mail. Klicken Sie neben dem Text auf **Hi** und klicken Sie dann auf **Personalisierung hinzufügen** Symbol.

![Journey Optimizer](./images/msg35.png)

Als Nächstes müssen Sie die **Vorname** Personalisierungstoken, das unter `profile.person.name.firstName`. Suchen Sie im Menü die **Person** -Element, Drilldown zum **Vollständiger Name** -Element und klicken Sie dann auf das **+** -Symbol, um das Feld Vorname zum Ausdruckseditor hinzuzufügen.

Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg36.png)

Sie werden jetzt feststellen, wie Ihrem Text das Personalisierungsfeld hinzugefügt wurde.

![Journey Optimizer](./images/msg37.png)

Klicken **Speichern** , um Ihre Nachricht zu speichern.

![Journey Optimizer](./images/msg55.png)

Gehen Sie zum Nachrichten-Dashboard zurück, indem Sie auf die Schaltfläche **Pfeil** neben dem Betreffzeilentext in der oberen linken Ecke.

![Journey Optimizer](./images/msg56.png)

Sie haben jetzt die Erstellung Ihrer Registrierungs-E-Mail abgeschlossen. Klicken Sie auf den Pfeil in der oberen linken Ecke, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/msg57.png)

Klicken Sie auf **OK**.

![Journey Optimizer](./images/msg57a.png)

## 2.3.3 Journey veröffentlichen

Sie müssen Ihrer Journey noch einen Namen geben. Klicken Sie hierzu auf die Schaltfläche **Eigenschaften** rechts oben auf dem Bildschirm angezeigt.

![ACOP](./images/journeyname.png)

Dann können Sie hier den Namen des Journey eingeben. Verwenden Sie `yourLastName - Account Creation Journey`. Klicken Sie auf **OK**, um die Änderungen zu speichern.

![ACOP](./images/journeyname1.png)

Sie können Ihre Journey jetzt veröffentlichen, indem Sie auf **Veröffentlichen**.

![ACOP](./images/publishjourney.png)

Klicken **Veröffentlichen** erneut.

![ACOP](./images/publish1.png)

Sie sehen dann eine grüne Bestätigungsleiste, dass Ihre Journey jetzt veröffentlicht ist.

![ACOP](./images/published.png)

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [2.4 Journey testen](./ex4.md)

[Zurück zum Benutzerfluss 2](./uc2.md)

[Zu allen Modulen zurückkehren](../../overview.md)