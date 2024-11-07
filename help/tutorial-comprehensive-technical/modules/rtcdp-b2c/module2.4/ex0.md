---
title: Segmentaktivierung zum Microsoft Azure Event Hub - Konfigurieren Ihrer Microsoft Azure-Umgebung
description: Segmentaktivierung zum Microsoft Azure Event Hub - Konfigurieren Ihrer Microsoft Azure-Umgebung
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# 2.4.0 Umgebung konfigurieren

## 2.4.0.1 Azure-Abonnement erstellen

>[!NOTE]
>
>Wenn Sie bereits über ein Azure-Abonnement verfügen, können Sie diesen Schritt überspringen. Fahren Sie in diesem Fall mit der Übung 13.0.2 fort.

Gehen Sie zu [https://portal.azure.com](https://portal.azure.com) und melden Sie sich mit Ihrem Azure-Konto an. Wenn Sie noch keine haben, verwenden Sie bitte Ihre persönliche E-Mail-Adresse, um Ihr Azure-Konto zu erstellen.

![02-azure-portal-email.png](./images/02-azure-portal-email.png)

Nach erfolgreicher Anmeldung wird der folgende Bildschirm angezeigt:

![03-azure-logged-in.png](./images/03-azure-logged-in.png)

Klicken Sie auf das Menü links und wählen Sie **Alle Ressourcen**. Der Azure-Anmeldebildschirm wird angezeigt, wenn Sie noch kein Abonnement haben. Wählen Sie in diesem Fall **Starten Sie mit einer freien Azure-Testversion**.

![04-azure-start-subscribe.png](./images/04-azure-start-subscribe.png)

Füllen Sie das Azure-Anmeldeformular aus, geben Sie Ihr Mobiltelefon und Ihre Kreditkarte zur Aktivierung an (Sie haben eine kostenlose Ebene für 30 Tage und Sie werden nicht belastet, es sei denn, Sie aktualisieren):

![05-azure-subscription-form.png](./images/05-azure-subscription-form.png)

Wenn der Abonnementprozess abgeschlossen ist, können Sie Folgendes tun:

![06-azure-subscription-ok.png](./images/06-azure-subscription-ok.png)


## 2.4.0.2 Visual Code Studio installieren

Sie werden Microsoft Visual Code Studio verwenden, um Ihr Azure-Projekt zu verwalten. Sie können es über [diesen Link](https://code.visualstudio.com/download) herunterladen. Befolgen Sie die Installationsanweisungen für Ihr bestimmtes Betriebssystem auf derselben Website.

## 2.4.0.3 Visual Code-Erweiterungen installieren

Installieren Sie Azure Functions for Visual Studio Code von [https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions). Klicken Sie auf die Schaltfläche Installieren :

![07-azure-code-extension-install.png](./images/07-azure-code-extension-install.png)

Installieren Sie Azure Account und Sign-In für Visual Studio Code von [https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account](https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account). Klicken Sie auf die Schaltfläche Installieren :

![08-azure-account-extension-install.png](./images/08-azure-account-extension-install.png)

## 2.4.0.4 Knoten.js installieren

>[!NOTE]
>
>Wenn Sie node.js bereits installiert haben, können Sie diesen Schritt überspringen. Fahren Sie in diesem Fall mit der Übung 13.0.5 fort.

### macOS

Stellen Sie sicher, dass [Homebrew](https://brew.sh/) zuerst installiert ist. Befolgen Sie die Anweisungen [hier](https://brew.sh/).

![Node](./images/brew.png)

Nachdem Sie Homebrew installiert haben, führen Sie diesen Befehl aus:

```javascript
brew install node
```

### Windows

Laden Sie den [Windows Installer](https://nodejs.org/en/#home-downloadhead) direkt von der Website [nodejs.org](https://nodejs.org/en/) herunter.

## 2.4.0.5 &quot;node.js&quot;-Version überprüfen

Für dieses Modul muss node.js , Version 12 installiert sein. Jede andere Version von node.js kann Probleme mit Übung 13.5 verursachen.

Bevor Sie fortfahren, überprüfen Sie bitte jetzt Ihre Version von node.js.

Führen Sie diesen Befehl aus, um Ihre node.js-Version zu überprüfen:

```javascript
node -v
```

Wenn Ihre Version unter oder über 12 liegt, müssen Sie ein Upgrade oder ein Downgrade durchführen.

### Aktualisieren/Herunterladen der node.js-Version auf macOS

Stellen Sie sicher, dass das Paket **n** installiert ist.

Führen Sie folgenden Befehl aus, um das Paket **n** zu installieren:

```javascript
sudo npm install -g n
```

Wenn Ihre Version unter oder über Version 12 liegt, führen Sie diesen Befehl aus, um ein Upgrade oder ein Downgrade durchzuführen:

```javascript
sudo n 12.6.0
```

### Aktualisieren/Herunterladen der node.js-Version unter Windows

Deinstallieren Sie node.js über Windows > Systemsteuerung > Programme hinzufügen oder entfernen.

Installieren der erforderlichen Version von der Website [nodejs.org](https://nodejs.org/en/) aus.

## 2.4.0.6 NPM-Paket installieren: Anfrage

Sie müssen das Paket **request** im Rahmen der node.js-Einrichtung installieren.

Führen Sie folgenden Befehl aus, um das Paket **request** zu installieren:

```javascript
npm install request
```


Nächster Schritt: [2.4.1 Konfigurieren der Microsoft Azure EventHub-Umgebung](./ex1.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
