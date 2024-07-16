---
title: Importieren von Beispieldaten in Adobe Experience Platform
description: Erfahren Sie, wie Sie eine Experience Platform-Sandbox-Umgebung mit einigen Beispieldaten einrichten.
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

# Importieren von Beispieldaten in Adobe Experience Platform

Erfahren Sie, wie Sie eine Experience Platform-Sandbox-Umgebung mit Beispieldaten einrichten. Mithilfe einer Postman-Sammlung können Sie Feldergruppen, Schemata und Datensätze erstellen und dann Beispieldaten in Experience Platform importieren.

## Anwendungsfall für Beispieldaten

Experience Platform-Business-Anwender müssen häufig eine Reihe von Schritten durchlaufen, darunter das Identifizieren von Feldergruppen, das Erstellen von Schemas, das Vorbereiten von Daten, das Erstellen von Datensätzen und das anschließende Erfassen von Daten, bevor sie die von Experience Platform angebotenen Marketingfunktionen untersuchen können. In diesem Tutorial werden einige der Schritte automatisiert, sodass Sie Daten so schnell wie möglich in eine Platform-Sandbox übertragen können.

Dieses Tutorial konzentriert sich auf eine fiktive Einzelhandelsmarke namens Luma. Sie investieren in Adobe Experience Platform, um Loyalitäts-, CRM-, Produktkatalog- und Offline-Kaufdaten in Echtzeit-Kundenprofile zu kombinieren und diese Profile zu aktivieren, um ihr Marketing auf die nächste Stufe zu bringen. Wir haben Beispieldaten für Luma generiert. Im Rest dieses Tutorials importieren Sie diese Daten in eine Ihrer Experience Platform-Sandbox-Umgebungen.

>[!NOTE]
>
>Das Endergebnis dieses Tutorials ist eine Sandbox mit ähnlichen Daten wie das Tutorial [Erste Schritte mit Adobe Experience Platform für Datenarchitekten und Dateningenieure](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=de). Sie wurde im April 2023 aktualisiert, um die [Journey Optimizer-Herausforderungen](https://experienceleague.adobe.com/docs/journey-optimizer-learn/challenges/introduction-and-prerequisites.html?lang=de) zu unterstützen. Es wurde im Juni 2023 aktualisiert, um die Authentifizierungsmethode auf OAuth umzustellen.


## Voraussetzungen

* Sie haben Zugriff auf Experience Platform-APIs und können sich authentifizieren. Wenn nicht, lesen Sie dieses [Tutorial](https://experienceleague.adobe.com/docs/platform-learn/tutorials/platform-api-authentication.html?lang=de).
* Sie haben Zugriff auf eine Experience Platform-Entwicklungs-Sandbox.
* Sie kennen Ihre Experience Platform-Mandanten-ID. Sie können sie abrufen, indem Sie eine authentifizierte [API-Anfrage](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/getting-started.html?lang=en#know-your-tenant_id) stellen
oder extrahieren Sie sie aus der URL, wenn Sie sich bei Ihrem Platform-Konto anmelden. In der folgenden URL ist der Mandant beispielsweise &quot;`techmarketingdemos`&quot; `https://experience.adobe.com/#/@techmarketingdemos/sname:prod/platform/home`.

## Verwenden [!DNL Postman] {#postman}

### Umgebungsvariablen einrichten

Bevor Sie die Schritte ausführen, stellen Sie sicher, dass Sie die Anwendung [Postman](https://www.postman.com/downloads/) heruntergeladen haben. Los geht‘s!

1. Laden Sie die Datei [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) herunter, die alle für dieses Tutorial erforderlichen Dateien enthält.

   >[!NOTE]
   >
   >Die in der Datei [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) enthaltenen Benutzerdaten sind fiktiv und dürfen nur zu Demonstrationszwecken verwendet werden.

1. Verschieben Sie die Datei `platform-utils-main.zip` aus dem Downloads-Ordner an den gewünschten Speicherort auf Ihrem Computer und entpacken Sie sie.
1. Öffnen Sie im Ordner `luma-data` alle `json` -Dateien in einem Texteditor und ersetzen Sie alle Instanzen von `_yourTenantId` durch Ihre eigene Mandanten-ID, der ein Unterstrich vorangestellt ist.
1. Öffnen Sie `luma-offline-purchases.json`, `luma-inventory-events.json` und `luma-web-events.json` in einem Texteditor und aktualisieren Sie alle Zeitstempel, sodass die Ereignisse im letzten Monat auftreten (suchen Sie beispielsweise nach `"timestamp":"2022-11` und ersetzen Sie Jahr und Monat).
1. Notieren Sie den Speicherort des entpackten Ordners, wie Sie ihn später beim Einrichten der Umgebungsvariablen `FILE_PATH` [!DNL Postman] benötigen:

   >[!NOTE]
   > Um den Dateipfad auf Ihrer Mac abzurufen, navigieren Sie zum Ordner &quot;`platform-utils-main`&quot;, klicken Sie mit der rechten Maustaste auf den Ordner und wählen Sie die Option &quot;**Info abrufen**&quot;.
   >
   > ![MAC-Dateipfad](../assets/data-generator/images/mac-file-path.png)

   >[!NOTE]
   > Um den Dateipfad in Ihren Fenstern abzurufen, klicken Sie auf den Speicherort des gewünschten Ordners und klicken Sie dann mit der rechten Maustaste rechts neben dem Pfad in der Adressleiste. Kopieren Sie die Adresse, um den Dateipfad abzurufen.
   > 
   > ![Windows-Dateipfad](../assets/data-generator/images/windows-file-path.png)

1. Öffnen Sie [!DNL Postman] und erstellen Sie einen Arbeitsbereich aus dem Dropdown-Menü **Arbeitsbereiche**:\
   ![Arbeitsbereich erstellen](../assets/data-generator/images/create-workspace.png)
1. Geben Sie einen **Namen** und optional eine **Zusammenfassung** für Ihren Arbeitsbereich ein und klicken Sie auf **Workspace erstellen**. [!DNL Postman] wechselt beim Erstellen zu Ihrem neuen Arbeitsbereich.
   ![Arbeitsbereich speichern](../assets/data-generator/images/save-workspace.png)
1. Passen Sie jetzt einige Einstellungen an, um die [!DNL Postman]-Sammlungen in diesem Arbeitsbereich auszuführen. Klicken Sie in der Kopfzeile von [!DNL Postman] auf das Zahnradsymbol und wählen Sie **Einstellungen** aus, um das Einstellungs-Modal zu öffnen. Sie können auch den Tastaturbefehl (CMD/STRG + , ) verwenden, um das Modal zu öffnen.
1. Aktualisieren Sie auf der Registerkarte &quot;`General`&quot; das Anforderungszeitlimit in ms auf `5000 ms` und aktivieren Sie `allow reading file outside this directory`
   ![Einstellungen](../assets/data-generator/images/settings.png)

   >[!NOTE]
   > Wenn Dateien aus dem Arbeitsverzeichnis geladen werden, wird sie geräteübergreifend reibungslos ausgeführt, wenn dieselben Dateien auf den anderen Geräten gespeichert werden. Wenn Sie jedoch Dateien von außerhalb des Arbeitsverzeichnisses ausführen möchten, muss eine Einstellung aktiviert sein, um denselben Intent anzugeben. Wenn Ihr `FILE_PATH` nicht mit dem Arbeitsverzeichnispfad von [!DNL Postman] übereinstimmt, sollte diese Option aktiviert sein.

1. Schließen Sie das Bedienfeld **Einstellungen** .
1. Wählen Sie **Umgebungen** und dann **Import** aus:
   ![Umgebungsimport](../assets/data-generator/images/env-import.png)
1. Importieren Sie die heruntergeladene JSON-Umgebungsdatei, `DataInExperiencePlatform.postman_environment`
1. Wählen Sie in Postman Ihre Umgebung in der oberen rechten Dropdown-Liste aus und klicken Sie auf das Augensymbol, um die Umgebungsvariablen anzuzeigen:
   ![Umgebungsauswahl](../assets/data-generator/images/env-selection.png)

1. Stellen Sie sicher, dass die folgenden Umgebungsvariablen ausgefüllt sind. Informationen zum Abrufen des Werts der Umgebungsvariablen finden Sie im Tutorial [Für Experience Platform-APIs authentifizieren](/help/platform/authentication/platform-api-authentication.md) mit schrittweisen Anweisungen.

   * `CLIENT_SECRET`
   * `API_KEY`—`Client ID` in Adobe Developer Console
   * `SCOPES`
   * `TECHNICAL_ACCOUNT_ID`
   * `IMS`
   * `IMS_ORG`—`Organization ID` in Adobe Developer Console
   * `SANDBOX_NAME`
   * `TENANT_ID`—Stellen Sie sicher, dass ein Unterstrich angezeigt wird, z. B. `_techmarketingdemos`
   * `CONTAINER_ID`
   * `platform_end_point`
   * `FILE_PATH` - Verwenden Sie den lokalen Ordnerpfad, in dem Sie die `platform-utils-main.zip`-Datei entpackt haben. Stellen Sie sicher, dass er den Ordnernamen enthält, z. B. `/Users/dwright/Desktop/platform-utils-main`

1. **Speichern** der aktualisierten Umgebung

### Importieren von Postman-Sammlungen

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

   ![Import von Sammlungen](../assets/data-generator/images/collection-files.png)

### Authentifizieren

Als Nächstes müssen Sie sich authentifizieren und ein Benutzer-Token generieren. Bitte beachten Sie, dass die in diesem Tutorial verwendeten Methoden zur Token-Generierung nur für produktionsfremde Zwecke geeignet sind. &quot;Lokales Signieren&quot;lädt eine JavaScript-Bibliothek von einem Drittanbieter-Host, und das Remote-Signieren sendet den privaten Schlüssel an einen Adobe-eigenen und verwalteten Webdienst. Während Adobe diesen privaten Schlüssel nicht speichert, sollten Produktionsschlüssel niemals für andere freigegeben werden.

1. Öffnen Sie die Sammlung &quot;`0-Authentication`&quot;, wählen Sie die Anforderung &quot;`OAuth: Request Access Token`&quot;aus und klicken Sie auf &quot;`SEND`&quot;, um sich zu authentifizieren und das Zugriffstoken zu erhalten.

   ![Import von Sammlungen](../assets/data-generator/images/authentication.png)

1. Überprüfen Sie die Umgebungsvariablen und beachten Sie, dass die `ACCESS_TOKEN` jetzt gefüllt ist.

### Datenimport

Jetzt können Sie die Daten vorbereiten und in Ihre Platform-Sandbox importieren. Die Postman Kollektionen, die Sie importiert haben, werden die ganze Mühe tun!

1. Öffnen Sie die Sammlung &quot;`1-Luma-Loyalty-Data`&quot; und klicken Sie auf der Registerkarte &quot;Übersicht&quot;auf &quot;**Ausführen**&quot;, um einen &quot;Collection Runner&quot;zu starten.

   ![Import von Sammlungen](../assets/data-generator/images/loyalty.png)

1. Wählen Sie im Fenster des Sammlungs-Runners die Umgebung aus der Dropdown-Liste aus, aktualisieren Sie die Option **Verzögerung** auf `4000ms`, aktivieren Sie die Option **Antworten speichern** und stellen Sie sicher, dass die Ausführungsreihenfolge korrekt ist. Klicken Sie auf die Schaltfläche **Luma Loyalty Data ausführen** .

   ![Import von Sammlungen](../assets/data-generator/images/loyalty-run.png)

   >[!NOTE]
   >
   >**1-Luma-Loyalty-Data** erstellt ein Schema für Kundenloyalitätsdaten. Das Schema basiert auf der Klasse &quot;XDM Individual Profile&quot;, der Standardfeldgruppe sowie einer benutzerdefinierten Feldergruppe und einem benutzerdefinierten Datentyp. Die Sammlung erstellt einen Datensatz mithilfe des Schemas und lädt Beispieldaten zur Kundenloyalität in Adobe Experience Platform hoch.

   >[!NOTE]
   >
   >Wenn Sammlungsanfragen während des Postman-Sammlungs-Runners fehlschlagen, stoppen Sie die Ausführung und führen Sie die Sammlungsanfragen einzeln aus.

1. Wenn alles gut geht, sollten alle Anforderungen in der `Luma-Loyalty-Data` -Sammlung übergeben werden.

   ![Treueergebnis](../assets/data-generator/images/loyalty-result.png)

1. Melden wir uns nun bei [Adobe Experience Platform-Oberfläche](https://platform.adobe.com/) an und navigieren zu Datensätzen.
1. Öffnen Sie den Datensatz &quot;`Luma Loyalty Dataset`&quot;. Im Fenster der Datensatzaktivität können Sie eine erfolgreiche Batch-Ausführung anzeigen, die 1.000 Datensätze erfasst hat. Sie können auch auf die Option Datensatz-Vorschau klicken, um die erfassten Datensätze zu überprüfen. Möglicherweise müssen Sie einige Minuten warten, um zu bestätigen, dass 1000 [!UICONTROL neue Profilfragmente] erstellt wurden.
   ![Treuedatensatz](../assets/data-generator/images/loyalty-dataset.png)
1. Wiederholen Sie die Schritte 1 bis 3, um die anderen Sammlungen auszuführen:
   * `2-Luma-CRM-Data.postman_collection.json` erstellt ein Schema und einen befüllten Datensatz für CRM-Daten von Kunden. Das Schema basiert auf der Klasse &quot;XDM Individual Profile&quot;, die demografische Details, persönliche Kontaktdetails, Präferenzdetails und eine benutzerdefinierte Identitätsfeldgruppe umfasst.
   * `3-Luma-Product-Catalog.postman_collection.json` erstellt ein Schema und einen ausgefüllten Datensatz für Produktkataloginformationen. Das Schema basiert auf einer benutzerdefinierten Produktkatalogklasse und verwendet eine benutzerdefinierte Feldgruppe für den Produktkatalog.
   * `4-Luma-Offline-Purchase-Events.postman_collection.json` erstellt ein Schema und füllt den Datensatz für Offline-Kaufereignisdaten von Kunden. Das Schema basiert auf der XDM ExperienceEvent-Klasse und umfasst eine benutzerdefinierte Identität sowie Commerce Details-Feldergruppen.
   * `5-Luma-Product-Inventory-Events.postman_collection.json` erstellt ein Schema und einen befüllten Datensatz für Ereignisse im Zusammenhang mit Produkten, die auf Lager sind. Das Schema basiert auf einer benutzerdefinierten Business-Event-Klasse und einer benutzerdefinierten Feldergruppe.
   * `6-Luma-Test-Profiles.postman_collection.json` erstellt ein Schema und füllt einen Datensatz mit Testprofilen, die in Adobe Journey Optimizer verwendet werden sollen
   * `7-Luma-Web-Events.postman_collection.json` erstellt ein Schema und füllt einen Datensatz mit einfachen historischen Webdaten.


## Validierung

Die Beispieldaten wurden so konzipiert, dass bei der Ausführung der Sammlungen Echtzeit-Kundenprofile erstellt werden, die Daten aus mehreren Systemen kombinieren. Ein gutes Beispiel dafür ist der erste Datensatz der Datensätze zu Treue, CRM und Offline-Einkäufen. Überprüfen Sie dieses Profil, um zu bestätigen, dass die Daten erfasst wurden. In der [Adobe Experience Platform-Oberfläche](https://experience.adobe.com/platform/):

1. Navigieren Sie zu **[!UICONTROL Profile]** > **[!UICONTROL Durchsuchen]** .
1. Wählen Sie `Luma Loyalty Id` als **[!UICONTROL Identitäts-Namespace]** aus.
1. Suchen Sie nach `5625458` als **[!UICONTROL Identitätswert]** .
1. Öffnen Sie das Profil `Daniel Wright` .

>[!TIP]
>
>Wenn das Profil nicht angezeigt wird, überprüfen Sie die Seite [!UICONTROL Datensätze] , um sicherzustellen, dass alle Datensätze erfolgreich erstellt und erfasst wurden. Wenn das gut aussieht, warten Sie fünfzehn Minuten und überprüfen Sie, ob das Profil im Viewer verfügbar ist.  Wenn bei der Datenerfassung Probleme aufgetreten sind, überprüfen Sie die Fehlermeldungen, um das Problem zu finden. Sie können auch versuchen, die Fehlerdiagnose auf der Seite [!UICONTROL Datensätze] zu aktivieren, und die JSON-Datendatei per Drag-and-Drop verschieben, um die Daten erneut zu erfassen.


![Öffnen eines Profils](../assets/data-generator/images/validation-profile-open.png)

Indem Sie die Daten auf den Registerkarten **[!UICONTROL Attribute]** und **[!UICONTROL Ereignisse]** durchsuchen, sollten Sie sehen, dass das Profil Daten aus den verschiedenen Datendateien enthält:
![Ereignisdaten aus der Datei &quot;Offline-Kaufereignisse&quot;](../assets/data-generator/images/validation-profile-events.png)

## Nächste Schritte

Wenn Sie mehr über Adobe Journey Optimizer erfahren möchten, enthält diese Sandbox alles, was Sie für die [Journey Optimizer-Herausforderungen](https://experienceleague.adobe.com/docs/journey-optimizer-learn/challenges/introduction-and-prerequisites.html?lang=de) benötigen

Wenn Sie mehr über Zusammenführungsrichtlinien, Data Governance, Query Service und den Segment Builder erfahren möchten, lesen Sie im Tutorial Erste Schritte für Datenarchitekten und Dateningenieure](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/create-merge-policies.html?lang=en) die [Lektion 11 . Die früheren Lektionen dieses anderen Tutorials zeigen Ihnen, wie Sie manuell alles erstellen können, was gerade von diesen Postman-Sammlungen befüllt wurde - genießen Sie den Vorsprung!

Wenn Sie eine Web SDK-Beispielimplementierung erstellen möchten, um eine Verknüpfung zu dieser Sandbox herzustellen, gehen Sie zu
[Tutorial zur Implementierung von Adobe Experience Cloud mit Web SDK](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=de). Nachdem Sie die Lektionen &quot;Erste Konfiguration&quot;, &quot;Tags-Konfiguration&quot;und &quot;Experience Platform einrichten&quot;des Web SDK-Tutorials eingerichtet haben, melden Sie sich mit den ersten zehn E-Mail-Adressen in der Datei `luma-crm.json` mit dem Kennwort `test` an der Luma-Website an, um zu sehen, wie die Profilfragmente mit den in diesem Tutorial hochgeladenen Daten zusammengeführt werden.

Wenn Sie eine Mobile SDK-Beispielimplementierung erstellen möchten, um eine Verknüpfung zu dieser Sandbox herzustellen, gehen Sie zu
[Tutorial zur Implementierung von Adobe Experience Cloud in Apps für mobile Apps](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html?lang=de). Nachdem Sie die Lektionen &quot;Erstkonfiguration&quot;, &quot;App-Implementierung&quot;und &quot;Experience Platform&quot;des Web SDK-Tutorials eingerichtet haben, melden Sie sich mit den ersten E-Mail-Adressen in der Datei &quot;`luma-crm.json`&quot;an der Luma-Website an, um die Zusammenführung eines Profilfragments mit den in diesem Tutorial hochgeladenen Daten anzuzeigen.

## Sandbox-Umgebung zurücksetzen {#reset-sandbox}

Beim Zurücksetzen einer Nicht-Produktions-Sandbox werden alle mit dieser Sandbox verbundenen Ressourcen (Schemata, Datensätze usw.) gelöscht, wobei der Name der Sandbox und die zugehörigen Berechtigungen beibehalten werden. Diese „saubere“ Sandbox ist für Benutzer, die Zugriff darauf haben, unter demselben Namen weiter verfügbar.

Führen Sie die Schritte [hier](https://experienceleague.adobe.com/docs/experience-platform/sandbox/ui/user-guide.html?lang=en#reset-a-sandbox) aus, um eine Sandbox-Umgebung zurückzusetzen.
