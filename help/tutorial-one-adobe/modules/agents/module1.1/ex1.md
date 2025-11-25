---
title: Erste Schritte mit Agent Orchestrator
description: Erste Schritte mit Agent Orchestrator
kt: 5342
doc-type: tutorial
source-git-commit: 9011c4093b5fd6612426baf7003cd7b99523b6e8
workflow-type: tm+mt
source-wordcount: '1296'
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

- **Dokumentations-Source**: **Customer Journey Analytics**
- **Sandbox**: **Accelerate**
- **Datenansicht**: **Accelerate 2026 B2C**

Klicken Sie **Kontext festlegen**.

![Agent Orchestrator](./images/ao3.png)

>[!NOTE]
>
>In diesem Labor wechseln Sie beim Wechsel zwischen Analyse und Orchestrierung zwischen Kontext.

## 1.1.1.2 Beginnen Sie mit den allgemeinen Kauftrends, um den Kontext zu verankern und in Fasern zu zoomen.

**Intent**: Erhalten Sie einen Top-Level-Puls auf Kategorieabfrage - Mobil, Festnetz, Internet, TV, Glasfaser - speziell für die letzten 60 Tage. Damit werden die Grundlinien für die Saisonabhängigkeit, die Werbewirkungseffekte und die regionale Varianz nach dem Rollout von NY festgelegt.

**Denken**:

„Werden Glasfaser-Anteile nach NY? Erleben wir eine Kannibalisierung des Kupfer-/DSL-Internets? Was ist der Mix-Wechsel im Vergleich zu TV-Paketen?“

„Das wird mir helfen, das adressierbare Publikum für Wien zu bestimmen und realistische Ziele zu setzen.“

**Vom Marketing-Experten erwartete umsetzbare**:

Ein gestapeltes Balken-/Liniendiagramm der Käufe nach Hauptkategorie (tägliche/wöchentliche Körnung).

Prozentualer Anteil der Käufe nach Kategorie im Vergleich zum vorherigen Zeitraum.

Wesentliche Spitzen, die mit Promotiondaten korrelieren.

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![Agent Orchestrator](./images/ao4.png)

Sie sollten dies dann sehen:

>[!NOTE]
>
>Behalten Sie die verzögerte Attribution im Auge: Fibre-Bestellungen können in einigen Legacy-Schemata unter „Internet“ erfasst werden. Wenn ja, stimmen Sie die Taxonomie vor den Entscheidungen ab.

![Agent Orchestrator](./images/ao5.png)

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

`Show me purchases by mainCategory = Fiber over the last 2 months per week`

![Agent Orchestrator](./images/ao6.png)

Sie sollten das dann sehen, welches sich detailliert mit faserspezifischen Trends beschäftigt.

**Aktion**: Beachten Sie die Wachstumskurve und regionale Spitzen.

![Agent Orchestrator](./images/ao7.png)

## 1.1.1.3 Korrelieren von Bestellungen mit Inhaltseinstellungen

**Intent**: Testen Sie die Hypothese, dass die Präferenz für Inhalte (z. B. SciFi, Sport, Drama) das Verhalten bei Breitband-Upgrades vorhersagt - insbesondere für Anforderungen mit hoher Bandbreite.

**Denken**

„SciFi-Fans schauen oft 4K und streamen von mehreren Geräten. Wahrscheinlich wird eine niedrige Latenz genutzt.“

„Beziffern wir, ob SciFi (und vielleicht auch Sport) mit den letzten Bestellungen korreliert.“

**Erwartete Ergebnisse**

Ein Pivot für Bestellungen (angewendeter YTD-Filter), aufgeschlüsselt nach bevorzugtem Genre, begrenzt auf die letzten 2 Monate.

Sortiert Genres nach Konversionsrate der Reihenfolge und AOV (durchschnittlicher Bestellwert).

Entscheidung: Zeigt SciFi ein starkes Signal, wird dies zu einer primären kreativen Säule für die Einführung von Wiens Fiber Max (z.B. „Niemals wieder puffern“-Messaging, Premium-Bundles).

**Absicht**

Konversionen nach Genre analysieren (z. B. Sci-Fi, Sport).

**Goal** Überprüfen Sie, ob Sci-Fi-Fans bei Fibre-Upgrades den Index überschreiben.

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![Agent Orchestrator](./images/ao8.png)

Sie sollten dies dann sehen:

![Agent Orchestrator](./images/ao9.png)

## 1.1.1.4 Identifizieren vorhandener Fibre-Journey

Klicken Sie auf **Fenster** Kontext“.

![Agent Orchestrator](./images/ao10.png)

Legen Sie den Kontext fest auf:

- **Dokumentations-Source**: **Adobe Journey Optimizer**
- **Sandbox**: **Accelerate**
- **Datenansicht**: **Accelerate 2026 B2C**

![Agent Orchestrator](./images/ao11.png)

**Intent** Entdecken Sie, welche aktiven oder kürzlich abgeschlossenen Journey „Fibre“ im Titel enthalten - z. B. „Fibre Upgrade NYC - Sept“, „Fibre Trial - Streaming Bundle“.

**Denken**

„Welche dieser Journey schnitten gut ab, und was waren ihre Trigger?“

„Kann ich die erfolgreichste Orchestrierungslogik für Wien wiederverwenden?“

**Erwartete Ergebnisse**

Liste der Journey mit Status (aktiv, angehalten, beendet), Datumsbereichen, Zielsegmenten, KPIs (Öffnungsrate, CTR, Konversion).

Nächster Schritt: Ein oder zwei erfolgreiche Faser-Journey für Klonen/Adaptieren in die engere Wahl ziehen.

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/ao12.png)

Sie sollten dies dann sehen:

![Agent Orchestrator](./images/ao13.png)

Auflisten der aktiven oder vergangenen Journey mit Fibre-Messaging.

Aktion: Hochleistungsfähige Journey für das Klonen in die engere Wahl ziehen.

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/ao14.png)

Sie sollten dies dann sehen:

![Agent Orchestrator](./images/ao15.png)

## 1.1.1.5 Testadressen prüfen

**Intent**:

Machen Sie sich mit der Testdefinition der Journey „CitiSignal - Fibre Max Launch Promotion“ vertraut, d. h. welche Eigenschaften das Targeting begünstigt haben (z. B. „SciFi Genre Preference“, „4+ devices“, „Stream ≥ 300 GB/Monat„).

**Denken**

„Ich möchte bewährte SciFi-Kreativität mit Fibre Max Performance-Messaging kombinieren.“

„Wenn sich die Zielgruppe mit umfangreichen Downloadern überschneidet, können wir die Tendenz stapeln.“

**Erwartete Ergebnisse**

Zielgruppenkriterien (Einschluss/Ausschluss), Zielgruppengröße, Regionsfilter, Neuigkeit, Häufigkeitsschwellen.

>[!NOTE]
>
>Kontext in CJA ändern

Von diesem Punkt an wechselt der Marketer in den Analysemodus, um ein ordnungsgemäßes Reporting zu gewährleisten.

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
What was the initial audience in the journey named 'CitiSignal - Fiber Max Launch Promotion'?
```

![Agent Orchestrator](./images/ao16.png)
Überprüfen Sie die Zielgruppenkriterien (Streaming-Gewohnheiten, Anzahl der Geräte).

**Ziel**: Eigenschaften für Anforderungen mit hoher Bandbreite verstehen.

## 1.1.1.6 Validieren der Journey-Performance über Fallout-Analyse

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

>[!NOTE]
>
>Kontext in CJA ändern)

**Intent**:

Erstellen eines schrittweisen funnels in Customer Journey Analytics

Zugestellt → geöffnet → geklickt → → Produktansicht → Zum Warenkorb hinzufügen → Checkout → Bestellung abgeschlossen

Schließen Sie faserbezogene SKU-Ansichten als Verzweigung ein.

**Denken**:

„Wo verlieren wir Personen - E-Mail-Öffnungen, Laden von Landingpages, PDPs, Kassenreibungsfehler?“

„Führen SciFi-Benutzer auf Fiber-PDPs mehr oder weniger häufig einen Bounce aus?“

**Erwartete Ausgaben**:

Eine Fallout-Visualisierung mit Abbruchraten bei jedem Schritt.

Segmentüberlagerungen (SciFi vs. Sport vs. Andere).

Geräte-/Browser-Ausfall für technische Reibung.

**Entscheidungen**:

Wenn der Checkout-Abfall hoch ist, stimmen Sie sich mit dem Produkt/UX ab, um den Zahlungsfluss zu beheben.

Wenn der PDP-Austritt hoch ist, muss die Klarheit der Nachbearbeitungsansprüche (Geschwindigkeiten, Installationszeiten, Paketwert) gewahrt bleiben.

>[!NOTE]
>
>Kontext in Auftrag ändern

Jetzt wechselt der Marketing-Experte zu Adobe Journey Optimizer für Orchestrierung und Audience Ops.

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey 
```

Funnel-Visualisierung erstellen: Lieferung → geöffnet → auf → Checkout → Bestellung geklickt.

**Action**: Identifizieren Sie Abfallpunkte und optimieren Sie Messaging oder UX.

## 1.1.1.7 Finden Sie vorhandene Zielgruppen, die auf eine hohe Nutzung ausgerichtet sind

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

>[!NOTE]
>
>Kontext in Adobe Journey Optimizer ändern

**Intent**:

Suchen Sie eine Job-Zielgruppe mit dem Namen „starke Downloader“, die wahrscheinlich durch monatliche Datennutzungsschwellen, Streaming-Stunden oder die gleichzeitige Nutzung von Geräten definiert wird.

**Denken**:

„Wenn es eine Audience wie Heavy Downloaders gibt, ist es perfekt für die Positionierung von Fibre Max: Geschwindigkeit, Zuverlässigkeit, unbegrenzte Stufen.“

**Erwartete Ausgaben**:

Zielgruppen-Metadaten: Definitionskriterien, Größe, letzte Aktualisierung, Governance-Tags, Regionsverfügbarkeit.

Suchen Sie Zielgruppen mit hoher Datennutzung.

**Ziel**: Kombinieren Sie mit Sci-Fi-Präferenz für Fibre-Max-Targeting.

## 1.1.1.8 Ermitteln, ob diese Zielgruppen bereits verwendet werden

**Intent**:

Überprüfen Sie die Verknüpfung von Zielgruppe zu Journey. Vergewissern Sie sich, dass keine doppelte Nachricht gesendet wird und dass keine Konflikte mit aktuellen Programmen auftreten.

**Denken**:

„Wenn sich Heavy Downloader bereits auf einer Retentions-Journey befindet, benötigen wir eine Unterdrückungslogik oder Frequenzlimitierung, um Ermüdung zu vermeiden.“

**Erwartete Ausgaben**:

Zuordnungen: Name der Zielgruppe → Journey, Status, Kontaktrichtlinie, letzter Versand, Leistung.

**Entscheidung**:

Wenn verwendet, erstellen Sie Ausschlüsse oder eine freigegebene Unterdrückung für den Wiener Launch.

Wenn nicht in Gebrauch, grünes Licht für neue Journey.

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
Which of the above are used in a journey? 
```

Überschneidungen mit aktiven Kampagnen vermeiden.

**Aktion**: Bei Bedarf Unterdrückung anwenden.

## 1.1.1.9 Neue Journey für Fibre Max Launch erstellen

**Intent**:

Erstellen Sie eine neue Journey für die zusammengesetzte Zielgruppe:

Umfangreiche Downloader ∩ SciFi-Voreinstellungen (Zielgruppenschlüssel kbaa_5207bf).

**Denken**:

„Das ist der Clou für Fiber Max: hohe Tendenz + kreative Relevanz.“

„Wir werden ein Multitouch-Erlebnis organisieren, das mit der Verfügbarkeit von Wien verknüpft ist.“

**Journey-Design (JO)**:

Einstiegskriterien:

Zielgruppe: Umfangreiche Downloader - Sci-Fi Preference_kbaa_5207bf

Geografie: Vienna Metro (Postleitzahl-/Postleitzahl-Liste oder Geopolygon)

Berechtigung: Nicht in der aktiven Kampagne „Fibre Upgrade NYC - September“; kein aktueller Fibre-Abonnent.

Trigger und Timing:

T14 Tage vor dem Launch in Wien (Januar 2026): Vorschau-E-Mail - „Fibre Max kommt.“

Launch-Woche: Primäre E-Mail + In-App-Banner + Paid-Media-Synchronisation (über das CDP-Ziel).

T+3 Tage: Verhaltens-Split - wenn kein Klick, SMS-Nudge; wenn geklickt, aber nicht bestellt, mit einem CTA-Installationsprogramm erneut ansprechen.

T+10 Tage: Angebotstest - kostenlose Installation vs. Ermäßigung für den 1. Monat (A/B).

Personalization:

Dynamische Kopie für SciFi-Fans (Latenz/4K-Streaming-Hooks).

Geschwindigkeits-/Latenzansprüche, die auf den Gerätemix zugeschnitten sind (Spielekonsolen, Streaming-Boxen).

Bundle-Empfehlung: Fiber Max + Premium TV Scifi Inhaltspaket.

Governance:

Häufigkeitsbegrenzung: max. 3 Kontakte pro 10 Tage.

Unterdrücken, wenn der aktuelle Fibre-Abonnent oder das Ticket für die Installation vorhanden ist.

Berücksichtigt Opt-out-Voreinstellungen.

Messplan (CJA):

Verfolgen: Versand, Öffnen, Klicken, PDP-Ansicht, Checkout-Start, Bestellungsabschluss.

KPIs: Konversionsrate zu Fibre Max, Steigerung vs. Kontrolle, Installationszeit.

Diagnose: Fallout-Bericht nach Gerät/Genre-Segment.

Form

Wie das alles zusammenpasst (das mentale Modell des Marketing-Experten)

Bedarfsdiagnose (allgemeine Kategorien → Glasfaserkomponenten).

Beweisen Sie den Inhalt für das Konversionssignal (Bestellungen nach Genre).

Meine erfolgreichen Journey (finden Sie Fibernames Journeys und die SciFi-Promo-Zielgruppe).

Reibungspunkte validieren (CJA-Fallout auf SciFi-Journey).

Aktivieren Sie für Segmente mit hoher Neigung (starke Downloader ∩ SciFi).

Geben Sie den folgenden **Prompt** ein und klicken Sie auf die Schaltfläche **Generate**.

```javascript
Create a  journey towards the audience Heavy Downloaders - Sci-Fi Preference_kbaa_5207bf. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

Zurück zu [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}