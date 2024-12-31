---
title: Bootcamp - Mischung aus physischem und digitalem - Journey testen
description: Bootcamp - Mischung aus physischem und digitalem - Journey testen
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: 45c77177-9ea9-4c3d-a40e-c04a747938eb
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# 3.4 Journey testen

Um Ihren Journey zu testen, müssen Sie die Ereignis-ID des Ereignisses verwenden, das Sie in Übung 3.2 erstellt haben. Das sieht wie folgt aus.

![ACOP](./images/payloadeventID.png)

Die Ereignis-ID ist das, was an Adobe Experience Platform gesendet werden muss, um die Journey zum Trigger zu bringen. In diesem Beispiel lautet die eventID:
`e76c0bf0c77c3517e5b6f4c457a0754ebaf5f1f6b9357d74e0d8e13ae517c3d5`.

Öffnen Sie die Mobile App und gehen Sie auf die Homepage. Klicken Sie auf **Symbol** Einstellungen“.

![DSN](./images/appsett.png)

Fügen Sie Ihre eventID in das Feld **Beacon EventID** ein und klicken Sie auf **Speichern**.

![DSN](./images/beacon1.png)

Bevor Sie fortfahren, öffnen Sie diese Webseite auf Ihrem Computer: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html)

Sie sehen dann Folgendes:

![DSN](./images/screen1.png)

Gehen Sie dann zurück zur Homepage. Klicken Sie auf das **Beacon**-Symbol.

![DSN](./images/app23.png)

Sie werden es dann sehen. Wählen Sie zunächst **Bootcamp Screen Beacon** und klicken Sie dann auf die **entry**-Schaltfläche. Auf diese Weise können Sie einen Beacon-Eintrag simulieren.

![DSN](./images/app21.png)

Sehen Sie sich jetzt den Bildschirm „In-Store“ an. Dort wird das zuletzt angezeigte Produkt innerhalb von 5 Sekunden angezeigt.

![DSN](./images/beacon3.png)

Außerdem haben Sie Ihre Push-Benachrichtigung erhalten.

![DSN](./images/beacon2.png)

Sie haben jetzt diese Übung beendet.

[Zurück zu Benutzerfluss 3](./uc3.md)

[Zurück zu „Alle Module“](../../overview.md)
