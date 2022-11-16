---
title: Verwendung der Adobe Client-Datenschicht
description: Verwendung der Adobe Client-Datenschicht
exl-id: b5af9e72-aa6c-4cd7-80dd-b2de762a7523
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Verwendung der Adobe Client-Datenschicht

In [Was ist eine Datenschicht?](whats-a-data-layer.md)haben Sie gelernt, dass bei der Diskussion über Datenschichten zwei Aspekte zu beachten sind: den Container und den Inhalt. Die [Adobe Client-Datenschicht](https://github.com/adobe/adobe-client-data-layer) ist der Container. Es ist egal, wie du bist [Daten strukturieren](../structuring-your-data.md) oder welche Informationen Sie in Ihre Daten eingeben möchten. Die Daten können wie folgt strukturiert sein: [XDM](../structuring-your-data.md#xdm), wie die folgenden Beispiele zeigen, oder Sie können Ihre eigene Struktur vollständig erstellen.

Im Idealfall ist das Engineering-Team Ihres Unternehmens dafür verantwortlich, alle erforderlichen Daten durch On-Page-Code in die Datenschicht zu übertragen. Das Marketing-Team ruft dann Daten aus der Datenschicht ab, vorzugsweise mithilfe der Funktion Tags von Adobe Experience Platform, ehemals Launch.

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

Wenn Sie die beiden vorherigen `push` -Aufrufe, würden Sie am Ende zwei Einträge im Datenschicht-Array haben. Die Datenschicht ist in diesem Status nicht nützlich. In der Regel möchten Sie auf den zusammengeführten Status der Datenschicht zugreifen, d. h. auf ein einzelnes Objekt, das das kombinierte Ergebnis aller Daten ist, die Sie in die Datenschicht übertragen haben. Sie erfahren, wie Sie später im Tutorial auf diesen zusammengeführten Status zugreifen können. Zunächst reicht es zu verstehen, dass der berechnete Zustand der Datenschicht nach unseren beiden `push` Aufrufe lauten wie folgt:

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

Manchmal müssen Sie Datenteile aus der Datenschicht entfernen. Dies kommt häufig bei Einzelseitenanwendungen vor, wenn der Benutzer von einer Ansicht zur nächsten navigiert. Wenn der Benutzer beispielsweise von einer Produktansicht zu einer Kontaktansicht navigiert, kann es sinnvoll sein, alle Produktdaten auf der Datenschicht zu löschen, da sie nicht mehr für die aktive Ansicht relevant sind.

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

<!--Later, you'll learn how to trigger rules within Adobe Experience Platform Tags when a particular event is pushed to the data layer.--> Also note that the `event` key is not included in the computed state. It receives special treatment by the data layer.


## Push von Ereignissen und Daten in die Datenschicht

Eine Benachrichtigung der Listener darüber, dass der Benutzer eine Suchabfrage eingegeben hat, ist hilfreich. Was ist jedoch hilfreich, wenn Sie zusätzliche Informationen zu dem Ereignis bereitstellen möchten? Vielleicht möchten Sie beispielsweise die Suchabfrage des Benutzers einbeziehen. Sie können diese Daten auf zwei Arten bereitstellen:

1. Stellen Sie die Daten so bereit, dass sie **beibehalten** in der Datenschicht als Teil des berechneten Zustands der Datenschicht.
1. Stellen Sie die Daten so bereit, dass sie **nicht beibehalten** in der Datenschicht als Teil des berechneten Zustands der Datenschicht.

Ob Sie die Daten in der Datenschicht beibehalten möchten, hängt in der Regel davon ab, ob Sie diese Daten während der gesamten Dauer des Besuchers auf der Seite referenzieren möchten. Wenn nicht, führt das Speichern der Daten innerhalb der Datenschicht zu einer überfüllten Datenschicht.

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

Beachten Sie in diesem Beispiel Folgendes: `siteKnowledge` in `eventInfo`. Die `eventInfo` -Schlüssel wird von der Datenschicht besonders behandelt. Er teilt der Datenschicht mit, dass diese Daten _sollte_ in das Ereignis eingeschlossen sein, das an Listener gesendet wird, es jedoch _nicht_ innerhalb der Datenschicht beibehalten werden. Nachdem Listener (wie ein Tag-Manager) über das Ereignis informiert wurden, werden diese Daten vergessen. Die `siteKnowledge` -Schlüssel wird nie im berechneten Status der Datenschicht angezeigt.

Jedes Mal, wenn Sie `push`, benachrichtigt die Adobe Client Data Layer alle Listener. Später erfahren Sie, wie Sie diese Benachrichtigungen abrufen. <!--from Adobe Experience Platform Tags--> und Trigger-Regeln entsprechend.

[Weiter: ](implement-product-page-data-layer.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
