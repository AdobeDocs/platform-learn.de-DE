---
title: Installieren von Adobe Experience Platform Mobile SDKs
description: Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in eine Mobile App implementieren.
hide: true
exl-id: 86348d8b-f428-465d-a79e-ce73d140da79
source-git-commit: c74053b99729269fa42d18372f84fd7c6c2c2e0c
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---

# Installieren von Adobe Experience Platform Mobile SDKs

Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in eine Mobile App implementieren.

## Voraussetzungen

* Eine Tag-Bibliothek mit den Erweiterungen, die im Abschnitt [vorherige Lektion](configure-tags.md).
* Entwicklungsumgebung - Datei-ID aus [Installationsanweisungen für Mobilgeräte](configure-tags.md#generate-sdk-install-instructions).
* Leere herunterladen [Beispielanwendung](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}.
* Erlebnis mit [Xcode](https://developer.apple.com/xcode/){target="_blank"}.

## Lernziele

In dieser Lektion werden Sie:

* Fügen Sie Ihrem Projekt mithilfe des Swift Package Manager die erforderlichen SDKs hinzu.
* Registrieren Sie die Erweiterungen.

>[!NOTE]
>
>In einer Mobile-App-Implementierung sind die Begriffe &quot;Erweiterungen&quot;und &quot;SDKs&quot;nahezu austauschbar.

## Swift Package Manager

Anstatt CocoaPods und eine Pod-Datei zu verwenden (siehe [SDK-Installationsanweisungen generieren](./configure-tags.md#generate-sdk-install-instructions)), fügen Sie mithilfe des nativen Swift Package Manager von Xcode einzelne Pakete hinzu. Für das Xcode-Projekt wurden bereits alle Paketabhängigkeiten hinzugefügt. Der Xcode **[!UICONTROL Paketabhängigkeiten]** Der Bildschirm sollte wie folgt aussehen:

![Abhängigkeiten von Xcode-Paketen](assets/xcode-package-dependencies.png){zoomable=&quot;yes&quot;}


In Xcode können Sie **[!UICONTROL Datei]** > **[!UICONTROL Pakete hinzufügen...]** , um Pakete hinzuzufügen. Die nachstehende Tabelle enthält Links zu den URLs, die Sie zum Hinzufügen von Paketen verwenden würden. Über die Links gelangen Sie zu weiteren Informationen zu den einzelnen Paketen.

| Paket | Beschreibung |
|---|---|
| [AEP Core](https://github.com/adobe/aepsdk-core-ios) | Die `AEPCore`, `AEPServices`, und `AEPIdentity` Erweiterungen stellen die Grundlage des Adobe Experience Platform SDK dar - jede App, die das SDK verwendet, muss sie enthalten. Diese Module enthalten einen gemeinsamen Satz von Funktionen und Diensten, die für alle SDK-Erweiterungen erforderlich sind.<br/><ul><li>`AEPCore` enthält die Implementierung des Ereignis-Hub. Der Ereignis-Hub ist der Mechanismus zur Bereitstellung von Ereignissen zwischen der App und dem SDK. Der Ereignis-Hub wird auch zum Freigeben von Daten zwischen Erweiterungen verwendet.</li><li>`AEPServices` bietet mehrere wiederverwendbare Implementierungen, die für die Plattformunterstützung erforderlich sind, einschließlich Netzwerk, Festplattenzugriff und Datenbankverwaltung.</li><li>`AEPIdentity` implementiert die Integration mit Adobe Experience Platform Identity-Diensten.</li><li>`AEPSignal` stellt die Signal-Erweiterung der Adobe Experience Platform SDKs dar, die es Marketing-Experten ermöglicht, ein &quot;Signal&quot;an ihre Apps zu senden, um Daten an externe Ziele zu senden oder URLs zu öffnen.</li><li>`AEPLifecycle` stellt die Adobe Experience Platform SDKs Lifecycle-Erweiterung dar, die bei der Erfassung von Lebenszyklusmetriken für Anwendungen wie Informationen zur Anwendungsinstallation oder -aktualisierung, zum Anwendungsstart und zu Sitzungsinformationen, Geräteinformationen und zusätzlichen Kontextdaten, die vom Anwendungsentwickler bereitgestellt werden, hilft.</li></ul> |
| [AEP Edge](https://github.com/adobe/aepsdk-edge-ios) | Die mobile Adobe Experience Platform Edge Network-Erweiterung (`AEPEdge`) ermöglicht den Versand von Daten von einer Mobile App an das Adobe Edge-Netzwerk. Mit dieser Erweiterung können Sie Adobe Experience Cloud-Funktionen robuster implementieren, mehrere Adobe-Lösungen über einen Netzwerkaufruf bereitstellen und diese Informationen gleichzeitig an die Adobe Experience Platform weiterleiten.<br/>Die mobile Edge Network-Erweiterung ist eine Erweiterung für das Adobe Experience Platform SDK und erfordert die `AEPCore` und `AEPServices` Erweiterungen für die Ereignisverarbeitung sowie die `AEPEdgeIdentity` Erweiterung zum Abrufen der Identitäten, z. B. ECID. |
| [AEP Edge Identity](https://github.com/adobe/aepsdk-edgeidentity-ios) | Die mobile Erweiterung &quot;AEP Edge Identity&quot;(`AEPEdgeIdentity`) ermöglicht die Verarbeitung von Benutzeridentitätsdaten aus einer Mobile App bei Verwendung des Adobe Experience Platform SDK und der Edge Network-Erweiterung. |
| [Zustimmung zu AEP Edge](https://github.com/adobe/aepsdk-edgeconsent-ios) | Die mobile Erweiterung &quot;AEP Consent Collection&quot;(`AEPConsent`) ermöglicht die Erfassung von Zustimmungsvoreinstellungen von der Mobile App bei Verwendung des Adobe Experience Platform SDK und der Edge Network-Erweiterung. |
| [AEP-Benutzerprofil](https://github.com/adobe/aepsdk-userprofile-ios) | Die Mobile-Erweiterung des Adobe Experience Platform-Benutzerprofils (`AEPUserProfile`) ist eine Erweiterung zur Verwaltung von Benutzerprofilen für das Adobe Experience Platform SDK. |
| [AEP Places](https://github.com/adobe/aepsdk-places-ios) | Die AEP Places-Erweiterung (`AEPPlaces`) können Sie Geolocation-Ereignisse verfolgen, wie in der Adobe Places-Benutzeroberfläche und in den Adobe-Datenerfassungs-Tag-Regeln definiert. |
| [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios) | Die AEP Messaging-Erweiterung (`AEPMessaging`) ermöglicht das Senden von Push-Benachrichtigungstoken und Push-Benachrichtigungs-Clickthrough-Feedback an die Adobe Experience Platform. |
| [AEP Optimize](https://github.com/adobe/aepsdk-optimize-ios) | Die AEP Optimize-Erweiterung (`AEPOptimize`) bietet APIs zum Aktivieren von Echtzeit-Personalisierungs-Workflows in den Adobe Experience Platform Mobile SDKs mithilfe der Adobe Target- oder Adobe Journey Optimizer-Offer decisioning. Sie erfordert `AEPCore` und `AEPEdge` Erweiterungen zum Senden von Personalisierungsabfrageereignissen an das Experience Edge-Netzwerk. |
| [AEP-Sicherheit](https://github.com/adobe/aepsdk-assurance-ios) | Assurance (alias Projekt Griffon) ist eine neue, innovative Erweiterung (`AEPAssurance`), damit Sie die Erfassung, den Testversand, die Simulation und die Validierung der Datenerfassung und der Bereitstellung von Erlebnissen in Ihrer App unterstützen können. Diese Erweiterung aktiviert Ihre App für die Qualitätssicherung. |


## Importieren von Erweiterungen

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

Navigieren Sie zu **[!DNL Luma]** > **[!DNL Luma]** > **AppDelegate** im Xcode-Projektnavigator.

1. Ersetzen Sie die `@AppStorage` value `YOUR_ENVIRONMENT_ID_GOES_HERE` für `environmentFileId` zum Wert der Datei-ID der Entwicklungsumgebung hinzufügen, den Sie aus den Tags in [SDK-Installationsanweisungen generieren](configure-tags.md#generate-sdk-install-instructions).

   ```swift
   @AppStorage("environmentFileId") private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"
   ```

1. Fügen Sie den folgenden Code zum `application(_, didFinishLaunchingWithOptions)` -Funktion.

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

Der obige Code führt Folgendes aus:

1. Registriert die erforderlichen Erweiterungen.
1. Konfiguriert MobileCore und andere Erweiterungen für die Verwendung Ihrer Tag-Eigenschaftenkonfiguration.
1. Aktiviert die Debug-Protokollierung. Weitere Informationen und Optionen finden Sie im [Dokumentation zum Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/).
1. Startet die Lebenszyklusüberwachung. Siehe [Lebenszyklus](lifecycle-data.md) im Tutorial für weitere Details.
1. Legt die Standardzustimmung auf unbekannt fest. Siehe [Einverständnis](consent.md) im Tutorial für weitere Details.

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie `MobileCore.configureWith(appId: self.environmentFileId)` mit dem `appId` basierend auf der `environmentFileId` aus der Tag-Umgebung, für die Sie erstellen (Entwicklung, Staging oder Produktion).
>

>[!SUCCESS]
>
>Sie haben jetzt die erforderlichen Pakete installiert und Ihr Projekt aktualisiert, um die erforderlichen Adobe Experience Platform Mobile SDK-Erweiterungen, die Sie für den Rest des Tutorials verwenden werden, ordnungsgemäß zu registrieren.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Einrichten der Sicherheit](assurance.md)**
