---
title: Grundlegende Einführung in APIs
description: Einführung in die Programmier-Schnittstellen von Anwendungen
activity: understand
doc-type: article
feature-set: Experience Platform
feature: Server API,API,Data Collection,Integrations
level: Beginner
role: User, Data Engineer, Developer
solution: Data Collection
topic: Integrations
exl-id: 9607e641-b0d5-49c1-b319-32ed0720e715
source-git-commit: ac07d62cf4bfb6a9a8b383bbfae093304d008b5f
workflow-type: tm+mt
source-wordcount: '2086'
ht-degree: 0%

---

# API 101 - Grundlegende Einführung in APIs

API steht für Application Programming Interface. Es bedeutet genau das, was es sagt - es gibt Schnittstellen zwischen Programmen und diese Schnittstellen ermöglichen es diesen Programmen zu kommunizieren. Wenn Programmierer Softwareanwendungen entwickeln, benötigen sie oft ihre Software, um mit anderer Software oder Hardware kommunizieren zu können. Die API definiert das Was, Wie, Wann, Wo und Warum für diese Kommunikationen und Interaktionen.

APIs sind eine Möglichkeit, geschäftliche Herausforderungen mit Software zu lösen. In den meisten Unternehmen ist das eine gemeinsame Anstrengung. Die Zusammenarbeit ist mit einem gemeinsamen Verständnis der Schlüsselbegriffe, Konzepte und Schritte immer einfacher.

Wenn Sie darüber nachdenken, auf einen Link auf einer Webseite zu klicken, verwendet der Browser beim Klicken auf den Link einige APIs. Der Browser erkennt den Klick, stellt die Anforderung für die Seite, die Sie besuchen möchten, ruft die Seite über das Internet ab und zeigt sie dann auf Ihrem Bildschirm an. Es gibt viele kleinere Zwischenschritte, aber Ihr Browser ist eine Software, die mit einer Vielzahl von APIs kommuniziert und interagiert, um Ihnen eine Webseite zu zeigen. In diesem Artikel werden Begriffe, Konzepte und Schritte hervorgehoben, die bei der Verwendung oder Erörterung von APIs wichtig sind.

Am Ende dieses Artikels sollten Sie ein klares Verständnis dieser grundlegenden Begriffe, Konzepte und Schritte haben. Die API-Dokumentation kann umfangreich sein, und Diskussionen über die Verwendung von APIs zur Behandlung bestimmter Anwendungsfälle können sehr detailliert sein. Das Navigieren in der Dokumentation und Erörterung von APIs ist mit klaren Grundlagen und einem gemeinsamen Verständnis einfacher und produktiver.

>[!NOTE]
>
> Obwohl es viele APIs gibt, wird der Fokus hier auf Web- und Browser-APIs liegen: im Grunde, wenn eine Software-Anwendung über das Internet mit einer anderen interagiert.

## API-Begriffe und -Konzepte

Was bedeutet ein Wort oder eine Wortgruppe, und wie kann ich einfach und einfach darüber nachdenken? In einer API bedeutet der &quot;Anwendungs&quot;-Teil eine Software-Anwendung oder ein Programm. Der Teil &quot;Programmierschnittstelle&quot; bezieht sich darauf, wie und wo eine Anwendung für bestimmte Zwecke mit einer anderen Anwendung interagiert. Wenn Sie in unserem Webseitenbeispiel auf einen Link klicken, sendet der Browser eine Anforderung für die Webseite an einen Server.

![Bild des Hyperlinks mit Ziel-URL](../assets/api101-link-destination.png)

In diesem Screenshot bewegt sich der Mauszeiger über den Adobe Experience Platform-Link. Unten befindet sich die Statusleiste des Webbrowsers, die die &quot;Adresse&quot;der Seite anzeigt, die der Browser erhält. Mit anderen Worten: Wenn Sie auf den Link Adobe Experience Platform klicken, wird der Browser angewiesen, &quot;diese Seite für mich zu erhalten, damit ich sie hier auf meinem Bildschirm sehen kann&quot;.

Wenn auf einen Link geklickt wird, fordert der Browser einen Server an, eine Seite zu erhalten. Dies ist eine `GET` -Anfrage, eine der Anforderungsmethoden, die häufig mit Web-APIs verwendet werden. Eine Sache, die der Browser benötigt, um die Anfrage zu erfüllen, ist die Seite &quot;Adresse&quot; - wo ist es im Web?

### Teile einer URL

![Browser-Adressleiste mit URL](../assets/api101-address-bar.png)

Die meisten Browser verfügen über eine &quot;Adressleiste&quot;, in der einige oder alle &quot;Adressen&quot; einer Webseite angezeigt werden. Wenn der Browser die Seite für den Link, auf den wir geklickt haben, &quot;erhält&quot;, wird in dieser Adressleiste die &quot;Adresse&quot;der Seite angezeigt. Was ist also die &quot;Adresse&quot; für eine Webseite?

Diese `https://business.adobe.com/products/experience-platform/adobe-experience-platform.html` oben ist die Adresse einer Seite im Internet und wird als URL oder Uniform Resource Locator bezeichnet. URLs können auf eine Seite wie diese, eine Bilddatei, ein Video oder andere Dateitypen verweisen.

![Teile einer URL](../assets/api101-url-parts.jpg)

Diese Adresse, die URL, hat bestimmte Teile, die für Web- und Browser-APIs sehr relevant sind.

**Scheme**

Die obige `scheme` wird auch als `protocol` mit Web-APIs bezeichnet und ist normalerweise entweder `http` oder `https`. HTTP oder HyperText Transfer Protocol ist die Art und Weise, wie Ressourcen wie Webseiten von einem Webserver auf einen Webbrowser übertragen werden. HTTPS ist die sichere Version, bei der die Übertragung über das Internet unter Verwendung von Sicherheitsfunktionen erfolgt, die eine Störung der übertragenen Ressource verhindern sollen. In der Browser-Adressleiste wird häufig ein kleines Sperrsymbol angezeigt, wenn eine Seite über HTTPS angezeigt wird.

Bei Web-APIs erfolgt die Übertragung dieser Ressourcen über HTTP-Anfragen - also HTTP-Anfragen.

**Hosts und Domänen**

Der `business.adobe.com` ist der Host der angeforderten Ressource. Wenn auf unseren Beispiel-Link geklickt wird, verwendet der Browser diesen Teil der URL, um den Server zu finden, auf dem die Seite gehostet wird. Es ist nicht immer genau das Gleiche wie der Webserver, aber auf einer einfachen Ebene können wir uns dies als den Server vorstellen, auf dem der Browser die Seite erhält, die wir angefordert haben.

Domänennamen sind Teil des Domänennamensystems, besser bekannt als DNS. Die meisten Menschen halten `adobe.com` oder `example.com` für einen &quot;Domänennamen&quot;, aber es gibt Teile, die für APIs relevant sind. `www.adobe.com` und `business.adobe.com` können als Domänennamen bezeichnet werden, aber die Teile `www.` und `business.` werden als Subdomänen bezeichnet. APIs interagieren oft mit einer URL, die eine Subdomäne wie `api.example.com` oder `sub.www.example.com` enthält.

Es ist sehr üblich, zu sehen, dass der Begriff _host_ auf einen vollständigen Domänennamen verweist, einschließlich aller Subdomänen wie `business.adobe.com`. Es ist auch üblich, die Begriffe _Domäne_ oder _Domänenname_ anzuzeigen, wenn auf einen Host ohne Subdomäne wie `adobe.com` verwiesen wird. Es ist hier nicht wichtig, die spezifischen Begriffe für jeden Teil und jede Variante eines Hosts zu merken. Aber es ist wichtig, dass Sie wissen, dass diese Begriffe häufig verwendet werden, damit Sie alle relevanten Details für Ihr Geschäft und Ihre Diskussionen klären können.

**Herkunft**

Der Ursprung ist ein weiterer Begriff, der darauf aufmerksam gemacht wird, dass eng mit den Teilen einer URL verbunden ist. Auf einer einfachen Ebene ist eine Herkunft ungefähr die `scheme` plus die `host` plus die `domain` wie `https://business.adobe.com`. Verschiedene Werte stellen oft unterschiedliche Ursprünge wie `https://business.adobe.com` und `http://business.adobe.com` dar, da sie unterschiedliche Schemas haben. `https://www.adobe.com` und `https://business.adobe.com` sind aufgrund der verschiedenen Subdomains in vielen Anwendungen ebenfalls nicht der gleiche Ursprung.

**Pfad**

Das letzte Bit im obigen URL-Beispiel ist der `path` zur Ressource - die Seite in unserem Beispiel. Der Teil `/products/experience-platform/` stellt normalerweise Ordner oder Ordner auf dem Webserver dar. So wie wir Ordner oder Verzeichnisse auf unseren Computern für Dokumente und Fotos haben, haben wir auch Ordner auf Webservern, um Inhalte zu organisieren. Und schließlich ist der Teil `/adobe-experience-platform.html` der Name der Datei - die Webseite.

Es gibt weitere detailliertere Teile einer URL, die im nächsten Teil dieser Reihe hervorgehoben werden.

### Drittanbieter-APIs

Web-APIs werden manchmal als Drittanbieter-APIs bezeichnet. Stellen Sie sich dies wie die an einer Transaktion beteiligten Parteien vor. In unserem Link-Beispiel sind Sie - oder genauer gesagt Ihr Browser - der Erstanbieter in der Anfrage für die Seite. Der Webserver ist der Zweitanbieter. Wo ist also die dritte?

Es kommt häufig vor, dass eine Webseite Inhalte oder Ressourcen von anderen Hosts oder Quellen enthält. Wenn Ihr Browser in diesen Fällen beginnt, die Seite anzuzeigen, sendet er eine weitere Reihe von Anfragen an diese anderen Hosts oder &quot;Drittanbieter&quot;, die diese Ressourcen hosten. Dies ist sehr häufig, insbesondere für Medieninhalte wie Videos oder Bilder, aber auch für Daten, die zum Zeitpunkt der Anzeige oder Verwendung aktualisiert werden müssen. Das Abrufen der aktuellen Tageszeit, des aktuellen Wetters oder einer personalisierten Willkommensnachricht für eine bestimmte Person sind Beispiele dafür, wie eine Drittanbieter-API die richtige Ressource zur richtigen Zeit bereitstellen kann. Diese Anfragen stammen häufig von diesen Drittanbieter-APIs.

## Häufige Verwendungen für Web-APIs

Neben der Tageszeit, dem Wetter oder personalisierten Inhalten werden viele Web-APIs verwendet. Social-Media-Plattformen wie Twitter, TikTok, Facebook, LinkedIn, Snapchat, Pinterest und andere verfügen über eine Vielzahl von APIs, die Programmierer für ihre Anwendungen verwenden können. Und natürlich hat Adobe auch [eine Vielzahl von APIs](https://developer.adobe.com/apis), die Programmierer verwenden, damit ihre Software mit Adobe-Produkten und -Services interagieren kann. Softwareprodukte und -dienste greifen über diese APIs auf andere Softwareprodukte und -dienste zu.

## Beispiel-APIs

Browser-APIs ermöglichen Programmierern die direkte Interaktion mit Funktionen des Browsers. Mit der Battery-API kann die Software den Akkustatus eines Geräts überprüfen, damit Sie bei Bedarf benachrichtigt werden können. Mit der Zwischenablage-API kann Software mit der Zwischenablage des Geräts kopieren oder einfügen. Mit der Vollbild-API kann die Software die Option zum Erweitern der Ansicht auf den Vollbildmodus des Geräts bereitstellen, z. B. YouTube.

Die Adobe Experience Platform Data Access API ist eine Web-API, mit der Programmierer auf Datensatzdateien von Adobe Experience Platform zugreifen und diese herunterladen können, sodass sie Kundenprofildaten in ihren eigenen Programmen verwenden können. Es ist sehr häufig, dass APIs wie diese Teil eines Softwareautomatisierungsprozesses sind, bei dem Software so programmiert wird, dass sie eine Reihe von Schritten mit mehreren APIs in Kombination durchführen. Dies kann im Vergleich zur manuellen Ausführung derselben Schritte häufig zu erheblichen Kosteneinsparungen führen.

## API-Endpunkte

Wenn Programmierer einen Browser oder eine Web-API in ihren Programmen &quot;verwenden&quot;, stellen sie normalerweise Anfragen zum Senden oder Empfangen von Ressourcen, z. B. unseren Beispielbrowser, der eine Webseite anfordert. In der API-Dokumentation werden häufig &quot;Endpunkte&quot;für diese Anfragen aufgeführt, z. B. `https://platform.adobe.io/data/foundation/export/files/{dataSetFileId}`. Dies ist das spezifische Muster oder &quot;Endpunkt&quot;der Platform Data Access-API, die ein Programmierer zum Abrufen einer Datensatzdatei verwendet.

Die von diesen geschweiften Klammern eingeschlossenen `{dataSetFileId}` stellen einen Wert dar, den der Programmierer in der Anfrage senden muss. Die URL in der eigentlichen API-Anfrage würde also etwa &quot;`https://platform.adobe.io/data/foundation/export/files/xyz123brb`&quot;entsprechen, wobei die &quot;`xyz123brb`&quot;eine gültige ID der Datensatzdatei sein muss, die der Programmierer empfangen möchte.

Anders ausgedrückt: Genau wie der Browser eine Seite an eine bestimmte URL erhält, erhalten API-Anfragen Ressourcen von einem bestimmten Endpunkt wie diesem Datensatzbeispiel oder senden Ressourcen an diesen.

## HTTP-Anfragemethoden

An dieser Stelle sollte klar sein, dass Web-APIs Anfragen für Ressourcen wie Webseiten oder Datensätze stellen. Wie die meisten Softwarekonzepte folgen diese HTTP-Anforderungen wiederholbaren Mustern. Eine Anfrage wird von einer Software-Anwendung an eine andere Software-Anwendung gesendet, die die Anfrage auswertet und dann antwortet: Der Browser fordert eine Seite von einem Webserver an und antwortet mit den Seiteninhalten.

Der gesamte Prozess von Anfrage bis Antwort umfasst viele kleinere und sehr detaillierte Schritte, aber die Anforderungsmethoden sind einfach. Anfragemethoden definieren den angeforderten Vorgang.

**`GET`**

Die `GET` -Anfragemethode wird verwendet, wenn eine Antwort angefordert wird, die eine Ressource bereitstellt, z. B. unsere Webseite und Datensatzbeispiele. Wenn wir in einem Browser auf einen Link klicken oder auf einen Link auf einem Mobilgerät tippen, stellen wir hinter den Kulissen eine `GET` -Anfrage.

**`POST`**

Die `POST` -Methode sendet Daten mit der Anfrage. Es mag seltsam klingen, dass eine &quot;Anfrage&quot;Daten sendet. Die Idee ist jedoch, dass die API-Anfrage den -Endpunkt - die empfangende Software - bittet, die Anfrage zu akzeptieren und im Fall von `POST` auch die gesendeten Daten zu akzeptieren. Die gesendeten Daten werden normalerweise wie eine Datenbank oder Datei in einen Datenspeicher geschrieben, damit sie gespeichert werden können.

**`PUT`**

Die Anforderungsmethode `PUT` ähnelt `POST` , da Daten gesendet werden. Wenn die gesendeten Daten jedoch bereits am Endpunkt vorhanden sind, aktualisiert ein `PUT` die vorhandenen Daten, indem er sie ersetzt. Ein `POST` wird nicht aktualisiert, sondern sendet einfach, sodass mehrere `POST` -Anfragen mehrere Datensätze der gesendeten Daten erstellen können, anstatt einen vorhandenen Datensatz zu aktualisieren.

**`PATCH`**

Mit der Anfragemethode `PATCH` können Daten gesendet werden, die einen Teil eines vorhandenen Datensatzes aktualisieren, z. B. wenn wir unsere Adresse ändern, indem wir unser Kontoprofil aktualisieren. Mit einer `POST` -Anfrage könnte ein zusätzliches Profil erstellt werden, und mit einem `PUT` kann das vorhandene Profil ersetzt werden. Mit der `PATCH` -Methode aktualisieren wir jedoch einfach den relevanten Teil des vorhandenen Datensatzes, wie z. B. unsere Adresse.

**`DELETE`**

Die Anforderungsmethode `DELETE` entfernt eine in der Anfrage angegebene Ressource, z. B. wenn wir auf einen Link klicken, um unser Kontoprofil vollständig zu löschen.

Es gibt mehrere weitere Methoden. Dies ist jedoch eine Liste der am häufigsten verwendeten Methoden für die Arbeit mit APIs.

### Anforderungsbeispiel

Da Sie nun über die grundlegenden Begriffe, Konzepte und Schritte verfügen, die mit APIs verbunden sind, können wir uns eine Beispiel-API-Anfrage in der Praxis ansehen.

Die Seite aus unserem Browser-Beispiel hat die URL &quot;`https://business.adobe.com/products/experience-platform/adobe-experience-platform.html`&quot;. Wenn auf den Adobe Experience Platform-Link geklickt wird, stellt der Browser eine `GET` -Anfrage für diese Seite. Da wir den Browser haben, der die Arbeit für uns erledigt, müssen wir nur klicken, aber wenn ein Programmierer möchte, dass diese Anfrage in einer Software-Anwendung erfolgt, muss er alle erforderlichen Details angeben, damit die API-Anfrage erfolgreich erfüllt werden kann.

So sieht das im Code aus:

```js
fetch(
  "https://business.adobe.com/products/experience-platform/adobe-experience-platform.html",
  {
    headers: {
      accept:
        "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
      "accept-language": "en-US,en;q=0.9",
      "sec-ch-ua":
        '" Not A;Brand";v="99", "Chromium";v="101", "Microsoft Edge";v="101"',
      "sec-fetch-dest": "document",
      "sec-fetch-mode": "navigate",
      "sec-fetch-site": "none",
      "sec-fetch-user": "?1",
      "upgrade-insecure-requests": "1",
    },
    referrerPolicy: "strict-origin-when-cross-origin",
    body: null,
    method: "GET",
    mode: "cors",
    credentials: "include",
  }
);
```

Im obigen Code können Sie den `URL` sehen, den der Browser anfordert, und unten sehen Sie die `method: "GET"` -Anforderungsmethode. Die anderen Codezeilen sind ebenfalls Teile der Anfrage, überschreiten jedoch den Geltungsbereich dieses Artikels.


*[API]: Application Programming Interface
*[URL]: Uniform Resource Locator
*[HTTP]: HyperText Transfer Protocol
*[DNS]: Domain Name System
