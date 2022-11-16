---
title: Segmentaktivierung für Microsoft Azure Event Hub - Aktivieren des Segments
description: Segmentaktivierung für Microsoft Azure Event Hub - Aktivieren des Segments
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 250f8536-b6bd-4c64-a552-80d5c6fb6358
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 3%

---

# 13.4 Segment aktivieren

## 13.4.1 Segment zum Azure Event Hub-Ziel hinzufügen

In dieser Übung fügen Sie Ihr Segment hinzu `--demoProfileLdap-- - Interest in Equipment` auf `--demoProfileLdap---aep-enablement` Azure Event Hub-Ziel.

Melden Sie sich über diese URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](../module2/images/sb1.png)

Navigieren Sie zu **Ziele** Klicken Sie auf **Durchsuchen**. Daraufhin werden alle verfügbaren Ziele angezeigt. Suchen Sie Ihr Ziel und klicken Sie auf die **+** wie unten angegeben.

![5-01-select-destination.png](./images/5-01-select-destination.png)

Dann wirst du das sehen. Suchen Sie mithilfe Ihrer ldap nach Ihrem Segment und wählen Sie `--demoProfileLdap-- - Interest in Equipment` aus der Segmentliste aus.

Klicken Sie auf **Weiter**.

![5-04-select-segment.png](./images/5-04-select-segment.png)

Die Echtzeit-Kundendatenplattform von Adobe Experience Platform kann eine Payload an zwei Zieltypen, Segmentziele und Profilziele bereitstellen.

Segmentziele erhalten eine vordefinierte Segmentqualifikationsnutzlast, die später besprochen wird. Diese Payload enthält **all** die Segmentqualifikationen für ein bestimmtes Profil. Selbst für Segmente, die nicht in der Aktivierungsliste des Ziels enthalten sind. Ein Beispiel für ein solches Segmentziel ist **Azure Event Hubs** und **AWS Kinesis**.

Mit profilbasierten Zielen können Sie beliebige Attribute (firstName, lastName, ...) aus dem XDM Profile Union Schema auswählen und in die Aktivierungs-Payload aufnehmen. Ein Beispiel für ein solches Ziel ist die **E-Mail-Marketing**.

Da Ihr Azure Event Hub-Ziel **Segment** Ziel, beispielsweise das Feld auswählen `--aepTenantId--.identification.core.ecid`.

Klicken **Neues Feld hinzufügen**, klicken Sie auf Schema durchsuchen und wählen Sie das Feld aus. `--aepTenantId--identification.core.ecid` (Löschen Sie alle anderen Felder, die automatisch angezeigt werden).

Klicken Sie auf **Weiter**.

![5-05-select-attributes.png](./images/5-05-select-attributes.png)

Klicken Sie auf **Fertigstellen**.

![5-06-destination-finish.png](./images/5-06-destination-finish.png)

Ihr Segment ist jetzt für Ihr Microsoft Event Hub-Ziel aktiviert.

![5-07-destination-segment-added.png](./images/5-07-destination-segment-added.png)

Nächster Schritt: [13.5 Microsoft Azure-Projekt erstellen](./ex5.md)

[Zurück zu Modul 13](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
