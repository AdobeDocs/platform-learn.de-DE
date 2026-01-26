---
title: Adobe Marketing Agent mit Microsoft Copilot
description: Adobe Marketing Agent mit Microsoft Copilot
kt: 5342
doc-type: tutorial
source-git-commit: 1eafbf27de93b45288bec8cb3cd70f04e8cc715e
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 5%

---

# 1.1.3 Adobe Marketing Agent mit Microsoft Copilot

[!BADGE Beta]

+++Details anzeigen
Durch die Verwendung des Adobe Marketing Agent mit Microsoft Copilot Beta erkennen Sie hiermit an, dass der Beta ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt wird. Adobe ist nicht verpflichtet, die Beta zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Es wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung solcher Beta und/oder Begleitmaterialien zu verlassen. Die Beta gilt als vertrauliche Information von Adobe.  Jedes „Feedback“ (Informationen zur Beta-Version, insbesondere Probleme oder Mängel, auf die Sie bei der Verwendung der Beta-Version stoßen, Vorschläge, Verbesserungen und Empfehlungen), das sie Adobe geben, wird hiermit Adobe zugewiesen, einschließlich aller Rechte, Titel und Interessen an diesem Feedback.

+++

>[!IMPORTANT]
>
>In diesem Labor wird eine Funktion verwendet, die noch nicht veröffentlicht wurde. Die Funktion wird noch entwickelt, sodass sie noch nicht allgemein verfügbar ist.

## Voraussetzungen

Um die Schritte in diesem Labor wie unten beschrieben zu befolgen, ist der folgende Zugriff erforderlich:

- Zugriff auf Real-Time CDP, Journey Optimizer und Customer Journey Analytics
- Zugriff auf den KI-Assistenten in Adobe Experience Cloud
- Zugriff auf AEP Agent Orchestrator
- Zugriff auf Microsoft Copilot

## Video

In diesem Video erhalten Sie eine Erklärung und Demonstration aller Schritte, die an dieser Übung beteiligt sind.

>[!VIDEO](https://video.tv.adobe.com/v/3479158?quality=12&learn=on)

## 1.1.3.1 Adobe Marketing Agent zu Microsoft Teams und Copilot hinzufügen

Öffnen Sie Microsoft Teams und melden Sie sich mit Ihren Kontodetails an. Sobald Sie angemeldet sind, sollten Sie dies sehen.

Klicken Sie auf **Apps**.

![ChatGPT](./images/copilot1.png)

Wählen Sie **Apps verwalten** aus.

![ChatGPT](./images/copilot2.png)

Wählen **App hochladen**.

![ChatGPT](./images/copilot3.png)

Wählen Sie **Benutzerdefinierte App hochladen** aus.

![ChatGPT](./images/copilot4.png)

Wählen Sie die Manifestdatei aus, die Ihnen von Ihrem Kursleiter gegeben wurde, und klicken Sie auf **Öffnen**.

![ChatGPT](./images/copilot5.png)

Klicken Sie auf **Hinzufügen**.

![ChatGPT](./images/copilot6.png)

Klicken Sie **Mit Copilot öffnen**.

![ChatGPT](./images/copilot7.png)

Adobe Marketing Agent wurde erfolgreich geladen.

![ChatGPT](./images/copilot8.png)

Geben Sie den `login` ein und klicken Sie auf die Schaltfläche **Senden**.

![ChatGPT](./images/copilotlogin1.png)

Klicken Sie **Bei Adobe Marketing Agent anmelden**.

![ChatGPT](./images/copilotlogin2.png)

Daraufhin wird ein neues Fenster geöffnet, in dem Sie aufgefordert werden, sich mit Ihren Adobe-Kontoanmeldeinformationen anzumelden.

![ChatGPT](./images/copilotlogin3.png)

Nach erfolgreicher Authentifizierung müssen Sie möglicherweise die spezifische Instanz auswählen, die Sie verwenden möchten. Wenn Sie diesen Bildschirm sehen, wählen Sie bitte die Instanz —aepImsOrgName— aus.

![ChatGPT](./images/copilotlogin4.png)

Anschließend wird ein ähnlicher Code generiert. Klicken Sie **Kopieren**, um den Code zu kopieren.

![ChatGPT](./images/copilotlogin5.png)

Fügen Sie den Code in das Adobe Marketing Agent-Fenster in Copilot ein und klicken Sie auf die **Senden**-Schaltfläche.

![ChatGPT](./images/copilotlogin6.png)

Sie sollten dann etwas Ähnliches sehen. Sie sind jetzt in Microsoft Copilot erfolgreich bei Adobe Marketing Agent angemeldet.

![ChatGPT](./images/copilotlogin7.png)

## 1.1.3.2 in Adobe Marketing Agent festlegen

Bevor Sie über Copilot weiter mit Adobe Marketing Agent interagieren, muss der Kontext festgelegt werden.

Für diese Übung muss der Kontext auf Folgendes festgelegt werden:

- **Sandbox**: **prod - Accelerate (VA7)**

  Die Sandbox-Einstellung hilft zu identifizieren, welchen Sandbox-KI-Assistenten beim Stellen von Fragen berücksichtigen sollte.

- **Datenansicht**: **Accelerate 2026 B2C**

  Die Datenansichtseinstellung hilft zu ermitteln, welchen Datenansichts-KI-Assistenten beim Stellen von Fragen berücksichtigen sollte.

![Agent Orchestrator](./images/copilotlogin7.png)

Um die Sandbox zu ändern, geben Sie den folgenden Befehl ein und klicken Sie auf die Schaltfläche **Senden**.

```javascript
change sandbox
```

![Agent Orchestrator](./images/copilot9.png)

Sie sollten dann etwas Ähnliches sehen. Wählen Sie die gewünschte Sandbox aus und klicken Sie auf **Auswählen**.

![Agent Orchestrator](./images/copilot10.png)

Sie sollten das dann sehen. Um die Datenansicht zu ändern, geben Sie den folgenden Befehl ein und klicken Sie auf die Schaltfläche **Senden**.

```javascript
change dataview
```

![Agent Orchestrator](./images/copilot11.png)

Sie sollten dann etwas Ähnliches sehen. Wählen Sie die gewünschte Datenansicht aus und klicken Sie auf **Auswählen**.

![Agent Orchestrator](./images/copilot12.png)

Sie sollten das dann sehen. Der Kontext ist jetzt korrekt eingestellt, sodass Sie als Nächstes mit dem Senden bestimmter Eingabeaufforderungen beginnen können.

![Agent Orchestrator](./images/copilot13.png)

## 1.1.3.3 Beginnen Sie mit den allgemeinen Kauftrends, um den Kontext zu verankern und in Fasern zu zoomen.

**Intent**

Erhalten Sie einen Top-Level-Puls auf Kategorieabruf - Mobil, Festnetz, Internet, TV, Glasfaser - speziell für die letzten 60 Tage. Dies legt die Grundlinien für die Saisonabhängigkeit, die Werbeeffekte und die regionale Varianz nach dem Rollout von New York fest.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me purchases by mainCategory over the last 4 months.
```

![Agent Orchestrator](./images/copilot18.png)

Sie sollten dies dann sehen:

![Agent Orchestrator](./images/copilot19.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me purchases by mainCategory = Fiber over the last 4 months broken down by week
```

![Agent Orchestrator](./images/copilot20.png)

Sie sollten das dann sehen, welches sich detailliert mit faserspezifischen Trends beschäftigt.

![Agent Orchestrator](./images/copilot21.png)

## 1.1.3.4 Korrelieren von Bestellungen mit Inhaltseinstellungen

**Intent**

Testen Sie die Hypothese, dass eine Präferenz für ein bestimmtes Genre (z. B. SciFi, Sport, Drama) das Breitband-Upgrade-Verhalten vorhersagt - insbesondere bei hohen Bandbreitenanforderungen.

Zunächst müssen Sie herausfinden, welches Feld zum Speichern der Genre-Voreinstellung verwendet wird.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Which field is used to store the preferred genre
```

![Agent Orchestrator](./images/copilot22.png)

Sie sollten dies dann sehen, was zeigt, dass das für Genre verwendete Feld **_experienceplatform.individualCharacteristics.preferences.preferencesGenre** ist.

![Agent Orchestrator](./images/copilot23.png)

Mit diesen Informationen können Sie mit dem Drilldown in den Kaufdaten beginnen.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me ordersYTD by preferredGenre for the last 4 months
```

![Agent Orchestrator](./images/copilot24.png)

Sie sollten das dann sehen. Klicken Sie **Daten anzeigen**.

![Agent Orchestrator](./images/copilot25.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/copilot26.png)

## 1.1.3.5 Identifizieren vorhandener Fibre-Journey

**Intent**

Finden Sie heraus, welche aktiven oder kürzlich abgeschlossenen Journey „Fibre“ im Titel enthalten - z. B. „Fibre Upgrade NYC - Sept“, „Fibre Trial - Streaming Bundle“.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/copilot28.png)

Sie sollten dann eine Liste der Journey sehen.

![Agent Orchestrator](./images/copilot29.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/copilot31.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/copilot33.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![Agent Orchestrator](./images/copilot35.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/copilot36.png)

## 1.1.3.6 Validieren der Journey-Performance über Fallout-Analyse

**Intent**

Sie sollten wissen, ob es auf der Journey Knoten oder Bedingungen gibt, bei denen eine große Anzahl von Journey-Profilen gelöscht wird. Dies ist hilfreich, um zu verstehen, ob zusätzliche Anpassungen im Journey erforderlich sind.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/copilot37.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/copilot38.png)

Scrollen Sie ein wenig weiter nach unten, um Beobachtungen und Empfehlungen zu sehen. Klicken Sie auf die 3-Punkte-**…** und wählen Sie dann **Journey-Details**, um die jeweilige Journey in Adobe Journey Optimizer zu öffnen.

![Agent Orchestrator](./images/copilot40.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/copilot41.png)

Sie haben jetzt dieses Labor abgeschlossen.

Zurück zu [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}