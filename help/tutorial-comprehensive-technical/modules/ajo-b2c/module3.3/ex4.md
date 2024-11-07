---
title: Offer decisioning - Testen Sie Ihre Entscheidung mithilfe der Demowebsite.
description: Testen Sie Ihre Entscheidung mithilfe der Demo-Website.
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 3%

---

# 3.3.4 Adobe Target und Offer decisioning kombinieren

## 3.3.4.1 Abruf des freigebbaren Links Ihres Demoprojekts

Um das Demo-Website-Projekt in Adobe Target zu laden, müssen Sie zunächst einen speziellen Link erfassen, über den Adobe Target Ihr Demo-Website-Projekt laden kann.

Gehen Sie dazu zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![RTCDP](./images/builder1.png)

Das wirst du jetzt sehen. Klicken Sie auf **Freigabe**.

![RTCDP](./images/builder2.png)

Klicken Sie auf **Link erzeugen** und kopieren Sie dann den Link in die Zwischenablage.

![RTCDP](./images/builder3.png)

Gehen Sie zu [https://bitly.com](https://bitly.com), fügen Sie den kopierten Link ein und klicken Sie auf **Kürzen**. Sie erhalten jetzt einen gekürzten Link, der wie folgt aussieht: `https://bit.ly/3JxN7aG`. Sie werden diesen Link in der nächsten Übung benötigen.

![RTCDP](./images/builder4.png)

## 3.3.4.2 Sammlung

Gehen Sie jetzt zur Adobe Experience Cloud-Homepage, indem Sie zu [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/) navigieren. Klicken Sie auf **Ziel**.

![RTCDP](./../../../modules/rtcdp-b2c/module2.3/images/excl.png)

Auf der Startseite von **Adobe Target** werden alle vorhandenen Aktivitäten angezeigt.

![RTCDP](./../../../modules/rtcdp-b2c/module2.3/images/exclatov.png)

Klicken Sie auf **+ Aktivität erstellen** , um eine neue Aktivität zu erstellen.

![RTCDP](./../../../modules/rtcdp-b2c/module2.3/images/exclatcr.png)

Wählen Sie **Erlebnis-Targeting** aus.

![RTCDP](./images/exclatcrxt.png)

Wählen Sie nun **Visual** aus und fügen Sie den gekürzten Link in das Feld **Aktivitäts-URL eingeben** ein. Klicken Sie auf **Weiter**.

![RTCDP](./images/exclatcrxt1.png)

Anschließend sehen Sie, wie Ihr Demowebsite-Projekt in den Visual Experience Composer geladen wird.

![RTCDP](./images/vec1.png)

Wechseln Sie zum Modus **Durchsuchen** , um im Popup für Cookie-Zustimmung auf **Alle erlauben** zu klicken.

![RTCDP](./images/vec2.png)

Klicken Sie auf den Bereich, der den Text **Vorgestellte Kategorien** enthält. Klicken Sie auf **Einfügen vor** und wählen Sie dann **Angebotsentscheidung** aus.

![RTCDP](./images/vec3.png)

Dann sehen Sie dieses Popup. Wählen Sie Ihre Sandbox `--aepSandboxId--` und dann die Platzierung **Web - Bild** aus.

![RTCDP](./images/vec4.png)

Wählen Sie anschließend Ihre Entscheidung `--demoProfileLdap-- - Luma Decision` aus. Klicken Sie auf **Speichern**.

![RTCDP](./images/vec5.png)

Dann wirst du das sehen. Stellen Sie sicher, dass die zusätzliche Vorlagenregel **URL** **enthält** **Ihren Projektnamen** enthält. Klicken Sie auf **Speichern**.

![RTCDP](./images/vec6.png)

Dann wirst du das sehen. Klicken Sie auf **Weiter**.

![RTCDP](./images/vec7.png)

Geben Sie einen Namen für Ihr Angebot ein und verwenden Sie folgenden Namen: `--demoProfileLdap-- - XT with Offers (VEC)`. Klicken Sie auf **Weiter**.

![RTCDP](./images/vec8.png)

Dann wirst du das sehen. Definieren Sie Ihre **Zielmetrik** wie angegeben. Klicken Sie auf **Speichern und schließen**.

![RTCDP](./images/vec9.png)

Ihr Angebot wird jetzt erstellt und veröffentlicht.

![RTCDP](./images/vec10.png)

Sobald Ihr Angebot veröffentlicht wurde, können Sie es aktivieren.

Nächster Schritt: [3.3.5 Verwenden Sie Ihre Entscheidung in einer E-Mail und SMS](./ex5.md)

[Zurück zu Modul 3.3](./offer-decisioning.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
