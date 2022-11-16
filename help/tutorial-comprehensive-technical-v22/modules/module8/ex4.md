---
title: Adobe Journey Optimizer - Konfigurieren und Verwenden des SMS-Kanals in Adobe Journey Optimizer
description: Adobe Journey Optimizer - Konfigurieren und Verwenden des SMS-Kanals in Adobe Journey Optimizer
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 1a08f666-4ea3-43bc-ace7-5dc9854b89ad
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 6%

---

# 8.4 Journey und Nachrichten erstellen

In dieser Übung erstellen Sie eine Journey und mehrere Textnachrichten, indem Sie Adobe Journey Optimizer verwenden.

In diesem Anwendungsfall besteht das Ziel darin, je nach den Wetterbedingungen des Standorts Ihres Kunden unterschiedliche SMS-Nachrichten zu senden. Es wurden 3 Szenarien definiert:

- Kälter als 10° Celsius
- Zwischen 10° und 25° Celsius
- Warmer als 25° Celsius

Für diese drei Bedingungen müssen Sie drei SMS-Nachrichten in Adobe Journey Optimizer definieren.

## 8.4.1 Journey erstellen

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie [Adobe Experience Cloud](https://experience.adobe.com). Klicken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxId--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)


Gehen Sie im linken Menü zu **Journey** und klicken Sie auf **Journey erstellen** , um mit der Erstellung Ihrer Journey zu beginnen.

![Demo](./images/jocreate.png)

Du solltest zuerst deine Journey benennen.

Verwenden Sie als Namen für die Journey . `--demoProfileLdap-- - Geofence Entry Journey`. In diesem Beispiel lautet der Journey-Name `vangeluw - Geofence Entry Journey`. Derzeit dürfen keine anderen Werte festgelegt werden. Klicken Sie auf **OK**.

![Demo](./images/joname.png)

Sehen Sie sich auf der linken Bildschirmseite Folgendes an: **Veranstaltungen**. Ihr zuvor erstelltes Ereignis sollte in dieser Liste angezeigt werden. Wählen Sie es aus und ziehen Sie es per Drag-and-Drop auf die Journey-Arbeitsfläche. Ihre Journey sieht dann so aus. Klicken Sie auf **OK**.

![Demo](./images/joevents.png)

Klicken Sie anschließend auf **Orchestrierung**. Jetzt sehen Sie die verfügbaren **Orchestrierung** Funktionen. Auswählen **Bedingung**, ziehen Sie sie per Drag-and-Drop auf die Journey-Arbeitsfläche.

![Demo](./images/jo2.png)

Definieren Sie nun drei Bedingungen:

- Es ist kälter als 10° Celsius
- Es ist zwischen 10° und 25° Celsius
- Es ist wärmer als 25° Celsius

Definieren wir die erste Bedingung.

### Bedingung 1: Kälter als 10° Celsius

Klicken Sie auf **Bedingung**.  Klicken Sie auf **Pfad 1** und bearbeiten Sie den Namen des Pfads zu **Mindestens 10 C**. Klicken Sie auf **Bearbeiten** für den Ausdruck von Path1.

![Demo](./images/jo5.png)

Dann sehen Sie eine leere **Einfacher Editor** angezeigt. Ihre Abfrage wird ein wenig erweiterter sein, sodass Sie die **Erweiterter Modus**. Klicken **Erweiterter Modus**.

![Demo](./images/jo7.png)

Sie werden dann die **Erweiterter Editor** , der die Codeeingabe zulässt.

![Demo](./images/jo9.png)

Wählen Sie den unten stehenden Code aus und fügen Sie ihn in den **Erweiterter Editor**.

`#{--demoProfileLdap--WeatherApi.--demoProfileLdap--WeatherByCity.main.temp} <= 10`

Dann wirst du das sehen.

![Demo](./images/jo10.png)

Um die Temperatur als Teil dieser Bedingung abzurufen, müssen Sie die Stadt angeben, in der sich der Kunde derzeit befindet.
Die **Ort** muss mit dem dynamischen Parameter verknüpft werden `q`, genau wie wir es zuvor in der Open Weather API-Dokumentation gesehen haben.

Klicken Sie auf das Feld **dynamisches Feld: q** wie im Screenshot angegeben.

![Demo](./images/jo11.png)

Dann müssen Sie das Feld, das die aktuelle Stadt des Kunden enthält, in einer der verfügbaren Data Sources finden.

![Demo](./images/jo12.png)

Sie können das Feld suchen, indem Sie zu `--demoProfileLdap--GeofenceEntry.placeContext.geo.city`.

Durch Klicken auf dieses Feld wird es als dynamischer Wert für den Parameter hinzugefügt `q`. Dieses Feld wird beispielsweise durch den Geolocation-Service ausgefüllt, den Sie in Ihrer Mobile App implementiert haben. In unserem Fall simulieren wir dies mit der Admin Console der Demo-Website. Klicken Sie auf **OK**.

![Demo](./images/jo13.png)

### Bedingung 2: Zwischen 10° und 25° Celsius

Nachdem Sie die erste Bedingung hinzugefügt haben, sehen Sie diesen Bildschirm. Klicken **Pfad hinzufügen**.

![Demo](./images/joc2.png)

Doppelklicken Sie auf **Pfad 1** und bearbeiten Sie den Pfadnamen in **Zwischen 10 und 25 C**. Klicken Sie auf **Bearbeiten** für den Ausdruck diesen Pfad.

![Demo](./images/joc6.png)

Dann sehen Sie eine leere **Einfacher Editor** angezeigt. Ihre Abfrage wird ein wenig erweiterter sein, sodass Sie die **Erweiterter Modus**. Klicken **Erweiterter Modus**.

![Demo](./images/jo7.png)

Sie werden dann die **Erweiterter Editor** , der die Codeeingabe zulässt.

![Demo](./images/jo9.png)

Wählen Sie den unten stehenden Code aus und fügen Sie ihn in den **Erweiterter Editor**.

`#{--demoProfileLdap--WeatherApi.--demoProfileLdap--WeatherByCity.main.temp} > 10 and #{--demoProfileLdap--WeatherApi.--demoProfileLdap--WeatherByCity.main.temp} <= 25`

Dann wirst du das sehen.

![Demo](./images/joc10.png)

Um die Temperatur als Teil dieser Bedingung abzurufen, müssen Sie die Stadt angeben, in der sich der Kunde derzeit befindet.
Die **Ort** muss mit dem dynamischen Parameter verknüpft werden **q**, genau wie wir es zuvor in der Open Weather API-Dokumentation gesehen haben.

Klicken Sie auf das Feld **dynamisches Feld: q** wie im Screenshot angegeben.

![Demo](./images/joc11.png)

Dann müssen Sie das Feld, das die aktuelle Stadt des Kunden enthält, in einer der verfügbaren Data Sources finden.

![Demo](./images/jo12.png)

Sie können das Feld suchen, indem Sie zu `--demoProfileLdap--GeofenceEntry.placeContext.geo.city`. Durch Klicken auf dieses Feld wird es als dynamischer Wert für den Parameter hinzugefügt **q**. Dieses Feld wird beispielsweise durch den Geolocation-Service ausgefüllt, den Sie in Ihrer Mobile App implementiert haben. In unserem Fall simulieren wir dies mit der Admin Console der Demo-Website. Klicken Sie auf **OK**.

![Demo](./images/jo13.png)

Als Nächstes fügen Sie die dritte Bedingung hinzu.

### Bedingung 3: Warmer als 25° Celsius

Nachdem Sie die zweite Bedingung hinzugefügt haben, sehen Sie diesen Bildschirm. Klicken **Pfad hinzufügen**.

![Demo](./images/joct2.png)

Doppelklicken Sie auf Pfad1 , um den Namen in **Warmer als 25 C**.
Klicken Sie dann auf die **Bearbeiten** für den Ausdruck diesen Pfad.

![Demo](./images/joct6.png)

Dann sehen Sie eine leere **Einfacher Editor** angezeigt. Ihre Abfrage wird ein wenig erweiterter sein, sodass Sie die **Erweiterter Modus**. Klicken **Erweiterter Modus**.

![Demo](./images/jo7.png)

Sie werden dann die **Erweiterter Editor** , der die Codeeingabe zulässt.

![Demo](./images/jo9.png)

Wählen Sie den unten stehenden Code aus und fügen Sie ihn in den **Erweiterter Editor**.

`#{--demoProfileLdap--WeatherApi.--demoProfileLdap--WeatherByCity.main.temp} > 25`

Dann wirst du das sehen.

![Demo](./images/joct10.png)

Um die Temperatur als Teil dieser Bedingung abzurufen, müssen Sie die Stadt angeben, in der sich der Kunde derzeit befindet.
Die **Ort** muss mit dem dynamischen Parameter verknüpft werden **q**, genau wie wir es zuvor in der Open Weather API-Dokumentation gesehen haben.

Klicken Sie auf das Feld **dynamisches Feld: q** wie im Screenshot angegeben.

![Demo](./images/joct11.png)

Dann müssen Sie das Feld, das die aktuelle Stadt des Kunden enthält, in einer der verfügbaren Data Sources finden.

![Demo](./images/jo12.png)

Sie können das Feld suchen, indem Sie zu ```--demoProfileLdap--GeofenceEntry.placeContext.geo.city```. Durch Klicken auf dieses Feld wird es als dynamischer Wert für den Parameter hinzugefügt **q**. Dieses Feld wird beispielsweise durch den Geolocation-Service ausgefüllt, den Sie in Ihrer Mobile App implementiert haben. In unserem Fall simulieren wir dies mit der Admin Console der Demo-Website. Klicken Sie auf **OK**.

![Demo](./images/jo13.png)

Sie haben jetzt drei konfigurierte Pfade. Klicken Sie auf **OK**.

![Demo](./images/jo3path.png)

Da dies eine Journey für Lernzwecke ist, konfigurieren wir nun eine Reihe von Aktionen, um die Vielfalt der Optionen zu veranschaulichen, die Marketing-Experten jetzt haben, um Nachrichten zu senden.

## 8.4.2 Nachrichten für Pfad senden: Kälter als 10° Celsius

Für jeden Temperaturkontext versuchen wir, eine Textnachricht an unseren Kunden zu senden. Wir können eine Textnachricht nur senden, wenn eine Mobiltelefonnummer für einen Kunden verfügbar ist. Daher müssen wir zunächst überprüfen, ob wir dies tun.

Fokussieren wir uns auf **Mindestens 10 C**.

![Demo](./images/p1steps.png)

Nehmen wir noch einen **Bedingung** und ziehen Sie es wie im Screenshot unten angegeben. Wir werden überprüfen, ob für diesen Kunden eine Mobiltelefonnummer zur Verfügung steht.

![Demo](./images/joa1.png)

Da dies nur ein Beispiel ist, konfigurieren wir nur die Option, bei der der Kunde über eine Mobiltelefonnummer verfügt. Fügen Sie einen Titel von **Hat Mobiltelefon?**.

Klicken Sie auf **Bearbeiten** -Symbol für den Ausdruck für **Pfad 1** Pfad.

![Demo](./images/joa2.png)

Navigieren Sie in den Datenquellen auf der linken Seite zu **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. Sie lesen die Mobiltelefonnummer jetzt direkt aus dem Echtzeit-Kundenprofil von Adobe Experience Platform.

![Demo](./images/joa3.png)

Feld auswählen **Zahl**, ziehen Sie es und legen Sie es auf die Arbeitsfläche &quot;Bedingung&quot;ab.

Operator auswählen **ist nicht leer**. Klicken Sie auf **OK**.

![Demo](./images/joa4.png)

Dann wirst du das sehen. Klicken **OK** erneut.

![Demo](./images/joa6.png)

Ihre Journey wird dann so aussehen. Klicken Sie auf **Aktionen** wie im Screenshot angegeben.

![Demo](./images/joa8.png)

Aktion auswählen **SMS** und ziehen Sie es dann nach der soeben hinzugefügten Bedingung per Drag-and-Drop.

![Demo](./images/joa9.png)

Legen Sie die **Kategorie** nach **Marketing** und wählen Sie eine SMS-Oberfläche aus, über die Sie SMS senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **SMS**.

![ACOP](./images/journeyactions1.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2.png)

Jetzt wird das Nachrichten-Dashboard angezeigt, in dem Sie den Text Ihrer SMS konfigurieren können. Klicken Sie auf **Nachricht erstellen** Bereich, um Ihre Nachricht zu erstellen.

![Journey Optimizer](./images/sms3.png)

Geben Sie folgenden Text ein: `Brrrr... {{profile.person.name.firstName}}, it's freezing. 20% discount on jackets today!`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/sms4.png)

Dann wirst du das sehen. Klicken Sie auf den Pfeil in der oberen linken Ecke, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/sms4a.png)

Du wirst dann wieder hier sein. Klicken Sie auf **OK**.

![Journey Optimizer](./images/sms4b.png)

Gehen Sie im linken Menü zurück zu **Aktionen**, wählen Sie die Aktion aus. `--demoProfileLdap--TextSlack`und ziehen Sie sie dann per Drag &amp; Drop hinter das **Nachricht** Aktion.

![Demo](./images/joa18.png)

Navigieren Sie zu **Aktionsparameter** und klicken Sie auf **Bearbeiten** Symbol für den Parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

Klicken Sie im Popup-Fenster auf **Erweiterter Modus**.

![Demo](./images/joa20.png)

Wählen Sie den unten stehenden Code aus, kopieren Sie ihn und fügen Sie ihn in den **Erweiterter Modus-Editor**. Klicken Sie auf **OK**.

`"Brrrr..." + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " It's freezing. 20% discount on Jackets today!"`

![Demo](./images/joa21.png)

Sie sehen Ihre abgeschlossene Aktion. Klicken Sie auf **OK**.

![Demo](./images/joa22.png)

Dieser Pfad der Journey ist jetzt bereit.

## 8.4.3 Nachrichten für Pfad senden: Zwischen 10° und 25° Celsius

Für jeden Temperaturkontext versuchen wir, eine Textnachricht an unseren Kunden zu senden. Wir können eine Textnachricht nur senden, wenn eine Mobiltelefonnummer für einen Kunden verfügbar ist. Daher müssen wir zunächst überprüfen, ob wir dies tun.

Fokussieren wir uns auf **Zwischen 10 und 25 C** Pfad.

![Demo](./images/p2steps.png)

Nehmen wir noch einen **Bedingung** und ziehen Sie es wie im Screenshot unten angegeben. Wir werden überprüfen, ob für diesen Kunden eine Mobiltelefonnummer zur Verfügung steht.

![Demo](./images/jop1.png)

Da dies nur ein Beispiel ist, konfigurieren wir nur die Option, bei der der Kunde über eine Mobiltelefonnummer verfügt. Fügen Sie einen Titel von **Hat Mobiltelefon?**.

Klicken Sie auf **Bearbeiten** -Symbol für den Ausdruck für **Pfad 1** Pfad.

![Demo](./images/joa2p2.png)

Navigieren Sie in den Datenquellen auf der linken Seite zu **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. Sie lesen die Mobiltelefonnummer jetzt direkt aus dem Echtzeit-Kundenprofil von Adobe Experience Platform.

![Demo](./images/joa3.png)

Feld auswählen **Zahl**, ziehen Sie es und legen Sie es auf die Arbeitsfläche &quot;Bedingung&quot;ab.

Operator auswählen **ist nicht leer**. Klicken Sie auf **OK**.

![Demo](./images/joa4.png)

Dann wirst du das sehen. Klicken Sie auf **OK**.

![Demo](./images/joa6.png)

Ihre Journey wird dann so aussehen. Klicken Sie auf **Aktionen** wie im Screenshot angegeben.

![Demo](./images/jop8.png)

Aktion auswählen **SMS** und ziehen Sie es dann nach der soeben hinzugefügten Bedingung per Drag-and-Drop.

![Demo](./images/jop9.png)

Legen Sie die **Kategorie** nach **Marketing** und wählen Sie eine SMS-Oberfläche aus, über die Sie SMS senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **SMS**.

![ACOP](./images/journeyactions1z.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2z.png)

Jetzt wird das Nachrichten-Dashboard angezeigt, in dem Sie den Text Ihrer SMS konfigurieren können. Klicken Sie auf **Nachricht erstellen** Bereich, um Ihre Nachricht zu erstellen.

![Journey Optimizer](./images/sms3a.png)

Geben Sie folgenden Text ein: `What a nice weather for the time of year, {{profile.person.name.firstName}} - 20% discount on Sweaters today!`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/sms4az.png)

Dann wirst du das sehen. Klicken Sie auf den Pfeil in der oberen linken Ecke, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/sms4azz.png)

Jetzt sehen Sie Ihre abgeschlossene Aktion. Klicken Sie auf **OK**.

![Demo](./images/jop17.png)

Gehen Sie im linken Menü zurück zu **Aktionen**, wählen Sie die Aktion aus. `--demoProfileLdap--TextSlack`und ziehen Sie sie dann per Drag &amp; Drop hinter das **Nachricht** Aktion.

![Demo](./images/jop18.png)

Navigieren Sie zu **Aktionsparameter** und klicken Sie auf **Bearbeiten** Symbol für den Parameter `TEXTTOSLACK`.

![Demo](./images/joa19z.png)

Klicken Sie im Popup-Fenster auf **Erweiterter Modus**.

![Demo](./images/joa20.png)

Wählen Sie den unten stehenden Code aus, kopieren Sie ihn und fügen Sie ihn in den **Erweiterter Modus-Editor**. Klicken Sie auf **OK**.

`"What nice weather for the time of year, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " 20% discount on Sweaters today!"`

![Demo](./images/jop21.png)

Sie sehen Ihre abgeschlossene Aktion. Klicken Sie auf **OK**.

![Demo](./images/jop22.png)

Dieser Pfad der Journey ist jetzt bereit.

## 8.4.4 Nachrichten für Pfad senden: Warmer als 25° Celsius

Für jeden Temperaturkontext versuchen wir, eine Textnachricht an unseren Kunden zu senden. Wir können eine Textnachricht nur senden, wenn eine Mobiltelefonnummer für einen Kunden verfügbar ist. Daher müssen wir zunächst überprüfen, ob wir dies tun.

Fokussieren wir uns auf **Warmer als 25 C** Pfad.

![Demo](./images/p3steps.png)

Nehmen wir noch einen **Bedingung** und ziehen Sie es wie im Screenshot unten angegeben. Sie überprüfen, ob für diesen Kunden eine Mobiltelefonnummer verfügbar ist.

![Demo](./images/jod1.png)

Da dies nur ein Beispiel ist, konfigurieren wir nur die Option, bei der der Kunde über eine Mobiltelefonnummer verfügt. Fügen Sie einen Titel von **Hat Mobiltelefon?**.

Klicken Sie auf **Bearbeiten** -Symbol für den Ausdruck für **Pfad 1** Pfad.

![Demo](./images/joa2p3.png)

Navigieren Sie in den Datenquellen auf der linken Seite zu **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. Sie lesen die Mobiltelefonnummer jetzt direkt aus dem Echtzeit-Kundenprofil von Adobe Experience Platform.

![Demo](./images/joa3.png)

Feld auswählen **Zahl**, ziehen Sie es und legen Sie es auf die Arbeitsfläche &quot;Bedingung&quot;ab.

Operator auswählen **ist nicht leer**. Klicken Sie auf **OK**.

![Demo](./images/joa4.png)

Dann wirst du das sehen. Klicken Sie auf **OK**.

![Demo](./images/joa6.png)

Ihre Journey wird dann so aussehen. Klicken Sie auf **Aktionen** wie im Screenshot angegeben.

![Demo](./images/jod8.png)

Aktion auswählen **SMS** und ziehen Sie es dann nach der soeben hinzugefügten Bedingung per Drag-and-Drop.

![Demo](./images/jod9.png)

Legen Sie die **Kategorie** nach **Marketing** und wählen Sie eine SMS-Oberfläche aus, über die Sie SMS senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **SMS**.

![ACOP](./images/journeyactions1zy.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2zy.png)

Jetzt wird das Nachrichten-Dashboard angezeigt, in dem Sie den Text Ihrer SMS konfigurieren können. Klicken Sie auf **Nachricht erstellen** Bereich, um Ihre Nachricht zu erstellen.

![Journey Optimizer](./images/sms3ab.png)

Geben Sie folgenden Text ein: `So warm, {{profile.person.name.firstName}}! 20% discount on swimwear today!`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/sms4ab.png)

Dann wirst du das sehen. Klicken Sie auf den Pfeil in der oberen linken Ecke, um zu Ihrer Journey zurückzukehren.

![Journey Optimizer](./images/sms4azzz.png)

Jetzt sehen Sie Ihre abgeschlossene Aktion. Klicken Sie auf **OK**.

![Demo](./images/jod17.png)

Gehen Sie im linken Menü zurück zu **Aktionen**, wählen Sie die Aktion aus. `--demoProfileLdap--TextSlack`und ziehen Sie sie dann per Drag &amp; Drop hinter das **Nachrichten** Aktion.

![Demo](./images/jod18.png)

Navigieren Sie zu **Aktionsparameter** und klicken Sie auf **Bearbeiten** Symbol für den Parameter `TEXTTOSLACK`.

![Demo](./images/joa19zzz.png)

Klicken Sie im Popup-Fenster auf **Erweiterter Modus**.

![Demo](./images/joa20.png)

Wählen Sie den unten stehenden Code aus, kopieren Sie ihn und fügen Sie ihn in den **Erweiterter Modus-Editor**. Klicken Sie auf **OK**.

`"So warm, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + "! 20% discount on swimwear today!"`

![Demo](./images/jod21.png)

Sie sehen Ihre abgeschlossene Aktion. Klicken Sie auf **OK**.

![Demo](./images/jod22.png)

Dieser Pfad der Journey ist jetzt bereit.

## 8.4.5 Journey veröffentlichen

Ihre Journey ist jetzt vollständig konfiguriert. Klicken Sie auf **Veröffentlichen**.

![Demo](./images/jodone.png)

Klicken **Veröffentlichen** erneut.

![Demo](./images/jopublish1.png)

Ihre Journey ist jetzt veröffentlicht.

![Demo](./images/jopublish2.png)

Nächster Schritt: [8.5 Trigger Journey](./ex5.md)

[Zurück zu Modul 8](journey-orchestration-external-weather-api-sms.md)

[Zu allen Modulen zurückkehren](../../overview.md)
