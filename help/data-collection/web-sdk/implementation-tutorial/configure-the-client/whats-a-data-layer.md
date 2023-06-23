---
title: Was ist eine Datenschicht?
description: Was ist eine Datenschicht?
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
jira: KT-10447
hide: true
hidefromtoc: true
exl-id: 747f2e60-646e-4324-993c-88568415ea59
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Was ist eine Datenschicht?

Bei der Implementierung von Marketingtechnologien auf Ihrer Site sind wahrscheinlich wichtige Daten über die gesamte Benutzeroberfläche verteilt. Beispielsweise könnte sich der Name eines Produkts in einer Überschrift auf der Seite befinden und der Preis auf der Seite unter dem Produktbild möglicherweise niedriger sein. Wenn Sie diese Daten an Adobe oder einen anderen Anbieter senden möchten, können Sie die Datenelemente mit HTML finden, indem Sie nach bestimmten HTML-Tags oder -Attributen suchen, die Daten aus diesen Elementen abrufen und abschicken. Was passiert jedoch, wenn Ihr Technikerteam beschließt, den Produktnamen aus der Kopfzeile in eine Seitenleiste zu verschieben? Ihre Implementierung bricht ab. Ihre Implementierung kann die Überschrift nicht mehr finden oder, schlimmer noch, sie findet die Überschrift und sendet irrelevante Daten an den Server.

Ein Hauptziel einer Datenschicht besteht darin, dieses Problem zu lösen. Am einfachsten ist eine Datenschicht ein JavaScript-Objekt (oder, wie wir später sehen werden, ein Array), das Daten zum Produkt auf der Seite oder andere relevante Daten enthält, auf die Ihre Marketing-Technologien zur Erreichung Ihrer Ziele angewiesen sind. Wenn wir uns bei der Bereitstellung dieser Daten nicht auf die Elemente der Benutzeroberfläche verlassen, wird unsere Implementierung robuster. Die Datenschicht enthält die Daten und sollte als Vertrag betrachtet werden. Dieser Vertrag besteht normalerweise zwischen dem Technikerteam, das Daten in die Datenschicht eingibt, und dem Marketing-Team, das Daten aus der Datenschicht abruft.

Wenn ein Ingenieur kurz davor ist, die Struktur der Datenschicht zu ändern, ist es viel wahrscheinlicher, dass er mit dem Marketing-Team zusammenarbeitet, damit geeignete Änderungen an der Marketing-Implementierung vorgenommen werden können. Diese Mitteilung und Zusammenarbeit _must_ in Ihrem Unternehmen eingerichtet werden, um eine robuste Implementierung sicherzustellen.

## Container vs. Inhalt

In der Branche wird der Begriff &quot;Datenschicht&quot;etwas locker umgeschlagen und kann oft zu Verwirrung und Misskommunikation führen. Man denke an eine Schachtel Marmor. Es gibt zwei Teile: den Container (die Box) und den Inhalt (die Marmor). Eine Datenschicht besteht häufig aus zwei Teilen: den Container (das JavaScript-Objekt oder -Array) und den Inhalt (die Datenteile wie `priceTotal`, `currencyCode`und `purchaseOrderNumber` ).

Da sich dieses Tutorial auf die Adobe Client-Datenschicht bezieht, bezieht es sich auf den Container und nicht auf den Inhalt. Wenn er auf XDM verweist, bezieht er sich auf den Inhalt und nicht auf den Container. Bei der Adobe Client-Datenschicht spielt es keine Rolle, ob es sich um XDM oder Ihr eigenes Datenmodell handelt. Die Adobe Client-Datenschicht spielt keine Rolle. Das ist nur eine Kiste. Aber es _is_ eine Kiste mit Spezialantrieb...

## Änderungen kommunizieren

Bei Verwendung einer Datenschicht können Sie den Inhalt jederzeit ändern. Das ist eine nette Funktion, da Daten zu verschiedenen Zeiten verfügbar sein können. Beispielsweise können Sie sofort Daten zum Benutzer zur Verfügung haben, müssen aber möglicherweise eine asynchrone Anfrage an einen Drittanbieter richten, um weitere Informationen zu erhalten. Dies erfordert besondere Beachtung. Wenn Sie diese asynchronen Daten irgendwann an Adobe Experience Platform senden müssen, wie wissen Ihre Marketingtechnologien, wann bestimmte Daten zur Datenschicht hinzugefügt wurden und bereit zum Senden sind? Sie benötigen eine intelligentere Datenschicht - eine ereignisgesteuerte Datenschicht.

Eine ereignisbasierte Datenschicht kann kommunizieren, dass ihr Inhalt geändert wurde, sodass Marketing-Technologien auf die Änderung reagieren können. Bei ordnungsgemäßer Verwendung kann dies dazu beitragen, Timing-Probleme zu vermeiden, die häufig bei Datenschichten auftreten, die bei Änderungen nicht kommunizieren können.

Die Adobe Client-Datenschicht ist eine ereignisgesteuerte Datenschicht.
