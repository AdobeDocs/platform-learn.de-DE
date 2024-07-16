---
title: Einrichten von Adobe Target mit dem Platform Web SDK
description: Erfahren Sie, wie Sie Adobe Target mit dem Platform Web SDK implementieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
solution: Data Collection, Target
jira: KT-15410
exl-id: 9084f572-5fec-4a26-8906-6d6dd1106d36
source-git-commit: e7bb1a7856d04c30da63cc013c2d5a5fea3d718e
workflow-type: tm+mt
source-wordcount: '4363'
ht-degree: 1%

---

# Einrichten von Adobe Target mit dem Platform Web SDK

Erfahren Sie, wie Sie Adobe Target mit Adobe Experience Platform Web SDK implementieren. Erfahren Sie, wie Sie Erlebnisse bereitstellen und zusätzliche Parameter an Target übergeben.

[Adobe Target](https://experienceleague.adobe.com/en/docs/target/using/target-home) ist die Adobe Experience Cloud-Anwendung, die Ihnen all das bietet, was Sie benötigen, um das Kundenerlebnis anzupassen und zu personalisieren, sodass Sie Umsätze auf Ihren Web- und mobilen Sites, in Apps und anderen digitalen Kanälen maximieren können.

![Web SDK- und Adobe Target-Diagramm](assets/dc-websdk-at.png)

## Lernziele

Am Ende dieser Lektion können Sie Folgendes mit einer Web SDK-Implementierung von Target tun:

* Codeausschnitt zur Vorab-Ausblendung hinzufügen, um Flackern zu verhindern
* Konfigurieren eines Datenspeichers zur Aktivierung der Target-Funktion
* Rendern von Visual Experience Composer-Aktivitäten
* Render Form Composer-Aktivitäten
* Übergeben von XDM-Daten an Target und Verstehen der Zuordnung zu Target-Parametern
* Übergeben benutzerdefinierter Daten an Target, z. B. Profil- und Entitätsparameter
* eine Target-Implementierung überprüfen
* Trennen von Personalisierungsanforderungen von Analyseanforderungen

>[!TIP]
>
>Eine schrittweise Anleitung zur Migration Ihrer vorhandenen at.js-Implementierung finden Sie in unserem Tutorial zur Migration von Target von at.js 2.x auf das Platform Web SDK](/help/tutorial-migrate-target-websdk/introduction.md) .[


## Voraussetzungen

Um die Lektionen in diesem Abschnitt abzuschließen, müssen Sie zunächst:

* Schließen Sie alle Lektionen für die Erstkonfiguration des Platform Web SDK ab, einschließlich der Einrichtung von Datenelementen und Regeln.
* Stellen Sie sicher, dass Sie in Adobe Target über die Rolle [Bearbeiter oder Genehmiger](https://experienceleague.adobe.com/en/docs/target/using/administer/manage-users/enterprise/properties-overview#section_8C425E43E5DD4111BBFC734A2B7ABC80) verfügen.
* Installieren Sie die Helper-Erweiterung [Visual Experience Composer](https://experienceleague.adobe.com/en/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension) , wenn Sie den Google Chrome-Browser verwenden.
* Erfahren Sie, wie Sie Aktivitäten in Target einrichten. Wenn Sie einen Auffrischungskurs benötigen, sind die folgenden Tutorials und Handbücher für diese Lektion hilfreich:
   * [Verwenden der Visual Experience Composer (VEC) Helper-Erweiterung](https://experienceleague.adobe.com/en/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension)
   * [Visual Experience Composer verwenden](https://experienceleague.adobe.com/en/docs/target-learn/tutorials/experiences/use-the-visual-experience-composer)
   * [Verwenden des formularbasierten Experience Composer](https://experienceleague.adobe.com/en/docs/target-learn/tutorials/experiences/use-the-form-based-experience-composer)
   * [Erstellen von Erlebnis-Targeting-Aktivitäten](https://experienceleague.adobe.com/en/docs/target-learn/tutorials/activities/create-experience-targeting-activities)

## Flackernde Behandlung hinzufügen

Stellen Sie vor dem Start fest, ob je nachdem, wie die Tag-Bibliothek geladen wird, eine zusätzliche Lösung zur Flackerverarbeitung erforderlich ist.

>[!NOTE]
>
>In diesem Tutorial wird die [Luma-Website](https://luma.enablementadobe.com/content/luma/us/en.html){target=_blank} verwendet, die über eine asynchrone Implementierung von Tags und eine Flackerverhinderung verfügt. In diesem Abschnitt erhalten Sie Informationen dazu, wie die Flackerverhinderung mit dem Platform Web SDK funktioniert.


### Asynchrone Implementierung

Wenn eine Tag-Bibliothek asynchron geladen wird, kann das Rendern der Seite abgeschlossen sein, bevor Target Standardinhalte durch personalisierte Inhalte ersetzt hat. Dieses Verhalten kann zum so genannten &quot;Flackern&quot;führen, bei dem kurz Standardinhalte angezeigt werden, bevor sie durch den personalisierten Inhalt ersetzt werden. Wenn Sie dieses Flimmern vermeiden möchten, empfiehlt Adobe, unmittelbar vor dem asynchronen Tag-Einbettungscode einen speziellen Codeausschnitt zur Vorab-Ausblendung hinzuzufügen.

Dieses Snippet ist bereits auf der Site &quot;Luma&quot;vorhanden, aber schauen wir uns genauer an, um zu verstehen, was dieser Code bewirkt:

```html
<script>
  !function(e,a,n,t){var i=e.head;if(i){
  if (a) return;
  var o=e.createElement("style");
  o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
  (document, document.location.href.indexOf("adobe_authoring_enabled") !== -1, ".personalization-container { opacity: 0 !important }", 3000);
</script>
```

Der vorab ausgeblendete Ausschnitt erstellt ein Stil-Tag im Seitenkopf mit der CSS-Definition Ihrer Wahl. Dieses Stil-Tag wird entfernt, wenn eine Antwort von Target empfangen wird oder die Zeitüberschreitung erreicht wird.

Das Verhalten der Vorab-Ausblendung wird durch zwei Konfigurationen am Ende des Ausschnitts gesteuert.

* `body { opacity: 0 !important }` gibt die CSS-Definition an, die für die Vorab-Ausblendung verwendet werden soll, bis Target geladen wird. Standardmäßig ist die gesamte Seite ausgeblendet. Sie können diese Definition auf die Selektoren aktualisieren, die Sie vorab ausblenden möchten, sowie auf die Art und Weise, wie Sie sie ausblenden möchten. Sie können mehrere Definitionen einbeziehen, da dieser Wert einfach in das vorab ausgeblendete Stil-Tag eingefügt wird. Wenn Sie über ein leicht identifizierbares Container-Element verfügen, das den Inhalt unter Ihrer Navigation einschließt, können Sie diese Einstellung verwenden, um die Vorab-Ausblendung auf dieses Container-Element zu beschränken.
* `3000` gibt die Zeitüberschreitung in Millisekunden für die Vorab-Ausblendung an. Wenn vor der Zeitüberschreitung keine Antwort von Target empfangen wird, wird das Stil-Tag für die Vorab-Ausblendung entfernt. Das Erreichen dieser Zeitüberschreitung sollte selten sein.

>[!NOTE]
>
>Der Codeausschnitt zur Vorab-Ausblendung für das Platform Web SDK unterscheidet sich geringfügig von dem für die at.js-Bibliothek von Target verwendeten. Verwenden Sie unbedingt das richtige Snippet für das Platform Web SDK, da es eine andere Stil-ID von `alloy-prehiding` verwendet. Wenn der vorab ausgeblendete Ausschnitt für at.js verwendet wird, funktioniert er möglicherweise nicht ordnungsgemäß.

Der vorab ausgeblendete Ausschnitt ist auch innerhalb von Tags verfügbar:

1. Navigieren Sie zum Abschnitt **[!UICONTROL Erweiterungen]** der Tags.
1. Wählen Sie **[!UICONTROL Konfigurieren]** für die Adobe Experience Platform Web SDK-Erweiterung
1. Wählen Sie die Schaltfläche **[!UICONTROL Vorab-Ausblendungs-Snippet in Zwischenablage kopieren]** aus

   ![Snippet zur Vorab-Ausblendung von Target für asynchrone Implementierungen](assets/target-flicker-async.png)

   >[!NOTE]
   >
   >Der standardmäßige Codeausschnitt zur Vorab-Ausblendung, der aus der Platform Web SDK-Erweiterung kopiert wird, kann eine CSS-Definition enthalten, die auf Ihrer Site nicht vorhanden ist, z. B. `.personalization-container { opacity: 0 !important }`. Stellen Sie sicher, dass Sie das vorab ausgeblendete Snippet für Ihre Site entsprechend überprüfen und ändern.

### Synchrone Implementierung

Adobe empfiehlt die asynchrone Implementierung von Tags, wie auf der Site &quot;Luma&quot;gezeigt. Wenn die Tag-Bibliothek jedoch synchron geladen wird, ist das vorab ausgeblendete Snippet nicht erforderlich. Stattdessen wird der Vorab-Ausblendestil in den Einstellungen der Platform Web SDK-Erweiterung angegeben.

Der Vorab-Ausblendestil für synchrone Implementierungen kann wie folgt konfiguriert werden:

1. Navigieren Sie zum Abschnitt **[!UICONTROL Erweiterungen]** der Tags.
1. Wählen Sie die Schaltfläche **[!UICONTROL Konfigurieren]** für die Platform Web SDK-Erweiterung
1. Wählen Sie die Schaltfläche **[!UICONTROL Vorab-Ausblendestil bearbeiten]** aus

   ![Snippet zur Vorab-Ausblendung von Target für asynchrone Implementierungen](assets/target-flicker-sync.png)

1. Ändern Sie das CSS, um die Selektoren und Ausblendemethoden einzuschließen, die Sie verwenden möchten, z. B.: `body { opacity: 0 !important }` , wenn Sie den gesamten Body der Seite vorab ausblenden möchten.
1. Speichern Sie Ihre Änderungen und erstellen Sie sie in einer Bibliothek.

>[!NOTE]
>
>Die Einstellung für den Stil vor der Ausblendung sollte nur für synchrone Implementierungen verwendet werden. Dieser Stil sollte leer sein oder auskommentiert sein, wenn Sie eine asynchrone Implementierung von Tags verwenden.

Weiterführende Informationen zur Verwaltung von Flackern mit dem Platform Web SDK finden Sie im Abschnitt &quot;Handbuch&quot;: [Beheben von Flackern für personalisierte Erlebnisse](https://experienceleague.adobe.com/en/docs/experience-platform/edge/personalization/manage-flicker).


## Konfigurieren des Datenspeichers

Target muss in der Datastream-Konfiguration aktiviert sein, bevor Target-Aktivitäten vom Platform Web SDK bereitgestellt werden können.

So konfigurieren Sie Target im Datastream:

1. Wechseln Sie zur Oberfläche [Datenerfassung](https://experience.adobe.com/#/data-collection){target="blank"} .
1. Wählen Sie im linken Navigationsbereich **[!UICONTROL Datastreams]** aus.
1. Wählen Sie den zuvor erstellten `Luma Web SDK: Development Environment`-Datastream aus.

   ![Wählen Sie den Luma Web SDK-Datenspeicher aus](assets/datastream-luma-web-sdk-development.png)

1. Wählen Sie **[!UICONTROL Dienst hinzufügen]** aus
   ![Hinzufügen eines Dienstes zum Datastream](assets/target-datastream-addService.png)
1. Wählen Sie **[!UICONTROL Adobe Target]** als **[!UICONTROL Dienst]** aus.
1. Geben Sie bei Bedarf die optionalen Details zur Target-Implementierung ein. Befolgen Sie dabei die unten stehenden Anleitungen.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

   ![Target-Datastream-Konfiguration](assets/target-datastream.png)

### Eigenschafts-Token

Target Premium-Kunden haben die Möglichkeit, Benutzerberechtigungen mit Eigenschaften zu verwalten. Mit Target-Eigenschaften können Sie Grenzen festlegen, um die Benutzer Target-Aktivitäten ausführen können. Weitere Informationen finden Sie im Abschnitt [Unternehmensberechtigungen](https://experienceleague.adobe.com/en/docs/target/using/administer/manage-users/enterprise/properties-overview) der Target-Dokumentation.

Um Eigenschafts-Token einzurichten oder zu finden, navigieren Sie zu &quot;**Adobe Target**&quot;> &quot;**[!UICONTROL Administration]**&quot;> &quot;**[!UICONTROL Eigenschaften]**&quot;. Das Symbol `</>` zeigt den Implementierungscode an. Der Wert `at_property` ist das Eigenschafts-Token, das Sie in Ihrem Datastream verwenden würden.

![Target-Eigenschafts-Token](assets/target-admin-properties.png)

<a id="advanced-pto"></a>

Pro Datastream kann nur ein Eigenschafts-Token angegeben werden, aber Eigenschafts-Token-Überschreibungen ermöglichen es Ihnen, alternative Eigenschafts-Token anzugeben, um das im Datastream definierte primäre Eigenschafts-Token zu ersetzen. Eine Aktualisierung der Aktion `sendEvent` ist auch erforderlich, um den Datastream zu überschreiben.

![Identitätsliste](assets/advanced-property-token.png)

### Target-Umgebungs-ID

[Umgebungen](https://experienceleague.adobe.com/en/docs/target/using/administer/environments) in Target helfen Ihnen bei der Verwaltung Ihrer Implementierung in allen Phasen der Entwicklung. Diese optionale Einstellung gibt an, welche Target-Umgebung Sie für jeden Datastream verwenden werden.

Adobe empfiehlt, die Target-Umgebungs-ID für jeden Ihrer Entwicklungs-, Staging- und Produktionsdatastreams unterschiedlich festzulegen, um die Dinge einfach zu halten. Alternativ können Sie Ihre Umgebungen in der Target-Oberfläche mithilfe der Funktion [hosts](https://experienceleague.adobe.com/en/docs/target/using/administer/hosts) organisieren.

Um Umgebungs-IDs einzurichten oder zu finden, navigieren Sie zu &quot;**Adobe Target**&quot;> &quot;**[!UICONTROL Administration]**&quot;> &quot;**[!UICONTROL Umgebungen]**&quot;.

![Target-Umgebungen](assets/target-admin-environments.png)

>[!NOTE]
>
>Wenn keine Target-Umgebungs-ID angegeben ist, wird von der Target-Produktionsumgebung ausgegangen.

### Target-Drittanbieter-ID-Namespace

Mit dieser optionalen Einstellung können Sie angeben, welches Identitätssymbol für die Target-Drittanbieter-ID verwendet werden soll. Target unterstützt nur die Profilsynchronisierung für ein einzelnes Identitätssymbol oder Namespace. Weitere Informationen finden Sie im Abschnitt [Echtzeit-Profilsynchronisation für mbox3rdPartyId](https://experienceleague.adobe.com/en/docs/target/using/audiences/visitor-profiles/3rd-party-id) des Target-Handbuchs.

Die Identitätssymbole befinden sich in der Identitätsliste unter **Datenerfassung** > **[!UICONTROL Kunde]** > **[!UICONTROL Identitäten]**.

![Identitätsliste](assets/target-identities.png)

Verwenden Sie für die Zwecke dieses Tutorials mit der Site &quot;Luma&quot;das Identitätssymbol `lumaCrmId` , das während der Lektion über [Identitäten](configure-identities.md) eingerichtet wurde.




## visuelle Personalisierungsentscheidungen rendern

Entscheidungen zur visuellen Personalisierung beziehen sich auf Erlebnisse, die im Visual Experience Composer von Adobe Target erstellt wurden. Zunächst sollten Sie die in den Target- und Tag-Schnittstellen verwendete Terminologie verstehen:

* **Aktivität**: Ein Satz von Erlebnissen, die auf eine oder mehrere Zielgruppen ausgerichtet sind. Ein einfacher A/B-Test könnte beispielsweise eine Aktivität mit zwei Erlebnissen sein.
* **Erlebnis**: Ein Satz von Aktionen, die auf einen oder mehrere Orte oder Entscheidungsbereiche ausgerichtet sind.
* **Entscheidungsbereich**: Ein Ort, an dem ein Target-Erlebnis bereitgestellt wird. Entscheidungsbereiche entsprechen &quot;Mboxes&quot;, wenn Sie mit älteren Target-Versionen vertraut sind.
* **Personalization-Entscheidung**: Eine Aktion, von der der Server bestimmt, dass ausgeführt werden soll. Diese Entscheidungen können auf Zielgruppenkriterien und der Priorisierung der Target-Aktivität basieren.
* **Vorschlag**: Das Ergebnis der vom Server getroffenen Entscheidungen, die in der Platform Web SDK-Antwort bereitgestellt werden. Ein Tausch eines Bannerbilds wäre beispielsweise ein Vorschlag.

### Aktualisieren der Aktion [!UICONTROL Ereignis senden]

Entscheidungen zur visuellen Personalisierung von Target werden vom Platform Web SDK bereitgestellt, wenn Target im Datastream aktiviert ist. _sie werden jedoch nicht automatisch gerendert_. Sie müssen die Aktion [!UICONTROL Ereignis senden] aktualisieren, um das automatische Rendering zu aktivieren.

1. Öffnen Sie in der Benutzeroberfläche [Datenerfassung](https://experience.adobe.com/#/data-collection){target="blank"} die Tag-Eigenschaft, die Sie für dieses Tutorial verwenden
1. Öffnen Sie die Regel `all pages - library loaded - send event - 50` .
1. Wählen Sie die Aktion `Adobe Experience Platform Web SDK - Send event` aus.
1. Aktivieren Sie **[!UICONTROL visuelle Personalisierungsentscheidungen rendern]** mit dem Kontrollkästchen

   ![Aktivieren Sie das Rendern visueller Personalisierungsentscheidungen](assets/target-rule-enable-visual-decisions.png)

<!--
1. In the **[!UICONTROL Datastream configuration overrides**] the **[!UICONTROL Target Property Token]** can be overridden either as a static value or with a data element. Only property tokens defined in the [**Advanced Property Token Overrides**](#advanced-pto) section in **Datastream Configuration** will return results.
   
   ![Override the Property Token](assets/target-property-token-ovrrides.png)
   -->

1. Speichern Sie Ihre Änderungen und erstellen Sie sie dann in Ihrer Bibliothek.

Durch die Einstellung der visuellen Personalisierungsentscheidungen beim Rendern wendet das Platform Web SDK automatisch alle Änderungen an, die mit dem Target Visual Experience Composer oder der &quot;globalen Mbox&quot;angegeben wurden.

>[!NOTE]
>
>In der Regel sollte die Einstellung [!UICONTROL visuelle Personalisierungsentscheidungen rendern] nur für eine einzelne Aktion &quot;Ereignis senden&quot;pro vollständigem Laden der Seite aktiviert werden. Wenn diese Einstellung für mehrere Aktionen vom Typ Ereignis senden aktiviert ist, werden nachfolgende Renderanforderungen ignoriert.

Wenn Sie diese Entscheidungen mithilfe von benutzerdefiniertem Code lieber selbst rendern oder bearbeiten möchten, können Sie die Einstellung [!UICONTROL visuelle Personalisierungsentscheidungen rendern] deaktivieren. Das Platform Web SDK ist flexibel und bietet diese Möglichkeit, Ihnen vollständige Kontrolle zu geben. Weitere Informationen zum manuellen Rendern personalisierter Inhalte finden Sie im Handbuch [ .](https://experienceleague.adobe.com/en/docs/experience-platform/edge/personalization/rendering-personalization-content)


### Target-Aktivität mit dem Visual Experience Composer einrichten

Nachdem der grundlegende Implementierungsabschnitt abgeschlossen ist, erstellen Sie eine Erlebnis-Targeting-Aktivität (XT) in Target, um zu überprüfen, ob alles ordnungsgemäß funktioniert. Wenn Sie Hilfe benötigen, lesen Sie das Target-Tutorial zum Erstellen von Erlebnis-Targeting-Aktivitäten](https://experienceleague.adobe.com/en/docs/target-learn/tutorials/activities/create-experience-targeting-activities).[

>[!NOTE]
>
>Wenn Sie Google Chrome als Browser verwenden, ist die [Visual Experience Composer (VEC) Helper-Erweiterung](https://experienceleague.adobe.com/en/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension) erforderlich, um die Site ordnungsgemäß zur Bearbeitung im VEC zu laden.

1. Navigieren zur Adobe Target-Benutzeroberfläche
1. Erstellen Sie eine Erlebnis-Targeting-Aktivität (XT) mit der Startseite &quot;Luma&quot;für die Aktivitäts-URL

   ![Erstellen einer neuen XT-Aktivität](assets/target-xt-create-activity.png)

1. Ändern Sie die Seite beispielsweise, indem Sie den Text im Hero Banner der Startseite ändern.  Wählen Sie abschließend **[!UICONTROL Speichern]** und dann **[!UICONTROL Weiter]** aus.

   ![Target VEC-Änderung](assets/target-xt-vec-modification.png)

1. Aktualisieren Sie den Ereignisnamen und wählen Sie dann **[!UICONTROL Weiter]** aus.

   ![Target VEC-Aktualisierungsereignis](assets/target-xt-vec-updateevent.png)

1. Wählen Sie Adobe Analytics als Berichtsquelle mit der entsprechenden Report Suite und der Bestellungsmetrik als Ziel aus.

   ![Target VEC-Berichtsquelle](assets/target-xt-vec-reportingsource.png)

   >[!NOTE]
   >
   >Wenn Sie Adobe Analytics nicht verwenden, wählen Sie Target als Berichtsquelle aus und wählen Sie stattdessen eine andere Metrik wie **Interaktion > Seitenansichten** . Zum Speichern und Anzeigen der Vorschau der Aktivität ist eine Zielmetrik erforderlich.

1. Speichern Sie die Aktivität
1. Wenn Sie mit Ihren Änderungen vertraut sind, können Sie Ihre Aktivität aktivieren. Wenn Sie andernfalls eine Vorschau des Erlebnisses ohne Aktivierung anzeigen möchten, können Sie die [QA-Vorschau-URL](https://experienceleague.adobe.com/en/docs/target/using/activities/activity-qa/activity-qa) kopieren.
1. Laden Sie die Startseite von Luma und Sie sollten sehen, wie Ihre Änderungen angewendet wurden.
1. Nach einigen Stunden sollten Target-Aktivitätsdaten und -konversionen in Adobe Analytics angezeigt werden. Detaillierte Informationen zur Berichterstellung von [Analytics for Target (A4T)](https://experienceleague.adobe.com/en/docs/target/using/integrate/a4t/reporting) finden Sie im Target-Handbuch.



### Validieren mit dem Debugger

Wenn Sie eine Aktivität einrichten, sollten Ihre Inhalte auf der Seite wiedergegeben werden. Selbst wenn keine Aktivitäten live sind, können Sie sich auch den Netzwerkaufruf &quot;Ereignis senden&quot;ansehen, um zu bestätigen, dass Target ordnungsgemäß konfiguriert ist.

>[!CAUTION]
>
>Wenn Sie Google Chrome verwenden und die Visual Experience Composer (VEC) Helper-Erweiterung ](https://experienceleague.adobe.com/en/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension) installiert ist, stellen Sie sicher, dass die Einstellung **Target-Bibliotheken einfügen** deaktiviert ist. [ Die Aktivierung dieser Einstellung führt zu zusätzlichen Target-Anforderungen.

1. Öffnen Sie die Adobe Experience Platform Debugger-Browsererweiterung
1. Wechseln Sie zur Demosite &quot;[Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html)&quot;und verwenden Sie den Debugger, um die Tag-Eigenschaft auf der Site in Ihre eigene Entwicklungseigenschaft zu ändern. ](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)[
1. Seite neu laden
1. Wählen Sie das Tool **[!UICONTROL Netzwerk]** im Debugger aus.
1. Filtern nach **[!UICONTROL Experience Platform Web SDK]**
1. Wählen Sie den Wert in der Ereigniszeile für den ersten Aufruf aus

   ![Netzwerkaufruf im Adobe Experience Platform-Debugger](assets/target-debugger-network.png)

1. Beachten Sie, dass es Schlüssel unter `query` > `personalization` gibt und `decisionScopes` den Wert `__view__` hat. Dieser Umfang entspricht dem Wert `target-global-mbox`. Bei diesem Platform Web SDK-Aufruf wurden Entscheidungen von Target angefordert.

   ![`__view__` decisionScope request](assets/target-debugger-view-scope.png)

1. Schließen Sie die Überlagerung und wählen Sie die Ereignisdetails für den zweiten Netzwerkaufruf aus. Dieser Aufruf ist nur vorhanden, wenn Target eine Aktivität zurückgegeben hat.
1. Beachten Sie, dass es Details zur Aktivität und zum Erlebnis gibt, die von Target zurückgegeben werden. Dieser Platform Web SDK-Aufruf sendet eine Benachrichtigung, dass eine Target-Aktivität an den Benutzer gerendert wurde, und erhöht eine Impression.

   ![Target Activity Impression](assets/target-debugger-activity-impression.png)

## Einrichten und Rendern eines benutzerdefinierten Entscheidungsbereichs

Benutzerdefinierte Entscheidungsbereiche (ehemals &quot;Mboxes&quot;) können verwendet werden, um HTML- oder JSON-Inhalte mit dem formularbasierten Experience Composer von Target strukturiert bereitzustellen. Inhalte, die an einen dieser benutzerdefinierten Bereiche gesendet werden, werden nicht automatisch vom Platform Web SDK gerendert. Sie kann mithilfe einer Aktion in Tags gerendert werden.

### Fügen Sie der Aktion [!UICONTROL Ereignis senden] einen Bereich hinzu.

Ändern Sie Ihre Seitenladeregel, um einen benutzerdefinierten Entscheidungsbereich hinzuzufügen:

1. Öffnen Sie die Regel `all pages - library loaded - send event - 50` .
1. Wählen Sie die Aktion `Adobe Experience Platform Web SDK - Send Event` aus.
1. Fügen Sie einen oder mehrere Bereiche hinzu, die Sie verwenden möchten. Verwenden Sie für dieses Beispiel `homepage-hero`.

   ![Benutzerdefinierter Umfang](assets/target-rule-custom-scope.png)

1. Speichern Sie Ihre Änderungen und erstellen Sie in Ihrer Bibliothek.

>[!TIP]
>
>Für dieses Tutorial verwenden Sie einen einzigen manuell definierten Bereich zu Demonstrationszwecken. Wenn Sie sich für die Verwendung mehrerer Entscheidungsbereiche entscheiden, die für bestimmte Seiten vorgesehen sind, sollten Sie in Erwägung ziehen, ein Datenelement zu verwenden, das abhängig vom Seitenpfad ein Array von Bereichen zurückgibt. Dieser Ansatz hilft, Ihre Implementierung einfach und skalierbar zu halten.

### Antwort von Target verarbeiten

Nachdem Sie das Platform Web SDK so konfiguriert haben, dass Inhalte für den Bereich `homepage-hero` angefordert werden, müssen Sie etwas mit der Antwort tun. Die Platform Web SDK-Tag-Erweiterung stellt ein [!UICONTROL Ereignis senden abgeschlossen] -Ereignis bereit, mit dem sofort eine neue Regel Trigger werden kann, wenn eine Antwort von einer [!UICONTROL Ereignis senden] -Aktion empfangen wird.

1. Erstellen Sie eine Regel mit dem Namen `homepage - send event complete - render homepage-hero`.
1. Fügen Sie der Regel ein Ereignis hinzu. Verwenden Sie die Erweiterung **Adobe Experience Platform Web SDK** und den Ereignistyp **[!UICONTROL Ereignis-Abschluss senden]** .
1. Fügen Sie eine Bedingung hinzu, um die Regel auf die Startseite von Luma zu beschränken (Pfad ohne Abfragezeichenfolge ist gleich `/content/luma/us/en.html`).
1. Fügen Sie der Regel eine Aktion hinzu. Verwenden Sie die Erweiterung **Adobe Experience Platform Web SDK** und den Aktionstyp **Vorschläge anwenden** .

   ![Render homepage hero rule](assets/target-rule-render-hero.png)

   >[!TIP]
   >
   >Geben Sie Ihren Regelereignissen, Bedingungen und Aktionen beschreibende Namen, anstatt die Standardnamen zu verwenden. Robuste Komponentennamen von Regeln machen die Suchergebnisse viel nützlicher.

1. Geben Sie `%event.propositions%` in das Feld Vorschläge ein, da wir das Ereignis &quot;Ereignis-Abschluss senden&quot;als Trigger für diese Regel verwenden.
1. Wählen Sie im Abschnitt &quot;Vorschlagsmetadaten&quot;die Option **[!UICONTROL Formular verwenden]**
1. Für das Feld **[!UICONTROL Perimeter]** geben Sie `homepage-hero` ein.
1. Für das Feld **[!UICONTROL Selektor]** geben Sie `div.heroimage` ein.
1. Wählen Sie für **[!UICONTROL Aktionstyp]** **[!UICONTROL HTML festlegen]** aus.
1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus

   ![Render homepage hero action](assets/target-action-render-hero.png)

   Zusätzlich zum Rendern der Aktivität müssen Sie einen zusätzlichen Aufruf an Target vornehmen, um anzugeben, dass die formularbasierte Aktivität gerendert wurde:

1. Fügen Sie der Regel eine weitere Aktion hinzu. Verwenden Sie die Erweiterung **Core** und den Aktionstyp **[!UICONTROL Benutzerspezifischer Code]** :
1. Fügen Sie den folgenden JavaScript-Code ein:

   ```javascript
   var propositions = event.propositions;
   var heroProposition;
   if (propositions) {
      // Find the hero proposition, if it exists.
      for (var i = 0; i < propositions.length; i++) {
         var proposition = propositions[i];
         if (proposition.scope === "homepage-hero") {
            heroProposition = proposition;
            break;
         }xw
      }
   }
   // Send a "display" event
   if (heroProposition !== undefined){
      alloy("sendEvent", {
         xdm: {
            eventType: "display",
            _experience: {
               decisioning: {
                  propositions: [{
                     id: heroProposition.id,
                     scope: heroProposition.scope,
                     scopeDetails: heroProposition.scopeDetails
                  }]
               }
            }
         }
      });
   }
   ```

   ![Render homepage hero action](assets/target-action-fire-display.png)

1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus

1. Speichern Sie Ihre Änderungen und erstellen Sie in Ihrer Bibliothek.
1. Laden Sie die Startseite von Luma einige Male, was ausreicht, um den neuen Entscheidungsbereich `homepage-hero` in der Target-Oberfläche zu registrieren.





### Target-Aktivität mit dem formularbasierten Experience Composer einrichten

Nachdem Sie jetzt über eine Regel verfügen, um einen benutzerdefinierten Entscheidungsbereich manuell zu rendern, können Sie eine weitere Erlebnis-Targeting-Aktivität (XT) in Target erstellen. Verwenden Sie diesmal den formularbasierten Experience Composer.

1. Öffnen Sie [Adobe Target](https://experience.adobe.com/target)
1. Deaktivieren Sie die für die vorherige Lektion verwendete Aktivität
1. Erstellen einer Erlebnis-Targeting-Aktivität (XT) mit der Option Form-Based Experience Composer

   ![Erstellen einer neuen XT-Aktivität](assets/target-xt-create-form-activity.png)

1. Wählen Sie den Speicherort **`homepage-hero`** aus der Dropdown-Liste &quot;Position&quot;und **[!UICONTROL HTML-Angebot erstellen]** aus der Dropdown-Liste &quot;Inhalt&quot;. Wenn der Speicherort nicht verfügbar ist, können Sie ihn eingeben. Target füllt regelmäßig neue Ortsnamen aus, nachdem Anforderungen für diesen Ort oder Bereich empfangen wurden.

   ![Erstellen einer neuen XT-Aktivität](assets/target-xt-form-activity.png)

1. Fügen Sie den folgenden Code in das Inhaltsfeld ein. Dieser Code ist ein einfaches Hero-Banner mit einem anderen Hintergrundbild:

   ```html
   <div class="we-HeroImage jumbotron" style="background-image: url('/content/luma/us/en/women/_jcr_content/root/hero_image.coreimg.jpeg');">
      <div class="container cq-dd-image">
         <div class="we-HeroImage-wrapper">
            <p class="h3">New Luma Yoga Collection</p>
            <strong class="we-HeroImage-title h1">Be active with style&nbsp;</strong>
            <p>
               <a class="btn btn-primary btn-action" href="/content/luma/us/en/products.html" role="button">Shop Now</a>
            </p>
         </div>
      </div>
   </div>
   ```

1. Wählen Sie im Schritt [!UICONTROL Ziele und Einstellungen] Adobe Target als Berichtsquelle und als Ziel [!UICONTROL Interaktion] > [!UICONTROL Seitenansichten] aus.
1. Speichern Sie die Aktivität
1. Wenn Sie mit Ihren Änderungen vertraut sind, können Sie Ihre Aktivität aktivieren. Wenn Sie andernfalls eine Vorschau des Erlebnisses ohne Aktivierung anzeigen möchten, können Sie die [QA-Vorschau-URL](https://experienceleague.adobe.com/en/docs/target/using/activities/activity-qa/activity-qa) kopieren.
1. Laden Sie die Startseite von Luma und Sie sollten sehen, wie Ihre Änderungen angewendet wurden.

>[!NOTE]
>
>Das Konversionsziel &quot;Auf mbox geklickt&quot;funktioniert nicht automatisch. Da das Platform Web SDK benutzerdefinierte Bereiche nicht automatisch rendert, werden Klicks nicht an Orte verfolgt, an denen Sie den Inhalt anwenden möchten. Sie können Ihr eigenes Klick-Tracking für jeden Bereich mit dem &quot;click&quot; `eventType` mit den entsprechenden `_experience` Details mithilfe der `sendEvent` -Aktion erstellen.

### Validieren mit dem Debugger

Wenn Sie Ihre Aktivität aktiviert haben, sollte Ihr Inhalt auf der Seite gerendert werden. Selbst wenn keine Aktivitäten live sind, können Sie sich auch den Netzwerkaufruf [!UICONTROL Ereignis senden] ansehen, um zu bestätigen, dass Target Inhalte für Ihre benutzerdefinierten Bereiche anfordert.

1. Öffnen Sie die Adobe Experience Platform Debugger-Browsererweiterung
1. Wechseln Sie zur Demosite &quot;[Luma&quot;](https://luma.enablementadobe.com/content/luma/us/en.html)&quot;und verwenden Sie den Debugger, um die Tag-Eigenschaft auf der Site in Ihre eigene Entwicklungseigenschaft zu ändern. ](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)[
1. Seite neu laden
1. Wählen Sie das Tool **[!UICONTROL Netzwerk]** im Debugger aus.
1. Filtern nach **[!UICONTROL Adobe Experience Platform Web SDK]**
1. Wählen Sie den Wert in der Ereigniszeile für den ersten Aufruf aus

   ![Netzwerkaufruf im Adobe Experience Platform-Debugger](assets/target-debugger-network.png)

1. Beachten Sie, dass es Schlüssel unter `query` > `personalization` gibt und `decisionScopes` wie zuvor den Wert `__view__` hat, aber jetzt ist auch ein `homepage-hero` -Bereich enthalten. Mit diesem Platform Web SDK-Aufruf wurden Entscheidungen von Target für Änderungen angefordert, die mit dem VEC und dem spezifischen `homepage-hero` -Speicherort vorgenommen wurden.

   ![`__view__` decisionScope request](assets/target-debugger-view-custom-scope.png)

1. Schließen Sie die Überlagerung und wählen Sie die Ereignisdetails für den zweiten Netzwerkaufruf aus. Dieser Aufruf ist nur vorhanden, wenn Target eine Aktivität zurückgegeben hat.
1. Beachten Sie, dass es Details zur Aktivität und zum Erlebnis gibt, die von Target zurückgegeben werden. Dieser Platform Web SDK-Aufruf sendet eine Benachrichtigung, dass eine Target-Aktivität an den Benutzer gerendert wurde, und erhöht eine Impression. Sie wurde durch die Aktion mit benutzerdefiniertem Code ausgelöst, die Sie zuvor hinzugefügt haben.

   ![Target Activity Impression](assets/target-debugger-activity-impression.png)

## Parameter an Target senden

In diesem Abschnitt übergeben Sie Target-spezifische Daten und sehen sich genauer an, wie XDM-Daten Target-Parametern zugeordnet werden.

### Seiten- (Mbox-)Parameter und XDM

Alle XDM-Felder werden automatisch als [Seitenparameter](https://experienceleague.adobe.com/en/docs/target-dev/developer/implementation/methods/page-parameters) oder Mbox-Parameter an Target übergeben.

Einige dieser XDM-Felder werden bestimmten Objekten im Target-Backend zugeordnet. Beispielsweise ist `web.webPageDetails.URL` automatisch verfügbar, um URL-basierte Targeting-Bedingungen zu erstellen, oder als `page.url` -Objekt, wenn Profilskripte erstellt werden.

Sie können Seitenparameter auch über das Datenobjekt hinzufügen.

### Spezielle Parameter und das Datenobjekt

Es gibt einige Datenpunkte, die für Target nützlich sein können und nicht vom XDM-Objekt zugeordnet sind. Zu diesen speziellen Target-Parametern gehören:

* [Profilattribute](https://experienceleague.adobe.com/en/docs/target-dev/developer/implementation/methods/in-page-profile-attributes)
* [Recommendations-Entitätsattribute](https://experienceleague.adobe.com/en/docs/target/using/recommendations/entities/entity-attributes)
* [Recommendations - reservierte Parameter](https://experienceleague.adobe.com/en/docs/target/using/recommendations/plan-implement#pass-behavioral)
* Kategoriewerte für [Kategorieaffinität](https://experienceleague.adobe.com/en/docs/target/using/audiences/visitor-profiles/category-affinity)

Diese Parameter müssen im Objekt `data` statt im Objekt `xdm` gesendet werden. Darüber hinaus können Seitenparameter (oder Mbox-Parameter) auch in das `data` -Objekt aufgenommen werden.

Um das Datenobjekt zu füllen, erstellen Sie das folgende Datenelement und verwenden Sie dabei die Datenelemente, die Sie in der Lektion [Datenelemente erstellen](create-data-elements.md) erstellt haben:

* **`data.content`** mit dem folgenden benutzerspezifischen Code:

  ```javascript
  var data = {
     __adobe: {
        target: {
           "entity.id": _satellite.getVar("product.productInfo.sku"),
           "entity.name": _satellite.getVar("product.productInfo.title"),
           "profile.loggedIn": _satellite.getVar("user.profile.attributes.loggedIn"),
           "user.categoryId": _satellite.getVar("product.category")
        }
     }
  }
  return data;
  ```



### Seitenladeregel aktualisieren

Das Übergeben zusätzlicher Daten für Target außerhalb des XDM-Objekts erfordert die Aktualisierung der entsprechenden Regeln. Für dieses Beispiel müssen Sie nur das neue Datenelement **data.content** in die generische Seitenladeregel und Produktseitenansichtsregel aufnehmen.

1. Öffnen Sie die Regel `all pages - library loaded - send event - 50` .
1. Wählen Sie die Aktion `Adobe Experience Platform Web SDK - Send event` aus.
1. Hinzufügen des Datenelements `data.content` zum Datenfeld

   ![Hinzufügen von Target-Daten zu Regel](assets/target-rule-data.png)

1. Speichern Sie Ihre Änderungen und erstellen Sie in Ihrer Bibliothek.

>[!NOTE]
>
>Im obigen Beispiel wird ein `data` -Objekt verwendet, das nicht vollständig mit allen Seitentypen gefüllt ist. Tags handhabt diese Situation ordnungsgemäß und lässt Schlüssel mit einem nicht definierten Wert aus. Beispielsweise würden `entity.id` und `entity.name` auf keinen Seiten außer Produktdetails weitergegeben.


## Aufteilen von Personalization- und Analytics-Anforderungen

Die Datenschicht auf der Site &quot;Luma&quot;ist vor dem Einbettungscode der Tags vollständig definiert. Auf diese Weise können wir einen einzigen Aufruf verwenden, um sowohl personalisierte Inhalte (z. B. aus Adobe Target) abzurufen als auch Analysedaten (z. B. an Adobe Analytics) zu senden.

Auf vielen Websites kann die Datenschicht jedoch nicht früh genug oder schnell genug geladen werden, um einen einzelnen Aufruf für beide Anwendungen zu verwenden. In diesen Situationen können Sie zwei Aktionen vom Typ [!UICONTROL Ereignis senden] beim Laden einer einzelnen Seite verwenden und die erste für die Personalisierung und die zweite für die Analyse verwenden. Wenn Sie die Ereignisse auf diese Weise aufschlüsseln, kann das Personalisierungsereignis so früh wie möglich ausgelöst werden, während darauf gewartet wird, dass die Datenschicht vollständig geladen wird, bevor das Analytics-Ereignis gesendet wird. Dies ähnelt vielen Implementierungen des Pre-Web-SDK, bei denen Adobe Target den `target-global-mbox` oben auf der Seite auslöst und Adobe Analytics den `s.t()` -Aufruf am unteren Seitenrand auslöst.

So erstellen Sie die Personalisierungsanforderung:

1. Öffnen Sie die Regel `all pages - library loaded - send event - 50` .
1. Öffnen Sie die Aktion **Ereignis senden** .
1. Wählen Sie **[!UICONTROL Geführte Ereignisse verwenden]** und dann **[!UICONTROL Personalisierung anfordern]** aus.
1. Dadurch wird der **Typ** als **[!UICONTROL Abrufen des Entscheidungsvorschlags]** gesperrt.

   ![send_decision_request_alone](assets/target-decision-request.png)

So erstellen Sie die Analytics-on-bottom-Anforderung:

1. Neue Regel mit dem Namen `all pages - page bottom - send event - 50` erstellen
1. Fügen Sie der Regel ein Ereignis hinzu. Verwenden Sie die Erweiterung **Core** und den Ereignistyp **[!UICONTROL Page Bottom]** .
1. Fügen Sie der Regel eine Aktion hinzu. Verwenden Sie die Erweiterung **Adobe Experience Platform Web SDK** und den Aktionstyp **Ereignis senden** .
1. Wählen Sie **[!UICONTROL Geführte Ereignisse verwenden]** und dann **[!UICONTROL Analyse erfassen]** aus.
1. Dadurch wird das Kontrollkästchen **[!UICONTROL Ausstehende Display-Benachrichtigungen einschließen]** gesperrt, damit die Anzeige-Benachrichtigung in der Warteschlange aus der Entscheidungsanfrage gesendet wird.

![send_decision_request_alone](assets/target-aa-request-guided.png)

>[!TIP]
>
>Wenn das Ereignis, für das Sie einen Entscheidungsvorschlag abrufen, kein Adobe Analytics-Ereignis nach hat, verwenden Sie den Ereignistyp **Geführter Ereignistyp** **[!UICONTROL Nicht geleitet - zeigen Sie alle Felder an]**. Sie müssen alle Optionen manuell auswählen. Dadurch wird jedoch die Option zum automatischen Senden einer Anzeigebenachrichtigung ]**zusammen mit Ihrer Abrufanforderung aufgehoben.**[!UICONTROL 


### Validieren mit dem Debugger

Nachdem die Regeln aktualisiert wurden, können Sie überprüfen, ob die Daten mithilfe des Adobe Debuggers korrekt übergeben wurden.

1. Navigieren Sie zur Demosite [Luma ](https://luma.enablementadobe.com/content/luma/us/en.html) und melden Sie sich mit der E-Mail-Adresse `test@adobe.com` und dem Kennwort `test` an.
1. Navigieren zu einer Produktdetailseite
1. Öffnen Sie die Adobe Experience Platform Debugger-Browsererweiterung und wechseln Sie [die Tag-Eigenschaft in Ihre eigene Entwicklungseigenschaft](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)
1. Seite neu laden
1. Wählen Sie das Tool **Netzwerk** im Debugger aus und filtern Sie nach **Adobe Experience Platform Web SDK**.
1. Wählen Sie den Wert in der Ereigniszeile für den ersten Aufruf aus
1. Beachten Sie, dass es Schlüssel unter `data` > `__adobe` > `target` gibt und sie mit Informationen zum Produkt, zur Kategorie und zum Anmeldestatus gefüllt werden.

   ![`__view__` decisionScope request](assets/target-debugger-data.png)

### Validierung in der Target-Oberfläche

Überprüfen Sie dann in der Target-Oberfläche, ob Daten empfangen wurden und für Zielgruppen und Aktivitäten verfügbar sind. XDM-Daten werden automatisch benutzerdefinierten Target-Parametern zugeordnet. Sie können überprüfen, ob XDM-Daten von Target empfangen wurden und durch Erstellen einer Zielgruppe verfügbar sind.

1. Öffnen Sie [Adobe Target](https://experience.adobe.com/target)
1. Navigieren Sie zum Abschnitt **[!UICONTROL Zielgruppen]** .
1. Erstellen Sie eine Zielgruppe und wählen Sie den Attributtyp **[!UICONTROL Benutzerdefiniert]** aus
1. Durchsuchen Sie das Feld **[!UICONTROL Parameter]** nach `web`. Das Dropdown-Menü sollte mit allen XDM-Feldern gefüllt werden, die sich auf die Webseitendetails beziehen.

   ![Validieren des benutzerdefinierten Attributs &quot;Target&quot;](assets/validate-in-target-customattribute.png)

Überprüfen Sie anschließend, ob das Profilattribut für den Anmeldestatus erfolgreich übergeben wurde.

1. Wählen Sie den Attributtyp **[!UICONTROL Besucherprofil]** aus
2. Suchen Sie nach `loggedIn`. Wenn das Attribut im Dropdown-Menü verfügbar ist, wurde das Attribut korrekt an Target übergeben. Es kann mehrere Minuten dauern, bis neue Attribute in der Target-Benutzeroberfläche verfügbar sind.

   ![Validieren in Target-Profil](assets/validate-in-target-profile.png)

Wenn Sie über Target Premium verfügen, können Sie auch überprüfen, ob die Entitätsdaten korrekt übergeben wurden und die Produktdaten in den Recommendations-Produktkatalog geschrieben wurden.

1. Navigieren Sie zum Abschnitt **[!UICONTROL Recommendations]** .
1. Wählen Sie im linken Navigationsbereich **[!UICONTROL Katalogsuche]** aus.
1. Suchen Sie nach der Produkt-SKU oder dem Produktnamen, den Sie zuvor auf der Site &quot;Luma&quot;besucht haben. Das Produkt sollte im Produktkatalog angezeigt werden. Es kann mehrere Minuten dauern, bis neue Produkte im Recommendations-Produktkatalog durchsucht werden können.

   ![Validieren in der Target-Katalogsuche](assets/validate-in-target-catalogsearch.png)

### Mit Assurance validieren

Darüber hinaus können Sie gegebenenfalls mithilfe von Assurance überprüfen, ob Target-Entscheidungsanfragen die richtigen Daten erhalten und ob serverseitige Umwandlungen korrekt durchgeführt werden. Sie können auch überprüfen, ob die Kampagnen- und Erlebnisinformationen in den Adobe Analytics-Aufrufen enthalten sind, selbst wenn die Target-Entscheidungsfindungs- und Adobe Analytics-Aufrufe separat gesendet werden.

1. Öffnen Sie [Assurance](https://experience.adobe.com/assurance) .
1. Starten Sie eine neue Sicherheitssitzung, geben Sie den **[!UICONTROL Sitzungsnamen]** ein und geben Sie die **[!UICONTROL Basis-URL]** für Ihre Site oder jede andere Seite ein, die Sie testen.
1. Klicken Sie auf **[!UICONTROL Weiter]**

   ![In neuer Sitzung validieren](assets/validate-in-assurance-newsession.png)

1. Wählen Sie Ihre Verbindungsmethode aus. In diesem Fall verwenden wir **[!UICONTROL Link kopieren]**
1. Kopieren Sie den Link und fügen Sie ihn in eine neue Browser-Registerkarte ein
1. Klicken Sie auf **[!UICONTROL Fertig]**

   ![Validieren Sie in der Zusicherung die Verbindung durch den Kopierlink.](assets/validate-in-assurance-copylink.png)

1. Nach dem Start Ihrer Assurance-Sitzung werden Ereignisse auf der Registerkarte &quot;Ereignisse&quot;angezeigt
1. Filtern nach &quot;tnta&quot;
1. Wählen Sie den letzten Aufruf aus und erweitern Sie die Nachrichten, um sicherzustellen, dass sie korrekt ausgefüllt sind, und notieren Sie die &quot;tnta&quot;-Werte.

   ![Validieren im sichernden Target-Treffer](assets/validate-in-assurance-targetevent.png)

1. Behalten Sie als Nächstes den Filter &quot;tnta&quot;bei und wählen Sie das Ereignis analytics.mapping aus, das nach dem soeben angezeigten Zielereignis auftritt.
1. Überprüfen Sie &quot;context.mappedQueryParams&quot;.\&lt;IhrSchemaName\>&quot;, um zu bestätigen, dass es ein &quot;tnta&quot;-Attribut mit einer verketteten Zeichenfolge enthält, die mit den &quot;tnta&quot;-Werten übereinstimmt, die im vorherigen Zielereignis gefunden wurden.

   ![Validieren in der Zuverlässigkeitsanalyse-Treffer](assets/validate-in-assurance-analyticsevent.png)

Dadurch wird bestätigt, dass die A4T-Informationen, die bei der Zielbestimmungsaufruf zur späteren Übertragung in die Warteschlange gestellt wurden, ordnungsgemäß gesendet wurden, wenn der Analytics-Tracking-Aufruf später auf der Seite ausgelöst wurde.

Nachdem Sie diese Lektion abgeschlossen haben, sollten Sie über eine funktionierende Implementierung von Adobe Target mit dem Platform Web SDK verfügen.

[Weiter: ](setup-web-channel.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
