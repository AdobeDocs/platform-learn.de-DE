---
title: Kunden-KI - Scoring-Dashboard und Segmentierung (Prognose und Maßnahmen ergreifen)
description: Kunden-KI - Scoring-Dashboard und Segmentierung (Prognose und Maßnahmen ergreifen)
kt: 5342
doc-type: tutorial
exl-id: a6df3ff1-f907-4185-8189-f0b39c67c943
source-git-commit: 2d5ca888eb24c1f65b4ecd48030ec8d1659b7f84
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 3%

---

# 2.2.3 Kunden-KI - Scoring-Dashboard und Segmentierung (Prognose und Maßnahmen ergreifen)

Sobald Ihre Customer AI-Instanz einen Modelldurchgang abgeschlossen hat, können Sie den Tendenzwert visualisieren, der ausgewertet wird, um vorherzusagen, dass eine Kundin oder ein Kunde in den nächsten 30 Tagen einen Kauf tätigt.

![AI](./images/caiinstancesummary1.png)

>[!NOTE]
>
>Nur eine Customer AI-Instanz mit dem Status **Erfolg** ermöglicht eine Vorschau der Einblicke des Service.

## Tendenzvorhersage

Sehen wir uns nun die prognostizierte Neigung an, die vom Kunden-KI-Instanzmodell generiert wird. Klicken Sie auf den Instanznamen, um das Dashboard anzuzeigen.

![AI](./images/caimodels1.png)

Das Dashboard der Kundinnen- und Kunden-KI zeigt die Zusammenfassung der Bewertung, die Verteilung der Population und die Einflussfaktoren für das Modell an, das ausgewertet werden soll.

![KI-Beschreibung](./images/caidescription.png)

Bewegen Sie den Mauszeiger über die Einflussfaktoren, um die weitere Aufschlüsselung der Datenverteilung anzuzeigen.

![Einflussfaktoren](./images/caiinfluencefactors.png)

## Geschäftliche Aktionen

### Kunden segmentieren

Im Dashboard der Kundinnen- und Kunden-KI können Sie Segmente mit einem Klick definieren. Klicken Sie auf den **Segment erstellen** auf den Neigungs -Karten.

![Erstellen eines Segments](./images/caiinfluencefactors1.png)

Sie werden sehen, dass automatisch eine Segmentdefinition erstellt wird.

![Segmentregel](./images/caicreatesegment.png)

Benennen Sie Ihr Segment entsprechend dieser Namenskonvention: `--aepUserLdap-- - Customer AI High Propensity`. Klicken Sie auf **Veröffentlichen**.

![Segmentregel](./images/caicreatesegment1.png)

Sie können dieses Segment jetzt für das Targeting verwenden, indem Sie beispielsweise Real-Time CDP, Journey Optimizer und Adobe Target verwenden.

## Bereinigen

Um sicherzustellen, dass keine unnötigen Demodaten in Ihrer Umgebung aufbewahrt werden, stellen Sie sicher, dass Sie den Datensatz `--aepUserLdap-- - Demo System - Customer Experience Event Dataset` löschen, nachdem Sie diese Übung erfolgreich abgeschlossen haben. Wenn Sie die Demodaten nicht löschen, hat dies Auswirkungen auf die Kosten Ihrer AEP-Instanz.

![Profil](./images/cleanup.png)

## Nächste Schritte

Zurück zu [Intelligent Services](./intelligent-services.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
