---
title: Erste Schritte mit Adobe Experience Platform für Datenarchitekten und Dateningenieure
description: Erste Schritte mit Adobe Experience Platform für Datenarchitekten und Dateningenieure.
breadcrumb-title: Übersicht
role: Data Architect, Data Engineer
jira: KT-4348
thumbnail: 4348-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2023-06-21T00:00:00Z
exl-id: fabbc591-840b-40dc-89af-305626a16338
source-git-commit: efef0389cedfec7dfa19d876df96c58b7463ee12
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# Erste Schritte mit Adobe Experience Platform für Datenarchitekten und Dateningenieure

<!--5min-->

_Erste Schritte mit Adobe Experience Platform für Datenarchitekten und Dateningenieure_ ist der perfekte Ausgangspunkt, um sich mit dem Experience Platform vertraut zu machen.


<!--How do we address ETL-->

## Lernziele

Für eine erfolgreiche Experience Platform-Implementierung müssen Datenarchitekten und Dateningenieure eng zusammenarbeiten. In diesem Tutorial lernen Sie die wichtigsten von _Beide Rollen_ damit Sie wissen, wie Sie mit der Implementierung von Platform für Ihr eigenes Unternehmen beginnen können. Sie werden durch Übungen geführt, die Ihnen die wichtigsten Begriffe, Funktionen, Oberflächen und APIs von Experience Platform vorstellen. Kunden von Adobe Experience Cloud-Anwendungen wie Real-time Customer Data Platform, Customer Journey Analytics und Journey Optimizer werden diesen Inhalt ebenfalls für nützlich halten, da Plattformdienste eine wichtige Grundlage für diese Anwendungen darstellen.

![Adobe Experience Cloud-Marketing-Architektur, die die in diesem Tutorial behandelten Platform-Dienste hervorhebt: Identität, Profil, Segmentierung, Aufnahme, Abfrage und Governance](assets/marketecture.png)

Zu den Themen gehören:

* Konfigurieren von Benutzerberechtigungen
* Erstellen von Sandboxes
* Einrichten eines Projekts in der Developer Console und Verwenden der Platform API
* Datenmanagement, einschließlich Erstellen von Schemas, Datensätzen, Identitäten, Zusammenführungsrichtlinien und Data Governance
* Datenerfassung mit Batch- und Streaming-Modus
* Erfassen von Webdaten mit dem Adobe Experience Platform Web SDK
* Echtzeit-Kundenprofile erstellen
* Verwenden von Query Service zum Überprüfen von Daten und Extrahieren von Daten
* Segmente erstellen

## Geschäftsszenario

Adobe Experience Platform ist eine technische Plattform, mit der Sie Marketingziele erreichen können. Die geschäftlichen Anwendungsfälle sollten die Entwicklung und Implementierung der Technologie vorantreiben. Dieses Tutorial konzentriert sich auf eine fiktive Einzelhandelsmarke namens Luma. Luma betreibt Ziegelsteine und Mörser in mehreren Ländern und verfügt über eine Online-Präsenz mit einer Website und mobilen Apps. Sie investieren in Adobe Experience Platform, um Loyalitäts-, CRM-, Web- und Offline-Kaufdaten in Echtzeit-Kundenprofile zu kombinieren und diese Profile zu aktivieren, um ihr Marketing auf die nächste Stufe zu bringen. Die Geschäftsziele von Luma stimmen möglicherweise nicht mit den Zielen Ihres Unternehmens überein, aber Sie sollten die praktischen Schritte in diesem Tutorial mit Ihren eigenen Geschäftszielen verknüpfen können.

## Voraussetzungen

* Sie haben die [Einführung in den Adobe Experience Platform-Kurs](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-U-1-2020.1&amp;lang=de) auf dem Experience League und mit Platform-Funktionen vertraut sind
* Sie haben Zugriff auf ein mit Adobe Experience Platform bereitgestelltes Konto (oder eine plattformbasierte Anwendung wie Real-Time CDP oder Journey Optimizer) und auf die Datenerfassung (früher Launch).
* Sie sind Systemadministrator dieses Kontos oder können über einen [Benutzerberechtigungen konfigurieren](configure-permissions.md) für Sie.

## Verwenden dieses Tutorials

In diesem Tutorial werden Aufgaben für Dateningenieure und Datenarchitekten kombiniert. Da es sich um ein Tutorial auf Einführungsebene handelt, sollten Sie die Aufgaben für beide Rollen ausführen können. Da viele der Lektionen auf dem aufbauen, was in früheren Lektionen implementiert wurde, sollten Sie die Lektionen in der richtigen Reihenfolge durchlaufen. Ich werde herausfinden, welche Lektionen übersprungen werden können.

Wenn Sie während dieses Tutorials verschiedene Platform-Elemente erstellen, sollten Sie möglichst an die von mir empfohlenen Namen festhalten. Es gibt jedoch einige allgemeine Elementnamen, die Sie anpassen können, falls in Ihrem Unternehmen mehrere Personen dieses Tutorial gleichzeitig absolvieren. Sie können beispielsweise die Platform-Sandbox &quot;Luma Tutorial Platform - Ignatius J Reilly&quot;anstelle von &quot;Luma Tutorial Platform&quot;nennen.

Wenn Sie feststecken, versuchen Sie zunächst, die Anweisungen erneut zu lesen, und verwenden dann die ![Problem protokollieren](https://experienceleague.adobe.com/assets/img/feedback.svg) auf der Seitenleiste jeder Seite, um mich zu kontaktieren.

## Technische Hinweise

### Sandbox-Umgebungen

Im Tutorial erstellen Sie eine Sandbox-Umgebung und verwenden sie zum Abschließen der Übungen. Die Sandbox-Umgebung ermöglicht es Ihnen, die Übungen und Experimente durchzuführen, ohne sich Gedanken über die Beeinträchtigung Ihrer Produktionsdaten machen zu müssen.

### API

Platform ist als API-Erste konzipiert. Während es für alle wichtigen Platform-Workflows Workflows Schnittstellen-Workflows gibt und primär verwendet wird, enthält das Tutorial einige API-orientierte Übungen. Ich werde Sie durch die grundlegende Projekteinrichtung in der Adobe Developer Console führen und Ihnen Folgendes bereitstellen: [!DNL Postman] Umgebungen und Sammlungen , um mit der Platform-API zu beginnen. Nach Abschluss des Tutorials können Sie sich mit der Platform-API vertraut machen und sie in Ihrer eigenen Implementierung verwenden.

### Drittanbietertechnologien

Obwohl Sie in diesem Tutorial mehrere Technologien verwenden werden, bleiben Sie fast vollständig im Adobe-Ökosystem. In Ihrer eigenen Platform-Implementierung integrieren Sie Platform wahrscheinlich mit bestimmten Drittanbietertechnologien. Um dieses Tutorial für alle Kunden relevant zu halten, verwenden wir eine allgemeinere Implementierung.

## Tutorial-Aktualisierungen

* Juni 2023: Es wurde aktualisiert, um neuen Berechtigungs-Workflow und die Verwendung von OAuth-Server-zu-Server-API-Anmeldedaten einzuschließen.


Gehen wir nun zur ersten Lektion über —[Berechtigungen konfigurieren](configure-permissions.md).
