---
title: Audience Activation zu Microsoft Azure Event Hub - Einrichten des Event Hub RTCDP-Ziels in Adobe Experience Platform
description: Audience Activation zu Microsoft Azure Event Hub - Einrichten des Event Hub RTCDP-Ziels in Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: e48b7b50-c95b-46da-b696-494da3926325
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 1%

---

# 2.4.3 Konfigurieren des Azure Event Hub-Ziels in Adobe Experience Platform

## Identifizieren erforderlicher Azure-Verbindungsparameter

Zum Konfigurieren eines Event Hub-Ziels in Adobe Experience Platform benötigen Sie Folgendes:

- Namespace von Event Hubs
- Ereignis-Hub
- Azure SAS-Schlüsselname
- Azure SAS-Schlüssel

Event Hub und EventHub-Namespace wurden in der vorherigen Übung definiert: [Einrichten von Event Hub in Azure](./ex2.md)

### Namespace der Ereignis-Hubs

Um die oben genannten Informationen im Azure-Portal zu suchen, navigieren Sie zu [https://portal.azure.com/#home](https://portal.azure.com/#home). Stellen Sie sicher, dass Sie das richtige Azure-Konto verwenden.

Klicken Sie **Alle Ressourcen** in Ihrem Azure-Portal:

![2-01-azure-all-resources.png](./images/201azureallresources.png)

Suchen Sie Ihren **Event Hubs-Namespace** in der Liste und klicken Sie darauf.

![2-01-azure-all-resources.png](./images/201azureallresources1.png)

Der Name Ihres **Event Hubs-Namespace** ist jetzt deutlich sichtbar. Es sollte ähnlich wie `--aepUserLdap---aep-enablement` sein.

![2-01-azure-all-resources.png](./images/201azureallresources2.png)

### Ereignis-Hub

Klicken Sie auf Ihrer Seite **Event Hubs-** Namespace) auf **Entitäten > Ereignis-Hubs**, um eine Liste der in Ihrem Event Hubs-Namespace definierten Ereignis-Hubs zu erhalten. Wenn Sie die in der vorherigen Übung verwendeten Benennungskonventionen befolgt haben, finden Sie einen Ereignis-Hub mit dem Namen `--aepUserLdap---aep-enablement-event-hub`. Notieren Sie sich das. Sie benötigen es in der nächsten Übung.

![2-04-event-hub-selected.png](./images/204eventhubselected.png)

### SAS-Schlüsselname

Klicken Sie auf **Seite „Namespace** Ereignis-Hubs“ auf **Einstellungen > Richtlinien für gemeinsamen Zugriff**. Es wird eine Liste mit Richtlinien für den gemeinsamen Zugriff angezeigt. Der gesuchte SAS-Schlüssel ist **RootManageSharedAccessKey**, der **SAS-Schlüsselname. Schreib es auf.

![2-05-select-sas.png](./images/205selectsas.png)

### SAS-Schlüsselwert

Klicken Sie anschließend auf **RootManageSharedAccessKey**, um den SAS-Schlüsselwert abzurufen. und drücken Sie das Symbol **In Zwischenablage kopieren**, um die Primäre **&#x200B;**&#x200B;Taste zu kopieren, in diesem Fall `pqb1jEC0KLazwZzIf2gTHGr75Z+PdkYgv+AEhObbQEY=`.

![2-07-sas-key-value.png](./images/207saskeyvalue.png)

### Zusammenfassung der Zielwerte

An dieser Stelle sollten Sie alle Werte identifiziert haben, die zum Definieren des Azure Event Hub-Ziels in Adobe Experience Platform Real-time CDP erforderlich sind.

| Zielattributname | Zielattributwert | Beispielwert |
|---|---|---|
| sasKeyName | SAS-Schlüsselname | RootManageSharedAccessKey |
| sasKey | SAS-Schlüsselwert | pqb1jEC0KLazwZzIf2gTHGr75Z+PdkYgv+AEhObbQEY= |
| Namespace | Namespace der Ereignis-Hubs | `--aepUserLdap---aep-enablement` |
| eventHubName | Ereignis-Hub | `--aepUserLdap---aep-enablement-event-hub` |

## Erstellen eines Azure Event Hub-Ziels in Adobe Experience Platform

Melden Sie sich über die folgende URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

Gehen Sie zu **Ziele** und dann zu **Katalog**. Wählen Sie **Cloud-Speicher**, gehen Sie zu **Azure Event** und klicken Sie auf **Einrichten**.

![2-08-list-destinations.png](./images/208listdestinations.png)

Wählen Sie **Standardauthentifizierung** aus. Füllen Sie die Verbindungsdetails aus, die Sie in der vorherigen Übung erfasst haben. Klicken Sie anschließend auf **Mit Ziel verbinden**.

![2-09-destination-values.png](./images/209destinationvalues.png)

Wenn Ihre Anmeldeinformationen korrekt waren, wird eine Bestätigung angezeigt: **Verbunden**.

![2-09-destination-values.png](./images/209destinationvaluesa.png)

Nun müssen Sie den Namen und die Beschreibung im `--aepUserLdap---aep-enablement` Format eingeben. Geben Sie **eventHubName** ein (siehe vorherige Übung, es sieht wie folgt aus: `--aepUserLdap---aep-enablement-event-hub`) und klicken Sie auf **Weiter**.

![2-10-create-destination.png](./images/210createdestination.png)

Sie können optional eine Data Governance-Richtlinie auswählen. Klicken Sie auf **Speichern und beenden**.

![2-11-save-exit-activation.png](./images/211saveexitactivation.png)

Ihr Ziel ist jetzt in Adobe Experience Platform erstellt und verfügbar.

![2-12-destination-created.png](./images/212destinationcreated.png)

## Nächste Schritte

Navigieren Sie zu [2.4.4 Zielgruppe erstellen](./ex4.md){target="_blank"}

Zurück zu [Real-Time CDP: Audience Activation zum Microsoft Azure Event Hub](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
