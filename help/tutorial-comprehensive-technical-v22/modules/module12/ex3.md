---
title: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Verbinden von GCP und BigQuery mit Adobe Experience Platform
description: Erfassen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Verbinden von GCP und BigQuery mit Adobe Experience Platform
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: b2b29cb7-dd5c-48f2-b881-3e10d9f1a0df
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1758'
ht-degree: 2%

---

# 12.3 GCP und BigQuery mit Adobe Experience Platform verbinden

## Ziele

- API und Dienste in Google Cloud Platform
- Machen Sie sich mit OAuth Playground vertraut, um Google-APIs zu testen.
- Erstellen der ersten BigQuery-Verbindung in Adobe Experience Platform

## Kontext

Adobe Experience Platform bietet einen Connector in **Quellen** wird Ihnen dabei helfen, BigQuery-Datensätze in Adobe Experience Platform zu importieren. Dieser Data Connector basiert auf der Google BigQuery-API. Daher ist es wichtig, Ihre Google Cloud-Plattform und Ihre BigQuery-Umgebung ordnungsgemäß darauf vorzubereiten, API-Aufrufe von Adobe Experience Platform zu empfangen.

Zum Konfigurieren des BigQuery Source Connectors in Adobe Experience Platform benötigen Sie die folgenden vier Werte:

- Projekt
- clientId
- clientSecret
- refreshToken

Bisher gibt es nur den ersten **Projekt-ID**. Diese **Projekt-ID** ist eine zufällige ID, die von Google bei der Erstellung Ihres BigQuery-Projekts in Übung 12.1 generiert wurde.

Kopieren Sie die Projekt-ID in eine separate Textdatei.

| Anmeldedaten | Namenskonvention | Beispiel |
| ----------------- |-------------| -------------|
| Projekt-ID | random | created-task-306413 |

Sie können Ihre Projekt-ID jederzeit überprüfen, indem Sie auf Ihre **Projektname** in der oberen Menüleiste:

![Demo](./images/ex1/projectMenu.png)

Auf der rechten Seite sehen Sie die Projekt-ID:

![Demo](./images/ex1/projetcselection.png)

In dieser Übung erfahren Sie, wie Sie die anderen 3 erforderlichen Felder abrufen:

- clientId
- clientSecret
- refreshToken

## 12.3.1 Google Cloud-API und -Dienste

Gehen Sie zunächst zur Startseite der Google Cloud Platform zurück. Klicken Sie dazu einfach auf das Logo oben links im Bildschirm.

![Demo](./images/ex2/5.png)

Sobald Sie sich auf der Startseite befinden, wechseln Sie zum linken Menü und klicken Sie auf **APIs und Dienste**, klicken Sie auf **Dashboard**.

![Demo](./images/ex2/4.png)

Sie werden jetzt die **APIs und Dienste** homepage.

![Demo](./images/ex2/6.png)

Auf dieser Seite können Sie die Nutzung Ihrer verschiedenen Google API-Verbindungen sehen. Führen Sie die folgenden Schritte aus, um eine API-Verbindung einzurichten, damit Adobe Experience Platform aus BigQuery lesen kann:

- Zunächst müssen Sie einen OAuth-Einverständnisbildschirm erstellen, um zukünftige Authentifizierungen zu ermöglichen. Aus Sicherheitsgründen von Google ist es auch erforderlich, dass ein Mensch die erste Authentifizierung durchführt, bevor ein programmatischer Zugriff erlaubt ist.
- Außerdem benötigen Sie API-Anmeldeinformationen (clientId und clientSecret), die für die API-Authentifizierung und den Zugriff auf Ihren BigQuery Connector verwendet werden.

## 12.3.2 OAuth-Einverständnisbildschirm

Beginnen wir mit der Erstellung des OAuth-Einverständnisbildschirms. Im linken Menü auf der **APIs und Dienste** homepage, click **OAuth-Einverständnisbildschirm**.

![Demo](./images/ex2/6-1a.png)

Daraufhin sehen Sie Folgendes:

![Demo](./images/ex2/6-1.png)

Wählen Sie den Benutzertyp aus: **Externe**. Klicken Sie anschließend auf **ERSTELLEN**.

![Demo](./images/ex2/6-2.png)

Sie werden dann auf der **OAuth Consent Screen-Konfiguration** Fenster.

Hier müssen Sie lediglich den Namen des Zustimmungsbildschirms im **Anwendungsname** und wählen Sie die **Benutzerunterstützungs-E-Mail**. Verwenden Sie für den Anwendungsnamen die folgende Benennungsregel:

| Namenskonvention | Beispiel |
| ----------------- |-------------| 
| `--demoProfileLdap-- - AEP BigQuery Connector` | vangeluw - AEP BigQuery Connector |

![Demo](./images/ex2/6-3.png)

Scrollen Sie als Nächstes nach unten, bis Sie **Kontaktdaten für Entwickler** und geben Sie eine E-Mail-Adresse ein.

![Demo](./images/ex2/6-3a.png)

Klicken **SPEICHERN UND FORTFAHREN**.

![Demo](./images/ex2/6-4.png)

Dann wirst du das sehen. Klicken **SPEICHERN UND FORTFAHREN**.

![Demo](./images/ex2/o1.png)

Dann wirst du das sehen. Klicken **SPEICHERN UND FORTFAHREN**.

![Demo](./images/ex2/o2.png)

Dann wirst du das sehen. Klicken **ZURÜCK ZUM DASHBOARD**.

![Demo](./images/ex2/o3.png)

Dann wirst du das sehen. Klicken **VERÖFFENTLICHEN DER APP**.

![Demo](./images/ex2/o4.png)

Klicken **BESTÄTIGEN**.

![Demo](./images/ex2/o5.png)

Dann wirst du das sehen.

![Demo](./images/ex2/o6.png)

Im nächsten Schritt werden Sie die API-Einrichtung abschließen und Ihre API-Anmeldeinformationen abrufen.

## 12.3.3 Google API-Anmeldeinformationen: Client-Geheimnis und Client-ID

Klicken Sie im linken Menü auf **Anmeldeinformationen**. Daraufhin sehen Sie Folgendes:

![Demo](./images/ex2/7.png)

Klicken Sie auf **+ ANMELDEDATEN ERSTELLEN** Schaltfläche.

![Demo](./images/ex2/9.png)

Sie werden drei Optionen sehen. Klicken Sie auf **OAuth-Client-ID**:

![Demo](./images/ex2/11.png)

Wählen Sie im nächsten Bildschirm **Webanwendung**.

![Demo](./images/ex2/12.png)

Es werden mehrere neue Felder angezeigt. Sie müssen nun die **Name** der OAuth-Client-ID und geben Sie außerdem die **Autorisierte Umleitungs-URIs**.

Befolgen Sie diese Benennungskonvention:

| Feld | Wert | Beispiel |
| ----------------- |-------------| -------------| 
| Name | ldap - AEP BigQuery Connector | vangeluw - Platform BigQuery Connector |
| Autorisierte Umleitungs-URIs | https://developers.google.com/oauthplayground | https://developers.google.com/oauthplayground |

Die **Autorisierte Umleitungs-URIs** -Feld ist ein sehr wichtiges Feld, da Sie es später benötigen werden, um das RefreshToken zu erhalten, das Sie benötigen, um die Einrichtung des BigQuery Source Connectors in Adobe Experience Platform abzuschließen.

![Demo](./images/ex2/12-1.png)

Bevor Sie fortfahren, müssen Sie die **Eingabe** Schaltfläche nach Eingabe der URL zum Speichern des Werts im **Autorisierte Umleitungs-URIs** -Feld. Wenn Sie nicht auf die **Eingabe** -Schaltfläche, werden Sie zu einem späteren Zeitpunkt in der **OAuth 2.0 Playground**.

Klicken Sie anschließend auf **Erstellen**:

![Demo](./images/ex2/19.png)

Jetzt sehen Sie Ihre Client-ID und Ihr Client-Geheimnis.

![Demo](./images/ex2/20.png)

Kopieren Sie diese beiden Felder und fügen Sie sie in eine Textdatei auf Ihrem Desktop ein. Sie können auf diese Anmeldedaten immer zu einem späteren Zeitpunkt zugreifen. Es ist jedoch einfacher, sie in einer Textdatei neben Ihrer BigQuery Project-ID zu speichern.

Die folgenden Werte sind jetzt bereits verfügbar, da dies für Ihre BigQuery Source Connector-Einrichtung in Adobe Experience Platform erforderlich ist:

| BigQuery Connector-Anmeldedaten | Wert |
| ----------------- |-------------| 
| Projekt-ID | Ihre eigene Projekt-ID (z. B.: created-task-306413) |
| clientid | yourclientid |
| clientsecret | yourclientsecret |


Sie vermissen immer noch die **refreshToken**. Das refreshToken ist aus Sicherheitsgründen eine Anforderung. In der Welt der APIs laufen Token normalerweise alle 24 Stunden ab. Also **refreshToken** ist erforderlich, um das Sicherheits-Token alle 24 Stunden zu aktualisieren, damit Ihr Source Connector-Setup weiterhin eine Verbindung zu Google Cloud Platform und BigQuery herstellen kann.

## 12.3.4 BigQuery-API und der refreshToken

Es gibt viele Möglichkeiten, ein refreshToken für den Zugriff auf Google Cloud Platform-APIs abzurufen. Eine dieser Optionen ist beispielsweise die Verwendung von Postman.
Google hat jedoch etwas einfacher entwickelt, um ihre APIs zu testen und mit ihnen zu spielen, ein Tool namens **OAuth 2.0 Playground**.

So greifen Sie auf **OAuth 2.0 Playground**, gehen Sie zu [https://developers.google.com/oauthplayground](https://developers.google.com/oauthplayground).

Sie werden dann die **OAuth 2.0 Playground** homepage.

![Demo](./images/ex2/22.png)

Klicken Sie auf **Zahnrad** rechts oben auf dem Bildschirm:

![Demo](./images/ex2/22-1.png)

Stellen Sie sicher, dass Ihre Einstellungen mit denen im Bild oben übereinstimmen.

Überprüfen Sie, ob die Einstellungen zu 100 % sicher sind.

Wenn Sie fertig sind, aktivieren Sie das Kontrollkästchen von **Verwenden Ihrer eigenen OAuth-Anmeldeinformationen**

![Demo](./images/ex2/22-2.png)

Es sollten zwei Felder angezeigt werden, für die Sie den Wert haben.

![Demo](./images/ex2/23.png)

Bitte füllen Sie die Felder in dieser Tabelle aus:

| Einstellungen der Player-API | Ihre Google API-Anmeldeinformationen |
| ----------------- |-------------| 
| OAuth-Client-ID | Ihre eigene Client-ID (in der Textdatei auf Ihrem Desktop) |
| OAuth Client Secret | Ihr eigenes Client-Geheimnis (in der Textdatei auf Ihrem Desktop) |

![Demo](./images/ex2/23-a.png)

Kopieren Sie die **Client-ID** und **Client Secret** aus der Textdatei, die Sie auf Ihrem Desktop erstellt haben.

![Demo](./images/ex2/20.png)

Nachdem Sie Ihre Anmeldedaten ausgefüllt haben, klicken Sie auf **Schließen**

![Demo](./images/ex2/23-1.png)

Im linken Menü sehen Sie alle verfügbaren Google-APIs. Suchen Sie nach **BigQuery API v2**.

![Demo](./images/ex2/27.png)

Wählen Sie dann den Umfang wie in der folgenden Abbildung angegeben aus:

![Demo](./images/ex2/26.png)

Nachdem Sie sie ausgewählt haben, sollte eine blaue Schaltfläche angezeigt werden, auf der **APIs autorisieren**. Klicken Sie darauf.

![Demo](./images/ex2/28.png)

Wählen Sie das Google-Konto aus, das Sie zum Einrichten von GCP und BigQuery verwendet haben.

Möglicherweise wird eine große Warnung angezeigt: **Diese App ist nicht verifiziert**. Dies geschieht, weil Ihr Platform BigQuery-Connector noch nicht offiziell überprüft wurde. Google weiß also nicht, ob es sich um eine authentische App handelt oder nicht. Sie sollten diese Benachrichtigung ignorieren.

Klicken **Erweitert**.

![Demo](./images/ex2/32.png)

Klicken Sie anschließend auf **Gehen Sie zu ldap - AEP BigQuery Connector (unsicher)**.

![Demo](./images/ex2/33.png)

Sie werden zu unserem OAuth-Einverständnisbildschirm weitergeleitet, den Sie erstellt haben.

![Demo](./images/ex2/29.png)

Wenn Sie Zweifaktorauthentifizierung (2FA) verwenden, geben Sie den an Sie gesendeten Verifizierungscode ein.

![Demo](./images/ex2/30.png)

Google zeigt Ihnen jetzt acht verschiedene **Berechtigung** aufgefordert. Klicken **Zulassen** für alle acht Berechtigungsanfragen. (Dies ist ein Verfahren, das einmal von einem echten Menschen befolgt und bestätigt werden muss, bevor die API programmatische Anfragen zulässt.)

Auch hier: **acht verschiedene Popup-Fenster** nicht angezeigt wird, müssen Sie auf **Zulassen** für alle.

![Demo](./images/ex2/29.png)

Nach den acht Berechtigungsanfragen wird diese Übersicht angezeigt. Klicken **Zulassen** , um den Prozess abzuschließen.

![Demo](./images/ex2/35.png)

Nach dem letzten **Zulassen**-Klick, Sie werden zum OAuth 2.0-Playground zurückgesendet und sehen Folgendes:

![Demo](./images/ex2/36.png)

Klicken **Exchange-Autorisierungscode für Token**.

![Demo](./images/ex2/36-1.png)

Nach einigen Sekunden wird die **Schritt 2: Exchange authorization code for tokens** wird die Ansicht automatisch geschlossen und Sie sehen **Schritt 3: Anfrage an API konfigurieren**.

Du musst zurück zu **Schritt 2: Exchange authorization code for tokens** klicken Sie auf **Schritt 2: Exchange authorization code for tokens** erneut, um die **Aktualisierungstoken**.

![Demo](./images/ex2/37.png)

Sie werden jetzt die **Aktualisierungstoken**.

![Demo](./images/ex2/38.png)

Kopieren Sie die **Aktualisierungstoken** und fügen Sie sie zusammen mit den anderen BigQuery Source Connector-Anmeldeinformationen in die Textdatei auf Ihrem Desktop ein:

| BigQuery Source Connector-Anmeldeinformationen | Wert |
| ----------------- |-------------| 
| Projekt-ID | Ihre eigene zufällige Projekt-ID (z. B.: apt-summer-273608) |
| clientid | yourclientid |
| clientsecret | yourclientsecret |
| refreshToken | yourrefreshToken |

Als Nächstes richten wir Ihren Quell-Connector in Adobe Experience Platform ein.

## Übung 12.3.5 - Plattform mit Ihrer eigenen BigQuery-Tabelle verbinden

Melden Sie sich über diese URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](../module2/images/sb1.png)

Gehen Sie im linken Menü zu Quellen . Sie werden dann die **Quellen** homepage. Im **Quellen** Menü, klicken Sie auf **Datenbanken**. Klicken Sie auf **Google BigQuery** Karte. Klicken Sie anschließend auf **Einrichten** oder **+ Konfigurieren**.

![Demo](./images/1.png)

Sie sollten jetzt eine neue Verbindung erstellen.

Klicken Sie auf **Neues Konto**. Jetzt müssen Sie alle folgenden Felder ausfüllen, basierend auf der Einrichtung, die Sie in GCP und BigQuery durchgeführt haben.

![Demo](./images/3.png)

Beginnen wir mit der Benennung der Verbindung:

Bitte verwenden Sie diese Namenskonvention:

| BigQuery Connector-Anmeldedaten | Wert | Beispiel |
| ----------------- |-------------| -------------| 
| Kontoname | `--demoProfileLdap-- - BigQuery Connection` | vangeluw - BigQuery-Verbindung |
| Beschreibung | `--demoProfileLdap-- - BigQuery Connection` | vangeluw - BigQuery-Verbindung |

Was sollte Ihnen so etwas geben:

![Demo](./images/ex2/39-a.png)

Füllen Sie als Nächstes die GCP- und BigQuery-API aus **Kontoauthentifizierung**-details, die Sie in einer Textdatei auf Ihrem Desktop gespeichert haben:

| BigQuery Connector-Anmeldedaten | Wert |
| ----------------- |-------------| 
| Projekt-ID | Ihre eigene zufällige Projekt-ID (z. B.: apt-summer-273608) |
| clientId | ... |
| clientSecret | ... |
| refreshToken | ... |

Ihre **Kontoauthentifizierung**-details sollten jetzt wie folgt aussehen:

![Demo](./images/ex2/39-xx.png)

Nachdem Sie alle diese Felder ausgefüllt haben, klicken Sie auf **Verbindung mit Quelle herstellen**.

![Demo](./images/ex2/39-2.png)

Wenn **Kontoauthentifizierung** Informationen korrekt ausgefüllt wurden, sollten Sie nun eine visuelle Bestätigung darüber erhalten, dass die Verbindung ordnungsgemäß funktioniert. **Verbunden** Bestätigung.

![Demo](./images/ex2/projectid.png)

Nachdem die Verbindung erstellt wurde, klicken Sie auf **Nächste**:

![Demo](./images/42.png)

Jetzt wird der BigQuery-Datensatz angezeigt, den Sie in Übung 12.2 erstellt haben.

![Demo](./images/datasets.png)

Gut gemacht! In der nächsten Übung laden Sie Daten aus dieser Tabelle und ordnen sie einem Schema und Datensatz in Adobe Experience Platform zu.

Nächster Schritt: [12.4 Daten aus BigQuery in Adobe Experience Platform laden](./ex4.md)

[Zurück zu Modul 12](./customer-journey-analytics-bigquery-gcp.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
