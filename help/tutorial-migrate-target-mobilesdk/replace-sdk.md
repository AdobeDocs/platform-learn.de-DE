---
title: Ersetzen Sie die Erweiterung SDK - Migrieren der Adobe Target-Implementierung in Ihrer Mobile App zur Erweiterung Adobe Journey Optimizer - Decisioning .
description: Erfahren Sie, wie Sie SDK bei der Migration von der Adobe Target zur Adobe Journey Optimizer - Decisioning Mobile-Erweiterung ersetzen.
exl-id: f1b77cad-792b-4a80-acff-e1a2f29250e1
source-git-commit: d2da62ed2d36f73af1c8053be5af27feea32cb14
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 2%

---

# Ersetzen Sie Target SDK durch Optimieren von SDK

Erfahren Sie, wie Sie die Adobe Target-SDKs in Ihrer mobilen Implementierung durch die SDKs von Optimize ersetzen. Ein einfacher Ersatz besteht aus den folgenden Schritten:

* Aktualisieren von Abhängigkeiten in der Profildatei oder `build.gradle`
* Importe aktualisieren
* Anwendungscode aktualisieren


>[!INFO]
>
>Innerhalb des Adobe Experience Platform Mobile SDK-Ökosystems werden Erweiterungen durch SDKs implementiert, die in Ihre Anwendungen importiert werden, die unterschiedliche Namen haben können:
>
> * **Target SDK** implementiert die Erweiterung **Adobe Target**
> * **SDK optimieren** implementiert die Erweiterung **Adobe Journey Optimizer - Decisioning**

## Aktualisieren von Abhängigkeiten

+++Android-Beispiel

>[!BEGINTABS]

>[!TAB SDK optimieren]

`build.gradle` Abhängigkeiten nach der Migration

```Java
implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')
implementation 'com.adobe.marketing.mobile:core'
implementation 'com.adobe.marketing.mobile:edgeidentity'
implementation 'com.adobe.marketing.mobile:edge'
implementation 'com.adobe.marketing.mobile:optimize'
```


>[!TAB Target SDK]

`build.gradle` Abhängigkeiten vor der Migration

```Java
implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')
implementation 'com.adobe.marketing.mobile:analytics'
implementation 'com.adobe.marketing.mobile:target'
implementation 'com.adobe.marketing.mobile:core'
implementation 'com.adobe.marketing.mobile:identity'
implementation 'com.adobe.marketing.mobile:lifecycle'
implementation 'com.adobe.marketing.mobile:signal'
implementation 'com.adobe.marketing.mobile:userprofile'
```


>[!ENDTABS]

+++

+++ iOS-Beispiel

>[!BEGINTABS]


>[!TAB SDK optimieren]

`Podfile` Abhängigkeiten nach der Migration

```Swift
use_frameworks!
target 'YourAppTarget' do
    pod 'AEPCore', '~> 5.0'
    pod 'AEPEdge', '~> 5.0'
    pod 'AEPEdgeIdentity', '~> 5.0'
    pod 'AEPOptimize', '~> 5.0'
end
```

>[!TAB Target SDK]

`Podfile` Abhängigkeiten vor der Migration

```Swift
use_frameworks!
pod 'AEPAnalytics', '~> 5.0'
pod 'AEPTarget', '~> 5.0'
pod 'AEPCore', '~> 5.0'
pod 'AEPIdentity', '~> 5.0'
pod 'AEPSignal', '~>5.0'
pod 'AEPLifecycle', '~>5.0'
pod 'AEPUserProfile', '~> 5.0'
```

>[!ENDTABS]

+++

## Importe und Code aktualisieren

+++ Android-Beispiel

>[!BEGINTABS]

>[!TAB SDK optimieren]

Java-Initialisierungscode nach der Migration

```Java
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Edge;
import com.adobe.marketing.mobile.edge.identity.Identity;
import com.adobe.marketing.mobile.optimize.Optimize;
import com.adobe.marketing.mobile.AdobeCallback;
 
public class MainApp extends Application {
 
  private final String ENVIRONMENT_FILE_ID = "YOUR_APP_ENVIRONMENT_ID";
 
    @Override
    public void onCreate() {
        super.onCreate();
 
        MobileCore.setApplication(this);
        MobileCore.configureWithAppID(ENVIRONMENT_FILE_ID);
 
        MobileCore.registerExtensions(
            Arrays.asList(Edge.EXTENSION, Identity.EXTENSION, Optimize.EXTENSION),
            o -> Log.d("MainApp", "Adobe Journey Optimizer - Decisioning Mobile SDK was initialized.")
        );
    }
}
```

>[!TAB Target SDK]

Java-Initialisierungscode vor der Migration

```Java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.Analytics;
import com.adobe.marketing.mobile.Extension;
import com.adobe.marketing.mobile.Identity;
import com.adobe.marketing.mobile.Lifecycle;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Signal;
import com.adobe.marketing.mobile.Target;
import com.adobe.marketing.mobile.UserProfile;
import java.util.Arrays;
import java.util.List;
...
import android.app.Application;
...
public class MainApp extends Application {
...
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.setLogLevel(LoggingMode.DEBUG);
        ...
        List<Class<? extends Extension>> extensions = Arrays.asList(
            Analytics.EXTENSION,
            Target.EXTENSION,
            Identity.EXTENSION,
            Lifecycle.EXTENSION,
            Signal.EXTENSION,
            UserProfile.EXTENSION
        );
 
 
        MobileCore.registerExtensions(extensions, new AdobeCallback () {
            @Override
            public void call(Object o) {
                MobileCore.configureWithAppID(<Environment File ID>);
            }
        });
    }
}
```

>[!ENDTABS]

+++

+++ iOS

>[!BEGINTABS]

>[!TAB SDK optimieren]

Schneller Initialisierungs-Code nach der Migration

```Swift
import AEPCore
import AEPEdge
import AEPEdgeIdentity
import AEPOptimize
 
@UIApplicationMain
final class AppDelegate: UIResponder, UIApplicationDelegate {
  var window: UIWindow?
 
  func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]? = nil) -> Bool {
 
      // register the extensions
      MobileCore.registerExtensions([Edge.self, AEPEdgeIdentity.Identity.self, Optimize.self]) {
        MobileCore.configureWith(appId: <YOUR_ENVIRONMENT_FILE_ID>) // Replace <YOUR_ENVIRONMENT_FILE_ID> with a String containing your own ID.
      }
 
      return true
  }
}
```

>[!TAB Target SDK]

Schneller Initialisierungs-Code vor der Migration

```Swift
import AEPCore
import AEPAnalytics
import AEPTarget
import AEPIdentity
import AEPLifecycle
import AEPSignal
import AEPServices
import AEPUserProfile
...
@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        MobileCore.setLogLevel(.debug)
        let appState = application.applicationState
        ...
        let extensions = [
            Analytics.self,
            Target.self,
            Identity.self,
            Lifecycle.self,
            Signal.self,
            UserProfile.self
        ]
        MobileCore.registerExtensions(extensions, {
        MobileCore.configureWith(<Environment File ID>)
        if appState != .background {
            MobileCore.lifecycleStart(additionalContextData: ["contextDataKey": "contextDataVal"])
            }
        })
        ...
        return true
    }
}
```

>[!ENDTABS]

+++

## API-Vergleich

Viele Target-Erweiterungs-APIs verfolgen einen gleichwertigen Ansatz unter Verwendung der in der folgenden Tabelle beschriebenen Decisioning-Erweiterung. Weitere Informationen zu den [Funktionen](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/) finden Sie in der API-Referenz.

| Target-Erweiterung | Decisioning-Erweiterung | Anmerkungen |
| --- | --- | --- | 
| [prefetchContent](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#prefetchcontent){target=_blank} | [updatePropositions](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#updatepropositionswithcompletionhandlerandtimeout){target=_blank} |  |
| [retrieveLocationContent](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#retrievelocationcontent){target=_blank} | [getPropositions](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#getpropositionswithtimeout){target=_blank} | Bei Verwendung `getPropositions` -API wird kein Remote-Aufruf durchgeführt, um nicht zwischengespeicherte Bereiche in der SDK abzurufen. |
| [displayLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#retrievelocationcontent){target=_blank} | [Angebot -> angezeigt()](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} | Darüber hinaus kann `generateDisplayInteractionXdm` Angebotsmethode verwendet werden, um das XDM für die Elementanzeige zu generieren. Anschließend kann die sendEvent-API des Edge-Netzwerk-SDK verwendet werden, um zusätzliche XDM- und Freiformdaten anzuhängen und ein Erlebnisereignis an die Remote-Instanz zu senden. |
| [clickedLocation](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#clickedlocation){target=_blank} | [offer -> tapped()](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} | Darüber hinaus kann `generateTapInteractionXdm` Angebotsmethode verwendet werden, um das XDM-Element für das Tippen zu generieren. Anschließend kann die sendEvent-API des Edge-Netzwerk-SDK verwendet werden, um zusätzliche XDM- und Freiformdaten anzuhängen und ein Erlebnisereignis an die Remote-Instanz zu senden. |
| [clearPrefetchCache](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#clickedlocation){target=_blank} | [clearCachedPropositions](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} |  |
| [resetExperience](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#resetexperience){target=_blank} | k. A. | Verwenden Sie [removeIdentity](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity){target=_blank} API von Identity for Edge Network für die SDK, um das Senden der Besucherkennung an das Edge-Netzwerk zu stoppen. Weitere Informationen finden Sie unter [Dokumentation zur removeIdentity-API](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). <br><br>Hinweis: Die `resetIdentities`-API von Mobile Core löscht alle in der SDK gespeicherten Identitäten, einschließlich der Experience Cloud-ID (ECID), und sollte sparsam verwendet werden! |
| [getSessionId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#getsessionid){target=_blank} | k. A. | `state:store` Antwort-Handle enthält sitzungsbezogene Informationen. Die Edge-Netzwerkerweiterung erleichtert die Verwaltung, indem sie nicht abgelaufene Statusspeicherelemente an nachfolgende Anfragen anhängt. |
| [setSessionId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#setsessionid){target=_blank} | k. A. | `state:store` Antwort-Handle enthält sitzungsbezogene Informationen. Die Edge-Netzwerkerweiterung erleichtert die Verwaltung, indem sie nicht abgelaufene Statusspeicherelemente an nachfolgende Anfragen anhängt. |
| [getThirdPartyId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#getthirdpartyid){target=_blank} | k. A. | Verwenden Sie die updateIdentities-API der Erweiterung Identity for Edge Network , um den Wert der Drittanbieter-ID anzugeben. Konfigurieren Sie dann den Namespace der Drittanbieter-ID im Datenstrom. Weitere Informationen finden Sie unter [Target Third-Party-ID für Mobilgeräte](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| [setThirdPartyId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#setthirdpartyid){target=_blank} | k. A. | Verwenden Sie die updateIdentities-API der Erweiterung Identity for Edge Network , um den Wert der Drittanbieter-ID anzugeben. Konfigurieren Sie dann den Namespace der Drittanbieter-ID im Datenstrom. Weitere Informationen finden Sie unter [Target Third-Party-ID für Mobilgeräte](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| [getTntId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#gettntid){target=_blank} | k. A. | `locationHint:result` Antwort-Handle enthält die Informationen zum Ziel-Standorthinweis. Es wird davon ausgegangen, dass Target Edge mit Experience Edge zusammengelegt wird. <br> <br>Die Edge-Netzwerkerweiterung verwendet den EdgeNetwork-Standorthinweis, um den Edge-Netzwerkcluster zu ermitteln, an den Anforderungen gesendet werden sollen. Verwenden Sie zum Freigeben von Speicherorthinweisen für das Edge-Netzwerk über SDKs (Hybrid-Apps) die APIs `getLocationHint` und `setLocationHint` aus der Edge Network-Erweiterung. Weitere Informationen finden Sie unter [die `getLocationHint` API-Dokumentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |
| [setTntId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#gettntid){target=_blank} | k. A. | [locationHint:result](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#setlocationhint){target=_blank} Das Antwort-Handle enthält die Informationen zum Ziel-Standorthinweis. Es wird davon ausgegangen, dass Target Edge mit Experience Edge zusammengelegt wird. <br> <br>Die Edge-Netzwerkerweiterung verwendet den EdgeNetwork-Standorthinweis, um den Edge-Netzwerkcluster zu ermitteln, an den Anforderungen gesendet werden sollen. Verwenden Sie zum Freigeben von Speicherorthinweisen für das Edge-Netzwerk über SDKs (Hybrid-Apps) die APIs `getLocationHint` und `setLocationHint` aus der Edge Network-Erweiterung. Weitere Informationen finden Sie unter [die `getLocationHint` API-Dokumentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |


Erfahren Sie als Nächstes, wie Sie [Aktivitäten anfordern und rendern](retrieve-activities.md) auf der Seite ausführen.

>[!NOTE]
>
>Wir möchten Ihnen dabei helfen, Ihre mobile Target-Migration von der Target-Erweiterung zur Decisioning-Erweiterung erfolgreich durchzuführen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) posten.
