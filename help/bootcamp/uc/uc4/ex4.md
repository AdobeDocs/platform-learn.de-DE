---
title: Bootcamp - Customer Journey Analytics - Datenvorbereitung in Analysis Workspace
description: Bootcamp - Customer Journey Analytics - Datenvorbereitung in Analysis Workspace
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Workspace Basics, Calculated Metrics
exl-id: 6a9fc1a4-9a6a-43f2-9393-815f9dc2cb4e
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 2%

---

# 4.4 Datenvorbereitung in Analysis Workspace

## Ziele

- Grundlegendes zur Benutzeroberfläche von Analysis Workspace in CJA
- Verstehen der Konzepte der Datenvorbereitung in Analysis Workspace
- Erfahren Sie, wie Sie Datenberechnungen durchführen

## 4.4.1 Analysis Workspace-Benutzeroberfläche in CJA

Analysis Workspace beseitigt alle typischen Einschränkungen eines einzelnen Analytics-Berichts. Sie bietet eine robuste, flexible Arbeitsfläche zum Erstellen benutzerdefinierter Analyseprojekte. Ziehen Sie eine beliebige Anzahl von Datentabellen, Visualisierungen und Komponenten (Dimensionen, Metriken, Segmente und Zeitgranularitäten) in ein Projekt. Erstellen Sie sofort Aufschlüsselungen und Segmente, erstellen Sie Kohorten für Analysen, erstellen Sie Warnhinweise, vergleichen Sie Segmente, führen Sie Fluss- und Fallout-Analysen durch und kuratieren und planen Sie Berichte für die Freigabe für alle Personen in Ihrem Unternehmen.

Customer Journey Analytics stellt diese Lösung auf Platform-Daten bereit. Wir empfehlen dringend, sich dieses vierminütige Übersichtsvideo anzusehen:

>[!VIDEO](https://video.tv.adobe.com/v/35109?quality=12&learn=on&enablevpops)

Wenn Sie Analysis Workspace noch nie verwendet haben, empfehlen wir dringend, sich dieses Video anzusehen:

>[!VIDEO](https://video.tv.adobe.com/v/35525?quality=12&learn=on&enablevpops&captions=ger)

### Erstellen eines Projekts

Jetzt ist es an der Zeit, Ihr erstes CJA-Projekt zu erstellen. Navigieren Sie zur Registerkarte Projekte in CJA.
Klicken Sie **Neu erstellen**.

![demo](./images/prmenu.png)

Sie werden es dann sehen. Wählen Sie **Leeres Projekt** aus und klicken Sie dann auf **Erstellen**.

![demo](./images/prmenu1.png)

Anschließend wird ein leeres Projekt angezeigt.

![demo](./images/premptyprojects.png)

Wählen Sie zunächst die richtige Datenansicht in der oberen rechten Ecke Ihres Bildschirms aus. In diesem Beispiel ist die auszuwählende Datenansicht `CJA Bootcamp - Omnichannel Data View`.

Als Nächstes speichern Sie Ihr Projekt und geben ihm einen Namen. Sie können den folgenden Befehl verwenden, um zu speichern:

| Betriebssystem | Abkürzung |
| ----------------- |-------------| 
| Windows | Strg+S |
| Mac | Befehl + S |

Daraufhin wird dieses Popup angezeigt:

![demo](./images/prsave.png)

Bitte diese Namenskonvention verwenden:

| Name | Beschreibung |
| ----------------- |-------------| 
| `yourLastName - Omnichannel Analysis` | `yourLastName - Omnichannel Analysis` |

Klicken Sie anschließend auf **Speichern**.

![demo](./images/prsave2.png)

## 4.4.2 Berechnete Metriken

Obwohl wir alle Komponenten in der Datenansicht organisiert haben, müssen Sie einige von ihnen noch anpassen, damit Business-Anwender bereit sind, mit ihrer Analyse zu beginnen. Außerdem können Sie bei jeder Analyse berechnete Metriken erstellen, um die Ergebnisse der Einblicke zu vertiefen.

Als Beispiel erstellen wir eine berechnete **Konversionsrate** unter Verwendung der Metrik **Käufe**/Ereignis, die wir in der Datenansicht definiert haben.

### Konversionsrate

Öffnen wir nun den Generator für berechnete Metriken. Klicken Sie auf das **+**, um Ihre erste berechnete Metrik in Analysis Workspace zu erstellen.

![demo](./images/pradd.png)

Der **Generator für berechnete**&quot; wird angezeigt:

![demo](./images/prbuilder.png)

Suchen Sie **Bestellungen** in der Liste der Metriken im Menü links. Klicken Sie unter **Metriken** auf **Alle anzeigen**

![demo](./images/calcbuildercr1.png)

Ziehen Sie nun die Metrik **Bestellungen** per Drag-and-Drop in die Definition der berechneten Metrik.

![demo](./images/calcbuildercr2.png)

In der Regel bedeutet Konversionsrate **Konversionen / Sitzungen**. Führen wir also dieselbe Berechnung auf der Arbeitsfläche für die berechnete Metrikdefinition durch. Suchen Sie die **Sitzungen** und ziehen Sie sie per Drag-and-Drop unter dem Ereignis **Bestellungen** in den Definitionsgenerator.

![demo](./images/calcbuildercr3.png)

Beachten Sie, dass der Operator Division automatisch ausgewählt wird.

![demo](./images/calcbuildercr4.png)

Die Konversionsrate wird im Allgemeinen in Prozent angegeben. Ändern wir also das Format in Prozent und wählen auch zwei Dezimalstellen aus.

![demo](./images/calcbuildercr5.png)

Ändern Sie abschließend den Namen und die Beschreibung der berechneten Metrik:

| Titel | Beschreibung |
| ----------------- |-------------| 
| yourLastName - Konversionsrate | yourLastName - Konversionsrate |

Auf dem Bildschirm wird etwas wie das folgende angezeigt:

![demo](./images/calcbuildercr6.png)

Vergessen Sie nicht, **berechnete** zu speichern.

![demo](./images/pr9.png)

## 4.4.3 Berechnete Dimensionen: Filter (Segmentierung) und Datumsbereiche

### Filter: Berechnete Dimensionen

Berechnungen dürfen nicht nur für Metriken durchgeführt werden. Bevor Sie mit einer Analyse beginnen, ist es auch interessant, einige **berechnete Dimensionen** zu erstellen. Das bedeutete **Segmente** zurück in Adobe Analytics. In Customer Journey Analytics werden diese Segmente als &quot;**&quot;**.

![demo](./images/prfilters.png)

Das Erstellen von Filtern hilft Business-Anwendern, die Analyse mit einigen wertvollen berechneten Dimensionen zu starten. Dadurch werden einige Aufgaben automatisiert und die Übernahme erleichtert. Hier einige Beispiele:

1. Eigene Medien, bezahlte Medien,
2. Neue und wiederkehrende Besuche
3. Kunden mit Transaktionsabbruch

Diese Filter können vor oder während des Analyseteils erstellt werden (was Sie in der nächsten Übung tun werden).

### Datumsbereiche: Berechnete Zeitdimensionen

Zeitdimensionen sind ein weiterer Typ berechneter Dimensionen. Einige werden bereits erstellt, aber Sie haben auch die Möglichkeit, in der Datenvorbereitungsphase eigene benutzerdefinierte Zeitdimensionen zu erstellen.

Mit diesen berechneten Zeitdimensionen helfen wir Analysten und Business-Anwendern, sich wichtige Daten zu merken und sie zum Filtern und Ändern der Berichtszeit zu verwenden. Typische Fragen und Zweifel, die uns bei der Analyse in den Sinn kommen:

- Wann war der Schwarze Freitag letztes Jahr? 21.-29.?
- Wann haben wir diese Fernsehkampagne im Dezember gestartet?
- Von wann bis wann haben wir die Sommerverkäufe 2018 getätigt? Ich möchte es mit 2019 vergleichen. Kennst du übrigens die genauen Tage im Jahr 2019?

![demo](./images/timedimensions.png)

Sie haben jetzt die Datenvorbereitung mit CJA Analysis Workspace abgeschlossen.

Nächster Schritt: [4.5-Visualisierung mithilfe von Customer Journey Analytics](./ex5.md)

[Zurück zu Benutzerfluss 4](./uc4.md)

[Zurück zu „Alle Module“](./../../overview.md)
