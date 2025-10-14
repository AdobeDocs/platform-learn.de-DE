---
title: Verbinden von ACS mit der AEM Sites CS/EDS-Storefront
description: Verbinden von ACS mit der AEM Sites CS/EDS-Storefront
kt: 5342
doc-type: tutorial
exl-id: 81d826a8-c9f0-4e2a-9107-d6e06a4b8427
source-git-commit: 7280f6b7d3579226f2d8c7f94e75ca8d3f2941cc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 1.5.2 Verbinden von ACCS mit der AEM Sites CS/EDS-Storefront

>[!IMPORTANT]
>
>Um diese Übung abzuschließen, benötigen Sie Zugriff auf eine funktionierende Umgebung für AEM Sites und Assets CS mit EDS.
>
>Wenn Sie noch keine solche Umgebung haben, gehen Sie zu Übung [Adobe Experience Manager Cloud Service &amp; Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Folgen Sie den Anweisungen dort, und Sie haben Zugriff auf eine solche Umgebung.

>[!IMPORTANT]
>
>Wenn Sie zuvor ein AEM CS-Programm mit einer AEM Sites- und Assets CS-Umgebung konfiguriert haben, wurde Ihre AEM CS-Sandbox möglicherweise in den Ruhezustand versetzt. Da der Ruhezustand einer solchen Sandbox 10-15 Minuten dauert, ist es ratsam, den Ruhezustand jetzt zu beenden, damit Sie nicht zu einem späteren Zeitpunkt warten müssen.

In dieser Übung verknüpfen Sie die AEM Sites CS/EDS-Storefront mit dem ACCS-Backend. Wenn Sie im Moment Ihre AEM Sites CS/EDS-Storefront öffnen und zur Produktlistenseite **Telefone** gehen, sehen Sie noch keine Produkte.

Am Ende dieser Übung sollten die Produkte, die Sie in der vorherigen Übung konfiguriert haben, auf der Produktlistenseite &quot;**&quot;** Ihrer AEM Sites CS/EDS-Storefront angezeigt werden.

![ACCS+AEM Sites](./images/accsaemsites0.png)

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Stellen Sie sicher, dass Sie sich in der richtigen Umgebung befinden, die `--aepImsOrgName--` benannt werden sollte. Auf **Commerce**.

![ACCS+AEM Sites](./images/accsaemsites1.png)

Klicken Sie auf **info**-Symbol neben Ihrer ACS-Instanz, die `--aepUserLdap-- - ACCS` benannt werden sollte.

![ACCS+AEM Sites](./images/accsaemsites2.png)

Sie sollten das dann sehen. Kopieren Sie den **GraphQL-Endpunkt**.

![ACCS+AEM Sites](./images/accsaemsites3.png)

Navigieren Sie zu [https://da.live/app/adobe-commerce/storefront-tools/tools/config-generator/config-generator](https://da.live/app/adobe-commerce/storefront-tools/tools/config-generator/config-generator). Sie müssen jetzt eine config.json-Datei generieren, mit der Ihre AEM Sites CS-Storefront mit Ihrem ACCS-Backend verknüpft wird.

Fügen Sie auf **Seite &quot;**&quot; die kopierte **GraphQL** Endpunkt-URL ein.

Klicken Sie **Generieren**.

![ACCS+AEM Sites](./images/accsaemsites4.png)

Kopieren Sie die vollständige generierte JSON-Payload.

![ACCS+AEM Sites](./images/accsaemsites5.png)

Gehen Sie zum GitHub-Repository, das beim Einrichten Ihrer AEM Sites CS/EDS-Umgebung erstellt wurde. Dieses Repository wurde in der Übung [1.1.2 Einrichten der AEM CS-Umgebung erstellt &#x200B;](./../../../modules/asset-mgmt/module2.1/ex3.md){target="_blank"} sollte den Namen &quot;**-aem-accs** erhalten.

![ACCS+AEM Sites](./images/accsaemsites6.png)

Scrollen Sie im Stammverzeichnis nach unten und klicken Sie, um die Datei (**.json)** öffnen.

![ACCS+AEM Sites](./images/accsaemsites7.png)

Verwenden Sie das Symbol **Bearbeiten**.

![ACCS+AEM Sites](./images/accsaemsites8.png)

Entfernen Sie den gesamten aktuellen Text und ersetzen Sie ihn, indem Sie die JSON-Payload einfügen, die Sie auf die Seite &quot;**&quot; kopiert**.

Klicken Sie **Änderungen übernehmen…**.

![ACCS+AEM Sites](./images/accsaemsites9.png)

Klicken Sie **Änderungen übernehmen**.

![ACCS+AEM Sites](./images/accsaemsites10.png)

Die **config.json** wurde jetzt aktualisiert. Sie sollten Ihre Änderungen innerhalb weniger Minuten auf der Website sehen. Die Möglichkeit, zu überprüfen, ob die Änderungen erfolgreich erfasst wurden, besteht darin, zur Produktseite **Telefone** zu wechseln. Auf der Seite sollte nun **iPhone Air** angezeigt werden.

Um auf Ihre Website zuzugreifen, müssen Sie zu `main--citisignal-aem-accs--XXX.aem.page` und/oder `main--citisignal-aem-accs--XXX.aem.live` gehen, nachdem Sie XXX durch Ihr GitHub-Benutzerkonto ersetzt haben, was in diesem Beispiel `woutervangeluwe` ist.

In diesem Beispiel lautet die vollständige URL wie folgt:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` und/oder `https://main--citisignal-aem-accs--woutervangeluwe.aem.live`.

![ACCS+AEM Sites](./images/accsaemsites11.png)

Obwohl das Produkt jetzt erfolgreich angezeigt wird, ist noch kein Bild für das Produkt verfügbar. Sie werden in der nächsten Übung den Link mit AEM Assets CS für Produktbilder einrichten.

Nächster Schritt: [Verbinden von ACCS mit AEM Assets CS](./ex3.md){target="_blank"}

Zurück zu [Adobe Commerce as a Cloud Service](./accs.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
