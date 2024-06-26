---
title: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen einer Zielgruppe und Handeln - Senden Sie Ihre Zielgruppe an Adobe Target
description: Bootcamp - Echtzeit-Kundendatenplattform - Erstellen einer Zielgruppe und Handeln - Senden Sie Ihre Zielgruppe an Adobe Target
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
solution: Experience Platform, Target
feature: Audiences, Integrations
exl-id: 6a76c2ab-96b7-4626-a6d3-afd555220b1e
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 2%

---

# 1.4 Aktion durchführen: Senden Sie Ihre Audience an Adobe Target

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

## 1.4.1 Zielgruppe für Adobe Target aktivieren

Adobe Target ist als Ziel von Real-Time CDP verfügbar. Informationen zum Einrichten der Adobe Target-Integration finden Sie unter **Ziele**, um **Katalog**.

Klicks **Personalisierung** im **Kategorien** Menü. Sie werden dann die **Adobe Target** Zielkarte. Klicks **Aktivieren von Zielgruppen**.

![AT](./images/atdest1.png)

Ziel auswählen ``Bootcamp Target`` und klicken **Nächste**.

![AT](./images/atdest3.png)

Wählen Sie in der Liste der verfügbaren Zielgruppen die in [1.3 Erstellen einer Zielgruppe](./ex3.md), der `yourLastName - Interest in Real-Time CDP`. Klicken Sie dann auf **Weiter**.

![AT](./images/atdest8.png)

Klicken Sie auf der nächsten Seite auf **Nächste**.

![AT](./images/atdest9.png)

Klicken Sie auf **Fertigstellen**.

![AT](./images/atdest10.png)

Ihre Audience ist jetzt für Adobe Target aktiviert.

![AT](./images/atdest11.png)

>[!IMPORTANT]
>
>Wenn Sie Ihr Adobe Target-Ziel gerade in Real-Time CDP erstellt haben, kann es bis zu einer Stunde dauern, bis das Ziel aktiv ist. Dies ist eine einmalige Wartezeit aufgrund der Einrichtung der Backend-Konfiguration. Sobald die anfängliche Wartezeit von einer Stunde und die Backend-Konfiguration abgeschlossen sind, sind neu hinzugefügte Edge-Zielgruppen, die an das Adobe Target-Ziel gesendet werden, für das Targeting in Echtzeit verfügbar.

## 1.4.2 Konfigurieren der formularbasierten Adobe Target-Aktivität

Nachdem Ihre Real-Time CDP-Audience für den Versand an Adobe Target konfiguriert wurde, können Sie Ihre Erlebnis-Targeting-Aktivität in Adobe Target konfigurieren. In dieser Übung konfigurieren Sie eine Visual Experience Composer-basierte Aktivität.

Rufen Sie die Adobe Experience Cloud-Homepage auf, indem Sie [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Klicks **Target** , um es zu öffnen.

![RTCDP](./images/excl.png)

Im **Adobe Target** Homepage werden Sie alle vorhandenen Aktivitäten sehen.
Klicks **+ Aktivität erstellen** , um eine neue Aktivität zu erstellen.

![RTCDP](./images/exclatov.png)

Auswählen **Erlebnis-Targeting**.

![RTCDP](./images/exclatcrxt.png)

Auswählen **Visuell** und legen Sie die **Aktivitäts URL** nach `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpantXX.html`, aber bevor Sie dies tun, ersetzen Sie XX durch eine Zahl zwischen 01 und 30.

>[!IMPORTANT]
>
>Jeder Teilnehmer der Aktivierung sollte eine separate Webseite verwenden, um Kollisionen verschiedener Adobe Target-Erlebnisse zu vermeiden. Sie können eine Webseite auswählen und die URL finden, indem Sie hier gehen: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Seiten teilen alle dieselbe Basis-URL und enden in der Anzahl der Teilnehmer.
>
>Beispiel: Teilnehmer 1 sollte URL verwenden `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html`, Teilnehmer 30 sollte URL verwenden `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html`.

Arbeitsbereich auswählen **AT Bootcamp**.

Klicken Sie auf **Weiter**.

![RTCDP](./images/exclatcrxtdtlform.png)

Sie befinden sich jetzt im Visual Experience Composer. Es kann 20-30 Sekunden dauern, bis die Website vollständig geladen ist.

![RTCDP](./images/atform1.png)

Die Standardzielgruppe ist derzeit **Alle Besucher**. Klicken Sie auf **3 Punkte** neben **Alle Besucher** und klicken **Zielgruppe ändern**.

![RTCDP](./images/atform3.png)

Jetzt wird die Liste der verfügbaren Zielgruppen angezeigt. Die zuvor erstellte und an Adobe Target gesendete Adobe Experience Platform-Zielgruppe ist jetzt Teil dieser Liste. Wählen Sie die zuvor in Adobe Experience Platform erstellte Audience aus. Klicks **Zielgruppe zuweisen**.

![RTCDP](./images/exclatvecchaud.png)

Ihre Adobe Experience Platform-Zielgruppe ist jetzt Teil dieser Erlebnis-Targeting-Aktivität.

![RTCDP](./images/atform4.png)

Bevor Sie das Hero-Bild ändern können, müssen Sie auf **Alle zulassen** im Cookie-Banner.

Gehen Sie dazu zu **Durchsuchen**

![RTCDP](./images/cook1.png)

Klicken Sie anschließend auf **Alle zulassen**.

![RTCDP](./images/cook2.png)

Gehen Sie als Nächstes zurück zu **Erstellen**.

![RTCDP](./images/cook3.png)

Ändern wir nun das Hero-Bild auf der Startseite der Website. Klicken Sie auf das standardmäßige Hero-Bild auf der Website und klicken Sie auf **Inhalt ersetzen** und wählen Sie **Bild**.

![RTCDP](./images/atform5.png)

Suchen Sie nach der Bilddatei. **rtcdp.png**. Wählen Sie es aus und klicken Sie dann auf **Speichern**.

![RTCDP](./images/atform6.png)

Anschließend sehen Sie das neue Erlebnis mit dem neuen Bild für Ihre ausgewählte Zielgruppe.

![RTCDP](./images/atform7.png)

Klicken Sie auf den Titel Ihrer Aktivität in der oberen linken Ecke, um sie umzubenennen.

![RTCDP](./images/exclatvecname.png)

Für den Namen verwenden Sie bitte:

- `yourLastName - RTCDP - XT (VEC)`

Klicken Sie auf **Weiter**.

![RTCDP](./images/atform8.png)

Klicken Sie auf **Weiter**.

![RTCDP](./images/atform8a.png)

Im **Ziele und Einstellungen** - Seite, navigieren Sie zu **Zielmetriken**.

![RTCDP](./images/atform9.png)

Primäres Ziel festlegen auf **Interaktion** - **Besuchszeit pro Site**. Klicken Sie auf **Speichern und schließen**.

![RTCDP](./images/vec3.png)

Du bist jetzt auf der **Aktivitätsübersicht** Seite. Sie müssen Ihre Aktivität weiterhin aktivieren.

![RTCDP](./images/atform10.png)

Klicken Sie auf das Feld **Inaaktiv** und wählen **Aktivieren**.

![RTCDP](./images/atform11.png)

Sie erhalten dann eine visuelle Bestätigung, dass Ihre Aktivität jetzt live ist.

![RTCDP](./images/atform12.png)

Ihre Aktivität ist jetzt live und kann auf der Bootcamp-Website getestet werden.

Wenn Sie jetzt zu Ihrer Demo-Website zurückkehren und die Produktseite für **Real-Time CDP** eingeben, werden Sie sich sofort für die von Ihnen erstellte Zielgruppe qualifizieren und die Adobe Target-Aktivität wird auf der Startseite in Echtzeit angezeigt.

>[!IMPORTANT]
>
>Jeder Teilnehmer der Aktivierung sollte eine separate Webseite verwenden, um Kollisionen verschiedener Adobe Target-Erlebnisse zu vermeiden. Sie können eine Webseite auswählen und die URL finden, indem Sie hier gehen: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Seiten teilen alle dieselbe Basis-URL und enden in der Anzahl der Teilnehmer.
>
>Beispiel: Teilnehmer 1 sollte URL verwenden `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html`, Teilnehmer 30 sollte URL verwenden `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html`.

![RTCDP](./images/atform12a.png)

Nächster Schritt: [1.5 Aktion durchführen: Senden Sie Ihre Audience an Facebook](./ex5.md)

[Zurück zum Benutzerfluss 1](./uc1.md)

[Zu allen Modulen zurückkehren](../../overview.md)
