---
title: Adobe Experience Platform-Datenerfassung und Echtzeit-Ereignisweiterleitung - Erstellen einer Adobe Experience Platform-Eigenschaft zur Ereignisweiterleitung für Datenerfassung
description: Erstellen einer Adobe Experience Platform-Eigenschaft zur Ereignisweiterleitung für die Datenerfassung
kt: 5342
doc-type: tutorial
exl-id: 9c64e57d-c91c-4d4c-923f-91a02edeb2ac
source-git-commit: b4a7144217a68bc0b1bc70b19afcbc52e226500f
workflow-type: tm+mt
source-wordcount: '737'
ht-degree: 1%

---

# 2.5.1 Erstellen einer Adobe Experience Platform-Eigenschaft zur Ereignisweiterleitung für die Datenerfassung

## Was ist die Eigenschaft &quot;Adobe Experience Platform Data Collection Event Forwarding&quot;?

Wenn Daten mit der Adobe Experience Platform-Datenerfassung erfasst werden, werden sie in der Regel auf der **Client-Seite** erfasst. Die clientseitige **ist eine Umgebung wie eine Website oder eine Mobile App.** In Erste Schritte und Datenerfassung wurde die Konfiguration einer Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft ausführlich besprochen und Sie haben diese Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft in Ihre Website und Mobile App implementiert, sodass dort Daten erfasst werden konnten, wenn ein Kunde mit der Website und Mobile App interagierte.

Wenn diese Interaktionsdaten von der Adobe Experience Platform-Datenerfassungs-Client-Eigenschaft erfasst werden, wird eine Anforderung von der Website oder mobilen App an Adobe Edge gesendet. Die Edge ist die Adobe-Datenerfassungsumgebung und der Einstiegspunkt für Clickstream-Daten in das Adobe-Ökosystem. Diese erfassten Daten werden dann aus der Edge an Anwendungen wie Adobe Experience Platform, Adobe Analytics, Adobe Audience Manager oder Adobe Target gesendet.

Mit der Eigenschaft &quot;Adobe Experience Platform Data Collection Event Forwarding&quot;kann jetzt eine Adobe Experience Platform-Datenerfassungseigenschaft konfiguriert werden, die eingehende Daten in Edge überwacht. Wenn die in Edge ausgeführte Adobe Experience Platform-Eigenschaft zur Datenerfassungs-Ereignisweiterleitung eingehende Daten anzeigt, können diese Daten verwendet und an eine andere Stelle weitergeleitet werden. Diese andere Stelle kann nun auch ein externer Webhook sein, der keine Adobe ist und es ermöglicht, diese Daten beispielsweise an Ihren gewünschten Data Lake, eine Entscheidungsanwendung oder eine andere Anwendung zu senden, die in der Lage ist, einen Webhook zu öffnen.

Die Konfiguration einer Adobe Experience Platform-Eigenschaft zur Ereignisweiterleitung für Datenerfassung sieht einer clientseitigen Eigenschaft vertraut aus, mit der Datenelemente und Regeln so konfiguriert werden können, wie es früher mit den Adobe Experience Platform-Datenerfassungs-Client-Eigenschaften der Fall war. Die Art und Weise, wie Daten aufgerufen und verwendet werden, unterscheidet sich jedoch je nach Anwendungsfall geringfügig.

Beginnen wir mit der Erstellung der Adobe Experience Platform-Eigenschaft für die Ereignisweiterleitung zur Datenerfassung.

## Erstellen einer Adobe Experience Platform-Eigenschaft zur Ereignisweiterleitung für Datenerfassung

Wechseln Sie zu [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Klicken Sie im linken Menü auf **Ereignisweiterleitung**. Daraufhin wird eine Übersicht über alle verfügbaren Eigenschaften der Adobe Experience Platform-Datenerfassungs-Ereignisweiterleitung angezeigt. Klicken Sie auf die Schaltfläche **Eigenschaft erstellen** .

![Adobe Experience Platform-Datenerfassung SSF](./images/launchhome.png)

Wenn andere Eigenschaften für die Ereignisweiterleitung bereits erstellt wurden, sieht die Benutzeroberfläche etwas anders aus. Klicken Sie in diesem Fall auf **Neue Eigenschaft**.

![Adobe Experience Platform-Datenerfassung SSF](./images/launchhomea.png)

Sie müssen nun einen Namen für Ihre Adobe Experience Platform-Eigenschaft zur Ereignisweiterleitung für die Datenerfassung eingeben. Verwenden Sie als Namenskonvention `--aepUserLdap-- - Demo System (DD/MM/YYYY) (Edge)`. In diesem Beispiel lautet der Name beispielsweise &quot;**vangeluw - Demo System (22/02/2022) (Edge)**&quot;. Klicken Sie auf **Speichern**.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf1.png)

Sie befinden sich dann wieder in der Liste der Eigenschaften für die Adobe Experience Platform-Datenerfassungs-Ereignisweiterleitung. Klicken Sie auf , um die soeben erstellte Eigenschaft zu öffnen.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf2.png)

## Adobe Cloud Connector-Erweiterung konfigurieren

Navigieren Sie im linken Menü zu **Erweiterungen**. Sie werden sehen, dass die Erweiterung **Core** bereits konfiguriert ist.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf3.png)

Wechseln Sie zu **Katalog**. Neben vielen anderen wird die Erweiterung **Adobe Cloud Connector** angezeigt. Klicken Sie auf **Installieren**, um es zu installieren.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf4.png)

Die Erweiterung wird dann hinzugefügt. In diesem Schritt gibt es keine Konfiguration. Sie werden zurück zur Übersicht der installierten Erweiterungen geleitet.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf5.png)

## 2.5.1.3 Bereitstellen der Adobe Experience Platform-Eigenschaft zur Ereignisweiterleitung für die Datenerfassung

Wechseln Sie im linken Menü zu **Veröffentlichungsfluss**. Klicken Sie auf **Bibliothek hinzufügen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf6.png)

Geben Sie den Namen **Main** ein, wählen Sie die Umgebung **Entwicklung (Entwicklung)** aus und klicken Sie auf **+ Alle geänderten Ressourcen hinzufügen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf7.png)

Dann wirst du das sehen. Klicken Sie auf **Speichern und Build zur Entwicklung erstellen**.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf8.png)

Ihre Bibliothek wird dann erstellt, was 1-2 Minuten dauern kann.

![Adobe Experience Platform-Datenerfassung SSF](./images/ssf10.png)

Nächster Schritt: [2.5.2 Aktualisieren Sie Ihren Datenspeicher, um Daten für Ihre Datenerfassungs-Ereignisweiterleitungseigenschaft verfügbar zu machen](./ex2.md)

[Zurück zu Modul 2.5](./aep-data-collection-ssf.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
