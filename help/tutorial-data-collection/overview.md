---
title: Übersicht
description: Übersicht
exl-id: 527d8f73-33d0-45a6-b7a4-5e46cdb7c138
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Verwenden der Adobe Experience Platform-Datenerfassung

Die Erfassung von Daten über Ereignisse im Browser eines Benutzers ist ein grundlegender Grundsatz einer Marketing-Strategie. Adobe hat mehrere Tools zur Verfügung gestellt, mit denen Sie diese Daten verwalten können. Während Sie sich mit jedem dieser Tools individuell vertraut machen können, versucht dieses Tutorial, einen umfassenderen Überblick darüber zu verschaffen, was jedes dieser Tools tut und wie es zusammenarbeitet, um ein gemeinsames Ziel zu erreichen.

In diesem Tutorial besprechen wir eine Strategie für:

1. Strukturierung und Persistenz Ihrer Daten in Adobe Experience Platform,
1. Daten im Browser verwalten und darüber informieren, dass bestimmte Ereignisse aufgetreten sind, und
1. Reaktion auf solche Ereignisse durch Senden relevanter Daten an Adobe Experience Platform.

Während dieses Tutorials die Adobe Client Data Layer, das Adobe Experience Platform Web SDK und die [!DNL Tags] -Funktion für eine präzisere, nahtlose Implementierung können Sie diese Tools auch mit Drittanbieter- oder internen Tools kombinieren, um höchste Flexibilität zu erzielen.

## Beispiel-Szenario

In diesem Tutorial implementieren Sie die Datenerfassung für eine einfache Produktseite auf einer E-Commerce-Site:

1. Die Produktseite wird im Browser geladen. Hier verfolgen Sie, ob der Benutzer das Produkt angesehen hat.
1. Der Benutzer entscheidet sich, das Produkt zu erwerben. Er klickt daher auf eine Schaltfläche, um das Produkt seinem Warenkorb hinzuzufügen. Hier verfolgen Sie, ob der Benutzer einen neuen Warenkorb geöffnet und das Produkt zum Warenkorb hinzugefügt hat, indem Sie Erlebnisereignisse an Adobe Experience Platform senden.
1. Schließlich klickt der Benutzer auf einen _App herunterladen_ verknüpfen, da sie an Ihrer App interessiert sind. Sie verfolgen, dass der Benutzer auf den Link geklickt hat.

Los geht‘s!

[Weiter: ](structuring-your-data.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
