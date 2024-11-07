---
title: Adobe Experience Platform-Datenerfassung und serverseitige Weiterleitung in Echtzeit
description: In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemas und die Adobe Experience Platform-Datenerfassungsservereigenschaft, um Daten zu erfassen und diese Daten dann Server-seitig an einen gewünschten Endpunkt weiterzuleiten.
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# 2.5 Real-Time CDP-Verbindungen: Ereignisweiterleitung

**Autor: [Wouter van Geluwe](https://www.linkedin.com/in/woutervangeluwe/), [Clement Delalande](https://www.linkedin.com/in/clement-delalande/)**

In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemas und die Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft, um Daten zu erfassen und diese Daten dann Server-seitig an einen gewünschten Endpunkt weiterzuleiten.

In diesem Modul werden Sie:

- Erstellen einer Adobe Experience Platform-Datenerfassungsservereigenschaft
- Installieren und Verwenden der Adobe Cloud Connector-Erweiterung in der Adobe Experience Platform-Datenerfassung
- Google-Funktionsendpunkt erstellen und Daten streamen
- AWS-Endpunkt erstellen und Daten streamen

Sehen Sie sich dieses Video an, um den Wert, die Journey und den Konfigurationsprozess für Kunden zu verstehen:

>[!VIDEO](https://video.tv.adobe.com/v/331987?quality=12&learn=on)

## Lernziele

- Machen Sie sich mit den Eigenschaften des Adobe Experience Platform-Datenerfassungsservers und der neuen Adobe Cloud Connector-Erweiterung vertraut
- Erfahren Sie, wie Sie Adobe Experience Platform Web SDK-Daten in Drittanbieterlösungen wie Google und AWS wiederverwenden können.
- Machen Sie sich mit der Architektur der Datenerfassung und serverseitigen Weiterleitung von Adobe Experience Platform vertraut.

## Voraussetzungen

- Zugriff auf die Datenerfassung von Adobe Experience Platform und Adobe Experience Platform
- Grundlagen zu Adobe Experience Platform-Datensätzen und XDM

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [0.1 - Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../gettingstarted/gettingstarted/ex1.md) beschrieben.

## Übungen

[2.5.1 Eigenschaft &quot;Datenerfassungs-Ereignisweiterleitung&quot;erstellen](./ex1.md)

In dieser Übung erstellen Sie Ihre Adobe Experience Platform-Eigenschaft für die Ereignisweiterleitung zur Datenerfassung.

[2.5.2 Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Datenerfassungs-Ereignisweiterleitungseigenschaft verfügbar zu machen.](./ex2.md)

In dieser Übung aktualisieren Sie Ihr vorhandenes Datastream, um die von Ihrer Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft erfassten Daten für Ihre Adobe Experience Platform-Datenerfassungsservereigenschaft verfügbar zu machen.

[2.5.3 Benutzerdefinierten Webhook erstellen und konfigurieren](./ex3.md)

In dieser Übung erstellen und konfigurieren Sie einen benutzerdefinierten Webhook, und Sie beginnen mit der Weiterleitung von Daten, die vom Web SDK erfasst werden, an diesen benutzerdefinierten Webhook.

[2.5.4 Google Cloud-Funktion erstellen und konfigurieren](./ex4.md)

In dieser Übung erstellen und konfigurieren Sie eine Google Cloud-Funktion und beginnen mit der Weiterleitung von Daten, die vom Web SDK erfasst werden, an Google.

[2.5.5 Weiterleiten von Ereignissen an das AWS-Ökosystem](./ex5.md)

In dieser Übung konfigurieren Sie Ihre AWS-Umgebung mithilfe von AWS API Gateway, AWS Kinesis, AWS Firewalls und AWS S3. Danach beginnen Sie mit der Weiterleitung von Ereignisdaten, die vom Web SDK erfasst werden.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investieren, um alles über Adobe Experience Platform und seine Anwendungen zu erfahren. Wenn Sie Fragen haben, möchten Sie allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com** senden.

[Zu allen Modulen zurückkehren](../../../overview.md)
