---
title: Einrichten der Journey Optimizer-Entscheidungsverwaltung mit dem Platform Web SDK
description: Erfahren Sie, wie Sie die Entscheidungsverwaltung mit dem Platform Web SDK implementieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
solution: Data Collection,Experience Platform,Journey Optimizer
feature-set: Journey Optimizer
feature: Decision Management,Offers
jira: KT-15412
exl-id: f7852ef4-44b0-49df-aec8-cb211726247d
source-git-commit: 901b90ca165a74bbc4f871469222064b70d0a20a
workflow-type: tm+mt
source-wordcount: '2513'
ht-degree: 3%

---

# Entscheidungsverwaltung mit dem Platform Web SDK einrichten

Erfahren Sie, wie Sie die Entscheidungsverwaltungsfunktion von Adobe Journey Optimizer mithilfe des Platform Web SDK implementieren. In diesem Handbuch werden die grundlegenden Entscheidungsverwaltungsvoraussetzungen, detaillierte Konfigurationsschritte und ein tiefer Einblick in einen Anwendungsfall zum Treuestatus gegeben.

In diesem Tutorial werden Journey Optimizer-Benutzer mit Funktionen zur Entscheidungsverwaltung ausgestattet, um die Personalisierung und Relevanz ihrer Kundeninteraktionen zu verbessern.


![Web SDK- und Adobe Analytics-Diagramm](assets/dc-websdk-ajo.png)

## Lernziele

Am Ende dieser Lektion können Sie:

* Machen Sie sich mit den Kernkonzepten der Entscheidungsverwaltung in der Adobe Journey Optimizer und ihrer Integration in das Adobe Experience Platform Web SDK vertraut.

* Erfahren Sie Schritt für Schritt, wie Sie das Web SDK für Offer decisioning konfigurieren und so eine nahtlose Integration mit Journey Optimizer sicherstellen.

* Erfahren Sie mehr über einen detaillierten Anwendungsfall, der sich auf Treuestatus-Angebote konzentriert und Einblicke in die effektive Erstellung und Verwaltung von Angeboten, Entscheidungen und Platzierungen bietet.

* Machen Sie sich mit wesentlichen Begriffen und deren Auswirkungen im Rahmen der Entscheidungsverwaltung vertraut.

* Machen Sie sich mit der Bedeutung von Entscheidungsregeln, Sammlungsqualifizierern und Fallback-Angeboten für die Bereitstellung des richtigen Angebots für den richtigen Benutzer vertraut.

* Erfahren Sie mehr über erweiterte Themen wie Simulationen und die Datenerfassung für benutzerdefinierte Ereignisse, mit denen Sie Ihre Mechanismen zur Angebotsbereitstellung testen, validieren und erweitern können.

## Voraussetzungen

Um die Lektionen in diesem Abschnitt abzuschließen, müssen Sie zunächst:

* Stellen Sie sicher, dass Ihr Unternehmen Zugriff auf Adobe Journey Optimizer Ultimate (Journey Optimizer und Offer decisioning) oder Adobe Experience Platform und das Offer decisioning-Add-on hat.

* Schließen Sie alle Lektionen für die Erstkonfiguration des Platform Web SDK ab.

* Aktivieren Sie Ihr Unternehmen für Edge Decisioning.

* Erfahren Sie, wie Sie eine Platzierung konfigurieren und Platzierungs- und Aktivitäts-IDs in Ihrer JSON-Entscheidungsbereich-JSON instanziieren.

## Einschränkungen

Ereignisbasierte Angebote werden in Adobe Journey Optimizer derzeit nicht unterstützt. Wenn Sie eine auf einem Ereignis basierende Entscheidungsregel erstellen, können Sie sie nicht auf ein Angebot anwenden.

## Zugriff auf das Entscheidungs-Management gewähren

Um Zugriff auf die Entscheidungsverwaltungsfunktion zu gewähren, müssen Sie ein **Produktprofil** erstellen und den Benutzern die entsprechenden Berechtigungen zuweisen. [Weitere Informationen zum Verwalten von Journey Optimizer-Benutzern und -Berechtigungen finden Sie in diesem Abschnitt](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/access-control/privacy/high-low-permissions#decisions-permissions).

## Konfigurieren des Datenspeichers

Offer decisioning muss in der Konfiguration **datastream** aktiviert sein, bevor Entscheidungsverwaltungsaktivitäten vom Platform Web SDK bereitgestellt werden können.

So konfigurieren Sie Offer decisioning im Datastream:

1. Wechseln Sie zur Oberfläche [Datenerfassung](https://experience.adobe.com/#/data-collection) .

1. Wählen Sie im linken Navigationsbereich **Datenspeicher** aus.

1. Wählen Sie den zuvor erstellten Datenspeicher des Luma Web SDK aus.

   ![Wählen Sie datastream](assets/decisioning-datastream-select.png)

1. Wählen Sie **Bearbeiten** innerhalb des **Adobe Experience Platform-Dienstes** aus.

   ![Dienst bearbeiten](assets/decisioning-edit-datastream.png)

1. Aktivieren Sie das Kontrollkästchen **Offer decisioning** .

   ![SCREENSHOT HINZUFÜGEN](assets/decisioning-check-offer-box.png)

1. Wählen Sie **Speichern** aus.

Dadurch wird sichergestellt, dass eingehende Ereignisse für Journey Optimizer vom **Adobe Experience Platform Edge** ordnungsgemäß verarbeitet werden.

## SDK für die Entscheidungsverwaltung konfigurieren

Die Entscheidungsverwaltung erfordert je nach Ihrem Web SDK-Implementierungstyp zusätzliche SDK-Schritte. Es gibt zwei verfügbare Optionen zum Konfigurieren des SDK für die Entscheidungsverwaltung.

* Eigenständige SDK-Installation
   1. Konfigurieren Sie die `sendEvent` -Aktion mit Ihrem `decisionScopes`.

      ```javascript
      alloy("sendEvent", {
         ...
         "decisionScopes": [
            "[DECISION SCOPE 1]",
            "[DECISION SCOPE 2]"
         ]
      })
      ```

* Installation von SDK-Tags
   1. Wechseln Sie zur Datenerfassungsoberfläche.

   1. Wählen Sie im linken Navigationsbereich **Tags** aus.

      ![Tags auswählen](assets/decisioning-data-collection-tags.png)

   1. Wählen Sie die **Tag-Eigenschaft** aus.

   1. Erstellen Sie Ihre **Regeln**.
      * Fügen Sie eine Platform Web SDK **Aktion &quot;Ereignis senden&quot;** hinzu und fügen Sie die relevante `decisionScopes` zur Konfiguration dieser Aktion hinzu.

   1. Erstellen und veröffentlichen Sie eine **Bibliothek** mit allen relevanten **Regeln**, **Datenelemente** und **Erweiterungen**, die Sie konfiguriert haben.

## Terminologie

Zunächst sollten Sie die in der Benutzeroberfläche für die Entscheidungsverwaltung verwendete Terminologie verstehen.

* **Begrenzung**: Eine Begrenzung, die bestimmt, wie oft ein Angebot angezeigt wird. Zwei Typen:
   * Höchstwerte für die Gesamtanzahl: Maximale Anzahl der Wiedergaben eines Angebots in der gesamten Zielgruppe.
   * Profilbegrenzung: Die Zeiten, in denen ein Angebot einem bestimmten Benutzer angezeigt werden kann.
* **Sammlungen**: Untergruppen von Angeboten, die nach bestimmten, von einem Marketing-Experten festgelegten Bedingungen gruppiert sind, z. B. Angebotskategorien.
* **Entscheidung**: Logik, die die Auswahl eines Angebots vorschreibt.
* **Entscheidungsregel**: Begrenzungen für Angebote, um die Eignung eines Benutzers zu ermitteln.
* **Geeignetes Angebot**: Ein Angebot, das den voreingestellten Begrenzungen entspricht und einem Benutzer angezeigt werden kann.
* **Entscheidungsverwaltung**: Das System zum Erstellen und Verteilen personalisierter Angebote mithilfe von Geschäftslogik und Entscheidungsregeln.
* **Fallback-Angebote**: Das Standardangebot, das angezeigt wird, wenn ein Benutzer für keine Angebote in einer Sammlung qualifiziert ist.
* **Angebot**: Eine Marketing-Nachricht mit potenziellen Eignungsregeln, die die Viewer bestimmen.
* **Angebotsbibliothek**: Ein zentrales Repository, das Angebote, Entscheidungen und zugehörige Regeln verwaltet.
* **Personalisierte Angebote**: Benutzerdefinierte Marketing-Nachrichten, die auf Eignungsbegrenzungen basieren.
* **Platzierungen**: Die Einstellung oder das Szenario, in der einem Benutzer ein Angebot angezeigt wird.
* **Priorität**: Rangmetrik für Angebote unter Berücksichtigung verschiedener Einschränkungen wie Eignung und Begrenzung.
* **Darstellungen**: Kanalspezifische Informationen, z. B. Ort oder Sprache, die die Anzeige eines Angebots lenken.

## Nutzungsszenario - Überblick über Treuebelohnungen

In dieser Lektion implementieren Sie ein Anwendungsbeispiel für Treuebelohnungen , um die Entscheidungsverwaltung mithilfe des Web SDK zu verstehen.

In diesem Anwendungsbeispiel wird erläutert, wie Journey Optimizer mithilfe der zentralisierten Angebotsbibliothek und der Entscheidungs-Engine für die Entscheidungsfindung bei der Bereitstellung des besten Angebots für Ihre Kunden helfen kann.

>[!NOTE]
>
> Da dieses Tutorial auf Implementierer ausgerichtet ist, ist zu beachten, dass diese Lektion umfangreiche Arbeit an der Benutzeroberfläche in Journey Optimizer erfordert. Während solche Aufgaben in der Regel von Marketingexperten verarbeitet werden, können Implementoren Einblicke in den Prozess erhalten, selbst wenn sie langfristig nicht für die Erstellung von Entscheidungskampagnen verantwortlich sind.

## Komponenten

Bevor Sie mit der Erstellung der Angebote beginnen, müssen Sie mehrere Voraussetzungen definieren.

### Erstellen einer Platzierung für Treueangebote

**Platzierungen** sind Container, mit denen die Angebote präsentiert werden. In diesem Beispiel erstellen Sie eine Platzierung am Anfang der Site &quot;Luma&quot;.

Die Liste der Platzierungen ist im Menü **Komponenten** verfügbar. Es gibt Filter, mit denen Sie Platzierungen nach einem bestimmten Kanal oder Inhalt abrufen können.

![Anzeigen von Platzierungen](assets/decisioning-placements-list.png)

Gehen Sie wie folgt vor, um die Platzierung zu erstellen:

1. Klicken Sie auf **Platzierung erstellen**.

   ![Platzierung erstellen](assets/decisioning-create-placement.png)

1. Definieren Sie die Eigenschaften der Platzierung:
   * **Name**: der Name der Platzierung. Rufen wir die Beispielplatzierung *&#39;Homepage Banner&#39;* auf.
   * **Kanaltyp**: Der Kanal, für den die Platzierung verwendet wird. Verwenden wir *&#39;Web&#39;* , da die Angebote auf der Luma-Website angezeigt werden.
   * **Inhaltstyp**: Der Inhaltstyp, den die Platzierung anzeigen darf: Text, HTML, Bild-Link oder JSON. Sie können *&#39;HTML&#39;* für das Angebot verwenden.
   * **Beschreibung**: eine Beschreibung der Platzierung (optional).

   ![Details hinzufügen](assets/decisioning-placement-details.png)

1. Klicken Sie auf **Speichern**.
1. Nachdem die Platzierung erstellt wurde, wird sie in der Platzierungsliste angezeigt.
1. Wählen Sie die Zeile aus, die Ihre neue Platzierung enthält, und notieren Sie sich die Platzierungs-ID, da dies für die Konfiguration in Ihrem Entscheidungsbereich erforderlich sein kann.

   ![Siehe Platzierungs-ID ](assets/decisioning-placement-id.png)

### Entscheidungsregeln für den Treuestatus

**Entscheidungsregeln** geben die Bedingungen an, unter denen die Angebote unterbreitet werden. In diesem Beispiel erstellen Sie Entscheidungsregeln, die abhängig vom Treuestatus eines Benutzers für verschiedene Angebote gelten.

Die Liste der Entscheidungsregeln ist im Menü **Komponenten** verfügbar.

Gehen Sie wie folgt vor, um die Entscheidungsregeln zu erstellen:

1. Navigieren Sie zur Registerkarte **Regeln** und klicken Sie auf **Regel erstellen**.

   ![ Regel erstellen](assets/decisioning-create-rule.png)

1. Nennen wir die erste Regel &quot;*Gold Loyalty Status Rule*&quot;. Sie können XDM-Felder verwenden, um die Regel zu definieren. Der Adobe Experience Platform **Segmentaufbau** ist eine intuitive Benutzeroberfläche, mit der Sie Regelbedingungen erstellen können.

   ![Regel definieren](assets/decisioning-define-rule.png)

1. Klicken Sie auf **Speichern** , um die Regelbedingung zu bestätigen.
1. Die neu gespeicherte Regel &quot;*Gold Loyalty Status Rule*&quot;wird in der Liste **Regeln** angezeigt. Wählen Sie es aus, um seine Eigenschaften anzuzeigen.

   ![Erstellte Regel anzeigen](assets/decisioning-view-rules.png)

1. Erstellen Sie nun die verbleibenden Bedingungen für die Treueangebotsregel für den Anwendungsfall.


### Sammlungskennungen

**Sammlungsbezeichner** ermöglichen es Ihnen, Angebote in der Angebotsbibliothek einfach zu organisieren und zu suchen. In diesem Beispiel fügen Sie den Angeboten &quot;Treuebelohnungen&quot;Sammlungsbezeichner hinzu, um die Organisation des Angebots zu verbessern.

Die Liste der Sammlungsbezeichner ist im Menü **Komponenten** verfügbar.

Gehen Sie wie folgt vor, um den Sammlungsbezeichner &quot;Treuebelohnungen&quot;zu erstellen:

1. Navigieren Sie zur Registerkarte **Sammlungsbezeichner** und klicken Sie auf **Sammlungsbezeichner erstellen**.

   ![Sammlungsbezeichner erstellen](assets/decisioning-create-collection-qualifier.png)

1. Benennen wir den Sammlungsbezeichner &quot;*Treuebelohnungen*&quot;.

   ![Benennen der Sammlung](assets/decisioning-name-collection.png)

1. Der neue Sammlungsbezeichner sollte jetzt auf der Registerkarte **Sammlungsqualifikator** angezeigt werden.

## Angebote

Jetzt ist es an der Zeit, die Angebote für Treuebelohnungen zu erstellen.

Auf die Liste der Angebote kann im Menü **Angebote** zugegriffen werden.

![Menü &quot;Angebote anzeigen&quot;](assets/decisioning-offers-menu.png)


### Erstellen von Angeboten für verschiedene Treueebenen

Erstellen Sie zunächst personalisierte Angebote für die verschiedenen Treueebenen in Luma.

Gehen Sie wie folgt vor, um das erste **Angebot** zu erstellen:

1. Klicken Sie auf **Angebot erstellen** und wählen Sie dann **Personalisiertes Angebot** aus.

1. Nennen wir das erste Angebot &quot;*Luma Loyalty Tier - Gold*&quot;. Sie müssen ein Start-/Enddatum und eine Uhrzeit für dieses Angebot angeben. Sie sollten auch den **Sammlungsqualifikator** &#39;*Treuebelohnungen*&#39; mit dem Angebot verknüpfen, damit Sie sich besser in der **Angebotsbibliothek** organisieren können. Klicken Sie anschließend auf **Weiter**.

   ![Hinzufügen von Angebotsdetails](assets/decisioning-add-offer-details.png)

1. Jetzt müssen Sie **Darstellungen** hinzufügen, um festzulegen, wo das Angebot angezeigt wird. Wählen wir den **Webkanal** aus. Wählen wir auch die zuvor konfigurierte Platzierung &quot;*Homepage-Banner*&quot; **Platzierung**&quot;. Die ausgewählte **Platzierung** ist vom HTML-Typ, sodass Sie dem Editor direkt HTML-, JSON- oder Textinhalte hinzufügen können, um das Angebot mithilfe des Optionsfelds **Benutzerdefiniert** zu erstellen.

   ![Hinzufügen von Darstellungsdetails](assets/decisioning-add-representation-details.png)

1. Bearbeiten Sie den Angebotsinhalt direkt mit dem **Ausdruckseditor**. Denken Sie daran, dass Sie dieser Platzierung HTML-, JSON- oder TEXTinhalte hinzufügen können. Stellen Sie sicher, dass Sie je nach Inhaltstyp unten im Editor den richtigen **mode** auswählen. Sie können auch auf **validate** klicken, um sicherzustellen, dass keine Fehler auftreten.

   ![Angebot hinzufügen, HTML](assets/decisioning-add-offer-html.png)

1. Sie können auch den Ausdruckseditor verwenden, um in Adobe Experience Platform gespeicherte Attribute abzurufen. Fügen wir den Vornamen eines Profils zum Angebotsinhalt hinzu, um die Mitglieder des Treueprogramms auf 1:1-Ebene besser zu personalisieren.

   ![Angebotspersonalisierung hinzufügen](assets/decisioning-add-offer-personalization.png)

1. Fügen Sie Einschränkungen hinzu, um das Angebot nur Profilen anzuzeigen, die für die &quot;*Gold Loyalty Status Rule*&quot;-Regel qualifiziert sind.

   ![Fügen Sie Regelbegrenzung hinzu](assets/decisioning-add-rule-constraint.png)

1. Nachdem Sie die Überprüfung Ihres Angebots abgeschlossen haben, klicken Sie auf **Beenden**. Wählen Sie **Speichern und genehmigen** aus.

Erstellen Sie nun den Rest der Angebote für die verschiedenen Loyalitätsstufen von Luma

### Fallback-Angebote

Sie möchten weiterhin ein Angebot für Besucher ohne Luma-Treueprogramm auf der Site &quot;Luma&quot;bereitstellen. Dazu können Sie ein **Fallback-Angebot** für die Kampagne konfigurieren.

Gehen Sie wie folgt vor, um das Fallback-Angebot zu erstellen:

1. Klicken Sie auf **Angebot erstellen** und wählen Sie dann **Fallback-Angebot** aus.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Nennen wir das Fallback-Angebot &quot;*Nicht-Luma-Treue*&quot;. Sie können auch den zuvor erstellten **Sammlungsqualifikator**, &#39;*Treuebelohnungen*&#39;, dem Fallback-Angebot zuordnen, um die Organisation des Angebots zu vereinfachen.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Fügen Sie den Inhalt des Fallback-Angebots zum **Ausdruckseditor** hinzu. Denken Sie daran, dass Sie dieser Platzierung HTML-, JSON- oder TEXTinhalte hinzufügen können. Stellen Sie sicher, dass Sie je nach Inhaltstyp unten im Editor den richtigen **mode** auswählen. Sie können auch auf **validate** klicken, um sicherzustellen, dass keine Fehler auftreten.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Wenn alles korrekt konfiguriert ist, drücken Sie **Beenden** und dann **Speichern und genehmigen**.
<!--
   ![ADD SCREENSHOT](#)
-->

## Entscheidungen

**Entscheidungen** sind Container für Angebote, die je nach Zielgruppe das beste für einen Kunden verfügbare Angebot auswählen.

Die Liste der Entscheidungen ist auf der Registerkarte **Entscheidungen** des Menüs **Angebote** verfügbar.
<!--
   ![ADD SCREENSHOT](#)
-->

### Erstellen einer Entscheidung für Treueangebote

Erstellen wir eine Entscheidung für den Anwendungsfall &quot;Loyalitätsbelohnungen für Luma&quot;.

Gehen Sie wie folgt vor, um die Entscheidung zu erstellen:

1. Klicken Sie auf **Entscheidung erstellen**.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Nennen wir die Entscheidung &quot;*Treueangebote für Dezember*&quot;. Die Angebote sollten einen Monat lang ausgeführt werden. Legen wir also fest, dass dies hier der Fall ist.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Jetzt müssen Sie die **Entscheidungsbereiche** definieren. Wählen Sie zuerst eine Platzierung aus. Sie können das zuvor erstellte &quot;*Homepage-Banner*&quot; verwenden.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Als Nächstes müssen Sie **Bewertungskriterien** für den Entscheidungsbereich hinzufügen. Klicken Sie auf **Hinzufügen** und wählen Sie die zuvor erstellte Sammlung &quot;*Treuebelohnungen*&quot;aus, die alle zu berücksichtigenden Treueangebote enthält.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. In der Kollektion &#39;*Treuebelohnungen*&#39; können Sie das Feld &quot;Eignung&quot;verwenden, um den Versand von Angeboten auf eine Untergruppe von Luma-Besuchern zu beschränken. Für diesen Anwendungsfall möchten Sie jedoch, dass jeder Besucher eines der Angebote erhält. Beachten Sie, dass Sie für alle Besucher, die nicht dem Treueprogramm angehören, ein **Fallback-Angebot** konfiguriert haben. Setzen Sie die Berechtigung auf &quot;Keine&quot;.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Sie können auch das Feld **Ranking method** verwenden, um das beste Angebot für jeden Luma-Besucher auszuwählen, wenn mehrere Angebote für die Benutzer-/Platzierungskombination infrage kommen. Für diesen Anwendungsfall können Sie die Methode **Angebotspriorität** verwenden, die die in den Angeboten definierten Werte verwendet, um das beste Angebot bereitzustellen.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Fügen Sie der Entscheidung jetzt das Fallback-Angebot **1} hinzu.** Beachten Sie, dass das Fallback-Angebot das Standardangebot ist, das Luma-Besuchern angezeigt wird, wenn sie keiner der Zielgruppen vom Typ &quot;Treue zu Luma&quot;angehören. Wählen Sie &quot;*Nicht-Luma-Treue*&quot;aus der Liste der verfügbaren Fallback-Angebote für die Platzierung &quot;*Homepage-Banner*&quot;aus.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Bevor wir die Entscheidung aktivieren, überprüfen wir den Umfang der Entscheidung, das Fallback-Angebot, zeigen eine Vorschau der verfügbaren Angebote an und schätzen die qualifizierten Profile. Sobald alles gut aussieht, können Sie auf **Beenden** und **Speichern und aktivieren** klicken.
<!--
   ![ADD SCREENSHOT](#)
-->

## Simulationen

Als Best Practice sollten Sie die Entscheidungslogik für das Treueprogramm von Luma validieren, um sicherzustellen, dass die richtigen Angebote an die richtigen Loyalitätszielgruppen gesendet werden. Sie können diese Validierung mit **Testprofilen** durchführen. Außerdem ist es empfehlenswert, Änderungen an Angeboten über Testprofile zu testen, bevor neue Angebotsversionen in die Produktion gepusht werden.

Um den Test zu starten, wählen Sie die Registerkarte **Simulationen** aus dem Menü **Angebote** aus.

### Testen von Treueangeboten

1. Wählen Sie ein Testprofil aus, das für die Simulation verwendet werden soll. Klicken Sie auf **Profil verwalten**. [Befolgen Sie dieses Handbuch](https://experienceleague.adobe.com/en/docs/journeys/using/building-journeys/about-journey-building/creating-test-profiles#create-test-profiles-csv), um ein neues Testprofil für Angebotstests zu erstellen oder festzulegen.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Fügen Sie ein oder mehrere Testprofile zur Simulation hinzu und speichern Sie Ihre Auswahl. Für die Falltests sollten Sie sicherstellen, dass Sie Testprofile für jede Luma Loyalty Rewards-Zielgruppe konfiguriert haben.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Wählen Sie den zu testenden Entscheidungsbereich aus. Wählen Sie **Entscheidungsumfang hinzufügen** aus.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Wählen Sie die zuvor erstellte Platzierung &quot;*Homepage-Banner*&quot;aus.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Die verfügbaren Entscheidungen werden angezeigt, wählen Sie die zuvor erstellte Entscheidung &quot;*Treueangebote für Dezember*&quot;aus und klicken Sie auf **Hinzufügen**.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Nachdem Sie ein Testprofil ausgewählt haben, klicken Sie auf **Ergebnisse anzeigen**. Das beste verfügbare Angebot wird dem ausgewählten Testprofil für die Entscheidung &quot;*Treueangebote für Dezember in Luma*&quot;angezeigt.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Wählen Sie ein anderes Testprofil aus und klicken Sie auf **Ergebnisse anzeigen**. Idealerweise sollte ein anderes simuliertes Angebot angezeigt werden, das der Treuestufe des Testprofils entspricht.

## Validierung der Entscheidungsverwaltung mithilfe von Adobe Experience Platform Debugger

Die sowohl für Chrome als auch Firefox verfügbare Erweiterung **Adobe Experience Platform Debugger** analysiert Ihre Webseiten, um Probleme bei der Implementierung von Adobe Experience Cloud-Lösungen zu identifizieren.

Sie können den Debugger auf der Site &quot;Luma&quot;verwenden, um die Entscheidungslogik in der Produktion zu überprüfen. Diese Validierung empfiehlt sich, sobald der Anwendungsfall &quot;Treuebelohnungen&quot;aktiv ist, um sicherzustellen, dass alles korrekt konfiguriert ist.

[Erfahren Sie hier, wie Sie den Debugger in Ihrem Browser mithilfe des Leitfadens konfigurieren](https://experienceleague.adobe.com/en/docs/platform-learn/data-collection/debugger/overview).

So starten Sie die Validierung mit dem Debugger:

1. Navigieren Sie mit der Angebotsplatzierung zur Webseite &quot;Luma&quot;.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Öffnen Sie auf der Webseite den **Adobe Experience Platform-Debugger**.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Navigieren Sie zu **Zusammenfassung**. Stellen Sie sicher, dass die **Datastream-ID** mit dem **Datastream** in der **Adobe-Datenerfassung** übereinstimmt, für den Sie Offer decisioning aktiviert haben.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Navigieren Sie unter **Lösungen** zum **Experience Platform Web SDK**.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Schalten Sie auf der Registerkarte **Konfiguration** die Option **Debugging aktivieren** um. Dadurch wird die Protokollierung für die Sitzung in einer **Adobe Experience Platform Assurance**-Sitzung aktiviert.
   <!--
      ![ADD SCREENSHOT](#)
   -->
1. Sie können sich dann mit verschiedenen Treuekonten von Luma bei der Site anmelden und den Debugger verwenden, um die an das Adobe Experience Platform Edge-Netzwerk gesendeten Anforderungen zu validieren.**** Alle diese Anfragen sollten in **Assurance** für die Protokollverfolgung erfasst werden.
<!--
   ![ADD SCREENSHOT](#)
-->

[Weiter: ](setup-consent.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
