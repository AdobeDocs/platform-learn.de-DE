---
title: Erstellen eines XDM-Schemas für Web-Daten
description: Erfahren Sie, wie Sie in der Datenerfassungsoberfläche ein XDM-Schema für Web-Daten erstellen. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Schemas
jira: KT-15398
exl-id: 2858ce03-4f95-43ac-966c-1b647b33ef16
source-git-commit: 7ccbaaf4db43921f07c971c485e1460a1a7f0334
workflow-type: tm+mt
source-wordcount: '1541'
ht-degree: 3%

---

# Erstellen eines XDM-Schemas für Web-Daten

Erfahren Sie, wie Sie ein XDM-Schema für Web-Daten in der Datenerfassungsoberfläche von Adobe Experience Platform erstellen.

Experience-Datenmodell-Schemas (XDM) sind die Bausteine, Grundsätze und Best Practices für die Datenerfassung in Adobe Experience Platform.

Platform Web SDK verwendet Ihr Schema, um Ihre Web-Ereignisdaten zu standardisieren, an Platform Edge Network zu senden und letztendlich an alle im Datenstrom konfigurierten Experience Cloud-Anwendungen zu übermitteln. Dieser Schritt ist wichtig, da er ein Standarddatenmodell definiert, das für die Aufnahme von Kundenerlebnisdaten in Experience Platform erforderlich ist, und nachgelagerte Services und Anwendungen ermöglicht, die auf diesen Standards basieren.

>[!NOTE]
>
>Ein XDM-Schema ist _nicht erforderlich_ um Adobe Analytics, Adobe Target oder Adobe Audience Manager mit Web SDK zu implementieren (Daten können im `data`-Objekt anstelle des `xdm`-Objekts übergeben werden, wie Sie später sehen werden). Für die leistungsfähigsten Implementierungen plattformnativer Anwendungen wie Journey Optimizer, Real-Time Customer Data Platform und Customer Journey Analytics ist ein XDM-Schema erforderlich. Sie können sich zwar entscheiden, kein XDM-Schema in Ihrer eigenen Implementierung zu verwenden, dies wird jedoch im Rahmen dieses Tutorials erwartet.

## Warum sollten die Daten modelliert werden?

Unternehmen haben ihre eigene Sprache für die Kommunikation über ihren Bereich. Autohäuser beschäftigen sich mit Marken, Modellen und Zylindern. Fluggesellschaften kümmern sich um Flugnummern, Serviceklasse und Sitzplatzzuweisungen. Einige dieser Begriffe beziehen sich ausschließlich auf ein bestimmtes Unternehmen, andere werden in vertikalen Branchen verwendet und wieder andere werden von fast allen Unternehmen verwendet. Für Begriffe, die in einer vertikalen Branche verwendet werden oder sogar noch weiter gefasst sind, können Sie in Ihren Daten bereits viele wichtige Funktionen übernehmen, wenn Sie diese Begriffe gemeinsam benennen und strukturieren.

Viele Unternehmen bearbeiten beispielsweise Bestellungen. Was wäre, wenn diese Unternehmen gemeinsam beschließen, eine Bestellung auf ähnliche Weise zu modellieren? Was wäre beispielsweise, wenn das Datenmodell aus einem Objekt mit einer `priceTotal` besteht, die den Gesamtpreis der Bestellung darstellt? Was wäre, wenn dieses Objekt auch Eigenschaften mit den Namen `currencyCode` und `purchaseOrderNumber` hätte? Möglicherweise enthält das Bestellobjekt eine Eigenschaft mit dem Namen `payments`, die ein Array von Zahlungsobjekten wäre. Jedes Objekt würde eine Zahlung für die Bestellung darstellen. Vielleicht hat ein Kunde einen Teil der Bestellung mit einer Geschenkkarte bezahlt und der Rest mit einer Kreditkarte. Sie können mit dem Erstellen eines Modells beginnen, das in etwa wie folgt aussieht:

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

Wenn sich alle Unternehmen, die mit Bestellungen zu tun haben, dafür entscheiden würden, ihre Auftragsdaten konsistent nach branchenüblichen Begriffen zu modellieren, könnten magische Dinge passieren. Informationen können innerhalb und außerhalb Ihres Unternehmens flüssiger ausgetauscht werden, anstatt die Daten ständig zu interpretieren und zu übersetzen (Props und eVars, irgendjemand?). Maschinelles Lernen könnte leichter verstehen, was Ihre Daten _bedeuten_ und umsetzbare Einblicke bieten. Die Benutzeroberflächen zum Aufdecken relevanter Daten könnten intuitiver werden. Ihre Daten können nahtlos mit Partnern und Anbietern integriert werden, die dieselbe Modellierung verfolgen.

Dies ist das Ziel des [Experience-Datenmodells](https://business.adobe.com/products/experience-platform/experience-data-model.html) von Adobe. XDM bietet eine präskriptive Datenmodellierung, die in der Branche üblich ist, und ermöglicht es Ihnen gleichzeitig, das Modell für Ihre spezifischen Anforderungen zu erweitern. Adobe Experience Platform basiert auf XDM und daher müssen in Experience Platform gesendete Daten in XDM gespeichert werden. Anstatt darüber nachzudenken, wo und wie Sie Ihre aktuellen Datenmodelle in XDM umwandeln können, bevor Sie die Daten an Experience Platform senden, sollten Sie eher in Betracht ziehen, XDM in Ihrem Unternehmen pervasiv anzuwenden, sodass Übersetzungen selten auftreten müssen.


>[!NOTE]
>
> Zu Demonstrationszwecken erstellen die Übungen in dieser Lektion ein Beispielschema zur Erfassung von Inhalten und Produkten, die von Kundinnen und Kunden auf der [Demo-Site von Luma) angesehen ](https://luma.enablementadobe.com/content/luma/us/en.html). Sie können diese Schritte zwar verwenden, um ein anderes Schema für Ihre eigenen Zwecke zu erstellen, es wird jedoch empfohlen, zunächst das Beispielschema zu erstellen, um mehr über die Funktionen des Schema-Editors zu erfahren.

Weitere Informationen zu XDM-Schemata finden Sie in der Wiedergabeliste [Modellieren Ihrer Kundenerlebnisdaten mit XDM](https://experienceleague.adobe.com/en/playlists/experience-platform-model-your-customer-experience-data-with-xdm) oder in der [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home).

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen eines XDM-Schemas über die Datenerfassungsoberfläche
* Hinzufügen von Feldergruppen zu Ihrem XDM-Schema
* Erstellen von XDM-Schemata für Web-Ereignisdaten mithilfe von Best Practices

## Voraussetzungen

Alle erforderlichen Bereitstellungs- und Benutzerberechtigungen für die Datenerfassung und Adobe Experience Platform, die auf der Seite [Übersicht](overview.md) beschrieben werden.

## Erstellen eines XDM-Schemas

XDM-Schemata sind die Standardmethode zur Beschreibung von Daten in Experience Platform. Dadurch können alle Daten, die den Schemata entsprechen, innerhalb einer Organisation ohne Konflikte wiederverwendet oder sogar von mehreren Organisationen gemeinsam genutzt werden. Weitere Informationen finden Sie unter [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition).

In dieser Übung erstellen Sie ein XDM-Schema mit den empfohlenen grundlegenden Feldergruppen für die Erfassung von Web-Ereignisdaten auf der [Demo-Site von Luma](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"}:

1. Öffnen Sie die [Datenerfassungsschnittstelle](https://experience.adobe.com/data-collection/){target="_blank"}
1. Stellen Sie sicher, dass Sie sich in der richtigen Sandbox befinden. Suchen Sie die Sandbox in der oberen rechten Ecke

   >[!NOTE]
   >
   >Wenn Sie Kunde eines plattformbasierten Programms wie Real-Time CDP oder Journey Optimizer sind, empfehlen wir, für dieses Tutorial eine Entwicklungs-Sandbox zu verwenden. Andernfalls verwenden Sie die **[!UICONTROL Prod]**-Sandbox.

1. Navigieren Sie **[!UICONTROL linken Navigationsbereich]** Schemata“.
1. Klicken Sie auf **[!UICONTROL Schaltfläche]** Schema erstellen“ oben rechts

   ![Schema erstellen](assets/schema-xdm-create-schema.png)
1. Wählen **[!UICONTROL Erlebnisereignis]** im folgenden Bildschirm aus.
1. Wählen Sie **[!UICONTROL Weiter]**

   ![Schema Experience Event](assets/schema-experience-event.png)

1. Geben Sie den Namen für Ihr Schema im Feld **[!UICONTROL Anzeigename des Schemas]** ein, in diesem Fall `Luma Web Event Data`

   >[!TIP]
   >
   >Eine gängige Namenskonvention für XDM-Schemata besteht darin, das Schema nach der Quelle der Daten zu benennen.


1. Wählen Sie Beenden aus

   ![Beendigung des Schema-Erlebnisereignisses](assets/schema-name-schema.png)

## Feldergruppen hinzufügen

Wie bereits erwähnt, ist XDM das zentrale Framework, das Kundenerlebnisdaten standardisiert, indem gemeinsame Strukturen und Definitionen für nachgelagerte Adobe Experience Platform-Services bereitgestellt werden. Durch die Einhaltung von XDM-Standards _alle Kundenerlebnisdaten_ in eine gemeinsame Darstellung integriert werden. Mit diesem Ansatz können Sie wertvolle Einblicke aus Kundenaktionen gewinnen, Zielgruppen mithilfe von Segmenten definieren und Kundenattribute für Personalisierungszwecke mithilfe von Daten aus verschiedenen Quellen ausdrücken. Weitere Informationen finden [ unter „Best Practices ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/best-practices) Datenmodellierung“.

Wenn möglich, wird empfohlen, vorhandene Feldergruppen zu verwenden und ein produktunabhängiges Modell und Namenskonventionen einzuhalten. Für alle unternehmensspezifischen Daten, die nicht zu den oben vordefinierten Feldergruppen passen, können Sie eine benutzerdefinierte Feldergruppe erstellen. Unter [Erstellen eines Schemas mit dem Schema-Editor](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui#create) finden Sie detailliertere Schritte zu benutzerdefinierten Schemata.

>[!TIP]
> 
>In dieser Übung fügen Sie die empfohlenen vordefinierten Feldergruppen für die Web-Datenerfassung hinzu: _**[!UICONTROL AEP Web SDK ExperienceEvent]**_ und _**[!UICONTROL Consumer Experience Event]**_.
>


1. Wählen Sie im **[!UICONTROL Feldergruppen]** die Option &quot;**[!UICONTROL &quot;]**

   ![Neue Feldergruppe](assets/schema-new-field-group.png)

1. Nach [!UICONTROL `AEP Web SDK ExperienceEvent`] suchen
1. Aktivieren Sie das Kontrollkästchen
1. Nach [!UICONTROL `Consumer Experience Event`] suchen
1. Aktivieren Sie das Kontrollkästchen
1. Wählen Sie **[!UICONTROL Feldergruppen hinzufügen]**

   ![Feldergruppe hinzufügen](assets/schema-add-field-group.png)

Beachten Sie bei beiden Feldergruppen, dass Sie Zugriff auf die am häufigsten verwendeten Schlüssel-Wert-Paare haben, die für die Datenerfassung im Web erforderlich sind. Der [!UICONTROL Anzeigename] jedes Felds wird Marketing-Experten in der Segment Builder-Benutzeroberfläche von Platform-basierten Programmen angezeigt. Sie können den Anzeigenamen von Standardfeldern Ihren Anforderungen entsprechend ändern. Sie können auch unerwünschte Felder entfernen. Wenn Sie auf einen der Feldergruppennamen klicken, wird in der Benutzeroberfläche hervorgehoben, zu welchen Schlüssel-Wert-Paargruppierungen sie gehören. Im folgenden Beispiel sehen Sie, welche Felder zu **[!UICONTROL Consumer Experience Event]** gehören.

![Schemafeldgruppen](assets/schema-consumer-experience-event.png)

Diese Lektion ist nur ein Anfang. Beim Erstellen eines eigenen Web-Ereignisschemas müssen Sie Ihre Geschäftsanforderungen untersuchen und dokumentieren. Dieser Prozess ähnelt dem Erstellen eines [Geschäftsanforderungsdokuments](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-a-business-requirements-document) und einer [Lösungs-Design-Referenz](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-and-maintaining-an-sdr) für eine Adobe Analytics-Implementierung, sollte jedoch Anforderungen für _alle nachgelagerten Datenempfänger_ wie Platform-, Target- und Ereignisweiterleitungsziele enthalten.


### Das identityMap-Objekt

Es gibt ein spezielles Feld namens `[!UICONTROL identityMap]`, das zur Identifizierung von Web-Benutzern verwendet wird.

![Luma-Web-Ereignisdaten](assets/schema-identityMap.png)

Es ist ein unverzichtbares Objekt für jede Web-bezogene Datenerfassung, da es die Experience Cloud-ID enthält, die zum Identifizieren von Benutzenden im Web erforderlich ist. Dies ist auch der Schlüssel zum Festlegen interner Kunden-IDs für authentifizierte Benutzer. `[!UICONTROL identityMap]` wird in der Lektion [Konfigurieren von Identitäten](configure-identities.md) näher erläutert. Sie wird mithilfe der Klasse **[!UICONTROL XDM ExperienceEvent]** automatisch in alle Schemas eingefügt.


>[!IMPORTANT]
>
> Es ist möglich, &quot;**[!UICONTROL &quot; für]** Schema zu aktivieren, bevor das Schema gespeichert wird. **Aktivieren Sie** jetzt nicht. Nachdem ein Schema für das Profil aktiviert wurde, kann es nicht mehr deaktiviert oder gelöscht werden, ohne dass die gesamte Sandbox zurückgesetzt wird. Felder können derzeit auch nicht aus Schemata entfernt werden, obwohl es möglich ist, Felder in der Benutzeroberfläche [ verwerfen](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/field-deprecation-ui#deprecate). Diese Auswirkungen sollten Sie später im Auge behalten, wenn Sie mit Ihren eigenen Daten in Ihrer Produktionsumgebung arbeiten.
>
>
>Diese Einstellung wird in der Lektion [Einrichten von Experience Platform](setup-experience-platform.md) näher erläutert.
>>![Profilschema](assets/schema-profile.png)

Um diese Lektion abzuschließen, wählen **[!UICONTROL oben]** auf „Speichern“.

![Schema speichern](assets/schema-select-save.png)


Jetzt können Sie auf dieses Schema verweisen, wenn Sie die Web SDK-Erweiterung zu Ihrer Tag-Eigenschaft hinzufügen.

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
