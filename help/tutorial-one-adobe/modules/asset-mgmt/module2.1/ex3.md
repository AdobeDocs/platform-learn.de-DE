---
title: AEM CS - Benutzerdefinierter Standardblock
description: AEM CS - Benutzerdefinierter Standardblock
kt: 5342
doc-type: tutorial
exl-id: 57c08a88-d885-471b-ad78-1dba5992da9d
source-git-commit: 7537cd4d4ca6bc25afcb8f61a736498b0c297850
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 2%

---

# 1.1.3 Entwickeln eines einfachen benutzerdefinierten Bausteins

## Einrichten 1.1.3.1 lokalen Entwicklungsumgebung

Wechseln Sie zu [https://desktop.github.com/download/](https://desktop.github.com/download/){target="_blank"}, laden Sie (GitHub **) herunter und installieren Sie**.

![Block](./images/block1.png){zoomable="yes"}

Sobald GitHub Desktop installiert ist, wechseln Sie zum GitHub-Repository, das Sie in der vorherigen Übung erstellt haben. Klicken Sie auf **&lt;> Code** dann auf **Mit GitHub Desktop öffnen**.

![Block](./images/block2.png){zoomable="yes"}

Ihr GitHub-Repository wird dann in GitHub Desktop geöffnet. Sie können auch den **Lokaler Pfad** ändern. Klicken Sie **Klonen**.

![Block](./images/block3.png){zoomable="yes"}

Ein lokaler Ordner wird jetzt erstellt.

![Block](./images/block4.png){zoomable="yes"}

Öffnen Sie Visual Studio Code. Navigieren Sie **Datei** > **Ordner öffnen**.

![Block](./images/block5.png){zoomable="yes"}

Wählen Sie den Ordner aus, der von Ihrem GitHub-Setup für **Citisignal** verwendet wird.

![Block](./images/block6.png){zoomable="yes"}

Sie sehen nun, dass der Ordner in Visual Studio Code geöffnet ist und Sie nun bereit sind, einen neuen Block zu erstellen.

![Block](./images/block7.png){zoomable="yes"}

## 1.1.3.2 Erstellen eines einfachen benutzerdefinierten Blocks

Adobe empfiehlt, Bausteine in einem dreistufigen Ansatz zu entwickeln:

- Erstellen Sie die Definition und das Modell für den Block, überprüfen Sie ihn und bringen Sie ihn in die Produktion.
- Erstellen Sie Inhalte mit dem neuen Block.
- Implementierung der Dekoration und Stile für den neuen Block.

### component-definition.json

Öffnen Sie in Visual Studio Code die Datei **component-definition.json**.

![Block](./images/block8.png){zoomable="yes"}

Scrollen Sie nach unten, bis Sie die Komponente **Zitat** sehen. Setzen Sie den Cursor neben die schließende Klammer der letzten Komponente.

![Block](./images/block9.png){zoomable="yes"}

Fügen Sie diesen Code ein und geben Sie **nach dem Codeblock ein** ein:

```json
{
  "title": "FiberOffer",
  "id": "fiberoffer",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "FiberOffer",
          "model": "fiberoffer",
          "offerText": "<p>Fiber will soon be available in your region!</p>",
          "offerCallToAction": "Get your offer now!",
          "offerImage": ""
        }
      }
    }
  }
}
```

Speichern Sie Ihre Änderungen.

![Block](./images/block10.png){zoomable="yes"}

### component-models.json

Öffnen Sie in Visual Studio Code die Datei **component-models.json**.

![Block](./images/block11.png){zoomable="yes"}

Scrollen Sie nach unten, bis Sie das letzte Element sehen. Setzen Sie den Cursor neben die schließende Klammer der letzten Komponente.

![Block](./images/block12.png){zoomable="yes"}

Geben Sie einen **ein,** drücken Sie dann die Eingabetaste, und fügen Sie in der nächsten Zeile diesen Code ein:

```json
{
  "id": "fiberoffer",
  "fields": [
     {
       "component": "richtext",
       "name": "offerText",
       "value": "",
       "label": "Offer Text",
       "valueType": "string"
     },
     {
       "component": "richtext",
       "valueType": "string",
       "name": "offerCallToAction",
       "label": "Offer CTA",
       "value": ""
     },
     {
       "component": "reference",
       "valueType": "string",
       "name": "offerImage",
       "label": "Offer Image",
        "multi": false
     }
   ]
}
```

Speichern Sie Ihre Änderungen.

![Block](./images/block13.png){zoomable="yes"}

### component-filters.json

Öffnen Sie in Visual Studio Code die Datei **component-filters.json**.

![Block](./images/block14.png){zoomable="yes"}

Geben **unter** Abschnitt“ einen **,** und die ID Ihrer Komponente **Fiberoffer** nach der aktuellen letzten Zeile ein.

Speichern Sie Ihre Änderungen.

![Block](./images/block15.png){zoomable="yes"}

## 1.1.3.3 Übertragen Sie Ihre Änderungen

Sie haben jetzt mehrere Änderungen an Ihrem Projekt vorgenommen, die wieder in Ihr GitHub-Repository übertragen werden müssen. Öffnen Sie dazu „GitHub **Desktop**.

Anschließend sollten die 3 Dateien angezeigt werden, die Sie gerade unter &quot;**&quot; bearbeitet**. Überprüfen Sie Ihre Änderungen.

![Block](./images/block16.png){zoomable="yes"}

Geben Sie einen Namen für Ihren PR ein, `Fiber Offer custom block`. Klicken Sie **Auf Haupt übertragen**.

![Block](./images/block17.png){zoomable="yes"}

Sie sollten das dann sehen. Klicken Sie auf **Push-Herkunft**.

![Block](./images/block18.png){zoomable="yes"}

Nach einigen Sekunden wurden Ihre Änderungen an Ihr GitHub-Repository gepusht.

![Block](./images/block19.png){zoomable="yes"}

Navigieren Sie in Ihrem Browser zu Ihrem GitHub-Konto und zu dem Repository, das Sie für CitiSignal erstellt haben. Sie sollten dann etwas wie das hier sehen, das anzeigt, dass Ihre Änderungen empfangen wurden.

![Block](./images/block20.png){zoomable="yes"}

## 1.1.3.4 Hinzufügen eines Blocks zu einer Seite

Nachdem Sie nun Ihren einfachen Zitatblock definiert und an das CitiSignal-Projekt übergeben haben, können Sie einen **fiberoffer**-Block zu einer vorhandenen Seite hinzufügen.

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Klicken Sie anschließend auf der Registerkarte **Umgebungen** auf die **mit den drei Punkten** und anschließend auf **Details anzeigen**.

![AEMCS](./images/aemcs9.png){zoomable="yes"}

Anschließend werden Ihre Umgebungsdetails angezeigt. Klicken Sie auf die URL Ihrer **Author**-Umgebung.

>[!NOTE]
>
>Möglicherweise befindet sich Ihre Umgebung im Ruhezustand. In diesem Fall müssen Sie zunächst den Ruhezustand Ihrer Umgebung aufheben.

![AEMCS](./images/aemcs10.png){zoomable="yes"}

Anschließend sollte Ihre AEM-Autorenumgebung angezeigt werden. Navigieren Sie zu **Sites**.

![AEMCS](./images/block21.png){zoomable="yes"}

Gehen Sie **CitiSignal** > **us** > **en**.

![AEMCS](./images/block22.png){zoomable="yes"}

Klicken Sie **Erstellen** und wählen Sie **Seite** aus.

![AEMCS](./images/block23.png){zoomable="yes"}

Wählen Sie **Seite** aus und klicken Sie auf **Weiter**.

![AEMCS](./images/block24.png){zoomable="yes"}

Geben Sie die folgenden Werte ein:

- Titel: **CitiSignal Fibre**
- Name: **citsignal-fiber**
- Seitentitel: **CitiSignal Fibre**

Klicken Sie auf **Erstellen**.

![AEMCS](./images/block25.png){zoomable="yes"}

Sie sollten das dann sehen.

![AEMCS](./images/block26.png){zoomable="yes"}

Klicken Sie in den leeren Bereich, um die Komponente **Abschnitt** auszuwählen. Klicken Sie dann im rechten Menü auf das Pluszeichen **+**.

![AEMCS](./images/block27.png){zoomable="yes"}

Anschließend sollte der benutzerdefinierte Block in der Liste der verfügbaren Blöcke angezeigt werden. Zur Auswahl klicken.

![AEMCS](./images/block28.png){zoomable="yes"}

CTA Anschließend werden Felder wie **Angebotstext**, **Angebotsbild** und **Angebotsbild** zum Editor hinzugefügt. Klicken Sie im Feld **Angebotsbild** auf **+ Hinzufügen**, um ein Bild auszuwählen.

![AEMCS](./images/block29.png){zoomable="yes"}

Sie sollten das dann sehen. Klicken, um den Ordner **Citisignal** zu öffnen.

![AEMCS](./images/blockpub1.png){zoomable="yes"}

Wählen Sie das Bild **product-enrichment-1.png** aus. Klicken Sie auf **Auswählen**.

![AEMCS](./images/blockpub2.png){zoomable="yes"}

Sie sollten dann diese haben. Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/blockpub3.png){zoomable="yes"}

Klicken **erneut auf** Veröffentlichen“.

![AEMCS](./images/blockpub4.png){zoomable="yes"}

Ihre neue Seite wurde jetzt veröffentlicht.

## 1.1.3.5 Hinzufügen einer neuen Seite zum Navigationsmenü

AEM Sites Gehen Sie in der Übersicht zu **CitiSignal** > **Fragments** und aktivieren Sie das Kontrollkästchen für **Header**. Klicken Sie auf **Bearbeiten**.

![AEMCS](./images/nav0.png){zoomable="yes"}

Fügen Sie eine Menüoption zum Navigationsmenü mit dem `Fiber` hinzu. Wählen Sie den Text **Faser** und klicken Sie auf das **link**-Symbol.

![AEMCS](./images/nav1.png){zoomable="yes"}

Geben Sie dies für die **&#x200B;**&#x200B;URL`/us/en/citisignal-fiber` ein und klicken Sie zum Bestätigen auf das Symbol **V** .

![AEMCS](./images/nav3.png){zoomable="yes"}

Sie sollten dann diese haben. Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/nav4.png){zoomable="yes"}

Klicken **erneut auf** Veröffentlichen“.

![AEMCS](./images/nav5.png){zoomable="yes"}

Sie können nun die Änderungen an Ihrer Website anzeigen, indem Sie zu `main--citisignal--XXX.aem.page/us/en/` und/oder `main--citisignal--XXX.aem.live/us/en/` wechseln, nachdem Sie XXX durch Ihr GitHub-Benutzerkonto ersetzt haben, was in diesem Beispiel `woutervangeluwe` ist.

In diesem Beispiel lautet die vollständige URL wie folgt:
`https://main--citisignal--woutervangeluwe.aem.page/us/en/` und/oder `https://main--citisignal--woutervangeluwe.aem.live/us/en/`.

Sie sollten das dann sehen. Klicken Sie auf **Faser**.

![AEMCS](./images/nav6.png){zoomable="yes"}

Hier finden Sie Ihren grundlegenden benutzerdefinierten Block, der jetzt auf der Website gerendert wird.

![AEMCS](./images/nav7.png){zoomable="yes"}

Nächster Schritt: [Erweiterter benutzerdefinierter Block](./ex5.md){target="_blank"}

Zurück zu [Adobe Experience Manager Cloud Service und Edge Delivery Services](./aemcs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
