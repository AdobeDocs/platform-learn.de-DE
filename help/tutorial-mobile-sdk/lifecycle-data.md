---
title: Erfassen von Lebenszyklusdaten mit dem Platform Mobile SDK
description: Erfahren Sie, wie Sie Lebenszyklusdaten in einer mobilen App erfassen.
jira: KT-14630
exl-id: 75b2dbaa-2f84-4b95-83f6-2f38a4f1d438
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 2%

---

# Lebenszyklusdaten erfassen

Erfahren Sie, wie Sie Lebenszyklusdaten in einer mobilen App erfassen.

Die Adobe Experience Platform Mobile SDK Lifecycle-Erweiterung ermöglicht die Erfassung von Lebenszyklusdaten aus Ihrer mobilen App. Die Adobe Experience Platform Edge Network-Erweiterung sendet diese Lebenszyklusdaten an das Platform Edge Network, wo sie dann gemäß Ihrer Datenspeicherkonfiguration an andere Anwendungen und Dienste weitergeleitet werden. Weitere Informationen zum [Lebenszykluserweiterung](https://developer.adobe.com/client-sdks/documentation/lifecycle-for-edge-network/) in der Produktdokumentation.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind. Im Rahmen dieser Lektion haben Sie bereits mit der Lebenszyklusüberwachung begonnen. Siehe [Installieren von SDKs - Aktualisieren von AppDelegate](install-sdks.md#update-appdelegate) zu überprüfen.
* Registriert die Erweiterung &quot;Assurance&quot;, wie im Abschnitt [vorherige Lektion](install-sdks.md).

## Lernziele

In dieser Lektion werden Sie:

<!--
* Add lifecycle field group to the schema.
* -->
* Aktivieren Sie genaue Lebenszyklusmetriken, indem Sie sie beim Wechsel zwischen Vordergrund und Hintergrund korrekt starten/anhalten.
* Senden Sie Daten aus der App an das Platform Edge Network.
* Validieren Sie in &quot;Assurance&quot;.

<!--
## Add lifecycle field group to schema

The Consumer Experience Event field group you added in the [previous lesson](create-schema.md) already contains the lifecycle fields, so you can skip this step. If you don't use Consumer Experience Event field group in your own app, you can add the lifecycle fields by doing the following:

1. Navigate to the schema interface as described in the [previous lesson](create-schema.md).
1. Open the **Luma Mobile App Event Schema** schema and select **[!UICONTROL Add]** next to Field groups.
    ![select add](assets/lifecycle-add.png)
1. In the search bar, enter "lifecycle".
1. Select the checkbox next to **[!UICONTROL AEP Mobile Lifecycle Details]**.
1. Select **[!UICONTROL Add field groups]**.
    ![add field group](assets/lifecycle-lifecycle-field-group.png)
1. Select **[!UICONTROL Save]**.
    ![save](assets/lifecycle-lifecycle-save.png)
-->

## Implementierungsänderungen

Jetzt können Sie Ihr Projekt aktualisieren, um die Lebenszyklusereignisse zu registrieren.

1. Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL SceneDelegate]** im Xcode-Projektnavigator.

1. Wenn Ihre App beim Start aus einem Hintergrundstatus fortgesetzt wird, kann iOS Ihre `sceneWillEnterForeground:` -Delegierungsmethode verwenden. Hier möchten Sie ein Lebenszyklusstartereignis Trigger werden. Fügen Sie diesen Code zu `func sceneWillEnterForeground(_ scene: UIScene)`:

   ```swift
   // When in foreground start lifecycle data collection
   MobileCore.lifecycleStart(additionalContextData: nil)
   ```

1. Wenn die App in den Hintergrund gelangt, möchten Sie die Erfassung der Lebenszyklusdaten aus der App anhalten `sceneDidEnterBackground:` delegate-Methode. Fügen Sie diesen Code zu  `func sceneDidEnterBackground(_ scene: UIScene)`:

   ```swift
   // When in background pause lifecycle data collection
   MobileCore.lifecyclePause()
   ```

## Validierung mit Versicherung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md#connecting-to-a-session) -Abschnitt, um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Senden Sie die App in den Hintergrund. Suchen Sie nach **[!UICONTROL LifecyclePause]** -Ereignisse in der Assurance-Benutzeroberfläche.
1. App in den Vordergrund rücken Suchen Sie nach **[!UICONTROL LifecycleResume]** -Ereignisse in der Assurance-Benutzeroberfläche.
   ![Lebenszyklus überprüfen](assets/lifecycle-lifecycle-assurance.png)


## Weiterleiten von Daten an Platform Edge Network

Die vorherige Übung sendet die Vordergrund- und Hintergrundereignisse an das Adobe Experience Platform Mobile SDK. So leiten Sie diese Ereignisse an das Platform Edge Network weiter:

1. Auswählen **[!UICONTROL Regeln]** in der Eigenschaft &quot;Tags&quot;.
   ![Regel erstellen](assets/rule-create.png)
1. Auswählen **[!UICONTROL Ursprünglicher Build]** als zu verwendende Bibliothek.
1. Wählen Sie **[!UICONTROL Neue Regel erstellen]** aus.
   ![Neue Regel erstellen](assets/rules-create-new.png)
1. Im **[!UICONTROL Regel erstellen]** Bildschirm, Eingabe `Application Status` für **[!UICONTROL Name]**.
1. Auswählen ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** below **[!UICONTROL EREIGNISSE]**.
   ![Dialogfeld &quot;Regel erstellen&quot;](assets/rule-create-name.png)
1. Im **[!UICONTROL Ereigniskonfiguration]** step:
   1. Auswählen **[!UICONTROL Mobile Core]** als **[!UICONTROL Erweiterung]**.
   1. Auswählen **[!UICONTROL Vordergrund]** als **[!UICONTROL Ereignistyp]**.
   1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus.
      ![Regelereigniskonfiguration](assets/rule-event-configuration.png)
1. Zurück im **[!UICONTROL Regel erstellen]** Bildschirm, auswählen ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** neben **[!UICONTROL Mobile Core - Vordergrund]**.
   ![Nächste Ereigniskonfiguration](assets/rule-event-configuration-next.png)
1. Im **[!UICONTROL Ereigniskonfiguration]** step:
   1. Auswählen **[!UICONTROL Mobile Core]** als **[!UICONTROL Erweiterung]**.
   1. Auswählen **[!UICONTROL Hintergrund]** als **[!UICONTROL Ereignistyp]**.
   1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus.
      ![Regelereigniskonfiguration](assets/rule-event-configuration-background.png)
1. Zurück im **[!UICONTROL Regel erstellen]** Bildschirm, auswählen ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** darunter **[!UICONTROL AKTIONEN]**.
   ![Aktion zum Hinzufügen von Regeln](assets/rule-action-button.png)
1. Im **[!UICONTROL Aktionskonfiguration]** step:
   1. Auswählen **[!UICONTROL Adobe Experience Edge Network]** als **[!UICONTROL Erweiterung]**.
   1. Auswählen **[!UICONTROL Weiterleiten von Ereignissen an Edge Network]** als **[!UICONTROL Aktionstyp]**.
   1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus.
      ![Regelaktionskonfiguration](assets/rule-action-configuration.png)
1. Auswählen **[!UICONTROL In Bibliothek speichern]**.
   ![Regel - In Bibliothek speichern](assets/rule-save-to-library.png)
1. Auswählen **[!UICONTROL Build]** , um die Bibliothek neu zu erstellen.
   ![Regel - Build](assets/rule-build.png)

Nachdem Sie die Eigenschaft erfolgreich erstellt haben, werden die Ereignisse an Platform Edge Network gesendet und die Ereignisse gemäß Ihrer Datastream-Konfiguration an andere Anwendungen und Dienste weitergeleitet.

Sie sollten **[!UICONTROL Anwendungsbeendigung (Hintergrund)]** und **[!UICONTROL Application Launch (Vordergrund)]** Ereignisse, die XDM-Daten in Assurance enthalten.

![Lebenszyklus validieren, der an Platform Edge gesendet wird](assets/lifecycle-edge-assurance.png)

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass sie App-Zustandsereignisse (Vordergrund, Hintergrund) an das Adobe Experience Platform Edge Network und alle Dienste sendet, die Sie in Ihrem Datastream definiert haben.
>
> Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Tracking von Ereignisdaten](events.md)**
