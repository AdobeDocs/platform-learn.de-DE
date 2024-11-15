---
title: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Trigger Ihrer koordinierten Kunden-Journey
description: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Trigger Ihrer koordinierten Kunden-Journey
kt: 5342
doc-type: tutorial
exl-id: 068c8be4-2e9e-4d38-9c0e-f769ac927b57
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 1%

---

# 3.2.5 Trigger Ihrer Journey

In dieser Übung testen und Trigger Sie die in diesem Modul konfigurierte Journey.

## 3.2.5.1 Konfiguration des Geofence-Ereignisses aktualisieren

Wechseln Sie zu [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/launch/) und wählen Sie **Tags** aus.

Dies ist die Seite mit den Eigenschaften der Adobe Experience Platform-Datenerfassung , die Sie zuvor gesehen haben.

![Eigenschaftsseite](./../../../modules/datacollection/module1.1/images/launch1.png)

In Modul 0 hat Demo System zwei Client-Eigenschaften für Sie erstellt: eine für die Website und eine für die mobile App. Suchen Sie sie, indem Sie im Feld **[!UICONTROL Suche]** nach `--aepUserLdap--` suchen. Klicken Sie auf , um die Eigenschaft **Web** zu öffnen.

![Suchfeld](./../../../modules/datacollection/module1.1/images/property6.png)

Dann wirst du das sehen.

![Einrichtung des Launches](./images/rule1.png)

Navigieren Sie im linken Menü zu **Regeln** und suchen Sie nach der Regel **Geofence-Ereignis**. Klicken Sie auf die Regel **Geofence-Ereignis** , um sie zu öffnen.

![Einrichtung des Launches](./images/rule2.png)

Dann sehen Sie die Details dieser Regel. Klicken Sie auf , um die Aktion &quot;**Geofence-Ereignis an AEP senden - Trigger JO**&quot;zu öffnen.

![Einrichtung des Launches](./images/rule3.png)

Wenn diese Aktion ausgelöst wird, sehen Sie, dass ein bestimmtes Datenelement verwendet wird, um die XDM-Datenstruktur zu definieren. Sie müssen dieses Datenelement aktualisieren und die **Ereignis-ID** des Ereignisses definieren, das Sie in [Übung 8.1](./ex1.md) konfiguriert haben.

![Einrichtung des Launches](./images/rule4.png)

Sie müssen jetzt das Datenelement **XDM - Geofence Event** aktualisieren. Gehen Sie dazu zu **Datenelemente**. Suchen Sie nach **XDM - Geofence Event** und klicken Sie, um dieses Datenelement zu öffnen.

![Einrichtung des Launches](./images/rule5.png)

Daraufhin sehen Sie Folgendes:

![Einrichtung des Launches](./images/rule6.png)

Navigieren Sie zum Feld `_experience.campaign.orchestration.eventID`. Entfernen Sie den aktuellen Wert und fügen Sie dort Ihre eventID ein.

Zur Erinnerung: Die Ereignis-ID befindet sich in Adobe Journey Optimizer unter **Konfigurationen > Ereignisse** und Sie finden die Ereignis-ID in der Beispiel-Payload Ihres Ereignisses, die wie folgt aussieht: `"eventID": "fa42ab7982ba55f039eacec24c1e32e5c51b310c67f0fa559ab49b89b63f4934"`.

![ACOP](./images/payloadeventID.png)

Als Nächstes sollten Sie Ihre Stadt in diesem Datenelement definieren. Gehen Sie zu **placeContext > geo > city** und geben Sie eine Stadt der Wahl ein. Klicken Sie als Nächstes auf **Speichern** oder **In Bibliothek speichern**.

![ACOP](./images/payloadeventIDgeo.png)

Schließlich müssen Sie Ihre Änderungen veröffentlichen. Wechseln Sie im linken Menü zu **Veröffentlichungsfluss** .

![Einrichtung des Launches](./images/rule8.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und dann auf **Speichern und in Entwicklung erstellen**.

![Einrichtung des Launches](./images/rule9.png)

## 3.2.5.2 Trigger Ihrer Journey

Wechseln Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web7.png)

Klicken Sie auf das Adobe-Logo-Symbol oben links im Bildschirm, um den Profilanzeige zu öffnen.

![Demo](./../../../modules/datacollection/module1.2/images/pv1.png)

Sehen Sie sich das Bedienfeld &quot;Profil-Viewer&quot;und das Echtzeit-Kundenprofil mit der **Experience Cloud-ID** als primäre ID für diesen derzeit unbekannten Kunden an.

![Demo](./../../../modules/datacollection/module1.2/images/pv2.png)

Gehen Sie zur Seite Registrieren/Anmelden . Klicken Sie auf **KONTO ERSTELLEN**.

![Demo](./../../../modules/datacollection/module1.2/images/pv9.png)

Füllen Sie Ihre Details aus und klicken Sie auf **Registrieren** . Danach werden Sie zur vorherigen Seite weitergeleitet.

![Demo](./../../../modules/datacollection/module1.2/images/pv10.png)

Öffnen Sie das Bedienfeld Profil-Viewer und wechseln Sie zum Echtzeit-Kundenprofil. Im Bedienfeld &quot;Profil-Viewer&quot;sollten alle Ihre personenbezogenen Daten angezeigt werden, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](./../../../modules/datacollection/module1.2/images/pv11.png)

Klicken Sie im Bedienfeld &quot;Profil-Viewer&quot;auf **UTILITIES**. Geben Sie `geofenceevent` ein und klicken Sie auf **Senden**.

![Demo](./images/smsdemo1.png)

Einige Sekunden später erhalten Sie eine SMS von Adobe Journey Optimizer.

![Demo](./images/smsdemo4.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 3.2](journey-orchestration-external-weather-api-sms.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
