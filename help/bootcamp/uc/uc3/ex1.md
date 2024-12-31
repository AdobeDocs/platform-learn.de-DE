---
title: Bootcamp - Mischung aus physischem und digitalem - Verwenden der mobilen App und Trigger eines Beacon-Eintrags
description: Bootcamp - Mischung aus physischem und digitalem - Verwenden der mobilen App und Trigger eines Beacon-Eintrags
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Mobile SDK
exl-id: c33c973b-db8a-49ce-bd6c-a6c4fbe579a0
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# 3.1 Verwenden der Mobile App und Trigger eines Beacon-Eintrags

## Installieren der Mobile App

Bevor Sie die App installieren, müssen Sie **Tracking** auf Ihrem iOS-Gerät aktivieren. Navigieren Sie dazu zu **Einstellungen** > **Datenschutz und Sicherheit** > **Tracking** und stellen Sie sicher, dass die Option **Zulassen, dass Apps Tracking anfordern**.

![DSN](./../uc3/images/app4.png)

Navigieren Sie zu Apple App Store und suchen Sie nach `aepmobile-bootcamp`. Klicken **auf** oder **Herunterladen**.

![DSN](./../uc3/images/app1.png)

Nachdem die App installiert wurde, klicken Sie auf **Öffnen**.

![DSN](./../uc3/images/app2.png)

Klicken Sie auf **OK**.

![DSN](./../uc3/images/app9.png)

Klicken Sie **Zulassen**.

![DSN](./../uc3/images/app3.png)

Klicken Sie **Ich stimme zu**.

![DSN](./../uc3/images/app7.png)

Klicken Sie **Erlauben bei Verwendung des -Programms**.

![DSN](./../uc3/images/app8.png)

Klicken Sie **Zulassen**.

![DSN](./../uc3/images/app5.png)

Jetzt sind Sie in der App, auf der Startseite, bereit, die Kunden-Journey zu durchlaufen.

![DSN](./../uc3/images/app12.png)

## Kunden-Journey-Fluss

Zunächst müssen Sie sich anmelden. Klicken Sie **Anmelden**.

![DSN](./images/app13.png)

Nachdem Sie Ihr Konto in den vorherigen Übungen erstellt haben, haben Sie dies auf der Website gesehen. Sie müssen jetzt die E-Mail-Adresse des Kontos wiederverwenden, das Sie in der App erstellt haben, um sich anzumelden.

![Demo](./images/pv1.png)

Geben Sie hier die auf der Website verwendete E-Mail-Adresse ein und klicken Sie auf **Login**.

![DSN](./images/app14.png)

Sie erhalten dann eine Bestätigung, dass Sie angemeldet sind, und Sie erhalten eine Push-Benachrichtigung.

![DSN](./images/app15.png)

Kehren Sie zur Startseite in der App zurück, und Sie werden sehen, dass zusätzliche Funktionen angezeigt werden.

![DSN](./images/app17.png)

Gehen Sie zunächst zu **Produkte**. Klicken Sie auf ein beliebiges Produkt, in diesem Beispiel **Coffee to go**.

![DSN](./images/app19.png)

In der App wird die **Coffee to go**-Produktseite angezeigt.

![DSN](./images/app20.png)

Sie simulieren jetzt ein Beacon-Eintrittsereignis an einem Offline-Store-Speicherort. Ziel der Simulation ist es, das Kundenerlebnis auf den Bildschirmen im Geschäft zu personalisieren. Um das In-Store-Erlebnis zu visualisieren, wurde eine Seite erstellt, auf der die Informationen dynamisch angezeigt werden, die für den Kunden relevant sind, der gerade den Store betreten hat.

Bevor Sie fortfahren, öffnen Sie diese Webseite auf Ihrem Computer: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html)

Sie sehen dann Folgendes:

![DSN](./images/screen1.png)

Gehen Sie dann zurück zur Homepage. Klicken Sie auf das **Beacon**-Symbol.

![DSN](./images/app23.png)

Sie werden es dann sehen. Wählen Sie zunächst **Bootcamp Screen Beacon** und klicken Sie dann auf die **entry**-Schaltfläche. Auf diese Weise können Sie einen Beacon-Eintrag simulieren.

![DSN](./images/app21.png)

Sehen Sie sich jetzt den Bildschirm „In-Store“ an. Dort wird das zuletzt angezeigte Produkt innerhalb von 5 Sekunden angezeigt.

![DSN](./images/screen2.png)

Gehen Sie dann zurück zu **Produkte**. Klicken Sie auf ein beliebiges Produkt, in diesem Beispiel **Stranddecke Tan**.

![DSN](./images/app22.png)

Gehen Sie dann zurück zur Homepage. Klicken Sie auf das **Beacon**-Symbol.

![DSN](./images/app23.png)

Sie werden es dann sehen. Wählen Sie zunächst **Bootcamp Screen Beacon** aus und klicken Sie dann erneut auf **entry**-Schaltfläche. Auf diese Weise können Sie einen Beacon-Eintrag simulieren.

![DSN](./images/app21.png)

Sehen Sie sich jetzt noch einmal den Bildschirm im Geschäft an. Dort wird das zuletzt angezeigte Produkt innerhalb von 5 Sekunden angezeigt.

![DSN](./images/screen3.png)

Sehen wir uns jetzt auch Ihren Profil-Viewer auf der Website an. Dort werden Sie viele Ereignisse sehen, die hinzugefügt wurden, nur um zu zeigen, dass jede Interaktion mit einem Kunden in Adobe Experience Platform erfasst und gespeichert wird.

![DSN](./images/screen4.png)

In den nächsten Übungen konfigurieren und testen Sie Ihre eigene Beacon-Einstiegs-Journey.

Nächster Schritt: [3.2 Erstellen Sie Ihr Ereignis](./ex2.md)

[Zurück zu Benutzerfluss 3](./uc3.md)

[Zurück zu „Alle Module“](../../overview.md)
