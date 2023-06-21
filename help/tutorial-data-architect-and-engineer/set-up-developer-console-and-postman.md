---
title: Einrichten von Developer Console und Postman
seo-title: Set up Developer Console and Postman | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Einrichten von Developer Console und Postman
description: In dieser Lektion richten Sie ein Projekt in der Adobe Developer-Konsole ein und stellen Ihnen [!DNL Postman] Sammlungen , damit Sie mit der Verwendung von Platform-APIs beginnen können.
role: Data Architect, Data Engineer
feature: API
kt: 4348
thumbnail: 4348-set-up-developer-console-and-postman.jpg
exl-id: 72b541fa-3ea1-4352-b82b-c5b79ff98491
source-git-commit: 35242a037bc79f18e90399c47e47064634d26a37
workflow-type: tm+mt
source-wordcount: '1320'
ht-degree: 2%

---

# Einrichten der Entwicklerkonsole und [!DNL Postman]

<!--30min-->

In dieser Lektion richten Sie ein Projekt in der Adobe Developer-Konsole ein und laden [!DNL Postman] Sammlungen, damit Sie mit der Verwendung von Platform-APIs beginnen können.

Um die API-Übungen in diesem Tutorial abzuschließen, müssen Sie [Laden Sie die Postman-App für Ihr Betriebssystem herunter.](https://www.postman.com/downloads/) Postman ist zwar nicht erforderlich, um Experience Platform-APIs zu verwenden, erleichtert aber API-Workflows. Adobe Experience Platform bietet Dutzende von Postman-Kollektionen, die Ihnen bei der Ausführung von API-Aufrufen und der Funktionsweise helfen. Im Rest dieses Tutorials werden einige Kenntnisse über Postman vorausgesetzt. Informationen zur Unterstützung finden Sie im Abschnitt [Postman-Dokumentation](https://learning.postman.com/).

Platform ist als API-Erste konzipiert. Auch wenn Schnittstellenoptionen für alle Hauptaufgaben vorhanden sind, sollten Sie die Platform-API irgendwann verwenden. Um beispielsweise Daten zu erfassen, verschieben Sie Elemente zwischen Sandboxes, automatisieren Sie Routineaufgaben oder verwenden Sie neue Platform-Funktionen, bevor die Benutzeroberfläche erstellt wurde.

**Datenarchitekten** und **Dateningenieure** Möglicherweise müssen Sie die Platform-API außerhalb dieses Tutorials verwenden.

## Erforderliche Berechtigungen

Im [Berechtigungen konfigurieren](configure-permissions.md) Lektion erstellen Sie alle Zugriffssteuerungen, die zum Abschluss dieser Lektion erforderlich sind.

<!--
* Permission item Sandboxes > `Luma Tutorial`
* Developer-role access to the `Luma Tutorial Platform` product profile
-->

## Einrichten der Adobe Developer-Konsole

Adobe Developer Console ist das Entwicklerziel für den Zugriff auf Adobe-APIs und SDKs, das Abhören von nahezu Echtzeit-Ereignissen, das Ausführen von Funktionen in Runtime oder das Erstellen von Plug-ins oder App Builder-Anwendungen. Sie greifen damit auf die Experience Platform-API zu. Weitere Informationen finden Sie unter [Dokumentation zur Adobe Developer Console](https://www.adobe.io/apis/experienceplatform/console/docs.html)

1. Erstellen Sie auf Ihrem lokalen Computer einen Ordner mit dem Namen `Luma Tutorial Assets` für Dateien, die im Tutorial verwendet werden.

1. Öffnen Sie die [Adobe Developer-Konsole](https://console.adobe.io){target="_blank"}

1. Melden Sie sich an und vergewissern Sie sich, dass Sie sich in der richtigen Organisation befinden

1. Auswählen **[!UICONTROL Neues Projekt erstellen]** in [!UICONTROL Schnellstart] Menü.

   ![Neues Projekt erstellen](assets/adobeio-createNewProject.png)


1. Wählen Sie im neu erstellten Projekt die **[!UICONTROL Projekt bearbeiten]** button
1. Ändern Sie die **[!UICONTROL Projekttitel]** nach `Luma Tutorial API Project` (Fügen Sie am Ende Ihren Namen hinzu, wenn mehrere Personen aus Ihrem Unternehmen dieses Tutorial absolvieren)
1. Wählen Sie **[!UICONTROL Speichern]** aus

   ![Konfiguration der Adobe Developer Console-Projekt-API](assets/adobeio-renameProject.png)


1. Auswählen **[!UICONTROL API hinzufügen]**

   ![Konfiguration der Adobe Developer Console-Projekt-API](assets/adobeio-addAPI.png)

1. Filtern der Liste durch Auswahl **[!UICONTROL Adobe Experience Platform]**

1. Wählen Sie in der Liste der verfügbaren APIs **[!UICONTROL Experience Platform-API]** und wählen Sie **[!UICONTROL Nächste]**.

   ![Konfiguration der Adobe Developer Console-Projekt-API](assets/adobeio-AEPAPI.png)

1. Auswählen **[!UICONTROL OAuth Server-zu-Server]** als Berechtigung und wählen Sie **[!UICONTROL Nächste]**.
   ![OAuth Server-zu-Server auswählen](assets/adobeio-choose-auth.png)

1. Wählen Sie die `AEP-Default-All-Users` Produktprofil und wählen Sie **[!UICONTROL Konfigurierte API speichern]**

   ![Profil auswählen](assets/adobeio-selectProductProfile.png)

1. Jetzt wurde Ihr Entwicklerkonsole-Projekt erstellt!

1. Im **[!UICONTROL Testen]** -Abschnitt der Seite, wählen Sie **[!UICONTROL Herunterladen für Postman]** und wählen Sie **[!UICONTROL OAuth Server-zu-Server]** zum Herunterladen der [!DNL Postman] Umgebungs-JSON-Datei. Speichern Sie die `oauth_server_to_server.postman_environment.json` in `Luma Tutorial Assets` Ordner.


   ![Konfiguration der Adobe Developer Console-Projekt-API](assets/adobeio-io-api.png)

## Bitten Sie einen Systemadministrator, die API-Berechtigung zur Rolle hinzuzufügen.

Damit Sie die API-Anmeldeinformationen für die Interaktion mit Experience Platform verwenden können, muss ein Systemadministrator die API-Anmeldeinformationen der in der vorherigen Lektion erstellten Rolle zuweisen.  Wenn Sie kein Systemadministrator sind, senden Sie ihnen Folgendes:

1. Die [!UICONTROL Name] Ihrer API-Anmeldedaten (`Credential in Luma Tutorial API Project`)
1. Die [!UICONTROL Email für technische Konten] Ihrer Anmeldedaten (dies hilft dem Systemadministrator, die Anmeldedaten zu finden)

   ![[!UICONTROL Name] und [!UICONTROL Email für technische Konten] Ihrer Anmeldedaten](assets/postman-credentialDetails.png)

Hier finden Sie die Anweisungen für den Systemadministrator:

1. Anmelden [Adobe Experience Platform](https://platform.adobe.com)
1. Auswählen **[!UICONTROL Berechtigungen]** in der linken Navigation, die Sie zum [!UICONTROL Rollen] Bildschirm
1. Öffnen Sie die `Luma Tutorial Platform` Rolle
   ![Rolle öffnen](assets/postman-openRole.png)
1. Wählen Sie die **[!UICONTROL API-Anmeldeinformationen]** tab
1. Auswählen **[!UICONTROL API-Anmeldeinformationen hinzufügen]**
   ![Berechtigung hinzufügen](assets/postman-addCredential.png)
1. Suchen Sie die `Credential in Luma Tutorial API Project` Berechtigung, mit der [!UICONTROL Email für technische Konten] bereitgestellt vom Tutorial-Teilnehmer, wenn die Liste lang ist
1. Berechtigung auswählen
1. Wählen Sie **[!UICONTROL Speichern]** aus


   ![Berechtigung hinzufügen](assets/postman-findCredential.png)

## Einrichten von Postman

>[!CAUTION]
>
>Die Benutzeroberfläche von Postman wird regelmäßig aktualisiert. Die Screenshots in diesem Tutorial wurden mit Postman v10.15.1 für Mac erstellt, die Benutzeroberflächenoptionen wurden jedoch möglicherweise geändert.


1. Herunterladen und installieren [[!DNL Postman]](https://www.postman.com/downloads/)
1. Öffnen [!DNL Postman] und erstellen Sie einen Arbeitsbereich
   ![Importumgebung](assets/postman-createWorkspace.png)

1. Importieren Sie die heruntergeladene JSON-Umgebungsdatei, `oauth_server_to_server.postman_environment.json`
   ![Importumgebung](assets/postman-importEnvironment.png)
1. In [!DNL Postman], wählen Sie Ihre Umgebung im Dropdown-Menü aus.

1. Wählen Sie das Symbol aus, um die Umgebungsvariablen anzuzeigen:

   ![Umgebung ändern](assets/postman-changeEnvironment.png)


### Sandbox-Name und Mandanten-ID hinzufügen

Die `SANDBOX_NAME` und `TENANT_ID` und `CONTAINER_ID` -Variablen sind nicht im Adobe Developer Console-Export enthalten, daher fügen wir sie manuell hinzu:

1. In [!DNL Postman], öffnen Sie die **Umgebungsvariablen**
1. Wählen Sie die **Bearbeiten** Link rechts neben dem Umgebungsnamen
1. Im **Neues Variablenfeld hinzufügen**, eingeben `SANDBOX_NAME`
1. Geben Sie in beide Wertfelder ein. `luma-tutorial`, der Name, den wir unserer Sandbox in der vorherigen Lektion gegeben haben. Wenn Sie einen anderen Namen für Ihre Sandbox verwendet haben, z. B. &quot;luma-tutorial-ignatiusjreilly&quot;, stellen Sie sicher, dass Sie diesen Wert verwenden.
1. Im **Neues Variablenfeld hinzufügen**, eingeben `TENANT_ID`
1. Wechseln Sie zu Ihrem Webbrowser und suchen Sie nach der Mandanten-ID Ihres Unternehmens, indem Sie die Benutzeroberfläche von Experience Platform aufrufen und den Teil der URL extrahieren. *nach dem @-Zeichen*. Beispielsweise lautet meine Mandanten-ID `techmarketingdemos` aber Ihre ist anders:

   ![Beziehen der Mandanten-ID über die Platform-URL](assets/postman-getTenantId.png)

1. Kopieren Sie diesen Wert und kehren Sie zum [!DNL Postman] Bildschirm &quot;Umgebungen verwalten&quot;
1. Fügen Sie Ihre Mandanten-ID in beide Wertfelder ein.
1. Im **Neues Variablenfeld hinzufügen**, eingeben `CONTAINER_ID`
1. Eingabe `global` in beide Wertfelder

   >[!NOTE]
   >
   >`CONTAINER_ID` ist ein Feld, dessen Wert wir während des Tutorials mehrmals ändern. Wann `global` verwendet wird, interagiert die API mit von Adobe bereitgestellten Elementen in Ihrem Platform-Konto. Wann `tenant` verwendet wird, interagiert die API mit Ihren eigenen benutzerdefinierten Elementen.

1. Wählen Sie **Speichern** aus

   ![Die Felder SANDBOX_NAME, TENANT_ID und CONTAINER_ID wurden als Umgebungsvariablen hinzugefügt](assets/postman-addEnvFields.png)



## API-Aufrufe erstellen

### Zugriffstoken abrufen

Adobe bietet eine umfangreiche Auswahl an [!DNL Postman] Sammlungen, die Ihnen bei der Erforschung der API von Experience Platform helfen. Diese Sammlungen befinden sich im [Adobe Experience Platform Postman-Beispiele für GitHub-Repository](https://github.com/adobe/experience-platform-postman-samples). Sie sollten dieses Repo mit einem Lesezeichen versehen, da Sie es in diesem Tutorial und später bei der Implementierung der Experience Platform für Ihr eigenes Unternehmen mehrmals verwenden werden.

Die erste Sammlung funktioniert mit den Adobe Identity Management Service (IMS)-APIs. Dies ist eine praktische Methode, um ein Zugriffstoken aus Postman abzurufen.

So generieren Sie das Zugriffstoken:

1. Laden Sie die [Erfassung von Identity Management Service-APIs](https://github.com/adobe/experience-platform-postman-samples/blob/master/apis/ims/Identity%20Management%20Service.postman_collection.json) auf `Luma Tutorial Assets` Ordner
1. Importieren Sie die Sammlung in [!DNL Postman]
1. Anforderung auswählen **oAuth: Zugriffstoken anfordern** Anforderung und Auswahl **Senden**
1. Sie sollten eine `200 OK` Antwort mit einem Zugriffstoken in der Antwort

   ![Token anfordern](assets/postman-requestToken.png)

1. Das Zugriffstoken sollte automatisch als **ACCESS_TOKEN** Umgebungsvariable Ihres [!DNL Postman] Umgebung.

   ![Postman](assets/postman-config.png)


### Interagieren mit einer Platform-API

Nehmen wir nun einen Platform-API-Aufruf vor, um zu bestätigen, dass wir alles korrekt konfiguriert haben.

Öffnen Sie die [Experience Platform [!DNL Postman] Sammlungen in GitHub](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform). Auf dieser Seite finden Sie viele Sammlungen für verschiedene Platform-APIs. Ich empfehle dringend, ein Lesezeichen zu setzen.

Nehmen wir nun unseren ersten API-Aufruf vor:

1. Laden Sie die [Schema Registry-API-Sammlung](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Schema%20Registry%20API.postman_collection.json) auf `Luma Tutorial Assets` Ordner
1. Importieren in [!DNL Postman]
1. Öffnen **Schema Registry-API > Schemas > Schemas auflisten**
1. Sehen Sie sich die **Parameter** und **Kopfzeilen** -Tabs und beachten Sie, dass sie einige der zuvor eingegebenen Umgebungsvariablen enthalten.
1. Beachten Sie Folgendes: **Kopfzeilen > Wertefeld akzeptieren** auf `application/vnd.adobe.xed-id+json`. Für die Schema Registry-APIs ist eine dieser Voraussetzungen erforderlich [angegebene Accept-Kopfzeilenwerte](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/getting-started.html?lang=en#accept) , die unterschiedliche Formate in der Antwort bereitstellen.
1. Auswählen **Senden** , um Ihren ersten Platform-API-Aufruf durchzuführen!

Hoffentlich haben Sie einen erfolgreichen `200 OK` Antwort mit einer Liste der verfügbaren von der Adobe bereitgestellten XDM-Schemas in Ihrer Sandbox, wie unten dargestellt.

![Erster API-Aufruf in Postman](assets/postman-firstAPICall.png)

Wenn Ihr Aufruf nicht erfolgreich war, versuchen Sie einen Moment, das Debugging mithilfe der Fehlerantwortendetails des API-Aufrufs durchzuführen und überprüfen Sie die oben beschriebenen Schritte. Wenn Sie feststecken bleiben, bitten Sie um Hilfe im [Community-Forum](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform/ct-p/adobe-experience-platform-community?profile.language=de) oder verwenden Sie den Link rechts auf dieser Seite, um ein Problem zu protokollieren.

Mit Ihren Plattformberechtigungen, Sandbox und [!DNL Postman] einrichten, können Sie [Modelldaten in Schemata](model-data-in-schemas.md)!
