---
title: Hinzufügen und Konfigurieren der Web SDK-Erweiterung
description: Erfahren Sie, wie Sie die Web SDK-Erweiterung zu Ihrer Tags-Eigenschaft hinzufügen und konfigurieren, um Ihnen die Funktionen bereitzustellen, die Sie in weiteren Lektionen benötigen, um die Migration abzuschließen.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16758
source-git-commit: 7ae56d997884cf1558e72c0ad553df1c5d43c081
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Hinzufügen und Konfigurieren der Web SDK-Erweiterung

Erfahren Sie, wie Sie die Web SDK-Erweiterung in Ihrer Tags-Eigenschaft hinzufügen und konfigurieren, um Ihnen die Funktionen bereitzustellen, die Sie in weiteren Lektionen benötigen, um die Migration abzuschließen.
Führen Sie die folgenden Schritte aus, um die Erweiterung hinzuzufügen und zu konfigurieren:

1. Navigieren Sie zur Experience Platform-Datenerfassung. Dies lässt sich auf zwei Arten erreichen:
   1. Wechseln Sie zur [Adobe Experience Platform](https://platform.adobe.com/)Benutzeroberfläche und wählen Sie **[!UICONTROL Tags]** unten im linken Navigationsbereich aus.

      ![Zugriff auf Tags 1](assets/access-tags-1.jpg)
   1. Wenn Sie keinen Zugriff auf Platform haben, können Sie den Programmumschalter (9 Punkte) oben rechts im Fenster verwenden und Datenerfassung auswählen (nachdem Sie sich bei Experience.Adobe.com angemeldet haben).

      ![Zugriff auf Tags 2](assets/access-tags-2.jpg)
1. Suchen Sie Ihre Tag-Eigenschaft, die Sie in die Web-SDK migrieren, und wählen Sie sie aus.
1. Wählen Sie im linken Navigationsbereich der Tag-Eigenschaft die Option **[!UICONTROL Erweiterungen]** aus.
1. Wählen Sie **[!UICONTROL Katalog]** oben aus, um eine Liste aller verfügbaren Erweiterungen anzuzeigen.
1. Suchen Sie nach der Erweiterung **[!UICONTROL Adobe Experience Platform Web SDK]** und wählen Sie sie aus. Klicken Sie dann **rechts auf** Installieren“.

   ![Suchen der Web SDK-Erweiterung](assets/find-the-websdk-extension.jpg){style="border:1px solid lightslategray"}

1. Die Konfigurationseinstellungen der Erweiterung werden angezeigt. Suchen Sie den Abschnitt Datenströme und legen Sie die Experience Platform-Sandbox fest, die Sie für diese Migration verwenden möchten (Dropdown-Listen „Umgebung“ für alle drei Umgebungen). Wenn Sie nur Adobe Analytics migrieren und keine Daten an Adobe Experience Platform senden möchten, wählen Sie die **Produktions-)** aus. Wenn Sie diese Verhaltensanalysedaten zur Verwendung in den Anwendungen an die Experience Platform senden möchten, wählen Sie die Sandbox aus, die Sie dafür verwenden möchten. Sie sollten wahrscheinlich zunächst eine Entwicklungs-Sandbox auswählen, bis Sie mit der Migration fertig sind und Ihren Platform-Service hinzugefügt/getestet haben.
1. Verbinden Sie vor allem Ihren Code und Ihre Einstellungen hier in Tags mit der Edge, indem Sie die Datenströme auswählen, die Sie im vorherigen Schritt für Produktions-, Staging- und Entwicklungsumgebungen erstellt haben.

   ![Datenstromauswahl](assets/choose-datastreams.jpg){style="border:1px solid lightslategray"}

1. Scrollen Sie nach unten und beachten Sie, **die Einstellungen** Identität“ standardmäßig ausgewählt sind. Lassen Sie diese Kontrollkästchen aktiviert, da sie dazu beitragen, Ihre Website-Besucher bei der Migration zur Web-SDK korrekt zu identifizieren. Weitere Informationen finden Sie in der Dokumentation, die unten verlinkt ist.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

>[!NOTE]
>
>Ihre Tags-Eigenschaft verfügt jetzt über eine grundlegende Installation und Konfiguration der Web SDK-Erweiterung. Wir verwenden Teile der Web SDK-Erweiterung, während wir während dieses Migrationstutorials Datenelemente und Regeln erstellen oder ändern. Wir werden jedoch die Erweiterungskonfigurationselemente im Tutorial nicht mehr ändern. Zusätzliche Konfigurationselemente können und sollten für zusätzliche Anwendungsfälle verwendet werden. Eine ausführliche Dokumentation zu diesen Konfigurationen finden Sie unter [Konfigurieren der Tag-Erweiterung für Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/web-sdk/web-sdk-extension-configuration).
