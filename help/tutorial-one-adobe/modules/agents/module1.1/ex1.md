---
title: Erste Schritte mit Agent Orchestrator
description: Erste Schritte mit Agent Orchestrator
kt: 5342
doc-type: tutorial
source-git-commit: bb31fe8a36f1c9ee9d212500e2e58e01be1129b8
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 0%

---

# 1.1.1 Erste Schritte mit Agent Orchestrator

## 1.1.1.1 in Agent Orchestrator

Navigieren Sie zu [https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Sie sollten das dann sehen. Stellen Sie sicher, dass Sie sich in der Organisation **Experience Platform International** befinden.

![Agent Orchestrator](./images/ao1.png)

Klicken Sie auf **Fenster** Kontext“.

![Agent Orchestrator](./images/ao2.png)

Legen Sie den Kontext fest auf:

- **Dokumentations-Source**: **Journey Optimizer**

Die Einstellung Dokumentations-Source hilft dabei, vorzuziehen, welche Experience League-Dokumente auf Fragen geprüft werden sollen, die sich auf Produktkenntnisse/Experience League beziehen.

- **Sandbox**: **prod - Accelerate (VA7)**

Die Sandbox-Einstellung hilft zu identifizieren, welchen Sandbox-KI-Assistenten beim Stellen von Fragen berücksichtigen sollte.

- **Datenansicht**: **Accelerate 2026 B2C**

Die Datenansichtseinstellung hilft zu identifizieren, welchen Datenansichts-KI-Assistenten beim Stellen von Fragen berücksichtigen sollte.

Klicken Sie **Kontext festlegen**.

![Agent Orchestrator](./images/ao3.png)

## 1.1.1.2 Beginnen Sie mit den allgemeinen Kauftrends, um den Kontext zu verankern und in Fasern zu zoomen.

**Intent**

Erhalten Sie einen Top-Level-Puls auf Kategorieabruf - Mobil, Festnetz, Internet, TV, Glasfaser - speziell für die letzten 60 Tage. Dies legt die Grundlinien für die Saisonabhängigkeit, die Werbeeffekte und die regionale Varianz nach dem Rollout von New York fest.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![Agent Orchestrator](./images/ao4.png)

Sie sollten dies dann sehen:

![Agent Orchestrator](./images/ao5.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

`Show me purchases by mainCategory = Fiber over the last 2 months per week`

![Agent Orchestrator](./images/ao6.png)

Sie sollten das dann sehen, welches sich detailliert mit faserspezifischen Trends beschäftigt.

![Agent Orchestrator](./images/ao7.png)

## 1.1.1.3 Korrelieren von Bestellungen mit Inhaltseinstellungen

**Intent**

Testen Sie die Hypothese, dass eine Präferenz für ein bestimmtes Genre (z. B. SciFi, Sport, Drama) das Breitband-Upgrade-Verhalten vorhersagt - insbesondere bei hohen Bandbreitenanforderungen.

Zunächst müssen Sie herausfinden, welches Feld zum Speichern der Genre-Voreinstellung verwendet wird.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Which field is used to store the preferred genre?
```

![Agent Orchestrator](./images/ao7a.png)

Sie sollten dies dann sehen, was zeigt, dass das für Genre verwendete Feld **_experienceplatform.individualCharacteristics.preferences.preferencesGenre** ist.

![Agent Orchestrator](./images/ao7b.png)

Mit diesen Informationen können Sie mit dem Drilldown in den Kaufdaten beginnen.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![Agent Orchestrator](./images/ao8.png)

Sie sollten das dann sehen. Klicken Sie auf das Symbol im Block **Reasoning complete**, um zu verstehen, was hinter den Kulissen in Agent Orchestrator passiert.

![Agent Orchestrator](./images/ao9.png)

Sie sollten dann eine ähnliche Erklärung sehen.

![Agent Orchestrator](./images/ao10.png)

## 1.1.1.4 Identifizieren vorhandener Fibre-Journey

**Intent**

Finden Sie heraus, welche aktiven oder kürzlich abgeschlossenen Journey „Fibre“ im Titel enthalten - z. B. „Fibre Upgrade NYC - Sept“, „Fibre Trial - Streaming Bundle“.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/ao12.png)

Sie sollten das dann sehen. Klicken Sie **Weitere anzeigen**.

![Agent Orchestrator](./images/ao13.png)

Sie sollten dann eine größere Liste der aktiven oder vergangenen Journey sehen. Klicken Sie auf **Herunterladen**-Symbol, um eine Liste dieser Journey herunterzuladen.

![Agent Orchestrator](./images/ao13a.png)

Dadurch wird eine CSV-Datei für Sie generiert, die die gesamte Ausgabe des KI-Assistenten enthält.

![Agent Orchestrator](./images/ao13b.png)

Klicken, um den rechten Bereich zu schließen. Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/ao14.png)

Sie sollten das dann sehen. Klicken Sie auf den Link auf einem der Journey und wählen Sie **Journey-Details**.

![Agent Orchestrator](./images/ao15.png)

Es öffnet sich ein neues Fenster und Sie gelangen sofort zur Journey-Detailübersicht.

![Agent Orchestrator](./images/ao15a.png)

## 1.1.1.5 Überprüfen, welche Zielgruppe verwendet wird

**Intent**:

Machen Sie sich mit der Testdefinition der Journey „CitiSignal - Fibre Max Launch Promotion“ vertraut, d. h. welche Eigenschaften das Targeting begünstigt haben (z. B. „SciFi Genre Preference“, „4+ devices“, „Stream ≥ 300 GB/Monat„).

Geben Sie Folgendes ein **Prompt**:

```javascript
What was the initial audience in the journey named 
```

Geben Sie dann manuell `+CitiSignal fib` ein, um die automatische Vervollständigung zu aktivieren. Wählen Sie die Journey **CitiSignal - Fiber Max Launch Promotion**.

![Agent Orchestrator](./images/ao16.png)

Sie sollten das dann sehen. Klicken Sie auf **Senden**.

![Agent Orchestrator](./images/ao17.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/ao18.png)

## 1.1.1.6 Validieren der Journey-Performance über Fallout-Analyse

**Intent**

Sie sollten wissen, ob es auf der Journey Knoten oder Bedingungen gibt, bei denen eine große Anzahl von Journey-Profilen gelöscht wird. Dies ist hilfreich, um zu verstehen, ob zusätzliche Anpassungen im Journey erforderlich sind.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/ao19.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/ao20.png)

Scroll ein bisschen nach unten. Sie können die Tabelle nun überprüfen, indem Sie jeden Knoten und seine entsprechenden Eingeben von Zahlen, Fallout-Zahlen und Fallout-Rate überprüfen.

Der KI-Assistent liefert Beobachtungen und Empfehlungen.

Klicken Sie auf den Satz **So habe ich die Ergebnisse erhalten**.

![Agent Orchestrator](./images/ao21.png)

Sie können dann die Schritte sehen, denen der KI-Assistent folgt, um zu den Ergebnissen zu gelangen.

![Agent Orchestrator](./images/ao22.png)

## 1.1.1.7 Erstellen einer neuen Zielgruppe

**Intent**

Basierend auf den obigen Ergebnissen und Untersuchungen besteht eine Korrelation zwischen Kunden, die viele Daten verbrauchen und ein bevorzugtes Genre von Science-Fiction oder Fantasie haben. Sie kombinieren diese Attribute jetzt in einer Zielgruppe.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Create an audience that combines people with an average download per month of over 2000 GB and a preferred genre of sci-fi or fantasy.
```

![Agent Orchestrator](./images/ao32.png)

Überprüfen Sie den Plan. Geben Sie `yes` ein und klicken Sie auf **Senden**.

>[!NOTE]
>
>Dieser Plan wird basierend auf einem Referenzhandbuch im System generiert. Kunden werden letztendlich in der Lage sein, Pläne anzupassen und ihre eigenen Pläne hinzuzufügen, aber für den Moment sind sie statisch.

![Agent Orchestrator](./images/ao33.png)

Überprüfen Sie den Segmentabfrageausdruck. Geben Sie `yes` ein und klicken Sie auf die Schaltfläche **Senden**.

![Agent Orchestrator](./images/ao34.png)

Überprüfen Sie die Schätzung der Segmentgröße. Geben Sie `yes` ein und klicken Sie auf die Schaltfläche **Senden**.

![Agent Orchestrator](./images/ao35.png)

Klicken Sie **Überprüfen**.

![Agent Orchestrator](./images/ao36.png)

Überprüfen Sie die Segmentdefinition. Klicken Sie auf **Erstellen**.

![Agent Orchestrator](./images/ao37.png)

Ihre Zielgruppe wurde jetzt erstellt.

![Agent Orchestrator](./images/ao38.png)

>[!NOTE]
>
>Beim Erstellen einer neuen Zielgruppe dauert es 24 Stunden, bis die Zielgruppe dem KI-Assistenten zur weiteren Verwendung zur Verfügung steht.

## 1.1.1.8 Finden Sie vorhandene Zielgruppen, die auf eine hohe Nutzung ausgerichtet sind, und überprüfen Sie, ob sie verwendet werden.

**Intent**:

Suchen Sie eine Zielgruppe mit dem Namen „starke Downloader“, die durch die monatlichen Datennutzungsschwellen definiert werden.

>[!NOTE]
>
>Im vorherigen Schritt haben Sie eine neue Zielgruppe erstellt. Es dauert 24 Stunden, bis die Zielgruppe für den KI-Assistenten zur weiteren Verwendung verfügbar ist. Sie sollten stattdessen eine andere, bereits vorhandene Zielgruppe verwenden.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

![Agent Orchestrator](./images/ao30.png)

Sie sollten das dann sehen. Jetzt möchten Sie alle Ihre Zielgruppen sehen und sehen, wie stark sie sich in den letzten Tagen verändert haben.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
List how much these audiences changed over the last few days.
```

![Agent Orchestrator](./images/ao31.png)

Sie sollten das dann sehen. Klicken Sie **Weitere anzeigen**.

![Agent Orchestrator](./images/ao31a.png)

Sie sollten das dann sehen. Klicken, um den rechten Bereich zu schließen.

![Agent Orchestrator](./images/ao31b.png)

Scrollen Sie ein wenig nach unten, um die Schritte zu überprüfen, die vom KI-Assistenten ausgeführt werden.

![Agent Orchestrator](./images/ao31c.png)

Es gibt bereits Zielgruppen für „starke Downloader“. Mal sehen, ob sie bereits verwendet werden.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Which of the above are used in a journey? 
```

![Agent Orchestrator](./images/ao50.png)

Sie sollten dann etwas Ähnliches sehen.

![Agent Orchestrator](./images/ao51.png)

Sie sollten nun überprüfen, ob diese Journey aktiv ist. Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Are these journeys active? 
```

![Agent Orchestrator](./images/ao52.png)

Sie sollten dann etwas Ähnliches sehen. Keiner dieser Journey läuft derzeit.

![Agent Orchestrator](./images/ao53.png)

Für die bevorstehende Einführung von Fiber Max sollten Sie jetzt eine neue Journey erstellen.

## 1.1.1.9 Neue Journey für Fibre Max Launch erstellen

**Intent**:

Erstellen Sie eine neue Journey für die zusammengesetzte Zielgruppe:

Umfangreiche Downloader ∩ SciFi-Voreinstellungen.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Create a  journey towards the audience Heavy Downloaders - Sci-Fi Preference_kbaa_5207bf. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

![Agent Orchestrator](./images/aocj1.png)

Sie sollten das dann sehen. Geben Sie `yes` ein und klicken Sie auf Generieren.

![Agent Orchestrator](./images/aocj2.png)

Sie sollten das dann sehen. Geben Sie `yes` ein und klicken Sie auf Generieren.

![Agent Orchestrator](./images/aocj3.png)

Sie sollten das dann sehen. Geben Sie `The first one` ein und klicken Sie auf Senden.

![Agent Orchestrator](./images/aocj4.png)

Sie sollten das dann sehen. Geben Sie `yes` ein und klicken Sie auf Senden.

![Agent Orchestrator](./images/aocj5.png)

Überprüfen Sie die Antwort. Geben Sie `yes` ein und klicken Sie auf Senden.

![Agent Orchestrator](./images/aocj6.png)

Klicken Sie **Überprüfen**.

![Agent Orchestrator](./images/aocj7.png)

Aktualisieren Sie den Journey-Namen mit Ihrem LDAP, um ihn eindeutig zu machen. Klicken Sie auf **Speichern**.

![Agent Orchestrator](./images/aocj8.png)

Ihr Journey wurde jetzt im Entwurfsmodus erstellt.

![Agent Orchestrator](./images/aocj9.png)

## 1.1.1.10 Journey-Konfliktmanagement

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
How can I manage journey conflicts?
```

![Agent Orchestrator](./images/aocj80.png)

Überprüfen Sie die Informationen.

![Agent Orchestrator](./images/aocj81.png)

Scrollen Sie nach unten und wählen Sie **Quellen** aus, um herauszufinden, dass die Informationen aus Experience League stammen.

![Agent Orchestrator](./images/aocj82.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
List any conflicts for the journey +CitiSignal Fiber Max
```

Wählen Sie anschließend manuell die Journey **CitiSignal - Fiber Max Launch Promotion** aus der Liste aus.

![Agent Orchestrator](./images/aocj70.png)

Sie sollten das dann sehen. Klicken Sie auf **Senden**.

![Agent Orchestrator](./images/aocj70a.png)

Überprüfen Sie die Journey-Konfliktinformationen.

![Agent Orchestrator](./images/aocj71.png)

Scrollen Sie nach unten, um weitere Informationen zu Journey-Konflikten zu erhalten.

![Agent Orchestrator](./images/aocj72.png)

## 1.1.1.11 Experimente

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
How are the experiments performing for the journey named 'CitiSignal - Fiber Max Launch Promotion'?
```

![Agent Orchestrator](./images/aoea0.png)

Sie sollten dies dann sehen:

![Agent Orchestrator](./images/aoea1.png)

Scrollen Sie nach unten und klicken Sie auf einen der Vorschläge. Klicken Sie auf **Senden**.

>[!NOTE]
>
>Die Vorschläge sind dynamisch. Daher sollten Sie bei jeder Antwort mit unterschiedlichen Vorschlägen rechnen. Ihre Vorschläge unterscheiden sich wahrscheinlich von den Vorschlägen, die in diesem Screenshot angezeigt werden.

![Agent Orchestrator](./images/aoea2.png)

Sie sollten dann eine detaillierte Antwort im Zusammenhang mit dem ausgewählten Vorschlag sehen.

![Agent Orchestrator](./images/aoea4.png)

Sie haben jetzt dieses Labor abgeschlossen.

Zurück zu [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}