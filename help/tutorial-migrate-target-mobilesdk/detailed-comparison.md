---
title: Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung
description: Erfahren Sie mehr über die Unterschiede zwischen der Target-Erweiterung und der Decisioning-Erweiterung, einschließlich Funktionen, Einstellungen und Datenfluss.
source-git-commit: 78d04d625aa55ce5eb76615c220b49aefd958431
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 4%

---

# Vergleich der Target-Erweiterung mit der Decisioning-Erweiterung

Die Adobe Journey Optimizer - Decisioning-Erweiterung unterscheidet sich von der Adobe Target-Erweiterung für mobile Apps. Die folgenden Tabellen sind eine Referenz, die Sie bei der Bewertung von Bereichen Ihrer Implementierung unterstützen soll, auf die Sie sich während des Migrationsprozesses konzentrieren müssen.

Nachdem Sie die unten stehenden Informationen überprüft und Ihre aktuelle technische Target-Erweiterungsimplementierung bewertet haben, sollten Sie Folgendes verstehen:

- Welche Target-Funktionen werden von Adobe Journey Optimizer unterstützt - Decisioning
- Welche Adobe Target-Erweiterungsfunktionen verfügen über Adobe Journey Optimizer - Decisioning-Entsprechungen
- Anwendung von Target-Einstellungen mit Adobe Journey Optimizer - Decisioning
- Unterschiede zwischen dem Datenfluss der Adobe Target-Erweiterung und der Adobe Journey Optimizer - Decisioning-Erweiterung

Wenn Sie mit dem Platform Web SDK noch nicht vertraut sind, machen Sie sich keine Gedanken - die unten stehenden Elemente werden in diesem Tutorial ausführlicher behandelt.

## Funktionsvergleich

| Funktion | Target-Erweiterung | Decisioning-Erweiterung (Target über Edge) |
|---|---|---|
| Vorabruf-Modus | Unterstützt | Unterstützt |
| Ausführungsmodus | Unterstützt | Nicht unterstützt |
| Benutzerdefinierte Parameter | Unterstützt | Pro Mbox-Parameter werden nicht unterstützt |
| Einstiegszielgruppen | Unterstützt | Unterstützt |
| Zielgruppensegmentierung mithilfe mobiler Lebenszyklusmetriken | Unterstützt | Unterstützt über Datenerfassungsregeln |
| thirdPartyId (mbox3rdPartyId) | Wird über Identity Map und die Namespace-Konfiguration im Datastream unterstützt |
| Benachrichtigungen (anzeigen, klicken) | Unterstützt | Unterstützt |
| Antwort-Token | Unterstützt | Unterstützt |
| Dynamische Angebote | Unterstützt | Unterstützt |
| Analytics for Target (A4T) | Nur Client-seitig | Client- und Server-seitig |
| Mobile Vorschau (QA-Modus) | Unterstützt | Eingeschränkte Unterstützung |



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

Die folgenden Diagramme sollen Ihnen dabei helfen, die Datenflussunterschiede zwischen einer Target-Implementierung mit der Adobe Journey Optimizer - Decisioning-Erweiterung und einer Implementierung mit der Adobe Target-Erweiterung zu verstehen.

### Systemdiagramm der Target-Erweiterung



### Decisioning Extension-Systemdiagramm




>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Decisioning-Erweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
