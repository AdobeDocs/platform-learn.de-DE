---
title: Erste Schritte mit Workfront, Frame.io und ESM
description: Erste Schritte mit Workfront, Frame.io und ESM
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 2f9a3eef-16ef-497c-97f7-377ff9ed2f82
source-git-commit: 8f746831d4a1481f8ccc14539273c4b16ca5170b
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 1%

---

# 1.8.1 Erste Schritte mit Workfront, Frame.io und ESM

## Terminologie 1.8.1.1 Workfront-Workflows

Im Folgenden finden Sie die wichtigsten Workfront-Objekte und -Konzepte:

| Name | Letzte Aktualisierung |
| ---------------------- | ------------ | 
| Portfolio | Eine Sammlung von Projekten mit einheitlichen Merkmalen. Diese Projekte konkurrieren normalerweise um dieselben Ressourcen, Budgets oder Zeitfenster. |
| Programm | Eine Untergruppe innerhalb eines Portfolios, in der ähnliche Projekte gruppiert werden können, um einen klar definierten Nutzen zu erzielen. |
| Projekt | Ein großer Arbeitsaufwand, der innerhalb eines bestimmten Zeitrahmens abgeschlossen werden muss und ein bestimmtes Budget und eine bestimmte Anzahl von Ressourcen erfordern muss. Um es überschaubar zu machen, unterteilen Sie das Projekt in eine Reihe von Aufgaben. Das Abschließen aller Aufgaben führt zum Abschluss des Projekts. |
| Projektvorlage | Sie können Projektvorlagen verwenden, um die meisten wiederholbaren Prozesse, Informationen und Einstellungen zu erfassen, die mit den Projekten in Ihrer Organisation verbunden sind. Nach dem Erstellen von Vorlagen können Sie sie an vorhandene Projekte anhängen oder zum Erstellen neuer Projekte verwenden. |
| Aufgabe | Eine Aktivität, die als Schritt zum Erreichen eines endgültigen Ziels (Abschluss des Projekts) ausgeführt werden muss. Aufgaben können niemals unabhängig voneinander existieren. Sie sind immer Teil eines Projekts. |
| Zuweisung | Ein Benutzer, ein Aufgabengebiet oder ein Team, das bzw. das einem Problem oder einer Aufgabe zugewiesen ist. Projekte, Portfolios oder Programme dürfen keine Zuweisungen haben. |
| Dokument/Version | Jede Datei, die an ein Objekt in Workfront angehängt ist. Jedes Mal, wenn dasselbe Dokument in dasselbe Objekt hochgeladen wird, wird ihm eine Versionsnummer zugewiesen. Benutzer können mehrere Optionen für eine frühere Version eines Dokuments anzeigen und ändern. |
| Validierung | Für ein bestimmtes Arbeitselement, z. B. eine Aufgabe, ein Dokument oder eine Arbeitszeittabelle, kann es erforderlich sein, dass ein Verantwortlicher oder ein anderer Benutzer das Arbeitselement abzeichnet. Dieser Prozess der Abzeichnung wird als Genehmigung bezeichnet. |


Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Klicken, um **Workfront zu**.

![Workfront-Planung](./images/wfpl1.png)

Sie werden es dann sehen.

![WF](./images/wfb1.png)

## 1.8.1.2 Workfront Blueprint aktivieren

Im nächsten Schritt erstellen Sie ein neues Projekt mithilfe einer Vorlage. Adobe Workfront stellt eine Reihe verfügbarer Blueprints bereit, die nur aktiviert werden müssen.

Für den Anwendungsfall von CitiSignal ist die Blueprint **Integrierte Kampagnenausführung** zu verwenden.

Um diese Blueprint zu installieren, öffnen Sie das Menü und wählen Sie **Blueprints**.

![WF](./images/blueprint1.png)

Wählen Sie den Filter **Marketing** und scrollen Sie dann nach unten, um den Blueprint **Integrierte Kampagnenausführung** zu finden. Klicken Sie auf **Installieren**.

![WF](./images/blueprint2.png)

Klicken Sie auf **Fortfahren**.

![WF](./images/blueprint3.png)

Ändern Sie **Name der Projektvorlage** in `--aepUserLdap-- - Integrated Campaign Execution`.

Klicken Sie **Blueprint installieren**.

![WF](./images/blueprint4.png)

Nach einigen Minuten wird die Blueprint installiert.

![WF](./images/blueprint6.png)

## 1.8.1.3 Neues Projekt erstellen

Öffnen Sie das **Menü** und gehen Sie zu **Portfolios**.

![WF](./images/wfp6a.png)

Klicken Sie auf **+ Neue Portfolio**.

![WF](./images/wfpfolio1.png)

Geben Sie den Portfolionamen `--aepUserLdap-- - CitiSignal`.

![WF](./images/wfpfolio2.png)

Gehen Sie zu **Programme** und klicken Sie auf **+ Neues Programm**. Wählen Sie **Neues Programm** aus.

![WF](./images/wfnp1.png)

Geben Sie den Programmnamen ein: `--aepUserLdap-- - CitiSignal Fiber Launch`.

![WF](./images/wfp6b.png)

Navigieren Sie in Ihrem Programm zu **Projekte**. Klicken Sie auf **+ Neues Projekt** und wählen Sie dann **Neues Projekt aus Vorlage**.

![WF](./images/wfp6.png)

Wählen Sie die `--aepUserLdap-- - Integrated Campaign Execution` aus und klicken Sie auf **Vorlage verwenden**.

![WF](./images/wfp6g.png)

Sie sollten das dann sehen. Ändern Sie den Namen in `--aepUserLdap-- - CitiSignal Fiber Launch Winter 2026` und klicken Sie auf **Projekt erstellen**.

![WF](./images/wfp6c.png)

Ihr Projekt ist jetzt erstellt. Gehen Sie zu **Projektdetails**.

![WF](./images/wfp6h.png)

Gehen Sie zu **Projektdetails**. Klicken Sie, um den aktuellen Text unter **Beschreibung** auszuwählen.

Legen Sie die Beschreibung auf `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.` fest

Klicken Sie **Änderungen speichern**.

![WF](./images/wfp6e.png)

Ihr Projekt kann jetzt verwendet werden.

![WF](./images/wfp7.png)

Die Aufgaben und Abhängigkeiten im Projekt wurden auf der Grundlage der von Ihnen ausgewählten Vorlage erstellt und als festgelegt. Projektbesitzer. Der Status des Projekts wurde auf &quot;**&quot;**. Sie können den Status des Projekts ändern, indem Sie einen anderen Wert in der Liste auswählen.

![WF](./images/wfp7z.png)

## 1.8.1.4 der Projektansicht in Frame.io

Navigieren Sie zu [https://next.frame.io/](https://next.frame.io/){target="_blank"}. Melden Sie sich an und wählen Sie die zu verwendende Instanz aus, in diesem Beispiel **Experience Platform International ESM**. Sie werden feststellen, dass in Frame.io bereits ein Ordner für das soeben erstellte Projekt vorhanden ist. Der Ordner wird nach dem zuvor eingegebenen Projektnamen benannt.

Dies ist eine Funktion von Enterprise Storage Management, einer Cloud-basierten Speicherlösung, die als zentrales Repository für Assets in allen Adobe-Unternehmensprodukten dient, einschließlich Workfront und Frame.io.

Zu den wichtigsten Vorteilen von Adobe Enterprise Storage gehören:

- Unified Storage Layer für das Kreativ- und Arbeits-Management von Assets
- Zentralisierte Berechtigungen über das Adobe Identity Management System (IMS) für eine sichere Zugriffskontrolle
- End-to-End-Sichtbarkeit von Assets in Workfront und Frame.io
- Skalierbares Speicher- und Kontingent-Management für Unternehmensanforderungen

![WF](./images/fio1.png)

## 1.8.1.5 Neue Aufgabe erstellen

Zurück zu Workfront. Navigieren Sie zu **Aufgaben**, bewegen Sie den Mauszeiger über die Aufgabe **Mit dem Erstellen von Design-** beginnen und klicken Sie auf die drei Punkte **…**.

![WF](./images/wfp7a.png)

Wählen Sie die Option **Aufgabe unten einfügen**.

![WF](./images/wfp7x.png)

Geben Sie diesen Namen für Ihre Aufgabe ein: `Create layout using approved assets and copy`.

Legen Sie das Feld **Arbeitsaufträge** auf die Rolle **Designer** fest.
Legen Sie das Feld **Dauer** auf **5 Tage** fest.
Setzen Sie den Vorgänger des Feldes auf **9**.
Geben Sie ein Datum für die Felder **Start am** und **Fällig am** ein (das Startdatum dieser Aufgabe sollte nach dem Enddatum der vorherigen Aufgabe geplant werden).

Klicken Sie auf eine andere Stelle im Bildschirm, um die neue Aufgabe zu speichern.

![WF](./images/wfp8.png)

Sie sollten das dann sehen. Klicken Sie auf die Aufgabe, um sie zu öffnen.

![WF](./images/wfp9.png)

Gehen Sie zu **Aufgabendetails** und legen Sie das Feld **Beschreibung** auf: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Klicken Sie **Änderungen speichern**.

![WF](./images/wfp9a.png)

Sie sollten das dann sehen. Klicken Sie auf das **Arbeitsaufträge** und wählen Sie **Mir zuweisen**.

![WF](./images/wfpwlb7.png)

Klicken Sie auf **Speichern**.

![WF](./images/wfpwlb8.png)

Klicken Sie **Bearbeiten**.

![WF](./images/wfpwlb9.png)

Sie sollten das dann sehen.

![WF](./images/wfpwlb10.png)

Im Rahmen dieser Aufgabe muss ein neues Asset erstellt werden. Im nächsten Schritt stellen Sie zunächst Referenzbilder in Workfront bereit, damit der Designer weiß, was erwartet wird. Anschließend wechseln Sie in die Rolle von Designer und erstellen dieses Asset selbst mit Adobe Express.

## 1.8.1.6 Hochladen von Referenzbildern

Laden Sie die Referenzbilder [hier](./assets/reference_images.zip) auf Ihren Desktop herunter und entpacken Sie sie.

![WF](./images/wfrefimg1.png)

Navigieren Sie in Workfront zur Ebene **Projekt** .

![WF](./images/wfrefimg2.png)

Navigieren Sie zu **Dokumente**, klicken Sie auf **+ Neu hinzufügen** wählen Sie dann **Dokument** aus.

![WF](./images/wfrefimg3.png)

Navigieren Sie zu dem Ordner, den Sie heruntergeladen haben und der die Referenzbilder enthält. Wählen Sie alle Bilder aus und klicken Sie auf **Öffnen**.

![WF](./images/wfrefimg4.png)

Nach einigen Minuten werden alle Bilder hochgeladen und an das Projekt angehängt.

![WF](./images/wfrefimg5.png)

Nachdem die Referenzbilder eingerichtet sind, kann der Designer jetzt das neue Asset für diese Kampagne erstellen.

## Nächste Schritte

Nächster Schritt: [Erstellen Sie ein neues Asset, überprüfen und genehmigen Sie es](./ex2.md){target="_blank"}

Gehen Sie zurück zu [Einheitliche Prüfung und Genehmigung mit Workfront, Frame.io und Enterprise Storage Management](./esm.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
