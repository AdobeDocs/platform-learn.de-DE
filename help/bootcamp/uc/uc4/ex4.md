---
title: Bootcamp - Customer Journey Analytics - Datenvorbereitung in Analysis Workspace
description: Bootcamp - Customer Journey Analytics - Datenvorbereitung in Analysis Workspace
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 6a9fc1a4-9a6a-43f2-9393-815f9dc2cb4e
source-git-commit: bc872b4fe440106475668eeb790242e1862875aa
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 2%

---

# 4.4 Datenvorbereitung in Analysis Workspace

## Ziele

- Grundlegendes zur Analysis Workspace-Benutzeroberfläche in CJA
- Grundlegendes zur Datenvorbereitung in Analysis Workspace
- Erfahren Sie, wie Sie Datenberechnungen durchführen.

## 4.4.1 Analysis Workspace-Benutzeroberfläche in CJA

Analysis Workspace beseitigt alle typischen Einschränkungen eines einzelnen Analytics-Berichts. Es bietet eine robuste, flexible Arbeitsfläche zum Erstellen benutzerdefinierter Analyseprojekte. Ziehen Sie per Drag-and-Drop eine beliebige Anzahl von Datentabellen, Visualisierungen und Komponenten (Dimensionen, Metriken, Segmente und Zeitgranularitäten) in ein Projekt. Erstellen Sie sofort Aufschlüsselungen und Segmente, erstellen Sie Kohorten für die Analyse, erstellen Sie Warnhinweise, vergleichen Sie Segmente, führen Sie Fluss- und Fallout-Analysen durch und kuratieren und planen Sie Berichte für die Freigabe für andere in Ihrem Unternehmen.

Customer Journey Analytics stellt diese Lösung auf die Platform-Daten. Es wird dringend empfohlen, sich dieses vierminütige Übersichtsvideo anzusehen:

>[!VIDEO](https://video.tv.adobe.com/v/35109?quality=12&learn=on)

Wenn Sie Analysis Workspace noch nie verwendet haben, empfehlen wir dringend, sich dieses Video anzusehen:

>[!VIDEO](https://video.tv.adobe.com/v/26266?quality=12&learn=on)

### Projekt erstellen

Jetzt ist es an der Zeit, Ihr erstes CJA-Projekt zu erstellen. Navigieren Sie zur Registerkarte &quot;Projekte&quot;in CJA.
Klicken Sie auf **Neu erstellen**.

![Demo](./images/prmenu.png)

Dann wirst du das sehen. Auswählen **Leeres Projekt** und klicken Sie anschließend auf **Erstellen**.

![Demo](./images/prmenu1.png)

Dann sehen Sie ein leeres Projekt.

![Demo](./images/premptyprojects.png)

Wählen Sie zuerst die richtige Datenansicht in der oberen rechten Ecke des Bildschirms aus. In diesem Beispiel lautet die auszuwählende Datenansicht . `CJA Bootcamp - Omnichannel Data View`.

Als Nächstes speichern Sie Ihr Projekt und geben ihm einen Namen. Sie können den folgenden Befehl zum Speichern verwenden:

| BS | Kurzschnitt |
| ----------------- |-------------| 
| Windows | Kontrolle + S |
| Mac | Befehl + S |

Dieses Popup wird angezeigt:

![Demo](./images/prsave.png)

Bitte verwenden Sie diese Namenskonvention:

| Name | Beschreibung |
| ----------------- |-------------| 
| `yourLastName - Omnichannel Analysis` | `yourLastName - Omnichannel Analysis` |

Klicken Sie anschließend auf **Speichern**.

![Demo](./images/prsave2.png)

## 4.4.2 Berechnete Metriken

Obwohl wir alle Komponenten in der Datenansicht organisiert haben, müssen Sie dennoch einige davon anpassen, damit Geschäftsbenutzer bereit sind, ihre Analyse zu starten. Außerdem können Sie bei jeder Analyse eine berechnete Metrik erstellen, um die Insights-Suche genauer zu untersuchen.

Als Beispiel erstellen wir eine berechnete **Konversionsrate** mithilfe der **Käufe** Metrik/Ereignis, die wir in der Datenansicht definiert haben.

### Konversionsrate

Beginnen wir damit, den Generator für berechnete Metriken zu öffnen. Klicken Sie auf **+** , um Ihre erste berechnete Metrik in Analysis Workspace zu erstellen.

![Demo](./images/pradd.png)

Die **Generator für berechnete Metriken** wird angezeigt:

![Demo](./images/prbuilder.png)

Suchen Sie die **Käufe** in der Liste der Metriken im Menü auf der linken Seite. under **Metriken** click **Alle anzeigen**

![Demo](./images/calcbuildercr1.png)

Ziehen Sie jetzt eine Dropdown-Liste **Käufe** -Metrik in die Definition der berechneten Metrik ein.

![Demo](./images/calcbuildercr2.png)

Normalerweise bedeutet Konversionsrate **Konversionen/Sitzungen**. Gehen wir also dieselbe Berechnung in die Arbeitsfläche der berechneten Metrik-Definition. Suchen Sie die **Sitzungen** Metrik und ziehen Sie sie per Drag-and-Drop in den Definition-Builder unter **Käufe** -Ereignis.

![Demo](./images/calcbuildercr3.png)

Beachten Sie, dass der Trennzeichen-Operator automatisch ausgewählt ist.

![Demo](./images/calcbuildercr4.png)

Die Konversionsrate wird häufig in Prozent dargestellt. Ändern wir also das Format in Prozent und wählen 2 Dezimalstellen aus.

![Demo](./images/calcbuildercr5.png)

Ändern Sie abschließend den Namen und die Beschreibung der berechneten Metrik:

| Titel | Beschreibung |
| ----------------- |-------------| 
| yourLastName - Konversionsrate | yourLastName - Konversionsrate |

Sie haben so etwas auf Ihrem Bildschirm:

![Demo](./images/calcbuildercr6.png)

Vergiss nicht, **Speichern** die berechnete Metrik.

![Demo](./images/pr9.png)

## 4.4.3 Berechnete Dimensionen: Filter (Segmentierung) und Datumsbereiche

### Filter: Berechnete Dimensionen

Berechnungen sind nicht nur für Metriken vorgesehen. Bevor Sie mit einer Analyse beginnen, ist es auch interessant, einige **Berechnete Dimensionen**. Das bedeutet **Segmente** zurück in Adobe Analytics. Im Customer Journey Analytics werden diese Segmente **Filter**.

![Demo](./images/prfilters.png)

Das Erstellen von Filtern hilft Benutzern aus Unternehmen, die Analyse mit einigen wertvollen berechneten Dimensionen zu beginnen. Dadurch werden einige Aufgaben automatisiert und der Adoptionsteil unterstützt. Im Folgenden finden Sie einige Beispiele:

1. Eigene Medien, gebührenpflichtige Medien,
2. Neue und wiederkehrende Besuche
3. Kunden mit Warenkorb

Diese Filter können vor oder während des Analyseabschnitts erstellt werden (was Sie in der nächsten Übung tun werden).

### Datumsbereiche: Berechnete Dimensionen

Zeitdimensionen sind andere Dimensionen. Einige sind bereits erstellt, Sie können aber auch Ihre eigenen benutzerdefinierten Time-Dimensionen in der Datenvorbereitungsphase erstellen.

Mithilfe dieser Dimensionen für berechnete Zeit können Analysten und Geschäftsbenutzer wichtige Daten speichern und diese zum Filtern und Ändern der Berichtszeit verwenden. Typische Fragen und Zweifel, die uns bei der Analyse am Herzen liegen:

- Wann war Black Friday letztes Jahr? 21.-29.?
- Wann haben wir diese Fernsehkampagne im Dezember geführt?
- Von wann bis wann haben wir die Sommerverkäufe 2018 getätigt? Ich möchte es mit 2019 vergleichen. Wissen Sie übrigens genau die Tage 2019?

![Demo](./images/timedimensions.png)

Sie haben die Datenvorbereitung mit CJA Analysis Workspace abgeschlossen.

Nächster Schritt: [4.5 Visualisierung mit Customer Journey Analytics](./ex5.md)

[Zurück zum Benutzerfluss 4](./uc4.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
