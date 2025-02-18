---
title: Veröffentlichen der Migration in der Staging- und Produktionsumgebung
description: Wenn die gesamte Entwicklung für die Migration abgeschlossen und validiert ist, erstellen Sie in der Staging-Umgebung und veröffentlichen Sie dann in der Produktionsumgebung, wenn Sie bereit sind.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16767
exl-id: 47c86999-6a9c-4451-8a59-475e8c65ab6a
source-git-commit: 3084590685bee9cd139c27b9a27026f08abf897f
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# Veröffentlichen der Migration in der Staging- und Produktionsumgebung

Wenn die gesamte Entwicklung für die Migration abgeschlossen und validiert ist, erstellen Sie in der Staging-Umgebung und veröffentlichen Sie dann in der Produktionsumgebung, wenn Sie bereit sind.

## Übersicht

Dies ist wirklich der letzte Hauptschritt Ihrer Migration. Sie müssen die Bibliothek, die Sie zum Entwickeln und Testen Ihrer Migration verwendet haben, in Ihre Staging-Umgebung verschieben, um sie dort endgültig zu testen, und dann in die Produktionsumgebung.

Wenn Sie zur Lektion [Erstellen und Konfigurieren eines Datenstroms](create-and-configure-the-analytics-datastream.md) zurückkehren, sehen Sie am Ende, dass wir auf den Staging-Datenstrom verwiesen haben, um die Analysedaten an dieselbe Entwicklungs-Report Suite (oder alternativ an eine neue Staging-Report Suite) zu senden. Sie werden dort auch daran erinnert, dass wir auf den Produktionsdatenstrom verwiesen haben, um Daten an die vorhandene Produktions-Report-Suite zu senden, die Sie verwendet haben.
Dies sind nur gute Informationen, da wir nun die migrierte Bibliothek auf dem Veröffentlichungspfad in die Staging- und Produktionsumgebung verschieben.

## Pushen in Staging- und Produktionsumgebungen

Im Folgenden finden Sie die Schritte, die unsere Bibliothek in Staging- und Produktionsumgebungen bringen:

1. Wählen Sie in der Benutzeroberfläche „Tags“ im linken Navigationsbereich Veröffentlichungsfluss aus.
1. Ihre Migrationsbibliothek sollte nun unter Entwicklung angezeigt werden (wobei der Name dem entspricht, den Sie zu Beginn dieses Migrationsprozesses ausgewählt haben)

   ![Migrationsbibliothek in der Entwicklung](assets/migration-lib-in-dev.jpg)

1. Wenn Sie sicher sind, dass Sie bereits jede einzelne Änderung an der Bibliothek vorgenommen haben, können Sie die Bibliothek unter den drei Punkten nach vorne verschieben und die nächsten Schritte überspringen. Wenn Sie sich nicht sicher sind, führen Sie die nächsten fünf Schritte aus.
1. Klicken Sie auf den Bibliotheksnamen, um die Bibliotheksdetails anzuzeigen
1. Stellen Sie über den Namen sicher, dass Sie sich in der richtigen Bibliothek befinden
1. Wählen Sie Alle geänderten Ressourcen hinzufügen unten auf der Seite aus.
1. Klicken Sie dann auf Speichern und in Entwicklung erstellen , um alle Änderungen in der Warteschlange zur Bibliothek hinzuzufügen

   ![Alle geänderten Ressourcen hinzufügen](assets/add-all-changed-resources.jpg)

1. Dadurch gelangen Sie zurück in die Oberfläche des Veröffentlichungsflusses. Wenn der Build erfolgreich abgeschlossen wurde, wird neben Ihrer Bibliothek ein grüner Punkt angezeigt.
1. Anschließend können Sie Ihre Bibliothek je nach Bedarf im Veröffentlichungsprozess weiterleiten. Sie können ihn für Genehmigungen einstellen, direkt in die Staging-Umgebung verschieben, um dort zu testen und zu genehmigen, oder ihn sogar zur Genehmigung verschieben oder direkt in der Produktion veröffentlichen. Dies hängt wiederum von den Veröffentlichungsanforderungen in Ihrer Organisation ab.

   ![Veröffentlichungsprozess](assets/publishing-process.jpg)

Herzlichen Glückwunsch! Zu diesem Zeitpunkt befindet sich Ihre Analytics-Implementierung vollständig auf der Web-SDK!

Ich füge hier einen wichtigen Hinweis hinzu, den wir am Anfang dieses Tutorials hatten:

>[!IMPORTANT]
>
>Beachten Sie, dass einer der Hauptgründe für diese Migration Ihrer Implementierung die Vorbereitung auf die Verwendung von Adobe Experience Platform-Programmen wie Customer Journey Analytics, Real-Time CDP oder Journey Optimizer ist. Die Verwendung Ihrer Website-Daten zu diesem Zweck umfasst zusätzliche Schritte, die in diesem Tutorial nicht enthalten sind, aber dieses Tutorial ist sicherlich eine Voraussetzung für diesen weiteren Fortschritt Ihrer Implementierung. Nachdem Sie dieses Tutorial abgeschlossen haben, können Sie nun die Schritte ausführen, die erforderlich sind, um dieselben Website-Daten auch an Experience Platform zu senden.

Viel Glück auf Ihrem Journey mit Analytics und anderen Inhalts- und Marketingbemühungen!
