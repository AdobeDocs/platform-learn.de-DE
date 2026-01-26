---
title: CJA und ChatGPT mit MCP-Server
description: CJA und ChatGPT mit MCP-Server
kt: 5342
doc-type: tutorial
source-git-commit: ca2812e14a22b80b7f00066f9cc482e708b4ac6a
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# 1.5.1 CJA und ChatGPT mit MCP-Server

>[!IMPORTANT]
>
>In diesem Labor wird eine Funktion verwendet, die noch nicht veröffentlicht wurde. Die Funktion wird noch entwickelt, sodass sie noch nicht allgemein verfügbar ist.


>[!NOTE]
>
>Diese Übung zum Einrichten und Verwenden eines MCP-Servers mit ChatGPT zur Verbindung mit CJA steht im Zusammenhang mit dieser Übung [1.1 Customer Journey Analytics: Erstellen eines Dashboards mit Analysis Workspace auf Adobe Experience Platform](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/customer-journey-analytics-build-a-dashboard.md). Die CJA-Datenansicht und -Verbindung, die in der folgenden Übung verwendet wird, ist die Datenansicht und -verbindung, die in dieser Übung eingerichtet wurde. Wenn Sie die folgenden Ergebnisse replizieren möchten, sollten Sie zuerst diese Anweisungen befolgen.

## Video

In diesem Video erhalten Sie eine Erklärung und Demonstration aller Schritte, die an dieser Übung beteiligt sind.

>[!VIDEO](https://video.tv.adobe.com/v/3479159?quality=12&learn=on)

## 1.5.1.1 Erstellen einer benutzerdefinierten App in ChatGPT für CJA

>[!NOTE]
>
>Die Verwendung von CJA in ChatGPT erfordert Folgendes:
>- eine kostenpflichtige Version von OpenAI ChatGPT
>- Verwenden des ChatGPT-Web-Clients

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

- **Name**: `CJA`
- **MCP-Server-URL**: Wenden Sie sich an den Adobe-Support
- **Authentifizierung**: `OAuth`

Aktivieren Sie das Kontrollkästchen für **Ich verstehe und möchte fortfahren**.

Klicken Sie auf **Erstellen**.

![ChatGPT](./images/chatgpt6.png)

Nachdem Sie sich erfolgreich angemeldet haben, sollten Sie sehen, dass Ihre CJA-App jetzt erfolgreich verbunden ist.

![ChatGPT](./images/chatgpt8.png)

## 1.5.1.2 in CJA festlegen

Schließen Sie dieses Fenster.

![ChatGPT und CJA](./images/chatgpt9.png)

Sie sollten das dann sehen. Klicken Sie auf das Symbol **+**, gehen Sie zu **Mehr** und wählen Sie dann **CJA** aus.

![ChatGPT und CJA](./images/chatgpt10.png)

Bevor Sie über ChatGPT weiter mit CJA interagieren, muss der Kontext festgelegt werden.

Für diese Übung muss der Kontext auf Folgendes festgelegt werden:

- **Datenansicht**: **—aepUserLdap— - Omni-Channel-Datenansicht**

Die Einstellung Datenansicht hilft zu identifizieren, welche Datenansicht ChatGPT beim Stellen von Fragen berücksichtigen sollte.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
list dataviews
```

![ChatGPT und CJA](./images/chatgpt11.png)

Anschließend sollte eine ähnliche Liste der verfügbaren Datenansichten angezeigt werden.

![ChatGPT und CJA](./images/chatgpt11a.png)

Um dies in die zu verwendende Datenansicht zu ändern, geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
switch to dataview --aepUserLdap-- - Omnichannel Data View
```

![ChatGPT und CJA](./images/chatgpt12.png)

Sie sollten das dann sehen.

![ChatGPT und CJA](./images/chatgpt16.png)

Ihr Kontext ist jetzt ordnungsgemäß festgelegt, sodass Sie als Nächstes bestimmte Eingabeaufforderungen senden können.

## 1.5.1.3 Erkunden der Datenansicht

>[!NOTE]
>
>Die hier verwendete Datenansicht wurde im Rahmen der Übung [Erstellen einer Datenansicht](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/ex3.md) eingerichtet.

Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**, um zu ermitteln, welche Metriken und Dimensionen Ihnen zur Verfügung stehen.

```javascript
list the available metrics and dimensions
```

![ChatGPT und CJA](./images/chatgpt101.png)

Sie sollten dann diese Antwort sehen, die die Metriken und Dimensionen enthält, die im Rahmen der Übung [Erstellen einer Datenansicht](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/ex3.md) eingerichtet wurden.

![ChatGPT und CJA](./images/chatgpt102.png)

## 1.5.1.4 Freiformtabelle - Produktansichten

Jetzt können Sie beginnen, die Daten zu untersuchen. Beginnen Sie, indem Sie die unten stehende Eingabeaufforderung eingeben und auf **Senden** klicken, um Ihre Berichtsanfrage zu senden.

```javascript
how many product views happened on January 21?
```

![ChatGPT und CJA](./images/chatgpt103.png)

Wählen Sie **RunReport** aus.

![ChatGPT und CJA](./images/chatgpt104.png)

Sie sollten dann eine Antwort wie diese sehen.

![ChatGPT und CJA](./images/chatgpt105.png)

Sie können die Antwort jetzt aufschlüsseln, indem Sie eine Dimension hinzufügen. Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
break down product views by product name
```

![ChatGPT und CJA](./images/chatgpt106.png)

Sie sollten dann eine Antwort wie diese sehen.

![ChatGPT und CJA](./images/chatgpt107.png)

Jetzt können Sie auch eine Visualisierung erstellen. Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
create a line visualization by hour for product views on January 21
```

![ChatGPT und CJA](./images/chatgpt108.png)

Wählen Sie **UpsertProject** aus.

![ChatGPT und CJA](./images/chatgpt109.png)

Wählen Sie **RunReport** aus.

![ChatGPT und CJA](./images/chatgpt110.png)

Sie sollten das dann sehen.

![ChatGPT und CJA](./images/chatgpt111.png)

Scroll down.

![ChatGPT und CJA](./images/chatgpt112.png)

Sie können dieses Liniendiagramm jetzt auch herunterladen. Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
export this chart to PNG
```

![ChatGPT und CJA](./images/chatgpt113.png)

Sie sollten das dann sehen. Klicken Sie **PNG herunterladen**.

![ChatGPT und CJA](./images/chatgpt114.png)

Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
can you breakdown product views by user agent?
```

![ChatGPT und CJA](./images/chatgpt115.png)

Wählen Sie **RunReport** aus.

![ChatGPT und CJA](./images/chatgpt116.png)

Sie sollten das dann sehen.

![ChatGPT und CJA](./images/chatgpt117.png)

## 1.5.1.5 Fallout-Visualisierung

Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
can you create a fallout visualization for the product interaction funnel, starting with all traffic and then in the next steps add Product Views, Add to Cart and purchases?
```

![ChatGPT und CJA](./images/chatgpt118.png)

Wählen Sie **UpsertProject** aus.

![ChatGPT und CJA](./images/chatgpt119.png)

Wählen Sie **RunReport** aus.

![ChatGPT und CJA](./images/chatgpt120.png)

Sie sollten dann so etwas sehen. Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
can you show me a visualization of the above fallout analysis?
```

![ChatGPT und CJA](./images/chatgpt120a.png)

Klicken Sie **PNG herunterladen**.

![ChatGPT und CJA](./images/chatgpt121.png)

Jetzt sehen Sie die Visualisierung Ihrer Fallout-Analyse.

![ChatGPT und CJA](./images/chatgpt122.png)

Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
break down the fallout analysis at the touchpoint of the add to carts
```

![ChatGPT und CJA](./images/chatgpt123.png)

Wählen Sie **RunReport** aus.

![ChatGPT und CJA](./images/chatgpt124.png)

Zurück zu [Analytics und Agenten](./analyticsagents.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}