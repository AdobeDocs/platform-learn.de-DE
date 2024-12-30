---
title: Adobe Journey Optimizer - Externe Datenquellen und benutzerdefinierte Aktionen
description: Adobe Journey Optimizer - Externe Datenquellen und benutzerdefinierte Aktionen
kt: 5342
doc-type: tutorial
exl-id: 068c8be4-2e9e-4d38-9c0e-f769ac927b57
source-git-commit: c531412a2c0a5c216f49560e01fb26b9b7e71869
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# 3.2.5 Trigger des Journey

Trigger In dieser Übung testen und testen Sie die in diesem Modul konfigurierte Journey.

## 3.2.5.1 Aktualisieren der Geofence-Ereigniskonfiguration

Wechseln Sie zu [Adobe Experience Platform-](https://experience.adobe.com/launch/) und wählen Sie **Tags** aus.

Dies ist die Seite mit den Eigenschaften der Adobe Experience Platform-Datenerfassung, die Sie zuvor gesehen haben.

![Eigenschaftenseite](./../../../modules/datacollection/module1.1/images/launch1.png)

In **Erste Schritte** hat Demo System zwei Client-Eigenschaften für Sie erstellt: eine für die Website und eine für die Mobile App. Suchen Sie sie, indem Sie im Feld **[!UICONTROL nach `--aepUserLdap--`]**. Klicken Sie, um die Eigenschaft **Web** zu öffnen.

![Suchfeld](./../../../modules/datacollection/module1.1/images/property6.png)

Sie werden es dann sehen.

![Launch-Einrichtung](./images/rule1.png)

Gehen Sie im linken Menü zu **Regeln** und suchen Sie nach der Regel **Geofence-Ereignis**. Klicken Sie auf die Regel **Geofence-Ereignis**, um sie zu öffnen.

![Launch-Einrichtung](./images/rule2.png)

Anschließend werden die Details dieser Regel angezeigt. Klicken, um die Aktion **Adobe Experience Platform Web SDK - Ereignis senden** zu öffnen.

![Launch-Einrichtung](./images/rule3.png)

Anschließend sehen Sie, dass beim Auslösen dieser Aktion ein bestimmtes Datenelement zum Definieren der XDM-Datenstruktur verwendet wird. Sie müssen dieses Datenelement aktualisieren und die **Ereignis-ID** des Ereignisses definieren, das Sie in [Übung 3.2.1](./ex1.md) konfiguriert haben.

![Launch-Einrichtung](./images/rule4.png)

Jetzt müssen Sie das Datenelement (XDM - **)**. Navigieren Sie dazu zu **Datenelemente**. Suchen Sie nach **XDM - Geofence-** und klicken Sie, um dieses Datenelement zu öffnen.

![Launch-Einrichtung](./images/rule5.png)

Sie sehen dann Folgendes:

![Launch-Einrichtung](./images/rule6.png)

Navigieren Sie zur `_experience.campaign.orchestration.eventID`. Entfernen Sie den aktuellen Wert und fügen Sie Ihre eventID dort ein.

Zur Erinnerung: Die Ereignis-ID finden Sie in Adobe Journey Optimizer unter **Konfigurationen > Ereignisse** und Sie finden die Ereignis-ID in der Beispiel-Payload Ihres Ereignisses, die wie folgt aussieht: `"eventID": "4df8dc10731eba7b0c37af83a9db38d4de7aa6aebcce38196d9d47929b9c598e"`.

![ACOP](./images/payloadeventID.png)

Als Nächstes sollten Sie Ihre Stadt in diesem Datenelement definieren. Gehen Sie **placeContext > Geo > Stadt** und geben Sie eine Stadt Ihrer Wahl ein. Klicken Sie anschließend auf **Speichern** oder **In Bibliothek speichern**.

![ACOP](./images/payloadeventIDgeo.png)

Schließlich müssen Sie Ihre Änderungen veröffentlichen. Navigieren Sie **linken Menü zu** Veröffentlichungsfluss) und klicken Sie auf **Man**, um Ihre Bibliothek zu öffnen.

![Launch-Einrichtung](./images/rule8.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und anschließend auf **Für Entwicklung speichern und erstellen**.

![Launch-Einrichtung](./images/rule9.png)

## Trigger des Journey 3.2.5.2

Navigieren Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf die 3 Punkte **…** in Ihrem Website-Projekt und dann auf **Ausführen**, um es zu öffnen.

![DSN](./../../datacollection/module1.1/images/web8.png)

Anschließend wird Ihre Demo-Website geöffnet. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browser-Fenster.

![DSN](../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../gettingstarted/gettingstarted/images/web6.png)

Ihre Website wird dann in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../gettingstarted/gettingstarted/images/web7.png)

Klicken Sie auf das Adobe-Logo oben links im Bildschirm, um den Profil-Viewer zu öffnen.

![Demo](./../../../modules/datacollection/module1.2/images/pv1.png)

Öffnen Sie das Bedienfeld Profil-Viewer und navigieren Sie zum Echtzeit-Kundenprofil. Im Profil-Viewer-Fenster sollten Sie alle Ihre personenbezogenen Daten angezeigt bekommen, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](./images/pv2.png)

Klicken Sie im Profil-Viewer-Fenster auf **DIENSTPROGRAMME**. Geben Sie `geofenceevent` ein und klicken Sie auf **Senden**.

>[!NOTE]
>
>Falls Sie im Profil-Viewer-Bereich nicht die Möglichkeit haben, ein Direktaufrufereignis zu senden, können Sie eines manuell senden, indem Sie die Entwickleransicht Ihres Browsers öffnen und zu **Konsole** wechseln und dann diesen Befehl einfügen und senden: `_satellite.track('geofenceevent')`.

Ein paar Sekunden später wird die Meldung von Adobe Journey Optimizer im Slack-Kanal angezeigt.

![Demo](./images/smsdemo4.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zum Modul 3.2](journey-orchestration-external-weather-api-sms.md)

[Zurück zu „Alle Module“](../../../overview.md)
