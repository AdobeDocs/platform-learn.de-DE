---
title: Konversionsereignisse verfolgen - Migrieren der Adobe Target-Implementierung in Ihrer Mobile App zur Offer Decisioning- und Target-Erweiterung
description: Erfahren Sie, wie Sie Adobe Target-Konversionsereignisse mit der Offer Decisioning- und Target Mobile-Erweiterung verfolgen.
exl-id: 7b53aab1-0922-4d9f-8bf0-f5cf98ac04c4
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Tracking von Target-Konversionsereignissen mit der Decisioning Mobile-Erweiterung

Ziel der meisten Target-Aktivitäten ist es, wertvolle Benutzeraktionen in Ihrer Anwendung zu fördern, z. B. Käufe, Registrierung, Klicks und mehr. Target-Implementierungen verwenden häufig benutzerdefinierte Konversionsereignisse, um diese Aktionen zu verfolgen, die häufig zusätzliche Details zur Konversion enthalten. Konversionsereignisse für Target können mit Optimize SDK ähnlich wie Target SDK verfolgt werden. Spezifische APIs müssen aufgerufen werden, um Konversionsereignisse zu verfolgen, wie in der folgenden Tabelle dargestellt:

| Aktivitätsziel | Target-Erweiterung | Offer Decisioning- und Target-Erweiterung |
|---|---|---|
| Verfolgen eines Ansichtskonversionsereignisses für einen Mbox-Speicherort (Umfang) | Rufen Sie die [displayLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}-API auf, wenn der mbox-Speicherort angezeigt wird | Rufen Sie die [Angezeigt](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank}-API auf, wenn das Angebot für den mbox-Speicherort angezeigt wird. Dadurch wird ein Ereignis mit dem Ereignistyp decisioning.propositionDisplay an das Experience Edge-Netzwerk gesendet. **Dies ist wichtig, um Besucher in Ihren Target-Aktivitäten zu erhöhen, und muss bei der Bereitstellung sowohl regulärer als auch standardmäßiger Target-Angebote erfolgen.** |
| Verfolgen eines Klick-Konversionsereignisses für einen Mbox-Speicherort (Umfang) | Rufen Sie die [clickedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}-API in auf, wenn auf den mbox-Speicherort geklickt wird | Rufen Sie die [getippt](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank}-API auf, wenn auf das Angebot für den mbox-Speicherort geklickt wird. Dadurch wird ein Ereignis mit dem Ereignistyp decisioning.propositionInteract an das Experience Edge-Netzwerk gesendet. |
| Verfolgen Sie ein benutzerdefiniertes Konversionsereignis, das auch zusätzliche Daten wie Zielgruppenprofilparameter und Bestelldetails enthalten kann | Übergeben Sie die zusätzlichen Daten in das TargetParameters-Feld, das von den APIs [displaysLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} und [clickedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} bereitgestellt wird | Verwenden Sie die öffentlichen Methoden [generateDisplayInteractionXdm](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank} und [generateTapInteractionXdm](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank} im Angebot für den Mbox-Speicherort, um die XDM-formatierten Daten für Ansicht bzw. Klicken zu generieren. Rufen Sie dann die Edge SDK [sendEvent](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#sendevent){target=_blank}-API auf, um diese XDM-Tracking-Daten zusammen mit allen zusätzlichen XDM- und Freiformdaten an das Experience Edge-Netzwerk zu senden. |


Erfahren Sie als Nächstes, wie Sie [Zielgruppen und Profilskripte aktualisieren](update-audiences.md) um die Kompatibilität mit der Offer Decisioning- und Target-Erweiterung sicherzustellen.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=de#M463) posten.
