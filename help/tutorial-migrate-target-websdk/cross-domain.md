---
title: Domain-übergreifende Unterstützung aktivieren - Target von at.js 2.x zu Web SDK migrieren
description: Erfahren Sie, wie Sie Adobe Target für domänenübergreifende und mobile App-zu-Webbrowser-Szenarien mit Experience Platform Web SDK konfigurieren.
exl-id: 6ec24ddc-8f6d-4331-a3ae-bd0f3a7d6e78
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Domänenübergreifende Besucherprofile aktivieren

Die Platform Web SDK unterstützt Funktionen zum Freigeben von Besucher-IDs, mit denen Kunden personalisierte Erlebnisse präziser über Ihre Domains hinweg bereitstellen können. Mit dieser Funktion können Sie eine konsistente Personalisierung über Domains hinweg bereitstellen und die Genauigkeit der Berichte zu Besucheraktivitäten verbessern, ohne auf Drittanbieter-Cookies angewiesen zu sein.

## Voraussetzungen

Um die Domain-übergreifende ID-Freigabe zu verwenden, müssen Sie Platform Web SDK Version 2.11.0 oder höher verwenden. Diese Funktion ist auch mit VisitorAPI.js Version 1.7.0 oder höher kompatibel.

Die Domain-übergreifende ID-Freigabe funktioniert durch Anhängen eines speziellen `adobe_mc` Abfragezeichenfolgenparameters an die URL der Ziel-Domain. Dieser Parameter wird verwendet, um die Besucher-ID anzugeben, anstatt eine neue ID zu generieren oder eine vorhandene ID zu verwenden.

Die Ziel-Domain muss eine dieser Bibliotheken für die Domain-übergreifende ID-Freigabe verwenden, um den `adobe_mc` Parameter zu verarbeiten und die Besucher-ID ordnungsgemäß freizugeben.

## Anflugvergleich

Stellen Sie vor der Implementierung zunächst fest, ob Ihre vorhandene Implementierung die `visitor.appendVisitorIDsTo()` verwendet. Jeder benutzerdefinierte Code, der diese Funktion verwendet, sollte aktualisiert werden, um den neuen `appendIdentityToUrl` Web SDK-Befehl zu verwenden.

| VisitorAPI.js | Platform Web-SDK |
| --- | --- |
| `visitor.appendVisitorIDsTo(*url*)` | `alloy("appendIdentityToUrl", { url: *url* })` |

## Verwenden des `appendIdentityToURL` Befehls

Bei der Domain-übergreifenden ID-Freigabe unterstützt Web SDK Version 2.11.0 den Befehl `appendIdentityToUrl`. Bei Verwendung dieses Befehls wird der `adobe_mc` Abfragezeichenfolgenparameter generiert.

Der Befehl akzeptiert ein -Objekt mit der Eigenschaft `url` und gibt ein -Objekt mit der Eigenschaft URL zurück.

Dieser Befehl wartet nicht auf eine Aktualisierung des Einverständnisses. Wenn kein Einverständnis erteilt wurde, wird die URL unverändert zurückgegeben.

Wenn keine ECID bereitgestellt wird, wird der `/acquire`-Endpunkt aufgerufen, um eine ECID zu generieren.

Im Folgenden finden Sie ein Beispiel dafür, wie Sie die Domain-übergreifende ID-Freigabe implementieren können.

Dieser Code fügt einen Ereignis-Listener für alle Klicks auf der Seite hinzu. Wenn der Klick auf einen Link zu einer entsprechenden Domain erfolgte, in diesem Fall adobe.com oder behance.com, wird die Identität zur URL hinzugefügt und der Benutzer wird dorthin weitergeleitet.

```Javascript
document.addEventListener("click", event => {
  const anchor = event.target.closest("a");
  if (!anchor || !anchor.href) {
    return;
  }
  const url = new URL(anchor.href);
  if (!url.hostname.endsWith("adobe.com") && !url.hostname.endsWith("behance.com")) {
    return;
  }
  event.preventDefault();
  alloy("appendIdentityToUrl", { url: anchor.href }).then(result => {
    document.location = result.url;
  });
});
```

>[!TIP]
>
>Bei Verwendung der Tags-Funktion (früher Launch) zur Implementierung von Web SDK kann die Domain-übergreifende ID-Freigabe ohne benutzerdefinierten Code durchgeführt werden. Weitere Informationen finden Sie in [dedizierten ](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html#tags-extension)).

>[!NOTE]
>
>Die Platform Web SDK unterstützt auch die Freigabe von IDs von Mobilgeräten an das Web für native Anwendungsfälle von Mobile Apps. Weitere Informationen finden Sie in der entsprechenden Dokumentation [Mobile-zu-Web und Domain-übergreifender ID-Austausch](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html).

Erfahren Sie als Nächstes, wie Sie [Zielgruppen und Profilskripte aktualisieren](update-audiences.md) um die Kompatibilität mit Platform Web SDK sicherzustellen.

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von at.js zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
