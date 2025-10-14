---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Erläuterung der Adobe Experience Platform-Datenerfassung
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Erläuterung der Adobe Experience Platform-Datenerfassung
kt: 5342
doc-type: tutorial
exl-id: 098031c6-4d8b-46a5-ae86-8fd7692268d3
source-git-commit: 1526661a80b4d551627dfca42a7e97c9498dd1f2
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 3%

---

# 1.1.1 Grundlagen zur Datenerfassung in Adobe Experience Platform

## Kontext

Die Datenerfassung in Adobe Experience Platform wird von Marken für eine Reihe von Anwendungsfällen verwendet. Hierbei handelt es sich um ein Tag Management-System der nächsten Generation (TMS), mit dem Kunden alle Analyse-, Marketing- und Werbelösungen, die für relevante Kundenerlebnisse erforderlich sind, einfach bereitstellen und verwalten können. Die Datenerfassung in Adobe Experience Platform ist kostenlos und steht jedem Adobe Experience Cloud-Kunden zur Verfügung. Eine Marke kann die Datenerfassung von Adobe Experience Platform für Folgendes verwenden:

- Implementieren Sie Adobe Experience Cloud-Programme sowie Adobe Experience Platform.
- Verwalten Sie die verschiedenen Anforderungen der verschiedenen Teile der Organisation, indem Sie jedem eine eigene **Eigenschaft** zur Verwaltung bereitstellen.
- Ermöglicht Tests und Lebenszyklus-Management.
- Fügen Sie benutzerdefinierte JavaScript- und Drittanbieter-Tags ein, die alle an einem Ort verwaltet werden.

## Erkunden der Benutzeroberfläche

Zur [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/#/data-collection/).

Navigieren Sie zu **Tags**. Die Ansicht **[!UICONTROL Eigenschaften]** wird angezeigt. Die hier aufgelisteten Eigenschaften dienen zur Verwaltung von Tutorials. Diese Eigenschaften stellen Folgendes dar:

- App- und Web-Eigenschaften
- Verschiedene Websites, die Kunden auf unterschiedliche Weise bedienen. Zum Beispiel hätte Luma Retail eine Eigenschaft, Luma Travel eine andere.
- Alte und aktuelle Websites
- Ein spezifisches Adobe Analytics-Design, das für mehrere verschiedene Websites verwendet wird
- Interne Intranetseiten neben externen Sites

![Launch-Eigenschaften anzeigen](./images/launch1.png)

Schauen Sie sich jetzt die linke Leiste an.

![Linke Leiste starten](./images/launch2.png)

- **[!UICONTROL Tags]** bietet einen Überblick über alle Client-seitigen Eigenschaften
- **[!UICONTROL App-Oberflächen]** bietet einen Überblick über alle App-Konfigurationen zum Aktivieren von Push-Benachrichtigungen (die in Kombination mit Project Sierra verwendet/aktiviert wird)
- **[!UICONTROL Datenströme]** werden in der [&#x200B; Übung untersucht](./ex2.md)
- **[!UICONTROL Ereignisweiterleitung]** bietet einen Überblick über alle Server-seitigen Eigenschaften, die in untersucht werden [Modul 2.5 - Real-Time CDP Connections: Ereignisweiterleitung](./../../../modules/rtcdp-b2c/module2.5/aep-data-collection-ssf.md)
- **[!UICONTROL Monitoring]** bietet einen Überblick über den eingehenden und ausgehenden Ereignisdatenverkehr durch die Ereignisweiterleitung
- **[!UICONTROL Assurance]** bietet Zugriff zum Debuggen einer Implementierung mithilfe des Adobe Debuggers
- **[!UICONTROL Places]** bietet Zugriff auf die Verwaltung von POIs, die für die standortbasierte Personalisierung in Mobile Apps zugänglich werden
- **[!UICONTROL Schemas]** bietet Zugriff auf den Schema-Editor von Adobe Experience Platform
- **[!UICONTROL Identitäten]** bietet Zugriff auf die Einrichtung des Identitätsdiagramms in Adobe Experience Platform

## Weitere Informationen

Die Adobe Experience Platform-Datenerfassung ist ein sehr fortschrittliches Tool, das über ein Adobe Experience Platform-Tutorial hinausgeht. Unternehmen verwenden möglicherweise nicht die Adobe Experience Platform-Datenerfassung für ihre Tag-Management-Funktionen. Stattdessen verwenden sie Nicht-Adobe-Tag-Management-Lösungen für das Einfügen von Code und das Verwalten von Tags. Die Verwendung einer Tag-Management-Lösung ohne Adobe wird von Adobe und Adobe Professional Services unterstützt.
Weitere Informationen für diejenigen, die die Datenerfassung in Adobe Experience Platform besser verstehen möchten, finden Sie im Folgenden.

- [Benutzerhandbuch zur Datenerfassung in Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
- [Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK](https://experienceleague.adobe.com/de/docs/platform-learn/implement-web-sdk/overview)
- [Einrichten von Benutzerberechtigungen](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de)
- [API-Handbuch](https://developer.adobelaunch.com/api/)

Nächster Schritt: [1.1.2 Edge Network, Datenströme und Server-seitige Datenerfassung](./ex2.md)

[Zurück zum Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zurück zu „Alle Module“](./../../../overview.md)
