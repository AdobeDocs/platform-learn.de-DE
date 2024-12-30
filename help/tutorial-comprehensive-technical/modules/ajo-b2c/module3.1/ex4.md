---
title: Aktualisieren Sie Ihre Konfigurations-ID und testen Sie Ihre Journey
description: Aktualisieren Sie Ihre Konfigurations-ID und testen Sie Ihre Journey
kt: 5342
doc-type: tutorial
source-git-commit: 2bd4249d96eb697da66db68895761f8b0bd6e638
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 1%

---

# 3.1.3 Aktualisieren der Datenerfassungseigenschaft und Testen des Journey

## 3.1.3.1 Aktualisieren der Datenerfassungseigenschaft

Wechseln Sie zu [Adobe Experience Platform-](https://experience.adobe.com/launch/) und wählen Sie **Tags** aus.

![Eigenschaftenseite](./../../../modules/datacollection/module1.1/images/launch1.png)

In **Erste Schritte** hat Demo System zwei Client-Eigenschaften für Sie erstellt: eine für die Website und eine für die Mobile App. Suchen Sie sie, indem Sie im Feld **[!UICONTROL nach `--aepUserLdap--`]**. Klicken Sie, um die Eigenschaft **Web** zu öffnen.

![Suchfeld](./../../../modules/datacollection/module1.1/images/property6.png)

Sie werden es dann sehen.

![Launch-Einrichtung](./images/rule1.png)

Gehen Sie im linken Menü zu **Regeln** und suchen Sie nach der Regel **Konto erstellen**. Klicken Sie auf die Regel **Konto erstellen**, um sie zu öffnen.

![Launch-Einrichtung](./images/rule2.png)

Anschließend werden die Details dieser Regel angezeigt. Klicken, um die Aktion &quot;**-Ereignis senden“ zu**.

![Launch-Einrichtung](./images/rule3.png)

Anschließend sehen Sie, dass beim Auslösen dieser Aktion ein bestimmtes Datenelement zum Definieren der XDM-Datenstruktur verwendet wird. Sie müssen dieses Datenelement aktualisieren und die **Ereignis-ID** des Ereignisses definieren, das Sie in [Übung 3.1.1](./ex1.md) konfiguriert haben.

![Launch-Einrichtung](./images/rule4.png)

Jetzt müssen Sie das Datenelement (XDM - **)**. Navigieren Sie dazu zu **Datenelemente**. Suchen Sie nach **XDM - Registrierung** und klicken Sie, um dieses Datenelement zu öffnen.

![Launch-Einrichtung](./images/rule5.png)

Sie sehen dann Folgendes:

![Launch-Einrichtung](./images/rule6.png)

Navigieren Sie zur `_experience.campaign.orchestration.eventID`. Entfernen Sie den aktuellen Wert und fügen Sie Ihre eventID dort ein.

Zur Erinnerung: Die Ereignis-ID finden Sie in Adobe Journey Optimizer unter **Konfigurationen > Ereignisse** und Sie finden die Ereignis-ID in der Beispiel-Payload Ihres Ereignisses, die wie folgt aussieht: `"eventID": "5ae9b8d3f68eb555502b0c07d03ef71780600c4bd0373a4065c692ae0bfbd34d"`.

![ACOP](./images/payloadeventID.png)

Nach dem Einfügen Ihrer eventID sollte Ihr Bildschirm wie folgt aussehen. Klicken Sie anschließend auf **Speichern** oder **In Bibliothek speichern**.

![Launch-Einrichtung](./images/rule7.png)

Schließlich müssen Sie Ihre Änderungen veröffentlichen. Navigieren Sie **linken Menü zu** Veröffentlichungsfluss) und klicken Sie darauf, um Ihre **Hauptbibliothek** zu öffnen.

![Launch-Einrichtung](./images/rule8.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** und anschließend auf **Für Entwicklung speichern und erstellen**.

![Launch-Einrichtung](./images/rule9.png)

Ihre Bibliothek wird dann aktualisiert und nach 1-2 Minuten können Sie mit dem Testen Ihrer Konfiguration fortfahren.

## 3.1.3.2 Testen des Journey

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

Sehen Sie sich das Bedienfeld Profil-Viewer und das Echtzeit-Kundenprofil mit der **Experience Cloud-ID** als primäre Kennung für diesen derzeit unbekannten Kunden an. Klicken Sie auf **Anmelden**.

![Demo](./../../../modules/datacollection/module1.2/images/pv2.png)

Klicken Sie **KONTO ERSTELLEN**.

![Demo](./../../../modules/datacollection/module1.2/images/pv9.png)

Füllen Sie Ihre Daten aus und klicken Sie **Registrieren**, woraufhin Sie zur vorherigen Seite weitergeleitet werden.

![Demo](./../../../modules/datacollection/module1.2/images/pv10.png)

Öffnen Sie das Bedienfeld Profil-Viewer und navigieren Sie zum Echtzeit-Kundenprofil. Im Profil-Viewer-Fenster sollten Sie alle Ihre personenbezogenen Daten angezeigt bekommen, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](./../../../modules/datacollection/module1.2/images/pv11.png)

1 Minute nach der Erstellung Ihres Kontos erhalten Sie Ihre E-Mail zur Kontoerstellung von Adobe Journey Optimizer.

![Launch-Einrichtung](./images/email.png)

Außerdem werden der Journey-Eintrag und der Fortschritt durch die Journey im Journey-Dashboard in Journey Optimizer angezeigt.

![Launch-Einrichtung](./images/emaildash.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zum Modul 3.1](./journey-orchestration-create-account.md)

[Zurück zu „Alle Module“](../../../overview.md)
