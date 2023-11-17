---
title: Lebenszyklusdaten
description: Erfahren Sie, wie Sie Lebenszyklusdaten in einer mobilen App erfassen.
exl-id: 75b2dbaa-2f84-4b95-83f6-2f38a4f1d438
source-git-commit: bc53cb5926f708408a42aa98a1d364c5125cb36d
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---

# Lebenszyklusdaten

Erfahren Sie, wie Sie Lebenszyklusdaten in einer mobilen App erfassen.

>[!INFO]
>
> Dieses Tutorial wird Ende November 2023 mithilfe einer neuen Beispiel-Mobile-App durch ein neues Tutorial ersetzt.

Die Adobe Experience Platform Mobile SDK Lifecycle-Erweiterung ermöglicht die Erfassung von Lebenszyklusdaten aus Ihrer mobilen App. Die Adobe Experience Platform Edge Network-Erweiterung sendet diese Lebenszyklusdaten an das Platform Edge Network, wo sie dann gemäß Ihrer Datenspeicherkonfiguration an andere Anwendungen und Dienste weitergeleitet werden. Weitere Informationen zum [Lebenszykluserweiterung](https://developer.adobe.com/client-sdks/documentation/lifecycle-for-edge-network/) in der Produktdokumentation.


## Voraussetzungen

* App erfolgreich erstellt und ausgeführt, wobei SDKs installiert und konfiguriert sind.
* Das Assurance-SDK wurde importiert.

  ```swift
  import AEPAssurance
  ```

* Registriert die Erweiterung &quot;Assurance&quot;, wie im Abschnitt [vorherige Lektion](install-sdks.md).

## Lernziele

In dieser Lektion werden Sie:

* Fügen Sie dem Schema die Feldergruppe Lebenszyklus hinzu.
* Aktivieren Sie genaue Lebenszyklusmetriken, indem Sie sie beim Wechsel zwischen Vordergrund und Hintergrund korrekt starten/anhalten.
* Senden Sie Daten aus der App an das Platform Edge Network.
* Validieren Sie in &quot;Assurance&quot;.

## Lebenszyklusfeldgruppe zum Schema hinzufügen

Die Feldergruppe &quot;Consumer Experience Event&quot;, die Sie im [vorherige Lektion](create-schema.md) bereits die Lebenszyklusfelder enthält, sodass Sie diesen Schritt überspringen können. Wenn Sie die Feldergruppe &quot;Consumer Experience Event&quot;nicht in Ihrer eigenen App verwenden, können Sie die Lebenszyklusfelder wie folgt hinzufügen:

1. Navigieren Sie zur Schema-Oberfläche, wie im Abschnitt [vorherige Lektion](create-schema.md).
1. Öffnen Sie das Schema &quot;Luma App&quot;und wählen Sie **[!UICONTROL Hinzufügen]**.
   ![Auswählen](assets/mobile-lifecycle-add.png)
1. Geben Sie in der Suchleiste &quot;Lebenszyklus&quot;ein.
1. Aktivieren Sie das Kontrollkästchen neben **[!UICONTROL AEP Mobile-Lebenszyklusdetails]**.
1. Wählen Sie **[!UICONTROL Feldergruppen hinzufügen]** aus.
   ![Feldergruppe hinzufügen](assets/mobile-lifecycle-lifecycle-field-group.png)
1. Wählen Sie **[!UICONTROL Speichern]** aus.
   ![Speichern](assets/mobile-lifecycle-lifecycle-save.png)


## Implementierungsänderungen

Jetzt können Sie aktualisieren `AppDelegate.swift` zum Registrieren der Lebenszyklusereignisse:

1. Wenn Ihre App beim Start aus einem Hintergrundstatus fortgesetzt wird, kann iOS Ihre `applicationWillEnterForeground:` delegate-Methode. Hinzufügen `lifecycleStart:`

   ```swift
   MobileCore.lifecycleStart(additionalContextData: nil)
   ```

1. Wenn die App in den Hintergrund gelangt, unterbrechen Sie die Erfassung der Lebenszyklusdaten aus der App. `applicationDidEnterBackground:` delegate-Methode.

   ```swift
   MobileCore.lifecyclePause()
   ```

>[!NOTE]
>
>Informationen zu iOS 13 und höher finden Sie im Abschnitt [Dokumentation](https://developer.adobe.com/client-sdks/documentation/mobile-core/lifecycle/#register-lifecycle-with-mobile-core-and-add-appropriate-startpause-calls) für etwas anderen Code.

## Validierung mit Versicherung

1. Überprüfen Sie die [Einrichtungsanweisungen](assurance.md) und verbinden Sie Ihren Simulator oder Ihr Gerät mit Assurance.
1. Starten Sie die App.
1. Senden Sie die App in den Hintergrund. Suchen Sie nach `LifecyclePause`.
1. App in den Vordergrund rücken Suchen Sie nach `LifecycleResume`.
   ![Lebenszyklus überprüfen](assets/mobile-lifecycle-lifecycle-assurance.png)


## Weiterleiten von Daten an Platform Edge Network

Die vorherige Übung sendet die Vordergrund- und Hintergrundereignisse an das Mobile SDK. Gehen Sie wie folgt vor, um diese Ereignisse an Platform Edge Network zu senden [here](https://developer.adobe.com/client-sdks/documentation/lifecycle-for-edge-network/#configure-a-rule-to-forward-lifecycle-metrics-to-platform). Sobald die Ereignisse an Platform Edge Network gesendet werden, werden sie gemäß Ihrer Datastream-Konfiguration an andere Anwendungen und Dienste weitergeleitet.

Nachdem Sie die Regel zum Senden der Lebenszyklusereignisse an Platform Edge Network hinzugefügt haben, sollte Folgendes angezeigt werden: `Application Close (Background)` und `Application Launch (Foreground)` Ereignisse, die XDM-Daten in Assurance enthalten.

![Lebenszyklus validieren, der an Platform Edge gesendet wird](assets/mobile-lifecycle-edge-assurance.png)



Weiter: **[Ereignisse verfolgen](events.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)