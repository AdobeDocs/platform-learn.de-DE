---
title: Query Service - Datensatz mit Tableau durchsuchen
description: Query Service - Datensatz mit Tableau durchsuchen
kt: 5342
doc-type: tutorial
exl-id: 29525740-fe1f-4770-bcc9-f2ad499a2cb5
source-git-commit: d9d9a38c1e160950ae755e352a54667c8a7b30f7
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 5.1.7 Query Service und Tableau

Öffnen Sie Tableau.

![start-tableau.png](./images/starttableau.png)

Klicken Sie in &quot;**Verbindung zu einem Server herstellen**&quot;auf &quot;**Mehr**&quot;und dann auf &quot;**PostgreSQL**&quot;.

![tableau-connect-postgress.png](./images/tableauconnectpostgress.png)

Wenn Sie PostgeSQL noch nicht mit Tableau verwendet haben, können Sie dies sehen. Klicken Sie auf **Treiber herunterladen**.

![tableau-connect-postgress.png](./images/tableauconnectpostgress1.png)

Befolgen Sie die Anweisungen zum Herunterladen und Installieren des PostgreSQL-Treibers.

![tableau-connect-postgress.png](./images/tableauconnectpostgress2.png)

Nachdem Sie die Installation des Treibers abgeschlossen haben, beenden Sie den Tableau Desktop und starten Sie ihn neu. Wechseln Sie nach dem Neustart erneut zu **Verbindung zu einem Server herstellen**, klicken Sie auf **Mehr** und klicken Sie dann erneut auf **PostgreSQL** .

![tableau-connect-postgress.png](./images/tableauconnectpostgress.png)

Dann wirst du das sehen.

![tableau-connect-postgress.png](./images/tableauconnectpostgress3.png)

Wechseln Sie zu Adobe Experience Platform, zu **Abfragen** und zu **Anmeldeinformationen**.

![query-service-credentials.png](./images/queryservicecredentials.png)

Kopieren Sie auf der Seite **Anmeldedaten** in Adobe Experience Platform den **Host** und fügen Sie ihn in das Feld **Server** ein, kopieren Sie die **Datenbank** und fügen Sie sie in das Feld **Datenbank** in Tableau ein, kopieren Sie den **Port** und fügen Sie ihn in das Feld **Port** in Tableau ein. Dasselbe für **Benutzername** und **Kennwort**. Klicken Sie anschließend auf **Anmelden**.

![tableau-connection-dialog.png](./images/tableauconnectiondialog.png)

Suchen Sie in der Liste der verfügbaren Tabellen die Tabelle, die Sie in der vorherigen Übung erstellt haben, nämlich `--aepUserLdap--_callcenter_interaction_analysis`. Ziehen Sie es auf die Arbeitsfläche.

![tableau-drag-table.png](./images/tableaudragtable.png)

Dann wirst du das sehen. Klicken Sie auf **Jetzt aktualisieren**.

![tableau-drag-table.png](./images/tableaudragtable1.png)

Sie werden sehen, wie die Daten von AEP in Tableau verfügbar werden. Klicken Sie auf **Blatt 1** , um mit der Arbeit mit den Daten zu beginnen.

![tableau-drag-table.png](./images/tableaudragtable2.png)

Um Ihre Daten auf der Karte zu visualisieren, müssen Sie Längen- und Breitengrad in Dimensionen konvertieren. Klicken Sie in **Kennzahlen** mit der rechten Maustaste auf **Breitengrad** und wählen Sie im Menü die Option **In Dimension konvertieren** aus. Führen Sie dasselbe für die Maßnahme **Längengrad** aus.

![tableau-convert-dimension.png](./images/tableauconvertdimension.png)

Ziehen Sie die Kennzahl **Längengrad** auf die Kennzahl **Spalten** und die Kennzahl **Breitengrad** auf **Zeilen**. Die Karte von **Belgien** wird automatisch mit kleinen Punkten angezeigt, die die Städte in dem Datensatz darstellen.

![tableau-drag-lon-lat.png](./images/tableaudraglonlat.png)

Wählen Sie **Namen der Messung** und klicken Sie auf **Zu Blatt hinzufügen**.

![tableau-select-measure-names.png](./images/selectmeasurenames.png)

Sie haben jetzt eine Karte mit Punkten unterschiedlicher Größe. Die Größe gibt die Anzahl der Interaktionen des Callcenters für diese spezifische Stadt an. Um die Größe der Punkte zu ändern, navigieren Sie zum rechten Bereich und öffnen Sie **Messwerte messen** (über das Dropdown-Symbol). Wählen Sie aus der Dropdownliste **Größen bearbeiten** aus. Spielen Sie mit unterschiedlichen Größen herum.

![tableau-variation-size-dots.png](./images/tableauvarysizedots.png)

Um die Daten pro **Aufrufthema** weiter anzuzeigen, ziehen Sie die Dimension **Aufrufthema** auf **Seiten**. Navigieren Sie mithilfe des **Aufrufethemas** auf der rechten Seite des Bildschirms durch die verschiedenen **Aufrufthemen**:

![tableau-call-topic-navigation.png](./images/tableaucalltopicnavigation.png)

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [5.1.8 Query Service API](./ex8.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
