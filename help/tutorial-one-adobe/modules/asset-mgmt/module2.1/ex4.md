---
title: AEM CS - Erweiterter benutzerdefinierter Block
description: AEM CS - Erweiterter benutzerdefinierter Block
kt: 5342
doc-type: tutorial
exl-id: 31fd1dea-70c9-4f82-87ad-16276ffa7f5b
source-git-commit: 179b83b733f3314280d307e5eee0db9600a173b0
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 0%

---

# 1.1.4 Erweiterter benutzerdefinierter Block

CTA In der vorherigen Übung haben Sie einen einfachen benutzerdefinierten Block mit dem Namen &quot;**&quot; konfiguriert** der Felder wie **Angebotstext**, **Angebotsbild** und **Angebotsbild** auf Ihrer Website anzeigt.

Sie können nun mit der Arbeit an diesem Block fortfahren.

![AEMCS](./images/nav7.png){zoomable="yes"}

## Gestalten 1.1.4.1 Blocks

Nachdem Sie nun über einen funktionierenden **Fiberoffer**-Block verfügen, können Sie Stile darauf anwenden.

Kehren Sie zu Visual Studio Code zurück und öffnen Sie den Ordner **Bausteine**. Es sollten jetzt mehrere Ordner angezeigt werden, die jeweils auf einen bestimmten Block verweisen. Um Ihren **FibreOffer**-Block zu erweitern, müssen Sie jetzt einen Ordner für Ihren benutzerdefinierten Block erstellen.

![AEMCS](./images/blockadv1.png){zoomable="yes"}

Wählen Sie den Ordner **Blöcke** und klicken Sie dann auf das Symbol **Neuen Ordner erstellen**.

![AEMCS](./images/blockadv2.png){zoomable="yes"}

Benennen Sie Ihren Ordner `fiberoffer` und drücken Sie **Eingabetaste**.

![AEMCS](./images/blockadv3.png){zoomable="yes"}

Wählen Sie den neuen Ordner **fiberoffer** und klicken Sie auf das Symbol **Neue Datei erstellen**.

![AEMCS](./images/blockadv4.png){zoomable="yes"}

Es wird jetzt eine neue Datei erstellt. Geben Sie den Namen **fiberoffer.js** ein und drücken Sie die Eingabetaste.

![AEMCS](./images/blockadv5.png){zoomable="yes"}

Sie können jetzt Blockdekoration implementieren, indem Sie die folgende JavaScript in die Datei &quot;**.js“**.

Speichern Sie die Datei.

```js
export default function decorate(block) {
  const offerText = block.children[0];
  const offerCTA = block.children[1];
  const offerImage = block.children[2];

  offerText.id = 'offerText';
  offerText.className = 'offerText';
  offerCTA.id = 'offerCTA';
  offerCTA.className = 'offerCTA';
  offerImage.id = 'offerImage';
  offerImage.className = 'offerImage';
}
```

![AEMCS](./images/blockadv6.png){zoomable="yes"}

Wählen Sie den neuen Ordner **fiberoffer** aus und klicken Sie erneut auf **Symbol Neue Datei**.

![AEMCS](./images/blockadv7.png){zoomable="yes"}

Es wird jetzt eine neue Datei erstellt. Geben Sie den Namen **fiberoffer.css** ein und drücken Sie die Eingabetaste.

![AEMCS](./images/blockadv8.png){zoomable="yes"}

Kopieren Sie den folgenden CSS-Code und fügen Sie ihn in die neu erstellte Datei ein.

```js
.offerText, .offerCTA, .offerImage{
    color: #14161A;
    font-size: 30px;
    padding: 0 0 24px;
    display: flex;
    flex-direction: column;
    margin: 1rem 0;
    text-align: center;
}
```

Speichern Sie Ihre Änderungen.

![AEMCS](./images/blockadv9.png){zoomable="yes"}

Sie haben jetzt mehrere Änderungen an Ihrem Projekt vorgenommen, die wieder in Ihr GitHub-Repository übertragen werden müssen. Öffnen Sie dazu „GitHub **Desktop**.

Anschließend sollten die beiden soeben bearbeiteten Dateien unter &quot;**&quot; angezeigt**. Überprüfen Sie Ihre Änderungen.

Geben Sie einen Namen für Ihren PR ein, `js css`. Klicken Sie **Auf Haupt übertragen**.

![Block](./images/blockadv10.png){zoomable="yes"}

Sie sollten das dann sehen. Klicken Sie auf **Push-Herkunft**.

![Block](./images/blockadv11.png){zoomable="yes"}

Navigieren Sie in Ihrem Browser zu Ihrem GitHub-Konto und zu dem Repository, das Sie für CitiSignal erstellt haben. Sie sollten dann etwas wie das hier sehen, das anzeigt, dass Ihre Änderungen empfangen wurden.

![Block](./images/blockadv12.png){zoomable="yes"}

Sie können nun die Änderungen an Ihrer Website anzeigen, indem Sie zu `main--citisignal--XXX.aem.page/us/en/` und/oder `main--citisignal--XXX.aem.live/us/en/` wechseln, nachdem Sie XXX durch Ihr GitHub-Benutzerkonto ersetzt haben, was in diesem Beispiel `woutervangeluwe` ist.

In diesem Beispiel lautet die vollständige URL wie folgt:
`https://main--citisignal--woutervangeluwe.aem.page/us/en/` und/oder `https://main--citisignal--woutervangeluwe.aem.live/us/en/`.

Sie sollten dies dann sehen, wenn der Stil auf Ihre Seite angewendet wird.

![Block](./images/blockadv13.png){zoomable="yes"}

## 1.1.4.2 Hinzufügen von Logik und Laden von Daten von einem externen Endpunkt

In dieser Übung konfigurieren Sie Adobe Web SDK im Rohformat und fordern das nächstbeste Angebot von Adobe Journey Optimizer Offer Decisioning an.

Um es deutlich zu sagen: Dies ist nicht als Best-Practice-Implementierung von Web SDK für AEM as a Cloud Service gedacht. In der nächsten Übung implementieren Sie die Datenerfassung mit einem speziellen Plug-in, das für diesen Zweck entwickelt wurde.

In dieser Übung sollen Ihnen einige grundlegende Dinge in JavaScript gezeigt werden, z. B. das Laden einer externen JS-Bibliothek, die Verwendung der Bibliothek **alloy.js**, das Senden einer Anfrage und mehr.

Die Bibliothek **alloy.js** ist die Bibliothek von Web SDK, die es ermöglicht, Anfragen von einer Website an Adobes Edge Network zu senden und von dort aus Programme wie Adobe Experience Platform, Adobe Analytics, Adobe Target und mehr.

Fügen Sie diesen Code unter dem vorherigen Code ein, den Sie für die Formatierung Ihres Blocks hinzugefügt haben:

```javascript
var script1 = document.createElement('script');
  script1.text = "!function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||[]).push(o),n[o]=function(){var u=arguments;return new Promise(function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}(window,['alloy']);"
  document.head.appendChild(script1);

  var script2 = document.createElement('script');
  script2.async = true;
  script2.src = "https://cdn1.adoberesources.net/alloy/2.14.0/alloy.min.js";
  document.head.appendChild(script2);

  alloy("configure", {
    "edgeConfigId": "045c5ee9-468f-47d5-ae9b-a29788f5948f",
    "orgId": "907075E95BF479EC0A495C73@AdobeOrg",
    "defaultConsent": "in"
  });
```

Sie sollten dann diese haben.

Das erste Skript-Tag (script1), das Sie hinzugefügt haben, ist eine Funktion, die von Web SDK verwendet wird und ein Fensterobjekt namens &quot;**&quot;**.

Das zweite Skript-Tag (script2) lädt asynchron die Bibliothek alloy.js aus dem CDN von Adobe.

Der dritte Code-Block konfiguriert im Wesentlichen das Legierungsobjekt, um Daten an eine bestimmte Adobe IMS-Organisation und einen Datenstrom zu senden.

Im Modul **Erste Schritte** haben Sie bereits einen Datenstrom mit dem Namen `--aepUserLdap-- - One Adobe Datastream` konfiguriert. Das Feld **edgeConfigId** im obigen Code verweist auf die ID des konfigurierten Datenstroms.

Das Feld „edgeConfigId **muss** geändert werden. In der nächsten Übung können Sie dies mit dem Plug-in **MarTech** tun.

![Block](./images/blockadv15.png){zoomable="yes"}

Du solltest das jetzt haben.

![Block](./images/blockadv14.png){zoomable="yes"}

Fügen Sie anschließend diesen Block unter dem vorherigen Code hinzu, den Sie hinzugefügt haben.

```javascript
var ECID = "";

  alloy("getIdentity")
    .then(function (result) {
      // The command succeeded.
      console.log("ECID:", result.identity.ECID);
      ECID = result.identity.ECID;
      getOffer(ECID);

    })
    .catch(function (error) {
      // The command failed.
      // "error" will be an error object with additional information.
    });
```

Dieser Codeblock wird zum Abrufen des Werts der Experience Cloud-ID (ECID) verwendet. Die ECID ist die eindeutige Gerätekennung Ihres Browsers.

Wie Sie im obigen Code sehen können, wird nach dem Abrufen der ECID eine andere Funktion aufgerufen. Diese Funktion wird als **getOffer()** bezeichnet, die Sie als Nächstes hinzufügen.

![Block](./images/blockadv16.png){zoomable="yes"}

Fügen Sie anschließend den folgenden Code unter dem folgenden Code hinzu:

```javascript
async function getOffer(ECID) {
  var url = "https://edge.adobedc.net/ee/irl1/v1/interact?configId=045c5ee9-468f-47d5-ae9b-a29788f5948f";

  var timestamp = new Date().toISOString();

  var offerRequest = {
    "events": [
      {
        "xdm": {
          "eventType": "decisioning.propositionDisplay",
          "timestamp": timestamp,
          "_experienceplatform": {
            "identification": {
              "core": {
                "ecid": ECID
              }
            }
          },
          "identityMap": {
            "ECID": [
              {
                "id": ECID
              }
            ]
          }
        },
        "query": {
          "personalization": {
            "schemas": [
              "https://ns.adobe.com/personalization/default-content-item",
              "https://ns.adobe.com/personalization/html-content-item",
              "https://ns.adobe.com/personalization/json-content-item",
              "https://ns.adobe.com/personalization/redirect-item",
              "https://ns.adobe.com/personalization/ruleset-item",
              "https://ns.adobe.com/personalization/message/in-app",
              "https://ns.adobe.com/personalization/message/content-card",
              "https://ns.adobe.com/personalization/dom-action"
            ],
            "decisionScopes": [
              "eyJ4ZG06YWN0aXZpdHlJZCI6ImRwczpvZmZlci1hY3Rpdml0eToxYTI3ODk3NzAzYTY5NWZmIiwieGRtOnBsYWNlbWVudElkIjoiZHBzOm9mZmVyLXBsYWNlbWVudDoxYTI0ZGM2MWJmYjJlMjIwIn0=",
              "eyJ4ZG06YWN0aXZpdHlJZCI6ImRwczpvZmZlci1hY3Rpdml0eToxYTI3ODk3NzAzYTY5NWZmIiwieGRtOnBsYWNlbWVudElkIjoiZHBzOm9mZmVyLXBsYWNlbWVudDoxYTI0ZGM0MzQyZjJlMjFlIn0="
            ]
          }
        }
      }
    ]
  }

  try {
    const response = await fetch(url, {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(offerRequest),
    });

    if (response.status === 200) {
      var body = await response.json();
      console.log("Offer Decisioning Response: ", body);

      const decisions = body["handle"];

      decisions.forEach(decision => {
        if (decision["type"] == "personalization:decisions") {
          console.log("Offer Decisioning decision detail: ", decision);
          const payloads = decision["payload"];

          if (payloads === undefined || payloads.length == 0) {
            //do nothing
          } else {
            payloads.forEach(payload => {
              if (payload["placement"]["name"] == "Web - Image") {
                console.log("Web-Image payload");
                const items = payload["items"];
                items.forEach(item => {
                  if (item["id"].includes("dps:fallback-offer")) {
                    console.log("Item details: ", item);
                    const deliveryURL = item["data"]["deliveryURL"];

                    document.querySelector("#offerImage").innerHTML = "<img style='max-width:100%;' src='" + item["data"]["deliveryURL"] + "'/>";
                  } else if (item["id"].includes("dps:personalized-offer")) {
                    console.log("Item details: ", item);
                    const deliveryURL = item["data"]["deliveryURL"];
                    console.log("Web-Image Personalized Offer Content: ", deliveryURL)

                    document.querySelector("#offerImage").innerHTML = "<img style='max-width:100%;' src='" + item["data"]["deliveryURL"] + "'/>";
                  }
                });
              } else if (payload["placement"]["name"] == "Web - JSON") {
                console.log("Web-JSON payload");
                const items = payload["items"];
                items.forEach(item => {
                  if (item["id"].includes("dps:fallback-offer")) {
                    const content = JSON.parse(item["data"]["content"]);

                    console.log("Web-JSON Fallback Content: ", content)

                    document.querySelector("#offerText").innerHTML = content.text;
                    document.querySelector("#offerCTA").innerHTML = content.cta;
                  } else if (item["id"].includes("dps:personalized-offer")) {
                    const content = JSON.parse(item["data"]["content"]);

                    console.log("Web-JSON Personalized Offer Content: " + content);

                    document.querySelector("#offerText").innerHTML = content.text;
                    document.querySelector("#offerCTA").innerHTML = content.cta;
                  }
                });
              }
            });
          }
          document.querySelector("#offerImage").style.display = "block";
          document.querySelector("#offerText").style.display = "block";
          document.querySelector("#offerCTA").style.display = "block";
        }
      });
    } else {
      console.warn("Offer Decisioning Response unsuccessful:", response.body);
    }
  } catch (error) {
    console.error("Error when getting Offer Decisioning Response:", error);
  }
}
```

Es ist sehr wichtig, dass dieser Code-Block unter der schließenden Klammer eingefügt wird, die Sie in diesem Beispiel in Zeile 42 sehen können. Der Code, den Sie gerade eingefügt haben, ist eine separate Funktion, die ihre eigene Position in dieser Datei benötigt und nicht in der obigen (**)** verschachtelt werden kann.

![Block](./images/blockadv17.png){zoomable="yes"}

Der soeben eingefügte Code-Block simuliert eine Anfrage, die normalerweise von Web SDK/alloy.js gestellt würde. In diesem Beispiel **eine &quot;**&quot;-Anfrage an **edge.adobedc.net**.

In der Anfrage werden zwei **Entscheidungsumfänge** angegeben, in denen Adobe Journey Optimizer Offer Decisioning aufgefordert wird, eine Entscheidung darüber vorzulegen, welches Angebot von dieser ECID angezeigt werden muss.

Sobald die Antwort eingegangen ist, analysiert dieser Code die Antwort und filtert Dinge wie die URL des anzuzeigenden Bildes und auch die JSON-Antwort heraus, die Dinge wie den Angebotstext und die CTA enthält. Danach werden diese auf der Website angezeigt.

Denken Sie daran: Dieser Ansatz wird nur für Aktivierungszwecke verwendet und ist nicht die Best Practice-Methode zur Implementierung der Datenerfassung.

Speichern Sie Ihre Änderungen. Öffnen Sie dann **GitHub Desktop**, geben Sie Ihrem PR einen Namen und klicken Sie auf **Zum Haupt übertragen**.

![Block](./images/blockadv18.png){zoomable="yes"}

Klicken Sie anschließend auf **Push-Herkunft**.

![Block](./images/blockadv19.png){zoomable="yes"}

Sie können nun die Änderungen an Ihrer Website anzeigen, indem Sie zu `main--citisignal--XXX.aem.page/us/en/` und/oder `main--citisignal--XXX.aem.live/us/en/` wechseln, nachdem Sie XXX durch Ihr GitHub-Benutzerkonto ersetzt haben, was in diesem Beispiel `woutervangeluwe` ist.

In diesem Beispiel lautet die vollständige URL wie folgt:
`https://main--citisignal--woutervangeluwe.aem.page/us/en/` und/oder `https://main--citisignal--woutervangeluwe.aem.live/us/en/`.

Sie sollten das dann sehen.

![Block](./images/blockadv20.png){zoomable="yes"}

Nächster Schritt: [MarTech-Plug-in für AEM Edge Delivery Services](./ex5.md){target="_blank"}

Zurück zu [Adobe Experience Manager Cloud Service und Edge Delivery Services](./aemcs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
