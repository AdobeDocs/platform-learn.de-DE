---
title: Erstellen eines XDM-Schemas
description: Erfahren Sie, wie Sie ein XDM-Schema für App-Ereignisse erstellen.
feature: Mobile SDK,Schemas
exl-id: c6b0d030-437a-4afe-b7d5-5a7831877983
source-git-commit: bc53cb5926f708408a42aa98a1d364c5125cb36d
workflow-type: tm+mt
source-wordcount: '1314'
ht-degree: 18%

---

# Erstellen eines XDM-Schemas

Erfahren Sie, wie Sie ein XDM-Schema für App-Ereignisse erstellen.

>[!INFO]
>
> Dieses Tutorial wird Ende November 2023 mithilfe einer neuen Beispiel-Mobile-App durch ein neues Tutorial ersetzt.

Standardisierung und Interoperabilität sind Schlüsselkonzepte von Adobe Experience Platform. Das von Adobe unterstützte Experience-Datenmodell (XDM) ermöglicht die Standardisierung von Kundenerlebnisdaten und die Definition von Schemas für das Customer Experience Management.

## Was sind XDM-Schemata?

XDM ist eine öffentlich dokumentierte Spezifikation, die die Leistungsfähigkeit digitaler Erlebnisse verbessern soll. Es bietet allgemeine Strukturen und Definitionen, die es jeder Anwendung ermöglichen, mit Platform-Diensten zu kommunizieren. Durch die Einhaltung von XDM-Standards können alle Kundenerlebnisdaten in ein gemeinsames System integriert werden, wodurch Erkenntnisse schneller und besser integriert verfügbar werden. Sie können wertvolle Einblicke durch Kundenaktionen gewinnen, Zielgruppen mithilfe von Segmenten definieren und Kundenattribute zur Personalisierung verwenden.

Schemas dienen in Experience Platform zur konsistenten und wiederverwendbaren Beschreibung der Struktur von Daten. Durch die systemübergreifende einheitliche Definition von Daten wird es einfacher, deren Bedeutung beizubehalten und somit Wert aus Daten zu ziehen.

Bevor Daten in Platform aufgenommen werden können, muss ein Schema erstellt werden, das die Datenstruktur beschreibt und den Datentyp entsprechend des jeweiligen Feldes einschränkt. Schemas bestehen aus einer Basisklasse und keiner oder mehreren Schema-Feldergruppen.

Weitere Informationen zum Schema-Kompositionsmodell, einschließlich Designgrundsätzen und Best Practices, finden Sie in der [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=de) oder des Kurses [Modellieren Ihrer Kundenerlebnisdaten mit XDM](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de).

>[!TIP]
>
>Wenn Sie mit Analytics Solution Design Reference (SDRs) vertraut sind, können Sie sich ein Schema als robustere SDR vorstellen.

## Voraussetzungen

Um die Lektion abzuschließen, müssen Sie über die Berechtigung zum Erstellen eines Experience Platform-Schemas verfügen.

## Lernziele

In dieser Lektion werden Sie:

* Erstellen eines Schemas in der Datenerfassungsoberfläche
* Hinzufügen einer Standardfeldgruppe zum Schema
* Erstellen und Hinzufügen einer benutzerdefinierten Feldergruppe zum Schema

## Navigieren zu Schemata

1. Melden Sie sich bei Adobe Experience Cloud an.

1. Öffnen Sie den App-Umschalter und wählen Sie **[!UICONTROL Datenerfassung]**

   ![3x3-Dropdown](assets/mobile-schema-navigate1.png)

1. Stellen Sie sicher, dass Sie sich in der Experience Platform-Sandbox befinden, die Sie für dieses Tutorial verwenden.

   >[!NOTE]
   >
   > Kunden von Platform-basierten Anwendungen wie Real-Time CDP sollten für dieses Tutorial eine Entwicklungs-Sandbox verwenden. Andere Kunden verwenden die standardmäßige Produktions-Sandbox.


1. Auswählen **[!UICONTROL Schemas]** under **[!UICONTROL Data Management]**.

   ![Tags-Startbildschirm](assets/mobile-schema-navigate3.png)

Sie befinden sich nun auf der Hauptseite der Schemas und erhalten eine Liste der vorhandenen Schemas. Sie können auch Registerkarten sehen, die den Kernbausteinen eines Schemas entsprechen:

* **Feldergruppen** sind wiederverwendbare Komponenten, die ein oder mehrere Felder definieren, um bestimmte Daten zu erfassen, z. B. persönliche Details, Hotelpräferenzen oder Adressen.
* **Klassen** definieren die Verhaltensaspekte der Daten, die das Schema enthält. Beispiel: `XDM ExperienceEvent` erfasst Zeitreihen, Ereignisdaten und `XDM Individual Profile` erfasst Attributdaten zu einer Person.
* **Datentypen** werden als Referenzfeldtypen in Klassen oder Feldgruppen auf die gleiche Weise wie grundlegende literale Felder verwendet.

Die obigen Beschreibungen geben einen Überblick auf hoher Ebene. Weitere Informationen finden Sie unter [Schema-Bausteine](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/schema-building-blocks.html?lang=de) Video oder lesen [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=de) in der Produktdokumentation.

In diesem Tutorial verwenden Sie die Feldergruppe &quot;Consumer Experience Event&quot;und erstellen eine benutzerdefinierte, um den Prozess zu demonstrieren.

>[!NOTE]
>
>Adobe fügt weiterhin mehr Standardfeldgruppen hinzu und sollten nach Möglichkeit verwendet werden, da diese Felder implizit von Experience Platform-Diensten verstanden werden und bei der Verwendung über Plattformkomponenten hinweg eine größere Konsistenz gewährleistet ist. Die Verwendung von Standardfeldgruppen bietet greifbare Vorteile wie die automatische Zuordnung in Analytics- und AI-Funktionen in Platform.

## Architektur des Luma-App-Schemas

In einem realen Szenario könnte der Schemaentwurfsprozess wie folgt aussehen:

* Sammeln Sie Geschäftsanforderungen.
* Suchen Sie nach vordefinierten Feldergruppen, um so viele Anforderungen wie möglich abzudecken.
* Erstellen Sie benutzerdefinierte Feldergruppen für Lücken.

Zu Lernzwecken verwenden Sie vordefinierte und benutzerdefinierte Feldergruppen.

* **Ereignis für Kundenerlebnisse**: Vordefinierte Feldergruppe mit vielen gemeinsamen Feldern.
* **App-Informationen**: Benutzerdefinierte Feldergruppe, die für die Nachahmung von TrackState-/TrackAction-Analytics-Konzepten entwickelt wurde.

<!--Later in the tutorial, you can [update the schema](lifecycle-data.md) to include the **[!UICONTROL AEP Mobile Lifecycle Details]** field group.-->

## Erstellen eines Schemas

1. Auswählen **[!UICONTROL Schema erstellen]** um das Dropdown-Menü &quot;Optionen&quot;aufzurufen, wählen Sie **[!UICONTROL XDM ExperienceEvent]**.

   ![Auswählen von ExperienceEvent aus der Dropdown-Liste](assets/mobile-schema-create.png)

1. Suchen Sie nach `Consumer Experience Event`.

1. Sie können eine Vorschau der Felder anzeigen und/oder die Beschreibung lesen, um weitere Details zu erhalten, bevor Sie sie auswählen.

1. Aktivieren Sie das Kontrollkästchen und klicken Sie auf **[!UICONTROL Feldergruppen hinzufügen]**.

   ![Feldgruppe auswählen](assets/mobile-schema-select-field-groups.png)

   Sie gelangen zurück zum Bildschirm zur Hauptschemakomposition, wo Sie alle verfügbaren Felder sehen können.

1. Geben Sie Ihrem Schema einen Namen, indem Sie **[!UICONTROL Unbenanntes Schema]** von oben links aus und geben Sie dann eine **[!UICONTROL Anzeigename]** &amp; **[!UICONTROL Beschreibung]**, beispielsweise `Luma Tutorial Mobile` und `"Luma App" schema for Adobe Tutorial`

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Anwenden auswählen](assets/mobile-schema-name-save.png)

>[!NOTE]
>
>Beachten Sie, dass nicht alle Felder einer Gruppe verwendet werden müssen. Wenn es hilfreich ist, können Sie sich ein Schema als leere Datenschicht vorstellen. In Ihrer App füllen Sie die entsprechenden Werte zum richtigen Zeitpunkt aus.
>
>Die `Consumer Experience Event` hat einen Datentyp namens `Web information`, der Ereignisse wie Seitenansichten und Link-Klicks beschreibt. Zum Zeitpunkt des Schreibens gibt es keine App-Parität für diese Funktion. Daher erstellen Sie Ihre eigene.

## Erstellen eines benutzerdefinierten Datentyps

Erstellen Sie zunächst einen benutzerdefinierten Datentyp, der die beiden Ereignisse beschreibt:

* Bildschirmansicht
* App-Interaktion

1. Wählen Sie die **[!UICONTROL Datentypen]** Registerkarte und wählen Sie **[!UICONTROL Erstellen eines Datentyps]**.

   ![Datentypmenü auswählen](assets/mobile-schema-datatype-create.png)

1. Geben Sie einen **[!UICONTROL Anzeigename]** und **[!UICONTROL Beschreibung]**, beispielsweise `App Information` und `Custom data type describing "Screen Views" & "App Actions"`

   ![Name und Beschreibung angeben](assets/mobile-schema-datatype-name.png)

   >[!TIP]
   >
   > Immer lesbar, beschreibend verwenden [!UICONTROL Anzeigenamen] für Ihre benutzerdefinierten Felder verwenden, da diese Vorgehensweise Marketing-Experten den Zugriff darauf erleichtert, wenn die Felder in nachgelagerten Diensten wie dem Segment Builder angezeigt werden.


1. Um ein Feld hinzuzufügen, wählen Sie die Schaltfläche (+) aus.

   Dieses Feld ist ein Container-Objekt für die App-Interaktion. Gib ihm ein Kamelgehäuse **[!UICONTROL Feldname]** `appInteraction`, **[!UICONTROL Anzeigename]** `App Interaction`, und **[!UICONTROL type]** `Object`.

1. Wählen Sie **[!UICONTROL Anwenden]** aus.

   ![Hinzufügen eines neuen App-Aktionsereignisses](assets/mobile-schema-datatype-app-action.png)

1. Um zu messen, wie oft eine Aktion aufgetreten ist, fügen Sie ein Feld hinzu, indem Sie die Schaltfläche (+) neben dem `appInteraction` -Objekt, das Sie erstellt haben.

1. Gib ihm ein Kamelgehäuse **[!UICONTROL Feldname]** `appAction`, **[!UICONTROL Anzeigename]** von `App Action` und **[!UICONTROL type]** `Measure`.

   Dieser Schritt entspricht einem Erfolgsereignis in Adobe Analytics.

1. Wählen Sie **[!UICONTROL Anwenden]** aus.

   ![Feld für Aktionsnamen hinzufügen](assets/mobile-schema-datatype-action-name.png)

1. Fügen Sie ein Feld hinzu, das den Interaktionstyp beschreibt, indem Sie die Schaltfläche (+) neben dem `appInteraction` -Objekt.

1. Geben Sie einen **[!UICONTROL Feldname]** `name`, **[!UICONTROL Anzeigename]** von `Name` und **[!UICONTROL type]** `String`.

   Dieser Schritt entspricht einer Dimension in Adobe Analytics.

   ![Anwenden auswählen](assets/mobile-schema-datatype-apply.png)

1. Scrollen Sie nach unten in der rechten Leiste und wählen Sie **[!UICONTROL Anwenden]**.

1. Gehen Sie zum Erstellen eines `appStateDetails` Objekt, das ein Messfeld namens enthält `screenView` und zwei Zeichenfolgen mit dem Namen `screenName` und `screenType`.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Endgültiger Status des Datentyps](assets/mobile-schema-datatype-final.png)

## Benutzerdefinierte Feldergruppe hinzufügen

Fügen Sie nun mithilfe Ihres benutzerdefinierten Datentyps eine benutzerdefinierte Feldergruppe hinzu:

1. Öffnen Sie das Schema, das Sie zuvor in dieser Lektion erstellt haben.

1. Auswählen **[!UICONTROL Hinzufügen]** neben **[!UICONTROL Feldergruppen]**.

   ![Neue Feldergruppe hinzufügen](assets/mobile-schema-fieldgroup-add.png)

1. Wenn Sie dieses Mal eine benutzerdefinierte Feldergruppe erstellen, wählen Sie die **[!UICONTROL Neue Feldergruppe erstellen]** Optionsfeld oben, geben Sie dann einen Namen und eine Beschreibung ein, z. B. `App Interactions` und `Fields for app interactions`.

   ![Name und Beschreibung angeben](assets/mobile-schema-fieldgroup-name.png)

1. Fügen Sie im Hauptkompositionsbildschirm ein Feld zum Stammverzeichnis des Schemas hinzu.

1. Wählen Sie das (+) neben dem Namen des Schemas aus.

1. Geben Sie in der rechten Leiste einen **[!UICONTROL Feldname]** von `appInformation`, einen Anzeigenamen von `App Information`.

1. Auswählen `App Information` aus dem **[!UICONTROL Typ]** Dropdown-Liste den Datentyp aus, den Sie in der vorherigen Übung erstellt haben.

1. Wählen Sie **[!UICONTROL Anwenden]** aus.

   ![Anwenden auswählen](assets/mobile-schema-fieldgroup-apply.png)

>[!NOTE]
>
>Benutzerdefinierte Feldergruppen werden immer unter Ihrer Experience Cloud-Organisationskennung platziert.
>
>`_techmarketingdemos` durch den eindeutigen Wert Ihrer Organisation ersetzt.

Sie haben jetzt ein Schema, das für den Rest des Tutorials verwendet werden kann.

Weiter: **[Erstellen Sie eine [!UICONTROL datastream]](create-datastream.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)