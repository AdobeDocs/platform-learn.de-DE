---
title: Rendern von Target-Aktivitäten - Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung
description: Erfahren Sie, wie Sie eine Adobe Target-Implementierung von at.js 2.x zu Adobe Experience Platform Web SDK migrieren. Zu den Themen gehören eine Übersicht über die Bibliothek, Implementierungsunterschiede und andere bemerkenswerte Hinweise.
exl-id: 39569088-a254-4e64-9956-0c6e1a8ed2a5
source-git-commit: 314f0279ae445f970d78511d3e2907afb9307d67
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Rendering Target-Aktivitäten

Einige Target-Implementierungen verwenden möglicherweise regionale Mboxes (jetzt als „Bereiche“ bezeichnet), um Inhalte aus Aktivitäten bereitzustellen, die den formularbasierten Experience Composer verwenden. Wenn Ihre at.js-Target-Implementierung Mboxes verwendet, müssen Sie Folgendes tun:

* Aktualisieren Sie alle Verweise aus Ihrer at.js-Implementierung, die `getOffer()` oder `getOffers()` zu den entsprechenden Platform Web SDK-Methoden verwenden.
* Fügen Sie Code zum Trigger eines `propositionDisplay` hinzu, damit eine Impression gezählt wird.

## Anfordern und Anwenden von Inhalten bei Bedarf

+++ Android-Beispiel

>[!BEGINTABS]

>[!TAB Target SDK]

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

>[!TAB Target SDK]

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


Aktivitäten, die mit dem formularbasierten Composer von Target erstellt und für regionale Mboxes bereitgestellt werden, können nicht automatisch von Platform Web SDK gerendert werden. Ähnlich wie at.js müssen Angebote, die an bestimmte Target-Speicherorte gesendet werden, nach Bedarf gerendert werden.



Erfahren Sie als Nächstes, wie Sie [Target-Parameter mithilfe der Platform Web SDK übergeben](send-parameters.md).

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
