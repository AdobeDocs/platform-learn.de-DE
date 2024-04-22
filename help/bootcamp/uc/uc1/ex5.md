---
title: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln - Senden Sie Ihr Segment an DV360
description: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln - Senden Sie Ihr Segment an DV360
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
feature: Destinations
exl-id: 31f46e37-f1c0-4730-8520-1ccd98df6501
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 3%

---

# 1.5 Aktion durchführen: Segment an Facebook senden

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

Gehen Sie im linken Menü zu **Ziele**, gehen Sie dann zu **Katalog**. Sie werden dann die **Zielkatalog**. In **Ziele** klicken **Segmente aktivieren** auf **Benutzerdefinierte facebook-Zielgruppe** Karte.

![RTCDP](./images/rtcdpgoogleseg.png)

Ziel auswählen **bootcamp-facebook** und klicken **Nächste**.

![RTCDP](./images/rtcdpcreatedest2.png)

Wählen Sie in der Liste der verfügbaren Segmente das Segment aus, das Sie in der vorherigen Übung erstellt haben. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest3.png)

Im **Zuordnung** -Seite, stellen Sie sicher, dass die **Anwenden von Umwandlungen** aktiviert ist. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Im **Segmentplan** Seite, wählen Sie die **Herkunft der Audience** und legen Sie **Direkt von Kunden**. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4.png)

Abschließend zur **Überprüfen** Seite, klicken **Beenden**.

![RTCDP](./images/rtcdpcreatedest5.png)

Ihr Segment ist jetzt mit benutzerdefinierten Facebook-Zielgruppen verknüpft. Jedes Mal, wenn sich ein Kunde für dieses Segment qualifiziert, wird ein Signal an die Server-seitige Facebook gesendet, um diesen Kunden in die benutzerdefinierte Zielgruppe auf Facebook-Seite aufzunehmen.

In Facebook finden Sie Ihr Segment aus Adobe Experience Platform unter Benutzerdefinierte Zielgruppen :

![RTCDP](./images/rtcdpcreatedest5b.png)

Ihre benutzerdefinierte Zielgruppe wird jetzt in Facebook angezeigt:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Zurück zum Benutzerfluss 1](./uc1.md)

[Zu allen Modulen zurückkehren](../../overview.md)
