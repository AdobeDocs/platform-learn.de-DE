---
title: AEM CS - Erstellen einer dokumentbasierten Website
description: AEM CS - Erstellen einer dokumentbasierten Website
kt: 5342
doc-type: tutorial
exl-id: db366111-3873-4504-95f1-b240836c833f
source-git-commit: dd075b0296c6ba06d72b229145635060c2c6abb1
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 1%

---

# 1.1.2 Erstellen einer dokumentbasierten Website

Während Sie auf die Erstellung Ihres Cloud Manager-Programms warten, haben Sie genügend Zeit, um Ihre erste dokumentbasierte Authoring-Website einzurichten. Die folgende Übung basiert auf dem [aem.live-Entwickler-Tutorial](https://www.aem.live/developer/tutorial){target="_blank"}. Gehen Sie wie folgt vor, um zu beginnen.

## 1.1.2.1 Einrichten des Google-Laufwerks

Navigieren Sie zu [https://drive.google.com](https://drive.google.com){target="_blank"}. Klicken Sie auf **+ Neu** dann auf **Neuer Ordner**.

![AEMCS](./images/googledrive1.png){zoomable="yes"}

Benennen Sie den Ordner `aemdocb-test`. Klicken Sie auf **Erstellen**.

![AEMCS](./images/googledrive2.png){zoomable="yes"}

Laden Sie die Datei [aemboilerplate.zip](./../../../assets/aem/aemboilerplate.zip){target="_blank"} herunter und extrahieren Sie sie auf Ihrem Computer.

![AEMCS](./images/googledrive3.png){zoomable="yes"}

In diesem Ordner werden 3 Dateien angezeigt. Kopieren Sie diese Dateien in den neuen Google Drive-Ordner.

![AEMCS](./images/googledrive4.png){zoomable="yes"}

Jetzt müssen Sie diese Dateien in eine native Google-Datei konvertieren. Öffnen Sie dazu jede Datei und navigieren Sie zu **Datei** > **Als Google Docs speichern**.

![AEMCS](./images/googledrive5.png){zoomable="yes"}

Dies sollten Sie für alle drei Dateien tun. Danach werden 6 Dateien in Ihrem Google Drive-Ordner angezeigt.

![AEMCS](./images/googledrive6.png){zoomable="yes"}

Sie haben dies dann in Ihrem Ordner.

![AEMCS](./images/googledrive7.png){zoomable="yes"}

Damit die dokumentbasierte Authoring-Demo funktioniert, müssen Sie jetzt Ihren Google Drive-Ordner mit der E-Mail-Adresse **helix@adobe.com** freigeben. Klicken Sie auf Ihren Ordnernamen, klicken Sie auf **Freigeben** und klicken Sie dann erneut **Freigeben**.

![AEMCS](./images/googledrive8.png){zoomable="yes"}

helix@adobe.com Geben Sie die E-Mail-Adresse **&#x200B;**&#x200B;ein und klicken Sie auf **Senden**.

![AEMCS](./images/googledrive9.png){zoomable="yes"}

Kopieren Sie als Nächstes die URL Ihres Google Drive-Ordners und schreiben Sie sie auf, da Sie sie in der nächsten Übung benötigen werden. Klicken Sie auf den Ordnernamen, auf **Freigeben** und dann auf **Link kopieren**.

![AEMCS](./images/googledrive10.png){zoomable="yes"}

`https://drive.google.com/drive/folders/1PNIOFeptIfszSebawT-Y_bwB4_anQWk5?usp=drive_link`

Sie sollten den Abfragezeichenfolgenparameter `?usp=drive_link` entfernen, sodass die URL wie folgt aussehen sollte:

`https://drive.google.com/drive/folders/1PNIOFeptIfszSebawT-Y_bwB4_anQWk5`

## 1.1.2.2 Einrichten des GitHub-Repositorys

Navigieren Sie zu [https://github.com](https://github.com){target="_blank"}. Klicken Sie auf **Anmelden**.

![AEMCS](./images/aemcssetup1.png){zoomable="yes"}

Geben Sie Ihre Anmeldedaten ein. Klicken Sie auf **Anmelden**.

![AEMCS](./images/aemcssetup2.png){zoomable="yes"}

Nach der Anmeldung sehen Sie Ihr GitHub-Dashboard.

![AEMCS](./images/aemcssetup3.png){zoomable="yes"}

Navigieren Sie zu [https://github.com/adobe/aem-boilerplate](https://github.com/adobe/aem-boilerplate){target="_blank"}. Sie werden es dann sehen. Klicken Sie **Diese Vorlage verwenden** und anschließend auf **Neues Repository erstellen**.

![AEMCS](./images/aemdocbcssetup4.png){zoomable="yes"}

Für den **Repository-Namen** verwenden Sie `aemdocb-test`. Setzen Sie die Sichtbarkeit auf **Privat**. Klicken Sie **Repository erstellen**.

![AEMCS](./images/aemdocbcssetup5.png){zoomable="yes"}

Nach einigen Sekunden wird dann Ihr Repository erstellt.

![AEMCS](./images/aemdocbcssetup6.png){zoomable="yes"}

Navigieren Sie anschließend zu [https://github.com/apps/aem-code-sync](https://github.com/apps/aem-code-sync){target="_blank"}. Klicken Sie **Konfigurieren**.

![AEMCS](./images/aemcssetup7.png){zoomable="yes"}

Klicken Sie auf Ihr GitHub-Konto.

![AEMCS](./images/aemcssetup8.png){zoomable="yes"}

Klicken Sie **Nur Repositorys auswählen** und fügen Sie dann das soeben erstellte Repository hinzu. Klicken Sie anschließend auf **Installieren**.

![AEMCS](./images/aemdocbcssetup9.png){zoomable="yes"}

Sie erhalten dann diese Bestätigung.

![AEMCS](./images/aemcssetup10.png){zoomable="yes"}

## 1.1.2.3 Aktualisierungsdatei fstab.yaml

Klicken Sie in Ihrem GitHub-Repository auf , um die Datei `fstab.yaml` zu öffnen.

![AEMCS](./images/aemdocbcssetup11.png){zoomable="yes"}

Klicken Sie auf **Symbol** Bearbeiten“.

![AEMCS](./images/aemdocbcssetup12.png){zoomable="yes"}

Jetzt müssen Sie den Wert für das Feld (URL **in** 2 aktualisieren.

![AEMCS](./images/aemdocbcssetup13.png){zoomable="yes"}

Sie müssen den aktuellen Wert durch die URL Ihrer spezifischen AEM CS-Umgebung in Kombination mit den Einstellungen Ihres GitHub-Repositorys ersetzen.

Dies ist der aktuelle Wert der URL: `https://drive.google.com/drive/u/0/folders/1MGzOt7ubUh3gu7zhZIPb7R7dyRzG371j`.

Ersetzen Sie diesen Wert durch die URL, die Sie `https://drive.google.com/drive/folders/1PNIOFeptIfszSebawT-Y_bwB4_anQWk5` aus Ihrem Google-Laufwerksordner kopiert haben. Klicken Sie **Änderungen übernehmen…**.

![AEMCS](./images/aemdocbcssetup14.png){zoomable="yes"}

Klicken Sie **Änderungen übernehmen**.

![AEMCS](./images/aemdocbcssetup15.png){zoomable="yes"}

## 1.1.2.4 AEM Sidekick-Erweiterung installieren

Navigieren Sie zu [https://chromewebstore.google.com/detail/aem-sidekick/ccfggkjabjahcjoljmgmklhpaccedipo](https://chromewebstore.google.com/detail/aem-sidekick/ccfggkjabjahcjoljmgmklhpaccedipo){target="_blank"}. Klicken Sie **Zu Chrome hinzufügen**.

![AEMCS](./images/aemdocbcssetup16.png){zoomable="yes"}

Die Erweiterung **AEM Sidekick** anheften.

![AEMCS](./images/aemdocbcssetup17.png){zoomable="yes"}

## 1.1.2.5 Vorschau und Veröffentlichung der dokumentbasierten Website

Kehren Sie zu Ihrem Google Drive-Ordner zurück. Klicken Sie in der Taskleiste auf die Erweiterung **AEM Sidekick**. Anschließend wird ein Popup in der AEM Sidekick-Leiste in Ihrem Ordner angezeigt.

![AEMCS](./images/aemdocbcssetup18.png){zoomable="yes"}

Wählen Sie die drei Dateien in Ihrem Google Drive-Ordner aus. Klicken Sie auf **Vorschau**.

![AEMCS](./images/aemdocbcssetup19.png){zoomable="yes"}

Klicken **erneut auf** Vorschau“.

![AEMCS](./images/aemdocbcssetup20.png){zoomable="yes"}

Klicken, um das grüne Dialogfeld zu schließen.

![AEMCS](./images/aemdocbcssetup21.png){zoomable="yes"}

Wählen Sie die drei Dateien in Ihrem Google Drive-Ordner erneut aus. Klicken Sie jetzt auf **Veröffentlichen**.

![AEMCS](./images/aemdocbcssetup22.png){zoomable="yes"}

Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/aemdocbcssetup23.png){zoomable="yes"}

Klicken, um das grüne Dialogfeld wieder zu schließen. Wählen Sie nun die Datei **index**, klicken Sie auf **URLs kopieren** und klicken Sie dann auf **Live-URLs kopieren**.

![AEMCS](./images/aemdocbcssetup24.png){zoomable="yes"}

Die kopierte URL sieht wie folgt aus: `https://main--aemdocb-test--woutervangeluwe.aem.live/`.

In der obigen URL:

- **main** bezieht sich auf die Verzweigung in Ihrem GitHub-Repository
- **aemdocb-test** bezieht sich auf den GitHub-Repository-Namen
- **wouterVangeluwe** bezieht sich auf den Namen des GitHub-Benutzerkontos
- **.live:** auf die Live-Umgebung Ihrer AEM-Instanz
- Sie können **.live** durch **.page ersetzen** um die Vorschauumgebung Ihrer AEM-Instanz zu öffnen

Öffnen Sie ein neues Browser-Fenster und navigieren Sie zur URL.

![AEMCS](./images/aemdocbcssetup25.png){zoomable="yes"}

## 1.1.2.6 Nehmen Sie eine Änderung vor und veröffentlichen Sie Ihre Änderung

Kehren Sie zu Ihrem Google-Laufwerk zurück und öffnen Sie den Filter **index** in Google.

![AEMCS](./images/aemdocbcssetup27.png){zoomable="yes"}

Ersetzen Sie den **Test** durch einen beliebigen anderen Text. Klicken Sie auf **Vorschau**.

![AEMCS](./images/aemdocbcssetup28.png){zoomable="yes"}

Die Vorschauversion Ihrer Website wird dann geöffnet. Überprüfen Sie Ihre Änderung und klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/aemdocbcssetup29.png){zoomable="yes"}

Anschließend wird die Live-Version Ihrer Website angezeigt.

![AEMCS](./images/aemdocbcssetup30.png){zoomable="yes"}

Die obige Übung war eine gute Möglichkeit, um loszulegen und das dokumentenbasierte Authoring selbst zu erleben. Sie können jetzt mit der nächsten Übung fortfahren, in der Sie Ihre eigene Demo-Website mit CitiSignal als Demo-Marke einrichten.

Nächster Schritt: [1.1.3 Einrichten der AEM CS-Umgebung](./ex3.md){target="_blank"}

Zurück zu [Adobe Experience Manager Cloud Service und Edge Delivery Services](./aemcs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
