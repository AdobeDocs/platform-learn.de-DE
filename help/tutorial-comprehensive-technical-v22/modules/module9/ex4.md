---
title: offer decisioning - Testen Sie Ihre Entscheidung mithilfe der Demowebsite.
description: Testen Sie Ihre Entscheidung mithilfe der Demo-Website.
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: cdb2ba7d-bfc3-43ce-b9a1-1f0866322589
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 4%

---

# 9.4 Adobe Target und Offer decisioning kombinieren

## 9.4.1 Abruf des freigebbaren Links Ihres Demoprojekts

Um das Demo-Website-Projekt in Adobe Target zu laden, müssen Sie zunächst einen speziellen Link erfassen, über den Adobe Target Ihr Demo-Website-Projekt laden kann.

Gehen Sie dazu zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![RTCDP](./images/builder1.png)

Das wirst du jetzt sehen. Klicken Sie auf **Freigabe**.

![RTCDP](./images/builder2.png)

Klicken **Link generieren** und kopieren Sie dann den Link in die Zwischenablage.

![RTCDP](./images/builder3.png)

Navigieren Sie zu [https://bitly.com](https://bitly.com), fügen Sie den kopierten Link ein und klicken Sie auf **Kürzen**. Sie erhalten jetzt einen gekürzten Link, der wie folgt aussieht: `https://bit.ly/3JxN7aG`. Sie werden diesen Link in der nächsten Übung benötigen.

![RTCDP](./images/builder4.png)

## 9.4.2 Sammlung

Gehen Sie jetzt zur Adobe Experience Cloud-Homepage, indem Sie [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Klicken **Target**.

![RTCDP](../module6/images/excl.png)

Im **Adobe Target** Homepage werden Sie alle vorhandenen Aktivitäten sehen.

![RTCDP](../module6/images/exclatov.png)

Klicken **+ Aktivität erstellen** , um eine neue Aktivität zu erstellen.

![RTCDP](../module6/images/exclatcr.png)

Auswählen **Erlebnis-Targeting**.

![RTCDP](./images/exclatcrxt.png)

Jetzt auswählen **Visuell** und fügen Sie Ihren gekürzten Link in das Feld ein **Aktivitäts-URL eingeben**. Klicken Sie auf **Weiter**.

![RTCDP](./images/exclatcrxt1.png)

Anschließend sehen Sie, wie Ihr Demowebsite-Projekt in den Visual Experience Composer geladen wird.

![RTCDP](./images/vec1.png)

Navigieren Sie zu **Durchsuchen** Modus zum Klicken **Alle zulassen** im Popup für Cookie-Einwilligung.

![RTCDP](./images/vec2.png)

Klicken Sie auf den Bereich, der den Text enthält **Vorgestellte Kategorien**. Klicken **Einfügen vor** und wählen Sie **Angebotsentscheidung**.

![RTCDP](./images/vec3.png)

Dann sehen Sie dieses Popup. Sandbox auswählen `--aepSandboxId--` und wählen Sie dann die Platzierung aus **Web - Image**.

![RTCDP](./images/vec4.png)

Wählen Sie als Nächstes Ihre Entscheidung aus. `--demoProfileLdap-- - Luma Decision`. Klicken Sie auf **Speichern**.

![RTCDP](./images/vec5.png)

Dann wirst du das sehen. Stellen Sie sicher, dass Sie eine zusätzliche Vorlagenregel hinzufügen **URL** **contains** **your-project-name**. CLick **Speichern**.

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

Nächster Schritt: [9.5 Ihre Entscheidung in einer E-Mail und SMS verwenden](./ex5.md)

[Zurück zu Modul 9](./offer-decisioning.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
