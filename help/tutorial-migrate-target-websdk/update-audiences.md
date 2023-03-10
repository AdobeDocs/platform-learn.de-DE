---
title: Zielgruppen und Profilskripte aktualisieren | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Adobe Target-Zielgruppen und Profilskripte aktualisieren können, um die Kompatibilität mit dem Experience Platform Web SDK zu gewährleisten.
source-git-commit: 287ebcb275c4fca574dbd6cdf7e07ba4268bddb5
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Aktualisierung von Target-Zielgruppen und Profilskripten für die Platform Web SDK-Kompatibilität

Nach Abschluss der technischen Aktualisierungen für die Migration von Target zum Platform Web SDK müssen Sie möglicherweise einige Ihrer Zielgruppen, Profilskripte und Aktivitäten aktualisieren, um einen reibungslosen Übergang zu gewährleisten.

Alle Target-Mbox-Parameter müssen im XDM-Format mit einer Platform Web SDK-Implementierung übergeben werden. Bevor Sie Ihre Änderungen in der Produktion veröffentlichen, sollten Sie:

* Zielgruppen aktualisieren, die Mbox-Parameter verwenden
* Profilskripte aktualisieren, die Mbox-Parameter verwenden
* Aktualisieren Sie alle Angebote und Aktivitäten, indem Sie die Ersetzung des Mbox-Parameter-Tokens verwenden (z. B. `${mbox.parameter_name}`)

## Zielgruppen anpassen

Alle Zielgruppen, die benutzerdefinierte Mbox-Parameter verwenden, sollten aktualisiert werden, um die neuen XDM-Parameternamen zu verwenden. Beispiel: ein benutzerdefinierter Parameter für `page_name` wahrscheinlich `web.webpagedetails.pageName`.

Um die Kompatibilität mit at.js und Platform Web SDK sicherzustellen, müssen alle relevanten Zielgruppen aktualisiert werden, damit `OR` -Bedingungen verwendet werden, wie unten dargestellt:

![Anzeigen der Aktualisierung einer Target-Zielgruppe für die Platform Web SDK-Kompatibilität](assets/target-audience-update.png){zoomable=&quot;yes&quot;}

## Profilskripte bearbeiten

Profilskripte sollten aktualisiert werden, um auf neue XDM-Parameternamen zu verweisen, ähnlich wie bei Zielgruppen. Abgesehen von der Änderung der Mbox-Parameternamen gibt es keinen Unterschied in der Funktionsweise von Profilskripten zwischen einer at.js- und einer Platform Web SDK-Implementierung.

Ein Ansatz, um sicherzustellen, dass Kompatibilität verwendet wird `OR` Bedingungen in Ihrem Profilskriptcode.

Beispielprofilskript:

```Javascript
if(mbox.param('pageName') == 'Product Details'){
  return true
}
```

Profilskript zur Kompatibilität mit dem Platform Web SDK aktualisiert:

```Javascript
if((mbox.param('pageName') == 'Product Details') || (mbox.param('web.webPageDetails.pageName') =='Product Details')){
  return true
}
```

Weitere Informationen und Best Practices finden Sie im entsprechenden Handbuch zu [Profilskripte](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/profile-parameters.html).

## Parameter-Token für dynamischen Inhalt aktualisieren

Wenn Sie über Angebote, Empfehlungsentwürfe oder Aktivitäten verfügen, die [Dynamischer Content-Ersatz](https://experienceleague.adobe.com/docs/target/using/experiences/offers/passing-profile-attributes-to-the-html-offer.html), müssen sie möglicherweise entsprechend aktualisiert werden, um die neuen XDM-Parameternamen zu berücksichtigen.

Je nachdem, wie Sie die Token-Ersetzung für Mbox-Parameter verwenden, können Sie Ihre vorhandene Einrichtung verbessern, um sowohl alte als auch neue Parameternamen zu berücksichtigen. In Situationen, in denen benutzerdefinierter JavaScript-Code nicht möglich ist, wie z. B. in JSON-Angeboten, sollten Sie jedoch Kopien erstellen und Aktualisierungen vornehmen, nachdem die Migration abgeschlossen ist und auf Ihrer Produktionswebsite live ist.

JSON-Beispielangebot:

```JSON
{
  "pageName" : "${mbox.page_name}",
  "layoutVariation" : "grid"
}
```

Beispiel für ein JSON-Angebot mit Parameternamen des Platform Web SDK:

```JSON
{
  "pageName" : "${mbox.web.webPagedDetails.pageName}",
  "layoutVariation" : "grid"
}
```

Wenn Sie nach der Migration Anpassungen vornehmen möchten, um die neuen XDM-Mbox-Parameternamen zu berücksichtigen, stellen Sie sicher, dass Sie alle betroffenen Aktivitäten während des Migrationsereignisses anhalten, um Aktivitätsanzeigefehler für Besucher zu vermeiden.

Als Nächstes erfahren Sie, wie Sie [Validieren der Target-Implementierung](validate.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).