---
title: Adobe Journey Optimizer - Einrichten und Verwenden von Push-Benachrichtigungen für iOS
description: Einrichten und Verwenden von Push-Benachrichtigungen für iOS
kt: 5342
doc-type: tutorial
exl-id: a49fa91c-5235-4814-94c1-8dcdec6358c5
source-git-commit: c531412a2c0a5c216f49560e01fb26b9b7e71869
workflow-type: tm+mt
source-wordcount: '1802'
ht-degree: 6%

---

# 3.4.4 Einrichten und Verwenden von Push-Benachrichtigungen für iOS

Um Push-Benachrichtigungen mit Adobe Journey Optimizer verwenden zu können, müssen Sie eine Reihe von Einstellungen überprüfen und darüber Bescheid wissen.

Im Folgenden finden Sie alle zu überprüfenden Einstellungen:

- Datensätze und Schemata in Adobe Experience Platform
- Datenstrom für Mobilgeräte
- Datenerfassungseigenschaft für Mobilgeräte
- Programmoberfläche für Push-Zertifikate
- Testen des Push-Setups mit AEP Assurance

Sehen wir uns diese einzeln an.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

## Push-Datensätze 3.4.4.1

Adobe Journey Optimizer verwendet Datensätze, um Dinge wie die Push-Token von Mobilgeräten oder Interaktionen mit Push-Nachrichten (z. B.: gesendete Nachricht, geöffnete Nachricht usw.) in einem Datensatz in Adobe Journey Optimizer zu speichern.

Diese Datensätze finden Sie unter **[!UICONTROL Datensätze]** im Menü auf der linken Bildschirmseite. Um Systemdatensätze anzuzeigen, klicken Sie auf das Filtersymbol.

![Datenaufnahme](./images/menudsjo.png)

Aktivieren Sie die Option **Systemdatensätze anzeigen** und suchen Sie nach **AJO**. Anschließend werden die für Push-Benachrichtigungen verwendeten Datensätze angezeigt.

![Datenaufnahme](./images/menudsjo1.png)

## 3.4.4.2 für Mobilgeräte

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

Gehen Sie im linken Menü zu **[!UICONTROL Datenstrom]** und suchen Sie nach Ihrem Datenstrom, den Sie in [Übung 0.2](./../../../modules/gettingstarted/gettingstarted/ex2.md) erstellt haben, der `--aepUserLdap-- - Demo System Datastream (Mobile)` heißt. Klicken, um sie zu öffnen.

![Klicken Sie im linken Navigationsbereich auf das Datenstrom -Symbol](./images/edgeconfig1a.png)

Klicken Sie **{**}Adobe Experience Platform **-Service auf Bearbeiten.**

![Klicken Sie im linken Navigationsbereich auf das Datenstrom -Symbol](./images/edgeconfig1.png)

Anschließend werden die definierten Datenstromeinstellungen angezeigt und Sie erfahren, in welchen Datensätzen Ereignisse und Profilattribute gespeichert werden.

![Benennen Sie den Datenstrom und speichern Sie ihn](./images/edgeconfig2.png)

Es sind keine Änderungen erforderlich, Ihr Datenstrom kann jetzt in Ihrer Datenerfassungs-Client-Eigenschaft für Mobilgeräte verwendet werden.

## 3.4.4.3 Überprüfen der Datenerfassungseigenschaft für Mobilgeräte

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Im Rahmen von [Übung 0.1](./../../../modules/gettingstarted/gettingstarted/ex1.md) wurden zwei Datenerfassungseigenschaften erstellt.
Sie haben diese Datenerfassungs-Client-Eigenschaften bereits als Teil früherer Module verwendet.

Klicken Sie, um die Datenerfassungseigenschaft für Mobilgeräte zu öffnen.

![DSN](./images/launchprop.png)

Wechseln Sie in Ihrer Datenerfassungseigenschaft zu **Erweiterungen**. Anschließend werden die verschiedenen Erweiterungen angezeigt, die für die Mobile App erforderlich sind. Klicken Sie, um das **Adobe Experience Platform-Edge Network der Erweiterung zu**.

![Adobe Experience Platform – Datenerfassung](./images/launchprop1.png)

Anschließend sehen Sie, dass Ihr Datenstrom für Mobilgeräte hier verknüpft ist. Klicken Sie anschließend auf **Abbrechen**, um zur Übersicht über Ihre Erweiterungen zurückzukehren.

![Adobe Experience Platform – Datenerfassung](./images/launchprop2.png)

Dann bist du wieder hier. Assurance Es wird die Erweiterung für „AEP **&quot;**. Mit AEP Assurance können Sie die Datenerfassung und die Bereitstellung von Erlebnissen in Ihrer Mobile App untersuchen, testen, simulieren und validieren. Weitere Informationen zu AEP Assurance und Project Griffon finden Sie hier [https://aep-sdks.gitbook.io/docs/beta/project-griffon](https://aep-sdks.gitbook.io/docs/beta/project-griffon).

![Adobe Experience Platform – Datenerfassung](./images/launchprop8.png)

Klicken Sie anschließend auf **Konfigurieren**, um die Erweiterung **Adobe Journey Optimizer** zu öffnen.

![Adobe Experience Platform – Datenerfassung](./images/launchprop9.png)

Anschließend sehen Sie, dass hier der Datensatz für das Tracking von Push-Ereignissen verknüpft ist.

![Adobe Experience Platform – Datenerfassung](./images/launchprop10.png)

Sie müssen keine Änderungen an Ihrer Datenerfassungseigenschaft vornehmen.

## 3.4.4.4 Überprüfen der Einrichtung der Programmoberfläche

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Gehen Sie im linken Menü zu **App-Oberflächen** und öffnen Sie die Programmoberfläche für **DX Demo App APNS**.

![Adobe Experience Platform – Datenerfassung](./images/appsf.png)

Anschließend wird die konfigurierte Programmoberfläche für iOS und Android angezeigt.

![Adobe Experience Platform – Datenerfassung](./images/appsf1.png)

## 3.4.4.5 Testen Sie die Einrichtung der Push-Benachrichtigung mithilfe von AEP Assurance.

Sobald die App installiert ist, finden Sie sie auf dem Startbildschirm Ihres Geräts. Klicken Sie auf das Symbol, um die App zu öffnen.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn1.png)

Wenn Sie die App zum ersten Mal verwenden, werden Sie aufgefordert, sich mit Ihrer Adobe ID anzumelden. Schließen Sie den Anmeldevorgang ab.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn2.png)

Nach der Anmeldung wird eine Benachrichtigung angezeigt, in der Sie um Ihre Erlaubnis zum Senden von Benachrichtigungen gebeten werden. Wir senden Benachrichtigungen im Rahmen des Tutorials. Klicken Sie daher auf **Zulassen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn3.png)

Anschließend wird die Startseite der App angezeigt. Navigieren Sie zu **Einstellungen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn4.png)

In den Einstellungen wird angezeigt, dass derzeit ein &quot;**Projekt** in der App geladen ist. Klicken Sie auf **Benutzerdefiniertes Projekt**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn5.png)

Sie können jetzt ein benutzerdefiniertes Projekt laden. Klicken Sie auf den QR-Code, um Ihr Projekt einfach zu laden.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn6.png)

Nach Übung 0.1 hatten Sie dieses Ergebnis. Klicken Sie hier, um das **Mobile-Einzelhandelsprojekt** zu öffnen, das für Sie erstellt wurde.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/dsn5b.png)

Falls Sie Ihr Browser-Fenster versehentlich geschlossen haben oder zukünftige Demo- oder Aktivierungssitzungen geplant sind, können Sie unter [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects) auch auf Ihr Website-Projekt zugreifen. Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf Ihr Mobile-App-Projekt, um es zu öffnen.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8a.png)

Sie werden es dann sehen. Klicken Sie auf **Integrationen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8aa.png)

Sie müssen die Datenerfassungseigenschaft für Mobilgeräte auswählen, die in Übung 0.1 erstellt wurde. Klicken Sie anschließend auf **Ausführen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8b.png)

Sie sehen dann dieses Popup, das einen QR-Code enthält. Scannen Sie diesen QR-Code aus der mobilen App heraus.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8c.png)

Anschließend wird Ihre Projekt-ID in der App angezeigt, wonach Sie auf &quot;**&quot;** können.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn7.png)

Gehen Sie nun zurück zu **Startseite** in der App. Ihre App kann jetzt verwendet werden.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn8.png)

Sie müssen jetzt einen QR-Code scannen, um Ihr Mobilgerät mit Ihrer AEP Assurance-Sitzung zu verbinden.

Um eine AEP Assurance-Sitzung zu starten, navigieren Sie zu [https://experience.adobe.com/#/@experienceplatform/griffon](https://experience.adobe.com/#/@experienceplatform/griffon). Klicken Sie **Sitzung erstellen**.

![Adobe Experience Platform – Datenerfassung](./images/griffon3.png)

Klicken Sie auf **Starten**.

![Adobe Experience Platform – Datenerfassung](./images/griffon5.png)

Füllen Sie die Werte aus:

- Sitzungsname: Verwenden Sie `--aepUserLdap-- - push debugging` und ersetzen Sie ldap durch Ihren ldap
- Basis-URL: **dxdemo://default**

Klicken Sie auf **Weiter**.

![Adobe Experience Platform – Datenerfassung](./images/griffon4.png)

Daraufhin wird ein QR-Code auf dem Bildschirm angezeigt, den Sie mit Ihrem iOS-Gerät scannen sollten.

![Adobe Experience Platform – Datenerfassung](./images/griffon6.png)

Öffnen Sie auf Ihrem Mobilgerät die Kamera-App und scannen Sie den QR-Code, der von AEP Assurance angezeigt wird.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest8a.png)

Daraufhin wird ein Popup-Fenster angezeigt, in dem Sie aufgefordert werden, den PIN-Code einzugeben. Kopieren Sie den PIN-Code aus Ihrem AEP Assurance-Bildschirm und klicken Sie auf **Verbinden**.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest9.png)

Sie werden es dann sehen.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest11.png)

In AEP Assurance sehen Sie jetzt, dass ein Gerät zur AEP Assurance-Sitzung hinzugefügt wird.

![Adobe Experience Platform – Datenerfassung](./images/griffon7.png)

Navigieren Sie zu **Push-**. Sie werden so etwas sehen.

![Adobe Experience Platform – Datenerfassung](./images/griffon10.png)

Eine Erklärung:

- Die erste Spalte, **Client**, zeigt die verfügbaren IDs auf Ihrem iOS-Gerät. Es werden eine ECID und ein Push-Token angezeigt.
- Die zweite Spalte zeigt **Profil**-Informationen mit zusätzlichen Informationen darüber, in welcher Plattform das Push-Token lebt (APNS oder APNSSandbox). Wenn Sie auf die Schaltfläche **Inspect** klicken, gelangen Sie zu Adobe Experience Platform und Sie sehen das vollständige Echtzeit-Kundenprofil.
- Die dritte Spalte zeigt die **App-Konfiguration**, die im Rahmen der Übung **3.4.5.4 Erstellen der App-Konfiguration in Launch eingerichtet wurde**

Um die Einrichtung Ihrer Push-Konfiguration zu testen, klicken Sie auf die Schaltfläche **Push-Benachrichtigung senden**.

![Adobe Experience Platform – Datenerfassung](./images/griffon11.png)

Stellen Sie sicher, dass die **DX Demo**-App nicht geöffnet ist, wenn Sie auf die Schaltfläche **Push-Benachrichtigung senden** klicken. Wenn die App geöffnet ist, wird die Push-Benachrichtigung möglicherweise im Hintergrund empfangen und nicht angezeigt.

Anschließend wird eine Push-Benachrichtigung wie diese auf Ihrem Mobilgerät angezeigt.

![Adobe Experience Platform – Datenerfassung](./images/ipadPush2.png)

Wenn Sie die Push-Benachrichtigung erhalten haben, bedeutet dies, dass Ihre Einrichtung korrekt ist und einwandfrei funktioniert.

## 3.4.4.6 Neues Ereignis erstellen

Wechseln Sie im Menü zu **Journey-Administration** und klicken Sie auf **Verwalten** unter **Ereignisse**.

![ACOP](./images/acopmenu.png)

Auf dem **Ereignisse** wird eine ähnliche Ansicht angezeigt. Klicken Sie **Ereignis erstellen**.

![ACOP](./images/add.png)

Anschließend wird eine leere Ereigniskonfiguration angezeigt.

![ACOP](./images/emptyevent.png)

Geben Sie Ihrem Ereignis zunächst einen Namen wie den folgenden: `--aepUserLdap--StoreEntryEvent` und legen Sie die Beschreibung auf `Store Entry Event` fest.

![ACOP](./images/eventname.png)

Als Nächstes sehen Sie **Auswahl** Ereignistyp). Wählen Sie **Unitär** aus.

![ACOP](./images/eventidtype1.png)

Als Nächstes sehen Sie die Auswahl **Ereignis-ID-**). Wählen Sie **Systemgeneriert**

![ACOP](./images/eventidtype.png)

Als Nächstes sehen Sie die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Verwenden Sie das Schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nach Auswahl des Schemas werden Sie eine Reihe von Feldern sehen, die im Abschnitt **Payload** ausgewählt sind. Ihr Ereignis ist jetzt vollständig konfiguriert.

![ACOP](./images/eventpayload.png)

Sie sollten das dann sehen. Klicken Sie auf **Speichern**.

![ACOP](./images/eventsave.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert. Klicken Sie erneut auf Ihr Ereignis, um den Bildschirm **Ereignis bearbeiten** erneut zu öffnen.

![ACOP](./images/eventdone.png)

Bewegen Sie den Mauszeiger über **Feld** Payload“ und klicken Sie auf das Symbol **Payload anzeigen**.

![ACOP](./images/hover.png)

Im Folgenden sehen Sie ein Beispiel für die erwartete Payload.

![ACOP](./images/fullpayload.png)

Ihr Ereignis verfügt über eine eindeutige Orchestrierungs-eventID, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID` sehen.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, um die Journey, die Sie im nächsten Schritt erstellen, zum Trigger zu bringen. Notieren Sie sich diese eventID, da Sie sie im nächsten Schritt benötigen werden.
`"eventID": "e3a8f0bdc0b609667cd96a72a6b1e5aafa0ddaf6ccf121c574e6a2030860a633"`

Klicken Sie **OK** gefolgt von **Abbrechen**.

## 3.4.4.7 Erstellen einer Journey

Wechseln Sie im Menü zu **Journey** und klicken Sie auf **Journey erstellen**.

![DSN](./images/sjourney1.png)

Sie werden es dann sehen. Geben Sie Ihrem Journey einen Namen. Verwenden Sie `--aepUserLdap-- - Store Entry journey`. Klicken Sie auf **OK**.

![DSN](./images/sjourney3.png)

Zunächst müssen Sie Ihr Ereignis als Ausgangspunkt Ihres Journey hinzufügen. Suchen Sie nach Ihrer `--aepUserLdap--StoreEntryEvent` und ziehen Sie sie per Drag-and-Drop auf die Arbeitsfläche. Klicken Sie auf **OK**.

![DSN](./images/sjourney4.png)

Suchen Sie als Nächstes unter **Aktionen** nach der **Push**-Aktion.
Ziehen Sie die Aktion **Push** per Drag-and-Drop auf die Arbeitsfläche.

![DSN](./images/sjourney5.png)

Legen Sie die **Kategorie** auf **Marketing** fest und wählen Sie eine Push-Oberfläche aus, mit der Sie Push-Benachrichtigungen senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **Push-iOS-Android**.

![ACOP](./images/journeyactions1push.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2push.png)

Sie werden es dann sehen. Klicken Sie auf **Personalisierung** für das Feld **Titel**.

![Push-Benachrichtigung](./images/bp5.png)

Sie werden es dann sehen. Sie können jetzt jedes Profilattribut direkt aus dem Echtzeit-Kundenprofil auswählen.

![Push-Benachrichtigung](./images/bp6.png)

Suchen Sie nach dem Feld **Vorname** und klicken Sie dann auf das Symbol **+** neben dem Feld **Vorname**. Anschließend wird das Personalisierungs-Token für Vorname hinzugefügt: **{{profile.person.name.firstName}}**.

![Push-Benachrichtigung](./images/bp9.png)

Als Nächstes fügen Sie den Text **hinzu, willkommen in unserem Shop!** hinter **{{profile.person.name.firstName}}**.

Klicken Sie auf **Speichern**.

![Push-Benachrichtigung](./images/bp10.png)

Jetzt hast du das. Klicken Sie auf **Personalisierung** für das Feld **Hauptteil**.

![Push-Benachrichtigung](./images/bp11.png)

Geben Sie diesen Text ein **Klicken Sie hier, um einen Rabatt von 10 % zu erhalten, wenn Sie heute kaufen!** und klicken Sie auf **Speichern**.

![Push-Benachrichtigung](./images/bp12.png)

Dann hast du das hier. Klicken Sie auf den Pfeil oben links, um zu Ihrem Journey zurückzukehren.

![Journey Optimizer](./images/bp12a.png)

Klicken Sie auf **OK**, um die Push-Aktion zu schließen.

![DSN](./images/sjourney8.png)

Klicken Sie auf **Veröffentlichen**.

![DSN](./images/sjourney10.png)

Klicken Sie erneut auf **** Publish.

![DSN](./images/sjourney10a.png)

Ihr Journey ist jetzt veröffentlicht.

![DSN](./images/sjourney11.png)

## 3.4.4.8 Testen von Journey- und Push-Nachrichten

Rufen Sie in Ihrer DX Demo 2.0-Mobile-App den Bildschirm &quot;**&quot;**. Klicken Sie auf **Schaltfläche** Store-Eintrag“.

>[!NOTE]
>
>Die **Store Entry**-Schaltfläche wird derzeit implementiert. Sie werden sie noch nicht in der App finden.

![DSN](./images/demo1b.png)

Stellen Sie sicher, dass Sie die App sofort schließen, nachdem Sie auf **Store-Eintrag**-Symbol geklickt haben, da sonst die Push-Nachricht nicht angezeigt wird.

![DSN](./images/demo2.png)

Nach einigen Sekunden wird die Meldung angezeigt.

![DSN](./images/demo3.png)

Du hast diese Übung beendet.

Nächster Schritt: [3.4.5 Erstellen einer Geschäftsereignis-Journey](./ex5.md)

[Zurück zum Modul 3.4](./journeyoptimizer.md)

[Zurück zu „Alle Module“](../../../overview.md)
