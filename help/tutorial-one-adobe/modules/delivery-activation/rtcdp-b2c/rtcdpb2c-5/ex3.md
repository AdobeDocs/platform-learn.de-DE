---
title: Adobe Experience Platform-Datenerfassung und Server-seitige Echtzeit-Weiterleitung - Erstellen und Konfigurieren eines benutzerdefinierten Webhooks
description: Erstellen und Konfigurieren eines benutzerdefinierten Webhooks
kt: 5342
doc-type: tutorial
exl-id: 80f8ca6d-5540-4c39-89c2-361941fe168b
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 1%

---

# 2.5.3 Erstellen und Konfigurieren eines benutzerdefinierten Webhooks

## Erstellen eines benutzerdefinierten Webhooks

Navigieren Sie zu [https://pipedream.com/requestbin](https://pipedream.com/requestbin). Sie haben diese Anwendung bereits in [SDK für Ziele von Übung 2.3.6 verwendet](./../../../../modules/delivery-activation/rtcdp-b2c/rtcdpb2c-3/ex6.md)

Wenn Sie diesen Dienst noch nicht verwendet haben, erstellen Sie ein Konto und dann einen Arbeitsbereich. Nachdem der Arbeitsbereich erstellt wurde, sehen Sie etwas Ähnliches.

Klicken Sie **Kopieren**, um die URL zu kopieren. Sie müssen diese URL in der nächsten Übung angeben. Die URL in diesem Beispiel lautet `https://eodts05snjmjz67.m.pipedream.net`.

![demo](./images/webhook1.png)

Diese Website hat jetzt diesen Webhook für Sie erstellt, und Sie können diesen Webhook in Ihrem **[!DNL Event Forwarding property]** konfigurieren, um mit dem Testen der Weiterleitung von Ereignissen zu beginnen.

## Aktualisieren der Ereignisweiterleitungseigenschaft: Datenelement erstellen

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/) und dann zu **Ereignisweiterleitung**. Suchen Sie Ihre Ereignisweiterleitungs-Eigenschaft und klicken Sie darauf, um sie zu öffnen.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/prop1.png)

Wechseln Sie im linken Menü zu **Datenelemente**. Klicken Sie auf **Neues Datenelement erstellen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/de1.png)

Anschließend wird ein neues zu konfigurierendes Datenelement angezeigt.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/de2.png)

Nehmen Sie die folgende Auswahl vor:

- Geben Sie als **Name** &quot;**-Ereignis“**.
- Wählen Sie als **Erweiterung** die Option **Core**.
- Wählen Sie als **Datenelementtyp** die Option **Pfad**.
- Wählen Sie als **Pfad** die Option **Daten aus XDM lesen (arc.event.xdm)**. Wenn Sie diesen Pfad auswählen, filtern Sie den Abschnitt **XDM** aus der Ereignis-Payload, die von der Website oder der Mobile App an Adobe Edge gesendet wird.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/de3.png)

Jetzt hast du das hier. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/de3a.png)

>[!NOTE]
>
>Im obigen Pfad wird auf „arc **verwiesen**. **arc** steht für Adobe Resource Context und **arc** steht immer für das höchste verfügbare Objekt, das im Server-seitigen Kontext verfügbar ist. Zu diesem **arc**-Objekt können mithilfe der Datenerfassungs-Server-Funktionen von Adobe Experience Platform Anreicherungen und Umwandlungen hinzugefügt werden.
>
>Im obigen Pfad wird auf &quot;**&quot;**. **event** steht für ein eindeutiges Ereignis, und der Adobe Experience Platform-Datenerfassungsserver bewertet jedes Ereignis immer einzeln. Manchmal wird ein Verweis auf **Ereignisse** in der Payload angezeigt, die von Web SDK Client Side gesendet wird, aber auf dem Adobe Experience Platform-Datenerfassungsserver wird jedes Ereignis einzeln ausgewertet.

## Aktualisieren der Adobe Experience Platform-Datenerfassungs-Server-Eigenschaft: Regel erstellen

Navigieren Sie im linken Menü zu **Regeln**. Klicken Sie auf **Neue Regel erstellen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl1.png)

Anschließend wird eine neue zu konfigurierende Regel angezeigt. Geben Sie **Name** ein: **Alle Seiten**. Für diese Übung müssen Sie keine Bedingung konfigurieren. Stattdessen richten Sie eine Aktion ein. Klicken Sie auf die Schaltfläche **+ Hinzufügen** unter **Aktionen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl2.png)

Sie werden es dann sehen. Nehmen Sie die folgende Auswahl vor:

- Wählen Sie **Erweiterung** aus: **Adobe Cloud Connector**.
- Wählen Sie den **Aktionstyp** aus: **Abrufaufruf durchführen**.

Daraus sollte folgender **bestehenName**: **Adobe Cloud Connector - Abruf durchführen**. Sie sollten dies jetzt sehen:

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl4.png)

Konfigurieren Sie anschließend Folgendes:

- Ändern Sie die Anfragemethode von GET in **POST**
- Geben Sie die URL des benutzerdefinierten Webhooks ein, den Sie in einem der vorherigen Schritte erstellt haben. Sie sieht wie folgt aus: `https://eodts05snjmjz67.m.pipedream.net`

Du solltest das jetzt haben. Gehen Sie dann zu **Body**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl6.png)

Sie werden es dann sehen. Klicken Sie auf das Datenelementsymbol, wie unten angegeben.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl7.png)

Wählen Sie im Popup das Datenelement **XDM-Ereignis** aus, das Sie im vorherigen Schritt erstellt haben. Klicken Sie auf **Auswählen**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl8.png)

Sie werden es dann sehen. Klicken Sie auf **Änderungen beibehalten**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl9.png)

Sie werden es dann sehen. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl10.png)

Sie haben jetzt Ihre erste Regel in einer Ereignisweiterleitungs-Eigenschaft konfiguriert. Gehen Sie zu **Veröffentlichungsfluss**, um Ihre Änderungen zu veröffentlichen.
Öffnen Sie Ihre Entwicklungsbibliothek **Main**, indem Sie wie **auf** Bearbeiten“ klicken.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl11.png)

Klicken Sie auf **Schaltfläche „Alle geänderten Ressourcen hinzufügen**. Danach werden Ihre Regel und Ihr Datenelement in dieser Bibliothek angezeigt. Klicken Sie anschließend auf **Für Entwicklung speichern und erstellen**. Ihre Änderungen werden jetzt bereitgestellt.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl13.png)

Nach einigen Minuten sehen Sie, dass die Bereitstellung abgeschlossen ist und getestet werden kann.

![Adobe Experience Platform-Datenerfassungs-SSF](./images/rl14.png)

## Testen der Konfiguration

Navigieren Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf die 3 Punkte **…** in Ihrem Website-Projekt und dann auf **Ausführen**, um es zu öffnen.

![DSN](./../../datacollection/dc1.1/images/web8.png)

Anschließend wird Ihre Demo-Website geöffnet. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../../getting-started/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browser-Fenster.

![DSN](../../../getting-started/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../../getting-started/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../../getting-started/gettingstarted/images/web6.png)

Ihre Website wird dann in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../../getting-started/gettingstarted/images/web7.png)

Wenn Sie die Entwickleransicht Ihres Browsers öffnen, können Sie Netzwerkanfragen wie unten angegeben überprüfen. Wenn Sie den Filter **interact** verwenden, sehen Sie die Netzwerkanfragen, die vom Datenerfassungs-Client von Adobe Experience Platform an Adobe Edge gesendet werden.

![Einrichtung der Adobe Experience Platform-Datenerfassung](./images/hook1.png)

Wenn Sie die Roh-Payload auswählen, gehen Sie zu [https://jsonformatter.org/json-pretty-print](https://jsonformatter.org/json-pretty-print) und fügen Sie die Payload ein. Klicken Sie **Minimieren/Verschönern**. Anschließend sehen Sie die JSON-Payload, das **events**-Objekt und das **xdm**-Objekt. In einem der vorherigen Schritte haben Sie beim Definieren des Datenelements den Verweis **arc.event.xdm** verwendet, was dazu führt, dass Sie das **xdm**-Objekt dieser Payload analysieren.

![Einrichtung der Adobe Experience Platform-Datenerfassung](./images/hook2.png)

Wechseln Sie zur Ansicht Ihres benutzerdefinierten Webhooks [https://pipedream.com/requestbin](https://pipedream.com/requestbin) den Sie in einem der vorherigen Schritte verwendet haben. Sie sollten jetzt eine ähnliche Ansicht wie diese haben, wobei Netzwerkanfragen im linken Menü angezeigt werden. Es wird die Payload **xdm** angezeigt, die aus der oben gezeigten Netzwerkanfrage herausgefiltert wurde.

![Einrichtung der Adobe Experience Platform-Datenerfassung](./images/hook3.png)

Scrollen Sie in der Payload etwas nach unten, um den Seitennamen zu finden, der in diesem Fall &quot;**&quot;**.

![Einrichtung der Adobe Experience Platform-Datenerfassung](./images/hook4.png)

Wenn Sie jetzt auf der Website navigieren, werden zusätzliche Netzwerkanfragen in Echtzeit für diesen benutzerdefinierten Webhook verfügbar.

![Einrichtung der Adobe Experience Platform-Datenerfassung](./images/hook5.png)

Sie haben jetzt die Server-seitige Ereignisweiterleitung von Web-SDK-/XDM-Payloads an einen externen benutzerdefinierten Webhook konfiguriert. In den nächsten Übungen konfigurieren Sie einen ähnlichen Ansatz und senden dieselben Daten an Google Cloud Platform und AWS.

## Nächste Schritte

Navigieren Sie zu [2.5.4 Ereignisse an GCP Pub/Sub weiterleiten](./ex4.md){target="_blank"}

Zurück zu [Real-Time CDP Connections: Ereignisweiterleitung](./aep-data-collection-ssf.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
