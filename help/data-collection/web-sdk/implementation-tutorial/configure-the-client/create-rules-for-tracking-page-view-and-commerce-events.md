---
title: Erstellen von Regeln für die Verfolgung von Seitenansichten und Commerce-Ereignissen
description: Erstellen von Regeln für die Verfolgung von Seitenansichten und Commerce-Ereignissen
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
jira: KT-10447
hide: true
hidefromtoc: true
exl-id: 2dd02462-ddb5-4f67-8b0f-4a5bf5f7d655
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 2%

---

# Erstellen von Regeln für die Verfolgung von Seitenansichten und Commerce-Ereignissen

Um nachzuverfolgen, ob der Benutzer die Produktseite angezeigt hat, erstellen Sie eine Regel innerhalb von Adobe Experience Platform-Tags. Klicken Sie dazu auf [!UICONTROL Regeln] Klicken Sie im Menü links auf [!UICONTROL Regel hinzufügen].

Geben Sie für den Regelnamen _Angezeigte Seite_.

## Ereignis hinzufügen

Klicken Sie auf [!UICONTROL Hinzufügen] Schaltfläche unter [!UICONTROL Veranstaltungen]. Sie werden jetzt in der Ereignisansicht angezeigt. Für [!UICONTROL Erweiterung] Feld, wählen Sie [!UICONTROL Adobe Client-Datenschicht]. Für [!UICONTROL Ereignistyp] Feld, wählen Sie [!UICONTROL Übermittelte Daten].

Da diese Regel nur ausgelöst werden soll, wenn die Variable `pageViewed` -Ereignis an die Datenschicht gesendet wird, wählen Sie [!UICONTROL Bestimmtes Ereignis] under [!UICONTROL Hören Sie zu] und Typ _pageViewed_ in [!UICONTROL Ereignis/Schlüssel zur Registrierung] Textfeld.

![Ereignis &quot;Seite angezeigt&quot;](../../../assets/implementation-strategy/page-viewed-event.png)

Klicken Sie auf [!UICONTROL Änderungen beibehalten].

## Hinzufügen einer Aktion

Nachdem Sie sich wieder in der Regelansicht befinden, klicken Sie auf die [!UICONTROL Hinzufügen] Schaltfläche unter [!UICONTROL Aktionen]. Sie sollten sich jetzt in der Aktionsansicht befinden. Für [!UICONTROL Erweiterung] Feld, wählen Sie [!UICONTROL Adobe Experience Platform Web SDK]. Für [!UICONTROL Aktionstyp] Feld, wählen Sie [!UICONTROL Ereignis senden]. Mit dieser Aktion können Sie ein Erlebnisereignis an Adobe Experience Platform Edge Network senden.

Suchen Sie rechts auf dem Bildschirm die [!UICONTROL Typ] Feld und wählen Sie `web.webpagedetails.pageViews`. Dies ist einer der kanonischen Erlebnisereignistypen, die Adobe Experience Platform standardmäßig bereitstellt. Es stellt eine Seitenansicht dar.

Für [!UICONTROL XDM-Daten] Feld, eingeben `%event.fullState%`. Dies bedeutet, dass der berechnete Status (auch als vollständiger Status bezeichnet) der Datenschicht, der zum Zeitpunkt der Regelauslösung erfasst wird, als Teil des Erlebnisereignisses gesendet werden sollte.

![Aktion &quot;Seite angezeigt&quot;](../../../assets/implementation-strategy/page-viewed-action.png)

Wenn die Daten, die Sie von Ihrer Website in die Datenschicht gesendet haben, nicht mit Ihrem XDM-Schema übereinstimmen oder Sie nur einen Teil des berechneten Status der Datenschicht senden möchten, verwenden Sie die [!UICONTROL XDM-Objekt] Datenelementtyp (bereitgestellt von der Adobe Experience Platform Web SDK-Erweiterung) zum Erstellen eines geeigneten Objekts, das Ihrem Schema entspricht.

Klicken Sie auf [!UICONTROL Änderungen beibehalten] Schaltfläche.

## Speichern Sie die Regel

Ihre Regel sollte jetzt abgeschlossen sein.

![Seitenanzeigeregel](../../../assets/implementation-strategy/page-viewed-rule.png)

Speichern Sie die Regel, indem Sie auf [!UICONTROL Speichern].

## Wiederholen Sie den Vorgang

Wiederholen Sie den oben beschriebenen Prozess, um Regeln für die Anzeige eines Produkts, für das Öffnen eines Warenkorbs und für das Hinzufügen eines Produkts zum Warenkorb zu erstellen. Die einzigen Unterschiede zwischen den Regeln sind der Regelname und der in der Variablen [!UICONTROL Ereignis/Schlüssel zur Registrierung] im Feld [!UICONTROL Übermittelte Daten] und dem [!UICONTROL Typ] im Feld [!UICONTROL Ereignis senden] Aktion. Hier finden Sie die Werte für jede Regel:

Vom Produkt angezeigte Regel:

* **Regelname**: _Angezeigte Produkte_
* **Ereignis/Schlüssel zur Registrierung** Innerhalb [!UICONTROL Übermittelte Daten] event: `productViewed`
* **Typ** Innerhalb [!UICONTROL Ereignis senden] Aktion: `commerce.productViews`

Regel zum Öffnen des Warenkorbs:

* **Regelname**: _Öffnung des Warenkorbs_
* **Ereignis/Schlüssel zur Registrierung** Innerhalb [!UICONTROL Übermittelte Daten] event: `cartOpened`
* **Typ** Innerhalb [!UICONTROL Ereignis senden] Aktion: `commerce.productListOpens`

Produkt zur Warenkorbregel hinzugefügt:

* **Regelname**: _Produkt zum Warenkorb hinzugefügt_
* **Ereignis/Schlüssel zur Registrierung** Innerhalb [!UICONTROL Übermittelte Daten] event: `productAddedToCart`
* **Typ** Innerhalb [!UICONTROL Ereignis senden] Aktion: `commerce.productListAdds`

Als Nächstes werden wir mit dem Tracking von Klicks auf die [!UICONTROL App herunterladen] Link.
