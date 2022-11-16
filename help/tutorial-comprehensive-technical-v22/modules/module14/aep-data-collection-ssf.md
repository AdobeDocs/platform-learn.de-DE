---
title: Adobe Experience Platform-Datenerfassung und serverseitige Weiterleitung in Echtzeit
description: In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemas und die Adobe Experience Platform-Datenerfassungsservereigenschaft, um Daten zu erfassen und diese Daten dann Server-seitig an einen gewünschten Endpunkt weiterzuleiten.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: c157ca52-c84f-4398-a658-2b6067e41707
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 1%

---

# 14. Real-Time CDP-Verbindungen: Ereignisweiterleitung

**Autor: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/), [Clement Delalande](https://www.linkedin.com/in/clement-delalande/)**

In diesem Modul verwenden Sie die zuvor konfigurierten Datensätze, Schemas und die Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft, um Daten zu erfassen und diese Daten dann Server-seitig an einen gewünschten Endpunkt weiterzuleiten.

In diesem Modul werden Sie:

- Erstellen einer Adobe Experience Platform-Datenerfassungsservereigenschaft
- Installieren und Verwenden der Adobe Cloud Connector-Erweiterung in der Adobe Experience Platform-Datenerfassung
- Google-Funktionsendpunkt erstellen und Daten streamen
- AWS-Endpunkt erstellen und Daten streamen

Sehen Sie sich dieses Video an, um den Wert, die Journey und den Konfigurationsprozess für Kunden zu verstehen:

>[!VIDEO](https://video.tv.adobe.com/v/331987?quality=12&learn=on)

## Lernziele

- Machen Sie sich mit den Eigenschaften des Adobe Experience Platform-Datenerfassungsservers und der neuen Adobe Cloud Connector-Erweiterung vertraut.
- Erfahren Sie, wie Sie Adobe Experience Platform Web SDK-Daten in Drittanbieterlösungen wie Google und AWS wiederverwenden können.
- Machen Sie sich mit der Architektur der Datenerfassung und serverseitigen Weiterleitung von Adobe Experience Platform vertraut.

## Voraussetzungen

- Zugriff auf die Datenerfassung von Adobe Experience Platform und Adobe Experience Platform
- Grundlagen zu Adobe Experience Platform-Datensätzen und XDM

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem21.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--aepSandboxId--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[14.1 Eigenschaft &quot;Datenerfassungs-Ereignisweiterleitung&quot;erstellen](./ex1.md)

In dieser Übung erstellen Sie Ihre Adobe Experience Platform-Eigenschaft für die Ereignisweiterleitung zur Datenerfassung.

[14.2 Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Datenerfassungs-Ereignisweiterleitungseigenschaft verfügbar zu machen.](./ex2.md)

In dieser Übung aktualisieren Sie Ihr vorhandenes Datastream, um die von Ihrer Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft erfassten Daten für Ihre Adobe Experience Platform-Datenerfassungsservereigenschaft verfügbar zu machen.

[14.3 Benutzerdefinierten Webhook erstellen und konfigurieren](./ex3.md)

In dieser Übung erstellen und konfigurieren Sie einen benutzerdefinierten Webhook, und Sie beginnen mit der Weiterleitung von Daten, die vom Web SDK erfasst werden, an diesen benutzerdefinierten Webhook.

[14.4 Erstellen und Konfigurieren einer Google Cloud-Funktion](./ex4.md)

In dieser Übung erstellen und konfigurieren Sie eine Google Cloud-Funktion und beginnen mit der Weiterleitung von Daten, die vom Web SDK erfasst werden, an Google.

[14.5 Weiterleiten von Ereignissen an das AWS-Ökosystem](./ex5.md)

In dieser Übung konfigurieren Sie Ihre AWS-Umgebung mithilfe von AWS API Gateway, AWS Kinesis, AWS Firewalls und AWS S3. Danach beginnen Sie mit der Weiterleitung von Ereignisdaten, die vom Web SDK erfasst werden.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
