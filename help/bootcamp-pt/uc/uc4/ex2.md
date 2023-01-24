---
title: Bootcamp - Customer Journey Analytics - Adobe Experience Platform-Datensätze in Customer Journey Analytics verbinden - Brasilien
description: Bootcamp - Customer Journey Analytics - Adobe Experience Platform-Datensätze in Customer Journey Analytics verbinden - Brasilien
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
source-git-commit: 75a878ba596078e6d013b65062606931402302dd
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 3%

---

# 4.2 Adobe Experience Platform-Datensätze in Customer Journey Analytics verbinden

## Ziele

- Grundlegendes zur Benutzeroberfläche der Datenverbindung
- Einbinden von Adobe Experience Platform-Daten in CJA
- Personen-ID und Datenzuordnung verstehen
- Erfahren Sie mehr über das Konzept des Daten-Streaming in Customer Journey Analytics

## 4.2.1 Verbindung

Navigieren Sie zu [analytics.adobe.com](https://analytics.adobe.com) , um auf Customer Journey Analytics zuzugreifen.

Gehen Sie auf der Customer Journey Analytics-Homepage zu **Verbindungen**.

![Demo](./images/cja2.png)

Hier sehen Sie alle Verbindungen, die zwischen CJA und Platform hergestellt wurden. Diese Verbindungen haben dasselbe Ziel wie Report Suites in Adobe Analytics. Die Erfassung der Daten ist jedoch völlig anders. Alle Daten stammen aus Adobe Experience Platform-Datensätzen.

Erstellen wir Ihre erste Verbindung. Klicken Sie auf **Neue Verbindung erstellen**.

![Demo](./images/cja4.png)

Sie werden dann die **Verbindung erstellen** Benutzeroberfläche.

![Demo](./images/cja5.png)

Jetzt können Sie Ihrer Verbindung einen Namen geben.

Bitte verwenden Sie diese Namenskonvention: `yourLastName – Omnichannel Data Connection`.

Beispiel: `vangeluw - Omnichannel Data Connection`

Sie müssen auch die richtige Sandbox auswählen, die verwendet werden soll. Wählen Sie im Sandbox-Menü Ihre Sandbox aus, die `Bootcamp`. In diesem Beispiel lautet die zu verwendende Sandbox **Bootcamp**. Außerdem müssen Sie die **Durchschnittliche Anzahl der täglichen Ereignisse** nach **weniger als 1 Million**.

![Demo](./images/cjasb.png)

Nachdem Sie Ihre Sandbox ausgewählt haben, können Sie damit beginnen, dieser Verbindung Datensätze hinzuzufügen. Klicken **Hinzufügen von Datensätzen**.

![Demo](./images/cjasb1.png)

## 4.2.2 Adobe Experience Platform-Datensätze auswählen

Suche nach dem Datensatz `Demo System - Event Dataset for Website (Global v1.1)`. Klicken **+** , um den Datensatz zu dieser Verbindung hinzuzufügen.

![Demo](./images/cja7.png)

Suchen Sie jetzt und aktivieren Sie die Kontrollkästchen für `Demo System - Event Dataset for Voice Assistants (Global v1.1)` und `Demo System - Event Dataset for Call Center (Global v1.1)`.

Dann wirst du das haben. Klicken Sie auf **Weiter**.

![Demo](./images/cja9.png)

## 4.2.3 Personen-ID und Datenzuordnung

### Personen-ID

Das Ziel besteht nun darin, sich diesen Datensätzen anzuschließen. Für jeden ausgewählten Datensatz wird ein Feld namens **Personen-ID**. Jeder Datensatz verfügt über ein eigenes Personen-ID-Feld.

![Demo](./images/cja11.png)

Wie Sie sehen können, ist bei den meisten Benutzern automatisch die Personen-ID ausgewählt. Dies liegt daran, dass in jedem Schema in Adobe Experience Platform eine Primäre Kennung ausgewählt ist. Hier finden Sie beispielsweise das Schema für `Demo System - Event Schema for Call Center (Global v1.1)`, wo Sie sehen können, dass die Primäre Kennung auf `phoneNumber`.

![Demo](./images/cja13.png)

Sie können jedoch weiterhin beeinflussen, welche Kennung zum Zuordnen von Datensätzen für Ihre Verbindung verwendet wird. Sie können jede beliebige Kennung verwenden, die im mit Ihrem Datensatz verknüpften Schema konfiguriert ist. Klicken Sie auf das Dropdown-Menü, um die für jeden Datensatz verfügbaren IDs zu untersuchen.

![Demo](./images/cja14.png)

Wie bereits erwähnt, können Sie für jeden Datensatz verschiedene Personen-IDs festlegen. Auf diese Weise können Sie verschiedene Datensätze aus mehreren Quellen in CJA zusammenführen. Stellen Sie sich vor, Sie würden NPS- oder Umfragedaten einbringen, die sehr interessant und hilfreich wären, um den Kontext und die Gründe zu verstehen, warum etwas passiert ist.

Der Name des Felds Personen-ID ist nicht wichtig, solange der Wert in den Feldern Personen-ID übereinstimmt. Sagen wir, wir haben `email` in einem Datensatz und `emailAddress` in einem anderen Datensatz, der als Personen-ID definiert ist. Wenn `delaigle@adobe.com` denselben Wert für das Personen-ID-Feld in beiden Datensätzen hat, kann CJA die Daten zuordnen.

Derzeit gibt es einige andere Einschränkungen, wie die Zuordnung des anonymen Verhaltens zu bekannt. Lesen Sie die häufig gestellten Fragen hier: [FAQs](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-faq.html?lang=de).

### Daten mithilfe der Personen-ID zuordnen

Nachdem Sie nun das Konzept der Zuordnung von Datensätzen mit der Personen-ID kennen, wählen Sie `email` als Personen-ID für jeden Datensatz.

![Demo](./images/cja15.png)

Gehen Sie zu jedem Datensatz, um die Personen-ID zu aktualisieren.

![Demo](./images/cja12a.png)

Füllen Sie nun das Feld Personen-ID aus, das die `email` in der Dropdown-Liste.

![Demo](./images/cja17.png)

Sobald Sie die drei Datensätze zugeordnet haben, können wir fortfahren.

| Datensatz | Personen-ID |
| ----------------- |-------------| 
| Demosystem - Ereignis-Datensatz für Website (Global v1.1) | email |
| Demosystem - Ereignis-Datensatz für Sprachassistenten (Global v1.1) | email |
| Demosystem - Ereignis-Datensatz für das Callcenter (Global v1.1) | email |

Sie müssen außerdem sicherstellen, dass diese Optionen für jeden Datensatz aktiviert sind:

- Alle neuen Daten importieren
- Alle vorhandenen Daten aufstocken

Klicken **Hinzufügen von Datensätzen**.

![Demo](./images/cja16.png)

Klicken **Speichern** und gehen Sie zur nächsten Übung.
Nachdem Sie die **Verbindung** Es kann einige Stunden dauern, bis Ihre Daten in Customer Journey Analytics verfügbar sind.

![Demo](./images/cja20.png)

Nächster Schritt: [4.3 Datenansicht erstellen](./ex3.md)

[Zurück zum Benutzerfluss 4](./uc4.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
