---
title: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Implementieren von Adobe Analytics und Adobe Audience Manager
description: Foundation - Einrichtung der Adobe Experience Platform-Datenerfassung und der Web-SDK-Erweiterung - Implementieren von Adobe Analytics und Adobe Audience Manager
kt: 5342
doc-type: tutorial
exl-id: a9022269-6db2-46c6-a82b-ec8d5b881a55
source-git-commit: 1526661a80b4d551627dfca42a7e97c9498dd1f2
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# 1.1.5 Implementieren von Adobe Analytics und Adobe Audience Manager

## Kontext

Sie wissen jetzt, dass XDM-Daten in Platform fließen. Sie erfahren mehr darüber, was XDM in [Modul 1.2](./../module1.2/data-ingestion.md) ist, sowie darüber, wie Sie Ihr eigenes Schema zum Nachverfolgen benutzerdefinierter Variablen erstellen. Im Moment werden Sie sich ansehen, was passiert, wenn Sie Ihren Datenstrom so einstellen, dass Daten an Analytics und Audience Manager weitergeleitet werden.

## Zuordnen von Variablen in Analytics

Die Adobe Experience Platform-[!DNL Web SDK] ordnet bestimmte Werte automatisch zu, sodass eine neue Implementierung von Analytics über die Web-SDK so schnell wie möglich erfolgt. Die automatisch zugeordneten Variablen werden [hier](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/adobe-analytics/automatically-mapped-vars.html?lang=de#data-collection) aufgelistet.

Bei XDM-Daten, die nicht automatisch Adobe Analytics zugeordnet werden, können Sie [Kontextdaten](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=de) verwenden, um Ihren ([) ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=de). Anschließend kann sie mithilfe von [Verarbeitungsregeln“ in Analytics zugeordnet werden](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-configuration/t-processing-rules.html?lang=de) um Analytics-Variablen aufzufüllen. Kontextdaten und Verarbeitungsregeln sind Konzepte, die denjenigen bekannt sind, die in der Vergangenheit mit Analytics gearbeitet haben. Sie sollten sich jedoch vorerst nicht um die Details kümmern, wenn es sich um neue Konzepte handelt.

Sie können auch einen Standardsatz von Aktionen und Produktlisten verwenden, um Daten mit der AEP Web SDK zu senden oder abzurufen. Weitere Informationen hierzu finden Sie unter [Produkte](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/collect-commerce-data.html?lang=de#data-collection).

### Kontextdaten

Zur Verwendung in Analytics werden XDM-Daten mit Punktnotation reduziert und als `contextData` bereitgestellt. Die folgende Liste von Wertpaaren zeigt ein Beispiel für `context data`:

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

Auf alle vom Edge Network erfassten Daten kann über [Verarbeitungsregeln“ zugegriffen ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-configuration/t-processing-rules.html?lang=de). In Analytics können Sie Verarbeitungsregeln verwenden, um Kontextdaten in Analytics-Variablen einzubinden.

## Audience Manager auf dem Experience Platform-Edge Network

Die Server-seitige Weiterleitung ist kein neues Konzept für Audience Manager und es gilt der gleiche Prozess wie zuvor. Sie können auch Identitäten synchronisieren.

## Überprüfen Ihres Datenstroms, um Daten an Adobe Analytics zu senden

Wenn Sie von Web SDK erfasste Daten an Adobe Analytics und Adobe Audience Manager senden möchten, führen Sie die folgenden Schritte aus.

Wechseln Sie zu [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) und dann zu **Datenströme**.

Wählen Sie oben rechts im Bildschirm den Namen Ihrer Sandbox aus, der `--aepSandboxName--` werden soll. Öffnen Sie Ihren spezifischen Datenstrom mit dem Namen `--aepUserLdap-- - Demo System Datastream`.

![Klicken Sie im linken Navigationsbereich auf das Symbol Edge-Konfiguration ](./images/edgeconfig1b.png)

Sie werden es dann sehen. Um Adobe Analytics zu aktivieren, klicken Sie auf **Service hinzufügen**.

![AEP-Debugger](./images/aa2.png)

Sie werden es dann sehen. Wählen Sie den Dienst **Adobe Analytics** aus, nach dem Sie die Report Suite in Adobe Analytics hinzufügen müssen, um Daten an zu senden. In diesem Tutorial liegt dies außerhalb des Projektumfangs. Klicken Sie **Abbrechen**.

![AEP-Debugger](./images/aa3.png)

## Überprüfen Ihres Datenstroms, um Daten an Adobe Audience Manager zu senden

Sie werden es dann sehen. Um Adobe Audience Manager zu aktivieren, klicken Sie auf **Service hinzufügen**.

![AEP-Debugger](./images/aa2.png)

Sie werden es dann sehen. Wählen Sie den Dienst **Adobe Audience Manager** aus, nach dem Sie Adobe Audience Manager-Cookie-Ziele und/oder URL-Ziele aktivieren oder deaktivieren können. In diesem Tutorial liegt diese Konfiguration außerhalb des Bereichs. Klicken Sie **Abbrechen**.

![AEP-Debugger](./images/aam1.png)

Nächster Schritt: [1.1.6 Implementieren von Adobe Target](./ex6.md)

[Zurück zum Modul 1.1](./data-ingestion-launch-web-sdk.md)

[Zurück zu „Alle Module“](./../../../overview.md)
