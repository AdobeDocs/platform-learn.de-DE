---
title: Durchführen von A/B-Tests mit Target
description: Erfahren Sie, wie Sie mit dem Platform Mobile SDK und Adobe Target einen Target-A/B-Test in Ihrer mobilen App verwenden.
solution: Data Collection,Target
feature-set: Target
feature: A/B Tests
hide: true
exl-id: 87546baa-2d8a-4cce-b531-bec3782d2e90
source-git-commit: 4a12f8261cf1fb071bc70b6a04c34f6c16bcce64
workflow-type: tm+mt
source-wordcount: '1911'
ht-degree: 3%

---

# Optimieren und Personalisieren mit Adobe Target

Erfahren Sie, wie Sie die Erlebnisse in Ihren mobilen Apps mit dem Platform Mobile SDK und Adobe Target optimieren und personalisieren können.

Target bietet alles, was Sie an die Erlebnisse Ihrer Kunden anpassen und personalisieren müssen. Mit Target können Sie den Umsatz Ihrer Web- und mobilen Sites, Apps, sozialen Medien und anderer digitaler Kanäle maximieren. Target kann A/B-Tests durchführen, Multivarianz-Tests durchführen, Produkte und Inhalte empfehlen, Inhalte auf Zielgruppen ausrichten, Inhalte mit KI automatisch personalisieren und vieles mehr. Der Schwerpunkt dieser Lektion liegt auf der A/B-Test-Funktionalität von Target. Siehe [A/B-Test - Überblick](https://experienceleague.adobe.com/docs/target/using/activities/abtest/test-ab.html?lang=en) für weitere Informationen.

![Architektur](assets/architecture-at.png)

Bevor Sie A/B-Tests mit Target durchführen können, müssen Sie sicherstellen, dass die richtigen Konfigurationen und Integrationen vorhanden sind.

>[!NOTE]
>
>Diese Lektion ist optional und gilt nur für Adobe Target-Benutzer, die A/B-Tests durchführen möchten.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.
* Zugriff auf Adobe Target mit Berechtigungen, ordnungsgemäß konfigurierten Rollen, Arbeitsbereichen und Eigenschaften, wie beschrieben [here](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/property-channel.html?lang=de).


## Lernziele

In dieser Lektion werden Sie:

* Aktualisieren Sie Ihren Datastream für die Target-Integration.
* Aktualisieren Sie Ihre Tag-Eigenschaft mit der Journey Optimizer - Decisioning-Erweiterung.
* Aktualisieren Sie Ihr Schema, um Projektereignisse zu erfassen.
* Validieren Sie die Einrichtung in &quot;Assurance&quot;.
* Erstellen Sie einen einfachen A/B-Test in Target.
* Aktualisieren Sie Ihre App, um die Optimizer-Erweiterung zu registrieren.
* Implementieren Sie den A/B-Test in Ihre App.
* Validieren Sie die Implementierung in Assurance.


## Einrichten

>[!TIP]
>
>Wenn Sie Ihre App bereits als Teil der [Journey Optimizer-Angebote](journey-optimizer-offers.md) -Lektion verwenden, haben Sie möglicherweise bereits einige der Schritte in diesem Einrichtungsabschnitt ausgeführt.

### Aktualisierung der Konfiguration des Datenspeichers

#### Adobe Target

Um sicherzustellen, dass Daten, die von Ihrer mobilen App an das Experience Platform Edge Network gesendet werden, an Adobe Target weitergeleitet werden, müssen Sie Ihre Datenspeicherkonfiguration aktualisieren.

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche die Option **[!UICONTROL Datenspeicher]** und wählen Sie Ihren Datastream aus, z. B. **[!DNL Luma Mobile App]**.
1. Auswählen **[!UICONTROL Dienst hinzufügen]** und wählen **[!UICONTROL Adobe Target]** aus dem **[!UICONTROL Dienst]** Liste.
1. Wenn Sie Target Premium-Kunde sind und Eigenschafts-Token verwenden möchten, geben Sie die **[!UICONTROL Eigenschafts-Token]** -Wert, den Sie für diese Integration verwenden möchten. Target Standard-Benutzer können diesen Schritt überspringen.

   Sie finden Ihre Eigenschaften in der Target-Benutzeroberfläche in **[!UICONTROL Administration]** > **[!UICONTROL Eigenschaften]**. Auswählen ![Code](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) , um das Eigenschafts-Token für die Eigenschaft anzuzeigen, die Sie verwenden möchten. Das Eigenschafts-Token hat ein Format wie `"at_property": "xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx"`; Sie dürfen nur den Wert eingeben `xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx`.

   Optional können Sie eine Target-Umgebungs-ID angeben. Target verwendet Umgebungen, um Ihre Sites und Umgebungen vor der Produktion zu organisieren und so eine einfache Verwaltung und separate Berichterstellung zu ermöglichen. Zu den vordefinierten Umgebungen gehören Produktion, Staging und Entwicklung. Siehe [Umgebungen](https://experienceleague.adobe.com/docs/target/using/administer/environments.html?lang=en) und [Target-Umgebungs-ID](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html?lang=en#target-environment-id) für weitere Informationen.

   Optional können Sie einen Target-Drittanbieter-ID-Namespace angeben, um die Profilsynchronisierung für einen Identitäts-Namespace zu unterstützen (z. B. CRM-ID). Siehe [Namespace der Target-Drittanbieter-ID](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html?lang=en#target-third-party-id-namespace) für weitere Informationen.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Target zum Datenspeicher hinzufügen](assets/edge-datastream-target.png)


#### Adobe Journey Optimizer

Um sicherzustellen, dass Daten, die von Ihrer mobilen App an das Edge-Netzwerk gesendet werden, an Journey Optimizer weitergeleitet werden - Entscheidungsverwaltung, aktualisieren Sie Ihre Datenspeicherkonfiguration.

1. Wählen Sie in der Datenerfassungs-Benutzeroberfläche die Option **[!UICONTROL Datenspeicher]** und wählen Sie Ihren Datastream aus, z. B. **[!DNL Luma Mobile App]**.
1. Auswählen ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) für **[!UICONTROL Experience Platform]** und wählen ![Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Bearbeiten]** aus dem Kontextmenü aus.
1. Im **[!UICONTROL Datenspeicher]** > ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) >  **[!UICONTROL Adobe Experience Platform]** Bildschirm, stellen Sie sicher, dass **[!UICONTROL Offer decisioning]**, **[!UICONTROL Edge-Segmentierung]**, und **[!UICONTROL Personalisierungsziele]** ausgewählt sind. Wenn Sie auch den Journey Optimizer-Lektionen folgen, wählen Sie **[!UICONTROL Adobe Journey Optimizer]**. Siehe [Adobe Experience Platform-Einstellungen](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=en#aep) für weitere Informationen.
1. Wählen Sie zum Speichern Ihrer Datastream-Konfiguration **[!UICONTROL Speichern]** .

   ![AEP-Datenspeicherkonfiguration](assets/datastream-aep-configuration-target.png)


### Installieren von Adobe Journey Optimizer - Decisioning Tags-Erweiterung

1. Navigieren Sie zu **[!UICONTROL Tags]**, suchen Sie Ihre mobile Tag-Eigenschaft und öffnen Sie die Eigenschaft .
1. Auswählen **[!UICONTROL Erweiterungen]**.
1. Auswählen **[!UICONTROL Katalog]**.
1. Suchen Sie nach **[!UICONTROL Adobe Journey Optimizer - Entscheidungsfindung]** -Erweiterung.
1. Installieren der Erweiterung. Die Erweiterung erfordert keine zusätzliche Konfiguration.

   ![Entscheidungserweiterung hinzufügen](assets/tag-add-decisioning-extension.png)


### Schema aktualisieren

1. Navigieren Sie zur Datenerfassungsoberfläche und wählen Sie **[!UICONTROL Schemas]** über die linke Leiste.
1. Auswählen **[!UICONTROL Durchsuchen]** aus der oberen Leiste.
1. Wählen Sie Ihr Schema aus, um es zu öffnen.
1. Wählen Sie im Schema-Editor ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** neben **[!UICONTROL Feldergruppen]**.
1. Im **[!UICONTROL Feldergruppen hinzufügen]** Dialogfeld, suchen Sie nach `proposition`auswählen **[!UICONTROL Erlebnisereignis - Interaktionen bei Vorschlägen]** und wählen **[!UICONTROL Feldergruppen hinzufügen]**.
   ![Vorschlag](assets/schema-fieldgroup-proposition.png)
1. Um die Änderungen am Schema zu speichern, wählen Sie **[!UICONTROL Speichern]**.


### Validieren der Einrichtung in der Zuverlässigkeitserklärung

So überprüfen Sie Ihre Einrichtung in Assurance:

1. Navigieren Sie zur Benutzeroberfläche &quot;Assurance&quot;.
1. Auswählen **[!UICONTROL Konfigurieren]** Wählen Sie in der linken Leiste ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) neben **[!UICONTROL Einrichtung überprüfen]** darunter **[!UICONTROL ADOBE JOURNEY OPTIMIZER-ENTSCHEIDUNG]**.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
1. Auswählen **[!UICONTROL Einrichtung überprüfen]** in der linken Leiste. Beide Datastream-Einstellungen werden validiert und das SDK-Setup in Ihrer Anwendung.
   ![Validierung von AJO-Entscheidungen](assets/ajo-decisioning-validation.png)

## Erstellen eines A/B-Tests

Es gibt viele Aktivitätstypen, die Sie in Adobe Target erstellen und in einer App implementieren können, wie in der Einführung beschrieben. Für diese Lektion implementieren Sie einen A/B-Test.

1. Wählen Sie in der Target-Benutzeroberfläche **[!UICONTROL Tätigkeiten]** aus der oberen Leiste.
1. Auswählen **[!UICONTROL Aktivität erstellen]** und **[!UICONTROL A/B-Test]** aus dem Kontextmenü aus.
1. Im **[!UICONTROL A/B-Test-Aktivität erstellen]** Dialogfeld auswählen **[!UICONTROL Mobilnummer]** als **[!UICONTROL Typ]**, wählen Sie einen Arbeitsbereich aus der **[!UICONTROL Arbeitsbereich auswählen]** und wählen Sie Ihre Eigenschaft aus dem **[!UICONTROL Eigenschaft auswählen]** auflisten, wenn Sie Target Premium-Kunde sind und im Datastream ein Eigenschafts-Token angegeben haben.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.
   ![Target-Aktivität erstellen](assets/target-create-activity1.png)

1. Im **[!UICONTROL Unbenannte Aktivität]** Bildschirm am **[!UICONTROL Erlebnisse]** step:

   1. Eingabe `luma-mobileapp-abtest` in **[!UICONTROL Standort auswählen]** darunter **[!UICONTROL STANDORT 1]**. Dieser Ortsname (häufig als Mbox bezeichnet) wird später in der App-Implementierung verwendet.
   1. Auswählen ![Chrevron nach unten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) neben **[!UICONTROL Standardinhalt]** und wählen **[!UICONTROL JSON-Angebot erstellen]** aus dem Kontextmenü aus.
   1. Kopieren Sie die folgende JSON in **[!UICONTROL Gültiges JSON-Objekt eingeben]**.

      ```json
      { 
          "title": "Luma Anaolog Watch",
          "text": "Designed to stand up to your active lifestyle, this women's Luma Analog Watch features a tasteful brushed chrome finish and a stainless steel, water-resistant construction for lasting durability.", 
          "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/watches/Luma_Analog_Watch.jpg" 
      }
      ```

   1. Auswählen **[!UICONTROL + Erlebnis hinzufügen]**.

      ![Erlebnis A](assets/target-create-activity-experienceA.png)

   1. Wiederholen Sie Schritt b und c für Erlebnis B, verwenden Sie stattdessen die folgende JSON:

      ```json
      { 
          "title": "Aim Analog Watch",
          "text": "The flexible, rubberized strap is contoured to conform to the shape of your wrist for a comfortable all-day fit. The face features three illuminated hands, a digital read-out of the current time, and stopwatch functions.", 
          "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/watches/Aim_Watch.jpg" 
      }
      ```

   1. Klicken Sie auf **[!UICONTROL Weiter]**.

      ![Erlebnis B](assets/target-create-activity-experienceB.png)

1. Im **[!DNL Targeting]** Schritt, überprüfen Sie die Einrichtung Ihres A/B-Tests. Standardmäßig werden beide Angebote gleichmäßig allen Besuchern zugeordnet. Klicken Sie auf **[!UICONTROL Weiter]**, um fortzufahren.

   ![Targeting](assets/taget-targeting.png)

1. Im **[!UICONTROL Ziele und Einstellungen]** step:

   1. Benennen Sie Ihre unbenannte Aktivität um, beispielsweise in `Luma Mobile SDK Tutorial - A/B Test Example`.
   1. Geben Sie eine **[!UICONTROL Ziel]** für Ihren A/B-Test, beispielsweise `A/B Test for Luma mobile app tutorial`.
   1. Auswählen **[!UICONTROL Konversion]**, **[!UICONTROL Anzeige einer mbox]** im **[!UICONTROL Zielmetrik]** > **[!UICONTROL MEIN PRIMÄRES ZIEL]** und geben Sie den Namen Ihres Standorts (Mbox) ein, z. B. `luma-mobileapp-abtest`.
   1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

      ![Zieleinstellungen](assets/target-goals.png)

1. Zurück im **[!UICONTROL Alle Aktivitäten]** screen:

   1. Auswählen ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) in Ihrer Aktivität.
   1. Auswählen ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg) **[!UICONTROL Aktivieren]** , um Ihren A/B-Test zu aktivieren.

   ![Aktivieren](assets/target-activate.png)


## Implementieren von Target in Ihre App

Wie in den vorherigen Lektionen erläutert, bietet die Installation einer mobilen Tag-Erweiterung nur die Konfiguration. Als Nächstes müssen Sie das Optimize SDK installieren und registrieren. Wenn diese Schritte nicht klar sind, überprüfen Sie die [SDKs installieren](install-sdks.md) Abschnitt.

>[!NOTE]
>
>Wenn Sie die [SDKs installieren](install-sdks.md) -Abschnitt, ist das SDK bereits installiert und Sie können diesen Schritt überspringen.
>

1. Stellen Sie in Xcode sicher, dass [AEP Optimize](https://github.com/adobe/aepsdk-messaging-ios) wird zur Liste der Pakete in Package-Abhängigkeiten hinzugefügt. Siehe [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL AppDelegate]** im Xcode-Projektnavigator.
1. Sichern `AEPOptimize` ist Teil Ihrer Importliste.

   `import AEPOptimize`

1. Sichern `Optimize.self` ist Teil des Arrays von Erweiterungen, die Sie registrieren.

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

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!DNL MobileSDK]** im Xcode-Projektnavigator. Suchen Sie die ` func updatePropositionAT(ecid: String, location: String) async` -Funktion. Fügen Sie den folgenden Code hinzu:

   ```swift
   // set up the XDM dictionary, define decision scope and call update proposition API
   Task {
       let ecid = ["ECID" : ["id" : ecid, "primary" : true] as [String : Any]]
       let identityMap = ["identityMap" : ecid]
       let xdmData = ["xdm" : identityMap]
       let decisionScope = DecisionScope(name: location)
       Optimize.clearCachedPropositions()
       Optimize.updatePropositions(for: [decisionScope], withXdm: xdmData)
   }
   ```

   Diese Funktion:

   * richtet ein XDM-Wörterbuch ein `xdmData`, die die ECID zur Identifizierung des Profils enthält, für das Sie den A/B-Test vorlegen müssen, und
   * definiert eine `decisionScope`, ein Array von Orten, an denen der A/B-Test präsentiert werden soll.

   Anschließend ruft die Funktion zwei APIs auf: [`Optimize.clearCachedPropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#clearpropositions) und [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions). Mit diesen Funktionen werden zwischengespeicherte Vorschläge gelöscht und die Vorschläge für dieses Profil aktualisiert. Ein Vorschlag in diesem Zusammenhang ist das Erlebnis (Angebot), das aus der Target-Aktivität ausgewählt wurde (Ihr A/B-Test) und in dem Sie [Erstellen eines A/B-Tests](#create-an-ab-test).

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Personalization]** > **[!DNL TargetOffersView]** im Xcode-Projektnavigator. Suchen Sie die `func onPropositionsUpdateAT(location: String) async {` und überprüfen Sie den Code dieser Funktion. Der wichtigste Teil dieser Funktion ist die  [`Optimize.onPropositionsUpdate`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#onpropositionsupdate) API-Aufruf, der:
   * ruft die Vorschläge für das aktuelle Profil basierend auf dem Entscheidungsbereich ab (dem Ort, den Sie im A/B-Test definiert haben),
   * ruft das Angebot aus dem Vorschlag ab,
   * entpackt den Inhalt des Angebots, damit er ordnungsgemäß in der App angezeigt werden kann, und
   * Trigger `displayed()` -Aktion für das Angebot, durch die ein Ereignis an Platform Edge Network zurückgesendet wird, um Informationen zum Angebot zu erhalten.

1. Noch in **[!DNL TargetOffersView]** Fügen Sie den folgenden Code zum `.onFirstAppear` -Modifikator. Dieser Code stellt sicher, dass der Callback zur Aktualisierung der Angebote nur einmal registriert wird.

   ```swift
   // Invoke callback for offer updates
   Task {
       await self.onPropositionsUpdateAT(location: location)
   }
   ```

1. Noch in **[!DNL TargetOffersView]** Fügen Sie den folgenden Code zum `.task` -Modifikator. Dieser Code aktualisiert die Angebote, wenn die Ansicht aktualisiert wird.

   ```swift
   // Clear and update offers
   await self.updatePropositionsAT(ecid: currentEcid, location: location)
   ```

Sie können zusätzliche Target-Parameter (wie Mbox-, Profil-, Produkt- oder Bestellparameter) in einer Personalisierungsabfrageanfrage an das Experience Edge-Netzwerk senden, indem Sie sie beim Aufruf der [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions) API. Weitere Informationen finden Sie unter [Zielparameter](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/#target-parameters).


## Validieren mit der App

1. Erstellen Sie die App im Simulator oder auf einem physischen Gerät aus Xcode neu und führen Sie sie mithilfe von ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Navigieren Sie zu **[!UICONTROL Personalisierung]** Registerkarte.

1. Scrollen Sie nach unten, und eines der beiden Angebote, die Sie in Ihrem A/B-Test definiert haben, wird im **[!UICONTROL TARGET]** Kachel.

   <img src="assets/target-app-offer.png" width="300">


## Validieren der Implementierung in Assurance

So validieren Sie den A/B-Test in Assurance:

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) -Abschnitt, um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Auswählen **[!UICONTROL Konfigurieren]** Wählen Sie in der linken Leiste ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) neben **[!UICONTROL Überprüfen und Simulieren]** darunter **[!UICONTROL ADOBE JOURNEY OPTIMIZER-ENTSCHEIDUNG]**.
1. Wählen Sie **[!UICONTROL Speichern]** aus.
1. Auswählen **[!UICONTROL Überprüfen und Simulieren]** in der linken Leiste. Beide Datastream-Einstellungen werden validiert und das SDK-Setup in Ihrer Anwendung.
1. Auswählen **[!UICONTROL Anforderungen]** in der oberen Leiste. Sie sehen Ihre **[!DNL Target]** -Anfragen.
   ![Validierung von AJO-Entscheidungen](assets/assurance-decisioning-requests.png)

1. Sie können **[!UICONTROL Simulieren]** und **[!UICONTROL Ereignisliste]** Registerkarten für weitere Funktionen, in denen Sie Ihre Einrichtung für Target-Angebote überprüfen.

## Nächste Schritte

Sie sollten jetzt über alle Tools verfügen, um Ihrer App, sofern relevant und zutreffend, weitere A/B-Tests oder andere Target-Aktivitäten (wie Erlebnis-Targeting, Multivarianz-Test) hinzuzufügen. Detailliertere Informationen finden Sie im [GitHub-Repository für die Optimize-Erweiterung](https://github.com/adobe/aepsdk-optimize-ios) wo Sie auch einen Link zu einem [Tutorial](https://opensource.adobe.com/aepsdk-optimize-ios/#/tutorials/README) Informationen zur Verfolgung von Adobe Target-Angeboten.

>[!SUCCESS]
>
>Sie haben die App für A/B-Tests aktiviert und die Ergebnisse eines A/B-Tests mit Adobe Target und der Adobe Journey Optimizer - Decisioning-Erweiterung für das Adobe Experience Platform Mobile SDK angezeigt.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Weiter: **[Schlussfolgerung und nächste Schritte](conclusion.md)**
