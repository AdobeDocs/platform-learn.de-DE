---
title: Einrichten der AEM CS-Umgebung
description: Einrichten der AEM CS-Umgebung
kt: 5342
doc-type: tutorial
exl-id: 62715072-0257-4d07-af1a-8becbb793459
source-git-commit: 18151b91d18ebb53fc485151effd12a6fdc2b6b8
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 1%

---

# 2.1.3 Einrichten der AEM CS-Umgebung

## 2.1.3.1 Einrichten des GitHub-Repositorys

Navigieren Sie zu [https://github.com](https://github.com){target="_blank"}. Klicken Sie auf **Anmelden**.

![AEMCS](./images/aemcssetup1.png){zoomable="yes"}

Geben Sie Ihre Anmeldedaten ein. Klicken Sie auf **Anmelden**.

![AEMCS](./images/aemcssetup2.png){zoomable="yes"}

Nach der Anmeldung sehen Sie Ihr GitHub-Dashboard.

![AEMCS](./images/aemcssetup3.png){zoomable="yes"}

Navigieren Sie zu [https://github.com/AdobeDevXSC/citisignal-one](https://github.com/AdobeDevXSC/citisignal-one){target="_blank"}. Sie werden es dann sehen. Klicken Sie **Diese Vorlage verwenden** und anschließend auf **Neues Repository erstellen**.

![AEMCS](./images/aemcssetup4.png){zoomable="yes"}

Für den **Repository-Namen** verwenden Sie `citisignal`. Setzen Sie die Sichtbarkeit auf **Privat**. Klicken Sie **Repository erstellen**.

![AEMCS](./images/aemcssetup5.png){zoomable="yes"}

Nach einigen Sekunden wird dann Ihr Repository erstellt.

![AEMCS](./images/aemcssetup6.png){zoomable="yes"}

Navigieren Sie anschließend zu [https://github.com/apps/aem-code-sync](https://github.com/apps/aem-code-sync){target="_blank"}. Klicken Sie **Konfigurieren**.

![AEMCS](./images/aemcssetup7.png){zoomable="yes"}

Klicken Sie auf Ihr GitHub-Konto.

![AEMCS](./images/aemcssetup8.png){zoomable="yes"}

Klicken Sie **Nur Repositorys auswählen** und fügen Sie dann das soeben erstellte Repository hinzu. Klicken Sie anschließend auf **Installieren**.

![AEMCS](./images/aemcssetup9.png){zoomable="yes"}

Sie erhalten dann diese Bestätigung.

![AEMCS](./images/aemcssetup10.png){zoomable="yes"}

## 2.1.3.2 Aktualisierungsdatei fstab.yaml

Klicken Sie in Ihrem GitHub-Repository auf , um die Datei `fstab.yaml` zu öffnen.

![AEMCS](./images/aemcssetup11.png){zoomable="yes"}

Klicken Sie auf **Symbol** Bearbeiten“.

![AEMCS](./images/aemcssetup12.png){zoomable="yes"}

Jetzt müssen Sie den Wert für das Feld (URL **in** 4 aktualisieren.

![AEMCS](./images/aemcssetup13.png){zoomable="yes"}

Sie müssen den aktuellen Wert durch die URL Ihrer spezifischen AEM CS-Umgebung in Kombination mit den Einstellungen Ihres GitHub-Repositorys ersetzen.

Dies ist der aktuelle Wert der URL: `https://author-p131639-e1282833.adobeaemcloud.com/bin/franklin.delivery/adobedevxsc/citisignal-one/main`.

Es gibt drei Teile der URL, die aktualisiert werden müssen

`https://XXX/bin/franklin.delivery/YYY/ZZZ/main`

XXX sollte durch die URL Ihrer AEM CS Author-Umgebung ersetzt werden.

JJJJ sollte durch Ihr GitHub-Benutzerkonto ersetzt werden.

ZZZ sollte durch den Namen des GitHub-Repositorys ersetzt werden, das Sie in der vorherigen Übung verwendet haben.

Die URL Ihrer AEM CS-Autorenumgebung finden Sie unter [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Klicken Sie anschließend auf der Registerkarte **Umgebungen** auf die **mit den drei Punkten** und anschließend auf **Details anzeigen**.

![AEMCS](./images/aemcs9.png){zoomable="yes"}

Anschließend werden die Details Ihrer Umgebung angezeigt, einschließlich der URL Ihrer **Author**-Umgebung. Kopieren Sie die URL.

![AEMCS](./images/aemcs10.png){zoomable="yes"}

XXX = `author-p148073-e1511503.adobeaemcloud.com`

Den Namen des GitHub-Benutzerkontos finden Sie leicht in der URL Ihres Browsers. In diesem Beispiel ist der Name des Benutzerkontos `woutervangeluwe`.

JJJJ = `woutervangeluwe`

![AEMCS](./images/aemcs11.png){zoomable="yes"}

Den GitHub-Repository-Namen finden Sie auch im Browser-Fenster, das Sie in GitHub geöffnet haben. In diesem Fall ist der Repository-Name `citisignal`.

ZZZ = `citisignal`

![AEMCS](./images/aemcs12.png){zoomable="yes"}

Diese drei Werte zusammen führen zu dieser neuen URL, die im `fstab.yaml` konfiguriert werden muss.

`https://author-p148073-e1511503.adobeaemcloud.com/bin/franklin.delivery/woutervangeluwe/citisignal/main`

Klicken Sie **Änderungen übernehmen…**.

![AEMCS](./images/aemcs13.png){zoomable="yes"}

Klicken Sie **Änderungen übernehmen**.

![AEMCS](./images/aemcs14.png){zoomable="yes"}

Die Datei `fstab.yaml` wurde aktualisiert.

## 2.1.3.3 Hochladen von CitiSignal-Assets

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Klicken Sie anschließend auf die URL Ihrer Autorenumgebung.

![AEMCS](./images/aemcssetup18.png){zoomable="yes"}

Klicken Sie **Mit Adobe anmelden**.

![AEMCS](./images/aemcssetup19.png){zoomable="yes"}

Anschließend wird Ihre Autorenumgebung angezeigt.

![AEMCS](./images/aemcssetup20.png){zoomable="yes"}

Ihre URL sieht dann wie folgt aus: `https://author-p148073-e1511503.adobeaemcloud.com/ui#/aem/aem/start.html?appId=aemshell`

Sie müssen jetzt auf die Umgebung **CRX Package Manager** von AEM zugreifen. Entfernen Sie dazu `ui#/aem/aem/start.html?appId=aemshell` aus der URL und ersetzen Sie sie durch `crx/packmgr`. Ihre URL sollte jetzt wie folgt aussehen:
`https://author-p148073-e1511503.adobeaemcloud.com/crx/packmgr`.
Drücken Sie **Eingabetaste**, um die Package Manager-Umgebung zu laden

![AEMCS](./images/aemcssetup22.png){zoomable="yes"}

Klicken Sie anschließend auf **Paket hochladen**.

![AEMCS](./images/aemcssetup21.png){zoomable="yes"}

Klicken Sie **Durchsuchen**, um das hochzuladende Paket zu suchen.

Das Paket, das hochgeladen werden soll, heißt **Citisignal-assets.zip** und kann hier heruntergeladen werden: [https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip](https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip){target="_blank"}.

![AEMCS](./images/aemcssetup23.png){zoomable="yes"}

Wählen Sie das Paket aus und klicken Sie auf **Öffnen**.

![AEMCS](./images/aemcssetup24.png){zoomable="yes"}

Klicken Sie anschließend auf **OK**.

![AEMCS](./images/aemcssetup25.png){zoomable="yes"}

Das Paket wird dann hochgeladen.

![AEMCS](./images/aemcssetup26.png){zoomable="yes"}

Klicken Sie anschließend auf **Installieren** auf dem soeben hochgeladenen Paket.

![AEMCS](./images/aemcssetup27.png){zoomable="yes"}

Klicken Sie auf **Installieren**.

![AEMCS](./images/aemcssetup28.png){zoomable="yes"}

Nach einigen Minuten wird Ihr Paket installiert.

![AEMCS](./images/aemcssetup29.png){zoomable="yes"}

Sie können dieses Fenster jetzt schließen.


## 2.1.3.4 von Publish CitiSignal-Assets

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Klicken Sie anschließend auf die URL Ihrer Autorenumgebung.

![AEMCS](./images/aemcssetup18.png){zoomable="yes"}

Klicken Sie **Mit Adobe anmelden**.

![AEMCS](./images/aemcssetup19.png){zoomable="yes"}

Anschließend wird Ihre Autorenumgebung angezeigt. Klicken Sie auf **Sites**.

![AEMCS](./images/aemcsassets1.png){zoomable="yes"}

Klicken Sie auf **Dateien**.

![AEMCS](./images/aemcsassets2.png){zoomable="yes"}

Klicken Sie auf den Ordner **CitiSignal** und dann auf **Veröffentlichung verwalten**.

![AEMCS](./images/aemcsassets3.png){zoomable="yes"}

Klicken Sie auf **Weiter**.

![AEMCS](./images/aemcsassets4.png){zoomable="yes"}

Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/aemcsassets5.png){zoomable="yes"}

Ihre Assets wurden veröffentlicht.

## 2.1.3.5 Erstellen einer CitiSignal-Website

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Klicken Sie anschließend auf die URL Ihrer Autorenumgebung.

![AEMCS](./images/aemcssetup18.png){zoomable="yes"}

Klicken Sie **Mit Adobe anmelden**.

![AEMCS](./images/aemcssetup19.png){zoomable="yes"}

Anschließend wird Ihre Autorenumgebung angezeigt. Klicken Sie auf **Sites**.

![AEMCS](./images/aemcssetup30.png){zoomable="yes"}

Klicken Sie auf **Erstellen** und dann auf **Site aus Vorlage**.

![AEMCS](./images/aemcssetup31.png){zoomable="yes"}

Klicken Sie **Importieren**.

![AEMCS](./images/aemcssetup32.png){zoomable="yes"}

Sie müssen jetzt eine vorkonfigurierte Vorlage für Ihre Site importieren. Sie können die Vorlage ([) ](./../../../assets/aem/citisignal-edge-delivery-services-template-0.0.4.zip){target="_blank"}. Speichern Sie die Datei auf Ihrem Desktop.

Wählen Sie als Nächstes die `citisignal-edge-delivery-services-template-0.0.4.zip` aus und klicken Sie auf **Öffnen**.

![AEMCS](./images/aemcssetup33.png){zoomable="yes"}

Sie werden es dann sehen. Klicken Sie auf die gerade hochgeladene Vorlage, um sie auszuwählen, und klicken Sie dann auf **Weiter**.

![AEMCS](./images/aemcssetup34.png){zoomable="yes"}

Nun müssen Sie einige Details ausfüllen.

- Site-Titel: Verwenden **CitiSignal**
- Site-Name: verwenden **Citisignal-One**
- GitHub-URL: Kopieren Sie die URL des GitHub-Repositorys, das Sie zuvor verwendet haben

![AEMCS](./images/aemcssetup35.png){zoomable="yes"}

Dann hast du das hier. Klicken Sie auf **Erstellen**.

![AEMCS](./images/aemcssetup36.png){zoomable="yes"}

Ihre Site wird jetzt erstellt. Dies kann einige Minuten dauern. Klicken Sie auf **OK**.

![AEMCS](./images/aemcssetup37.png){zoomable="yes"}

Aktualisieren Sie Ihren Bildschirm nach einigen Minuten. Danach sehen Sie Ihre neu erstellte CitiSignal-Website.

![AEMCS](./images/aemcssetup38.png){zoomable="yes"}

## 2.1.3.6 Publish CitiSignal-Website

Klicken Sie anschließend auf das Kontrollkästchen vor **CitiSignal**. Klicken Sie dann auf **Veröffentlichung verwalten**.

![AEMCS](./images/aemcssetup39.png){zoomable="yes"}

Klicken Sie auf **Weiter**.

![AEMCS](./images/aemcssetup40.png){zoomable="yes"}

Klicken Sie auf **Untergeordnete Einstellungen einschließen**.

![AEMCS](./images/aemcssetup41.png){zoomable="yes"}

Aktivieren Sie das Kontrollkästchen **Untergeordnete Elemente einbeziehen** und heben Sie dann die Auswahl der anderen Kontrollkästchen auf. Klicken Sie auf **OK**.

![AEMCS](./images/aemcssetup42.png){zoomable="yes"}

Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/aemcssetup43.png){zoomable="yes"}

Sie werden dann hierher zurückgeschickt. Navigieren Sie **CitiSignal** > **us** > **en**. Aktivieren Sie das Kontrollkästchen vor **index** und klicken Sie dann auf **Bearbeiten**.

![AEMCS](./images/aemcssetup44.png){zoomable="yes"}

Ihre Website wird dann im **universellen Editor** geöffnet.

![AEMCS](./images/aemcssetup45.png){zoomable="yes"}

Sie können nun auf Ihre Website zugreifen, indem Sie zu `main--citisignal--XXX.aem.page/us/en` und/oder `main--citisignal--XXX.aem.live/us/en` wechseln, nachdem Sie XXX durch Ihr GitHub-Benutzerkonto ersetzt haben, was in diesem Beispiel `woutervangeluwe` ist.

In diesem Beispiel lautet die vollständige URL wie folgt:
`https://main--citisignal--woutervangeluwe.aem.page/us/en` und/oder `https://main--citisignal--woutervangeluwe.aem.live/us/en`.

Es kann einige Zeit dauern, bis alle Assets korrekt angezeigt werden, da sie zuerst veröffentlicht werden müssen.

Sie sehen dann Folgendes:

![AEMCS](./images/aemcssetup46.png){zoomable="yes"}

Nach einigen Minuten werden die Assets alle ordnungsgemäß geladen.

![AEMCS](./images/aemcssetup47.png){zoomable="yes"}

## 2.1.3.7 der Testseitenleistung

Navigieren Sie zu [https://pagespeed.web.dev/](https://pagespeed.web.dev/){target="_blank"}. Geben Sie Ihre URL ein und klicken Sie auf **Analysieren**.

![AEMCS](./images/aemcssetup48.png){zoomable="yes"}

Anschließend sehen Sie, dass Ihre Website sowohl in einer Mobile- als auch in einer Desktop-Visualisierung einen Highscore erhält:

**Mobil**:

![AEMCS](./images/aemcssetup49.png){zoomable="yes"}

**Desktop**:

![AEMCS](./images/aemcssetup50.png){zoomable="yes"}

Nächster Schritt: [2.1.4 Konfigurieren eines benutzerdefinierten Blocks](./ex4.md){target="_blank"}

[Zurück zum Modul 2.1](./aemcs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
