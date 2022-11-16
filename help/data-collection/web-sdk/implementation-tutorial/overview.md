---
title: Übersicht
description: Übersicht
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 8ffa258b-6ff7-4413-aead-21b106668c65
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 1%

---

# Übersicht

Die Erfassung von Daten über Ereignisse im Browser eines Benutzers ist ein grundlegender Grundsatz einer Marketing-Strategie. Adobe hat mehrere Tools zur Verfügung gestellt, mit denen Sie diese Daten verwalten können. Während Sie sich mit jedem dieser Tools individuell vertraut machen können, versucht dieses Tutorial, einen umfassenderen Überblick darüber zu verschaffen, was jedes dieser Tools tut und wie es zusammenarbeitet, um ein gemeinsames Ziel zu erreichen.

In diesem Tutorial besprechen wir eine Strategie zur (1) Strukturierung und Speicherung Ihrer Daten in Adobe Experience Platform, (2) Verwaltung Ihrer Daten im Browser und Kommunikation darüber, dass bestimmte Ereignisse aufgetreten sind und (3) Reaktion auf solche Ereignisse durch Senden relevanter Daten an Adobe Experience Platform.

Während dieses Tutorial die Adobe Client Data Layer, das Adobe Experience Platform Web SDK und die Tags-Funktion für eine verschreibungspflichtigere, nahtlosere Implementierung verwendet, können Sie diese Tools mit Tools von Drittanbietern oder internen Tools kombinieren und abgleichen, um höchste Flexibilität zu erzielen.

## Beispiel-Szenario

Für dieses Tutorial gehen wir davon aus, dass Sie die Datenerfassung für eine einfache Produktseite auf einer E-Commerce-Site implementieren. Die Produktseite wird im Browser geladen. Hier verfolgen Sie, ob der Benutzer das Produkt angesehen hat. Der Benutzer entscheidet sich, das Produkt zu erwerben. Er klickt daher auf eine Schaltfläche, um das Produkt seinem Warenkorb hinzuzufügen. In diesem Beispiel verfolgen Sie, ob der Benutzer einen neuen Warenkorb geöffnet und das Produkt zum Warenkorb hinzugefügt hat, indem Sie Erlebnisereignisse an Adobe Experience Platform senden. Schließlich klickt der Benutzer auf einen _App herunterladen_ verknüpfen, da sie an Ihrer App interessiert sind. Sie werden verfolgen, ob der Benutzer auf den Link geklickt hat.
