---
title: Erstellen und Anzeigen von Angeboten mit dem Platform Mobile SDK
description: Erfahren Sie, wie Sie mit dem Platform Mobile SDK und der Adobe Journey Optimizer-Entscheidungsverwaltung Angebote erstellen und anzeigen.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: Offers
jira: KT-14640
exl-id: c08a53cb-683e-4487-afab-fd8828c3d830
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '2470'
ht-degree: 2%

---

# Erstellen und Anzeigen von Angeboten mit der Entscheidungsverwaltung

Erfahren Sie, wie Sie mit dem Experience Platform Mobile SDK Angebote aus Journey Optimizer Decision Management in Ihren mobilen Apps anzeigen können.

Mit der Entscheidungsverwaltung von Journey Optimizer können Sie Ihren Kunden das beste Angebot und Erlebnis für alle Touchpoints zur richtigen Zeit bereitstellen. Danach können Sie Ihre Audience mit personalisierten Angeboten auswählen.

![Architektur](assets/architecture-ajo.png)

Die Entscheidungsverwaltung erleichtert die Personalisierung mit einer zentralen Bibliothek von Marketing-Angeboten und einer Entscheidungs-Engine, die Regeln und Begrenzungen auf von Adobe Experience Platform erstellte umfangreiche Echtzeit-Profile anwendet. Dadurch können Sie Ihren Kunden das richtige Angebot zum richtigen Zeitpunkt senden. Weitere Informationen finden Sie unter [Über die Entscheidungsverwaltung](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=en) .




>[!NOTE]
>
>Diese Lektion ist optional und gilt nur für Journey Optimizer-Benutzer, die die Entscheidungsverwaltungsfunktion verwenden möchten, um Angebote in einer Mobile App anzuzeigen.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.
* Richten Sie die App für Adobe Experience Platform ein.
* Zugriff auf Journey Optimizer - Entscheidungsverwaltung mit den entsprechenden Berechtigungen zum Verwalten von Angeboten und Entscheidungen, wie [hier](https://experienceleague.adobe.com/docs/journey-optimizer/using/access-control/privacy/high-low-permissions.html?lang=en#decisions-permissions) beschrieben.


## Lernziele

In dieser Lektion werden Sie

* Aktualisieren Sie Ihre Edge-Konfiguration für die Entscheidungsverwaltung.
* Aktualisieren Sie Ihre Tag-Eigenschaft mit der Journey Optimizer - Decisioning-Erweiterung.
* Aktualisieren Sie Ihr Schema, um Vorschlagsereignisse zu erfassen.
* Validieren Sie die Einrichtung in &quot;Assurance&quot;.
* Erstellen Sie eine Angebotsentscheidung, die auf Angeboten in Journey Optimizer - Entscheidungsverwaltung basiert.
* Aktualisieren Sie Ihre App, um die Optimizer-Erweiterung zu registrieren.
* Implementieren Sie Angebote aus der Entscheidungsverwaltung in Ihre App.


## Einrichten

>[!TIP]
>
>Wenn Sie Ihre Umgebung bereits im Rahmen der Lektion [A/B-Tests mit Target einrichten](target.md) eingerichtet haben, haben Sie möglicherweise bereits einige der Schritte in diesem Einrichtungsabschnitt ausgeführt.

### Aktualisierung der Konfiguration des Datenspeichers

Um sicherzustellen, dass Daten, die von Ihrer Mobile App an Platform Edge Network gesendet werden, an Journey Optimizer weitergeleitet werden - Entscheidungsverwaltung, aktualisieren Sie Ihren Datenspeicher.

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche **[!UICONTROL Datastreams]** aus und wählen Sie Ihren Datastream aus, z. B. **[!DNL Luma Mobile App]**.
1. Wählen Sie ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) für **[!UICONTROL Experience Platform]** und dann ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Bearbeiten]** aus dem Kontextmenü.
1. Stellen Sie im Bildschirm **[!UICONTROL Datastreams]** > ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) > **[!UICONTROL Adobe Experience Platform]** sicher, dass die Optionen **[!UICONTROL Offer decisioning]**, **[!UICONTROL Edge Segmentation]** und **[!UICONTROL Adobe Journey Optimizer]** ausgewählt sind. Wenn Sie die Target-Lektion ausführen, wählen Sie auch **[!UICONTROL Personalization-Ziele]** aus. Weitere Informationen finden Sie unter [Adobe Experience Platform-Einstellungen](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=en#aep) .
1. Wählen Sie **[!UICONTROL Speichern]** aus, um Ihre Datastream-Konfiguration zu speichern.

   ![AEP-Datastream-Konfiguration](assets/datastream-aep-configuration-offers.png)




### Installieren von Journey Optimizer - Decisioning Tags-Erweiterung

1. Navigieren Sie zu **[!UICONTROL Tags]** , suchen Sie Ihre mobile Tag-Eigenschaft und öffnen Sie die Eigenschaft .
1. Wählen Sie **[!UICONTROL Erweiterungen]** aus.
1. Wählen Sie **[!UICONTROL Katalog]** aus.
1. Suchen Sie nach der Erweiterung **[!UICONTROL Adobe Journey Optimizer - Decisioning]** .
1. Installieren Sie die -Erweiterung. Die Erweiterung erfordert keine zusätzliche Konfiguration.

   ![Entscheidungserweiterung hinzufügen](assets/tag-add-decisioning-extension.png)


### Schema aktualisieren

1. Navigieren Sie zur Datenerfassungsoberfläche und wählen Sie in der linken Leiste **[!UICONTROL Schemas]** aus.
1. Wählen Sie in der oberen Leiste **[!UICONTROL Durchsuchen]** aus.
1. Wählen Sie Ihr Schema aus, um es zu öffnen.
1. Wählen Sie im Schema-Editor neben Feldgruppen die Option ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** aus.
1. Wählen Sie im Dialogfeld **[!UICONTROL Feldergruppen hinzufügen]** die Option ![Suche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) nach `proposition`, wählen Sie **[!UICONTROL Erlebnisereignis - Vorschlagsinteraktionen]** und dann **[!UICONTROL Feldergruppen hinzufügen]** aus. Diese Feldergruppe erfasst die Erlebnisereignisdaten, die für Angebote relevant sind: welches Angebot wird präsentiert, als Teil von Sammlung, Entscheidung und anderen Parametern (siehe weiter unten in dieser Lektion). Aber was passiert auch mit dem Angebot? Wird angezeigt, interagiert, verworfen usw.
   ![proposition](assets/schema-fieldgroup-proposition.png)
1. Wählen Sie **[!UICONTROL Speichern]** aus, um die Änderungen an Ihrem Schema zu speichern.


## Validieren der Einrichtung in der Zuverlässigkeitserklärung

So überprüfen Sie Ihre Einrichtung in Assurance:

1. Navigieren Sie zur Benutzeroberfläche &quot;Assurance&quot;.
1. Wählen Sie **[!UICONTROL Konfigurieren]** in der linken Leiste und klicken Sie auf ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) neben **[!UICONTROL Einrichtung validieren]** unter **[!UICONTROL ADOBE JOURNEY OPTIMIZER-ENTSCHEIDUNG]**.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
1. Wählen Sie in der linken Leiste **[!UICONTROL Setup überprüfen]** aus. Sowohl die Datastream-Einrichtung als auch das SDK-Setup in Ihrer Anwendung werden validiert.
   ![AJO Decisioning-Validierung](assets/ajo-decisioning-validation.png)


## Platzierung erstellen

Bevor Sie Angebote erstellen können, müssen Sie definieren, wie und wo diese Angebote in der App platziert werden können. In der Entscheidungsverwaltung definieren Sie zu diesem Zweck Platzierungen und definieren eine Platzierung für den Mobile-Kanal, die eine JSON-Payload unterstützt:

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche in der linken Leiste ![Komponenten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OfferActivities_18_N.svg) **[!UICONTROL Komponenten]** aus **[!UICONTROL ENTSCHEIDUNGSMANAGEMENT]** .

1. Wählen Sie in der oberen Leiste **[!UICONTROL Platzierungen]** aus.

1. Wenn keine Platzierung mit dem Namen **[!UICONTROL Mobile JSON]**, **[!UICONTROL Mobile]** als **[!UICONTROL Kanaltyp]** und **[!UICONTROL JSON]** als **[!UICONTROL Inhaltstyp]** aufgeführt ist, müssen Sie eine Platzierung erstellen. Fahren Sie andernfalls mit [Angebote erstellen](#create-offers) fort.

So erstellen Sie die mobile JSON-Platzierung:

1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) Platzierung erstellen aus.

   1. Geben Sie im Abschnitt **[!UICONTROL Details]** den Wert `Mobile JSON` als den Wert **[!UICONTROL Namen]** ein, wählen Sie **[!UICONTROL Mobil]** aus dem Wert **[!UICONTROL Kanaltyp]** und **[!UICONTROL JSON]** aus dem Wert **[!UICONTROL Inhaltstyp]**.
   1. Wählen Sie **[!UICONTROL Speichern]** aus, um die Platzierung zu speichern.

   ![Platzierung erstellen](assets/ajo-create-placement.png)



## Angebote erstellen

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche in der linken Leiste unter **[!UICONTROL DECISION MANAGEMENT]** die Option ![Angebote](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Offers_18_N.svg) **[!UICONTROL Angebote]** aus.
1. Wählen Sie im Bildschirm **[!UICONTROL Angebote]** die Option **[!UICONTROL Durchsuchen]** aus, um die Liste der Angebote anzuzeigen.
1. Wählen Sie **[!UICONTROL Angebot erstellen]** aus.
1. Wählen Sie im Dialogfeld **[!UICONTROL Neues Angebot]** die Option **[!UICONTROL Personalisiertes Angebot]** und klicken Sie auf **[!UICONTROL Weiter]**.
1. Im Schritt **[!UICONTROL Details]** von **[!UICONTROL Neues personalisiertes Angebot erstellen]**:
   1. Geben Sie einen **[!UICONTROL Namen]** für das Angebot ein, z. B. `Luma - Juno Jacket`, und geben Sie ein **[!UICONTROL Startdatum und -zeit]** sowie ein **[!UICONTROL Enddatum und eine Endzeit]** ein. Außerhalb dieses Datumsbereichs wird das Angebot nicht von der Entscheidungs-Engine ausgewählt.
   1. Klicken Sie auf **[!UICONTROL Weiter]**.
      ![Angebote - Details](assets/ajo-offers-details.png)

1. Im Schritt **[!UICONTROL Darstellungen hinzufügen]** von **[!UICONTROL Neues personalisiertes Angebot erstellen]**:
   1. Wählen Sie ![Mobil](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DevicePhone_18_N.svg) **[!UICONTROL Mobil]** aus der Liste **[!UICONTROL Kanal]** und dann **[!UICONTROL Mobil JSON]** aus der Liste **[!UICONTROL Platzierung]**.
   1. Wählen Sie **[!UICONTROL Benutzerdefiniert]** für **[!UICONTROL Inhalt]** aus.
   1. Wählen Sie **[!UICONTROL Inhalt hinzufügen]** aus. Im Dialogfeld **[!UICONTROL Personalisierung hinzufügen]** :
      1. Wenn ein [!UICONTROL Modus] -Selektor verfügbar ist, stellen Sie sicher, dass er auf **[!UICONTROL JSON]** eingestellt ist.
      1. Geben Sie die folgende JSON ein:

         ```json
         { 
             "title": "Juno Jacket",
             "text": "On colder-than-comfortable mornings, you'll love warming up in the Juno All-Ways Performance Jacket, designed to compete with wind and chill. Built-in Cocona&trade; technology aids evaporation, while a special zip placket and stand-up collar keep your neck protected.", 
             "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/women/tops/jackets/wj06-purple_main.jpg" 
         }  
         ```

      1. Wählen Sie **[!UICONTROL Speichern]** aus.
         ![Angebote - Benutzerspezifischer Inhalt](assets/ajo-offers-customcontent.png)
   1. Klicken Sie auf **[!UICONTROL Weiter]**.
      ![Angebotsdarstellungen](assets/ajo-offers-representations.png)

1. Fügen Sie im Schritt **[!UICONTROL Einschränkungen hinzufügen]** des Schritts **[!UICONTROL Neues personalisiertes Angebot erstellen]** Folgendes hinzu:
   1. Setzen Sie **[!UICONTROL Priorität]** auf `10`.
   1. Schalten Sie **[!UICONTROL Begrenzungen einschließen]** aus.
   1. Klicken Sie auf **[!UICONTROL Weiter]**.
      ![Angebote - Begrenzungen](assets/ajo-offers-constraints.png)

1. Im Schritt **[!UICONTROL Überprüfen]** des Schritts **[!UICONTROL Neues personalisiertes]** Angebot erstellen:
   1. Überprüfen Sie das Angebot und wählen Sie dann **[!UICONTROL Beenden]** aus.
   1. Wählen Sie im Dialogfeld **[!UICONTROL Angebot speichern]** die Option **[!UICONTROL Speichern und genehmigen]**.

1. Wiederholen Sie die Schritte 3 bis 8, um vier weitere Angebote mit unterschiedlichen Namen und Inhalten zu erstellen. Alle anderen Konfigurationswerte, z. B. Startdatum und -zeit oder -priorität, ähneln dem ersten von Ihnen erstellten Angebot. Sie können Angebote schnell duplizieren und bearbeiten.

   1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche in der linken Leiste die Option ![Angebote](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Offers_18_N.svg) **[!UICONTROL Angebote]** und dann in der oberen Leiste die Option Angebote aus.
   1. Wählen Sie die Zeile des erstellten Angebots aus.
   1. Wählen Sie im rechten Bereich ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmall_18_N.svg) **[!UICONTROL Mehr Aktionen]** und wählen Sie im Kontextmenü die Option ![Duplizieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Duplicate_18_N.svg) **[!UICONTROL Duplizieren]**.

      Verwenden Sie die nachstehende Tabelle, um die vier anderen Angebote zu definieren.

      | Name des Angebots | Angebotsinhalt in JSON |
      |---|---|
      | Luma - Affirsiche Wasserflasche | `{ "title": "Affirm Water Bottle", "text": "You'll stay hydrated with ease with the Affirm Water Bottle by your side or in hand. Measurements on the outside help you keep track of how much you're drinking, while the screw-top lid prevents spills. A metal carabiner clip allows you to attach it to the outside of a backpack or bag for easy access.", "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/fitness-equipment/ug06-lb-0.jpg" }` |
      | Luma - Fitness-Tee | `{ "title": "Desiree Fitness Tee", "text": "When you're too far to turn back, thank yourself for choosing the Desiree Fitness Tee. Its ultra-lightweight, ultra-breathable fabric wicks sweat away from your body and helps keeps you cool for the distance.", "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/women/tops/tees/ws05-yellow_main.jpg" }` |
      | Luma - Adrienne Trek Jacket | `{ "title": "Adrienne Trek Jacket", "text": "You're ready for a cross-country jog or a coffee on the patio in the Adrienne Trek Jacket. Its style is unique with stand collar and drawstrings, and it fits like a jacket should.", "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/women/tops/jackets/wj08-gray_main.jpg" }` |
      | Luma - Aero Daily Fitness Tee | `{ "title": "Aero Daily Fitness Tee", "text": "Need an everyday action tee that helps keep you dry? The Aero Daily Fitness Tee is made of 100% polyester wicking knit that funnels moisture away from your skin. Don't be fooled by its classic style; this tee hides premium performance technology beneath its unassuming look.", "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/men/tops/tees/ms01-black_main.jpg" }` |

      {style="table-layout:fixed"}

1. Als letzten Schritt müssen Sie ein Fallback-Angebot erstellen, bei dem es sich um ein Angebot handelt, das an Kunden gesendet wird, wenn diese nicht für andere Angebote geeignet sind.
   1. Wählen Sie **[!UICONTROL Angebot erstellen]** aus.
   1. Wählen Sie im Dialogfeld **[!UICONTROL Neues Angebot]** die Option **[!UICONTROL Personalisiertes Angebot]** und danach **[!UICONTROL Weiter]** aus.
   1. Geben Sie im Schritt **[!UICONTROL Details]** von **[!UICONTROL Neues Fallback-Angebot erstellen]** einen **[!UICONTROL Namen]** für das Angebot ein, z. B. `Luma - Fallback Offer`, und wählen Sie **[!UICONTROL Weiter]** aus.

   1. Im Schritt **[!UICONTROL Darstellungen hinzufügen]** von **[!UICONTROL Neues Fallback-Angebot erstellen]**:
      1. Wählen Sie ![Mobil](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DevicePhone_18_N.svg) **[!UICONTROL Mobil]** aus der Liste **[!UICONTROL Kanal]** und wählen Sie **[!UICONTROL Mobil JSON]** aus der Liste **[!UICONTROL Platzierung]** aus.
      1. Wählen Sie **[!UICONTROL Benutzerdefiniert]** für **[!UICONTROL Inhalt]** aus.
      1. Wählen Sie **[!UICONTROL Inhalt hinzufügen]** aus.
      1. Geben Sie im Dialogfeld **[!UICONTROL Personalisierung hinzufügen]** die folgende JSON ein und wählen Sie **[!UICONTROL Speichern]** aus:

         ```json
         {  
            "title": "Luma",
            "text": "Your store for sports wear and equipment.", 
            "image": "https://luma.enablementadobe.com/content/dam/luma/en/logos/Luma_Logo.png" 
         }  
         ```

      1. Klicken Sie auf **[!UICONTROL Weiter]**.


1. Im Schritt **[!UICONTROL Überprüfen]** von **[!UICONTROL Neues Fallback-Angebot erstellen]**:
   1. Überprüfen Sie das Angebot und wählen Sie dann **[!UICONTROL Beenden]** aus.
   1. Wählen Sie im Dialogfeld **[!UICONTROL Angebot speichern]** die Option **[!UICONTROL Speichern und genehmigen]**.

Sie sollten nun über die folgende Liste von Angeboten verfügen:
![Angebotsliste](assets/ajo-offers-list.png)


## Erstellen einer Sammlung

Um dem Benutzer Ihrer Mobile App ein Angebot zu unterbreiten, müssen Sie eine Angebotskollektion definieren, die aus einem oder mehreren von Ihnen erstellten Angeboten besteht.

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche in der linken Leiste **[!UICONTROL Angebote]** aus.
1. Wählen Sie in der oberen Leiste **[!UICONTROL Sammlungen]** aus.
1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Sammlung erstellen]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Neue Sammlung]** einen **[!UICONTROL Namen]** für Ihre Sammlung ein, z. B. `Luma - Mobile App Collection`, wählen Sie **[!UICONTROL Statische Sammlung erstellen]** und klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie in **[!DNL Luma - Mobile App Collection]** die Angebote aus, die Sie in die Kollektion aufnehmen möchten. Wählen Sie für dieses Tutorial die fünf von Ihnen erstellten Angebote aus. Sie können die Liste einfach mithilfe des Suchfelds filtern, z. B. durch Eingabe von **[!DNL Luma]**.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Angebote - Sammlung](assets/ajo-collection-offersselected.png)


## Eine Entscheidung erstellen

Der letzte Schritt besteht darin, eine Entscheidung zu definieren, bei der es sich um die Kombination aus einem oder mehreren Entscheidungsbereichen und Ihrem Fallback-Angebot handelt.

Ein Entscheidungsbereich ist eine Kombination aus einer bestimmten Platzierung (z. B. HTML in einer E-Mail oder JSON in einer mobilen App) und einem oder mehreren Bewertungskriterien.

Ein Bewertungskriterium ist die Kombination aus

* eine Angebotskollektion,
* Eignungsregeln: Ist beispielsweise das Angebot nur für eine bestimmte Zielgruppe verfügbar?
* Ranking-Methode: Wenn mehrere Angebote zur Auswahl verfügbar sind, welche Methode Sie verwenden, um sie zu bewerten (z. B. nach Angebotspriorität, anhand einer Formel oder eines KI-Modells).

Weitere Informationen zur Interaktion und zum Bezug zueinander finden Sie unter [Wichtige Schritte zum Erstellen und Verwalten von Angeboten](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/key-steps.html?lang=en) . Diese Lektion konzentriert sich ausschließlich auf die Verwendung der Ergebnisse einer Entscheidung und nicht auf die Flexibilität bei der Definition von Entscheidungen innerhalb von Journey Optimizer - Entscheidungsmanagement.

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche in der linken Leiste **[!UICONTROL Angebote]** aus.
1. Wählen Sie in der oberen Leiste **[!UICONTROL Entscheidungen]** aus.
1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Entscheidung erstellen]**.
1. Im Schritt **[!UICONTROL Details]** von **[!UICONTROL Erstellen einer neuen Angebotsentscheidung]**:
   1. Geben Sie einen **[!UICONTROL Namen]** für die Entscheidung ein, z. B. `Luma - Mobile App Decision`, geben Sie **[!UICONTROL Startdatum und -zeit]** und **[!UICONTROL Enddatum und -zeit]** ein.
   1. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Im Schritt **[!UICONTROL Entscheidungsbereiche hinzufügen]** von **[!UICONTROL Erstellen einer neuen Angebotsentscheidung]**:
   1. Wählen Sie **[!UICONTROL Mobile JSON]** aus der Liste **[!UICONTROL Platzierung]** aus.
   1. Wählen Sie in der Kachel **[!UICONTROL Bewertungskriterien]** die Option ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** aus.
      1. Wählen Sie im Dialogfeld **[!UICONTROL Angebotskollektion hinzufügen]** Ihre Angebotskollektion aus. Beispiel: **[!DNL Luma - Mobile App Collection]**.
      1. Wählen Sie **[!UICONTROL Hinzufügen]** aus.
         ![Entscheidung - Sammlung auswählen](assets/ajo-decision-selectcollection.png)
   1. Stellen Sie sicher, dass für **[!UICONTROL Eignung]** der Wert **[!UICONTROL Keine]** und für **[!UICONTROL Angebotspriorität]** der Wert **[!UICONTROL Ranking method]** ausgewählt ist.
   1. Klicken Sie auf **[!UICONTROL Weiter]**.
      ![Entscheidungsbereiche](assets/ajo-decision-scopes.png).
1. Im Schritt **[!UICONTROL Fallback-Angebot hinzufügen]** von **[!UICONTROL Erstellen einer neuen Angebotsentscheidung]**:
   1. Wählen Sie Ihr Fallback-Angebot aus, z. B. &quot;**[!DNL Luma - Fallback offer]**&quot;.
   1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Im Schritt **[!UICONTROL Zusammenfassung]** von **[!UICONTROL Erstellen einer neuen Angebotsentscheidung]**:
   1. Wählen Sie **[!UICONTROL Beenden]** aus.
   1. Wählen Sie im Dialogfeld **[!UICONTROL Angebotsentscheidung speichern]** die Option **[!UICONTROL Speichern und aktivieren]**.
   1. Auf der Registerkarte **[!UICONTROL Entscheidungen]** sehen Sie Ihre Entscheidung mit dem Status **[!UICONTROL Live]**.

Ihre Angebotsentscheidung, die aus einer Reihe von Angeboten besteht, kann jetzt verwendet werden. Um die Entscheidung in Ihrer App zu verwenden, müssen Sie in Ihrem Code auf den Entscheidungsbereich verweisen.

1. Wählen Sie in der Journey Optimizer-Benutzeroberfläche **[!UICONTROL Angebote]** aus.
1. Wählen Sie in der oberen Leiste **[!UICONTROL Entscheidungen]** aus.
1. Wählen Sie Ihre Entscheidung aus, z. B. **[!DNL Luma - Mobile App Decision]**.
1. Wählen Sie in der Kachel **[!UICONTROL Entscheidungsbereiche]** die Option ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) **[!UICONTROL Kopieren]**.
1. Wählen Sie im Kontextmenü die Option **[!UICONTROL Entscheidungsbereich]** aus.
   ![Entscheidungsbereich kopieren](assets/ajo-copy-decisionscope.png)
1. Verwenden Sie einen beliebigen Texteditor, um den Entscheidungsbereich für die spätere Verwendung einzufügen. Der Entscheidungsbereich hat das folgende JSON-Format.

   ```json
   {
       "xdm:activityId":"xcore:offer-activity:xxxxxxxxxxxxxxx",
       "xdm:placementId":"xcore:offer-placement:xxxxxxxxxxxxxxx"
   }
   ```

## Implementieren von Angeboten in Ihre App

Wie in den vorherigen Lektionen erläutert, bietet die Installation einer mobilen Tag-Erweiterung nur die Konfiguration. Als Nächstes müssen Sie das Optimize SDK installieren und registrieren. Wenn diese Schritte nicht klar sind, lesen Sie den Abschnitt [SDKs installieren](install-sdks.md) .

>[!NOTE]
>
>Wenn Sie den Abschnitt [SDK installieren](install-sdks.md) abgeschlossen haben, ist das SDK bereits installiert und Sie können diesen Schritt überspringen.
>

1. Stellen Sie in Xcode sicher, dass [AEP Optimize](https://github.com/adobe/aepsdk-messaging-ios) zur Liste der Pakete in Package-Abhängigkeiten hinzugefügt wird. Siehe [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** .
1. Stellen Sie sicher, dass `AEPOptimize` Teil Ihrer Importliste ist.

   ```swift
   import AEPOptimize
   ```

1. Stellen Sie sicher, dass `Optimize.self` Teil des Arrays von Erweiterungen ist, die Sie registrieren.

   ```swift
   let extensions = [
       AEPIdentity.Identity.self,
       Lifecycle.self,
       Signal.self,
       Edge.self,
       AEPEdgeIdentity.Identity.self,
       Consent.self,
       UserProfile.self,
       Places.self,
       Messaging.self,
       Optimize.self,
       Assurance.self
   ]
   ```

1. Navigieren Sie im Xcode-Projekt-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Model]** > **[!DNL Data]** > **[!UICONTROL entscheidungen]** . Aktualisieren Sie die Werte `activityId` und `placementId` mit den Details zum Entscheidungsbereich, die Sie aus der Journey Optimizer-Oberfläche kopiert haben.

1. Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** . Suchen Sie die Funktion `func updatePropositionOD(ecid: String, activityId: String, placementId: String, itemCount: Int) async` . Fügen Sie den folgenden Code hinzu:

   ```swift
   // set up the XDM dictionary, define decision scope and call update proposition API
   Task {  
      let ecid = ["ECID" : ["id" : ecid, "primary" : true] as [String : Any]]
      let identityMap = ["identityMap" : ecid]
      let xdmData = ["xdm" : identityMap]
      let decisionScope = DecisionScope(activityId: activityId, placementId: placementId, itemCount: UInt(itemCount))
      Optimize.clearCachedPropositions()
      Optimize.updatePropositions(for: [decisionScope], withXdm: xdmData)
   }
   ```

   Diese Funktion:

   * richtet ein XDM-Wörterbuch `xdmData` ein, das die ECID enthält, um das Profil zu identifizieren, für das Sie die Angebote unterbreiten müssen.
   * definiert `decisionScope`, ein Objekt, das auf der Entscheidung basiert, die Sie in der Journey Optimizer-Entscheidungsverwaltungsoberfläche definiert haben, und das mithilfe des kopierten Entscheidungsbereichs aus [Entscheidungsfindung erstellen](#create-a-decision) definiert wird.  Die Luma-App verwendet eine Konfigurationsdatei (`decisions.json`), die die Perimeter basierend auf dem folgenden JSON-Format abruft:

     ```swift
     "scopes": [
         {
             "name": "name of the scope",
             "activityId": "xcore:offer-activity:xxxxxxxxxxxxxxx",
             "placementId": "xcore:offer-placement:xxxxxxxxxxxxxxx",
             "itemCount": 2
         }
     ]
     ```

     Sie können jedoch jede Art von Implementierung verwenden, um sicherzustellen, dass die Optimize-APIs die richtigen Parameter (`activityId`, `placementId` und `itemCount`) erhalten, um ein gültiges [`DecisionScope`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#decisionscope) -Objekt für Ihre Implementierung zu erstellen. <br/>Für Ihre Informationen: Die anderen Schlüsselwerte in der Datei `decisions.json` sind für die zukünftige Verwendung bestimmt und nicht relevant und werden derzeit in dieser Lektion und als Teil des Tutorials verwendet.

   * ruft zwei APIs auf: [`Optimize.clearCachePropositions`](https://support.apple.com/en-ie/guide/mac-help/mchlp1015/mac) und [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions).  Mit diesen Funktionen werden zwischengespeicherte Vorschläge gelöscht und die Vorschläge für dieses Profil aktualisiert.

1. Navigieren Sie im Xcode-Projektnavigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!UICONTROL Personalization]** > **[!UICONTROL EdgeOffersView]**. Suchen Sie die Funktion `func onPropositionsUpdateOD(activityId: String, placementId: String, itemCount: Int) async` und überprüfen Sie den Code dieser Funktion. Der wichtigste Teil dieser Funktion ist der API-Aufruf [`Optimize.onPropositionsUpdate`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#onpropositionsupdate) , der

   * ruft die Vorschläge für das aktuelle Profil basierend auf dem Entscheidungsbereich ab (den Sie in Journey Optimizer - Entscheidungsverwaltung) definiert haben,
   * ruft das Angebot aus dem Vorschlag ab,
   * entpackt den Inhalt des Angebots, damit er ordnungsgemäß in der App angezeigt werden kann, und
   * Triggers die Aktion `displayed()` des Angebots, das ein Ereignis an das Edge Network zurücksendet, das das Angebot informiert, angezeigt wird.

1. Fügen Sie in **[!DNL EdgeOffersView]** den folgenden Code zum Modifikator `.onFirstAppear` hinzu. Dieser Code stellt sicher, dass der Callback zur Aktualisierung der Angebote nur einmal registriert wird.

   ```swift
   // Invoke callback for offer updates
   Task {
       await self.onPropositionsUpdateOD(activityId: decision.activityId, placementId: decision.placementId, itemCount: decision.itemCount)
   }
   ```

1. Fügen Sie in **[!UICONTROL EdgeOffersView]** den folgenden Code zum Modifikator `.task` hinzu. Dieser Code aktualisiert die Angebote, wenn die Ansicht aktualisiert wird.

   ```swift
   // Clear and update offers
   await self.updatePropositionsOD(ecid: currentEcid, activityId: decision.activityId, placementId: decision.placementId, itemCount: decision.itemCount)
   ```



## Validieren mit der App

1. Erstellen Sie die App im Simulator oder auf einem physischen Gerät aus Xcode neu und führen Sie sie mit ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg) aus.

1. Navigieren Sie zur Registerkarte **[!DNL Personalisation]**.

1. Wählen Sie **[!DNL Edge Personalisation]** aus.

1. Scrollen Sie nach oben und Sie sehen zwei zufällige Angebote aus der Sammlung, die Sie in der Kachel **[!DNL DECISION LUMA - MOBILE APP DECISION]** definiert haben.

   <img src="assets/ajo-app-offers.png" width="300">

   Die Angebote sind zufällig, da Sie allen Angeboten die gleiche Priorität gegeben haben und der Rang für die Entscheidung auf der Priorität basiert.


## Validieren der Implementierung in Assurance

Validieren der Implementierung von Angeboten in Assurance:

1. Lesen Sie den Abschnitt [Setup instructions](assurance.md#connecting-to-a-session) , um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Wählen Sie **[!UICONTROL Konfigurieren]** in der linken Leiste und klicken Sie auf ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) neben **[!UICONTROL Überprüfen und Simulieren]** unter **[!UICONTROL ADOBE JOURNEY OPTIMIZER DECISIONING]**.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
1. Wählen Sie in der linken Leiste **[!UICONTROL Überprüfen und simulieren]** aus. Beide Datastream-Einstellungen werden validiert und das SDK-Setup in Ihrer Anwendung.
1. Wählen Sie in der oberen Leiste **[!UICONTROL Anforderungen]** aus. Sie sehen Ihre **[!UICONTROL Angebote]** -Anfragen.
   ![AJO Decisioning-Validierung](assets/assurance-decisioning-requests.png)

1. Auf den Registerkarten **[!UICONTROL Simulieren]** und **[!UICONTROL Ereignisliste]** finden Sie weitere Funktionen. Überprüfen Sie Ihre Einrichtung der Journey Optimizer-Entscheidungsverwaltung.

## Nächste Schritte

Sie sollten jetzt über alle Tools verfügen, um Ihrer Journey Optimizer - Implementierung der Entscheidungsverwaltung - mehr Funktionen hinzuzufügen. Beispiel:

* Anwenden verschiedener Parameter auf Ihre Angebote (z. B. Priorität, Begrenzung)
* Profilattribute in der App erfassen (siehe [Profil](profile.md)) und diese Profilattribute zum Erstellen von Zielgruppen verwenden. Verwenden Sie diese Zielgruppen dann als Teil der Eignungsregeln Ihrer Entscheidung.
* mehrere Entscheidungsbereiche kombinieren.

>[!SUCCESS]
>
>Sie haben die App für die Anzeige von Angeboten mithilfe der Journey Optimizer - Decisioning-Erweiterung für das Experience Platform Mobile SDK aktiviert.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu zukünftigen Inhalten haben möchten, teilen Sie diese in diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Durchführen von A/B-Tests](target.md)**
