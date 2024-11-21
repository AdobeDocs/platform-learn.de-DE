---
title: Adobe Experience Platform-Datenerfassung und serverseitige Weiterleitung in Echtzeit - Erstellen und konfigurieren Sie einen benutzerdefinierten Webhook
description: Benutzerdefinierten Webhook erstellen und konfigurieren
kt: 5342
doc-type: tutorial
exl-id: bb712980-5910-4f01-976b-b7fcf03f5407
source-git-commit: 7779e249b4ca03c243cf522811cd81370002d51a
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 1%

---

# 2.5.3 Benutzerdefinierten Webhook erstellen und konfigurieren

## Benutzerdefinierten Webhook erstellen

Wechseln Sie zu [https://pipedream.com/requestbin](https://pipedream.com/requestbin). Sie haben diese Anwendung bereits im [Übung 2.3.7 Destinations SDK](./../../../modules/rtcdp-b2c/module2.3/ex7.md) verwendet

Wenn Sie diesen Dienst noch nicht verwendet haben, erstellen Sie ein Konto und dann einen Arbeitsbereich. Nachdem der Arbeitsbereich erstellt wurde, wird etwas Ähnliches angezeigt.

Klicken Sie auf **copy** , um die URL zu kopieren. Sie müssen diese URL in der nächsten Übung angeben. Die URL in diesem Beispiel lautet `https://eodts05snjmjz67.m.pipedream.net`.

![demo](./images/webhook1.png)

Diese Website hat jetzt diesen Webhook für Sie erstellt und Sie können diesen Webhook in Ihrem **[!DNL Event Forwarding property]** konfigurieren, um die Ereignisweiterleitung zu testen.

## Eigenschaft für die Ereignisweiterleitung aktualisieren: Erstellen Sie ein Datenelement

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/) und gehen Sie zu **Ereignisweiterleitung**. Suchen Sie die Eigenschaft &quot;Ereignisweiterleitung&quot;und klicken Sie darauf, um sie zu öffnen.

![Adobe Experience Platform-Datenerfassung SSF](./images/prop1.png)

Gehen Sie im linken Menü zu **Datenelemente**. Klicken Sie auf **Neues Datenelement erstellen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/de1.png)

Anschließend wird ein neues Datenelement angezeigt, das konfiguriert werden soll.

![Adobe Experience Platform-Datenerfassung SSF](./images/de2.png)

Wählen Sie Folgendes aus:

- Geben Sie als **Name** **XDM-Ereignis** ein.
- Wählen Sie als **Erweiterung** **Core** aus.
- Wählen Sie als **Datenelementtyp** **Pfad** aus.
- Wählen Sie als **Pfad** **Daten aus XDM lesen (arc.event.xdm)**. Durch Auswahl dieses Pfads filtern Sie den Abschnitt **XDM** aus der Ereignis-Payload heraus, die von der Website oder App an die Adobe Edge gesendet wird.

![Adobe Experience Platform-Datenerfassung SSF](./images/de3.png)

Das wirst du jetzt haben. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassung SSF](./images/de3a.png)

>[!NOTE]
>
>Im obigen Pfad wird ein Verweis auf **arc** erstellt. **arc** steht für Adobe Resource Context und **arc** steht immer für das höchste verfügbare Objekt, das im serverseitigen Kontext verfügbar ist. Das Objekt **arc** kann mit den Adobe Experience Platform-Datenerfassungsserverfunktionen um Anreicherungen und Umwandlungen erweitert werden.
>
>Im obigen Pfad wird ein Verweis auf **event** erstellt. **event** steht für ein eindeutiges Ereignis, und der Adobe Experience Platform-Datenerfassungsserver wertet jedes Ereignis immer einzeln aus. Manchmal wird in der vom Web SDK Client Side gesendeten Payload ein Verweis auf **events** angezeigt, aber in Adobe Experience Platform Data Collection Server wird jedes Ereignis einzeln ausgewertet.

## Adobe Experience Platform-Datenerfassungsservereigenschaft aktualisieren: Erstellen Sie eine Regel

Gehen Sie im linken Menü zu **Regeln**. Klicken Sie auf **Neue Regel erstellen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl1.png)

Danach wird eine neue Regel zum Konfigurieren angezeigt. Geben Sie den **Namen**: **Alle Seiten** ein. Für diese Übung müssen Sie keine Bedingung konfigurieren. Stattdessen richten Sie eine Aktion ein. Klicken Sie auf die Schaltfläche **+ Hinzufügen** unter **Aktionen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl2.png)

Dann wirst du das sehen. Wählen Sie Folgendes aus:

- Wählen Sie die **Erweiterung**: **Adobe Cloud Connector** aus.
- Wählen Sie den **Aktionstyp**: **Fetch-Aufruf durchführen**.

Dadurch erhalten Sie den folgenden **Namen**: **Adobe Cloud-Connector - Abrufen des Abrufs**. Sie sollten jetzt Folgendes sehen:

![Adobe Experience Platform-Datenerfassung SSF](./images/rl4.png)

Konfigurieren Sie als Nächstes Folgendes:

- Ändern Sie die Anfragemethode von GET in **POST** .
- Geben Sie die URL des benutzerdefinierten Webhooks ein, den Sie in einem der vorherigen Schritte erstellt haben. Sie sieht wie folgt aus: `https://eodts05snjmjz67.m.pipedream.net`

Du solltest das jetzt haben. Navigieren Sie als Nächstes zu **Hauptteil**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl6.png)

Dann wirst du das sehen. Klicken Sie auf das Datenelementsymbol, wie unten angegeben.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl7.png)

Wählen Sie im Popup das Datenelement **XDM Event** aus, das Sie im vorherigen Schritt erstellt haben. Klicken Sie auf **Auswählen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl8.png)

Dann wirst du das sehen. Klicken Sie auf **Änderungen beibehalten**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl9.png)

Dann wirst du das sehen. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl10.png)

Sie haben Ihre erste Regel jetzt in einer Eigenschaft für die Ereignisweiterleitung konfiguriert. Wechseln Sie zu **Veröffentlichungsfluss** , um Ihre Änderungen zu veröffentlichen.
Öffnen Sie Ihre Entwicklungsbibliothek **Main**, indem Sie wie angegeben auf **Bearbeiten** klicken.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl11.png)

Klicken Sie auf die Schaltfläche **Alle geänderten Ressourcen hinzufügen** , nach der Ihre Regel und Ihr Datenelement in dieser Bibliothek angezeigt werden. Klicken Sie anschließend auf **Speichern und für Entwicklung erstellen**. Ihre Änderungen werden jetzt bereitgestellt.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl13.png)

Nach einigen Minuten werden Sie feststellen, dass die Implementierung abgeschlossen ist und getestet werden kann.

![Adobe Experience Platform-Datenerfassung SSF](./images/rl14.png)

## Testen der Konfiguration

Wechseln Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf die drei Punkte **..** im Website-Projekt und dann auf **Ausführen** , um es zu öffnen.

![DSN](./../../datacollection/module1.1/images/web8.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../gettingstarted/gettingstarted/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../gettingstarted/gettingstarted/images/web7.png)

Wenn Sie die Entwickleransicht des Browsers öffnen, können Sie Netzwerkanforderungen wie unten angegeben überprüfen. Wenn Sie den Filter **interact** verwenden, sehen Sie die Netzwerkanforderungen, die vom Adobe Experience Platform-Datenerfassungs-Client an die Adobe Edge gesendet werden.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook1.png)

Wenn Sie die Rohdaten-Payload auswählen, gehen Sie zu &quot;[https://jsonformatter.org/json-pretty-print](https://jsonformatter.org/json-pretty-print)&quot;und fügen Sie die Payload ein. Klicken Sie auf **Minify / Beautify**. Anschließend werden die JSON-Payload, das Objekt **events** und das Objekt **xdm** angezeigt. In einem der vorherigen Schritte haben Sie bei der Definition des Datenelements die Referenz **arc.event.xdm** verwendet, was dazu führt, dass Sie das Objekt **xdm** dieser Payload analysieren.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook2.png)

Wechseln Sie Ihre Ansicht zu Ihrem benutzerdefinierten Webhook [https://pipedream.com/requestbin](https://pipedream.com/requestbin) , den Sie in einem der vorherigen Schritte verwendet haben. Sie sollten jetzt eine ähnliche Ansicht wie diese haben, wobei Netzwerkanforderungen im linken Menü angezeigt werden. Sie sehen die **xdm**-Payload, die aus der oben gezeigten Netzwerkanforderung herausgefiltert wurde.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook3.png)

Scrollen Sie in der Payload ein wenig nach unten, um den Seitennamen zu finden, der in diesem Fall **home** ist.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook4.png)

Wenn Sie jetzt über die Website navigieren, werden in Echtzeit zusätzliche Netzwerkanforderungen auf diesem benutzerdefinierten Webhook verfügbar sein.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook5.png)

Sie haben jetzt die serverseitige Ereignisweiterleitung von Web SDK-/XDM-Payloads an einen externen benutzerdefinierten Webhook konfiguriert. In den nächsten Übungen konfigurieren Sie einen ähnlichen Ansatz und senden dieselben Daten an Google Cloud Platform und AWS.

Nächster Schritt: [2.5.4 Ereignisse an GCP Pub/Sub](./ex4.md) weiterleiten

[Zurück zu Modul 2.5](./aep-data-collection-ssf.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
