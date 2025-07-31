---
title: Einrichten des Einverständnisses mit Platform Web SDK
description: Erfahren Sie, wie Sie die Datenschutzeinstellungen der Tag-Erweiterung "Experience Platform Web SDK" konfigurieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Tags,Consent
jira: KT-15413
exl-id: 502a7467-3699-4b2b-93bf-6b6069ea2090
source-git-commit: 7ccbaaf4db43921f07c971c485e1460a1a7f0334
workflow-type: tm+mt
source-wordcount: '1603'
ht-degree: 1%

---

# Einrichten des Einverständnisses mit Platform Web SDK

Erfahren Sie, wie Sie die Datenschutzeinstellungen der Tag-Erweiterung &quot;Adobe Experience Platform Web SDK&quot; konfigurieren. Legen Sie das Einverständnis basierend auf der Interaktion des Besuchers mit einem Banner von einer Einverständnisverwaltungs-Plattform (CMP) fest.

>[!NOTE]
> 
>Zu Demonstrationszwecken wird in diesem Tutorial [Klaro](https://klaro.org/) als CMP verwendet. Sie können Klaro oder den CMP, den Sie mit Ihrer Website verwenden, gerne folgen.


## Lernziele

Am Ende dieser Lektion können Sie:

* Laden einer CMP mithilfe von Tags
* Konfigurieren von Datenschutzeinstellungen in der Tag-Erweiterung &quot;Experience Platform Web SDK&quot;
* Festlegen des Einverständnisses für Experience Platform Web SDK basierend auf der Besucheraktion

## Voraussetzungen

Sie sollten mit Tags und den Schritten zum Erstellen von Regeln und Datenelementen, zum Erstellen von Bibliotheken in Umgebungen und zum Wechseln von Tag-Bibliotheken mithilfe des Experience Platform-Debuggers vertraut sein.

Bevor Sie mit der Konfiguration der Datenschutzeinstellungen und der Erstellung der Regeln zum Festlegen des Einverständnisses beginnen, stellen Sie sicher, dass Sie Ihr Einverständnisverwaltungs-Plattformskript auf der Website eingefügt haben und ordnungsgemäß funktioniert. Eine CMP kann entweder direkt im Quellcode mithilfe von Site-Entwicklern geladen werden oder über Tags selbst geladen werden. Diese Lehre zeigt den letztgenannten Ansatz.

>[!NOTE]
> 
>1. Eine Einverständnisverwaltungsplattform (oder CMP) wird von Unternehmen verwendet, um die Einverständnisentscheidungen eines Besuchers rechtlich zu dokumentieren und zu verwalten, bevor Besucherdaten aus Online-Quellen wie Websites und Programmen erfasst, freigegeben oder verkauft werden.
>
>2. Der empfohlene Ansatz für das Einfügen einer CMP ist direkt über den Quell-Code vor dem Tag-Manager-Skript.

### Klaro konfigurieren

Bevor Sie zu den Tag-Konfigurationen springen, erfahren Sie in diesem Tutorial Klaro mehr über die Einverständnisverwaltungsplattform.

1. Besuchen Sie [Klaro](https://klaro.org/) und richten Sie ein Konto ein.
1. Gehen Sie **Privacy Manager** und erstellen Sie eine Instanz entsprechend den Anweisungen.
1. Verwenden Sie den **Integrationscode**, um Klaro in Ihre Tag-Eigenschaft zu injizieren (Anweisungen befinden sich in der nächsten Übung).
1. Überspringen Sie den **Scannen**-Abschnitt, da er die Tag-Eigenschaft erkennt, die auf der Luma-Demo-Website hartcodiert ist und nicht die, die Sie für dieses Tutorial erstellt haben.
1. Fügen Sie einen Dienst mit dem Namen `aep web sdk` hinzu und schalten Sie auf **Standardstatus des Dienstes** um. Wenn diese Option aktiviert ist, wird der standardmäßige Einverständniswert `true`, andernfalls wird er `false`. Diese Konfiguration ist praktisch, wenn Sie entscheiden möchten, wie der standardmäßige Einverständnisstatus (vor dem Einverständnis des Besuchers) für Ihre Web-Anwendung aussehen soll. Beispiel:
   * Für CCPA wird im Allgemeinen das Standardeinverständnis auf `true` festgelegt. In diesem Tutorial werden Sie auf dieses Szenario als **implizites Opt-in** verweisen
   * Für die DSGVO ist die standardmäßige Einwilligung normalerweise auf `false` festgelegt. In diesem Tutorial werden Sie auf dieses Szenario als **implizites Opt-out** verweisen.

<!--
    This consent value can be verified by returning the JavaScript object ```klaro.getManager().consents``` in the browser's developer console.
-->
    >[!NOTE]
    >
    >Im Allgemeinen werden die oben genannten Schritte von dem Team oder der Person durchgeführt, die für die Handhabung der CMP verantwortlich ist, z. B. OneTrust oder TrustArc.

## Injizieren einer CMP

>[!WARNING]
>
>Die Best Practice zum Implementieren einer Einverständnisverwaltungsplattform besteht normalerweise darin, die CMP zu laden _bevor_ Sie Ihren Tag-Manager laden. Um dieses Tutorial zu vereinfachen, laden Sie die CMP _mit_ dem Tag-Manager. Diese Lektion soll Ihnen zeigen, wie Sie die Einverständnisfunktionen in Platform Web SDK verwenden können, und sollte nicht als Anleitung für die korrekte Konfiguration von Klaro oder anderen CMPs verwendet werden.


Nun, wenn Sie mit den Klaro-Konfigurationen fertig sind, erstellen Sie Tag-Regeln mit den folgenden Konfigurationen:

* [!UICONTROL Name]: `all pages - library load - Klaro`
* [!UICONTROL Ereignis]: [!UICONTROL Bibliothek geladen (Seitenanfang)] mit [!UICONTROL Erweiterte Optionen] > [!UICONTROL Reihenfolge] auf 1 gesetzt
* [!UICONTROL Action]: [!UICONTROL Benutzerdefinierter Code], [!UICONTROL Language]: HTML zum Laden des CMP-Skripts.

![CMP-Regel ](assets/consent-cmp-inject-rule-1.png)

Der benutzerdefinierte Code-Block sollte etwa wie folgt aussehen:

![CMP-Regel ](assets/consent-cmp-inject-rule-2.png)

Speichern und erstellen Sie nun diese Regel in Ihrer Entwicklungsbibliothek. Überprüfen Sie, ob das Einverständnisbanner angezeigt wird, indem Sie die Tag-Bibliothek von der Luma-Site zu Ihrer eigenen wechseln. Auf der Website sollte ein CMP-Banner angezeigt werden, wie unten dargestellt. Um die Einverständnisberechtigung des aktuellen Besuchers zu überprüfen, können Sie folgenden Code-Ausschnitt in der Browser-Konsole verwenden.

```javascript
    klaro.getManager().consents 
```

![Einverständnisbanner](assets/consent-cmp-banner.png)

Um in den Debugging-Modus zu wechseln, verwenden Sie das folgende Kontrollkästchen im Adobe Experience Platform-Debugger.

![Tag-Debugging-Modus](assets/consent-rule-debugging.png)

Außerdem müssen Sie Ihre Cookies und den lokalen Speicher möglicherweise mehrmals löschen, während Sie dieses Tutorial durchlaufen, da der Einverständniswert des Besuchers dort gespeichert wird. Sie können dies einfach wie folgt tun:

![Speicher wird gelöscht](assets/consent-clearning-cookies.png)

## Einverständnisszenarien

Datenschutzgesetze wie die DSGVO, der CCPA und andere spielen eine wichtige Rolle bei der Gestaltung der Einverständnisimplementierung. In dieser Lektion erfahren Sie, wie ein Besucher mit dem Einverständnisbanner unter zwei prominentesten Datenschutzgesetzen interagieren kann.
![Einverständnisszenarien](assets/consent-scenarios.jpeg)


### Szenario 1: Implizites Opt-in

Implizites Opt-in bedeutet, dass das Unternehmen die Zustimmung des Besuchers (oder das „Opt-in„) nicht einholen muss, bevor es seine Daten erfasst. Daher werden alle Besucher der Website standardmäßig als Opt-in behandelt. Der Besucher kann sich jedoch abmelden, indem er die Cookies über das Einverständnisbanner ablehnt. Dieser Anwendungsfall ähnelt dem CCPA.

Jetzt konfigurieren und implementieren Sie das Einverständnis für dieses Szenario:

1. Stellen Sie **[!UICONTROL Abschnitt Datenschutz]** der Tag-Erweiterung &quot;Experience Platform Web SDK&quot; sicher, dass **[!UICONTROL Standardeinverständnis]** auf **[!UICONTROL In]** festgelegt ist:


   ![Einverständniserweiterung für AEP - Datenschutzkonfiguration](assets/consent-web-sdk-privacy-in.png)

   >[!NOTE]
   > 
   >Bei einer dynamischen Lösung wählen Sie die Option „Datenelement bereitstellen“ und übergeben ein Datenelement, das den Wert von ```klaro.getManager().consents``` zurückgibt
   >
   >Diese Option wird verwendet, wenn die CMP in den Quell-Code (*)* Tag-Einbettungs-Code eingefügt wird, sodass das Standardeinverständnis verfügbar ist, bevor die Experience Platform Web SDK-Erweiterung geladen wird. In unserem Beispiel können wir diese Option nicht verwenden, da die CMP mit Tags und nicht vor Tags geladen wird.



2. Speichern und erstellen Sie diese Änderung in Ihrer Tag-Bibliothek
3. Laden Sie Ihre Tag-Bibliothek auf der Demo-Site von Luma .
4. Aktivieren Sie das Tags-Debugging auf der Luma-Site und laden Sie die Seite neu. In der Entwicklerkonsole Ihres Browsers sollten Sie sehen, dass „defaultConsent“ gleich &quot;**[!UICONTROL &quot;]**
5. Mit dieser Konfiguration stellt die Experience Platform Web SDK-Erweiterung weiterhin Netzwerkanfragen, es sei denn, ein Besucher entscheidet sich dafür, die Cookies abzulehnen und sich abzumelden:

   ![Einverständnis impliziert Opt-in](assets/consent-Implied-optin-default.png)



Wenn sich ein Besucher für ein Opt-out entscheidet (Tracking-Cookies ablehnen), müssen Sie sein Einverständnis in &quot;**[!UICONTROL &quot;]**. Ändern Sie die Einverständniseinstellung, indem Sie die folgenden Schritte ausführen:

<!--
1. Create a data element to store the consent value of the visitor. Let's call it `klaro consent value`. Use the code snippet to create a custom code type data element:
    
    ```javascript
    return klaro.getManager().consents["aep web sdk"]
    ```

    ![Data Element consent value](assets/consent-data-element-value.png)


1. Create another custom code data element, `consent confirmed`, with the following snippet which returns ```true``` only after a visitor confirms consent:

    
    ```javascript
    return klaro.getManager().confirmed
    ```

    ![Data Element consent confirmed](assets/consent-data-element-confirmed.png)
-->

1. Erstellen Sie eine Regel, die Trigger, wenn der Besucher auf &quot;**ablehnen** klickt.  Benennen Sie diese Regel wie folgt: `all pages - click consent banner - set consent "out"`

1. Verwenden Sie **[!UICONTROL Ereignis]** die Option **[!UICONTROL Klicken]** auf **[!UICONTROL Elemente, die mit der CSS-Auswahl übereinstimmen]** `#klaro .cn-decline`

   ![Regelbedingung - Benutzer klickt auf „Ich lehne ab“](assets/consent-optOut-clickEvent.png)

1. Verwenden Sie jetzt Experience Platform Web SDK, [!UICONTROL Einverständnis festlegen] [!UICONTROL Aktionstyp], um das Einverständnis als „out“ festzulegen:

   ![Aktion zum Opt-out von Einverständnisregeln](assets/consent-rule-optout-action.png)

1. Wählen Sie **[!UICONTROL In Bibliothek speichern und erstellen]**:

   ![Bibliothek speichern und erstellen](assets/consent-rule-optout-saveAndBuild.png)

Wenn sich ein Besucher jetzt abmeldet, wird die auf die oben beschriebene Weise konfigurierte Regel ausgelöst und die Web SDK-Zustimmung auf &quot;**[!UICONTROL &quot;]**.

Validieren Sie, indem Sie zur Demo-Site von Luma gehen, Cookies ablehnen und bestätigen, dass keine Web SDK-Anfrage nach der Abmeldung ausgelöst wird.

### Szenario 2: Implizites Opt-out


Implizites Opt-out bedeutet, dass Besucher standardmäßig als Opt-out behandelt und keine Cookies gesetzt werden sollten. Web-SDK-Anfragen sollten nur ausgelöst werden, wenn Besucherinnen und Besucher sich manuell anmelden, indem sie die Cookies über das Einverständnisbanner akzeptieren. Möglicherweise müssen Sie sich mit einem solchen Anwendungsfall in der Region der Europäischen Union befassen, in der die DSGVO gilt.

So können Sie die Konfiguration für ein implizites Opt-out-Szenario einrichten:

1. Schalten Sie in Klaro den **Service-Standardstatus** in Ihrem `aep web sdk`-Service aus und speichern Sie die aktualisierte Konfiguration.

1. Legen **[!UICONTROL im Abschnitt]** Datenschutz“ der Experience Platform Web SDK-Erweiterung das Standardeinverständnis auf **[!UICONTROL Out]** oder **[!UICONTROL Pending]** fest.

   ![Einverständniserweiterung für AEP - Datenschutzkonfiguration](assets/consent-implied-opt-out.png)

1. **Speichern** Sie die aktualisierte Konfiguration in Ihrer Tag-Bibliothek und erstellen Sie sie neu.

   Mit dieser Konfiguration stellt Experience Platform Web SDK sicher, dass keine Anfrage ausgelöst wird, es sei denn, die Einverständnisberechtigung ändert sich in **[!UICONTROL In]**. Dies kann vorkommen, wenn ein Besucher die Cookies manuell akzeptiert, indem er sich anmeldet.

1. Stellen Sie im Debugger sicher, dass die Luma-Site Ihrer Tag-Eigenschaft zugeordnet ist und dass die Tags-Konsolenprotokollierung aktiviert ist.
1. Verwenden Sie die Entwicklerkonsole Ihres Browsers, um **Site-Daten löschen** in **Anwendung** > **Speicher**

1. Laden Sie die Luma-Site neu. Sie sollten sehen, dass `defaultConsent` auf **[!UICONTROL Out]** eingestellt ist und keine Web SDK-Anfragen gestellt wurden

   ![IMPLIZIERTE EINVERSTÄNDNISERKLÄRUNG](assets/consent-implied-out-cmp.png)

Falls sich ein Besucher für das Opt-in entscheidet (Tracking-Cookies akzeptieren), müssen Sie sein Einverständnis ändern und auf &quot;**[!UICONTROL &quot;]**. Gehen Sie wie folgt vor, um dies mit einer Regel durchzuführen:

1. Erstellen Sie eine Regel, die Trigger erzeugt, wenn der Besucher **Das ist in Ordnung**.  Benennen Sie diese Regel wie folgt: `all pages - click consent banner - set consent "in"`

1. Verwenden Sie **[!UICONTROL Ereignis]** die Option **[!UICONTROL Klicken]** auf **[!UICONTROL Elemente, die mit der CSS-Auswahl übereinstimmen]** `#klaro .cm-btn-success`

   ![Regelbedingung - Benutzer klickt auf „Das ist OK“](assets/consent-optIn-clickEvent.png)

1. Fügen Sie eine Aktion mit der Experience Platform Web SDK [!UICONTROL Erweiterung], **[!UICONTROL Aktionstyp]** von **[!UICONTROL Einverständnis festlegen]**, **[!UICONTROL Allgemeines Einverständnis]** als **[!UICONTROL In]** hinzu.

   ![Opt-in-Aktion für Einverständnisregel](assets/consent-rule-optin-action.png)

   An dieser Stelle ist zu beachten, dass [!UICONTROL &#x200B; Aktion „Einverständnis festlegen] die erste Anfrage ist, die ausgeführt wird und eine Identität herstellt. Aus diesem Grund kann es wichtig sein, Identitäten bei der ersten Anfrage selbst zu synchronisieren. Die Identitätszuordnung kann zur Aktion [!UICONTROL Einverständnis festlegen“ hinzugefügt &#x200B;], indem ein Identitätstyp-Datenelement übergeben wird.

1. Wählen Sie **[!UICONTROL In Bibliothek speichern und erstellen]**:

   ![Opt-out von Einverständnisregeln](assets/consent-rule-optin-saveAndBuild.png)

1. **[!UICONTROL Speichern]** Sie die Regel in Ihrer Bibliothek und erstellen Sie sie neu.

Sobald Sie diese Regel eingerichtet haben, sollte die Ereignissammlung beginnen, wenn sich ein Besucher anmeldet.

![Option „Einverständnisnachrichtenbesucher“](assets/consent-post-user-optin.png)


Weitere Informationen zum Einverständnis in Web SDK finden Sie unter [Unterstützen von Voreinstellungen für das Einverständnis ](https://experienceleague.adobe.com/en/docs/experience-platform/edge/consent/supporting-consent).


Weitere Informationen zur Aktion [!UICONTROL Einverständnis festlegen] finden Sie unter [Einverständnis festlegen](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/web-sdk/action-types#set-consent).

>[!NOTE]
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese bitte auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
