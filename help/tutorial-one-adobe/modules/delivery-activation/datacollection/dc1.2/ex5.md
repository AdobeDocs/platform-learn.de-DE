---
title: Foundation - Datenaufnahme - Datenaufnahme aus Offline-Quellen
description: Foundation - Datenaufnahme - Datenaufnahme aus Offline-Quellen
kt: 5342
doc-type: tutorial
exl-id: 9fce6ece-f454-45de-9c95-35d604b3ae95
source-git-commit: 23816907de778cbe3b9708f4a7273bdcb8e86d5c
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 4%

---

# 1.2.5 Data Landing Zone

In dieser Übung besteht das Ziel darin, Ihren Source-Connector für die Data Landing Zone mit Azure Blob Storage einzurichten.

Data Landing Zone ist eine von Adobe Experience Platform bereitgestellte Azure Blob Storage-Schnittstelle, die Ihnen Zugriff auf eine sichere, Cloud-basierte Dateispeichereinrichtung gewährt, um Dateien in Platform zu laden. Data Landing Zone unterstützt die SAS-basierte Authentifizierung, und die Daten werden im Ruhezustand und bei der Übertragung mit standardmäßigen Azure Blob-Speichersicherheitsmechanismen geschützt. Mit der SAS-basierten Authentifizierung können Sie sicher über eine öffentliche Internetverbindung auf Ihren Data Landing Zone-Container zugreifen.

>[!NOTE]
>
> Adobe Experience Platform **erzwingt eine strikte sieben Tage lange Lebensdauer („time-to-live“, TTL** für alle Dateien, die in einen Data Landing Zone-Container hochgeladen werden. Alle Dateien werden nach sieben Tagen gelöscht.


## Voraussetzungen

Um Blobs oder Dateien in Ihre Adobe Experience Platform Data Landing Zone zu kopieren, verwenden Sie AzCopy, ein Befehlszeilenprogramm. Sie können eine Version für Ihr Betriebssystem über [https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) herunterladen, auf dieser Seite nach unten scrollen, um zu **Herunterladen der Portable Binary AzCopy** und die passende Version für Ihr Betriebssystem auswählen.

![dlz-install-az-copy.png](./images/dlzinstallazcopy.png)

- Entpacken Sie die heruntergeladene Datei

![dlz-install-az-copy.png](./images/dlz1.png)

- Laden Sie die Beispieldatendatei [global-context-websiteInteractions.csv](./../../../../assets/csv/data-ingestion/global-context-websiteinteractions.csv) herunter, die Beispiel-Website-Interaktionen enthält, und speichern Sie sie in dem Ordner, in den Sie entpackt haben **azcopy**.

![dlz-install-az-copy.png](./images/dlz2.png)

- Öffnen Sie ein Terminal-Fenster und navigieren Sie zum Ordner auf Ihrem Desktop. Sie sollten den folgenden Inhalt (azcopy und global-context-website-interaction.csv) sehen, z. B. unter OSX:

![dlz-unzip-azcopy.png](./images/dlzunzipazcopy.png)

## 1.2.5.2 Verbinden der Data Landing Zone mit Adobe Experience Platform

Melden Sie sich über die folgende URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``.  Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./images/sb1.png)

Navigieren Sie im linken Menü zu **Quellen**. Suchen Sie im Quellkatalog nach **Data Landing**.

![Datenaufnahme](./images/sourcesdlz.png)

Klicken Sie auf **Karte** Data Landing Zone“, die Anmeldeinformationen werden auf der rechten Registerkarte angezeigt.

![dlz-view-credentials.png](./images/dlzviewcredentials.png)

Klicken Sie auf das Symbol wie angegeben, um den **SASUri** zu kopieren.

![dlz-copy-sas-uri.png](./images/dlzcopysasuri.png)

## Kopieren Sie Ihre CSV-Datei in Ihre AEP Data Landing Zone

Sie nehmen jetzt Daten mithilfe von Azure-Befehlszeilen-Tools mithilfe von AZCopy in Adobe Experience Platform auf.

Öffnen Sie ein Terminal am Speicherort Ihres AzCopy-Installationsspeicherorts und führen Sie den folgenden Befehl aus, um eine Datei in die Data Landing Zone von AEP zu kopieren:

``./azcopy copy <your-local-file> <your SASUri>``

Stellen Sie sicher, dass Sie Ihren SASUri mit doppelten Anführungszeichen umgeben. Ersetzen Sie `<your-local-file>` durch den Pfad zu Ihrer lokalen Kopie der Datei **global-context-websiteinteractions.csv** im azcopy-Verzeichnis und ersetzen Sie `<your SASUri>` durch den **SASUri**-Wert, den Sie aus der Adobe Experience Platform-Benutzeroberfläche kopiert haben. Ihr Befehl sollte wie folgt aussehen:

```command
./azcopy copy global-context-websiteinteractions.csv "https://sndbxdtlnd2bimpjpzo14hp6.blob.core.windows.net/dlz-user-container?sv=2020-04-08&si=dlz-xxxxxxx-9843-4973-ae52-xxxxxxxx&sr=c&sp=racwdlm&sig=DN3kdhKzard%2BQwKASKg67Zxxxxxxxxxxxxxxxx"
```

Nachdem Sie den obigen Befehl an Ihrem Terminal ausgeführt haben, sehen Sie Folgendes:

![dlz-exec-copy-command.png](./images/dlzexeccopycommand.png)

## Suchen der Datei in der Data Landing Zone

Wechseln Sie zu Ihrer Data Landing Zone in Adobe Experience Platform.

Wählen Sie **Quellen** aus, suchen Sie nach **Data Landing** und klicken Sie auf die Schaltfläche **Setup**.

![dlz-inspect-datalanding-zone.png](./images/dlzinspectdatalandingzone.png)

Dadurch wird die Data Landing Zone geöffnet. Die Datei, die Sie gerade hochgeladen haben, wird im Bedienfeld „Daten auswählen **der Data Landing Zone**.

![dlz-datalanding-zone-open.png](./images/dlzdatalandingzoneopen.png)

## Verarbeiten der Datei

Wählen Sie Ihre Datei aus und wählen Sie **Getrennt** als Datenformat. Anschließend sehen Sie eine Vorschau Ihrer Daten. Klicken Sie auf **Weiter**.

![dlz-datalanding-select-file.png](./images/dlzdatalandingselectfile.png)

Sie können jetzt mit der Zuordnung der hochgeladenen Daten zum XDM-Schema Ihres Datensatzes beginnen.

Wählen Sie **Vorhandener Datensatz** und wählen Sie den Datensatz **Demosystem - Ereignisdatensatz für Website (Global v1.1)**. Klicken Sie auf **Weiter**.

![dlz-target-dataset.png](./images/dlztargetdataset.png)

Jetzt können Sie die eingehenden Quelldaten aus Ihrer CSV-Datei den Zielfeldern aus dem XDM-Schema des Datensatzes zuordnen.

![dlz-start-mapping.png](./images/dlzstartmapping.png)

>[!NOTE]
>
> Beachten Sie die potenziellen Fehler bei der Zuordnung. Sie korrigieren die Zuordnung im nächsten Schritt.

## Zuordnen von Feldern

Klicken Sie zunächst auf die Schaltfläche **Alle Zuordnungen löschen**. Anschließend können Sie mit einer sauberen Zuordnung beginnen.

![dlz-clear-mapping.png](./images/mappings1.png)

Klicken Sie anschließend auf **Neuer Feldtyp** und wählen Sie **Neues Feld hinzufügen** aus.

![dlz-clear-mapping.png](./images/dlzclearmappings.png)

Um das Quellfeld **ecid** zuzuordnen, wählen Sie das Feld **identities.ecid** aus und klicken Sie auf **Auswählen**.

![dlz-map-identity.png](./images/dlzmapidentity.png)

Klicken Sie anschließend auf **Zielfeld zuordnen**.

![dlz-map-select-target-field.png](./images/dlzmapselecttargetfield.png)

Wählen Sie das Feld ``--aepTenantId--``.identification.core.ecid in der Schemastruktur aus.

![dlz-map-target-field.png](./images/dlzmaptargetfield.png)

Sie müssen noch einige andere Felder zuordnen. Klicken Sie auf **+ Neuer Feldtyp** dann auf **Neues Feld hinzufügen** und fügen Sie Felder für diese Zuordnung hinzu

| source | target |
|---|---|
| resource.info.pagename | web.webPageDetails.name |
| Zeitstempel | Zeitstempel |
| Zeitstempel | _id |

![dlz-add-other-mapping.png](./images/dlzaddothermapping.png)

Wenn Sie fertig sind, sollte Ihr Bildschirm wie folgt aussehen: Der folgende Bildschirm. Klicken Sie auf **Weiter**.

![dlz-mapping-result.png](./images/dlzmappingresult.png)

Klicken Sie auf **Weiter**.

![dlz-default-scheduling.png](./images/dlzdefaultscheduling.png)

Klicken Sie auf **Fertigstellen**.

![dlz-import-finish.png](./images/dlzimportfinish.png)

## Überwachen des Datenflusses

Um Ihren Datenfluss zu überwachen, gehen Sie zu **Quellen**, **Datenflüsse** und klicken Sie auf Ihren Datenfluss:

![dlz-monitor-dataflow.png](./images/dlzmonitordataflow.png)

Das Laden der Daten kann einige Minuten dauern. Bei Erfolg wird der Status „Erfolg **angezeigt**:

![dlz-monitor-dataflow-result.png](./images/dlzmonitordataflowresult.png)

## Nächste Schritte

Zurück zu [Datenaufnahme](./data-ingestion.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
