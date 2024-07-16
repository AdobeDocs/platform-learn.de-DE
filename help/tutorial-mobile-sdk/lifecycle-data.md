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

Die Adobe Experience Platform Mobile SDK Lifecycle-Erweiterung ermöglicht die Erfassung von Lebenszyklusdaten aus Ihrer mobilen App. Die Adobe Experience Platform Edge Network-Erweiterung sendet diese Lebenszyklusdaten an das Platform-Edge Network, wo sie dann gemäß Ihrer Datenspeicherkonfiguration an andere Anwendungen und Dienste weitergeleitet werden. Weitere Informationen zur [Lebenszykluserweiterung](https://developer.adobe.com/client-sdks/documentation/lifecycle-for-edge-network/) finden Sie in der Produktdokumentation.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind. Im Rahmen dieser Lektion haben Sie bereits mit der Lebenszyklusüberwachung begonnen. Weitere Informationen finden Sie unter [Installieren von SDKs - Aktualisieren von AppDelegate](install-sdks.md#update-appdelegate) .
* Registrierte Erweiterung &quot;Assurance&quot;, wie in der vorherigen Lektion ](install-sdks.md) beschrieben.[

## Lernziele

In dieser Lektion werden Sie:

<!--
* Add lifecycle field group to the schema.
* -->
* Aktivieren Sie genaue Lebenszyklusmetriken, indem Sie sie beim Wechsel zwischen Vordergrund und Hintergrund korrekt starten/anhalten.
* Senden Sie Daten aus der App an Platform Edge Network.
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

1. Navigieren Sie im Xcode-Projektnavigator zu **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL SceneDelegate]** .

1. Wenn Ihre App beim Start aus einem Hintergrundstatus fortgesetzt wird, kann iOS Ihre `sceneWillEnterForeground:` -Delegierungsmethode aufrufen. In diesem Fall möchten Sie ein Lebenszyklusstartereignis Trigger haben. Fügen Sie diesen Code zu `func sceneWillEnterForeground(_ scene: UIScene)` hinzu:

   ```swift
   // When in foreground start lifecycle data collection
   MobileCore.lifecycleStart(additionalContextData: nil)
   ```

1. Wenn die App in den Hintergrund gelangt, möchten Sie die Erfassung der Lebenszyklusdaten aus der Delegate-Methode `sceneDidEnterBackground:` Ihrer App anhalten. Fügen Sie diesen Code zu `func sceneDidEnterBackground(_ scene: UIScene)` hinzu:

   ```swift
   // When in background pause lifecycle data collection
   MobileCore.lifecyclePause()
   ```

## Mit Assurance validieren

1. Lesen Sie den Abschnitt [Setup instructions](assurance.md#connecting-to-a-session) , um Ihren Simulator oder Ihr Gerät mit Assurance zu verbinden.
1. Senden Sie die App in den Hintergrund. Suchen Sie in der Assurance-Benutzeroberfläche nach **[!UICONTROL LifecyclePause]** -Ereignissen.
1. App in den Vordergrund rücken Suchen Sie in der Assurance-Benutzeroberfläche nach **[!UICONTROL LifecycleResume]** -Ereignissen.
   ![Lebenszyklus validieren](assets/lifecycle-lifecycle-assurance.png)


## Weiterleiten von Daten an Platform Edge Network

Die vorherige Übung sendet die Vordergrund- und Hintergrundereignisse an das Adobe Experience Platform Mobile SDK. So leiten Sie diese Ereignisse an Platform Edge Network weiter:

1. Wählen Sie **[!UICONTROL Regeln]** in der Eigenschaft &quot;Tags&quot;aus.
   ![Regel erstellen](assets/rule-create.png)
1. Wählen Sie **[!UICONTROL Ursprünglicher Build]** als Bibliothek aus, die verwendet werden soll.
1. Wählen Sie **[!UICONTROL Neue Regel erstellen]** aus.
   ![Neue Regel erstellen](assets/rules-create-new.png)
1. Geben Sie im Bildschirm **[!UICONTROL Regel erstellen]** den Wert `Application Status` für **[!UICONTROL Name]** ein.
1. Wählen Sie ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** unter **[!UICONTROL EREIGNISSE]** aus.
   ![Dialogfeld &quot;Regel erstellen&quot;](assets/rule-create-name.png)
1. Im Schritt **[!UICONTROL Ereigniskonfiguration]** :
   1. Wählen Sie **[!UICONTROL Mobile Core]** als **[!UICONTROL Erweiterung]** aus.
   1. Wählen Sie **[!UICONTROL Vordergrund]** als **[!UICONTROL Ereignistyp]** aus.
   1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus.
      ![Regelereigniskonfiguration](assets/rule-event-configuration.png)
1. Wählen Sie im Bildschirm **[!UICONTROL Regel erstellen]** die Option ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** neben **[!UICONTROL Mobile Core - Vordergrund]**.
   ![Nächste Ereigniskonfiguration](assets/rule-event-configuration-next.png)
1. Im Schritt **[!UICONTROL Ereigniskonfiguration]** :
   1. Wählen Sie **[!UICONTROL Mobile Core]** als **[!UICONTROL Erweiterung]** aus.
   1. Wählen Sie **[!UICONTROL Hintergrund]** als **[!UICONTROL Ereignistyp]** aus.
   1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus.
      ![Regelereigniskonfiguration](assets/rule-event-configuration-background.png)
1. Wählen Sie im Bildschirm **[!UICONTROL Regel erstellen]** die Option ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Hinzufügen]** unter **[!UICONTROL AKTIONEN]** aus.
   ![Aktion zum Hinzufügen von Regeln](assets/rule-action-button.png)
1. Im Schritt **[!UICONTROL Aktionskonfiguration]** :
   1. Wählen Sie **[!UICONTROL Adobe Experience Edge Network]** als **[!UICONTROL Erweiterung]** aus.
   1. Wählen Sie **[!UICONTROL Ereignis an Edge Network weiterleiten]** als **[!UICONTROL Aktionstyp]** aus.
   1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus.
      ![Konfiguration der Regelaktion](assets/rule-action-configuration.png)
1. Wählen Sie **[!UICONTROL In Bibliothek speichern]** aus.
   ![Regel - In Bibliothek speichern](assets/rule-save-to-library.png)
1. Wählen Sie **[!UICONTROL Build]** aus, um die Bibliothek neu zu erstellen.
   ![Regel - Build](assets/rule-build.png)

Nachdem Sie die Eigenschaft erfolgreich erstellt haben, werden die Ereignisse an Platform Edge Network gesendet und die Ereignisse gemäß Ihrer Datastream-Konfiguration an andere Anwendungen und Dienste weitergeleitet.

Es sollten die Ereignisse **[!UICONTROL Anwendungsbeendigung (Hintergrund)]** und **[!UICONTROL Anwendungsstart (Vordergrund)]** angezeigt werden, die XDM-Daten in Assurance enthalten.

![ Lebenszyklus validieren, der an Platform Edge gesendet wird](assets/lifecycle-edge-assurance.png)

>[!SUCCESS]
>
>Sie haben Ihre App jetzt so eingerichtet, dass sie App-Zustandsereignisse (Vordergrund, Hintergrund) an das Adobe Experience Platform-Edge Network und alle Dienste sendet, die Sie in Ihrem Datastream definiert haben.
>
> Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu künftigen Inhalten teilen möchten, teilen Sie diese auf diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Tracking von Ereignisdaten](events.md)**
