---
title: Segmentaktivierung zum Microsoft Azure Event Hub - Erstellen eines Streaming-Segments
description: Segmentaktivierung zum Microsoft Azure Event Hub - Erstellen eines Streaming-Segments
kt: 5342
doc-type: tutorial
source-git-commit: 7d2f5f842559b2d6d9f115f3993268a4b36a0fe0
workflow-type: tm+mt
source-wordcount: '363'
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

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Navigieren Sie zu **Segmente**. Klicken Sie auf die Schaltfläche **+ Segment erstellen** .

![Datenaufnahme](./images/seg.png)

Benennen Sie Ihr Segment `--demoProfileLdap-- - Interest in Equipment` und fügen Sie das Erlebnisereignis für Seitennamen hinzu:

Klicken Sie auf **Ereignisse** und ziehen Sie **XDM ExperienceEvent > Web > Web page details > Name** per Drag-and-Drop. Geben Sie **equipment** als Wert ein:

![4-05-create-ee-2.png](./images/4-05-create-ee-2.png)

Ziehen Sie **XDM ExperienceEvent > `--aepTenantIdSchema--` > demoEnvironment > brandName** in den Arbeitsbereich. Geben Sie `--demoProfileLdap--` als Wert ein, setzen Sie den Vergleichsparameter auf **contains** und klicken Sie auf **Save**:

![4-05-create-ee-2-brand.png](./images/4-05-create-ee-2-brand.png)

### PQL-Definition

Die PQL Ihres Segments sieht wie folgt aus:

```code
CHAIN(xEvent, timestamp, [C0: WHAT(web.webPageDetails.name.equals("equipment", false) and _experienceplatform.demoEnvironment.brandName.contains("--demoProfileLdap--", false))])
```

Nächster Schritt: [2.4.4 Segment aktivieren](./ex4.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
