---
title: Bootcamp - Vermischen von physisch und digital - Verwenden Sie die mobile App und den Trigger eines Beacon-Eintrags - Brasilien
description: Bootcamp - Vermischen von physisch und digital - Verwenden Sie die mobile App und den Trigger eines Beacon-Eintrags - Brasilien
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
source-git-commit: 75a878ba596078e6d013b65062606931402302dd
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# 3.1 Verwenden der App und Trigger eines Beacon-Eintrags

## Installieren der App

Vor der Installation des Programms müssen Sie **Tracking** auf Ihrem iOS-Gerät. Gehen Sie dazu zu **Einstellungen** > **Datenschutz und Sicherheit** > **Tracking** und stellen sicher, dass die Option **Zulassen, dass Apps die Verfolgung anfordern**.

![DSN](./../uc3/images/app4.png)

Navigieren Sie zur Apple App Store und suchen Sie nach `aepmobile-bootcamp`. Klicken **Installieren** oder **Download**.

![DSN](./../uc3/images/app1.png)

Nachdem die App installiert wurde, klicken Sie auf **Öffnen**.

![DSN](./../uc3/images/app2.png)

Klicken Sie auf **OK**.

![DSN](./../uc3/images/app9.png)

Klicken **Zulassen**.

![DSN](./../uc3/images/app3.png)

Klicken **Ich stimme zu**.

![DSN](./../uc3/images/app7.png)

Klicken **Verwendung der App zulassen**.

![DSN](./../uc3/images/app8.png)

Klicken **Zulassen**.

![DSN](./../uc3/images/app5.png)

Sie befinden sich jetzt in der App auf der Startseite und können die Journey durchlaufen.

![DSN](./../uc3/images/app12.png)

## Journey-Fluss des Kunden

Zunächst müssen Sie sich anmelden. Klicken Sie auf **Anmelden**.

![DSN](./images/app13.png)

Nachdem Sie Ihr Konto in den vorherigen Übungen erstellt haben, haben Sie dies auf der Website gesehen. Sie müssen jetzt die E-Mail-Adresse des Kontos, das Sie in der App erstellt haben, erneut verwenden, um sich anzumelden.

![Demo](./images/pv1.png)

Geben Sie hier die E-Mail-Adresse ein, die Sie auf der Website verwendet haben, und klicken Sie auf **Anmelden**.

![DSN](./images/app14.png)

Sie erhalten dann eine Bestätigung, dass Sie angemeldet sind, und Sie erhalten eine Push-Benachrichtigung.

![DSN](./images/app15.png)

Kehren Sie zur Homepage in der App zurück und sehen Sie zusätzliche Funktionen.

![DSN](./images/app17.png)

Gehen Sie zuerst zu **Produkte**. Klicken Sie in diesem Beispiel auf ein beliebiges Produkt. **Kaffee zum Mitnehmen**.

![DSN](./images/app19.png)

Du wirst die **Kaffee zum Mitnehmen** Produktseite in der App.

![DSN](./images/app20.png)

Sie simulieren jetzt ein Beacon-Eintrittsereignis an einem Offline-Store-Speicherort. Das Ziel der Simulation ist es, das Kundenerlebnis auf den In-Store-Bildschirmen zu personalisieren. Um das Erlebnis im Store zu visualisieren, wurde eine Seite erstellt, auf der die Informationen dynamisch angezeigt werden, die für den Kunden relevant sind, der gerade in den Store eingetreten ist.

Bevor Sie fortfahren, öffnen Sie bitte diese Webseite auf Ihrem Computer: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html)

Daraufhin sehen Sie Folgendes:

![DSN](./images/screen1.png)

Gehen Sie dann zurück zur Homepage. Klicken Sie auf **Beacon** Symbol.

![DSN](./images/app23.png)

Dann wirst du das sehen. Wählen Sie zuerst **Bootcamp Screen Beacon** und klicken Sie dann auf **Einstieg** Schaltfläche. Auf diese Weise können Sie einen Beacon-Eintrag simulieren.

![DSN](./images/app21.png)

Sehen Sie sich nun den Bildschirm im Geschäft an. Das zuletzt angezeigte Produkt wird innerhalb von 5 Sekunden angezeigt.

![DSN](./images/screen2.png)

Gehen Sie dann zurück zu **Produkte**. Klicken Sie in diesem Beispiel auf ein beliebiges Produkt. **Stranddecke Tan**.

![DSN](./images/app22.png)

Gehen Sie dann zurück zur Homepage. Klicken Sie auf **Beacon** Symbol.

![DSN](./images/app23.png)

Dann wirst du das sehen. Wählen Sie zuerst **Bootcamp Screen Beacon** und klicken Sie dann auf **Einstieg** erneut. Auf diese Weise können Sie einen Beacon-Eintrag simulieren.

![DSN](./images/app21.png)

Sehen Sie sich nun noch einmal den Bildschirm im Geschäft an. Das zuletzt angezeigte Produkt wird innerhalb von 5 Sekunden angezeigt.

![DSN](./images/screen3.png)

Sehen wir uns jetzt auch Ihren Profil-Viewer auf der Website an. Dort wurden viele Ereignisse hinzugefügt, um zu zeigen, dass jede Interaktion mit einem Kunden in Adobe Experience Platform erfasst und gespeichert wird.

![DSN](./images/screen4.png)

In den nächsten Übungen konfigurieren und testen Sie Ihre eigene Beacon-Einstiegs-Journey.

Nächster Schritt: [3.2 Ereignis erstellen](./ex2.md)

[Zurück zum Benutzerfluss 3](./uc3.md)

[Zu allen Modulen zurückkehren](../../overview.md)
