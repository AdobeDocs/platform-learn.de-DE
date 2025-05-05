---
title: Installieren von Adobe Experience Platform Mobile SDKs
description: Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in einer App implementieren.
jira: KT-14627
exl-id: 98d6f59e-b8a3-4c63-ae7c-8aa11e948f59
source-git-commit: 3dd9c68203d0021e87caaa82bd962b3f9160a397
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 7%

---

# Installieren von Adobe Experience Platform Mobile SDKs {#tutorial_install_mobile_sdks}

>[!CONTEXTUALHELP]
>
>id="platform_mobile_sdk_tutorial_install"
>title="Installieren von Adobe Experience Platform Mobile SDKs"
>abstract="Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in einer App implementieren."

Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in einer App implementieren.

## Voraussetzungen

* Eine Tag-Bibliothek mit den in der vorherigen Lektion beschriebenen Erweiterungen wurde [ erstellt](configure-tags.md).
* Datei-ID der Entwicklungsumgebung aus der [Installationsanweisungen für Mobilgeräte](configure-tags.md#generate-sdk-install-instructions).
* Leere (Beispiel[App heruntergeladen ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}.
* Erfahrung mit [Xcode](https://developer.apple.com/xcode/){target="_blank"}.

## Lernziele

In dieser Lektion erfahren Sie Folgendes:

* Fügen Sie Ihrem Projekt die erforderlichen SDKs mithilfe von Swift Package Manager hinzu.
* Registrieren Sie die Erweiterungen.

>[!NOTE]
>
>In einer Mobile-App-Implementierung sind die Begriffe „Erweiterungen“ und „SDKs“ nahezu austauschbar.

## Swift Package Manager

Anstatt CocoaPods und eine Pod-Datei zu verwenden (wie unter [Generate SDK install instructions](./configure-tags.md#generate-sdk-install-instructions) beschrieben), fügen Sie einzelne Pakete mit dem nativen Swift Package Manager von Xcode hinzu. Dem Xcode-Projekt wurden bereits alle Paketabhängigkeiten hinzugefügt. Der Bildschirm Xcode **[!UICONTROL Paketabhängigkeiten]** sollte wie folgt aussehen:

![Xcode-Paketabhängigkeiten](assets/xcode-package-dependencies.png){zoomable="yes"}


In Xcode können Sie **[!UICONTROL Datei]** > **[!UICONTROL Pakete hinzufügen…]** verwenden. Die nachstehende Tabelle enthält Links zu den URLs, die Sie zum Hinzufügen von Paketen verwenden würden. Über die Links gelangen Sie zu weiteren Informationen zu den einzelnen Paketen.

| Paket | Beschreibung |
|---|---|
| [AEP-Core](https://github.com/adobe/aepsdk-core-ios) | Die `AEPCore`-, `AEPServices`- und `AEPIdentity`-Erweiterungen bilden die Grundlage des Adobe Experience Platform SDKS. Jede App, die SDK verwendet, muss diese Erweiterungen enthalten. Diese Module enthalten einen gemeinsamen Satz von Funktionen und Services, die für alle SDK-Erweiterungen erforderlich sind.<br/><ul><li>`AEPCore` enthält die Implementierung des Event Hub. Der Event Hub ist der Mechanismus, der zum Bereitstellen von Ereignissen zwischen der Mobile App und der SDK verwendet wird. Der Event Hub wird auch für die Datenfreigabe zwischen Erweiterungen verwendet.</li><li>`AEPServices` bietet mehrere wiederverwendbare Implementierungen, die für die Plattformunterstützung erforderlich sind, einschließlich Netzwerk, Festplattenzugriff und Datenbankverwaltung.</li><li>`AEPIdentity` implementiert die Integration mit Adobe Experience Platform Identity Services.</li><li>`AEPSignal` stellt die Signalerweiterung der Adobe Experience Platform SDKs dar, die es Marketing-Experten ermöglicht, ein „Signal“ an ihre Apps zu senden, um Daten an externe Ziele zu senden oder URLs zu öffnen.</li><li>`AEPLifecycle` stellt die Adobe Experience Platform SDKs-Lebenszykluserweiterung dar, mit der Lebenszyklusmetriken von Anwendungen wie Informationen zur Anwendungsinstallation oder -aktualisierung, Informationen zum Anwendungsstart und zur Sitzung, Geräteinformationen und zusätzliche vom Anwendungsentwickler bereitgestellte Kontextdaten erfasst werden können.</li></ul> |
| [AEP Edge](https://github.com/adobe/aepsdk-edge-ios) | Mit der Adobe Experience Platform Edge Network Mobile-Erweiterung (`AEPEdge`) können Sie Daten von einer Mobile App an das Adobe Edge-Netzwerk senden. Mit dieser Erweiterung können Sie Adobe Experience Cloud-Funktionen robuster implementieren, mehrere Adobe-Lösungen über einen Netzwerkaufruf bereitstellen und diese Informationen gleichzeitig an Adobe Experience Platform weiterleiten.<br/>Die Edge Network Mobile-Erweiterung ist eine Erweiterung für Adobe Experience Platform SDK und erfordert die `AEPCore`- und `AEPServices`-Erweiterungen für die Ereignisverarbeitung sowie die `AEPEdgeIdentity` zum Abrufen der Identitäten (z. B. ECID). |
| [AEP Edge Identity](https://github.com/adobe/aepsdk-edgeidentity-ios) | Die AEP Edge Identity Mobile Extension (`AEPEdgeIdentity`) ermöglicht die Verarbeitung von Benutzeridentitätsdaten aus einer Mobile App unter Verwendung der Adobe Experience Platform SDK und der Edge Network-Erweiterung. |
| [AEP - Edge-Einverständnis](https://github.com/adobe/aepsdk-edgeconsent-ios) | Die Mobile-Erweiterung der AEP-Einverständniserfassung (`AEPConsent`) ermöglicht die Erfassung von Einverständnisvoreinstellungen über die Mobile App bei Verwendung der Adobe Experience Platform SDK und der Edge Network-Erweiterung. |
| [AEP-Benutzerprofil](https://github.com/adobe/aepsdk-userprofile-ios) | Die Adobe Experience Platform User Profile Mobile-Erweiterung (`AEPUserProfile`) ist eine Erweiterung zur Verwaltung von Benutzerprofilen für die Adobe Experience Platform SDK. |
| [AEP-Orte](https://github.com/adobe/aepsdk-places-ios) | Mit der AEP Places-Erweiterung (`AEPPlaces`) können Sie Geolokalisierungsereignisse verfolgen, wie sie in der Adobe Places-Benutzeroberfläche und in den Tag-Regeln für das Adobe der Datenerfassung definiert sind. |
| [AEP-Messaging](https://github.com/adobe/aepsdk-messaging-ios) | Mit der AEP Messaging-Erweiterung (`AEPMessaging`) können Sie Push-Benachrichtigungs-Token und Clickthrough-Feedback für Push-Benachrichtigungen an die Adobe Experience Platform senden. |
| [AEP Optimize](https://github.com/adobe/aepsdk-optimize-ios) | Die AEP Optimize-Erweiterung (`AEPOptimize`) bietet APIs, um Echtzeit-Personalisierungs-Workflows in den Adobe Experience Platform Mobile SDKs mithilfe von Adobe Target oder Adobe Journey Optimizer Offer decisioning zu ermöglichen. Es sind `AEPCore`- und `AEPEdge`-Erweiterungen erforderlich, um Personalisierungsabfrageereignisse an das Experience Edge-Netzwerk zu senden. |
| [AEP Assurance](https://github.com/adobe/aepsdk-assurance-ios) | Assurance (auch als Griffon-Projekt bekannt) ist eine neue, innovative Erweiterung (`AEPAssurance`), mit der Sie die Datenerfassung und die Bereitstellung von Erlebnissen in Ihrer Mobile App untersuchen, testen, simulieren und validieren können. Diese Erweiterung aktiviert Ihre App für Assurance. |


## Erweiterungen importieren

Navigieren Sie in Xcode zu **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** und stellen Sie sicher, dass die folgenden Importe Teil dieser Quelldatei sind.

```swift
// import AEP MobileSDK libraries
import AEPCore
import AEPServices
import AEPIdentity
import AEPSignal
import AEPLifecycle
import AEPEdge
import AEPEdgeIdentity
import AEPEdgeConsent
import AEPUserProfile
import AEPPlaces
import AEPMessaging
import AEPOptimize
import AEPAssurance
```

Tun Sie dasselbe für **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]**.

## AppDelegate aktualisieren

Navigieren Sie im Xcode-Projekt **Navigator zu &#x200B;** [!DNL Luma]&#x200B;**>**&#x200B;[!DNL Luma]&#x200B;**>** AppDelegate.

1. Ersetzen Sie den `@AppStorage`-Wert, der für `environmentFileId` auf den Datei-ID-Wert der Entwicklungsumgebung `YOUR_ENVIRONMENT_ID_GOES_HERE` ist, den Sie von Tags in [Installationsanweisungen für SDK generieren](configure-tags.md#generate-sdk-install-instructions) abgerufen haben.

   ```swift
   @AppStorage("environmentFileId") private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"
   ```

1. Fügen Sie der `application(_, didFinishLaunchingWithOptions)`-Funktion den folgenden Code hinzu.

   ```swift
   // Define extensions
   let extensions = [
       AEPIdentity.Identity.self,
       Lifecycle.self,
       Signal.self,
       Edge.self,
       AEPEdgeIdentity.Identity.self,
       Consent.self,
       UserProfile.self,
       Places.self,
       Messaging.self,
       Optimize.self,
       Assurance.self
   ]
   
   // Register extensions
   MobileCore.registerExtensions(extensions, {
       // Use the environment file id assigned to this application via Adobe Experience Platform Data Collection
       Logger.aepMobileSDK.info("Luma - using mobile config: \(self.environmentFileId)")
       MobileCore.configureWith(appId: self.environmentFileId)
   
       // set this to false or comment it when deploying to TestFlight (default is false),
       // set this to true when testing on your device.
       MobileCore.updateConfigurationWith(configDict: ["messaging.useSandbox": true])
       if appState != .background {
           // only start lifecycle if the application is not in the background
           MobileCore.lifecycleStart(additionalContextData: nil)
       }
   
       // assume unknown, adapt to your needs.
       MobileCore.setPrivacyStatus(.unknown)
   })
   ```

Der obige Code bewirkt Folgendes:

1. Registriert die erforderlichen Erweiterungen.
1. Konfiguriert MobileCore und andere Erweiterungen für die Verwendung Ihrer Tag-Eigenschaftskonfiguration.
1. Aktiviert die Debug-Protokollierung. Weitere Informationen und Optionen finden Sie in der Dokumentation zu [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/).
1. Startet die Lebenszyklusüberwachung. Weitere [ finden Sie ](lifecycle-data.md) Schritt „Lebenszyklus“ im Tutorial .
1. Setzt das Standard-Einverständnis auf unbekannt. Weitere [ finden Sie ](consent.md) Schritt „Einverständnis“ im Tutorial .

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie `MobileCore.configureWith(appId: self.environmentFileId)` mit der `appId` aktualisieren, basierend auf der `environmentFileId` aus der Tag-Umgebung, für die Sie sie erstellen (Entwicklung, Staging oder Produktion).
>

>[!SUCCESS]
>
>Sie haben jetzt die erforderlichen Pakete installiert und Ihr Projekt aktualisiert, um die erforderlichen Adobe Experience Platform Mobile SDK-Erweiterungen, die Sie für den Rest des Tutorials verwenden werden, ordnungsgemäß zu registrieren.
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796?profile.language=de)

Weiter: **[Einrichten von Assurance](assurance.md)**
