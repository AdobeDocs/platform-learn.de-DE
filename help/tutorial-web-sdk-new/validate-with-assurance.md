---
title: WebSDK-Implementierungen mit Experience Platform Assurance validieren
description: Erfahren Sie, wie Sie Ihre Platform Web SDK-Implementierung mit Adobe Experience Platform Assurance überprüfen. Diese Lektion ist Teil des Tutorials zum Implementieren von Adobe Experience Cloud mit Web SDK.
feature: Web SDK,Tags,Assurance
source-git-commit: 4361d8e688ff2c2f3b5472f2cfff246efa627c7f
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# WebSDK-Implementierungen mit Experience Platform Assurance validieren


## Starten einer Assurance-Sitzung

Adobe Experience Platform Assurance ist ein Produkt aus Adobe Experience Cloud, mit dem Sie die Datenerfassung und Bereitstellung von Erlebnissen überprüfen, testen, simulieren und validieren können.

Mehr dazu [Adobe Assurance](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html?lang=en).

Jedes Mal, wenn Sie Edge Trace aktivieren, wird eine Zuverlässigkeitssitzung im Hintergrund gestartet.

So zeigen Sie die Assurance-Sitzung an:

1. Wenn Edge Trace aktiviert ist, sehen Sie oben ein Symbol für einen ausgehenden Link. Wählen Sie das Symbol aus, um &quot;Versicherung&quot;zu öffnen. Eine neue Registerkarte in Ihrem Browser wird geöffnet.

   ![Starten einer Assurance-Sitzung](assets/validate-debugger-start-assurnance.png)

1. Wählen Sie die Zeile mit dem Ereignis Adobe Response Handle aus.
1. Rechts wird ein Menü angezeigt. Wählen Sie die `+` neben `[!UICONTROL ACPExtensionEvent]`
1. Drilldown durch Auswahl von `[!UICONTROL payload > 0 > payload > 0 > namespace]`. Die unter der letzten `0` entspricht `ECID`. Sie wissen dies anhand des Wertes, der unter `namespace` Abgleich `ECID`

   ![Zuverlässigkeitsprüfung ECID](assets/validate-assurance-ecid.png)

   >[!CAUTION]
   >
   >Aufgrund der Breite Ihres Fensters wird möglicherweise ein abgeschnittener ECID-Wert angezeigt. Wählen Sie einfach die Griffleiste in der Benutzeroberfläche aus und ziehen Sie sie nach links, um die gesamte ECID anzuzeigen.

In zukünftigen Lektionen verwenden Sie Assurance, um vollständig verarbeitete Payloads zu validieren und eine Adobe-Anwendung zu erreichen, die in Ihrem Datastream aktiviert ist.

Da jetzt ein XDM-Objekt auf einer Seite ausgelöst wird und Sie wissen, wie Sie Ihre Datenerfassung überprüfen können, können Sie die einzelnen Adobe-Anwendungen mithilfe des Platform Web SDK einrichten.