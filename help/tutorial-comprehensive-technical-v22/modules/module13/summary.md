---
title: Segmentaktivierung für Microsoft Azure Event Hub - Zusammenfassung und Vorteile
description: Segmentaktivierung für Microsoft Azure Event Hub - Zusammenfassung und Vorteile
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 2174ac52-b5dd-4bc8-ab5f-4d84ae9ef19b
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# Zusammenfassung und Vorteile

Herzlichen Glückwunsch und vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über Microsoft Azure Event Hub und Adobe Experience Platform zu erfahren!
In diesem Modul haben Sie erfahren, wie Sie eine Azure Event Hub-Instanz einrichten und diese mit Adobe Experience Platform verbinden.

## Vorteile

Lassen Sie uns die Vorteile der Integration von Adobe Experience Platform mit Microsoft Azure Event Hub hervorheben:

- Mit Microsoft Azure Event Hub as a Adobe Experience Platform Destination können Sie die Segmentqualifizierung in Echtzeit erfassen und mithilfe einer Azure Event Hub-Funktion verarbeiten. Mit einer solchen Azure Event Hub-Funktion können Sie eine beliebige Art von benutzerdefinierten Segmentaktivierungs-Handler erstellen und daher jede Art von Ziel eines Drittanbieters integrieren.

- Ziele werden zwar nur durch bestimmte Segmente ausgelöst, die Aktivierungs-Payload enthält jedoch alle Segmente, für die ein bestimmtes Profil qualifiziert ist.

- Ein Segment wird nur dann aktiviert, wenn sich sein Status ändert. Wenn beispielsweise ein Profil in einem Zeitraum von drei Monaten viermal für ein Segment qualifiziert ist, werden nur die ersten beiden aktiviert. Die erste ist eine Statusänderung von zu **realisiert**, wird die zweite durch eine Statusänderung von **realisiert** nach **vorhandene**.

- Beim Aktivieren von Segmenten für bekannte Profile wird eine vollständige Identitätszuordnung in die Aktivierungs-Payload eingefügt. Ihre Azure-Funktion kann eine der verfügbaren Identitäten verwenden, um die Segmente einem in einer Drittanbieteranwendung verwalteten Profil zuzuordnen, während die Kunden-ID der Anwendung verwendet wird.

- In diesem Modul wurde die Ereignis-Hub-Funktion lokal bereitgestellt (Debug-Modus in Visual Studio Code) und bietet Ihnen zahlreiche Fehlerbehebungs- und Debugoptionen.

## Sehen Sie sich das an

- K. A.

[Zurück zu Modul 13](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
