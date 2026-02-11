---
title: Verwenden von Cursor.ai zum Entwickeln Ihres Projekts
description: Verwenden von Cursor.ai zum Entwickeln Ihres Projekts
kt: 5342
doc-type: tutorial
source-git-commit: 2bfa7f4bee54df8411c96b001224d2986e9fcaf9
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# 1.7.2 Verwenden Sie Cursor.ai, um Ihr Projekt zu entwickeln

## 1.7.2.1 Einrichten von Verzeichnis und Tools

Erstellen Sie auf Ihrem Desktop ein neues Verzeichnis mit dem Namen `--aepUserLdap---commerce`

![Commerce und Agent](./images/cursorai1.png)

Klicken Sie mit der rechten Maustaste auf den Ordner und wählen Sie **Neues Terminal unter Ordner**.

![Commerce und Agent](./images/cursorai2.png)

Sie sollten das dann sehen.

![Commerce und Agent](./images/cursorai3.png)

Sie müssen jetzt ein vorhandenes GitHub-Repository klonen, das Sie anzeigen können [https://github.com/adobe/commerce-integration-starter-kit](https://github.com/adobe/commerce-integration-starter-kit).

Dieses Repository ist das Integrations-Starter-Kit von Adobe, das Adobe Developer App Builder verwendet, um die Verbindungszuverlässigkeit in Echtzeit zu verbessern und die Time-to-Market für Integrationen zwischen Adobe Commerce und anderen Back-Office-Systemen wie ERPs, CRMs und PIMs zu reduzieren.

![Commerce und Agent](./images/cursorai4.png)

Es gibt mehrere Möglichkeiten, dieses Repository zu klonen, in diesem Beispiel wird Terminal verwendet.

Geben Sie den folgenden Befehl in Ihr Terminal-Fenster ein und führen Sie ihn aus.

`git clone https://github.com/adobe/commerce-integration-starter-kit`

![Commerce und Agent](./images/cursorai5.png)

Nach einigen Sekunden sollten Sie dieses Ergebnis sehen.

![Commerce und Agent](./images/cursorai6.png)

Als Nächstes sollten Sie zum soeben erstellten Ordner navigieren. Geben Sie den folgenden Befehl ein und führen Sie ihn dann aus.

`cd commerce-integration-starter-kit`

![Commerce und Agent](./images/cursorai7.png)

Sie sollten das dann sehen.

![Commerce und Agent](./images/cursorai8.png)

Als Nächstes müssen Sie die Commerce-Erweiterbarkeits-Tools für Cursor.ai einrichten. Geben Sie den folgenden Befehl ein und führen Sie ihn dann aus.

`aio commerce extensibility tools-setup`

![Commerce und Agent](./images/cursorai9.png)

Wählen Sie **Aktuelles Verzeichnis** aus.

![Commerce und Agent](./images/cursorai10.png)

Wählen Sie **Cursor**.

![Commerce und Agent](./images/cursorai11.png)

Wählen Sie **npm** aus.

![Commerce und Agent](./images/cursorai12.png)

Nach ein paar Minuten sollten Sie das hier sehen.

![Commerce und Agent](./images/cursorai13.png)

Durch die Installation der Commerce-Erweiterbarkeits-Tools für Cursor.ai steht nun ein MCP-Server als Teil Ihrer Cursor.ai-Umgebung zur Verfügung. In den nächsten Übungen verwenden Sie diesen MCP-Server, um das App Builder-Projekt zu entwickeln und bereitzustellen.

## 1.7.2.2 Webhook einrichten

Für diese Übung benötigen Sie einen Webhook, der so konfiguriert werden muss, dass bei der Erstellung einer Bestellung das Auftragsereignis an diesen Webhook gestreamt werden kann. In dieser Übung verwenden Sie einen Beispielendpunkt mit [https://pipedream.com/requestbin](https://pipedream.com/requestbin).

Wechseln Sie zu [https://pipedream.com/requestbin](https://pipedream.com/requestbin), erstellen Sie ein Konto und dann einen Arbeitsbereich. Nachdem der Arbeitsbereich erstellt wurde, sehen Sie etwas Ähnliches.

Klicken Sie **Kopieren**, um die URL zu kopieren. Sie müssen diese URL in der nächsten Übung angeben. Die URL in diesem Beispiel lautet `https://eodts05snjmjz67.m.pipedream.net`.

![cursor.ai + Commerce](./images/webhook1.png)

## 1.7.2.3 Cursor.ai

Öffnen Sie Cursor.ai. Klicken Sie **Projekt öffnen**.

![cursor.ai + Commerce](./images/cursorai14.png)

Navigieren Sie zu dem von Ihnen erstellten Ordner, der `--aepUserLdap---commerce` benannt werden sollte. Wählen Sie in diesem Ordner den Ordner aus, der `commerce-integration-starter-kit` heißt. Klicken Sie auf **Öffnen**.

![cursor.ai + Commerce](./images/cursorai15.png)

Sie sollten das dann sehen. Stellen Sie vor dem Fortfahren sicher, dass der Ordner der obersten Ebene, der in Cursor.ai geöffnet ist, `commerce-integration-starter-kit` ist.

![cursor.ai + Commerce](./images/cursorai16.png)

`I would like to build an app that subscribes to order created events and sends them to a configurable URL with basic authentication`

## Nächste Schritte

Zurück zu [Intelligent Developer Tools for Adobe Commerce](./aiassisteddev.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}