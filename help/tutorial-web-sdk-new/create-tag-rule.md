---
title: Tag-Regel erstellen
description: Erfahren Sie, wie Sie mit Ihrem XDM-Objekt mithilfe einer Tag-Regel ein Ereignis an das Platform Edge Network senden. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Tags
source-git-commit: f08866de1bd6ede50bda1e5f8db6dbd2951aa872
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 1%

---

# Tag-Regel erstellen

Erfahren Sie, wie Sie mit Ihrem XDM-Objekt mithilfe einer Tag-Regel ein Ereignis an das Platform Edge Network senden. Eine Tag-Regel ist eine Kombination aus Ereignissen, Bedingungen und Aktionen, die die Tag-Eigenschaft anweist, etwas zu tun.

>[!NOTE]
>
> Zu Demonstrationszwecken bauen die Übungen in dieser Lektion auf dem Beispiel auf, das während der [Erstellen von Identitäten](create-identities.md) Schritt; Senden einer XDM-Ereignisaktion zum Erfassen von Inhalten und Identitäten von Benutzern auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html).


## Lernziele

Am Ende dieser Lektion können Sie:

* Verwenden einer Benennungskonvention zum Verwalten von Regeln innerhalb von Tags
* Senden eines XDM-Ereignisses mithilfe der Aktionstypen &quot;Variable aktualisieren&quot;und &quot;Ereignis senden&quot;in einer Tag-Regel
* Veröffentlichen einer Tag-Regel in einer Entwicklungsbibliothek


## Voraussetzungen

Sie kennen Datenerfassungs-Tags und die [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html)und Sie müssen die folgenden vorherigen Lektionen im Tutorial abgeschlossen haben:

* [Konfigurieren eines XDM-Schemas](configure-schemas.md)
* [Identitäts-Namespace konfigurieren](configure-identities.md)
* [Konfigurieren eines Datenstroms](configure-datastream.md)
* [In der Tag-Eigenschaft installierte Web SDK-Erweiterung](install-web-sdk.md)
* [Erstellen von Datenelementen](create-data-elements.md)
* [Erstellen von Identitäten](create-identities.md)

## Benennungskonventionen

Um Regeln in Tags besser zu verwalten, wird empfohlen, eine standardmäßige Namenskonvention zu befolgen. In diesem Tutorial wird eine dreiteilige Namenskonvention verwendet:

* [**location**] - [**event**] - [**Tool**] (**Sequenz**)

wo;

1. **location** ist die Seite oder die Seiten auf der Site, auf der die Regel ausgelöst wird.
1. **event** ist der Trigger für die Regel
1. **Tool** ist die spezifische(n) Anwendung(en), die im Aktionsschritt für diese Regel verwendet wird/werden.
1. **Sequenz** ist die Reihenfolge, in der die Regel im Verhältnis zu anderen Regeln ausgelöst werden soll
<!-- minor update -->

## Tag-Regel erstellen

In -Tags werden Regeln verwendet, um unter verschiedenen Bedingungen Aktionen (Aufrufe auslösen) auszuführen. Die Platform Web SDK-Tag-Erweiterung umfasst zwei Aktionen, die in dieser Lektion verwendet werden:

* **[!UICONTROL Variable aktualisieren]** ordnet Datenelemente XDM-Feldern zu
* **[!UICONTROL Ereignis senden]** sendet das XDM-Objekt an das Experience Platform Edge Network

### Variable aktualisieren

Erstellen Sie diese erste Regel als &quot;globale Konfiguration&quot;, um alle wichtigen Inhaltsvariablen im XDM-Objekt mithilfe der Platform Web SDKs festzulegen. **[!UICONTROL Variable aktualisieren]** Aktion. Erstellen Sie dann eine zweite Regel, die nach der ersten auf Trigger sequenziert wird, um das XDM-Objekt mithilfe der **[!UICONTROL Ereignis senden]** Aktion. Später in diesem Tutorial senden Sie verschiedene XDM-Felder basierend auf dem Seitentyp, auf der sich der Besucher befindet (z. B. Produkt-SKUs auf Produktseiten). Dazu sequenzieren Sie die Regeln, die **[!UICONTROL Variable aktualisieren]** Aktionen vor der Regel, die die **[!UICONTROL Ereignis senden]** Aktion.

So erstellen Sie eine Tag-Regel:

1. Öffnen Sie die Tag-Eigenschaft, die Sie für dieses Tutorial verwenden

1. Navigieren Sie zu **[!UICONTROL Regeln]** in der linken Navigation

1. Wählen Sie die **[!UICONTROL Neue Regel erstellen]** button

   ![Regel erstellen](assets/rules-create.png)

1. Geben Sie einen Namen für die Regel ein `all pages global content variables - page bottom - AA (order 1)`.

1. Im **[!UICONTROL Veranstaltungen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

   ![Benennen Sie die Regel und fügen Sie ein Ereignis hinzu](assets/rule-name-new.png)

1. Verwenden Sie die **[!UICONTROL Haupterweiterung]** und wählen `Page Bottom` als **[!UICONTROL Ereignistyp]**

1. Unter dem **[!UICONTROL Name]** Feld, nennen Sie es `Core - Page Bottom - order 1`. Auf diese Weise können Sie den Trigger mit einem aussagekräftigen Namen beschreiben.

1. Auswählen **[!UICONTROL Erweitert]** Dropdown und `1` in **[!UICONTROL Bestellung]**

   >[!NOTE]
   >
   > Je höher die Zahl, die Sie eingeben, desto später wird die Gesamtzahl der Vorgänge Trigger.

1. Auswählen **[!UICONTROL Änderungen beibehalten]** zum Hauptregelbildschirm zurückzukehren
   ![Seitenende auswählen, Trigger](assets/create-tag-rule-trigger-bottom.png)

1. Im **[!UICONTROL Aktionen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

1. Als **[!UICONTROL Erweiterung]** auswählen **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als **[!UICONTROL Aktionstyp]** auswählen **[!UICONTROL Variable aktualisieren]**

1. Als **[!UICONTROL Datenelement]**, wählen Sie die `xdm.variable.content` die Sie in der [Erstellen von Datenelementen](create-data-elements.md) Lektion

   ![Variablenschema aktualisieren](assets/create-rule-update-variable.png)

Jetzt zuordnen [!UICONTROL Datenelemente] der [!UICONTROL schema] verwendet von Ihrem XDM-Objekt.

>[!NOTE]
> 
> Sie können einzelnen Eigenschaften oder ganzen Objekten zuordnen. In diesem Beispiel ordnen Sie einzelne Eigenschaften zu.


1. Scrollen Sie nach unten, bis Sie zum **`web`** Objekt

1. Auswahl zum Öffnen

1. Ordnen Sie die folgenden Datenelemente den entsprechenden `web` XDM-Variablen

   * **`web.webPageDetials.name`** in `%page.pageInfo.pageName%`
   * **`web.webPageDetials.server`** in `%page.pageInfo.server%`
   * **`web.webPageDetials.siteSection`** in `%page.pageInfo.hierarchie1%`

   ![Variableninhalt aktualisieren](assets/create-rule-xdm-variable-content.png)

1. Suchen Sie als Nächstes die `identityMap` -Objekt im Schema und wählen Sie es aus

1. Zuordnung zu `identityMap.loginID` Datenelement

   ![Variable-Identitätszuordnung aktualisieren](assets/create-rule-variable-identityMap.png)

1. Suchen Sie anschließend das Feld eventType und wählen Sie es aus

1. Wert eingeben `web.webpagedetails.pageViews`

   >[!WARNING]
   >
   > Mit diesem Dropdown-Menü wird die **`xdm.eventType`** im XDM-Objekt. Sie können in dieses Feld zwar auch Freiform-Beschriftungen eingeben, es wird jedoch dringend empfohlen, **nicht** da es mit Platform negative Auswirkungen hat.

   >[!TIP]
   >
   > So verstehen Sie, welche Werte im `eventType` -Feld, müssen Sie zur Schemaseite gehen und die `eventType` -Feld, um die vorgeschlagenen Werte in der rechten Leiste anzuzeigen.

   ![Variable-Identitätszuordnung aktualisieren](assets/create-tag-rule-eventType.png)


1. Auswählen **[!UICONTROL Änderungen beibehalten]** und dann **[!UICONTROL Speichern]** die Regel im nächsten Bildschirm, um die Erstellung der Regel abzuschließen

### Ereignis senden

Nachdem Sie die Variablen festgelegt haben, können Sie die zweite Regel erstellen, um das XDM-Objekt mit dem **[!UICONTROL Ereignis senden]** Aktionstyp.

1. Wählen Sie rechts Folgendes aus: **[!UICONTROL Regel hinzufügen]** zum Erstellen einer weiteren Regel

1. Geben Sie einen Namen für die Regel ein `all pages send event - page bottom - AA (order 50)`.

1. Im **[!UICONTROL Veranstaltungen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

1. Verwenden Sie die **[!UICONTROL Haupterweiterung]** und wählen `Page Bottom` als **[!UICONTROL Ereignistyp]**

1. Unter dem **[!UICONTROL Name]** Feld, nennen Sie es `Core - Page Bottom - order 50`. Auf diese Weise können Sie den Trigger mit einem aussagekräftigen Namen beschreiben.

1. Auswählen **[!UICONTROL Erweitert]** Dropdown und `50` in **[!UICONTROL Bestellung]**. Dadurch wird sichergestellt, dass die zweite Regel Trigger nach der ersten Regel, die Sie auf Trigger als `1`.

1. Auswählen **[!UICONTROL Änderungen beibehalten]** zum Hauptregelbildschirm zurückzukehren
   ![Seitenende auswählen, Trigger](assets/create-tag-rule-trigger-bottom-send.png)

1. Im **[!UICONTROL Aktionen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

1. Als **[!UICONTROL Erweiterung]** auswählen  **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als  **[!UICONTROL Aktionstyp]** auswählen  **[!UICONTROL Ereignis senden]**

1. Als **[!UICONTROL XDM]**, wählen Sie die `xdm.variable.content` Datenelement, das in der vorherigen Lektion erstellt wurde

1. Auswählen **[!UICONTROL Änderungen beibehalten]** zum Hauptregelbildschirm zurückzukehren

   ![Hinzufügen der Aktion &quot;Ereignis senden&quot;](assets/create-rule-send-event-action.png)
1. Auswählen **[!UICONTROL Speichern]** zum Speichern der Regel

   ![Speichern der Regel](assets/create-rule-save-rule.png)

## Regel in einer Bibliothek veröffentlichen

Veröffentlichen Sie dann die Regel in Ihrer Entwicklungsumgebung, damit Sie überprüfen können, ob sie funktioniert.

So erstellen Sie eine Bibliothek:

1. Navigieren Sie zu **[!UICONTROL Veröffentlichungsfluss]** in der linken Navigation

1. Auswählen **[!UICONTROL Bibliothek hinzufügen]**

   ![Bibliothek hinzufügen](assets/rule-publish-library.png)
1. Für **[!UICONTROL Name]**, eingeben `Luma Web SDK Tutorial`
1. Für **[!UICONTROL Umgebung]** auswählen `Development`
1. Auswählen  **[!UICONTROL Alle geänderten Ressourcen hinzufügen]**

   >[!NOTE]
   >
   >    Zusätzlich zur Adobe Experience Platform Web SDK-Erweiterung und der `all pages global content variables - page bottom - AA (order 50)` -Regel sehen Sie die Tag-Komponenten, die in vorherigen Lektionen erstellt wurden. Die Haupterweiterung enthält das grundlegende JavaScript, das für alle Web-Tag-Eigenschaften erforderlich ist.

1. Auswählen **[!UICONTROL Speichern und erstellen für Entwicklung]**

   ![Erstellen und Erstellen der Bibliothek](assets/create-tag-rule-library-changes.png)

Die Erstellung der Bibliothek kann einige Minuten dauern. Wenn sie abgeschlossen ist, wird links neben dem Bibliotheksnamen ein grüner Punkt angezeigt:

![Build-Abschluss](assets/create-rule-development-success.png)

Wie Sie auf der [!UICONTROL Veröffentlichungsfluss] -Bildschirm gibt es viel mehr im Veröffentlichungsprozess, was über den Rahmen dieses Tutorials hinausgeht. In diesem Tutorial wird nur eine einzige Bibliothek in Ihrer Entwicklungsumgebung verwendet.

Jetzt können Sie die Daten in der Anfrage mithilfe des Adobe Experience Platform Debuggers überprüfen.

[Nächste ](validate-with-debugger.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
