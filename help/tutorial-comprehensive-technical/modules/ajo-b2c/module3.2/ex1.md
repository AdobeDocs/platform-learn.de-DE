---
title: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr - Ereignis definieren
description: Adobe Journey Optimizer - Externe Wetter-API, SMS-Aktion und mehr
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 2%

---

# 3.2.1 Ereignis definieren

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der Ansicht **Home** Ihrer Sandbox `--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

Scrollen Sie im linken Menü nach unten und klicken Sie auf **Konfigurationen**. Klicken Sie anschließend unter **Ereignisse** auf die Schaltfläche **Verwalten** .

![ACOP](./images/acopmenu.png)

Daraufhin wird eine Übersicht über alle verfügbaren Ereignisse angezeigt. Klicken Sie auf **Ereignis erstellen** , um mit der Erstellung Ihres eigenen Ereignisses zu beginnen.

![ACOP](./images/emptyevent.png)

Daraufhin wird ein neues, leeres Ereignisfenster angezeigt.

![ACOP](./images/emptyevent1.png)

Verwenden Sie als Namen für das Ereignis `--aepUserLdap--GeofenceEntry`. In diesem Beispiel ist der Ereignisname `vangeluwGeofenceEntry`.

Legen Sie für Beschreibung den Wert `Geofence Entry Event` fest.

![Demo](./images/evname.png)

Stellen Sie als Nächstes sicher, dass der **Typ** auf **Einzel** gesetzt ist, und wählen Sie für die Auswahl des **Ereignis-ID-Typs** die Option **Systemgeneriert** aus.

![ACOP](./images/eventidtype.png)

Als Nächstes müssen Sie ein Schema auswählen. Alle hier gezeigten Schemas sind Adobe Experience Platform-Schemas.

![Demo](./images/evschema.png)

Sie werden feststellen, dass nicht alle Schemas angezeigt werden. In Adobe Experience Platform stehen noch viele weitere Schemata zur Verfügung.
Um in dieser Liste angezeigt zu werden, muss ein Schema eine sehr spezifische Feldergruppe enthalten. Die Feldergruppe, die hier angezeigt werden muss, heißt `Orchestration eventID`.

Sehen wir uns kurz an, wie diese Schemas in Adobe Experience Platform definiert sind.

Navigieren Sie im linken Menü zu **Schemas** und öffnen Sie es in einer neuen Browser-Registerkarte. Navigieren Sie in **Schemas** zu **Durchsuchen** , um die Liste der verfügbaren Schemas anzuzeigen.
Öffnen Sie das Schema `Demo System - Event Schema for Website (Global v1.1)`.

![Datenaufnahme](./images/schemas.png)

Nach dem Öffnen des Schemas sehen Sie, dass die Feldergruppe `Orchestration eventID` Teil des Schemas ist.
Diese Feldergruppe hat nur zwei Felder: `_experience.campaign.orchestration.eventID` und `originJourneyID`.

![Datenaufnahme](./images/schemageo.png)

Sobald diese Feldergruppe und dieses spezifische eventID-Feld Teil eines Schemas sind, kann dieses Schema von Adobe Journey Optimizer verwendet werden.

Gehen Sie zurück zur Ereigniskonfiguration in Adobe Journey Optimizer.

![Demo](./images/evschema.png)

In diesem Anwendungsfall möchten Sie ein Geofence-Ereignis überwachen, um zu verstehen, ob sich ein Kunde an einem bestimmten Ort befindet. Wählen Sie daher jetzt das Schema `Demo System - Event Schema for Website (Global v1.1)` als Schema für Ihr Ereignis aus.

![Demo](./images/evschema1.png)

Adobe Journey Optimizer wählt dann automatisch einige erforderliche Felder aus, Sie können jedoch die Felder bearbeiten, die Adobe Journey Optimizer zur Verfügung gestellt werden.

Klicken Sie auf das Symbol **Stift** , um die Felder zu bearbeiten.

![Demo](./images/editfields.png)

Daraufhin wird ein Popup-Fenster mit einer Schemahierarchie angezeigt, in dem Sie Felder auswählen können.

![Demo](./images/popup.png)

Felder wie die ECID und die Orchestration eventID sind erforderlich und als solche vorausgewählt.

Ein Marketing-Experte muss jedoch flexibel auf alle Datenpunkte zugreifen können, die Kontext zu einer Journey bieten. Stellen Sie also sicher, dass Sie auch die folgenden Felder als Minimum auswählen (zu finden im Kontextknoten Ort ):

- Stadt

Klicken Sie danach auf **OK**.

![Demo](./images/popupok.png)

Adobe Journey Optimizer benötigt auch eine Kennung, um den Kunden zu identifizieren. Da Adobe Journey Optimizer mit Adobe Experience Platform verknüpft ist, wird die Primäre Kennung eines Schemas automatisch als Kennung für die Journey verwendet.
Der Primäre Bezeichner berücksichtigt auch automatisch das vollständige Identitätsdiagramm von Adobe Experience Platform und verknüpft das gesamte Verhalten aller verfügbaren Identitäten, Geräte und Kanäle mit demselben Profil, sodass Adobe Journey Optimizer kontextbezogen, relevant und konsistent ist.

![Demo](./images/eventidentifier.png)

Klicken Sie auf **Speichern** , um Ihr benutzerdefiniertes Ereignis zu speichern.

![Demo](./images/save.png)

Ihr Ereignis wird dann Teil der Liste der verfügbaren Ereignisse sein.

![Demo](./images/eventlist.png)

Schließlich müssen Sie die `Orchestration eventID` für Ihr benutzerspezifisches Ereignis wiederherstellen.

Öffnen Sie das Ereignis erneut, indem Sie es in der Ereignisliste anklicken.
Klicken Sie in Ihrem Ereignis auf das Symbol **Payload anzeigen** neben **Felder**.

![Demo](./images/eventlist1.png)

Wenn Sie auf das Symbol **Payload anzeigen** klicken, wird eine Beispiel-XDM-Payload für dieses Ereignis geöffnet.

![Demo](./images/fieldseyepayload.png)

Scrollen Sie nach unten in die **Payload**, bis Sie die Zeile `eventID` sehen.

![Demo](./images/fieldseyepayloadev.png)

Notieren Sie sich die `eventID` , da Sie sie im letzten benötigen werden, um Ihre Konfiguration zu testen.

In diesem Beispiel ist `eventID` `fa42ab7982ba55f039eacec24c1e32e5c51b310c67f0fa559ab49b89b63f4934`.

Sie haben nun das Ereignis definiert, das den Trigger der Journey, die wir erstellen, darstellt. Sobald die Journey ausgelöst wird, werden die Geofence-Felder wie City und alle anderen, von Ihnen ausgewählten Felder (z. B. Land, Breitengrad und Längengrad) der Journey zur Verfügung gestellt.

Wie in der Anwendungsfallbeschreibung erläutert, müssen wir dann kontextbezogene Promotions bereitstellen, die vom Wetter abhängen. Um Wetterinformationen zu erhalten, müssen wir externe Datenquellen definieren, die uns die Wetterinformationen für diesen Ort liefern. Sie verwenden den Dienst **OpenWeather** , um uns mitzuteilen, welche Informationen diese als Teil von 2 liefern.

Nächster Schritt: [3.2.2 Externe Datenquelle definieren](./ex2.md)

[Zurück zu Modul 3.2](journey-orchestration-external-weather-api-sms.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
