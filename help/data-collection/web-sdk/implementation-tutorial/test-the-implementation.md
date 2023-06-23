---
title: Implementierung testen
description: Implementierung testen
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
jira: KT-10447
hide: true
hidefromtoc: true
exl-id: e2213c23-d395-4c57-8c6c-0319cd0fb0ac
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 2%

---

# Implementierung testen

Nachdem Sie Ihre Webseite eingerichtet und Ihre Adobe Experience Platform-Tag-Bibliothek bereitgestellt haben, ist es an der Zeit, die Implementierung zu testen.

Öffnen Sie Ihre Produktseite in Ihrem Browser. Klicken Sie dazu auf _Datei_ then _Datei öffnen..._ in Ihrem Browser oder Sie können Ihre Seite auf einem Webserver hosten und die entsprechende URL eingeben.

Nachdem die Seite geladen wurde, sollte Folgendes angezeigt werden:

![Webpage](../../assets/implementation-strategy/webpage.png)

Es ist nicht hübsch, aber es wird die Aufgabe erledigen.

## Inspect der Seitenansichts- und Produktansichtsereignisse

Öffnen Sie die Entwicklertools in Ihrem Browser und klicken Sie auf das Netzwerkfenster. Aktualisieren Sie Ihre Seite.

An dieser Stelle sollten vier Anfragen angezeigt werden:

1. product.html - Ihre Webseite.
2. launch-###############-development.js - Ihre Launch-Bibliothek.
3. interact - Das Seitenansichtsereignis, das an den Server gesendet wird.
4. interact - Das Produktansichtsereignis, das an den Server gesendet wird.

Sie können die Payloads jeder Anfrage prüfen. Für die erste `interact` -Anfrage, sollte die Payload angezeigt werden, die mit einer `eventType` von `web.webpagedetails.pageViews`.

![Überprüfung der Seitenansichtsanforderung](../../assets/implementation-strategy/webpage-page-viewed-inspection.png)

Für das zweite `interact` -Anfrage, sollte die Payload angezeigt werden, die mit einer `eventType` von `commerce.productViews`.

![Überprüfung der Produktansicht](../../assets/implementation-strategy/webpage-product-view-inspection.png)

Sie können die restlichen gesendeten Daten, einschließlich der Produktinformationen, einsehen.

## Öffnen Sie den Warenkorb und fügen Sie ihn zu Warenkorbereignissen hinzu.

Klicken Sie nun auf _Zum Warenkorb hinzufügen_ Schaltfläche.

Es sollten zwei zusätzliche Anfragen angezeigt werden, die erste mit einer `eventType` von `commerce.productListOpens` (zum Öffnen eines neuen Warenkorbs) und der zweite mit einer `eventType` von `commerce.productListAdds` (zum Hinzufügen des Produkts zum Warenkorb).

## Inspect: Link-Klickereignis der Download-App

Je nach Browser können Sie durch Klicken auf einen Link, der von der aktuellen Seite weg führt, aus dem Netzwerkbereich löschen. Da Sie die Netzwerkanforderung für das Link-Klickereignis überprüfen möchten, das unmittelbar vor dem Navigieren von der Seite auftritt, müssen Sie Ihren Browser so konfigurieren, dass die Netzwerkprotokolle auf allen Seiten beibehalten werden. Dies geschieht durch Überprüfung der _Protokoll beibehalten_ Kontrollkästchen im Netzwerkbereich (Chrome, Safari, Edge) oder auf ein Zahnradsymbol klicken und eine _Persistente Protokolle_ im angezeigten Menü (Firefox).

Klicken Sie nun auf _App herunterladen_ Link.

Sie sollten eine weitere `interact` -Anfrage wird im Netzwerkbereich angezeigt. Wenn Sie die Anfrage untersuchen, sollten Sie eine `eventType` von `web.webinteraction.linkClicks` sowie Details zum angeklickten Link.

## Überprüfen, ob Daten in den Adobe Experience Platform-Datensatz eingehen

Nachdem jetzt Anfragen gesendet werden, möchten Sie auch überprüfen, ob die Daten sicher in den von Ihnen erstellten Adobe Experience Platform-Datensatz gelangen. Navigieren Sie zunächst zur [!UICONTROL Datensätze] Ansicht in Adobe Experience Platform.

Wählen Sie den zuvor erstellten Datensatz aus.

Möglicherweise müssen Sie einige Minuten warten, aber bald sollten Sie Anzeichen dafür sehen, dass Daten verarbeitet und in Ihren Datensatz eingefügt werden. Sie sollten auch sehen, ob die Verarbeitung erfolgreich war oder fehlgeschlagen ist. Wenn es fehlschlägt, werden Sie sehen können, warum es fehlgeschlagen ist. In der Regel treten Fehler auf, da die von Ihnen gesendeten Daten nicht mit dem Schema übereinstimmen und Sie Ihre Daten oder Ihr Schema entsprechend anpassen müssen.

![Datensatzaufnahme](../../assets/implementation-strategy/dataset-ingestion.png)

## Verwenden der Adobe Experience Platform Debugger-Erweiterung

Weitere Informationen dazu, wie sich Ihre Implementierung sowohl im Browser als auch auf den Servern der Adobe verhält, finden Sie in der Browsererweiterung für Adobe Experience Platform Debugger .

[Adobe Experience Platform Debugger-Erweiterung für Chrome](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

[Adobe Experience Platform Debugger-Erweiterung für Firefox](https://addons.mozilla.org/de/firefox/addon/adobe-experience-platform-dbg/)
