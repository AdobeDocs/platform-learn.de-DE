---
title: Bootcamp - Personalisierung im Callcenter - Brasilien
description: Bootcamp - Personalisierung im Callcenter - Brasilien
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
source-git-commit: 75a878ba596078e6d013b65062606931402302dd
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 1%

---

# 2.6 Personalisierung im Callcenter

Wie bereits mehrfach während des Bootcamps besprochen wurde, sollte die Personalisierung des Kundenerlebnisses auf Omnichannel-Weise erfolgen. Ein Callcenter ist oft ziemlich vom Rest der Journey getrennt und führt oft zu frustrierenden Kundenerlebnissen, muss aber nicht sein. Lassen Sie uns Ihnen ein Beispiel dafür zeigen, wie das Callcenter in Echtzeit problemlos mit Adobe Experience Platform verbunden werden kann.

## Journey des Kunden

In der vorherigen Übung haben Sie mithilfe der Mobile App ein Produkt gekauft, indem Sie auf die **Kaufen** Schaltfläche.

![DSN](./images/app20.png)

Nehmen wir an, Sie haben eine Frage zum Status Ihrer Bestellung, was würden Sie tun? Normalerweise rufen Sie das Callcenter an.

Bevor Sie das Callcenter anrufen, müssen Sie Ihre **Treueprogramm-ID**. Ihre Treuekennung finden Sie im Profil-Viewer der Website.

![DSN](./images/cc1.png)

In diesem Fall wird die **Treueprogramm-ID** is **5863105**. Im Rahmen unserer benutzerdefinierten Implementierung der Callcenter-Funktion in der Demo-Umgebung müssen Sie Ihrem **Treueprogramm-ID**. Das Präfix lautet **11373**, sodass die in diesem Beispiel zu verwendende Loyalitäts-ID **11373 5863105**.

Machen wir das jetzt! Ihr Telefon benutzen und die Nummer anrufen **+1 (323) 745-1670**.

![DSN](./images/cc2.png)

Sie werden aufgefordert, Ihre Loyalitäts-ID einzugeben, gefolgt von **#**. Geben Sie Ihre Loyalitäts-ID ein.

![DSN](./images/cc3.png)

Sie werden dann hören **Hallo, Vorname**. Dieser Vorname stammt aus dem Echtzeit-Kundenprofil in Adobe Experience Platform. Sie haben dann drei Möglichkeiten. Pressenummer **1**, **Bestellstatus**.

![DSN](./images/cc4.png)

Nachdem Sie Ihren Bestellstatus gehört haben, können Sie auswählen, ob Sie **1** um zum Hauptmenü zurückzukehren, oder drücken Sie andernfalls 2. Presse **2**.

![DSN](./images/cc5.png)

Sie werden dann aufgefordert, Ihr Callcenter-Erlebnis zu bewerten, indem Sie eine Zahl zwischen 1 und 5 auswählen, wobei 1 niedrig und 5 hoch ist. Treffen Sie Ihre Wahl.

![DSN](./images/cc6.png)

Ihr Anruf an das Callcenter wird nun eingestellt.

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](./images/sb1.png)

Gehen Sie im linken Menü zu **Profile** und **Durchsuchen**.

![Kundenprofil](./images/homemenu.png)

Wählen Sie die **Identitäts-Namespace** **Email** und geben Sie die E-Mail-Adresse Ihres Kundenprofils ein. Klicken **Ansicht**. Klicken Sie auf , um Ihr Profil zu öffnen.

![DSN](./images/cc7.png)

Ihr Kundenprofil wird erneut angezeigt. Navigieren Sie zu **Veranstaltungen**.

![DSN](./images/cc8.png)

Unter &quot;events&quot;sehen Sie 2 Ereignisse mit einem eventType von **callCenter**. Das erste Ereignis ist das Ergebnis Ihrer Antwort auf die Frage **Bewerten Sie die Zufriedenheit Ihrer Anrufe**.

![DSN](./images/cc9.png)

Scrollen Sie ein wenig nach unten, und Sie sehen das Ereignis, das aufgezeichnet wurde, als Sie die Option zum Überprüfen Ihrer **Bestellstatus**.

![DSN](./images/cc10.png)

Navigieren Sie zu **Segmentmitgliedschaft**. Jetzt sehen Sie, dass sich zwei Segmente in Echtzeit auf Ihr Profil qualifizieren, basierend auf den Interaktionen, die Sie über das Callcenter hatten. Diese Segmentmitgliedschaften können und sollten dann verwendet werden, um zu beeinflussen, welche Kommunikation und Personalisierung über andere Kanäle hinweg erfolgt.

![DSN](./images/cc11.png)

Du bist jetzt mit dieser Übung fertig.

[Zurück zum Benutzerfluss 2](./uc2.md)

[Zu allen Modulen zurückkehren](../../overview.md)
