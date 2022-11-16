---
title: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Edge Network, Datastreams und serverseitige Datenerfassung
description: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Edge Network, Datastreams und serverseitige Datenerfassung
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 6f7c540f-3804-483d-90f9-b26b4a252b8b
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 2%

---

# 1.2 Edge-Netzwerk, Datenspeicher und serverseitige Datenerfassung

## Kontext

In dieser Übung erstellen Sie eine **Datastream**. A **Datastream** teilt den Adobe Edge-Servern mit, wohin die Daten gesendet werden sollen, nachdem sie vom Web SDK erfasst wurden. Möchten Sie beispielsweise die Daten an Adobe Experience Platform senden? Adobe Analytics? Adobe Audience Manager? Adobe Target?

Datenspeicher werden immer in der Benutzeroberfläche der Adobe Experience Platform-Datenerfassung verwaltet und sind für die Adobe Experience Platform-Datenerfassung mit dem Web SDK von entscheidender Bedeutung. Selbst wenn Sie das Web SDK mit einer Nicht-Adobe-Tag-Management-Lösung implementieren, müssen Sie Ihren Datastream weiterhin in der Benutzeroberfläche der Adobe Experience Platform-Datenerfassung erstellen.

Sie werden das Web SDK in der nächsten Übung im Browser implementieren. Dann wird Ihnen klarer sein, wie die erfassten Daten aussehen. Zunächst teilen wir dem Datastream nur mit, wohin die Daten weitergeleitet werden sollen.

## Erstellen eines Datenspeichers

In [Übung 0.2](./../module0/ex2.md) Sie haben bereits einen Datastream erstellt, aber wir haben nicht über den Hintergrund und den Grund für das Sein des Datastreams diskutiert.

Ein Datastream teilt den Adobe Edge-Servern mit, wohin die Daten gesendet werden sollen, nachdem sie vom Web SDK erfasst wurden. Möchten Sie beispielsweise die Daten an Adobe Experience Platform senden? Adobe Analytics? Adobe Audience Manager? Adobe Target? Datenspeicher werden in der Benutzeroberfläche der Adobe Experience Platform-Datenerfassung verwaltet und sind für die Platform-Datenerfassung mit dem Web SDK von entscheidender Bedeutung, unabhängig davon, ob Sie das Web SDK über die Adobe Experience Platform-Datenerfassung implementieren oder nicht.

Überprüfen wir Ihre **[!UICONTROL Datastream]**:

Navigieren Sie zu [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/).

Klicken **[!UICONTROL Datenspeicher]** oder **[!UICONTROL Datenspeicher (Beta)]** im linken Menü.

![Klicken Sie im linken Navigationsbereich auf das Symbol Datastream .](./images/edgeconfig1.png)

Suchen Sie nach Ihrem Datastream mit dem Namen `--demoProfileLdap-- - Demo System Datastream`.

![Benennen Sie den Datastream und speichern Sie ihn.](./images/edgeconfig2.png)

Sie sehen dann die Details Ihres Datastreams.

![Benennen Sie den Datastream und speichern Sie ihn.](./images/edgecfg1.png)

Klicken **...** neben **Adobe Experience Platform** und klicken Sie auf **Bearbeiten**.

![Benennen Sie den Datastream und speichern Sie ihn.](./images/edgecfg1a.png)

Dann wirst du das sehen. Derzeit haben Sie nur Adobe Experience Platform aktiviert. Ihre Konfiguration ähnelt der unten stehenden Konfiguration. (Abhängig von Ihrer Umgebung und Adobe Experience Platform-Instanz kann der Sandbox-Name unterschiedlich sein.)

![Benennen Sie den Datastream und speichern Sie ihn.](./images/edgecfg2.png)

Sie sollten die folgenden Felder wie folgt interpretieren:

Für diesen Datastream ...

- Alle erfassten Daten werden im `--aepSandboxId--` Sandbox in Adobe Experience Platform
- Alle Erlebnisereignis-Daten werden standardmäßig im Datensatz erfasst **Demosystem - Ereignis-Datensatz für Website (Global v1.1)**
- Alle Profildaten werden standardmäßig im Datensatz erfasst **Demosystem - Profildatensatz für Website (Global v1.1)** (Die native Erfassung von Profildaten mit dem Web SDK wird derzeit noch nicht vom Web SDK unterstützt und zu einem späteren Zeitpunkt bereitgestellt.)
- Wenn Sie die **offer decisioning** Anwendungsdienst für diesen Datastream, müssen Sie das Kontrollkästchen für Offer decisioning aktivieren. (Dies wird Teil von [Modul 9](./../module9/offer-decisioning.md))
- Wenn Sie die **Edge-Segmentierung** müssen Sie das Kontrollkästchen für die Edge-Segmentierung aktivieren.
- Wenn Sie die **Personalisierungsziele** müssen Sie das Kontrollkästchen für Personalisierungsziele aktivieren.

Derzeit ist keine andere Konfiguration für Ihren Datastream erforderlich.

Nächster Schritt: [1.3 Einführung in die Adobe Experience Platform-Datenerfassung](./ex3.md)

[Zurück zu Modul 1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../overview.md)
