---
title: Audience Activation zu Microsoft Azure Event Hub - Definieren einer Azure-Funktion
description: Audience Activation zu Microsoft Azure Event Hub - Definieren einer Azure-Funktion
kt: 5342
doc-type: tutorial
exl-id: 2ce9dcfc-4b2c-48b4-b554-8a30abb850f3
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# 2.4.6 Microsoft Azure-Projekt erstellen

## Kennenlernen der Azure Event Hub-Funktionen

Mit Azure-Funktionen können Sie kleine Code-Abschnitte (so genannte **) ausführen** ohne sich Gedanken über die Anwendungsinfrastruktur machen zu müssen. Mit Azure Functions stellt die Cloud-Infrastruktur alle aktuellen Server bereit, die Sie benötigen, um Ihre Anwendung skaliert laufen zu lassen.
Eine Funktion wird **einem** Ereignistyp ausgelöst. Zu den unterstützten Trigger gehören die Reaktion auf Datenänderungen, die Reaktion auf Nachrichten (z. B. Event Hubs), die nach einem Zeitplan oder als Ergebnis einer HTTP-Anfrage ausgeführt werden.
Azure Functions ist ein Server-loser Compute-Service, mit dem Sie ereignisgesteuerten Code ausführen können, ohne die Infrastruktur explizit bereitstellen oder verwalten zu müssen.
Azure Event Hubs lässt sich mit Azure-Funktionen für eine Server-lose Architektur integrieren.

## Öffnen Sie Visual Studio Code und melden Sie sich bei Azure an

Visual Studio Code erleichtert das…
- Definieren und Binden von Azure-Funktionen an Event Hubs- Lokaler Test- Bereitstellen in Azure- Remote-Protokollfunktion

### Visual Studio Code öffnen

### Bei Azure anmelden

Wenn Sie sich mit Ihrem Azure-Konto anmelden, das Sie in der vorherigen Übung registriert haben, können Sie mit Visual Studio Code alle Event Hub-Ressourcen finden und binden.
Öffnen Sie Visual Studio Code und klicken Sie auf das Symbol **Azure**.
Wählen Sie als Nächstes **Bei Azure anmelden**:
![3-01-vsc-open.png](./images/301vscopen.png)
Sie werden zum Anmelden zu Ihrem Browser weitergeleitet. Denken Sie daran, das Azure-Konto auszuwählen, das Sie für die Registrierung verwendet haben.
Wenn der folgende Bildschirm im Browser angezeigt wird, sind Sie mit Visual Code Studio angemeldet:
![3-03-vsc-login-ok.png](./images/303vscloginok.png)
Kehren Sie zu Visual Code Studio zurück (Sie sehen den Namen Ihres Azure-Abonnements, z. B. **Azure-Abonnement 1**):
![3-04-vsc-logged-in.png](./images/304vscloggedin.png)

## Erstellen eines Azure-Projekts

Klicken Sie **Funktionsprojekt erstellen…**:
![3-05-vsc-create-project.png](./images/vsc2.png)
Wählen oder erstellen Sie einen lokalen Ordner Ihrer Wahl, um das Projekt zu speichern, und klicken Sie auf **Auswählen**:
![3-06-vsc-select-folder.png](./images/vsc3.png)
Sie gelangen nun in den Assistenten zur Projekterstellung. Klicken Sie **JavaScript** als Sprache für Ihr Projekt:
![3-07-vsc-select-language.png](./images/vsc4.png)
Wählen Sie dann **Modell v4** aus.
![3-07-vsc-select-language.png](./images/vsc4a.png)
Trigger Wählen Sie **Azure Event Hub** als erste Funktionsvorlage Ihres Projekts aus:
![3-08-vsc-function-template.png](./images/vsc5.png)
Geben Sie einen Namen für Ihre Funktion ein, verwenden Sie das folgende `--aepUserLdap---aep-event-hub-trigger` und drücken Sie die Eingabetaste:
![3-09-vsc-function-name.png](./images/vsc6.png)
Wählen Sie **Neue lokale App-Einstellung erstellen**:
![3-10-vsc-function-local-app-setting.png](./images/vsc7.png)
Klicken Sie auf den zuvor erstellten Event Hub-Namespace, der `--aepUserLdap---aep-enablement` heißt, um ihn auszuwählen.
![3-11-vsc-function-select-namespace.png](./images/vsc8.png)
Klicken Sie als Nächstes auf den zuvor erstellten Event Hub mit dem Namen `--aepUserLdap---aep-enablement-event-hub`.
![3-12-vsc-function-select-eventHub.png](./images/vsc9.png)
Klicken Sie, um **RootManageSharedAccessKey** als Event Hub-Richtlinie auszuwählen:
![3-13-vsc-function-select-eventHub-policy.png](./images/vsc10.png)
Wählen Sie **Zu Arbeitsbereich hinzufügen** aus, um Ihr Projekt zu öffnen:
![3-15-vsc-project-add-to-workspace.png](./images/vsc12.png)
Sie erhalten dann möglicherweise eine Nachricht wie diese. Klicken Sie dann auf **Ja, ich vertraue den Autoren**.
![3-15-vsc-project-add-to-workspace.png](./images/vsc12a.png)
Öffnen Sie nach dem Erstellen des Projekts die Datei `--aepUserLdap---aep-event-hub-trigger.js` im Editor:
![3-16-vsc-open-index-js.png](./images/vsc13.png)
Die Payload, die von Adobe Experience Platform an Ihren Event Hub gesendet wird, sieht wie folgt aus:

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

Aktualisieren Sie den Code in der `--aepUserLdap---aep-event-hub-trigger.js` Ihres Visual Studio-Codes mit dem folgenden Code. Dieser Code wird jedes Mal ausgeführt, wenn Real-Time CDP Zielgruppenqualifikationen an Ihr Event Hub-Ziel sendet. In diesem Beispiel geht es im Code nur um die Anzeige eingehender Payload. Sie können sich jedoch jede Art zusätzlicher Funktionen vorstellen, um Zielgruppenqualifikationen in Echtzeit zu verarbeiten und sie weiter unten in Ihrem Datenpipeline-Ökosystem zu verwenden.
Zeile 11 in Ihrer Datei `--aepUserLdap---aep-event-hub-trigger.js` zeigt derzeit Folgendes:

```javascript
context.log('Event hub message:', message);
```

Ändern Sie Zeile 11 in `--aepUserLdap---aep-event-hub-trigger.js` so, dass sie wie folgt aussieht:

```javascript
context.log('Event hub message:', JSON.stringify(message));
```

Die gesamte Payload sollte dann wie folgt aussehen:

```javascript
const { app } = require('@azure/functions');

app.eventHub('--aepUserLdap---aep-event-hub-trigger', {
    connection: '--aepUserLdap--aepenablement_RootManageSharedAccessKey_EVENTHUB',
    eventHubName: '--aepUserLdap---aep-enablement-event-hub',
    cardinality: 'many',
    handler: (messages, context) => {
        if (Array.isArray(messages)) {
            context.log(`Event hub function processed ${messages.length} messages`);
            for (const message of messages) {
                context.log('Event hub message:', message);
            }
        } else {
            context.log('Event hub function processed message:', messages);
        }
    }
});
```


Das Ergebnis sollte wie folgt aussehen:
![3-16b-vsc-edit-index-js.png](./images/vsc1.png)

## Azure-Projekt ausführen

Jetzt ist es Zeit, Ihr Projekt auszuführen. In dieser Phase werden wir das Projekt nicht in Azure bereitstellen. Wir führen es lokal im Debug-Modus aus. Wählen Sie das Symbol Ausführen aus und klicken Sie auf den grünen Pfeil.
![3-17-vsc-run-project.png](./images/vsc14.png)
Wenn Sie Ihr Projekt zum ersten Mal im Debugging-Modus ausführen, müssen Sie ein Azure-Speicherkonto anhängen. Klicken Sie dann auf **Speicherkonto auswählen**.
![3-17-vsc-run-project.png](./images/vsc14a.png)
Wählen Sie anschließend das zuvor erstellte Speicherkonto mit dem Namen `--aepUserLdap--aepstorage` aus.
![3-17-vsc-run-project.png](./images/vsc14b.png)
Ihr Projekt läuft jetzt und wird für Ereignisse im Event Hub aufgelistet. In der nächsten Übung demonstrieren Sie das Verhalten auf der Demo-Website von CitiSignal, das Sie für Zielgruppen qualifiziert. Als Ergebnis erhalten Sie eine Payload zur Zielgruppen-Qualifizierung im Terminal Ihrer Event Hub-Trigger-Funktion.
![3-24-vsc-application-stop.png](./images/vsc18.png)

## Azure-Projekt stoppen

Um Ihr Projekt zu stoppen, gehen Sie zum Lenu **CALL STACK** in VSC, klicken Sie auf den Pfeil Ihres laufenden Projekts und dann auf **Stopp**.
![3-24-vsc-application-stop.png](./images/vsc17.png)

## Nächste Schritte

Zum End-to-End-Szenario [2.4.7](./ex7.md){target="_blank"}
Zurück zu [Real-Time CDP: Audience Activation zum Microsoft Azure Event Hub](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}
Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
