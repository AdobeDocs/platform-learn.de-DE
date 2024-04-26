---
title: Erstellen eines XDM-Schemas für Webdaten
description: Erfahren Sie, wie Sie in der Datenerfassungsoberfläche ein XDM-Schema für Webdaten erstellen. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Web SDK,Schemas
jira: KT-15398
exl-id: 2858ce03-4f95-43ac-966c-1b647b33ef16
source-git-commit: 8602110d2b2ddc561e45f201e3bcce5e6a6f8261
workflow-type: tm+mt
source-wordcount: '1498'
ht-degree: 1%

---

# Erstellen eines XDM-Schemas für Webdaten

Erfahren Sie, wie Sie ein XDM-Schema für Webdaten in der Datenerfassungsoberfläche von Adobe Experience Platform erstellen.

Experience-Datenmodell (XDM)-Schemas sind die Bausteine, Grundsätze und Best Practices für die Datenerfassung in Adobe Experience Platform.

Das Platform Web SDK verwendet Ihr Schema zur Standardisierung Ihrer Web-Ereignisdaten, zum Senden an das Platform-Edge Network und schließlich zum Weiterleiten der Daten an alle im Datastream konfigurierten Experience Cloud-Anwendungen. Dieser Schritt ist wichtig, da er ein Standarddatenmodell definiert, das für die Aufnahme von Kundenerlebnisdaten in Experience Platform erforderlich ist, und nachgelagerte Dienste und Anwendungen ermöglicht, die auf diesen Standards basieren.

## Warum modellieren die Daten?

Unternehmen haben ihre eigene Sprache, um über ihre Domain zu kommunizieren. Autohändler handeln von Marken, Modellen und Zylindern. Die Fluggesellschaften kümmern sich um Flugnummern, Serviceklasse und Sitzzuweisungen. Einige dieser Begriffe beziehen sich ausschließlich auf ein bestimmtes Unternehmen, einige werden von einem vertikalen Markt übernommen, andere werden von fast allen Unternehmen übernommen. Für Begriffe, die von einem vertikalen oder sogar weiter gefassten Sektor gemeinsam verwendet werden, können Sie mit Ihren Daten leistungsstarke Dinge tun, wenn Sie diese Begriffe auf gemeinsame Weise benennen und strukturieren.

Viele Unternehmen bearbeiten beispielsweise Bestellungen. Was wäre, wenn diese Unternehmen gemeinsam beschlossen hätten, eine Bestellung auf ähnliche Weise zu modellieren? Wenn das Datenmodell beispielsweise aus einem Objekt mit einer `priceTotal` Eigenschaft, die den Gesamtpreis der Bestellung darstellt? Was passiert, wenn dieses Objekt auch Eigenschaften namens `currencyCode` und `purchaseOrderNumber`? Vielleicht enthält das Bestellobjekt eine Eigenschaft mit dem Namen `payments` das eine Reihe von Zahlungsobjekten wäre. Jedes Objekt würde eine Zahlung für die Bestellung darstellen. Vielleicht hat ein Kunde zum Beispiel einen Teil der Bestellung mit einer Geschenkkarte bezahlt und der Rest mit einer Kreditkarte. Sie können damit beginnen, ein Modell zu erstellen, das ungefähr so aussieht:

```json
{
  "order": {
    "priceTotal": 89.50,
    "currencyCode": "EUR",
    "purchaseOrderNumber": "JWN20192388410012",
    "payments": [
      {
        "paymentType": "gift_card",
        "paymentAmount": 50
      },
      {
        "paymentType": "credit_card",
        "paymentAmount": 39.50
      }
    ]
  }
}
```

Wenn sich alle Unternehmen, die mit Bestellungen arbeiten, dazu entschlossen haben, ihre Auftragsdaten konsistent für Begriffe zu modellieren, die in der Branche gängig sind, könnten magische Dinge eintreten. Informationen können innerhalb und außerhalb Ihrer Organisation fließender ausgetauscht werden, anstatt die Daten (Props und eVars, andere?) ständig zu interpretieren und zu übersetzen. Das maschinelle Lernen könnte leichter verstehen, was Ihre Daten enthalten. _bedeutet_ und bieten praktische Einblicke. Benutzeroberflächen zum Aufdecken relevanter Daten könnten intuitiver werden. Ihre Daten können nahtlos mit Partnern und Anbietern integriert werden, die demselben Modell folgen.

Dies ist das Ziel von Adobe [Experience-Datenmodell](https://business.adobe.com/products/experience-platform/experience-data-model.html). XDM bietet eine präskriptive Modellierung für Daten, die in der Branche häufig vorkommen, und ermöglicht Ihnen gleichzeitig, das Modell für Ihre spezifischen Anforderungen zu erweitern. Adobe Experience Platform basiert auf XDM und daher müssen Daten, die an Experience Platform gesendet werden, in XDM gespeichert werden. Anstatt darüber nachzudenken, wo und wie Sie Ihre aktuellen Datenmodelle in XDM umwandeln können, bevor Sie die Daten an Experience Platform senden, sollten Sie XDM in Ihrem gesamten Unternehmen umfassender einsetzen, damit nur selten Übersetzungen vorgenommen werden müssen.


>[!NOTE]
>
> Zu Demonstrationszwecken erstellen die Übungen in dieser Lektion ein Beispielschema, um angesehene Inhalte und Produkte zu erfassen, die von Kunden im [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html). Sie können diese Schritte zwar verwenden, um ein anderes Schema für Ihre eigenen Zwecke zu erstellen, es wird jedoch empfohlen, zunächst das Beispielschema zu erstellen, um mehr über die Funktionen des Schema-Editors zu erfahren.

Um mehr über XDM-Schemas zu erfahren, gehen Sie zum Kurs [Modellieren Ihrer Kundenerlebnisdaten mit XDM](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) oder sehen Sie [XDM-System - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home).

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen eines XDM-Schemas über die Datenerfassungsoberfläche
* Hinzufügen von Feldergruppen zu Ihrem XDM-Schema
* Erstellen von XDM-Schemata für Web-Ereignisdaten mithilfe von Best Practices

## Voraussetzungen

Alle erforderlichen Bereitstellungs- und Benutzerberechtigungen für die Datenerfassung und Adobe Experience Platform werden im Abschnitt [Übersicht](overview.md) Seite.

## Erstellen eines XDM-Schemas

XDM-Schemata sind die Standardmethode zum Beschreiben von Daten auf Experience Platform, sodass alle Daten, die den Schemas entsprechen, in einer Organisation ohne Konflikte wiederverwendet oder sogar von mehreren Organisationen gemeinsam genutzt werden können. Weitere Informationen finden Sie unter [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition).

In dieser Übung erstellen Sie ein XDM-Schema mit den empfohlenen Grundfeldgruppen für die Erfassung von Webereignisdaten auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"}:

1. Öffnen Sie die [Datenerfassungsoberfläche](https://launch.adobe.com/){target="_blank"}
1. Vergewissern Sie sich, dass Sie sich in der richtigen Sandbox befinden. Suchen Sie die Sandbox in der oberen rechten Ecke.

   >[!NOTE]
   >
   >Wenn Sie Platform-basierte Anwendungen wie Real-Time CDP oder Journey Optimizer nutzen, empfehlen wir für dieses Tutorial die Verwendung einer Entwicklungs-Sandbox. Wenn nicht, verwenden Sie die **[!UICONTROL Prod]** Sandbox.

1. Navigieren Sie zu **[!UICONTROL Schemas]** in der linken Navigation
1. Wählen Sie die **[!UICONTROL Schema erstellen]** Schaltfläche oben rechts

   ![Schema erstellen](assets/schema-xdm-create-schema.png)
1. Auswählen **[!UICONTROL Erlebnisereignis]** im folgenden Bildschirm
1. Auswählen **[!UICONTROL Nächste]**

   ![Schema-Erlebnisereignis](assets/schema-experience-event.png)

1. Geben Sie den Namen für Ihr Schema unter ein. **[!UICONTROL Anzeigename des Schemas]** -Feld, in diesem Fall `Luma Web Event Data`

   >[!TIP]
   >
   >Eine gängige Benennungskonvention für XDM-Schemas besteht darin, das Schema nach der Datenquelle zu benennen.


1. Wählen Sie Beenden

   ![Schema-Erlebnisereignis-Finsen](assets/schema-name-schema.png)

## Feldergruppen hinzufügen

Wie bereits erwähnt, ist XDM das zentrale Framework, das Kundenerlebnisdaten durch Bereitstellung gemeinsamer Strukturen und Definitionen für nachgelagerte Adobe Experience Platform-Dienste standardisiert. Durch Einhaltung von XDM-Standards _alle Kundenerlebnisdaten_ in eine gemeinsame Vertretung aufgenommen werden. Dieser Ansatz ermöglicht es Ihnen, wertvolle Einblicke aus Kundenaktionen zu gewinnen, Kundenzielgruppen über Segmente zu definieren und Kundenattribute für Personalisierungszwecke mithilfe von Daten aus verschiedenen Quellen auszudrücken. Siehe [Best Practices für die Datenmodellierung](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/best-practices) für weitere Informationen.

Wenn möglich, wird empfohlen, vorhandene Feldergruppen zu verwenden und ein produktagnostisches Modell und Namenskonventionen einzuhalten. Für alle Daten, die spezifisch für Ihr Unternehmen sind und nicht in die vordefinierten Feldergruppen oben passen, können Sie eine benutzerdefinierte Feldergruppe erstellen. Siehe [Erstellen eines Schemas mit dem Schema Editor](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui#create) für detailliertere Schritte zu benutzerdefinierten Schemas.

>[!TIP]
> 
>In dieser Übung fügen Sie die empfohlenen vordefinierten Feldergruppen für die Web-Datenerfassung hinzu: _**[!UICONTROL AEP Web SDK ExperienceEvent]**_ und _**[!UICONTROL Ereignis für Kundenerlebnisse]**_.
>
>
> Wenn Sie nur **Adobe Analytics** mit Web SDK und Senden von Daten an **Experience Platform**, verwenden Sie die [!UICONTROL Adobe Analytics ExperienceEvent-Vorlage] Feldergruppe, um das XDM-Schema zu definieren. Dies wird im [Einrichten von Analytics](setup-analytics.md) Lektion.

1. Im **[!UICONTROL Feldergruppen]** Bereich, wählen Sie **[!UICONTROL Hinzufügen]**

   ![Neue Feldergruppe](assets/schema-new-field-group.png)

1. Suchen Sie nach [!UICONTROL `AEP Web SDK ExperienceEvent`].
1. Aktivieren Sie das Kontrollkästchen
1. Suchen Sie nach [!UICONTROL `Consumer Experience Event`].
1. Aktivieren Sie das Kontrollkästchen
1. Auswählen **[!UICONTROL Feldergruppen hinzufügen]**

   ![Feldergruppe hinzufügen](assets/schema-add-field-group.png)

Beachten Sie bei beiden Feldergruppen, dass Sie Zugriff auf die am häufigsten verwendeten Schlüssel-Wert-Paare haben, die für die Datenerfassung im Internet erforderlich sind. Die [!UICONTROL Anzeigename] für Marketing-Experten in der Segment Builder-Oberfläche von Platform-basierten Anwendungen angezeigt werden und Sie können den Anzeigenamen von Standardfeldern an Ihre Anforderungen anpassen. Sie können auch Felder entfernen, die Sie nicht möchten. Wenn Sie auf einen der Feldgruppennamen klicken, wird in der Benutzeroberfläche hervorgehoben, zu welchen Schlüssel-Wert-Paargruppierungen gehören. Im folgenden Beispiel sehen Sie, zu welchen Feldern gehören **[!UICONTROL Ereignis für Kundenerlebnisse]**.

![Schemafeldgruppen](assets/schema-consumer-experience-event.png)

Diese Lektion ist nur ein Ausgangspunkt. Beim Erstellen Ihres eigenen Web-Ereignisschemas müssen Sie Ihre Geschäftsanforderungen untersuchen und dokumentieren. Dieser Vorgang ähnelt dem Erstellen einer [Geschäftsanforderungsdokument](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-a-business-requirements-document) und [Lösungsdesign-Referenz](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-and-maintaining-an-sdr) für eine Adobe Analytics-Implementierung, sollte jedoch Anforderungen für _alle nachgelagerten Datenempfänger_ , wie z. B. Ziele für die Plattform-, Target- und Ereignisweiterleitung.


### Das identityMap -Objekt

Es gibt ein spezielles Feld zur Identifizierung von Webbenutzern, das `[!UICONTROL identityMap]`.

![Luma-Web-Ereignisdaten](assets/schema-identityMap.png)

Es handelt sich um ein &quot;must-have&quot;-Objekt für jede webbezogene Datenerfassung, da es die Experience Cloud-ID enthält, die zur Identifizierung von Benutzern im Internet erforderlich ist. Dies ist auch der Schlüssel zum Festlegen interner Kunden-IDs für authentifizierte Benutzer. `[!UICONTROL identityMap]` wird im Abschnitt [Identitäten konfigurieren](configure-identities.md) Lektion. Sie wird automatisch in alle Schemas mit der Variablen **[!UICONTROL XDM ExperienceEvent]** -Klasse.


>[!IMPORTANT]
>
> Es ist möglich **[!UICONTROL Profil]** für ein Schema vor dem Speichern des Schemas. **Nicht** aktivieren. Nachdem ein Schema für Profil aktiviert wurde, kann es nicht mehr deaktiviert oder gelöscht werden, ohne die gesamte Sandbox zurückzusetzen. Auch Felder können zu diesem Zeitpunkt nicht aus Schemata entfernt werden. Sie können jedoch [Veraltete Felder in der Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/field-deprecation-ui#deprecate). Diese Implikationen sollten Sie später bei der Arbeit mit Ihren eigenen Daten in Ihrer Produktionsumgebung berücksichtigen.
>
>
>Diese Einstellung wird während der [Einrichten von Experience Platform](setup-experience-platform.md) Lektion.
>![Profilschema](assets/schema-profile.png)

Um diese Lektion abzuschließen, wählen Sie **[!UICONTROL Speichern]** oben rechts.

![Schema speichern](assets/schema-select-save.png)


Jetzt können Sie dieses Schema referenzieren, wenn Sie die Web SDK-Erweiterung zu Ihrer Tag-Eigenschaft hinzufügen.


[Weiter: ](configure-identities.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
