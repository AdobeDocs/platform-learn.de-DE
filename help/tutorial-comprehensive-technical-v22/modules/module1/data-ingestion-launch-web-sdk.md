---
title: 1. Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 86da7132-cb06-4be3-b6b8-ea3ab937e6dc
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 1%

---

# 1. Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung

**Autor: [Matthew Joseph Woolley](https://www.linkedin.com/in/matthewjwoolley/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

Dieses grundlegende Modul stellt Ihnen eine Einführung in die Datenerfassungsansicht von Adobe vor und erläutert, wie Sie Daten von einer Website und Mobile App über die Adobe Experience Platform-Datenerfassung, die Adobe Experience Platform-SDKs und das Adobe Experience Platform Edge Network in Adobe Experience Platform und andere Anwendungen übertragen können. In diesem Modul werden einige Konzepte und Technologien vorgestellt, die sich über das technische Tutorial von Adobe Experience Platform hinaus auswirken. Es sollte klar sein, welche Teile dieser Übungen für den Rest des umfassenden Tutorials von grundlegender Bedeutung sind, das Ihnen mehr über Experience Edge und seine Funktionen beibringt und wo Sie weitere Informationen und Tutorials erhalten können.

## Lernziele

- Erfahren Sie, wie eine Marke die Adobe Experience Platform-Datenerfassung als Tag Management-System (TMS) verwendet.
- Erfahren Sie, welche Datenflüsse eine Marke verwendet, um Daten in ihre Adobe-Produkte aufzunehmen.
- Erfahren Sie, wie Sie Daten über das Adobe Experience Platform Edge Network an die Adobe Experience Platform und andere Produkte senden.
- Erfahren Sie, wie Sie Datenelemente und Regeln erstellen, die Daten aus Web und Mobile erfassen.
- Erfahren Sie mehr über die Web SDK-Tracking-Ereignisse und das Debugging ihrer Inhalte.
- Erfahren Sie, was eine Datenschicht ist und welche Adobe bei der Implementierung empfiehlt.
- Erfahren Sie, wie Sie das Web SDK von Grund auf implementieren können.
- Erfahren Sie mehr über den Unterschied zwischen einer Web- und einer mobilen Implementierung.

## Voraussetzungen

- Zugriff auf Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Zugriff auf die Adobe Experience Platform-Datenerfassung: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Zugriff auf die Demowebsite

>[!IMPORTANT]
>
>Dieses Tutorial wurde erstellt, um ein bestimmtes Workshop-Format zu vereinfachen. Es verwendet bestimmte Systeme und Konten, auf die Sie möglicherweise keinen Zugriff haben. Auch ohne Zugriff können Sie noch viel lernen, indem Sie diesen sehr detaillierten Inhalt durchlesen. Wenn Sie an einem der Workshops teilnehmen und Ihre Zugangsdaten benötigen, wenden Sie sich an Ihren Kundenbetreuer, der Ihnen die erforderlichen Informationen zur Verfügung stellt.

## Architekturüberblick

Sehen Sie sich die folgende Architektur an, in der die Komponenten hervorgehoben werden, die in diesem Modul besprochen und verwendet werden.

![Architekturüberblick](../../assets/images/architecturem1.png)

## Sandbox zur Verwendung

Verwenden Sie für dieses Modul diese Sandbox: `--aepSandboxId--`.

>[!NOTE]
>
>Vergessen Sie nicht, die Chrome-Erweiterung zu installieren, zu konfigurieren und zu verwenden, wie unter [0.1 - Installieren der Chrome-Erweiterung für die Dokumentation zur Experience League](../module0/ex1.md)

## Übungen

[1.1 Grundlagen zur Datenerfassung in Adobe Experience Platform](./ex1.md)

In dieser Übung sollten Sie die Benutzeroberfläche der Adobe Experience Platform-Datenerfassung erkunden und sich über ihre Funktionen informieren.

[1.2 Edge-Netzwerk, Datenspeicher und serverseitige Datenerfassung](./ex2.md)

In dieser Übung erfahren Sie, wie Sie Daten an Adobe-Produkte in der Adobe Experience Platform-Datenerfassungsoberfläche weiterleiten und die von der Demowebsite verwendeten Datenströme untersuchen können.

[1.3 Einführung in die Adobe Experience Platform-Datenerfassung](./ex3.md)

In dieser Übung erfahren Sie, wie Sie eine Erweiterung einrichten, Datenelemente und Regeln erstellen und im Web veröffentlichen.

[1.4 Clientseitige Web-Datenerfassung](./ex4.md)

Debuggen Sie in dieser Übung das installierte Web SDK, um zu verstehen, wie es funktioniert und welche Daten in zukünftigen Übungen verwendet werden.

[1.5 Implementieren von Adobe Analytics und Adobe Audience Manager](./ex5.md)

In dieser Übung sehen und verwenden Sie Webdaten, die mit dem Web SDK in Adobe Analytics und Adobe Audience Manager erfasst wurden.

[1.6 Adobe Target implementieren](./ex6.md)

Richten Sie in dieser Übung eine Aktivität in Adobe Target ein, die über das Web SDK implementiert wurde.

[1.7 XDM-Schema-Anforderungen in Adobe Experience Platform](./ex7.md)

Um sicherzustellen, dass Web SDK und legierte.js Daten in Adobe Experience Platform erfassen können, muss ein bestimmtes XDM-Mixin zum XDM-Schema in Adobe Experience Platform gehören.

[Zusammenfassung und Vorteile](./summary.md)

Zusammenfassung dieses Moduls und Übersicht über die Vorteile.

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um alles über Adobe Experience Platform zu erfahren. Wenn Sie Fragen haben, möchten allgemeine Rückmeldungen von Vorschlägen zu künftigen Inhalten teilen, wenden Sie sich bitte direkt an Wouter Van Geluwe, indem Sie eine E-Mail an **vangeluw@adobe.com**.

[Zu allen Modulen zurückkehren](../../overview.md)
