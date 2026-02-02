---
title: Adobe Analytics & Claude.ai mit MCP-Server
description: Adobe Analytics & Claude.ai mit MCP-Server
kt: 5342
doc-type: tutorial
source-git-commit: 5eb5432251ee7193909ed4ec7decd0d94d0843a2
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 1.5.3 Adobe Analytics &amp; Claude.ai mit MCP-Server

[!BADGE Alpha]

+++Alpha-Details
Durch die Nutzung der CJA &amp; Claude.ai mit dem MCP-Server Alpha erkennen Sie hiermit an, dass die Alpha ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt wird. Adobe ist nicht verpflichtet, die Alpha zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Es wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung solcher Alpha und/oder Begleitmaterialien zu verlassen. Die Alpha gilt als vertrauliche Information von Adobe. Jedes „Feedback“ (Informationen zur Alpha, einschließlich, aber nicht beschränkt auf Probleme oder Mängel, auf die Sie bei der Verwendung der Alpha stoßen, Vorschläge, Verbesserungen und Empfehlungen), das Sie Adobe zur Verfügung stellen, wird hiermit Adobe zugewiesen, einschließlich aller Rechte, Titel und Interessen an diesem Feedback.

+++

## Video

In diesem Video erhalten Sie eine Erklärung und Demonstration aller Schritte, die an dieser Übung beteiligt sind.

>[!VIDEO](https://video.tv.adobe.com/v/3479562?quality=12&learn=on)

## 1.5.3.1 Erstellen einer benutzerdefinierten App in Claude.ai für Adobe Analytics

>[!NOTE]
>
>Die Verwendung von Adobe Analytics in Claude.ai erfordert Folgendes:
>- eine kostenpflichtige Version von Claude.ai
>- Verwenden des Claude.ai-Webclients

Navigieren Sie zu [https://claude.ai/](https://claude.ai/){target="_blank"} und melden Sie sich mit Ihren Kontodetails an. Sobald Sie angemeldet sind, sollten Sie dies sehen. Klicken Sie auf das Symbol **+**.

![Claude.ai](./images/claudeaa1.png)

Wählen Sie **Connectoren hinzufügen** aus.

![Claude.ai](./images/claudeaa2.png)

Klicken Sie **Benutzerdefinierte hinzufügen**.

![Claude.ai](./images/claudeaa3.png)

Füllen Sie die Felder wie folgt aus:

- **Name**: `CJA`
- **MCP-Server-URL**: Wenden Sie sich an den Adobe-Support

Klicken Sie auf **Hinzufügen**.

![Claude.ai](./images/claudeaa4.png)

Sie sollten das dann sehen. Klicken Sie auf **Verbinden**.

![Claude.ai](./images/claudeaa5.png)

Sobald Sie erfolgreich authentifiziert wurden, sollten Sie dies sehen. Klicken Sie auf das **+**-Symbol, um einen neuen Chat zu starten.

![Claude.ai](./images/claudeaa6.png)

Wechseln Sie zu **+**, zu **Connectoren** und Sie sollten sehen, dass der **Adobe Analytics**-Connector jetzt aktiviert ist.

![Claude.ai](./images/claudeaa7.png)

Sie können nun mit der Datenanalyse beginnen.

![Claude.ai](./images/claudeaa8.png)

## 1.5.3.2 in Adobe Analytics festlegen

Bevor Sie über Claude.ai weiter mit CJA interagieren, muss der Kontext festgelegt werden.

Für diese Übung muss der Kontext auf Folgendes festgelegt werden:

- **Report Suite**: **CID - Demodaten**

Die Einstellung Report Suite hilft zu identifizieren, welche Daten Claude.ai beim Stellen von Fragen berücksichtigen sollte.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
list report suites
```

![Claude.ai](./images/claudeaa9.png)

Wählen Sie **Immer zulassen** aus.

![Claude.ai](./images/claudeaa10.png)

Wählen Sie **Immer zulassen** aus.

![Claude.ai](./images/claudeaa11.png)

Sie sollten dann so etwas sehen.

![Claude.ai](./images/claudeaa12.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
use report suite CID Demo Data
```

![Claude.ai](./images/claudeaa13.png)

Wählen Sie **Immer zulassen** aus.

![Claude.ai](./images/claudeaa14.png)

Ihre Report Suite wurde jetzt ausgewählt.

![Claude.ai](./images/claudeaa15.png)

## 1.5.2.3 Erkunden der Report Suite

Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**, um zu ermitteln, welche Metriken und Dimensionen Ihnen zur Verfügung stehen.

```javascript
list the available metrics and dimensions
```

![Claude.ai und CJA](./images/claudeaa101.png)

Wählen Sie **Immer zulassen** aus.

![Claude.ai und CJA](./images/claudeaa102.png)

Wählen Sie **erneut** Immer“ aus.

![Claude.ai und CJA](./images/claudeaa103.png)

Sie sollten dann diese Antwort sehen, die die Metriken und Dimensionen enthält, die in dieser Report Suite eingerichtet wurden.

![Claude.ai und CJA](./images/claudeaa104.png)

## 1.5.2.4 Berichte

Jetzt können Sie beginnen, die Daten zu untersuchen. Beginnen Sie, indem Sie die unten stehende Eingabeaufforderung eingeben und auf **Senden** klicken, um Ihre Berichtsanfrage zu senden.

```javascript
show me pageviews for Feb 2?
```

![Claude.ai und CJA](./images/claudeaa105.png)

Sie sollten dann so etwas sehen.

![Claude.ai und CJA](./images/claudeaa106.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
break down pageviews by page name
```

![Claude.ai und CJA](./images/claudeaa107.png)

Sie sollten das dann sehen.

![Claude.ai und CJA](./images/claudeaa108.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
give me an overview of page names, page views by marketing channel
```

![Claude.ai und CJA](./images/claudeaa109.png)

Sie sollten dann so etwas sehen.

![Claude.ai und CJA](./images/claudeaa110.png)

Scrollen Sie ein wenig nach unten, um die Analyse zu sehen.

![Claude.ai und CJA](./images/claudeaa111.png)

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
Analyze different metrics by marketing channel
```

![Claude.ai und CJA](./images/claudeaa112.png)

Sie sollten dann so etwas sehen.

![Claude.ai und CJA](./images/claudeaa113.png)

Sie haben jetzt diese Übung beendet.

Zurück zu [Analytics und Agenten](./analyticsagents.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}