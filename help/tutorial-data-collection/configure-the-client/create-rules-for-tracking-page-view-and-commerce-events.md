---
title: Erstellen von Regeln für die Verfolgung von Seitenansichten und Commerce-Ereignissen
description: Erstellen von Regeln für die Verfolgung von Seitenansichten und Commerce-Ereignissen
exl-id: 00bf3374-9319-47ce-a75a-2b94f793c938
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 3%

---

# Erstellen von Regeln für die Verfolgung von Seitenansichten und Commerce-Ereignissen

Um nachzuverfolgen, ob der Benutzer die Produktseite angezeigt hat, erstellen Sie eine Regel in Adobe Experience Platform [!DNL Tags].

1. Klicken Sie auf **[!UICONTROL Regeln]** Klicken Sie in der linken Seitennavigation auf **[!UICONTROL Neue Regel erstellen]**.

1. Geben Sie für den Regelnamen **_Angezeigte Seite_**.

## Ereignis hinzufügen

1. Klicken Sie auf **[!UICONTROL Hinzufügen]** Schaltfläche unter [!UICONTROL Veranstaltungen]. Sie werden jetzt in der Ereignisansicht angezeigt. Für [!UICONTROL Erweiterung] Feld, wählen Sie **[!UICONTROL Adobe Client-Datenschicht]**. Für [!UICONTROL Ereignistyp] Feld, wählen Sie **[!UICONTROL Übermittelte Daten]**.
1. Da diese Regel nur ausgelöst werden soll, wenn die Variable `pageViewed` -Ereignis an die Datenschicht gesendet wird, wählen Sie **[!UICONTROL Bestimmtes Ereignis]** under [!UICONTROL Hören Sie zu] und Typ **_pageViewed_** in [!UICONTROL Ereignis/Schlüssel zur Registrierung] Textfeld.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.
   ![Ereignis &quot;Seite angezeigt&quot;](../assets/page-viewed-event.png)

## Hinzufügen einer Aktion

Nachdem Sie sich wieder in der Regelansicht befinden:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** unter [!UICONTROL Aktionen]. Sie sollten sich jetzt in der Aktionsansicht befinden. Für [!UICONTROL Erweiterung] Feld, wählen Sie **[!UICONTROL Adobe Experience Platform Web SDK]**. Für [!UICONTROL Aktionstyp] Feld, wählen Sie **[!UICONTROL Ereignis senden]**. Mit dieser Aktion können Sie ein Erlebnisereignis an Adobe Experience Platform Edge Network senden.
1. Suchen Sie in der Mitte des Bildschirms die [!UICONTROL Typ] Feld und wählen Sie **`web.webpagedetails.pageViews`**. Dies ist einer der kanonischen Erlebnisereignistypen, die Adobe Experience Platform standardmäßig bereitstellt. Es stellt eine Seitenansicht dar.
1. Für [!UICONTROL XDM-Daten] Feld, eingeben **`%event.fullState%`**. Dies zeigt an, dass der berechnete Status (auch als vollständiger Status bezeichnet) der Datenschicht, der zum Zeitpunkt der Regelauslösung erfasst wird. Dies sollte als Teil des Erlebnisereignisses gesendet werden.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]** Schaltfläche.
   ![Aktion &quot;Seite angezeigt&quot;](../assets/page-viewed-action.png)

Wenn die Daten, die Sie von Ihrer Website in die Datenschicht gesendet haben, nicht mit Ihrem XDM-Schema übereinstimmen oder Sie nur einen Teil des berechneten Status der Datenschicht senden möchten, verwenden Sie die [!UICONTROL XDM-Objekt] Datenelementtyp (bereitgestellt von der Adobe Experience Platform Web SDK-Erweiterung) zum Erstellen eines geeigneten Objekts, das Ihrem Schema entspricht.

## Speichern Sie die Regel

1. Speichern Sie die Regel, indem Sie auf **[!UICONTROL Speichern]**.
   ![Seitenanzeigeregel](../assets/page-viewed-rule.png)

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

Als Nächstes verarbeiten wir Tracking-Klicks auf die [!UICONTROL App herunterladen] Link.

[Weiter: ](create-a-data-element-and-rule-for-tracking-app-downloads.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
