---
title: Offer Decisioning - Testen der Entscheidung
description: Offer Decisioning - Testen der Entscheidung
kt: 5342
doc-type: tutorial
exl-id: c40b9b8c-9717-403c-bf02-6b8f42a59c05
source-git-commit: 2e856759e1a9b5509ad0632e28b269bcfc4ae861
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 1%

---

# 3.3.3 Konfigurieren einer Kampagne mit In-App-Nachrichten

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## Konfiguration 3.3.3.1 In-App-Nachrichtenkanals

Gehen Sie im linken Menü zu **Kanäle** und wählen Sie dann **Kanalkonfigurationen** aus. Klicken Sie **Kanalkonfiguration erstellen**.

![InApp](./images/inapp1.png)

Geben Sie den Namen ein: `--aepUserLdap--_In-app_Messages`, wählen Sie den Kanal **In-App-** aus und aktivieren Sie dann die Plattformen **Web**, **iOS** und **Android**.

![InApp](./images/inapp2.png)

Scrollen Sie nach unten. Sie sollten dann Folgendes sehen.

![InApp](./images/inapp3.png)

Stellen Sie sicher **dass „Einzelne Seite** aktiviert ist.

Geben Sie **Web** die URL der Website ein, die zuvor als Teil des Moduls **Erste Schritte** erstellt wurde. Sie sieht wie folgt aus: `https://dsn.adobe.com/web/--aepUserLdap---XXXX`. Vergessen Sie nicht, den **XXXX** in den eindeutigen Code Ihrer Website zu ändern.

Geben Sie für &lbrace;0 **iOS** und **Android** ein.`com.adobe.dsn.dxdemo`

![InApp](./images/inapp4.png)

Scrollen Sie nach oben und klicken Sie auf **Absenden**.

![InApp](./images/inapp5.png)

Ihre Kanalkonfiguration kann jetzt verwendet werden.

![InApp](./images/inapp6.png)

## 3.3.3.2 Konfigurieren einer geplanten Kampagne für In-App-Nachrichten

Gehen Sie im linken Menü zu **Kampagnen** und klicken Sie dann auf **Kampagne erstellen**.

![InApp](./images/inapp7.png)

Wählen Sie **Geplant - Marketing** und klicken Sie dann auf **Erstellen**.

![InApp](./images/inapp8.png)

Geben Sie den `--aepUserLdap-- - CitiSignal Fiber Max` ein und klicken Sie dann auf **Aktionen**.

![InApp](./images/inapp9.png)

Klicken Sie auf **+ Aktion** und wählen Sie dann **In-App-Nachricht** aus.

![InApp](./images/inapp10.png)

Wählen Sie die Konfiguration des In-App-Nachrichtenkanals aus, die Sie im vorherigen Schritt erstellt haben und die folgendermaßen lautet: `--aepUserLdap--_In-app_Messages`. Klicken Sie auf **Inhalt bearbeiten**.

![InApp](./images/inapp11.png)

Sie sollten das dann sehen. Klicken Sie auf **Modal**.

![InApp](./images/inapp12.png)

Klicken Sie **Layout ändern**.

![InApp](./images/inapp13.png)

Klicken Sie auf das **Medien-URL**-Symbol, um Assets aus AEM Assets auszuwählen.

![InApp](./images/inapp14.png)

Gehen Sie zum Ordner **Citisignal-images** und wählen Sie die Bilddatei **neon-rabbit.jpg** aus. Klicken Sie auf **Auswählen**.

![InApp](./images/inapp15.png)

Verwenden Sie für **Text** Kopfzeile): `CitiSignal Fiber Max`.
Verwenden Sie für **Text** Hauptteil): `Conquer lag with Fiber Max`.

![InApp](./images/inapp16.png)

Legen Sie den **#1-Text** auf `Go to Plans` fest.
Legen Sie die **Ziel** auf `com.adobe.dsn.dxdemo://plans` fest.

Klicken Sie auf **Zum Aktivieren überprüfen**.

![InApp](./images/inapp17.png)

Klicken Sie **Aktivieren**.

![InApp](./images/inapp18.png)

Der Status Ihrer Kampagne ist jetzt auf &quot;**&quot;**. Es kann einige Minuten dauern, bevor die Kampagne live ist.

![InApp](./images/inapp19.png)

Sobald der Status auf &quot;**&quot; geändert wurde** können Sie Ihre Kampagne testen.

![InApp](./images/inapp20.png)

## 3.3.3.3 Testen der In-App-Messaging-Kampagne auf einem Mobilgerät

Öffnen Sie die App auf Ihrem Mobilgerät. Nach dem Starten der App sollte dann die neue In-App-Nachricht angezeigt werden. Klicken Sie auf die Schaltfläche **Zu Plänen wechseln**.

![InApp](./images/inapp21.png)

Sie werden dann zur Seite &quot;**&quot;**.

![InApp](./images/inapp22.png)

## Nächste Schritte

Wechseln Sie zu [Zusammenfassung und Vorteile](./summary.md){target="_blank"}

Zurück zu [Adobe Journey Optimizer: Push- und In-App-Nachrichten](ajopushinapp.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
