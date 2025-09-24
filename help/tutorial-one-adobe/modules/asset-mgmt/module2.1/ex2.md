---
title: Einrichten der AEM CS-Umgebung
description: Einrichten der AEM CS-Umgebung
kt: 5342
doc-type: tutorial
exl-id: 62715072-0257-4d07-af1a-8becbb793459
source-git-commit: 15adbf950115f0b6bb6613e69a60b310f25de058
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 1%

---

# 1.1.2 Einrichten der AEM CS-Umgebung

## 1.1.2.1 Einrichten des GitHub-Repositorys

Navigieren Sie zu [https://github.com](https://github.com){target="_blank"}. Klicken Sie auf **Anmelden**.

![AEMCS](./images/aemcssetup1.png)

Geben Sie Ihre Anmeldedaten ein. Klicken Sie auf **Anmelden**.

![AEMCS](./images/aemcssetup2.png)

Nach der Anmeldung sehen Sie Ihr GitHub-Dashboard.

![AEMCS](./images/aemcssetup3.png)

Navigieren Sie zu [https://github.com/adobe-rnd/aem-boilerplate-xcom](https://github.com/adobe-rnd/aem-boilerplate-xcom){target="_blank"}. Sie werden es dann sehen. Klicken Sie **Diese Vorlage verwenden** und anschließend auf **Neues Repository erstellen**.

![AEMCS](./images/aemcssetup4.png)

Für den **Repository-Namen** verwenden Sie `citisignal-aem-accs`. Setzen Sie die Sichtbarkeit auf **Privat**. Klicken Sie **Repository erstellen**.

![AEMCS](./images/aemcssetup5.png)

Nach einigen Sekunden wird dann Ihr Repository erstellt.

![AEMCS](./images/aemcssetup6.png)

Navigieren Sie anschließend zu [https://github.com/apps/aem-code-sync](https://github.com/apps/aem-code-sync){target="_blank"}. Klicken Sie **Installieren** oder **Konfigurieren**.

![AEMCS](./images/aemcssetup7.png)

Klicken Sie auf **Schaltfläche &quot;**&quot; neben Ihrem GitHub-Benutzerkonto.

![AEMCS](./images/aemcssetup8.png)

Klicken Sie **Konfigurieren** neben Ihrem GitHub-Benutzerkonto auf.

![AEMCS](./images/aemcssetup8a.png)

Klicken Sie **Nur Repositorys auswählen** und fügen Sie dann das soeben erstellte Repository hinzu.

![AEMCS](./images/aemcssetup9.png)

Scrollen Sie nach unten und klicken Sie auf **Speichern**.

![AEMCS](./images/aemcssetup9a.png)

Sie erhalten dann diese Bestätigung.

![AEMCS](./images/aemcssetup10.png)

## 1.1.2.2 Aktualisierungsdatei fstab.yaml

Klicken Sie in Ihrem GitHub-Repository auf , um die Datei `fstab.yaml` zu öffnen.

![AEMCS](./images/aemcssetup11.png)

Klicken Sie auf **Symbol** Bearbeiten“.

![AEMCS](./images/aemcssetup12.png)

Jetzt müssen Sie den Wert für das Feld (URL **in** 3 aktualisieren.

![AEMCS](./images/aemcssetup13.png)

Sie müssen den aktuellen Wert durch die URL Ihrer spezifischen AEM Sites CS-Umgebung in Kombination mit den Einstellungen Ihres GitHub-Repositorys ersetzen.

Dies ist der aktuelle Wert der URL: `https://author-p130360-e1272151.adobeaemcloud.com/bin/franklin.delivery/adobe-rnd/aem-boilerplate-xcom/main`.

Es gibt drei Teile der URL, die aktualisiert werden müssen

`https://XXX/bin/franklin.delivery/YYY/ZZZ/main`

XXX sollte durch die URL Ihrer AEM CS-Autorenumgebung ersetzt werden.

JJJJ sollte durch Ihr GitHub-Benutzerkonto ersetzt werden.

ZZZ sollte durch den Namen des GitHub-Repositorys ersetzt werden, das Sie in der vorherigen Übung verwendet haben.

Die URL Ihrer AEM CS-Autorenumgebung finden Sie unter [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png)

Klicken Sie anschließend auf der Registerkarte **Umgebungen** auf die **mit den drei Punkten** und anschließend auf **Details anzeigen**.

![AEMCS](./images/aemcs9.png)

Anschließend werden die Details Ihrer Umgebung angezeigt, einschließlich der URL Ihrer **Author**-Umgebung. Kopieren Sie die URL.

![AEMCS](./images/aemcs10.png)

XXX = `author-p166717-e1786231.adobeaemcloud.com`

Den Namen des GitHub-Benutzerkontos finden Sie leicht in der URL Ihres Browsers. In diesem Beispiel ist der Name des Benutzerkontos `woutervangeluwe`.

JJJJ = `woutervangeluwe`

![AEMCS](./images/aemcs11.png)

Den GitHub-Repository-Namen finden Sie auch im Browser-Fenster, das Sie in GitHub geöffnet haben. In diesem Fall ist der Repository-Name `citisignal`.

ZZZ = `citisignal-aem-accs`

![AEMCS](./images/aemcs12.png)

Diese drei Werte zusammen führen zu dieser neuen URL, die im `fstab.yaml` konfiguriert werden muss.

`https://author-p166717-e1786231.adobeaemcloud.com/bin/franklin.delivery/woutervangeluwe/citisignal-aem-accs/main`

Klicken Sie **Änderungen übernehmen…**.

![AEMCS](./images/aemcs13.png)

Klicken Sie **Änderungen übernehmen**.

![AEMCS](./images/aemcs14.png)

Die Datei `fstab.yaml` wurde aktualisiert.

## 1.1.2.3 Hochladen von CitiSignal-Assets und -Sites

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png)

Klicken Sie anschließend auf die URL Ihrer Autorenumgebung.

![AEMCS](./images/aemcssetup18.png)

Klicken Sie **Mit Adobe anmelden**.

![AEMCS](./images/aemcssetup19.png)

Anschließend wird Ihre Autorenumgebung angezeigt.

![AEMCS](./images/aemcssetup20.png)

Ihre URL sieht dann wie folgt aus: `https://author-p166717-e1786231.adobeaemcloud.com/ui#/aem/aem/start.html?appId=aemshell`

Sie müssen jetzt auf die Umgebung **CRX Package Manager** von AEM zugreifen. Entfernen Sie dazu `ui#/aem/aem/start.html?appId=aemshell` aus der URL und ersetzen Sie sie durch `crx/packmgr`. Ihre URL sollte jetzt wie folgt aussehen:
`https://author-p166717-e1786231.adobeaemcloud.com/crx/packmgr`.
Drücken Sie **Eingabetaste**, um die Package Manager-Umgebung zu laden

![AEMCS](./images/aemcssetup22.png)

Klicken Sie anschließend auf **Paket hochladen**.

![AEMCS](./images/aemcssetup21.png)

Klicken Sie **Durchsuchen**, um das hochzuladende Paket zu suchen.

Das Paket, das hochgeladen werden soll, heißt **Citisignal-assets.zip** und kann hier heruntergeladen werden: [https://one-adobe-tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal_aem_accs.zip](https://one-adobe-tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal_aem_accs.zip){target="_blank"}.

![AEMCS](./images/aemcssetup23.png)

Wählen Sie die `citisignal_aem_accs.zip` aus und klicken Sie auf **Öffnen**.

![AEMCS](./images/aemcssetup24.png)

Klicken Sie anschließend auf **OK**.

![AEMCS](./images/aemcssetup25.png)

Das Paket wird dann hochgeladen. Klicken Sie anschließend auf **Installieren** auf dem soeben hochgeladenen Paket.

![AEMCS](./images/aemcssetup27.png)

Klicken Sie auf **Installieren**.

![AEMCS](./images/aemcssetup28.png)

Nach einigen Minuten wird Ihr Paket installiert.

![AEMCS](./images/aemcssetup29.png)

Sie können dieses Fenster jetzt schließen.

## 1.1.2.4 Veröffentlichen von CitiSignal-Assets

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Klicken Sie auf **Programm**, um es zu öffnen.

![AEMCS](./images/aemcs6.png)

Klicken Sie anschließend auf die URL Ihrer Autorenumgebung.

![AEMCS](./images/aemcssetup18.png)

Klicken Sie **Mit Adobe anmelden**.

![AEMCS](./images/aemcssetup19.png)

Anschließend wird Ihre Autorenumgebung angezeigt. Auf **Assets**.

![AEMCS](./images/aemcsassets1.png)

Klicken Sie auf **Dateien**.

![AEMCS](./images/aemcsassets2.png)

Klicken Sie auf den Ordner **CitiSignal** und dann auf **Veröffentlichung verwalten**.

![AEMCS](./images/aemcsassets3.png)

Klicken Sie auf **Weiter**.

![AEMCS](./images/aemcsassets4.png)

Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/aemcsassets5.png)

Ihre Assets wurden veröffentlicht.

## 1.1.2.5 Publish CitiSignal-Website

Klicken Sie auf den **Adobe Experience Manager**-Produktnamen oben links im Bildschirm und anschließend auf den **Pfeil** neben **Assets**.

![AEMCS](./images/aemcssetup30a.png)

Klicken Sie anschließend auf **Sites**.

![AEMCS](./images/aemcssetup30.png)

Sie sollten dann Ihre **CitiSignal**-Website sehen, die nach der Installation des Pakets erstellt wurde.

![AEMCS](./images/aemcssetup31.png)

Um Ihre Site mit dem zuvor erstellten GitHub-Repository zu verknüpfen, müssen Sie eine **Edge Delivery Services-Konfiguration erstellen**.

Der erste Schritt dazu besteht darin, eine **Cloud-Konfiguration** zu erstellen.

Klicken Sie dazu auf den **Adobe Experience Manager** Produktnamen oben links im Bildschirm, klicken Sie dann auf das Symbol **Tools** und wählen Sie dann **Allgemein** aus. Klicken, um **Konfigurationsbrowser** zu öffnen.

![AEMCS](./images/aemcssetup31a.png)

Sie sollten das dann sehen. Klicken Sie auf **Erstellen**

![AEMCS](./images/aemcssetup31b.png)

Legen Sie die Felder **Titel** und **Name** auf `CitiSignal` fest. Aktivieren Sie das Kontrollkästchen für **Cloud-Konfigurationen**.

Klicken Sie auf **Erstellen**.

![AEMCS](./images/aemcssetup31c.png)

Sie sollten dann diese haben.

![AEMCS](./images/aemcssetup31d.png)

Als Nächstes müssen Sie einige Felder der soeben erstellten **Cloud-Konfiguration** aktualisieren.

Klicken Sie dazu auf den **Adobe Experience Manager**-Produktnamen oben links im Bildschirm, klicken Sie dann auf das Symbol **Tools** und wählen Sie dann **Cloud Services** aus. Klicken, um **Edge Delivery Services-Konfiguration zu**.

![AEMCS](./images/aemcssetup32.png)

Wählen Sie **CitiSignal**, klicken Sie auf **Erstellen** und wählen Sie **Konfiguration**.

![AEMCS](./images/aemcssetup31e.png)

Füllen Sie jetzt die Felder **Organisation** und **Site-Name** aus. Sehen Sie sich dazu zunächst die URL Ihres GitHub-Repositorys an.

![AEMCS](./images/aemcssetup31f.png)

- **Organisation**: Verwenden Sie den Namen Ihrer GitHub-Organisation, in diesem Beispiel ist er `woutervangeluwe`
- **Site-Name**: Verwenden Sie den Namen des GitHub-Repositorys, der `citisignal-aem-accs` werden soll.

Klicken Sie **Speichern und schließen**.

![AEMCS](./images/aemcssetup33.png)

Sie sollten dann diese haben. Aktivieren Sie das Kontrollkästchen vor Ihrer neu erstellten Edge-Cloud-Konfiguration und klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/aemcssetup34.png)

## 1.1.2.6 Aktualisieren der Datei „pfads.json“

Klicken Sie in Ihrem GitHub-Repository auf , um die Datei `paths.json` zu öffnen.

![AEMCS](./images/aemcssetupjson1.png)

Klicken Sie auf **Symbol** Bearbeiten“.

![AEMCS](./images/aemcssetupjson2.png)

Aktualisieren Sie nun den `aem-boilerplate-commerce` durch `CitiSignal` ersetzen in den Zeilen 3, 4, 5, 6, 7 und 10.

Klicken Sie **Änderungen übernehmen**.

![AEMCS](./images/aemcssetupjson3.png)

Klicken Sie **Änderungen übernehmen**.

![AEMCS](./images/aemcssetupjson4.png)

Die Datei `paths.json` wurde aktualisiert.

## 1.1.2.7 Publish CitiSignal-Website

Klicken Sie auf den **Adobe Experience Manager**-Produktnamen oben links im Bildschirm und anschließend auf **Sites**.

![AEMCS](./images/aemcssetup38.png)

Klicken Sie anschließend auf das Kontrollkästchen vor **CitiSignal**. Klicken Sie dann auf **Veröffentlichung verwalten**.

![AEMCS](./images/aemcssetup39.png)

Klicken Sie auf **Weiter**.

![AEMCS](./images/aemcssetup40.png)

Klicken Sie auf **Untergeordnete Einstellungen einschließen**.

![AEMCS](./images/aemcssetup41.png)

Aktivieren Sie das Kontrollkästchen **Untergeordnete Elemente einbeziehen** und heben Sie dann die Auswahl der anderen Kontrollkästchen auf. Klicken Sie auf **OK**.

![AEMCS](./images/aemcssetup42.png)

Klicken Sie auf **Veröffentlichen**.

![AEMCS](./images/aemcssetup43.png)

Sie werden dann hierher zurückgeschickt. Klicken Sie auf **CitiSignal**, aktivieren Sie das Kontrollkästchen vor **index** und klicken Sie dann auf **Bearbeiten**.

![AEMCS](./images/aemcssetup44.png)

Ihre Website wird dann im **universellen Editor** geöffnet.

![AEMCS](./images/aemcssetup45.png)

Sie können nun auf Ihre Website zugreifen, indem Sie zu `main--citisignal-aem-accs--XXX.aem.page` und/oder `main--citisignal-aem-accs--XXX.aem.live` wechseln, nachdem Sie XXX durch Ihr GitHub-Benutzerkonto ersetzt haben, was in diesem Beispiel `woutervangeluwe` ist.

In diesem Beispiel lautet die vollständige URL wie folgt:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` und/oder `https://main--citisignal-aem-accs--woutervangeluwe.aem.live`.

Es kann einige Zeit dauern, bis alle Assets korrekt angezeigt werden, da sie zuerst veröffentlicht werden müssen.

Sie sehen dann Folgendes:

![AEMCS](./images/aemcssetup46.png)

## 1.1.2.8 der Testseitenleistung

Navigieren Sie zu [https://pagespeed.web.dev/](https://pagespeed.web.dev/){target="_blank"}. Geben Sie Ihre URL ein und klicken Sie auf **Analysieren**.

![AEMCS](./images/aemcssetup48.png)

Anschließend sehen Sie, dass Ihre Website sowohl in einer Mobile- als auch in einer Desktop-Visualisierung einen Highscore erhält:

**Mobil**:

![AEMCS](./images/aemcssetup49.png)

**Desktop**:

![AEMCS](./images/aemcssetup50.png)

Nächster Schritt: [Entwickeln eines benutzerdefinierten Blocks](./ex3.md){target="_blank"}

Zurück zu [Adobe Experience Manager Cloud Service und Edge Delivery Services](./aemcs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
