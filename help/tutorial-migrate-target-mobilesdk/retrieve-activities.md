---
title: 'Abrufen von Target-Aktivitäten : Migrieren der Adobe Target-Implementierung in Ihrer Mobile App zur Offer Decisioning- und Target-Erweiterung'
description: Erfahren Sie, wie Sie Adobe Target-Aktivitäten bei der Migration von der Adobe Target zur Offer Decisioning- und Target Mobile-Erweiterung abrufen.
exl-id: 39569088-a254-4e64-9956-0c6e1a8ed2a5
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# Abrufen von Target-Aktivitäten

Mobile Target-Implementierungen verwenden regionale Mboxes (jetzt als „Bereiche“ bezeichnet), um Inhalte aus Aktivitäten bereitzustellen, die den formularbasierten Experience Composer von Target verwenden. Sie müssen Ihre Mobile App aktualisieren, um Bereiche in Ihre Netzwerkaufrufe aufzunehmen.

Der von Target zurückgegebene Inhalt, auch als „Angebote“ bezeichnet, besteht normalerweise aus Text oder JSON, den Sie in Ihrem Programm verwenden müssen, um das endgültige Kundenerlebnis zu rendern. Angebote aus Target werden häufig verwendet, um:

* Feature Flags in der Anwendung aktivieren
* Alternativtext oder -bilder bereitstellen

Wenn Sie über Aktivitäten verfügen, die sowohl in der Target-Erweiterung als auch in den Offer Decisioning- und Target-Erweiterungsversionen Ihres Programms ausgeführt werden müssen, sollten Sie diese gründlich testen. Wenn Sie verschiedene Angebote für verschiedene Versionen Ihrer App verwenden müssen, sollten Sie die Targeting-Optionen in der -Benutzeroberfläche verwenden, um verschiedene Angebote für die verschiedenen Versionen bereitzustellen.

Stellen Sie sicher, dass Sie eine Fehlerbehandlung einschließen, um unter Fehlerbedingungen geeignete Erlebnisse anzuzeigen.


## Anfordern und Anwenden von Inhalten bei Bedarf

>[!IMPORTANT]
>
>Nachdem Sie Inhalte auf die App angewendet haben, müssen Sie `displayed` API auslösen, damit Target weiß, dass der Besucher den in der Aktivität angegebenen alternativen oder Standardinhalt gesehen hat. Weitere Einzelheiten finden Sie auf [ Seite ](track-events.md)Verfolgen von Target-Konversionsereignissen“.


+++ Android-Beispiel

>[!BEGINTABS]

>[!TAB SDK optimieren]

```Java
// Mboxes for Target activities
final DecisionScope decisionScope1 = DecisionScope("myTargetMbox1");
final DecisionScope decisionScope2 = new DecisionScope("myTargetMbox2");
 
final List<DecisionScope> decisionScopes = new ArrayList<>();
decisionScopes.add(decisionScope1);
decisionScopes.add(decisionScope2);
 
// Prefetch the Target mboxes
Optimize.updatePropositions(decisionScopes,
                            new HashMap<String, Object>() {
                                {
                                    put("xdmKey", "xdmValue");
                                }
                            },
                            new HashMap<String, Object>() {
                                {
                                    put("dataKey", "dataValue");
                                }
                            },
                            new AdobeCallbackWithOptimizeError<Map<DecisionScope, OptimizeProposition>>() {
                                @Override
                                public void fail(AEPOptimizeError optimizeError) {
                                    // Log in case of error
                                    Log.d("Target Prefetch error", optimizeError.title);
                                }
 
                                @Override
                                public void call(Map<DecisionScope, OptimizeProposition> propositionsMap) {
                                    // Retrieve cached propositions if prefetch succeeds
                                    Optimize.getPropositions(scopes, new AdobeCallbackWithError<Map<DecisionScope, OptimizeProposition>>() {
                                        @Override
                                      public void fail(final AdobeError adobeError) {
                                              // handle error
                                        }
 
                                        @Override
                                        public void call(Map<DecisionScope, OptimizeProposition> propositionsMap) {
                                              if (propositionsMap != null && !propositionsMap.isEmpty()) {
                                                // get the propositions for the given decision scopes
                                                if (propositionsMap.contains(decisionScope1)) {
                                                      final OptimizeProposition proposition1 = propsMap.get(decisionScope1)
                                                      // read proposition1 offers and display them
                                                }
                                                if (propositionsMap.contains(decisionScope2)) {
                                                      final OptimizeProposition proposition2 = propsMap.get(decisionScope2)
                                                      // read proposition2 offers and display them
                                                }
                                              }
                                        }
                                      });
                                }
                            });
```

>[!ENDTABS]

+++

+++ iOS-Beispiel

>[!BEGINTABS]

>[!TAB SDK optimieren]

```Swift
// Mboxes for Target activities
let decisionScope1 = DecisionScope(name: "myTargetMbox1")
let decisionScope2 = DecisionScope(name: "myTargetMbox2")
 
// Prefetch the Target mboxes
Optimize.updatePropositions(for: [decisionScope1, decisionScope2]
                            withXdm: ["xdmKey": "xdmValue"]
                            andData: ["dataKey": "dataValue"]) { data, error in
            if let error = error as? AEPOptimizeError {
                // handle error
                return
            }
            // Retrieve cached propositions if prefetch succeeds
            Optimize.getPropositions(for: [decisionScope1, decisionScope2]) { propositionsDict, error in
                if let error = error {
                    // handle error
                    return
                }
 
                if let propositionsDict = propositionsDict {
                    // get the propositions for the given decision scopes
 
                    if let proposition1 = propositionsDict[decisionScope1] {
                        // read proposition1 offers and display them
                    }
 
                    if let proposition2 = propositionsDict[decisionScope2] {
                        // read proposition2 offers and display them
                    }
                }
            }
        }
```

>[!ENDTABS]

+++



Erfahren Sie als Nächstes, wie Sie [Target-Parameter mithilfe der Offer Decisioning- und Target-Erweiterung übergeben](send-parameters.md).

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Offer Decisioning- und Target-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625) posten.
