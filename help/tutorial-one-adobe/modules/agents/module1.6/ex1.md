---
title: Content Production Agent
description: Content Production Agent
kt: 5342
doc-type: tutorial
exl-id: cb1bf6f0-f329-4e38-ba64-36ffdc3b8bd4
source-git-commit: 7ea3bdc9557ea9e88ddd9693f9ffbfbc634857f8
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 1%

---

# 1.6.1 Erste Schritte mit AEM-Agenten

>[!IMPORTANT]
>
>Um diese Übung abzuschließen, benötigen Sie Zugriff auf eine funktionierende Umgebung für AEM Sites und Assets CS mit EDS, und die verschiedenen AEM-Agenten müssen für die von Ihnen verwendete IMS-Organisation aktiviert sein.
>
>Wenn Sie noch keine solche Umgebung haben, gehen Sie zu Übung [Adobe Experience Manager Cloud Service &amp; Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Folgen Sie den Anweisungen dort, und Sie haben Zugriff auf eine solche Umgebung.

>[!IMPORTANT]
>
>Wenn Sie zuvor ein AEM CS-Programm mit einer AEM Sites- und Assets CS-Umgebung konfiguriert haben, wurde Ihre AEM CS-Sandbox möglicherweise in den Ruhezustand versetzt. Da der Ruhezustand einer solchen Sandbox 10-15 Minuten dauert, ist es ratsam, den Ruhezustand jetzt zu beenden, damit Sie nicht zu einem späteren Zeitpunkt warten müssen.

## 1.6.1.1

Der Adobe Experience Manager (AEM) Discovery Agent ist ein KI-gestütztes Tool in AEM as a Cloud Service, mit dem Anwender Inhalte - einschließlich Assets, Inhaltsfragmenten und adaptivem Forms - mithilfe natürlicher Sprachaufforderungen finden, abrufen und verwenden können. Dadurch entfällt die Notwendigkeit manueller, klickintensiver oder komplexer Filter, da Intent und Suche im gesamten Repository verstanden werden.

Um den **Discovery Agent** verwenden zu können, erstellen Sie zunächst einige Tags in Adobe Experience Manager, die Sie dann mit Tags versehen. Sobald dies geschehen ist, können Sie den KI-Assistenten verwenden, um Assets auf einfache und geschäftsfreundliche Weise zu finden.

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Die gewünschte Organisation ist `--aepImsOrgName--`.

### Erstellen und Verwenden von Tags mit Assets

Klicken Sie hier, um Ihr Cloud Manager-Programm zu öffnen, das `--aepUserLdap-- - CitiSignal AEM+ACCS` heißen sollte.

![AEM-Agenten](./images/aemagents1.png)

Klicken Sie auf die URL Ihrer Umgebung, um sie zu öffnen.

![AEM-Agenten](./images/aemagents2.png)

Klicken Sie auf **Symbol** Hammer“.

![AEM-Agenten](./images/aemagents3.png)

Klicken **unter** Allgemein **auf**.

![AEM-Agenten](./images/aemagents4.png)

Sie sollten das dann sehen. Klicken Sie auf **Erstellen** und wählen Sie dann **Namespace erstellen** aus.

![AEM-Agenten](./images/aemagents5.png)

Geben Sie im Feld **Titel** Folgendes ein: `CitiSignal`. Klicken Sie auf **Erstellen**.

![AEM-Agenten](./images/aemagents6.png)

Drilldown in den Namespace **CitiSignal** durch Klicken darauf. Klicken Sie **Erstellen** und wählen Sie dann **Tag erstellen** aus.

![AEM-Agenten](./images/aemagents7.png)

Geben Sie im Feld **Titel** Folgendes ein: `Campaign`. Klicken Sie auf **Senden**.

![AEM-Agenten](./images/aemagents8.png)

Wählen Sie das Tag **Kampagne** aus, indem Sie darauf klicken. Klicken Sie **Erstellen** und wählen Sie dann **Tag erstellen** aus.

![AEM-Agenten](./images/aemagents9.png)

Geben Sie im Feld **Titel** Folgendes ein: `Winter 2026`. Klicken Sie auf **Senden**.

![AEM-Agenten](./images/aemagents10.png)

Wählen Sie das Tag **Kampagne** aus, indem Sie darauf klicken. Klicken Sie **Erstellen** und wählen Sie dann **Tag erstellen** aus.

![AEM-Agenten](./images/aemagents11.png)

Geben Sie im Feld **Titel** Folgendes ein: `Spring 2026`. Klicken Sie auf **Senden**.

![AEM-Agenten](./images/aemagents12.png)

Du solltest das jetzt haben.

![AEM-Agenten](./images/aemagents13.png)

Klicken Sie auf **Adobe Experience Manager** und dann auf **Assets**.

![AEM-Agenten](./images/aemagents14.png)

Klicken Sie auf **Dateien**.

![AEM-Agenten](./images/aemagents15.png)

Doppelklicken Sie auf den Ordner **CitiSignal**, um ihn zu öffnen.

![AEM-Agenten](./images/aemagents16.png)

Klicken Sie **Erstellen** und wählen Sie dann **Dateien** aus.

![AEM-Agenten](./images/aemagents17.png)

Laden Sie die Datei [Citisignal-images-campaign.zip](./assets/citisignal-images-campaign.zip) herunter und entpacken Sie sie auf Ihren Desktop.

![AEM-Agenten](./images/aemagents17a.png)

Auswählen. Die 3 Dateien, die Sie gerade heruntergeladen haben, und klicken Sie auf **Öffnen**.

![AEM-Agenten](./images/aemagents18.png)

Klicken Sie **Hochladen**.

![AEM-Agenten](./images/aemagents19.png)

Sie sollten das dann sehen.

![AEM-Agenten](./images/aemagents20.png)

Wählen Sie das erste Bild aus und klicken Sie dann auf **Eigenschaften**.

![AEM-Agenten](./images/aemagents21.png)

Klicken Sie auf **Ordner**-Symbol unter Tags.

![AEM-Agenten](./images/aemagents22.png)

Wählen Sie das Tag **Frühling 2026** aus und klicken Sie auf **Auswählen**. Wiederholen Sie diesen Vorgang für die folgenden Bilder:

- Citisignal_lion.png
- Citisignal_Leopard.png
- Citisignal_Gorilla.png
- Citisignal_rabbit.png

![AEM-Agenten](./images/aemagents23.png)

Nachdem Sie dieses Tag für alle Bilder ausgewählt haben, navigieren Sie zu **Experience Manager Assets**.

![AEM-Agenten](./images/aemagents24.png)

Wählen Sie das verwendete Repository aus.

![AEM-Agenten](./images/aemagents25.png)

Wechseln Sie zu **Assets** und öffnen Sie den Ordner **CitiSignal**.

![AEM-Agenten](./images/aemagents26.png)

Öffnen Sie das erste Bild.

![AEM-Agenten](./images/aemagents27.png)

Wählen Sie **Genehmigt** und klicken Sie dann auf **Speichern**.

![AEM-Agenten](./images/aemagents28.png)

Unter **Tags** wird das zuvor ausgewählte Tag angezeigt.

![AEM-Agenten](./images/aemagents29.png)

Wiederholen Sie diesen Vorgang, damit alle vier Bilder validiert werden.

![AEM-Agenten](./images/aemagents30.png)

Navigieren Sie dann zu **Mein Arbeitsbereich** und klicken Sie zum Öffnen auf **KI-Assistent**.

![AEM-Agenten](./images/aemagents31.png)

Geben Sie die folgende Eingabeaufforderung ein und klicken Sie auf **Senden**.

```javascript
find all assets tagged with 'Spring 2026'
```

![AEM-Agenten](./images/aemagents32.png)

Wenn Sie Zugriff auf mehrere AEM Assets CS-Umgebungen haben, sehen Sie Folgendes. Klicken Sie auf die vorgeschlagene Antwort für die gewünschte Umgebung und dann auf **Senden**.

![AEM-Agenten](./images/aemagents34.png)

Sie sollten dann eine ähnliche Antwort sehen. Klicken Sie auf das Symbol , um den KI-Assistenten auf den Vollbildmodus zu erweitern.

![AEM-Agenten](./images/aemagents35.png)

Überprüfen Sie die Antworten.

![AEM-Agenten](./images/aemagents36.png)

Sie können im Fenster des KI-Assistenten auf eines dieser Assets klicken, um es anzuzeigen.

![AEM-Agenten](./images/aemagents37.png)

Sie werden dann direkt zu AEM Assets CS weitergeleitet, zu diesem spezifischen Bild.

![AEM-Agenten](./images/aemagents38.png)

Sie können dann auch alle anderen verfügbaren Metadaten überprüfen.

![AEM-Agenten](./images/aemagents39.png)

## 1.6.1.2 Experience Production Agent

### Inhaltsaktualisierung

Die Fähigkeit zur Inhaltsaktualisierung aktualisiert vorhandene Inhalte - einschließlich Inhaltsfragmenten, Seiten, Formularen und Assets - mit Leichtigkeit. Der Agent kann Aktionen wie das Aktualisieren, Entfernen, Ersetzen oder Hinzufügen von Inhaltselementen durchführen, um Erlebnisse genau und aktuell zu halten. Eingaben können Beschreibungen in natürlicher Sprache sein und bei Verwendung mit Jira-PDFs und Screenshots auch Eingaben liefern.

Kehren Sie zum Bildschirm KI-Assistent zurück.

![AEM-Agenten](./images/aemagents40.png)

Geben Sie die folgende Eingabeaufforderung ein und klicken Sie auf **Senden**.

`Generate multiple social media formats (Instagram 1080x1920, Facebook 1200x630, Twitter 1200x675) for the third image`

![AEM-Agenten](./images/aemagents40a.png)

Nach einigen Minuten sollten Sie eine ähnliche Antwort sehen.

![AEM-Agenten](./images/aemagents41.png)

Überprüfen Sie die generierten Bilder.

![AEM-Agenten](./images/aemagents42.png)

### Formularerstellung

Die Fähigkeit zur Formularerstellung ermöglicht es Benutzenden, adaptive Formulare über Eingabeaufforderungen in natürlicher Sprache zu erstellen, ohne von Entwicklungs- oder IT-Teams abhängig zu sein. Diese Funktion beschleunigt die Formularentwicklung, während die Markenkonsistenz gewahrt bleibt und es Geschäftsbenutzern ermöglicht wird, Formulare ohne fundierte technische Produktkenntnisse zu erstellen.


## Nächste Schritte

Zurück zu [AEM und Agenten](./aemagents.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
