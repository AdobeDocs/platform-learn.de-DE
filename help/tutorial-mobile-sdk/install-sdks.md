---
title: Installieren von Adobe Experience Platform Mobile SDKs
description: Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in eine Mobile App implementieren.
exl-id: 98d6f59e-b8a3-4c63-ae7c-8aa11e948f59
source-git-commit: bc53cb5926f708408a42aa98a1d364c5125cb36d
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 2%

---

# Installieren von Adobe Experience Platform Mobile SDKs

Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK in eine Mobile App implementieren.

>[!INFO]
>
> Dieses Tutorial wird Ende November 2023 mithilfe einer neuen Beispiel-Mobile-App durch ein neues Tutorial ersetzt.

## Voraussetzungen

* Erfolgreich erstellte Tag-Bibliothek mit den Erweiterungen, die im Abschnitt [vorherige Lektion](configure-tags.md).
* Entwicklungsumgebung - Datei-ID aus [Installationsanweisungen für Mobilgeräte](configure-tags.md#generate-sdk-install-instructions).
* Heruntergeladen, leer [Beispielanwendung](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}.
* Erlebnis mit [XCode](https://developer.apple.com/xcode/){target="_blank"}.
* Allgemein [Befehlszeile](https://en.wikipedia.org/wiki/Command-line_interface){target="_blank"} Wissen.

## Lernziele

In dieser Lektion werden Sie:

* Aktualisieren Sie Ihre CocoaPod -Datei.
* Importieren Sie die erforderlichen SDK.
* Registrieren Sie die Erweiterungen.

>[!NOTE]
>
>In einer Mobile-App-Implementierung sind die Begriffe &quot;Erweiterungen&quot;und &quot;SDKs&quot;nahezu austauschbar.


## PodFile aktualisieren

>[!NOTE]
>
> Wenn Sie nicht mit CocoaPods vertraut sind, lesen Sie bitte den offiziellen Abschnitt [Erste Schritte](https://guides.cocoapods.org/using/getting-started.html).

Installieren ist normalerweise ein einfacher sudo-Befehl:

```console
sudo gem install cocoapods
```

Sobald Sie CocoaPods installiert haben, öffnen Sie die Podfile.

![Initial-Podfile](assets/mobile-install-initial-podfile.png)

Aktualisieren Sie die Datei, um die folgenden Pods einzuschließen:

```swift
pod 'AEPCore', '~> 3'
pod 'AEPEdge', '~> 1'
pod 'AEPUserProfile', '~> 3'
pod 'AEPAssurance', '~> 3'
pod 'AEPServices', '~> 3'
pod 'AEPEdgeConsent', '~> 1'
pod 'AEPLifecycle', '~>3'
pod 'AEPMessaging', '~>1'
pod 'AEPEdgeIdentity', '~>1'
pod 'AEPSignal', '~>3'
```

>[!NOTE]
>
> `AEPMessaging` ist nur erforderlich, wenn Sie Push-Nachrichten mit Adobe Journey Optimizer implementieren möchten. Lesen Sie das Tutorial unter [Push-Nachrichten mit Adobe Journey Optimizer implementieren](journey-optimizer-push.md) für weitere Informationen.

Nachdem Sie die Änderungen in Ihrer Podfile gespeichert haben, navigieren Sie mit Ihrem Projekt zum Ordner und führen Sie die `pod install` -Befehl, um Ihre Änderungen zu installieren.

![pod install](assets/mobile-install-podfile-install.png)

>[!NOTE]
>
> Wenn Sie die Meldung &quot;Keine Podfile im Projektverzeichnis gefunden&quot; erhalten. -Fehler, befindet sich Ihr Terminal im falschen Ordner. Navigieren Sie zum Ordner mit der aktualisierten Podfile und versuchen Sie es erneut.

Wenn Sie auf die neueste Version aktualisieren möchten, führen Sie die `pod update` Befehl.

>[!INFO]
>
>Wenn Sie nicht in der Lage sind, CocoaPods in Ihren eigenen Apps zu verwenden, können Sie mehr über andere [unterstützte Implementierungen](https://github.com/adobe/aepsdk-core-ios#binaries) im GitHub-Projekt.

## Erstellen von CocoaPods

Um CocoaPods zu erstellen, öffnen Sie `Luma.xcworkspace`und wählen Sie **Produkt**, gefolgt von **Bereinigen des Ordners**.

>[!NOTE]
>
> Möglicherweise müssen Sie **Nur aktive Architektur erstellen** nach **Nein**. Wählen Sie dazu im Projektnavigator das Projekt Pods aus und wählen Sie **Build-Einstellungen** und legen Sie die **Erstellen einer aktiven Architektur** nach **Nein**.

Sie können jetzt das Projekt erstellen und ausführen.

![Build-Einstellungen](assets/mobile-install-build-settings.png)

>[!NOTE]
>
>Das Projekt Luma wurde mit Xcode v12.5 auf einem M1-Chipsatz erstellt und wird auf dem iOS-Simulator ausgeführt. Wenn Sie ein anderes Setup verwenden, müssen Sie möglicherweise Ihre Build-Einstellungen entsprechend Ihrer Architektur ändern.
>
>Wenn Ihr Build nicht erfolgreich war, versuchen Sie, die **Erstellen einer aktiven Architektur** > **Debuggen** zurücksetzen auf **Ja**.
>
>Die Simulatorkonfiguration &quot;iPod touch (7. Generation)&quot;wurde bei der Erstellung dieses Tutorials verwendet.

## Importieren von Erweiterungen

In jedem der `.swift` -Dateien, fügen Sie die folgenden Importe hinzu. Beginnen Sie mit Hinzufügen zu `AppDelegate.swift`.

```swift
import AEPUserProfile
import AEPAssurance
import AEPEdge
import AEPCore
import AEPEdgeIdentity
import AEPEdgeConsent
import AEPLifecycle
import AEPMessaging //Optional, used for AJO push messaging
import AEPSignal
import AEPServices
```

## AppDelegate aktualisieren

Im `AppDelegate.swift` -Datei, fügen Sie den folgenden Code zu `didFinishLaunchingWithOptions`. Ersetzen Sie currentAppId durch den Wert der Datei-ID der Entwicklungsumgebung , den Sie aus den Tags in der [vorherige Lektion](configure-tags.md).

```swift
let currentAppId = "b5cbd1a1220e/bae66382cce8/launch-88492c6dcb6e-development"

let extensions = [Edge.self, Assurance.self, Lifecycle.self, UserProfile.self, Consent.self, AEPEdgeIdentity.Identity.self, Messaging.self]

MobileCore.setLogLevel(.trace)

MobileCore.registerExtensions(extensions, {
    MobileCore.configureWith(appId: currentAppId)
})
```

`Messaging.self` ist nur erforderlich, wenn Sie Push-Nachrichten über Adobe Journey Optimizer implementieren möchten, wie beschrieben [here](journey-optimizer-push.md).

Der obige Code führt Folgendes aus:

* Registriert die erforderlichen Erweiterungen.
* Konfiguriert MobileCore und andere Erweiterungen für die Verwendung Ihrer Tag-Eigenschaftenkonfiguration.
* Aktiviert die Debug-Protokollierung. Weitere Informationen und Optionen finden Sie im [Dokumentation zum Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/).

>[!IMPORTANT]
>In einer Produktions-App müssen Sie AppId basierend auf der aktuellen Umgebung (dev/stage/prod) wechseln.
>

Weiter: **[Einrichten der Sicherheit](assurance.md)**

>[!NOTE]
>
>Vielen Dank, dass Sie Ihre Zeit investiert haben, um mehr über das Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, ein allgemeines Feedback oder Vorschläge zu künftigen Inhalten teilen möchten, teilen Sie diese hier mit. [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)