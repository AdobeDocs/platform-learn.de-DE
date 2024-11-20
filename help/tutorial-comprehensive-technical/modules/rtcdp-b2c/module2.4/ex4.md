---
title: Segmentaktivierung für Microsoft Azure Event Hub - Aktivieren des Segments
description: Segmentaktivierung für Microsoft Azure Event Hub - Aktivieren des Segments
kt: 5342
doc-type: tutorial
exl-id: 56f6a6dc-82aa-4b64-a3f6-b6f59c484ccb
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 3%

---

# 2.4.4 Segment aktivieren

## 2.4.4.1 Segment zum Azure Event Hub-Ziel hinzufügen

In dieser Übung fügen Sie Ihr Segment `--aepUserLdap-- - Interest in Equipment` zu Ihrem `--aepUserLdap---aep-enablement` Azure Event Hub-Ziel hinzu.

Melden Sie sich bei Adobe Experience Platform an, indem Sie diese URL verwenden: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Wechseln Sie zu **Ziele** und klicken Sie dann auf **Durchsuchen**. Daraufhin werden alle verfügbaren Ziele angezeigt. Suchen Sie Ihr Ziel und klicken Sie auf das Symbol **+** , wie unten angegeben.

![5-01-select-destination.png](./images/5-01-select-destination.png)

Dann wirst du das sehen. Suchen Sie mithilfe Ihrer LDAP nach Ihrem Segment und wählen Sie `--aepUserLdap-- - Interest in Equipment` aus der Segmentliste aus.

Klicken Sie auf **Weiter**.

![5-04-select-segment.png](./images/5-04-select-segment.png)

Die Echtzeit-Kundendatenplattform von Adobe Experience Platform kann eine Payload an zwei Zieltypen, Segmentziele und Profilziele bereitstellen.

Segmentziele erhalten eine vordefinierte Segmentqualifikations-Payload, die später besprochen wird. Eine solche Payload enthält **all** die Segmentqualifikationen für ein bestimmtes Profil. Selbst für Segmente, die nicht in der Aktivierungsliste des Ziels enthalten sind. Ein Beispiel für ein solches Segmentziel sind **Azure Event Hub** und **AWS Kinesis**.

Mit profilbasierten Zielen können Sie beliebige Attribute (firstName, lastName, ...) aus dem XDM Profile Union Schema auswählen und in die Aktivierungs-Payload aufnehmen. Ein Beispiel für ein solches Ziel ist das **E-Mail-Marketing**.

Da Ihr Azure Event Hub-Ziel ein **Segment** -Ziel ist, wählen Sie beispielsweise das Feld `--aepTenantId--.identification.core.ecid` aus.

Klicken Sie auf **Neues Feld hinzufügen**, klicken Sie auf Schema durchsuchen und wählen Sie das Feld `--aepTenantId--identification.core.ecid` aus (löschen Sie alle anderen Felder, die automatisch angezeigt werden).

Klicken Sie auf **Weiter**.

![5-05-select-attributes.png](./images/5-05-select-attributes.png)

Klicken Sie auf **Fertigstellen**.

![5-06-destination-finish.png](./images/5-06-destination-finish.png)

Ihr Segment ist jetzt für Ihr Microsoft Event Hub-Ziel aktiviert.

![5-07-destination-segment-added.png](./images/5-07-destination-segment-added.png)

Nächster Schritt: [2.4.5 Erstellen Sie Ihr Microsoft Azure-Projekt](./ex5.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
