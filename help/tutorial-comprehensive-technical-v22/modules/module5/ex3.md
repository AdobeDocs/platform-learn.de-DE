---
title: Customer AI - Scoring-Dashboard und Segmentierung (Vorhersage und Aktion)
description: Customer AI - Scoring-Dashboard und Segmentierung (Vorhersage und Aktion)
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 57d6c714-5d41-4ac1-8e60-3000da45b76e
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 3%

---

# 5.3 Customer AI - Scoring-Dashboard und Segmentierung (Vorhersagen und Handeln)

Sobald Ihre Customer AI-Instanz einen Modelllauf abgeschlossen hat, können Sie den Tendenzwert visualisieren, der ausgewertet wird, um einen Kunden vorherzusagen, der in den nächsten 30 Tagen einen Kauf tätigt.

![AI](./images/caimodels.png)

>[!NOTE]
>
>Nur eine Customer AI-Instanz mit dem Status **Erfolg** können Sie eine Vorschau der Einblicke des Dienstes anzeigen.

## 5.3.1 Tendenzaussage

Sehen wir uns nun die prognostizierte Tendenz an, die vom Customer AI-Instanzmodell generiert wurde. Klicken Sie auf den Instanznamen, um das Dashboard anzuzeigen.

![KI](./images/caimodels1.png)

Das Dashboard Customer AI zeigt die Zusammenfassung zu Bewertung, Verteilung der Population und den Einflussfaktoren für das Modell an.

![AI-Beschreibung](./images/caidescription.png)

![Dashboard-Zusammenfassung](./images/caidashboard.png)

Bewegen Sie den Mauszeiger über die Einflussfaktoren, um die weitere Aufschlüsselung der Datenverteilung anzuzeigen.

![Einflussfaktoren](./images/caiinfluencefactors.png)

## 5.3.2 Geschäftsaktionen

### 5.3.2.1 Kunden segmentieren

Das Dashboard Customer AI ermöglicht die Definition von Segmenten mit einem Klick. Klicken Sie auf **Segment erstellen** auf den Tendenzkarten.

![Erstellen eines Segments](./images/caiinfluencefactors1.png)

Sie werden sehen, dass eine Segmentdefinition automatisch erstellt wird.

![Segmentregel](./images/caicreatesegment.png)

Benennen Sie Ihr Segment gemäß dieser Benennungsregel: `--demoProfileLdap-- - Customer AI High Propensity`. Klicken Sie auf **Speichern**.

![Segmentregel](./images/caicreatesegment1.png)

Sie können dieses Segment jetzt für das Targeting mit z. B. Echtzeit-Kundendatenplattform, Journey Orchestration und Adobe Target verwenden.

### 5.3.2.2 Profilübersicht

Da die Tendenzbewertung der Customer AI Teil des Echtzeit-Kundenprofils wird, können Sie die Bewertung einzelner Kunden anzeigen.

Navigieren Sie in Adobe Experience Platform zu **Profile** im linken Menü und wählen Sie **Durchsuchen**.

Suchen Sie mithilfe einer der Kennungen nach einem Profil, z. B. **E-MAIL hbirkenshawa@businessweek.com**, die in der von Ihnen erfassten JSON-Datei verfügbar sind. Klicken Sie auf **Profil-ID** , um das Profil zu öffnen.

![Profil](./images/profile1.png)

Daraufhin sehen Sie Folgendes:

![Profil](./images/profile2.png)

Navigieren Sie zu **Attribute**, der die Ausgabe aus Ihrem Customer AI-Modell enthält.

![Profil](./images/profile3.png)

Scrollen Sie nach unten, um die von Ihrem Customer AI-Modell berechnete Tendenzbewertung anzuzeigen.

![Profil](./images/profile4.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 5](./intelligent-services.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
