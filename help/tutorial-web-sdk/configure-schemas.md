---
title: Erstellen eines XDM-Schemas für Webdaten
description: Erfahren Sie, wie Sie in der Datenerfassungsoberfläche ein XDM-Schema für Webdaten erstellen. Diese Lektion ist Teil des Tutorials Adobe Experience Cloud mit Web SDK implementieren .
feature: Schemas
exl-id: 2858ce03-4f95-43ac-966c-1b647b33ef16
source-git-commit: fc0567823039f8a2005aa64a3f10c5a2564cbf64
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 6%

---

# Erstellen eines XDM-Schemas für Webdaten

Erfahren Sie, wie Sie in der Datenerfassungsoberfläche ein XDM-Schema für Webdaten erstellen.

Experience-Datenmodell (XDM)-Schemas sind die Bausteine, Grundsätze und Best Practices zum Erstellen von Schemas in Adobe Experience Platform.

Das Platform Web SDK verwendet Ihr Schema zur Standardisierung Ihrer Web-Ereignisdaten, zum Senden an das Platform Edge Network und schließlich zum Weiterleiten der Daten an alle im Datastream konfigurierten Experience Cloud-Anwendungen. Dieser Schritt ist wichtig, da er ein Standarddatenmodell definiert, das für die Aufnahme von Kundenerlebnisdaten in Experience Platform erforderlich ist, und nachgelagerte Dienste und Anwendungen ermöglicht, die auf diesen Standards basieren.

>[!NOTE]
>
> Zu Demonstrationszwecken erstellen die Übungen in dieser Lektion ein Beispielschema, um die angezeigten Inhalte und die von Kunden im Abschnitt gekauften Produkte zu erfassen. [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html). Sie können diese Schritte zwar verwenden, um ein anderes Schema für Ihre eigenen Zwecke zu erstellen, es wird jedoch empfohlen, zunächst das Beispielschema zu erstellen, um mehr über die Funktionen des Schema-Editors zu erfahren.

Weitere Informationen zu XDM-Schemata finden Sie im Kurs &quot;[Modellieren Ihrer Kundenerlebnisdaten mit XDM](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)&quot; oder sehen Sie die [XDM-System - Übersicht](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html?lang=de).

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen eines XDM-Schemas über die Datenerfassungsoberfläche
* Hinzufügen von Feldergruppen zu Ihrem XDM-Schema
* Erstellen von XDM-Schemata für Web-Ereignisdaten mithilfe von Best Practices

## Voraussetzungen

Alle erforderlichen Bereitstellungs- und Benutzerberechtigungen für die Datenerfassung und Adobe Experience Platform werden im Abschnitt [Berechtigungen konfigurieren](configure-permissions.md) Lektion.

## Erstellen eines XDM-Schemas

XDM-Schemata sind die Standardmethode, um Daten in Experience Platform zu beschreiben, sodass alle Daten, die den Schemas entsprechen, in einer Organisation ohne Konflikte wiederverwendet oder sogar von mehreren Organisationen gemeinsam genutzt werden können. Weitere Informationen finden Sie unter [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=de).

In dieser Übung erstellen Sie ein XDM-Schema mit den empfohlenen Grundfeldgruppen für die Erfassung von Webereignisdaten auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target=&quot;_blank&quot;}:

1. Öffnen Sie die [Datenerfassungsoberfläche](https://launch.adobe.com/){target=&quot;_blank&quot;}
1. Vergewissern Sie sich, dass Sie sich in der richtigen Sandbox befinden.

   >[!NOTE]
   >
   >Wenn Sie Kunde einer plattformbasierten Anwendung wie der Echtzeit-Kundendatenplattform sind, empfehlen wir für dieses Tutorial die Verwendung einer Entwicklungs-Sandbox. Wenn nicht, verwenden Sie die **[!UICONTROL Prod]** Sandbox.

1. Navigieren Sie zu **[!UICONTROL Schemas]** in der linken Navigation
1. Wählen Sie die **[!UICONTROL Schema erstellen]** Schaltfläche oben rechts
1. Wählen Sie aus dem Dropdown-Menü **[!UICONTROL XDM ExperienceEvent]**

![Schema-Erlebnisereignis](assets/schema-XDM-experience-event.jpg)

## Klicken Sie auf Feldergruppen hinzufügen

Wie bereits erwähnt, ist XDM das zentrale Framework, das Kundenerlebnisdaten durch Bereitstellung gemeinsamer Strukturen und Definitionen für nachgelagerte Adobe Experience Platform-Dienste standardisiert. Durch Einhaltung von XDM-Standards _alle Kundenerlebnisdaten_ in eine gemeinsame Vertretung aufgenommen werden. Dieser Ansatz ermöglicht es Ihnen, wertvolle Einblicke aus Kundenaktionen zu gewinnen, Kundenzielgruppen über Segmente zu definieren und Kundenattribute für Personalisierungszwecke mithilfe von Daten aus verschiedenen Quellen auszudrücken. Siehe [Best Practices für die Datenmodellierung](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/best-practices.html?lang=en) für weitere Informationen.

Wenn möglich, wird empfohlen, vorhandene Feldergruppen zu verwenden und ein produktagnostisches Modell und Namenskonventionen einzuhalten. Für alle Daten, die spezifisch für Ihr Unternehmen sind und nicht in die vordefinierten Feldergruppen oben passen, können Sie eine benutzerdefinierte Feldergruppe erstellen. Siehe [Erstellen eines Schemas mit dem Schema Editor](https://experienceleague.adobe.com/docs/experience-platform/xdm/tutorials/create-schema-ui.html?lang=en#create) für detailliertere Schritte zu benutzerdefinierten Schemas.

>[!TIP]
> 
>In dieser Übung fügen Sie die empfohlenen vordefinierten Feldergruppen für die Web-Datenerfassung hinzu: _**[!UICONTROL AEP Web SDK ExperienceEvent]**_ und _**[!UICONTROL Ereignis für Kundenerlebnisse]**_.

1. Im **[!UICONTROL Feldergruppen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**
1. Suchen Sie nach [!UICONTROL `AEP Web SDK ExperienceEvent`].
1. Aktivieren Sie das Kontrollkästchen
1. Suchen Sie nach [!UICONTROL `Consumer Experience Event`].
1. Aktivieren Sie das Kontrollkästchen
1. Auswählen **[!UICONTROL Feldergruppen hinzufügen]**

   ![Feldergruppe hinzufügen](assets/schema-add-field-group.jpg)

Wenn die Feldergruppen ausgewählt sind, können Sie Ihr Schema benennen. Eine gängige Benennungskonvention für XDM-Schemas besteht darin, das Schema nach der Datenquelle zu benennen:

1. Im **[!UICONTROL Komposition**] Bereich, wählen Sie die `Untitled schema name`
1. Im **[!UICONTROL Schemaeigenschaften]** Bereich, geben Sie die **[!UICONTROL Anzeigename]** `Luma Web Event Data`
1. Alles außerhalb der **[!UICONTROL Anzeigename]** -Feld zum Aktivieren der **[!UICONTROL Speichern]** option
1. Wählen Sie **[!UICONTROL Speichern]** aus

![Luma-Web-Ereignisdaten](assets/schema-luma-web-event-data.png)

Beachten Sie bei beiden Feldergruppen, dass Sie Zugriff auf die am häufigsten verwendeten Schlüssel-Wert-Paare haben, die für die Datenerfassung im Internet erforderlich sind. Die [!UICONTROL Anzeigename] für Marketing-Experten in der Segment Builder-Oberfläche von Platform-basierten Anwendungen angezeigt werden und Sie können den Anzeigenamen von Standardfeldern an Ihre Anforderungen anpassen. Sie können auch Felder entfernen, die Sie nicht möchten. Wenn Sie auf einen der Feldgruppennamen klicken, wird in der Benutzeroberfläche hervorgehoben, zu welchen Schlüssel-Wert-Paargruppierungen gehören. Im folgenden Beispiel sehen Sie, zu welchen Gruppen gehören **[!UICONTROL Ereignis für Kundenerlebnisse]**.

![Schemafeldgruppen](assets/schema-consumer-experience-event.jpg)

Diese Lektion ist nur ein Ausgangspunkt. Beim Erstellen Ihres eigenen Web-Ereignisschemas müssen Sie Ihre Geschäftsanforderungen untersuchen und dokumentieren. Dieser Vorgang ähnelt dem Erstellen einer [Geschäftsanforderungsdokument](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-a-business-requirements-document.html?lang=de) und [Lösungsdesign-Referenz](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-and-maintaining-an-sdr.html) für eine Adobe Analytics-Implementierung, sollte jedoch Anforderungen für _alle nachgelagerten Datenempfänger_ , wie z. B. Ziele für die Plattform-, Target- und Ereignisweiterleitung.


### Das identityMap -Objekt

Zur Identifizierung von Webbenutzern ist ein spezieller Datensatz erforderlich, der `[!UICONTROL identityMap]`.

![Luma-Web-Ereignisdaten](assets/schema-identityMap.png)

Es handelt sich um ein &quot;must-have&quot;-Objekt für jede webbezogene Datenerfassung, da es die Experience Cloud-ID enthält, die zur Identifizierung von Benutzern im Internet erforderlich ist. Dies ist auch der Schlüssel zum Festlegen interner Kunden-IDs für authentifizierte Benutzer. `[!UICONTROL identityMap]` wird im Abschnitt [Identitäten konfigurieren](configure-identities.md) Lektion. Sie wird automatisch in alle Schemas mit der Variablen **[!UICONTROL XDM ExperienceEvent]** -Klasse.


>[!IMPORTANT]
>
> Es ist möglich, **[!UICONTROL Profil]** für ein Schema vor dem Speichern des Schemas. **Nicht** aktivieren. Nachdem ein Schema für Profil aktiviert wurde, kann es nicht mehr deaktiviert oder gelöscht werden. Außerdem können Felder nach diesem Punkt nicht mehr aus dem Schema entfernt werden. Diese Implikationen sollten Sie später bei der Arbeit mit Ihren eigenen Daten in Ihrer Produktionsumgebung berücksichtigen.
>
>Diese Einstellung wird während der [Setup-Experience Platform](setup-experience-platform.md) Lektion.
>![Profilschema](assets/schema-profile.png)

Jetzt können Sie dieses Schema referenzieren, wenn Sie die Web SDK-Erweiterung Ihrer Tag-Eigenschaft hinzufügen.


[Weiter: ](configure-identities.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
