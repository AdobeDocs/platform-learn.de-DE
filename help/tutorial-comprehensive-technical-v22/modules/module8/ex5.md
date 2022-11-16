---
title: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Trigger Ihrer koordinierten Kunden-Journey
description: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Trigger Ihrer koordinierten Kunden-Journey
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 4d92877d-8fdc-4902-ad32-7fa068bc1395
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 1%

---

# 8.5 Trigger Journey

In dieser Übung testen und Trigger Sie die Journey, die Sie in diesem Modul konfiguriert haben.

## 8.5.1 Konfiguration des Geofence-Ereignisses aktualisieren

Navigieren Sie zu [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/launch/) und wählen Sie **Tags**.

Dies ist die Seite mit den Eigenschaften der Adobe Experience Platform-Datenerfassung , die Sie zuvor gesehen haben.

![Eigenschaften-Seite](../module1/images/launch1.png)

In Modul 0 hat Demo System zwei Client-Eigenschaften für Sie erstellt: eine für die Website und eine für die mobile App. Suchen Sie sie, indem Sie nach `--demoProfileLdap--` im **[!UICONTROL Suche]** ankreuzen. Klicken Sie auf , um die **Web** -Eigenschaft.

![Suchfeld](../module1/images/property6.png)

Dann wirst du das sehen.

![Launch-Einrichtung](./images/rule1.png)

Gehen Sie im linken Menü zu **Regeln** und nach der Regel suchen **Geofence-Ereignis**. Klicken Sie auf die Regel **Geofence-Ereignis** um es zu öffnen.

![Launch-Einrichtung](./images/rule2.png)

Dann sehen Sie die Details dieser Regel. Klicken Sie auf , um die Aktion zu öffnen. **Senden des &quot;Geofence-Ereignisses&quot;an AEP - Trigger JO**.

![Launch-Einrichtung](./images/rule3.png)

Wenn diese Aktion ausgelöst wird, sehen Sie, dass ein bestimmtes Datenelement verwendet wird, um die XDM-Datenstruktur zu definieren. Sie müssen dieses Datenelement aktualisieren und die **Ereignis-ID** des Ereignisses, das Sie in [Übung 8.1](./ex1.md).

![Launch-Einrichtung](./images/rule4.png)

Jetzt müssen Sie das Datenelement aktualisieren **XDM - Geofence-Ereignis**. Gehen Sie dazu zu **Datenelemente**. Suchen Sie nach **XDM - Geofence-Ereignis** und klicken Sie auf , um dieses Datenelement zu öffnen.

![Launch-Einrichtung](./images/rule5.png)

Daraufhin sehen Sie Folgendes:

![Launch-Einrichtung](./images/rule6.png)

Navigieren Sie zum Feld `_experience.campaign.orchestration.eventID`. Entfernen Sie den aktuellen Wert und fügen Sie dort Ihre eventID ein.

Zur Erinnerung: Die Ereignis-ID finden Sie in Adobe Journey Optimizer unter **Konfigurationen > Ereignisse** und Sie finden die Ereignis-ID in der Beispiel-Payload Ihres Ereignisses, was wie folgt aussieht: `"eventID": "fa42ab7982ba55f039eacec24c1e32e5c51b310c67f0fa559ab49b89b63f4934"`.

![ACOP](./images/payloadeventID.png)

Als Nächstes sollten Sie Ihre Stadt in diesem Datenelement definieren. Navigieren Sie zu **placeContext > geo > city** und geben Sie eine Stadt der Wahl ein. Klicken Sie anschließend auf **Speichern** oder **In Bibliothek speichern**.

![ACOP](./images/payloadeventIDgeo.png)

Schließlich müssen Sie Ihre Änderungen veröffentlichen. Navigieren Sie zu **Veröffentlichungsfluss** im linken Menü.

![Launch-Einrichtung](./images/rule8.png)

Klicken **Alle geänderten Ressourcen hinzufügen** und klicken Sie anschließend auf **Speichern und in Entwicklung erstellen**.

![Launch-Einrichtung](./images/rule9.png)

## 8.5.2 Trigger Ihrer Journey

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

Öffnen Sie das Bedienfeld Profil-Viewer und wechseln Sie zum Echtzeit-Kundenprofil. Im Bedienfeld &quot;Profil-Viewer&quot;sollten alle Ihre personenbezogenen Daten angezeigt werden, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](../module2/images/pv11.png)

Klicken Sie im Bereich &quot;Profil-Viewer&quot;auf **AKTIVITÄTEN**. Eingabe `geofenceevent` und klicken Sie auf **Senden**.

![Demo](./images/smsdemo1.png)

Einige Sekunden später erhalten Sie eine SMS von Adobe Journey Optimizer.

![Demo](./images/smsdemo4.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 8](journey-orchestration-external-weather-api-sms.md)

[Zu allen Modulen zurückkehren](../../overview.md)
