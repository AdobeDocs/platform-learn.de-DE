---
title: Implementieren von Brand Concierge auf Ihrer Website
description: Implementieren von Brand Concierge auf Ihrer Website
kt: 5342
doc-type: tutorial
source-git-commit: ea5fa4694205a94f63d277fdcf2018951fa31fbc
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 0%

---

# 1.4.2 Implementieren von Brand Concierge auf Ihrer Website

>[!IMPORTANT]
>
>Um diese Übung abzuschließen, benötigen Sie Zugriff auf eine funktionierende AEM Assets CS Author-Umgebung und eine AEM CS/EDS-Website.
>
>Wenn Sie keine solche Umgebung haben, navigieren Sie zu [Adobe Experience Manager Cloud Service und Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Folgen Sie den Anweisungen dort, und Sie haben Zugriff auf eine solche Umgebung.

>[!IMPORTANT]
>
>Wenn Sie zuvor ein AEM CS-Programm mit einer AEM Assets CS-Umgebung konfiguriert haben, kann es sein, dass Ihre AEM CS-Sandbox in den Ruhezustand versetzt wurde. Da der Ruhezustand einer solchen Sandbox 10-15 Minuten dauert, ist es ratsam, den Ruhezustand jetzt zu beenden, damit Sie nicht zu einem späteren Zeitpunkt warten müssen.

## 1.4.2.1 Konfigurieren Ihrer Website, um Brand Concierge anzuzeigen - AEM Author

Damit Brand Concierge auf Ihrer Website angezeigt wird, müssen Sie einen neuen benutzerdefinierten Block erstellen, der zu einer neuen Seite hinzugefügt werden muss, und Sie müssen sicherstellen, dass Ihre neue Seite zur Navigation Ihrer Website hinzugefügt wird.

Konfigurieren Sie nun die folgenden Elemente in dieser Reihenfolge:

- Erstellen Sie einen neuen benutzerdefinierten Block, mit dem Brand Concierge auf Ihrer Website geladen wird.
- Erstellen Sie eine neue Seite auf Ihrer Website für Brand Concierge.
- Verknüpfen Sie den neu erstellten benutzerdefinierten Block auf der neu erstellten Brand Concierge-Seite.
- Fügen Sie einen Verweis hinzu, um zur neu erstellten Brand Concierge-Seite in der Navigationskopfzeilendatei Ihrer Website zu navigieren.

### Neuen benutzerdefinierten Block erstellen

Um den neuen benutzerdefinierten Block zu erstellen, navigieren Sie zum GitHub-Repository, das mit Ihrer Website verknüpft ist.

![Block](./images/block1.png)

#### component-definition.json

Scrollen Sie nach unten, bis Sie die Datei **component-definition.json** sehen, und öffnen Sie sie

![Block](./images/block8.png)

Klicken Sie auf das **pencl**-Symbol, um mit der Bearbeitung der Datei zu beginnen.

![Block](./images/block8a.png)

Scrollen Sie nach unten, bis Sie die **Blöcke“**. Setzen Sie den Cursor unter die schließende Klammer der Komponente **Karten**

![Block](./images/block9.png)

Fügen Sie diesen Code ein und geben Sie **nach dem Codeblock ein** ein:

```json
{
  "title": "BrandConcierge",
  "id": "brandconcierge",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "BrandConcierge",
          "model": "brandconcierge"
        }
      }
    }
  }
},
```

Klicken Sie **Änderungen übernehmen…**.

![Block](./images/block10.png)

Klicken Sie **Änderungen übernehmen**.

![Block](./images/block10a.png)

#### component-models.json

Scrollen Sie nach unten, bis Sie die Datei **component-models.json** sehen, und klicken Sie auf das **Bleistiftsymbol**, um mit der Bearbeitung der Datei zu beginnen.

![Block](./images/block11.png)

Scrollen Sie nach unten, bis Sie das letzte Element sehen. Setzen Sie den Cursor neben die schließende Klammer der letzten Komponente.

![Block](./images/block12.png)

Geben Sie einen **ein,** drücken Sie dann die Eingabetaste, und fügen Sie in der nächsten Zeile diesen Code ein:

```json
{
  "id": "brandconcierge",
  "fields": []
}
```

Klicken Sie **Änderungen übernehmen…**.

![Block](./images/block13.png)

Klicken Sie **Änderungen übernehmen**.

![Block](./images/block13a.png)

#### component-filters.json

Scrollen Sie nach unten, bis Sie die Datei **component-filters.json** sehen, und klicken Sie auf das **Bleistiftsymbol**, um mit der Bearbeitung der Datei zu beginnen.

![Block](./images/block14.png)

Sie sollten das dann sehen.

![Block](./images/block14a.png)

Geben **unter** Abschnitt“ einen `,` ein und fügen Sie die ID Ihrer `"brandconcierge"` nach der aktuellen letzten Zeile ein.

Klicken Sie **Änderungen übernehmen…**.

![Block](./images/block15.png)

Klicken Sie **Änderungen übernehmen**.

![Block](./images/block15a.png)

#### brandconcierge.css

Beim Erstellen eines Blocks empfiehlt es sich, eine Datei für den Stil des Blocks zu erstellen. Sie sollte denselben Namen wie der Block aufweisen. Jetzt sollten Sie diese Datei erstellen, die wir vorerst leer lassen.

Wechseln Sie zum **blocks**-Ordner. Klicken Sie dann auf **Datei hinzufügen** und wählen Sie **Neue Datei erstellen** aus.

![Block](./images/css1.png)

Geben Sie in das Textfeld `brandconcierge/brandconcierge.css` ein. Die Datei kann vorerst leer bleiben. Klicken Sie **Änderungen übernehmen…**.

![Block](./images/css2.png)

Klicken Sie **Änderungen übernehmen**.

![Block](./images/css3.png)

#### brandconcierge.js

Beim Erstellen eines Blocks empfiehlt es sich, eine Datei für das JavaScript zu erstellen, das sich auf Ihren Block bezieht. Außerdem sollte sie denselben Namen wie der Block haben.

Klicken Sie **Datei hinzufügen** und wählen Sie **Neue Datei erstellen** aus.

![Block](./images/js1.png)

Geben Sie in das Textfeld `brandconcierge.js` ein. Die Datei kann vorerst leer bleiben. Klicken Sie **Änderungen übernehmen…**.

```javascript
export default function decorate(block) {
  block.setAttribute('id', 'brand-concierge-mount');
}
```

![Block](./images/js2.png)

Klicken Sie **Änderungen übernehmen**.

![Block](./images/js3.png)

### Neue Seite erstellen und neuen benutzerdefinierten Block verknüpfen

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png)

Klicken Sie anschließend auf der Registerkarte **Umgebungen** auf die **mit den drei Punkten** und anschließend auf **Details anzeigen**.

![AEMCS](./images/aemcs9.png)

Anschließend werden Ihre Umgebungsdetails angezeigt. Klicken Sie auf die URL Ihrer **Author**-Umgebung.

>[!NOTE]
>
>Möglicherweise befindet sich Ihre Umgebung im Ruhezustand. In diesem Fall müssen Sie zunächst den Ruhezustand Ihrer Umgebung aufheben.

![AEMCS](./images/aemcs10.png)

Anschließend sollte Ihre AEM-Autorenumgebung angezeigt werden. Navigieren Sie zu **Sites**.

![AEMCS](./images/block21.png)

Gehen Sie zu **CitiSignal**. Klicken Sie **Erstellen** und wählen Sie **Seite** aus.

![AEMCS](./images/block23.png)

Wählen Sie **Seite** aus und klicken Sie auf **Weiter**.

![AEMCS](./images/block24.png)

Geben Sie die folgenden Werte ein:

- Titel: **Brand Concierge**
- Name: **brandconcierge**
- Seitentitel: **Brand Concierge**

Klicken Sie auf **Erstellen**.

![AEMCS](./images/block25.png)

Wählen Sie **Öffnen** aus.

![AEMCS](./images/block22.png)

Sie sollten das dann sehen.

![AEMCS](./images/block26.png)

Klicken Sie in den leeren Bereich, um die Komponente **Abschnitt** auszuwählen. Klicken Sie dann im rechten Menü auf das Pluszeichen **+**.

![AEMCS](./images/block27.png)

Anschließend sollte der benutzerdefinierte Block in der Liste der verfügbaren Blöcke angezeigt werden. Zur Auswahl klicken.

![AEMCS](./images/block28.png)

Anschließend sollte dieser Seite ein leerer Block hinzugefügt werden. Dieser Block wird dynamisch mit den JavaScript-Bibliotheken geladen, die Sie im nächsten Schritt hinzufügen werden.

Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/block29.png)

Klicken **erneut auf** Veröffentlichen“.

![AEMCS](./images/block30.png)

Ihre neue Seite ist jetzt veröffentlicht und kann im nächsten Schritt zur Navigationskopfzeile hinzugefügt werden.

### Navigationskopfzeilendatei aktualisieren

Gehen Sie in Ihrer AEM Sites-Übersicht zu **CitiSignal** und aktivieren Sie das Kontrollkästchen für die Datei **Header/nav**. Klicken Sie auf **Bearbeiten**.

![AEMCS](./images/nav0.png)

Wählen Sie das **Text**-Feld im Vorschaubildschirm aus und klicken Sie dann auf das **Text**-Feld auf der rechten Bildschirmseite, um es zu bearbeiten.

![AEMCS](./images/nav0a.png)

Erstellen Sie eine neue Menüoption im Navigationsmenü mit dem `Brand Concierge`. Wählen Sie dann den Text **Brand Concierge** und klicken Sie auf das Symbol **link**.

![AEMCS](./images/nav1.png)

Geben Sie dies für das Feld **Pfad oder URL** `/content/CitiSignal/brandconcierge.html` und geben Sie `Brand Concierge` für das Feld **Titel** ein. Klicken Sie auf **Speichern**.

![AEMCS](./images/nav3.png)

Sie sollten dann diese haben. Klicken Sie auf **Fertig**.

![AEMCS](./images/nav4.png)

Sie sollten dann diese haben. Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/nav4a.png)

Klicken **erneut auf** Veröffentlichen“.

![AEMCS](./images/nav5.png)

Ihre neue Seite wird nun dem Menü hinzugefügt.

## 1.4.2.2 Konfigurieren Ihrer Website, um Brand Concierge anzuzeigen - GitHub

Nachdem Sie den Inhalt mit Ihrer AEM-Autorenumgebung aktualisiert haben, müssen Sie jetzt den Code im GitHub-Repository aktualisieren, der für Ihre Website verwendet wird.

### JavaScript-Bibliotheken

Die folgenden Bibliotheken sind erforderlich, um Brand Concierge auf Ihrer Website zu implementieren, die auf AEM CS/EDS ausgeführt wird:

- [styleconfigurations.js](./assets/styleconfigurations.js)
- [alloy.js](./assets/alloy.js)
- [brandconciergemain.js](./assets/brandconciergemain.js)

Laden Sie alle drei Dateien auf Ihren Desktop herunter.

![Brand Concierge](./images/aem0.png)

Gehen Sie zum GitHub-Projekt Ihrer AEM CS/EDS-Website. Navigieren Sie zu **scripts**.

![Brand Concierge](./images/aem1.png)

Klicken Sie auf **Datei hinzufügen** und wählen Sie dann **Dateien hochladen** aus.

![Brand Concierge](./images/aem3.png)

Klicken Sie **Dateien auswählen**.

![Brand Concierge](./images/aem3a.png)

Wählen Sie alle drei Dateien **styleConfigurations.js, alloy.js und brandconciergemain.js** von Ihrem Desktop aus und klicken Sie auf **Öffnen**.

![Brand Concierge](./images/aem4.png)

Klicken Sie **Änderungen übernehmen**.

![Brand Concierge](./images/aem5.png)

### head.html aktualisieren

Im vorherigen Schritt haben Sie drei neue Bibliotheken hochgeladen. Diese Bibliotheken müssen jetzt geladen werden, wenn Ihre Website geladen wird. Dazu müssen Verweise auf diese Dateien in der Datei „head.**&quot; hinzugefügt**.

Darüber hinaus müssen Sie auch Anweisungen in der Datei **head.html** bereitstellen, um sicherzustellen, dass die Bibliotheken in der richtigen Reihenfolge und auf richtige Weise geladen werden.

Gehen Sie dazu zum GitHub-Projekt Ihrer AEM CS/EDS-Website, indem Sie auf **Code** klicken.

![Brand Concierge](./images/aem6.png)

Scroll ein bisschen nach unten. Öffnen Sie die Datei **head.html**.

![Brand Concierge](./images/aem7.png)

Klicken Sie auf **Bleistiftsymbol**, um diese Datei zu bearbeiten.

![Brand Concierge](./images/aem8.png)

Sie sollten das dann sehen.

![Brand Concierge](./images/aem9.png)

Scrollen Sie nach unten zu Zeile 43 und fügen Sie Folgendes ein:

Im folgenden Code gibt es zwei Felder, die Sie aktualisieren müssen:

>[!IMPORTANT]
>
>- **datastreamId** ist derzeit auf „XXXXX“ festgelegt und muss durch die ID des Datenstroms ersetzt werden, den Sie im vorherigen Schritt erstellt haben.
>- **orgId** muss durch die IMS-Org-ID Ihrer Adobe Experience Cloud-Instanz ersetzt werden.

```javascript
<script src="/scripts/styleconfigurations.js"></script>

<script>
		!function (n, o) {
      o.forEach(function (o) {
        n[o] || ((n.__alloyNS = n.__alloyNS ||
          []).push(o), n[o] = function () {
            var u = arguments; return new Promise(
              function (i, l) { n[o].q.push([i, l, u]) })
          }, n[o].q = [])
      })
    }
      (window, ["alloy"]);
	</script>


<script src="/scripts/alloy.js"></script>

<script>
	alloy("configure", {
		defaultConsent: "in",
        edgeDomain: "edge.adobedc.net",
        edgeBasePath: "ee",
        datastreamId: "XXXXX", // replace datastreamId
        orgId: "--aepImsOrgId--", // replace ims org Id
        debugEnabled: true,
        idMigrationEnabled: false,
        thirdPartyCookiesEnabled: false,
        prehidingStyle: ".personalization-container { opacity: 0 !important }",
    });

window["alloy"]("sendEvent", {
    conversation: {
        fetchConversationalExperience: true
    }
}).then(result => {
    console.log("Conversation experience fetched", result);
    window["alloy"]("bootstrapConversationalExperience", {
        selector: "#brand-concierge-mount",
        src: "/scripts/brandconciergemain.js",
        stylingConfigurations: window.styleConfiguration,
        stickySession: true // create a sticky session cookie with expiration
    })
});
</script>
```

Klicken Sie **Änderung übernehmen…**.

![Brand Concierge](./images/aem10.png)

Klicken Sie **Änderung übernehmen**.

![Brand Concierge](./images/aem11.png)

Sie haben jetzt den erforderlichen Code aktualisiert, um die Bibliotheken auf Ihrer Website zu laden.

![Brand Concierge](./images/aem12.png)

## 1.4.2.3 Testen der Konfiguration

Sie können Ihre Änderungen auf Ihrer Website jetzt testen, indem Sie zu `main--citisignal-aem-accs--XXX.aem.page` oder `main--citisignal-aem-accs--XXX.aem.live` wechseln, nachdem Sie XXX durch Ihr GitHub-Benutzerkonto ersetzt haben, was in diesem Beispiel `woutervangeluwe` ist.

In diesem Beispiel lautet die vollständige URL wie folgt:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` und/oder `https://main--citisignal-aem-accs--woutervangeluwe.aem.live`.

Es kann einige Zeit dauern, bis alle Assets korrekt angezeigt werden, da sie zuerst veröffentlicht werden müssen.

Sie sollten das dann sehen. Auf **Brand Concierge**.

![Brand Concierge](./images/aem13.png)

Sie sollten dann diese Brand Concierge sehen, in der Sie Ihre Eingabeaufforderung eingeben können.

![Brand Concierge](./images/aem14.png)

Zurück zu [Brand Concierge](./brandconcierge.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}