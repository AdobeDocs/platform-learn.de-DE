---
title: Konversionsereignisse verfolgen - Migrieren der Adobe Target-Implementierung in Ihrer Mobile App zur Erweiterung Adobe Journey Optimizer - Decisioning
description: Erfahren Sie, wie Sie Adobe Target-Konversionsereignisse mithilfe der Adobe Journey Optimizer - Decisioning Mobile-Erweiterung verfolgen.
exl-id: 7b53aab1-0922-4d9f-8bf0-f5cf98ac04c4
source-git-commit: 4bc5323e1f406b1fc9524838978ba8673e33b44e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Tracking von Target-Konversionsereignissen mit der Decisioning Mobile-Erweiterung

Ziel der meisten Target-Aktivitäten ist es, wertvolle Benutzeraktionen in Ihrer Anwendung zu fördern, z. B. Käufe, Registrierung, Klicks und mehr. Target-Implementierungen verwenden häufig benutzerdefinierte Konversionsereignisse, um diese Aktionen zu verfolgen, die häufig zusätzliche Details zur Konversion enthalten. Konversionsereignisse für Target können mit Optimize SDK ähnlich wie Target SDK verfolgt werden. Spezifische APIs müssen aufgerufen werden, um Konversionsereignisse zu verfolgen, wie in der folgenden Tabelle dargestellt:

| Aktivitätsziel | Target-Erweiterung | Decisioning-Erweiterung |
|---|---|---|

| Verfolgen eines Ansichtskonversionsereignisses für einen Mbox-Speicherort (Umfang) | Rufen Sie die [displayLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}-API auf, wenn der mbox-Speicherort angezeigt wird | Rufen Sie die [Angezeigt](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}-API auf, wenn das Angebot für den mbox-Speicherort angezeigt wird. Dadurch wird ein Ereignis mit dem Ereignistyp decisioning.propositionDisplay an das Experience Edge-Netzwerk gesendet. |

| Verfolgen eines Klick-Konversionsereignisses für einen Mbox-Speicherort (Umfang) | Rufen Sie die [clickedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}-API in auf, wenn auf den mbox-Speicherort geklickt wird | Rufen Sie die [getippt](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}-API auf, wenn auf das Angebot für den mbox-Speicherort geklickt wird. Dadurch wird ein Ereignis mit dem Ereignistyp decisioning.propositionInteract an das Experience Edge-Netzwerk gesendet. |

| Verfolgen Sie ein benutzerdefiniertes Konversionsereignis, das auch zusätzliche Daten wie Zielgruppenprofilparameter und Bestelldetails enthalten kann |Übergeben Sie die zusätzlichen Daten in das TargetParameters-Feld, das von den APIs [displayLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} und [clickedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} bereitgestellt wird | Verwenden Sie die öffentlichen Methoden [generateDisplayInteractionXdm](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank} und [generateTapInteractionXdm](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank} im Angebot für den Mbox-Speicherort, um die XDM-formatierten Daten für Ansicht bzw. Klicken zu generieren. Rufen Sie dann die Edge SDK [sendEvent](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#sendevent){target=_blank}-API auf, um diese XDM-Tracking-Daten zusammen mit allen zusätzlichen XDM- und Freiformdaten an das Experience Edge-Netzwerk zu senden. |


Erfahren Sie als Nächstes, wie Sie [Audiences und Profilskripte aktualisieren](update-audiences.md) um die Kompatibilität mit der Decisioning-Erweiterung sicherzustellen.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
