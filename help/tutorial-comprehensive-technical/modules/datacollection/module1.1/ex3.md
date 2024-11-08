---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Einführung in die Adobe Experience Platform-Datenerfassung
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Einführung in die Adobe Experience Platform-Datenerfassung
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '1334'
ht-degree: 9%

---

# 1.1.3 - Einführung in die Adobe Experience Platform-Datenerfassung

## Kontext

Sehen wir uns nun die Bausteine der Adobe Experience Platform-Datenerfassung genauer an, um zu verstehen, was auf Ihrer Demowebsite installiert ist. Sehen Sie sich die Adobe Experience Platform Web SDK-Erweiterung genauer an, konfigurieren Sie ein Datenelement und eine Regel und lernen Sie, wie Sie eine Bibliothek veröffentlichen.

## 1.1.3.1 - Adobe Experience Platform Web SDK-Erweiterung

Eine Erweiterung ist ein gepackter Code-Satz, der die Adobe Experience Platform-Datenerfassungsschnittstelle und die Bibliotheksfunktionalität erweitert. Die Adobe Experience Platform-Datenerfassung ist die Plattform. Erweiterungen sind wie Apps, die auf der Plattform ausgeführt werden. Alle im Tutorial verwendeten Erweiterungen werden von Adobe erstellt und verwaltet. Drittanbieter können jedoch eigene Erweiterungen erstellen, um die Anzahl der benutzerdefinierten Codes zu begrenzen, die Adobe Experience Platform Data Collection-Benutzer verwalten müssen.

Wechseln Sie zu [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/launch/) und wählen Sie **Tags** aus.

Dies ist die Seite mit den Eigenschaften der Adobe Experience Platform-Datenerfassung , die Sie zuvor gesehen haben.

![Eigenschaftsseite](./images/launch1.png)

In Modul 0 hat Demo System zwei Client-Eigenschaften für Sie erstellt: eine für die Website und eine für die mobile App. Suchen Sie sie, indem Sie im Feld **[!UICONTROL Suche]** nach `--aepUserLdap--` suchen.

![Suchfeld](./images/property6.png)

Öffnen Sie die Eigenschaft **Web** .

Daraufhin wird die Seite Eigenschaftsübersicht angezeigt. Klicken Sie in der linken Leiste auf **[!UICONTROL Erweiterungen]** . Klicken Sie unter der Adobe Experience Platform Web SDK-Erweiterung auf die Schaltfläche **[!UICONTROL Konfigurieren]** .

![Eigenschaftenübersichtsseite](./images/property7.png)

Willkommen beim Adobe Experience Platform Web SDK! Hier können Sie die Erweiterung mit dem Datastream konfigurieren, den Sie in [Übung 0.2](./../../../modules/gettingstarted/gettingstarted/ex2.md) erstellt haben, sowie mit einer erweiterten Konfiguration. Sie werden nur zwei Einstellungen für diese Übung konfigurieren.

Die standardmäßige Edge-Domäne ist immer **edge.adobedc.net**. Wenn Sie eine CNAME-Konfiguration in Ihrer Adobe Experience Cloud- oder Adobe Experience Platform-Umgebung implementiert haben, müssen Sie die **[!UICONTROL Edge-Domäne]** aktualisieren. Ihre Adobe Experience Platform-Instanz verwendet diese Edge-Domäne: `--webSdkEdgeDomain--`.

Wenn sich die Edge-Domäne Ihrer Instanz von der Standarddomäne unterscheidet, aktualisieren Sie die Edge-Domäne. Eine Edge-Domäne ermöglicht die Konfiguration eines Erstanbieter-Tracking-Servers, der dann eine CNAME-Konfiguration im Backend verwendet, um sicherzustellen, dass Daten im Adobe erfasst werden.

![Startseite der Erweiterungen](./images/property9edgedomain.png)

Stellen Sie nun sicher, dass die Optionsschaltfläche **[!UICONTROL Aus Liste auswählen]** unter der Überschrift **[!UICONTROL Datastreams]** ausgewählt ist, und wählen Sie Ihren Datenspeicher mit dem Namen `--aepUserLdap-- - Demo System Datastream` aus der Liste im Feld **[!UICONTROL Datastream]** aus.

![Startseite der Erweiterungen](./images/property9edge.png)

Klicken Sie auf **[!UICONTROL Speichern]** , um zur Ansicht &quot;Erweiterungen&quot;zurückzukehren.

![Adobe Experience Platform Web SDK-Homepage](./images/save.png)

## 1.1.3.2 Datenelemente

Datenelemente sind Bausteine für Ihr Datenwörterbuch (oder Ihre Datenkarte). Verwenden Sie Datenelemente zum Sammeln, Organisieren und Bereitstellen von Daten in Marketing- und Werbetechnologie.

Ein einzelnes Datenelement ist eine Variable, deren Wert Abfragezeichenfolgen, URLs, Cookie-Werten, JavaScript-Variablen usw. zugeordnet werden kann. Sie können diesen Wert in der gesamten Adobe Experience Platform-Datenerfassung anhand seines Variablennamens referenzieren. Diese Sammlung von Datenelementen wird zum Wörterbuch definierter Daten, mit deren Hilfe Sie eigene Regeln erstellen können (Ereignisse, Bedingungen und Aktionen). Dieses Datenwörterbuch wird für die gesamte Adobe Experience Platform-Datenerfassung verwendet und kann mit beliebigen Erweiterungen verwendet werden, die Sie Ihrer Eigenschaft hinzugefügt haben.

Sie werden jetzt ein bereits vorhandenes Datenelement im Format Web SDK Friendly bearbeiten.

Klicken Sie in der linken Leiste auf Datenelemente , um zur Seite Datenelemente zu gelangen.

![Homepage für Datenelemente](./images/dataelement1.png)

>[!NOTE]
>
>Sie bearbeiten nur ein Datenelement in dieser Übung, aber Sie können die Schaltfläche **[!UICONTROL Datenelement hinzufügen]** auf dieser Seite sehen, mit der dem Datenwörterbuch eine neue Variable hinzugefügt wird. Dies kann dann für die gesamte Adobe Experience Platform-Datenerfassung verwendet werden. Sehen Sie sich auch einige andere bereits vorhandene Datenelemente an, meist unter Verwendung des lokalen Speichers als Datenquelle.

Geben Sie in die Suchleiste **XDM - Product View** ein und klicken Sie auf das zurückgegebene Datenelement.

![Suche nach ruleArticlePages](./images/dataelement2.png)

Dieser Bildschirm zeigt das XDM-Objekt, das Sie bearbeiten werden. Das Experience-Datenmodell (XDM) ist ein Konzept, das in diesem Tutorial viel weiter untersucht wird. Zunächst reicht es jedoch aus, es als das Format zu verstehen, das das Adobe Experience Platform Web SDK erfordert. Sie werden den Daten, die auf den Artikelseiten der Demo-Website erfasst wurden, ein wenig mehr Informationen hinzufügen.

Klicken Sie unten im Baum auf die Plusschaltfläche neben **web**.

Klicken Sie auf die Plusschaltfläche neben **webPageDetails**.

Klicken Sie auf **siteSection**. Jetzt sehen Sie, dass **siteSection** noch nicht mit einem Datenelement verknüpft ist. Ändern wir das.

![Navigieren zum Sitebereich](./images/dataelement3.png)

Scrollen Sie nach oben und geben Sie den Text `%Product Category%` ein. Klicken Sie auf **[!UICONTROL Speichern]**.

![Speichern](./images/dataelement4.png)

An dieser Stelle wird die Adobe Experience Platform Web SDK-Erweiterung installiert und Sie haben ein Datenelement aktualisiert, um Daten anhand einer XDM-Struktur zu erfassen. Als Nächstes überprüfen wir die Regeln, die Daten zum richtigen Zeitpunkt senden.

## 1.1.3.3 Regeln

Die Adobe Experience Platform-Datenerfassung ist ein regelbasiertes System. Es wird nach Benutzerinteraktionen und verknüpften Daten gesucht. Wenn die in Ihren Regeln formulierten Kriterien erfüllt sind, löst die Regel die jeweils definierte Erweiterung, das Skript oder den clientseitigen Code aus.

Erstellen Sie Regeln, um die Daten und Funktionen von Marketing- und Werbetechnologien zu integrieren, die verschiedene Produkte in einer einzigen Lösung zusammenführen.

Unterteilen wir die Regel, die Daten auf Artikelseiten sendet.

Klicken Sie in der linken Leiste auf **[!UICONTROL Regeln]** .

**[!UICONTROL Suche]** nach `Product View`.

Klicken Sie auf die zurückgegebene Regel.

![Medien - Regelsuche für Artikelseiten](./images/rule1.png)

Werfen wir einen Blick auf die einzelnen Elemente, aus denen diese Regel besteht. Für alle Regeln Wenn ein angegebenes **[!UICONTROL Ereignis]** auftritt, werden die **[!UICONTROL Bedingungen]** ausgewertet, dann finden bei Bedarf die angegebenen **[!UICONTROL Aktionen]** statt.

![Medien - Regel für Artikelseiten](./images/rule2.png)

Klicken Sie auf das Ereignis **Benutzerspezifisches Ereignis - Produktansicht**. Dies ist die Ansicht, die geladen wird.

Klicken Sie auf die Dropdown-Liste **Ereignistyp** .

Hier werden einige der Standardinteraktionen aufgelistet, mit denen Sie signalisieren können, dass die Adobe Experience Platform-Datenerfassung die Aktionen ausführt, falls die Bedingungen wahr sind.

![Ereignisse](./images/rule3.png)

Klicken Sie auf **[!UICONTROL Abbrechen]** , um zur Regel zurückzukehren.

Klicken Sie auf die Aktion **&quot;Produktansicht&quot;an AEP senden**.

Hier sehen Sie die Daten, die vom Adobe Experience Platform Web SDK an die Adobe Edge gesendet werden. Genauer gesagt wird dabei die **Legierung** **[!UICONTROL Instanz]** des Web SDK verwendet. Durch das Einrichten einer weiteren **[!UICONTROL Instanz]** können u. a. verschiedene Datastreams verwendet werden. Sie haben das Ereignis **[!UICONTROL Typ]** als **commerce.productViews** angegeben und die XDM-Daten, die Sie senden, sind das Datenelement **XDM - Produktansicht** , das Sie zuvor geändert haben.

![Ereignisaktion senden](./images/rule5.png)

Nachdem Sie sich die Regel angesehen haben, können Sie alle Ihre Änderungen in der Adobe Experience Platform-Datenerfassung veröffentlichen.

## 1.1.3.4 Publish in einer Bibliothek

Um die gerade aktualisierte Regel und das Datenelement zu validieren, müssen Sie schließlich eine Bibliothek veröffentlichen, die die bearbeiteten Elemente in unserer Eigenschaft enthält. Im Abschnitt **[!UICONTROL Veröffentlichen]** der Adobe Experience Platform-Datenerfassung müssen Sie einige schnelle Schritte ausführen.

Klicken Sie im linken Navigationsbereich auf **[!UICONTROL Veröffentlichungsfluss]** .

Klicken Sie auf die vorhandene Bibliothek mit dem Namen **Main**.

![Bibliothekszugriff](./images/publish1.png)

Klicken Sie auf die Schaltfläche **Alle geänderten Ressourcen hinzufügen** .

![Bibliothekszugriff](./images/publish1a.png)

Scrollen Sie nach unten, um die meisten Ressourcen als **Revision 1 (Neueste Version)** zu sehen, aber die beiden geänderten Elemente - **Datenelement: ruleArticlePages** und **Extension: Adobe Experience Platform Web SDK** werden nur mit **Neueste** markiert.

Klicken Sie auf die Schaltfläche **Speichern und für Entwicklung erstellen** .

![Inhaltsbibliothek](./images/publish2.png)

Die Erstellung der Bibliothek kann einige Minuten dauern. Wenn sie abgeschlossen ist, wird links neben dem Bibliotheksnamen ein grüner Punkt angezeigt.

Wie Sie auf dem Bildschirm &quot;Veröffentlichungsfluss&quot;sehen können, gibt es viel mehr im Veröffentlichungsprozess in der Adobe Experience Platform-Datenerfassung, was über den Rahmen dieses Tutorials hinausgeht. Wir werden nur eine einzige Bibliothek in unserer Entwicklungsumgebung verwenden.

Nächster Schritt: [1.1.4 Clientseitige Web-Datenerfassung](./ex4.md)

[Zurück zu Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
