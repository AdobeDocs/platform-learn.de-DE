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
source-git-commit: 63987fb652a653283a05a5f35f7ce670127ae905
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# Erste Schritte mit Adobe Experience Platform für Datenarchitekten und Dateningenieure

<!--5min-->

_Erste Schritte mit Adobe Experience Platform für Datenarchitekten und Dateningenieure_ ist der perfekte Ausgangspunkt, um sich mit Experience Platform vertraut zu machen.


<!--How do we address ETL-->

## Lernziele

Datenarchitekten und Dateningenieure müssen eng zusammenarbeiten, um eine erfolgreiche Experience Platform-Bereitstellung zu ermöglichen. In diesem praxisorientierten Tutorial lernen Sie die wichtigsten Aufgaben kennen, die von _beiden Rollen_ ausgeführt werden, damit Sie wissen, wie Sie Platform für Ihr eigenes Unternehmen implementieren können. Sie werden durch Übungen geführt, in denen Sie die wichtigsten Begriffe, Funktionen, Benutzeroberflächen und APIs von Experience Platform kennenlernen. Kunden von Adobe Experience Cloud-Programmen wie Real-time Customer Data Platform, Customer Journey Analytics und Journey Optimizer werden diese Inhalte ebenfalls nützlich finden, da Platform-Services eine wichtige Grundlage dieser Programme darstellen.

![Adobe Experience Cloud-Marketing-Architektur mit Hervorhebung der in diesem Tutorial behandelten Platform-Services: Identität, Profil, Segmentierung, Aufnahme, Abfrage und Governance](assets/marketecture.png)

Zu den Themen gehören:

* Konfigurieren von Benutzerberechtigungen
* Erstellen von Sandboxes
* Einrichten eines Developer Console-Projekts und Verwenden der Platform-API
* Daten-Management - einschließlich der Erstellung von Schemata, Datensätzen, Identitäten, Zusammenführungsrichtlinien und Data Governance
* Datenaufnahme im Batch- und Streaming-Modus
* Erfassen von Web-Daten mit Adobe Experience Platform Web SDK
* Erstellen von Echtzeit-Kundenprofilen
* Verwendung des Abfrage-Service zur Datenvalidierung und -extraktion
* Erstellen von Segmenten

## Geschäftsszenario

Adobe Experience Platform ist eine technische Plattform, mit der Sie Marketing-Ziele erreichen können. Die geschäftlichen Anwendungsfälle sollten bestimmen, wie Sie die Technologie entwerfen und implementieren. Dieses Tutorial konzentriert sich auf eine fiktive Einzelhandelsmarke namens Luma. Luma betreibt stationäre Geschäfte in mehreren Ländern und unterhält zudem eine Online-Präsenz mit einer Website und mobilen Apps. Sie investieren in Adobe Experience Platform, um Treue-, CRM-, Web- und Offline-Kaufdaten in Echtzeit-Kundenprofilen zu kombinieren und diese Profile zu aktivieren, damit sie ihr Marketing auf die nächste Stufe bringen können. Die Geschäftsziele von Luma können mit den Zielen Ihres Unternehmens übereinstimmen oder nicht, aber Sie sollten in der Lage sein, die praktischen Schritte in diesem Tutorial mit Ihren eigenen Geschäftszielen zu verknüpfen.

## Voraussetzungen

* Sie haben die [Einführung in die Adobe Experience Platform-Playlist](https://experienceleague.adobe.com/de/playlists/experience-platform-introduction) auf Experience League gesehen und sind mit den Funktionen von Platform vertraut
* Sie haben Zugriff auf ein Konto, das mit Adobe Experience Platform (oder einem plattformbasierten Programm wie Real-Time CDP oder Journey Optimizer) und der Datenerfassung (früher Launch) bereitgestellt wurde.
* Sie sind Systemadministrator dieses Kontos oder können über eine ([&#x200B; Benutzerberechtigungen) &#x200B;](configure-permissions.md).

## Verwenden dieses Tutorials

In diesem Tutorial werden Aufgaben für Dateningenieure und Datenarchitekten kombiniert. Da es sich um ein Tutorial auf Einführungsebene handelt, sollten Sie die Aufgaben für beide Rollen abschließen können. Da viele der Lektionen auf dem aufbauen, was in früheren Lektionen implementiert wurde, sollten Sie die Lektionen in der richtigen Reihenfolge durchgehen. Ich werde darauf hinweisen, welche Lektionen übersprungen werden können.

Wenn Sie während dieses Tutorials verschiedene Platform-Elemente erstellen, versuchen Sie, die von mir empfohlenen Namen so gut wie möglich einzuhalten. Es gibt jedoch einige allgemeine Elementnamen, die Sie anpassen können, falls mehrere Personen in Ihrem Unternehmen an diesem Tutorial gleichzeitig teilnehmen. Beispielsweise können Sie der Platform-Sandbox den Namen „Luma-Tutorial-Plattform - Ignatius J. Reilly“ anstelle von „Luma-Tutorial-Plattform“ geben.

Wenn Sie hängen bleiben, lesen Sie zuerst die Anweisungen erneut und verwenden Sie dann den Link ![Problem protokollieren](https://experienceleague.adobe.com/assets/img/feedback.svg?lang=de) in der Seitenleiste jeder Seite, um mich zu kontaktieren.

## Technische Hinweise

### Sandbox-Umgebungen

Im Tutorial erstellen Sie eine Sandbox-Umgebung und verwenden sie, um die Übungen abzuschließen. Die Sandbox-Umgebung macht es sicher für Sie, die Übungen und Experimente abzuschließen, ohne sich Gedanken über die Beeinträchtigung Ihrer Produktionsdaten zu machen.

### API

Platform wird API-First erstellt. Während für alle gängigen Platform-Workflows Schnittstellen-Workflows vorhanden sind und hauptsächlich verwendet werden, enthält das Tutorial einige API-orientierte Übungen. Ich führe Sie durch die grundlegende Projekteinrichtung in der Adobe Developer Console und stelle Ihnen [!DNL Postman] Umgebungen und Sammlungen zur Verfügung, um mit der Platform-API zu beginnen. Nach Abschluss des Tutorials ist es möglicherweise nützlich, mit der Platform-API vertraut zu sein und sie in Ihrer eigenen Bereitstellung zu verwenden.

### Technologien von Drittanbietern

Obwohl Sie in diesem Tutorial mehrere Technologien verwenden werden, bleiben Sie fast vollständig im Adobe-Ökosystem. In Ihrer eigenen Platform-Implementierung integrieren Sie Platform wahrscheinlich mit bestimmten Technologien von Drittanbietern. Damit dieses Tutorial für alle Kunden relevant bleibt, verwenden wir eine allgemeinere Implementierung.

## Tutorial-Updates

* Juni 2023: Aktualisiert, um einen neuen Berechtigungs-Workflow und die Verwendung von OAuth-Server-zu-Server-API-Anmeldeinformationen einzuschließen


Fahren wir nun mit der ersten Lektion fort: [Konfigurieren von Berechtigungen](configure-permissions.md).
