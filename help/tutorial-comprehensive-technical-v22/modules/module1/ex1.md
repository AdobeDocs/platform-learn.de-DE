---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Erläuterung der Adobe Experience Platform-Datenerfassung
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Erläuterung der Adobe Experience Platform-Datenerfassung
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: f498bb8c-659c-44b4-bb2e-36ea14640773
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 7%

---

# 1.1 Grundlagen zur Datenerfassung in Adobe Experience Platform

## Kontext

Die Datenerfassung von Adobe Experience Platform wird von Marken für eine Reihe von Anwendungsfällen verwendet. Es handelt sich um ein Tag Management-System der nächsten Generation (TMS), das Kunden eine einfache Möglichkeit bietet, alle Analyse-, Marketing- und Werbelösungen bereitzustellen und zu verwalten, die zur Unterstützung entsprechender Kundenerlebnisse erforderlich sind. Für die Datenerfassung in Adobe Experience Platform fallen keine zusätzlichen Gebühren an. Diese sind für Adobe Experience Cloud-Kunden verfügbar. Eine Marke könnte die Datenerfassung von Adobe Experience Platform für folgende Zwecke verwenden:

- Implementieren Sie Adobe Experience Cloud-Anwendungen sowie Adobe Experience Platform.
- Verwalten Sie die verschiedenen Anforderungen verschiedener Teile der Organisation, indem Sie jedem eine eigene **Eigenschaft** zu verwalten.
- Ermöglichen Sie Tests und Lebenszyklusverwaltung.
- Fügen Sie benutzerdefinierte JavaScript- und Drittanbieter-Tags ein, die alle an einem Ort verwaltet werden.

## Benutzeroberfläche durchsuchen

Navigieren Sie zu [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/#/data-collection/).

Navigieren Sie zu **Tags**. Sie sehen jetzt die **[!UICONTROL Eigenschaften]** anzeigen. Die hier aufgeführten Eigenschaften dienen der Tutorial-Verwaltung. Diese Eigenschaften repräsentieren ...

- App- und Webeigenschaften
- Verschiedene Websites bedienen Kunden auf unterschiedliche Weise. Beispiel: Luma Retail hätte eine Eigenschaft, Luma Travel eine andere
- Alte und aktuelle Websites
- Ein spezifisches Adobe Analytics-Design, das auf mehreren verschiedenen Websites verwendet wird
- Interne Intranet-Seiten neben externen Sites

![Ansicht &quot;Launch-Eigenschaften&quot;](./images/launch1.png)

Sehen Sie sich nun die linke Leiste an.

![Linke Leiste starten](./images/launch2.png)

- **[!UICONTROL Tags]** gibt einen Überblick über alle clientseitigen Eigenschaften
- **[!UICONTROL App-Oberflächen]** bietet einen Überblick über alle App-Konfigurationen zur Aktivierung von Push-Benachrichtigungen (die in Kombination mit Project Sierra verwendet/aktiviert wird)
- **[!UICONTROL Datenspeicher]** werden im [nächste Übung](./ex2.md)
- **[!UICONTROL Ereignisweiterleitung]** bietet einen Überblick über alle serverseitigen Eigenschaften, die unter [Modul 14 - Real-Time CDP-Verbindungen: Ereignisweiterleitung](../module14/aep-data-collection-ssf.md)

## Weiterführende Informationen

Die Adobe Experience Platform-Datenerfassung ist ein sehr fortschrittliches Tool, das über ein Adobe Experience Platform-Tutorial hinausgeht. Unternehmen verwenden möglicherweise nicht die Adobe Experience Platform-Datenerfassung für ihre Tag-Management-Funktionen und stattdessen Tagverwaltungslösungen, die keine Adobe sind, zum Einfügen von Code und Verwalten von Tags. Die Verwendung einer Nicht-Adobe-Tag-Management-Lösung wird von Adobe und Adobe Professional Services unterstützt.
Im Folgenden finden Sie weitere Informationen für diejenigen, die die Datenerfassung in Adobe Experience Platform vertiefen möchten.

- [Benutzerhandbuch zur Datenerfassung in Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
- [Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=de)
- [Einrichten von Benutzerberechtigungen](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=de)
- [API-Handbuch](https://developer.adobelaunch.com/api/)

Nächster Schritt: [1.2 Edge-Netzwerk, Datenspeicher und serverseitige Datenerfassung](./ex2.md)

[Zurück zu Modul 1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
