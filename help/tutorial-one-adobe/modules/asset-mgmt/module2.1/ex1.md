---
title: Erstellen des Cloud Manager-Programms
description: Erstellen des Cloud Manager-Programms
kt: 5342
doc-type: tutorial
exl-id: fda247eb-1865-4936-b46e-84128ccab357
source-git-commit: 7384eabe00354374f7012be10c24870c68ea7f2c
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 3%

---

# 1.1.1 Cloud Manager-Programm erstellen

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Die gewünschte Organisation ist `--aepImsOrgName--`. Sie werden dann so etwas sehen. Klicken Sie **Programm hinzufügen**.

![AEMCS](./images/aemcs1.png)

Verwenden Sie für **Programmnamen** &quot;`--aepUserLdap-- - CitiSignal AEM+ACCS`&quot;. Wählen Sie die Option **Einrichten einer Sandbox**. Klicken Sie auf **Fortfahren**.

![AEMCS](./images/aemcs2.png)

Stellen Sie sicher, dass die folgenden Optionen ausgewählt sind:

- Sites
- Formulare
- Assets

Klicken Sie auf den Pfeil für **Assets**, um die Optionsliste zu öffnen.

![AEMCS](./images/aemcs3.png)

Stellen Sie sicher, dass die folgenden Optionen ausgewählt sind:

- Content Hub

Scrollen Sie in der Liste nach unten.

![AEMCS](./images/aemcs3a.png)

Stellen Sie sicher, dass die folgenden Optionen ausgewählt sind:

- Edge-Bereitstellungsdienste
- Dynamic Media

Klicken Sie auf **Erstellen**.

![AEMCS](./images/aemcs3b.png)

Das Erstellen Ihrer Umgebung dauert einige Zeit, 10-20mins.

![AEMCS](./images/aemcs4.png)

Sobald die Umgebungen erstellt und einsatzbereit sind, erhalten Sie eine E-Mail-Bestätigung, nach der Sie hierher zurückkehren können.

![AEMCS](./images/aemcs5.png)

Nachdem Sie Ihre E-Mail-Bestätigung erhalten haben, gehen Sie zurück zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Anschließend sehen Sie, dass der Status Ihres Programms in &quot;**&quot;** wurde. Klicken Sie auf das Programm, um es zu öffnen.

![AEMCS](./images/aemcs6.png)

Sehen Sie sich die Registerkarte **Pipelines** an. Klicken Sie auf die 3 Punkte **…** und dann auf **Ausführen**.

![AEMCS](./images/aemcs7.png)

Klicken Sie auf **Ausführen**.

![AEMCS](./images/aemcs8.png)

Klicken Sie anschließend auf der Registerkarte **Umgebungen** auf die **mit den drei Punkten** und anschließend auf **Details anzeigen**.

![AEMCS](./images/aemcs9.png)

Anschließend werden die Details Ihrer Umgebung angezeigt, einschließlich der URL Ihrer **Author**-Umgebung, die Sie in der nächsten Übung benötigen.

Sehen Sie sich die Zeile **Content Hub** an und wählen Sie **Zum Aktivieren klicken**.

![AEMCS](./images/aemcs10.png)

Klicken Sie **Aktivieren**.

![AEMCS](./images/aemcsact1.png)

Die Aktivierung von **&#x200B;**&#x200B;Content Hub&quot; wurde jetzt gestartet. Dies kann 10 Minuten oder länger dauern.

![AEMCS](./images/aemcsact2.png)

Nach etwa 10 Minuten wird **Content Hub** aktiviert.
Sehen Sie sich als Nächstes die Zeile **Dynamic Media** an und wählen Sie **Zum Aktivieren klicken** aus.

![AEMCS](./images/aemcsact3.png)

Klicken Sie **Aktivieren**.

![AEMCS](./images/aemcsact4.png)

**Dynamic Media**-Aktivierung wurde jetzt gestartet. Dies kann 10 Minuten oder länger dauern.

![AEMCS](./images/aemcsact5.png)

Nach etwa 10 Minuten erfolgt die Aktivierung **Dynamic Media**.

![AEMCS](./images/aemcsact6.png)

Sobald die Pipeline-Ausführung abgeschlossen ist, können Sie mit der nächsten Übung fortfahren.

Nächster Schritt: [Einrichten der AEM CS-Umgebung](./ex2.md){target="_blank"}

Zurück zu [Adobe Experience Manager Cloud Service und Edge Delivery Services](./aemcs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
