---
title: Aktualisierung von Zielgruppen und Profilskripten - Migration von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Adobe Target-Zielgruppen und Profilskripte aktualisieren können, um die Kompatibilität mit dem Experience Platform Web SDK zu gewährleisten.
exl-id: 2c0f85f7-6e8c-4d0b-8ed5-53897d06e563
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Aktualisierung von Target-Zielgruppen und Profilskripten für die Platform Web SDK-Kompatibilität

Nach Abschluss der technischen Aktualisierungen für die Migration von Target zum Platform Web SDK müssen Sie möglicherweise einige Ihrer Zielgruppen, Profilskripte und Aktivitäten aktualisieren, um einen reibungslosen Übergang zu gewährleisten.

Alle Target-Mbox-Parameter müssen im XDM-Format mit einer Platform Web SDK-Implementierung übergeben werden. Bevor Sie Ihre Änderungen in der Produktion veröffentlichen, sollten Sie:

* Zielgruppen aktualisieren, die Mbox-Parameter verwenden
* Profilskripte aktualisieren, die Mbox-Parameter verwenden
* Aktualisieren Sie alle Angebote und Aktivitäten, die die Ersetzung des Mbox-Parameter-Tokens verwenden (z. B. `${mbox.parameter_name}`).

## Zielgruppen anpassen

Alle Zielgruppen, die benutzerdefinierte Mbox-Parameter verwenden, sollten aktualisiert werden, um die neuen XDM-Parameternamen zu verwenden. Beispielsweise würde ein benutzerdefinierter Parameter für `page_name` wahrscheinlich `web.webpagedetails.pageName` zugeordnet.

Um die Kompatibilität mit at.js und Platform Web SDK sicherzustellen, müssen alle relevanten Zielgruppen aktualisiert werden, damit `OR` -Bedingungen verwendet werden, wie unten dargestellt:

![Anzeigen der Aktualisierung einer Target-Zielgruppe für die Platform Web SDK-Kompatibilität](assets/target-audience-update.png){zoomable="yes"}

## Profilskripte bearbeiten

Profilskripte sollten aktualisiert werden, um auf neue XDM-Parameternamen zu verweisen, ähnlich wie bei Zielgruppen. Abgesehen von der Änderung der Mbox-Parameternamen gibt es keinen Unterschied in der Funktionsweise von Profilskripten zwischen einer at.js- und einer Platform Web SDK-Implementierung.

Eine Möglichkeit, um sicherzustellen, dass die Kompatibilität gewährleistet ist, besteht darin, `OR` -Bedingungen in Ihrem Profilskriptcode zu verwenden.

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

Weitere Informationen und Best Practices finden Sie in der entsprechenden Dokumentation zu [Profilskripten](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/profile-parameters.html).

## Parameter-Token für dynamischen Inhalt aktualisieren

Wenn Sie über Angebote, Empfehlungsentwürfe oder Aktivitäten verfügen, die den [dynamischen Inhaltsaustausch](https://experienceleague.adobe.com/docs/target/using/experiences/offers/passing-profile-attributes-to-the-html-offer.html) verwenden, müssen diese möglicherweise entsprechend aktualisiert werden, um die neuen XDM-Parameternamen zu berücksichtigen.

Je nachdem, wie Sie die Token-Ersetzung für Mbox-Parameter verwenden, können Sie Ihre vorhandene Einrichtung verbessern, um sowohl alte als auch neue Parameternamen zu berücksichtigen. In Situationen, in denen benutzerdefinierter JavaScript-Code nicht möglich ist, z. B. in JSON-Angeboten, sollten Sie jedoch Kopien erstellen und Aktualisierungen vornehmen, nachdem die Migration abgeschlossen ist und auf Ihrer Produktionswebsite live ist.

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

Als Nächstes erfahren Sie, wie Sie [die Target-Implementierung validieren](validate.md).

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
