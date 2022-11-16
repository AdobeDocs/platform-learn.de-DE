---
title: Konfigurieren des HTTP-API-Endpunkts in Adobe Experience Platform
description: Konfigurieren des HTTP-API-Endpunkts in Adobe Experience Platform
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 3346c57b-3a78-40b1-a891-053fc8781659
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 9%

---

# 15.3 HTTP-API-Streaming-Endpunkt in Adobe Experience Platform konfigurieren

Bevor Sie den Adobe Experience Platform Sink Connector in Kafka einrichten können, müssen Sie einen HTTP-API-Quell-Connector in Adobe Experience Platform erstellen. Die HTTP-API-Streaming-Endpunkt-URL ist erforderlich, um den Adobe Experience Platform Sink Connector einzurichten.

Um einen HTTP-API-Quell-Connector zu erstellen, melden Sie sich unter folgender URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](../module2/images/sb1.png)

Gehen Sie im linken Menü zu **Quellen** und scrollen Sie nach unten in die **Quellen-Katalog** bis **HTTP-API**. Klicken **Daten hinzufügen**.

![Datenaufnahme](./images/kaep1.png)

Klicken **Neues Konto**. Verwendung `--demoProfileLdap-- - Kafka` als Namen für Ihre HTTP-API-Verbindung verwenden, in diesem Fall **vangeluw - Kafka**. Aktivieren Sie das Kontrollkästchen für **XDM-kompatibel**. Klicken **Verbindung mit Quelle herstellen**.

![Datenaufnahme](./images/kaep2.png)

Sie sehen das hier, klicken Sie auf **Nächste**.

![Datenaufnahme](./images/kaep3.png)

Auswählen **Vorhandener Datensatz**, öffnen Sie das Dropdown-Menü. Datensatz suchen und auswählen **Demosystem - Ereignis-Datensatz für das Callcenter (Global v1.1)**.

![Datenaufnahme](./images/kaep4.png)

Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/kaep6.png)

Klicken Sie auf **Weiter**.

![Datenaufnahme](./images/kaep7.png)

Klicken Sie auf **Fertigstellen**.

![Datenaufnahme](./images/kaep8.png)

Daraufhin wird eine Übersicht über den soeben erstellten HTTP API Source Connector angezeigt.

![Datenaufnahme](./images/kaep9.png)

Sie müssen die **Streaming-Endpunkt** URL, die wie die unten stehende aussieht, da Sie sie in der nächsten Übung benötigen werden.

`https://dcs.adobedc.net/collection/d282bbfc8a540321341576275a8d052e9dc4ea80625dd9a5fe5b02397cfd80dc`

Du hast diese Übung beendet.

Nächster Schritt: [15.4 Installieren und Konfigurieren von Kafka Connect und Adobe Experience Platform Sink Connector](./ex4.md)

[Zurück zu Modul 15](./aep-apache-kafka.md)

[Zu allen Modulen zurückkehren](../../overview.md)
