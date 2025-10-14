---
title: Sie sollten Anbieter-Tags zur Ereignisweiterleitung verschieben.
description: Erfahren Sie, wie Sie ein Client-seitiges Anbieter-Tag für die Server-seitige Datenverteilung auswerten.
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

# Informationen zum Umstieg von Client-seitigen Anbieter-Tags auf die Ereignisweiterleitung .

Es gibt mehrere überzeugende Gründe, Client-seitige Anbieter-Tags aus Browsern und Geräten auf einen Server zu verschieben. In diesem Artikel besprechen wir, wie ein Client-seitiges Anbieter-Tag ausgewertet werden kann, um es möglicherweise in eine Ereignisweiterleitungs-Eigenschaft zu verschieben.

Diese Auswertung ist nur erforderlich, wenn Sie erwägen, ein Client-seitiges Anbieter-Tag zu entfernen und es in einer Ereignisweiterleitungseigenschaft durch eine Server-seitige Datenverteilung zu ersetzen. In diesem Artikel wird davon ausgegangen, dass Sie mit den Grundlagen der [Datenerfassung](https://experienceleague.adobe.com/docs/data-collection.html?lang=de) und [Ereignisweiterleitung“ &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de) sind.

>[!NOTE]
>
>Adobe Experience Platform Launch wurde als eine Suite von Datenerfassungstechnologien in Adobe Experience Platform umbenannt. Infolgedessen wurden in der gesamten Produktdokumentation mehrere terminologische Änderungen eingeführt. Eine konsolidierte Übersicht der terminologischen Änderungen finden Sie im folgenden [Dokument](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html?lang=de).

Browser-Anbieter ändern die Art und Weise, wie sie Cookies von Drittanbietern behandeln. Advertising- und Marketing-Anbieter und -Technologien erfordern häufig die Verwendung vieler Client-seitiger Tags. Diese Herausforderungen sind nur zwei überzeugende Gründe dafür, dass unsere Kunden eine Server-seitige Datenverteilung hinzufügen.

>[!NOTE]
>
>`Tag` in diesem Artikel bezieht sich auf Client-seitigen Code, normalerweise JavaScript von einem Anbieter, der für die Datenerfassung im Browser oder Gerät verwendet wird, während ein Besucher mit der Site oder dem Programm interagiert. `Website` oder `site` bezieht sich hier auf eine Website, eine Web-Anwendung oder eine Anwendung für ein Mobilgerät. Ein „Tag“ wird für diese Zwecke oft auch als Pixel bezeichnet.

## Anwendungsfälle und Daten {#use-cases-data}

Der erste Schritt besteht darin, die Anwendungsfälle zu definieren, die mit dem Client-seitigen Anbieter-Tag implementiert werden. Nehmen wir zum Beispiel das Facebook-Pixel (Meta). Wenn Sie sie mit der Erweiterung für die Ereignisweiterleitung von unserer Site in [Meta Conversions](https://exchange.adobe.com/apps/ec/109168/meta-conversions-api)API) verschieben, müssen Sie zunächst die spezifischen Anwendungsfälle dokumentieren.

Für den aktuellen Client-seitigen Anbieter-Code:

- Welche spezifischen Ereignisse und anderen Datenpunkte werden bereitgestellt und an das Client-seitige Tag übergeben?
- Wann und wo findet diese Datenübertragung statt?

Es ist hilfreich, eine Liste, ein Arbeitsblatt, ein Diagramm oder eine andere Aufzeichnung der Daten und der Sequenz von Ereignissen zu erstellen, um diese Bewertung zu dokumentieren - auch wenn es nur für Ihren eigenen Gebrauch ist. Geben Sie für Datenquellen Beschriftungen an, woher diese stammen? Ziele - wo geht das hin? Und Transformationen - was passiert mit ihr zwischen Quelle und Ziel?

In unserem Beispiel verfolgen wir Konversionen mit dem Facebook-Pixel, wenn Besucher nach dem Anzeigen einer Facebook-Anzeige mit unserer Site interagieren. Sie können auch mit unserer Website interagieren, nachdem sie verwandte Anzeigen auf einer anderen sozialen Plattform angesehen haben. Um diese Konversionen in den Werbetools und -berichten von Facebook zu sehen, müssen die erforderlichen Daten an Facebook übermittelt werden. Zu diesen Daten können Konversionsereignisse wie Downloads, Registrierungen, Likes oder Käufe gehören.

### Daten {#data}

Was passiert mit den Daten für unseren Anwendungsfall, wenn das vorhandene Client-seitige Tag auf unserer Site ausgeführt wird? Können wir die benötigten Daten im Client ohne Anbieter-Tag erfassen, damit wir sie an die Ereignisweiterleitung senden können? Bei Verwendung [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) oder anderer Tag-Management-Systeme stehen die meisten Daten zu Besucherinteraktionen für die Sammlung und Verteilung zur Verfügung. Sind die Daten, die wir für unseren Anwendungsfall benötigen, jedoch verfügbar, wenn wir sie benötigen, wo wir sie benötigen, und in dem Format, in dem wir sie benötigen - ohne das Client-seitige Anbieter-Tag? Im Folgenden sind einige weitere Datenfragen zu berücksichtigen:

- Ist für jedes Ereignis eine Benutzer-ID des Anbieters erforderlich?
- Wenn ja, wie kann sie ohne das Client-seitige Tag erfasst oder generiert werden?
- Benötigt der Anbieter speziell Client-seitigen Code zur Laufzeit?
- Welche anderen Daten sind erforderlich? Woher kommen diese Daten?

Die meisten Client-seitigen Anbieter-Tags erfordern nicht viele Datenpunkte für einen bestimmten Anwendungsfall, es ist jedoch hilfreich, die Anwendungsfälle und erforderlichen Daten während dieser Auswertungen zu beachten.

## Anbieter-APIs {#vendor-apis}

Jetzt kennen wir die spezifischen zu implementierenden Anwendungsfälle, die erforderlichen Daten und die Sequenz der Ereignisse von der Quelle bis zum Ziel. Um festzustellen, ob der Anwendungsfall gut für die Ereignisweiterleitung geeignet ist, können wir jetzt die API-Details des Anbieters untersuchen.

>[!IMPORTANT]
>
>Viele Anbieter aktivieren APIs für die Server-zu-Server-Übertragung, es gibt aber auch viele, die derzeit keine APIs für diese Zwecke haben.

### Untersuchen von APIs {#investigate-apis}

Im Folgenden finden Sie einige Schritte, die wir unternehmen können, um API-Endpunkte von Anbietern zu untersuchen.

Verfügt der Anbieter über APIs für die Server-zu-Server-Übertragung von Ereignisdaten? Suchen Sie zunächst die Anforderungen für diese spezifischen API-Endpunkte:

- Sind die API-Endpunkte vorhanden, um die erforderlichen Daten zu senden? Die Endpunkte, die Ihre Anwendungsfälle unterstützen, finden Sie in der Entwickler- oder API-Dokumentation des Anbieters.
- Sind Streaming-Ereignisdaten zulässig oder nur Batch-Daten?
- Welche Authentifizierungsmethoden werden unterstützt? Token, HTTP, OAuth-Client-Anmeldedaten, Version oder andere? Siehe [hier](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets?lang=de) für Methoden, die von der Ereignisweiterleitung unterstützt werden.
- Was ist der Aktualisierungsversatz ihrer API? Ist diese Beschränkung mit den Mindestwerten für die Ereignisweiterleitung vereinbar? Details [hier](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html?lang=de#:~:text=you%20can%20configure%20the%20Refresh%20Offset%20value%20for%20the%20secret).
- Welche Daten benötigen sie für die entsprechenden Endpunkte?
- Benötigen sie bei jedem Aufruf des Endpunkts eine anbieterspezifische Benutzerkennung?
- Wenn sie diese Kennung benötigen, wo und wie kann sie ohne Client-seitigen Code generiert oder erfasst werden?

Mit anderen Worten:

- Stellt der Anbieter die für unsere Anwendungsfälle erforderlichen API-Endpunkte bereit?
- Verfügen sie über eine kompatible Authentifizierungsmethode für die Ereignisweiterleitung?
- Können wir auf alle Daten zugreifen, die für eine Implementierung der Ereignisweiterleitung erforderlich sind (entweder von der Client-Seite aus oder über andere API-Aufrufe)?

Das Tag ist wahrscheinlich ein guter Kandidat, um vom Client zu unseren Servern in einer Ereignisweiterleitungs-Eigenschaft zu wechseln, wenn wir diese Fragen mit „Ja“ beantworten können.

Wenn der Anbieter nicht über die API-Endpunkte zur Unterstützung unserer Anwendungsfälle verfügt, ist dieses Anbieter-Tag offensichtlich kein guter Kandidat für die Verwendung der Ereignisweiterleitung anstelle des Client-seitigen Anbieter-Tags.

Was passiert, wenn sie APIs haben, aber bei jedem API-Aufruf auch eine Unique-Visitor- oder Benutzer-ID benötigen? Wie können wir auf diese ID zugreifen, wenn der Client-seitige Code (Tag) des Anbieters nicht auf der Website ausgeführt wird?

Einige Anbieter ändern ihre Systeme für die neue Welt ohne Drittanbieter-Cookies. Zu diesen Änderungen gehört die Verwendung alternativer eindeutiger Kennungen wie [UUID](https://developer.mozilla.org/en-US/docs/Glossary/UUID) oder anderer [kundengenerierter ID](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html?lang=de). Wenn der Anbieter eine vom Kunden generierte ID zulässt, können wir sie entweder vom Client an das Platform-Edge Network mit Web- oder Mobile SDK senden oder sie möglicherweise von einem API-Aufruf in der Ereignisweiterleitung erhalten. Wenn wir Daten in einer Ereignisweiterleitungsregel an diesen Anbieter senden, schließen wir diese Kennung einfach nach Bedarf ein.

Wenn der Anbieter Daten benötigt (z. B. eine anbieterspezifische eindeutige ID), die nur von seinem eigenen Client-seitigen Tag generiert oder aufgerufen werden können, ist dieses Anbieter-Tag wahrscheinlich kein guter Kandidat, um verschoben zu werden. _Es wird davon abgeraten, ein Client-seitiges Tag so zu rekonstruieren, dass diese Datenerfassung in die Ereignisweiterleitung ohne die entsprechenden APIs verschoben wird._

Die Erweiterung [Adobe Experience Platform Cloud Connector](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/cloud-connector/overview.html?lang=de) kann bei Bedarf HTTP-Anfragen an Anbieter stellen, die über die entsprechenden APIs für die Server-zu-Server-Ereignisdatenübertragung verfügen. Während anbieterspezifische Erweiterungen schön zu haben sind und derzeit weitere Erweiterungen aktiv entwickelt werden, können wir heute Ereignisweiterleitungsregeln mit der Cloud Connector-Erweiterung implementieren, ohne auf zusätzliche Anbietererweiterungen warten zu müssen.

## Tools {#tools}

Das Untersuchen und Testen von API-Endpunkten von Anbietern ist mit Tools wie [Postman](https://www.postman.com/) oder Texteditorerweiterungen wie Visual Studio Code [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client) oder [HTTP Client](https://marketplace.visualstudio.com/items?itemName=mkloubert.vscode-http-client) einfacher.

## Nächste Schritte {#next-steps}

Dieser Artikel enthält eine Sequenz von Schritten, um ein Client-seitiges Tag des Anbieters zu bewerten und es möglicherweise Server-seitig in eine Ereignisweiterleitungseigenschaft zu verschieben. Weitere Informationen zu verwandten Themen finden Sie unter den folgenden Links:

- [Tag-Management](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) in Adobe Experience Platform
- [Ereignisweiterleitung](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de) für Server-seitige Verarbeitung
- [Terminologieaktualisierungen](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html?lang=de) in der Datenerfassung
