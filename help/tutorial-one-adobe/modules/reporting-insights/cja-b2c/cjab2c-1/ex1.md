---
title: Customer Journey Analytics - Customer Journey Analytics 101
description: Customer Journey Analytics - Customer Journey Analytics 101
kt: 5342
doc-type: tutorial
exl-id: ea1469a4-cbfd-4633-8678-9467c2146a2a
source-git-commit: 1e3a8d585503eddad4c642a3b13d2b5f7ddc9943
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 1%

---

# 1.1.1 Customer Journey Analytics 101

## Ziele

- Grundlegendes zum CJA-Programm-Service
- Informationen zur Positionierung von CJA
- Grundlegendes zum CJA-Workflow: von der Datenverbindung zu Einblicken

## 1.1.1.1 Was ist Customer Journey Analytics?

Customer Journey Analytics (CJA) bietet den Business Intelligence- und Datenwissenschafts-Teams ein Toolkit zum Zusammenfügen und Analysieren kanalübergreifender Daten (online und offline). Die Funktionen in CJA bieten Kontext und Klarheit für die komplexe Multi-Channel-Kunden-Journey. Der bereitgestellte Kontext bietet praktische Einblicke in die Beseitigung von Schwachstellen im Kundenkonvertierungsprozess und die Entwicklung und Bereitstellung außergewöhnlicher Erlebnisse für die Momente, die am wichtigsten sind.

CJA bringt Analysis Workspace auf Adobe Experience Platform. Adobe Experience Platform ist das Gehirn für Kommunikation und Orchestrierung. Mit CJA können Marken nun all diese Daten kontextualisieren und visualisieren, sodass Geschäfts- und Insight-Teams daraus lernen können, indem sie das vollständige Online- bis Offline-Kunden-Journey analysieren.

Business- und Insight-Teams können mit CJA sprechen, Fragen stellen und mit der Drag-and-Drop-, Point-and-Click- und benutzerfreundlichen Benutzeroberfläche von Analysis Workspace spontan Antworten erhalten.

![demo](./images/cja-adv-analysis1.png)

## 1.1.1.2 Die wichtigsten Vorteile

Die drei Hauptvorteile für Kunden sind:

- Die Möglichkeit, Einblicke für alle verfügbar zu machen (d. h. den Datenzugriff zu demokratisieren)
- Die Möglichkeit, den Kunden in einer kontextuellen Journey zu sehen (d. h. Daten können sequenziell visualisiert werden, wobei sich mehrere Kanäle sowohl online als auch offline erstrecken)
- Die Möglichkeit, die Leistungsfähigkeit von Daten ohne die Notwendigkeit von zu nutzen (d. h., sie ermöglicht es normalen Menschen, Daten zu verwenden, um tiefe Einblicke und Analysen für die Marketing-Aktivierung zu erschließen)

## 1.1.1.3 Warum Customer Journey Analytics?

CJA ist nicht dazu gedacht, eine aktuelle BI-Anwendung wie Power BI, Microstrategy, Locker oder Tableau zu ersetzen. Diese BI-Anwendungen sollen Daten visualisieren, um Unternehmens-Dashboards zu erstellen, damit sich jeder in einer Organisation schnell wichtige Metriken ansehen kann.\
Das Ziel von CJA ist es, Marketing- und Business-Teams Analysefähigkeiten zu bieten, sodass es ein unverzichtbares Analyse-Tool für diese Personas ist.

Bisher waren BI-Anwendungen nicht in der Lage, echte Kundenanalyse zu ermöglichen:

- Sie können keine Attribution durchführen und keine Journey-Analyse auf Kundenseite durchführen.
- BI-Anwendungen müssen die Frage im Voraus kennen
- Interaktive Abfragen sind durch die Datenbankstruktur eingeschränkt
- SQL-Kenntnisse sind erforderlich.
- BI-Anwendungen geben Ihnen nicht die Möglichkeit zu fragen, warum etwas passiert ist.
- BI-Anwendungen haben keine direkte Verbindung zu Kunden-Touchpoints.

Aus diesem Grund sind Geschäftsanwender und Analysten fast sofort in eine Sackgasse geraten, was die Analyse teuer, langsam, unflexibel und von den Aktionssystemen getrennt macht.

Mit CJA erhalten Sie eine 360-Grad-Ansicht des Kunden-Journey. Sie verwenden Offline- und Online-Daten und die richtigen Tools, um die Zeit bis zur Erkenntnis zu verkürzen, sodass Geschäftsanwender unabhängig sind, wenn es darum geht, zu verstehen, warum etwas passiert ist und wie darauf reagiert werden soll.

![demo](./images/cja-use-case.png)

## 1.1.1.4 Den Customer Journey Analytics-Workflow verstehen

Bevor Sie mit den nächsten Übungen beginnen, müssen Sie verstehen, welche Schritte erforderlich sind, um Daten von Adobe Experience Platform in CJA zu importieren, damit Sie sie visualisieren und detaillierte Einblicke erhalten können. Das nennen wir CJA-Workflow. Sehen wir uns das einmal an:

![demo](./images/cja-work-flow.jpg)

Bevor Sie mit den obigen Schritten beginnen, vergessen Sie nicht Schritt 0, der darin besteht, die in Adobe Experience Platform verfügbaren Daten zu verstehen.

**Müll rein, Müll raus.** erinnern? Sie müssen eine klare Vorstellung davon haben, welche Daten verfügbar sind und wie die Schemata in Adobe Experience Platform konfiguriert sind. Das Verständnis der Daten in Adobe Experience Platform erleichtert die Arbeit nicht nur im Datenverbindungsteil, sondern auch beim Erstellen von Visualisierungen und bei der Durchführung von Analysen.

## 1.1.1.5 Schritt 0: Grundlegendes zu Adobe Experience Platform-Schemata und -Datensätzen

Melden Sie sich über die folgende URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

Sehen Sie sich diese Schemata und Datensätze in Adobe Experience Platform an.

| Datensatz | Schema |
| ----------------- |-------------| 
| Demosystem - Ereignisdatensatz für eine Website (Global v1.1) | Demosystem - Ereignisschema für Website (Global v1.1) |
| Demosystem - Ereignisdatensatz für Callcenter (Global v1.1) | Demosystem - Ereignisschema für Callcenter (Global v1.1) |
| Demosystem - Ereignisdatensatz für Sprachassistenten (Global v1.1) | Demosystem - Ereignisschema für Sprachassistenten (Global v1.1) |

Stellen Sie sicher, dass Sie mindestens Folgendes überprüft haben:

- Identitäten: CRMID, Telefonnummer, ECID, E-Mail. Welche Identitäten sind die primären, welche die sekundären Identifikatoren?
Sie können die Kennungen finden, indem Sie ein Schema öffnen und die `--aepTenantId--.identification.core` des Objekts betrachten. Sehen Sie sich das Schema [Demosystem - Ereignisschema für Website (Global v1.1) an](https://experience.adobe.com/platform/schema).

![demo](./images/identity.png)

- Erkunden Sie das Commerce-Objekt im Schema [Demosystem - Ereignisschema für Website (Global v1.1)](https://experience.adobe.com/platform/schema).

![demo](./images/commerce.png)

- Vorschau für alle [Datensätze](https://experience.adobe.com/platform/dataset/browse?limit=50&amp;page=1&amp;sortDescending=1&amp;sortField=created) und Datenansicht

Sie können jetzt mit der Verwendung der Customer Journey Analytics-Benutzeroberfläche beginnen.

## Nächste Schritte

Navigieren Sie zu [1.1.2 Verbinden von Adobe Experience Platform-Datensätzen in Customer Journey Analytics](./ex2.md){target="_blank"}

Zurück zu [Customer Journey Analytics](./customer-journey-analytics-build-a-dashboard.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
