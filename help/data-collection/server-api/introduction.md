---
title: Grundlegende Einführung in APIs
description: Einführung in die Programmierschnittstellen für Anwendungen
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

# API 101 - eine grundlegende Einführung in APIs

API steht für Application Programming Interface. Es bedeutet genau das, was es sagt - es gibt Schnittstellen zwischen Programmen und diese Schnittstellen ermöglichen es diesen Programmen zu kommunizieren. Wenn Programmierer Software-Anwendungen entwickeln, benötigen sie oft ihre Software, um mit anderer Software oder Hardware zu kommunizieren. Die API definiert das Was, Wie, Wann, Wo und Warum für diese Kommunikationen und Interaktionen.

APIs bieten eine Möglichkeit, geschäftliche Herausforderungen mit Software zu lösen. In den meisten Unternehmen ist dies eine Gemeinschaftsanstrengung. Die Zusammenarbeit ist immer einfacher mit einem gemeinsamen Verständnis der wichtigsten Begriffe, Konzepte und Schritte.

Wenn Sie daran denken, auf einen Link auf einer Web-Seite zu klicken, verwendet der Browser beim Klicken auf den Link eine ganze Reihe von APIs. Der Browser erkennt den Klick, stellt die Anfrage für die Seite, die Sie besuchen möchten, ruft die Seite über das Internet ab und zeigt sie dann auf Ihrem Bildschirm an. Es gibt viele kleinere Schritte dazwischen, aber Ihr Browser ist eine Software, die mit einer Vielzahl von APIs kommuniziert und interagiert, nur um Ihnen eine Web-Seite zu zeigen. In diesem Artikel werden Begriffe, Konzepte und Schritte hervorgehoben, die bei der Verwendung oder Diskussion von APIs wichtig sind.

Am Ende dieses Artikels sollten Sie ein klares Verständnis dieser grundlegenden Begriffe, Konzepte und Schritte haben. Die API-Dokumentation kann umfangreich sein, und die Diskussionen über die Verwendung von APIs für bestimmte Anwendungsfälle können sehr detailliert werden. Das Navigieren in der Dokumentation und das Besprechen von APIs ist einfacher und produktiver, mit klaren Grundlagen und gemeinsamem Verständnis.

>[!NOTE]
>
> Es gibt zwar viele APIs, aber der Fokus liegt hier auf Web- und Browser-APIs: Grundsätzlich, wenn eine Software-Anwendung über das Internet mit einer anderen interagiert.

## API-Begriffe und -Konzepte

Was bedeutet ein Wort oder eine Wortgruppe, und wie kann ich einfach und leicht darüber nachdenken? In einer API bezeichnet der „Anwendungsteil“ eine Softwareanwendung oder ein Programm. Der Teil „Programmierschnittstelle“ bezieht sich darauf, wie und wo eine Anwendung zu bestimmten Zwecken mit einer anderen Anwendung interagiert. Wenn Sie in unserem Webseitenbeispiel auf einen Link klicken, sendet der Browser eine Anforderung an einen Server für die Web-Seite.

![Bild eines Hyperlinks mit der Ziel-URL](../assets/api101-link-destination.png)

In diesem Screenshot zeigt der Mauszeiger auf den Link für Adobe Experience Platform. Unten befindet sich die Statusleiste des Webbrowsers, die die „Adresse“ der Seite anzeigt, die der Browser erhält. Mit anderen Worten: Wenn Sie auf den Adobe Experience Platform-Link klicken, wird der Browser aufgefordert, „die Seite für mich abzurufen, damit ich sie hier auf meinem Bildschirm sehen kann“.

Wenn auf einen Link geklickt wird, sendet der Browser eine Anfrage an einen Server, um eine Seite abzurufen. Dies ist eine `GET` Anfrage, eine der häufig mit Web-APIs verwendeten Anfragemethoden. Eine Sache, die der Browser benötigt, um die Anfrage zu erfüllen, ist die Seite „Adresse“ - wo ist sie im Web?

### Teile einer URL

![Browser-Adressleiste mit URL](../assets/api101-address-bar.png)

Die meisten Browser verfügen über eine „Adressleiste“, die einige oder alle „Adressen“ für eine Web-Seite anzeigt. Wenn der Browser die Seite für den angeklickten Link „abruft“, wird die „Adresse“ der Seite in dieser Adressleiste angezeigt. Was ist also die „Adresse“ für eine Webseite?

Das `https://business.adobe.com/products/experience-platform/adobe-experience-platform.html` oben ist die Adresse einer Web-Seite. Sie wird als URL oder Uniform Resource Locator bezeichnet. URLs können auf eine Seite wie diese oder eine Bilddatei, ein Video oder andere Dateitypen verweisen.

![Teile einer URL](../assets/api101-url-parts.jpg)

Diese Adresse, die URL, enthält bestimmte Teile, die für Web- und Browser-APIs sehr relevant sind.

**Schema**

Der obige `scheme` wird auch als `protocol` mit Web-APIs bezeichnet und ist normalerweise entweder `http` oder `https`. Unter HTTP oder HyperText Transfer Protocol versteht man, wie Ressourcen wie Web-Seiten von einem Webserver an einen Webbrowser übertragen werden. HTTPS ist die sichere Version, bei der die Übertragung über das Internet erfolgt, wobei die Sicherheit verwendet wird, um Interferenzen mit der übertragenen Ressource zu verhindern. Häufig wird ein kleines Sperrsymbol in der Adressleiste des Browsers angezeigt, wenn eine Seite über HTTPS aufgerufen wird.

Bei Web-APIs erfolgt die Übertragung dieser Ressourcen über HTTP-Anfragen - Anfragen über HTTP, mit anderen Worten.

**Hosts und Domains**

Der `business.adobe.com` ist der Host der angeforderten Ressource. Wenn auf unseren Beispiel-Link geklickt wird, verwendet der Browser diesen Teil der URL, um den Server zu finden, auf dem die Seite gehostet wird. Es ist nicht immer genau das gleiche wie der Web-Server, aber auf einer grundlegenden Ebene können wir es als den Server, wo der Browser die von uns angeforderte Seite erhalten wird denken.

Domain-Namen sind Teil des Domain Name System, besser bekannt als DNS. Die meisten Menschen betrachten `adobe.com` oder `example.com` als „Domain-Namen“, aber es gibt Teile, die für APIs relevant sind. `www.adobe.com` und `business.adobe.com` können als Domain-Namen bezeichnet werden, die `www.` und die `business.` werden jedoch als Subdomains bezeichnet. APIs interagieren oft mit einer URL, die eine Subdomain wie `api.example.com` oder `sub.www.example.com` enthält.

Es ist sehr üblich, dass der Begriff _Host“_ einen vollständigen Domain-Namen einschließlich einer Subdomain wie `business.adobe.com` verweist. Es ist auch üblich, die Begriffe _Domain_ oder _Domain-Name_ zu sehen, wenn auf einen Host ohne die Subdomain wie `adobe.com` verwiesen wird. Die spezifischen Begriffe für jeden Teil und jede Variante eines Hosts zu lernen, ist hier nicht wichtig. Es ist jedoch wichtig zu wissen, dass diese Begriffe häufig verwendet werden, damit Sie alle relevanten Details für Ihr Unternehmen und Ihre Gespräche klären können.

**Herkunft**

„Herkunft“ ist ein weiterer Begriff, der zu beachten ist, der eng mit den Teilen einer URL verbunden ist. Auf einer grundlegenden Ebene ist ein Ursprung ungefähr der `scheme` plus der `host` plus der `domain` wie `https://business.adobe.com`. Unterschiedliche Werte stellen häufig unterschiedliche Ursprünge dar, z. B. `https://business.adobe.com` und `http://business.adobe.com` sind nicht dieselben Ursprünge, da sie unterschiedliche Schemata haben. `https://www.adobe.com` und `https://business.adobe.com` sind aufgrund der verschiedenen Subdomains bei vielen Anwendungen ebenfalls nicht identisch.

**Pfad**

Das letzte Bit im obigen URL-Beispiel ist die `path` zur Ressource - die Seite in unserem Beispiel. Der `/products/experience-platform/` Teil stellt normalerweise Ordner oder Ordner auf dem Webserver dar. So wie wir Ordner oder Verzeichnisse auf unseren Computern für Dokumente und Fotos haben, haben wir auch Ordner auf Webservern, um Inhalte zu organisieren. Und schließlich ist der `/adobe-experience-platform.html` Teil der Name der Datei - die Web-Seite.

Es gibt weitere, detailliertere Teile einer URL, die im nächsten Teil dieser Reihe hervorgehoben werden.

### APIs von Drittanbietern

Web-APIs werden auch als Drittanbieter-APIs bezeichnet. Stellen Sie sich das so vor wie die an einer Transaktion beteiligten Parteien. In unserem Link-Beispiel sind Sie - oder genauer gesagt Ihr Browser - die erste Partei in der Anfrage für die Seite. Der Webserver ist der zweite Anbieter. Also, wo ist die dritte?

Es ist üblich, dass eine Web-Seite Inhalte oder Ressourcen von anderen Hosts oder Quellen enthält. In diesen Fällen sendet der Browser, wenn er mit der Anzeige der Seite beginnt, eine weitere Reihe von Anfragen an diese anderen Hosts oder „Drittanbieter“, die diese Ressourcen hosten. Dies ist sehr häufig, insbesondere für Medieninhalte wie Videos oder Bilder, aber auch für Daten, die zum Zeitpunkt der Anzeige oder Verwendung aktualisiert werden müssen. Die aktuelle Tageszeit, das aktuelle Wetter oder eine personalisierte Willkommensnachricht für eine bestimmte Person abzurufen, sind alles Beispiele, bei denen eine Drittanbieter-API die richtige Ressource zur richtigen Zeit bereitstellen kann. Häufig kommen diese Anfragen von APIs von Drittanbietern.

## Häufige Verwendungszwecke für Web-APIs

Neben der Tageszeit, dem Wetter oder personalisierten Inhalten gibt es viele Verwendungsmöglichkeiten für Web-APIs. Social-Media-Plattformen wie Twitter, TikTok, Facebook, LinkedIn, Snapchat, Pinterest und andere verfügen über eine Vielzahl von APIs, die Programmierer mit ihren Programmen verwenden können. Und natürlich verfügt Adobe auch über [eine Vielzahl von APIs](https://developer.adobe.com/apis) die Programmierer verwenden, damit ihre Software mit Adobe-Produkten und -Services interagieren kann. Software-Produkte und -Services greifen über diese APIs auf andere Software-Produkte und -Services zu.

## Beispiel-APIs

Browser-APIs ermöglichen es Programmierern, direkt mit Funktionen des Browsers zu interagieren. Mit der Batterie-API kann die Software den Akkustatus eines Geräts überprüfen, sodass sie Sie bei Bedarf warnen kann. Mit der Zwischenablage-API kann Software mit der Zwischenablage Ihres Geräts kopieren oder einfügen. Mit der Vollbild-API bietet Software die Möglichkeit, die Ansicht auf den Vollbildmodus des Geräts, z. B. YouTube, zu erweitern.

Die Adobe Experience Platform-Datenzugriffs-API ist eine Web-API, mit der Programmierer auf Datensatzdateien in Adobe Experience Platform zugreifen und diese herunterladen können, damit sie Kundenprofildaten in ihren eigenen Programmen verwenden können. Es ist üblich, dass APIs wie diese Teil eines Software-Automatisierungsprozesses sind, bei dem Software so programmiert ist, dass sie eine Sequenz von Schritten ausführt, indem mehrere APIs kombiniert verwendet werden. Dies kann häufig eine erhebliche Kosteneinsparung im Vergleich zur manuellen Durchführung derselben Schritte darstellen.

## API-Endpunkte

Wenn Programmierer einen Browser oder eine Web-API in ihren Programmen „verwenden“, stellen sie normalerweise Anfragen zum Senden oder Empfangen von Ressourcen, wie z. B. unser Beispiel-Browser, der eine Web-Seite anfordert. In der API-Dokumentation werden für diese Anfragen häufig „Endpunkte“ aufgeführt, z. B.: `https://platform.adobe.io/data/foundation/export/files/{dataSetFileId}`. Dies ist das spezifische Muster oder der „Endpunkt“ der Platform Data Access-API, das ein Programmierer verwendet, um eine Datensatzdatei abzurufen.

Der `{dataSetFileId}`, der von diesen geschweiften Klammern umgeben ist, stellt einen Wert dar, den der Programmierer in der Anfrage senden muss. Die URL in der eigentlichen API-Anfrage würde also in etwa so aussehen, `https://platform.adobe.io/data/foundation/export/files/xyz123brb` der `xyz123brb` eine gültige ID der Datensatzdatei sein muss, die der Programmierer empfangen möchte.

Anders ausgedrückt: Genau wie der Browser eine Seite mit einer bestimmten URL abruft, rufen API-Anfragen Ressourcen von einem bestimmten Endpunkt wie diesem Datensatzbeispiel ab oder senden Ressourcen an diesen.

## HTTP-Anfragemethoden

An dieser Stelle sollte klar sein, dass Web-APIs Anfragen für Ressourcen wie Web-Seiten oder Datensätze stellen. Wie die meisten Softwarekonzepte folgen diese HTTP-Anfragen wiederholbaren Mustern. Eine Anforderung wird von einer Softwareanwendung an eine andere Softwareanwendung gesendet, die die Anforderung auswertet und dann antwortet: Der Browser fordert eine Seite von einem Webserver an und antwortet mit dem Seiteninhalt.

Der gesamte Prozess von der Anfrage bis zur Antwort umfasst viele kleinere und sehr detaillierte Schritte, aber die Anfragemethoden sind einfach. Anfragemethoden definieren den angeforderten Vorgang.

**`GET`**

Die `GET`-Anfragemethode wird verwendet, wenn eine Antwort angefordert wird, die eine Ressource bereitstellt, z. B. unsere Web-Seite und Datensatzbeispiele. Wenn wir in einem Browser auf einen Link klicken oder auf einen Link auf einem Mobilgerät tippen, stellen wir hinter den Kulissen eine `GET` Anfrage.

**`POST`**

Die `POST` Methode sendet Daten mit der Anfrage. Es mag merkwürdig klingen, dass eine „Anfrage“ Daten sendet, aber die Idee ist, dass bei der API-Anfrage der Endpunkt - die empfangende Software - aufgefordert wird, die Anfrage zu akzeptieren und im Falle eines `POST` auch die gesendeten Daten zu akzeptieren. Die gesendeten Daten werden normalerweise in einen Datenspeicher wie eine Datenbank oder eine Datei geschrieben, damit sie gespeichert werden können.

**`PUT`**

Die `PUT` Anfragemethode ähnelt `POST`, da sie Daten sendet, aber wenn die gesendeten Daten bereits am Endpunkt vorhanden sind, aktualisiert ein `PUT` die vorhandenen Daten, indem er sie ersetzt. Ein `POST` wird nicht aktualisiert, sondern lediglich gesendet, sodass mehrere `POST`-Anfragen mehrere Datensätze der gesendeten Daten erstellen können, anstatt einen vorhandenen Datensatz zu aktualisieren.

**`PATCH`**

Die `PATCH`-Anfragemethode wird verwendet, um Daten zu senden, die einen Teil eines vorhandenen Datensatzes aktualisieren, z. B. wenn wir unsere Adresse ändern, indem wir unser Kontoprofil aktualisieren. Mit einer `POST` Anfrage konnte ein zusätzliches Profil erstellt werden, und mit einer `PUT` konnte das vorhandene Profil ersetzt werden. Durch die Verwendung der `PATCH` Methode aktualisieren wir jedoch einfach den relevanten Teil des vorhandenen Datensatzes, wie unsere Adresse.

**`DELETE`**

Die `DELETE`-Anfragemethode entfernt eine in der Anfrage angegebene Ressource, z. B. wenn wir auf einen Link klicken, um unser Kontoprofil vollständig zu löschen.

Es gibt mehrere andere, aber dies ist eine Liste der häufigsten Methoden beim Arbeiten mit APIs.

### Beispiel für eine Anfrage

Nachdem Sie nun über die grundlegenden Begriffe, Konzepte und Schritte bei -APIs verfügen, können wir uns ein Beispiel für eine API-Anfrage in der Praxis ansehen.

Die Seite aus unserem Browser-Beispiel hat eine URL von `https://business.adobe.com/products/experience-platform/adobe-experience-platform.html`. Wenn auf den Adobe Experience Platform-Link geklickt wird, führt der Browser eine `GET` Anfrage für diese Seite durch. Da wir den Browser haben, um die Arbeit für uns zu erledigen, müssen wir nur klicken, aber wenn ein Programmierer möchte, dass diese Anfrage in einer Software-Anwendung geschieht, müssen sie alle erforderlichen Details angeben, damit die API-Anfrage erfolgreich erfüllt wird.

So könnte das im Code aussehen:

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

Im obigen Code können Sie die `URL` sehen, die der Browser anfordert, und unten unten in der Nähe befindet sich die `method: "GET"`. Die anderen Codezeilen sind ebenfalls Teil der Anfrage, würden jedoch den Rahmen dieses Artikels sprengen.


*[API]: Anwendungsprogrammierschnittstelle
*[URL]: URL (Uniform Resource Locator)
*[HTTP]: HyperText Transfer Protocol
*[DNS]: Domain-Namenssystem
