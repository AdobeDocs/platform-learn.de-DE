---
title: Segmentaktivierung für Microsoft Azure Event Hub - Konfigurieren Ihrer Microsoft Azure-Umgebung
description: Segmentaktivierung für Microsoft Azure Event Hub - Konfigurieren Ihrer Microsoft Azure-Umgebung
kt: 5342
doc-type: tutorial
exl-id: 772b4d2b-144a-4f29-a855-8fd3493a85d2
source-git-commit: 216914c9d97827afaef90e21ed7d4f35eaef0cd3
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# 2.4.1 Konfigurieren der Umgebung

## Erstellen eines Azure-Abonnements

>[!NOTE]
>
>Wenn Sie bereits über ein Azure-Abonnement verfügen, können Sie diesen Schritt überspringen. Bitte fahren Sie in diesem Fall mit der nächsten Übung fort.

Wechseln Sie zu [https://portal.azure.com](https://portal.azure.com) und melden Sie sich mit Ihrem Azure-Konto an. Wenn Sie noch keine haben, verwenden Sie bitte Ihre persönliche E-Mail-Adresse, um Ihr Azure-Konto zu erstellen.

![02-azure-portal-email.png](./images/02azureportalemail.png)

Nach erfolgreicher Anmeldung wird der folgende Bildschirm angezeigt:

![03-azure-logged-in.png](./images/03azureloggedin.png)

Klicken Sie auf das linke Menü und wählen Sie **Alle Ressourcen**. Der Azure-Abonnementbildschirm wird angezeigt, wenn Sie noch kein Abonnement haben. Wählen Sie in diesem Fall **Mit einer kostenlosen Azure-Testversion beginnen**.

![04-azure-start-subscribe.png](./images/04azurestartsubscribe.png)

Füllen Sie das Azure-Abonnementformular aus, stellen Sie Ihr Mobiltelefon und Ihre Kreditkarte zur Aktivierung bereit (Sie haben 30 Tage lang eine kostenlose Stufe und werden nicht belastet, es sei denn, Sie führen ein Upgrade durch).

Wenn der Anmeldeprozess abgeschlossen ist, können Sie loslegen:

![06-azure-subscription-ok.png](./images/06azuresubscriptionok.png)

## Installieren von Visual Code Studio

Zur Verwaltung Ihres Azure-Projekts verwenden Sie Microsoft Visual Code Studio. Sie können ihn über [diesen Link](https://code.visualstudio.com/download) herunterladen. Befolgen Sie die Installationsanweisungen für Ihr Betriebssystem auf derselben Website.

## Installieren von Visual Code-Erweiterungen

Installieren Sie die Azure-Funktionen für Visual Studio Code von [https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions). Klicken Sie auf die Schaltfläche Installieren:

![07-azure-code-extension-install.png](./images/07azurecodeextensioninstall.png)

Installieren Sie das Azure-Konto und die Anmeldung für Visual Studio Code von [https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account](https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account). Klicken Sie auf die Schaltfläche Installieren:

![08-azure-account-extension-install.png](./images/08azureaccountextensioninstall.png)

## Installieren von node.js

>[!NOTE]
>
>Wenn Sie Node.js bereits installiert haben, können Sie diesen Schritt überspringen. Bitte fahren Sie in diesem Fall mit der nächsten Übung fort.

### macOS

Stellen Sie sicher, dass Sie [Homebrew](https://brew.sh/) zuerst installiert haben. Befolgen Sie die Anweisungen [hier](https://brew.sh/).

![Knoten](./images/brew.png)

Nachdem Sie HomeBrew installiert haben, führen Sie diesen Befehl aus:

```javascript
brew install node
```

### Windows

Laden Sie das [Windows Installer](https://nodejs.org/en/#home-downloadhead) direkt von der Website [nodejs.org](https://nodejs.org/en/) herunter.

## Überprüfen der node.js-Version

Für dieses Modul muss node.js, Version 18 installiert sein. Jede andere Version von Node.js kann Probleme mit dieser Übung verursachen.

Bevor Sie fortfahren, überprüfen Sie jetzt Ihre Version von node.js.

Führen Sie diesen Befehl aus, um Ihre Node.js-Version zu überprüfen:

```javascript
node -v
```

Wenn Ihre Version unter oder über 18 ist, müssen Sie ein Upgrade oder ein Downgrade durchführen.

### Node.js-Version auf macOS aktualisieren/herunterladen

Stellen Sie sicher, dass das Paket **n** installiert ist.

Um das Paket **n** zu installieren, führen Sie diesen Befehl aus:

```javascript
sudo npm install -g n
```

Wenn die Version unter oder über Version 12 liegt, führen Sie diesen Befehl aus, um ein Upgrade oder ein Downgrade durchzuführen:

```javascript
sudo n 18
```

### Aktualisieren/Downgrade der Node.js-Version unter Windows

Deinstallieren Sie node.js unter Windows > Systemsteuerung > Programme hinzufügen oder entfernen.

Installieren der erforderlichen Version von der Website [nodejs.org](https://nodejs.org/en/).

## NPM-Paket installieren: Anfrage

Sie müssen das Paket **request** im Rahmen Ihrer Node.js-Einrichtung installieren.

Führen Sie zum Installieren des Pakets **request** diesen Befehl aus:

```javascript
npm install request
```

## Installieren Sie die Core Tools für Azure-Funktionen:

```
brew tap azure/functions
brew install azure-functions-core-tools@4
```

Nächster Schritt: [2.4.2 Konfigurieren Sie Ihre Microsoft Azure EventHub-Umgebung](./ex2.md)

[Zurück zum Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zurück zu „Alle Module“](./../../../overview.md)
