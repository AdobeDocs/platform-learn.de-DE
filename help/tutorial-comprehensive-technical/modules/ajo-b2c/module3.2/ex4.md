---
title: Adobe Journey Optimizer - Journey und Nachricht konfigurieren
description: Adobe Journey Optimizer - Journey und Nachricht konfigurieren
kt: 5342
doc-type: tutorial
exl-id: dc7c6f18-06d2-4497-96b0-8dc78d389731
source-git-commit: c531412a2c0a5c216f49560e01fb26b9b7e71869
workflow-type: tm+mt
source-wordcount: '1470'
ht-degree: 5%

---

# 3.2.4 Erstellen von Journey und Nachrichten

In dieser Übung erstellen Sie mithilfe von Adobe Journey Optimizer eine Journey und mehrere Textnachrichten.

In diesem Anwendungsfall besteht das Ziel darin, je nach Wetterbedingungen des Standorts Ihres Kunden unterschiedliche Nachrichten zu senden. Es wurden drei Szenarien definiert:

- Kälter als 10° Celsius
- Zwischen 10° und 25° Celsius
- Wärmer als 25° Celsius

Für diese drei Bedingungen müssen Sie drei Nachrichten in Adobe Journey Optimizer definieren.

## 3.2.4.1 Journey erstellen

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

Wechseln Sie im linken Menü zu **Journey** und klicken Sie auf **Journey erstellen** um mit der Erstellung Ihres Journey zu beginnen.

![Demo](./images/jocreate.png)

Sie sollten Ihren Journey mit dem Vornamen versehen.

Verwenden Sie `--aepUserLdap-- - Geofence Entry Journey` als Namen für die Journey. Es dürfen derzeit keine anderen Werte festgelegt werden. Klicken Sie auf **Speichern**.

![Demo](./images/joname.png)

Sehen Sie sich auf der linken Seite Ihres Bildschirms &quot;**&quot;**. In dieser Liste sollte das zuvor erstellte Ereignis angezeigt werden. Wählen Sie es aus und ziehen Sie es dann per Drag-and-Drop auf die Journey-Arbeitsfläche. Ihr Journey sieht dann wie folgt aus: Klicken Sie auf **Speichern**.

![Demo](./images/joevents.png)

Klicken Sie anschließend auf **Orchestrierung**. Jetzt sehen Sie die verfügbaren **Orchestration**-Funktionen. Wählen Sie **Bedingung** aus und ziehen Sie es dann per Drag-and-Drop auf die Journey-Arbeitsfläche.

![Demo](./images/jo2.png)

Für diese Bedingung müssen jetzt drei Pfade konfiguriert werden:

- Es ist kälter als zehn Grad Celsius
- Es ist zwischen 10° und 25° Celsius
- Es ist wärmer als 25° Celsius

Definieren wir die erste Bedingung.

### Bedingung 1: Kälter als 10° Celsius

Klicken Sie auf **Bedingung**.  Klicken Sie auf **Path1** und bearbeiten Sie den Namen des Pfads in **älter als 10 C**. Klicken Sie auf das **Bearbeiten**-Symbol für den Ausdruck von Path1.

![Demo](./images/jo5.png)

Daraufhin wird ein leerer Bildschirm **Einfacher Editor** angezeigt. Ihre Abfrage ist etwas komplexer, daher benötigen Sie den **Erweiterten Modus**. Klicken Sie **Erweiterter Modus**.

![Demo](./images/jo7.png)

Daraufhin wird der &quot;**Editor“ angezeigt** mit dem Code eingegeben werden kann.

![Demo](./images/jo9.png)

Wählen Sie den folgenden Code aus und fügen Sie ihn in den **Erweiterten Editor“**.

`#{--aepUserLdap--WeatherApi.--aepUserLdap--WeatherByCity.main.temp} <= 10`

Sie werden es dann sehen.

![Demo](./images/jo10.png)

Um die Temperatur als Teil dieser Bedingung abzurufen, müssen Sie die Stadt angeben, in der sich der Kunde derzeit befindet.
**Stadt** muss mit dem dynamischen `q` verknüpft sein, genau wie Sie es zuvor in der Open Weather-API-Dokumentation gesehen haben.

Klicken Sie auf **Feld (dynamischer Wert: q** wie im Screenshot gezeigt.

![Demo](./images/jo11.png)

Anschließend müssen Sie das Feld finden, das die aktuelle Stadt des Kunden in einer der verfügbaren Datenquellen enthält. In diesem Fall müssen Sie es unter &quot;**&quot;**.

![Demo](./images/jo12.png)

Sie können das Feld finden, indem Sie zu `--aepUserLdap--GeofenceEntry.placeContext.geo.city` navigieren.

Durch Klicken auf dieses Feld oder Klicken auf **+** wird es als dynamischer Wert für den `q` hinzugefügt. Dieses Feld wird beispielsweise mit dem Geolocation-Service ausgefüllt, den Sie in Ihrer Mobile App implementiert haben. In diesem Fall simulieren Sie dies mithilfe der Datenerfassungseigenschaft der Demo-Website. Klicken Sie auf **OK**.

![Demo](./images/jo13.png)

### Bedingung 2: Zwischen 10° und 25° Celsius

Nachdem Sie die erste Bedingung hinzugefügt haben, wird dieser Bildschirm angezeigt. Klicken Sie **Pfad hinzufügen**.

![Demo](./images/joc2.png)

Doppelklicken Sie auf **Path1** und bearbeiten Sie den Pfadnamen in **Zwischen 10 und 25 C**. Klicken Sie auf **Bearbeiten** für den Ausdruck unter diesem Pfad.

![Demo](./images/joc6.png)

Daraufhin wird ein leerer Bildschirm **Einfacher Editor** angezeigt. Ihre Abfrage ist etwas komplexer, daher benötigen Sie den **Erweiterten Modus**. Klicken Sie **Erweiterter Modus**.

![Demo](./images/jo7.png)

Daraufhin wird der &quot;**Editor“ angezeigt** mit dem Code eingegeben werden kann.

![Demo](./images/jo9.png)

Wählen Sie den folgenden Code aus und fügen Sie ihn in den **Erweiterten Editor“**.

`#{--aepUserLdap--WeatherApi.--aepUserLdap--WeatherByCity.main.temp} > 10 and #{--aepUserLdap--WeatherApi.--aepUserLdap--WeatherByCity.main.temp} <= 25`

Sie werden es dann sehen.

![Demo](./images/joc10.png)

Um die Temperatur als Teil dieser Bedingung abzurufen, müssen Sie die Stadt angeben, in der sich der Kunde derzeit befindet.
Der **Stadt** muss mit dem dynamischen Parameter **q** verknüpft sein, wie Sie zuvor in der Open Weather-API-Dokumentation gesehen haben.

Klicken Sie auf **Feld (dynamischer Wert: q** wie im Screenshot gezeigt.

![Demo](./images/joc11.png)

Anschließend müssen Sie das Feld finden, das die aktuelle Stadt des Kunden in einer der verfügbaren Datenquellen enthält.

![Demo](./images/jo12.png)

Sie können das Feld finden, indem Sie zu `--aepUserLdap--GeofenceEntry.placeContext.geo.city` navigieren. Wenn Sie auf dieses Feld klicken, wird es als dynamischer Wert für den Parameter &quot;**&quot;**. Dieses Feld wird beispielsweise mit dem Geolocation-Service ausgefüllt, den Sie in Ihrer Mobile App implementiert haben. In diesem Fall simulieren Sie dies mithilfe der Datenerfassungseigenschaft der Demo-Website. Klicken Sie auf **OK**.

![Demo](./images/jo13.png)

Als Nächstes fügen Sie die dritte Bedingung hinzu.

### Zustand 3: wärmer als 25° Celsius

Nachdem Sie die zweite Bedingung hinzugefügt haben, wird dieser Bildschirm angezeigt. Klicken Sie **Pfad hinzufügen**.

![Demo](./images/joct2.png)

Doppelklicken Sie auf Path1, um den Namen in &quot;**als 25 C“** ändern.
Klicken Sie dann auf das **Bearbeiten**-Symbol für den Ausdruck unter diesem Pfad.

![Demo](./images/joct6.png)

Daraufhin wird ein leerer Bildschirm **Einfacher Editor** angezeigt. Ihre Abfrage ist etwas komplexer, daher benötigen Sie den **Erweiterten Modus**. Klicken Sie **Erweiterter Modus**.

![Demo](./images/jo7.png)

Daraufhin wird der &quot;**Editor“ angezeigt** mit dem Code eingegeben werden kann.

![Demo](./images/jo9.png)

Wählen Sie den folgenden Code aus und fügen Sie ihn in den **Erweiterten Editor“**.

`#{--aepUserLdap--WeatherApi.--aepUserLdap--WeatherByCity.main.temp} > 25`

Sie werden es dann sehen.

![Demo](./images/joct10.png)

Um die Temperatur als Teil dieser Bedingung abzurufen, müssen Sie die Stadt angeben, in der sich der Kunde derzeit befindet.
Der **Stadt** muss mit dem dynamischen Parameter **q** verknüpft sein, wie Sie zuvor in der Open Weather-API-Dokumentation gesehen haben.

Klicken Sie auf **Feld (dynamischer Wert: q** wie im Screenshot gezeigt.

![Demo](./images/joct11.png)

Anschließend müssen Sie das Feld finden, das die aktuelle Stadt des Kunden in einer der verfügbaren Datenquellen enthält.

![Demo](./images/jo12.png)

Sie können das Feld finden, indem Sie zu ```--aepUserLdap--GeofenceEntry.placeContext.geo.city``` navigieren. Wenn Sie auf dieses Feld klicken, wird es als dynamischer Wert für den Parameter &quot;**&quot;**. Dieses Feld wird beispielsweise mit dem Geolocation-Service ausgefüllt, den Sie in Ihrer Mobile App implementiert haben. In diesem Fall simulieren Sie dies mithilfe der Datenerfassungseigenschaft der Demo-Website. Klicken Sie auf **OK**.

![Demo](./images/jo13.png)

Sie haben jetzt drei konfigurierte Pfade. Klicken Sie auf **Speichern**.

![Demo](./images/jo3path.png)

Da dies eine Journey für Lernzwecke ist, konfigurieren Sie jetzt eine Reihe von Aktionen, um die Vielfalt der Optionen zu präsentieren, die Marketing-Experten jetzt zum Versand von Nachrichten haben.

## 3.2.4.2 Senden von Nachrichten für Pfad: Kälter als 10° Celsius

Für jeden Temperaturkontext versuchen Sie, eine Textnachricht an einen Kunden zu senden. Für diese Übung senden Sie eine echte Nachricht an einen Slack-Kanal anstelle einer Mobiltelefonnummer.

Konzentrieren wir uns auf den Pfad **Kälter als 10 C**.

![Demo](./images/p1steps.png)

Gehen Sie im linken Menü zurück zu **Aktionen** wählen Sie die `--aepUserLdap--TextSlack` Aktion aus und ziehen Sie sie dann nach der Aktion **Nachricht**.

![Demo](./images/joa18.png)

Wechseln Sie **Aktionsparameter** und klicken Sie auf das Symbol **Bearbeiten** für die `textToSlack`.

![Demo](./images/joa19.png)

Klicken Sie im Popup-Fenster auf **Erweiterter Modus**.

![Demo](./images/joa20.png)

Wählen Sie den folgenden Code aus, kopieren Sie ihn und fügen Sie ihn in den **Editor für den erweiterten Modus** ein. Klicken Sie auf **OK**.

`"Brrrr..." + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + ",  it's cold and freezing outside. Get comfortable at home with a 20% discount on a Disney+ subscription!"`

![Demo](./images/joa21.png)

Ihre abgeschlossene Aktion wird angezeigt. Klicken Sie auf **Speichern**.

![Demo](./images/joa22.png)

Dieser Pfad der Journey ist jetzt bereit.

## 3.2.4.3 Senden von Nachrichten für den Pfad zwischen 10° und 25° Celsius

Für jeden Temperaturkontext versuchen Sie, eine Nachricht an Ihren Kunden zu senden. Für diese Übung senden Sie eine echte Nachricht an einen Slack-Kanal anstelle einer Mobiltelefonnummer.

Konzentrieren wir uns auf **Zwischen 10 und 25 C** Pfad.

![Demo](./images/p2steps.png)

Gehen Sie im linken Menü zurück zu **Aktionen** wählen Sie die `--aepUserLdap--TextSlack` Aktion aus und ziehen Sie sie dann nach der Aktion **Nachricht**.

![Demo](./images/jop18.png)

Wechseln Sie **Aktionsparameter** und klicken Sie auf das Symbol **Bearbeiten** für die `textToSlack`.

![Demo](./images/joa19z.png)

Klicken Sie im Popup-Fenster auf **Erweiterter Modus**.

![Demo](./images/joa20.png)

Wählen Sie den folgenden Code aus, kopieren Sie ihn und fügen Sie ihn in den **Editor für den erweiterten Modus** ein. Klicken Sie auf **OK**.

`"What nice weather for the time of year, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " 20% discount on Apple AirPods so you can go for a walk and listen to your favorite podcast!"`

![Demo](./images/jop21.png)

Ihre abgeschlossene Aktion wird angezeigt. Klicken Sie auf **OK**.

![Demo](./images/jop22.png)

Dieser Pfad der Journey ist jetzt bereit.

## 3.2.4.4 Senden von Nachrichten für Pfad: wärmer als 25° Celsius

Für jeden Temperaturkontext versuchen Sie, eine Nachricht an Ihren Kunden zu senden. Für diese Übung senden Sie eine echte Nachricht an einen Slack-Kanal anstelle einer Mobiltelefonnummer.

Konzentrieren wir uns auf **wärmer als 25 C** Pfad.

![Demo](./images/p3steps.png)

Gehen Sie im linken Menü zurück zu **Aktionen** wählen Sie die `--aepUserLdap--TextSlack` Aktion aus und ziehen Sie sie dann nach der Aktion **Nachrichten**.

![Demo](./images/jod18.png)

Wechseln Sie **Aktionsparameter** und klicken Sie auf das Symbol **Bearbeiten** für die `textToSlack`.

![Demo](./images/joa19zzz.png)

Klicken Sie im Popup-Fenster auf **Erweiterter Modus**.

![Demo](./images/joa20.png)

Wählen Sie den folgenden Code aus, kopieren Sie ihn und fügen Sie ihn in den **Editor für den erweiterten Modus** ein. Klicken Sie auf **OK**.

`"So warm, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + "! 20% discount on adding 10GB of extra data so you can get online at the beach!"`

![Demo](./images/jod21.png)

Ihre abgeschlossene Aktion wird angezeigt. Klicken Sie auf **Speichern**.

![Demo](./images/jod22.png)

Dieser Pfad der Journey ist jetzt bereit.

## Publish auf Journey 3.2.4.5

Ihr Journey ist jetzt vollständig konfiguriert. Klicken Sie auf **Veröffentlichen**.

![Demo](./images/jodone.png)

Klicken Sie erneut auf **** Publish.

![Demo](./images/jopublish1.png)

Ihr Journey ist jetzt veröffentlicht.

![Demo](./images/jopublish2.png)

Nächster Schritt: [3.2.5 Trigger des Journey](./ex5.md)

[Zurück zum Modul 3.2](journey-orchestration-external-weather-api-sms.md)

[Zurück zu „Alle Module“](../../../overview.md)
