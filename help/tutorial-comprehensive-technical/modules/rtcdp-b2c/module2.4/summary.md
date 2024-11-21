---
title: Audience Activation zu Microsoft Azure Event Hub - Übersicht und Vorteile
description: Audience Activation zu Microsoft Azure Event Hub - Übersicht und Vorteile
kt: 5342
doc-type: tutorial
exl-id: 3b598ffc-875e-468d-b91c-882062e8203f
source-git-commit: 216914c9d97827afaef90e21ed7d4f35eaef0cd3
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---

# Zusammenfassung und Vorteile

Herzlichen Glückwunsch und vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über Microsoft Azure Event Hub und Adobe Experience Platform zu erfahren!
In diesem Modul haben Sie erfahren, wie Sie eine Azure Event Hub-Instanz einrichten und diese mit Adobe Experience Platform verbinden.

## Vorteile

Lassen Sie uns die Vorteile der Integration von Adobe Experience Platform mit Microsoft Azure Event Hub hervorheben:

- Mit Microsoft Azure Event Hub as a Adobe Experience Platform Destination können Sie die Zielgruppenqualifizierung in Echtzeit erfassen und mithilfe einer Azure Event Hub-Funktion verarbeiten. Mit einer solchen Azure Event Hub-Funktion können Sie eine beliebige Art von benutzerdefinierten Zielgruppen-Aktivierungs-Handler erstellen und als solche jede Art von Ziel von Drittanbietern integrieren.

- Ziele werden zwar nur durch bestimmte Zielgruppen ausgelöst, doch enthält die Aktivierungs-Payload alle Zielgruppen, für die sich das jeweilige Profil qualifiziert.

- Eine Zielgruppe Trigger nur dann eine Aktivierung, wenn sich ihr Status ändert. Wenn beispielsweise ein Profil in einem Zeitraum von drei Monaten viermal für eine Zielgruppe qualifiziert ist, werden nur die ersten beiden aktiviert. Die erste ist eine Statusänderung von zu **realisiert**, die zweite wird durch eine Statusänderung von **realisiert** zu **existierend** ausgelöst.

- Beim Aktivieren von Zielgruppen für bekannte Profile wird eine vollständige Identitätszuordnung in die Aktivierungs-Payload eingefügt. Ihre Azure-Funktion kann eine der verfügbaren Identitäten verwenden, um die Zielgruppen einem in einer Drittanbieteranwendung verwalteten Profil zuzuordnen, während die Kunden-ID der Anwendung verwendet wird.

- In diesem Modul wurde die Ereignis-Hub-Funktion lokal bereitgestellt (Debug-Modus in Visual Studio Code) und bietet Ihnen zahlreiche Fehlerbehebungs- und Debugoptionen.

## Sehen Sie sich das an

- K. A.

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
