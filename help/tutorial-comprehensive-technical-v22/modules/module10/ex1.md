---
title: Adobe Journey Optimizer - Trigger-basierte Journey konfigurieren - Bestellbestätigung
description: In diesem Abschnitt konfigurieren Sie eine Trigger-basierte Journey - Bestellbestätigung
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 69bb9eca-3942-4c31-a3d2-0b218143e1eb
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 9%

---

# 10.1 Trigger-basierte Journey konfigurieren - Bestellbestätigung

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxId--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 10.1.1 Ereignis erstellen

Gehen Sie im Menü zu **Konfigurationen** und klicken Sie auf **Verwalten** under **Veranstaltungen**.

![Journey Optimizer](./images/oc30.png)

Im **Veranstaltungen** -Bildschirm angezeigt, sehen Sie eine ähnliche Ansicht. Klicken **Ereignis erstellen**.

![Journey Optimizer](./images/oc31.png)

Anschließend wird eine leere Ereigniskonfiguration angezeigt.

![Journey Optimizer](./images/oc32.png)

Geben Sie Ihrem Ereignis zunächst einen Namen wie den folgenden: `--demoProfileLdap--PurchaseEvent`und fügen Sie eine Beschreibung wie die folgende hinzu: `Purchase Event`.

![Journey Optimizer](./images/oc34.png)

Als Nächstes folgt die **Ereignistyp** auswählen. Auswählen **Einzelfall**.

![Journey Optimizer](./images/eventidtype1.png)

Als Nächstes folgt die **Ereignis-ID-Typ** auswählen. Auswählen **Systemgeneriert**

![Journey Optimizer](./images/eventidtype.png)

Als Nächstes folgt die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Bitte verwenden Sie das Schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![Journey Optimizer](./images/oc35.png)

Nach Auswahl des Schemas werden im **Nutzlast** Abschnitt. Klicken Sie auf **Bearbeiten/Bleistift** -Symbol, um diesem Ereignis zusätzliche Felder hinzuzufügen.

![Journey Optimizer](./images/oc36.png)

Dann sehen Sie dieses Popup. Sie müssen jetzt zusätzliche Kontrollkästchen aktivieren, um auf zusätzliche Daten zuzugreifen, wenn dieses Ereignis ausgelöst wird.

![Journey Optimizer](./images/oc37.png)

Aktivieren Sie zunächst das Kontrollkästchen in der Zeile `--aepTenantId--`.

![Journey Optimizer](./images/oc38.png)

Scrollen Sie dann nach unten und aktivieren Sie das Kontrollkästchen in der Zeile `productListItems`.

![Journey Optimizer](./images/oc39.png)

Scrollen Sie dann nach unten und aktivieren Sie das Kontrollkästchen in der Zeile `commerce`.

![Journey Optimizer](./images/oc391.png)

Klicken Sie anschließend auf **Ok**.

Anschließend werden Sie sehen, dass dem Ereignis zusätzliche Felder hinzugefügt wurden. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/oc40.png)

Ihr neues Ereignis wird dann freigegeben und Ihr Ereignis wird jetzt in der Liste der verfügbaren Ereignisse angezeigt.

Klicken Sie erneut auf Ihr Ereignis, um die **Ereignis bearbeiten** erneut angezeigt.
Bewegen Sie den Mauszeiger über die **Nutzlast** erneut ein, um die 3 Symbole erneut anzuzeigen. Klicken Sie auf **Payload anzeigen** Symbol.

![Journey Optimizer](./images/oc41.png)

Sie sehen nun ein Beispiel der erwarteten Payload. Ihr Ereignis verfügt über eine eindeutige eventID für die Orchestrierung, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID`.

![Journey Optimizer](./images/oc42.png)

Die Ereignis-ID muss an Adobe Journey Optimizer gesendet werden, um die Journey Trigger, die Sie im nächsten Schritt erstellen werden. Notieren Sie sich diese eventID, da Sie sie in einem der nächsten Schritte benötigen werden.
`"eventID": "ef6dd943c94fe1b4763c098ccd1772344662f2a9f614513106cb5ada8be36857"`

Klicken **Ok**, gefolgt von **Abbrechen**.

Ihr Ereignis ist jetzt konfiguriert und kann verwendet werden.

## 10.1.2 Journey erstellen

Gehen Sie im Menü zu **Journey** und klicken Sie auf **Journey erstellen**.

![Journey Optimizer](./images/oc43.png)

Dann wirst du das sehen. Benennen Sie Ihre Journey. Verwenden Sie `--demoProfileLdap-- - Order Confirmation journey`. Klicken Sie auf **OK**.

![Journey Optimizer](./images/oc45.png)

Zunächst müssen Sie Ihr Ereignis als Ausgangspunkt Ihrer Journey hinzufügen. Suchen nach Ihrem Ereignis `--demoProfileLdap--PurchaseEvent` und ziehen Sie es auf die Arbeitsfläche. Klicken Sie auf **OK**.

![Journey Optimizer](./images/oc46.png)

Weiter, unter **Aktionen**, suchen Sie nach der **Email** und fügen Sie sie auf der Arbeitsfläche hinzu.

![Journey Optimizer](./images/oc47.png)

Legen Sie die **Kategorie** nach **Marketing** und wählen Sie eine E-Mail-Oberfläche aus, über die Sie E-Mails versenden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **Email**. Stellen Sie sicher, dass die Kontrollkästchen für **Klicks auf E-Mail** und **E-Mail-Öffnungen** beide aktiviert sind.

![ACOP](./images/journeyactions1.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

Das sehen Sie jetzt. Klicken Sie auf **Betreff** Textfeld.

![ACOP](./images/journeyactions3.png)

Beginnen Sie im Textbereich mit dem Schreiben **Danke für Ihre Bestellung!**

![Journey Optimizer](./images/oc5.png)

Die Betreffzeile ist noch nicht fertig. Als Nächstes müssen Sie das Personalisierungstoken für das Feld einfügen **Vorname** die unter `profile.person.name.firstName`. Scrollen Sie im linken Menü nach unten, um die **Person** > **Vollständiger Name** >  **Vorname** und klicken Sie auf **+** -Symbol, um das Personalisierungstoken zur Betreffzeile hinzuzufügen. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/oc6.png)

Du wirst dann wieder hier sein. Klicken **Email Designer** um den Inhalt der E-Mail zu erstellen.

![Journey Optimizer](./images/oc7.png)

Klicken Sie im nächsten Bildschirm auf **Design von Grund auf neu**.

![Journey Optimizer](./images/oc8.png)

Im linken Menü finden Sie die Strukturkomponenten, mit denen Sie die Struktur der E-Mail definieren können (Zeilen und Spalten).

Ziehen Sie 8-mal pro **1:1-Spalte** auf der Arbeitsfläche, die Ihnen Folgendes geben sollte:

![Journey Optimizer](./images/oc9.png)

Navigieren Sie zu **Inhaltskomponenten**.

![Journey Optimizer](./images/oc10.png)

Ziehen und Ablegen eines **Bild** -Komponente in der ersten Zeile. Klicken Sie auf **Durchsuchen**.

![Journey Optimizer](./images/oc11.png)

Navigieren Sie zum Ordner . **enable-assets**, wählen Sie die Datei aus. **luma-logo.png** und klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/oc12.png)

Du bist jetzt wieder hier. Klicken Sie auf das Bild, um es auszuwählen, und verwenden Sie dann **Größe** -Regler, um das Logo-Bild etwas kleiner zu machen.

![Journey Optimizer](./images/oc13.png)

Navigieren Sie zu **Inhaltskomponenten** und ziehen Sie eine **Bild** -Komponente in der zweiten Zeile. Wählen Sie die **Bildkomponente** aber nicht auf Durchsuchen klicken.

![Journey Optimizer](./images/oc15.png)

Fügen Sie diese Bild-URL in das Feld ein. **Quelle**: `https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/29043bedcde632a9cbe8a02a164189c9_preparing.png`. Dieses Bild wird außerhalb von Adobe gehostet.

![Journey Optimizer](./images/oc14.png)

Wenn Sie den Umfang in ein anderes Feld ändern, wird das Bild gerendert und Sie sehen Folgendes:

![Journey Optimizer](./images/oc16.png)

Navigieren Sie als Nächstes zu **Inhaltskomponenten** und ziehen Sie eine **Text** -Komponente in der dritten Zeile.

![Journey Optimizer](./images/oc17.png)

Wählen Sie den Standardtext in dieser Komponente aus **Bitte geben Sie Ihren Text hier ein.** und ersetzen Sie sie durch den folgenden Text:

```javascript
You’re one step closer!

Hi 

We've received your order details!

We will also send you a separate email containing your VAT Invoice.

We'll be back in touch with you as soon as we've finished packing your package. Please read carefully the Order Information detailed below.
```

![Journey Optimizer](./images/oc18.png)

Setzen Sie den Cursor neben den Text **Hi** und klicken Sie auf **Personalisierung hinzufügen**.

![Journey Optimizer](./images/oc19.png)

Navigieren Sie zum **Person** > **Vollständiger Name** > **Vorname** und klicken Sie auf **+** -Symbol, um das Personalisierungstoken zur Betreffzeile hinzuzufügen. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/oc20.png)

Daraufhin sehen Sie Folgendes:

![Journey Optimizer](./images/oc21.png)

Navigieren Sie als Nächstes zu **Inhaltskomponenten** und ziehen Sie eine **Text** -Komponente in der vierten Zeile.

![Journey Optimizer](./images/oc22.png)

Wählen Sie den Standardtext in dieser Komponente aus **Bitte geben Sie Ihren Text hier ein.** und ersetzen Sie sie durch den folgenden Text:

`Order Information`

Ändern Sie die Schriftgröße in **26 px** und zentrieren Sie Ihren Text in diese Zelle. Dann haben Sie Folgendes:

![Journey Optimizer](./images/oc23.png)

Navigieren Sie als Nächstes zu **Inhaltskomponenten** und ziehen Sie eine **HTML** -Komponente in der fünften Zeile. Klicken Sie auf die HTML-Komponente und dann auf **Quellcode anzeigen**.

![Journey Optimizer](./images/oc24.png)

Im **HTML bearbeiten** Popup öffnen, diese HTML einfügen:

```<table><tbody><tr><td><b>Items purchased</b></td><td></td><td><b>Quantity</b></td><td><b>Subtotal</b></td></tr><tr><td colspan="4" width="500"><hr></td></tr></tbody></table>```

Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/oc25.png)

Dann wirst du das haben. Klicken **Speichern** um den Fortschritt zu speichern.

![Journey Optimizer](./images/oc26.png)

Navigieren Sie zu **Inhaltskomponenten** und ziehen Sie eine **HTML** -Komponente in der sechsten Zeile. Klicken Sie auf die HTML-Komponente und dann auf **Quellcode anzeigen**.

![Journey Optimizer](./images/oc57.png)

Im **HTML bearbeiten** Popup öffnen, diese HTML einfügen:

```{{#each xxx as |item|}}<table width="500"><tbody><tr><td><img src="{{item.--aepTenantId--.core.imageURL}}" width="100"></td><td><table><tbody><tr><td><b>{{item.name}}</b><br>{{item.--aepTenantId--.core.subCategory}}<br><b>{{item.priceTotal}}</b><br>&nbsp;<br>Article no: {{item.SKU}}</td></tr></tbody></table></td><td>{{item.quantity}}</td><td><b>{{item.priceTotal}}</b></td></tr></tbody></table>{{/each}}```

Dann haben Sie Folgendes:

![Journey Optimizer](./images/oc58.png)

Sie müssen jetzt **xxx** durch einen Verweis auf das productListItems-Objekt, das Teil des Ereignisses ist, das die Journey Trigger.

![Journey Optimizer](./images/oc59.png)

Löschen Sie zunächst **xxx** in Ihren HTML-Code.

![Journey Optimizer](./images/oc60.png)

Klicken Sie im linken Menü auf **Kontextattribute**. Dieser Kontext wird von der Journey an die Nachricht übergeben.

![Journey Optimizer](./images/oc601.png)

Dann wirst du das sehen. Klicken Sie auf den Pfeil neben **Journey Orchestration** um tiefer zu bohren.

![Journey Optimizer](./images/oc61.png)

Klicken Sie auf den Pfeil neben **Veranstaltungen** um tiefer zu bohren.

![Journey Optimizer](./images/oc62.png)

Klicken Sie auf den Pfeil neben `--demoProfileLdap--PurchaseEvent` um tiefer zu bohren.

![Journey Optimizer](./images/oc63.png)

Klicken Sie auf den Pfeil neben **productListItems** um tiefer zu bohren.

![Journey Optimizer](./images/oc64.png)

Klicken Sie auf **+** Symbol neben **Name** , um es der Arbeitsfläche hinzuzufügen. Dann wirst du das haben. Sie müssen jetzt  **.name** wie im folgenden Screenshot angegeben, sollten Sie **.name**.

![Journey Optimizer](./images/oc65.png)

Dann wirst du das haben. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/oc66.png)

Jetzt sind Sie wieder in Email Designer. Klicken **Speichern** um den Fortschritt zu speichern.

![Journey Optimizer](./images/oc67.png)

Navigieren Sie als Nächstes zu **Inhaltskomponenten** und ziehen Sie eine **HTML** -Komponente in der siebten Zeile. Klicken Sie auf die HTML-Komponente und dann auf **Quellcode anzeigen**.

![Journey Optimizer](./images/oc68.png)

Im **HTML bearbeiten** Popup öffnen, diese HTML einfügen:

```<table><tbody><tr><td><b>Subtotal</b><br>Delivery charge (included)</td><td align="right"><b>xxx</b><br><b>5</b></td></tr><tr><td colspan="2" width="500"><hr></td></tr><tr><td><b>Total including VAT</b></td><td align="right"><b>xxx</b></td></tr></tbody></table>```

Es gibt 2 Verweise auf **xxx** in diesem HTML-Code. Sie müssen jetzt jede **xxx** durch einen Verweis auf das productListItems-Objekt, das Teil des Ereignisses ist, das die Journey Trigger.

![Journey Optimizer](./images/oc69.png)

Löschen Sie zunächst den ersten **xxx** in Ihrem HTML-Code.

![Journey Optimizer](./images/oc71.png)

Klicken Sie im linken Menü auf **Kontextuelle Attribute**.

![Journey Optimizer](./images/oc711.png)

Klicken Sie auf den Pfeil neben **Journey Orchestration** um tiefer zu bohren.

![Journey Optimizer](./images/oc72.png)

Klicken Sie auf den Pfeil neben **Veranstaltungen** um tiefer zu bohren.

![Journey Optimizer](./images/oc722.png)

Klicken Sie auf den Pfeil neben `--demoProfileLdap--PurchaseEvent` um tiefer zu bohren.

![Journey Optimizer](./images/oc73.png)

Klicken Sie auf den Pfeil neben **Handel** um tiefer zu bohren.

![Journey Optimizer](./images/oc733.png)

Klicken Sie auf den Pfeil neben **Bestellung** um tiefer zu bohren.

![Journey Optimizer](./images/oc74.png)

Klicken Sie auf **+** Symbol neben **Preis gesamt** , um dies zur Arbeitsfläche hinzuzufügen.

![Journey Optimizer](./images/oc75.png)

Dann wirst du das haben. Löschen Sie jetzt die zweite **xxx** in Ihrem HTML-Code.

![Journey Optimizer](./images/oc76.png)

Klicken Sie auf **+** Symbol neben **Preis gesamt** erneut, um dies zur Arbeitsfläche hinzuzufügen.

![Journey Optimizer](./images/oc77.png)

Sie können auch das Feld hinzufügen **Währung** innerhalb von **Bestellung** -Objekt auf die Arbeitsfläche, wie Sie hier sehen können.
Wenn Sie fertig sind, klicken Sie auf **Speichern** , um Ihre Änderungen zu speichern.

![Journey Optimizer](./images/oc771.png)

Sie sind dann wieder in Email Designer. Klicken **Speichern** erneut.

![Journey Optimizer](./images/oc78.png)

Gehen Sie zum Nachrichten-Dashboard zurück, indem Sie auf die Schaltfläche **Pfeil** neben dem Betreffzeilentext in der oberen linken Ecke.

![Journey Optimizer](./images/oc79.png)

Klicken Sie auf den Pfeil in der oberen linken Ecke, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/oc79a.png)

Klicken **Ok** um Ihre E-Mail-Aktion zu schließen.

![Journey Optimizer](./images/oc79b.png)

Klicken **Veröffentlichen** um Ihre Journey zu veröffentlichen.

![Journey Optimizer](./images/oc511.png)

Klicken **Veröffentlichen** erneut.

![Journey Optimizer](./images/oc512.png)

Ihre Journey ist jetzt veröffentlicht.

![Journey Optimizer](./images/oc513.png)

## 10.1.5 Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft aktualisieren

Navigieren Sie zu [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/launch/) und wählen Sie **Tags**.

Dies ist die Seite mit den Eigenschaften der Adobe Experience Platform-Datenerfassung , die Sie zuvor gesehen haben.

![Eigenschaften-Seite](../module1/images/launch1.png)

In Modul 0 hat Demo System zwei Client-Eigenschaften für Sie erstellt: eine für die Website und eine für die mobile App. Suchen Sie sie, indem Sie nach `--demoProfileLdap--` im **[!UICONTROL Suche]** ankreuzen. Klicken Sie auf , um die **Web** -Eigenschaft.

![Suchfeld](../module1/images/property6.png)

Navigieren Sie zu **Datenelemente**. Datenelement durchsuchen und öffnen **XDM - Kauf**.

![Journey Optimizer](./images/oc91.png)

Dann wirst du das sehen. Navigieren Sie zum Feld **_experience.campaign.orchestration.eventID** und geben Sie hier Ihre eventID ein. Die hier auszufüllende eventID ist die eventID, die Sie im Rahmen von Übung 10.1.2 erstellt haben. Klicken Sie auf **Speichern** oder **In Bibliothek speichern**.

![Journey Optimizer](./images/oc92.png)

Speichern Sie Ihre Änderungen in Ihrer Client-Eigenschaft und veröffentlichen Sie dann Ihre Änderungen, indem Sie Ihre Entwicklungsbibliothek aktualisieren.

![Journey Optimizer](./images/oc93.png)

Ihre Änderungen sind jetzt bereitgestellt und können getestet werden.

## 10.1.6 Testen Sie Ihre Bestätigungs-E-Mail mit der Demo-Website.

Testen wir die aktualisierte Journey, indem wir ein Produkt auf der Demowebsite kaufen.

Navigieren Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](../module0/images/web8.png)

Im **Screens** Seite, klicken Sie auf **Ausführen**.

![DSN](../module1/images/web2.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../module0/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](../module0/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../module0/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../module0/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../module0/images/web7.png)

Klicken Sie auf das Symbol für das Adobe-Logo oben links im Bildschirm, um den Profilanzeige zu öffnen.

![Demo](../module2/images/pv1.png)

Sehen Sie sich das Bedienfeld Profil-Viewer und das Echtzeit-Kundenprofil mit dem **Experience Cloud-ID** als primäre Kennung für diesen derzeit unbekannten Kunden.

![Demo](../module2/images/pv2.png)

Gehen Sie zur Seite Registrieren/Anmelden . Klicken **KONTO ERSTELLEN**.

![Demo](../module2/images/pv9.png)

Füllen Sie Ihre Details aus und klicken Sie auf **registrieren** Danach werden Sie zur vorherigen Seite weitergeleitet.

![Demo](../module2/images/pv10.png)

Fügen Sie Ihrem Warenkorb ein Produkt hinzu und wechseln Sie zur **Warenkorb** Seite. Klicken **Begeben Sie sich zum Checkout**.

![Journey Optimizer](./images/cart1.png)

Überprüfen Sie anschließend die Felder auf der Checkout-Seite und klicken Sie auf **Checkout**.

![Journey Optimizer](./images/cart2.png)

Sie erhalten dann Ihre Bestätigungs-E-Mail innerhalb von Sekunden.

![Journey Optimizer](./images/oc98.png)

Du hast diese Übung beendet.

Nächster Schritt: [10.2 Batch-basierte Newsletter-Journey konfigurieren](./ex2.md)

[Zurück zu Modul 10](./journeyoptimizer.md)

[Zu allen Modulen zurückkehren](../../overview.md)
