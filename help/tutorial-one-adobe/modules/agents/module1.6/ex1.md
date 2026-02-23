---
title: Erste Schritte mit AEM-Agenten
description: Erste Schritte mit AEM-Agenten
kt: 5342
doc-type: tutorial
exl-id: cb1bf6f0-f329-4e38-ba64-36ffdc3b8bd4
source-git-commit: c7108c2818ee7fad820af33b99f277181bcf6a02
workflow-type: tm+mt
source-wordcount: '1674'
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

### Inhaltsaktualisierung - Assets

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

### Inhaltsaktualisierung - Seiten

Gehen Sie zurück zu Ihrer Adobe Experience Manager-Autorenumgebung und dann zu **Sites**.

![AEM-Agenten](./images/aemagents43.png)

Gehen Sie zu **CitiSignal**. Klicken Sie **Erstellen** und wählen Sie **Seite** aus.

![AEM-Agenten](./images/aemagents44.png)

Wählen Sie **Seite** aus und klicken Sie auf **Weiter**.

![AEM-Agenten](./images/aemagents45.png)

Geben Sie die folgenden Werte ein:

- Titel: **Fibre Max**
- Name: **fiber-max**
- Seitentitel: **Fibre Max**

Klicken Sie auf **Erstellen**.

![AEM-Agenten](./images/aemagents46.png)

Wählen Sie **Öffnen** aus.

![AEM-Agenten](./images/aemagents47.png)

Sie sollten das dann sehen.

![AEM-Agenten](./images/aemagents48.png)

Klicken Sie in den leeren Bereich, um die Komponente **Abschnitt** auszuwählen. Klicken Sie dann auf das Pluszeichen **+** im rechten Menü und wählen Sie **Hero**.

![AEM-Agenten](./images/aemagents49.png)

Sie sollten das dann sehen. Klicken Sie auf **+**, um ein Bild hinzuzufügen.

![AEM-Agenten](./images/aemagents50.png)

Wählen Sie Ihr Assets-Repository aus. Öffnen Sie dann den Ordner **CitiSignal**.

![AEM-Agenten](./images/aemagents51.png)

Wählen Sie das Bild des Löwen, das Sie zuvor hochgeladen haben. Klicken Sie auf **Auswählen**.

![AEM-Agenten](./images/aemagents52.png)

Sie sollten das dann sehen. Klicken Sie auf **Text**-Bereich, um den Text zu ändern.

![AEM-Agenten](./images/aemagents53.png)

Fügen Sie diesen Text in den Bereich ein:

```
This winter, be as fast as a lion.
```

Wählen Sie **Überschrift 1** aus und klicken Sie dann auf **Fertig**.

![AEM-Agenten](./images/aemagents54.png)

Sie sollten das dann sehen. Navigieren Sie **Inhaltsstruktur** und wählen Sie den Bereich **Abschnitt** aus.

![AEM-Agenten](./images/aemagents55.png)

Klicken Sie auf das Symbol **+** und wählen Sie dann **Karten** aus.

![AEM-Agenten](./images/aemagents56.png)

Sie sollten das dann sehen. Stellen Sie sicher, dass in der **Inhaltsstruktur** die Option **Karten** ausgewählt ist.

Klicken Sie dann viermal auf die Schaltfläche **+**.

![AEM-Agenten](./images/aemagents57.png)

Sie sollten dies nun sehen, wo es vier **Card**-Objekte im **Cards**-Objekt gibt.

![AEM-Agenten](./images/aemagents58.png)

Wählen Sie die erste **Karte** aus. Klicken Sie auf **Text**-Bereich, um den Text zu ändern.

![AEM-Agenten](./images/aemagents59.png)

Fügen Sie den folgenden Text ein. Stellen Sie sicher, dass in der ersten Textzeile „Überschrift **&quot; verwendet**. Klicken Sie auf **Fertig**.

```
99.9% network reliability

Game, video chat and stream on multiple devices with ultra low lag.
```

![AEM-Agenten](./images/aemagents60.png)

Wählen Sie die zweite **Karte** aus. Klicken Sie auf **Text**-Bereich, um den Text zu ändern.

![AEM-Agenten](./images/aemagents61.png)

Fügen Sie den folgenden Text ein. Stellen Sie sicher, dass in der ersten Textzeile „Überschrift **&quot; verwendet**. Klicken Sie auf **Fertig**.

```
3-year

price lock guarantee

For new and existing Fiber Max customers on all internet plans.

No hidden fees.
```

![AEM-Agenten](./images/aemagents62.png)

Wählen Sie die dritte **Karte** aus. Klicken Sie auf **Text**-Bereich, um den Text zu ändern.

![AEM-Agenten](./images/aemagents63.png)

Fügen Sie den folgenden Text ein. Stellen Sie sicher, dass in der ersten Textzeile „Überschrift **&quot; verwendet**. Klicken Sie auf **Fertig**.

```
More ways to save

Save over 45% on the best entertainment with CitiSignal
```

![AEM-Agenten](./images/aemagents64.png)

Wählen Sie die vierte **Karte** aus. Klicken Sie auf **Text**-Bereich, um den Text zu ändern.

![AEM-Agenten](./images/aemagents65.png)

Fügen Sie den folgenden Text ein. Stellen Sie sicher, dass in der ersten Textzeile „Überschrift **&quot; verwendet**. Klicken Sie auf **Fertig**.

```
Get Fiber Max now!

Fill out the form here to get started.
```

![AEM-Agenten](./images/aemagents66.png)

Du solltest das jetzt haben. Klicken Sie auf **Veröffentlichen**.

![AEM-Agenten](./images/aemagents67.png)

Klicken **erneut auf** Veröffentlichen“.

![AEM-Agenten](./images/aemagents68.png)

Klicken Sie **Seite öffnen**.

![AEM-Agenten](./images/aemagents69.png)

Kopieren Sie die URL der Seite so, wie Sie sie als Nächstes benötigen.

Die URL sollte etwa wie folgt lauten: `https://author-pXXXXXX-eXXXXXXX.adobeaemcloud.com/content/CitiSignal/fiber-max.html`.

![AEM-Agenten](./images/aemagents70.png)

Navigieren Sie zu [https://experience.adobe.com/#/experiencemanager/](https://experience.adobe.com/#/experiencemanager/). Klicken, um **KI-Assistent** zu öffnen.

![AEM-Agenten](./images/aemagents71.png)

Fügen Sie die folgende Eingabeaufforderung ein und klicken Sie auf **Senden**. Ersetzen Sie XXX in dieser Eingabeaufforderung durch die URL, die Sie im vorherigen Schritt kopiert haben.

```
On the page XXX, please make the following changes:

- change the word 'winter' to 'spring'
- change the word 'lion' to 'leopard'
- change the image in the hero block to use the image 'citisignal_leopard.png'
- change the text '99.9% network reliability' to '99.999% network reliability'
```

![AEM-Agenten](./images/aemagents72.png)

Nach 1-2 Minuten sollten Sie dies sehen. Geben Sie den `generate` ein und klicken Sie auf **Senden**.

![AEM-Agenten](./images/aemagents74.png)

Einige Minuten später sollten Sie eine Bestätigung wie die folgende sehen, dass die Änderungen durchgeführt wurden. Klicken Sie **Vorschau der aktualisierten Seite anzeigen**.

![AEM-Agenten](./images/aemagents75.png)

Sie erhalten jetzt eine visuelle Bestätigung der vorgenommenen Änderungen. Diese Vorschauseite dient nur zu Informationszwecken. Sie können von dieser Seite aus keine Aktion ausführen.

![AEM-Agenten](./images/aemagents76.png)

Um eine Aktion durchzuführen, klicken Sie auf **In AEM bearbeiten**.

![AEM-Agenten](./images/aemagents75a.png)

Im universellen Editor sehen Sie nun alle Änderungen im Detail, mit der Möglichkeit, alles zu ändern. Nachdem Sie die Seite überprüft haben, klicken Sie auf **Veröffentlichen**.

![AEM-Agenten](./images/aemagents77.png)

Klicken **erneut auf** Veröffentlichen“. Die von Ihnen vorgenommene Änderung wird noch nicht in Ihrer Produktionsumgebung veröffentlicht. Stattdessen wurde es unter &quot;**&quot;** AEM veröffentlicht.

Launches ermöglichen die effiziente Entwicklung von Inhalten für eine zukünftige Version. Ein Launch wird erstellt, damit Sie Änderungen in Vorbereitung auf eine zukünftige Veröffentlichung vornehmen und gleichzeitig Ihre aktuellen Seiten pflegen können. Das bedeutet, dass Sie effektiv zwei Versionen gleichzeitig bearbeiten: Seiten, die derzeit veröffentlicht sind, und eine Version dieser Seiten, die zu einem späteren Zeitpunkt veröffentlicht werden sollen. Sobald diese Zeit gekommen ist, können Sie die Originalseiten ersetzen und die neue Version veröffentlichen.

![AEM-Agenten](./images/aemagents78.png)

Um **ausstehenden** für eine zukünftige Version zu bewerben, gehen Sie zurück zu AEM. Klicken Sie oben auf **Seite auf** Adobe Experience Manager, klicken Sie auf das **Hammer**-Symbol und wählen Sie dann **Launches** aus.

![AEM-Agenten](./images/aemagents79.png)

Es sollte jetzt ein ausstehender &quot;**&quot;**. Aktivieren Sie das Kontrollkästchen vor dem ausstehenden **Launch**.

![AEM-Agenten](./images/aemagents80.png)

Klicken Sie auf **Bewerben**.

![AEM-Agenten](./images/aemagents81.png)

Wählen Sie **Vollständigen Launch hochstufen** und klicken Sie auf **Weiter**.

![AEM-Agenten](./images/aemagents82.png)

Klicken Sie auf **Bewerben**.

![AEM-Agenten](./images/aemagents83.png)

Sie sollten das jetzt sehen. Ihre Änderungen sind jetzt in Produktion.

![AEM-Agenten](./images/aemagents84.png)

Aktualisieren Sie Ihre Seite. Jetzt sollten alle Ihre Änderungen auf der veröffentlichten Seite angezeigt werden.

![AEM-Agenten](./images/aemagents85.png)

Anstatt den manuellen Weiterleitungsprozess zu durchlaufen, können Sie auch die `accept` im KI-Assistenten eingeben.

![AEM-Agenten](./images/aemagents86.png)

Sie sollten dann eine Bestätigung erhalten, dass Änderungen veröffentlicht werden.

![AEM-Agenten](./images/aemagents87.png)

### Inhaltsaktualisierung - Formularerstellung

Im Modul [Adobe Experience Manager Forms mit Edge Delivery Services ](./../../asset-mgmt/module1.3/aemforms.md){target="_blank"} Sie die Schritte, die bei der manuellen Erstellung eines Formulars erforderlich sind.

Die Fähigkeit zur Formularerstellung ermöglicht es Benutzenden jetzt, adaptive Formulare über Eingabeaufforderungen in natürlicher Sprache zu erstellen, ohne von Entwicklungs- oder IT-Teams abhängig zu sein. Diese Funktion beschleunigt die Formularentwicklung, während die Markenkonsistenz gewahrt bleibt und es Geschäftsbenutzern ermöglicht wird, Formulare ohne fundierte technische Produktkenntnisse zu erstellen.

Navigieren Sie zu [https://experience.adobe.com/#/ai-assistant/chat](https://experience.adobe.com/#/ai-assistant/chat).

![AEM-Agenten](./images/aemagentsforms1.png)

Geben Sie die folgende Eingabeaufforderung ein und klicken Sie auf **Senden**.

```
Create a new adaptive form using Edge Delivery Services with the following details:
- Form name: "citisignal-fiber-max-interest-2"
- Form fields: 4 text input fields are needed, for "first-name", "last-name", "email" and "city"
- When the form is submitted, send the submission to a spreadsheet, with this URL: https://docs.google.com/spreadsheets/d/1WwKrcM8mZ2d_W3sMheUAw3nFhP_OFk05TsqxhHkudfQ/edit?usp=sharing.
```



## Nächste Schritte

Zurück zu [AEM und Agenten](./aemagents.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
