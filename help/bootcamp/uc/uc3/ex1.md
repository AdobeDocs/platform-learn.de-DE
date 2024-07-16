---
title: Bootcamp - Kombinieren von physisch und digital - Verwenden Sie die mobile App und Trigger eines Beacon-Eintrags
description: Bootcamp - Kombinieren von physisch und digital - Verwenden Sie die mobile App und Trigger eines Beacon-Eintrags
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

# 3.1 Verwenden der mobilen App und Trigger eines Beacon-Eintrags

## Installieren der App

Bevor Sie die App installieren, müssen Sie das **Tracking** auf Ihrem iOS-Gerät aktivieren. Wechseln Sie dazu zu **Einstellungen** > **Datenschutz und Sicherheit** > **Tracking** und stellen Sie sicher, dass die Option **Zulassen, dass Apps verfolgt werden können**, verwendet wird.

![DSN](./../uc3/images/app4.png)

Navigieren Sie zur Apple App Store und suchen Sie nach `aepmobile-bootcamp`. Klicken Sie auf **Installieren** oder **Herunterladen**.

![DSN](./../uc3/images/app1.png)

Klicken Sie nach der Installation der App auf **Öffnen**.

![DSN](./../uc3/images/app2.png)

Klicken Sie auf **OK**.

![DSN](./../uc3/images/app9.png)

Klicken Sie auf **Allow**.

![DSN](./../uc3/images/app3.png)

Klicken Sie auf **Ich stimme zu**.

![DSN](./../uc3/images/app7.png)

Klicken Sie auf **Zulassen bei Verwendung von App**.

![DSN](./../uc3/images/app8.png)

Klicken Sie auf **Allow**.

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

Sie erhalten dann eine Bestätigung, dass Sie angemeldet sind, und eine Push-Benachrichtigung.

![DSN](./images/app15.png)

Kehren Sie zur Homepage in der App zurück und sehen Sie zusätzliche Funktionen.

![DSN](./images/app17.png)

Gehen Sie zuerst zu **Produkte**. Klicken Sie auf ein beliebiges Produkt, in diesem Beispiel **Kaffee, um zu gehen**.

![DSN](./images/app19.png)

Sie sehen die Produktseite **Kaffee zum Wechseln** in der App.

![DSN](./images/app20.png)

Sie simulieren jetzt ein Beacon-Eintrittsereignis an einem Offline-Store-Speicherort. Das Ziel der Simulation ist es, das Kundenerlebnis auf den In-Store-Bildschirmen zu personalisieren. Um das Erlebnis im Store zu visualisieren, wurde eine Seite erstellt, auf der die Informationen dynamisch angezeigt werden, die für den Kunden relevant sind, der gerade in den Store eingetreten ist.

Bevor Sie fortfahren, öffnen Sie diese Webseite auf Ihrem Computer: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html)

Daraufhin sehen Sie Folgendes:

![DSN](./images/screen1.png)

Gehen Sie dann zurück zur Homepage. Klicken Sie auf das Symbol **Beacon** .

![DSN](./images/app23.png)

Dann wirst du das sehen. Wählen Sie zunächst **Bootcamp Screen Beacon** und klicken Sie dann auf die Schaltfläche **entry** . Auf diese Weise können Sie einen Beacon-Eintrag simulieren.

![DSN](./images/app21.png)

Sehen Sie sich nun den Bildschirm im Geschäft an. Das zuletzt angezeigte Produkt wird innerhalb von 5 Sekunden angezeigt.

![DSN](./images/screen2.png)

Gehen Sie dann zurück zu **Products**. Klicken Sie auf ein beliebiges Produkt, in diesem Beispiel **Stranddecke Tan**.

![DSN](./images/app22.png)

Gehen Sie dann zurück zur Homepage. Klicken Sie auf das Symbol **Beacon** .

![DSN](./images/app23.png)

Dann wirst du das sehen. Wählen Sie zunächst **Bootcamp Screen Beacon** und klicken Sie dann erneut auf die Schaltfläche **entry** . Auf diese Weise können Sie einen Beacon-Eintrag simulieren.

![DSN](./images/app21.png)

Sehen Sie sich nun noch einmal den Bildschirm im Geschäft an. Das zuletzt angezeigte Produkt wird innerhalb von 5 Sekunden angezeigt.

![DSN](./images/screen3.png)

Sehen wir uns jetzt auch Ihren Profil-Viewer auf der Website an. Dort wurden viele Ereignisse hinzugefügt, um zu zeigen, dass jede Interaktion mit einem Kunden in Adobe Experience Platform erfasst und gespeichert wird.

![DSN](./images/screen4.png)

In den nächsten Übungen konfigurieren und testen Sie Ihre eigene Beacon-Journey.

Nächster Schritt: [3.2 Ereignis erstellen](./ex2.md)

[Zurück zum Benutzerfluss 3](./uc3.md)

[Zu allen Modulen zurückkehren](../../overview.md)
