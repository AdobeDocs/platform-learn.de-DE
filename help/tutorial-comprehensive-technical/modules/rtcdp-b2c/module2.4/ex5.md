---
title: Segmentaktivierung zum Microsoft Azure Event Hub - Definieren einer Azure-Funktion
description: Segmentaktivierung zum Microsoft Azure Event Hub - Definieren einer Azure-Funktion
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# 2.4.5 Microsoft Azure-Projekt erstellen

## 2.4.5.1 Azure Event Hub-Funktionen kennenlernen

Mit Azure Functions können Sie kleine Code-Abschnitte (namens **Funktionen**) ausführen, ohne sich um die Anwendungs-Infrastruktur zu sorgen. Mit Azure Functions stellt die Cloud-Infrastruktur alle aktuellen Server bereit, die Sie benötigen, um Ihre Anwendung im Maßstab ausführen zu können.

Eine Funktion wird **durch einen bestimmten Ereignistyp ausgelöst**. Zu den unterstützten Triggern gehören die Reaktion auf Datenänderungen, die Reaktion auf Nachrichten (z. B. Ereignis-Hubs), die planmäßige Ausführung oder die Ausführung einer HTTP-Anfrage.

Azure Functions ist ein Server-loser Compute-Dienst, mit dem Sie ereignisbasierten Code ausführen können, ohne Infrastruktur explizit bereitstellen oder verwalten zu müssen.

Azure Event Hub ist mit Azure Functions für eine Server-lose Architektur integriert.

## 2.4.5.2 Visual Studio-Code öffnen und bei Azure anmelden

Visual Studio Code macht es einfach...

- Definieren und Binden von Azure-Funktionen an Event-Hubs
- lokal testen
- Bereitstellung auf Azure
- Ausführung der Remote-Protokollfunktion

### Öffnen von Visual Studio Code

Um Visual Studio Code zu öffnen, geben Sie **visual** in die Suche Ihres Betriebssystems ein (Spotlight-Suche auf OSX, Suche in der Taskleiste von Windows). Wenn Sie sie nicht finden, müssen Sie die Schritte wiederholen, die unter [Übung 0 - Voraussetzungen](./ex0.md) beschrieben sind.

![visual-studio-code-icon.png](./images/visual-studio-code-icon.png)

### Anmelden bei Azure

Wenn Sie sich mit Ihrem Azure-Konto anmelden, das Sie zur Registrierung in [Übung 0 - Voraussetzungen](./ex0.md) verwendet haben, können Sie mit Visual Studio Code alle Ereignis-Hub-Ressourcen finden und binden.

Klicken Sie auf das Symbol **Azure** in Visual Studio Code. Wenn Sie diese Option nicht haben, ist bei der Installation der erforderlichen Erweiterungen möglicherweise etwas schiefgelaufen.

Wählen Sie dann **Anmelden bei Azure** aus:

![3-01-vsc-open.png](./images/3-01-vsc-open.png)

Sie werden zu Ihrem Browser weitergeleitet, um sich anzumelden. Denken Sie daran, das Azure-Konto auszuwählen, das Sie zur Registrierung verwendet haben.

![3-02-vsc-pick-account.png](./images/3-02-vsc-pick-account.png)

Wenn der folgende Bildschirm in Ihrem Browser angezeigt wird, sind Sie bei Visual Code Studio angemeldet:

![3-03-vsc-login-ok.png](./images/3-03-vsc-login-ok.png)

Kehren Sie zu Visual Code Studio zurück (Sie sehen den Namen Ihres Azure-Abonnements, z. B. **Azure subscription 1**):

![3-04-vsc-logged-in.png](./images/3-04-vsc-logged-in.png)

## 2.4.5.3 Azure-Projekt erstellen

Wenn Sie den Mauszeiger über **Azure subscription 1** bewegen, wird ein Menü über dem Abschnitt angezeigt. Wählen Sie **Create New Project..**:

![3-05-vsc-create-project.png](./images/vsc2.png)

Wählen Sie einen lokalen Ordner Ihrer Wahl aus, um das Projekt zu speichern, und klicken Sie auf **Auswählen**:

![3-06-vsc-select-folder.png](./images/vsc3.png)

Geben Sie nun den Assistenten zur Projekterstellung ein. Wählen Sie **Javascript** als Sprache für Ihr Projekt aus:

![3-07-vsc-select-language.png](./images/vsc4.png)

Wählen Sie **Azure Event Hub Trigger** als erste Funktionsvorlage Ihres Projekts aus:

![3-08-vsc-function-template.png](./images/vsc5.png)

Geben Sie einen Namen für Ihre Funktion ein, verwenden Sie das folgende Format: `--demoProfileLdap---aep-event-hub-trigger` und drücken Sie die Eingabetaste:

![3-09-vsc-function-name.png](./images/vsc6.png)

Wählen Sie **Neue lokale App-Einstellung erstellen**:

![3-10-vsc-function-local-app-setting.png](./images/vsc7.png)

Wählen Sie einen Ereignis-Hub-Namespace aus. Sie sollten den Ereignis-Hub sehen, den Sie in **Übung 2** definiert haben. In diesem Beispiel lautet der Ereignis-Hub-Namespace **vangeluw-aep-enablement**:

![3-11-vsc-function-select-namespace.png](./images/vsc8.png)

Wählen Sie Ihren Ereignis-Hub aus. Sie sollten den Ereignis-Hub sehen, den Sie in **Übung 2** definiert haben. In meinem Fall ist dies **vangeluw-aep-enablement-event-hub**:

![3-12-vsc-function-select-eventhub.png](./images/vsc9.png)

Wählen Sie **RootManageSharedAccessKey** als Hub-Richtlinie für Ereignisse aus:

![3-13-vsc-function-select-eventhub-policy.png](./images/vsc10.png)

Geben Sie ein, um **$Default** zu verwenden:

![3-14-vsc-eventhub-consumer-group.png](./images/vsc11.png)

Wählen Sie **Zum Arbeitsbereich hinzufügen** aus, um das Projekt zu öffnen:

![3-15-vsc-project-add-to-workspace.png](./images/vsc12.png)

Nachdem Sie das Projekt erstellt haben, klicken Sie auf **index.js** , damit die Datei im Editor geöffnet wird:

![3-16-vsc-open-index-js.png](./images/vsc13.png)

Die Payload, die von Adobe Experience Platform an Ihren Event Hub gesendet wird, umfasst die Segment-IDs:

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

Ersetzen Sie den Code in der index.js-Datei Ihres Visual Studio-Codes durch den unten stehenden Code. Dieser Code wird jedes Mal ausgeführt, wenn die Echtzeit-Kundendatenplattform Segmentqualifikationen an Ihr Event Hub-Ziel sendet. In unserem Beispiel geht es im Code nur darum, die empfangene Payload anzuzeigen und zu verbessern. Sie können sich jedoch jede Art von Funktion vorstellen, um Segmentqualifikationen in Echtzeit zu verarbeiten.

```javascript
// Marc Meewis - Solution Consultant Adobe - 2020
// Adobe Experience Platform Enablement - Module 13

// Main function
// -------------
// This azure function is fired for each segment activated to the Adobe Exeperience Platform Real-time CDP Azure 
// Eventhub destination
// This function enriched the received segment payload with the name fo the segment. 
// You can replace this function with any logic that is require to process and deliver
// Adobe Experience Platform segments in real-time to any application or platform that 
// would need to act upon an AEP segment qualiification.
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

## 2.4.5.4 Azure-Projekt ausführen

Jetzt ist es an der Zeit, Ihr Projekt auszuführen. In dieser Phase werden wir das Projekt nicht auf Azure bereitstellen. Sie wird lokal im Debug-Modus ausgeführt. Wählen Sie das Symbol Ausführen und danach den grünen Pfeil aus.

![3-17-vsc-run-project.png](./images/vsc14.png)

Wenn Sie Ihr Projekt zum ersten Mal im Debug-Modus ausführen, müssen Sie ein Azure-Speicherkonto anhängen. Klicken Sie auf **Speicherkonto auswählen**.

![3-17-vsc-run-project.png](./images/vsc15.png)

Wählen Sie aus der Liste der Speicherkonten das Konto aus, das Sie im Rahmen von [13.1.4 Einrichten Ihres Azure Storage-Kontos](./ex1.md) erstellt haben. Ihr Speicherkonto trägt den Namen &quot;`--demoProfileLdap--aepstorage`&quot;, z. B. &quot;**mmeewisaepstorage**&quot;.

![3-22-vsc-select-storage-account.png](./images/vsc16.png)

Ihr Projekt läuft jetzt und listet Ereignisse auf dem Ereignis-Hub auf. In der nächsten Übung werden Sie das Verhalten auf der Demowebsite von Luma demonstrieren, das Sie für diese Segmente qualifizieren wird. Daher erhalten Sie im Terminal Ihrer Event Hub-Trigger-Funktion eine Payload für die Segmentqualifizierung:

![3-23-vsc-application-started.png](./images/vsc17.png)

## 2.4.5.5 Azure-Projekt beenden

Um Ihr Projekt zu stoppen, wählen Sie die Registerkarte **Terminal** aus, klicken Sie im Terminal-Fenster auf und drücken Sie unter OSX auf **CMD-C** oder unter Windows auf **STRG-C**:

![3-24-vsc-application-stop.png](./images/vsc18.png)

Nächster Schritt: [2.4.6 End-to-End-Szenario](./ex6.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
