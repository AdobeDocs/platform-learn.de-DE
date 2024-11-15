---
title: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Implementieren von Adobe Analytics und Adobe Audience Manager
description: Foundation - Einrichten der Adobe Experience Platform-Datenerfassung und der Web SDK-Erweiterung - Implementieren von Adobe Analytics und Adobe Audience Manager
kt: 5342
doc-type: tutorial
exl-id: a9022269-6db2-46c6-a82b-ec8d5b881a55
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# 1.1.5 - Implementieren von Adobe Analytics und Adobe Audience Manager

## Kontext

Sie wissen jetzt, dass XDM-Daten in die Plattform fließen. Erfahren Sie mehr darüber, was XDM in [Modul 1.2](./../module1.2/data-ingestion.md) ist und wie Sie Ihr eigenes Schema zur Verfolgung benutzerdefinierter Variablen erstellen. Zunächst werden Sie sehen, was passiert, wenn Sie Ihren Datastream so einstellen, dass Daten an Analytics und Audience Manager weitergeleitet werden.

## 1.1.5.1 Zuordnen von Variablen in Analytics

Die Adobe Experience Platform [!DNL Web SDK] ordnet bestimmte Werte automatisch zu, wodurch eine neue Implementierung von Analytics über das Web SDK so schnell wie möglich erfolgt. Die automatisch zugeordneten Variablen werden [hier](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/adobe-analytics/automatically-mapped-vars.html#data-collection) aufgelistet.

Bei XDM-Daten, die nicht automatisch Adobe Analytics zugeordnet werden, können Sie [Kontextdaten](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=de) verwenden, um Ihrem [Schema](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=de) zu entsprechen. Anschließend kann sie mithilfe von [Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-configuration/t-processing-rules.html) in Analytics zugeordnet werden, um Analytics-Variablen zu füllen. Kontextdaten und Verarbeitungsregeln sind Konzepte, die mit denen vertraut sind, die in der Vergangenheit mit Analytics gearbeitet haben, sich aber nicht um die Details kümmern, wenn es sich um neue Konzepte handelt.

Sie können auch einen Standardsatz von Aktionen und Produktlisten zum Senden oder Abrufen von Daten mit dem AEP Web SDK verwenden. Weitere Informationen hierzu finden Sie unter [Produkte](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/collect-commerce-data.html?lang=en#data-collection).

### Kontextdaten

Zur Verwendung durch Analytics werden XDM-Daten mit Punktnotation reduziert und als `contextData` verfügbar gemacht. Die folgende Liste von Wertpaaren zeigt ein Beispiel für `context data`:

```javascript
{
    "bh": "900",
    "bw": "1680",
    "c": "24",
    "c.a.d.key.[0]": "value1",
    "c.a.d.key.[1]": "value2",
    "c.a.d.object.key1": "value1",
    "c.a.d.object.key2.[0]": "value2",
    "c.a.x.environment.browserdetails.javascriptenabled": "true",
    "c.a.x.environment.type": "browser",
    "cust_hit_time_gmt": "1579781427",
    "g": "http://example.com/home",
    "gn": "home",
    "j": "1.8.5",
    "k": "Y",
    "s": "1680x1050",
    "tnta": "218287:1:0|0,218287:1:0|2,218287:1:0|1,218287:1:0|32767,218287:1:01,218287:1:0|0,218287:1:0|1,218287:1:0|0,218287:1:0|1",
    "user_agent": "Mozilla/5.0 AppleWebKit/537.36 Safari/537.36",
    "v": "Y"
}
```

### Verarbeitungsregeln

Auf alle vom Edge Network erfassten Daten kann über [Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-configuration/t-processing-rules.html) zugegriffen werden. In Analytics können Sie Verarbeitungsregeln verwenden, um Kontextdaten in Analytics-Variablen zu integrieren.

## 1.1.5.2 Audience Manager auf dem Experience Platform-Edge Network

Die serverseitige Weiterleitung ist kein neues Konzept für den Audience Manager, und es gilt der gleiche Prozess wie zuvor. Sie können auch Identitäten synchronisieren.

## 1.1.5.3 Überprüfen Sie Ihren Datenspeicher, um Daten an Adobe Analytics zu senden.

Wenn Sie vom Web SDK erfasste Daten an Adobe Analytics und Adobe Audience Manager senden möchten, führen Sie die folgenden Schritte aus.

Wechseln Sie zu [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) und gehen Sie zu **Datastreams**.

Wählen Sie oben rechts auf Ihrem Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` lauten soll. Öffnen Sie Ihren spezifischen Datastream mit dem Namen `--aepUserLdap-- - Demo System Datastream`.

![Klicken Sie auf das Symbol Edge-Konfiguration im linken Navigationsbereich](./images/edgeconfig1b.png)

Dann wirst du das sehen. Um Adobe Analytics zu aktivieren, klicken Sie auf **+Dienst hinzufügen**.

![AEP-Debugger](./images/aa2.png)

Dann wirst du das sehen. Wählen Sie den Dienst **Adobe Analytics** aus, nach dem Sie die Report Suite in Adobe Analytics hinzufügen müssen, an die Daten gesendet werden sollen. In diesem Tutorial ist dies nicht möglich. Klicken Sie auf **Abbrechen**.

![AEP-Debugger](./images/aa3.png)

## 1.1.5.4 Überprüfen Sie Ihren Datenspeicher, um Daten an Adobe Audience Manager zu senden.

Dann wirst du das sehen. Um Adobe Audience Manager zu aktivieren, klicken Sie auf **+Dienst hinzufügen**.

![AEP-Debugger](./images/aa2.png)

Dann wirst du das sehen. Wählen Sie den Dienst **Adobe Audience Manager** aus, nach dem Sie Adobe Audience Manager-Cookie-Ziele und/oder URL-Ziele aktivieren oder deaktivieren können. In diesem Tutorial ist diese Konfiguration nicht möglich. Klicken Sie auf **Abbrechen**.

![AEP-Debugger](./images/aam1.png)

Nächster Schritt: [1.1.6 Adobe Target implementieren](./ex6.md)

[Zurück zu Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
