---
title: Aktualisieren von Audiences und Profilskripten - Migrieren von Target aus at.js 2.x nach Web SDK
description: Erfahren Sie, wie Sie Adobe Target-Zielgruppen und Profilskripte aktualisieren können, um die Kompatibilität mit Experience Platform Web SDK zu gewährleisten.
exl-id: 2c0f85f7-6e8c-4d0b-8ed5-53897d06e563
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Aktualisieren von Target-Zielgruppen und Profilskripten für die Kompatibilität mit Platform Web SDK

Nach Abschluss der technischen Updates für die Migration von Target auf Platform Web SDK müssen Sie möglicherweise einige Ihrer Zielgruppen, Profilskripte und Aktivitäten aktualisieren, um einen reibungslosen Übergang sicherzustellen.

Alle Target-Mbox-Parameter müssen mit einer Platform Web SDK-Implementierung im XDM-Format übergeben werden. Bevor Sie Ihre Änderungen in der Produktionsumgebung veröffentlichen, sollten Sie:

* Aktualisieren von Zielgruppen, die Mbox-Parameter verwenden
* Aktualisieren von Profilskripten, die Mbox-Parameter verwenden
* Aktualisieren von Angeboten und Aktivitäten mit Ersetzung des Mbox-Parameter-Tokens (z. B. `${mbox.parameter_name}`)

## Zielgruppen anpassen

Alle Zielgruppen, die benutzerdefinierte Mbox-Parameter verwenden, sollten so aktualisiert werden, dass sie die neuen XDM-Parameternamen verwenden. Beispielsweise würde wahrscheinlich ein benutzerdefinierter Parameter für `page_name` `web.webpagedetails.pageName` zugeordnet.

Um die Kompatibilität mit at.js und Platform Web SDK sicherzustellen, sollten Sie beispielsweise alle relevanten Zielgruppen aktualisieren, sodass `OR` Bedingungen verwendet werden, wie unten dargestellt:

![Anzeigen und Aktualisieren einer Target-Zielgruppe für die Kompatibilität mit Platform Web SDK](assets/target-audience-update.png){zoomable="yes"}

## Profilskripte bearbeiten

Profilskripte sollten aktualisiert werden, um auf neue XDM-Parameternamen zu verweisen, die den Audiences ähneln. Abgesehen von der Änderung der Mbox-Parameternamen gibt es keinen Unterschied in der Funktionsweise von Profilskripten zwischen einer at.js- und einer Platform Web SDK-Implementierung.

Um die Kompatibilität sicherzustellen, sollten Sie `OR` Bedingungen in Ihrem Profilskript-Code verwenden.

Beispiel für ein Profilskript:

```Javascript
if(mbox.param('pageName') == 'Product Details'){
  return true
}
```

Das Profilskript für die Kompatibilität mit Platform Web SDK wurde aktualisiert:

```Javascript
if((mbox.param('pageName') == 'Product Details') || (mbox.param('web.webPageDetails.pageName') =='Product Details')){
  return true
}
```

Weitere Informationen und Best Practices finden Sie in der entsprechenden Dokumentation zu [Profilskripten](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/profile-parameters.html?lang=de).

## Aktualisieren von Parameter-Token für dynamische Inhalte

Wenn Sie über Angebote, Recommendations, Designs oder Aktivitäten verfügen, die [dynamische Inhaltsersetzung](https://experienceleague.adobe.com/docs/target/using/experiences/offers/passing-profile-attributes-to-the-html-offer.html?lang=de) verwenden, müssen diese möglicherweise entsprechend aktualisiert werden, um die neuen XDM-Parameternamen zu berücksichtigen.

Je nachdem, wie Sie die Token-Ersetzung für mbox-Parameter verwenden, können Sie Ihre vorhandene Einrichtung möglicherweise erweitern, um sowohl alte als auch neue Parameternamen zu berücksichtigen. In Situationen, in denen benutzerdefinierter JavaScript-Code nicht möglich ist, z. B. in JSON-Angeboten, sollten Sie jedoch nach Abschluss der Migration Kopien erstellen und Aktualisierungen vornehmen und diese auf Ihrer Produktions-Site live schalten.

Beispiel eines JSON-Angebots:

```JSON
{
  "pageName" : "${mbox.page_name}",
  "layoutVariation" : "grid"
}
```

Beispiel für ein JSON-Angebot mit Platform Web SDK-Parameternamen:

```JSON
{
  "pageName" : "${mbox.web.webPagedDetails.pageName}",
  "layoutVariation" : "grid"
}
```

Wenn Sie nach der Migration Anpassungen vornehmen möchten, um die neuen XDM-Mbox-Parameternamen zu berücksichtigen, achten Sie darauf, alle betroffenen Aktivitäten während des Migrationsereignisses anzuhalten, um Fehler bei der Aktivitätsanzeige für Besucher zu vermeiden.

Erfahren Sie als Nächstes, wie [ die Target-Implementierung validieren](validate.md).

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=de#M463) posten.
