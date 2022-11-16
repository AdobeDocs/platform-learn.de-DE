---
title: Foundation - Echtzeit-Kundenprofil
description: Foundation - Echtzeit-Kundenprofil
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 050e5d99-544d-4a86-a7f6-9f103381dca5
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 1%

---

# 3. Foundation - Echtzeit-Kundenprofil

**Autor: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In diesem Modul werden wir einen tiefen Einblick in die Echtzeit-Kundenprofil- und Identitätsfunktionen von Adobe Experience Platform erhalten. Sie erfahren, wie Zielgruppen definiert werden können, wie die Rolle von Identity Service und Experience Cloud-ID genutzt werden kann und wie Sie Segmentaufbauabfragen definieren, um eigene Segmente zu definieren.

## Lernziele

- Erfahren Sie, wie Sie das Echtzeit-Kundenprofil eines Kunden über die Benutzeroberfläche von Adobe Experience Platform visualisieren können.
- Erfahren Sie, wie Sie mit dem Segmentaufbau von Adobe Experience Platform ein Segment erstellen.
- Erfahren Sie, wie Sie mithilfe von Adobe Experience Platform-APIs ein Segment erstellen und die Segmentergebnisse in einem Datensatz speichern.
- Erfahren Sie mehr über die Auswirkungen des Zugriffs auf ein vollständiges Kundenprofil, einschließlich Echtzeit-Verhalten, in Offline-Umgebungen

## Voraussetzungen

- Zugriff auf [Adobe Experience Platform](https://experience.adobe.com/platform)
- Zugriff auf [https://public.aepdemo.net](https://public.aepdemo.net)
- **Herunterladen dieser Assets**:
   - [Postman-Sammlungen](./../../assets/postman/postman_profile.zip)

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem3.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--aepSandboxId--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[3.1 Website besuchen](./ex1.md)

In dieser Übung folgen Sie einem Skript und gehen durch die Website.

[3.2 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche](./ex2.md)

In dieser Übung melden Sie sich bei Adobe Experience Platform an und sehen sich Ihr eigenes Echtzeit-Kundenprofil in der Benutzeroberfläche an.

[3.3 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - API](./ex3.md)

In dieser Übung verwenden Sie Postman und Adobe I/O, um Ihr eigenes Echtzeit-Kundenprofil anzuzeigen, indem Sie die APIs von Adobe Experience Platform verwenden.

[3.4 Segment erstellen - Benutzeroberfläche](./ex4.md)

In dieser Übung erstellen Sie ein Segment, indem Sie den Segmentaufbau von Adobe Experience Platform verwenden.

[3.5 Segment erstellen - API](./ex5.md)

In dieser Übung verwenden Sie Postman und Adobe I/O, um ein Segment zu erstellen und die Ergebnisse dieses Segments als Datensatz zu speichern, indem Sie Adobe Experience Platform-APIs verwenden.

[3.6 Echtzeit-Kundenprofil in Aktion im Callcenter anzeigen](./ex6.md)

In dieser Übung stellen Sie sich als Mitarbeiter eines Callcenters vor, der einen Anruf von einem Kunden erhält. Um wirklich Einfluss auf das Kundenerlebnis zu nehmen, benötigen Sie Zugriff auf alle verfügbaren Informationen in Echtzeit.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
