---
title: Einrichten der Zustimmung mit dem Platform Web SDK
description: Erfahren Sie, wie Sie die Datenschutzeinstellungen der Experience Platform Web SDK-Tag-Erweiterung konfigurieren. Diese Lektion ist Teil des Tutorials „Implementieren von Adobe Experience Cloud mit Web SDK“.
feature: Web SDK,Tags,Consent
jira: KT-15413
exl-id: 502a7467-3699-4b2b-93bf-6b6069ea2090
source-git-commit: 8602110d2b2ddc561e45f201e3bcce5e6a6f8261
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 1%

---

# Einrichten der Zustimmung mit dem Platform Web SDK

Erfahren Sie, wie Sie die Datenschutzeinstellungen der Adobe Experience Platform Web SDK-Tag-Erweiterung konfigurieren. Legen Sie die Zustimmung basierend auf der Interaktion des Besuchers mit einem Banner von einer Consent Management Platform (CMP) fest.

>[!NOTE]
> 
>Zu Demonstrationszwecken verwendet dieses Tutorial [Klaro](https://klaro.org/) als CMP. Sie können gerne mit Klaro oder dem CMP weitermachen, den Sie mit Ihrer Website verwenden.


## Lernziele

Am Ende dieser Lektion können Sie:

* Laden einer CMP mithilfe von Tags
* Datenschutzeinstellungen in der Experience Platform Web SDK-Tag-Erweiterung konfigurieren
* Festlegen der Zustimmung für das Experience Platform Web SDK basierend auf der Aktion des Besuchers

## Voraussetzungen

Sie sollten mit Tags und den Schritten zum Erstellen von Regeln, Datenelementen, Erstellen von Bibliotheken in Umgebungen und Wechseln von Tag-Bibliotheken mithilfe des Experience Platform Debugger vertraut sein.

Bevor Sie mit der Konfiguration der Datenschutzeinstellungen und der Erstellung der Regeln zum Festlegen der Einwilligung beginnen, stellen Sie sicher, dass Sie Ihr Plattformskript für die Einwilligungsverwaltung auf die Website eingefügt haben und ordnungsgemäß funktionieren. Eine CMP kann entweder direkt mithilfe von Site-Entwicklern in den Quellcode geladen oder über Tags selbst geladen werden. Diese Lektion zeigt den letzteren Ansatz.

>[!NOTE]
> 
>1. Eine Consent Management Platform (oder CMP) wird von Organisationen verwendet, um die Einwilligungsoptionen eines Besuchers gesetzlich zu dokumentieren und zu verwalten, bevor Besucherdaten aus Online-Quellen wie Websites und Apps erfasst, weitergegeben oder verkauft werden.
>
>2. Der empfohlene Ansatz für die Injektion einer CMP erfolgt direkt über den Quellcode vor dem Tag-Manager-Skript.

### Klaro konfigurieren

Bevor Sie in die Tag-Konfigurationen springen, erfahren Sie mehr über die in diesem Tutorial Klaro verwendete Zustimmungsverwaltungsplattform.

1. Besuchen Sie [Klaro](https://klaro.org/) und richten Sie ein Konto ein.
1. Gehen Sie zu **Privacy Manager** und erstellen Sie eine Instanz gemäß den Anweisungen.
1. Verwenden Sie den **Integrationscode**, um Klaro in Ihre Tag-Eigenschaft einzufügen (Anweisungen finden Sie in der nächsten Übung).
1. Überspringen Sie den Abschnitt **Scannen** , da er die Tag-Eigenschaft erkennt, die auf der Demowebsite von Luma fest codiert ist, und nicht die Eigenschaft, die Sie für dieses Tutorial erstellt haben.
1. Fügen Sie einen Dienst mit dem Namen `aep web sdk` hinzu und schalten Sie den **Dienststandardstatus** ein. Wenn diese Option aktiviert ist, ist der Standardwert für die Zustimmung `true`, andernfalls ist er `false`. Diese Konfiguration ist nützlich, wenn Sie entscheiden möchten, welcher standardmäßige Zustimmungsstatus (vor der Zustimmung des Besuchers) für Ihre Webanwendung gelten soll. Beispiel:
   * Beim CCPA wird die Standardzustimmung normalerweise auf `true` gesetzt. Sie werden dieses Szenario in diesem Tutorial als **implizite Opt-in** referenzieren
   * Für die DSGVO wird die standardmäßige Zustimmung normalerweise auf `false` gesetzt. Sie werden dieses Szenario in diesem Tutorial als **implizites Opt-out** referenzieren.

<!--
    This consent value can be verified by returning the JavaScript object ```klaro.getManager().consents``` in the browser's developer console.
-->
    >[!HINWEIS]
    >
    >Im Allgemeinen werden die oben genannten Schritte vom Team oder von der Person durchgeführt und durchgeführt, die für die Verarbeitung des CMP verantwortlich ist, z. B. OneTrust oder TrustArc.

## CMP injizieren

>[!WARNING]
>
>Die Best Practice bei der Implementierung einer Consent Management Platform besteht normalerweise darin, den CMP _vor_ zu laden, um Ihren Tag-Manager zu laden. Um dieses Tutorial zu erleichtern, laden Sie den CMP _mit_ in den Tag-Manager. In dieser Lektion erfahren Sie, wie Sie die Zustimmungsfunktionen im Platform Web SDK verwenden. Sie sollte nicht als Anleitung zur korrekten Konfiguration von Klaro oder anderen CMP verwendet werden.


Nachdem Sie mit den Konfigurationen von Klaro fertig sind, erstellen Sie Tag-Regeln mit den folgenden Konfigurationen:

* [!UICONTROL Name]: `all pages - library load - Klaro`
* [!UICONTROL Ereignis]: [!UICONTROL Bibliothek geladen (Seitenanfang)] , wobei [!UICONTROL Erweiterte Optionen] > [!UICONTROL Reihenfolge] auf 1 gesetzt ist
* [!UICONTROL Aktion]: [!UICONTROL Benutzerspezifischer Code], [!UICONTROL Sprache]: HTML zum Laden des CMP-Skripts.

![CMP-Regel einfügen](assets/consent-cmp-inject-rule-1.png)

Der benutzerdefinierte Codeblock sollte in etwa wie folgt aussehen:

![CMP-Regel einfügen](assets/consent-cmp-inject-rule-2.png)

Speichern und erstellen Sie diese Regel jetzt in Ihrer Entwicklungsbibliothek. Überprüfen Sie, ob das Einwilligungsbanner angezeigt wird, indem Sie die Tag-Bibliothek von der Site &quot;Luma&quot;zu Ihrer eigenen wechseln. Auf der Website sollte ein CMP-Banner wie unten dargestellt angezeigt werden. Um die Zustimmung des aktuellen Besuchers zu überprüfen, können Sie folgendes Snippet in der Browser-Konsole verwenden.

```javascript
    klaro.getManager().consents 
```

![Einverständnisbanner](assets/consent-cmp-banner.png)

Um in den Debug-Modus zu wechseln, aktivieren Sie im Adobe Experience Platform-Debugger das folgende Kontrollkästchen.

![Tag-Debug-Modus](assets/consent-rule-debugging.png)

Außerdem müssen Sie möglicherweise während dieses Tutorials Ihre Cookies und Ihren lokalen Speicher mehrmals löschen, da der Wert für die Zustimmung des Besuchers dort gespeichert wird. Sie können dies einfach wie folgt tun:

![Speicher bereinigen](assets/consent-clearning-cookies.png)

## Einverständnisszenarios

Datenschutzgesetze wie die DSGVO, der CCPA und andere spielen eine entscheidende Rolle bei der Architektur der Implementierung der Einwilligung. In dieser Lektion erfahren Sie, wie ein Besucher mit dem Einwilligungsbanner unter zwei wichtigen Datenschutzaktionen interagieren kann.
![Einverständnisszenarien](assets/consent-scenarios.jpeg)


### Szenario 1: Implizites Opt-in

Das implizite Opt-in bedeutet, dass das Unternehmen vor der Erfassung seiner Daten keine Zustimmung des Besuchers (oder die &quot;Opt-in&quot;-Option) einholen muss und daher alle Besucher der Website standardmäßig als angemeldet behandelt werden. Der Besucher kann sich jedoch abmelden, indem er die Cookies über das Einwilligungsbanner ablehnt. Dieser Anwendungsfall ähnelt dem CCPA.

Jetzt konfigurieren und implementieren Sie die Zustimmung für dieses Szenario:

1. Stellen Sie im Abschnitt **[!UICONTROL Datenschutz]** der Experience Platform Web SDK-Tag-Erweiterung sicher, dass die **[!UICONTROL Standardzustimmung]** auf **[!UICONTROL In]** eingestellt ist:


   ![Datenschutzkonfiguration der AEP-Erweiterung zustimmen](assets/consent-web-sdk-privacy-in.png)

   >[!NOTE]
   > 
   >Wählen Sie für eine dynamische Lösung die Option &quot;Datenelement bereitstellen&quot;aus und übergeben Sie ein Datenelement, das den Wert ```klaro.getManager().consents``` zurückgibt.
   >
   >Diese Option wird verwendet, wenn der CMP im Quellcode *vor* des Tag-Einbettungscodes eingefügt wird, damit die standardmäßige Zustimmung verfügbar ist, bevor die Experience Platform Web SDK-Erweiterung geladen wird. In unserem Beispiel können wir diese Option nicht verwenden, da die CMP mit Tags und nicht vor Tags geladen wird.



2. Speichern und erstellen Sie diese Änderung in Ihrer Tag-Bibliothek.
3. Laden der Tag-Bibliothek auf der Demosite &quot;Luma&quot;
4. Aktivieren Sie das Debugging von Tags auf der Site &quot;Luma&quot;und laden Sie die Seite neu. In der Entwicklerkonsole Ihres Browsers sollte der Wert defaultConsent gleich **[!UICONTROL In]** sein.
5. Mit dieser Konfiguration sendet die Experience Platform Web SDK-Erweiterung weiterhin Netzwerkanforderungen, es sei denn, ein Besucher entscheidet, die Cookies abzulehnen und abzumelden:

   ![Einverständnisbezogene Opt-in](assets/consent-Implied-optin-default.png)



Wenn ein Besucher sich entscheidet, sich abzumelden (die Tracking-Cookies abzulehnen), müssen Sie die Zustimmung zu **[!UICONTROL Out]** ändern. Ändern Sie die Zustimmungseinstellung, indem Sie die folgenden Schritte ausführen:

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

1. Erstellen Sie eine Regel, die Trigger, wenn der Besucher auf **Ich lehne** klickt.  Benennen Sie diese Regel wie folgt: `all pages - click consent banner - set consent "out"`

1. Verwenden Sie als **[!UICONTROL Ereignis]** **[!UICONTROL Klick]** auf **[!UICONTROL Elemente, die mit dem CSS-Selektor übereinstimmen]** `#klaro .cn-decline`

   ![Regelbedingung Der Benutzer klickt auf &quot;Ich lehne ab&quot;](assets/consent-optOut-clickEvent.png)

1. Verwenden Sie jetzt das Experience Platform Web SDK, [!UICONTROL Setzen Sie die Einwilligung] [!UICONTROL Aktionstyp], um die Einwilligung auf &quot;out&quot;festzulegen:

   ![Opt-out-Aktion für Einwilligungsregeln](assets/consent-rule-optout-action.png)

1. Wählen Sie **[!UICONTROL In Bibliothek speichern und erstellen]**:

   ![Speichern und Erstellen Ihrer Bibliothek](assets/consent-rule-optout-saveAndBuild.png)

Wenn sich ein Besucher abmeldet, löst die oben konfigurierte Regel aus und legt die Web SDK-Zustimmung auf **[!UICONTROL Out]** fest.

Validieren Sie, indem Sie zur Site &quot;Luma Demo&quot;gehen, Cookies ablehnen und bestätigen Sie, dass keine Web SDK-Anforderung ausgelöst wird, nachdem Sie sich abgemeldet haben.

### Szenario 2: Implizites Opt-out


Implizites Opt-out bedeutet, dass Besucher standardmäßig als Opt-out behandelt werden und keine Cookies gesetzt werden sollten. Web SDK-Anfragen sollten nur ausgelöst werden, wenn sich Besucher manuell anmelden und die Cookies über das Zustimmungsbanner akzeptieren. Möglicherweise müssen Sie sich in der Region der Europäischen Union, in der die DSGVO gilt, mit einem solchen Anwendungsfall befassen.

So können Sie die Konfiguration für ein implizites Opt-out-Szenario einrichten:

1. Deaktivieren Sie in Klaro den Standardstatus **Dienst** in Ihrem `aep web sdk`-Dienst und speichern Sie die aktualisierte Konfiguration.

1. Stellen Sie im Abschnitt **[!UICONTROL Datenschutz]** der Experience Platform Web SDK-Erweiterung die Standardzustimmung auf **[!UICONTROL Out]** oder **[!UICONTROL Ausstehend]** ein.

   ![Datenschutzkonfiguration der AEP-Erweiterung zustimmen](assets/consent-implied-opt-out.png)

1. **Speichern** Sie die aktualisierte Konfiguration in Ihrer Tag-Bibliothek und erstellen Sie sie neu.

   Mit dieser Konfiguration stellt das Experience Platform Web SDK sicher, dass keine Anfrage ausgelöst wird, es sei denn, die Zustimmungsberechtigung ändert sich in **[!UICONTROL in]**. Dies kann daran liegen, dass ein Besucher die Cookies manuell akzeptiert, indem er sich anmeldet.

1. Stellen Sie im Debugger sicher, dass die Site &quot;Luma&quot;Ihrer Tag-Eigenschaft zugeordnet ist und dass die Protokollierung der Tags in der Konsole aktiviert ist.
1. Verwenden Sie die Entwicklerkonsole Ihres Browsers, um **Site-Daten löschen** in **Anwendung** > **Speicher** zu löschen.

1. Laden Sie die Site &quot;Luma&quot;neu und Sie sollten sehen, dass `defaultConsent` auf **[!UICONTROL Out]** festgelegt ist und keine Web SDK-Anfragen gesendet wurden.

   ![Einverständnisbezogene Abmeldung](assets/consent-implied-out-cmp.png)

Falls ein Besucher sich entscheidet, sich anzumelden (die Tracking-Cookies zu akzeptieren), müssen Sie die Zustimmung ändern und auf **[!UICONTROL In]** festlegen. So können Sie dies mit einer Regel durchführen:

1. Erstellen Sie eine Regel, die Trigger, wenn der Besucher auf **So ist es in Ordnung** klickt.  Benennen Sie diese Regel wie folgt: `all pages - click consent banner - set consent "in"`

1. Verwenden Sie als **[!UICONTROL Ereignis]** **[!UICONTROL Klick]** auf **[!UICONTROL Elemente, die mit dem CSS-Selektor übereinstimmen]** `#klaro .cm-btn-success`

   ![Regelbedingung Der Benutzer klickt auf &quot;In Ordnung&quot;](assets/consent-optIn-clickEvent.png)

1. Fügen Sie eine Aktion mit dem Experience Platform Web SDK [!UICONTROL Extension], **[!UICONTROL Aktionstyp]** von **[!UICONTROL Set consent]**, **[!UICONTROL General consent]** als **[!UICONTROL in]** hinzu.

   ![Opt-in-Aktion für Einwilligungsregeln](assets/consent-rule-optin-action.png)

   Beachten Sie hier, dass diese Aktion [!UICONTROL Einverständnis festlegen] die erste Anfrage sein wird, die gesendet wird und Identität feststellt. Daher kann es wichtig sein, Identitäten für die erste Anfrage selbst zu synchronisieren. Die Identitätszuordnung kann der Aktion [!UICONTROL Einverständnis festlegen] hinzugefügt werden, indem ein Datenelement vom Typ Identität übergeben wird.

1. Wählen Sie **[!UICONTROL In Bibliothek speichern und erstellen]**:

   ![Opt-out für Einwilligungsregeln](assets/consent-rule-optin-saveAndBuild.png)

1. **[!UICONTROL Speichern]** Sie die Regel in Ihrer Bibliothek und erstellen Sie sie neu.

Sobald Sie diese Regel eingerichtet haben, sollte die Erfassung von Ereignissen beginnen, wenn sich ein Besucher anmeldet.

![Post-Besucheroption zustimmen](assets/consent-post-user-optin.png)


Weitere Informationen zur Einwilligung im Web SDK finden Sie unter [Unterstützende Voreinstellungen für die Einwilligung von Kunden](https://experienceleague.adobe.com/en/docs/experience-platform/edge/consent/supporting-consent).


Weitere Informationen zur Aktion [!UICONTROL Einverständnis festlegen] finden Sie unter [Einverständnis festlegen](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/web-sdk/action-types#set-consent).

[Weiter: ](setup-event-forwarding.md)

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Web SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback teilen oder Anregungen zu künftigen Inhalten haben möchten, teilen Sie diese bitte in diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996) mit.
