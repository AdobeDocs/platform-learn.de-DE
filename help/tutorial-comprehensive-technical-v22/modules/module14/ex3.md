---
title: Adobe Experience Platform-Datenerfassung und serverseitige Weiterleitung in Echtzeit - Erstellen und konfigurieren Sie einen benutzerdefinierten Webhook
description: Benutzerdefinierten Webhook erstellen und konfigurieren
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: db15c445-b45a-44cb-bc24-598676f02a5d
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 2%

---

# 14.3 Benutzerdefinierten Webhook erstellen und konfigurieren

## 14.3.1 Benutzerdefinierten Webhook erstellen

Navigieren Sie zu [https://webhook.site/](https://webhook.site/). Sie sehen etwas wie das:

![Demo](./images/webhook1.png)

Sie sehen Ihre eindeutige URL, die wie folgt aussieht: `https://webhook.site/585126a1-41fc-4721-864b-d4aa8c268a1d`.

Diese Website hat jetzt diesen Webhook für Sie erstellt und Sie können diesen Webhook in Ihrem **[!DNL Event Forwarding property]** , um die Weiterleitung von Ereignissen zu testen.

## 14.3.2 Eigenschaft &quot;Ereignisweiterleitung&quot;aktualisieren: Erstellen eines Datenelements

Navigieren Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/) und gehen Sie zu **Ereignisweiterleitung**. Suchen Sie die Eigenschaft &quot;Ereignisweiterleitung&quot;und klicken Sie darauf, um sie zu öffnen.

![Adobe Experience Platform Data Collection SSF](./images/prop1.png)

Gehen Sie im linken Menü zu **Datenelemente**. Klicken Sie auf **Neues Datenelement erstellen**.

![Adobe Experience Platform Data Collection SSF](./images/de1.png)

Anschließend wird ein neues Datenelement angezeigt, das konfiguriert werden soll.

![Adobe Experience Platform Data Collection SSF](./images/de2.png)

Wählen Sie Folgendes aus:

- Als **Name**, eingeben **XDM-Ereignis**.
- Als **Erweiterung** auswählen **Core**.
- Als **Datenelementtyp** auswählen **Pfad**.
- Als **Pfad**, eingeben **arc.event.xdm**. Durch Eingabe dieses Pfads filtern Sie die **XDM** aus der Ereignis-Payload, die von der Website oder App an die Adobe Edge gesendet wird.

Das wirst du jetzt haben. Klicken Sie auf **Speichern**.

![Adobe Experience Platform Data Collection SSF](./images/de3.png)

>[!NOTE]
>
>Im obigen Pfad wird ein Verweis auf **Bogen**. **Bogen** steht für Adobe Resource Context und **Bogen** steht immer für das höchste verfügbare Objekt, das im serverseitigen Kontext verfügbar ist. Anreicherungen und Umwandlungen können hinzugefügt werden. **Bogen** -Objekt, das die Datenerfassungsserverfunktionen von Adobe Experience Platform verwendet.
>
>Im obigen Pfad wird ein Verweis auf **event**. **event** steht für ein eindeutiges Ereignis und Adobe Experience Platform Data Collection Server wertet jedes Ereignis immer einzeln aus. Manchmal wird Ihnen ein Verweis auf **events** in der vom Web SDK Client Side gesendeten Payload, aber in Adobe Experience Platform Data Collection Server wird jedes Ereignis einzeln ausgewertet.

## 14.3.3 Eigenschaft des Adobe Experience Platform-Datenerfassungsservers aktualisieren: Erstellen einer Regel

Gehen Sie im linken Menü zu **Regeln**. Klicken Sie auf **Neue Regel erstellen**.

![Adobe Experience Platform Data Collection SSF](./images/rl1.png)

Danach wird eine neue Regel zum Konfigurieren angezeigt. Geben Sie die **Name**: **Alle Seiten**. Für diese Übung müssen Sie keine Bedingung konfigurieren. Stattdessen richten Sie eine Aktion ein. Klicken Sie auf **+ Hinzufügen** Schaltfläche unter **Aktionen**.

![Adobe Experience Platform Data Collection SSF](./images/rl2.png)

Dann wirst du das sehen. Wählen Sie Folgendes aus:

- Wählen Sie die **Erweiterung**: **Adobe Cloud Connector**.
- Wählen Sie die **Aktionstyp**: **Abrufen eines Aufrufs**.

Das sollte dir das geben **Name**: **Adobe Cloud Connector - Abrufen eines Aufrufs**. Sie sollten jetzt Folgendes sehen:

![Adobe Experience Platform Data Collection SSF](./images/rl4.png)

Konfigurieren Sie als Nächstes Folgendes:

- Ändern Sie die Anforderungsmethode von GET in **POST**
- Geben Sie die URL des benutzerdefinierten Webhooks ein, den Sie in einem der vorherigen Schritte auf der Seite [https://webhook.site/](https://webhook.site/) Website, die wie folgt aussieht: `https://webhook.site/585126a1-41fc-4721-864b-d4aa8c268a1d`

Du solltest das jetzt haben. Navigieren Sie als Nächstes zu **body**.

![Adobe Experience Platform Data Collection SSF](./images/rl6.png)

Dann wirst du das sehen. Klicken Sie auf das Datenelementsymbol, wie unten angegeben.

![Adobe Experience Platform Data Collection SSF](./images/rl7.png)

Wählen Sie im Popup das Datenelement aus **XDM-Ereignis** die Sie im vorherigen Schritt erstellt haben. Klicken Sie auf **Auswählen**.

![Adobe Experience Platform Data Collection SSF](./images/rl8.png)

Dann wirst du das sehen. Klicken Sie auf **Änderungen beibehalten**.

![Adobe Experience Platform Data Collection SSF](./images/rl9.png)

Dann wirst du das sehen. Klicken Sie auf **Speichern**.

![Adobe Experience Platform Data Collection SSF](./images/rl10.png)

Sie haben Ihre erste Regel jetzt in einer Eigenschaft für die Ereignisweiterleitung konfiguriert. Navigieren Sie zu **Veröffentlichungsfluss** , um Ihre Änderungen zu veröffentlichen.
Entwicklungsbibliothek öffnen **Main** durch Klicken auf **Bearbeiten** wie angegeben.

![Adobe Experience Platform Data Collection SSF](./images/rl11.png)

Klicken Sie auf **Alle geänderten Ressourcen hinzufügen** -Schaltfläche, nach der Ihre Regel und Ihr Datenelement in dieser Bibliothek angezeigt werden. Klicken Sie anschließend auf **Speichern und erstellen für Entwicklung**. Ihre Änderungen werden jetzt bereitgestellt.

![Adobe Experience Platform Data Collection SSF](./images/rl13.png)

Nach einigen Minuten werden Sie feststellen, dass die Implementierung abgeschlossen ist und getestet werden kann.

![Adobe Experience Platform Data Collection SSF](./images/rl14.png)

## 14.3.4 Testen der Konfiguration

Navigieren Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](../module0/images/web8.png)

Sie können nun den unten stehenden Fluss ausführen, um auf die Website zuzugreifen. Klicken **Integrationen**.

![DSN](../module0/images/web1.png)

Im **Integrationen** müssen Sie die Datenerfassungseigenschaft auswählen, die in Übung 0.1 erstellt wurde.

![DSN](../module0/images/web2.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../module0/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](../module0/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../module0/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../module0/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../module0/images/web7.png)

Wenn Sie die Entwickleransicht des Browsers öffnen, können Sie Netzwerkanforderungen wie unten angegeben überprüfen. Wenn Sie den Filter verwenden **interact** angezeigt, sehen Sie die Netzwerkanforderungen, die vom Adobe Experience Platform-Datenerfassungsclient an die Adobe Edge gesendet werden.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook1.png)

Wenn Sie die Rohdaten-Payload auswählen, navigieren Sie zu [https://jsonformatter.org/json-pretty-print](https://jsonformatter.org/json-pretty-print) und fügen Sie die Payload ein. Klicken **Make Pretty**. Sie sehen dann die JSON-Payload, die **events** -Objekt und **xdm** -Objekt. In einem der vorherigen Schritte haben Sie bei der Definition des Datenelements die Referenz verwendet **arc.event.xdm**, was dazu führt, dass Sie die **xdm** -Objekt dieser Payload.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook2.png)

Zur Website wechseln [https://webhook.site/](https://webhook.site/) die Sie in einem der vorherigen Schritte verwendet haben. Sie sollten jetzt eine ähnliche Ansicht wie diese haben, wobei Netzwerkanforderungen im linken Menü angezeigt werden. Sie sehen die **xdm** Nutzlast, die aus der oben gezeigten Netzwerkanforderung herausgefiltert wurde.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook3.png)

Scrollen Sie in der Payload ein wenig nach unten, um den Seitennamen zu finden, was in diesem Fall der Fall ist **vangeluw-OCUC** (der Projektname Ihrer Demowebsite).

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook4.png)

Wenn Sie jetzt über die Website navigieren, werden in Echtzeit zusätzliche Netzwerkanforderungen auf diesem benutzerdefinierten Webhook verfügbar sein.

![Einrichten der Adobe Experience Platform-Datenerfassung](./images/hook5.png)

Sie haben jetzt die serverseitige Weiterleitung von Web SDK-/XDM-Payloads an einen externen benutzerdefinierten Webhook konfiguriert. In den nächsten Übungen konfigurieren Sie einen ähnlichen Ansatz und senden dieselben Daten an Google- und AWS-Umgebungen.

Nächster Schritt: [14.4 Erstellen und Konfigurieren einer Google Cloud-Funktion](./ex4.md)

[Zurück zu Modul 14](./aep-data-collection-ssf.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
