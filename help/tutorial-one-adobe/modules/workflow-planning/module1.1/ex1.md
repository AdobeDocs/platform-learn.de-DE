---
title: Erste Schritte mit Workfront Planning
description: Erste Schritte mit Workfront Planning
kt: 5342
doc-type: tutorial
exl-id: 26fa872b-c872-46b6-8f56-fa41696100da
source-git-commit: 9af7cc3e221ddacd8b6ddc02a2215b7d9c134d0a
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 1%

---

# 1.1.1 Erste Schritte mit Workfront Planning

## 1.1.1.1 CitiSignal-Kampagnenbeschreibung

Um den Kontext von CitiSignal und das, was sie erreichen wollen, zu verstehen, laden Sie sich die Campaign Brief von CitiSignal hier herunter: [CitiSignal-Fiber-Launch-Winter-2026.pdf](./../../../assets/brief/CitiSignal-Fiber-Launch-Winter-2026.pdf).

## 1.1.1.2 Workfront-Planungsterminologie

Im Folgenden finden Sie die wichtigsten Workfront-Planungsobjekte und -konzepte:

| Begriff | Erklärung |
| --- | ---|
| **Workspace** | Eine Sammlung von Datensatztypen, die den Betriebslebenszyklus einer bestimmten Organisation definieren. Ein Arbeitsbereich ist der Arbeitsrahmen einer Organisationseinheit. |
| **Datensatztyp** | Der Name der Objekttypen in Workfront Planning. Datensatztypen befüllen Arbeitsbereiche. Im Gegensatz zum Workfront-Workflow, bei dem die Objekttypen vordefiniert sind, können Sie in Workfront Planning Ihre eigenen Objekttypen erstellen. |
| **Eintrag** | Eine Instanz eines Datensatztyps. |
| **Workspace-Vorlage** | Sie können einen Arbeitsbereich mithilfe vordefinierter Vorlagen erstellen. Sie können die vordefinierten Datensatztypen und Felder in einer Vorlage verwenden oder eigene hinzufügen. |
| **Felder** | Felder sind Attribute, die Sie Datensatztypen hinzufügen können. Felder enthalten Informationen über den Datensatztyp. |

>[!NOTE]
>
>Es gibt Einschränkungen für die Anzahl der Workfront Planning-Objekte, die Sie erstellen können. Weitere Informationen finden Sie unter Übersicht über Adobe Workfront Planning-Objektbeschränkungen .

Sie werden nun praktisch anfangen, einige dieser Objekte selbst zu erstellen.

## 1.1.1.3 Workspace, Datensatztyp, Felder

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Klicken, um **Workfront zu**.

![Workfront-Planung](./images/wfpl1.png)

Klicken Sie in Workfront auf , um das Menü zu öffnen, und wählen Sie dann **Planung** aus.

![Workfront-Planung](./images/wfpl2.png)

Sie sollten das dann sehen. Klicken Sie **Workspace erstellen**.

![Workfront-Planung](./images/wfpl3.png)

Klicken Sie auf **Vorlage verwenden** für die Vorlage **Einfache Marketing-Verwaltung**.

![Workfront-Planung](./images/wfpl4.png)

Es wird jetzt ein neuer Arbeitsbereich erstellt. Bevor Sie fortfahren, müssen Sie den Namen des Arbeitsbereichs ändern. Klicken Sie auf die 3 Punkte **…** und wählen Sie **Bearbeiten**.

![Workfront-Planung](./images/wfpl5.png)

Ändern Sie den Namen in `--aepUserLdap-- - Basic: Marketing Management`. Klicken Sie auf **Speichern**.

![Workfront-Planung](./images/wfpl6.png)

Sie sollten dann diese haben.

![Workfront-Planung](./images/wfpl7a.png)

## 1.1.1.4-Taxonomien: Datensatztyp und Felder

Klicken **unter &quot;**&quot; auf **+ Datensatztyp hinzufügen** wählen Sie dann **Manuell hinzufügen** aus.

![Workfront-Planung](./images/wfpl7.png)

Anschließend sollte das Popup **Datensatztyp hinzufügen** angezeigt werden.

![Workfront-Planung](./images/wfpl8.png)

Aktualisieren Sie die folgenden Informationen auf der Registerkarte **Erscheinungsbild**:

- Ersetzen **Nicht benannter Datensatztyp** durch `Business Unit`.
- Beschreibung: `Defines which BU is leading campaign planning.`.
- Wählen Sie eine Farbe und eine Form für das Symbol Ihrer Wahl

Klicken Sie auf **Speichern**.

![Workfront-Planung](./images/wfpl9.png)

Klicken Sie, um den neu erstellten Datensatztyp **Geschäftseinheit** zu öffnen.

![Workfront-Planung](./images/wfpl10.png)

Es wird jetzt eine leere Tabellenansicht angezeigt, da für Ihren neu erstellten Datensatztyp noch keine Geschäftseinheitendatensätze definiert sind.

![Workfront-Planung](./images/wfpl11.png)

Klicken Sie auf die Dropdown-Schaltfläche im Feld **Startdatum** und wählen Sie dann **Löschen**.

![Workfront-Planung](./images/wfpl12.png)

Wählen Sie **Löschen** aus.

![Workfront-Planung](./images/wfpl13.png)

Klicken Sie auf die Dropdown-Schaltfläche im Feld **Enddatum** und wählen Sie dann **Löschen**.

![Workfront-Planung](./images/wfpl14.png)

Wählen Sie **Löschen** aus.

![Workfront-Planung](./images/wfpl15.png)

Klicken Sie anschließend auf das Symbol **+** , um ein neues Feld hinzuzufügen. Scrollen Sie in der Liste der verfügbaren Feldtypen nach unten und wählen Sie **Personen** aus.

![Workfront-Planung](./images/wfpl16.png)

Legen Sie **Name** des Felds auf `Business Unit Lead` fest und legen Sie die Beschreibung des Felds auf `Business Unit Lead responsible for budget and resources (VP, Head).` fest

Klicken Sie auf **Erstellen**.

![Workfront-Planung](./images/wfpl17.png)

Klicken Sie auf die 3 Punkte **…** auf dem ersten Datensatz und wählen Sie **Anzeigen**.

![Workfront-Planung](./images/wfpla1.png)

Legen Sie **Name** auf `Consumer Services` fest.

Legen Sie **Beschreibung** auf `Handles residential offerings like mobile plans, internet packages, and customer support.` fest.

Legen Sie **Business Unit Lead** selbst fest.

Klicken Sie abschließend auf den Pfeil, um zum vorherigen Bildschirm zurückzukehren.

![Workfront-Planung](./images/wfpla2.png)

Klicken Sie auf die 3 Punkte **…** auf dem zweiten Datensatz und wählen Sie **Anzeigen**.

![Workfront-Planung](./images/wfpla3.png)

Legen Sie **Name** auf `Enterprise & Business Solutions` fest

Legen Sie **Beschreibung** auf `Provides connectivity, cloud, and managed services to corporate clients and government entities.` fest

Legen Sie **Business Unit Lead** selbst fest.

Klicken Sie abschließend auf den Pfeil, um zum vorherigen Bildschirm zurückzukehren.

![Workfront-Planung](./images/wfpla4.png)

Klicken Sie auf die 3 Punkte **…** auf dem dritten Eintrag und wählen Sie **Anzeigen**.

![Workfront-Planung](./images/wfpla5.png)

Legen Sie **Name** auf `Sales & Marketing` fest

Legen Sie **Beschreibung** auf `Drives customer acquisition, brand strategy, advertising, and market segmentation.` fest

Legen Sie **Business Unit Lead** selbst fest.

Klicken Sie abschließend auf den Pfeil, um zum vorherigen Bildschirm zurückzukehren.

![Workfront-Planung](./images/wfpla6.png)

Sie haben jetzt einen neuen Datensatztyp erstellt, Sie haben sowohl Felder gelöscht als auch erstellt und 3 Geschäftseinheiten erstellt. Kehren Sie zum Workspace-Übersichtsbildschirm zurück, indem Sie auf den Pfeil oben links klicken.

![Workfront-Planung](./images/wfpl18.png)

Sie sollten das dann sehen.

![Workfront-Planung](./images/wfpl19.png)

## 1.1.1.5 operative Datensatztypen: Felder

Zum Öffnen hier klicken **Kampagnen**.

![Workfront-Planung](./images/wfpl20.png)

Klicken Sie auf das Symbol **+** , um ein neues Feld zu erstellen. Wählen Sie **Neue Verbindung** und dann **Geschäftseinheit** aus.

![Workfront-Planung](./images/wfpl21.png)

Behalten Sie die Standardeinstellungen bei. Klicken Sie auf **Erstellen**.

![Workfront-Planung](./images/wfpl22.png)

Wählen Sie **Überspringen** aus.

![Workfront-Planung](./images/wfpl23.png)

Das neue Feld wird dann in der Tabellenansicht angezeigt.

![Workfront-Planung](./images/wfpl24.png)

## 1.1.1.6 Erstellen eines Anfrageformulars

Klicken Sie im Bildschirm Kampagnen - Überblick auf die 3 Punkte **…** und wählen Sie dann **Anfrageformular erstellen**.

![Workfront-Planung](./images/wfpl25.png)

Ändern Sie den Namen in `Campaign Request Form`. Klicken Sie auf **Erstellen**.

![Workfront-Planung](./images/wfpl26.png)

In diesem Moment ist es nicht erforderlich, Änderungen am Formular vorzunehmen. Sie werden es ohne Änderungen verwenden. Klicken Sie zunächst auf **Speichern** und dann auf **Veröffentlichen**.

![Workfront-Planung](./images/wfpl27.png)

Klicken Sie auf den Pfeil oben links, um zum Bildschirm Forms anfragen zurückzukehren.

![Workfront-Planung](./images/wfpl28.png)

Klicken Sie auf den Pfeil oben links, um zum Bildschirm Kampagnen - Übersicht zurückzukehren.

![Workfront-Planung](./images/wfpl29.png)

## 1.1.1.7 Senden eines neuen Datensatzes mit dem Anfrageformular

Klicken Sie im Bildschirm Kampagnenübersicht auf **+ Neuer Datensatz**.

![Workfront-Planung](./images/wfpl31.png)

Wählen Sie **Anfrage senden** und klicken Sie auf **Weiter**.

![Workfront-Planung](./images/wfpl32.png)

Legen Sie den **Betreff** auf `--aepUserLdap-- - New Campaign Creation Request` fest.

Legen Sie **Kampagnenname** auf `--aepUserLdap-- - CitiSignal Fiber Launch` fest.

Legen Sie die **Kampagnenübersicht** auf fest:

```
The CitiSignal Fiber Launch campaign introduces CitiSignal’s flagship fiber internet service—CitiSignal Fiber Max—to key residential markets. This campaign is designed to build awareness, drive sign-ups, and establish CitiSignal as the go-to provider for ultra-fast, reliable, and future-ready internet. The campaign will highlight the product’s benefits for remote professionals, online gamers, and smart home families, using persona-driven messaging across digital and physical channels.
```

Füllen Sie die anderen Felder wie gewünscht aus.

Klicken Sie **Senden-Anfrage**.

![Workfront-Planung](./images/wfpl33.png)

Klicken Sie auf **X**, um das Popup zu schließen.

![Workfront-Planung](./images/wfpl34.png)

Die neu erstellte Kampagne sollte dann in der Übersicht zu sehen sein.

![Workfront-Planung](./images/wfpl35.png)

## 1.1.1.8 Erstellen von Portfolio und benutzerdefinierten Formularen

Im nächsten Schritt erstellen Sie eine Automatisierung, die Informationen aus der in Workfront Planning erstellten Kampagne übernimmt und diese Informationen in Workfront zum Erstellen eines Programms verwendet. Bevor Sie die Automatisierung erstellen können, müssen Sie in Workfront zunächst zwei Dinge konfigurieren: ein Portfolio und ein benutzerdefiniertes Formular.

Um das Portfolio zu erstellen, öffnen Sie das Menü und klicken Sie auf **Portfolios**.

![Workfront-Planung](./images/wfplss1.png)

Klicken Sie auf **+ Neue Portfolio**.

![Workfront-Planung](./images/wfplss2.png)

Legen Sie den Namen des Portfolios auf `--aepUserLdap-- - Marketing` fest.

![Workfront-Planung](./images/wfplss3.png)

Öffnen Sie anschließend das Menü und klicken Sie auf **Setup**, um das benutzerdefinierte Formular zu erstellen.

![Workfront-Planung](./images/wfplss4.png)

Wechseln Sie im linken Menü zu **Benutzerdefinierte Forms**, zu **Forms** und klicken Sie dann auf **+ Neues benutzerdefiniertes Formular**.

![Workfront-Planung](./images/wfplss5.png)

Wählen Sie **Programm** aus und klicken Sie auf **Weiter**.

![Workfront-Planung](./images/wfplss6.png)

Ändern Sie den Namen des Formulars in `--aepUserLdap-- - Program Information`.

![Workfront-Planung](./images/wfplss7.png)

Gehen Sie dann zu **Feldbibliothek** und suchen Sie nach `budget`. Ziehen Sie das vorhandene Feld **Budget** auf das Formular.

Klicken Sie auf **Übernehmen**.

![Workfront-Planung](./images/wfplss8.png)

Die Konfiguration Ihres benutzerdefinierten Formulars wurde jetzt gespeichert.

![Workfront-Planung](./images/wfplss9.png)

## Automatisierung 1.1.1.8

Nachdem das Portfolio und das benutzerdefinierte Formular erstellt wurden, können Sie nun die Automatisierung erstellen.

Klicken Sie, um das Menü zu öffnen, und wählen Sie dann **Planung** aus.

![Workfront-Planung](./images/wfpl36.png)

Klicken Sie auf , um den zuvor erstellten Arbeitsbereich mit dem Namen `--aepUserLdap-- - Basic: Marketing Management` zu öffnen.

![Workfront-Planung](./images/wfpl37.png)

Zum Öffnen hier klicken **Kampagnen**.

![Workfront-Planung](./images/wfpl38.png)

Klicken Sie im Bildschirm Kampagnen - Überblick auf die 3 Punkte **…** und wählen Sie dann **Automatisierungen verwalten**.

![Workfront-Planung](./images/wfpl40.png)

Klicken Sie auf **Neue Automatisierung**.

![Workfront-Planung](./images/wfpl41.png)

Legen Sie den Namen der Automatisierung auf `Campaign to Program` fest.

Legen Sie die Beschreibung auf `This automation will convert a Planning Campaign record to a Workfront Program.` fest

Klicken Sie auf **Speichern**.

![Workfront-Planung](./images/wfpl42.png)

Legen Sie **Aktion** auf **Programm erstellen** fest. Klicken Sie auf **+ Verbundenes Feld hinzufügen**.

![Workfront-Planung](./images/wfpl43.png)

Wählen Sie das **Programm-Portfolio**: `--aepUserLdap-- - Marketing`.

Wählen Sie dieses **benutzerdefinierte Formular** aus: `--aepUserLdap-- Program information`.

Klicken Sie auf **Speichern**.

![Workfront-Planung](./images/wfpl44.png)

Sie sollten das dann sehen. Klicken Sie auf den Pfeil, um zum Bildschirm Kampagnen - Übersicht zurückzukehren.

![Workfront-Planung](./images/wfpl45.png)

Aktivieren Sie das Kontrollkästchen vor der Kampagne, die Sie zuvor erstellt haben. Klicken Sie dann auf die Automatisierung **Kampagne in Programm**.

![Workfront-Planung](./images/wfpl46.png)

Nach einigen Sekunden sollte eine Bestätigung angezeigt werden, dass die Automatisierung erfolgreich abgeschlossen wurde. Das bedeutet, dass auf der Grundlage des Campaign-Objekts in Workfront Planning ein Programm in Workfront erstellt wurde.

![Workfront-Planung](./images/wfpl47.png)

Um das Programm in Workfront zu überprüfen, scrollen Sie nach rechts und klicken Sie in der Spalte **Verbundenes Programm** auf das Programm.

![Workfront-Planung](./images/wfpl48.png)

Sie sollten dann das Programm sehen, das gerade von der von Ihnen konfigurierten Automatisierung erstellt wurde.

![Workfront-Planung](./images/wfpl50.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md){target="_blank"}

Zurück zu [Einführung in Workfront Planning](./wfplanning.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
