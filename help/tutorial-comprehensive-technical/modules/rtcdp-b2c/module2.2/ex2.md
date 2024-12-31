---
title: Intelligent Services - Kunden-KI Neue Instanz erstellen (Konfigurieren)
description: Kunden-KI - Neue Instanz erstellen (Konfigurieren)
kt: 5342
doc-type: tutorial
exl-id: 067f3fa2-5c1e-4861-b26a-4315cad73a85
source-git-commit: b53ee64ae8438b8f48f842ed1f44ee7ef3e813fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 9%

---

# 2.2.2 Kunden-KI - Neue Instanz erstellen (Konfigurieren)

Customer AI analysiert vorhandene Kundenerlebnis-Ereignisdaten, um Tendenzwerte für Abwanderung oder Konversion vorherzusagen. Durch das Erstellen einer neuen Kunden-KI-Instanz können Marketing-Experten Ziele und Maßnahmen definieren.

## Einrichten einer neuen Kunden-KI-Instanz

Klicken Sie in Adobe Experience Platform **Menü** Dienste“ auf der linken Seite. Der Browser für **Dienste** erscheint und zeigt alle Dienste an, die Ihnen zur Verfügung stehen. Klicken Sie in der Karte für Kunden-KI auf **Öffnen**.

![Service-Navigation](./images/navigatetoservice.png)

Klicken Sie auf **Instanz erstellen**.

![Neue Instanz erstellen](./images/createnewinstance.png)

Sie werden es dann sehen.

![Neue Instanz erstellen](./images/custai1.png)


Geben Sie die erforderlichen Details für die Kunden-KI-Instanz ein:

- Name: use `--aepUserLdap-- Product Purchase Propensity`
- Beschreibung: Verwenden Sie **Prognostizieren der Wahrscheinlichkeit, dass Kunden ein Produkt kaufen**
- Neigungstyp: wählen Sie **Konversion**

Klicken Sie **Speichern und fortfahren**.

![Seite 1 ](./images/setuppage1.png)

Sie werden es dann sehen. Wählen Sie den Datensatz aus, den Sie in der vorherigen Übung mit dem Namen `--demoProfileLdap - Demo System - Customer Experience Event Dataset` erstellt haben. Klicken Sie auf **Hinzufügen**.

![Seite 1 ](./images/custai2.png)

Sie werden es dann sehen. Sie müssen das Feld **Identität** definieren. Klicken Sie **Keine**.

![Seite 1 ](./images/custai2a.png)

Wählen Sie im Popup die Option **Identitätszuordnung (identityMap)** und wählen Sie dann den Namespace **Demo System - CRMID (crmId)**. Klicken Sie anschließend auf **Speichern**.

![Seite 1 ](./images/custai2b.png)

Klicken Sie **Speichern und fortfahren**.

![Seite 1 ](./images/custai2c.png)

Wählen Sie **Wird auftreten** in Ihrem spezifischen Datensatz aus und definieren Sie das Feld **commerce.purchases.value** als Zielvariable.

![Definieren des CAI-Ziels](./images/caidefinegoal.png)

Stellen Sie als Nächstes Ihren Zeitplan auf **Wöchentlich** und legen Sie die Uhrzeit so nah wie möglich an Ihrer aktuellen Zeit fest. Stellen Sie sicher, dass der Umschalter **Scores für Profil aktivieren** aktiviert ist. Klicken Sie **Speichern und fortfahren**.

![Definieren des CAI-Vorhabens](./images/caiadvancepage.png)

Nach der Konfiguration der Instanz wird sie in der Liste des Kunden-KI-Service angezeigt. Sie können außerdem eine Vorschau der Zusammenfassung der Einrichtungs- und Ausführungsdetails anzeigen, indem Sie auf die Zeile der Kunden-KI-Instanz klicken. Im Zusammenfassungsfenster werden auch Fehlerdetails angezeigt, falls Fehler gefunden wurden.

![Zusammenfassung der Instanzeinstellungen](./images/caiinstancesummary.png)

>[!NOTE]
>
>Sie können jede Definition oder jedes Attribut ändern, solange der Status Ihrer Kunden-KI-Instanz entweder **Training steht aus** oder **Fehler**

Sobald Ihr Modell ausgeführt wurde, sehen Sie dies.

![Zusammenfassung der Instanzeinstellungen](./images/caiinstancesummary1.png)


Nächster Schritt: [2.2.3 Kunden-KI - Scoring-Dashboard und Segmentierung (Prognose und Aktion)](./ex3.md)

[Zurück zum Modul 2.2](./intelligent-services.md)

[Zurück zu „Alle Module“](./../../../overview.md)
