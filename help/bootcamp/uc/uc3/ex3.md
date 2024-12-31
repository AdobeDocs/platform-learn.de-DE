---
title: Bootcamp - Mischung aus physischer und digitaler Technologie - Journey Optimizer Erstellen Sie Ihre Journey- und Push-Benachrichtigung
description: Bootcamp - Mischung aus physischer und digitaler Technologie - Journey Optimizer Erstellen Sie Ihre Journey- und Push-Benachrichtigung
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

# 3.3 Erstellen von Journey- und Push-Benachrichtigungen

In dieser Übung konfigurieren Sie die Journey und die Nachricht, die ausgelöst werden muss, wenn jemand über die Mobile App einen Beacon betritt.

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `Bootcamp`. Um von einer Sandbox in eine andere zu wechseln, klicken Sie auf **Prod** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel heißt die Sandbox **Bootcamp**. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 3.3.1 Journey erstellen

Klicken Sie im linken Menü auf **Journeys**. Klicken Sie anschließend auf **Journey erstellen**, um eine neue Journey zu erstellen.

![ACOP](./images/createjourney.png)

Daraufhin wird ein leerer Journey-Bildschirm angezeigt.

![ACOP](./images/journeyempty.png)

In der vorherigen Übung haben Sie ein neues &quot;**&quot;**. Sie haben ihn wie `yourLastNameBeaconEntryEvent` benannt und `yourLastName` durch Ihren Nachnamen ersetzt. Dies war das Ergebnis der Erstellung des Ereignisses:

![ACOP](./images/eventdone.png)

Jetzt müssen Sie dieses Ereignis als Beginn dieser Journey nehmen. Dies können Sie tun, indem Sie zur linken Seite Ihres Bildschirms gehen und in der Ereignisliste nach Ihrem Ereignis suchen.

![ACOP](./images/eventlist.png)

Wählen Sie Ihr Ereignis aus und ziehen Sie es per Drag-and-Drop auf die Journey-Arbeitsfläche. Ihr Journey sieht jetzt wie folgt aus. Klicken Sie auf **OK**, um Ihre Änderungen zu speichern.

![ACOP](./images/journeyevent.png)

Als zweiten Schritt auf der Journey müssen Sie eine **Push“-** hinzufügen. Gehen Sie auf der linken Seite des Bildschirms zu **Aktionen** wählen Sie die Aktion **Push** aus und ziehen Sie sie dann per Drag-and-Drop auf den zweiten Knoten in Ihrem Journey.

![ACOP](./images/journeyactions.png)

Jetzt müssen Sie Ihre Push-Benachrichtigung auf der rechten Bildschirmseite erstellen.

Legen Sie die **Kategorie** auf **Marketing** fest und wählen Sie eine Push-Oberfläche aus, mit der Sie Push-Benachrichtigungen senden können. In diesem Fall ist die auszuwählende Push-Oberfläche **mmeeewis-app-mobile-bootcamp**.

![ACOP](./images/journeyactions1.png)

## 3.3.2 Erstellen einer Nachricht

Klicken Sie **Inhalt bearbeiten**.

![ACOP](./images/emptymsg.png)

Sie sehen dann Folgendes:

![ACOP](./images/emailmsglist.png)

Definieren wir den Inhalt der Push-Benachrichtigung.

Klicken Sie auf **Textfeld** Titel“.

![Journey Optimizer](./images/msg5.png)

Beginnen Sie im Textbereich mit dem Schreiben **Hi**. Klicken Sie auf das Personalisierungssymbol.

![Journey Optimizer](./images/msg6.png)

Nun müssen Sie das Personalisierungs-Token für das Feld **Vorname“ einfügen** das unter `profile.person.name.firstName` gespeichert ist. Wählen Sie im linken Menü **Profilattribute**, scrollen Sie nach unten/navigieren Sie, um das Element **Person** zu finden, und klicken Sie auf den Pfeil, um eine Ebene tiefer zu gehen, bis Sie die `profile.person.name.firstName` erreichen. Klicken Sie auf das Symbol **+** , um das Feld zur Arbeitsfläche hinzuzufügen. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/msg7.png)

Dann bist du wieder hier. Klicken Sie auf das Personalisierungssymbol neben dem Feld **Hauptteil**.

![Journey Optimizer](./images/msg11.png)

Schreiben Sie `Welcome at the ` in den Textbereich.

![Journey Optimizer](./images/msg12.png)

Klicken Sie anschließend auf **Kontextuelle Attribute** und dann auf **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Klicken Sie auf **Ereignisse**.

![ACOP](./images/jomsg4.png)

Klicken Sie auf den Namen Ihres Ereignisses, der wie folgt aussehen sollte: **yourLastNameBeaconEntryEvent**.

![ACOP](./images/jomsg5.png)

Klicken Sie **Ortskontext**.

![ACOP](./images/jomsg6.png)

Klicken Sie **POI Interaction**.

![ACOP](./images/jomsg7.png)

Klicken Sie auf **POI-Detail**.

![ACOP](./images/jomsg8.png)

Klicken Sie auf das Symbol **+** in **POI-Name**.
Sie werden es dann sehen. Klicken Sie auf **Speichern**.

![ACOP](./images/jomsg9.png)

Ihre Nachricht ist jetzt bereit. Klicken Sie auf den Pfeil oben links, um zu Ihrem Journey zurückzukehren.

![ACOP](./images/jomsg11.png)

Klicken Sie auf **OK**.

![ACOP](./images/jomsg14.png)

## 3.3.2 Senden einer Nachricht an einen Bildschirm

Als dritten Schritt auf der Journey müssen Sie eine Aktion **sendMessageToScreen** hinzufügen. Gehen Sie auf der linken Seite des Bildschirms zu **Aktionen**, wählen Sie die Aktion **sendMessageToScreen** aus und ziehen Sie sie dann per Drag-and-Drop auf den dritten Knoten in Ihrem Journey. Sie werden es dann sehen.

![ACOP](./images/jomsg15.png)

Die **sendMessageToScreen**-Aktion ist eine benutzerdefinierte Aktion, mit der eine Nachricht an dem Endpunkt veröffentlicht wird, der von der Anzeige im Geschäft verwendet wird. Die **sendMessageToScreen**-Aktion erwartet, dass eine Reihe von Variablen definiert wird. Sie können diese Variablen anzeigen, indem Sie nach unten scrollen, bis Sie **Aktionsparameter** sehen.

![ACOP](./images/jomsg16.png)

Jetzt müssen Sie die Werte für jeden Aktionsparameter festlegen. In dieser Tabelle erfahren Sie, welche Werte wo erforderlich sind.

| Parameter | Wert |
|:-------------:| :---------------:|
| VERSAND | `'image'` |
| ECID | `@{yourLastNameBeaconEntryEvent._experienceplatform.identification.core.ecid}` |
| VORNAME | `#{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName}` |
| EREIGNISBETREFF | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first().name}` |
| EVENTSUBJECTURL | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first()._experienceplatform.core.imageURL}` |
| SANDBOX | `'bootcamp'` |
| CONTAINER-ID | `''` |
| ACTIVITYID | `''` |
| PLACEMENTID | `''` |

{style="table-layout:auto"}

Um diese Werte festzulegen, klicken Sie auf das Symbol **Bearbeiten**.

![ACOP](./images/jomsg17.png)

Wählen Sie als Nächstes **Erweiterter Modus** aus.

![ACOP](./images/jomsg18.png)

Fügen Sie dann den Wert basierend auf der obigen Tabelle ein. Klicken Sie auf **OK**.

![ACOP](./images/jomsg19.png)

Wiederholen Sie diesen Vorgang, um Werte für jedes Feld hinzuzufügen.

>[!IMPORTANT]
>
>Für das Feld ECID gibt es einen Verweis auf die `yourLastNameBeaconEntryEvent`. Bitte stellen Sie sicher, dass Sie `yourLastName` durch Ihren Nachnamen ersetzen.

Das Endergebnis sollte wie folgt aussehen:

![ACOP](./images/jomsg20.png)

Scrollen Sie nach oben und klicken Sie auf **OK**.

![ACOP](./images/jomsg21.png)

Sie müssen Ihrem Journey dennoch einen Namen geben. Klicken Sie dazu auf das **Bleistift**-Symbol oben links auf Ihrem Bildschirm.

![ACOP](./images/journeyname.png)

Geben Sie hier den Namen der Journey ein. Bitte verwenden Sie `yourLastName - Beacon Entry Journey`. Klicken Sie auf **OK**, um die Änderungen zu speichern.

![ACOP](./images/journeyname1.png)

Sie können Ihren Journey jetzt veröffentlichen, indem Sie auf **Publish** klicken.

![ACOP](./images/publishjourney.png)

Klicken Sie erneut auf **** Publish.

![ACOP](./images/publish1.png)

Sie sehen dann eine grüne Bestätigungsleiste, dass Ihr Journey jetzt veröffentlicht ist.

![ACOP](./images/published.png)

Ihr Journey ist jetzt live und kann ausgelöst werden.

Sie haben jetzt diese Übung beendet.

Nächster Schritt: [3.4 Journey testen](./ex4.md)

[Zurück zu Benutzerfluss 3](./uc3.md)

[Zurück zu „Alle Module“](../../overview.md)
