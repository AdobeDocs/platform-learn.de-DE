---
title: Offer decisioning - Testen Sie Ihre Entscheidung mithilfe der Demo-Website
description: Testen Sie Ihre Entscheidung mithilfe der Demo-Website
kt: 5342
doc-type: tutorial
exl-id: 5cc9f134-1434-4e76-9d26-9d73dbf6c0be
source-git-commit: fc24f3c9fb1683db35026dc53d0aaa055aa87e34
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 2%

---

# 3.3.4 Adobe Target und Offer decisioning kombinieren

## 3.3.4.1 Abruf des freigebbaren Links Ihres Demoprojekts

Um das Demo-Website-Projekt in Adobe Target zu laden, müssen Sie zunächst einen speziellen Link erfassen, über den Adobe Target Ihr Demo-Website-Projekt laden kann.

Navigieren Sie dazu zu [https://dsn.adobe.com/projects](https://builder.adobedemo.com/projects). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![RTCDP](./images/builder1.png)

Das wirst du jetzt sehen. Navigieren Sie zu **Freigeben**. Klicken Sie auf **Link erstellen** und kopieren Sie dann den Link in die Zwischenablage.

![RTCDP](./images/builder2.png)

Wechseln Sie zu [https://bitly.com](https://bitly.com), fügen Sie den kopierten Link ein und klicken Sie auf **Link erstellen**.

![RTCDP](./images/builder4.png)

Sie erhalten jetzt einen gekürzten Link, der wie folgt aussieht: `https://adobe.ly/3PpGcFk`. Sie benötigen diesen Link in der nächsten Übung.

![RTCDP](./images/builder5.png)

## 3.3.4.2

Rufen Sie jetzt die Adobe Experience Cloud-Homepage auf. Wechseln Sie dazu zu [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Klicken Sie auf **Target**.

![RTCDP](./../../../modules/rtcdp-b2c/module2.3/images/excl.png)

Auf der Startseite von {**}Adobe Target werden alle vorhandenen Aktivitäten angezeigt.** Klicken Sie auf **Aktivität erstellen** und dann auf **Erlebnis-Targeting**.

![RTCDP](./../../../modules/rtcdp-b2c/module2.3/images/exclatov.png)

Wählen Sie nun **Visual** und fügen Sie den gekürzten Link in das Feld **Enter Activity URL** ein. Klicken Sie auf **Erstellen**.

![RTCDP](./images/exclatcrxt1.png)

Anschließend wird Ihr Demo-Website-Projekt in Visual Experience Composer geladen.

>[!NOTE]
>
>Falls Ihre Website nicht korrekt geladen wird, installieren und aktivieren Sie diese Chrome-Erweiterung: **Adobe Target VEC Helper** über den Chrome Web Store, und versuchen Sie es dann erneut.

![RTCDP](./images/vec1.png)

Klicken Sie auf den Bereich, der das Disney+-Angebot enthält. Stellen Sie sicher, dass Sie den vollständigen **Container** auswählen. Klicken Sie **Einfügen vor** und wählen Sie dann **Angebotsentscheidung** aus.

![RTCDP](./images/vec3.png)

Dann sehen Sie dieses Popup. Wählen Sie Ihre Sandbox-`--aepSandboxName--` und dann die Platzierung **Web - Bild** aus.

![RTCDP](./images/vec4.png)

Wählen Sie als Nächstes Ihre `--aepUserLdap-- - CitiSignal Decision` aus. Klicken Sie auf **Speichern**.

![RTCDP](./images/vec5.png)

Sie werden es dann sehen. Klicken Sie **Regel überprüfen**.

![RTCDP](./images/vec5a.png)

Stellen Sie sicher, dass die zusätzliche Vorlagenregel **URL** **contains** **your-project-name**. Klicken Sie auf **Speichern**.

![RTCDP](./images/vec6.png)

Sie werden es dann sehen. Klicken Sie auf **Weiter**.

![RTCDP](./images/vec7.png)

Geben Sie einen Namen für Ihr Angebot ein. Verwenden Sie diesen Namen: `--aepUserLdap-- - XT with Offers (VEC)`. Klicken Sie auf **Weiter**.

![RTCDP](./images/vec8.png)

Sie werden es dann sehen. Definieren Sie **Zielmetrik** wie angegeben. Klicken Sie **Speichern und schließen**.

![RTCDP](./images/vec9.png)

Ihr Angebot wurde erstellt und wird veröffentlicht. Sobald Ihr Angebot veröffentlicht wurde, können Sie es aktivieren.

![RTCDP](./images/vec11.png)

Nächster Schritt: [3.3.5 Verwenden Sie Ihre Entscheidung in einer E-Mail und SMS](./ex5.md)

[Zurück zum Modul 3.3](./offer-decisioning.md)

[Zurück zu „Alle Module“](./../../../overview.md)
