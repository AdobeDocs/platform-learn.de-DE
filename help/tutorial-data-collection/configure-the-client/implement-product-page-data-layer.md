---
title: Implementieren einer Datenschicht auf einer Produktseite
description: Implementieren einer Datenschicht auf einer Produktseite
exl-id: 0debf34a-48d4-4029-b790-7fd78865c334
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---

# Implementieren einer Datenschicht auf einer Produktseite

Für dieses Tutorial implementieren Sie die Adobe Client Data Layer für eine typische E-Commerce-Website. Wenn Sie dies noch nicht getan haben, lesen Sie bitte [Verwendung der Adobe Client-Datenschicht](how-to-use-the-adobe-client-data-layer.md) Lernen Sie zunächst die Adobe Client-Datenschicht kennen.

Nehmen wir an, der Benutzer durchsucht Ihre Produkte und klickt auf eine Schaumwalze, um mehr zu erfahren. Der Benutzer landet auf der Detailseite der Schaumstoffwalze.

## Einfache Produktdetailseite erstellen

1. Kopieren Sie den folgenden Code und fügen Sie ihn in eine neue HTML-Datei ein und speichern Sie ihn auf Ihrem Computer.

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

Innerhalb des `<head>` Tag gibt es eine `<script>` -Tag. Hier platzieren Sie Ihren JavaScript-Code. Obwohl es nicht erforderlich ist, die `<script>` -Tag in `<head>` Container, wird dies empfohlen. Dadurch wird sichergestellt, dass Daten so bald wie möglich für die Datenschicht verfügbar sind, um eine Vielzahl von Anwendungsfällen zu unterstützen.

## Hinzufügen der Adobe-Datenschicht

1. Innerhalb des `<script>` Tag hinzufügen, fügen Sie diesen Code hinzu, der die `adobeDataLayer` -Array und sendet dann die entsprechenden Ereignis- und Dateninformationen in das -Array. Die Daten entsprechen dem XDM-Schema [Sie haben zuvor](../configure-the-server/create-a-schema.md).

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

In diesem Beispiel haben Sie zwei Push-Benachrichtigungen an die Datenschicht gesendet, die jeweils eine `event` Schlüssel. Einschließen einer `event` -Schlüssel kommuniziert nicht nur, welches Ereignis auf der Seite aufgetreten ist, sondern erleichtert es dem Marketing-Experten, geeignete Regeln innerhalb von Tags zu erstellen.

Beim ersten Push an die Datenschicht werden Listener (Tag-Regeln) darüber informiert, dass der Benutzer die Seite angezeigt hat. Außerdem werden der Datenschicht der Seitenname und der Website-Abschnitt hinzugefügt.

Beim zweiten Push an die Datenschicht werden Listener (Tags-Regeln) benachrichtigt, dass der Benutzer ein Produkt angezeigt hat. Außerdem werden Produktinformationen zur Datenschicht hinzugefügt.

## Code für das Hinzufügen zum Warenkorb hinzufügen

In diesem Tutorial verfolgen Sie, wann der Benutzer auf die [!UICONTROL Zum Warenkorb hinzufügen] Schaltfläche.

1. Kopieren Sie diesen Code und fügen Sie ihn nach dem Datenschichtcode ein. Die Funktion wird aufgerufen, wenn der Benutzer auf die [!UICONTROL Zum Warenkorb hinzufügen] Schaltfläche.

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

Diese Funktion prüft zunächst, ob für einen Benutzer bereits ein Warenkorb vorhanden ist.  Wenn der Warenkorb nicht vorhanden ist, wird eine `cartOpened` -Ereignis an die Datenschicht übergeben. Später wird ein `productAddedToCart` -Ereignis in die Datenschicht ein. Die Produktinformationen sind bereits in der Datenschicht vorhanden, sodass Sie sie nicht erneut hinzufügen müssen.

## Attribut zum Hinzufügen zur Schaltfläche &quot;Warenkorb&quot;hinzufügen

1. Hinzufügen einer `onclick` -Attribut [!UICONTROL Zum Warenkorb hinzufügen] -Schaltfläche, die die neue `onAddToCartClick` -Funktion.

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

## Code zum App-Download-Tracking hinzufügen

Eine letzte zu verfolgende Maßnahme ist, wenn der Benutzer auf die _[!UICONTROL App herunterladen]_ Link.

1. Kopieren Sie dazu diesen Code und fügen Sie ihn unterhalb des Codes zum Hinzufügen zum Warenkorb ein. Diese Funktion wird aufgerufen, wenn der Benutzer auf die _[!UICONTROL App herunterladen]_ Link.

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

## Attribut zum Herunterladen des App-Links hinzufügen

1. Hinzufügen einer `onclick` -Attribut [!UICONTROL App herunterladen] Link, der die neue `onDownloadAppClick` -Funktion.

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

[Weiter: ](create-a-tags-property-and-install-extensions.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
