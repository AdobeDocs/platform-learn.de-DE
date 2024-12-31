---
title: Bootcamp - Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen - Zielgruppe an Adobe Target senden
description: Bootcamp - Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen - Zielgruppe an Adobe Target senden
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
ht-degree: 1%

---

# 1.4 Aktion durchführen: Zielgruppe an Adobe Target senden

Zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``Bootcamp``. Klicken Sie dazu auf den Text **[!UICONTROL Produktion]** in der blauen Linie am oberen Bildschirmrand. Nach Auswahl der entsprechenden [!UICONTROL Sandbox] wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

## 1.4.1 Aktivieren Ihrer Zielgruppe für Ihr Adobe Target-Ziel

Adobe Target ist als Ziel über Real-Time CDP verfügbar. Um Ihre Adobe Target-Integration einzurichten, gehen Sie zu **Ziele**, zu **Katalog**.

Klicken Sie im Menü **Kategorien** auf **Personalization&quot;.** Anschließend wird die Zielkarte **Adobe Target** angezeigt. Klicken Sie **Zielgruppen aktivieren**.

![AT](./images/atdest1.png)

Wählen Sie die ``Bootcamp Target`` aus und klicken Sie auf **Weiter**.

![AT](./images/atdest3.png)

Wählen Sie in der Liste der verfügbaren Zielgruppen die Zielgruppe aus, die Sie in [1.3 Zielgruppe erstellen](./ex3.md) erstellt haben. Diese heißt `yourLastName - Interest in Real-Time CDP`. Klicken Sie dann auf **Weiter**.

![AT](./images/atdest8.png)

Klicken Sie auf der nächsten Seite auf **Weiter**.

![AT](./images/atdest9.png)

Klicken Sie auf **Fertigstellen**.

![AT](./images/atdest10.png)

Ihre Zielgruppe ist jetzt für Adobe Target aktiviert.

![AT](./images/atdest11.png)

>[!IMPORTANT]
>
>Wenn Sie soeben Ihr Adobe Target-Ziel in Real-Time CDP erstellt haben, kann es bis zu einer Stunde dauern, bis das Ziel live ist. Dies ist eine einmalige Wartezeit aufgrund der Einrichtung der Backend-Konfiguration. Sobald die anfängliche Wartezeit von einer Stunde und die Backend-Konfiguration abgeschlossen sind, stehen neu hinzugefügte Edge-Zielgruppen, die an das Adobe Target-Ziel gesendet werden, für das Targeting in Echtzeit zur Verfügung.

## 1.4.2 Konfigurieren der formularbasierten Aktivität in Adobe Target

Nachdem Sie nun Ihre Real-Time CDP-Zielgruppe für den Versand an Adobe Target konfiguriert haben, können Sie Ihre Experience Targeting-Aktivität in Adobe Target konfigurieren. In dieser Übung konfigurieren Sie eine auf Visual Experience Composer basierende Aktivität.

Gehen Sie zur Adobe Experience Cloud-Homepage unter [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Klicken Sie auf **Target**, um es zu öffnen.

![RTCDP](./images/excl.png)

Auf der Startseite von {**}Adobe Target werden alle vorhandenen Aktivitäten angezeigt.**
Klicken Sie auf **+ Aktivität erstellen** um eine neue Aktivität zu erstellen.

![RTCDP](./images/exclatov.png)

Wählen Sie **Erlebnis-Targeting** aus.

![RTCDP](./images/exclatcrxt.png)

Wählen Sie **Visual** aus und legen Sie **Aktivitäts-URL** auf `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpantXX.html` fest. Ersetzen Sie jedoch vorher XX durch eine Zahl zwischen 01 und 30.

>[!IMPORTANT]
>
>Jeder Teilnehmer der Aktivierung sollte eine separate Web-Seite verwenden, um Kollisionen zwischen verschiedenen Adobe Target-Erlebnissen zu vermeiden. Sie können eine Web-Seite auswählen und die URL finden, indem Sie hier gehen: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Alle Seiten verwenden dieselbe Basis-URL und enden auf die Nummer des Teilnehmers .
>
>Beispielsweise sollte Teilnehmer 1 die URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html` und Teilnehmer 30 die URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html` verwenden.

Wählen Sie den Arbeitsbereich **AT Bootcamp** aus.

Klicken Sie auf **Weiter**.

![RTCDP](./images/exclatcrxtdtlform.png)

Sie befinden sich jetzt im Visual Experience Composer. Es kann 20-30 Sekunden dauern, bis die Website vollständig geladen ist.

![RTCDP](./images/atform1.png)

Die Standardzielgruppe ist derzeit **Alle Besucher**. Klicken Sie auf die **3** neben **Alle Besucher** und klicken Sie auf **Zielgruppe ändern**.

![RTCDP](./images/atform3.png)

Jetzt sehen Sie die Liste der verfügbaren Zielgruppen, und die Adobe Experience Platform-Zielgruppe, die Sie zuvor erstellt und an Adobe Target gesendet haben, ist jetzt Teil dieser Liste. Wählen Sie die zuvor in Adobe Experience Platform erstellte Zielgruppe aus. Klicken Sie **Zielgruppe zuweisen**.

![RTCDP](./images/exclatvecchaud.png)

Ihre Adobe Experience Platform-Zielgruppe ist jetzt Teil dieser Experience Targeting-Aktivität.

![RTCDP](./images/atform4.png)

Bevor Sie das Hero-Bild ändern können, müssen Sie auf **Alle zulassen** im Cookie-Banner klicken.

Navigieren Sie dazu zu **Durchsuchen**

![RTCDP](./images/cook1.png)

Klicken Sie anschließend auf **Alle zulassen**.

![RTCDP](./images/cook2.png)

Gehen Sie dann zurück zu **Erstellen**.

![RTCDP](./images/cook3.png)

Lassen Sie uns nun das Hero-Bild auf der Homepage der Website ändern. Klicken Sie auf das standardmäßige Hero-Bild auf der Website, klicken Sie auf **Inhalt ersetzen** und wählen Sie dann **Bild** aus.

![RTCDP](./images/atform5.png)

Suchen Sie nach der Bilddatei **rtcdp.png**. Wählen Sie es aus und klicken Sie dann auf **Speichern**.

![RTCDP](./images/atform6.png)

Anschließend sehen Sie das neue Erlebnis mit dem neuen Bild für Ihre ausgewählte Zielgruppe.

![RTCDP](./images/atform7.png)

Klicken Sie auf den Titel Ihrer Aktivität oben links, um sie umzubenennen.

![RTCDP](./images/exclatvecname.png)

Für den Namen verwenden Sie:

- `yourLastName - RTCDP - XT (VEC)`

Klicken Sie auf **Weiter**.

![RTCDP](./images/atform8.png)

Klicken Sie auf **Weiter**.

![RTCDP](./images/atform8a.png)

Gehen Sie auf der **Ziele und Einstellungen** zu **Zielmetriken**.

![RTCDP](./images/atform9.png)

Setzen Sie das Primäre Ziel auf **Interaktion** - **Zeit vor Ort**. Klicken Sie **Speichern und schließen**.

![RTCDP](./images/vec3.png)

Sie befinden sich jetzt auf der Seite **Aktivitätsübersicht**. Sie müssen Ihre Aktivität noch aktivieren.

![RTCDP](./images/atform10.png)

Klicken Sie auf das Feld **Inaktiv** und wählen Sie **Aktivieren** aus.

![RTCDP](./images/atform11.png)

Sie erhalten dann eine visuelle Bestätigung, dass Ihre Aktivität jetzt live ist.

![RTCDP](./images/atform12.png)

Ihre Aktivität ist jetzt live und kann auf der Bootcamp-Website getestet werden.

Wenn Sie jetzt zu Ihrer Demo-Website zurückkehren und die Produktseite für **Real-Time CDP** besuchen, qualifizieren Sie sich sofort für die von Ihnen erstellte Zielgruppe, und die Adobe Target-Aktivität wird auf der Startseite in Echtzeit angezeigt.

>[!IMPORTANT]
>
>Jeder Teilnehmer der Aktivierung sollte eine separate Web-Seite verwenden, um Kollisionen zwischen verschiedenen Adobe Target-Erlebnissen zu vermeiden. Sie können eine Web-Seite auswählen und die URL finden, indem Sie hier gehen: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Alle Seiten verwenden dieselbe Basis-URL und enden auf die Nummer des Teilnehmers .
>
>Beispielsweise sollte Teilnehmer 1 die URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html` und Teilnehmer 30 die URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html` verwenden.

![RTCDP](./images/atform12a.png)

Nächster Schritt: [1.5 Aktion durchführen: Ihre Zielgruppe an Facebook senden](./ex5.md)

[Zurück zu Benutzerfluss 1](./uc1.md)

[Zurück zu „Alle Module“](../../overview.md)
