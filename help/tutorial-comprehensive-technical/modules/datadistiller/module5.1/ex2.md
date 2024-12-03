---
title: Query Service - Erste Schritte
description: Query Service - Erste Schritte
kt: 5342
doc-type: tutorial
exl-id: 5c4615c6-41c0-465a-b9b6-f59eef388c73
source-git-commit: b53ee64ae8438b8f48f842ed1f44ee7ef3e813fc
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---

# 5.1.2 Erste Schritte

## Kennenlernen der Benutzeroberfläche von Adobe Experience Platform

Wechseln Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Nachdem Sie die entsprechende [!UICONTROL Sandbox] ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)


## Daten auf der Plattform durchsuchen

Daten aus verschiedenen Kanälen zu beziehen, ist für jede Marke eine schwierige Aufgabe. In dieser Übung interagieren Kunden von Citi Signal mit Citi Signal auf ihrer Website, über ihre mobile App werden Kaufdaten vom Point of Sale-System von Citi Signal erfasst und sie verfügen über CRM- und Treuedaten. Citi Signal verwendet Adobe Analytics und Adobe Launch, um Daten über seine Website, mobile Anwendung und POS-System zu erfassen. Daher fließen diese Daten bereits in Adobe Experience Platform. Beginnen wir mit der Erforschung aller Daten für Citi Signal, die bereits in Adobe Experience Platform vorhanden sind.

Gehen Sie im linken Menü zu **Datensätze**.

![emea-website-interaction-dataset.png](./images/emea-website-interaction-dataset.png)

Citi Signal streamt Daten an Adobe Experience Platform und diese Daten sind im Datensatz `Demo System - Event Dataset for Website (Global v1.1)` verfügbar. Suchen Sie nach `Demo System - Event Dataset for Website`.

![emea-callcenter-interaction-dataset.png](./images/emea-website-interaction-dataset1.png)

Die Callcenter-Interaktionsdaten von Citi Signal werden im Datensatz `Demo System - Event Dataset for Call Center (Global v1.1)` erfasst. Suchen Sie im Suchfeld nach `Demo System - Event Dataset for Call Center` Daten. Klicken Sie auf den Namen des Datensatzes, um ihn zu öffnen.

![emea-callcenter-interaction-dataset.png](./images/emea-callcenter-interaction-dataset.png)

Nachdem Sie auf den Datensatz geklickt haben, erhalten Sie einen Überblick über die Datensatzaktivität, z. B. aufgenommene und fehlgeschlagene Batches.

![preview-interaction-dataset.png](./images/preview-interaction-dataset.png)

Klicken Sie auf **Datensatz-Vorschau anzeigen** , um ein Beispiel der im `Demo System - Event Dataset for Call Center (Global v1.1)` -Datensatz gespeicherten Daten anzuzeigen. Das linke Bedienfeld zeigt die Schemastruktur für diesen Datensatz an.

![exploration-interaction-dataset.png](./images/explore-interaction-dataset.png)

Klicken Sie auf die Schaltfläche **Schließen** , um das Fenster **Vorschau des Datensatzes anzeigen** zu schließen.

## Einführung in Query Service

Der Zugriff auf den Adobe Experience Platform-Abfragedienst erfolgt über **Abfragen** im linken Menü.

![select-queries.png](./images/select-queries.png)

Durch Wechseln zu **Protokoll** wird die Seite &quot;Abfrageliste&quot;angezeigt, auf der Sie eine Liste aller Abfragen erhalten, die in dieser Organisation ausgeführt wurden, wobei sich die neueste Seite oben befindet.

![query-list.png](./images/query-list.png)

Klicken Sie in der Liste auf eine SQL-Abfrage und beachten Sie die Details in der rechten Leiste.

![click-sql-query.png](./images/click-sql-query.png)

Sie können im Fenster einen Bildlauf durchführen, um die gesamte Abfrage anzuzeigen, oder auf das unten hervorgehobene Symbol klicken, um die gesamte Abfrage in Ihr Notebook zu kopieren. Sie müssen die Abfrage derzeit nicht kopieren.

![click-copy-query.png](./images/click-copy-query.png)

Sie können nicht nur die ausgeführten Abfragen sehen, sondern über diese Benutzeroberfläche neue Datensätze aus Abfragen erstellen. Diese Datensätze können mit dem Echtzeit-Kundenprofil von Adobe Experience Platform verknüpft oder als Eingabe für Adobe Experience Platform Data Science Workspace verwendet werden.

## PSQL-Client mit Query Service verbinden

Query Service unterstützt Clients mit einem Treiber für PostgreSQL. Dabei werden wir PSQL, eine Befehlszeilenschnittstelle, und Power BI oder Tableau verwenden. Stellen wir eine Verbindung zu PSQL her.

Klicken Sie auf **Anmeldedaten**.

![queries-select-configuration.png](./images/queries-select-configuration.png)

Daraufhin wird der Bildschirm unten angezeigt. Der Bildschirm &quot;Konfiguration&quot;enthält Serverinformationen und Anmeldedaten für die Authentifizierung bei Query Service. Zunächst konzentrieren wir uns auf die rechte Seite des Bildschirms, der einen Verbindungsbefehl für PSQL enthält. Klicken Sie auf die Schaltfläche Kopieren , um den Befehl in die Zwischenablage zu kopieren.

![copy-psql-connection.png](./images/copy-psql-connection.png)

Für Windows: Öffnen Sie die Befehlszeile, indem Sie die Windows-Taste drücken, Befehl eingeben und dann auf das Ergebnis Eingabeaufforderung klicken.

![open-command-quick.png](./images/open-command-prompt.png)

Für macOS: Öffnen Sie &quot;terminal.app&quot;über die Spotlight-Suche:

![open-terminal-osx.png](./images/open-terminal-osx.png)

Fügen Sie den Verbindungsbefehl ein, den Sie aus der Query Service-Benutzeroberfläche kopiert haben, und drücken Sie die Eingabetaste im Eingabeaufforderungsfenster:

Windows:

![command-quick-linked.png](./images/command-prompt-connected.png)

MacOS:

![command-quick-paste-osx.png](./images/command-prompt-paste-osx.png)

Sie sind jetzt mit Query Service über PSQL verbunden.

In den nächsten Übungen wird es eine gewisse Interaktion mit diesem Fenster geben. Dies wird als Ihre **PSQL-Befehlszeilenschnittstelle** bezeichnet.

Jetzt können Sie mit dem Senden von Abfragen beginnen.

Nächster Schritt: [5.1.3 Verwenden des Abfragediensts](./ex3.md)

[Zurück zu Modul 5.1](./query-service.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
