---
title: Adobe Journey Optimizer - Einrichten und Verwenden von Push-Benachrichtigungen für iOS
description: Push-Benachrichtigungen für iOS einrichten und verwenden
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 14a2306a-eb2f-47ee-ad3c-1169412811ca
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1841'
ht-degree: 6%

---

# 10.4 Push-Benachrichtigungen für iOS einrichten und verwenden

Um Push-Benachrichtigungen mit Adobe Journey Optimizer verwenden zu können, müssen Sie eine Reihe von Einstellungen festlegen.

Im Folgenden finden Sie alle zu überprüfenden Einstellungen:

- Datensätze und Schemata in Adobe Experience Platform
- Datenspeicher für Mobilgeräte
- Datenerfassungseigenschaft für Mobilgeräte
- App-Oberfläche für Push-Zertifikate
- Testen Sie Ihr Push-Setup mit AEP Assurance.

Lasst uns diese einzeln überprüfen.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxId--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 10.4.1 Push-Datensätze

Adobe Journey Optimizer verwendet Datensätze, um Dinge wie Push-Token von Mobilgeräten oder Interaktionen mit Push-Nachrichten zu speichern (z. B.: Nachricht gesendet, Nachricht geöffnet usw.) in einem Datensatz in Adobe Journey Optimizer gespeichert.

Sie können diese Datensätze finden, indem Sie **[!UICONTROL Datensätze]** im Menü auf der linken Bildschirmseite. Um Systemdatensätze anzuzeigen, klicken Sie auf das Filtersymbol.

![Datenaufnahme](./images/menudsjo.png)

Aktivieren Sie die Option **Anzeigen von Systemdatensätzen** und suchen Sie nach **AJO**. Anschließend werden die für Push-Benachrichtigungen verwendeten Datensätze angezeigt.

![Datenaufnahme](./images/menudsjo1.png)

## 10.4.2 Datenspeicher für Mobilgeräte

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

Gehen Sie im linken Menü zu **[!UICONTROL Datastream]** und suchen Sie nach Ihrem Datenspeicher, den Sie in erstellt haben. [Übung 0.2](./../module0/ex2.md), der `--demoProfileLdap-- - Demo System Datastream (Mobile)`. Klicken Sie auf , um es zu öffnen.

![Klicken Sie im linken Navigationsbereich auf das Symbol Datastream .](./images/edgeconfig1a.png)

Klicken **Bearbeiten** auf **Adobe Experience Platform** Dienst.

![Klicken Sie im linken Navigationsbereich auf das Symbol Datastream .](./images/edgeconfig1.png)

Anschließend werden die definierten Datenspeichereinstellungen angezeigt, in denen Datensätze und Profilattribute gespeichert werden.

![Benennen Sie den Datastream und speichern Sie ihn.](./images/edgeconfig2.png)

Es sind keine Änderungen erforderlich. Ihr Datastream kann jetzt in Ihrer Datenerfassungs-Client-Eigenschaft für Mobile verwendet werden.

## 10.4.3 Überprüfen Sie Ihre Datenerfassungseigenschaft für Mobile

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Als Teil von [Übung 0.1](./../module0/ex1.md), wurden 2 Datenerfassungseigenschaften erstellt.
Sie haben diese Datenerfassungs-Client-Eigenschaften bereits als Teil früherer Module verwendet.

Klicken Sie auf , um die Datenerfassungseigenschaft für Mobilgeräte zu öffnen.

![DSN](./images/launchprop.png)

Navigieren Sie in der Datenerfassungseigenschaft zu **Erweiterungen**. Anschließend werden die verschiedenen Erweiterungen angezeigt, die für die mobile App erforderlich sind. Klicken Sie auf , um die Erweiterung zu öffnen. **Adobe Experience Platform Edge Network**.

![Adobe Experience Platform – Datenerfassung](./images/launchprop1.png)

Dann sehen Sie, dass Ihr Datastream für Mobilgeräte hier verknüpft ist. Klicken Sie anschließend auf **Abbrechen** , um zur Übersicht über Ihre Erweiterungen zurückzukehren.

![Adobe Experience Platform – Datenerfassung](./images/launchprop2.png)

Du wirst dann wieder hier sein. Sie sehen die Erweiterung für **AEP Assurance**. Mit AEP Assurance können Sie die Datenerfassung und Bereitstellung von Erlebnissen in Ihrer App überprüfen, testen, simulieren und überprüfen. Weitere Informationen zu AEP Assurance und Project Griffon finden Sie hier . [https://aep-sdks.gitbook.io/docs/beta/project-griffon](https://aep-sdks.gitbook.io/docs/beta/project-griffon).

![Adobe Experience Platform – Datenerfassung](./images/launchprop8.png)

Klicken Sie anschließend auf **Konfigurieren** , um die Erweiterung zu öffnen **Adobe Journey Optimizer**.

![Adobe Experience Platform – Datenerfassung](./images/launchprop9.png)

Dann sehen Sie, dass der Datensatz für die Verfolgung von Push-Ereignissen hier verknüpft ist.

![Adobe Experience Platform – Datenerfassung](./images/launchprop10.png)

Sie müssen keine Änderungen an Ihrer Datenerfassungseigenschaft vornehmen.

## 10.4.4 Einrichten der App-Oberfläche überprüfen

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Gehen Sie im linken Menü zu **App-Oberflächen** und &quot;open&quot;, die App-Oberfläche für **DX Demo App-APNS**.

![Adobe Experience Platform – Datenerfassung](./images/appsf.png)

Anschließend wird die konfigurierte App-Oberfläche für iOS und Android angezeigt.

![Adobe Experience Platform – Datenerfassung](./images/appsf1.png)

## 10.4.5 Testen der Einrichtung von Push-Benachrichtigungen mithilfe von AEP Assurance.

Sobald die App installiert ist, finden Sie sie auf dem Startbildschirm Ihres Geräts. Klicken Sie auf das Symbol , um die App zu öffnen.

![DSN](../module0/images/mobileappn1.png)

Wenn Sie die App zum ersten Mal verwenden, werden Sie aufgefordert, sich mit Ihrer Adobe ID anzumelden. Schließen Sie den Anmeldevorgang ab.

![DSN](../module0/images/mobileappn2.png)

Nach der Anmeldung wird eine Benachrichtigung angezeigt, in der Sie um Ihre Berechtigung zum Senden von Benachrichtigungen ersucht werden. Wir senden Benachrichtigungen im Rahmen des Tutorials. Klicken Sie daher auf **Zulassen**.

![DSN](../module0/images/mobileappn3.png)

Sie sehen dann die Startseite der App. Navigieren Sie zu **Einstellungen**.

![DSN](../module0/images/mobileappn4.png)

In den Einstellungen sehen Sie, dass derzeit ein **Öffentliches Projekt** in die App geladen wird. Klicken **Benutzerdefiniertes Projekt**.

![DSN](../module0/images/mobileappn5.png)

Sie können jetzt ein benutzerdefiniertes Projekt laden. Klicken Sie auf den QR-Code, um Ihr Projekt einfach zu laden.

![DSN](../module0/images/mobileappn6.png)

Nach Übung 0.1 hatten Sie dieses Ergebnis. Klicken Sie auf , um die **Mobiles Einzelhandelsprojekt** die für Sie erstellt wurde.

![DSN](../module0/images/dsn5b.png)

Falls Sie Ihr Browser-Fenster versehentlich geschlossen haben oder für zukünftige Demo- oder Aktivierungssitzungen, können Sie auch auf Ihr Website-Projekt zugreifen, indem Sie [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Mobile-App-Projekt, um es zu öffnen.

![DSN](../module0/images/web8a.png)

Dann wirst du das sehen. Klicken **Integrationen**.

![DSN](../module0/images/web8aa.png)

Wählen Sie die Datenerfassungseigenschaft für Mobilgeräte aus, die in Übung 0.1 erstellt wurde. Klicken Sie anschließend auf **Ausführen**.

![DSN](../module0/images/web8b.png)

Dann sehen Sie dieses Popup, das einen QR-Code enthält. Scannen Sie diesen QR-Code aus der Mobile App heraus.

![DSN](../module0/images/web8c.png)

Anschließend wird Ihre Projekt-ID in der App angezeigt. Anschließend können Sie auf **Speichern**.

![DSN](../module0/images/mobileappn7.png)

Gehen Sie zurück zu **Startseite** in der App. Ihre App kann jetzt verwendet werden.

![DSN](../module0/images/mobileappn8.png)

Sie müssen jetzt einen QR-Code scannen, um Ihr mobiles Gerät mit Ihrer AEP Assurance-Sitzung zu verbinden.

Um eine AEP Assurance-Sitzung zu starten, gehen Sie zu [https://experience.adobe.com/#/@experienceplatform/griffon](https://experience.adobe.com/#/@experienceplatform/griffon). Klicken **Sitzung erstellen**.

![Adobe Experience Platform – Datenerfassung](./images/griffon3.png)

Klicken Sie auf **Starten**.

![Adobe Experience Platform – Datenerfassung](./images/griffon5.png)

Füllen Sie die Werte aus:

- Sitzungsname: use `--demoProfileLdap-- - push debugging` und ersetzen Sie ldap durch Ihren ldap
- Basis-URL: use **dxdemo://default**

Klicken Sie auf **Weiter**.

![Adobe Experience Platform – Datenerfassung](./images/griffon4.png)

Daraufhin wird auf Ihrem Bildschirm ein QR-Code angezeigt, den Sie mit Ihrem iOS-Gerät scannen sollten.

![Adobe Experience Platform – Datenerfassung](./images/griffon6.png)

Öffnen Sie auf Ihrem Mobilgerät die Kamera-App und scannen Sie den QR-Code, der von AEP Assurance angezeigt wird.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest8a.png)

Dann sehen Sie einen Popup-Bildschirm, in dem Sie aufgefordert werden, den PIN-Code einzugeben. Kopieren Sie den PIN-Code aus Ihrem AEP Assurance-Bildschirm und klicken Sie auf **Verbinden**.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest9.png)

Dann wirst du das sehen.

![Adobe Experience Platform – Datenerfassung](./images/ipadPushTest11.png)

In AEP Assurance sehen Sie jetzt, dass ein Gerät zur AEP Assurance-Sitzung gehört.

![Adobe Experience Platform – Datenerfassung](./images/griffon7.png)

Navigieren Sie zu **Push Debug**. Du wirst so etwas sehen.

![Adobe Experience Platform – Datenerfassung](./images/griffon10.png)

Einige Erklärungen:

- Die erste Spalte, **Client** zeigt die verfügbaren IDs auf Ihrem iOS-Gerät an. Es werden eine ECID und ein Push-Token angezeigt.
- Die zweite Spalte zeigt **Profil** Informationen mit zusätzlichen Informationen zur Plattform, auf der sich das Push-Token befindet (APNS oder APNSSandbox). Wenn Sie auf die **Inspect-Profil** -Schaltfläche, werden Sie zu Adobe Experience Platform weitergeleitet und erhalten das vollständige Echtzeit-Kundenprofil.
- Die dritte Spalte zeigt die **App-Konfiguration**, das im Rahmen der Übung eingerichtet wurde **10.5.4 App-Konfiguration in Launch erstellen**

Um die Einrichtung Ihrer Push-Konfiguration zu testen, klicken Sie auf das **Push-Benachrichtigung senden** Schaltfläche.

![Adobe Experience Platform – Datenerfassung](./images/griffon11.png)

Sie müssen sicherstellen, dass die Variable **DX Demo** Die App ist zum Zeitpunkt des Klicks auf die **Push-Benachrichtigung senden** Schaltfläche. Wenn die App geöffnet ist, wird die Push-Benachrichtigung möglicherweise im Hintergrund empfangen und nicht angezeigt.

Daraufhin wird auf Ihrem Mobilgerät eine Push-Benachrichtigung wie diese angezeigt.

![Adobe Experience Platform – Datenerfassung](./images/ipadPush2.png)

Wenn Sie die Push-Benachrichtigung erhalten haben, bedeutet dies, dass Ihr Setup korrekt ist und ordnungsgemäß funktioniert.

## 10.4.6 Neues Ereignis erstellen

Gehen Sie im Menü zu **Journey-Administration** und klicken Sie auf **Verwalten** under **Veranstaltungen**.

![ACOP](./images/acopmenu.png)

Im **Veranstaltungen** -Bildschirm angezeigt, sehen Sie eine ähnliche Ansicht. Klicken **Ereignis erstellen**.

![ACOP](./images/add.png)

Anschließend wird eine leere Ereigniskonfiguration angezeigt.

![ACOP](./images/emptyevent.png)

Geben Sie Ihrem Ereignis zunächst einen Namen wie den folgenden: `--demoProfileLdap--StoreEntryEvent` und legen Sie die Beschreibung auf `Store Entry Event`.

![ACOP](./images/eventname.png)

Als Nächstes folgt die **Ereignistyp** auswählen. Auswählen **Einzelfall**.

![ACOP](./images/eventidtype1.png)

Als Nächstes folgt die **Ereignis-ID-Typ** auswählen. Auswählen **Systemgeneriert**

![ACOP](./images/eventidtype.png)

Als Nächstes folgt die Schemaauswahl. Für diese Übung wurde ein Schema vorbereitet. Bitte verwenden Sie das Schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nach Auswahl des Schemas werden im **Nutzlast** Abschnitt. Ihr Ereignis ist jetzt vollständig konfiguriert.

![ACOP](./images/eventpayload.png)

Dann sollten Sie das sehen. Klicken Sie auf **Speichern**.

![ACOP](./images/eventsave.png)

Ihr Ereignis ist jetzt konfiguriert und gespeichert. Klicken Sie erneut auf Ihr Ereignis, um die **Ereignis bearbeiten** erneut angezeigt.

![ACOP](./images/eventdone.png)

Bewegen Sie den Mauszeiger über die **Nutzlast** und klicken Sie auf **Payload anzeigen** Symbol.

![ACOP](./images/hover.png)

Sie sehen nun ein Beispiel der erwarteten Payload.

![ACOP](./images/fullpayload.png)

Ihr Ereignis verfügt über eine eindeutige Orchestrierungs-eventID, die Sie finden können, indem Sie in dieser Payload nach unten scrollen, bis Sie `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID muss an Adobe Experience Platform gesendet werden, um die Journey Trigger, die Sie im nächsten Schritt erstellen werden. Notieren Sie sich diese eventID, da Sie sie im nächsten Schritt benötigen werden.
`"eventID": "e3a8f0bdc0b609667cd96a72a6b1e5aafa0ddaf6ccf121c574e6a2030860a633"`

Klicken **Ok**, gefolgt von **Abbrechen**.

## 10.4.7 Journey erstellen

Gehen Sie im Menü zu **Journey** und klicken Sie auf **Journey erstellen**.

![DSN](./images/sjourney1.png)

Dann wirst du das sehen. Benennen Sie Ihre Journey. Verwenden Sie `--demoProfileLdap-- - Store Entry journey`. Klicken Sie auf **OK**.

![DSN](./images/sjourney3.png)

Zunächst müssen Sie Ihr Ereignis als Ausgangspunkt Ihrer Journey hinzufügen. Suchen nach Ihrem Ereignis `--demoProfileLdap--StoreEntryEvent` und ziehen Sie es auf die Arbeitsfläche. Klicken Sie auf **OK**.

![DSN](./images/sjourney4.png)

Weiter, unter **Aktionen**, suchen Sie nach der **Push** Aktion.
Ziehen Sie die **Push** Aktion auf die Arbeitsfläche.

![DSN](./images/sjourney5.png)

Legen Sie die **Kategorie** nach **Marketing** und wählen Sie eine Push-Oberfläche aus, über die Sie Push-Benachrichtigungen versenden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **Push-iOS-Android**.

![ACOP](./images/journeyactions1push.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2push.png)

Dann wirst du das sehen. Klicken Sie auf **Personalisierung** -Symbol für **Titel** -Feld.

![Push-Benachrichtigung](./images/bp5.png)

Dann wirst du das sehen. Sie können jetzt jedes Profilattribut direkt aus dem Echtzeit-Kundenprofil auswählen.

![Push-Benachrichtigung](./images/bp6.png)

Suchen Sie nach dem Feld **Vorname** und klicken Sie dann auf **+** Symbol neben dem Feld **Vorname**. Daraufhin wird das Personalisierungstoken für Vorname hinzugefügt: **{{profile.person.name.firstName}}**.

![Push-Benachrichtigung](./images/bp9.png)

Fügen Sie als Nächstes den Text hinzu **, willkommen in unserem Geschäft!** hinter **{{profile.person.name.firstName}}**.

Klicken Sie auf **Speichern**.

![Push-Benachrichtigung](./images/bp10.png)

Das hast du jetzt. Klicken Sie auf **Personalisierung** -Symbol für **body** -Feld.

![Push-Benachrichtigung](./images/bp11.png)

Text eingeben **Klicken Sie hier, um einen 10% Rabatt zu erhalten, wenn Sie heute kaufen!** und klicken Sie auf **Speichern**.

![Push-Benachrichtigung](./images/bp12.png)

Dann wirst du das haben. Klicken Sie auf den Pfeil in der oberen linken Ecke, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/bp12a.png)

Klicken **OK** , um Ihre Push-Aktion zu schließen.

![DSN](./images/sjourney8.png)

Klicken Sie auf **Veröffentlichen**.

![DSN](./images/sjourney10.png)

Klicken **Veröffentlichen** erneut.

![DSN](./images/sjourney10a.png)

Ihre Journey ist jetzt veröffentlicht.

![DSN](./images/sjourney11.png)

## 10.4.8 Journey und Push-Nachricht testen

Wechseln Sie in Ihrer DX Demo 2.0-Mobile-App zum **Einstellungen** angezeigt. Klicken Sie auf **Store Entry** Schaltfläche.

>[!NOTE]
>
>Die **Store Entry** -Schaltfläche derzeit implementiert. Sie werden es noch nicht in der App finden.

![DSN](./images/demo1b.png)

Stellen Sie sicher, dass Sie die App sofort schließen, nachdem Sie auf die **Store Entry** angezeigt, da andernfalls die Push-Nachricht nicht angezeigt wird.

![DSN](./images/demo2.png)

Nach einigen Sekunden wird die Nachricht angezeigt.

![DSN](./images/demo3.png)

Du hast diese Übung beendet.

Nächster Schritt: [10.5 Geschäftsereignis-Journey erstellen](./ex5.md)

[Zurück zu Modul 10](./journeyoptimizer.md)

[Zu allen Modulen zurückkehren](../../overview.md)
