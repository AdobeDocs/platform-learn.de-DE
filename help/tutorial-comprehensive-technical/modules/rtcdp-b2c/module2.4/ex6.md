---
title: Audience Activation zu Microsoft Azure Event Hub - Definieren einer Azure-Funktion
description: Audience Activation zu Microsoft Azure Event Hub - Definieren einer Azure-Funktion
kt: 5342
doc-type: tutorial
exl-id: c39fea54-98ec-45c3-a502-bcf518e6fd06
source-git-commit: 216914c9d97827afaef90e21ed7d4f35eaef0cd3
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 2.4.6 Microsoft Azure-Projekt erstellen

## Kennenlernen der Azure Event Hub-Funktionen

Mit Azure-Funktionen können Sie kleine Code-Abschnitte (namens **Funktionen**) ausführen, ohne sich um die Anwendungs-Infrastruktur zu sorgen. Mit Azure Functions stellt die Cloud-Infrastruktur alle aktuellen Server bereit, die Sie benötigen, um Ihre Anwendung im Maßstab ausführen zu können.

Eine Funktion wird **durch einen bestimmten Ereignistyp ausgelöst**. Zu den unterstützten Triggern gehören die Reaktion auf Datenänderungen, die Reaktion auf Nachrichten (z. B. Ereignis-Hubs), die planmäßige Ausführung oder die Ausführung einer HTTP-Anfrage.

Azure Functions ist ein Server-loser Compute-Dienst, mit dem Sie ereignisbasierten Code ausführen können, ohne Infrastruktur explizit bereitstellen oder verwalten zu müssen.

Azure Event Hub ist mit Azure Functions für eine Server-lose Architektur integriert.

## Öffnen Sie Visual Studio Code und melden Sie sich bei Azure an.

Visual Studio Code macht es einfach...

- Definieren und Binden von Azure-Funktionen an Event-Hubs
- lokal testen
- Bereitstellung auf Azure
- Ausführung der Remote-Protokollfunktion

### Öffnen von Visual Studio Code

### Anmelden bei Azure

Wenn Sie sich mit Ihrem Azure-Konto anmelden, das Sie in der vorherigen Übung registriert haben, können Sie mit Visual Studio Code alle Event Hub-Ressourcen finden und binden.

Öffnen Sie Visual Studio Code und klicken Sie auf das Symbol **Azure** .

Wählen Sie dann **Anmelden bei Azure** aus:

![3-01-vsc-open.png](./images/301vscopen.png)

Sie werden zu Ihrem Browser weitergeleitet, um sich anzumelden. Denken Sie daran, das Azure-Konto auszuwählen, das Sie zur Registrierung verwendet haben.

Wenn der folgende Bildschirm in Ihrem Browser angezeigt wird, sind Sie bei Visual Code Studio angemeldet:

![3-03-vsc-login-ok.png](./images/303vscloginok.png)

Kehren Sie zu Visual Code Studio zurück (Sie sehen den Namen Ihres Azure-Abonnements, z. B. **Azure subscription 1**):

![3-04-vsc-logged-in.png](./images/304vscloggedin.png)

## Erstellen eines Azure-Projekts

Klicken Sie auf **Funktionsprojekt erstellen..**:

![3-05-vsc-create-project.png](./images/vsc2.png)

Wählen Sie einen lokalen Ordner Ihrer Wahl aus, um das Projekt zu speichern, und klicken Sie auf **Auswählen**:

![3-06-vsc-select-folder.png](./images/vsc3.png)

Geben Sie nun den Assistenten zur Projekterstellung ein. Klicken Sie auf **Javascript** als Sprache für Ihr Projekt:

![3-07-vsc-select-language.png](./images/vsc4.png)

Wählen Sie dann **Modell v4** aus.

![3-07-vsc-select-language.png](./images/vsc4a.png)

Wählen Sie **Azure Event Hub Trigger** als erste Funktionsvorlage Ihres Projekts aus:

![3-08-vsc-function-template.png](./images/vsc5.png)

Geben Sie einen Namen für Ihre Funktion ein, verwenden Sie das folgende Format: `--aepUserLdap---aep-event-hub-trigger` und drücken Sie die Eingabetaste:

![3-09-vsc-function-name.png](./images/vsc6.png)

Wählen Sie **Neue lokale App-Einstellung erstellen**:

![3-10-vsc-function-local-app-setting.png](./images/vsc7.png)

Klicken Sie auf , um den zuvor erstellten Event Hub-Namespace mit dem Namen `--aepUserLdap---aep-enablement` auszuwählen.

![3-11-vsc-function-select-namespace.png](./images/vsc8.png)

Klicken Sie anschließend auf , um den zuvor erstellten Event Hub mit dem Namen `--aepUserLdap---aep-enablement-event-hub` auszuwählen.

![3-12-vsc-function-select-eventhub.png](./images/vsc9.png)

Klicken Sie auf , um **RootManageSharedAccessKey** als Hub-Richtlinie für Ereignisse auszuwählen:

![3-13-vsc-function-select-eventhub-policy.png](./images/vsc10.png)

Wählen Sie **Zum Arbeitsbereich hinzufügen** aus, um das Projekt zu öffnen:

![3-15-vsc-project-add-to-workspace.png](./images/vsc12.png)

Sie können dann eine Nachricht wie diese bekommen. Klicken Sie in diesem Fall auf **Ja, ich vertraue den Autoren**.

![3-15-vsc-project-add-to-workspace.png](./images/vsc12a.png)

Nachdem Sie das Projekt erstellt haben, klicken Sie auf **index.js** , damit die Datei im Editor geöffnet wird:

![3-16-vsc-open-index-js.png](./images/vsc13.png)

Die von Adobe Experience Platform an Ihren Event Hub gesendete Payload enthält Zielgruppen-IDs:

```json
[{
"segmentMembership": {
"ups": {
"ca114007-4122-4ef6-a730-4d98e56dce45": {
"lastQualificationTime": "2020-08-31T10:59:43Z",
"status": "realized"
},
"be2df7e3-a6e3-4eb4-ab12-943a4be90837": {
"lastQualificationTime": "2020-08-31T10:59:56Z",
"status": "realized"
},
"39f0feef-a8f2-48c6-8ebe-3293bc49aaef": {
"lastQualificationTime": "2020-08-31T10:59:56Z",
"status": "realized"
}
}
},
"identityMap": {
"ecid": [{
"id": "08130494355355215032117568021714632048"
}]
}
}]
```

Ersetzen Sie den Code in der index.js-Datei Ihres Visual Studio-Codes durch den unten stehenden Code. Dieser Code wird jedes Mal ausgeführt, wenn die Echtzeit-Kundendatenplattform Zielgruppenqualifikationen an Ihr Event Hub-Ziel sendet. In unserem Beispiel geht es im Code nur darum, die empfangene Payload anzuzeigen und zu verbessern. Sie können sich aber jede Art von Funktion vorstellen, um Zielgruppenqualifikationen in Echtzeit zu verarbeiten.

```javascript
// Marc Meewis - Solution Consultant Adobe - 2020
// Adobe Experience Platform Enablement - Module 2.4

// Main function
// -------------
// This azure function is fired for each audience activated to the Adobe Exeperience Platform Real-time CDP Azure 
// Eventhub destination
// This function enriched the received audience payload with the name of the audience. 
// You can replace this function with any logic that is require to process and deliver
// Adobe Experience Platform audiences in real-time to any application or platform that 
// would need to act upon an AEP audience qualification.
// 

module.exports = async function (context, eventHubMessages) {

    return new Promise (function (resolve, reject) {

        context.log('Message : ' + JSON.stringify(eventHubMessages, null, 2));

        resolve();

    });    

};
```

Das Ergebnis sollte wie folgt aussehen:

![3-16b-vsc-edit-index-js.png](./images/vsc1.png)

## Azure-Projekt ausführen

Jetzt ist es an der Zeit, Ihr Projekt auszuführen. In dieser Phase werden wir das Projekt nicht auf Azure bereitstellen. Sie wird lokal im Debug-Modus ausgeführt. Wählen Sie das Symbol Ausführen und danach den grünen Pfeil aus.

![3-17-vsc-run-project.png](./images/vsc14.png)

Wenn Sie Ihr Projekt zum ersten Mal im Debug-Modus ausführen, müssen Sie ein Azure-Speicherkonto anhängen, auf **Speicherkonto auswählen** klicken und dann das zuvor erstellte Speicherkonto mit dem Namen `--aepUserLdap--aepstorage` auswählen.

Ihr Projekt läuft jetzt und listet Ereignisse auf dem Ereignis-Hub auf. In der nächsten Übung werden Sie das Verhalten auf der Demowebsite von CitiSignal demonstrieren, das Sie für Zielgruppen qualifiziert. Daher erhalten Sie eine Payload für die Zielgruppenqualifizierung im Terminal Ihrer Event Hub-Trigger-Funktion.

![3-24-vsc-application-stop.png](./images/vsc18.png)

## Azure-Projekt beenden

Um Ihr Projekt zu stoppen, navigieren Sie zur Lenu **AUFRUF STACK** in VSC, klicken Sie auf den Pfeil in Ihrem laufenden Projekt und klicken Sie dann auf **Stoppen**.

![3-24-vsc-application-stop.png](./images/vsc17.png)

Nächster Schritt: [2.4.7 End-to-End-Szenario](./ex7.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
