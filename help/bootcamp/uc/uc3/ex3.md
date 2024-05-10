---
title: Bootcamp - Vermischen von physisch und digital - Journey Optimizer Erstellen Sie Ihre Journey- und Push-Benachrichtigung
description: Bootcamp - Vermischen von physisch und digital - Journey Optimizer Erstellen Sie Ihre Journey- und Push-Benachrichtigung
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: be8c23ec-c5f8-4abc-849f-994446072a84
source-git-commit: cd59a41f4533f18a54d80298ee9faf3a8ba3c6e7
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 4%

---

# 3.3 Journey- und Push-Benachrichtigung erstellen

In dieser Übung konfigurieren Sie die Journey und Nachricht, die ausgelöst werden müssen, wenn ein Benutzer mithilfe der App ein Beacon betritt.

Melden Sie sich über Adobe Journey Optimizer an. [Adobe Experience Cloud](https://experience.adobe.com). Klicks **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zum **Startseite**  in Journey Optimizer anzeigen. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `Bootcamp`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **Prod** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel heißt die Sandbox **Bootcamp**. Sie sind dann im **Startseite** Ansicht Ihrer Sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 3.3.1 Journey erstellen

Klicken Sie im linken Menü auf **Journeys**. Klicken Sie anschließend auf **Journey erstellen** , um eine neue Journey zu erstellen.

![ACOP](./images/createjourney.png)

Dann sehen Sie einen leeren Journey-Bildschirm.

![ACOP](./images/journeyempty.png)

In der vorherigen Übung haben Sie eine neue **Ereignis**. Sie haben es wie folgt benannt: `yourLastNameBeaconEntryEvent` und ersetzt `yourLastName` mit Ihrem Nachnamen. Dies war das Ergebnis der Ereigniserstellung:

![ACOP](./images/eventdone.png)

Jetzt müssen Sie dieses Ereignis als Beginn dieser Journey nehmen. Gehen Sie dazu zur linken Seite des Bildschirms und suchen Sie in der Ereignisliste nach Ihrem Ereignis.

![ACOP](./images/eventlist.png)

Wählen Sie das Ereignis aus, ziehen Sie es auf die Journey-Arbeitsfläche und legen Sie es ab. Ihre Journey sieht jetzt so aus. Klicks **Ok** , um Ihre Änderungen zu speichern.

![ACOP](./images/journeyevent.png)

Als zweiten Schritt im Journey müssen Sie eine **Push** Aktion. Navigieren Sie zur linken Bildschirmseite, um **Aktionen**, wählen Sie die **Push** -Aktion und ziehen Sie sie dann per Drag-and-Drop auf den zweiten Knoten in Ihre Journey.

![ACOP](./images/journeyactions.png)

Erstellen Sie nun auf der rechten Bildschirmseite Ihre Push-Benachrichtigung.

Legen Sie die **Kategorie** nach **Marketing** und wählen Sie eine Push-Oberfläche aus, über die Sie Push-Benachrichtigungen versenden können. In diesem Fall ist die auszuwählende Push-Oberfläche **mmeeewis-app-mobile-bootcamp**.

![ACOP](./images/journeyactions1.png)

## 3.3.2 Nachricht erstellen

Klicks **Inhalt bearbeiten**.

![ACOP](./images/emptymsg.png)

Daraufhin sehen Sie Folgendes:

![ACOP](./images/emailmsglist.png)

Definieren wir den Inhalt der Push-Benachrichtigung.

Klicken Sie auf **Titel** Textfeld.

![Journey Optimizer](./images/msg5.png)

Beginnen Sie im Textbereich mit dem Schreiben **Hi**. Wählen Sie das Personalisierungssymbol aus.

![Journey Optimizer](./images/msg6.png)

Jetzt müssen Sie das Personalisierungstoken für das Feld einfügen **Vorname** die unter `profile.person.name.firstName`. Wählen Sie im linken Menü die Option **Profilattribute**, scrollen Sie nach unten/navigieren Sie zu der **Person** und auf den Pfeil klicken, um eine Ebene tiefer zu gehen, bis Sie das Feld erreichen `profile.person.name.firstName`. Klicken Sie auf **+** -Symbol, um das Feld zur Arbeitsfläche hinzuzufügen. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg7.png)

Du wirst dann wieder hier sein. Klicken Sie auf das Personalisierungssymbol neben dem Feld. **body**.

![Journey Optimizer](./images/msg11.png)

Schreiben Sie im Textbereich `Welcome at the `.

![Journey Optimizer](./images/msg12.png)

Klicken Sie anschließend auf **Kontextattribute** und dann **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Klicks **Veranstaltungen**.

![ACOP](./images/jomsg4.png)

Klicken Sie auf den Namen Ihres Ereignisses, der wie folgt aussehen sollte: **yourLastNameBeaconEntryEvent**.

![ACOP](./images/jomsg5.png)

Klicks **Ortskontext**.

![ACOP](./images/jomsg6.png)

Klicks **POI-Interaktion**.

![ACOP](./images/jomsg7.png)

Klicks **POI-Detail**.

![ACOP](./images/jomsg8.png)

Klicken Sie auf **+** Symbol auf **POI-Name**.
Dann wirst du das sehen. Klicken Sie auf **Speichern**.

![ACOP](./images/jomsg9.png)

Ihre Nachricht ist jetzt bereit. Klicken Sie auf den Pfeil oben links, um zu Ihrer Journey zurückzukehren.

![ACOP](./images/jomsg11.png)

Klicken Sie auf **OK**.

![ACOP](./images/jomsg14.png)

## 3.3.2 Nachricht an einen Bildschirm senden

Als dritten Schritt im Journey müssen Sie eine **sendMessageToScreen** Aktion. Navigieren Sie zur linken Bildschirmseite, um **Aktionen**, wählen Sie die **sendMessageToScreen** -Aktion und ziehen Sie sie dann per Drag-and-Drop auf den dritten Knoten im Journey. Dann wirst du das sehen.

![ACOP](./images/jomsg15.png)

Die **sendMessageToScreen** action ist eine benutzerdefinierte Aktion, mit der eine Nachricht an dem Endpunkt veröffentlicht wird, der von der In-Store-Anzeige verwendet wird. Die **sendMessageToScreen** -Aktion erwartet die Definition einer Reihe von Variablen. Sie können diese Variablen anzeigen, indem Sie nach unten scrollen, bis Sie **Aktionsparameter**.

![ACOP](./images/jomsg16.png)

Sie müssen jetzt die Werte für jeden Aktionsparameter festlegen. In dieser Tabelle erfahren Sie, welche Werte wohin benötigt werden.

| Parameter | value |
|:-------------:| :---------------:|
| VERSAND | `'image'` |
| ECID | `@{yourLastNameBeaconEntryEvent._experienceplatform.identification.core.ecid}` |
| VORNAME | `#{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName}` |
| EREIGNIS | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first().name}` |
| EVENTSUBJECTURL | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first()._experienceplatform.core.imageURL}` |
| SANDBOX | `'bootcamp'` |
| CONTAINERID | `''` |
| ACTIVITYID | `''` |
| PLACEMENTID | `''` |

{style="table-layout:auto"}

Um diese Werte festzulegen, klicken Sie auf das **Bearbeiten** Symbol.

![ACOP](./images/jomsg17.png)

Wählen Sie als Nächstes **Erweiterter Modus**.

![ACOP](./images/jomsg18.png)

Fügen Sie dann den Wert basierend auf der obigen Tabelle ein. Klicken Sie auf **OK**.

![ACOP](./images/jomsg19.png)

Wiederholen Sie diesen Vorgang, um Werte für jedes Feld hinzuzufügen.

>[!IMPORTANT]
>
>Für das Feld ECID gibt es einen Verweis auf das Ereignis `yourLastNameBeaconEntryEvent`. Bitte stellen Sie sicher, dass Sie `yourLastName` durch Ihren Nachnamen.

Das Endergebnis sollte wie folgt aussehen:

![ACOP](./images/jomsg20.png)

Scrollen Sie nach oben und klicken Sie **Ok**.

![ACOP](./images/jomsg21.png)

Sie müssen Ihrer Journey noch einen Namen geben. Klicken Sie hierzu auf die Schaltfläche **Bleistift** in der oberen linken Bildschirmseite angezeigt.

![ACOP](./images/journeyname.png)

Dann können Sie hier den Namen des Journey eingeben. Verwenden Sie `yourLastName - Beacon Entry Journey`. Klicken Sie auf **OK**, um die Änderungen zu speichern.

![ACOP](./images/journeyname1.png)

Sie können Ihre Journey jetzt veröffentlichen, indem Sie auf **Veröffentlichen**.

![ACOP](./images/publishjourney.png)

Klicks **Veröffentlichen** erneut.

![ACOP](./images/publish1.png)

Sie sehen dann eine grüne Bestätigungsleiste, dass Ihre Journey jetzt veröffentlicht ist.

![ACOP](./images/published.png)

Ihre Journey ist jetzt live und kann ausgelöst werden.

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [3.4 Journey testen](./ex4.md)

[Zurück zum Benutzerfluss 3](./uc3.md)

[Zu allen Modulen zurückkehren](../../overview.md)
