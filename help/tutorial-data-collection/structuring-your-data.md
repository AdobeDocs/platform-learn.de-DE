---
title: Daten strukturieren
description: Daten strukturieren
exl-id: 8d176389-25a4-4718-afff-efd2f87204ed
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Daten strukturieren

Unternehmen haben ihre eigene Sprache, um über ihre Domain zu kommunizieren. Autohändler handeln von Marken, Modellen und Zylindern. Die Fluggesellschaften kümmern sich um Flugnummern, Serviceklasse und Sitzzuweisungen. Einige dieser Begriffe beziehen sich ausschließlich auf ein bestimmtes Unternehmen, einige werden von einem vertikalen Markt übernommen, andere werden von fast allen Unternehmen übernommen. Für Begriffe, die von einem vertikalen oder sogar weiter gefassten Sektor gemeinsam verwendet werden, können Sie mit Ihren Daten leistungsstarke Dinge tun, wenn Sie diese Begriffe auf gemeinsame Weise benennen und strukturieren.

Viele Unternehmen bearbeiten beispielsweise Bestellungen. Was wäre, wenn diese Unternehmen gemeinsam beschlossen hätten, eine Bestellung auf ähnliche Weise zu modellieren? Wenn das Datenmodell beispielsweise aus einem Objekt mit einer `priceTotal` Eigenschaft, die den Gesamtpreis der Bestellung darstellt? Was passiert, wenn dieses Objekt auch Eigenschaften mit dem Namen `currencyCode` und `purchaseOrderNumber`? Vielleicht enthält das Bestellobjekt eine Eigenschaft mit dem Namen `payments` das eine Reihe von Zahlungsobjekten wäre. Jedes Objekt würde eine Zahlung für die Bestellung darstellen. Vielleicht hat ein Kunde zum Beispiel einen Teil der Bestellung mit einer Geschenkkarte bezahlt und den Rest mit einer Kreditkarte bezahlt. Sie können damit beginnen, ein Modell zu erstellen, das ungefähr so aussieht:

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

Wenn sich alle Unternehmen, die mit Bestellungen arbeiten, dazu entschlossen haben, ihre Auftragsdaten konsistent für Begriffe zu modellieren, die in der Branche gängig sind, könnten magische Dinge eintreten. Informationen können innerhalb und außerhalb Ihrer Organisation fließender ausgetauscht werden, anstatt die Daten (Props und eVars, andere?) ständig zu interpretieren und zu übersetzen. Das maschinelle Lernen könnte leichter verstehen, was Ihre Daten enthalten. _bedeutet_ und liefern umsetzbare Einblicke. Benutzeroberflächen zum Aufdecken relevanter Daten könnten intuitiver werden. Ihre Daten können nahtlos mit Partnern und Anbietern integriert werden, die demselben Modell folgen.

## XDM

Dies ist das Ziel der Adobe [Experience-Datenmodell](https://business.adobe.com/products/experience-platform/experience-data-model.html). XDM bietet eine präskriptive Modellierung für Daten, die in der Branche häufig vorkommen, und ermöglicht Ihnen gleichzeitig, das Modell für Ihre spezifischen Anforderungen zu erweitern. Adobe Experience Platform basiert auf XDM und daher müssen Daten, die an Experience Platform gesendet werden, in XDM gespeichert werden. Anstatt darüber nachzudenken, wo und wie Sie Ihre aktuellen Datenmodelle in XDM umwandeln können, bevor Sie die Daten an Experience Platform senden, sollten Sie XDM in Ihrem gesamten Unternehmen umfassender einsetzen, damit nur selten Übersetzungen vorgenommen werden müssen.

[Weiter: ](configure-the-server/create-a-schema.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit in das Erlernen der Datenerfassung investiert haben. Wenn Sie Fragen haben, ein allgemeines Feedback teilen möchten oder Vorschläge zu künftigen Inhalten haben, teilen Sie diese bitte mit. [Diskussionsbeitrag der Experience League](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
