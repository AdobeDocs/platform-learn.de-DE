---
title: AEM CS - Erweiterter benutzerdefinierter Block
description: AEM CS - Erweiterter benutzerdefinierter Block
kt: 5342
doc-type: tutorial
source-git-commit: 2f53c8da2cbe833120fa6555c65b8b753bfa4f8d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 2%

---

# 2.1.6 AEM-Edge Delivery Services MarTech-Plug-in

Mit dem AEM MarTech-Plug-in können Sie schnell einen vollständigen MarTech-Stack für Ihr AEM-Projekt einrichten.

>[!NOTE]
>
>Dieses Plug-in steht Kunden derzeit in Zusammenarbeit mit AEM Engineering über Co-Innovation-Projekte zur Verfügung. Weitere Informationen finden Sie unter [https://github.com/adobe-rnd/aem-martech](https://github.com/adobe-rnd/aem-martech).

Navigieren Sie zu dem Ordner, den Sie für Ihr GitHub-Repository **Citisignal** verwenden. Klicken Sie mit der rechten Maustaste auf den Ordnernamen und wählen Sie **Neues Terminal unter Ordner**.

![AEMCS](./images/mtplugin1.png)

Sie werden es dann sehen. Fügen Sie den folgenden Befehl ein und drücken Sie **enter**.

```
git subtree add --squash --prefix plugins/martech https://github.com/adobe/aem-experimentation.git main
```

Sie sollten das dann sehen.

![AEMCS](./images/mtplugin3.png)

Navigieren Sie zu dem Ordner, den Sie für Ihr GitHub-Repository **Citisignal** verwenden, und öffnen Sie den Ordner **plugins**. Jetzt sollte ein Ordner mit dem Namen **martech** angezeigt werden.

![AEMCS](./images/mtplugin4.png)


Öffnen Sie in Visual Studio Code die Datei **head.html**. Kopieren Sie den folgenden Code und fügen Sie ihn in die Datei **head.html** ein.

```javascript
<link rel="preload" as="script" crossorigin="anonymous" href="/plugins/martech/src/index.js"/>
<link rel="preload" as="script" crossorigin="anonymous" href="/plugins/martech/src/alloy.min.js"/>
<link rel="preconnect" href="https://edge.adobedc.net"/>
<!-- change to adobedc.demdex.net if you enable third party cookies -->
```

Speichern Sie Ihre Änderungen.

![AEMCS](./images/mtplugin5.png)

Wechseln Sie in Visual Studio Code zum Ordner **scripts** und öffnen Sie die Datei **scripts.js**. Kopieren Sie den folgenden Code und fügen Sie ihn in die Datei **scripts.js** unter den vorhandenen Importskripten ein.

```javascript
import {
  initMartech,
  updateUserConsent,
  martechEager,
  martechLazy,
  martechDelayed,
} from '../plugins/martech/src/index.js';
```

Speichern Sie Ihre Änderungen.

![AEMCS](./images/mtplugin6.png)

```javascript
const isConsentGiven = true;
  const martechLoadedPromise = initMartech(
    // The WebSDK config
    // Documentation: https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/configure/overview#configure-js
    {
      datastreamId: "045c5ee9-468f-47d5-ae9b-a29788f5948f",
      orgId: "907075E95BF479EC0A495C73@AdobeOrg",
      onBeforeEventSend: (payload) => {
        // set custom Target params 
        // see doc at https://experienceleague.adobe.com/en/docs/platform-learn/migrate-target-to-websdk/send-parameters#parameter-mapping-summary
        payload.data.__adobe.target ||= {};

        // set custom Analytics params
        // see doc at https://experienceleague.adobe.com/en/docs/analytics/implementation/aep-edge/data-var-mapping
        payload.data.__adobe.analytics ||= {};
      },

      // set custom datastream overrides
      // see doc at:
      // - https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/datastream-overrides
      // - https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overrides
      edgeConfigOverrides: {
        // Override the datastream id
        // datastreamId: '...'

        // Override AEP event datasets
        // com_adobe_experience_platform: {
        //   datasets: {
        //     event: {
        //       datasetId: '...'
        //     }
        //   }
        // },

        // Override the Analytics report suites
        // com_adobe_analytics: {
        //   reportSuites: ['...']
        // },

        // Override the Target property token
        // com_adobe_target: {
        //   propertyToken: '...'
        // }
      },
    },
    // The library config
    {
      launchUrls: ["https://assets.adobedtm.com/b754ed1bed61/b9f7c7c484de/launch-28b548849fb9.min.js"],
      personalization: !!getMetadata('target') && isConsentGiven,
    },
  );
```

![AEMCS](./images/mtplugin8.png)

![AEMCS](./images/mtplugin7.png)

```javascript
if (main) {
    decorateMain(main);
    await Promise.all([
      martechLoadedPromise.then(martechEager),
      waitForLCP(LCP_BLOCKS),
    ]);
  }
```

![AEMCS](./images/mtplugin10.png)

```javascript
await martechLazy();
```

![AEMCS](./images/mtplugin9.png)

```javascript
window.setTimeout(() => {
    martechDelayed();
    return import('./delayed.js');
  }, 3000);
```

![AEMCS](./images/mtplugin11.png)


![AEMCS](./images/mtplugin12.png)


![AEMCS](./images/mtplugin13.png)

Sie können nun die Änderungen an Ihrer Website anzeigen, indem Sie zu `main--citisignal--XXX.aem.page/us/en` und/oder `main--citisignal--XXX.aem.live/us/en` wechseln, nachdem Sie XXX durch Ihr GitHub-Benutzerkonto ersetzt haben, was in diesem Beispiel `woutervangeluwe` ist.

In diesem Beispiel lautet die vollständige URL wie folgt:
`https://main--citisignal--woutervangeluwe.aem.page/us/en` und/oder `https://main--citisignal--woutervangeluwe.aem.live/us/en`.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md){target="_blank"}

[Zurück zum Modul 2.1](./aemcs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
