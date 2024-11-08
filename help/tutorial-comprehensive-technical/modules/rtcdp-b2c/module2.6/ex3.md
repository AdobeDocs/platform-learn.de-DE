---
title: Konfigurieren des HTTP-API-Endpunkts in Adobe Experience Platform
description: Konfigurieren des HTTP-API-Endpunkts in Adobe Experience Platform
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 8%

---

# 2.6.3 HTTP-API-Streaming-Endpunkt in Adobe Experience Platform konfigurieren

Bevor Sie den Adobe Experience Platform Sink Connector in Kafka einrichten können, müssen Sie einen HTTP API Source Connector in Adobe Experience Platform erstellen. Die HTTP-API-Streaming-Endpunkt-URL ist erforderlich, um den Adobe Experience Platform Sink Connector einzurichten.

Um einen HTTP API Source Connector zu erstellen, melden Sie sich unter folgender URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Navigieren Sie im linken Menü zu **Quellen** und scrollen Sie im **Quellen-Katalog** nach unten, bis Sie die **HTTP-API** sehen. Klicken Sie auf **Daten hinzufügen**.

![Datenaufnahme](./images/kaep1.png)

Klicken Sie auf **Neues Konto**. Verwenden Sie `--aepUserLdap-- - Kafka` als Namen für Ihre HTTP-API-Verbindung, in diesem Fall **vangeluw - Kafka**. Aktivieren Sie das Kontrollkästchen für **XDM-kompatibel**. Klicken Sie auf **Mit Quelle verbinden**.

![Datenaufnahme](./images/kaep2.png)

Klicken Sie dann auf **Weiter**.

![Datenaufnahme](./images/kaep3.png)

Wählen Sie **Vorhandenen Datensatz** aus und öffnen Sie das Dropdown-Menü. Suchen Sie den Datensatz &quot;**Demo System - Event DataSet for Call Center&quot;(Global v1.1)** und wählen Sie ihn aus.

![Datenaufnahme](./images/kaep4.png)

Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/kaep6.png)

Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/kaep7.png)

Klicken Sie auf **Fertigstellen**.

![Datenaufnahme](./images/kaep8.png)

Daraufhin wird eine Übersicht über den soeben erstellten HTTP API Source Connector angezeigt.

![Datenaufnahme](./images/kaep9.png)

Sie müssen die URL **Streaming-Endpunkt** kopieren, die wie die unten stehende aussieht, da Sie sie in der nächsten Übung benötigen werden.

`https://dcs.adobedc.net/collection/d282bbfc8a540321341576275a8d052e9dc4ea80625dd9a5fe5b02397cfd80dc`

Du hast diese Übung beendet.

Nächster Schritt: [2.6.4 Installieren und konfigurieren Sie Kafka Connect und den Adobe Experience Platform Sink Connector](./ex4.md)

[Zurück zu Modul 2.6](./aep-apache-kafka.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
