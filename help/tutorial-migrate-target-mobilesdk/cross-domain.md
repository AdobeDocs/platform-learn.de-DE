---
title: Domänenübergreifende Unterstützung aktivieren - Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie, wie Sie Adobe Target für domänenübergreifende und mobile Apps mithilfe des Experience Platform Web SDK für Webbrowser-Szenarien konfigurieren.
source-git-commit: afbc8248ad81a5d9080a4fdba1167e09bbf3b33d
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Domänenübergreifende Besucherprofile aktivieren

Das Platform Web SDK unterstützt Funktionen zur Freigabe von Besucher-IDs, mit denen Kunden personalisierte Erlebnisse über Ihre Domänen hinweg genauer bereitstellen können. Mit dieser Funktion können Sie domänenübergreifend eine konsistente Personalisierung bereitstellen und die Genauigkeit der Berichte zu Besucheraktivitäten verbessern, ohne auf Drittanbieter-Cookies angewiesen zu sein.

## Voraussetzungen

Um die domänenübergreifende ID-Freigabe zu verwenden, müssen Sie die Platform Web SDK-Version 2.11.0 oder höher verwenden. Diese Funktion ist auch mit VisitorAPI.js Version 1.7.0 oder neuer kompatibel.

Die domänenübergreifende ID-Freigabe funktioniert durch Anhängen eines speziellen Abfragezeichenfolgenparameters `adobe_mc` an die URL der Zieldomäne. Dieser Parameter wird zum Angeben der Besucher-ID verwendet, anstatt eine neue ID zu generieren oder eine vorhandene ID zu verwenden.

Die Zieldomäne muss eine dieser Bibliotheken für die domänenübergreifende ID-Freigabe verwenden, um den Parameter `adobe_mc` zu verarbeiten und die Besucher-ID ordnungsgemäß zu teilen.

## Vergleich der Ansätze

Bestimmen Sie vor der Implementierung zunächst, ob Ihre vorhandene Implementierung die Funktion `visitor.appendVisitorIDsTo()` verwendet. Jeder benutzerspezifische Code, der diese Funktion verwendet, sollte aktualisiert werden, um den neuen Web SDK-Befehl `appendIdentityToUrl` zu verwenden.

| VisitorAPI.js | Platform Web-SDK |
| --- | --- |
| `visitor.appendVisitorIDsTo(*url*)` | `alloy("appendIdentityToUrl", { url: *url* })` |

## Verwenden des Befehls `appendIdentityToURL`

Für die domänenübergreifende ID-Freigabe bietet das Web SDK Version 2.11.0 Unterstützung für den Befehl `appendIdentityToUrl`. Wenn dieser Befehl verwendet wird, generiert er den Abfragezeichenfolgenparameter `adobe_mc` .

Der Befehl akzeptiert ein Objekt mit der Eigenschaft &quot;`url`&quot;und gibt ein Objekt mit der Eigenschaft &quot;url&quot;zurück.

Dieser Befehl wartet nicht auf eine Aktualisierung der Zustimmung. Wenn keine Zustimmung erteilt wurde, wird die URL unverändert zurückgegeben.

Wenn keine ECID angegeben wird, wird der `/acquire` -Endpunkt aufgerufen, um eine ECID zu generieren.

Im Folgenden finden Sie ein Beispiel für die Implementierung der domänenübergreifenden ID-Freigabe.

Dieser Code fügt einen Ereignis-Listener für alle Klicks auf der Seite hinzu. Wenn sich der Klick auf einen Link zu einer übereinstimmenden Domäne befand, in diesem Fall adobe.com oder behance.com, wird die Identität zur URL hinzugefügt und der Benutzer dorthin weitergeleitet.

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
>Bei Verwendung der Tags-Funktion (früher Launch) zur Implementierung des Web SDK kann die domänenübergreifende ID-Freigabe ohne benutzerdefinierten Code durchgeführt werden. Weitere Informationen finden Sie in der [dedizierten Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html#tags-extension) .

>[!NOTE]
>
>Das Platform Web SDK unterstützt auch die Freigabe von mobilen IDs für native Anwendungsfälle mobiler Apps. Weitere Informationen finden Sie in der entsprechenden Dokumentation zum Thema [Freigeben von IDs zwischen Mobilgeräten und Domänen sowie zum domänenübergreifenden Freigeben](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html).

Anschließend erfahren Sie, wie Sie [Zielgruppen und Profilskripte aktualisieren](update-audiences.md), um die Kompatibilität mit dem Platform Web SDK sicherzustellen.

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Migration Ihrer mobilen Target-Erweiterung von der Target-Erweiterung zur Decisioning-Erweiterung. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies mit, indem Sie in [dieser Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
