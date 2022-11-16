---
title: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Externe Datenquelle definieren
description: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Externe Datenquelle definieren
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: e3e04415-4258-4ad7-a227-0e68dfcba235
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 4%

---

# 8.2 Externe Datenquelle definieren

In dieser Übung erstellen Sie eine benutzerdefinierte externe Datenquelle, indem Sie Adobe Journey Optimizer verwenden.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxId--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend auf das **Verwalten** Schaltfläche unter **Data Sources**.

![Demo](./images/menudatasources.png)

Sie werden dann die **Data Sources** Liste.
Klicken **Datenquelle erstellen** , um Ihre Datenquelle hinzuzufügen.

![Demo](./images/dshome.png)

Es wird ein leeres Datenquellen-Popup angezeigt.

![Demo](./images/emptyds.png)

Bevor Sie mit der Konfiguration beginnen können, benötigen Sie ein Konto mit der **Wetterkarte öffnen** Dienst. Führen Sie diese Schritte aus, um Ihr Konto zu erstellen und Ihren API-Schlüssel zu erhalten.

Navigieren Sie zu [https://openweathermap.org/](https://openweathermap.org/). Klicken Sie auf der Startseite auf **Anmelden**.

![WeatherMap](./images/owm.png)

Klicken **Konto erstellen**.

![WeatherMap](./images/owm1.png)

Füllen Sie die Details aus.

![WeatherMap](./images/owm2.png)

Klicken **Konto erstellen**.

![WeatherMap](./images/owm3.png)

Sie werden dann zu Ihrer Kontoseite weitergeleitet.

![WeatherMap](./images/owm4.png)

Klicken Sie im Menü auf **API-Schlüssel** um Ihren API-Schlüssel abzurufen, den Sie zum Einrichten Ihrer benutzerdefinierten externen Datenquelle benötigen.

![WeatherMap](./images/owm5.png)

Ein **API-Schlüssel** sieht wie folgt aus: `b2c4c36b6bb59c3458d6686b05311dc3`.

Sie finden die **API-Dokumentation** für **Aktuelles Wetter** [here](https://openweathermap.org/current).

In unserem Anwendungsfall implementieren wir die Verbindung mit Open Weather Map basierend auf der Stadt, in der sich der Kunde befindet.

![WeatherMap](./images/owm6.png)

Gehen Sie zurück zu **Adobe Journey Optimizer**, um zu leeren **Externe Datenquelle** Popup.

![Demo](./images/emptyds.png)

Verwenden Sie als Namen für die Datenquelle . `--demoProfileLdap--WeatherApi`. In diesem Beispiel lautet der Name der Datenquelle `vangeluwWeatherApi `.

Legen Sie Beschreibung auf fest: `Access to the Open Weather Map`.

Die URL für die Open Weather Map-API lautet: **http://api.openweathermap.org/data/2.5/weather?units=metric**

![Demo](./images/dsname.png)

Als Nächstes müssen Sie die zu verwendende Authentifizierung auswählen.

Verwenden Sie diese Variablen:

| Feld | Wert |
|:-----------------------:| :-----------------------|
| Typ | **API-Schlüssel** |
| Name | **APPID** |
| Wert | **Ihren API-Schlüssel** |
| Standort | **Abfrageparameter** |

![Demo](./images/dsauth.png)

Schließlich müssen Sie eine **FieldGroup**; dies ist im Grunde die Anfrage, die Sie an die Wetter-API senden werden. In unserem Fall möchten wir den Namen der Stadt verwenden, um das aktuelle Wetter für diese Stadt anzufordern.

![Demo](./images/fg.png)

Gemäß der Wetter-API-Dokumentation müssen wir einen Parameter senden `q=City`.

![Demo](./images/owmapi.png)

Um die erwartete API-Anfrage zu erfüllen, konfigurieren Sie Ihre FieldGroup wie folgt:

>[!IMPORTANT]
>
>Der Feldgruppenname muss eindeutig sein. Verwenden Sie diese Namenskonvention: `--demoProfileLdap--WeatherByCity` In diesem Fall sollte der Name `vangeluwWeatherByCity`

![Demo](./images/fg1.png)

Für die Antwort-Payload müssen Sie ein Beispiel der Antwort einfügen, die von der Wetter-API gesendet wird.

Die erwartete API-JSON-Antwort finden Sie auf der Seite API-Dokumentation . [here](https://openweathermap.org/current).

![Demo](./images/owmapi1.png)

Alternativ können Sie die JSON-Antwort hier kopieren:

```json
{"coord": { "lon": 139,"lat": 35},
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01n"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 281.52,
    "feels_like": 278.99,
    "temp_min": 280.15,
    "temp_max": 283.71,
    "pressure": 1016,
    "humidity": 93
  },
  "wind": {
    "speed": 0.47,
    "deg": 107.538
  },
  "clouds": {
    "all": 2
  },
  "dt": 1560350192,
  "sys": {
    "type": 3,
    "id": 2019346,
    "message": 0.0065,
    "country": "JP",
    "sunrise": 1560281377,
    "sunset": 1560333478
  },
  "timezone": 32400,
  "id": 1851632,
  "name": "Shuzenji",
  "cod": 200
}
```

Kopieren Sie die obige JSON-Antwort in die Zwischenablage und rufen Sie dann den Konfigurationsbildschirm für benutzerdefinierte Datenquellen auf.

Klicken Sie auf **Payload bearbeiten** Symbol.

![Demo](./images/owmapi2.png)

Es wird ein Popup angezeigt, in das Sie jetzt die oben genannte JSON-Antwort einfügen müssen.

![Demo](./images/owmapi3.png)

Fügen Sie Ihre JSON-Antwort ein, danach wird dies angezeigt. Klicken Sie auf **Speichern**.

![Demo](./images/owmapi4.png)

Ihre benutzerdefinierte Datenquellenkonfiguration ist jetzt abgeschlossen. Scrollen Sie nach oben und klicken Sie auf **Speichern**.

![Demo](./images/dssave.png)

Ihre Datenquelle wurde erfolgreich erstellt und ist Teil der **Data Sources** Liste.

![Demo](./images/dslist.png)

Nächster Schritt: [8.3 Benutzerdefinierte Aktion definieren](./ex3.md)

[Zurück zu Modul 8](journey-orchestration-external-weather-api-sms.md)

[Zu allen Modulen zurückkehren](../../overview.md)
