---
title: Was ist eine Datenschicht?
description: Was ist eine Datenschicht?
exl-id: a53572c1-1295-4ed4-8a3d-aafff3235138
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# Was ist eine Datenschicht?

Bei der Implementierung von Marketingtechnologien auf Ihrer Site sind wahrscheinlich wichtige Daten über die gesamte Benutzeroberfläche verteilt. Beispielsweise könnte sich der Name eines Produkts in einer Überschrift auf der Seite befinden und der Preis auf der Seite unter dem Produktbild möglicherweise niedriger sein. Wenn Sie diese Daten an Adobe oder einen anderen Anbieter senden möchten, suchen Sie die HTML-Elemente, die die benötigten Daten enthalten, ziehen Sie die Daten aus diesen Elementen und senden Sie sie ab. Was passiert jedoch, wenn Ihr Technikerteam beschließt, den Produktnamen aus der Kopfzeile in eine Seitenleiste zu verschieben? Ihre Implementierung bricht ab. Ihre Implementierung kann die Überschrift nicht mehr finden oder, schlimmer noch, sie findet die Überschrift und sendet irrelevante Daten an den Server.

Ein Hauptziel einer Datenschicht besteht darin, dieses Problem zu lösen. Am einfachsten ist eine Datenschicht ein JavaScript-Objekt oder ein Array, das Daten über das Produkt auf der Seite enthält. Es enthält alle relevanten Daten, die Ihre Marketing-Technologien zur Erreichung Ihrer Ziele benötigen. Wenn wir uns bei der Bereitstellung dieser Daten nicht auf die Elemente der Benutzeroberfläche verlassen, wird unsere Implementierung robuster. Die Datenschicht enthält die Daten und sollte als Vertrag betrachtet werden. Dieser Vertrag besteht normalerweise zwischen dem Technikerteam, das Daten in die Datenschicht eingibt, und dem Marketing-Team, das Daten aus der Datenschicht abruft.

Wenn ein Ingenieur kurz davor ist, die Struktur der Datenschicht zu ändern, ist es viel wahrscheinlicher, dass er mit dem Marketing-Team zusammenarbeitet, damit geeignete Änderungen an der Marketing-Implementierung vorgenommen werden können. Diese Mitteilung und Zusammenarbeit _must_ in Ihrem Unternehmen eingerichtet werden, um eine robuste Implementierung sicherzustellen.

## Container vs. Inhalt

In der Branche wird der Begriff &quot;Datenschicht&quot;etwas locker umgeschlagen und kann oft zu Verwirrung und Misskommunikation führen. Man denke an eine Schachtel Marmor. Es gibt zwei Teile: den Container (die Box) und den Inhalt (die Marmor). Eine Datenschicht besteht häufig aus zwei Teilen: den Container (das JavaScript-Objekt oder -Array) und den Inhalt (die Datenteile wie `priceTotal`, `currencyCode`und `purchaseOrderNumber` ).

Da sich dieses Tutorial auf die Adobe Client-Datenschicht bezieht, bezieht es sich auf den Container und nicht auf den Inhalt. Wenn er auf XDM verweist, bezieht er sich auf den Inhalt und nicht auf den Container. Bei Verwendung der Adobe Client-Datenschicht spielt es keine Rolle, ob es sich um XDM oder Ihr eigenes Datenmodell handelt. Die Adobe Client-Datenschicht spielt keine Rolle. Das ist nur eine Kiste. Aber es _is_ eine Kiste mit Spezialantrieb...

## Änderungen kommunizieren

Bei Verwendung einer Datenschicht können Sie den Inhalt jederzeit ändern. Das ist eine nette Funktion, da Daten zu verschiedenen Zeiten verfügbar sein können. Beispielsweise können Sie sofort Daten zum Benutzer zur Verfügung haben, müssen aber möglicherweise eine asynchrone Anfrage an einen Drittanbieter richten, um weitere Informationen zu erhalten. Dies erfordert besondere Beachtung. Wenn Sie diese asynchronen Daten irgendwann an Adobe Experience Platform senden müssen, wie wissen Ihre Marketingtechnologien, wann bestimmte Daten zur Datenschicht hinzugefügt wurden und bereit zum Senden sind? Sie brauchen eine intelligentere Datenschicht - eine ereignisgesteuerte Datenschicht.

Eine ereignisbasierte Datenschicht kann kommunizieren, dass ihr Inhalt geändert wurde, sodass Marketing-Technologien auf die Änderung reagieren können. Bei ordnungsgemäßer Verwendung kann dies dazu beitragen, Timing-Probleme zu vermeiden, die häufig bei Datenschichten auftreten, die bei Änderungen nicht kommunizieren können.

Die Adobe Client-Datenschicht ist eine ereignisgesteuerte Datenschicht.

[Weiter: ](how-to-use-the-adobe-client-data-layer.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
