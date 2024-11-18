---
title: Foundation - Datenerfassung - Datenerfassung aus Offline-Quellen
description: Foundation - Datenerfassung - Datenerfassung aus Offline-Quellen
kt: 5342
doc-type: tutorial
exl-id: 21b84a77-4115-4ba7-b847-b236aa14bbdd
source-git-commit: 8bdcd03bd38a6da98b82439ad86482cad5f4e684
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 4%

---

# 1.2.5 Einstiegszone für Daten

In dieser Übung besteht das Ziel darin, Ihren Data Landing Zone Source-Connector mit Azure Blob Storage einzurichten.

Data Landing Zone ist eine Azure Blob-Speicherschnittstelle, die von Adobe Experience Platform bereitgestellt wird und Ihnen den Zugriff auf eine sichere, Cloud-basierte Dateispeicheranlage ermöglicht, über die Dateien in Platform importiert werden können. Data Landing Zone unterstützt SAS-basierte Authentifizierung und die Daten sind mit standardmäßigen Azure Blob Storage-Sicherheitsmechanismen im Ruhezustand und während der Übertragung geschützt. Mit der SAS-basierten Authentifizierung können Sie über eine öffentliche Internetverbindung sicher auf Ihren Data Landing Zone Container zugreifen.

>[!NOTE]
>
> Adobe Experience Platform **erzwingt eine strikte Gültigkeitsdauer von sieben Tagen (TTL)** für alle Dateien, die in einen Dateneinstiegszonen-Container hochgeladen wurden. Alle Dateien werden nach sieben Tagen gelöscht.


## Voraussetzungen

Um Blobs oder Dateien in Ihre Adobe Experience Platform Data Landing Zone zu kopieren, verwenden Sie AzCopy, ein Befehlszeilen-Dienstprogramm. Sie können eine Version für Ihr Betriebssystem über &quot;[https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10)&quot; herunterladen, auf dieser Seite nach unten scrollen und &quot;**Portable AzCopy-Binärdatei herunterladen**&quot;und die entsprechende Version für Ihr Betriebssystem auswählen.

![dlz-install-az-copy.png](./images/dlzinstallazcopy.png)

- Entpacken Sie die Download-Datei.

![dlz-install-az-copy.png](./images/dlz1.png)

- Laden Sie die Beispieldatendatei global-context-websiteinteractions.csv herunter, die Beispiel-Website-Interaktionen enthält, und speichern Sie sie in dem Ordner, in dem Sie **azcopy** entpackt haben.

![dlz-install-az-copy.png](./images/dlz2.png)

- Öffnen Sie ein Terminal-Fenster und navigieren Sie zum Ordner auf Ihrem Desktop. Sie sollten den folgenden Inhalt sehen (azcopy und global-context-websiteinteractions.csv), z. B. unter OSX:

![dlz-unzip-azcopy.png](./images/dlzunzipazcopy.png)

## 1.2.5.2 Data Landing Zone mit Adobe Experience Platform verbinden

Melden Sie sich bei Adobe Experience Platform an, indem Sie diese URL verwenden: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``.  Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](./images/sb1.png)

Gehen Sie im linken Menü zu **Quellen**. Suchen Sie im Quellkatalog nach **data landing**.

![Datenaufnahme](./images/sourcesdlz.png)

Klicken Sie auf die Karte **Dateneinstiegszone** , um die Anmeldedaten auf der rechten Registerkarte anzuzeigen.

![dlz-view-credentials.png](./images/dlzviewcredentials.png)

Klicken Sie auf das Symbol wie angegeben, um den **SASUri** zu kopieren.

![dlz-copy-sas-uri.png](./images/dlzcopysasuri.png)

## Kopieren Sie Ihre CSV-Datei in Ihre AEP-Daten-Landingzone.

Sie erfassen jetzt Daten mit Azure-Befehlszeilen-Tools mit AZCopy in Adobe Experience Platform.

Öffnen Sie ein Terminal am Speicherort Ihrer azcopy install-Position und führen Sie den folgenden Befehl aus, um eine Datei in die Daten-Landingzone von AEP zu kopieren:

``./azcopy copy <your-local-file> <your SASUri>``

Stellen Sie sicher, dass Sie Ihre SASUri mit doppelten Anführungszeichen umgeben. Ersetzen Sie `<your-local-file>` durch den Pfad zu Ihrer lokalen Kopie der Datei **global-context-websiteinteractions.csv** im azcopy-Verzeichnis und ersetzen Sie `<your SASUri>` durch den Wert **SASUri** , den Sie aus der Adobe Experience Platform-Benutzeroberfläche kopiert haben. Ihr Befehl sollte wie folgt aussehen:

```command
./azcopy copy global-context-websiteinteractions.csv "https://sndbxdtlnd2bimpjpzo14hp6.blob.core.windows.net/dlz-user-container?sv=2020-04-08&si=dlz-xxxxxxx-9843-4973-ae52-xxxxxxxx&sr=c&sp=racwdlm&sig=DN3kdhKzard%2BQwKASKg67Zxxxxxxxxxxxxxxxx"
```

Nach dem Ausführen des oben genannten Befehls in Ihrem Terminal sehen Sie Folgendes:

![dlz-exec-copy-command.png](./images/dlzexeccopycommand.png)

## Suchen Ihrer Datei in Ihrer Data Landing Zone

Navigieren Sie zu Ihrer Data Landing Zone in Adobe Experience Platform.

Wählen Sie **Quellen** aus, suchen Sie nach **Daten-Landing** und klicken Sie auf die Schaltfläche **Einrichten** .

![dlz-inspect-datalanding-zone.png](./images/dlzinspectdatalandingzone.png)

Dadurch wird die Dateneinstiegszone geöffnet. Die Datei, die Sie gerade hochgeladen haben, wird im Bereich **Daten auswählen** der Dateneinstiegszone angezeigt.

![dlz-datalanding-zone-open.png](./images/dlzdatalandingzoneopen.png)

## Datei verarbeiten

Wählen Sie Ihre Datei aus und wählen Sie als Datenformat **Getrennt** aus. Daraufhin wird eine Vorschau Ihrer Daten angezeigt. Klicken Sie auf **Weiter**.

![dlz-datalanding-select-file.png](./images/dlzdatalandingselectfile.png)

Sie können jetzt mit der Zuordnung der hochgeladenen Daten zum XDM-Schema Ihres Datensatzes beginnen.

Wählen Sie **Vorhandenen Datensatz** aus und wählen Sie den Datensatz **Demo System - Event Datensatz für Website (Global v1.1)**. Klicken Sie auf **Weiter**.

![dlz-target-dataset.png](./images/dlztargetdataset.png)

Jetzt können Sie die eingehenden Quelldaten aus Ihrer CSV-Datei den Zielfeldern aus dem XDM-Schema des Datensatzes zuordnen.

![dlz-start-mapping.png](./images/dlzstartmapping.png)

>[!NOTE]
>
> Die möglichen Fehler bei der Zuordnung stören Sie nicht. Sie werden die Zuordnung im nächsten Schritt korrigieren.

## Zuordnungsfelder

Klicken Sie zunächst auf die Schaltfläche **Alle Zuordnungen löschen** . Sie können dann mit einer sauberen Zuordnung beginnen.

![dlz-clear-mappings.png](./images/mappings1.png)

Klicken Sie anschließend auf **Neuer Feldtyp** und wählen Sie **Neues Feld hinzufügen** aus.

![dlz-clear-mappings.png](./images/dlzclearmappings.png)

Um das Quellfeld **ecid** zuzuordnen, wählen Sie das Feld **identities.ecid** aus und klicken Sie auf **Select**.

![dlz-map-identity.png](./images/dlzmapidentity.png)

Klicken Sie anschließend auf **Zielfeld zuordnen**.

![dlz-map-select-target-field.png](./images/dlzmapselecttargetfield.png)

Wählen Sie das Feld ``--aepTenantId--``.identification.core.ecid in der Schemastruktur aus.

![dlz-map-target-field.png](./images/dlzmaptargetfield.png)

Sie müssen ein paar weitere Felder zuordnen, auf **+ Neuer Feldtyp** und dann auf **Neues Feld hinzufügen** klicken und Felder für diese Zuordnung hinzufügen

| source | target |
|---|---|
| resource.info.pagename | web.webPageDetails.name |
| Zeitstempel | Zeitstempel |
| Zeitstempel | _id |

![dlz-add-other-mapping.png](./images/dlzaddothermapping.png)

Wenn Sie fertig sind, sollte der Bildschirm wie folgt aussehen: Klicken Sie auf **Weiter**.

![dlz-mapping-result.png](./images/dlzmappingresult.png)

Klicken Sie auf **Weiter**.

![dlz-default-scheduling.png](./images/dlzdefaultscheduling.png)

Klicken Sie auf **Fertigstellen**.

![dlz-import-finish.png](./images/dlzimportfinish.png)

## Überwachen des Datenflusses

Um Ihren Datenfluss zu überwachen, gehen Sie zu **Quellen**, **Datenflüsse** und klicken Sie auf Ihren Datenfluss:

![dlz-monitor-dataflow.png](./images/dlzmonitordataflow.png)

Das Laden der Daten kann einige Minuten dauern. Wenn es erfolgreich ist, wird der Status **Erfolg** angezeigt:

![dlz-monitor-dataflow-result.png](./images/dlzmonitordataflowresult.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 1.2](./data-ingestion.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
