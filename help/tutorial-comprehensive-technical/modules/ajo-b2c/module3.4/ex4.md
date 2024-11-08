---
title: Adobe Journey Optimizer - Einrichten und Verwenden von Push-Benachrichtigungen für iOS
description: Push-Benachrichtigungen für iOS einrichten und verwenden
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '1831'
ht-degree: 6%

---

# 3.4.4 Push-Benachrichtigungen für iOS einrichten und verwenden

Um Push-Benachrichtigungen mit Adobe Journey Optimizer verwenden zu können, müssen Sie eine Reihe von Einstellungen festlegen.

Im Folgenden finden Sie alle zu überprüfenden Einstellungen:

- Datensätze und Schemata in Adobe Experience Platform
- Datenspeicher für Mobilgeräte
- Datenerfassungseigenschaft für Mobilgeräte
- App-Oberfläche für Push-Zertifikate
- Testen des Push-Setups mit AEP Assurance

Lasst uns diese einzeln überprüfen.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der Ansicht **Home** Ihrer Sandbox `--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

## 3.4.4.1 Push-Datensätze

Adobe Journey Optimizer verwendet Datensätze, um Dinge wie die Push-Token von Mobilgeräten oder Interaktionen mit Push-Nachrichten (z. B. gesendete Nachrichten, geöffnete Nachrichten usw.) in einem Datensatz in Adobe Journey Optimizer zu speichern.

Sie können diese Datensätze finden, indem Sie im Menü links auf Ihrem Bildschirm zu **[!UICONTROL Datensätze]** navigieren. Um Systemdatensätze anzuzeigen, klicken Sie auf das Filtersymbol.

![Datenaufnahme](./images/menudsjo.png)

Aktivieren Sie die Option **Systemdatensätze anzeigen** und suchen Sie nach **AJO**. Anschließend werden die für Push-Benachrichtigungen verwendeten Datensätze angezeigt.

![Datenaufnahme](./images/menudsjo1.png)

## 3.4.4.2 Datenspeicher für Mobilgeräte

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

Navigieren Sie im linken Menü zu **[!UICONTROL Datastream]** und suchen Sie nach Ihrem Datastream, den Sie in [Übung 0.2](./../../../modules/gettingstarted/gettingstarted/ex2.md) erstellt haben, der den Namen `--aepUserLdap-- - Demo System Datastream (Mobile)` trägt. Klicken Sie auf , um es zu öffnen.

![Klicken Sie auf das Datastraam-Symbol in der linken Navigation](./images/edgeconfig1a.png)

Klicken Sie im Dienst **Adobe Experience Platform** auf **Bearbeiten** .

![Klicken Sie auf das Datastraam-Symbol in der linken Navigation](./images/edgeconfig1.png)

Anschließend werden die definierten Datenspeichereinstellungen angezeigt, in denen Datensätze und Profilattribute gespeichert werden.

![Benennen Sie den Datastream und speichern Sie](./images/edgeconfig2.png)

Es sind keine Änderungen erforderlich. Ihr Datastream kann jetzt in Ihrer Datenerfassungs-Client-Eigenschaft für Mobile verwendet werden.

## 3.4.4.3 Überprüfen Sie Ihre Datenerfassungseigenschaft für Mobile

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Im Rahmen von [Übung 0.1](./../../../modules/gettingstarted/gettingstarted/ex1.md) wurden 2 Datenerfassungseigenschaften erstellt.
Sie haben diese Datenerfassungs-Client-Eigenschaften bereits als Teil früherer Module verwendet.

Klicken Sie auf , um die Datenerfassungseigenschaft für Mobilgeräte zu öffnen.

![DSN](./images/launchprop.png)

Wechseln Sie in der Datenerfassungseigenschaft zu **Erweiterungen**. Anschließend werden die verschiedenen Erweiterungen angezeigt, die für die mobile App erforderlich sind. Klicken Sie auf , um die Erweiterung **Adobe Experience Platform-Edge Network** zu öffnen.

![Adobe Experience Platform – Datenerfassung](./images/launchprop1.png)

Dann sehen Sie, dass Ihr Datastream für Mobilgeräte hier verknüpft ist. Klicken Sie anschließend auf **Abbrechen** , um zur Übersicht über Ihre Erweiterungen zurückzukehren.

![Adobe Experience Platform – Datenerfassung](./images/launchprop2.png)

Du wirst dann wieder hier sein. Sie sehen die Erweiterung für **AEP Assurance**. Mit AEP Assurance können Sie die Erfassung, den Testversand, die Simulation und die Validierung der Datenerfassung und der Bereitstellung von Erlebnissen in Ihrer App überprüfen. Weitere Informationen zu AEP Assurance und Project Griffon finden Sie hier [https://aep-sdks.gitbook.io/docs/beta/project-griffon](https://aep-sdks.gitbook.io/docs/beta/project-griffon).

![Adobe Experience Platform – Datenerfassung](./images/launchprop8.png)

Klicken Sie anschließend auf **Konfigurieren** , um die Erweiterung **Adobe Journey Optimizer** zu öffnen.

![Adobe Experience Platform – Datenerfassung](./images/launchprop9.png)

Dann sehen Sie, dass der Datensatz für die Verfolgung von Push-Ereignissen hier verknüpft ist.

![Adobe Experience Platform – Datenerfassung](./images/launchprop10.png)

Sie müssen keine Änderungen an Ihrer Datenerfassungseigenschaft vornehmen.

## 3.4.4.4 Einrichten der App-Oberfläche überprüfen

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Navigieren Sie im linken Menü zu **App-Oberflächen** und öffnen Sie die App-Oberfläche für **DX Demo App APNS**.

![Adobe Experience Platform – Datenerfassung](./images/appsf.png)

Anschließend wird die konfigurierte App-Oberfläche für iOS und Android angezeigt.

![Adobe Experience Platform – Datenerfassung](./images/appsf1.png)

## 3.4.4.5 Testen der Einrichtung von Push-Benachrichtigungen mit AEP Assurance

Sobald die App installiert ist, finden Sie sie auf dem Startbildschirm Ihres Geräts. Klicken Sie auf das Symbol, um die App zu öffnen.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn1.png)

Wenn Sie die App zum ersten Mal verwenden, werden Sie aufgefordert, sich mit Ihrer Adobe ID anzumelden. Schließen Sie den Anmeldevorgang ab.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn2.png)

Nach der Anmeldung wird eine Benachrichtigung angezeigt, in der Sie um Ihre Berechtigung zum Senden von Benachrichtigungen ersucht werden. Wir senden Benachrichtigungen als Teil des Tutorials. Klicken Sie daher auf **Zulassen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn3.png)

Sie sehen dann die Startseite der App. Wechseln Sie zu **Einstellungen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn4.png)

In den Einstellungen wird angezeigt, dass derzeit ein **öffentliches Projekt** in die App geladen ist. Klicken Sie auf **Benutzerdefiniertes Projekt**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn5.png)

Sie können jetzt ein benutzerdefiniertes Projekt laden. Klicken Sie auf den QR-Code, um Ihr Projekt einfach zu laden.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn6.png)

Nach Übung 0.1 hatten Sie dieses Ergebnis. Klicken Sie auf , um das für Sie erstellte Projekt **Mobile Retail** zu öffnen.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/dsn5b.png)

Falls Sie Ihr Browser-Fenster versehentlich geschlossen haben oder für zukünftige Demo- oder Aktivierungssitzungen, können Sie auch auf Ihr Website-Projekt zugreifen, indem Sie [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects) aufrufen. Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Mobile-App-Projekt, um es zu öffnen.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8a.png)

Dann wirst du das sehen. Klicken Sie auf **Integrationen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8aa.png)

Sie müssen die Datenerfassungseigenschaft für Mobilgeräte auswählen, die in Übung 0.1 erstellt wurde. Klicken Sie anschließend auf **Ausführen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8b.png)

Dann sehen Sie dieses Popup, das einen QR-Code enthält. Scannen Sie diesen QR-Code aus der Mobile App heraus.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8c.png)

Anschließend wird Ihre Projekt-ID in der App angezeigt. Anschließend können Sie auf **Speichern** klicken.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn7.png)

Gehen Sie in der App zurück zu **Home** . Ihre App kann jetzt verwendet werden.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/mobileappn8.png)

Sie müssen jetzt einen QR-Code scannen, um Ihr Mobilgerät mit Ihrer AEP Assurance-Sitzung zu verbinden.

Um eine AEP Assurance-Sitzung zu starten, gehen Sie zu [https://experience.adobe.com/#/@experienceplatform/griffon](https://experience.adobe.com/#/@experienceplatform/griffon). Klicken Sie auf **Sitzung erstellen**.

![Adobe Experience Platform – Datenerfassung](./images/griffon3.png)

Klicken Sie auf **Starten**.

![Adobe Experience Platform – Datenerfassung](./images/griffon5.png)

Füllen Sie die Werte aus:

- Sitzungsname: Verwenden Sie `--aepUserLdap-- - push debugging` und ersetzen Sie ldap durch Ihren ldap
- Basis-URL: Verwenden Sie **dxdemo://default**

Klicken Sie auf **Weiter**.

![Adobe Experience Platform – Datenerfassung](./images/griffon4.png)

Daraufhin wird auf Ihrem Bildschirm ein QR-Code angezeigt, den Sie mit Ihrem iOS-Gerät scannen sollten.

![Adobe Experience Platform – Datenerfassung](./images/griffon6.png)

Öffnen Sie auf Ihrem Mobilgerät die Kamera-App und scannen Sie den QR-Code, der von AEP Assurance angezeigt wird.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest8a.png)

Dann sehen Sie einen Popup-Bildschirm, in dem Sie aufgefordert werden, den PIN-Code einzugeben. Kopieren Sie den PIN-Code aus Ihrem AEP Assurance-Bildschirm und klicken Sie auf **Verbinden**.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest9.png)

Dann wirst du das sehen.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest11.png)

In AEP Assurance sehen Sie jetzt, dass ein Gerät zur AEP Assurance-Sitzung gehört.

![Adobe Experience Platform – Datenerfassung](./images/griffon7.png)

Wechseln Sie zu **Push Debug**. Du wirst so etwas sehen.

![Adobe Experience Platform – Datenerfassung](./images/griffon10.png)

Einige Erklärungen:

- Die erste Spalte, **Client**, zeigt die verfügbaren IDs auf Ihrem iOS-Gerät an. Es werden eine ECID und ein Push-Token angezeigt.
- Die zweite Spalte enthält Informationen zum **Profil** mit zusätzlichen Informationen zur Plattform, auf der sich das Push-Token befindet (APNS oder APNSSandbox). Wenn Sie auf die Schaltfläche **Inspect-Profil** klicken, gelangen Sie zu Adobe Experience Platform und das vollständige Echtzeit-Kundenprofil wird angezeigt.
- Die dritte Spalte zeigt die **App-Konfiguration**, die im Rahmen der Übung **3.4.5.4 Erstellen einer App-Konfiguration in Launch** eingerichtet wurde.

Um die Einrichtung der Push-Konfiguration zu testen, klicken Sie auf die Schaltfläche **Push-Benachrichtigung senden** .

![Adobe Experience Platform – Datenerfassung](./images/griffon11.png)

Sie müssen sicherstellen, dass die **DX Demo**-App nicht geöffnet ist, wenn Sie auf die Schaltfläche **Push-Benachrichtigung senden** klicken. Wenn die App geöffnet ist, wird die Push-Benachrichtigung möglicherweise im Hintergrund empfangen und nicht angezeigt.

Daraufhin wird auf Ihrem Mobilgerät eine Push-Benachrichtigung wie diese angezeigt.

![Adobe Experience Platform – Datenerfassung](./images/ipadPush2.png)

Wenn Sie die Push-Benachrichtigung erhalten haben, bedeutet dies, dass Ihr Setup korrekt ist und ordnungsgemäß funktioniert.

## 3.4.4.6 Neues Ereignis erstellen

Wechseln Sie im Menü zu **Journey Administration** und klicken Sie unter **-Ereignisse** auf **Verwalten** .

![ACOP](./images/acopmenu.png)

Auf dem Bildschirm **Ereignisse** wird eine Ansicht ähnlich der folgenden angezeigt. Klicken Sie auf **Ereignis erstellen**.

![ACOP](./images/add.png)

Anschließend wird eine leere Ereigniskonfiguration angezeigt.

![ACOP](./images/emptyevent.png)

Geben Sie zunächst Ihrem Ereignis einen Namen wie folgt: `--aepUserLdap--StoreEntryEvent` und legen Sie die Beschreibung auf `Store Entry Event` fest.

![ACOP](./images/eventname.png)

Als Nächstes wird die Auswahl **Ereignistyp** ausgewählt. Wählen Sie **Einzeln** aus.

![ACOP](./images/eventidtype1.png)

Als Nächstes wählen Sie den **Ereignis-ID-Typ** aus. Wählen Sie **System generiert** aus.

![ACOP](./images/eventidtype.png)

Als Nächstes folgt die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Verwenden Sie das Schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nach Auswahl des Schemas werden im Abschnitt **Payload** eine Reihe von Feldern ausgewählt. Ihr Ereignis ist jetzt vollständig konfiguriert.

![ACOP](./images/eventpayload.png)

Dann sollten Sie das sehen. Klicken Sie auf **Speichern**.

![ACOP](./images/eventsave.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert. Klicken Sie erneut auf Ihr Ereignis, um den Bildschirm **Ereignis bearbeiten** erneut zu öffnen.

![ACOP](./images/eventdone.png)

Bewegen Sie den Mauszeiger über das Feld **Payload** und klicken Sie auf das Symbol **Payload anzeigen** .

![ACOP](./images/hover.png)

Sie sehen nun ein Beispiel der erwarteten Payload.

![ACOP](./images/fullpayload.png)

Ihr Ereignis verfügt über eine eindeutige eventID für die Orchestrierung, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID` sehen.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, um die Journey Trigger, die Sie im nächsten Schritt erstellen werden. Notieren Sie sich diese eventID, da Sie sie im nächsten Schritt benötigen werden.
`"eventID": "e3a8f0bdc0b609667cd96a72a6b1e5aafa0ddaf6ccf121c574e6a2030860a633"`

Klicken Sie auf **OK**, gefolgt von **Abbrechen**.

## 3.4.4.7 Journey erstellen

Wechseln Sie im Menü zu **Journey** und klicken Sie auf **Journey erstellen**.

![DSN](./images/sjourney1.png)

Dann wirst du das sehen. Benennen Sie Ihre Journey. Verwenden Sie `--aepUserLdap-- - Store Entry journey`. Klicken Sie auf **OK**.

![DSN](./images/sjourney3.png)

Zunächst müssen Sie Ihr Ereignis als Ausgangspunkt Ihrer Journey hinzufügen. Suchen Sie nach Ihrem Ereignis `--aepUserLdap--StoreEntryEvent` und ziehen Sie es auf die Arbeitsfläche. Klicken Sie auf **OK**.

![DSN](./images/sjourney4.png)

Suchen Sie dann unter **Aktionen** nach der Aktion **Push** .
Ziehen Sie die Aktion **Push** auf die Arbeitsfläche.

![DSN](./images/sjourney5.png)

Setzen Sie die **Kategorie** auf **Marketing** und wählen Sie eine Push-Oberfläche aus, über die Sie Push-Benachrichtigungen senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **Push-iOS-Android**.

![ACOP](./images/journeyactions1push.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2push.png)

Dann wirst du das sehen. Klicken Sie auf das Symbol **personalization** für das Feld **Title** .

![Push-Benachrichtigung](./images/bp5.png)

Dann wirst du das sehen. Sie können jetzt jedes Profilattribut direkt aus dem Echtzeit-Kundenprofil auswählen.

![Push-Benachrichtigung](./images/bp6.png)

Suchen Sie nach dem Feld **Vorname** und klicken Sie dann auf das Symbol **+** neben dem Feld **Vorname**. Anschließend wird das Personalisierungstoken für Vorname hinzugefügt: **{{profile.person.name.firstName}}**.

![Push-Benachrichtigung](./images/bp9.png)

Als Nächstes fügen Sie den Text **, willkommen in unserem Geschäft!** hinter **{{profile.person.name.firstName}}**.

Klicken Sie auf **Speichern**.

![Push-Benachrichtigung](./images/bp10.png)

Das hast du jetzt. Klicken Sie auf das Symbol **personalization** für das Feld **body** .

![Push-Benachrichtigung](./images/bp11.png)

Geben Sie diesen Text ein **Klicken Sie hier, um einen 10% Rabatt zu erhalten, wenn Sie heute kaufen!** und klicken Sie auf **Speichern**.

![Push-Benachrichtigung](./images/bp12.png)

Dann wirst du das haben. Klicken Sie auf den Pfeil oben links, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/bp12a.png)

Klicken Sie auf **OK** , um Ihre Push-Aktion zu schließen.

![DSN](./images/sjourney8.png)

Klicken Sie auf **Veröffentlichen**.

![DSN](./images/sjourney10.png)

Klicken Sie erneut auf **Publish**.

![DSN](./images/sjourney10a.png)

Ihre Journey ist jetzt veröffentlicht.

![DSN](./images/sjourney11.png)

## 3.4.4.8 Journey und Push-Nachricht testen

Wechseln Sie in Ihrer DX Demo 2.0-Mobile App zum Bildschirm **Einstellungen** . Klicken Sie auf die Schaltfläche **Eintrag speichern** .

>[!NOTE]
>
>Die Schaltfläche **Eintrag speichern** wird derzeit implementiert. Sie werden es noch nicht in der App finden.

![DSN](./images/demo1b.png)

Schließen Sie die App sofort, nachdem Sie auf das Symbol **Eintrag speichern** geklickt haben. Andernfalls wird die Push-Nachricht nicht angezeigt.

![DSN](./images/demo2.png)

Nach einigen Sekunden wird die Nachricht angezeigt.

![DSN](./images/demo3.png)

Du hast diese Übung beendet.

Nächster Schritt: [3.4.5 Geschäftsereignis-Journey erstellen](./ex5.md)

[Zurück zu Modul 3.4](./journeyoptimizer.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
