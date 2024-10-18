---
title: Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung
description: Lernen Sie die Unterschiede zwischen at.js 2.x und dem Platform Web SDK kennen, einschließlich Funktionen, Einstellungen und Datenfluss.
source-git-commit: afbc8248ad81a5d9080a4fdba1167e09bbf3b33d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 5%

---

# Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung

Die eigenständige Adobe Target at.js-Bibliothek unterscheidet sich erheblich vom Platform Web SDK. Die folgenden Tabellen sind eine Referenz, die Sie bei der Bewertung von Bereichen Ihrer Implementierung unterstützen soll, auf die Sie sich während des Migrationsprozesses konzentrieren müssen.

Nachdem Sie die unten stehenden Informationen überprüft und Ihre aktuelle technische at.js-Implementierung bewertet haben, sollten Sie Folgendes verstehen:

- Welche Target-Funktionen werden vom Platform Web SDK unterstützt?
- Welche at.js-Funktionen verfügen über Platform Web SDK-Entsprechungen
- Anwendung von Target-Einstellungen mit dem Platform Web SDK
- Unterschiede zwischen dem Datenfluss von at.js und dem Platform Web SDK

Wenn Sie mit dem Platform Web SDK noch nicht vertraut sind, machen Sie sich keine Gedanken - die unten stehenden Elemente werden in diesem Tutorial ausführlicher behandelt.

## Funktionsvergleich

| | Target-Erweiterung | Decisioning-Erweiterung (Target über Edge) | AJO Code-basierte Erlebnisse (Messaging SDK) |
|---|---|---|---|
| Vorabruf-Modus | Unterstützt | Unterstützt | Unterstützt |
| Ausführungsmodus | Unterstützt | Nicht unterstützt | Nicht unterstützt |
| Benutzerdefinierte Parameter | Unterstützt | Pro Mbox-Parameter werden nicht unterstützt | Nicht unterstützt |
| Einstiegszielgruppen | Unterstützt | Unterstützt | Unterstützt über Campaign-Audience- und Experiment-Holdout-Einstellung |
| Zielgruppensegmentierung mithilfe mobiler Lebenszyklusmetriken | Unterstützt | Unterstützt über Datenerfassungsregeln | Erlebnis-Targeting wird derzeit nicht unterstützt |
| thirdPartyId (mbox3rdPartyId) | Wird über Identity Map und die Namespace-Konfiguration im Datastream unterstützt | Nicht unterstützt |
| Benachrichtigungen (anzeigen, klicken) | Unterstützt | Unterstützt | Unterstützt |
| Antwort-Token | Unterstützt | Unterstützt | Keine Entsprechung für die Rückgabe von Campaign-spezifischen Metadaten außerhalb des Inhalts |
| Dynamische Angebote | Unterstützt | Unterstützt | Profil- und Entscheidungselement-bezogenes Token-Rendering im Inhalt wird unterstützt |
| Analytics for Target (A4T) | Nur Client-seitig | Client- und Server-seitig | Nicht unterstützt |
| Mobile Vorschau (QA-Modus) | Unterstützt | Eingeschränkte Unterstützung | Bearbeitung läuft |



## Wichtige Hinweise

>[!NOTE]
>
>Die Migration von Target zum Platform Web SDK unter Beibehaltung einer bestehenden AppMeasurement Adobe Analytics-Implementierung für eine bestimmte Seite wird nicht unterstützt.
>
> Es ist möglich, Ihre at.js- (und AppMeasurement.js-) Implementierung auf Platform Web SDK einzeln zu migrieren. Wenn Sie diesen Ansatz wählen, ist es am besten, die Optionen [`idMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) und [`targetMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) mit dem Befehl `configure` auf `true` festzulegen.

## Funktionen der Target-Erweiterung und Entsprechungen der Decisioning-Erweiterung

Viele Target-Erweiterungsfunktionen verfügen über einen gleichwertigen Ansatz unter Verwendung der in der folgenden Tabelle beschriebenen Decisioning-Erweiterung. Weitere Informationen zu den [Funktionen](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/) finden Sie im Adobe Target-Entwicklerhandbuch.

| Target-Erweiterung | Entscheidungserweiterung |
| --- | --- | 
| |  |

## Target-Erweiterungseinstellungen und Entsprechungen von Decisioning-Erweiterungen

Die Target-Erweiterung kann mit verschiedenen Einstellungen in der ...

| Target-Erweiterung | Entscheidungserweiterung |
| --- | --- | 
| |  |


## Vergleich von Systemdiagrammen

Die folgenden Diagramme sollen Ihnen dabei helfen, die Unterschiede zwischen einem Datenfluss zwischen einer Target-Implementierung mit at.js und einer Implementierung mit dem Platform Web SDK zu verstehen.

### Systemdiagramm der Target-Erweiterung



### Decisioning Extensionsystem-Diagramm




>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Decisioning-Erweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
