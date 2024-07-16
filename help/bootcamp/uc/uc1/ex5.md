---
title: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen einer Zielgruppe und Handeln - Senden Sie Ihre Zielgruppe an DV360
description: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen einer Zielgruppe und Handeln - Senden Sie Ihre Zielgruppe an DV360
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
feature: Destinations
exl-id: 31f46e37-f1c0-4730-8520-1ccd98df6501
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 3%

---

# 1.5 Aktion durchführen: Senden Sie Ihre Audience an Facebook

Wechseln Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende [!UICONTROL Sandbox] ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

Wechseln Sie im linken Menü zu **Ziele** und gehen Sie dann zu **Katalog**. Daraufhin wird der **Zielkatalog** angezeigt. Klicken Sie in **Ziele** auf der Karte **Benutzerdefinierte Facebook-Zielgruppe** auf **Zielgruppen aktivieren** .

![RTCDP](./images/rtcdpgoogleseg.png)

Wählen Sie das Ziel **bootcamp-facebook** aus und klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest2.png)

Wählen Sie in der Liste der verfügbaren Zielgruppen die Zielgruppe aus, die Sie in der vorherigen Übung erstellt haben. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest3.png)

Stellen Sie auf der Seite **Mapping** sicher, dass das Kontrollkästchen **Transformation anwenden** aktiviert ist. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Wählen Sie auf der Seite **Zielgruppenplan** den **Ursprung Ihrer Zielgruppe** aus und setzen Sie ihn auf **Direkt von Kunden**. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4.png)

Klicken Sie abschließend auf der Seite **Überprüfen** auf **Beenden**.

![RTCDP](./images/rtcdpcreatedest5.png)

Ihre Zielgruppe ist jetzt mit benutzerdefinierten Facebook-Zielgruppen verknüpft. Jedes Mal, wenn sich ein Kunde für diese Zielgruppe qualifiziert, wird ein Signal an die serverseitige Facebook gesendet, um diesen Kunden in die benutzerdefinierte Zielgruppe auf Facebook-Seite aufzunehmen.

In Facebook finden Sie Ihre Zielgruppe aus Adobe Experience Platform unter Benutzerdefinierte Zielgruppen :

![RTCDP](./images/rtcdpcreatedest5b.png)

Ihre benutzerdefinierte Zielgruppe wird jetzt in Facebook angezeigt:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Zurück zum Benutzerfluss 1](./uc1.md)

[Zu allen Modulen zurückkehren](../../overview.md)
