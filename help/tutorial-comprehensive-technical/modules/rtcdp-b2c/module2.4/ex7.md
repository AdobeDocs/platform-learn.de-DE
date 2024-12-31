---
title: Audience Activation zum Microsoft Azure Event Hub - Aktion
description: Audience Activation zum Microsoft Azure Event Hub - Aktion
kt: 5342
doc-type: tutorial
exl-id: f5b224bf-60b9-46e0-abdb-9d96a7e8c59f
source-git-commit: b4a7144217a68bc0b1bc70b19afcbc52e226500f
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# 2.4.7 End-to-End-Szenario

## Azure Event Hub-Trigger starten

Um die Payload anzuzeigen, die von Adobe Experience Platform Real-time CDP nach Zielgruppen-Qualifizierung an unseren Azure Event Hub gesendet wird, müssen wir unsere einfache Azure Event Hub-Trigger-Funktion starten. Diese Funktion gibt die Payload einfach in Visual Studio Code in die Konsole „ab“. Denken Sie jedoch daran, dass diese Funktion in jeder Weise erweitert werden kann, um eine Schnittstelle mit allen Arten von Umgebungen zu schaffen, wobei dedizierte APIs und Protokolle verwendet werden.

### Starten von Visual Studio Code und Starten des Projekts

Stellen Sie sicher, dass das Visual Studio Code-Projekt geöffnet ist und ausgeführt wird

Informationen zum Starten/Stoppen/Neustarten Ihrer Azure-Funktion in Visual Studio Code finden Sie in der vorherigen Übung.

Der Visual Studio Code-**Terminal** sollte etwas Ähnliches erwähnen:

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

## Laden der Citi Signal-Website

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

## Für Ihre Zielgruppe qualifizieren

Navigieren Sie zur Seite **Pläne**. Diese Aktion qualifiziert Sie für die `--aepUserLdap-- - Interest in Plans`.

![6-04-luma-telco-nav-sports.png](./images/cs1.png)

Öffnen Sie zum Überprüfen das Bedienfeld Profil-Viewer . Sie sollten jetzt Mitglied des `--aepUserLdap-- - Interest in Plans` sein. Wenn Ihre Zielgruppenzugehörigkeiten im Profil-Viewer-Bedienfeld noch nicht aktualisiert wurden, klicken Sie auf die Schaltfläche Neu laden .

![6-05-luma-telco-nav-breitband.png](./images/cs2.png)

Wechseln Sie zurück zu Visual Studio Code, und wenn Sie sich die Registerkarte **TERMINAL** ansehen, sollte eine Liste der Zielgruppen für Ihre spezifische **ECID)**. Diese Aktivierungs-Payload wird an Ihren Ereignis-Hub gesendet, sobald Sie sich für die `--aepUserLdap-- - Interest in Plans` Zielgruppe qualifizieren.

![6-06-vsc-activation-realized.png](./images/cs3.png)

Wenn Sie sich die Payload der Zielgruppe genauer ansehen, können Sie sehen, dass sich `--aepUserLdap-- - Interest in Plans` im Status **Realisiert** befindet.

```json
{
  "identityMap": {
    "ecid": [
      {
        "id": "36281682065771928820739672071812090802"
      }
    ]
  },
  "segmentMembership": {
    "ups": {
      "94db5aed-b90e-478d-9637-9b0fad5bba11": {
        "createdAt": 1732129904025,
        "lastQualificationTime": "2024-11-21T07:33:52Z",
        "mappingCreatedAt": 1732130611000,
        "mappingUpdatedAt": 1732130611000,
        "name": "vangeluw - Interest in Plans",
        "status": "realized",
        "updatedAt": 1732129904025
      }
    }
  }
}
```

Der Zielgruppenstatus **Realisiert** bedeutet, dass Ihr Profil Teil der Zielgruppe ist, während der **Verlassen**-Status bedeutet, dass Ihr Profil aus der Zielgruppe entfernt wurde.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zum Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zurück zu „Alle Module“](./../../../overview.md)
