---
title: Erste Schritte mit Firefly Services
description: Erfahren Sie, wie Sie Postman und Adobe I/O verwenden, um Adobe Firefly Services-APIs abzufragen
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: c5a80b87ac8e997922cb8c69b4180c4220dd9862
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 0%

---

# 1.1.1 Erste Schritte mit Firefly Services

Erfahren Sie, wie Sie Postman und Adobe I/O verwenden, um Adobe Firefly Services-APIs abzufragen.

## Voraussetzungen für 1.1.1.1

Bevor Sie mit dieser Übung fortfahren, müssen Sie das Setup von [Ihr Adobe I/O-Projekt](./../../../modules/getting-started/gettingstarted/ex6.md) abgeschlossen haben. Außerdem müssen Sie eine Anwendung für die Interaktion mit APIs konfiguriert haben, z. B. [Postman](./../../../modules/getting-started/gettingstarted/ex7.md) oder [PostBuster](./../../../modules/getting-started/gettingstarted/ex8.md).

## 1.1.1.2 firefly.adobe.com

Navigieren Sie zu [https://firefly.adobe.com](https://firefly.adobe.com). Klicken Sie auf **Profil**-Symbol und stellen Sie sicher, dass Sie beim rechten **Konto** angemeldet sind, der `--aepImsOrgName--` werden sollte. Klicken Sie bei Bedarf auf **Profil wechseln**, um zu diesem Konto zu wechseln.

![Postman](./images/ffui1.png){zoomable="yes"}

Geben Sie den `Horses in a field` ein und klicken Sie auf **Generieren**.

![Postman](./images/ffui2.png){zoomable="yes"}

Sie sollten dann etwas Ähnliches sehen.

![Postman](./images/ffui3.png){zoomable="yes"}

Öffnen Sie als Nächstes die **Entwickler-Tools** in Ihrem Browser.

![Postman](./images/ffui4.png){zoomable="yes"}

Sie sollten das dann sehen. Wechseln Sie zur Registerkarte **Netzwerk**.

![Postman](./images/ffui5.png){zoomable="yes"}

Geben Sie den Suchbegriff **Generieren** ein und klicken Sie erneut **Generieren**. Anschließend sollte eine Anfrage mit dem Namen &quot;**-async“**. Wählen Sie es aus und navigieren Sie **Payload**, wo Sie die Details der Anfrage sehen.

![Postman](./images/ffui6.png){zoomable="yes"}

Die Anfrage, die Sie hier sehen, ist die Anfrage, die an das Server-seitige Backend von Firefly Services gesendet wird. Es enthält mehrere wichtige Parameter:

- **prompt**: Dies ist Ihre Eingabeaufforderung, in der Sie gefragt werden, welche Art von Bild Firefly generieren soll

- **seed**: Bei dieser Anfrage wurden die Testadressen nach dem Zufallsprinzip erzeugt. Wenn Firefly ein Bild generiert, beginnt der Prozess standardmäßig mit der Auswahl einer zufälligen Zahl, die als Seed bezeichnet wird. Diese zufällige Zahl trägt dazu bei, was jedes Bild einzigartig macht, was großartig ist, wenn Sie eine Vielzahl von Bildern generieren möchten. Es kann jedoch vorkommen, dass Sie Bilder generieren möchten, die über mehrere Anfragen hinweg einander ähnlich sind. Wenn Firefly beispielsweise ein Bild generiert, das Sie mit den anderen Optionen von Firefly ändern möchten (z. B. Stilvorgaben, Referenzbilder usw.), verwenden Sie den Seed dieses Bildes in zukünftigen HTTP-Anfragen, um die Zufälligkeit zukünftiger Bilder zu begrenzen und das gewünschte Bild zu präzisieren.

![Postman](./images/ffui7.png){zoomable="yes"}

Sehen Sie sich die Benutzeroberfläche noch einmal an. Ändern Sie das **Seitenverhältnis** in **Querformat (4:3)**.

![Postman](./images/ffui8.png){zoomable="yes"}

Scrollen Sie nach unten zu **Effekte**, gehen Sie zu **Designs** und wählen Sie einen Effekt wie **Comic-Buch** aus.

![Postman](./images/ffui9.png){zoomable="yes"}

Öffnen Sie die **Entwickler-Tools** erneut in Ihrem Browser. Klicken Sie dann auf **Generieren** und überprüfen Sie die gesendete Netzwerkanfrage.

![Postman](./images/ffui10.png){zoomable="yes"}

Wenn Sie sich die Details der Netzwerkanfrage ansehen, sehen Sie Folgendes:

- **prompt** hat sich im Vergleich zur vorherigen Anfrage nicht geändert
- **Testadressen** haben sich im Vergleich zur vorherigen Anfrage nicht geändert
- **size** hat sich geändert, basierend auf der Änderung im **Seitenverhältnis**.
- **styles** wurde hinzugefügt und verweist auf den ausgewählten **comic_book** Effekt

![Postman](./images/ffui11.png){zoomable="yes"}

Für die nächste Übung müssen Sie eine der **Seed** Zahlen verwenden. Notieren Sie sich eine Testnummer Ihrer Wahl.

In der nächsten Übung machen Sie ähnliche Dinge mit Firefly Services, aber verwenden Sie dann die API anstelle der Benutzeroberfläche. In diesem Beispiel ist die Testnummer **45781**.

## 1.1.1.3 Adobe I/O - access_token

Wählen Sie in der Sammlung **Adobe IO - OAuth** die Anfrage mit dem Namen **POST - Zugriffstoken abrufen** und klicken Sie auf **Senden**. Die Antwort sollte ein neues &quot;**&quot;**.

![Postman](./images/ioauthresp.png){zoomable="yes"}

## 1.1.1.4 Firefly Services-API, Text 2 Bild

Nachdem Sie nun über ein gültiges und neues Zugriffs-Token verfügen, können Sie Ihre erste Anfrage an Firefly Services-APIs senden.

Wählen Sie die Anfrage **POST - Firefly - T2I V3** aus der Sammlung **FF - Firefly Services Tech Insiders** aus.

![Firefly](./images/ff1.png){zoomable="yes"}

Kopieren Sie die Bild-URL aus der Antwort und öffnen Sie sie in Ihrem Webbrowser, um das Bild anzuzeigen.

![Firefly](./images/ff2.png){zoomable="yes"}

Sie sollten ein schönes Bild sehen, das `horses in a field` darstellt.

![Firefly](./images/ff3.png){zoomable="yes"}

Fügen Sie im **Hauptteil** Ihrer Anfrage **POST - Firefly - T2I V3** Folgendes unter dem Feld `"promptBiasingLocaleCode": "en-US"` hinzu und ersetzen Sie die Variable `XXX` durch eine der Testnummern, die von der Firefly Services-Benutzeroberfläche zufällig verwendet wurden. In diesem Beispiel wird die **Seed**-Nummer `45781`.

```json
,
  "seeds": [
    XXX
  ]
```

Klicken Sie **Senden**. Sie erhalten dann eine Antwort mit einem neuen Bild, das von Firefly Services generiert wurde. Öffnen Sie das Bild, um es anzuzeigen.

![Firefly](./images/ff4.png){zoomable="yes"}

Anschließend sollte ein neues Bild mit leichten Unterschieden angezeigt werden, das auf dem verwendeten **Seed** basiert.

![Firefly](./images/ff5.png){zoomable="yes"}

Fügen Sie als Nächstes im **Hauptteil** Ihrer Anfrage **POST - Firefly - T2I V3** das folgende **styles**-Objekt unter das **seed**-Objekt ein. Dadurch wird der Stil des erzeugten Bildes in &quot;**_book“**.

```json
,
  "contentClass": "art",
  "styles": {
    "presets": [
      "comic_book"
    ],
    "strength": 50
  }
```

Sie sollten dann diese haben. Klicken Sie auf **Senden**.

![Firefly](./images/ff6.png){zoomable="yes"}

Klicken Sie auf die Bild-URL, um sie zu öffnen.

![Firefly](./images/ff7.png){zoomable="yes"}

Ihr Bild hat sich jetzt etwas verändert. Beim Anwenden von Stilvorgaben wird das Seed-Bild nicht mehr auf die gleiche Weise wie zuvor angewendet.

![Firefly](./images/ff8.png){zoomable="yes"}

Entfernen Sie den Code für das **seed**-Objekt aus **body** Ihrer Anfrage. Klicken Sie **Senden** und dann auf die Bild-URL, die Sie aus der Antwort erhalten.

```json
,
  "seeds": [
    XXX
  ]
```

![Firefly](./images/ff9.png){zoomable="yes"}

Ihr Bild hat sich jetzt wieder etwas verändert.

![Firefly](./images/ff10.png){zoomable="yes"}


## 1.1.1.5 Firefly Services-API, Gen-Erweiterung

Wählen Sie die Anfrage **POST - Firefly - Gen Expand** aus der **FF - Firefly Services Tech Insiders**-Sammlung aus und navigieren Sie zum **Hauptteil** der Anfrage.

- **size**: Geben Sie die gewünschte Auflösung ein. Der hier eingegebene Wert sollte größer als die Originalgröße des Bildes sein und darf nicht größer als 4096 sein.
- **image.source.url**: Dieses Feld erfordert einen Link zu dem Bild, das erweitert werden muss. In diesem Beispiel wird eine Variable verwendet, um auf das in der vorherigen Übung generierte Bild zu verweisen.

- **horizontale Ausrichtung**: Akzeptierte Werte sind: `"center"`,`"left`, `"right"`.
- **Vertikale Ausrichtung**: Akzeptierte Werte sind: `"center"`,`"top`, `"bottom"`.

![Firefly](./images/ff11.png){zoomable="yes"}

Klicken Sie auf die Bild-URL, die Teil der Antwort ist.

![Firefly](./images/ff12.png){zoomable="yes"}

Sie sehen nun, dass das in der vorherigen Übung generierte Bild auf die Auflösung von 3999x3999 erweitert wurde.

![Firefly](./images/ff13.png){zoomable="yes"}

Wenn Sie die Ausrichtung der Platzierung ändern, unterscheidet sich die Ausgabe ebenfalls geringfügig. In diesem Beispiel wird die Platzierung in &quot;**, unten“**. Klicken Sie auf **Senden** und dann auf , um die generierte Bild-URL zu öffnen.

![Firefly](./images/ff14.png){zoomable="yes"}

Anschließend sollte man sehen, dass das Originalbild an einer anderen Stelle verwendet wird, was das gesamte Bild beeinflusst.

![Firefly](./images/ff15.png){zoomable="yes"}

## Nächste Schritte

Navigieren Sie zu [Optimieren Ihres Firefly-Prozesses mit Microsoft Azure und vordefinierten URLs](./ex2.md){target="_blank"}

Zurück zu [Übersicht über Adobe Firefly Services](./firefly-services.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
