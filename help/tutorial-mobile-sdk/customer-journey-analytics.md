---
title: Daten Ihrer mobilen App mit Customer Journey Analytics melden und analysieren
description: Erfahren Sie, wie Sie die Interaktionen mit Ihrer App mithilfe von Customer Journey Analytics melden und analysieren können.
solution: Data Collection,Experience Platform,Analytics
exl-id: c41b76eb-2ed7-4a82-80c1-b67476c464ad
source-git-commit: b61be86cfa55e597539c05404182af33e33aaac9
workflow-type: tm+mt
source-wordcount: '3282'
ht-degree: 2%

---

# Bericht und Analyse mithilfe von Customer Journey Analytics

Erfahren Sie, wie Sie Ihre Interaktionen mit mobilen Apps mit Customer Journey Analytics melden und analysieren können.

Die Ereignisdaten der Mobile App, die Sie in früheren Lektionen erfasst und an Platform Edge Network gesendet haben, werden an die in Ihrem Datastream konfigurierten Dienste weitergeleitet. Wenn Sie die Lektion [Daten an Experience Platform senden](platform.md) befolgt haben, werden diese Daten jetzt in einem Experience Platform-Datensatz gespeichert und stehen Customer Journey Analytics zur Verwendung für Berichte und Analysen zur Verfügung.

Im Gegensatz zu Adobe Analytics verwendet Customer Journey Analytics ** Daten aus Datensätzen, die in Experience Platform erstellt wurden. Daten werden nicht direkt mit dem Adobe Experience Platform Mobile SDK an Customer Journey Analytics gesendet, sondern an Datensätze. Verbindungen werden dann im Customer Journey Analytics konfiguriert, um die Datensätze auszuwählen, die Sie in Ihren Berichts- und Analyseprojekten verwenden werden.

Diese Lektion im Tutorial konzentriert sich auf die Berichterstellung und Analyse der Daten, die aus der Tutorial-App &quot;Luma&quot;erfasst wurden. Eine der einzigartigen Möglichkeiten von Customer Journey Analytics besteht darin, Daten aus verschiedenen Quellen (CRM, Point-of-Sale, Treueprogramm, Callcenter) und Kanälen (Web, mobil, offline) zu kombinieren, um tiefgründige Einblicke in die Journey zu erhalten. Diese Fähigkeit geht über den Rahmen dieser Lektion hinaus. Weitere Informationen finden Sie unter [Customer Journey Analytics - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) .


## Voraussetzungen

Ihr Unternehmen muss für Customer Journey Analytics freigeschaltet und über entsprechende Berechtigungen verfügen. Sie benötigen Administratorzugriff auf Customer Journey Analytics.


## Lernziele

In dieser Lektion werden Sie:

- Erstellen Sie eine Verbindung, um die Datensätze von Experience Platform zu definieren, die Sie im Customer Journey Analytics verwenden möchten.
- Erstellen Sie eine Datenansicht, um die Daten aus den Datensätzen für Ihre Berichterstellung und Analyse vorzubereiten.
- Erstellen Sie ein Projekt, um Berichte und Visualisierungen zu erstellen, damit Sie die Daten aus Ihrer mobilen App analysieren können.

Die Sequenz ist absichtlich. Verbindungen verwenden Datensätze, und Datenansichten verwenden Verbindungen.


## Verbindung erstellen

Eine Verbindung in Customer Journey Analytics definiert die Datensätze (und die Daten in diesen Datensätzen) von Experience Platform, die Sie für die Berichterstellung und Analyse verwenden möchten.

1. Navigieren Sie mithilfe des Menüs Apps ![Apps](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) oben rechts zur Customer Journey Analytics-Oberfläche.

1. Wählen Sie in der oberen Menüleiste **[!UICONTROL Verbindungen]** aus.

1. Stellen Sie sicher, dass Sie in der Benutzeroberfläche &quot;Verbindungen&quot;die Registerkarte **[!UICONTROL Liste]** auswählen. Es wird eine Liste der vorhandenen Verbindungen angezeigt.

1. Wählen Sie **[!UICONTROL Neue Verbindung erstellen]** aus.

1. Im Bildschirm **[!UICONTROL Verbindungen]** > **[!UICONTROL Verbindung ohne Titel]** unter **[!UICONTROL Verbindungseinstellungen]**

   1. Geben Sie einen **[!UICONTROL Verbindungsnamen]** ein, z. B. `Luma App - AEP Mobile SDK Tutorial Connection`.
   2. Geben Sie eine **[!UICONTROL Verbindungsbeschreibung]** ein, z. B. `Connection for the Luma app used in the AEP Mobile SDK tutorial`.

      In **[!UICONTROL Dateneinstellungen]**:

   3. Wählen Sie die Sandbox aus, die Sie zum Erfassen Ihrer App-Daten verwendet haben, z. B. **[!UICONTROL Mobile- und Web SDK-Kurse]**.
   4. Wählen Sie **[!UICONTROL weniger als 1 Million]** aus dem Feld **[!UICONTROL Durchschnittliche Anzahl der täglichen Ereignisse]** aus.

   5. Wählen Sie **[!UICONTROL Datensätze hinzufügen]** aus, um die Datensätze aus der Experience Platform auszuwählen, die Sie im Customer Journey Analytics verwenden möchten.

      ![CJA-Verbindungen 1](assets/cja-connections-1.png)

   6. Im Schritt **[!UICONTROL Datensätze hinzufügen]** des Assistenten **[!UICONTROL Datensatz auswählen]**,

      1. Wählen Sie die folgenden Datensätze aus:

         - **[!UICONTROL Luma Mobile App Event Datensatz]**: der Datensatz, den Sie im Rahmen des Abschnitts [Datensatz erstellen](platform.md#create-a-dataset) in der Experience Platform-Lektion erstellt haben.
         - **[!UICONTROL ODE DecisionEvents - *Sandbox name*] decisioning**
         - **[!UICONTROL AJO-Push-Tracking-Ereignisdatensätze]**

      1. Klicken Sie auf **[!UICONTROL Weiter]**.

         ![CJA-Verbindungen 2](assets/cja-connections-2.png)

   7. Im Schritt **[!UICONTROL Datensätze hinzufügen]** des Assistenten, **[!UICONTROL Datensatzeinstellungen]** müssen Sie die Details für jeden Ereignis-Datensatz definieren.
      1. Informationen zur korrekten Einrichtung finden Sie in den folgenden Tabellen:

         | Datensatz | Personen-ID<br/>besäß | Zeitstempel<br>Callstamp | Datenquellentyp - Fehler | Importieren aller neuen Daten mit | Alle vorhandenen Daten aufstocken, um alle vorhandenen Daten aufstocken |
         |---|---|---|---|---|---|
         | Ereignis-Datensatz für Luma Mobile App | identityMap | Zeitstempel | App-Daten | enable | enable |
         | ODE DecisionEvents - *Sandbox name* decisioning | identityMap | Zeitstempel | App-Daten | enable | enable |
         | Erlebnisereignisdatensatz beim AJO-Push-Tracking | identityMap | Zeitstempel | App-Daten | enable | enable |

      1. Wählen Sie **[!UICONTROL Datensätze hinzufügen]** aus.

         ![CJA-Verbindungen 3](assets/cja-connections-3.png)

1. Wählen Sie in der Tutorial-Verbindung &quot;**[!UICONTROL Verbindungen]**&quot;> &quot;**[!UICONTROL Luma App - AEP Mobile SDK&quot;]** die Option &quot;**[!UICONTROL Speichern]**&quot;, um Ihre Verbindung zu speichern.

   ![CJA-Verbindungen 4](assets/cja-connections-4.png)

Sie haben jetzt Ihre Verbindung definiert und Customer Journey Analytics fügt die Daten aus den Datensätzen zu seiner eigenen internen Datenbank hinzu. Diese Datenerfassung kann abhängig von der Datenmenge einige Zeit in Anspruch nehmen. Für Ihre Tutorial-App sollten Sie einige Stunden warten, bis die Daten auf dem Customer Journey Analytics angezeigt werden.

So zeigen Sie den Status Ihrer Verbindung an:

1. Wählen Sie **[!UICONTROL Verbindungen]** in der Hauptschnittstelle von Customer Journey Analytics aus.
1. Wählen Sie den Namen Ihrer Verbindung aus, z. B. **[!UICONTROL Luma App - AEP Mobile SDK Tutorial Connection]**.

In der Tutorial-Verbindung **[!UICONTROL Verbindungen]** > **[!UICONTROL Luma App - AEP Mobile SDK]** sehen Sie:

1. Informationen zu den hinzugefügten, übersprungenen und gelöschten Datensätzen. Stellen Sie sicher, dass Sie &quot;**[!UICONTROL Alle Datensätze]**&quot;auswählen und einen geeigneten Zeitraum auswählen, um Details zu Ihrer Verbindung anzuzeigen. Sie können ![Kalender](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Calendar_18_N.svg) verwenden, um ein Dialogfeld zur Auswahl des Zeitraums zu öffnen.
1. Informationen für einzelne Datensätze zu hinzugefügten Datensätzen, übersprungenen Datensätzen, gelöschten Datensätzen und mehr.

   ![CJA-Verbindungen 6](assets/cja-connections-6.png)


## Datenansicht erstellen

Nachdem die Datensätze aus den Datensätzen zum Customer Journey Analytics hinzugefügt wurden, können Sie eine Datenansicht erstellen, um zu definieren, über welche Komponenten der Daten Sie Berichte erstellen möchten.

Eine Datenansicht ist ein für Customer Journey Analytics spezifischer Container, mit dem Sie bestimmen können, wie Daten aus einer Verbindung interpretiert werden. Sie können Standard- und Schemafelder aus allen Datensätzen konfigurieren, die Sie in Ihrer Verbindung als Komponenten (Dimensionen, Metriken) in Analysis Workspace definiert haben.

Eine Datenansicht in Customer Journey Analytics bietet enorme Flexibilität bei der richtigen Einrichtung und Definition der Daten Ihrer Verbindung. In diesem Tutorial verwenden Sie nur die für Ihre Berichterstellung und Analyse erforderlichen Funktionen. Weitere Informationen finden Sie unter [Datenansichten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views) .


So erstellen Sie Ihre Datenansicht:

1. Navigieren Sie mithilfe des Menüs Apps ![Apps](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) oben rechts zur Customer Journey Analytics-Oberfläche.

1. Wählen Sie in der oberen Menüleiste **[!UICONTROL Datenansichten]** aus.
1. Wählen Sie **[!UICONTROL Neue Datenansicht erstellen]** aus.
1. Stellen Sie in **[!UICONTROL Datenansichten >]** sicher, dass die Registerkarte **[!UICONTROL Konfigurieren]** ausgewählt ist.

   1. Wählen Sie Ihre Verbindung aus der Dropdown-Liste &quot;Verbindung einstellen&quot;aus, z. B. **[!UICONTROL Luma App - AEP Mobile SDK Tutorial Connection]**.
   1. Geben Sie einen Namen für Ihre Datenansicht ein, z. B.: `Luma App - AEP Mobile SDK Tutorial Data view`.
   1. Wählen Sie **[!UICONTROL Speichern und fortfahren]**.

      ![CJA-Datenansicht 1](assets/cja-dataview-1.png)

1. Auf der Registerkarte **[!UICONTROL Komponenten]** der Ansicht **[!UICONTROL Luma App - AEP Mobile SDK Tutorial Data (Datenansicht des mobilen SDK)]** können Sie die Metriken und Dimensionen definieren, die Sie für die Berichterstellung für Ihre mobile App verwenden möchten. Standardmäßig sind mehrere Standardmetriken und -dimensionen (gemeinsam auf Komponenten verwiesen) bereits für Ihre Datenansicht konfiguriert. Ihre Datenansicht erfordert jedoch mehr Komponenten. <br/>So fügen Sie ein Schemafeld aus Ihrem zuvor definierten Schema oder nativen Schemata hinzu (siehe [Schema erstellen](create-schema.md) -Lektion), als Komponente (Dimension oder Metrik):

   1. Suchen Sie das Schemafeld:

      - Suchen Sie mithilfe des Suchfelds ![Suche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) ***[!UICONTROL Suchschemafelder]*** nach der Komponente. Beispiel: `productListAdd` oder

        ![CJA-Datenansicht 2a](assets/cja-dataview-2a.png)

      - bis zum Schemafeld innerhalb von ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **[!UICONTROL Ereignis-Datensätzen]** ![Chevron](https://spectrum.adobe.com/static/icons/ui_18/ChevronSize100.svg) hinunter. <br/>Beispiel: ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **[!UICONTROL Ereignis-Datensätze]** ![Chevron](https://spectrum.adobe.com/static/icons/ui_18/ChevronSize100.svg) ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **[!UICONTROL commerce]** ![Chevron](https://spectrum.adobe.com/static/icons/ui_18/ChevronSize100.svg) ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **[!UICONTROL productListAdds]** ![Chevron](https://spectrum.adobe.com/static/icons/ui_18/ChevronSize100.svg)

        ![CJA-Datenansicht 2a](assets/cja-dataview-2b.png)

   1. Ziehen Sie das spezifische Schemafeld aus dem Bereich Schemafelder und legen Sie es auf der Liste **[!UICONTROL METRIKEN]** oder **[!UICONTROL DIMENSIONEN]** im Bereich [!UICONTROL Eingeschlossene Komponenten] ab.

      ![CJA-Datenansicht 2a](assets/cja-dataview-3.png)

   1. Sie können die Einstellungen einer Komponente konfigurieren. Wählen Sie die Komponente aus und konfigurieren Sie die Einstellungen im rechten Bereich. <br/>Sie können beispielsweise **[!UICONTROL commerce.productListAdds]** mit dem Feld **[!UICONTROL KOMPONENTENEINSTELLUNGEN]** > **[!UICONTROL Komponentenname]** im rechten Bereich in `Product Add To Lists` umbenennen.

      ![CJA-Datenansicht 3b](assets/cja-dataview-3b.png)

      Oder konfigurieren Sie **[!UICONTROL AUSSCHLUSSWERTE EINSCHLIESSEN]**.

      ![Einstellungen der CJA-Datenansichtskomponente](assets/cja-dataview-component-settings.png)

   1. Nachdem Sie nun wissen, wie Sie Ihrer Datenansicht Felder hinzufügen und die resultierende Komponente konfigurieren können, verwenden Sie die unten stehenden Tabellen für eine Liste von Schemafeldern, um sie als Metriken oder Dimensionen hinzuzufügen. Verwenden Sie den Spaltenwert **Schema Path** aus der Tabelle unten, um nach dem spezifischen Schemafeld zu suchen oder es zu ihm zu durchlaufen. Nachdem Metriken und Dimensionen hinzugefügt wurden, überprüfen Sie den Spaltenwert **Komponenteneinstellungen** in der Tabelle, ob bestimmte Einstellungen für eine Komponente erforderlich sind, z. B. ihr **[!UICONTROL Komponentenname]** oder die Definition von **[!UICONTROL AUSSCHLUSSWERTE EINSCHLIESSEN]**.

      **METRIKEN**

      | Komponentenname | Datensatz | Schema-Datentyp | Schema Path | Komponenteneinstellungen |
      |---|---|---|---|---|
      | Schließen | AJO Push Tracking Experience Event Datensatz, Datensatz zu Luma Mobile App-Ereignissen | Ganzzahl | _experience.decisioning.<br/>propositionEventType.dismiss | Komponentenname: `Dismiss` |
      | Abonnement beenden | AJO Push Tracking Experience Event Datensatz, Datensatz zu Luma Mobile App-Ereignissen | Ganzzahl | _experience.decisioning.<br/>propositionEventType.unsubscribe | Komponentenname: `Unsubscribe` |
      | Auslöser | AJO Push Tracking Experience Event Datensatz, Datensatz zu Luma Mobile App-Ereignissen | Ganzzahl | _experience.decisioning.<br/>propositionEventType.Trigger | Komponentenname: `Trigger` |
      | Anzeige | AJO Push Tracking Experience Event Datensatz, Datensatz zu Luma Mobile App-Ereignissen | Ganzzahl | _experience.decisioning.<br/>propositionEventType.display | Komponentenname: `Display` |
      | Senden | AJO Push Tracking Experience Event Datensatz, Datensatz zu Luma Mobile App-Ereignissen | Ganzzahl | _experience.decisioning.<br/>propositionEventType.send | Komponentenname: `Send` |
      | Interact | AJO Push Tracking Experience Event Datensatz, Datensatz zu Luma Mobile App-Ereignissen | Ganzzahl | _experience.decisioning.<br/>propositionEventType.interact | Komponentenname: `Interact` |
      | Standortereignisse | AJO Push Tracking Experience Event Datensatz, Luma Mobile App Event Datensatz, ODE DecisionEvents - mobile-and-web-sdk-kurse Decisioning | Zeichenfolge | Ereignistyp | Komponentenname: `Location Events`<br/><br/>![Einschließen/Ausschließen](assets/cja-dataview-include-exclude.png) |
      | Produktansichten | Ereignis-Datensatz für Luma Mobile App | Double | commerce.productViews.value | Komponentenname: `Product Views` |
      | Produkt zu Listen hinzufügen | Ereignis-Datensatz für Luma Mobile App | Double | commerce.productListAdds.value | Komponentenname: `Product Add To Lists` |
      | Käufe | Ereignis-Datensatz für Luma Mobile App | Double | commerce.purchases.value | Komponentenname: `Purchases` |
      | Für später speichern | Ereignis-Datensatz für Luma Mobile App | Double | commerce.saveForLaters.value | Komponentenname: `Save For Laters` |
      | App-Interaktionen | Ereignis-Datensatz für Luma Mobile App | Double | _techmarketingdemos.appInformation.<br/>appInteraction.appAction.value | Komponentenname: `App Interactions` |
      | Bildschirmansichten | Ereignis-Datensatz für Luma Mobile App | Double | _techmarketingdemos.appInformation.<br/>appStateDetails.screenView.value | Komponentenname: `Screen Views` |

      {style="table-layout:auto"}

      >[!NOTE]
      >
      >Beachten Sie, dass das Schemafeld für die Metrik &quot;Standortereignisse&quot;**[!UICONTROL AUSSCHLUSSWERTE EINSCHLIESSEN]** verwendet, um Ereignistypen zu zählen, die `location` enthalten.


      Ihre Datenansichtskonfiguration für **[!UICONTROL METRICS]** sollte mit der folgenden übereinstimmen, nachdem Sie alle Schemafelder aus der obigen Tabelle als Metrikkomponente hinzugefügt haben:

      ![CJA-Datenansicht 4](assets/cja-dataview-4.png)

      **DIMENSIONEN**

      | Komponentenname | Datensatz | Schema-Datentyp | Schema Path | Komponenteneinstellungen |
      |---|---|---|---|---|
      | Stadt | AJO Push Tracking Experience Event Datensatz, Datensatz zu Luma Mobile App-Ereignissen | Zeichenfolge | placeContext.geo.city | Komponentenname: `City` |
      | Ereignistypen | AJO Push Tracking Experience Event Datensatz, Luma Mobile App Event Datensatz, ODE DecisionEvents - mobile-and-web-sdk-kurse Decisioning | Zeichenfolge | eventType | Komponentenname: `Event Types` |
      | Name der Entscheidungsoption | AJO Push Tracking Experience Event Datensatz, Luma Mobile App Event Datensatz, ODE DecisionEvents - mobile-and-web-sdk-kurse Decisioning | Zeichenfolge | _experience.decisioning.<br/>propositions.items.name | Komponentenname: `Decision Option Name` |
      | App-Interaktionsname | Ereignis-Datensatz für Luma Mobile App | Zeichenfolge | _techmarketingdemos.appInformation.<br/>appInteraction.name | Komponentenname: `App Interaction Name` |
      | Bildschirmname | Ereignis-Datensatz für Luma Mobile App | Zeichenfolge | _techmarketingdemos.appInformation.<br/>appStateDetails.screenName | Komponentenname: `Screen Name` |
      | Aktivitätsname | ODE DecisioningEvents - mobile-and-web-sdk-kurse decisioning | Zeichenfolge | _experience.decisioning.<br/>propositionDetails.activity.name | Komponentenname: `Activity Name` |
      | Angebotsname | ODE DecisioningEvents - mobile-and-web-sdk-kurse decisioning | Zeichenfolge | _experience.decisioning.<br/>propositionDetails.selections.name | Komponentenname: `Offer Name` |

      {style="table-layout:auto"}

      Ihre Datenansichtskonfiguration für **[!UICONTROL DIMENSIONEN]** sollte mit der folgenden übereinstimmen, nachdem Sie alle Schemafelder aus der obigen Tabelle als Dimensionskomponente hinzugefügt haben:

      ![CJA-Datenansicht 4](assets/cja-dataview-5.png)

   1. Wählen Sie **[!UICONTROL Speichern und fortfahren]**.

1. Auf der Registerkarte **[!UICONTROL Einstellungen]** in der Ansicht **[!UICONTROL Luma App - AEP Mobile SDK Tutorial Data view]** können Sie Filter und Sitzungseinstellungen konfigurieren. Für dieses Tutorial ist keine zusätzliche Konfiguration erforderlich.

   - Wählen Sie **[!UICONTROL Speichern und beenden]** aus.

Sie haben Ihre Datenansicht definiert und alles ist vorhanden, um Ihre Berichte und Visualisierungen zu erstellen.

## Projekt erstellen

Workspace-Projekte werden in Customer Journey Analytics zum Erstellen von Berichten und Visualisierungen verwendet. Es gibt viele Möglichkeiten, umfassende Berichte und ansprechende Visualisierungen zu erstellen. Dies fällt jedoch nicht in den Rahmen dieses Tutorials. Weitere Informationen finden Sie unter [Workspace-Übersicht](https://experienceleague.adobe.com/en/docs/customer-journey-analytics-learn/tutorials/analysis-workspace/workspace-projects/analysis-workspace-overview) und [Erstellen eines neuen Projekts](https://experienceleague.adobe.com/en/docs/customer-journey-analytics-learn/tutorials/analysis-workspace/workspace-projects/build-a-new-project) .

In diesem Abschnitt der Lektion erstellen Sie ein Projekt, das Berichte und Visualisierungen zu folgenden Themen anzeigt:

- App-Nutzung: Verwendung der Informationen auf Bildschirm- und App-Interaktionen.
- Commerce: Durch die Verwendung der Commerce-Ereignisse, wie z. B. der Produktansicht, werden zum Warenkorb und zum Kauf hinzugefügt.
- Angebote: Verwendung der in der App angezeigten Angebote.
- Besuche speichern: Verwendung der (simulierten) Geofence-Ereignisse aus der App.

So erstellen Sie Ihr Projekt:

1. Navigieren Sie mithilfe des Menüs Apps ![Apps](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) oben rechts zur Customer Journey Analytics-Oberfläche.

1. Wählen Sie in der oberen Menüleiste **[!UICONTROL Workspace]** aus.

1. Wählen Sie **[!UICONTROL Projekt erstellen]** aus.

   1. Wählen Sie **[!UICONTROL Leeres Workspace-Projekt]** aus dem Popup-Dialogfeld.

   1. Wählen Sie **[!UICONTROL Erstellen]** aus.

      ![CJA-Projekte - 1](assets/cja-projects-1.png)

1. Sie erhalten die Benutzeroberfläche **[!UICONTROL Neues Projekt]** . Auf dieser Oberfläche erstellen Sie Ihre Berichte und Visualisierungen.

1. Wählen Sie den Namen des Projekts aus (**[!UICONTROL Neues Projekt]**) und geben Sie Ihren eigenen Namen für das Projekt an. Beispiel: `Luma App - AEP Mobile SDK Tutorial Project`.
   ![CJA-Projekt 2](assets/cja-projects-2.png)

1. Um das Projekt zu speichern, wählen Sie **[!UICONTROL Projekt]** > **[!UICONTROL Speichern]** aus.
   ![CJA-Projekt 3](assets/cja-projects-3.png)

1. Ignorieren Sie im Dialogfeld **[!UICONTROL Speichern]** alle anderen Felder und wählen Sie **[!UICONTROL Speichern]** aus.
   ![CJA-Projekt 4](assets/cja-projects-4.png)


>[!IMPORTANT]
>
>   Vergessen Sie nicht, Ihr Projekt regelmäßig zu speichern, da ansonsten Ihre Änderungen verloren gehen. Sie können Ihr Projekt schnell mit **[!UICONTROL Strg + S]** (Windows) oder **[!UICONTROL ⌘ (cmd) + s]** (macOS) speichern.

Sie haben jetzt Ihr Projekt eingerichtet. Standardmäßig wird eine Freiformtabelle bereitgestellt. Bevor Sie Komponenten hinzufügen, stellen Sie sicher, dass Ihr Freiform-Bedienfeld die richtige Datenansicht und den richtigen Zeitraum verwendet.

1. Wählen Sie Ihre Datenansicht aus der Dropdownliste aus. Beispiel: **[!UICONTROL Luma App - AEP Mobile SDK Tutorial Data view]**. Wenn Ihre Datenansicht nicht in der Liste angezeigt werden kann, wählen Sie unten in der Dropdown-Liste die Option **[!UICONTROL Alle anzeigen]** aus.
   ![CJA-Projekt 5](assets/cja-projects-5.png)

1. Um den entsprechenden Zeitraum für das Bedienfeld zu definieren, wählen Sie die Standardvorgabe **[!UICONTROL Diesen Monat]** aus, geben Sie ein benutzerdefiniertes Start- und Enddatum ein oder verwenden Sie eine **[!UICONTROL Vorgabe]** (z. B. **[!UICONTROL Letzte 6 volle Monate]**) und wählen Sie **[!UICONTROL Anwenden]**.
   ![CJA-Projekt 6](assets/cja-projects-6.png)


### App-Nutzung

Jetzt können Sie Berichte zur Verwendung der App erstellen. Sie haben den erforderlichen Code in der App hinzugefügt, um App-Interaktionen zu registrieren und herauszufinden, welche Bildschirme in der App verwendet werden (siehe die Lektion [Ereignisse verfolgen](events.md) ), und Sie möchten jetzt Berichte zu diesen Daten erstellen.

#### Bildschirmnamen

So melden Sie die in der App angezeigten Bildschirme:

1. Benennen Sie Ihr Bedienfeld **[!UICONTROL Freiform]** in `App Usage` um.

1. Benennen Sie Ihre **[!UICONTROL Freiformtabelle]** in `Screen Names` um.

1. Wählen Sie **[!UICONTROL Alle anzeigen]** unter der Liste **[!UICONTROL METRIKEN]** aus.

1. Ziehen Sie die Komponente **[!UICONTROL Bildschirmansichten]** per Drag-and-Drop auf [!UICONTROL _Legen Sie hier eine Metrik **4} (oder eine beliebige andere Komponente_)] ab.**
   ![CJA-Projekte 7](assets/cja-projects-7.png)
In Ihrer Freiformtabelle werden nun für jeden Tag des ausgewählten Zeitraums Bildschirmansichten angezeigt. Sie möchten jedoch die Anzahl der Bildschirmansichten für jeden der in der App verwendeten Bildschirme anzeigen.

1. Um die Komponentenliste **[!UICONTROL DIMENSIONEN]** anzuzeigen, wählen Sie ![Cross](https://spectrum.adobe.com/static/icons/ui_18/CrossSize100.svg) aus, um den Filter ![](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Event_18_N.svg) **[!UICONTROL Metriken]** aus der Komponentenleiste zu entfernen.
   ![CJA-Projekt 8](assets/cja-projects-8.png)

1. Wählen Sie **[!UICONTROL Alle anzeigen]** unter der Liste **[!UICONTROL DIMENSIONEN]** aus.

1. Ziehen Sie die Komponente **[!UICONTROL Bildschirmname]** in die Kopfzeile **[!UICONTROL Tag]** und legen Sie sie ab. Der Vorgang zeigt ![Switch](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Switch_18_N.svg) **[!UICONTROL Replace]** an, um den Austausch der Dimension anzuzeigen.
   ![CJA-Projekte 9](assets/cja-projects-9.png)

Ihre erste Freiformtabelle in Ihrem Bericht ist abgeschlossen.

![CJA-Projekte 10](assets/cja-projects-10.png)

>[!NOTE]
>
>Speichern Sie das Projekt, bevor Sie fortfahren.


#### App-Interaktionen

Als Nächstes erstellen Sie eine Freiformtabelle, in der die Interaktion der Benutzer mit der App beschrieben wird.

1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) und aus dem Popup-Fenster ![Freiformtabelle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Table_18_N.svg) aus, um eine neue Freiformtabelle hinzuzufügen.
   ![CJA-Projekte 11](assets/cja-projects-11.png)

1. Benennen Sie die Freiformtabelle (2)]**in `App Interactions` um.**[!UICONTROL 

1. Ziehen Sie die Metrik **[!UICONTROL App-Interaktionen]** per Drag-and-Drop auf [!UICONTROL _Legen Sie hier eine **Metrik**ab (oder eine beliebige andere Komponente_)].

1. Ziehen Sie die Dimension **[!UICONTROL App-Interaktionsname]** in die Kopfzeile **[!UICONTROL Tag]**, um diese Dimension zu ersetzen.

Ihr zweiter Bericht ist jetzt fertig und zeigt App-Interaktionen an.
![CJA-Projekte 12](assets/cja-projects-12.png)

Die Informationen sind hauptsächlich deshalb beschränkt, weil Sie `MobileSDK.shared.sendAppInteractionEvent(actionName: "<actionName>")` -API-Aufrufe nur auf dem Anmeldebildschirm implementiert haben. Wenn Sie diesen API-Aufruf in mehr Bildschirmen Ihrer App hinzufügen, wird dieser Bericht informativer.

>[!NOTE]
>
>Speichern Sie das Projekt, bevor Sie fortfahren.


### Commerce

Sie möchten nun in einem separaten Bedienfeld Berichte zu Commerce-Ereignissen erstellen, die in der App aufgetreten sind.

#### Commerce-Ereignisse

1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) außerhalb des aktuellen Bereichs [!UICONTROL App-Nutzung] aus, um einen neuen Bereich zu erstellen.
   ![CJA-Projekte 13](assets/cja-projects-13.png)

1. Stellen Sie sicher, dass Sie den entsprechenden Zeitraum auswählen.

1. Wählen Sie ![Freiformtabelle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Table_18_N.svg) **[!UICONTROL Freiformtabelle]** aus, um eine neue Freiformtabelle zu erstellen.
   ![CJA-Projekte 14](assets/cja-projects-14.png)

1. Benennen Sie **[!UICONTROL Bedienfeld]** in `Commerce` um.

1. Benennen Sie **[!UICONTROL Freiformtabelle]** in `Commerce Events` um.

1. Ziehen Sie die Metrik **[!UICONTROL Produktansichten]** per Drag-and-Drop auf [!UICONTROL _Legen Sie hier eine **Metrik**(oder eine andere Komponente_)] ab.

1. Ziehen Sie die Metrik **[!UICONTROL Produkt zu Listen hinzufügen]** rechts von der Spalte **[!UICONTROL Produktansichten]**, um diese Spalte in die Freiformtabelle einzufügen. Stellen Sie sicher, dass beim Einfügen der Spalte **[!UICONTROL + Hinzufügen]** (blau) angezeigt wird.
   ![CJA-Projekte 15](assets/cja-projects-15.png)

1. Wiederholen Sie den vorherigen Schritt, um die Metrik **[!UICONTROL Für Letzte speichern]** und die Metrik **[!UICONTROL Käufe]** zur Freiformtabelle hinzuzufügen.

1. Ziehen Sie die Dimension **[!UICONTROL Monat]** auf die Dimension **[!UICONTROL Tag]**, um die Berichterstellung von täglich in monatlich zu ändern.

Ihr Commerce-Ereignisbericht ist abgeschlossen.

![CJA-Projekte 16](assets/cja-projects-16.png)

>[!NOTE]
>
>Speichern Sie das Projekt, bevor Sie fortfahren.

#### Fallout

Als Nächstes erstellen Sie eine Fallout-Visualisierung für den Commerce-Trichter, die anzeigt, wie viele Benutzer, die Produkte angesehen haben, diese Produkte zu ihrem Warenkorb hinzugefügt haben und wie viele Benutzer diese Produkte zu einem späteren Zeitpunkt gespeichert haben.

1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) im Bedienfeld **[!UICONTROL Commerce]** aus und wählen Sie im Popup die Option ![Fallout](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ConversionFunnel_18_N.svg) aus (die die Fallout-Visualisierung darstellt).

1. Wählen Sie **[!UICONTROL Produktansichten]** aus der Dropdownliste [!UICONTROL *Touchpoint hinzufügen*] aus.
   ![CJA-Projekte 18](assets/cja-projects-18.png)
Alternativ können Sie die Dimension **[!UICONTROL Produktansicht]** unter die Dimension **[!UICONTROL Alle Personen]** ziehen und in die Visualisierung **[!UICONTROL Trichteranalyse]** ziehen.

1. Wiederholen Sie den obigen Schritt für die Dimensionen **[!UICONTROL Produkt zu Listen hinzufügen]** und **[!UICONTROL Einkäufe]** .

Ihr Fallout-Visualisierungsbericht ist abgeschlossen.
![CJA-Projekte 19](assets/cja-projects-19.png)

>[!NOTE]
>
>Speichern Sie das Projekt, bevor Sie fortfahren.


### Angebote

Sie möchten Berichte dazu erstellen, wie viele Angebote und welche Angebote den Benutzern Ihrer App angezeigt werden.

#### Monatsübersicht

1. Wählen Sie &quot;![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg)&quot;außerhalb des aktuellen Commerce-Bedienfelds aus, um einen neuen Bereich zu erstellen.

1. Benennen Sie das **[!UICONTROL Bedienfeld]** in `Offers` um.

1. Stellen Sie sicher, dass Sie den entsprechenden Zeitraum auswählen.

1. Wählen Sie ![Freiformtabelle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Table_18_N.svg) Freiformtabelle aus, um eine neue Freiformtabelle zu erstellen.

1. Benennen Sie die **[!UICONTROL Freiformtabelle]** in `Monthly Overview` um.

1. Ziehen Sie die Metrik **[!UICONTROL Anzeigen]** per Drag-and-Drop auf [!UICONTROL _Legen Sie hier eine **Metrik**(oder eine beliebige andere Komponente_)] ab.

1. Ziehen Sie die Dimension **[!UICONTROL Monat]** in die Spalte **[!UICONTROL Tag]**, um sie zu ersetzen.

Ihre monatliche Angebotsübersicht ist abgeschlossen.

![CJA-Projekte 20](assets/cja-projects-20.png)

>[!NOTE]
>
>Speichern Sie das Projekt, bevor Sie fortfahren.


#### Angebote für Personen

Sie möchten auch einen Bericht erstellen, der anzeigt, welche Angebote in welchen Zahlen den Benutzern der App angezeigt wurden.

1. Wählen Sie im Bedienfeld **[!UICONTROL Angebote]** die Option ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) und im Popup die Option ![Freiformtabelle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Table_18_N.svg)aus, um eine neue Freiformtabelle hinzuzufügen.

1. Benennen Sie die Freiformtabelle (2)]**in `People` um.**[!UICONTROL 

1. Ziehen Sie die Metrik **[!UICONTROL Personen]** per Drag-and-Drop auf [!UICONTROL _Legen Sie hier eine **Metrik**(oder eine beliebige andere Komponente_)] ab.

1. Ziehen Sie den **[!UICONTROL Aktivitätsnamen]** in die Spalte **[!UICONTROL Tag]**, um die Dimension zu ersetzen.

1. Klicken Sie mit der rechten Maustaste auf die Zeile und wählen Sie mindestens eine der Angebotsentscheidungen aus, die Sie in der Lektion [Angebote mit Entscheidungsverwaltung erstellen und anzeigen](journey-optimizer-offers.md) definiert haben. Beispiel: **[!UICONTROL Luma - App-Entscheidung]**.

1. Wählen Sie im Kontextmenü **[!UICONTROL Aufschlüsselung]** > **[!UICONTROL Dimensionen]** > **[!UICONTROL Angebotsname]** aus. Durch diese Auswahl wird die Dimension &quot;Aktivitätsname&quot;in Angebotsnamen unterteilt.
   ![CJA-Projekte 20b](assets/cja-projects-20b.png)

Der Bericht Angebote für Personen ist abgeschlossen.

![CJA-Projekte 21](assets/cja-projects-21.png)

>[!NOTE]
>
>Speichern Sie das Projekt, bevor Sie fortfahren.


### Store-Besuche

Schließlich möchten Sie Berichte zu Store-Besuchen erstellen.

1. Wählen Sie &quot;![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg)&quot;außerhalb des aktuellen Bedienfelds Angebote aus, um einen neuen Bereich zu erstellen.

1. Benennen Sie das **[!UICONTROL Bedienfeld]** in `Store Visits` um.

1. Stellen Sie sicher, dass Sie den entsprechenden Zeitraum auswählen.

1. Wählen Sie ![Freiformtabelle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Table_18_N.svg) Freiformtabelle aus, um eine neue Freiformtabelle zu erstellen.

1. Benennen Sie **[!UICONTROL Freiformtabelle]** in `Store Entries / Exits Across Cities` um.

1. Ziehen Sie die Metrik **[!UICONTROL Standortereignisse]** per Drag-and-Drop auf [!UICONTROL _Legen Sie hier eine **Metrik**(oder eine beliebige andere Komponente_)] ab. Der Bericht zeigt nun einen täglichen Überblick über alle Standortereignisse, die in der App aufgetreten sind. Denken Sie daran, wie Sie diese Dimension im Rahmen Ihrer [Datenansicht](#create-a-data-view) speziell konfiguriert haben.

1. Ziehen Sie die Dimension **[!UICONTROL Stadt]** in die Spaltenüberschrift **[!UICONTROL Tag]**, um die Dimension zu ersetzen. Der Bericht zeigt nun die Städte für die Standortereignisse an.

1. Um Geolocation-Ereignisse ohne zugehörige Städte zu entfernen, wählen Sie ![Filter](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Filter_18_N.svg) und deaktivieren Sie im Popup **[!UICONTROL Suche]** die Option **[!UICONTROL Kein Wert einschließen]** und wählen Sie dann **[!UICONTROL Anwenden]** aus.

   ![CJA-Projekte 22](assets/cja-projects-22.png)

   Dadurch wird die Zeile &quot;**[!UICONTROL Kein Wert]**&quot; aus dem Bericht entfernt.

1. Wählen Sie alle Zeilen in der Tabelle aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie im Kontextmenü Aufschlüsselung > Dimension > Ereignistypen aus.

Ihre Berichte zu Store-Besuchen sind abgeschlossen. Sie verfügen nun über einen Bericht, der zeigt, dass Benutzer sich in und aus der Nähe Ihrer Speicherorte befinden (wie Sie diese Orte in der Lektion [Orte](places.md) definiert haben).

![CJA-Projekt 23](assets/cja-projects-23.png)

Beachten Sie, dass Sie Beacons verwenden können, wenn Sie wirklich über Personen berichten möchten, die Ihren Store physisch besuchen. Aber hoffentlich haben Sie das Konzept der Berichterstattung über Geolocation-Daten erfasst.

## Nächste Schritte

Sie sollten jetzt über grundlegende Kenntnisse verfügen, wie Sie Berichte und Visualisierungen über die Nutzung Ihrer App, Interaktionen und mehr mithilfe von Customer Journey Analytics erstellen können.

>[!SUCCESS]
>
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu zukünftigen Inhalten haben möchten, teilen Sie diese in diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Abschluss und nächste Schritte](conclusion.md)**
