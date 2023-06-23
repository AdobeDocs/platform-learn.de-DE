---
title: Bootcamp - Customer Journey Analytics - Customer Journey Analytics 101
description: Bootcamp - Customer Journey Analytics - Customer Journey Analytics 101
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 587be8bc-8ebe-4f30-99d8-ba88ce40caf7
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 1%

---

# 4.1 Customer Journey Analytics 101

## Ziele

- Grundlegendes zum CJA Application Service
- Erfahren Sie, wie Sie CJA positionieren
- Erläuterung des CJA-Workflows: von Datenverbindung zu Einblicken

## 4.1.1 Was ist Customer Journey Analytics?

Customer Journey Analytics (CJA) bietet den Teams für Business Intelligence und Datenwissenschaften ein Toolkit für die Zuordnung und Analyse kanalübergreifender Daten (online und offline). Die Funktionen von CJA bieten Kontext und Klarheit für die komplexe Journey von Kunden mit mehreren Kanälen. Der bereitgestellte Kontext bietet praktische Einblicke in das Entfernen von Schmerzpunkten aus dem Kundenkonvertierungsprozess und das Entwerfen und Bereitstellen außergewöhnlicher Erlebnisse für die Momente, die am wichtigsten sind.

CJA bringt Analysis Workspace auf Adobe Experience Platform. Adobe Experience Platform ist das Gehirn für Kommunikation und Orchestrierung. Mit CJA können Marken jetzt all diese Daten kontextualisieren und visualisieren, sodass Geschäfts- und Insight-Teams daraus lernen können, indem sie die vollständige Online- bis Offline-Journey analysieren.

Mit der Drag-and-Drop-, Point-and-Click- und benutzerfreundlichen Benutzeroberfläche von Analysis Workspace können Geschäfts- und Insight-Teams direkt mit CJA sprechen, Fragen stellen und Antworten direkt erhalten.

![Demo](./images/cja-adv-analysis1.png)

## 4.1.2 Hauptvorteile

Die drei Hauptvorteile für Kunden sind:

- Möglichkeit, Einblicke für alle verfügbar zu machen (d. h. Demokratisierung des Datenzugriffs)
- Möglichkeit, den Kunden in einer kontextuellen Journey zu sehen (d. h. Daten können sequenziell über mehrere Online- und Offline-Kanäle hinweg visualisiert werden)
- Die Fähigkeit, die Leistungsfähigkeit von Daten ohne Notwendigkeit zu nutzen (d. h. sie ermöglicht normalen Menschen die Nutzung von Daten, um tiefe Einblicke zu gewinnen und Analysen für die Marketing-Aktivierung zu erstellen)

## 4.1.3 Warum Customer Journey Analytics wählen?

CJA soll keine aktuelle BI-Anwendung wie Power BI, Microstrategy, Locker oder Tableau ersetzen. Diese BI-Anwendungen sollen Daten visualisieren, um Unternehmens-Dashboards zu erstellen, sodass alle Mitarbeiter in einem Unternehmen wichtige Metriken schnell betrachten können.\
Das Ziel von CJA besteht darin, Marketing- und Unternehmensteams Analysefunktionen bereitzustellen, damit diese Analysefunktionen für diese Personen &quot;dringend erforderlich&quot;sind.

Traditionell waren BI-Anwendungen nicht in der Lage, echte Customer Intelligence zu ermöglichen:

- Sie können keine Attribution vornehmen und keine Journey-Analyse von Kunden durchführen.
- BI-Anwendungen müssen die Frage frühzeitig kennen
- Interaktive Abfragen sind durch die Struktur der Datenbank beschränkt.
- SQL-Kenntnisse sind erforderlich.
- BI-Anwendungen geben Ihnen nicht die Möglichkeit zu fragen, warum etwas passiert ist.
- BI-Anwendungen haben keine direkte Verbindung zu Kunden-Touchpoints.

Aus den oben genannten Gründen treffen Geschäftsbenutzer und Analysten fast sofort auf die Sackgasse, was die Analyse teuer, langsam, unflexibel und von den Aktionssystemen getrennt macht.

Mit CJA können Sie eine 360-Grad-Sicht auf die Journey der Kunden haben, indem Sie Offline- und Online-Daten nutzen, mit den richtigen Tools, um die Zeit für Einblicke zu verkürzen, Geschäftsbenutzer unabhängig davon zu machen, warum etwas passiert ist und wie sie darauf reagieren.

![Demo](./images/cja-use-case.png)

## 4.1.4 Customer Journey Analytics-Workflow verstehen

Bevor Sie mit den nächsten Übungen beginnen, müssen Sie wissen, welche Schritte unternommen werden müssen, um Daten aus Adobe Experience Platform in Customer Journey Analytics zu übertragen, um sie zu visualisieren und einige tiefe Einblicke zu erhalten. Das nennen wir CJA-Workflow. Sehen wir uns das einmal an:

![Demo](./images/cja-work-flow.jpg)

Bevor Sie mit den oben genannten Schritten beginnen, vergessen Sie Schritt 0, der darin besteht, die in Adobe Experience Platform verfügbaren Daten zu verstehen.

**Müll hinein, Müll raus.** Erinnern Sie sich? Sie müssen genau wissen, welche Daten verfügbar sind und wie die Schemas in Adobe Experience Platform konfiguriert sind. Das Verständnis der Daten in Adobe Experience Platform wird die Dinge nicht nur im Bereich der Datenverbindung, sondern auch beim Erstellen von Visualisierungen und beim Analysieren vereinfachen.

## 4.1.5 Schritt 0: Grundlegendes zu Adobe Experience Platform-Schemata und -Datensätzen

Melden Sie sich über diese URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../uc1/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``Bootcamp``. Klicken Sie hierzu auf den Text **[!UICONTROL Prod]** in der oberen rechten Ecke des Bildschirms. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](../uc1/images/sb1.png)

Sehen Sie sich diese Schemata und Datensätze in Adobe Experience Platform an.

| Datensatz | Schema |
| ----------------- |-------------| 
| Demosystem - Ereignis-Datensatz für Website (Global v1.1) | Demosystem - Ereignisschema für Website (Global v1.1) |
| Demosystem - Ereignis-Datensatz für das Callcenter (Global v1.1) | Demosystem - Ereignisschema für das Callcenter (Global v1.1) |
| Demosystem - Ereignis-Datensatz für Sprachassistenten (Global v1.1) | Demosystem - Ereignisschema für Sprachassistenten (Global v1.1) |

Stellen Sie sicher, dass zumindest Folgendes überprüft wurde:

- Identitäten: CRMID, phoneNumber, ECID, email. Welche Identitäten sind die primären Identifikatoren, welche sind die sekundären Identifikatoren?
Sie können die Kennungen finden, indem Sie ein Schema öffnen und sich das Objekt ansehen `_experienceplatform.identification.core`. Sehen Sie sich das Schema an [Demosystem - Ereignisschema für Website (Global v1.1)](https://experience.adobe.com/platform/schema).

![Demo](./images/identity.png)

- Commerce-Objekt im Schema durchsuchen [Demosystem - Ereignisschema für Website (Global v1.1)](https://experience.adobe.com/platform/schema).

![Demo](./images/commerce.png)

- Vorschau aller [Datensätze](https://experience.adobe.com/platform/dataset/browse?limit=50&amp;page=1&amp;sortDescending=1&amp;sortField=created) und sehen Sie sich die Daten an

Sie können jetzt mit der Verwendung der Customer Journey Analytics-Benutzeroberfläche beginnen.

Nächster Schritt: [4.2 Adobe Experience Platform-Datensätze in Customer Journey Analytics verbinden](./ex2.md)

[Zurück zum Benutzerfluss 4](./uc4.md)

[Zu allen Modulen zurückkehren](../../overview.md)
