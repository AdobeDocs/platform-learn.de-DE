---
title: 'Aktualisieren von Target-Zielgruppen und Profilskripten : Migrieren der Adobe Target-Implementierung in Ihrer Mobile App zur Offer Decisioning- und Target-Erweiterung'
description: Erfahren Sie, wie Sie Adobe Target-Zielgruppen und Profilskripte aktualisieren können, um die Kompatibilität mit der Offer Decisioning- und Target-Erweiterung sicherzustellen.
exl-id: de3ce2c7-0066-496a-a8a7-994d7ce3d92c
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# Aktualisieren von Target-Zielgruppen und Profilskripten für die Kompatibilität der Erweiterungen für Mobile Decisioning


Nach Abschluss der technischen Aktualisierungen für die Migration von Target zur Offer Decisioning- und Target-Erweiterung müssen Sie möglicherweise einige Ihrer Zielgruppen, Profilskripte und Aktivitäten aktualisieren, um einen reibungslosen Übergang sicherzustellen.

>[!INFO]
>
>Wenn Sie alle Ihre Mbox-Parameter in das `data.__adobe.target` migrieren, müssen Sie Ihre Zielgruppen, Profilskripte und Aktivitäten nicht wie unten dargestellt aktualisieren.


Wenn Sie Mbox-Parameter in das `xdm` migrieren, bevor Sie Ihre Änderungen in der Produktion veröffentlichen, sollten Sie:

* Aktualisieren von Zielgruppen, die Mbox-Parameter verwenden
* Aktualisieren von Profilskripten, die Mbox-Parameter verwenden
* Aktualisieren von Angeboten und Aktivitäten mit Ersetzung des Mbox-Parameter-Tokens (z. B. `${mbox.parameter_name}`)

## Zielgruppen anpassen

Wenn Sie Mbox-Parameter in das `xdm`-Objekt migrieren, sollten Zielgruppen, die benutzerdefinierte Mbox-Parameter verwenden, so aktualisiert werden, dass sie die neuen XDM-Parameternamen verwenden. Beispielsweise würde wahrscheinlich ein benutzerdefinierter Parameter für `page_name` `web.webpagedetails.pageName` zugeordnet.

Um die Kompatibilität sowohl mit der Target-Erweiterung als auch mit der Offer Decisioning- und Target-Erweiterung sicherzustellen, sollten Sie alle relevanten Zielgruppen aktualisieren, sodass `OR` Bedingungen verwendet werden, wie unten dargestellt:

![Anzeigen und Aktualisieren einer Target-Zielgruppe für die Kompatibilität mit der Offer Decisioning- und Target-Erweiterung](assets/target-audience-update.png){zoomable="yes"}

## Profilskripte bearbeiten

Wenn Sie Mbox-Parameter in das `xdm` migrieren, sollten Profilskripte aktualisiert werden, um auf die neuen XDM-Parameternamen zu verweisen, ähnlich wie bei Audiences. Abgesehen von der Änderung der Mbox-Parameternamen gibt es keinen Unterschied in der Funktionsweise von Profilskripten zwischen einer Target- und einer Decisioning-Implementierung.

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

Weitere Informationen und Best Practices finden Sie in der entsprechenden Dokumentation zu [Profilskripten](https://experienceleague.adobe.com/de/docs/target/using/audiences/visitor-profiles/profile-parameters).

## Aktualisieren von Parameter-Token für dynamische Inhalte

Wenn Sie Mbox-Parameter zum `xdm` migrieren und Angebote, Recommendations-Designs oder Aktivitäten haben, die [dynamische Inhaltsersetzung](https://experienceleague.adobe.com/de/docs/target/using/experiences/offers/passing-profile-attributes-to-the-html-offer) verwenden, müssen diese möglicherweise entsprechend aktualisiert werden, um die neuen XDM-Parameternamen zu berücksichtigen.

Je nachdem, wie Sie die Token-Ersetzung für mbox-Parameter verwenden, können Sie Ihre vorhandene Einrichtung möglicherweise erweitern, um sowohl alte als auch neue Parameternamen zu berücksichtigen. In Situationen, in denen benutzerdefinierter JavaScript-Code nicht möglich ist, z. B. in JSON-Angeboten, sollten Sie jedoch nach Abschluss der Migration Kopien erstellen und Aktualisierungen vornehmen und diese auf Ihrer Produktions-Site live schalten.

Beispiel eines JSON-Angebots:

```JSON
{
  "pageName" : "${mbox.page_name}",
  "layoutVariation" : "grid"
}
```

Beispiel eines JSON-Angebots mit XDM-Objektparameternamen:

```JSON
{
  "pageName" : "${mbox.web.webPagedDetails.pageName}",
  "layoutVariation" : "grid"
}
```

Wenn Sie nach der Migration Anpassungen vornehmen möchten, um die neuen XDM-Mbox-Parameternamen zu berücksichtigen, achten Sie darauf, alle betroffenen Aktivitäten während des Migrationsereignisses anzuhalten, um Fehler bei der Aktivitätsanzeige für Besucher zu vermeiden.


Erfahren Sie als Nächstes, wie [&#x200B; die Target-Implementierung validieren](validate.md).

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=de#M463) posten.
