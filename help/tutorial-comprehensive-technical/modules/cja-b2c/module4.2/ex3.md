---
title: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Verbinden von GCP und BigQuery mit Adobe Experience Platform
description: Aufnehmen und Analysieren von Google Analytics-Daten in Adobe Experience Platform mit dem BigQuery Source Connector - Verbinden von GCP und BigQuery mit Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 86b04b4e-0439-4491-b700-5b0591c493b7
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '1757'
ht-degree: 1%

---

# 4.2.3 Verbinden von GCP und BigQuery mit Adobe Experience Platform

## Ziele

- Erkunden der API und Services in Google Cloud Platform
- Kennenlernen von OAuth Playground zum Testen von Google-APIs
- Erstellen Ihrer ersten BigQuery-Verbindung in Adobe Experience Platform

## Kontext

Adobe Experience Platform bietet einen Connector in **Sources**, der Ihnen dabei hilft, BigQuery-Datensätze in Adobe Experience Platform zu importieren. Dieser Daten-Connector basiert auf der Google BigQuery-API. Daher ist es wichtig, Ihre Google Cloud Platform und Ihre BigQuery-Umgebung ordnungsgemäß auf den Empfang von API-Aufrufen von Adobe Experience Platform vorzubereiten.

Zum Konfigurieren des BigQuery Source-Connectors in Adobe Experience Platform benötigen Sie die folgenden vier Werte:

- Projekt
- clientId
- clientSecret
- refreshToken

Bisher haben Sie nur die erste, die **Projekt-ID**. Dieser **Projekt-ID**-Wert ist eine zufällige ID, die von Google beim Erstellen Ihres BigQuery-Projekts während Übung 12.1 generiert wurde.

Bitte Projekt-ID in eine separate Textdatei kopieren.

| Anmeldedaten | Benennung | Beispiel |
| ----------------- |-------------| -------------|
| Projekt-ID | random | compose-task-306413 |

Sie können Ihre Projekt-ID jederzeit überprüfen, indem Sie auf **Projektname** in der oberen Menüleiste klicken:

![demo](./images/ex1/projectMenu.png)

Auf der rechten Seite sehen Sie Ihre Projekt-ID:

![demo](./images/ex1/projetcselection.png)

In dieser Übung erfahren Sie, wie Sie die anderen drei erforderlichen Felder abrufen:

- clientId
- clientSecret
- refreshToken

## 4.2.3.1 Google Cloud-API und -Services

Navigieren Sie zunächst zurück zur Startseite von Google Cloud Platform. Klicken Sie dazu einfach auf das Logo oben links im Bildschirm.

![demo](./images/ex2/5.png)

Sobald Sie sich auf der Startseite befinden, wechseln Sie zum linken Menü und klicken Sie auf **APIs und Services** und dann auf **Dashboard**.

![demo](./images/ex2/4.png)

Jetzt sehen Sie die Startseite **APIs und Services**.

![demo](./images/ex2/6.png)

Auf dieser Seite sehen Sie die Verwendung Ihrer verschiedenen Google-API-Verbindungen. Um eine API-Verbindung einzurichten, damit Adobe Experience Platform aus BigQuery lesen kann, müssen Sie die folgenden Schritte ausführen:

- Zunächst müssen Sie einen OAuth-Einverständnisbildschirm erstellen, um zukünftige Authentifizierungen zu aktivieren. Googles Sicherheitsgründe erfordern auch, dass ein Mensch die erste Authentifizierung durchführt, bevor ein programmatischer Zugriff erlaubt wird.
- Zweitens benötigen Sie API-Anmeldeinformationen (clientId und clientSecret), die für die API-Authentifizierung und den Zugriff auf Ihren BigQuery-Connector verwendet werden.

## OAuth-Einverständnisbildschirm 4.2.3.2

Beginnen wir mit der Erstellung des OAuth-Einverständnisbildschirms. Klicken Sie im linken Menü auf der Startseite **APIs und Services** auf **OAuth-Einverständnisbildschirm**.

![demo](./images/ex2/6-1a.png)

Sie sehen dann Folgendes:

![demo](./images/ex2/6-1.png)

Wählen Sie den Benutzertyp aus: **Extern**. Klicken Sie anschließend auf **ERSTELLEN**.

![demo](./images/ex2/6-2.png)

Sie befinden sich dann im Fenster **OAuth-Einverständnisbildschirm-Konfiguration**.

Geben Sie hier nur den Namen des Einverständnisbildschirms in das Feld **Anwendungsname** ein und wählen Sie die E-**-Mail**. Verwenden Sie für den Anwendungsnamen diese Namenskonvention:

| Benennung | Beispiel |
| ----------------- |-------------| 
| `--aepUserLdap-- - AEP BigQuery Connector` | vangeluw - AEP BigQuery-Connector |

![demo](./images/ex2/6-3.png)

Scrollen Sie dann nach unten, bis Sie **Kontaktinformationen für Entwickler** sehen und eine E-Mail-Adresse ausfüllen.

![demo](./images/ex2/6-3a.png)

Klicken Sie **Speichern und fortfahren**.

![demo](./images/ex2/6-4.png)

Sie werden es dann sehen. Klicken Sie **Speichern und fortfahren**.

![demo](./images/ex2/o1.png)

Sie werden es dann sehen. Klicken Sie **Speichern und fortfahren**.

![demo](./images/ex2/o2.png)

Sie werden es dann sehen. Klicken Sie **ZURÜCK ZUM DASHBOARD**.

![demo](./images/ex2/o3.png)

Sie werden es dann sehen. Klicken Sie auf **PUBLISH-**.

![demo](./images/ex2/o4.png)

Klicken Sie **BESTÄTIGEN**.

![demo](./images/ex2/o5.png)

Sie werden es dann sehen.

![demo](./images/ex2/o6.png)

Im nächsten Schritt schließen Sie die API-Einrichtung ab und erhalten Ihre API-Anmeldeinformationen.

## 4.2.3.3 Google-API-Anmeldedaten: Client-Geheimnis und Client-ID

Klicken Sie im linken Menü auf **Anmeldedaten**. Sie sehen dann Folgendes:

![demo](./images/ex2/7.png)

Klicken Sie auf die Schaltfläche **+ ANMELDEINFORMATIONEN ERSTELLEN**.

![demo](./images/ex2/9.png)

Es werden drei Optionen angezeigt. Klicken Sie auf die **OAuth-Client-ID**:

![demo](./images/ex2/11.png)

Wählen Sie im nächsten Bildschirm **Web-Anwendung** aus.

![demo](./images/ex2/12.png)

Es werden mehrere neue Felder angezeigt. Sie müssen jetzt den **Namen** der OAuth-Client-ID und auch die (**Umleitungs-URIs)**.

Befolgen Sie diese Namenskonvention:

| Feld | Wert | Beispiel |
| ----------------- |-------------| -------------| 
| Name | ldap - AEP BigQuery-Connector | vangeluw - Platform BigQuery-Connector |
| Autorisierte Weiterleitungs-URIs | https://developers.google.com/oauthplayground | https://developers.google.com/oauthplayground |

Das Feld **Autorisierte Weiterleitungs-URIs** ist ein sehr wichtiges Feld, da Sie es später benötigen werden, um das RefreshToken zu erhalten, das Sie benötigen, um die Einrichtung des BigQuery Source-Connectors in Adobe Experience Platform abzuschließen.

![demo](./images/ex2/12-1.png)

Bevor Sie fortfahren, müssen Sie nach Eingabe der URL die **Eingabetaste** drücken, um den Wert im Feld **Autorisierte Umleitungs-URIs** zu speichern. Wenn Sie nicht auf die **Enter**-Schaltfläche klicken, werden Sie zu einem späteren Zeitpunkt auf Probleme stoßen, nämlich auf dem **OAuth 2.0 Playground**.

Klicken Sie anschließend auf **Erstellen**:

![demo](./images/ex2/19.png)

Jetzt sehen Sie Ihre Client-ID und Ihr Client-Geheimnis.

![demo](./images/ex2/20.png)

Bitte diese beiden Felder kopieren und in eine Textdatei auf Ihrem Desktop einfügen. Sie können jederzeit zu einem späteren Zeitpunkt auf diese Anmeldeinformationen zugreifen, es ist jedoch einfacher, wenn Sie sie in einer Textdatei neben Ihrer BigQuery-Projekt-ID speichern.

Zusammenfassend für Ihr BigQuery Source Connector-Setup in Adobe Experience Platform stehen Ihnen jetzt die folgenden Werte bereits zur Verfügung:

| BigQuery Connector-Anmeldedaten | Wert |
| ----------------- |-------------| 
| Projekt-ID | Ihre eigene Projekt-ID (z. B.: compose-task-306413) |
| clientId | yourClientID |
| clientSecret | yourClientSecret |


Ihnen fehlt noch das **refreshToken**. Das refreshToken ist aus Sicherheitsgründen erforderlich. In der Welt der APIs laufen Token normalerweise alle 24 Stunden ab. Daher wird **refreshToken** benötigt, um das Sicherheits-Token alle 24 Stunden zu aktualisieren, damit Ihr Source Connector-Setup weiterhin eine Verbindung zu Google Cloud Platform und BigQuery herstellen kann.

## 4.2.3.4 der BigQuery-API und des refreshToken

Es gibt viele Möglichkeiten, ein refreshToken für den Zugriff auf Google Cloud Platform-APIs zu erhalten. Eine dieser Optionen ist beispielsweise die Verwendung von Postman.
Google hat jedoch etwas entwickelt, das einfacher zu testen und mit seinen APIs zu spielen ist, ein Tool namens **OAuth 2.0 Playground**.

Um auf **OAuth 2.0 Playground** zuzugreifen, gehen Sie zu [https://developers.google.com/oauthplayground](https://developers.google.com/oauthplayground).

Anschließend sehen Sie die Homepage **OAuth 2.0**.

![demo](./images/ex2/22.png)

Klicken Sie auf **Zahnrad**-Symbol oben rechts im Bildschirm:

![demo](./images/ex2/22-1.png)

Achten Sie darauf, dass Ihre Einstellungen mit denen im Bild oben übereinstimmen.

Überprüfen Sie die Einstellungen so, dass sie 100 % sicher sind.

Aktivieren Sie abschließend das Kontrollkästchen **Eigene OAuth-Anmeldeinformationen verwenden**

![demo](./images/ex2/22-2.png)

Es sollten zwei Felder angezeigt werden, für die Sie den Wert angeben können.

![demo](./images/ex2/23.png)

Bitte die Felder dieser Tabelle ausfüllen:

| Playground-API-Einstellungen | Ihre Google API-Anmeldedaten |
| ----------------- |-------------| 
| OAuth Client-ID | Ihre eigene Client-ID (in der Textdatei auf Ihrem Desktop) |
| OAuth-Client-Geheimnis | Ihr eigenes Client-Geheimnis (in der Textdatei auf Ihrem Desktop) |

![demo](./images/ex2/23-a.png)

Kopieren Sie **Client-ID** und **Client-Geheimnis** aus der Textdatei, die Sie auf Ihrem Desktop erstellt haben.

![demo](./images/ex2/20.png)

Nachdem Sie Ihre Anmeldedaten ausgefüllt haben, klicken Sie auf **Schließen**

![demo](./images/ex2/23-1.png)

Im linken Menü sehen Sie alle verfügbaren Google-APIs. Suchen Sie nach **BigQuery API v2**.

![demo](./images/ex2/27.png)

Wählen Sie als Nächstes den Umfang aus, wie in der folgenden Abbildung dargestellt:

![demo](./images/ex2/26.png)

Nachdem Sie sie ausgewählt haben, sollten Sie eine blaue Schaltfläche sehen, auf der steht **APIs autorisieren**. Klicken Sie darauf.

![demo](./images/ex2/28.png)

Wählen Sie das Google-Konto aus, das Sie zum Einrichten von GCP und BigQuery verwendet haben.

Möglicherweise wird eine große Warnung angezeigt: **Diese App ist nicht verifiziert**. Dies geschieht, weil Ihr Platform BigQuery Connector noch nicht formal überprüft wurde, sodass Google nicht weiß, ob es eine authentische App ist oder nicht. Sie sollten diese Benachrichtigung ignorieren.

Klicken Sie auf **Erweitert**.

![demo](./images/ex2/32.png)

Klicken Sie anschließend auf **Wechseln zu LDAP - AEP BigQuery Connector (unsicher)**.

![demo](./images/ex2/33.png)

Sie werden zu unserem von Ihnen erstellten OAuth-Einverständnisbildschirm weitergeleitet.

![demo](./images/ex2/29.png)

Wenn Sie die Zwei-Faktor-Authentifizierung (2FA) verwenden, geben Sie den Verifizierungs-Code ein, der Ihnen gesendet wurde.

![demo](./images/ex2/30.png)

Google zeigt jetzt acht verschiedene Eingabeaufforderungen **Berechtigung** an. Klicken Sie **Zulassen** für alle acht Berechtigungsanfragen. (Dies ist ein Verfahren, das einmal von einem echten Menschen befolgt und bestätigt werden muss, bevor die API programmgesteuerte Anfragen zulässt.)

Auch hier **acht verschiedene Popup-Fenster** werden nicht angezeigt. Sie müssen für alle auf **Zulassen** klicken.

![demo](./images/ex2/29.png)

Nach den acht Berechtigungsanfragen sehen Sie diese Übersicht. Klicken Sie **Zulassen**, um den Vorgang abzuschließen.

![demo](./images/ex2/35.png)

Nach dem letzten **Zulassen**-Klick werden Sie zum OAuth 2.0-Playground zurückgeleitet und sehen dies:

![demo](./images/ex2/36.png)

Klicken Sie auf **Autorisierungs-Code für Token austauschen**.

![demo](./images/ex2/36-1.png)

Nach einigen Sekunden wird die Ansicht **Schritt 2 - Autorisierungs-Code für Token austauschen** automatisch geschlossen und Sie sehen **Schritt 3 - Anfrage an API konfigurieren**.

Sie müssen zurück zu **Schritt 2 Austausch-Autorisierungs-Code für Token**, klicken Sie also erneut auf **Schritt 2 Austausch-Autorisierungs-Code für**-Token, um das **Token aktualisieren** zu visualisieren.

![demo](./images/ex2/37.png)

Daraufhin wird die Meldung &quot;**Token“**.

![demo](./images/ex2/38.png)

Kopieren Sie das **Aktualisierungstoken** und fügen Sie es zusammen mit den anderen BigQuery Source Connector-Anmeldeinformationen in die Textdatei auf Ihrem Desktop ein:

| BigQuery Source Connector-Anmeldedaten | Wert |
| ----------------- |-------------| 
| Projekt-ID | Ihre eigene zufällige Projekt-ID (z. B.: apt-summer-273608) |
| clientId | yourClientID |
| clientSecret | yourClientSecret |
| refreshToken | yourRefreshToken |

Als Nächstes richten wir Ihren Source-Connector in Adobe Experience Platform ein.

## 4.2.3.5 - Verbinden von Platform mit Ihrer eigenen BigQuery-Tabelle

Melden Sie sich über die folgende URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Navigieren Sie im linken Menü zu Quellen . Anschließend wird die Homepage **Quellen** angezeigt. Klicken Sie **Menü** Quellen“ auf **Datenbanken**. Klicken Sie auf die Karte **Google BigQuery**. Klicken Sie anschließend auf **Einrichten** oder **+ Konfigurieren**.

![demo](./images/1.png)

Sie sollten jetzt eine neue Verbindung erstellen.

Klicken Sie auf **Neues**. Jetzt müssen Sie alle folgenden Felder ausfüllen, basierend auf der Einrichtung, die Sie in GCP und BigQuery vorgenommen haben.

![demo](./images/3.png)

Beginnen wir mit der Benennung der Verbindung:

Bitte diese Namenskonvention verwenden:

| BigQuery Connector-Anmeldedaten | Wert | Beispiel |
| ----------------- |-------------| -------------| 
| Kontoname | `--aepUserLdap-- - BigQuery Connection` | vangeluw - BigQuery-Verbindung |
| Beschreibung | `--aepUserLdap-- - BigQuery Connection` | vangeluw - BigQuery-Verbindung |

Das sollte Ihnen etwas wie das geben:

![demo](./images/ex2/39-a.png)

Füllen Sie anschließend die GCP- und BigQuery-API **Kontoauthentifizierung**-Details aus, die Sie in einer Textdatei auf Ihrem Desktop gespeichert haben:

| BigQuery Connector-Anmeldedaten | Wert |
| ----------------- |-------------| 
| Projekt-ID | Ihre eigene zufällige Projekt-ID (z. B.: apt-summer-273608) |
| clientId | ... |
| clientSecret | ... |
| refreshToken | ... |

Ihre **Kontoauthentifizierung**-details sollten jetzt wie folgt aussehen:

![demo](./images/ex2/39-xx.png)

Nachdem Sie alle diese Felder ausgefüllt haben, klicken Sie auf **Mit Quelle verbinden**.

![demo](./images/ex2/39-2.png)

Wenn Ihre **Kontoauthentifizierung** korrekt ausgefüllt wurden, sollten Sie jetzt eine visuelle Bestätigung sehen, dass die Verbindung ordnungsgemäß funktioniert, indem Sie die Bestätigung **Verbunden** sehen.

![demo](./images/ex2/projectid.png)

Nachdem Sie Ihre Verbindung erstellt haben, klicken Sie auf **Weiter**:

![demo](./images/42.png)

Jetzt wird der BigQuery-Datensatz angezeigt, den Sie während Übung 12.2 erstellt haben.

![demo](./images/datasets.png)

Gut gemacht! In der nächsten Übung laden Sie Daten aus dieser Tabelle und ordnen sie einem Schema und Datensatz in Adobe Experience Platform zu.

Nächster Schritt: [4.2.4 Daten von BigQuery in Adobe Experience Platform laden](./ex4.md)

[Zurück zum Modul 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Zurück zu „Alle Module“](./../../../overview.md)
