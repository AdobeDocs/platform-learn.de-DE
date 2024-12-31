---
title: Bootcamp - Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen - Zielgruppe an DV360 senden
description: Bootcamp - Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen - Zielgruppe an DV360 senden
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

# 1.5 Aktion durchführen: Zielgruppe an Facebook senden

Zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``Bootcamp``. Klicken Sie dazu auf den Text **[!UICONTROL Produktion]** in der blauen Linie am oberen Bildschirmrand. Nach Auswahl der entsprechenden [!UICONTROL Sandbox] wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

Gehen Sie im linken Menü zu **Ziele** und dann zu **Katalog**. Anschließend sehen Sie den **Zielkatalog**. Klicken Sie **Ziele** auf **Karte** Benutzerdefinierte Zielgruppe von **Facebook** auf „Zielgruppen aktivieren“.

![RTCDP](./images/rtcdpgoogleseg.png)

Wählen Sie das Ziel **bootcamp-facebook** aus und klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest2.png)

Wählen Sie in der Liste der verfügbaren Zielgruppen die Zielgruppe aus, die Sie in der vorherigen Übung erstellt haben. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest3.png)

Stellen Sie auf der **Zuordnung** sicher, dass das Kontrollkästchen **Umwandlung anwenden** aktiviert ist. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Wählen Sie auf der **Zielgruppen** Planung die Option **Herkunft Ihrer Zielgruppe** und setzen Sie sie auf **Direkt von Kunden**. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpcreatedest4.png)

Klicken Sie abschließend auf der **Überprüfen**-Seite auf **Beenden**.

![RTCDP](./images/rtcdpcreatedest5.png)

Ihre Zielgruppe ist jetzt mit benutzerdefinierten Facebook-Zielgruppen verknüpft. Jedes Mal, wenn sich eine Kundin oder ein Kunde für diese Zielgruppe qualifiziert, wird serverseitig an Facebook ein Signal gesendet, um diese Kundin oder diesen Kunden in die benutzerdefinierte Zielgruppe auf Facebook-Seite aufzunehmen.

In Facebook finden Sie Ihre Zielgruppe aus Adobe Experience Platform unter Benutzerdefinierte Zielgruppen :

![RTCDP](./images/rtcdpcreatedest5b.png)

Jetzt können Sie sehen, dass Ihre benutzerdefinierte Zielgruppe in Facebook angezeigt wird:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Zurück zu Benutzerfluss 1](./uc1.md)

[Zurück zu „Alle Module“](../../overview.md)
