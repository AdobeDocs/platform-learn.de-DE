---
title: Aktualisieren der Konfigurations-ID und Testen der Journey
description: Aktualisieren der Konfigurations-ID und Testen der Journey
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# 3.1.3 Aktualisieren Sie Ihre Datenerfassungseigenschaft und testen Sie Ihre Journey

## 3.1.3.1 Eigenschaft &quot;Datenerfassung&quot;aktualisieren

Wechseln Sie zu [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/launch/) und wählen Sie **Tags** aus.

Dies ist die Seite mit den Eigenschaften der Adobe Experience Platform-Datenerfassung , die Sie zuvor gesehen haben.

![Eigenschaftsseite](./../../../modules/datacollection/module1.1/images/launch1.png)

In Modul 0 hat Demo System zwei Client-Eigenschaften für Sie erstellt: eine für die Website und eine für die mobile App. Suchen Sie sie, indem Sie im Feld **[!UICONTROL Suche]** nach `--demoProfileLdap--` suchen. Klicken Sie auf , um die Eigenschaft **Web** zu öffnen.

![Suchfeld](./../../../modules/datacollection/module1.1/images/property6.png)

Dann wirst du das sehen.

![Einrichtung des Launches](./images/rule1.png)

Navigieren Sie im linken Menü zu **Regeln** und suchen Sie nach der Regel **Profil registrieren**. Klicken Sie auf die Regel &quot;**Profil registrieren**&quot;, um sie zu öffnen.

![Einrichtung des Launches](./images/rule2.png)

Dann sehen Sie die Details dieser Regel. Klicken Sie auf , um die Aktion &quot;**Registrierungsereignis an AEP senden - Trigger JO**&quot;zu öffnen.

![Einrichtung des Launches](./images/rule3.png)

Wenn diese Aktion ausgelöst wird, sehen Sie, dass ein bestimmtes Datenelement verwendet wird, um die XDM-Datenstruktur zu definieren. Sie müssen dieses Datenelement aktualisieren und die **Ereignis-ID** des Ereignisses definieren, das Sie in [Übung 7.1](./ex1.md) konfiguriert haben.

![Einrichtung des Launches](./images/rule4.png)

Sie müssen jetzt das Datenelement **XDM - Registrierungsereignis** aktualisieren. Gehen Sie dazu zu **Datenelemente**. Suchen Sie nach **XDM - Registration Event** und klicken Sie, um dieses Datenelement zu öffnen.

![Einrichtung des Launches](./images/rule5.png)

Daraufhin sehen Sie Folgendes:

![Einrichtung des Launches](./images/rule6.png)

Navigieren Sie zum Feld `_experience.campaign.orchestration.eventID`. Entfernen Sie den aktuellen Wert und fügen Sie dort Ihre eventID ein.

Zur Erinnerung: Die Ereignis-ID befindet sich in Adobe Journey Optimizer unter **Konfigurationen > Ereignisse** und Sie finden die Ereignis-ID in der Beispiel-Payload Ihres Ereignisses, die wie folgt aussieht: `"eventID": "227402c540eb8f8855c6b2333adf6d54d7153d9d7d56fa475a6866081c574736"`.

![ACOP](./images/payloadeventID.png)

Nach dem Einfügen Ihrer eventID sollte Ihr Bildschirm wie folgt aussehen: Klicken Sie als Nächstes auf **Speichern** oder **In Bibliothek speichern**.

![Einrichtung des Launches](./images/rule7.png)

Schließlich müssen Sie Ihre Änderungen veröffentlichen. Wechseln Sie im linken Menü zu **Veröffentlichungsfluss** .

![Einrichtung des Launches](./images/rule8.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und dann auf **Speichern und in Entwicklung erstellen**.

![Einrichtung des Launches](./images/rule9.png)

Ihre Bibliothek wird dann aktualisiert und nach 1-2 Minuten können Sie Ihre Konfiguration testen.

## 3.1.3.2 Journey testen

Wechseln Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8.png)

Klicken Sie auf der Seite **Screens** auf **Ausführen**.

![DSN](./../../../modules/datacollection/module1.1/images/web2.png)

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

1 Minute nach der Erstellung Ihres Kontos erhalten Sie Ihre E-Mail zur Kontoerstellung von Adobe Journey Optimizer.

![Einrichtung des Launches](./images/email.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 3.1](./journey-orchestration-create-account.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
