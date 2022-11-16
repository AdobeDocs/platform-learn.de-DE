---
title: Erstellen eines Datenelements und einer Regel zum Verfolgen von App-Downloads
description: Erstellen eines Datenelements und einer Regel zum Verfolgen von App-Downloads
feature: Web SDK
exl-id: 8012ba48-38ac-4fb5-9876-8f57d1c5da5d
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 5%

---

# Erstellen eines Datenelements und einer Regel zum Verfolgen von App-Downloads

Zur Erinnerung: Wenn Sie verfolgen, wann ein Benutzer auf die [!UICONTROL App herunterladen] -Link, haben Sie wie folgt zur Datenschicht gepusht:

```js
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
```

Sie haben die `eventInfo` -Schlüssel, der die Datenschicht anweist, diese Daten zusammen mit dem Ereignis zu kommunizieren, aber _not_ die Daten in der Datenschicht beibehalten. Bei einem Link-Klick ist es nicht nützlich, Informationen über den angeklickten Link zur Datenschicht hinzuzufügen, da dies nicht für andere Ereignisse gilt, die später auf der Seite auftreten können.

Für diese Implementierung senden Sie ein Erlebnisereignis an Adobe Experience Platform, das das zusammengeführte Ergebnis von (1) dem berechneten Status der Datenschicht und (2) dem Inhalt von `eventInfo`.

Dazu müssen Sie ein Datenelement erstellen, das diese beiden Informationsblöcke zusammenführt.

## ein Datenelement erstellen

So erstellen Sie das entsprechende Datenelement:

1. Klicken [!UICONTROL Datenelemente] im Menü links.
1. Klicken Sie anschließend auf das [!UICONTROL Neues Datenelement erstellen] Link.
1. Geben Sie den Namen des Datenelements ein, `computedStateAndEventInfo`.
1. Für [!UICONTROL Erweiterung] Feld, wählen Sie [!UICONTROL Core] , wenn sie nicht bereits ausgewählt ist.
1. Für [!UICONTROL Datenelementtyp] Feld, wählen Sie **[!UICONTROL Zusammengeführte Objekte]**. Mit diesem Datenelement können Sie mehrere Objekte zusammenführen. Das zusammengeführte Ergebnis wird vom Datenelement zurückgegeben.
1. Fügen Sie das erste Objekt hinzu, das Sie in die Zusammenführung aufnehmen möchten. Eingabe `%event.fullState%` im [!UICONTROL Objekt (erforderlich)] -Feld. Bei Verwendung in einer Regel, die von einer [!UICONTROL Übermittelte Daten] -Regelereignis, wird hierdurch der berechnete Status der Adobe Client-Datenschicht zum Zeitpunkt der Regelauslösung referenziert.
1. Klicken Sie auf  **[!UICONTROL Weitere hinzufügen]** Befehl.
1. Fügen Sie das zweite Objekt hinzu. Eingabe `%event.eventInfo%` im [!UICONTROL Objekt (erforderlich)] -Feld. Bei Verwendung in einer Regel, die von einer [!UICONTROL Übermittelte Daten] -Regelereignis, das auf die `eventInfo` -Teil, der in die Adobe Client-Datenschicht übertragen wurde.
1. Speichern Sie das Datenelement, indem Sie auf das [!UICONTROL Speichern] Schaltfläche.
   ![computedStateAndEventInfo-Datenelement](../assets/computed-state-and-event-info-data-element.png)

Das Datenelement ist abgeschlossen.

## Erstellen einer Regel

So erstellen Sie eine Regel zum Verfolgen von Klicks auf die [!UICONTROL App herunterladen] link:

1. Klicken **[!UICONTROL Regeln]** im Menü links.
1. Klicken Sie auf **[!UICONTROL Regel hinzufügen]**.
1. Eingabe **_Link zum Herunterladen des Programms angeklickt_** im [!UICONTROL Name] -Feld.

## Ereignis hinzufügen

1. Klicken Sie auf **[!UICONTROL Hinzufügen]** Schaltfläche unter [!UICONTROL Veranstaltungen]. Sie werden jetzt in der Ereignisansicht angezeigt.
1. Für [!UICONTROL Erweiterung] Feld, wählen Sie **[!UICONTROL Adobe Client-Datenschicht]**.
1. Für [!UICONTROL Ereignistyp] Feld, wählen Sie **[!UICONTROL Übermittelte Daten]**.
1. Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.
   ![Download-App-angeklicktes Ereignis](../assets/download-app-clicked-event.png)
Da diese Regel nur ausgelöst werden soll, wenn die Variable `downloadAppClicked` -Ereignis an die Datenschicht gesendet wird, wählen Sie die **[!UICONTROL Bestimmtes Ereignis]** Radio under [!UICONTROL Hören Sie zu] und Typ **_downloadAppClicked_** in [!UICONTROL Ereignis/Schlüssel zur Registrierung]  Textfeld, das angezeigt wird.

## Hinzufügen einer Aktion

Nachdem Sie sich wieder in der Regelansicht befinden:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** unter [!UICONTROL Aktionen].
1. Sie sollten sich jetzt in der Aktionsansicht befinden. Für [!UICONTROL Erweiterung] Feld, wählen Sie **[!UICONTROL Adobe Experience Platform Web SDK]**. Für [!UICONTROL Aktionstyp] Feld, wählen Sie **[!UICONTROL Ereignis senden]**.
1. Im [!UICONTROL Typ] rechts klicken, wählen Sie `web.webinteraction.linkClicks`.
1. Für [!UICONTROL XDM-Daten] Klicken Sie auf die Schaltfläche für die Datenelementauswahl rechts und wählen Sie **[!UICONTROL computedStateAndEventInfo]**. Dies ist das Datenelement, das Sie kürzlich erstellt haben.
1. Aktivieren Sie für diese Regel (im Gegensatz zu den anderen von Ihnen erstellten Regeln) die Option **[!UICONTROL Dokument wird entladen]** aktivieren.
   ![Kontrollkästchen &quot;Dokument wird entladen&quot;](../assets/document-will-unload.png)
1. Speichern Sie die Aktion, indem Sie auf die **[!UICONTROL Änderungen beibehalten]** Schaltfläche.

>[!TIP]
>
>Die [!UICONTROL Funktion zum Entladen des Dokuments] teilt dem SDK mit, dass der Benutzer beim Klicken auf den Link von der Seite weg navigiert. Dies ist wichtig, da es dem SDK ermöglicht, die Anfrage selbst dann zu stellen, wenn der Benutzer von der Seite weg navigiert, da die Anfrage im Hintergrund ausgeführt wird und den Server erreicht. Wenn dieses Kontrollkästchen deaktiviert ist, wird die Anfrage nicht auf diese Weise gestellt und daher beim Entladen des aktuellen Dokuments wahrscheinlich abgebrochen.
>
>Sie fragen sich vielleicht: &quot;Das klingt gut. Warum ist diese Option dann nicht immer aktiviert?&quot;
>
>Nun, es ist ein wenig kompliziert, aber bei Verwendung dieser Funktion verwendet das SDK eine Browser-Methode namens [`sendBeacon`](https://developer.mozilla.org/de-DE/docs/Web/API/Navigator/sendBeacon) , um die Anfrage zu senden. Beim Senden einer Anforderung mit `sendBeacon`, erlaubt der Browser dem SDK (oder anderen) nicht den Zugriff auf vom Server zurückgegebene Daten. Wenn das SDK diese Funktion für jede Anfrage verwenden würde, könnte das SDK nie Daten vom Server empfangen. Aus diesem Grund ist es wichtig, die [!UICONTROL Dokument wird entladen] nur dann, wenn das aktuelle Dokument entladen wird. In diesem Fall können die Antwortdaten trotzdem verworfen werden.

## Speichern Sie die Regel

Ihre Regel sollte jetzt abgeschlossen sein.

1. Klicken **[!UICONTROL Speichern]** in der oberen rechten Ecke.
   ![Herunterladen des App-Links, auf die Regel geklickt wurde](../assets/download-app-link-clicked-rule.png)

[Weiter: ](publish-the-library.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)