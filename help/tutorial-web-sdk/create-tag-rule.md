---
title: Tag-Regel erstellen
description: Erfahren Sie, wie Sie mit Ihrem XDM-Objekt mithilfe einer Tag-Regel ein Ereignis an das Platform-Edge Network senden. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Tags
exl-id: e06bad06-3ee3-475f-9b10-f0825a48a312
source-git-commit: 15bc08bdbdcb19f5b086267a6d94615cbfe1bac7
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 3%

---

# Tag-Regel erstellen


>[!CAUTION]
>
>Wir gehen davon aus, dass am Dienstag, dem 23. April 2024, wichtige Änderungen an diesem Tutorial veröffentlicht werden. Danach ändern sich viele Übungen und Sie müssen das Tutorial möglicherweise von Anfang an neu starten, um alle Lektionen abzuschließen.

Erfahren Sie, wie Sie mit Ihrem XDM-Objekt mithilfe einer Tag-Regel ein Ereignis an das Platform-Edge Network senden. Eine Tag-Regel ist eine Kombination aus Ereignissen, Bedingungen und Aktionen, die die Tag-Eigenschaft anweist, etwas zu tun.

>[!NOTE]
>
> Zu Demonstrationszwecken bauen die Übungen in dieser Lektion auf dem Beispiel auf, das während der [Erstellen von Datenelementen](create-data-elements.md) Schritt; Senden einer XDM-Ereignisaktion zum Erfassen von Inhalten und Identitäten von Benutzern auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html).


## Lernziele

Am Ende dieser Lektion können Sie:

* Verwenden einer Benennungskonvention zum Verwalten von Regeln innerhalb von Tags
* Erstellen einer Tag-Regel zum Senden eines XDM-Ereignisses
* Veröffentlichen einer Tag-Regel in einer Entwicklungsbibliothek


## Voraussetzungen

Sie kennen Datenerfassungs-Tags und die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html)und Sie müssen die folgenden vorherigen Lektionen im Tutorial abgeschlossen haben:

* [Berechtigungen konfigurieren](configure-permissions.md)
* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)
* [Erstellen von Datenelementen](create-data-elements.md)

## Benennungskonventionen

Um Regeln in Tags besser zu verwalten, wird empfohlen, eine standardmäßige Namenskonvention zu befolgen. In diesem Tutorial wird eine dreiteilige Namenskonvention verwendet:

* [location] - [event] - [Tool]

wo;

1. location ist die Seite oder die Seiten auf der Site, auf der die Regel ausgelöst wird.
1. -Ereignis ist der Trigger, der das -Beacon auslöst
1. -Tool ist die spezifische Anwendung bzw. die Anwendungen, die im Aktionsschritt für diese Regel verwendet werden


## Tag-Regel erstellen

In -Tags werden Regeln verwendet, um unter verschiedenen Bedingungen Aktionen (Aufrufe auslösen) auszuführen. Sie verwenden diese erste Regel, um das XDM-Objekt mithilfe von Web SDKs an das Edge Network zu senden. [!UICONTROL Ereignis senden] Aktion. Später in diesem Tutorial senden Sie verschiedene Versionen des XDM-Objekts basierend auf dem Typ der Seite, auf der sich der Besucher befindet. Aus diesem Grund verwenden Sie Regelbedingungen, um diese anderen Seitentypen auszuschließen.

So erstellen Sie eine Tag-Regel:

1. Öffnen Sie die Tag-Eigenschaft, die Sie für dieses Tutorial verwenden
1. Navigieren Sie zu **[!UICONTROL Regeln]** in der linken Navigation
1. Wählen Sie die **[!UICONTROL Neue Regel erstellen]** button
   ![Regel erstellen](assets/rules-create.png)
1. Geben Sie einen Namen für die Regel ein `all pages - library load - AA & AT`.

   >[!NOTE]
   >
   > Diese Regel wird von Adobe Analytics und Target in einer zukünftigen Lektion auf bestimmte Weise verwendet. Dies ist der Grund `AA & AT` wird am Ende des Namens verwendet.

1. Im **[!UICONTROL Veranstaltungen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**
   ![Benennen Sie die Regel und fügen Sie ein Ereignis hinzu](assets/rule-name.png)
1. Verwenden Sie die **[!UICONTROL Haupterweiterung]** und wählen `Library Loaded (Page Top)` als **[!UICONTROL Ereignistyp]**.

   Diese Einstellung bedeutet, dass die Regel jedes Mal ausgelöst wird, wenn die Tag-Bibliothek auf einer Seite geladen wird.
1. Auswählen **[!UICONTROL Änderungen beibehalten]** zum Hauptregelbildschirm zurückzukehren
   ![Hinzufügen des Ereignisses &quot;Bibliothek geladen&quot;](assets/rule-event-pagetop.png)
1. Im **[!UICONTROL Bedingungen]** auswählen, wählen Sie die **[!UICONTROL Hinzufügen]** button
   ![Bedingungen hinzufügen](assets/rules-add-conditions.png)
1. Auswählen **[!UICONTROL Logiktyp]** `Exception`, **[!UICONTROL Erweiterung]** `Core`, und **[!UICONTROL Bedingungstyp]** `Path Without Query String`
1. URL-Pfad eingeben `/content/luma/us/en/user/cart.html` im **[!UICONTROL path equals]** und **[!UICONTROL name]** it `Core - cart page`
1. Auswählen **[!UICONTROL Änderungen beibehalten]**
   ![Bedingungen hinzufügen](assets/rule-condition-exception.png)
1. Fügen Sie drei weitere Ausnahmen für die folgenden URL-Pfade hinzu

   * **`Core - checkout page`** for `/content/luma/us/en/user/checkout.html`
   * **`Core - thank you page`** for `/content/luma/us/en/user/checkout/order/thank-you.html`
   * **`Core - product page`** für `/products/` mit aktiviertem Regex-Schalter

   ![Bedingungen hinzufügen](assets/rule-condition-exception-all.png)

1. Im **[!UICONTROL Aktionen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**
1. Auswählen **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Erweiterung]**
1. Auswählen **[!UICONTROL Ereignis senden]** als **[!UICONTROL Aktionstyp]**
1. Auswählen **[!UICONTROL web.webpageDetails.pageViews]** als **[!UICONTROL Typ]**.

   >[!WARNING]
   >
   > Mit diesem Dropdown-Menü wird die **`xdm.eventType`** im XDM-Objekt. Sie können in dieses Feld zwar auch Freiform-Beschriftungen eingeben, es wird jedoch dringend empfohlen, **nicht** da es bei Platform negative Auswirkungen haben wird.

1. Als **[!UICONTROL XDM-Daten]**, wählen Sie die `xdm.content` Datenelement, das in der vorherigen Lektion erstellt wurde
1. Auswählen **[!UICONTROL Änderungen beibehalten]** zum Hauptregelbildschirm zurückzukehren

   ![Hinzufügen der Aktion &quot;Ereignis senden&quot;](assets/rule-set-action-xdm.png)
1. Auswählen **[!UICONTROL Speichern]** zum Speichern der Regel

   ![Speichern der Regel](assets/rule-save.png)

## Regel in einer Bibliothek veröffentlichen

Veröffentlichen Sie dann die Regel in Ihrer Entwicklungsumgebung, damit wir überprüfen können, ob sie funktioniert.

So erstellen Sie eine Bibliothek:

1. Navigieren Sie zu **[!UICONTROL Veröffentlichungsfluss]** in der linken Navigation
1. Auswählen **[!UICONTROL Bibliothek hinzufügen]**

   ![Bibliothek hinzufügen](assets/rule-publish-library.png)
1. Für **[!UICONTROL Name]**, eingeben `Luma Web SDK Tutorial`
1. Für **[!UICONTROL Umgebung]** auswählen `Development`
1. Auswählen  **[!UICONTROL Alle geänderten Ressourcen hinzufügen]**

   >[!NOTE]
   >
   >    Zusätzlich zur Adobe Experience Platform Web SDK-Erweiterung und der `all pages - library load - AA & AT` -Regel werden die Tag-Komponenten angezeigt, die in früheren Lektionen erstellt wurden. Die Haupterweiterung enthält das grundlegende JavaScript, das für alle Web-Tag-Eigenschaften erforderlich ist.

1. Auswählen **[!UICONTROL Speichern und erstellen für Entwicklung]**

   ![Erstellen und Erstellen der Bibliothek](assets/rule-publish-add-all-changes.png)

Die Erstellung der Bibliothek kann einige Minuten dauern. Wenn sie abgeschlossen ist, wird links neben dem Bibliotheksnamen ein grüner Punkt angezeigt:

![Build-Abschluss](assets/rule-publish-success.png)

Wie Sie auf der [!UICONTROL Veröffentlichungsfluss] -Bildschirm gibt es viel mehr im Veröffentlichungsprozess, was über den Rahmen dieses Tutorials hinausgeht. In diesem Tutorial wird nur eine einzige Bibliothek in Ihrer Entwicklungsumgebung verwendet.

Jetzt können Sie die Daten in der Anfrage mithilfe des Adobe Experience Platform Debuggers überprüfen.

[Nächste ](validate-with-debugger.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
