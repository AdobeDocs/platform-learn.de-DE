---
title: Audience Activation zu Microsoft Azure Event Hub - Zusammenfassung und Vorteile
description: Audience Activation zu Microsoft Azure Event Hub - Zusammenfassung und Vorteile
kt: 5342
doc-type: tutorial
exl-id: f081af11-3ea0-47cc-ae74-24a0e0231d66
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 1%

---

# Zusammenfassung und Vorteile

Herzlichen Glückwunsch und vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Microsoft Azure Event Hub und Adobe Experience Platform zu erfahren!
In diesem Modul haben Sie gelernt, wie Sie eine Azure Event Hub-Instanz einrichten und wie Sie diese mit Adobe Experience Platform verbinden.

## Vorteile

Im Folgenden werden die Vorteile der Integration von Adobe Experience Platform mit dem Microsoft Azure Event Hub beschrieben:

- Mit Microsoft Azure Event Hubs als Adobe Experience Platform-Ziel können Sie die Zielgruppen-Qualifizierung in Echtzeit erfassen und mit einer Azure Event Hub-Funktion verarbeiten. Mit einer solchen Azure Event Hub-Funktion können Sie jede Art von benutzerdefiniertem Zielgruppen-Aktivierungs-Handler erstellen und als solche jede Art von Drittanbieterziel integrieren.

- Obwohl Ziele nur durch angegebene Zielgruppen ausgelöst werden, enthält die Aktivierungs-Payload alle Zielgruppen, für die das jeweilige Profil qualifiziert ist.

- Eine Zielgruppe führt nur dann Trigger zu einer Aktivierung aus, wenn sich ihr Status ändert. Beispiel: Bei einem Profil, das sich innerhalb von drei Monaten viermal für eine Zielgruppe qualifiziert, werden nur die ersten beiden aktiviert. Die erste ist eine Statusänderung von zu **realisiert** die zweite wird durch eine Statusänderung von **realisiert** zu **vorhanden** ausgelöst.

- Beim Aktivieren von Zielgruppen für bekannte Profile wird eine vollständige Identitätszuordnung in die Aktivierungs-Payload eingefügt. Ihre Azure-Funktion kann jede der verfügbaren Identitäten verwenden, um die Zielgruppen einem Profil zuzuordnen, das in einer Drittanbieteranwendung verwaltet wird, während die Kundenkennung der Anwendung verwendet wird.

- In diesem Modul wurde die Ereignis-Hub-Funktion lokal bereitgestellt (Debug-Modus in Visual Studio Code) und bietet Ihnen viele Fehlerbehebungs- und Debugoptionen.

## Hier ist alles

- K. A.

## Nächste Schritte

Zurück zu [Real-Time CDP: Audience Activation zum Microsoft Azure Event Hub](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
