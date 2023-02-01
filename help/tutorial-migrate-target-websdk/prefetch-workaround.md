---
title: Problemumgehung für den Vorabruf | Migrieren von Target von at.js 2.x zum Web SDK
description: Erfahren Sie, wie Sie eine Problemumgehung für die Übergabe von Parametern mit Vorabruf implementieren
source-git-commit: d061d2492d6d5e8e7a8a6e03ce63b9b6cd3793d8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Problemumgehung für den Vorabruf

Alle Target-Kunden, die vor dem 1. Oktober 2022 nicht mit dem Experience Platform Web SDK in Produktion waren, stellen mithilfe des Vorab-Modus eine Anfrage an Target vom Experience Platform Edge Network. Durch den Vorabruf kann der Browser Target-Angebote vorab laden und zwischenspeichern, damit sie angewendet werden können, wenn der Besucher den korrekten Status der Seite erreicht. Dies ist in Einzelseiten-Apps (SPA) von Vorteil, da das gewünschte Benutzererlebnis so schnell wie möglich ohne zusätzliche Netzwerkanforderungen gerendert werden kann. Es gibt jedoch wichtige Auswirkungen auf SPA und nicht SPA Implementierungen.

Anstatt einen Besucher in einer Aktivität zu zählen, wenn der Angebotsinhalt in der Netzwerkanforderung bereitgestellt wird, werden Besucher jetzt in Aktivitäten gezählt, wenn ein `propositionDisplay` sendEvent -Anfrage wird vom Web SDK ausgeführt. Diese Anfragen werden automatisch von Visual Experience Composer-Aktivitäten (VEC) durchgeführt, wenn renderDecisions auf &quot;true&quot;festgelegt ist und das Erlebnis erfolgreich auf der Seite wiedergegeben wurde. Bei benutzerdefinierten Bereichen und wenn renderDecisions auf false festgelegt ist, müssen die propositionDisplay-Anforderungen absichtlich vom Implementor initiiert werden. Außerdem _alle Parameter, die für andere Zwecke als die unmittelbare Aktivitätsqualifikation verwendet werden, müssen über eine `propositionDisplay`  event_.

## Warum ist die Problemumgehung erforderlich?

Bei vielen Target-Implementierungen werden manchmal wichtige Netzwerkanfragen gestellt, ohne dass erwartet wird, dass eine Aktivität bereitgestellt wird. Anfragen können beispielsweise an folgende Personen gerichtet werden:

* Konvertierungen von Aufträgen
* Profilparameter festlegen
* Profilskripte für Trigger
* Senden von Entitätsparametern zum Ausfüllen des Recommendations-Katalogs

Leider verhalten sich diese im Vorabruf-Modus nicht wie erwartet. Im Vorabruf-Modus werden diese Daten nur erfasst, wenn sie Teil einer `propositionDisplay`.

## Was ist die Problemumgehung?

Die Problemumgehung besteht aus drei Teilen:

1. Definieren Sie einen benutzerdefinierten Bereich als Teil Ihrer `sendEvent`
1. Verwenden Sie den benutzerdefinierten Bereich in einer formularbasierten Aktivität (die Aktivität kann Standardinhalte bereitstellen).
1. Verwenden Sie einen Antwort-Handler, um einen weiteren `sendEvent` für propositionDisplay und die Parameter einschließen, die Sie zum Erfassen der Bestellung, zum Festlegen der Profilparameter, zum Trigger des Profilskripts, zum Senden der Entitätsparameter usw. benötigen.

Hier ist beispielsweise ein Beispiel dafür, wie mit der Problemumgehung ein Profilparameter gesendet werden kann:


```JavaScript
var data = {
    "__adobe": {
        "target": {
            "profile.gender": "male"
        }
    }
};
// Send the initial event with the data object and custom decision scope
alloy("sendEvent", {
    "renderDecisions": true,
    data,
    decisionScopes: ['profile-param-example']
}).then(function(result) {
    var propositions = result.propositions;
    var ctaProposition;
    if (propositions) {
        // Find the discount proposition, if it exists.
        for (var i = 0; i < propositions.length; i++) {
            var proposition = propositions[i];
            if (proposition.scope === "profile-param-example") {
                ctaProposition = proposition;
                break;
            }
        }
    }
    if (ctaProposition) {
        // Send a "decisioning.propositionDisplay" event signaling that the proposition has been rendered, and includes the data object again
        alloy("sendEvent", {
            xdm: {
                eventType: "decisioning.propositionDisplay",
                _experience: {
                    decisioning: {
                        propositions: [{
                            id: ctaProposition.id,
                            scope: ctaProposition.scope,
                            scopeDetails: ctaProposition.scopeDetails
                        }]
                    }
                }
            },
            data
        });
    }
});
```

Wenn das Profil als Teil von propositionDisplay festgelegt wird, wird es im Profil des Besuchers gespeichert und ist in nachfolgenden Anfragen verfügbar. Derselbe Ansatz kann für die Berichterstellung von Details zur Bestellumwandlung und Entitätsparametern verwendet werden.

Verwenden Sie in -Tags den Ereignistyp &quot;Ereignis abschließen senden&quot;, um ein Ereignis mit dem zusätzlichen sendEvent-Ereignis Trigger.

## Woher weiß ich, ob meine Implementierung den Vorabruf-Modus verwendet?

Sie müssen ein Ticket für die Kundenunterstützung öffnen, um festzustellen, ob Ihr Konto den Vorabruf verwendet.


>[!NOTE]
>
>Wir unterstützen Sie bei der erfolgreichen Target-Migration von at.js zum Web SDK. Wenn Sie bei Ihrer Migration auf Probleme stoßen oder der Eindruck haben, dass wichtige Informationen in diesem Handbuch fehlen, teilen Sie uns dies bitte mit, indem Sie [diese Gemeinschaftsdiskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).