---
title: CSC Bootcamp - Produkt-Homepage-Banner erstellen
description: CSC Bootcamp - Produkt-Homepage-Banner erstellen
doc-type: multipage-overview
exl-id: c78b6ba2-1a1a-4e95-a8ab-1b572fa2d8b1
source-git-commit: 143da6340b932563a3309bb46c1c7091e0ab2ee2
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---

# Produkt-Homepage-Banner erstellen

## Produktion des Banners

Durch die Inhaltsautomatisierung profitiert Experience Manager Assets von der Leistungsfähigkeit von Adobe Creative Cloud. Marketing-Experten können die Asset-Produktion skaliert automatisieren, wodurch die Erstellung von Varianten erheblich beschleunigt wird. Verwenden wir diese Funktionen, um ein Banner zu generieren, das auf der Homepage verwendet werden kann!

- Gehen Sie zur AEM-Autoreninstanz auf [https://author-p105462-e991028.adobeaemcloud.com/](https://author-p105462-e991028.adobeaemcloud.com/) und melden Sie sich mit den von uns angegebenen Anmeldeinformationen an.

- Navigieren Sie auf der Startseite zu Tools \> Assets \> Verarbeitungsprofile.

![Tools > Assets > Verarbeitungsprofile](./images/prod-processing-profiles.png)

- In der Benutzeroberfläche werden alle vorhandenen Verarbeitungsprofile angezeigt. Diese können verwendet werden, um bestimmte Automatisierungen zu ermöglichen.

![Liste der Verarbeitungsprofile](./images/prod-profile-list.png)


- Die folgenden sind für Sie von Interesse:
   - Adobe Banner Dark: Erstellt ein Adobe Banner mit einer dunklen Überlagerung, basierend auf dem ausgewählten Asset
     ![Dark Banner](./images/prod-banner-dark.jpg)
   - Adobe Banner Light: Erstellt ein Adobe Banner mit einer hellen Überlagerung, basierend auf dem ausgewählten Asset
     ![Light-Banner](./images/prod-banner-light.jpg)
   - Adobe Banner Green : Erstellt ein Adobe Banner mit einer grünen Überlagerung, basierend auf dem ausgewählten Asset
     ![Grünes Banner](./images/prod-banner-green.jpg)

- Nachdem Sie den Bannertyp ausgewählt haben, den Sie erstellen möchten, wählen Sie dieses Verarbeitungsprofil aus und klicken Sie auf „Profil auf Ordner anwenden“.

![Profil auf Ordner anwenden](./images/prod-apply-profile.png)

- Navigieren Sie im nächsten Bildschirm zum Ordner Ihres Teams in AEM Assets. Wählen Sie dann oben links die Schaltfläche „Erstellen“, um einen neuen Ordner zu erstellen und ihm einen aussagekräftigen Namen zu geben, z. B. „Dunkles Banner erstellen“.

![Ordner erstellen](./images/prod-create-profile-folder.png)

![Ordnerdetails erstellen](./images/prod-profile-folder-details.png)

- Aktivieren Sie nach dem Erstellen des Ordners das Kontrollkästchen neben seinem Namen und klicken Sie dann oben rechts auf die Schaltfläche „Anwenden“.

![Auf erstellten Ordner anwenden](./images/prod-select-profile-folder.png)

Nachdem wir nun die erforderliche Konfiguration vorgenommen haben, generieren wir unser Banner.

- Klicken Sie oben links auf das AEM-Logo, um die Navigation zu öffnen, und gehen Sie dann zu Navigation \> Assets \> Dateien.

![AEM-Startbildschirm](./images/prod-select-assets.png)
![AEM Assets-Bildschirm](./images/prod-select-assets-2.png)

- Suchen Sie den Ordner „Generated AdobeBike Assets&quot; und öffnen Sie ihn durch Klicken auf die Karte. Hier werden die generierten Banner angezeigt.

![generierte AdobeBike-Assets](./images/prod-generated-banners.png)

- Öffnen Sie eine neue Registerkarte und navigieren Sie erneut zu AEM Assets. Navigieren Sie dann zu dem Ordner, auf den wir das Verarbeitungsprofil angewendet haben.

- Laden Sie im Ordner das Bild hoch, für das Sie ein Banner erstellen möchten, indem Sie es entweder per Drag-and-Drop in Ihren Browser ziehen oder indem Sie oben rechts in der Benutzeroberfläche auf Erstellen > Dateien klicken.

![Hochladen durch Drag-and-Drop](./images/prod-drag-drop-banner.png)

![Hochladen mit Datei erstellen](./images/prod-create-file.png)


- Warten Sie eine Minute, bis das Asset verarbeitet wurde, und laden Sie dann Ihren Bildschirm neu. Wenn Ihr Asset im Status „Neu“ angezeigt wird, wissen Sie, dass die Verarbeitung abgeschlossen ist.

![Asset im neuen Status](./images/prod-asset-processed.png)

- Navigieren Sie zurück zur vorherigen Registerkarte und laden Sie auch hier den Bildschirm neu. Beachten Sie ein neues Asset im Status „Neu“. Dies ist unser generiertes Banner, alles aus dem DAM! Siehst du es noch nicht? Warten Sie noch eine Minute und laden Sie dann Ihren Bildschirm neu.

![generiertes Banner](./images/prod-new-banner.png)

>[!NOTE]
>
> Nicht zufrieden mit dem Ergebnis? Sie können auch ein anderes Verarbeitungsprofil auf Ihren Ordner anwenden und Ihr Asset erneut hochladen, um ein anderes Banner zu generieren (oder natürlich ein anderes Asset hochladen). Während des erneuten Uploads fragt das System Sie, was Sie mit dem vorhandenen Asset tun möchten, wählen Sie „Ersetzen“.
> ![Vorhandenes ersetzen](./images/prod-replace-asset.png)

Wir haben jetzt unser generiertes Banner, das wir später während des Versands unserer Kampagne verwenden können. Veröffentlichen Sie unbedingt das Banner, indem Sie es auswählen und dann auf der Multifunktionsleiste auf die Schaltfläche „Quick Publish&quot; klicken.

![Asset veröffentlichen](./images/prod-publish-banner.png)

## Folgemaßnahmen in Workfront

Wenn Sie einen formellen und überprüfbaren Prüfungs- und Genehmigungsprozess für Ihre Assets benötigen, ist Workfront der richtige Ort dafür.

>[!NOTE]
>
> Obwohl wir es hier explizit erwähnen, ist es beabsichtigt, die Aufgaben in Workfront zu aktualisieren, nachdem Sie sie abgeschlossen haben. Sie sollten immer nach einem Fluss vom Typ Erstellen > Überprüfen > Genehmigen streben.

- Gehen wir zurück zu unserem Projekt und erweitern das Akkordeon „Go/No Go Banner Review“, um die genannte Aufgabe durch Klicken zu öffnen:

![Banner Go/No-Go](./images/banner-gonogo.png)

- Klicken Sie auf den Abschnitt Dokumente der Aufgabe (linke Spalte) und dann auf den verknüpften AEM Assets-Ordner „Endgültig“. Wählen Sie Ihr Asset aus, indem Sie auf seine Zone und dann auf „Korrekturabzug erstellen“ klicken. Ein Korrekturabzug ist die Möglichkeit, Inhalte, wie z. B. Bilder, Texte, Videos, Websites usw., strukturiert und kollaborativ zu prüfen, wobei Kommentare, Korrekturen, Änderungen der beteiligten Stakeholder erfasst, Versionen und Ergebnisse verglichen und mit einem Klick endgültig genehmigt werden können.

![Korrekturabzug erstellen](./images/wf-create-proof.png)

- Wählen Sie „Erweiterter Korrekturabzug“ aus, da wir einen aufwändigen Genehmigungsprozess benötigen.

![Erweiterter Korrekturabzug](./images/wf-advanced-proof.png)

>[!NOTE]
>
> Wir werden manuell entscheiden, wer unseren Testversand in diesem Bootcamp überprüfen und/oder genehmigen wird. In den meisten realen Anwendungsfällen würden wir eine vordefinierte Vorlage von Genehmigungsflüssen verwenden, die bereits für jeden Testversand-Typ definiert ist bzw. sind.

- Standardmäßig haben wir den Workflow-Typ „Standard“ und wählen Ihren Workfront Bootcamp-Spezialisten als Prüfer und Genehmiger aus. Geben Sie den Namen Ihres Bootcamp Workfront-Spezialisten ein, der lautet: „Kontaktnamen oder E-Mail-Adresse eingeben, um einen Empfänger hinzuzufügen:

![Testversand zuweisen](./images/wf-proof-assign.png)

![Testversand zuweisen](./images/wf-assign-proof-2.png)

- Legen Sie sie als „Prüfende Person und genehmigende Person“ fest:

![Prüfer und genehmigende Person](./images/wf-review-approve.png)

- Klicken Sie auf „Korrekturabzug erstellen“. Workfront benötigt einige Minuten, um den Testversand zu generieren:

![Korrekturabzug wird erstellt](./images/wf-generating-proof.png)

- Ihr Workfront-Spezialist erhält jetzt eine neue Benachrichtigung, die ihn darüber informiert, dass er einen Korrekturabzug zur Überprüfung und/oder Genehmigung hat:

![Workfront-Aufgabe](./images/wf-proof-task.png)

- Nachdem er auf die Benachrichtigung geklickt hat, wird er mit Ihrem Korrekturabzug konfrontiert und kann einige Kommentare abgeben und/oder diesen Korrekturabzug genehmigen.

   - Er kann auf „Kommentar hinzufügen“ oben auf dem Bildschirm klicken, wenn er Anmerkungen hat:

  ![Kommentar hinzufügen](./images/wf-proof-add-comment.png)

   - Sie können dann nicht nur Kommentare hinzufügen, sondern auch die kleine Zeiger-Symbolleiste verwenden, um klar zu definieren, welcher Bereich geändert werden muss.

  ![Pin-Punkt-Kommentar](./images/wf-proof-comment.png)

   - Durch Hinzufügen des Kommentars können Sie darüber informiert werden, dass Sie an einer neuen Version des Korrekturabzugs zusätzliche Arbeit leisten müssen. Aktualisieren Sie Ihre Registerkarte Workfront . Sie erhalten eine neue Benachrichtigung, die Sie genau darüber informiert. Sobald Sie wissen, welche Änderungen Sie vornehmen müssen, nehmen Sie Ihre Änderungen in AEM vor und laden Sie dann Ihre neue Version hier hoch:

  ![Neue Version hochladen](./images/wf-upload-version.png)

   - Wählen Sie Ihr aktualisiertes Asset aus (wenn im Bootcamp-Szenario keine Änderungen erforderlich sind, laden Sie dasselbe Asset erneut hoch) und klicken Sie auf „Link“:

  ![Asset verknüpfen](./images/wf-link-new-asset.png)

   - Klicken Sie dann auf der rechten Seite auf „Korrekturabzug erstellen“.

  ![Korrekturabzug erstellen](./images/create-new-proof.png)

   - Sobald der Korrekturabzug erstellt wurde (dies kann einige Augenblicke dauern), erhält Ihr Workfront-Spezialist eine Benachrichtigung und kann diese neue Version überprüfen und hoffentlich genehmigen.  Beispielsweise können sie mithilfe der Schaltfläche für den Korrekturabzug-Vergleich einen direkten Vergleich von V1 und V2 mit allen vorgenommenen Kommentaren sehen.

  ![Korrekturabzug vergleichen](./images/wf-proof-compare.png)

  ![Entscheidung treffen](./images/make-decision-proof.png)

  ![genehmigt](./images/approved.png)

Wir haben jetzt eine formelle Genehmigung für die Verwendung unseres Banners. Es ist einfach zu verfolgen, wo wir uns befinden, und die Updates, die Sie vornehmen, führen automatisch zu einem Trigger von Benachrichtigungen, sodass Sie so effizient wie möglich arbeiten können.

Nächster Schritt: [Phase 2 - Produktion: Social-Media-Anzeige erstellen](./social.md)

[Zurück zu Phase 1 - Planung: Sonstige Vorarbeiten](../planning/prework.md)

[Zurück zu „Alle Module“](../../overview.md)
