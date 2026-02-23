---
title: AEM MCP-Server und Cursor
description: AEM MCP-Server und Cursor
kt: 5342
doc-type: tutorial
source-git-commit: 1abfd8d1f270a810dd65d9921c69834df2a9147d
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 1%

---

# 1.6.2 AEM MCP-Server und Cursor

>[!IMPORTANT]
>
>Um diese Übung abzuschließen, benötigen Sie Zugriff auf eine funktionierende Umgebung für AEM Sites und Assets CS mit EDS, und die verschiedenen AEM-Agenten müssen für die von Ihnen verwendete IMS-Organisation aktiviert sein.
>
>Wenn Sie noch keine solche Umgebung haben, gehen Sie zu Übung [Adobe Experience Manager Cloud Service &amp; Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Folgen Sie den Anweisungen dort, und Sie haben Zugriff auf eine solche Umgebung.

>[!IMPORTANT]
>
>Wenn Sie zuvor ein AEM CS-Programm mit einer AEM Sites- und Assets CS-Umgebung konfiguriert haben, wurde Ihre AEM CS-Sandbox möglicherweise in den Ruhezustand versetzt. Da der Ruhezustand einer solchen Sandbox 10-15 Minuten dauert, ist es ratsam, den Ruhezustand jetzt zu beenden, damit Sie nicht zu einem späteren Zeitpunkt warten müssen.


Im Folgenden finden Sie alle verfügbaren AEM MCP-Server:

- https://mcp.adobeaemcloud.com/adobe/mcp/content
- https://mcp.adobeaemcloud.com/adobe/mcp/content-readonly (schreibgeschützte Inhaltsvorgänge)
- https://mcp.adobeaemcloud.com/adobe/mcp/content-updater (legt die entsprechende Qualifikation vom Experience Production Agent offen)
- https://mcp.adobeaemcloud.com/adobe/mcp/experience-governance (stellt Fähigkeiten bereit, um die Markenrichtlinie für eine Seite abzurufen und zu überprüfen)
- https://mcp.adobeaemcloud.com/adobe/mcp/discovery (stellt Fähigkeiten zur Erkennung von Inhalten in einer AEM-Umgebung bereit)

In dieser Übung finden Sie Anweisungen zur Verwendung dieser spezifischen MCP-Server:

- https://mcp.adobeaemcloud.com/adobe/mcp/content
- https://mcp.adobeaemcloud.com/adobe/mcp/discovery

Sie können die folgenden Anweisungen verwenden, um ähnliche MCP-Server für die anderen verfügbaren AEM-MCP-Server einzurichten, da der Prozess sehr ähnlich ist.

## Setup für 1.6.2.1 Experience Production Agent Cursor MCP Server

Erstellen Sie einen neuen leeren Ordner auf Ihrem Desktop.

![Cursor + AEM](./images/cursorai1.png)

Cursor öffnen. Klicken Sie **Projekt öffnen**.

![Cursor + AEM](./images/cursorai2.png)

Wählen Sie den zuvor erstellten Ordner aus und klicken Sie auf **Öffnen**.

![Cursor + AEM](./images/cursorai3.png)

Klicken Sie **Ja, ich vertraue den Autoren**.

![Cursor + AEM](./images/cursorai4.png)

Sie sollten das dann sehen. Verwenden Sie den Tastaturbefehl `Cmd + Shift + J`, um die Cursor-Einstellungen zu öffnen. Sie sollten das dann sehen. Navigieren Sie zu **Tools und MCP**.

![Cursor + AEM](./images/cursorai5.png)

Klicken Sie auf **+ Neuer MCP-Server**.

![Cursor + AEM](./images/cursorai6.png)

Fügen Sie den folgenden MCP-Server zur Datei **mcp.json** hinzu. Möglicherweise sind bereits andere MCP-Server in dieser Datei angegeben. Entfernen Sie diese nicht und fügen Sie einfach die folgenden neuen Zeilen hinzu. Speichern Sie Ihre Änderungen.

```json
"aem": {
	"url": "https://mcp.adobeaemcloud.com/adobe/mcp/content"
	}
```

![Cursor + AEM](./images/cursorai7.png)

Wechseln Sie zurück zur Registerkarte **Cursoreinstellungen**. In der Liste der MCP **Server sollte nun ein Tool** aem) hinzugefügt werden. Klicken Sie auf **Verbinden**, um sich mit Ihrem Adobe-Konto zu authentifizieren.

![Cursor + AEM](./images/cursorai8.png)

Klicken Sie **Öffnen**, falls diese Meldung angezeigt wird. Anschließend sollten Sie sich in Ihrem Browser authentifizieren.

![Cursor + AEM](./images/cursorai9.png)

Nach erfolgreicher Authentifizierung sollten Sie Folgendes sehen.

![Cursor + AEM](./images/cursorai10.png)

Schließen Sie die **Cursor-Einstellungen** und **mcp.json**. Fügen Sie die folgende Aufforderung in den Chat ein und klicken Sie auf **Senden**.

```
I just created a new custom mcp server named 'aem'. what can I do with that?
```

![Cursor + AEM](./images/cursorai11.png)

Klicken Sie auf **Ausführen**.

![Cursor + AEM](./images/cursorai12.png)

Anschließend sollten Sie eine ähnliche Antwort sehen.

![Cursor + AEM](./images/cursorai13.png)

![Cursor + AEM](./images/cursorai14.png)

Wie Sie sehen können, werden ähnliche Funktionen über den MCP-Server in Cursor verfügbar gemacht, im Vergleich zu dem, was mit dem KI-Assistenten in der vorherigen Übung möglich war.

Geben Sie die folgende Eingabeaufforderung ein und klicken Sie auf **Senden**.

```javascript
List AEM Author instances
```

![Cursor + AEM](./images/cursorai15.png)

Sie sollten dann so etwas sehen. Suchen Sie nach der gewünschten Umgebung, geben Sie dann die folgende Eingabeaufforderung ein und klicken Sie auf **Senden**.

```javascript
use environment number X
```

![Cursor + AEM](./images/cursorai16.png)

Sie sollten das dann sehen.

![Cursor + AEM](./images/cursorai17.png)

Fügen Sie die folgende Eingabeaufforderung ein und klicken Sie auf **Senden**. Ersetzen Sie XXX in dieser Eingabeaufforderung durch die URL, die Sie in der vorherigen Übung kopiert haben.

```
On the page https://author-p185022-e1936676.adobeaemcloud.com/content/CitiSignal/fiber-max.html, please make the following changes:

- change the word 'winter' to 'summer'
- change the text 'be as fast as a leopard' to 'dominate your internet like a gorilla'
- change the image in the hero block to use the image 'citisignal_gorilla.png'
- change the text '99.9% network reliability' to '99.998% network reliability'
```

![Cursor + AEM](./images/cursorai18.png)

Nach 1-2 Minuten sollten Sie eine ähnliche Antwort erhalten. Kopieren Sie die URL und öffnen Sie die Seite in Ihrem Browser.

![Cursor + AEM](./images/cursorai19.png)

Sie sollten das dann sehen.

![Cursor + AEM](./images/cursorai20.png)

Geben Sie die folgende Eingabeaufforderung ein und klicken Sie auf **Senden**.

```javascript
promote the changes by creating a new launch and promoting it
```

![Cursor + AEM](./images/cursorai21.png)

Nach 1-2 Minuten wurden die Änderungen hochgestuft.

![Cursor + AEM](./images/cursorai22.png)

Sie können die Änderungen jetzt live auf Ihrer Website sehen.

![Cursor + AEM](./images/cursorai23.png)

Erkunden Sie auch die anderen Funktionen des AEM MCP-Servers.

## 1.6.2.2 Discovery Agent Cursor MCP Server-Setup

Verwenden Sie den Tastaturbefehl `Cmd + Shift + J`, um die Cursor-Einstellungen zu öffnen. Sie sollten das dann sehen. Navigieren Sie zu **Tools und MCP**. Klicken Sie auf **+ Neuer MCP-Server**.

![Cursor + AEM](./images/cursoraiz5.png)

Fügen Sie den folgenden MCP-Server zur Datei **mcp.json** hinzu. Möglicherweise sind bereits andere MCP-Server in dieser Datei angegeben. Entfernen Sie diese nicht und fügen Sie einfach die folgenden neuen Zeilen hinzu. Speichern Sie Ihre Änderungen.

```
,
"aem-discovery": {
	"url": "https://mcp.adobeaemcloud.com/adobe/mcp/discovery"
}
```

![Cursor + AEM](./images/cursoraiz7.png)

Wechseln Sie zurück zur Registerkarte **Cursoreinstellungen**. In der Liste der MCP **Server sollte nun ein Tool** aem) hinzugefügt werden. Klicken Sie auf **Verbinden**, um sich mit Ihrem Adobe-Konto zu authentifizieren.

![Cursor + AEM](./images/cursoraiz8.png)

Nach der Authentifizierung sollte Folgendes angezeigt werden.

![Cursor + AEM](./images/cursoraiz9.png)

Schließen Sie die **Cursor-Einstellungen** und **mcp.json**. Fügen Sie die folgende Aufforderung in den Chat ein und klicken Sie auf **Senden**.

```
I just created a new custom mcp server named 'aem-discovery'. what can I do with that?
```

![Cursor + AEM](./images/cursoraiz10.png)

```
for the environment https://author-pXXXXXX-eXXXXXXX.adobeaemcloud.com/, list all assets tagged with 'Spring 2026'
```

![Cursor + AEM](./images/cursoraiz11.png)

Sie sollten dann so etwas sehen.

![Cursor + AEM](./images/cursoraiz12.png)

## Nächste Schritte

Zurück zu [AEM und Agenten](./aemagents.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}