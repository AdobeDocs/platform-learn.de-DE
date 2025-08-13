---
title: Erstellen einer Journey mit Daten einer verbundenen Zielgruppe
seo-title: Build a journey with federated audience data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Erstellen einer Journey mit Daten einer verbundenen Zielgruppe
description: In dieser visuellen Übung wird eine Federated Audience auf einer Journey Optimizer-Journey verwendet.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-build-a-journey-with-federated-audience-data.jpg
exl-id: a153667a-9b3a-4db7-9f58-b83e695009e0
source-git-commit: 15619a8419f608da6a77745fabf72c356a2ac4b4
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 1%

---

# Erstellen einer Journey mit Daten einer verbundenen Zielgruppe

Federated Audiences können in Journey innerhalb von Adobe Journey Optimizer (AJO) verwendet werden. Dazu gehört die Verwendung von abgefragten Attributen aus der Federated Audience-Komposition zur Personalisierung von Nachrichten.

Um mit der SecurFinancial-Story fortzufahren, insbesondere mit dem Anwendungsfall Kunden-Retargeting und Personalisierung, orchestrieren wir eine Journey für vorqualifizierte Kunden. Ziel ist es, eine personalisierte E-Mail zu senden, die auf Attributen basiert, die aus der Data Warehouse von SecurFinancial zusammengeführt werden.

## Schritte

### Erstellen einer Journey mit der Option „Zielgruppe lesen“

1. Navigieren Sie zum Portal **Journey** und klicken Sie auf die Schaltfläche **Journey erstellen**.

   ![create-a-Journey](assets/create-journey.png)

2. Aktualisieren Sie die Journey-Eigenschaften mit einem neuen Namen. In unserem Beispiel: **`SecurFinancial - Home Loan Offer`**.

3. Klicken Sie auf **Orchestrierung** und ziehen Sie die Kachel **Zielgruppe lesen** auf die Arbeitsfläche.

4. Klicken Sie auf **Stiftsymbol** dem Feld Zielgruppe auf der rechten Seite des Bildschirms.

5. Suchen Sie in der Suchleiste nach der Zielgruppe. In unserem Beispiel: **`SecureFinancial Customers - No Loans, Good Credit`**. Klicken Sie auf **Speichern**.

   ![create-a-Journey](assets/select-audience.png)

6. Belassen Sie alle Einstellungen im Menü auf der rechten Seite und klicken Sie auf **Speichern**.

   ![save-audience-settings](assets/save-audience-settings.png)

### E-Mail personalisieren

1. Klicken Sie auf **Aktionen** und ziehen Sie die Kachel **E-Mail** auf die Arbeitsfläche.

2. Klicken Sie im Menü rechts auf **E-Mail-Konfiguration** und wählen Sie **E-Mail-Marketing**. Klicken Sie dann auf **Inhalt bearbeiten**.

3. Fügen Sie eine Betreffzeile hinzu. In unserem Beispiel: **`Learn more about SecurFinancial Home Loan`**. Klicken Sie dann auf **E-Mail-Textkörper bearbeiten**.

4. Klicken Sie auf **Inhaltsvorlage** oben rechts. Suchen und wählen Sie die entsprechende Vorlage aus. In unserem Beispiel wird die `SecureFinancial Template` verwendet. Klicken Sie dann auf **Bestätigen**.

   ![Journey-email-config](assets/journey-email-config.png)

   ![Journey-email-confirm](assets/journey-email-confirm.png)

5. Überprüfen Sie die Vorlage und klicken Sie auf **Vorlage verwenden**.

6. Sie befinden sich nun in der E-Mail-Designer. Bewegen Sie den Mauszeiger über das `{profile.person.name.firstName}` Makro und klicken Sie auf **Personalisierungsavatar**.

7. Führen Sie im Personalisierungsfenster einen Drilldown zum Ordnerpfad mit der hochgeladenen Federated Audience durch. In unserem Beispiel: **`[sandbox] > audienceEnrichment > CustomerAudienceUpload`**

8. Klicken Sie in den Ordner **Zielgruppe lesen**. Die Anreicherungsattribute Ihrer Federated Audience finden Sie hier .

9. Wählen Sie das **Vorname** für den Ausdrucksgenerator aus. Die E-Mail drückt den Vornamenwert des Kunden dynamisch aus, um die E-Mail zu personalisieren.

10. Klicken Sie auf **Speichern**.

11. Nachdem die Personalisierung mit dem Vornamen hinzugefügt wurde, fügen Sie `Hi, ` vor der Personalisierungsvariablen hinzu. Klicken Sie dann auf **Speichern**.

    ![Journey-email-save](assets/journey-email-save.png)

12. Klicken Sie zweimal auf **Zurück**, um zur Journey-Arbeitsfläche zurückzukehren. Klicken Sie dann im Menü **Aktion: E** Mail“ auf der rechten Seite auf **Speichern**.

   ![save-final-Journey](assets/save-final-journey.png)

Wir haben eine Journey in AJO mit einer Federated Audience und Federated Enrichment-Attributen erstellt.

Jetzt schauen wir uns an, wie [ bestehende Zielgruppen ](federated-audience-composition.md) Experience Platform mit Federated Data Warehouse anreichern können.
