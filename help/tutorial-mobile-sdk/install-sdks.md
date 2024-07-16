---
title: Installieren von Adobe Experience Platform Mobile SDKs
description: Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in eine Mobile App implementieren.
jira: KT-14627
exl-id: 98d6f59e-b8a3-4c63-ae7c-8aa11e948f59
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# Installieren von Adobe Experience Platform Mobile SDKs

Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in eine Mobile App implementieren.

## Voraussetzungen

* eine Tag-Bibliothek mit den in der [vorherigen Lektion](configure-tags.md) beschriebenen Erweiterungen erfolgreich erstellt wurde.
* Kennung der Entwicklungsumgebung aus den [Anweisungen zur mobilen Installation](configure-tags.md#generate-sdk-install-instructions).
* Laden Sie die leere [Beispiel-App](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"} herunter.
* Erlebnis mit [Xcode](https://developer.apple.com/xcode/){target="_blank"}.

## Lernziele

In dieser Lektion werden Sie:

* Fügen Sie Ihrem Projekt mithilfe des Swift Package Manager die erforderlichen SDKs hinzu.
* Registrieren Sie die Erweiterungen.

>[!NOTE]
>
>In einer Mobile-App-Implementierung sind die Begriffe &quot;Erweiterungen&quot;und &quot;SDKs&quot;nahezu austauschbar.

## Swift Package Manager

Anstatt CocoaPods und eine Pod-Datei zu verwenden (wie in [SDK-Installationsanweisungen generieren](./configure-tags.md#generate-sdk-install-instructions) beschrieben), fügen Sie einzelne Pakete mithilfe des nativen Swift Package Manager von Xcode hinzu. Für das Xcode-Projekt wurden bereits alle Paketabhängigkeiten hinzugefügt. Der Bildschirm Xcode **[!UICONTROL Paketabhängigkeiten]** sollte wie folgt aussehen:

![Xcode-Paketabhängigkeiten](assets/xcode-package-dependencies.png){zoomable="yes"}


In Xcode können Sie **[!UICONTROL Datei]** > **[!UICONTROL Pakete hinzufügen...]** verwenden, um Pakete hinzuzufügen. Die nachstehende Tabelle enthält Links zu den URLs, die Sie zum Hinzufügen von Paketen verwenden würden. Über die Links gelangen Sie zu weiteren Informationen zu den einzelnen Paketen.

| Paket | Beschreibung |
|---|---|
| [AEP Core](https://github.com/adobe/aepsdk-core-ios) | Die Erweiterungen `AEPCore`, `AEPServices` und `AEPIdentity` stellen die Grundlage des Adobe Experience Platform SDK dar. Jede App, die das SDK verwendet, muss sie enthalten. Diese Module enthalten einen gemeinsamen Satz von Funktionen und Diensten, die für alle SDK-Erweiterungen erforderlich sind.<br/><ul><li>`AEPCore` enthält die Implementierung des Ereignis-Hub. Der Ereignis-Hub ist der Mechanismus zur Bereitstellung von Ereignissen zwischen der App und dem SDK. Der Ereignis-Hub wird auch zum Freigeben von Daten zwischen Erweiterungen verwendet.</li><li>`AEPServices` bietet mehrere wiederverwendbare Implementierungen, die für die Plattformunterstützung erforderlich sind, einschließlich Netzwerk, Festplattenzugriff und Datenbankverwaltung.</li><li>`AEPIdentity` implementiert die Integration mit Adobe Experience Platform Identity-Diensten.</li><li>`AEPSignal` steht für die Adobe Experience Platform SDKs Signal-Erweiterung, mit der Marketing-Experten ein &quot;Signal&quot;an ihre Apps senden können, um Daten an externe Ziele zu senden oder URLs zu öffnen.</li><li>`AEPLifecycle` steht für die Adobe Experience Platform SDKs-Lebenszykluserweiterung, die die Erfassung von Lebenszyklusmetriken für Anwendungen unterstützt, wie z. B. Informationen zur Anwendungsinstallation oder -aktualisierung, zum Anwendungsstart und zu Sitzungsinformationen, Geräteinformationen und alle vom Anwendungsentwickler bereitgestellten zusätzlichen Kontextdaten.</li></ul> |
| [AEP Edge](https://github.com/adobe/aepsdk-edge-ios) | Mit der mobilen Adobe Experience Platform Edge Network-Erweiterung (`AEPEdge`) können Sie Daten von einer Mobile App an das Adobe Edge-Netzwerk senden. Mit dieser Erweiterung können Sie Adobe Experience Cloud-Funktionen robuster implementieren, mehrere Adobe-Lösungen über einen Netzwerkaufruf bereitstellen und diese Informationen gleichzeitig an die Adobe Experience Platform weiterleiten.<br/>Die mobile Edge Network-Erweiterung ist eine Erweiterung für das Adobe Experience Platform SDK und erfordert die Erweiterungen `AEPCore` und `AEPServices` für die Ereignisverarbeitung sowie die Erweiterung `AEPEdgeIdentity` zum Abrufen der Identitäten, z. B. ECID. |
| [AEP Edge Identity](https://github.com/adobe/aepsdk-edgeidentity-ios) | Die mobile AEP Edge Identity-Erweiterung (`AEPEdgeIdentity`) ermöglicht die Verarbeitung von Benutzeridentitätsdaten aus einer Mobile App bei Verwendung des Adobe Experience Platform SDK und der Edge Network-Erweiterung. |
| [AEP Edge-Einverständnis](https://github.com/adobe/aepsdk-edgeconsent-ios) | Die mobile Erweiterung &quot;AEP Consent Collection&quot;(`AEPConsent`) ermöglicht die Erfassung von Zustimmungsvoreinstellungen von der Mobile App bei Verwendung des Adobe Experience Platform SDK und der Edge Network-Erweiterung. |
| [AEP-Benutzerprofil](https://github.com/adobe/aepsdk-userprofile-ios) | Die Adobe Experience Platform User Profile Mobile-Erweiterung (`AEPUserProfile`) ist eine Erweiterung zur Verwaltung von Benutzerprofilen für das Adobe Experience Platform SDK. |
| [AEP Places](https://github.com/adobe/aepsdk-places-ios) | Mit der AEP Places-Erweiterung (`AEPPlaces`) können Sie Geolocation-Ereignisse verfolgen, wie in der Adobe Places-Benutzeroberfläche und in den Adobe-Datenerfassungs-Tag-Regeln definiert. |
| [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios) | Mit der AEP Messaging-Erweiterung (`AEPMessaging`) können Sie Push-Benachrichtigungstoken und Push-Benachrichtigungs-Clickthrough-Feedback an die Adobe Experience Platform senden. |
| [AEP Optimize](https://github.com/adobe/aepsdk-optimize-ios) | Die AEP Optimize-Erweiterung (`AEPOptimize`) bietet APIs, um Echtzeit-Personalisierungs-Workflows in den Adobe Experience Platform Mobile SDKs mithilfe von Adobe Target oder Adobe Journey Optimizer Offer decisioning zu aktivieren. Zum Senden von Personalisierungsabfrageereignissen an das Experience Edge-Netzwerk sind die Erweiterungen `AEPCore` und `AEPEdge` erforderlich. |
| [AEP-Versicherung](https://github.com/adobe/aepsdk-assurance-ios) | Assurance (auch bekannt als Projekt Griffon) ist eine neue, innovative Erweiterung (`AEPAssurance`), mit der Sie die Erfassung, den Testversand, die Simulation und die Validierung von Daten und die Bereitstellung von Erlebnissen in Ihrer App überprüfen und testen können. Diese Erweiterung aktiviert Ihre App für die Qualitätssicherung. |


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

Führen Sie dasselbe für **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** aus.

## AppDelegate aktualisieren

Navigieren Sie im Xcode Project-Navigator zu **[!DNL Luma]** > **[!DNL Luma]** > **AppDelegate** .

1. Ersetzen Sie den `@AppStorage` -Wert `YOUR_ENVIRONMENT_ID_GOES_HERE` für `environmentFileId` durch den Wert für die ID der Entwicklungsumgebung-Datei, den Sie aus den Tags in den [SDK-Installationsanweisungen generieren](configure-tags.md#generate-sdk-install-instructions) abgerufen haben.

   ```swift
   @AppStorage("environmentFileId") private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"
   ```

1. Fügen Sie der Funktion `application(_, didFinishLaunchingWithOptions)` den folgenden Code hinzu.

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
1. Aktiviert die Debug-Protokollierung. Weitere Informationen und Optionen finden Sie in der Dokumentation zum Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/) .[
1. Startet die Lebenszyklusüberwachung. Weitere Informationen finden Sie im Schritt [Lebenszyklus](lifecycle-data.md) des Tutorials.
1. Legt die Standardzustimmung auf unbekannt fest. Weitere Informationen finden Sie im Schritt [Einverständnis](consent.md) des Tutorials.

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie `MobileCore.configureWith(appId: self.environmentFileId)` mit dem `appId` aktualisieren, der auf dem `environmentFileId` der Tag-Umgebung basiert, für die Sie erstellen (Entwicklung, Staging oder Produktion).
>

>[!SUCCESS]
>
>Sie haben jetzt die erforderlichen Pakete installiert und Ihr Projekt aktualisiert, um die erforderlichen Adobe Experience Platform Mobile SDK-Erweiterungen, die Sie für den Rest des Tutorials verwenden werden, ordnungsgemäß zu registrieren.
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeine Rückmeldungen oder Anregungen zu künftigen Inhalten teilen möchten, teilen Sie diese auf diesem [Experience League Community-Diskussionbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) mit.

Weiter: **[Einrichten der Versicherung](assurance.md)**
