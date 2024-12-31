---
title: Beispieldaten nach Adobe Experience Platform importieren
description: Erfahren Sie anhand einiger Beispieldaten, wie Sie eine Experience Platform-Sandbox-Umgebung einrichten.
feature: API
role: Developer
level: Experienced
jira: KT-7349
last-substantial-update: 2023-06-21T00:00:00Z
exl-id: da94f4bd-0686-4d6a-a158-506f2e401b4e
source-git-commit: 4db88dbae923d37884391a65ff8fc16f53e19187
workflow-type: tm+mt
source-wordcount: '1776'
ht-degree: 6%

---

# Beispieldaten nach Adobe Experience Platform importieren

Erfahren Sie, wie Sie eine Experience Platform-Sandbox-Umgebung mit Beispieldaten einrichten. Mithilfe einer Postman-Sammlung können Sie Feldergruppen, Schemata und Datensätze erstellen und dann Beispieldaten in Experience Platform importieren.

## Anwendungsfall für Beispieldaten

Experience Platform-Business-Anwender müssen oft eine Reihe von Schritten durchlaufen, darunter die Identifizierung von Feldergruppen, die Erstellung von Schemata, die Vorbereitung von Daten, die Erstellung von Datensätzen und die Aufnahme von Daten, bevor sie die Marketing-Funktionen von Experience Platform erkunden können. In diesem Tutorial werden einige der Schritte automatisiert, damit Sie Daten so schnell wie möglich in eine Platform-Sandbox übertragen können.

Dieses Tutorial konzentriert sich auf eine fiktive Einzelhandelsmarke namens Luma. Sie investieren in Adobe Experience Platform, um Treue-, CRM-, Produktkatalog- und Offline-Kaufdaten in Echtzeit-Kundenprofilen zu kombinieren und diese Profile zu aktivieren, damit sie ihr Marketing auf die nächste Stufe bringen können. Wir haben Beispieldaten für Luma generiert. Im weiteren Verlauf dieses Tutorials importieren Sie diese Daten in eine Ihrer Experience Platform-Sandbox-Umgebungen.

>[!NOTE]
>
>Das Ergebnis dieses Tutorials ist eine Sandbox mit ähnlichen Daten wie das Tutorial [Erste Schritte mit Adobe Experience Platform für Datenarchitekten und Dateningenieure](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=de). Sie wurde im April 2023 aktualisiert, um die [Journey Optimizer-Herausforderungen zu ](https://experienceleague.adobe.com/docs/journey-optimizer-learn/challenges/introduction-and-prerequisites.html?lang=de). Sie wurde im Juni 2023 aktualisiert, um die Authentifizierungsmethode auf OAuth umzustellen.


## Voraussetzungen

* Sie haben Zugriff auf Experience Platform-APIs und wissen, wie Sie sich authentifizieren. Andernfalls sehen Sie sich dieses [Tutorial](https://experienceleague.adobe.com/docs/platform-learn/tutorials/platform-api-authentication.html?lang=de) an.
* Sie haben Zugriff auf eine Experience Platform-Entwicklungs-Sandbox.
* Sie kennen Ihre Experience Platform-Mandanten-ID. Sie können sie erhalten, indem Sie eine authentifizierte [API-Anfrage](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/getting-started.html?lang=en#know-your-tenant_id)
oder indem Sie sie bei der Anmeldung bei Ihrem Platform-Konto aus der URL extrahieren. Bei der folgenden URL lautet der Mandant beispielsweise &quot;`techmarketingdemos`&quot; `https://experience.adobe.com/#/@techmarketingdemos/sname:prod/platform/home`.

## Verwenden [!DNL Postman] {#postman}

### Einrichten von Umgebungsvariablen

Bevor Sie die Schritte ausführen, stellen Sie sicher, dass Sie das Programm [Postman](https://www.postman.com/downloads/) heruntergeladen haben. Los geht‘s!

1. Laden Sie die Datei [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) herunter, die alle für dieses Tutorial erforderlichen Dateien enthält.

   >[!NOTE]
   >
   >Die in der Datei [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) enthaltenen Benutzerdaten sind fiktiv und dürfen nur zu Demonstrationszwecken verwendet werden.

1. Verschieben Sie die Datei `platform-utils-main.zip` aus dem Downloads-Ordner an den gewünschten Speicherort auf Ihrem Computer und entpacken Sie sie.
1. Öffnen Sie im Ordner `luma-data` alle `json` Dateien in einem Texteditor und ersetzen Sie alle Instanzen von `_yourTenantId` durch Ihre eigene Mandanten-ID mit vorangestelltem Unterstrich.
1. Öffnen Sie `luma-offline-purchases.json`, `luma-inventory-events.json` und `luma-web-events.json` in einem Texteditor und aktualisieren Sie alle Zeitstempel, sodass die Ereignisse im letzten Monat auftreten (suchen Sie beispielsweise nach `"timestamp":"2022-11` und ersetzen Sie Jahr und Monat)
1. Notieren Sie sich den Speicherort des entpackten Ordners, da Sie ihn später beim Einrichten der Umgebungsvariablen `FILE_PATH` [!DNL Postman] benötigen:

   >[!NOTE]
   > Um den Dateipfad auf Ihrer Mac zu erhalten, navigieren Sie zum Ordner &quot;`platform-utils-main`&quot;, klicken Sie mit der rechten Maustaste auf den Ordner und wählen Sie **Option &quot;**&quot;.
   >
   > ![MAC-Dateipfad](../assets/data-generator/images/mac-file-path.png)

   >[!NOTE]
   > Um den Dateipfad in Ihren Fenstern zu erhalten, klicken Sie auf , um den Speicherort des gewünschten Ordners zu öffnen, und klicken Sie dann mit der rechten Maustaste auf rechts neben dem Pfad in der Adressleiste. Kopieren Sie die Adresse, um den Dateipfad abzurufen.
   > 
   > ![Windows-Dateipfad](../assets/data-generator/images/windows-file-path.png)

1. Öffnen Sie [!DNL Postman] und erstellen Sie einen Arbeitsbereich über das **Arbeitsbereiche** Dropdown-Menü:\
   ![Arbeitsbereich erstellen](../assets/data-generator/images/create-workspace.png)
1. Geben Sie einen **Namen** und optional **Zusammenfassung** für Ihren Arbeitsbereich ein und klicken Sie auf **Workspace erstellen**. [!DNL Postman] wechseln zu Ihrem neuen Arbeitsbereich, wenn Sie ihn erstellen.
   ![Arbeitsbereich speichern](../assets/data-generator/images/save-workspace.png)
1. Passen Sie jetzt einige Einstellungen an, um die [!DNL Postman] Sammlungen in diesem Arbeitsbereich auszuführen. Klicken Sie in der Kopfzeile von [!DNL Postman] auf das Zahnradsymbol und wählen Sie **Einstellungen** aus, um das Modal „Einstellungen“ zu öffnen. Sie können auch den Tastaturbefehl (CMD/STRG + ,) verwenden, um das Modal zu öffnen.
1. Aktualisieren Sie auf der Registerkarte `General` die maximale Wartezeit für Anfragen in ms, um `allow reading file outside this directory` zu `5000 ms` und zu aktivieren
   ![Einstellungen](../assets/data-generator/images/settings.png)

   >[!NOTE]
   > Wenn Dateien aus dem Arbeitsverzeichnis geladen werden, laufen sie problemlos auf allen Geräten, wenn dieselben Dateien auf den anderen Geräten gespeichert werden. Wenn Sie jedoch Dateien von außerhalb des Arbeitsverzeichnisses ausführen möchten, muss eine Einstellung aktiviert werden, um denselben Zweck anzugeben. Wenn Ihr `FILE_PATH` nicht mit dem Arbeitsordnerpfad des [!DNL Postman] übereinstimmt, sollte diese Option aktiviert werden.

1. Schließen Sie das Bedienfeld **Einstellungen**.
1. Wählen Sie **Umgebungen** und dann **Importieren**:
   ![Umgebungsimport](../assets/data-generator/images/env-import.png)
1. Importieren Sie die heruntergeladene JSON-Umgebungsdatei `DataInExperiencePlatform.postman_environment`
1. Wählen Sie in Postman oben rechts Ihre Umgebung aus und klicken Sie auf das Augensymbol, um die Umgebungsvariablen anzuzeigen:
   ![Umgebungsauswahl](../assets/data-generator/images/env-selection.png)

1. Stellen Sie sicher, dass die folgenden Umgebungsvariablen ausgefüllt sind. Um zu erfahren, wie Sie den Wert der Umgebungsvariablen abrufen, lesen Sie das Tutorial [Authentifizieren bei Experience Platform-APIs](/help/platform/authentication/platform-api-authentication.md), in dem Sie schrittweise Anweisungen finden.

   * `CLIENT_SECRET`
   * `API_KEY` - `Client ID` in Adobe Developer Console
   * `SCOPES`
   * `TECHNICAL_ACCOUNT_ID`
   * `IMS`
   * `IMS_ORG` - `Organization ID` in Adobe Developer Console
   * `SANDBOX_NAME`
   * `TENANT_ID` - Stellen Sie sicher, dass Sie mit einem Unterstrich führen, z. B. `_techmarketingdemos`
   * `CONTAINER_ID`
   * `platform_end_point`
   * `FILE_PATH` - Verwenden Sie den lokalen Ordnerpfad, in den Sie die `platform-utils-main.zip` entpackt haben. Stellen Sie sicher, dass der Ordnername enthalten ist, z. B. `/Users/dwright/Desktop/platform-utils-main`

1. **Speichern** der aktualisierten Umgebung

### Postman-Sammlungen importieren

Als Nächstes müssen Sie die Sammlungen in Postman importieren.

1. Wählen Sie **Sammlungen** und dann die Importoption aus:

   ![Sammlungen](../assets/data-generator/images/collections.png)

1. Importieren Sie die folgenden Sammlungen:

   * `0-Authentication.postman_collection.json`
   * `1-Luma-Loyalty-Data.postman_collection.json`
   * `2-Luma-CRM-Data.postman_collection.json`
   * `3-Luma-Product-Catalog.postman_collection.json`
   * `4-Luma-Offline-Purchase-Events.postman_collection.json`
   * `5-Luma-Product-Inventory-Events.postman_collection.json`
   * `6-Luma-Test-Profiles.postman_collection.json`
   * `7-Luma-Web-Events.postman_collection.json`

   ![Sammlungen importieren](../assets/data-generator/images/collection-files.png)

### Authentifizieren

Als Nächstes müssen Sie sich authentifizieren und ein Benutzer-Token generieren. Beachten Sie, dass die in diesem Tutorial verwendeten Methoden zur Token-Generierung nur für die Verwendung außerhalb der Produktion geeignet sind. Beim lokalen Signieren wird eine JavaScript-Bibliothek von einem Drittanbieter-Host geladen, und beim Remote-Signieren wird der private Schlüssel an einen Adobe-eigenen und betriebenen Webservice gesendet. Während Adobe diesen privaten Schlüssel nicht speichert, sollten Produktionsschlüssel niemals mit anderen geteilt werden.

1. Öffnen Sie die `0-Authentication`, wählen Sie die `OAuth: Request Access Token` aus und klicken Sie auf `SEND` , um sich zu authentifizieren und das Zugriffstoken abzurufen.

   ![Sammlungen importieren](../assets/data-generator/images/authentication.png)

1. Überprüfen Sie die Umgebungsvariablen, und beachten Sie, dass die `ACCESS_TOKEN` jetzt ausgefüllt ist.

### Datenimport

Jetzt können Sie die Daten in Ihre Platform-Sandbox vorbereiten und importieren. Die Postman-Kollektionen, die Sie importiert haben, erledigen alle Aufgaben!

1. Öffnen Sie die Sammlung `1-Luma-Loyalty-Data` und klicken Sie auf **Registerkarte Übersicht** Ausführen“, um einen Sammlungsrunner zu starten.

   ![Sammlungen importieren](../assets/data-generator/images/loyalty.png)

1. Wählen Sie im Fenster „Sammlungsausführung“ die Umgebung aus dem Dropdown-Menü aus, aktualisieren Sie **Verzögerung** auf `4000ms`, aktivieren Sie die Option **Antworten speichern** und stellen Sie sicher, dass die Ausführungsreihenfolge korrekt ist. Klicken Sie auf **Schaltfläche „Luma-Treuedaten ausführen**

   ![Sammlungen importieren](../assets/data-generator/images/loyalty-run.png)

   >[!NOTE]
   >
   >**1-Luma-Loyalty-Data** erstellt ein Schema für Kundenloyalitätsdaten. Das Schema basiert auf der Klasse „XDM Individual Profile“, einer Standardfeldgruppe sowie einer benutzerdefinierten Feldgruppe und einem Datentyp. Die -Sammlung erstellt einen Datensatz mit dem -Schema und lädt Beispieldaten zur Kundentreue in Adobe Experience Platform hoch.

   >[!NOTE]
   >
   >Wenn Sammlungsanfragen beim Postman-Sammlungsrunner fehlschlagen, stoppen Sie die Ausführung und führen Sie die Sammlungsanfragen einzeln aus.

1. Wenn alles gut geht, sollten alle Anfragen in der `Luma-Loyalty-Data`-Sammlung übergeben werden.

   ![Treueergebnis](../assets/data-generator/images/loyalty-result.png)

1. Melden wir uns jetzt bei der [Adobe Experience Platform-](https://platform.adobe.com/) an und navigieren zu den Datensätzen.
1. Öffnen Sie den `Luma Loyalty Dataset` Datensatz, und im Fenster Datensatzaktivität können Sie einen erfolgreichen Batch-Vorgang anzeigen, der 1.000 Datensätze aufgenommen hat. Sie können auch auf die Option Datensatz in der Vorschau anzeigen klicken, um die aufgenommenen Datensätze zu überprüfen. Möglicherweise müssen Sie mehrere Minuten warten, um zu bestätigen, dass 1000 [!UICONTROL neue Profilfragmente] erstellt wurden.
   ![Treueprogramm-Datensatz](../assets/data-generator/images/loyalty-dataset.png)
1. Wiederholen Sie die Schritte 1 bis 3, um die anderen Sammlungen auszuführen:
   * `2-Luma-CRM-Data.postman_collection.json` erstellt ein Schema und einen ausgefüllten Datensatz für CRM-Daten von Kunden. Das Schema basiert auf der Klasse „XDM Individual Profile“, die demografische Details, persönliche Kontaktdaten, Voreinstellungsdetails und eine benutzerdefinierte Identitätsfeldgruppe enthält.
   * `3-Luma-Product-Catalog.postman_collection.json` erstellt ein Schema und einen ausgefüllten Datensatz für Produktkataloginformationen. Das Schema basiert auf einer benutzerdefinierten Produktkatalogklasse und verwendet eine benutzerdefinierte Produktkatalog-Feldergruppe.
   * `4-Luma-Offline-Purchase-Events.postman_collection.json` erstellt ein Schema und einen ausgefüllten Datensatz für Offline-Kaufereignisdaten von Kunden. Das Schema basiert auf der XDM ExperienceEvent-Klasse und umfasst eine benutzerdefinierte Identität sowie Feldergruppen für Commerce-Details.
   * `5-Luma-Product-Inventory-Events.postman_collection.json` erstellt ein Schema und einen ausgefüllten Datensatz für Ereignisse im Zusammenhang mit Produkten, die auf Lager oder nicht vorrätig sind. Das Schema basiert auf einer benutzerdefinierten Geschäftsereignisklasse und einer benutzerdefinierten Feldergruppe.
   * `6-Luma-Test-Profiles.postman_collection.json` erstellt ein Schema und einen ausgefüllten Datensatz mit Testprofilen zur Verwendung in Adobe Journey Optimizer
   * `7-Luma-Web-Events.postman_collection.json` erstellt ein Schema und einen ausgefüllten Datensatz mit einfachen historischen Web-Daten.


## Validierung

Die Beispieldaten wurden so entworfen, dass nach der Ausführung der Sammlungen Echtzeit-Kundenprofile erstellt werden, die Daten aus mehreren Systemen kombinieren. Ein gutes Beispiel dafür ist der erste Datensatz der Treue-, CRM- und Offline-Kauf-Datensätze. Suchen Sie dieses Profil, um zu bestätigen, dass die Daten aufgenommen wurden. In der Benutzeroberfläche von [Adobe Experience Platform](https://experience.adobe.com/platform/):

1. Navigieren Sie **[!UICONTROL Profile]** > **[!UICONTROL Durchsuchen]**
1. Wählen Sie `Luma Loyalty Id` als **[!UICONTROL Identity-Namespace]**
1. Suchen Sie nach `5625458` als **[!UICONTROL Identitätswert]**
1. `Daniel Wright` öffnen

>[!TIP]
>
>Wenn das Profil nicht angezeigt wird, überprüfen Sie die Seite [!UICONTROL Datensätze], um sicherzustellen, dass alle Datensätze erfolgreich erstellt und aufgenommen wurden. Wenn dies gut aussieht, warten Sie fünfzehn Minuten und überprüfen Sie, ob das Profil im Viewer verfügbar ist.  Wenn bei der Datenaufnahme Probleme aufgetreten sind, überprüfen Sie die Fehlermeldungen und versuchen Sie, das Problem zu finden. Sie können auch versuchen, die Fehlerdiagnose auf der Seite [!UICONTROL Datensätze] zu aktivieren und die JSON-Datendatei per Drag-and-Drop zu ziehen, um die Daten erneut aufzunehmen.


![Öffnen eines Profils](../assets/data-generator/images/validation-profile-open.png)

Wenn Sie die Daten auf den Registerkarten **[!UICONTROL Attribute]** und **[!UICONTROL Ereignisse]** durchsuchen, sollten Sie sehen, dass das Profil Daten aus den verschiedenen Datendateien enthält:
![Ereignisdaten aus der Offline-Kaufereignisdatei](../assets/data-generator/images/validation-profile-events.png)

## Nächste Schritte

Wenn Sie mehr über Adobe Journey Optimizer erfahren möchten, enthält diese Sandbox alles, was Sie zur Bewältigung der [Journey Optimizer-Herausforderungen benötigen](https://experienceleague.adobe.com/docs/journey-optimizer-learn/challenges/introduction-and-prerequisites.html?lang=de)

Wenn Sie mehr über Zusammenführungsrichtlinien, Data Governance, den Abfrage-Service und den Segment Builder erfahren möchten, springen Sie im Tutorial Erste Schritte für Datenarchitekten und Dateningenieure zu [Lektion 11](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/create-merge-policies.html?lang=en). Die früheren Lektionen dieses anderen Tutorials haben Sie dazu beigetragen, alles, was gerade mit diesen Postman-Sammlungen gefüllt wurde, manuell zu erstellen - genießen Sie den Vorsprung!

Wenn Sie eine Beispiel-Web-SDK-Implementierung für den Link zu dieser Sandbox erstellen möchten, gehen Sie folgendermaßen vor
[Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK](https://experienceleague.adobe.com/de/docs/platform-learn/implement-web-sdk/overview). Nach dem Einrichten der Lektionen „Erstkonfiguration“, „Tags-Konfiguration“ und &quot;Experience Platform einrichten“ des Web SDK-Tutorials melden Sie sich bei der Luma-Website mit den ersten zehn E-Mail-Adressen in der `luma-crm.json`-Datei mit dem `test` Passwort an, um zu sehen, wie die Profilfragmente mit den in diesem Tutorial hochgeladenen Daten zusammengeführt werden.

Wenn Sie eine Beispielimplementierung von Mobile SDK erstellen möchten, um eine Verknüpfung zu dieser Sandbox herzustellen, gehen Sie folgendermaßen vor
[Tutorial zur Implementierung von Adobe Experience Cloud in Mobile Apps](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html?lang=de). Nach dem Einrichten der Lektionen „Erstkonfiguration“, „App-Implementierung“ und &quot;Experience Platform&quot; des Web SDK-Tutorials melden Sie sich bei der Luma-Website mit den ersten E-Mail-Adressen in der `luma-crm.json` an, um eine Profilfragmentzusammenführung mit den in diesem Tutorial hochgeladenen Daten zu sehen.

## Sandbox-Umgebung zurücksetzen {#reset-sandbox}

Beim Zurücksetzen einer Nicht-Produktions-Sandbox werden alle mit dieser Sandbox verbundenen Ressourcen (Schemata, Datensätze usw.) gelöscht, wobei der Name der Sandbox und die zugehörigen Berechtigungen beibehalten werden. Diese „saubere“ Sandbox ist für Benutzer, die Zugriff darauf haben, unter demselben Namen weiter verfügbar.

Gehen Sie wie folgt vor [hier](https://experienceleague.adobe.com/docs/experience-platform/sandbox/ui/user-guide.html?lang=en#reset-a-sandbox), um eine Sandbox-Umgebung zurückzusetzen.
