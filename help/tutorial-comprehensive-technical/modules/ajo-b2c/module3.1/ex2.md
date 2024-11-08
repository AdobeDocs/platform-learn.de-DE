---
title: Journey Optimizer Erstellen Ihrer Journey- und E-Mail-Nachricht
description: Journey Optimizer E-Mail-Nachricht erstellen
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 6%

---

# 3.1.2 Journey und E-Mail-Nachricht erstellen

In dieser Übung konfigurieren Sie die Journey und die Nachricht, die ausgelöst werden muss, wenn ein Benutzer ein Konto auf der Demowebsite erstellt.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der Ansicht **Home** Ihrer Sandbox `--aepSandboxName--`.

![ACOP](./images/acoptriglp.png)

## 3.1.2.1 Journey erstellen

Klicken Sie im linken Menü auf **Journeys**. Klicken Sie anschließend auf **Journey erstellen** , um eine neue Journey zu erstellen.

![ACOP](./images/createjourney.png)

Dann sehen Sie einen leeren Journey-Bildschirm.

![ACOP](./images/journeyempty.png)

In der vorherigen Übung haben Sie ein neues **Ereignis** erstellt. Sie haben es wie diese `ldapAccountCreationEvent` benannt und `ldap` durch Ihre LDAP ersetzt. Dies war das Ergebnis der Ereigniserstellung:

![ACOP](./images/eventdone.png)

Jetzt müssen Sie dieses Ereignis als Beginn dieser Journey nehmen. Gehen Sie dazu zur linken Seite des Bildschirms und suchen Sie in der Ereignisliste nach Ihrem Ereignis.

![ACOP](./images/eventlist.png)

Wählen Sie das Ereignis aus, ziehen Sie es auf die Journey-Arbeitsfläche und legen Sie es ab. Ihre Journey sieht nun wie folgt aus:

![ACOP](./images/journeyevent.png)

Als zweiten Schritt im Journey müssen Sie einen kurzen **Warten** -Schritt hinzufügen. Navigieren Sie zur linken Seite Ihres Bildschirms zum Abschnitt **Orchestrierung** , um dies zu finden. Sie verwenden Profilattribute und müssen sicherstellen, dass sie in das Echtzeit-Kundenprofil eingetragen sind.

![ACOP](./images/journeywait.png)

Ihre Journey sieht jetzt so aus. Auf der rechten Bildschirmseite müssen Sie die Wartezeit konfigurieren. Setzen Sie es auf 1 Minute. Dadurch wird ausreichend Zeit für die Profilattribute zur Verfügung stehen, nachdem das Ereignis ausgelöst wurde.

![ACOP](./images/journeywait1.png)

Klicken Sie auf **OK** , um Ihre Änderungen zu speichern.

Als dritten Schritt im Journey müssen Sie eine **E-Mail** -Aktion hinzufügen. Navigieren Sie auf der linken Bildschirmseite zu **Aktionen**, wählen Sie die Aktion **E-Mail** aus und ziehen Sie sie per Drag-and-Drop auf den zweiten Knoten im Journey. Das sehen Sie jetzt.

![ACOP](./images/journeyactions.png)

Setzen Sie die **Kategorie** auf **Marketing** und wählen Sie eine E-Mail-Oberfläche aus, über die Sie E-Mails senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **E-Mail**. Stellen Sie sicher, dass die Kontrollkästchen für **Klicks auf E-Mail** und **E-Mail-Öffnungen** aktiviert sind.

![ACOP](./images/journeyactions1.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

## 3.1.2.2 Nachricht erstellen

Um Ihre Nachricht zu erstellen, klicken Sie auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

Das sehen Sie jetzt.

![ACOP](./images/journeyactions3.png)

Klicken Sie auf das Textfeld **Betreff**.

![Journey Optimizer](./images/msg5.png)

Beginnen Sie im Textbereich mit dem Schreiben von **Hi**

![Journey Optimizer](./images/msg6.png)

Die Betreffzeile ist noch nicht fertig. Als Nächstes müssen Sie das Personalisierungstoken für das Feld **Vorname** einfügen, das unter `profile.person.name.firstName` gespeichert ist. Scrollen Sie im linken Menü nach unten, um das Element **Person** zu suchen, und klicken Sie auf den Pfeil, um eine Ebene tiefer zu gehen.

![Journey Optimizer](./images/msg7.png)

Suchen Sie nun das Element **Vollständiger Name** und klicken Sie auf den Pfeil, um eine Ebene tiefer zu gehen.

![Journey Optimizer](./images/msg8.png)

Suchen Sie abschließend das Feld **Vorname** und klicken Sie auf das Symbol **+** daneben. Daraufhin wird das Personalisierungstoken im Textfeld angezeigt.

![Journey Optimizer](./images/msg9.png)

Fügen Sie als Nächstes den Text **hinzu, vielen Dank für die Anmeldung!**. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg10.png)

Du wirst dann wieder hier sein. Klicken Sie auf **E-Mail-Designer** , um den E-Mail-Inhalt zu erstellen.

![Journey Optimizer](./images/msg11.png)

Im nächsten Bildschirm werden Sie mit 3 verschiedenen Methoden aufgefordert, den Inhalt der E-Mail bereitzustellen:

- **Neuen Entwurf erstellen**: Beginnen Sie mit einer leeren Arbeitsfläche und verwenden Sie den WYSIWYG-Editor, um Struktur- und Inhaltskomponenten per Drag-and-Drop zu verschieben, um den E-Mail-Inhalt visuell zu erstellen.
- **Eigenen Code kodieren**: Erstellen Sie Ihre eigene E-Mail-Vorlage, indem Sie sie mit HTML kodieren.
- **HTML importieren**: Importieren Sie eine vorhandene HTML-Vorlage, die Sie bearbeiten können.

Klicken Sie auf **Design von Grund auf**.

![Journey Optimizer](./images/msg12.png)

Im linken Menü finden Sie die Strukturkomponenten, mit denen Sie die Struktur der E-Mail definieren können (Zeilen und Spalten).

![Journey Optimizer](./images/msg13.png)

Ziehen Sie eine Spalte **1:2 links** aus dem Menü in die Arbeitsfläche. Dies ist der Platzhalter für das Logo-Bild.

![Journey Optimizer](./images/msg14.png)

Ziehen Sie eine **1:1-Spalte** unter die vorherige Komponente. Dies ist der Bannerblock.

![Journey Optimizer](./images/msg15.png)

Ziehen Sie eine Spalte **1:2 links** unter die vorherige Komponente. Dies ist der eigentliche Inhalt mit einem Bild auf der linken Seite und Text auf der rechten Seite.

![Journey Optimizer](./images/msg16.png)

Als Nächstes ziehen Sie eine **1:1-Spalte** unter die vorherige Komponente. Dies ist die Fußzeile der E-Mail. Ihre Arbeitsfläche sollte jetzt wie folgt aussehen:

![Journey Optimizer](./images/msg17.png)

Als Nächstes verwenden wir Inhaltskomponenten, um Inhalte in diesen Bausteinen hinzuzufügen. Klicken Sie auf das Menüelement **Inhaltskomponenten** .

![Journey Optimizer](./images/msg18.png)

Ziehen Sie eine **Bild** -Komponente in die erste Zelle der ersten Zeile und legen Sie sie ab. Klicken Sie auf **Durchsuchen**.

![Journey Optimizer](./images/msg19.png)

Dann wirst du das sehen. Navigieren Sie zum Ordner **enable-assets** und wählen Sie die Datei **luma-logo.png** aus. Klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/msg21.png)

Sie sind jetzt wieder hier:

![Journey Optimizer](./images/msg25.png)

Wechseln Sie zu **Inhaltskomponenten** und ziehen Sie eine **Bild** -Komponente in die erste Zelle der ersten Zeile. Klicken Sie auf **Durchsuchen**.

![Journey Optimizer](./images/msg26.png)

Wechseln Sie im Popup-Fenster **Assets** zum Ordner **enable-assets** . In diesem Ordner finden Sie alle Assets, die zuvor vom Kreativteam vorbereitet und hochgeladen wurden. Wählen Sie **module23-thankyou-new.png** und klicken Sie auf **Select**.

![Journey Optimizer](./images/msg28.png)

Dann haben Sie Folgendes:

![Journey Optimizer](./images/msg30.png)

Wählen Sie das Bild aus und scrollen Sie im rechten Menü nach unten, bis die Reglerkomponente **Größe** Breite angezeigt wird. Verwenden Sie den Schieberegler, um die Breite auf &quot;f.i.&quot;zu ändern. **60%**.

![Journey Optimizer](./images/msg31.png)

Navigieren Sie als Nächstes zu **Inhaltskomponenten** und ziehen Sie eine **Text** -Komponente in die Strukturkomponente und legen Sie sie auf der vierten Zeile ab.

![Journey Optimizer](./images/msg33.png)

Wählen Sie den Standardtext **Geben Sie hier Ihren Text ein.** genau wie bei jedem Texteditor. Schreiben Sie stattdessen **Lieber**. Beachten Sie, dass die Text-Symbolleiste angezeigt wird, wenn Sie sich im Textmodus befinden.

![Journey Optimizer](./images/msg34.png)

Klicken Sie in der Symbolleiste auf das Symbol **Personalisierung hinzufügen** .

![Journey Optimizer](./images/msg35.png)

Als Nächstes müssen Sie das Personalisierungstoken **Vorname** mitbringen, das unter `profile.person.name.firstName` gespeichert ist. Suchen Sie im Menü das Element **Person** , führen Sie einen Drilldown zum Element **Vollständiger Name** durch und klicken Sie dann auf das Symbol **+** , um das Feld &quot;Vorname&quot;zum Ausdruckseditor hinzuzufügen.

Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg36.png)

Sie werden jetzt feststellen, wie Ihrem Text das Personalisierungsfeld hinzugefügt wurde.

![Journey Optimizer](./images/msg37.png)

Tippen Sie im selben Textfeld zweimal auf **Enter** , um zwei Zeilen hinzuzufügen und **Vielen Dank, dass Sie Ihr Konto bei Luma!** erstellt haben.

![Journey Optimizer](./images/msg38.png)

Die letzte Prüfung, die durchgeführt werden muss, um sicherzustellen, dass Ihre E-Mail bereit ist, besteht darin, sie in der Vorschau anzuzeigen. Klicken Sie auf die Schaltfläche **Inhalt simulieren** .

![Journey Optimizer](./images/msg50.png)

Bestimmen Sie zunächst, welches Profil Sie für die Vorschau verwenden möchten. Wählen Sie den Namespace **email** aus, indem Sie auf das Symbol neben dem Feld **Identitäts-Namespace eingeben** klicken.

Wählen Sie in der Liste der Identitäts-Namespaces den Namespace **E-Mail** aus.

Geben Sie im Feld **Identitätswert** die E-Mail-Adresse eines früheren Demoprofils ein, das bereits im Echtzeit-Kundenprofil gespeichert ist. Beispiel: **woutervangeluwe+06022022-01@gmail.com** und klicken Sie auf die Schaltfläche **Testprofil suchen** .

![Journey Optimizer](./images/msg53.png)

Sobald Ihr Profil in der Tabelle angezeigt wird, klicken Sie auf die Registerkarte **Vorschau** , um auf den Vorschaubildschirm zuzugreifen.

Wenn die Vorschau fertig ist, überprüfen Sie, ob die Personalisierung in der Betreffzeile korrekt ist. Der Text des Hauptteils sowie der Abmelde-Link werden als Hyperlink hervorgehoben.

Klicken Sie auf **Schließen** , um die Vorschau zu schließen.

![Journey Optimizer](./images/msg54.png)

Klicken Sie auf **Speichern** , um Ihre Nachricht zu speichern.

![Journey Optimizer](./images/msg55.png)

Gehen Sie zurück zum Nachrichten-Dashboard, indem Sie in der oberen linken Ecke auf den Pfeil **11} neben dem Betreffzeilentext klicken.**

![Journey Optimizer](./images/msg56.png)

Sie haben jetzt die Erstellung Ihrer Registrierungs-E-Mail abgeschlossen. Klicken Sie auf den Pfeil oben links, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/msg57.png)

Klicken Sie auf **OK**.

![Journey Optimizer](./images/msg57a.png)

## 3.1.2.3 Publish Ihre Journey

Sie müssen Ihrer Journey noch einen Namen geben. Klicken Sie dazu oben rechts auf dem Bildschirm auf das Symbol **Eigenschaften** .

![ACOP](./images/journeyname.png)

Dann können Sie hier den Namen des Journey eingeben. Verwenden Sie bitte `--aepUserLdap-- - Account Creation Journey`. Klicken Sie auf **OK**, um die Änderungen zu speichern.

![ACOP](./images/journeyname1.png)

Sie können Ihre Journey jetzt veröffentlichen, indem Sie auf **Publish** klicken.

![ACOP](./images/publishjourney.png)

Klicken Sie erneut auf **Publish**.

![ACOP](./images/publish1.png)

Sie sehen dann eine grüne Bestätigungsleiste, dass Ihre Journey jetzt veröffentlicht ist.

![ACOP](./images/published.png)

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [3.1.3 Aktualisieren Sie Ihre Datenerfassungseigenschaft und testen Sie Ihre Journey](./ex3.md)

[Zurück zu Modul 3.1](./journey-orchestration-create-account.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
