---
title: Konfigurieren des HTTP-API-Endpunkts in Adobe Experience Platform
description: Konfigurieren des HTTP-API-Endpunkts in Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 621a4db7-0aff-42bf-ad42-daec6e924451
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 7%

---

# 2.6.3 Konfigurieren des HTTP-API-Streaming-Endpunkts in Adobe Experience Platform

Bevor Sie den Adobe Experience Platform Sink Connector in Kafka einrichten können, müssen Sie einen HTTP-API-Source-Connector in Adobe Experience Platform erstellen. Die HTTP-API-Streaming-Endpunkt-URL ist erforderlich, um den Adobe Experience Platform Sink Connector einzurichten.

Um einen Source-Connector für die HTTP-API zu erstellen, melden Sie sich unter dieser URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

Navigieren Sie im linken Menü zu **Quellen** und scrollen Sie im **Quellkatalog** nach unten, bis Sie **HTTP-API** sehen. Klicken Sie **Setup**.

![Datenaufnahme](./images/kaep1.png)

Klicken Sie auf **Neues Konto**. Verwenden Sie `--aepUserLdap-- - Kafka` als Namen für Ihre HTTP-API-Verbindung, in diesem Fall **vangeluw - Kafka**. Aktivieren Sie das Kontrollkästchen für **XDM-kompatibel**. Klicken Sie auf **Mit Quelle verbinden**.

![Datenaufnahme](./images/kaep2.png)

Sie sehen dies. Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/kaep3.png)

Wählen Sie **Vorhandener Datensatz** aus und öffnen Sie das Dropdown-Menü. Suchen Sie den Datensatz **Demosystem - Ereignisdatensatz für Callcenter (Global v1.1)** und wählen Sie ihn aus.

Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/kaep4.png)

Klicken Sie auf **Fertigstellen**.

![Datenaufnahme](./images/kaep8.png)

Anschließend sehen Sie einen Überblick über den soeben erstellten HTTP-API-Source-Connector.

Sie müssen die URL **Streaming-Endpunkt** kopieren, die wie die folgende aussieht, da Sie sie in der nächsten Übung benötigen werden.

`https://dcs.adobedc.net/collection/63751d0f299eeb7aa48a2f22acb284ed64de575f8640986d8e5a935741be9067`

![Datenaufnahme](./images/kaep9.png)

Du hast diese Übung beendet.

## Nächste Schritte

Wechseln Sie zu [2.6.4 Installieren und konfigurieren Sie Kafka Connect und den Adobe Experience Platform Sink Connector](./ex4.md){target="_blank"}

Gehen Sie zurück zu [Streamen Sie Daten von Apache Kafka nach Adobe Experience Platform](./aep-apache-kafka.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
