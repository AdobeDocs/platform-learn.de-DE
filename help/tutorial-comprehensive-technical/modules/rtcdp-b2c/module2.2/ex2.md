---
title: Intelligent Services - Customer AI Erstellen einer neuen Instanz (Konfigurieren)
description: Customer AI - Erstellen einer neuen Instanz (Konfigurieren)
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 12%

---

# 2.2.2 Customer AI - Erstellen einer neuen Instanz (Konfigurieren)

Customer AI analysiert vorhandene Kundenerlebnis-Ereignisdaten, um Tendenzwerte für Abwanderung oder Konversion vorherzusagen. Durch die Erstellung einer neuen Customer AI-Instanz können Marketing-Experten Ziele und Kennzahlen definieren.

## 2.2.2.1 Neue Customer AI-Instanz einrichten

Klicken Sie in Adobe Experience Platform im linken Menü auf **Dienste** . Der Browser für **Dienste** erscheint und zeigt alle Dienste an, die Ihnen zur Verfügung stehen. Klicken Sie auf der Karte für Customer AI auf **Öffnen**.

![Dienstnavigation](./images/navigatetoservice.png)

Klicken Sie auf **Instanz erstellen**.

![Neue Instanz erstellen](./images/createnewinstance.png)

Dann wirst du das sehen.

![Neue Instanz erstellen](./images/custai1.png)

Geben Sie die erforderlichen Details für die Customer AI-Instanz ein:

- Name: use `--aepUserLdap-- Product Purchase Propensity`
- Beschreibung: use: **Prognostizieren Sie die Wahrscheinlichkeit, dass Kunden ein Produkt kaufen**
- Propensity type: select **Conversion**

![Setup-Seite 1](./images/setuppage1.png)

Klicken Sie auf **Weiter**.

![Setup-Seite 1](./images/next.png)

Dann wirst du das sehen. Wählen Sie den Datensatz aus, den Sie in der vorherigen Übung erstellt haben und der den Namen `--demoProfileLdap - Demo System - Customer Experience Event Dataset` trägt. Klicken Sie auf **Weiter**.

![Setup-Seite 1](./images/custai2.png)

Wählen Sie **Vorkommen** aus und definieren Sie das Feld **commerce.purchases.value** als Zielvariable.

![CAI-Ziel definieren](./images/caidefinegoal.png)

Klicken Sie auf **Weiter**.

![Setup-Seite 1](./images/next.png)

Legen Sie als Nächstes Ihren Zeitplan so fest, dass **Wöchentlich** ausgeführt wird, und legen Sie die Zeit so nah wie möglich an Ihrer aktuellen Zeit fest. Stellen Sie sicher, dass der Umschalter **Bewertungen für Profil aktivieren** aktiviert ist.

![CAI-Fortschritte definieren](./images/caiadvancepage.png)

Klicken Sie auf **Fertigstellen**.

![Setup-Seite 1](./images/finish.png)

Dann sehen Sie dieses Popup. Klicken Sie auf **OK**.

![Setup-Seite 1](./images/finish1.png)

Nachdem Sie die Instanz konfiguriert haben, können Sie sie in der Liste der Customer AI-Instanzen sehen und die Zusammenfassung der Einrichtungs- und Ausführungsdetails durch Klicken auf die Zeile der Customer AI-Instanz in der Vorschau anzeigen. Im Zusammenfassungsfenster werden auch Fehlerdetails angezeigt, falls Fehler gefunden wurden.

![Übersicht über die Instanzeinrichtung](./images/caiinstancesummary.png)

>[!NOTE]
>
>Sie können jede Definition oder jedes Attribut ändern, solange der Status Ihrer Customer AI-Instanz entweder **Auf Training warten** oder **Fehler** lautet

Nächster Schritt: [2.2.3 Customer AI - Scoring Dashboard and Segmentation (Predict &amp; Take Action)](./ex3.md)

[Zurück zu Modul 2.2](./intelligent-services.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
