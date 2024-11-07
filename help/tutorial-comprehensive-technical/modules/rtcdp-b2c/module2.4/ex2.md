---
title: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten des Ereignis-Hub-RTCDP-Ziels in Adobe Experience Platform
description: Segmentaktivierung für Microsoft Azure Event Hub - Einrichten des Ereignis-Hub-RTCDP-Ziels in Adobe Experience Platform
kt: 5342
doc-type: tutorial
source-git-commit: c6ba1f751f18afe39fb6b746a62bc848fa8ec9bf
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# 2.4.2 Konfigurieren des Azure Event Hub-Ziels in Adobe Experience Platform

## 2.4.2.1 Erforderliche Azure-Verbindungsparameter identifizieren

Um ein Event Hub-Ziel in Adobe Experience Platform zu definieren, benötigen Sie Folgendes:

- Ereignis-Hubs-Namespace
- Ereignis-Hub
- Azure SAS-Schlüsselname
- Azure-SAS-Schlüssel

Event Hub- und EventHub-Namespace wurden in der vorherigen Übung definiert: [Übung 1 - Einrichten von Event Hub in Azure](./ex1.md)

### Ereignis-Hubs-Namespace

Um die oben genannten Informationen in Azure Portal zu suchen, navigieren Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home). Stellen Sie sicher, dass Sie das richtige Azure-Konto verwenden.

Wählen Sie **Alle Ressourcen** in Azure Portal aus:

![2-01-azure-all-resources.png](./images/2-01-azure-all-resources.png)

### Ereignis-Hub

Suchen Sie nach einer Ressource mit dem Ressourcentyp **Ereignis-Hubs-Namespace**. Wenn Sie die in der vorherigen Übung verwendeten Namenskonventionen befolgt haben, lautet Ihr Ereignis-Hubs-Namespace `--demoProfileLdap---aep-enablement`. Notieren Sie sich das, Sie werden es in der nächsten Übung brauchen.

![2-02-select-event-hubs-namespace.png](./images/2-02-select-event-hubs-namespace.png)

Klicken Sie auf den Namen des Ereignis-Hubs-Namespace , um die Details abzurufen:

![2-03-select-event-hub.png](./images/2-03-select-event-hub.png)

Wählen Sie **Ereignis-Hub** aus, um eine Liste der Ereignis-Hub zu erhalten, die in Ihrem Ereignis-Hub-Namespace definiert sind. Wenn Sie die in der vorherigen Übung verwendeten Namenskonventionen befolgt haben, finden Sie einen Ereignis-Hub mit dem Namen `--demoProfileLdap---aep-enablement-event-hub`. Notieren Sie sich das, Sie werden es in der nächsten Übung brauchen.

![2-04-event-hub-selected.png](./images/2-04-event-hub-selected.png)

### SAS-Schlüsselname

Wählen Sie **Freigegebene Zugriffsrichtlinien** für Ihren **Ereignis-Hubs-Namespace** aus.

![2-05-select-sas.png](./images/2-05-select-sas.png)

Daraufhin wird eine Liste der Richtlinien für den freigegebenen Zugriff angezeigt. Der SAS-Schlüssel, nach dem wir suchen, ist **RootManageSharedAccessKey**. Dies ist der Name des SAS-Schlüssels. Schreib es auf.

![2-06-sas-overview.png](./images/2-06-sas-overview.png)

### SAS-Schlüsselwert

Klicken Sie auf **RootManageSharedAccessKey** , um den SAS-Schlüsselwert abzurufen. Drücken Sie dann das Symbol **In die Zwischenablage kopieren** , um die **Primäre Taste** zu kopieren:

![2-07-sas-key-value.png](./images/2-07-sas-key-value.png)

### Zielwertzusammenfassung

An dieser Stelle sollten Sie alle Werte identifiziert haben, die zum Definieren des Azure Event Hub-Ziels in der Echtzeit-Kundendatenplattform von Adobe Experience Platform erforderlich sind.

| Zielattribut-Name | Zielattributwert | Beispielwert |
|---|---|---|
| sasKeyName | SAS-Schlüsselname | RootManageSharedAccessKey |
| sasKey | SAS-Schlüsselwert | srREx9ShJG1Rv7f/.. |
| Namespace | Ereignis-Hubs-Namespace | `--demoProfileLdap---aep-enablement` |
| eventHubName | Ereignis-Hub | `--demoProfileLdap---aep-enablement-event-hub` |

## 2.4.2.2 Azure Event Hub-Ziel in Adobe Experience Platform erstellen

Melden Sie sich bei Adobe Experience Platform an, indem Sie diese URL verwenden: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Wechseln Sie zu **Ziele** und gehen Sie dann zu **Katalog**.

![Datenaufnahme](./images/sb2a.png)

Wählen Sie **Cloud-Speicher** und gehen Sie zu **Azure Event Hub** und klicken Sie auf **Einrichten** oder **Konfigurieren**:

![2-08-list-destinations.png](./images/2-08-list-destinations.png)

Füllen Sie die Zielwerte aus, die Sie in der vorherigen Übung erfasst haben. Klicken Sie anschließend auf **Mit Ziel verbinden**.

![2-09-destination-values.png](./images/2-09-destination-values.png)

Wenn Ihre Anmeldedaten korrekt waren, sehen Sie eine Bestätigung: **Verbunden**.

![2-09-destination-values.png](./images/2-09-destination-valuesa.png)

Geben Sie nun den Namen und die Beschreibung im Format `--demoProfileLdap---aep-enablement` ein. Geben Sie den **eventHubName** ein (siehe vorherige Übung, sieht wie folgt aus: `--demoProfileLdap---aep-enablement-event-hub`) und klicken Sie auf **Weiter**.

![2-10-create-destination.png](./images/2-10-create-destination.png)

Klicken Sie auf **Speichern und beenden**.

![2-11-save-exit-activation.png](./images/2-11-save-exit-activation.png)

Ihr Ziel wurde jetzt in Adobe Experience Platform erstellt und verfügbar gemacht.

![2-12-destination-created.png](./images/2-12-destination-created.png)

Nächster Schritt: [2.4.3 Segment erstellen](./ex3.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
