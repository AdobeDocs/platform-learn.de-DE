---
title: Erstellen eines XDM-Schemas für Webdaten
description: Erfahren Sie, wie Sie in der Datenerfassungsoberfläche ein XDM-Schema für Webdaten erstellen. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Schemas
jira: KT-15398
exl-id: 2858ce03-4f95-43ac-966c-1b647b33ef16
source-git-commit: 1a4f2e3813a6db4bef77753525c8a7d40692a4b2
workflow-type: tm+mt
source-wordcount: '1542'
ht-degree: 3%

---

# Erstellen eines XDM-Schemas für Webdaten

Erfahren Sie, wie Sie ein XDM-Schema für Web-Daten in der Datenerfassungsoberfläche von Adobe Experience Platform erstellen.

Experience-Datenmodell (XDM)-Schemas sind die Bausteine, Grundsätze und Best Practices für die Datenerfassung in Adobe Experience Platform.

Das Platform Web SDK verwendet Ihr Schema zur Standardisierung Ihrer Web-Ereignisdaten, zum Senden an das Platform-Edge Network und schließlich zum Weiterleiten der Daten an alle im Datastream konfigurierten Experience Cloud-Anwendungen. Dieser Schritt ist wichtig, da er ein Standarddatenmodell definiert, das für die Aufnahme von Kundenerlebnisdaten in Experience Platform erforderlich ist, und nachgelagerte Dienste und Anwendungen ermöglicht, die auf diesen Standards basieren.

>[!NOTE]
>
>Ein XDM-Schema ist _nicht erforderlich_, um Adobe Analytics, Adobe Target oder Adobe Audience Manager mit dem Web SDK zu implementieren (Daten können im `data` -Objekt anstelle des `xdm` -Objekts übergeben werden, wie Sie später sehen werden). Ein XDM-Schema ist für die leistungsfähigsten Implementierungen plattformnativer Anwendungen wie Journey Optimizer, Real-time Customer Data Platform und Customer Journey Analytics erforderlich. Sie können sich zwar entscheiden, kein XDM-Schema in Ihrer eigenen Implementierung zu verwenden, doch wird davon ausgegangen, dass Sie dies im Rahmen dieses Tutorials tun.

## Warum modellieren die Daten?

Unternehmen haben ihre eigene Sprache, um über ihre Domain zu kommunizieren. Autohändler handeln von Marken, Modellen und Zylindern. Die Fluggesellschaften kümmern sich um Flugnummern, Serviceklasse und Sitzzuweisungen. Einige dieser Begriffe beziehen sich ausschließlich auf ein bestimmtes Unternehmen, einige werden von einem vertikalen Markt übernommen, andere werden von fast allen Unternehmen übernommen. Für Begriffe, die von einem vertikalen oder sogar weiter gefassten Sektor gemeinsam verwendet werden, können Sie mit Ihren Daten leistungsstarke Dinge tun, wenn Sie diese Begriffe auf gemeinsame Weise benennen und strukturieren.

Viele Unternehmen bearbeiten beispielsweise Bestellungen. Was wäre, wenn diese Unternehmen gemeinsam beschlossen hätten, eine Bestellung auf ähnliche Weise zu modellieren? Was wäre beispielsweise, wenn das Datenmodell aus einem Objekt mit einer `priceTotal` -Eigenschaft bestand, die den Gesamtpreis der Bestellung darstellte? Was passiert, wenn das Objekt auch Eigenschaften mit den Namen `currencyCode` und `purchaseOrderNumber` aufweist? Vielleicht enthält das Bestellobjekt eine Eigenschaft mit dem Namen `payments` , die ein Array von Zahlungsobjekten sein würde. Jedes Objekt würde eine Zahlung für die Bestellung darstellen. Vielleicht hat ein Kunde zum Beispiel einen Teil der Bestellung mit einer Geschenkkarte bezahlt und der Rest mit einer Kreditkarte. Sie können damit beginnen, ein Modell zu erstellen, das ungefähr so aussieht:

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

Wenn sich alle Unternehmen, die mit Bestellungen arbeiten, dazu entschlossen haben, ihre Auftragsdaten konsistent für Begriffe zu modellieren, die in der Branche gängig sind, könnten magische Dinge eintreten. Informationen können innerhalb und außerhalb Ihrer Organisation fließender ausgetauscht werden, anstatt die Daten (Props und eVars, andere?) ständig zu interpretieren und zu übersetzen. Das maschinelle Lernen könnte leichter verstehen, was Ihre Daten _bedeuten_, und praktische Einblicke bieten. Benutzeroberflächen zum Aufdecken relevanter Daten könnten intuitiver werden. Ihre Daten können nahtlos mit Partnern und Anbietern integriert werden, die demselben Modell folgen.

Dies ist das Ziel von Adobe [Erlebnisdatenmodell](https://business.adobe.com/products/experience-platform/experience-data-model.html). XDM bietet eine präskriptive Modellierung für Daten, die in der Branche häufig vorkommen, und ermöglicht Ihnen gleichzeitig, das Modell für Ihre spezifischen Anforderungen zu erweitern. Adobe Experience Platform basiert auf XDM und daher müssen Daten, die an Experience Platform gesendet werden, in XDM gespeichert werden. Anstatt darüber nachzudenken, wo und wie Sie Ihre aktuellen Datenmodelle in XDM umwandeln können, bevor Sie die Daten an Experience Platform senden, sollten Sie XDM in Ihrem gesamten Unternehmen umfassender einsetzen, damit nur selten Übersetzungen vorgenommen werden müssen.


>[!NOTE]
>
> Zu Demonstrationszwecken erstellen die Übungen in dieser Lektion ein Beispielschema, um die angezeigten Inhalte und die von Kunden auf der [Demosite &quot;Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html) gekauften Produkte zu erfassen. Sie können diese Schritte zwar verwenden, um ein anderes Schema für Ihre eigenen Zwecke zu erstellen, es wird jedoch empfohlen, zunächst das Beispielschema zu erstellen, um mehr über die Funktionen des Schema-Editors zu erfahren.

Weiterführende Informationen zu XDM-Schemata finden Sie im Kurs [Modellieren Ihrer Kundenerlebnisdaten mit XDM](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) oder in der [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home).

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen eines XDM-Schemas über die Datenerfassungsoberfläche
* Hinzufügen von Feldergruppen zu Ihrem XDM-Schema
* Erstellen von XDM-Schemata für Web-Ereignisdaten mithilfe von Best Practices

## Voraussetzungen

Alle erforderlichen Bereitstellungs- und Benutzerberechtigungen für die Datenerfassung und Adobe Experience Platform werden auf der Seite [Übersicht](overview.md) beschrieben.

## Erstellen eines XDM-Schemas

XDM-Schemata sind die Standardmethode zum Beschreiben von Daten auf Experience Platform, sodass alle Daten, die den Schemas entsprechen, in einer Organisation ohne Konflikte wiederverwendet oder sogar von mehreren Organisationen gemeinsam genutzt werden können. Weitere Informationen finden Sie in den [Grundlagen der Schema-Komposition](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition) .

In dieser Übung erstellen Sie ein XDM-Schema mit den empfohlenen Grundlinien-Feldgruppen zur Erfassung von Web-Ereignisdaten auf der [Luma Demo Site](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"}:

1. Öffnen Sie die [Datenerfassungsschnittstelle](https://launch.adobe.com/){target="_blank"} .
1. Vergewissern Sie sich, dass Sie sich in der richtigen Sandbox befinden. Suchen Sie die Sandbox in der oberen rechten Ecke.

   >[!NOTE]
   >
   >Wenn Sie Platform-basierte Anwendungen wie Real-Time CDP oder Journey Optimizer nutzen, empfehlen wir für dieses Tutorial die Verwendung einer Entwicklungs-Sandbox. Ist dies nicht der Fall, verwenden Sie die Sandbox **[!UICONTROL Prod]** .

1. Navigieren Sie im linken Navigationsbereich zu **[!UICONTROL Schemas]** .
1. Wählen Sie oben rechts die Schaltfläche **[!UICONTROL Schema erstellen]** aus.

   ![Schema erstellen](assets/schema-xdm-create-schema.png)
1. Wählen Sie im folgenden Bildschirm **[!UICONTROL Erlebnisereignis]** aus.
1. Wählen Sie **[!UICONTROL Weiter]**

   ![Schema-Erlebnisereignis](assets/schema-experience-event.png)

1. Geben Sie den Namen für Ihr Schema unter dem Feld **[!UICONTROL Anzeigename des Schemas]** ein, in diesem Fall `Luma Web Event Data`

   >[!TIP]
   >
   >Eine gängige Benennungskonvention für XDM-Schemas besteht darin, das Schema nach der Datenquelle zu benennen.


1. Wählen Sie Beenden

   ![Schema-Erlebnisereignis-Finsh](assets/schema-name-schema.png)

## Feldergruppen hinzufügen

Wie bereits erwähnt, ist XDM das zentrale Framework, das Kundenerlebnisdaten durch Bereitstellung gemeinsamer Strukturen und Definitionen für nachgelagerte Adobe Experience Platform-Dienste standardisiert. Durch Einhaltung von XDM-Standards können _alle Kundenerlebnisdaten_ in eine gemeinsame Darstellung integriert werden. Dieser Ansatz ermöglicht es Ihnen, wertvolle Einblicke aus Kundenaktionen zu gewinnen, Kundenzielgruppen über Segmente zu definieren und Kundenattribute für Personalisierungszwecke mithilfe von Daten aus verschiedenen Quellen auszudrücken. Weitere Informationen finden Sie unter [Best Practices für die Datenmodellierung](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/best-practices) .

Wenn möglich, wird empfohlen, vorhandene Feldergruppen zu verwenden und ein produktagnostisches Modell und Namenskonventionen einzuhalten. Für alle Daten, die spezifisch für Ihr Unternehmen sind und nicht in die vordefinierten Feldergruppen oben passen, können Sie eine benutzerdefinierte Feldergruppe erstellen. Detailliertere Schritte zu benutzerdefinierten Schemas finden Sie unter [Erstellen eines Schemas mit dem Schema-Editor](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui#create) .

>[!TIP]
> 
>In dieser Übung fügen Sie die empfohlenen vordefinierten Feldergruppen für die Web-Datenerfassung hinzu: _**[!UICONTROL AEP Web SDK ExperienceEvent]**_ und _**[!UICONTROL Consumer Experience Event]**_.
>


1. Wählen Sie im Abschnitt **[!UICONTROL Feldgruppen]** die Option **[!UICONTROL Hinzufügen]** aus.

   ![Neue Feldergruppe](assets/schema-new-field-group.png)

1. Suchen Sie nach [!UICONTROL `AEP Web SDK ExperienceEvent`]
1. Aktivieren Sie das Kontrollkästchen
1. Suchen Sie nach [!UICONTROL `Consumer Experience Event`]
1. Aktivieren Sie das Kontrollkästchen
1. Wählen Sie **[!UICONTROL Feldergruppen hinzufügen]** aus.

   ![Feldergruppe hinzufügen](assets/schema-add-field-group.png)

Beachten Sie bei beiden Feldergruppen, dass Sie Zugriff auf die am häufigsten verwendeten Schlüssel-Wert-Paare haben, die für die Datenerfassung im Internet erforderlich sind. Der [!UICONTROL Anzeigename] jedes Felds wird Marketing-Experten in der Segment Builder-Oberfläche von Platform-basierten Anwendungen angezeigt. Sie können den Anzeigenamen von Standardfeldern an Ihre Anforderungen anpassen. Sie können auch Felder entfernen, die Sie nicht möchten. Wenn Sie auf einen der Feldgruppennamen klicken, wird in der Benutzeroberfläche hervorgehoben, zu welchen Schlüssel-Wert-Paargruppierungen gehören. Im folgenden Beispiel sehen Sie, welche Felder zu **[!UICONTROL Consumer Experience Event]** gehören.

![Schemafeldgruppen](assets/schema-consumer-experience-event.png)

Diese Lektion ist nur ein Ausgangspunkt. Beim Erstellen Ihres eigenen Web-Ereignisschemas müssen Sie Ihre Geschäftsanforderungen untersuchen und dokumentieren. Dieser Vorgang ähnelt dem Erstellen eines [Geschäftsanforderungsdokuments](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-a-business-requirements-document) und der [Lösungsdesign-Referenz](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-and-maintaining-an-sdr) für eine Adobe Analytics-Implementierung. Er sollte jedoch Anforderungen für _alle nachgelagerten Datenempfänger_ enthalten, z. B. Ziele für die Plattform-, Target- und Ereignisweiterleitung.


### Das identityMap -Objekt

Es gibt ein spezielles Feld, das zur Identifizierung von Webbenutzern verwendet wird: `[!UICONTROL identityMap]`.

![Luma Web Event Data](assets/schema-identityMap.png)

Es handelt sich um ein &quot;must-have&quot;-Objekt für jede webbezogene Datenerfassung, da es die Experience Cloud-ID enthält, die zur Identifizierung von Benutzern im Internet erforderlich ist. Dies ist auch der Schlüssel zum Festlegen interner Kunden-IDs für authentifizierte Benutzer. `[!UICONTROL identityMap]` wird mehr in der Lektion [Identitäten konfigurieren](configure-identities.md) erläutert. Sie wird automatisch in alle Schemas aufgenommen, die die **[!UICONTROL XDM ExperienceEvent]** -Klasse verwenden.


>[!IMPORTANT]
>
> Es ist möglich, **[!UICONTROL Profil]** für ein Schema zu aktivieren, bevor Sie Ihr Schema speichern. **Aktivieren Sie sie an dieser Stelle nicht**. Nachdem ein Schema für Profil aktiviert wurde, kann es nicht mehr deaktiviert oder gelöscht werden, ohne die gesamte Sandbox zurückzusetzen. Auch Felder können zu diesem Zeitpunkt nicht aus Schemata entfernt werden. Es ist jedoch möglich, Felder in der Benutzeroberfläche ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/field-deprecation-ui#deprecate) nicht mehr zu verwenden. [ Diese Implikationen sollten Sie später bei der Arbeit mit Ihren eigenen Daten in Ihrer Produktionsumgebung berücksichtigen.
>
>
>Diese Einstellung wird während der Lektion [Setup-Experience Platform](setup-experience-platform.md) genauer besprochen.
>![Profilschema](assets/schema-profile.png)

Um diese Lektion abzuschließen, wählen Sie oben rechts **[!UICONTROL Speichern]** aus.

![Schema speichern](assets/schema-select-save.png)


Jetzt können Sie dieses Schema referenzieren, wenn Sie die Web SDK-Erweiterung zu Ihrer Tag-Eigenschaft hinzufügen.


[Weiter: ](configure-identities.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
