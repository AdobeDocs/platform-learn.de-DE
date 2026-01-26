---
title: Adobe Marketing Agent für ChatGPT Enterprise
description: Adobe Marketing Agent für ChatGPT Enterprise
kt: 5342
doc-type: tutorial
source-git-commit: 44d0e98ae4c7568411cb0e01ed8eff38b4a34137
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 4%

---

# 1.1.2 Adobe Marketing Agent für ChatGPT Enterprise

>[!IMPORTANT]
>
>In diesem Labor wird eine Funktion verwendet, die noch nicht veröffentlicht wurde. Die Funktion wird noch entwickelt, sodass sie noch nicht allgemein verfügbar ist.

[!BADGE In Entwicklung]

+++In Entwicklungsdetails
Durch die Verwendung der Adobe Marketing Agent für ChatGPT Enterprise Beta erkennen Sie hiermit an, dass die Beta ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt wird. Adobe ist nicht verpflichtet, die Beta zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Es wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung solcher Beta und/oder Begleitmaterialien zu verlassen. Die Beta gilt als vertrauliche Information von Adobe.  Jedes „Feedback“ (Informationen zur Beta-Version, insbesondere Probleme oder Mängel, auf die Sie bei der Verwendung der Beta-Version stoßen, Vorschläge, Verbesserungen und Empfehlungen), das sie Adobe geben, wird hiermit Adobe zugewiesen, einschließlich aller Rechte, Titel und Interessen an diesem Feedback.

+++

## Video

In diesem Video erhalten Sie eine Erklärung und Demonstration aller Schritte, die an dieser Übung beteiligt sind.

>[!VIDEO](https://video.tv.adobe.com/v/3478410?quality=12&learn=on)

## 1.1.2.1 Erstellen einer benutzerdefinierten App in ChatGPT Enterprise für Adobe Marketing Agent

>[!NOTE]
>
>Die Verwendung von Adobe Marketing Agent in ChatGPT erfordert Folgendes:
>- eine kostenpflichtige Version von OpenAI ChatGPT Enterprise
>- Verwenden des ChatGPT Enterprise-Webclients

Navigieren Sie zu [https://chatgpt.com/](https://chatgpt.com/){target="_blank"} und melden Sie sich mit Ihren Kontodetails an. Sobald Sie angemeldet sind, sollten Sie dies sehen. Klicken Sie auf Ihren Benutzernamen.

![ChatGPT](./images/chatgpt1.png)

Wählen Sie **Einstellungen** aus.

![ChatGPT](./images/chatgpt2.png)

Navigieren Sie zu **Apps** und wählen Sie **Erweiterte Einstellungen** aus.

![ChatGPT](./images/chatgpt3.png)

Aktivieren Sie **Entwicklermodus** und klicken Sie dann auf &quot;**&quot;**.

![ChatGPT](./images/chatgpt4.png)

Klicken Sie auf **App erstellen**.

![ChatGPT](./images/chatgpt5.png)

Füllen Sie die Felder wie folgt aus:

- **Name**: `Adobe Marketing Agent`
- **MCP-Server-URL**: Wenden Sie sich an den Adobe-Support
- **Authentifizierung**: `OAuth`

Aktivieren Sie das Kontrollkästchen für **Ich verstehe und möchte fortfahren**.

Klicken Sie auf **Erstellen**.

![ChatGPT](./images/chatgpt6.png)

ChatGPT versucht jetzt, eine Verbindung zu Ihrem Adobe-Konto herzustellen. Wählen **Zugriff zulassen** und Sie müssen sich dann mit Ihrem Adobe-Konto anmelden.

![ChatGPT](./images/chatgpt7.png)

Nachdem Sie sich erfolgreich angemeldet haben, sollten Sie sehen, dass Ihre Adobe Marketing Agent jetzt erfolgreich verbunden ist.

![ChatGPT](./images/chatgpt8.png)

## 1.1.2.2 in Adobe Marketing Agent festlegen

Schließen Sie dieses Fenster.

![Agent Orchestrator](./images/chatgpt9.png)

Sie sollten das dann sehen. Klicken Sie auf das Symbol **+**, gehen Sie zu **Mehr** und wählen Sie dann **Adobe Marketing Agent** aus.

![Agent Orchestrator](./images/chatgpt10.png)

Bevor Sie über ChatGPT weiter mit Adobe Marketing Agent interagieren, muss der Kontext festgelegt werden.

Für diese Übung muss der Kontext auf Folgendes festgelegt werden:

- **Sandbox**: **prod - Accelerate (VA7)**

Die Sandbox-Einstellung hilft zu identifizieren, welche Sandbox ChatGPT beim Stellen von Fragen betrachtet werden sollte.

- **Datenansicht**: **Accelerate 2026 B2C**

Die Einstellung Datenansicht hilft zu identifizieren, welche Datenansicht ChatGPT beim Stellen von Fragen berücksichtigen sollte.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
list sandboxes
```

![Agent Orchestrator](./images/chatgpt11.png)

Anschließend sollte eine ähnliche Liste der verfügbaren Sandboxes angezeigt werden. Die aktuelle Sandbox in diesem Beispiel ist auf &quot;**&quot;**.

Um dies in die zu verwendende Sandbox zu ändern, geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
switch to sandbox accelerate
```

![Agent Orchestrator](./images/chatgpt12.png)

Sie sollten das dann sehen. Klicken Sie **Kontext festlegen**.

![Agent Orchestrator](./images/chatgpt13.png)

Sie sollten das dann sehen. Geben Sie die folgende **Eingabeaufforderung** ein und klicken Sie auf die Schaltfläche **Senden**, um die zu verwendende Datenansicht festzulegen.

```javascript
list dataviews
```

![Agent Orchestrator](./images/chatgpt14.png)

Anschließend sollte eine ähnliche Liste der verfügbaren Datenansichten angezeigt werden.

Um die zu verwendende Datenansicht festzulegen, geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
switch to Accelerate 2026 B2C
```

![Agent Orchestrator](./images/chatgpt15.png)

Sie sollten das dann sehen. Klicken Sie **Kontext festlegen**.

![Agent Orchestrator](./images/chatgpt16.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/chatgpt17.png)

Ihr Kontext ist jetzt ordnungsgemäß festgelegt, sodass Sie als Nächstes mit dem Senden bestimmter Eingabeaufforderungen beginnen können.

## 1.1.2.3 Beginnen Sie mit den allgemeinen Kauftrends, um den Kontext zu verankern und in Fasern zu zoomen.

**Intent**

Erhalten Sie einen Top-Level-Puls auf Kategorieabruf - Mobil, Festnetz, Internet, TV, Glasfaser - speziell für die letzten 60 Tage. Dies legt die Grundlinien für die Saisonabhängigkeit, die Werbeeffekte und die regionale Varianz nach dem Rollout von New York fest.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![Agent Orchestrator](./images/chatgpt18.png)

Sie sollten dies dann sehen:

![Agent Orchestrator](./images/chatgpt19.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me purchases by mainCategory = Fiber over the last 2 months per week
```

![Agent Orchestrator](./images/chatgpt20.png)

Sie sollten das dann sehen, welches sich detailliert mit faserspezifischen Trends beschäftigt.

![Agent Orchestrator](./images/chatgpt21.png)

## 1.1.2.4 Korrelieren von Bestellungen mit Inhaltseinstellungen

**Intent**

Testen Sie die Hypothese, dass eine Präferenz für ein bestimmtes Genre (z. B. SciFi, Sport, Drama) das Breitband-Upgrade-Verhalten vorhersagt - insbesondere bei hohen Bandbreitenanforderungen.

Zunächst müssen Sie herausfinden, welches Feld zum Speichern der Genre-Voreinstellung verwendet wird.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Which field is used to store the preferred genre in the sandbox accelerate?
```

![Agent Orchestrator](./images/chatgpt22.png)

Sie sollten dies dann sehen, was zeigt, dass das für Genre verwendete Feld **_experienceplatform.individualCharacteristics.preferences.preferencesGenre** ist.

![Agent Orchestrator](./images/chatgpt23.png)

Mit diesen Informationen können Sie mit dem Drilldown in den Kaufdaten beginnen.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![Agent Orchestrator](./images/chatgpt24.png)

Sie sollten das dann sehen. Klicken Sie auf **Recherche**.

![Agent Orchestrator](./images/chatgpt25.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/chatgpt26.png)

Scrollen Sie nach unten, um weitere Informationen anzuzeigen.

![Agent Orchestrator](./images/chatgpt27.png)

## 1.1.2.5 Identifizieren vorhandener Fibre-Journey

**Intent**

Finden Sie heraus, welche aktiven oder kürzlich abgeschlossenen Journey „Fibre“ im Titel enthalten - z. B. „Fibre Upgrade NYC - Sept“, „Fibre Trial - Streaming Bundle“.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/chatgpt28.png)

Sie sollten das dann sehen. Klicken Sie auf **Recherche**.

![Agent Orchestrator](./images/chatgpt29.png)

Sie sollten dann eine Liste der Journey sehen.

![Agent Orchestrator](./images/chatgpt30.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/chatgpt31.png)

Sie sollten das dann sehen. Klicken Sie auf **Recherche**.

![Agent Orchestrator](./images/chatgpt32.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/chatgpt33.png)

Scrollen Sie nach unten, um weitere Details anzuzeigen.

![Agent Orchestrator](./images/chatgpt34.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![Agent Orchestrator](./images/chatgpt35.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/chatgpt36.png)

## 1.1.2.6 Validieren der Journey-Performance über Fallout-Analyse

**Intent**

Sie sollten wissen, ob es auf der Journey Knoten oder Bedingungen gibt, bei denen eine große Anzahl von Journey-Profilen gelöscht wird. Dies ist hilfreich, um zu verstehen, ob zusätzliche Anpassungen im Journey erforderlich sind.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/chatgpt37.png)

Sie sollten das dann sehen.

![Agent Orchestrator](./images/chatgpt38.png)

Scroll ein bisschen nach unten. Sie können die Tabelle nun überprüfen, indem Sie jeden Knoten und seine entsprechenden Eingeben von Zahlen, Fallout-Zahlen und Fallout-Rate überprüfen.

![Agent Orchestrator](./images/chatgpt39.png)

Scrollen Sie ein wenig weiter nach unten, um Beobachtungen und Empfehlungen zu sehen.

![Agent Orchestrator](./images/chatgpt40.png)

Sie haben jetzt dieses Labor abgeschlossen.

Zurück zu [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}