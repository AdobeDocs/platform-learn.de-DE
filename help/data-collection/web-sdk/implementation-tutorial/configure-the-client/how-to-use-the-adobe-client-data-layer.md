---
title: Verwendung der Adobe Client-Datenschicht
description: Verwendung der Adobe Client-Datenschicht
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 33a5db8c-e49b-4073-b4d7-4abe19537fcb
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 0%

---

# Verwendung der Adobe Client-Datenschicht

In [Was ist eine Datenschicht?](whats-a-data-layer.md)haben Sie gelernt, dass bei der Diskussion über Datenschichten zwei Aspekte zu beachten sind: den Container und den Inhalt. Die Adobe Client-Datenschicht ist der Container. Es ist egal, wie du bist [Daten strukturieren](../structuring-your-data.md) oder welche Informationen Sie in Ihre Daten eingeben möchten. Die Daten können wie folgt strukturiert sein: [XDM](../structuring-your-data.md#xdm), wie die folgenden Beispiele zeigen, oder Sie können Ihre eigene Struktur vollständig erstellen.

Im Idealfall ist das Engineering-Team Ihres Unternehmens dafür verantwortlich, alle erforderlichen Daten durch On-Page-Code in die Datenschicht zu übertragen. Das Marketing-Team ruft dann Daten aus der Datenschicht ab, vorzugsweise unter Verwendung von Adobe Experience Platform-Tags.

## Push von Daten in die Datenschicht

Die Adobe Client-Datenschicht ist ein JavaScript-Array. Wenn Sie die Adobe Client-Datenschicht erstellen, ist sie leer:

```js
window.adobeDataLayer = window.adobeDataLayer || [];
```

Um Daten in die Datenschicht zu platzieren, rufen Sie die `push` -Methode im Datenschicht-Array:

```js
window.adobeDataLayer.push({
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile"
  }
});
```

Sie können jederzeit zusätzliche Daten in die Datenschicht übertragen, indem Sie `push` erneut.

```js
window.adobeDataLayer.push({
  "claims": {
    "status": "approved",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
});
```

## Push-Daten sinnvoll nutzen

Wenn Sie die beiden vorherigen `push` -Aufrufe, würden Sie am Ende zwei Einträge im Datenschicht-Array haben. Die Datenschicht ist in diesem Status nicht besonders nützlich. In der Regel möchten Sie auf den zusammengeführten Status der Datenschicht zugreifen, d. h. auf ein einzelnes Objekt, das das kombinierte Ergebnis aller Daten ist, die Sie in die Datenschicht übertragen haben. Später im Tutorial erfahren wir, wie Sie auf diesen zusammengeführten Status zugreifen können. Zunächst reicht es zu verstehen, dass der berechnete Zustand der Datenschicht nach unseren beiden `push` Aufrufe lauten wie folgt:

```json
{
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile",
    "status": "approved",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
}
```

## Entfernen von Daten

Manchmal müssen Sie Datenteile aus der Datenschicht entfernen. Dies ist besonders bei Einzelseitenanwendungen üblich, wenn der Benutzer von einer Ansicht zur nächsten navigiert. Wenn der Benutzer beispielsweise von einer Produktansicht zu einer Kontaktansicht navigiert, kann es sinnvoll sein, alle Produktdaten auf der Datenschicht zu löschen, da sie nicht mehr für die aktive Ansicht relevant sind.

Sie können ein Datenelement entfernen, indem Sie einen Wert von `undefined` für den Schlüssel, den Sie entfernen möchten. aufbauend auf unseren vorherigen Beispielen, wenn Sie `status` aus der Datenschicht würde Ihr Code wie folgt aussehen:

```js
window.adobeDataLayer.push({
  "claims": {
    "status": undefined
  }
});
```

Der berechnete Status der Datenschicht würde nicht mehr beinhalten `status`:

```json
{
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
}
```

## Push von Ereignissen in die Datenschicht

Die Adobe Client-Datenschicht wird nicht nur zum Speichern von Daten verwendet, sondern auch zur Kommunikation darüber, welche Ereignisse auf der Seite auftreten. In der Regel werden Daten in die Datenschicht übertragen _als Ergebnis_ eines Ereignisses, das auf der Seite auftritt. Zu diesen Ereignissen gehören (1) Interaktionsereignisse, z. B. das Öffnen eines Chat-Bots oder das Eingeben eines Suchbegriffs in eine Suchleiste oder (2) Ereignisse ohne Interaktion, wie Impression einer Anzeige oder der Abschluss von Webseitenleistungsberechnungen.

Um mitzuteilen, dass ein Ereignis auf der Seite aufgetreten ist, fügen Sie eine `event` -Taste im Objekt, das Sie an die Datenschicht senden. Sie können beispielsweise mitteilen, dass ein Benutzer eine Suchabfrage in ein Suchfeld eingegeben hat.

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered"
});
```

Später erfahren Sie, wie Sie Regeln innerhalb von Adobe Experience Platform-Tags Trigger, wenn ein bestimmtes Ereignis in die Datenschicht gepusht wird. Beachten Sie außerdem, dass `event` Schlüssel ist _not_ im berechneten Status enthalten sind. Sie wird von der Datenschicht besonders behandelt.

## Push von Ereignissen und Daten in die Datenschicht

Eine Benachrichtigung der Listener darüber, dass der Benutzer eine Suchabfrage eingegeben hat, ist hilfreich. Was ist jedoch hilfreich, wenn Sie zusätzliche Informationen zu dem Ereignis bereitstellen möchten? Vielleicht möchten Sie beispielsweise die Suchabfrage des Benutzers einbeziehen. Sie können diese Daten auf zwei Arten bereitstellen:

1. Stellen Sie die Daten so bereit, dass sie **beibehalten** in der Datenschicht als Teil des berechneten Zustands der Datenschicht.
2. Stellen Sie die Daten so bereit, dass sie **nicht beibehalten** in der Datenschicht als Teil des berechneten Zustands der Datenschicht.

Ob Sie die Daten in der Datenschicht beibehalten möchten, hängt in der Regel davon ab, ob Sie diese Daten während der gesamten Dauer des Besuchers auf der Seite referenzieren möchten. Andernfalls kann das Speichern der Daten innerhalb der Datenschicht nur zu einer überfüllten Datenschicht führen.

Im Folgenden finden Sie ein Beispiel für das Pushen eines Ereignisses mit zusätzlichen Daten, die **beibehalten** in der Datenschicht:

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered",
  "siteKnowledge": {
    "supportSiteSearch": {
      "term": "roller",
      "locationInPage": "topSearchBar"
    }
  }
});
```

Danach `push` erfolgt, `siteKnowledge` wird immer im berechneten Status der Datenschicht angezeigt, bis die Seite entladen wird (es sei denn, Sie entfernen oder überschreiben sie absichtlich) `siteKnowledge`).

Im Gegensatz dazu finden Sie hier ein Beispiel für das Pushen eines Ereignisses mit zusätzlichen Daten, die **nicht beibehalten** in der Datenschicht:

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered",
  "eventInfo": {
    "siteKnowledge": {
      "supportSiteSearch": {
        "term": "roller",
        "locationInPage": "topSearchBar"
      }
    }
  }
});
```

Beachten Sie in diesem Beispiel Folgendes: `siteKnowledge` in `eventInfo`. Die `eventInfo` -Schlüssel wird von der Datenschicht besonders behandelt. Er teilt der Datenschicht mit, dass diese Daten _sollte_ in das Ereignis eingeschlossen sein, das an Listener gesendet wird, es jedoch _nicht_ innerhalb der Datenschicht beibehalten werden. Nachdem Listener (wie Adobe Experience Platform-Tags) über das Ereignis benachrichtigt wurden, werden diese Daten im Wesentlichen vergessen. Die `siteKnowledge` -Schlüssel wird nie im berechneten Status der Datenschicht angezeigt.

Jedes Mal, wenn Sie `push`, benachrichtigt die Adobe Client Data Layer alle Listener. Später erfahren wir, wie Sie diese Benachrichtigungen von Adobe Experience Platform-Tags und Trigger-Regeln entsprechend überwachen.
