---
title: Einrichten der Entwicklungsumgebung
description: Einrichten der Entwicklungsumgebung
kt: 5342
doc-type: tutorial
exl-id: c9bfb327-362f-4475-89da-8e9788940d56
source-git-commit: ce3ee3dde103383a6f7897cba36d548058879ea7
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 5%

---

# 1.7.1 Einrichten der Entwicklungsumgebung

## 1.7.1.1 Erstellen eines Adobe I/O-Projekts

Navigieren Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"}.

Achten Sie darauf, dass Sie die richtige Instanz in der oberen rechten Ecke Ihres Bildschirms auswählen. Ihre Instanz ist `--aepImsOrgName--`.

>[!NOTE]
>
> Der folgende Screenshot zeigt, wie eine bestimmte Organisation ausgewählt wird. Wenn Sie dieses Tutorial durchlaufen, hat Ihre Organisation höchstwahrscheinlich einen anderen Namen. Wenn Sie sich für dieses Tutorial angemeldet haben, wurden Ihnen die zu verwendenden Umgebungsdetails zur Verfügung gestellt. Befolgen Sie bitte diese Anweisungen.

Wählen Sie anschließend **Projekt aus Vorlage erstellen**.

![GSPeM-Erweiterbarkeit](./images/commerceagent1.png)

**App Builder**.

![GSPeM-Erweiterbarkeit](./images/commerceagent2.png)

Geben Sie den `--aepUserLdap-- vangeluw Commerce Events` ein. Klicken Sie auf **Speichern**.

![GSPeM-Erweiterbarkeit](./images/commerceagent4.png)

Sie sollten dann so etwas sehen.

![GSPeM-Erweiterbarkeit](./images/commerceagent5.png)

Klicken Sie auf **+ Service hinzufügen** wählen Sie dann **API** aus.

![GSPeM-Erweiterbarkeit](./images/commerceagent6.png)

Suchen Sie die API **I/O Events** und wählen Sie sie aus. Klicken Sie auf **Weiter**.

![GSPeM-Erweiterbarkeit](./images/commerceagent7.png)

Ändern Sie den Namen der Berechtigung in `vangeluw Commerce Events - Production`. Klicken Sie auf **Konfigurierte API speichern**.

![GSPeM-Erweiterbarkeit](./images/commerceagent8.png)

Sie sollten das dann sehen. Klicken Sie auf **+ Service hinzufügen** wählen Sie dann **API** aus.

![GSPeM-Erweiterbarkeit](./images/commerceagent9.png)

Suchen Sie die API **I/O Management API** und wählen Sie sie aus. Klicken Sie auf **Weiter**.

![GSPeM-Erweiterbarkeit](./images/commerceagent10.png)

Klicken Sie auf **Konfigurierte API speichern**.

![GSPeM-Erweiterbarkeit](./images/commerceagent11.png)

Sie sollten das dann sehen. Klicken Sie auf **+ Service hinzufügen** wählen Sie dann **API** aus.

![GSPeM-Erweiterbarkeit](./images/commerceagent12.png)

Suchen Sie die API **Adobe Commerce as a Cloud Service** und wählen Sie sie aus. Klicken Sie auf **Weiter**.

![GSPeM-Erweiterbarkeit](./images/commerceagent13.png)

Wählen Sie **Server-zu-Server-Authentifizierung** aus. Klicken Sie auf **Weiter**.

![GSPeM-Erweiterbarkeit](./images/commerceagent14.png)

Klicken Sie auf **Weiter**.

![GSPeM-Erweiterbarkeit](./images/commerceagent15.png)

Wählen Sie **Standard - Cloud Manager** aus. Klicken Sie auf **Konfigurierte API speichern**.

![GSPeM-Erweiterbarkeit](./images/commerceagent16.png)

Sie sollten das dann sehen. Klicken Sie auf **+ Service hinzufügen** wählen Sie dann **API** aus.

![GSPeM-Erweiterbarkeit](./images/commerceagent17.png)

Suchen Sie die API **Adobe I/O Events for Adobe Commerce** und wählen Sie sie aus. Klicken Sie auf **Weiter**.

![GSPeM-Erweiterbarkeit](./images/commerceagent18.png)

Klicken Sie auf **Konfigurierte API speichern**.

![GSPeM-Erweiterbarkeit](./images/commerceagent19.png)

Ihr Projekt ist jetzt eingerichtet und kann verwendet werden.

![GSPeM-Erweiterbarkeit](./images/commerceagent20.png)

## 1.7.1.2 Konfigurieren der Entwicklungsumgebung

Um Ihre erweiterbare Anwendung zu erstellen, zu übermitteln und bereitzustellen, sollten in Ihrer lokalen Entwicklungsumgebung auf Ihrem Computer die folgenden Anwendungen und Pakete installiert sein:

- Node.js (Version 20.x oder höher)
- npm (im Paket mit Node.js)
- Adobe Developer-Befehlszeilenschnittstelle (CLI)

Falls diese Anwendungen oder Pakete noch nicht auf Ihrem Computer installiert sind, führen Sie die folgenden Schritte aus.

### Node.js und npm

Navigieren Sie zu [https://nodejs.org/en/download](https://nodejs.org/en/download). Sie sollten dies dann sehen, mit einer Reihe von Terminal-Befehlen, die ausgeführt werden müssen, um Node.js und npm installiert zu haben. Die hier angezeigten Befehle gelten für MacBook.

![GSPeM-Erweiterbarkeit](./images/commerceagent21.png)

Öffnen Sie zunächst ein neues Terminal-Fenster. Fügen Sie den in Zeile 2 des Screenshots genannten Befehl ein und führen Sie ihn aus:

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash`

Führen Sie als Nächstes den Befehl in Zeile 5 des Screenshots aus:

`\. "$HOME/.nvm/nvm.sh"`

Führen Sie nach erfolgreicher Ausführung beider Befehle den folgenden Befehl aus:

`node -v`

Es sollte eine Versionsnummer zurückgegeben werden.

![GSPeM-Erweiterbarkeit](./images/commerceagent22.png)

Führen Sie als Nächstes diesen Befehl aus:

`npm -v`

Falls NPM noch nicht installiert ist, können Sie es mit diesem Befehl installieren: `npm install -g npm@11.9.0`.

Es sollte eine Versionsnummer zurückgegeben werden.

![GSPeM-Erweiterbarkeit](./images/commerceagent23.png)

Wenn die letzten beiden Befehle erfolgreich eine Versionsnummer zurückgegeben haben, ist Ihre Konfiguration dieser beiden Funktionen erfolgreich.

### Adobe Developer-Befehlszeilenschnittstelle (CLI)

Um die Adobe Developer-Befehlszeilenschnittstelle (CLI) zu installieren, führen Sie den folgenden Befehl in einem Terminal-Fenster aus:

`npm install -g @adobe/aio-cli`

Die Ausführung dieses Befehls kann einige Minuten dauern. Das Endergebnis sollte in etwa wie folgt aussehen:

![GSPeM-Erweiterbarkeit](./images/commerceagent24.png)

Die Adobe Developer-Befehlszeilenschnittstelle (CLI) wurde ebenfalls erfolgreich installiert.

### SDK-Erweiterung der Adobe Developer-Befehlszeilenschnittstelle (CLI) für Commerce

Um die Adobe I/O SDK-Erweiterung für Commerce zu installieren, führen Sie den folgenden Befehl in einem Terminal-Fenster aus:

`npm install @adobe/aio-commerce-sdk`

![GSPeM-Erweiterbarkeit](./images/commerceagent25.png)

### Adobe Commerce-Plug-ins für Adobe I/O CLI

Um die Adobe Commerce-Plug-ins für Adobe I/O CLI zu installieren, führen Sie den folgenden Befehl in einem Terminal-Fenster aus:

`aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce @adobe/aio-cli-plugin-app-dev @adobe/aio-cli-plugin-runtime`

![GSPeM-Erweiterbarkeit](./images/commerceagent26.png)

Sie haben jetzt die Grundelemente eingerichtet, damit Sie ein App Builder-Projekt in Kombination mit Adobe Commerce, Adobe I/O Events und Adobe I/O Runtime ausführen können.

## Nächste Schritte

Navigieren Sie zu [Verwenden Sie Cursor.ai, um Ihr Projekt zu entwickeln](./ex2.md){target="_blank"}

Zurück zu [Intelligent Developer Tools for Adobe Commerce](./aiassisteddev.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
