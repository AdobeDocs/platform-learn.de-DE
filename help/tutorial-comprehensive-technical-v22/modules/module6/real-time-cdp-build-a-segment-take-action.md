---
title: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln
description: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 147d9153-5742-4857-aae1-0ec434a1e626
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 2%

---

# 6. Echtzeit-Kundendatenplattform - Erstellen Sie ein Segment und ergreifen Sie Maßnahmen.

**Autor: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/), [Alberto De Caro](https://www.linkedin.com/in/albertodecaro/), [Benedikt Wedenik](https://www.linkedin.com/in/benedikt-wedenik/)**

In diesem Modul konfigurieren Sie ein Streaming-Segment und aktivieren das Segment für mehrere Ziele.

## Lernziele

- Erfahren Sie, wie Sie ein Segment erstellen und für Streaming aktivieren.
- Erfahren Sie, wie Sie ein Werbeziel mithilfe der Adobe Experience Platform-Benutzeroberfläche konfigurieren.
- Erfahren Sie, wie Sie ein Segment mit einem Ziel verbinden und aktivieren.
- Erfahren Sie, wie Sie Adobe Experience Platform-Segmente in Adobe Audience Manager verwenden und wie Sie Adobe Audience Manager-Segmente in Adobe Experience Platform verwenden, dank bidirektionaler Segmentfreigabe.

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf Adobe Target
- Zugriff auf AWS S3

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem11.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--module11sandbox--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[6.1 Segment erstellen](./ex1.md)

Erfahren Sie, wie Sie ein Segment erstellen.

[6.2 Überprüfen der Konfiguration des DV360-Ziels mithilfe von Zielen](./ex2.md)

Erfahren Sie, wie Sie ein Werbeziel mithilfe der Real-Time CDP-Benutzeroberfläche konfigurieren.

[6.3 Maßnahmen ergreifen: Senden Ihres Segments an DV360](./ex3.md)

Verbinden Sie das in Übung 6.1 erstellte Segment mit dem Ziel DV360.

[6.4 Maßnahmen ergreifen: Senden Ihres Segments an ein S3-Ziel](./ex4.md)

Verwenden Sie das in Übung 6.1 erstellte Segment und senden Sie es an ein S3-Ziel, das normalerweise für E-Mail-Marketing-Ziele verwendet wird.

[6.5 Maßnahmen ergreifen: Senden Ihres Segments an Adobe Target](./ex5.md)

Verwenden Sie das in Übung 6.1 erstellte Segment, um eine Erlebnis-Targeting-Aktivität in Adobe Target zu konfigurieren.

[6.6 Externe Zielgruppen](./ex6.md)

Importieren Sie Zielgruppen aus einem externen Quellsystem in Adobe Experience Platform.

[6.7 Destinations SDK](./ex7.md)

Konfigurieren Sie Ihr eigenes Ziel mit dem Ziel-SDK.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
