---
title: Debuggen und Validieren der Web SDK-Migration
description: Erfahren Sie, wie Sie Ihre Daten bei der Migration zur Web-SDK debuggen und validieren
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16763
source-git-commit: 7ae56d997884cf1558e72c0ad553df1c5d43c081
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 0%

---


# Debuggen und Validieren der Web SDK-Migration

In dieser Übung erfahren Sie, wie Sie Ihre Daten bei der Migration zur Web-SDK debuggen und validieren. Wir möchten zwei verschiedene Validierungsaktivitäten empfehlen, mit denen Sie sicherstellen können, dass alles ordnungsgemäß verläuft:

1. **Validierungsaktivität #1** führt den -Adobe Experience Platform Debugger aus, bei dem es sich um eine Browser-Erweiterung handelt, und ermöglicht es Ihnen, die Art und Weise zu überprüfen, wie Ihre Daten korrekt an Analytics gesendet werden. Es wird empfohlen, diese Aktivität häufig durchzuführen, wenn Sie Änderungen an Ihrer Tags-Eigenschaft vornehmen und die Änderungen in einer Entwicklungsbibliothek veröffentlichen.
1. **Validierungsaktivität #2** wird in Adobe Analytics gestartet. Sie richten ein oder mehrere Projekte ein, um Daten aus dem Web-SDK zu empfangen (über die neu erstellte Migrationsbericht-Suite), und überprüfen, ob Ihre Daten tatsächlich korrekt in die Berichte gelangen, wenn Sie auf Ihre Site klicken usw.

## Der Adobe Experience Platform Debugger

Dieser Debugger ist eine Browser-Erweiterung und im Chrome Store verfügbar. Es gibt ein [Video-Tutorial](https://experienceleague.adobe.com/en/docs/platform-learn/data-collection/debugger/overview) in dem erläutert wird, wie Sie den Debugger herunterladen und verwenden. Es wird empfohlen, dies zuerst zu durchlaufen, um die grundlegende Verwendung zu erfahren.

Sobald der Debugger eingerichtet ist und ausgeführt wird, können Sie damit sicherstellen, dass die Daten ordnungsgemäß von Ihrer Site und durch das Edge Network fließen. Dieses Tutorial bleibt bei der ziemlich einfachen Verwendung, aber verwenden Sie den Debugger bitte nicht, um Ihre Daten mit voller Kapazität zu überprüfen.

**Annahme (immer gefährlich, aber in diesem Fall hoffentlich gut):** Da wir in diesem Beispiel die Tag-Eigenschaft in den Web-SDK migrieren, müssen wir keinen neuen Einbettungs-Code auf der Site einfügen. Es wird schon da gewesen sein. Wenn Sie sich jedoch entscheiden, mehr von einem „Lift and Shift“-Ansatz auf eine völlig neue Tag-Eigenschaft anzuwenden, verfügen Sie über neue Einbettungs-Codes, um Ihre Entwicklungs-, Staging- und Produktionsumgebungen zu verwenden. In diesem Tutorial werden die Daten im Debugger angezeigt, sofern die Web SDK-Erweiterung installiert und mit Regeln zum Senden von Daten konfiguriert ist.

### Anzeigen von Web SDK-Daten im Debugger

Nachdem Sie nun Ihre Standardseitenregel migriert haben (oder falls Sie Regeln migriert haben) und sie in einer Bibliothek in der Entwicklungsumgebung veröffentlicht haben, sollten Sie Ihre Site ausführen und die Daten in den Debugger fließen sehen können.

Schritte zum Anzeigen Ihrer Daten:

1. Öffnen Sie die Entwicklungsumgebung Ihrer Site im Browser
1. Öffnen Sie den Debugger, indem Sie auf die Browser-Erweiterung in der Erweiterungsleiste am oberen Rand Ihres Browser-Fensters klicken

   ![Debugger-Erweiterung](assets/debugger-extension.jpg)

   >[!TIP]
   >
   >In der rechten unteren Ecke des Debuggers befindet sich ein „Sperrsymbol“ und eine Beschriftung, und links davon können Sie sehen, welche Seite Sie debuggen. Klicken Sie auf Ihrer Site auf das Schlosssymbol, um den Debugger für das Fenster Ihrer Site zu sperren. Andernfalls würde der Debugger auf diese Site reagieren, wenn Sie auf eine andere Browser-Registerkarte/ein anderes Fenster klicken. Während des Debuggens Ihrer Site ist es einfach einfacher, sicherzustellen, dass der Debugger immer Informationen für Ihre Site bereitstellt.

1. Stellen Sie sicher, dass Sie sich auf der **Zusammenfassung** des Debuggers befinden (Home-Symbol oben links). **Aktualisieren Sie Ihre Site** im Browser-Fenster. Wenn der Debugger den Einbettungs-Code auf Ihrer Site erfasst und Sie den Analytics-Code nicht gelöscht haben (wie in diesem Tutorial), sehen Sie Hinweise darauf, dass es sowohl für Adobe Experience Platform Web SDK als auch für Adobe Analytics sowie für Adobe Experience Platform-Tags Code gab. Andere werden ausgegraut sein.

   ![Debugger-Zusammenfassung](assets/debugger-summary.jpg)

1. Um die über die Web-SDK hinzugefügten Daten anzuzeigen, klicken Sie auf den Link **Experience Platform Web-SDK** in der linken Leiste
1. Klicken Sie auf **Ereignisse löschen** nur um alle Treffer zu entfernen, die aufgetreten sind
1. Aktualisieren Sie Ihre Site erneut und kehren Sie zum Debugger zurück
1. Klicken Sie dann auf das Datenfeld neben **Ereignisse** in der Tabelle

   ![Feld Ereignisse im Debugger](assets/events-field-in-debugger.jpg)

1. Erweitern Sie im Feld Wert den Eintrag durch 0, data, __adobe und analytics.
1. Sie sollten die Variablen sehen, die Sie in den Regeln festlegen, die auf dieser Seite ausgelöst werden, einschließlich der standardmäßigen Seitenladeregel und aller speziellen Regeln.

   ![Datenobjekt im Debugger](assets/data-object-in-debugger.jpg)

1. Führen Sie diese Schritte immer dann aus, wenn Sie etwas in Ihrer Tags-Eigenschaft geändert und die Änderungen an der Entwicklung veröffentlicht haben, damit Sie die Auswirkungen der Änderungen sehen können, die Sie an Ihrer Analytics-Implementierung vorgenommen haben.

## Validieren von Daten in Analysis Workspace

Das Hauptziel dieser Empfehlung besteht darin, Ihre aktuellen Analysedaten aus Ihrer Tags-Implementierung mithilfe der Adobe Analytics-Erweiterung zu verwenden und mit den gleichen Berichten zu vergleichen, die jetzt vom Web-SDK gefüllt werden.
Es gibt vermutlich mehrere Möglichkeiten, diese Vergleiche durchzuführen, aber ich gebe Ihnen zwei Beispiele, wie man das macht.

### Option 1: Vergleichen der Daten mithilfe von zwei Bereichen in einem Projekt

1. Erstellen eines neuen Projekts in Analysis Workspace und Hinzufügen von zwei Bedienfeldern
1. Legen Sie die Report Suite im Bedienfeld 1 auf Ihre aktuelle Adobe Analytics Production Report Suite fest
1. Legen Sie die Report Suite in Bedienfeld 2 auf Ihre neue Web SDK Development-Report Suite fest
1. Fügen Sie denselben Bericht in beide Bedienfelder ein, indem Sie einen Zeitraum im Kalender verwenden, in dem die Daten mit beiden Erweiterungen in Analytics übertragen wurden
1. Vergleichen der Daten

Dies könnte in etwa so aussehen (wenn Sie verstehen, dass in diesen leeren Demo-Report-Suites keine Daten vorhanden sind):

![Report Suite-Nummern vergleichen](assets/compare-report-suite-numbers-panels.jpg)

Wie Sie sehen können, ist der Bericht in beiden Bereichen identisch und der Kalender ist auch identisch. Der Unterschied besteht in der Report Suite, wie in den obigen Schritten beschrieben.
**Vorteil dieser Option:** Sie können bei Änderungen in der Implementierung nacheinander Berichte/Dimensionen erstellen und genau testen, was Sie testen möchten.

### Option 2: Vergleichen der Daten mithilfe zweier Projekte

1. Öffnen Sie ein vorhandenes Projekt, das Ihre aktuellen Adobe Analytics-Erweiterungsdaten verwendet
1. Erstellen Sie eine Kopie dieses Projekts unter dem Namen „Speichern unter“ und benennen Sie es zum Beispiel „Web SDK Migration Validation Project“.
1. Ändern Sie die Report Suite für das kopierte Projekt so, dass es auf Ihre Web SDK Development Report Suite verweist
1. Öffnen Sie jedes Projekt in einem anderen Fenster und passen Sie die Größe so an, dass Sie sie auf dem Monitor nebeneinander sehen können
1. Vergleichen der Daten

Dies wird dem Bild oben sehr ähnlich sein, mit der Ausnahme, dass sich jedes Bedienfeld in einem eigenen Projekt und in einem anderen Fenster befindet.
**Vorteil dieser Option:** In diesem Fall müssen Sie nicht alle Berichte erneut hinzufügen und konfigurieren. Sie können jedoch sehen, wie Ihre aktuellen Berichte mithilfe der neuen Web SDK-Erweiterung und mit nur minimalem Setup aussehen werden.

Es ist möglich, dass Sie beides tun wollen, was auch eine andere großartige Option ist.

>[!IMPORTANT]
>
>Nachdem Sie die Validierung Ihrer standardmäßigen Seitenladeregel abgeschlossen haben, können Sie im Tutorial fortfahren. Wir bitten Sie jedoch dringend, häufig zu testen/validieren, wahrscheinlich mindestens jedes Mal, wenn Sie eine Regel ändern oder andere wichtige Änderungen vornehmen. Denken Sie daran, dass Sie, wenn Sie beim Voranschreiten ein Problem feststellen, glücklicher sein werden, wenn Sie nur EINE Sache überprüfen müssen, anstatt mehrere Änderungen zu testen, die Sie seit der letzten Validierung vorgenommen haben.

Validieren Sie gerne!
