---
title: Segmentaktivierung zum Microsoft Azure Event Hub - Erstellen eines Streaming-Segments
description: Segmentaktivierung zum Microsoft Azure Event Hub - Erstellen eines Streaming-Segments
kt: 5342
doc-type: tutorial
exl-id: 86bc3afa-16a9-4834-9119-ce02445cd524
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# 2.4.3 Segment erstellen

## 2.4.3.1 Einführung

Sie erstellen ein einfaches Segment:

- **Interesse an Ausrüstung**, für welche Kundenprofile beim Besuch der Seite **Ausrüstung** auf der Demowebsite von Luma qualifiziert werden.

### Gut zu wissen

Die Echtzeit-Kundendatenplattform Trigger eine Aktivierung an ein Ziel, wenn Sie sich für ein Segment qualifizieren, das Teil der Aktivierungsliste dieses Ziels ist. In diesem Fall enthält die Payload der Segmentqualifizierung, die an dieses Ziel gesendet wird, **alle Segmente, für die Ihr Profil qualifiziert ist**.

Ziel dieses Moduls ist es, zu zeigen, dass die Segmentqualifikation Ihres Kundenprofils in Echtzeit an **Ihr** Ereignis-Hub-Ziel gesendet wird.

### Segmentstatus

Eine Segmentqualifizierung in Adobe Experience Platform hat immer die Eigenschaft **status** und kann eine der folgenden sein:

- **realisiert**: Dies weist auf eine neue Segmentqualifikation hin
- **existing**: Gibt eine vorhandene Segmentqualifikation an
- **exited**: Zeigt an, dass das Profil nicht mehr für das Segment qualifiziert ist.

## 2.4.3.2 Segment erstellen

Das Erstellen eines Segments wird im Abschnitt [Modul 2.3](./../../../modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md) ausführlich erläutert.

### Segment erstellen

Melden Sie sich bei Adobe Experience Platform an, indem Sie diese URL verwenden: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Navigieren Sie zu **Segmente**. Klicken Sie auf die Schaltfläche **+ Segment erstellen** .

![Datenaufnahme](./images/seg.png)

Benennen Sie Ihr Segment `--aepUserLdap-- - Interest in Equipment` und fügen Sie das Erlebnisereignis für Seitennamen hinzu:

Klicken Sie auf **Ereignisse** und ziehen Sie **XDM ExperienceEvent > Web > Web page details > Name** per Drag-and-Drop. Geben Sie **equipment** als Wert ein:

![4-05-create-ee-2.png](./images/4-05-create-ee-2.png)

Ziehen Sie **XDM ExperienceEvent > `--aepTenantId--` > demoEnvironment > brandName** in den Arbeitsbereich. Geben Sie `--aepUserLdap--` als Wert ein, setzen Sie den Vergleichsparameter auf **contains** und klicken Sie auf **Save**:

![4-05-create-ee-2-brand.png](./images/4-05-create-ee-2-brand.png)

### PQL-Definition

Die PQL Ihres Segments sieht wie folgt aus:

```code
CHAIN(xEvent, timestamp, [C0: WHAT(web.webPageDetails.name.equals("equipment", false) and _experienceplatform.demoEnvironment.brandName.contains("--aepUserLdap--", false))])
```

Nächster Schritt: [2.4.4 Segment aktivieren](./ex4.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
