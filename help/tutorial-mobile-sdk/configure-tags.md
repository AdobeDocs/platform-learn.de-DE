---
title: Konfigurieren einer Tag-Eigenschaft für Implementierungen von Platform Mobile SDK
description: Erfahren Sie, wie Sie über die Schnittstelle für die [!UICONTROL Datenerfassung] eine Tag-Eigenschaft konfigurieren.
feature: Mobile SDK,Tags
jira: KT-14626
exl-id: 0c4b00cc-34e3-4d08-945e-3fd2bc1b6ccf
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 4%

---

# Konfigurieren einer Tag-Eigenschaft

Erfahren Sie, wie Sie über die Schnittstelle für die [!UICONTROL Datenerfassung] eine Tag-Eigenschaft konfigurieren.

Tags in Adobe Experience Platform sind die nächste Generation von Funktionen für das Tag-Management von Adobe. Tags bieten Kunden eine einfache Möglichkeit, Analyse-, Marketing- und Werbe-Tags bereitzustellen und zu verwalten, die für relevante Kundenerlebnisse erforderlich sind. Weitere Informationen zu [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) finden Sie in der Produktdokumentation.

## Voraussetzungen

Um die Lektion abzuschließen, benötigen Sie die Berechtigung zum Erstellen einer Tag-Eigenschaft. Außerdem ist es hilfreich, ein grundlegendes Verständnis von Tags zu haben.

>[!NOTE]
>
> Platform launch (Client-seitig) heißt jetzt [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)

## Lernziele

In dieser Lektion erfahren Sie Folgendes:

* Installieren und konfigurieren Sie die mobilen Tag-Erweiterungen.
* Generieren Sie die SDK-Installationsanweisungen.

## Ersteinrichtung

1. Erstellen Sie eine neue mobile Tag-Eigenschaft in der Datenerfassungsoberfläche:
   1. Wählen **[!UICONTROL Tags]** im linken Navigationsbereich aus.
   1. Wählen Sie **[!UICONTROL Neue Eigenschaft]**

      ![Erstellen einer Tag-Eigenschaft](assets/tags-new-property.png).
   1. Geben Sie für **[!UICONTROL Name]** &quot;`Luma Mobile App Tutorial`&quot; ein.
   1. Wählen Sie für **[!UICONTROL Platform]** die Option **[!UICONTROL Mobile]** aus.
   1. Wählen Sie **[!UICONTROL Speichern]** aus.

      ![Konfigurieren Sie die Tag-Eigenschaft](assets/tags-property-config.png)

      >[!NOTE]
      >
      > Die standardmäßigen Einverständniseinstellungen für die Edge-basierten Mobile-SDK-Implementierungen, wie Sie sie in dieser Lektion durchführen, stammen von der [!UICONTROL Einverständniserweiterung] und nicht von der [!UICONTROL Datenschutz]-Einstellung in der Tag-Eigenschaftskonfiguration. Sie können die Einverständniserweiterung später in dieser Lektion hinzufügen und konfigurieren. Weitere Informationen finden Sie unter [Dokumentation](https://developer.adobe.com/client-sdks/edge/consent-for-edge-network/).


1. Öffnen Sie die neue Eigenschaft.
1. Erstellen Sie eine Bibliothek:

   1. Navigieren Sie **[!UICONTROL linken Navigationsbereich zu]** Veröffentlichungsablauf“.
   1. Wählen Sie **[!UICONTROL Bibliothek hinzufügen]** aus.

      ![Bibliothek hinzufügen auswählen](assets/tags-create-library.png)

   1. Geben Sie für **[!UICONTROL Name]** &quot;`Initial Build`&quot; ein.
   1. Wählen Sie für **[!UICONTROL Umgebung]** die Option **[!UICONTROL Entwicklung (Entwicklung)]** aus.
   1. Wählen Sie ![Schaltfläche hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Alle geänderten Ressourcen hinzufügen]**.
   1. Wählen Sie **[!UICONTROL Speichern und in Entwicklung erstellen]** aus.

      ![Bibliothek erstellen](assets/tags-save-library.png)

   1. Wählen Sie abschließend **[!UICONTROL Anfänglicher Build]** als Arbeitsbibliothek aus dem Menü **[!UICONTROL Arbeitsbibliothek auswählen]** aus.

      ![Wählen Sie als Arbeitsbibliothek aus](assets/tags-working-library.png)
1. Erweiterungen überprüfen:

   1. Stellen Sie sicher **[!UICONTROL dass „Anfänglicher Build]** als Standardbibliothek ausgewählt ist.

   1. Wählen **[!UICONTROL Erweiterungen]** in der linken Leiste aus.

   1. Wählen Sie die Registerkarte **[!UICONTROL Installiert]** aus.

      Die Erweiterungen [!UICONTROL Mobile Core] und [!UICONTROL Profile] sollten vorinstalliert sein.

      ![Tags installiert](assets/tags-installed.png)

## Erweiterungskonfiguration

1. Stellen Sie sicher, dass Sie sich in **[!UICONTROL Erweiterungen]** in der Eigenschaft Ihrer Mobile App befinden.

1. Wählen Sie **[!UICONTROL Katalog]** aus.

   ![Ersteinrichtung](assets/tags-starting.png)

1. Verwenden Sie das Feld ![Suche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Suche]** um die Erweiterung **Identität** zu finden.

   1. Suchen Sie nach `Identity`.

   2. Wählen Sie die **[!UICONTROL Identität]**-Erweiterung aus.

   3. Wählen Sie **[!UICONTROL Installieren]** aus.

      ![Identity-Installation](assets/tags-identity-install.png)

   Diese Erweiterung erfordert keine weitere Konfiguration.

1. Verwenden Sie das Feld ![Suche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Suche]**, um die Erweiterung **AEP Assurance** zu finden und zu installieren.

   Diese Erweiterung erfordert keine weitere Konfiguration.

1. Verwenden Sie das Feld ![Suche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Suche]**, um die Erweiterung **Einverständnis** zu finden und zu installieren. Im Konfigurationsbildschirm:

   1. Wählen Sie **[!UICONTROL Ausstehend]** aus. In diesem Tutorial verwalten Sie das Einverständnis im Programm weiter. Weitere Informationen zur Einverständniserweiterung finden Sie in [Dokumentation](https://developer.adobe.com/client-sdks/documentation/consent-for-edge-network/).
   1. Wählen Sie **[!UICONTROL In Bibliothek speichern]**.

      ![Einverständniseinstellungen](assets/tags-extension-consent.png)

1. Verwenden Sie das Feld ![Suche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Suche]**, um die Erweiterung **Adobe Experience Platform Edge Network** zu finden und zu installieren.

   1. Wählen **[!UICONTROL unter]** den **[!UICONTROL Datenstrom]** aus, den Sie im [vorherigen Schritt](create-datastream.md) für jede der Umgebungen erstellt haben, z. B. **[!DNL Luma Mobile App]**.

   1. Wenn Sie noch nicht ausgefüllt sind, geben Sie die **[!UICONTROL Edge Network-Domain]** innerhalb der **[!UICONTROL Domain-Konfiguration]** an. Die Edge Network-Domain ist der Name Ihres Unternehmens, gefolgt von `data.adobedc.net`, z. B. `techmarketingdemos.data.adobedc.net`.

   1. Wählen Sie im Menü **[!UICONTROL In Bibliothek speichern]** die Option **[!UICONTROL In Bibliothek speichern und erstellen]**.

      ![Edge-Netzwerkeinstellungen](assets/tags-extension-edge.png)

Ihre Bibliothek wurde für die neuen Erweiterungen und Konfigurationen erstellt. Ein erfolgreicher Build wird durch ein <span style="color:green">●</span> in der Schaltfläche **[!UICONTROL Anfänglicher Build]** angezeigt.


## Generieren von SDK-Installationsanweisungen

1. Wählen **[!UICONTROL Umgebungen]** in der linken Leiste aus.

1. Wählen Sie das Symbol **[!UICONTROL Entwicklung]** install ![Box](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) aus.

   ![Umgebungen - Startbildschirm](assets/tags-environments.png)

1. Wählen Sie **[!UICONTROL Dialogfeld „Mobile-]**&quot; die Registerkarte **[!UICONTROL iOS]** aus.

1. Sie können die ![ kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) um Ihr Projekt mit CocoaPods einzurichten. CocoaPods werden verwendet, um SDK-Versionen und -Downloads zu verwalten. Weitere Informationen finden Sie in der [Dokumentation zu CocoaPods](https://cocoapods.org/). Wenn Sie Android™ als Entwicklungsplattform verwenden, ist Gradle das Tool zur Verwaltung von SDK-Versionen, -Downloads und -Abhängigkeiten. Weitere Informationen finden Sie in der [Gradle-Dokumentation](https://gradle.org/)

   Die Installationsanweisungen bieten einen guten Ausgangspunkt für die Implementierung. Weitere Informationen finden Sie [hier](https://developer.adobe.com/client-sdks/documentation/getting-started/get-the-sdk/).

   >[!INFO]
   >
   >Für den Rest dieses Tutorials verwenden Sie **nicht** die CocoaPods-Anweisungen, sondern eine native Swift Package Manager (SPM)-basierte Einrichtung.
   >

1. Wählen Sie die Registerkarte **[!UICONTROL Swift]** unter **[!UICONTROL Initialisierungs-Code hinzufügen]**. Dieser Code-Block zeigt, wie Sie die erforderlichen SDKs importieren und die Erweiterungen beim Start registrieren. Weitere Informationen hierzu finden Sie unter [ von SDKs](install-sdks.md).

1. Kopieren Sie ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) die **[!UICONTROL Umgebungsdatei-ID]** und speichern Sie sie an einem Ort, wie Sie sie später benötigen. Diese eindeutige ID verweist auf Ihre Entwicklungsumgebung. Jede Umgebung (Produktion, Staging, Entwicklung) verfügt über einen eigenen eindeutigen ID-Wert.

   ![Installationsanweisungen](assets/tags-install-instructions.png)

>[!NOTE]
>
>Die Installationsanweisungen sollten als Ausgangspunkt und nicht als endgültige Dokumentation betrachtet werden. Die neuesten SDK-Versionen und Code-Beispiele finden Sie in der offiziellen [Dokumentation](https://developer.adobe.com/client-sdks/home/).

## Architektur mobiler Tags

Wenn Sie mit der Web-Version von Tags (früher Launch) vertraut sind, müssen Sie sich mit den Unterschieden auf Mobilgeräten vertraut machen.

* Im Web wird eine Tag-Eigenschaft in JavaScript gerendert, die dann (normalerweise) in der Cloud gehostet wird. Diese JavaScript-Datei wird direkt auf der Website referenziert.

* In einer mobilen Tag-Eigenschaft werden Regeln und Konfigurationen in JSON-Dateien gerendert, die in der Cloud gehostet werden. Die JSON-Dateien werden von der Mobile Core-Erweiterung in der Mobile App heruntergeladen und gelesen. Erweiterungen sind separate SDKs, die zusammenarbeiten. Wenn Sie Ihrer Tag-Eigenschaft eine Erweiterung hinzufügen, müssen Sie auch die App aktualisieren. Wenn Sie eine Erweiterungseinstellung ändern oder eine Regel erstellen, werden diese Änderungen in der App angezeigt, sobald Sie die aktualisierte Tag-Bibliothek veröffentlichen. Dank dieser Flexibilität können Sie Einstellungen (z. B. die Adobe Analytics Report Suite-ID) ändern oder sogar das Verhalten Ihrer App ändern (mithilfe von Datenelementen und Regeln, wie Sie in späteren Lektionen sehen werden), ohne den Code in Ihrer App ändern und den App Store erneut senden zu müssen.

>[!SUCCESS]
>
>Sie haben jetzt eine mobile Tag-Eigenschaft, die Sie im Rest dieses Tutorials verwenden können.
>
>Vielen Dank, dass Sie sich Zeit genommen haben, um mehr über Adobe Experience Platform Mobile SDK zu erfahren. Wenn Sie Fragen haben, allgemeines Feedback geben möchten oder Vorschläge für zukünftige Inhalte haben, teilen Sie diese auf diesem [Experience League Community-Diskussionsbeitrag](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Weiter: **[Installieren von SDKs](install-sdks.md)**
