---
title: Implementieren einer Datenschicht auf einer Produktseite
description: Implementieren einer Datenschicht auf einer Produktseite
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: a72011a5-ea9c-45df-a0f3-5eb40bc99d3f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Implementieren einer Datenschicht auf einer Produktseite

Für dieses Tutorial implementieren Sie die Adobe Client Data Layer für eine typische E-Commerce-Website. Wenn Sie dies noch nicht getan haben, lesen Sie bitte [Verwendung der Adobe Client-Datenschicht](how-to-use-the-adobe-client-data-layer.md) zunächst, um zu verstehen, wie die Adobe Client-Datenschicht funktioniert.

Nehmen wir an, der Benutzer durchsucht Ihre Produkte und klickt auf eine Schaumwalze, um mehr zu erfahren. Der Benutzer landet auf der Detailseite der Schaumstoffwalze.

Hier finden Sie die HTML für Ihre einfache Produktdetailseite:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      // Code will go here.
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button">Add to cart</button>
    <a href="https://example.com/download">Download the app</a>
  </body>
</html>
```

Wie Sie vielleicht bemerkt haben, befindet sich im `<head>` Tag gibt es eine `<script>` -Tag. Hier platzieren Sie Ihren JavaScript-Code. Es ist nicht erforderlich, die `<script>` Tag in `<head>`, aber das schnellstmögliche Verschieben von Daten in die Datenschicht stellt sicher, dass es für Marketing-Experten schnell verfügbar ist, Daten an Adobe Experience Platform zu senden, bevor der Benutzer die Seite verlässt.

Innerhalb des `<script>` -Tag, beginnen Sie mit der Erstellung der `adobeDataLayer` -Array und dann das Pushen der entsprechenden Ereignis- und Dateninformationen in das -Array. Die Daten entsprechen dem XDM-Schema [Sie haben zuvor](../configure-the-server/create-a-schema.md).

```js
window.adobeDataLayer = window.adobeDataLayer || [];
window.adobeDataLayer.push({
  "event": "pageViewed",
  "web": {
    "webPageDetails": {
      "name": "Foam Roller",
      "siteSection": "Equipment"
    },
  }
});
window.adobeDataLayer.push({
  "event": "productViewed",
  "productListItems": [
    {
      "SKU": "eqfr08",
      "currencyCode": "USD",
      "name": "Foam Roller",
      "priceTotal": 18.95
    }
  ]
});
```

In diesem Beispiel haben Sie zwei Push-Benachrichtigungen an die Datenschicht gesendet, die jeweils eine `event` Schlüssel. Einschließen einer `event` -Schlüssel kommuniziert nicht nur, welches Ereignis auf der Seite aufgetreten ist, sondern erleichtert es dem Marketing-Experten, geeignete Regeln innerhalb von Adobe Experience Platform-Tags zu erstellen.

Beim ersten Push an die Datenschicht werden Listener (Tags-Regeln) benachrichtigt, dass der Benutzer die Seite angezeigt hat. Außerdem werden der Datenschicht der Seitenname und der Website-Abschnitt hinzugefügt.

Beim zweiten Push an die Datenschicht werden Listener (Tags-Regeln) benachrichtigt, dass der Benutzer ein Produkt angezeigt hat. Außerdem werden Produktinformationen zur Datenschicht hinzugefügt.

## Zum Warenkorb hinzufügen

Sie möchten wahrscheinlich auch verfolgen, wann der Benutzer auf die [!UICONTROL Zum Warenkorb hinzufügen] Schaltfläche.

Erstellen Sie dazu eine Funktion, die aufgerufen wird, wenn der Benutzer auf die [!UICONTROL Zum Warenkorb hinzufügen] Schaltfläche.

```js
window.onAddToCartClick = function() {
  // In a real implementation, you would change this condition to 
  // only pass if a cart doesn't already exist. You would typically 
  // do this by checking a cookie or variable value.
  if (true) {
    window.adobeDataLayer.push({
      "event": "cartOpened",
    });
  }
  window.adobeDataLayer.push({
    "event": "productAddedToCart"
  });
};
```

Wenn diese Funktion aufgerufen wird, prüft sie zunächst, ob für einen Benutzer bereits ein Warenkorb vorhanden ist. In der Regel würde dies durch Überprüfen erfolgen, ob ein bestimmtes Cookie oder eine bestimmte Variable vorhanden ist. Wenn der Warenkorb nicht vorhanden ist, wird ein `cartOpened` -Ereignis in die Datenschicht ein. Anschließend drücken Sie eine `productAddedToCart` -Ereignis in die Datenschicht ein. Die Produktinformationen sind bereits in der Datenschicht vorhanden, sodass Sie sie nicht erneut hinzufügen müssen.

Hinzufügen einer `onclick` -Attribut [!UICONTROL Zum Warenkorb hinzufügen] -Schaltfläche, die die neue `onAddToCartClick` -Funktion.

Das Ergebnis Ihrer HTML-Seite sollte wie folgt aussehen:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      window.adobeDataLayer = window.adobeDataLayer || [];
      window.adobeDataLayer.push({
        "event": "pageViewed",
        "web": {
          "webPageDetails": {
            "name": "Foam Roller",
            "siteSection": "Equipment"
          },
        },
        "productListItems": [
          {
            "SKU": "eqfr08",
            "currencyCode": "USD",
            "name": "Foam Roller",
            "priceTotal": 18.95
          }
        ]
      });
      window.adobeDataLayer.push({
        "event": "productViewed"
      });
      window.onAddToCartClick = function() {
        // In a real implementation, you would change this condition to 
        // only pass if a cart doesn't already exist. You would typically 
        // do this by checking a cookie or variable value.
        if (true) {
          window.adobeDataLayer.push({
            "event": "cartOpened",
          });
        }
        window.adobeDataLayer.push({
          "event": "productAddedToCart"
        });
      };
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button" onclick="onAddToCartClick()">Add to cart</button>
    <a href="https://example.com/download">Download the app</a>
  </body>
</html>
```

## App herunterladen

Eine letzte Möglichkeit besteht darin, nachzuverfolgen, wann der Benutzer auf die _[!UICONTROL App herunterladen]_ Link.

Erstellen Sie dazu eine Funktion, die aufgerufen wird, wenn der Benutzer auf die _[!UICONTROL App herunterladen]_ Link.

```js
window.onDownloadAppClick = function(event) {
  window.adobeDataLayer.push({
    "event": "downloadAppClicked",
    "eventInfo": {
      "web": {
        "webInteraction": {
          "URL": "https://example.com/download",
          "name": "App Download",
          "type": "download"
        }
      }
    }
  });
};
```

In diesem Fall werden die Informationen zum Link in eine `eventInfo` Schlüssel. Wie in [Verwendung der Adobe Client-Datenschicht](how-to-use-the-adobe-client-data-layer.md), weist die Datenschicht an, diese Daten mit dem Ereignis zu kommunizieren, jedoch _not_ die Daten in der Datenschicht beibehalten. Bei einem Link-Klick ist es nicht nützlich, Informationen über den angeklickten Link zur Datenschicht hinzuzufügen, da er sich nicht auf die Seite als Ganzes bezieht und nicht auf andere Ereignisse anwendbar ist, die auftreten können.

Hinzufügen einer `onclick` -Attribut [!UICONTROL App herunterladen] Link, der die neue `onDownloadAppClick` -Funktion.

Das Ergebnis Ihrer HTML-Seite sollte wie folgt aussehen:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      window.adobeDataLayer = window.adobeDataLayer || [];
      window.adobeDataLayer.push({
        "event": "pageViewed",
        "web": {
          "webPageDetails": {
            "name": "Foam Roller",
            "siteSection": "Equipment"
          },
        },
        "productListItems": [
          {
            "SKU": "eqfr08",
            "currencyCode": "USD",
            "name": "Foam Roller",
            "priceTotal": 18.95
          }
        ]
      });
      window.adobeDataLayer.push({
        "event": "productViewed"
      });
      window.onAddToCartClick = function() {
        // In a real implementation, you would change this condition to 
        // only pass if a cart doesn't already exist. You would typically 
        // do this by checking a cookie or variable value.
        if (true) {
          window.adobeDataLayer.push({
            "event": "cartOpened",
          });
        }
        window.adobeDataLayer.push({
          "event": "productAddedToCart"
        });
      };
      window.onDownloadAppClick = function() {
        window.adobeDataLayer.push({
          "event": "downloadAppClicked",
          "eventInfo": {
            "web": {
              "webInteraction": {
                "URL": "https://example.com/download",
                "name": "App Download",
                "type": "download"
              }
            }
          }
        });
      };
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button" onclick="onAddToCartClick()">Add to cart</button>
    <a href="https://example.com/download" onclick="onDownloadAppClick()">Download the app</a>
  </body>
</html>
```
