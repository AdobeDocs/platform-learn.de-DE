---
title: Adobe Experience Platform-Datenerfassung und Server-seitige Echtzeit-Weiterleitung
description: In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemata und die Datenerfassungsserver-Eigenschaft von Adobe Experience Platform, um Daten zu erfassen, und leiten diese Daten dann Server-seitig an einen Endpunkt Ihrer Wahl weiter.
kt: 5342
doc-type: tutorial
exl-id: dbf5e995-9c2e-4f72-b336-e942cb22cde5
source-git-commit: 2d5ca888eb24c1f65b4ecd48030ec8d1659b7f84
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# 2.5 Real-Time CDP-Verbindungen: Ereignisweiterleitung

In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemata und die Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft, um Daten zu erfassen, und leiten diese Daten dann Server-seitig an einen Endpunkt Ihrer Wahl weiter.

In diesem Modul sehen Sie Folgendes:

- Erstellen einer Adobe Experience Platform-Datenerfassungs-Server-Eigenschaft
- Installieren und Verwenden der Adobe Cloud Connector-Erweiterung in der Adobe Experience Platform-Datenerfassung
- Erstellen eines Google Function-Endpunkts und Streamen von Daten an ihn
- Erstellen eines AWS-Endpunkts und Streamen von Daten an ihn

## Lernziele

- Machen Sie sich mit den Eigenschaften des Adobe Experience Platform-Datenerfassungsservers und der neuen Adobe Cloud Connector-Erweiterung vertraut
- Erfahren Sie, wie Sie Adobe Experience Platform Web SDK-Daten in Lösungen von Drittanbietern wie Google und AWS wiederverwenden
- Machen Sie sich mit der Architektur hinter der Datenerfassung und Server-seitigen Weiterleitung in Adobe Experience Platform vertraut.

## Voraussetzungen

- Zugriff auf die Datenerfassung in Adobe Experience Platform und Adobe Experience Platform
- Grundlagen zu Adobe Experience Platform-Datensätzen und XDM

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie in [Installieren der Chrome-Erweiterung für die Experience League-Dokumentation](../../../getting-started/gettingstarted/ex1.md) beschrieben

## Übungen

[2.5.1 Erstellen einer Datenerfassungs-Ereignisweiterleitungseigenschaft](./ex1.md)

In dieser Übung erstellen Sie Ihre Ereignisweiterleitungseigenschaft für die Adobe Experience Platform-Datenerfassung.

[2.5.2 Aktualisieren Sie Ihren Datenstrom, um Daten für Ihre Datenerfassungs-Ereignisweiterleitungseigenschaft verfügbar zu machen.](./ex2.md)

In dieser Übung aktualisieren Sie Ihren vorhandenen Datenstrom, um Daten, die von Ihrer Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft erfasst werden, für Ihre Adobe Experience Platform-Datenerfassungsserver-Eigenschaft verfügbar zu machen.

[2.5.3 Erstellen und Konfigurieren eines benutzerdefinierten Webhooks](./ex3.md)

In dieser Übung erstellen und konfigurieren Sie einen benutzerdefinierten Webhook und leiten die von Web SDK erfassten Daten an diesen benutzerdefinierten Webhook weiter.

[2.5.4 Weiterleiten von Ereignissen an GCP Pub/Sub](./ex4.md)

In dieser Übung erstellen und konfigurieren Sie eine Google-Cloud-Funktion und leiten von Web SDK erfasste Daten an Google weiter.

[2.5.5 Weiterleiten von Veranstaltungen an AWS Kinesis und AWS S3](./ex5.md)

In dieser Übung konfigurieren Sie Ihre AWS-Umgebung mit AWS IAM, AWS Kinesis, AWS Firehose und AWS S3. Danach beginnen Sie mit der Weiterleitung von Ereignisdaten, die von Web SDK erfasst werden.

![Tech Insiders](./../../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um alles über Adobe Experience Platform und seine Programme zu erfahren. Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.

[Zurück zu „Alle Module“](./../../../../overview.md)
