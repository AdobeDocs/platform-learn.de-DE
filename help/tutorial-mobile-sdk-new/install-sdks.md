---
title: Installieren von Adobe Experience Platform Mobile SDKs
description: Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in eine Mobile App implementieren.
hide: true
source-git-commit: e364d70375f687b9c50691efd04a1db757fee364
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 1%

---

# Installieren von Adobe Experience Platform Mobile SDKs

Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in eine Mobile App implementieren.

## Voraussetzungen

* Erfolgreich erstellte Tag-Bibliothek mit den Erweiterungen, die im Abschnitt [vorherige Lektion](configure-tags.md).
* Entwicklungsumgebung - Datei-ID aus [Installationsanweisungen für Mobilgeräte](configure-tags.md#generate-sdk-install-instructions).
* Heruntergeladen, leer [Beispielanwendung](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}.
* Erlebnis mit [XCode](https://developer.apple.com/xcode/){target="_blank"}.

## Lernziele

In dieser Lektion werden Sie:

* Fügen Sie Ihrem Projekt mithilfe des Swift Package Manager die erforderlichen SDKs hinzu.
* Registrieren Sie die Erweiterungen.

>[!NOTE]
>
>In einer Mobile-App-Implementierung sind die Begriffe &quot;Erweiterungen&quot;und &quot;SDKs&quot;nahezu austauschbar.

## Swift Package Manager

Anstatt CocoaPods zu verwenden und eine Pod-Datei zu verwenden (wie in den Installationsanweisungen für Mobilgeräte beschrieben), lesen Sie [SDK-Installationsanweisungen generieren](./configure-tags.md#generate-sdk-install-instructions)), fügen Sie mithilfe des nativen Swift Package Manager von Xcode einzelne Pakete hinzu.

Verwenden Sie in Xcode **[!UICONTROL Datei]** > **[!UICONTROL Pakete hinzufügen...]** und installieren Sie alle Pakete, die in der folgenden Tabelle aufgeführt sind. Wählen Sie den Link des Pakets in der Tabelle aus, um die vollständige URL für das spezifische Paket zu erhalten.

| Package | Beschreibung |
|---|---|
| [AEP Core](https://github.com/adobe/aepsdk-core-ios.git) | Die `AEPCore`, `AEPServices`, und `AEPIdentity` Erweiterungen stellen die Grundlage des Adobe Experience Platform SDK dar - jede App, die das SDK verwendet, muss sie enthalten. Diese Module enthalten einen gemeinsamen Satz von Funktionen und Diensten, die für alle SDK-Erweiterungen erforderlich sind.<br/>`AEPCore` enthält die Implementierung des Ereignis-Hub. Der Ereignis-Hub ist der Mechanismus zur Bereitstellung von Ereignissen zwischen der App und dem SDK. Der Ereignis-Hub wird auch zum Freigeben von Daten zwischen Erweiterungen verwendet.<br/>`AEPServices` bietet mehrere wiederverwendbare Implementierungen, die für die Plattformunterstützung erforderlich sind, einschließlich Netzwerk, Festplattenzugriff und Datenbankverwaltung.<br/>`AEPIdentity` implementiert die Integration mit Adobe Experience Platform Identity-Diensten.<br/>`AEPSignal` stellt die Signal-Erweiterung des Adobe Experience Platform SDK dar, mit der Marketing-Experten ein &quot;Signal&quot;an ihre Apps senden können, um Daten an externe Ziele zu senden oder URLs zu öffnen.<br/>`AEPLifecycle` stellt die Lebenszykluserweiterung des Adobe Experience Platform SDK dar, die die Erfassung von Lebenszyklusmetriken für Anwendungen wie Informationen zur Anwendungsinstallation oder -aktualisierung, zum Anwendungsstart und zu Sitzungsinformationen, Geräteinformationen und zusätzlichen Kontextdaten, die vom Anwendungsentwickler bereitgestellt werden, unterstützt. |
| [AEP Edge](https://github.com/adobe/aepsdk-edge-ios.git) | Mit der mobilen Adobe Experience Platform Edge Network-Erweiterung können Sie Daten von einer Mobile App an das Adobe Edge-Netzwerk senden. Mit dieser Erweiterung können Sie Adobe Experience Cloud-Funktionen robuster implementieren, mehrere Adobe-Lösungen über einen Netzwerkaufruf bereitstellen und diese Informationen gleichzeitig an die Adobe Experience Platform weiterleiten.<br/>Die mobile Edge Network-Erweiterung ist eine Erweiterung für das Adobe Experience Platform SDK und erfordert die `AEPCore` und `AEPServices` Erweiterungen für die Ereignisverarbeitung sowie die `AEPEdgeIdentity` Erweiterung zum Abrufen der Identitäten, z. B. ECID. |
| [AEP Edge Identity](https://github.com/adobe/aepsdk-edgeidentity-ios.git) | Die mobile AEP Edge Identity-Erweiterung ermöglicht die Verarbeitung von Benutzeridentitätsdaten aus einer Mobile App bei Verwendung des Adobe Experience Platform SDK und der Edge Network-Erweiterung. |
| [Zustimmung zu AEP Edge](https://github.com/adobe/aepsdk-edgeconsent-ios.git) | Die mobile Erweiterung &quot;AEP Consent Collection&quot;ermöglicht die Erfassung von Zustimmungsvoreinstellungen von der Mobile App bei Verwendung des Adobe Experience Platform SDK und der Edge Network-Erweiterung. |
| [AEP-Benutzerprofil](https://github.com/adobe/aepsdk-userprofile-ios.git) | Die Adobe Experience Platform User Profile Mobile-Erweiterung ist eine Erweiterung zur Verwaltung von Benutzerprofilen für das Adobe Experience Platform SDK. |
| [AEP Places](https://github.com/adobe/aepsdk-places-ios) | Die Adobe Experience Platform Places-Erweiterung ist eine Erweiterung für das Adobe Experience Platform Swift SDK. Mit der AEVPlaces-Erweiterung können Sie Geolocation-Ereignisse wie in der Adobe Places-Benutzeroberfläche und in Adobe Launch-Regeln definiert verfolgen. |
| [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios.git) | Die AEP Messaging-Erweiterung ist eine Erweiterung für das Adobe Experience Platform Swift SDK. Mit der AEP Messaging-Erweiterung können Sie Push-Benachrichtigungstoken und Push-Benachrichtigungs-Clickthrough-Feedback an die Adobe Experience Platform senden. |
| [AEP Optimize](https://github.com/adobe/aepsdk-optimize-ios) | Die AEP Optimize-Erweiterung stellt APIs bereit, um Echtzeit-Personalisierungs-Workflows in den Adobe Experience Platform Mobile SDKs mithilfe von Adobe Target oder Adobe Journey Optimizer Offer decisioning zu ermöglichen. Sie erfordert `AEPCore` und `AEPEdge` Erweiterungen zum Senden von Personalisierungsabfrageereignissen an das Experience Edge-Netzwerk. |
| [AEP-Sicherheit](https://github.com/adobe/aepsdk-assurance-ios.git) | Assurance (auch bekannt als Projekt Griffon) ist ein neues, innovatives Produkt, mit dem Sie die Erfassung, den Testversand, die Simulation und die Validierung von Daten und die Bereitstellung von Erlebnissen in Ihrer App überprüfen und testen können. |


Nachdem Sie alle Pakete installiert haben, Ihr Xcode **[!UICONTROL Paketabhängigkeiten]** Der Bildschirm sollte wie folgt aussehen:

![Abhängigkeiten von Xcode-Paketen](assets/xcode-package-dependencies.png)


## Importieren von Erweiterungen

Navigieren Sie in Xcode zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL AppDelegate]** und fügen Sie die folgenden Importe hinzu.

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

Tun Sie dasselbe für **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Utils]** > **[!UICONTROL MobileSDK]**.

## AppDelegate aktualisieren

Navigieren Sie zu **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **AppDelegate** im Xcode-Projektnavigator.

1. Legen Sie die `@AppStorage` Wert für `environmentFileId` zum Wert der Datei-ID der Entwicklungsumgebung hinzufügen, den Sie aus den Tags in Schritt 6 unter [SDK-Installationsanweisungen generieren](configure-tags.md#generate-sdk-install-instructions).

   ```swift
   @AppStorage("environmentFileId") private var environmentFileId = "b5cbd1a1220e/1857ef6cacb5/launch-2594f26b23cd-development"
   ```

1. Fügen Sie den folgenden Code zum `application(_, didFinishLaunchingWithOptions)` -Funktion.

   ```swift
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
   
       // update version and build
       Logger.configuration.info("Luma - Updating version and build number...")
       SettingsBundleHelper.setVersionAndBuildNumber()
   })
   ```

Der obige Code führt Folgendes aus:

1. Registriert die erforderlichen Erweiterungen.
1. Konfiguriert MobileCore und andere Erweiterungen für die Verwendung Ihrer Tag-Eigenschaftenkonfiguration.
1. Aktiviert die Debug-Protokollierung. Weitere Informationen und Optionen finden Sie im [Dokumentation zum Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/).

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie `MobileCore.configureWith(appId: self.environmentFileId)` mit dem `appId` basierend auf der `environmentFileId` aus der Tag-Umgebung, für die Sie erstellen (Entwicklung, Staging oder Produktion).
>

>[!SUCCESS]
>
>Sie haben jetzt die erforderlichen Pakete installiert und Ihr Projekt aktualisiert, um die erforderlichen Adobe Experience Platform Mobile SDK-Erweiterungen, die Sie für den Rest des Tutorials verwenden werden, ordnungsgemäß zu registrieren.<br/>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Einrichten der Sicherheit](assurance.md)**
