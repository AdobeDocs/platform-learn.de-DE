---
title: CJA & Claude.ai mit MCP-Server
description: CJA & Claude.ai mit MCP-Server
kt: 5342
doc-type: tutorial
source-git-commit: b8906d1995dcb470789be2a1297eb48cb7690a9c
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---

# 1.5.2 CJA &amp; Claude.ai mit MCP-Server

[!BADGE Alpha]

+++Alpha-Details
Durch die Nutzung der CJA &amp; Claude.ai mit dem MCP-Server Alpha erkennen Sie hiermit an, dass die Alpha ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt wird. Adobe ist nicht verpflichtet, die Alpha zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Es wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung solcher Alpha und/oder Begleitmaterialien zu verlassen. Die Alpha gilt als vertrauliche Information von Adobe. Jedes „Feedback“ (Informationen zur Alpha, einschließlich, aber nicht beschränkt auf Probleme oder Mängel, auf die Sie bei der Verwendung der Alpha stoßen, Vorschläge, Verbesserungen und Empfehlungen), das Sie Adobe zur Verfügung stellen, wird hiermit Adobe zugewiesen, einschließlich aller Rechte, Titel und Interessen an diesem Feedback.

+++


>[!NOTE]
>
>Diese Übung zum Einrichten und Verwenden eines MCP-Servers mit Claude.ai zum Herstellen einer Verbindung mit CJA steht im Zusammenhang mit dieser Übung [1.1 Customer Journey Analytics: Erstellen eines Dashboards mit Analysis Workspace auf Adobe Experience Platform](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/customer-journey-analytics-build-a-dashboard.md). Die CJA-Datenansicht und -Verbindung, die in der folgenden Übung verwendet wird, ist die Datenansicht und -verbindung, die in dieser Übung eingerichtet wurde. Wenn Sie die folgenden Ergebnisse replizieren möchten, sollten Sie zuerst diese Anweisungen befolgen.

## Video

In diesem Video erhalten Sie eine Erklärung und Demonstration aller Schritte, die an dieser Übung beteiligt sind.

>[!VIDEO](https://video.tv.adobe.com/v/3479159?quality=12&learn=on)

## 1.5.1.1 Erstellen einer benutzerdefinierten App in Claude.ai für CJA

>[!NOTE]
>
>Die Verwendung von CJA in Claude.ai erfordert Folgendes:
>- eine kostenpflichtige Version von Claude.ai
>- Verwenden des Claude.ai-Webclients

Navigieren Sie zu [https://claude.ai/](https://claude.ai/){target="_blank"} und melden Sie sich mit Ihren Kontodetails an. Sobald Sie angemeldet sind, sollten Sie dies sehen. Klicken Sie auf das Symbol **+**.

![Claude.ai](./images/claude1.png)

Wählen Sie **Connectoren hinzufügen** aus.

![Claude.ai](./images/claude2.png)

Klicken Sie **Benutzerdefinierte hinzufügen**.

![Claude.ai](./images/claude3.png)

Füllen Sie die Felder wie folgt aus:

- **Name**: `CJA`
- **MCP-Server-URL**: Wenden Sie sich an den Adobe-Support

Klicken Sie auf **Hinzufügen**.

![Claude.ai](./images/claude4.png)

Sie sollten das dann sehen. Klicken Sie auf **Hinzufügen**.

![Claude.ai](./images/claude5.png)

Sobald Sie erfolgreich authentifiziert wurden, sollten Sie dies sehen. Klicken Sie auf das **+**-Symbol, um einen neuen Chat zu starten.

![Claude.ai](./images/claude6.png)

Wechseln Sie zu **+**, zu **Connectoren** und Sie sollten sehen, dass der **CJA**-Connector jetzt aktiviert ist.

![Claude.ai](./images/claude8.png)

Sie können nun mit der Datenanalyse beginnen.

![Claude.ai](./images/claude7.png)


## 1.5.1.2 in CJA festlegen

Bevor Sie über Claude.ai weiter mit CJA interagieren, muss der Kontext festgelegt werden.

Für diese Übung muss der Kontext auf Folgendes festgelegt werden:

- **Datenansicht**: **—aepUserLdap— - Omni-Channel-Datenansicht**

Die Einstellung Datenansicht hilft zu identifizieren, welche Datenansicht Claude.ai beim Stellen von Fragen betrachten sollte.

Geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
list dataviews
```

![Claude.ai und CJA](./images/claude9.png)

Wählen Sie **Immer zulassen** aus.

![Claude.ai und CJA](./images/claude10.png)

Anschließend sollte eine ähnliche Liste der verfügbaren Datenansichten angezeigt werden.

![Claude.ai und CJA](./images/claude11.png)

Um dies in die zu verwendende Datenansicht zu ändern, geben Sie Folgendes ein **Eingabeaufforderung** und klicken Sie auf die Schaltfläche **Senden**.

```javascript
switch to dataview --aepUserLdap-- - Omnichannel Data View
```

![Claude.ai und CJA](./images/claude11a.png)

Wählen Sie **Immer zulassen** aus.

![Claude.ai und CJA](./images/claude12.png)

Sie sollten das dann sehen.

![Claude.ai und CJA](./images/claude16.png)

Ihr Kontext ist jetzt ordnungsgemäß festgelegt, sodass Sie als Nächstes bestimmte Eingabeaufforderungen senden können.

## 1.5.1.3 Erkunden der Datenansicht

>[!NOTE]
>
>Die hier verwendete Datenansicht wurde im Rahmen der Übung [Erstellen einer Datenansicht](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/ex3.md) eingerichtet.

Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**, um zu ermitteln, welche Metriken und Dimensionen Ihnen zur Verfügung stehen.

```javascript
list the available metrics and dimensions
```

![Claude.ai und CJA](./images/claude101.png)

Wählen Sie **Immer zulassen** zweimal aus, einmal zum Abrufen **Metriken** und ein zweites Mal zum Abrufen **Dimensionen**.

![Claude.ai und CJA](./images/claude101a.png)

Sie sollten dann diese Antwort sehen, die die Metriken und Dimensionen enthält, die im Rahmen der Übung [Erstellen einer Datenansicht](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/ex3.md) eingerichtet wurden.

![Claude.ai und CJA](./images/claude102.png)

## 1.5.1.4 Freiformtabelle - Produktansichten

Jetzt können Sie beginnen, die Daten zu untersuchen. Beginnen Sie, indem Sie die unten stehende Eingabeaufforderung eingeben und auf **Senden** klicken, um Ihre Berichtsanfrage zu senden.

```javascript
how many product views happened on January 21, 2026?
```

![Claude.ai und CJA](./images/claude103.png)

Wählen Sie **Immer zulassen** aus.

![Claude.ai und CJA](./images/claude104.png)

Sie sollten dann eine Antwort wie diese sehen.

![Claude.ai und CJA](./images/claude105.png)

Sie können die Antwort jetzt aufschlüsseln, indem Sie eine Dimension hinzufügen. Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
break down product views by product name
```

![Claude.ai und CJA](./images/claude106.png)

Sie sollten dann eine Antwort wie diese sehen.

![Claude.ai und CJA](./images/claude107.png)

Jetzt können Sie auch eine Visualisierung erstellen. Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
create a line visualization by hour for product views on January 21
```

![Claude.ai und CJA](./images/claude108.png)

Sie sollten das dann sehen.

![Claude.ai und CJA](./images/claude109.png)

Sie können dieses Liniendiagramm jetzt auch herunterladen. Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
export this chart to PNG
```

![Claude.ai und CJA](./images/claude113.png)

Sie sollten das dann sehen. Klicken Sie **Herunterladen**.

![Claude.ai und CJA](./images/claude114.png)

Sie können dann das heruntergeladene PNG öffnen und in anderen Dokumenten verwenden.

![Claude.ai und CJA](./images/claude114a.png)

Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
can you breakdown product views by user agent?
```

![Claude.ai und CJA](./images/claude115.png)

Sie sollten das dann sehen.

![Claude.ai und CJA](./images/claude117.png)

## 1.5.1.5 Fallout-Visualisierung

Geben Sie die folgende **ein** klicken Sie auf die Schaltfläche **Senden**.

```javascript
can you create a fallout visualization for the product interaction funnel, starting with all traffic and then in the next steps add Product Views, Add to Cart and purchases?
```

![Claude.ai und CJA](./images/claude118.png)

Sie sollten dann so etwas sehen, das eine Visualisierung enthält, die von Claude.ai basierend auf den von Customer Journey Analytics bereitgestellten Daten generiert wurde.

![Claude.ai und CJA](./images/claude119.png)

Zurück zu [Analytics und Agenten](./analyticsagents.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}