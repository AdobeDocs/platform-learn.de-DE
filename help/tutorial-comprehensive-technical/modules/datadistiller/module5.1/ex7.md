---
title: Query Service - Datensatz mit Tableau durchsuchen
description: Query Service - Datensatz mit Tableau durchsuchen
kt: 5342
doc-type: tutorial
exl-id: 29525740-fe1f-4770-bcc9-f2ad499a2cb5
source-git-commit: b53ee64ae8438b8f48f842ed1f44ee7ef3e813fc
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# 5.1.7 Query Service und Tableau

Öffnen Sie Tableau.

![start-tableau.png](./images/start-tableau.png)

Wählen Sie in **Verbindung zu einem Server herstellen** die Option **PostgreSQL**:

![tableau-connect-postgress.png](./images/tableau-connect-postgress.png)

Wechseln Sie zu Adobe Experience Platform, zu **Abfragen** und zu **Anmeldeinformationen**.

![query-service-credentials.png](./images/query-service-credentials.png)

Kopieren Sie auf der Seite **Anmeldedaten** in Adobe Experience Platform den **Host** und fügen Sie ihn in das Feld **Server** ein, kopieren Sie die **Datenbank** und fügen Sie sie in das Feld **Datenbank** in Tableau ein, kopieren Sie den **Port** und fügen Sie ihn in das Feld **Port** in Tableau ein. Dasselbe für **Benutzername** und **Kennwort**. Klicken Sie anschließend auf **Anmelden**.

Anmelden:

![tableau-connection-dialog.png](./images/tableau-connection-dialog.png)

Klicken Sie auf &quot;Suchen&quot;(1), geben Sie Ihren **ldap** in das Suchfeld ein, identifizieren Sie die Tabelle aus dem Ergebnissatz und ziehen Sie sie an die Stelle mit dem Namen **Tabellen hierher ziehen**. Klicken Sie abschließend auf **Blatt 1** (3).

![tableau-drag-table.png](./images/tableau-drag-table.png)

Um unsere Daten auf der Karte zu visualisieren, müssen wir Längen- und Breitengrad in Dimensionen konvertieren. Wählen Sie in **Kennzahlen** die Option **Breitengrad** (1) aus, öffnen Sie das Dropdown-Menü des Felds und wählen Sie **In Dimension konvertieren** (2). Führen Sie dasselbe für die Maßnahme **Längengrad** aus.

![tableau-convert-dimension.png](./images/tableau-convert-dimension.png)

Ziehen Sie die Kennzahl **Längengrad** auf die Kennzahl **Spalten** und die Kennzahl **Breitengrad** auf **Zeilen**. Die Karte von **Belgien** wird automatisch mit kleinen Punkten angezeigt, die die Städte in dem Datensatz darstellen.

![tableau-drag-lon-lat.png](./images/tableau-drag-lon-lat.png)

Wählen Sie **Namen der Messung** (1) aus, öffnen Sie das Dropdown-Menü und wählen Sie **Zu Blatt hinzufügen** (2):

![tableau-select-measure-names.png](./images/tableau-select-measure-names.png)

Sie haben jetzt eine Karte mit Punkten unterschiedlicher Größe. Die Größe gibt die Anzahl der Interaktionen des Callcenters für diese spezifische Stadt an. Um die Größe der Punkte zu ändern, navigieren Sie zum rechten Bereich und öffnen Sie **Messwerte messen** (über das Dropdown-Symbol). Wählen Sie aus der Dropdownliste **Größen bearbeiten** aus. Spielen Sie mit unterschiedlichen Größen herum.

![tableau-variation-size-dots.png](./images/tableau-vary-size-dots.png)

Um die Daten pro **Aufrufthema** weiter anzuzeigen, ziehen Sie (1) die Dimension **Aufrufthema** auf **Seiten**. Navigieren Sie mithilfe des **Aufrufethemas** (2) auf der rechten Seite des Bildschirms durch die verschiedenen **Aufrufthemen**:

![tableau-call-topic-navigation.png](./images/tableau-call-topic-navigation.png)

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [5.1.8 Query Service API](./ex8.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
