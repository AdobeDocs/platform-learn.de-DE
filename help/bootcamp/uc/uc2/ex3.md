---
title: Bootcamp - Journey Optimizer Journey und E-Mail erstellen
description: Bootcamp - Journey Optimizer Journey und E-Mail erstellen
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Journeys
exl-id: 138a70fa-fe50-4585-b47f-150db4770c3d
source-git-commit: cd59a41f4533f18a54d80298ee9faf3a8ba3c6e7
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 5%

---

# 2.3 Journey und E-Mail-Nachricht erstellen

In dieser Übung konfigurieren Sie die Journey, die ausgelöst werden muss, wenn jemand ein Konto auf der Demo-Website erstellt.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `Bootcamp`. Um von einer Sandbox in eine andere zu wechseln, klicken Sie auf **Prod** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel heißt die Sandbox **Bootcamp**. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 2.3.1 Journey erstellen

Klicken Sie im linken Menü auf **Journeys**. Klicken Sie anschließend auf **Journey erstellen**, um eine neue Journey zu erstellen.

![ACOP](./images/createjourney.png)

Daraufhin wird ein leerer Journey-Bildschirm angezeigt.

![ACOP](./images/journeyempty.png)

In der vorherigen Übung haben Sie ein neues &quot;**&quot;**. Sie haben ihn wie `yourLastNameAccountCreationEvent` benannt und `yourLastName` durch Ihren Nachnamen ersetzt. Dies war das Ergebnis der Erstellung des Ereignisses:

![ACOP](./images/eventdone.png)

Jetzt müssen Sie dieses Ereignis als Beginn dieser Journey nehmen. Dies können Sie tun, indem Sie zur linken Seite Ihres Bildschirms gehen und in der Ereignisliste nach Ihrem Ereignis suchen.

![ACOP](./images/eventlist.png)

Wählen Sie Ihr Ereignis aus und ziehen Sie es per Drag-and-Drop auf die Journey-Arbeitsfläche. Ihr Journey sieht nun wie folgt aus:

![ACOP](./images/journeyevent.png)

Als zweiten Schritt auf der Journey müssen Sie einen kurzen &quot;**&quot;-** hinzufügen. Gehen Sie auf der linken Seite Ihres Bildschirms zum Abschnitt **Orchestrierung**, um dies zu finden. Sie verwenden Profilattribute und müssen sicherstellen, dass diese im Echtzeit-Kundenprofil enthalten sind.

![ACOP](./images/journeywait.png)

Ihr Journey sieht jetzt wie folgt aus. Auf der rechten Seite des Bildschirms müssen Sie die Wartezeit konfigurieren. Auf 1 Minute einstellen. Dadurch haben Sie genügend Zeit, damit die Profilattribute verfügbar sind, nachdem das Ereignis ausgelöst wird.

![ACOP](./images/journeywait1.png)

Klicken Sie auf **OK**, um Ihre Änderungen zu speichern.

Als dritten Schritt auf der Journey müssen Sie eine „E-**&quot;-** hinzufügen. Gehen Sie auf der linken Seite des Bildschirms zu **Aktionen**, wählen Sie die Aktion **E-Mail** aus und ziehen Sie sie dann per Drag-and-Drop auf den zweiten Knoten in Ihrem Journey. Jetzt seht ihr das.

![ACOP](./images/journeyactions.png)

Legen Sie die **Kategorie** auf **Marketing** fest und wählen Sie eine E-Mail-Oberfläche aus, mit der Sie E-Mails senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **E-Mail**. Stellen Sie sicher, dass die Kontrollkästchen für **Klicks auf E-**) und **E-Mail-Öffnungen** beide aktiviert sind.

![ACOP](./images/journeyactions1.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

## 2.3.2 Nachricht erstellen

Um Ihre Nachricht zu erstellen, klicken Sie auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

Jetzt seht ihr das.

![ACOP](./images/journeyactions3.png)

Klicken Sie auf **Textfeld** Betreffzeile“.

![Journey Optimizer](./images/msg5.png)

Beginnen Sie im Textbereich mit dem Schreiben **Hi**

![Journey Optimizer](./images/msg6.png)

Die Betreffzeile ist noch nicht fertig. Als Nächstes müssen Sie das Personalisierungs-Token für das Feld **Vorname“**, das unter `profile.person.name.firstName` gespeichert ist. Scrollen Sie im linken Menü nach unten, um das Element **Person** zu finden, und klicken Sie auf den Pfeil, um eine Ebene tiefer zu gehen.

![Journey Optimizer](./images/msg7.png)

Suchen Sie nun das Element **Vollständiger Name** und klicken Sie auf den Pfeil, um eine Ebene tiefer zu gehen.

![Journey Optimizer](./images/msg8.png)

Suchen Sie abschließend das Feld **Vorname** und klicken Sie auf das **+** daneben. Anschließend wird das Personalisierungs-Token im Textfeld angezeigt.

![Journey Optimizer](./images/msg9.png)

Als Nächstes fügen Sie den Text **hinzu, danke für die Anmeldung!**. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg10.png)

Dann bist du wieder hier. Klicken Sie auf **E-Mail an** Designer), um den Inhalt der E-Mail zu erstellen.

![Journey Optimizer](./images/msg11.png)

Im nächsten Bildschirm werden Sie mit drei verschiedenen Methoden zum Bereitstellen des E-Mail-Inhalts aufgefordert:

- **Von Grund auf gestalten**: Beginnen Sie mit einer leeren Arbeitsfläche und verwenden Sie den WYSIWYG-Editor, um Struktur- und Inhaltskomponenten per Drag-and-Drop zu verschieben und visuell zum Erstellen des E-Mail-Inhalts zu verwenden.
- **Eigenen Code erstellen** Erstellen Sie Ihre eigene E-Mail-Vorlage, indem Sie sie mithilfe von HTML codieren
- **HTML importieren**: Importieren Sie eine vorhandene HTML-Vorlage, die Sie bearbeiten können.

Klicken Sie **HTML importieren**. Alternativ können Sie auf **Gespeicherte Vorlagen** klicken und die Vorlage **Bootcamp - E-Mail-Vorlage** auswählen.

![Journey Optimizer](./images/msg12.png)

Wenn Sie **HTML importieren** ausgewählt haben, können Sie jetzt die Datei **mailtemplatebootcamp.html) per Drag-and-Drop**, die Sie ([) ](../../assets/html/mailtemplatebootcamp.html.zip) können. Klicken Sie auf Importieren.

![Journey Optimizer](./images/msg13.png)

Anschließend wird diese standardmäßige E-Mail-Vorlage angezeigt:

![Journey Optimizer](./images/msg14.png)

Personalisieren wir die E-Mail. Klicken Sie neben dem Text **Hallo** und dann auf das Symbol **Personalization hinzufügen**.

![Journey Optimizer](./images/msg35.png)

Als Nächstes müssen Sie das Personalisierungs **Token „Vorname“**, das unter &quot;`profile.person.name.firstName`&quot; gespeichert ist. Suchen Sie im Menü das Element **Person**, schlüsseln Sie das Element **Full Name** auf und klicken Sie dann auf das Symbol **+**, um dem Ausdruckseditor das Feld Vorname hinzuzufügen.

Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg36.png)

Sie werden nun feststellen, wie das Personalisierungsfeld zu Ihrem Text hinzugefügt wurde.

![Journey Optimizer](./images/msg37.png)

Klicken Sie auf **Speichern**, um Ihre Nachricht zu speichern.

![Journey Optimizer](./images/msg55.png)

Kehren Sie zum Nachrichten-Dashboard zurück, indem Sie auf den **Pfeil** neben dem Betreffzeilentext in der oberen linken Ecke klicken.

![Journey Optimizer](./images/msg56.png)

Sie haben jetzt die Erstellung Ihrer Registrierungs-E-Mail abgeschlossen. Klicken Sie auf den Pfeil oben links, um zu Ihrem Journey zurückzukehren.

![Journey Optimizer](./images/msg57.png)

Klicken Sie auf **OK**.

![Journey Optimizer](./images/msg57a.png)

## 2.3.3 Publish auf Ihrem Journey

Sie müssen Ihrem Journey dennoch einen Namen geben. Klicken Sie dazu auf das **Bleistift**-Symbol oben links auf Ihrem Bildschirm.

![ACOP](./images/journeyname.png)

Geben Sie hier den Namen der Journey ein. Bitte verwenden Sie `yourLastName - Account Creation Journey`. Klicken Sie auf **OK**, um die Änderungen zu speichern.

![ACOP](./images/journeyname1.png)

Sie können Ihren Journey jetzt veröffentlichen, indem Sie auf **Publish** klicken.

![ACOP](./images/publishjourney.png)

Klicken Sie erneut auf **** Publish.

![ACOP](./images/publish1.png)

Sie sehen dann eine grüne Bestätigungsleiste, dass Ihr Journey jetzt veröffentlicht ist.

![ACOP](./images/published.png)

Sie haben jetzt diese Übung beendet.

Nächster Schritt: [2.4 Journey testen](./ex4.md)

[Zurück zu Benutzerfluss 2](./uc2.md)

[Zurück zu „Alle Module“](../../overview.md)