---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Erläuterung der Adobe Experience Platform-Datenerfassung
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Erläuterung der Adobe Experience Platform-Datenerfassung
kt: 5342
doc-type: tutorial
exl-id: 098031c6-4d8b-46a5-ae86-8fd7692268d3
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 3%

---

# 1.1.1 Grundlagen zur Datenerfassung in Adobe Experience Platform

## Kontext

Die Datenerfassung von Adobe Experience Platform wird von Marken für eine Reihe von Anwendungsfällen verwendet. Es handelt sich um ein Tag Management-System der nächsten Generation (TMS), das Kunden eine einfache Möglichkeit bietet, alle Analyse-, Marketing- und Werbelösungen bereitzustellen und zu verwalten, die zur Unterstützung entsprechender Kundenerlebnisse erforderlich sind. Für die Datenerfassung in Adobe Experience Platform fallen keine zusätzlichen Gebühren an. Diese sind auch für Adobe Experience Cloud-Kunden verfügbar. Eine Marke könnte die Datenerfassung von Adobe Experience Platform für folgende Zwecke verwenden:

- Implementieren Sie Adobe Experience Cloud-Anwendungen sowie Adobe Experience Platform.
- Verwalten Sie die verschiedenen Anforderungen verschiedener Teile der Organisation, indem Sie jedem eine eigene **Eigenschaft** zur Verwaltung bereitstellen.
- Ermöglichen Sie Tests und Lebenszyklusverwaltung.
- Fügen Sie benutzerdefinierte JavaScript- und Drittanbieter-Tags ein, die alle an einem Ort verwaltet werden.

## Benutzeroberfläche durchsuchen

Wechseln Sie zu [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/#/data-collection/).

Navigieren Sie zu **Tags**. Jetzt wird die Ansicht **[!UICONTROL Eigenschaften]** angezeigt. Die hier aufgeführten Eigenschaften dienen der Tutorial-Verwaltung. Diese Eigenschaften repräsentieren ...

- App- und Webeigenschaften
- Verschiedene Websites bedienen Kunden auf unterschiedliche Weise. Beispiel: Luma Retail hätte eine Eigenschaft, Luma Travel eine andere
- Alte und aktuelle Websites
- Ein spezifisches Adobe Analytics-Design, das auf mehreren verschiedenen Websites verwendet wird
- Interne Intranet-Seiten neben externen Sites

![Ansicht &quot;Launch-Eigenschaften&quot;](./images/launch1.png)

Sehen Sie sich nun die linke Leiste an.

![Linke Leiste starten](./images/launch2.png)

- **[!UICONTROL Tags]** bietet einen Überblick über alle clientseitigen Eigenschaften
- **[!UICONTROL App-Oberflächen]** bietet einen Überblick über alle App-Konfigurationen zur Aktivierung von Push-Benachrichtigungen (wird in Kombination mit Projekt-Sierra verwendet/aktiviert)
- **[!UICONTROL Datastreams]** werden in der [nächsten Übung](./ex2.md) untersucht.
- **[!UICONTROL Ereignisweiterleitung]** gibt einen Überblick über alle serverseitigen Eigenschaften, die im [Modul 2.5 - Real-Time CDP-Verbindungen: Ereignisweiterleitung](./../../../modules/rtcdp-b2c/module2.5/aep-data-collection-ssf.md) untersucht werden.
- **[!UICONTROL Überwachung]** bietet einen Überblick über den eingehenden und ausgehenden Ereignis-Traffic durch die Ereignisweiterleitung.
- **[!UICONTROL Assurance]** bietet Zugriff zum Debugging einer Implementierung mithilfe des Adobe Debuggers
- **[!UICONTROL Places]** bietet Zugriff auf die Verwaltung von POIs, die für standortbasierte Personalisierung in Mobile Apps verfügbar sind
- **[!UICONTROL Schemas]** bietet Zugriff auf den Schema-Editor von Adobe Experience Platform
- **[!UICONTROL Identitäten]** bietet Zugriff auf die Einrichtung des Identitätsdiagramms von Adobe Experience Platform

## Weitere Informationen

Die Adobe Experience Platform-Datenerfassung ist ein sehr fortschrittliches Tool, das über ein Adobe Experience Platform-Tutorial hinausgeht. Unternehmen verwenden möglicherweise nicht die Adobe Experience Platform-Datenerfassung für ihre Tag-Management-Funktionen und stattdessen Nicht-Adobe-Tag-Management-Lösungen für die Codeeingabe und die Verwaltung von Tags. Die Verwendung einer Nicht-Adobe-Tag-Management-Lösung wird von Adobe und Adobe Professional Services unterstützt.
Im Folgenden finden Sie weitere Informationen für diejenigen, die die Datenerfassung in Adobe Experience Platform vertiefen möchten.

- [Adobe Experience Platform-Datenerfassungs-Benutzerhandbuch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
- [Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=de)
- [Einrichten von Benutzerberechtigungen](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de)
- [API-Handbuch](https://developer.adobelaunch.com/api/)

Nächster Schritt: [1.1.2 Edge Network, Datenspeicher und serverseitige Datenerfassung](./ex2.md)

[Zurück zu Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
