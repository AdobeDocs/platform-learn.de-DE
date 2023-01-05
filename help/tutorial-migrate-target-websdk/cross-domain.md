---
title: Domänenübergreifende Unterstützung aktivieren | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie Adobe Target für domänenübergreifende und mobile Apps mithilfe des Experience Platform Web SDK für Webbrowser-Szenarien konfigurieren.
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---

# Domänenübergreifende Besucherprofile aktivieren

Das Platform Web SDK unterstützt Funktionen zur Freigabe von Besucher-IDs, mit denen Kunden personalisierte Erlebnisse über Ihre Domänen hinweg genauer bereitstellen können. Mit dieser Funktion können Sie domänenübergreifend eine konsistente Personalisierung bereitstellen und die Genauigkeit der Berichte zu Besucheraktivitäten verbessern, ohne auf Drittanbieter-Cookies angewiesen zu sein.

## Voraussetzungen

Um die domänenübergreifende ID-Freigabe zu verwenden, müssen Sie die Platform Web SDK-Version 2.11.0 oder höher verwenden. Diese Funktion ist auch mit VisitorAPI.js Version 1.7.0 oder neuer kompatibel.

Die domänenübergreifende ID-Freigabe funktioniert durch Anhängen einer speziellen `adobe_mc` -Abfragezeichenfolgenparameter an die URL der Zieldomäne an. Dieser Parameter wird zum Angeben der Besucher-ID verwendet, anstatt eine neue ID zu generieren oder eine vorhandene ID zu verwenden.

Die Zieldomäne muss eine dieser Bibliotheken für die domänenübergreifende ID-Freigabe verwenden, um die `adobe_mc` und teilen Sie die Besucher-ID ordnungsgemäß.

## Vergleich der Ansätze

Bestimmen Sie vor der Implementierung zunächst, ob Ihre vorhandene Implementierung die `visitor.appendVisitorIDsTo()` -Funktion. Jeder benutzerspezifische Code, der diese Funktion verwendet, sollte aktualisiert werden, um die neue `appendIdentityToUrl` Web SDK-Befehl.

| VisitorAPI.js | Platform Web-SDK |
| --- | --- |
| `visitor.appendVisitorIDsTo(*url*)` | `alloy("appendIdentityToUrl", { url: *url* })` |

## Verwenden der `appendIdentityToURL` command

Für die domänenübergreifende ID-Freigabe bietet das Web SDK Version 2.11.0 Unterstützung für die `appendIdentityToUrl` Befehl. Wenn dieser Befehl verwendet wird, generiert er die `adobe_mc` Abfragezeichenfolgen-Parameter.

Der Befehl akzeptiert ein Objekt mit einer Eigenschaft, `url`und gibt ein Objekt mit der Eigenschaft url zurück.

Dieser Befehl wartet nicht auf eine Aktualisierung der Zustimmung. Wenn keine Zustimmung erteilt wurde, wird die URL unverändert zurückgegeben.

Wenn keine ECID angegeben wird, wird die `/acquire` -Endpunkt wird aufgerufen, um eine ECID zu generieren.

Im Folgenden finden Sie ein Beispiel dafür, wie Sie die domänenübergreifende ID-Freigabe implementieren können.

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
>Bei Verwendung der Tags-Funktion (früher Launch) zur Implementierung des Web SDK kann die domänenübergreifende ID-Freigabe ohne benutzerdefinierten Code durchgeführt werden. Siehe Abschnitt [dedizierte Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html#tags-extension) für weitere Details.

>[!NOTE]
>
>Das Platform Web SDK unterstützt auch die Freigabe von mobilen IDs für native Anwendungsfälle mobiler Apps. Weitere Informationen finden Sie in der entsprechenden Dokumentation zu [Freigabe mobiler Daten im Internet und domänenübergreifende ID-Freigabe](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html).

Als Nächstes erfahren Sie, wie Sie [Zielgruppen und Profilskripte aktualisieren](update-audiences.md) , um die Kompatibilität mit dem Platform Web SDK sicherzustellen.

>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).