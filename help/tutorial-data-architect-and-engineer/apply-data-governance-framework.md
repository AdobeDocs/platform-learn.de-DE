---
title: Data Governance-Framework anwenden
seo-title: Apply the data governance framework | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Data Governance-Framework anwenden
description: In dieser Lektion wenden Sie das Data Governance-Framework auf die Daten an, die Sie in Ihre Sandbox aufgenommen haben.
role: Data Architect
feature: Data Governance
jira: KT-4348
thumbnail: 4348-apply-data-governance-framework.jpg
exl-id: 3cc3c794-5ffd-41bf-95d8-be5bca2e3a0f
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 5%

---

# Data Governance-Framework anwenden

<!--15min-->

In dieser Lektion wenden Sie das Data Governance-Framework auf die Daten an, die Sie in Ihre Sandbox aufgenommen haben.

Mit Data Governance in Adobe Experience Platform können Sie Kundendaten verwalten und bei der Verwendung von Daten die Einhaltung von Vorschriften, Einschränkungen und Richtlinien sicherstellen. Es spielt eine Schlüsselrolle beim Experience Platform auf verschiedenen Ebenen, einschließlich der Steuerung der Datennutzung.

Bevor Sie mit den Übungen beginnen, sehen Sie sich diese kurzen Videos über Data Governance an:
>[!VIDEO](https://video.tv.adobe.com/v/36653?learn=on)

>[!VIDEO](https://video.tv.adobe.com/v/29708?learn=on)

<!--
## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you set up all the access controls required to complete this lesson, specifically:

* Permission items **[!UICONTROL Data Governance]** > **[!UICONTROL Manage Usage Labels]**, **[!UICONTROL Manage Data Usage Policies]** and **[!UICONTROL View Data Usage Policies]**
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` Product Profile
-->

## Geschäftsszenario

Luma verspricht Mitgliedern seines Treueprogramms, dass Treuedaten nicht an Dritte weitergegeben werden. Wir werden dieses Szenario im Rest der Lektion umsetzen.

## Data Governance-Beschriftungen anwenden

Der erste Schritt im Data Governance-Prozess besteht darin, Governance-Beschriftungen auf Ihre Daten anzuwenden. Bevor wir dies tun, schauen wir uns kurz an, welche Beschriftungen verfügbar sind:

1. Wählen Sie in der Benutzeroberfläche von Platform im linken Navigationsbereich **[!UICONTROL Richtlinien]** aus.
1. Navigieren Sie zur Registerkarte **[!UICONTROL Beschriftungen]** , um alle Beschriftungen im Konto anzuzeigen.

Es gibt viele native Beschriftungen. Zusätzlich können Sie Ihre eigenen über die Schaltfläche [!UICONTROL Titel erstellen] erstellen. Es gibt drei Haupttypen: [!UICONTROL Vertragsbezeichnungen], [!UICONTROL Identitätsbezeichnungen] und [!UICONTROL vertrauliche Bezeichnungen], die häufigen Gründen entsprechen, weshalb Daten eingeschränkt sein können. Jede Beschriftung hat einen [!UICONTROL Anzeigenamen] und einen kurzen [!UICONTROL Namen], der nur eine Abkürzung des Typs und eine Zahl darstellt. Beispielsweise ist die Bezeichnung [!DNL C1] für &quot;Kein Export durch Dritte&quot;, was wir für unsere Loyalitätsrichtlinie benötigen.

![Beschriftung für Data Governance](assets/governance-policies.png)

Jetzt ist es an der Zeit, die Daten zu kennzeichnen, deren Nutzung wir beschränken möchten:

1. Wählen Sie in der Benutzeroberfläche von Platform im linken Navigationsbereich **[!UICONTROL Datensätze]** aus.
1. Öffnen Sie die `Luma Loyalty Dataset`
1. Navigieren Sie zur Registerkarte **[!UICONTROL Data Governance]** .
1. Sie können entweder Bezeichnungen auf einzelne Felder anwenden oder sie auf den gesamten Datensatz anwenden. Wir wenden die Bezeichnung auf den gesamten Datensatz an. Klicken Sie auf das Stiftsymbol. Wenn das Symbol nicht angezeigt wird, versuchen Sie, den Browser breiter zu gestalten oder scrollen Sie im mittleren Bereich nach rechts.
   ![Data Governance](assets/governance-dataset.png)
1. Erweitern Sie im Modal den Abschnitt **[!UICONTROL Vertragsbezeichnungen]** und aktivieren Sie die Bezeichnung **[!UICONTROL C2]** .
1. Wählen Sie die Schaltfläche **[!UICONTROL Änderungen speichern]** aus.
   ![Data Governance](assets/governance-applyLabel.png)
1. Kehren Sie zum Hauptbildschirm von [!UICONTROL Data Governance] zurück und schalten Sie mit dem Umschalter **[!UICONTROL Vererbte Beschriftungen anzeigen]** ein, um zu sehen, wie die Beschriftung auf alle Felder im Datensatz angewendet wurde.
   ![Data Governance](assets/governance-labelsAdded.png)


<!--adding extra, unnecessary fields from field groups makes it harder to see which fields really need labels-->
<!--Are there any best practices for applying governance labels-->

## Data Governance-Richtlinien erstellen

Nachdem unsere Daten jetzt beschriftet sind, können wir eine Richtlinie erstellen.

1. Wählen Sie in der Benutzeroberfläche von Platform im linken Navigationsbereich **[!UICONTROL Richtlinien]** aus.
1. Auf der Registerkarte Durchsuchen gibt es bereits eine vordefinierte Richtlinie namens &quot;Exportbeschränkung von Drittanbietern&quot;, die die Bezeichnung C2 mit der Marketing-Aktion [!UICONTROL Nach Drittanbieter exportieren] verknüpft - genau das, was wir benötigen!
1. Wählen Sie die Richtlinie aus und aktivieren Sie sie dann über den Umschalter **[!UICONTROL Richtlinienstatus]** .
   ![Data Governance](assets/governance-enablePolicy.png)

Sie können eigene Richtlinien erstellen, indem Sie die Schaltfläche **[!UICONTROL Richtlinie erstellen]** auswählen. Dadurch wird ein Assistent geöffnet, mit dem Sie mehrere Bezeichnungen und Einschränkungen von Marketing-Aktionen kombinieren können.

## Durchsetzung von Governance-Strategien

Die Durchsetzung von Governance-Strategien ist offensichtlich ein Schlüsselelement des Rahmens. Die Durchsetzung erfolgt nachgelagert, wenn Daten aktiviert und von Platform gesendet werden, insbesondere mit der Real-time Customer Data Platform, für die Sie möglicherweise eine Lizenzierung vornehmen oder nicht. In jedem Fall ist es nicht im Rahmen dieses Tutorials. Aber damit Sie nicht hängen gelassen werden, können Sie mehr darüber erfahren, wie Richtlinien in diesem Video durchgesetzt werden, das ich bis zum relevanten Teil in die Warteschlange gestellt habe. Sie zeigt Ihnen auch, was passiert, wenn eine Richtlinie verletzt wird.

>[!VIDEO](https://video.tv.adobe.com/v/33631/?t=151&quality=12&learn=on)


## Weitere Ressourcen

* [Dokumentation zu Data Governance](https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html?lang=de)
* [Referenz zur DataSet Service-API](https://www.adobe.io/experience-platform-apis/references/dataset-service/)
* [Referenz zur Governance Policy Service-API](https://www.adobe.io/experience-platform-apis/references/policy-service/)

Gehen wir nun zu [Abfragedienst](run-queries.md).
