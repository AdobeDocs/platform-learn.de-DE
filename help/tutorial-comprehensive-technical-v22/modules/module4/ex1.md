---
title: Query Service - Erste Schritte
description: Query Service - Erste Schritte
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: dae257d2-8c94-4558-b9ce-eca38a88667b
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---

# 4.1 Erste Schritte

## 4.1.1 Kennenlernen der Adobe Experience Platform-Benutzeroberfläche

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--module7sandbox--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](../module2/images/sb1.png)


## 4.1.2 Daten auf der Plattform durchsuchen

Daten aus verschiedenen Kanälen zu beziehen, ist für jede Marke eine schwierige Aufgabe. In dieser Übung interagieren Kunden von Citi Signal mit Citi Signal auf ihrer Website, über ihre mobile App werden Kaufdaten vom Point of Sale-System von Citi Signal erfasst und sie verfügen über CRM- und Loyalitätsdaten. Citi Signal verwendet Adobe Analytics und Adobe Launch, um Daten über seine Website, mobile App und POS-Systeme zu erfassen. Daher fließen diese Daten bereits in Adobe Experience Platform. Beginnen wir mit der Erforschung aller Daten für Citi Signal, die bereits in Adobe Experience Platform vorhanden sind.

Gehen Sie im linken Menü zu **Datensätze**.

![emea-website-interaction-dataset.png](./images/emea-website-interaction-dataset.png)

Citi Signal streamt Daten an Adobe Experience Platform, die im Abschnitt `Demo System - Event Dataset for Website (Global v1.1)` Datensatz. Suchen Sie nach `Demo System - Event Dataset for Website`.

![emea-callcenter-interaction-dataset.png](./images/emea-website-interaction-dataset1.png)

Die Callcenter-Interaktionsdaten von Citi Signal werden im `Demo System - Event Dataset for Call Center (Global v1.1)` Datensatz. Suchen Sie nach `Demo System - Event Dataset for Call Center` Daten in das Suchfeld ein. Klicken Sie auf den Namen des Datensatzes, um ihn zu öffnen.

![emea-callcenter-interaction-dataset.png](./images/emea-callcenter-interaction-dataset.png)

Nachdem Sie auf den Datensatz geklickt haben, erhalten Sie einen Überblick über die Datensatzaktivität, z. B. aufgenommene und fehlgeschlagene Batches.

![preview-interaction-dataset.png](./images/preview-interaction-dataset.png)

Klicken Sie auf **Vorschau eines Datensatzes anzeigen** um ein Beispiel der in gespeicherten Daten anzuzeigen `Demo System - Event Dataset for Call Center (Global v1.1)` Datensatz. Das linke Bedienfeld zeigt die Schemastruktur für diesen Datensatz an.

![explorer-interaction-dataset.png](./images/explore-interaction-dataset.png)

Klicken Sie auf **Schließen** Schaltfläche zum Schließen **Vorschau eines Datensatzes anzeigen** Fenster.

## 4.1.3 Einführung in Query Service

Auf den Adobe Experience Platform-Abfragedienst kann durch Klicken auf **Abfragen** im linken Menü.

![select-queries.png](./images/select-queries.png)

Indem Sie **Protokoll** sehen Sie die Seite &quot;Abfrageliste&quot;, die eine Liste aller Abfragen enthält, die in dieser Organisation ausgeführt wurden, wobei sich die neueste Seite oben befindet.

![query-list.png](./images/query-list.png)

Klicken Sie in der Liste auf eine SQL-Abfrage und beachten Sie die Details in der rechten Leiste.

![click-sql-query.png](./images/click-sql-query.png)

Sie können im Fenster einen Bildlauf durchführen, um die gesamte Abfrage anzuzeigen, oder auf das unten hervorgehobene Symbol klicken, um die gesamte Abfrage in Ihr Notebook zu kopieren. Sie müssen die Abfrage derzeit nicht kopieren.

![click-copy-query.png](./images/click-copy-query.png)

Sie können nicht nur die ausgeführten Abfragen sehen, sondern über diese Benutzeroberfläche neue Datensätze aus Abfragen erstellen. Diese Datensätze können mit dem Echtzeit-Kundenprofil von Adobe Experience Platform verknüpft oder als Eingabe für Adobe Experience Platform Data Science Workspace verwendet werden.

## 4.1.4 PSQL-Client mit Query Service verbinden

Query Service unterstützt Clients mit einem Treiber für PostgreSQL. Dabei werden wir PSQL, eine Befehlszeilenschnittstelle, und Power BI oder Tableau verwenden. Stellen wir eine Verbindung zu PSQL her.

Klicken Sie auf **Anmeldeinformationen**.

![queries-select-configuration.png](./images/queries-select-configuration.png)

Daraufhin wird der Bildschirm unten angezeigt. Der Bildschirm &quot;Konfiguration&quot;enthält Serverinformationen und Anmeldedaten für die Authentifizierung bei Query Service. Zunächst konzentrieren wir uns auf die rechte Seite des Bildschirms, der einen Verbindungsbefehl für PSQL enthält. Klicken Sie auf die Schaltfläche Kopieren , um den Befehl in die Zwischenablage zu kopieren.

![copy-psql-connection.png](./images/copy-psql-connection.png)

Windows: Öffnen Sie die Befehlszeile, indem Sie die Windows-Taste drücken, Befehl eingeben und auf das Ergebnis der Eingabeaufforderung klicken.

![open-command-quick.png](./images/open-command-prompt.png)

Für macOS: Öffnen Sie &quot;terminal.app&quot;über die Spotlight-Suche:

![open-terminal-osx.png](./images/open-terminal-osx.png)

Fügen Sie den Verbindungsbefehl ein, den Sie aus der Query Service-Benutzeroberfläche kopiert haben, und drücken Sie die Eingabetaste im Eingabeaufforderungsfenster:

Windows:

![command-quick-linked.png](./images/command-prompt-connected.png)

MacOS:

![command-quick-paste-osx.png](./images/command-prompt-paste-osx.png)

Sie sind jetzt mit Query Service über PSQL verbunden.

In den nächsten Übungen wird es eine gewisse Interaktion mit diesem Fenster geben. Wir werden es als Ihre **PSQL-Befehlszeilenschnittstelle**.

Jetzt können Sie mit dem Senden von Abfragen beginnen.

Nächster Schritt: [4.2 Query Service verwenden](./ex2.md)

[Zurück zu Modul 4](./query-service.md)

[Zu allen Modulen zurückkehren](../../overview.md)
