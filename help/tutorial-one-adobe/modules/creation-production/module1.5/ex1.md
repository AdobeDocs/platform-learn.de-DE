---
title: Erste Schritte mit Frame.io
description: Erste Schritte mit Frame.io
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
source-git-commit: efb4ecf90a27d00d256c1648e78c6e295199733e
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# 1.5.1 Erste Schritte mit Frame.io

>[!NOTE]
>
> Der folgende Screenshot zeigt, wie eine bestimmte Umgebung verwendet wird. Wenn Sie dieses Tutorial durchlaufen, hat Ihre Umgebung höchstwahrscheinlich einen anderen Namen. Wenn Sie sich für dieses Tutorial angemeldet haben, wurden Ihnen die zu verwendenden Umgebungsdetails zur Verfügung gestellt. Befolgen Sie bitte diese Anweisungen.

Navigieren Sie zu [https://next.frame.io/](https://next.frame.io/). Stellen Sie sicher, dass Sie bei der `--aepImsOrgName--` der Umgebung angemeldet sind.

![Frame.io](./images/frameio1.png)

Falls Sie nicht in der rechten Umgebung angemeldet sind, klicken Sie auf das Logo in der linken unteren Ecke und wählen Sie die gewünschte Umgebung aus.

![Frame.io](./images/frameio2.png)

## 1.5.1.1 Erstellen von Arbeitsbereich und Projekt

Klicken Sie auf **+ Neue Workspace**.

![Frame.io](./images/frameio3.png)

Für den Workspace-Namen verwenden Sie: `--aepUserLdap--`. Klicken Sie auf **Speichern**.

![Frame.io](./images/frameio4.png)

Ihr Arbeitsbereich wurde erstellt. Als Nächstes sollten Sie ein neues Projekt erstellen. Klicken Sie auf **+ Neues Projekt**.

![Frame.io](./images/frameio5.png)

Wählen Sie **Leer** aus und verwenden Sie den Namen `CitiSignal`. Klicken Sie **Neues Projekt erstellen**.

![Frame.io](./images/frameio6.png)

Ihr Projekt ist jetzt erstellt. Jetzt müssen Sie Assets in Ihr Projekt hochladen. Klicken Sie **Hochladen**.

![Frame.io](./images/frameio7.png)

Laden Sie diese Dateien: [https://tech-insiders.s3.us-west-2.amazonaws.com/Frame.io_Assets.zip](https://tech-insiders.s3.us-west-2.amazonaws.com/Frame.io_Assets.zip) auf Ihren Desktop herunter und entpacken Sie sie auf Ihren Desktop.

![Frame.io](./images/frameio8.png)

Wählen Sie alle Dateien aus und klicken Sie auf **Öffnen**.

>[!NOTE]
>
>Wie Sie im Screenshot sehen können, ist der Ordner **Soundeffekte** derzeit nicht ausgewählt. Dies liegt daran, dass der manuelle Upload das Hochladen von Ordnern nicht unterstützt. In wenigen Minuten installieren Sie die Frame.io Transfer App, mit der Sie diesen Ordner und seine Dateien hochladen.

![Frame.io](./images/frameio9.png)

Nach einigen Minuten werden Ihre Dateien in Frame.io verfügbar.

![Frame.io](./images/frameio10.png)

Sie haben jetzt Dateien manuell hochgeladen, aber es gibt eine bessere und schnellere Möglichkeit, Dateien in und von Frame.io hochzuladen und herunterzuladen. Die beste Möglichkeit, dies zu tun, besteht in der Verwendung der Frame.io Transfer App.

## 1.5.1.2 Herunterladen und Konfigurieren der Frame.io-Transfer-App

Wechseln Sie zu [https://frame.io/transfer](https://frame.io/transfer) und laden Sie die Version für Ihren Computer herunter.

![Frame.io](./images/frameio11.png)

Installieren Sie die Anwendung und öffnen Sie sie dann.

![Frame.io](./images/frameio12.png)

Beim Öffnen der Anwendung müssen Sie sich anmelden. Klicken Sie **Anmelden**.

![Frame.io](./images/frameio13.png)

Geben Sie die E-Mail-Adresse Ihres Adobe-Kontos ein und klicken Sie **Los**.

![Frame.io](./images/frameio14.png)

Klicken Sie nach erfolgreicher Authentifizierung auf **Frame.io Transfer App öffnen**.

![Frame.io](./images/frameio15.png)

Sie sollten das dann sehen. Um die richtige Umgebung auszuwählen, klicken Sie auf , um die Dropdown-Liste zu öffnen.

![Frame.io](./images/frameio16.png)

Wählen Sie die Umgebung aus, die Sie für dieses Tutorial verwenden müssen, das `--aepImsOrgName--` ist.

![Frame.io](./images/frameio17.png)

Anschließend sollten der zuvor erstellte Arbeitsbereich und das Projekt sowie die Dateien angezeigt werden, die Sie manuell hochgeladen haben.

Klicken Sie **Hochladen**.

![Frame.io](./images/frameio18.png)

Wechseln Sie zu dem zuvor verwendeten Ordner, der die zuvor heruntergeladenen entpackten Dateien enthält. Wählen Sie den Ordner **Soundeffekte** und klicken Sie auf **Hochladen**.

![Frame.io](./images/frameio19.png)

Ihre Dateien werden dann hochgeladen.

![Frame.io](./images/frameio20.png)

Nach dem Hochladen wird der neue Ordner in Frame.io verfügbar.

![Frame.io](./images/frameio21.png)

## 1.5.1.3 Einrichten von Adobe Premiere Pro Beta

Sie haben Adobe Premiere Pro Beta bereits als Teil des Moduls Erste Schritte installiert. Um Frame.io in Kombination mit Adobe Premiere Pro Beta zu nutzen, können Sie das für diese Integration entwickelte Plugin nutzen.

Öffnen Sie die Creative Cloud-App und suchen Sie nach `frame.io`.

![Frame.io](./images/frameio23.png)

Scrollen Sie in den Suchergebnissen nach unten, um das Plug-in **Frame.io V4-Kommentare** zu finden. Klicken Sie darauf.

![Frame.io](./images/frameio24.png)

Sie sollten das dann sehen. Klicken Sie auf **Installieren**.

![Frame.io](./images/frameio25.png)

Wenn Adobe Premiere Pro Beta geöffnet ist, müssen Sie **Schließen** bevor Sie das Plug-in installieren können.

![Frame.io](./images/frameio26.png)

Klicken Sie auf **OK**. Das Plug-in wird jetzt installiert.

![Frame.io](./images/frameio27.png)

Öffnen Sie nach der Installation des Plug-ins Adobe Premiere Pro Beta auf Ihrem Computer.

![Frame.io](./images/frameio22.png)

## Nächste Schritte

Gehe zu [-](./ex1.md){target="_blank"}

Gehen Sie zurück zu [Optimieren Sie Ihren Workflow mit Frame.io](./frameio.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
