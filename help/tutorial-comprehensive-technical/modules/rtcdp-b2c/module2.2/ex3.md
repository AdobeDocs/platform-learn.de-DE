---
title: Customer AI - Scoring-Dashboard und Segmentierung (Vorhersage und Aktion)
description: Customer AI - Scoring-Dashboard und Segmentierung (Vorhersage und Aktion)
kt: 5342
doc-type: tutorial
exl-id: 4dd8489a-65e4-489a-9228-3c642b10e761
source-git-commit: b53ee64ae8438b8f48f842ed1f44ee7ef3e813fc
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 2%

---

# 2.2.3 Customer AI - Scoring-Dashboard und Segmentierung (Vorhersagen und Handeln)

Sobald Ihre Customer AI-Instanz einen Modelllauf abgeschlossen hat, können Sie den Tendenzwert visualisieren, der ausgewertet wird, um einen Kunden vorherzusagen, der in den nächsten 30 Tagen einen Kauf tätigt.

![KI](./images/caiinstancesummary1.png)

>[!NOTE]
>
>Nur eine Customer AI-Instanz mit dem Status **Erfolg** ermöglicht die Vorschau der Einblicke des Dienstes.

## Propensity Predication

Sehen wir uns nun die prognostizierte Tendenz an, die vom Customer AI-Instanzmodell generiert wurde. Klicken Sie auf den Instanznamen, um das Dashboard anzuzeigen.

![KI](./images/caimodels1.png)

Das Dashboard Customer AI zeigt die Zusammenfassung zu Bewertung, Verteilung der Population und den Einflussfaktoren für das Modell an.

![KI-Beschreibung](./images/caidescription.png)

Bewegen Sie den Mauszeiger über die Einflussfaktoren, um die weitere Aufschlüsselung der Datenverteilung anzuzeigen.

![Einflussfaktoren](./images/caiinfluencefactors.png)

## Geschäftsaktionen

### Segmentieren von Kunden

Das Dashboard Customer AI ermöglicht die Definition von Segmenten mit einem Klick. Klicken Sie auf die Schaltfläche **Segment erstellen** auf den Tendenzkarten.

![Erstellen eines Segments](./images/caiinfluencefactors1.png)

Sie werden sehen, dass eine Segmentdefinition automatisch erstellt wird.

![Segmentregel](./images/caicreatesegment.png)

Geben Sie Ihrem Segment einen Namen gemäß dieser Benennungsregel: `--aepUserLdap-- - Customer AI High Propensity`. Klicken Sie auf **Veröffentlichen**.

![Segmentregel](./images/caicreatesegment1.png)

Sie können dieses Segment jetzt für das Targeting mit z. B. Echtzeit-Kundendatenplattform, Journey Optimizer und Adobe Target verwenden.

## Bereinigen

Um sicherzustellen, dass keine unnötigen Demodaten in Ihrer Umgebung aufbewahrt werden, löschen Sie den Datensatz `--aepUserLdap-- - Demo System - Customer Experience Event Dataset`, sobald Sie diese Übung erfolgreich abgeschlossen haben. Wenn Sie die Demodaten nicht löschen, wirkt sich dies auf Ihre AEP-Instanz aus.

![Profil](./images/cleanup.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 2.2](./intelligent-services.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
