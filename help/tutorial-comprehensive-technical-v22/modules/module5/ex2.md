---
title: Intelligent Services - Customer AI Erstellen einer neuen Instanz (Konfigurieren)
description: Customer AI - Erstellen einer neuen Instanz (Konfigurieren)
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: d9377c97-efed-427a-a063-aa9c6bd1a78a
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 13%

---

# 5.2 Customer AI - Erstellen einer neuen Instanz (Konfigurieren)

Customer AI analysiert vorhandene Kundenerlebnis-Ereignisdaten, um Tendenzwerte für Abwanderung oder Konversion vorherzusagen. Durch die Erstellung einer neuen Customer AI-Instanz können Marketing-Experten Ziele und Kennzahlen definieren.

## 5.2.1 Einrichten einer neuen Customer AI-Instanz

Klicken Sie in Adobe Experience Platform auf **Dienste** im linken Menü. Der Browser für **Dienste** erscheint und zeigt alle Dienste an, die Ihnen zur Verfügung stehen. Klicken Sie auf der Karte für Customer AI auf **Öffnen**.

![Dienstnavigation](./images/navigatetoservice.png)

Klicken Sie auf **Instanz erstellen**.

![Neue Instanz erstellen](./images/createnewinstance.png)

Dann wirst du das sehen.

![Neue Instanz erstellen](./images/custai1.png)

Geben Sie die erforderlichen Details für die Customer AI-Instanz ein:

- Name: use `--demoProfileLdap-- Product Purchase Propensity`
- Beschreibung: verwenden: **Vorhersagen der Wahrscheinlichkeit, mit der Kunden ein Produkt kaufen**
- Tendenztyp: select **Konversion**

![Seite 1 einrichten](./images/setuppage1.png)

Klicken Sie auf **Weiter**.

![Seite 1 einrichten](./images/next.png)

Dann wirst du das sehen. Wählen Sie den Datensatz aus, den Sie in der vorherigen Übung erstellt haben und der `--demoProfileLdap - Demo System - Customer Experience Event Dataset`. Klicken Sie auf **Weiter**.

![Seite 1 einrichten](./images/custai2.png)

Auswählen **Vorkommen** und definieren Sie das Feld **commerce.purchases.value** als Zielvariable.

![CAI-Ziel definieren](./images/caidefinegoal.png)

Klicken Sie auf **Weiter**.

![Seite 1 einrichten](./images/next.png)

Legen Sie als Nächstes den Zeitplan für die Ausführung fest. **Wöchentlich** und legen Sie die Zeit so nah wie möglich an Ihrer aktuellen Zeit fest. Stellen Sie sicher, dass der Umschalter **Bewertungen für Profil aktivieren** aktiviert ist.

![CAI-Erweiterungen definieren](./images/caiadvancepage.png)

Klicken Sie auf **Fertigstellen**.

![Seite 1 einrichten](./images/finish.png)

Dann sehen Sie dieses Popup. Klicken Sie auf **OK**.

![Seite 1 einrichten](./images/finish1.png)

Nachdem Sie die Instanz konfiguriert haben, können Sie sie in der Liste der Customer AI-Instanzen sehen und die Zusammenfassung der Einrichtungs- und Ausführungsdetails durch Klicken auf die Zeile der Customer AI-Instanz in der Vorschau anzeigen. Im Zusammenfassungsfenster werden auch Fehlerdetails angezeigt, falls Fehler gefunden wurden.

![Instanz-Setup-Zusammenfassung](./images/caiinstancesummary.png)

>[!NOTE]
>
>Sie können jede Definition oder jedes Attribut ändern, solange der Status Ihrer Customer AI-Instanz entweder **Vorbereitung der Schulung** oder **Fehler**

Nächster Schritt: [5.3 Customer AI - Scoring-Dashboard und Segmentierung (Vorhersagen und Handeln)](./ex3.md)

[Zurück zu Modul 5](./intelligent-services.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
