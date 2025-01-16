---
title: Offer decisioning - Testen der Entscheidung
description: Offer decisioning - Testen der Entscheidung
kt: 5342
doc-type: tutorial
source-git-commit: a1cba79313a651c929d76008943c1c5f8a64a9f7
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---

# 3.3.3 Vorbereiten der Client-Eigenschaft der Adobe Experience Platform-Datenerfassung und des Web-SDK-Setups für das Offer decisioning

## 3.3.3.1 Aktualisieren des Datenstroms

In [Erste Schritte](./../../../modules/getting-started/gettingstarted/ex2.md) haben Sie Ihren eigenen **Datenstrom** erstellt. Sie haben dann den Namen `--aepUserLdap-- - Demo System Datastream` verwendet.

In dieser Übung müssen Sie diesen **Datenstrom) so konfigurieren** dass er mit **Offer decisioning** funktioniert.

Navigieren Sie dazu zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Sie werden es dann sehen. Klicken Sie **Datenstrom**.

Wählen Sie oben rechts im Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` werden soll.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration ](./images/edgeconfig1b.png)

Suchen Sie nach Ihrem **Datenstrom**, der `--aepUserLdap-- - Demo System Datastream` heißt. Klicken Sie auf **Datenstrom**, um ihn zu öffnen.

![WebSDK](./images/websdk1.png)

Sie werden es dann sehen. Klicken Sie auf **…** neben **Adobe Experience Platform** und dann auf **Bearbeiten**.

![WebSDK](./images/websdk3.png)

Um **Offer decisioning** zu aktivieren, aktivieren Sie das Kontrollkästchen für **Offer decisioning**. Klicken Sie auf **Speichern**.

![WebSDK](./images/websdk5.png)

Ihr **Datenstrom** kann jetzt mit **Offer decisioning verwendet**.

![WebSDK](./images/websdk4.png)

## 3.3.3.2 Konfigurieren Sie die Client-Eigenschaft der Adobe Experience Platform-Datenerfassung, um personalisierte Angebote anzufordern

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/), zu **Tags**. Suchen Sie nach Ihren Datenerfassungseigenschaften, die `--aepUserLdap-- - Demo System (DD/MM/YYYY)` heißen. Öffnen Sie Ihre Datenerfassungs-Client-Eigenschaft für das Web.

![WebSDK](./images/launch1.png)

Wechseln Sie in Ihrer Eigenschaft zu **Regeln** und öffnen Sie die Regel **Seitenansicht**.

![WebSDK](./images/launch2.png)

Klicken, um die Aktion **Erlebnisereignis „Seitenansicht senden“ zu**.

![WebSDK](./images/launch3.png)

Sie werden es dann sehen. Unter **Personalization** sehen Sie die Option für **Bereiche**.

![WebSDK](./images/launch4.png)

Für jede Anfrage, die an den Edge und an Adobe Experience Platform gesendet wird, können ein oder mehrere **Entscheidungsumfänge“ angegeben**. Ein **Entscheidungsumfang** ist eine Kombination aus zwei Elementen:

- Entscheidungs-ID
- Platzierungs-ID

Schauen wir uns zunächst an, wo Sie diese beiden Elemente finden können.

### 3.3.3.2.1 Platzierungs-ID abrufen

Die Platzierungs-ID identifiziert den Speicherort und den Typ des erforderlichen Assets. Beispielsweise entspricht das Hero-Bild auf der Homepage der CitiSignal-Website der Platzierungs-ID für Web - Bild.

>[!NOTE]
>
>Im Rahmen von Übung 2.3.5 haben Sie bereits eine Adobe Target Experience Targeting -Aktivität konfiguriert, die das Bild des Hero-Standorts auf der Homepage ändert, wie Sie im Screenshot sehen können. Für diese Übung lassen Sie nun Ihre Angebote auf dem Bild unter dem Hero-Bild erscheinen, wie im Screenshot angegeben.

![WebSDK](./images/launch5.png)

Die Platzierungs-ID für Web-Bild finden Sie in Adobe Journey Optimizer unter [Adobe Experience Cloud](https://experience.adobe.com). Auf **Journey Optimizer**.

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

Gehen Sie dann zu Komponenten und dann zu Platzierungen. Klicken Sie auf **Platzierung „Web - Bild** , um die Details anzuzeigen.

![WebSDK](./images/launch6.png)

Wie Sie in der obigen Abbildung sehen können, ist in diesem Beispiel die Platzierungs-ID `dps:offer-placement:1a08a14ccfe533b6`. Notieren Sie sich die Platzierungs-ID für Ihre Platzierung für Web - Bild, da Sie sie in der nächsten Übung benötigen werden.

### 3.3.3.2.2 Abrufen Ihrer Angebotsentscheidungs-ID

Die **Angebotsentscheidungs-ID** gibt an, welche Kombination aus personalisierten Angeboten und Fallback-Angebot Sie verwenden möchten. In der vorherigen Übung haben Sie Ihre eigene Entscheidung erstellt und sie `--aepUserLdap-- - CitiSignal Decision` benannt.

Um die Angebotsentscheidungs-ID für Ihre `--aepUserLdap-- - CitiSignal Decision` zu finden, navigieren Sie zu Angebote und dann zu Entscheidungen. Klicken Sie, um Ihre Entscheidung mit dem Namen `--aepUserLdap-- - CitiSignal Decision` auszuwählen.

![WebSDK](./images/launch7.png)

Wie Sie in der obigen Abbildung sehen können, ist in diesem Beispiel die Entscheidungs-ID `dps:offer-activity:1a08ba4b529b2fb2`. Notieren Sie sich die Angebotsentscheidungs-ID für Ihre `--aepUserLdap-- - CitiSignal Decision`, da Sie sie in der nächsten Übung benötigen werden.

Nachdem Sie nun die beiden Elemente abgerufen haben, die Sie zum Erstellen eines **Entscheidungsumfänge** benötigen, können Sie mit dem nächsten Schritt fortfahren, der die Kodierung des Entscheidungsumfangs umfasst.

### 3.3.3.2.3 BASE64-Codierung

Der **Entscheidungsumfang** den Sie eingeben müssen, ist eine BASE64-kodierte Zeichenfolge. Diese BASE64-kodierte Zeichenfolge ist eine Kombination aus der Platzierungs-ID und der Entscheidungs-ID, wie unten dargestellt:

```json
{
  "xdm:activityId": "dps:offer-activity:1a08ba4b529b2fb2",
  "xdm:placementId": "dps:offer-placement:1a08a14ccfe533b6"
}
```

Sie können die BASE64-codierte Zeichenfolge von Adobe Experience Platform abrufen. Gehen Sie zu Entscheidungen und klicken Sie darauf, um Ihre Entscheidung mit dem Namen `--aepUserLdap-- - CitiSignal Decision` zu öffnen.

![WebSDK](./images/launch9.png)

Nach dem Öffnen von `--aepUserLdap-- - CitiSignal Decision` sehen Sie dies. Suchen Sie das Platzierungs-Web-Bild und klicken Sie auf die Schaltfläche **Kopieren**. Klicken Sie anschließend auf **Codierter Entscheidungsumfang**. Der **Entscheidungsumfang** wird jetzt in die Zwischenablage kopiert.

![WebSDK](./images/launch10.png)

Kehren Sie als Nächstes zu Launch und Ihrer Aktion zurück **AEP Web SDK - Ereignis senden**.

![WebSDK](./images/launch4.png)

Fügen Sie den kodierten Entscheidungsumfang in das Eingabefeld ein. Speichern Sie Ihre Änderungen in der Aktion **AEP Web SDK - Ereignis senden** indem Sie auf **[!UICONTROL Änderungen beibehalten]** klicken.

![WebSDK](./images/launch11.png)

Klicken Sie anschließend auf **[!UICONTROL Speichern]**.

![WebSDK](./images/launch12.png)

Wechseln Sie in der Adobe Experience Platform **[!UICONTROL Datenerfassung zu Veröffentlichungsfluss]** öffnen Sie Ihre **[!UICONTROL Entwicklungsbibliothek]** mit dem Namen **[!UICONTROL Main]**. Klicken Sie auf **[!UICONTROL + Alle geänderten Ressourcen hinzufügen]** anschließend auf **[!UICONTROL Für Entwicklung speichern und erstellen]**. Ihre Änderungen werden jetzt auf Ihrer Demo-Website veröffentlicht.

![WebSDK](./images/launch13.png)

Jedes Mal, wenn Sie jetzt eine **Allgemeine Seite** laden, wie z. B. die Homepage der Demo-Website, bewertet Offer decisioning das passende Angebot und gibt eine Antwort mit den Details des anzuzeigenden Angebots an die Website zurück. Das Anzeigen des Angebots auf der Website erfordert eine zusätzliche Konfiguration, die Sie im nächsten Schritt durchführen werden.

## 3.3.3.3 Konfigurieren Sie Ihre Client-Eigenschaft für die Adobe Experience Platform-Datenerfassung, um personalisierte Angebote zu empfangen und anzuwenden

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/), zu **[!UICONTROL Properties]**. Suchen Sie nach Ihren Datenerfassungseigenschaften, die `--aepUserLdap-- - Demo System (DD/MM/YYYY)` heißen. Öffnen Sie die Datenerfassungseigenschaft für das Web.

![WebSDK](./images/launch1.png)

Wechseln Sie in Ihrer Eigenschaft zu **Regeln**. Suchen und öffnen Sie die Regel **Angebot anzeigen (Offer decisioning)**.

![WebSDK](./images/decrec2.png)

Sie werden es dann sehen. Öffnen Sie die Aktion **Angebot auf der Seite anzeigen**.

![WebSDK](./images/decrec6a.png)

Klicken Sie auf **[!UICONTROL Editor öffnen]**

![WebSDK](./images/decrec6.png)

Überschreiben Sie den Code, indem Sie den folgenden Code in den Editor einfügen.

```javascript
if (!Array.isArray(event.decisions)) {
  console.log("No personalization decisions");
  return;
}

console.log("Received response from Offer Decisioning", event.decisions);

event.decisions.forEach(function (payload) {
  payload.items.forEach(function (item) {
    console.log("Offer", item.data.deliveryURL);

    if (!item.data || item.data?.deliveryURL==null) {
      return;
    }
    console.log("item.data.deliveryURL", item.data.deliveryURL)
    //document.querySelector(".TopRibbon").innerHTML = item.data.content;
    document.querySelector("#SpectrumProvider > div.App > div > div.Page.home > main > div:nth-child(2)").innerHTML = "<img style='max-width:100%;' src='"+item.data.deliveryURL+"'/>";
    document.querySelector("#SpectrumProvider > div.App > div > div.Page.home > main > div:nth-child(2) > img").style.backgroundRepeat="no-repeat";
    document.querySelector("#SpectrumProvider > div.App > div > div.Page.home > main > div:nth-child(2) > img").style.backgroundPosition="center center";
    document.querySelector("#SpectrumProvider > div.App > div > div.Page.home > main > div:nth-child(2) > img").style.backgroundSize = "contain";
  });
});
```

In Zeile 17 wird das von Offer decisioning zurückgegebene Bild auf die Website angewendet. Klicken Sie auf **[!UICONTROL Speichern]**.

![WebSDK](./images/decrec7.png)

Klicken Sie auf **[!UICONTROL Änderungen beibehalten]**.

![WebSDK](./images/keepchanges1dd.png)

Klicken Sie anschließend auf **[!UICONTROL Speichern]**.

![WebSDK](./images/decrec8.png)

Wechseln Sie in der Adobe Experience Platform **[!UICONTROL Datenerfassung zu Veröffentlichungsfluss]** öffnen Sie Ihre **[!UICONTROL Entwicklungsbibliothek]** mit dem Namen **[!UICONTROL Main]**. Klicken Sie auf **[!UICONTROL + Alle geänderten Ressourcen hinzufügen]** anschließend auf **[!UICONTROL Für Entwicklung speichern und erstellen]**. Ihre Änderungen werden jetzt auf Ihrer Demo-Website veröffentlicht.

![WebSDK](./images/decrec9.png)

Mit dieser Änderung überwacht diese Regel in der Adobe Experience Platform-Datenerfassung jetzt die Antwort von Offer decisioning, die Teil der Web-SDK-Antwort ist, und wenn die Antwort empfangen wird, wird das Angebotsbild auf der Homepage angezeigt.

Auf der Demo-Website werden Sie sehen, dass dieses Bild jetzt ersetzt wird. Statt der standardmäßigen CitiSignal-Website-Bilder wird nun ein Angebot wie dieses angezeigt. In diesem Fall wird das Fallback-Angebot angezeigt.

![WebSDK](./images/decrec10.png)

Sie haben jetzt zwei Arten der Personalisierung konfiguriert:

- 1 Experience Targeting-Aktivität mit Adobe Target in Übung 2.3.5
- 1 Offer decisioning-Implementierung mithilfe Ihrer Datenerfassungseigenschaft

In der nächsten Übung erfahren Sie, wie Sie Ihre in Adobe Journey Optimizer erstellten Angebote und Entscheidungen mit einer Adobe Target Experience Targeting-Aktivität kombinieren können.

Nächster Schritt: [3.3.4 Adobe Target und Offer decisioning kombinieren](./ex4.md)

[Zurück zum Modul 3.3](./offer-decisioning.md)

[Zurück zu „Alle Module“](./../../../overview.md)
