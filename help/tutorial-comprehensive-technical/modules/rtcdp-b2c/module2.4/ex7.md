---
title: Audience Activation zu Microsoft Azure Event Hub - Aktion
description: Audience Activation zu Microsoft Azure Event Hub - Aktion
kt: 5342
doc-type: tutorial
source-git-commit: cefebfe0336952f0e3099fd2dd9f4395d453f713
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# 2.4.7 End-to-End-Szenario

## Starten des Azure Event Hub-Triggers

Um die Payload anzuzeigen, die von der Echtzeit-Kundendatenplattform von Adobe Experience Platform bei der Zielgruppenqualifizierung an unseren Azure Event Hub gesendet wird, müssen wir unsere einfache Azure Event Hub-Trigger-Funktion starten. Diese Funktion vereinfacht die Nutzlast in der Konsole in Visual Studio Code. Beachten Sie jedoch, dass diese Funktion auf jede Weise erweitert werden kann, um mit allen möglichen Umgebungen mit dedizierten APIs und Protokollen zu arbeiten.

### Visual Studio-Code starten und Projekt starten

Stellen Sie sicher, dass Ihr Visual Studio Code-Projekt geöffnet und ausgeführt wird.

Informationen zum Starten/Stoppen/Neustart Ihrer Azure-Funktion in Visual Studio Code finden Sie in der vorherigen Übung.

Das **Terminal** Ihres Visual Studio-Codes sollte in etwa so aussehen:

```code
[2024-11-20T20:07:12.316Z] Debugger listening on ws://127.0.0.1:9229/86c8e251-8e2f-4c65-a063-cda77edbf2ca
[2024-11-20T20:07:12.318Z] For help, see: https://nodejs.org/en/docs/inspector
[2024-11-20T20:07:12.343Z] Worker process started and initialized.
[2024-11-20T20:07:12.359Z] Debugger attached.

Functions:

        vangeluw-aep-event-hub-trigger: eventHubTrigger

For detailed output, run func with --verbose flag.
[2024-11-20T20:07:18.150Z] Host lock lease acquired by instance ID '000000000000000000000000000C19D8'.
```

## Website zu Citi Signal laden

Wechseln Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf die drei Punkte **..** im Website-Projekt und dann auf **Ausführen** , um es zu öffnen.

![DSN](./../../datacollection/module1.1/images/web8.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../gettingstarted/gettingstarted/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../gettingstarted/gettingstarted/images/web7.png)

## Qualifizieren Sie sich für Ihre Zielgruppe

Navigieren Sie zur Seite **Pläne** . Diese Aktion qualifiziert Sie für die Zielgruppe &quot;`--aepUserLdap-- - Interest in Plans`&quot;.

![6-04-luma-telco-nav-sports.png](./images/cs1.png)

Öffnen Sie dazu das Bedienfeld Profil-Viewer . Sie sollten jetzt Mitglied der `--aepUserLdap-- - Interest in Plans` sein. Wenn Ihre Zielgruppenmitgliedschaften noch nicht in Ihrem Profil-Viewer-Bedienfeld aktualisiert wurden, klicken Sie auf die Schaltfläche &quot;Neu laden&quot;.

![6-05-luma-telco-nav-broad.png](./images/cs2.png)

Wechseln Sie zurück zu Visual Studio Code und sehen Sie sich die Registerkarte **TERMINAL** an. Es sollte eine Liste der Zielgruppen für Ihre spezifische **ECID** angezeigt werden. Diese Aktivierungs-Payload wird an Ihren Ereignis-Hub bereitgestellt, sobald Sie sich für die `--aepUserLdap-- - Interest in Plans` -Zielgruppe qualifizieren.

Wenn Sie sich die Nutzlast der Zielgruppe genauer ansehen, können Sie sehen, dass `--aepUserLdap-- - Interest in Plans` den Status **realisiert** aufweist.

Der Zielgruppenstatus **realisiert** bedeutet, dass Ihr Profil Teil der Zielgruppe ist, während der Status **Ausstieg** bedeutet, dass unser Profil aus der Zielgruppe entfernt wurde.

![6-06-vsc-activation-alized.png](./images/cs3.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
