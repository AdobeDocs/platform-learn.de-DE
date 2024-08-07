---
title: Erwägen Sie, Anbieter-Tags zur Ereignisweiterleitung zu verschieben.
description: Erfahren Sie, wie Sie ein Client-seitiges Anbieter-Tag für die serverseitige Datenverteilung auswerten.
feature: Event Forwarding, Tags, Integrations
role: Admin, Developer, Architect, Data Engineer
level: Intermediate, Experienced
jira: KT-9921
exl-id: f8fd351a-435c-4cc1-b987-ed2ead20d4d6
source-git-commit: 7edf8fc46943ae2f1e6e2e20f4d589d7959310c8
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 4%

---

# Erwägen Sie, clientseitige Anbieter-Tags zur Ereignisweiterleitung zu verschieben.

Es gibt mehrere zwingende Gründe, das Verschieben clientseitiger Anbieter-Tags aus Browsern und Geräten auf einen Server zu erwägen. In diesem Artikel besprechen wir, wie ein clientseitiges Anbieter-Tag dahingehend bewertet werden kann, dass es möglicherweise in eine Ereignisweiterleitungs-Eigenschaft verschoben wird.

Diese Bewertung ist nur erforderlich, wenn Sie erwägen, ein clientseitiges Anbieter-Tag zu entfernen und es durch die serverseitige Datenverteilung in einer Ereignisweiterleitungs-Eigenschaft zu ersetzen. In diesem Artikel wird davon ausgegangen, dass Sie mit den Grundlagen der [Datenerfassung](https://experienceleague.adobe.com/docs/data-collection.html) und der [Ereignisweiterleitung](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html) vertraut sind.

>[!NOTE]
>
>Adobe Experience Platform Launch wurde als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform umbenannt. Infolgedessen wurden in der gesamten Produktdokumentation mehrere terminologische Änderungen eingeführt. Eine konsolidierte Übersicht der terminologischen Änderungen finden Sie im folgenden [Dokument](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html?lang=de).

Browser-Anbieter ändern die Behandlung von Drittanbieter-Cookies. Advertising- und Marketing-Anbieter und -Technologien erfordern häufig die Verwendung vieler clientseitiger Tags. Diese Herausforderungen sind nur zwei überzeugende Gründe dafür, dass unsere Kunden die serverseitige Datenverteilung hinzufügen.

>[!NOTE]
>
>`Tag` in diesem Artikel bedeutet clientseitigen Code, normalerweise JavaScript von einem Anbieter, der für die Datenerfassung im Browser oder Gerät verwendet wird, während ein Besucher mit der Site oder App interagiert. `Website` oder `site` bezieht sich hier auf eine Website, eine Webanwendung oder eine Anwendung für ein Mobilgerät. Ein &quot;Tag&quot;für diese Zwecke wird häufig auch als Pixel bezeichnet.

## Anwendungsbeispiele und Daten {#use-cases-data}

Der erste Schritt besteht darin, die Anwendungsfälle zu definieren, die mit dem clientseitigen Anbieter-Tag implementiert wurden. Betrachten Sie beispielsweise das Facebook-Pixel (Meta). Wenn Sie ihn von unserer Site zur [Meta Conversions-API](https://exchange.adobe.com/apps/ec/109168/meta-conversions-api) mit der Ereignisweiterleitungs-Erweiterung verschieben, müssen Sie zuerst die spezifischen Anwendungsfälle dokumentieren.

Für den aktuellen clientseitigen Anbietercode:

- Welche bestimmten Ereignisse und anderen Datenpunkte werden bereitgestellt und an das clientseitige Tag übergeben?
- Wann und wo erfolgt diese Datenübertragung?

Es ist hilfreich, eine Liste, Tabelle, ein Diagramm oder einen anderen Datensatz der Daten und Ereignisabfolge zu erstellen, um diese Auswertung zu dokumentieren - auch wenn sie nur für Ihre eigene Verwendung bestimmt ist. Stellen Sie sicher, dass Beschriftungen für Datenquellen enthalten sind - woher kommen sie? Ziele - wohin geht es? Und Transformationen - was passiert damit zwischen Quelle und Ziel?

In unserem Beispiel verfolgen wir Konversionen mit dem Facebook-Pixel, wenn Besucher nach Ansicht einer Facebook-Anzeige mit unserer Site interagieren. Sie können auch mit unserer Site interagieren, nachdem sie verwandte Anzeigen auf einer anderen sozialen Plattform angesehen haben. Um diese Konversionen in den Facebook-Werbe-Tools und -Berichten anzuzeigen, müssen die erforderlichen Daten an Facebook übermittelt werden. Diese Daten können Konversionsereignisse wie Downloads, Registrierungen, &quot;Gefällt mir&quot;-Klicks oder Käufe enthalten.

### Daten {#data}

Was geschieht mit den Daten für unseren Anwendungsfall, wenn das vorhandene clientseitige Tag auf unserer Site ausgeführt oder ausgeführt wird? Können wir die benötigten Daten im Client ohne das Anbieter-Tag erfassen, damit wir sie an die Ereignisweiterleitung senden können? Bei Verwendung von [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) oder anderen Tag-Management-Systemen stehen die meisten Besucherinteraktionsdaten für die Erfassung und Verteilung zur Verfügung. Aber sind die Daten, die wir für unseren Anwendungsfall benötigen, verfügbar, wenn wir ihn benötigen, wo wir ihn brauchen und in dem Format, das wir ihn benötigen - ohne das Client-seitige Anbieter-Tag? Im Folgenden finden Sie einige weitere Datenfragen, die beachtet werden müssen:

- Ist bei jedem Ereignis eine Benutzer-ID des Anbieters erforderlich?
- Wenn ja, wie kann sie ohne das clientseitige Tag erfasst oder generiert werden?
- Benötigt der Anbieter speziell seinen clientseitigen Code zur Laufzeit?
- Welche anderen Daten sind erforderlich? Woher kommen diese Daten?

Die meisten clientseitigen Anbieter-Tags benötigen für keinen bestimmten Anwendungsfall viele Datenpunkte. Es ist jedoch hilfreich, die Anwendungsfälle und erforderlichen Daten bei diesen Auswertungen zu beachten.

## Anbieter-APIs {#vendor-apis}

Jetzt kennen wir die spezifischen Anwendungsfälle, die implementiert werden müssen, die erforderlichen Daten und die Reihenfolge der Ereignisse von der Quelle bis zum Ziel. Um festzustellen, ob der Anwendungsfall für die Ereignisweiterleitung geeignet ist, können wir jetzt die Details der Anbieter-API untersuchen.

>[!IMPORTANT]
>
>Während viele Anbieter APIs für die Übertragung von Server zu Server aktivieren, gibt es auch viele, die derzeit keine APIs für diese Zwecke haben.

### APIs untersuchen {#investigate-apis}

Im Folgenden finden Sie einige Schritte, die wir zur Untersuchung von Anbieter-API-Endpunkten durchführen können.

Verfügt der Anbieter über APIs für die Übertragung von Ereignisdaten von Server zu Server? Suchen Sie zunächst die Anforderungen für diese spezifischen API-Endpunkte:

- Existieren die API-Endpunkte, um die erforderlichen Daten zu senden? Die Endpunkte, die Ihre Anwendungsfälle unterstützen, finden Sie in der Entwickler- oder API-Dokumentation des Anbieters.
- Erlauben sie Streaming-Ereignisdaten oder nur Batch-Daten?
- Welche Authentifizierungsmethoden werden unterstützt? Token, HTTP, OAuth-Client-Anmeldedaten-Version oder andere? Informationen zu den von der Ereignisweiterleitung unterstützten Methoden finden Sie unter [hier](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html) .
- Wie hoch ist der Aktualisierungsversatz ihrer API? Ist diese Einschränkung mit den Mindestwerten für die Ereignisweiterleitung kompatibel? Details [hier](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html#:~:text=you%20can%20configure%20the%20Refresh%20Offset%20value%20for%20the%20secret).
- Welche Daten benötigen sie für die relevanten Endpunkte?
- Benötigen sie eine herstellerspezifische Benutzer-ID bei jedem Aufruf an den -Endpunkt?
- Wenn diese ID erforderlich ist, wo und wie kann sie ohne clientseitigen Code generiert oder erfasst werden?

Mit anderen Worten:

- Stellt der Anbieter die für unsere Anwendungsfälle erforderlichen API-Endpunkte bereit?
- Verfügen sie über eine kompatible Authentifizierungsmethode für die Ereignisweiterleitung?
- Können wir auf alle Daten zugreifen, die für die Implementierung der Ereignisweiterleitung erforderlich sind (entweder von der Client-Seite oder von anderen API-Aufrufen)?

Das -Tag ist wahrscheinlich ein guter Kandidat, um in einer Ereignisweiterleitungseigenschaft vom Client zu unseren Servern zu wechseln, wenn wir auf diese Fragen mit Ja antworten können.

Wenn der Anbieter nicht über die API-Endpunkte verfügt, die unsere Anwendungsfälle unterstützen, ist dieses Anbieter-Tag offensichtlich kein guter Kandidat für die Verwendung der Ereignisweiterleitung anstelle des clientseitigen Anbieter-Tags.

Was passiert, wenn sie über APIs verfügen, aber bei jedem API-Aufruf auch eine Unique Visitor- oder Benutzer-ID benötigen? Wie können wir auf diese ID zugreifen, wenn der clientseitige Code (Tag) des Anbieters nicht auf der Site ausgeführt wird?

Einige Anbieter ändern ihre Systeme für die neue Welt ohne Drittanbieter-Cookies. Zu diesen Änderungen gehört die Verwendung alternativer eindeutiger IDs, z. B. einer [UUID](https://developer.mozilla.org/en-US/docs/Glossary/UUID) oder einer anderen [kundengenerierten ID](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html). Wenn der Anbieter eine kundengenerierte ID zulässt, können wir sie entweder mit dem Web- oder Mobile-SDK vom Client an Platform Edge Network senden oder möglicherweise von einem API-Aufruf in der Ereignisweiterleitung abrufen. Wenn wir Daten an diesen Anbieter in einer Ereignisweiterleitungsregel senden, fügen wir diese Kennung einfach nach Bedarf hinzu.

Wenn der Anbieter Daten benötigt (z. B. eine herstellerspezifische eindeutige ID), die nur von seinem eigenen clientseitigen Tag generiert oder aufgerufen werden können, ist dieses Anbieter-Tag wahrscheinlich kein guter Kandidat für die Verschiebung. _Es wird davon abgeraten, einen Client-seitigen Tag umzukehren, um die Datenerfassung zur Ereignisweiterleitung ohne die entsprechenden APIs zu verschieben._

Die Erweiterung [Adobe Experience Platform Cloud Connector](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/cloud-connector/overview.html) kann bei Anbietern, die über die entsprechenden APIs für die Übertragung von Server-zu-Server-Ereignisdaten verfügen, nach Bedarf HTTP-Anfragen stellen. Auch wenn herstellerspezifische Erweiterungen gut zu haben sind und sich derzeit weitere Erweiterungen in der aktiven Entwicklung befinden, können wir heute mit der Cloud Connector-Erweiterung Ereignisweiterleitungsregeln implementieren, ohne auf zusätzliche Erweiterungen von Anbietern warten zu müssen.

## Tools {#tools}

Das Untersuchen und Testen von Anbieter-API-Endpunkten ist mit Tools wie [Postman](https://www.postman.com/) oder Texteditorerweiterungen wie Visual Studio Code [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client) oder [HTTP Client](https://marketplace.visualstudio.com/items?itemName=mkloubert.vscode-http-client) einfacher.

## Nächste Schritte {#next-steps}

Dieser Artikel enthält eine Reihe von Schritten zum Auswerten eines clientseitigen Tags eines Anbieters und zum möglichen Verschieben dieses Tags serverseitig in eine Ereignisweiterleitungseigenschaft. Weitere Informationen zu verwandten Themen finden Sie unter diesen Links:

- [Tag-Management](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) in Adobe Experience Platform
- [Ereignisweiterleitung](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html) für die serverseitige Verarbeitung
- [Aktualisierungen der Terminologie](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html?lang=de) in der Datenerfassung
