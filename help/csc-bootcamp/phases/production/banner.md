---
title: CSC Bootcamp - Erstellen eines Produkt-Homepage-Banners
description: CSC Bootcamp - Erstellen eines Produkt-Homepage-Banners
doc-type: multipage-overview
source-git-commit: 989e4e2add1d45571462eccaeebcbe66a77291db
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 0%

---

# Produkt-Homepage-Banner erstellen

## Erstellung des Banners

Durch die Automatisierung von Inhalten wird die Leistung von Adobe Creative Cloud auf Experience Manager Assets übertragen, sodass Marketing-Experten die Asset-Produktion skaliert automatisieren und so die Erstellung von Varianten erheblich beschleunigen können. Verwenden wir diese Funktionen, um ein Banner zu generieren, das auf der Homepage verwendet werden soll!

- Navigieren Sie zum AEM Autor auf [https://author-p105462-e991028.adobeaemcloud.com/](https://author-p105462-e991028.adobeaemcloud.com/) und melden Sie sich mit den angegebenen Anmeldedaten an.

- Navigieren Sie auf der Startseite zu Tools > Assets > Verarbeitungsprofile .

![Tools > Assets > Verarbeitungsprofile](./images/prod-processing-profiles.png)

- Auf der Benutzeroberfläche werden alle vorhandenen Verarbeitungsprofile angezeigt. Diese können verwendet werden, um bestimmte Automatisierungen zu ermöglichen.

![Liste der Verarbeitungsprofile](./images/prod-profile-list.png)


- Die folgenden sind für Sie von Interesse:
   - Adobe Banner Dark: erstellt ein AdobeBike-Banner mit einer dunklen Überlagerung basierend auf dem ausgewählten Asset.
      ![dunkles Banner](./images/prod-banner-dark.jpg)
   - Adobe Banner Light: erstellt ein AdobeBike-Banner mit einer Lichtüberlagerung, basierend auf dem ausgewählten Asset
      ![Leuchtbanner](./images/prod-banner-light.jpg)
   - Adobe Banner Green: erstellt ein AdobeBike-Banner mit einer grünen Überlagerung basierend auf dem ausgewählten Asset.
      ![grünes Banner](./images/prod-banner-green.jpg)

- Nachdem Sie den Bannertyp ausgewählt haben, den Sie erstellen möchten, wählen Sie dieses Verarbeitungsprofil und dann &quot;Profil auf Ordner anwenden&quot;.

![Profil auf Ordner anwenden](./images/prod-apply-profile.png)

- Navigieren Sie auf dem nächsten Bildschirm zum Ordner Ihres Teams in AEM Assets. Wählen Sie dann oben links die Schaltfläche &quot;Erstellen&quot; aus, um einen neuen Ordner zu erstellen und ihm einen aussagekräftigen Namen zu geben, z. B. &quot;Dark Banner erstellen&quot;.

![Ordner erstellen](./images/prod-create-profile-folder.png)

![Ordnerdetails erstellen](./images/prod-profile-folder-details.png)

- Markieren Sie nach der Erstellung des Ordners das Kästchen neben seinem Namen und klicken Sie dann oben rechts auf die Schaltfläche &quot;Anwenden&quot;.

![Auf erstellten Ordner anwenden](./images/prod-select-profile-folder.png)

Nachdem wir die erforderliche Konfiguration vorgenommen haben, erstellen wir unser Banner.

- Klicken Sie auf das AEM Logo oben links, um die Navigation zu öffnen, und navigieren Sie dann zu Navigation \> Assets \> Dateien .

![AEM-Startbildschirm](./images/prod-select-assets.png)
![Bildschirm für AEM Assets](./images/prod-select-assets-2.png)

- Suchen Sie den Ordner &quot;Generierte Adobe-Assets&quot;und öffnen Sie ihn durch Klicken auf die Karte. Hier werden die generierten Banner angezeigt.

![generierte Adobike-Assets](./images/prod-generated-banners.png)

- Öffnen Sie eine neue Registerkarte und navigieren Sie erneut zu AEM Assets. Navigieren Sie dann zu dem Ordner, auf den das Verarbeitungsprofil angewendet wurde.

- Laden Sie im Ordner das Bild hoch, für das Sie ein Banner erstellen möchten, indem Sie es in den Browser ziehen und dort ablegen oder oben rechts in der Benutzeroberfläche auf Dateien erstellen klicken.

![Upload durch Drag-and-Drop](./images/prod-drag-drop-banner.png)

![Upload mithilfe der Erstellungsdatei](./images/prod-create-file.png)


- Warten Sie eine Minute, bis Ihr Asset verarbeitet wurde, und laden Sie dann den Bildschirm neu. Wenn Ihr Asset den Status &quot;Neu&quot;aufweist, wissen Sie, dass die Verarbeitung abgeschlossen ist.

![Asset in neuem Status](./images/prod-asset-processed.png)

- Navigieren Sie zurück zur vorherigen Registerkarte und laden Sie den Bildschirm auch hier neu. Sie sollten ein neues Asset im Status &quot;Neu&quot;bemerken. Dies ist unser generiertes Banner, alles aus dem DAM! Siehst du es noch nicht? Warten Sie noch eine Minute und laden Sie dann den Bildschirm neu.

![generiertes Banner](./images/prod-new-banner.png)

>[!NOTE]
>
> Ist das Ergebnis nicht zufrieden? Sie können auch ein anderes Verarbeitungsprofil auf Ihren Ordner anwenden und Ihr Asset erneut hochladen, um ein anderes Banner zu generieren (oder natürlich ein anderes Asset hochladen). Während des Neuladens fragt das System Sie, was Sie mit dem vorhandenen Asset machen möchten, und wählen Sie &quot;Ersetzen&quot;.
> ![vorhandene ersetzen](./images/prod-replace-asset.png)

Jetzt haben wir unser generiertes Banner, das wir später bei der Bereitstellung unserer Kampagne verwenden können. Stellen Sie sicher, dass Sie das Banner veröffentlichen, indem Sie es auswählen und dann auf die Schaltfläche &quot;Quick Publish&quot;auf dem Band klicken.

![Asset veröffentlichen](./images/prod-publish-banner.png)

## Folgemaßnahmen zu Workfront

Wenn Sie einen formellen und prüfbaren Review- und Genehmigungsprozess für Ihre Assets benötigen, ist Workfront der richtige Ort.

>[!NOTE]
>
> Obwohl wir dies hier ausdrücklich erwähnen, ist es beabsichtigt, die Aufgaben in Workfront zu aktualisieren, nachdem Sie sie abgeschlossen haben. Sie sollten immer nach einem Ablauf &quot;Erstellen&quot;> &quot;Überprüfen&quot;> &quot;Genehmigen&quot;streben.

- Gehen wir zurück zu unserem Projekt und erweitern Sie das Akkordeon &quot;Go/No Go Banner Review&quot;, um die Aufgabe zu öffnen, indem Sie darauf klicken:

![Banner go/no-go](./images/banner-gonogo.png)

- Klicken Sie in der linken Spalte auf den Bereich Dokumente der Aufgabe und dann auf den mit AEM Assets verknüpften Ordner &#39;Final&#39;. Wählen Sie unser Asset aus, indem Sie auf seine Zone klicken und auf &quot;Testversand erstellen&quot;klicken. Ein Beweis ist die Möglichkeit, Inhalte, z. B. Bild, Text, Video, Website usw., in strukturierter und kollaborativer Weise zu überprüfen, wobei Kommentare, Korrekturen, Änderungen der beteiligten Akteure erfasst werden, Versionen und Ergebnisse verglichen und durch einen Klick endgültig genehmigt werden können.

![Testversand erstellen](./images/wf-create-proof.png)

- Wählen Sie &quot;Erweiterter Testversand&quot;, da Sie einen detaillierten Validierungsprozess benötigen.

![Advanced proof](./images/wf-advanced-proof.png)

>[!NOTE]
>
> Wir werden manuell entscheiden, wer unseren Testversand in diesem Bootcamp überprüfen und/oder genehmigen wird. In den meisten realen Anwendungsfällen würden wir eine voreingestellte Vorlage für den/die Validierungsfluss(e) verwenden, die bereits für jeden Testversand-Typ definiert ist/sind.

- Standardmäßig befinden wir uns in einem Workflow-Typ &quot;Standard&quot; und wählen Ihren Workfront Bootcamp-Spezialisten als Reviewer &amp; Genehmiger aus. Geben Sie den Namen Ihres Bootcamp Workfront Specialist ein, in dem steht: Kontaktname oder E-Mail-Adresse, um einen Empfänger hinzuzufügen:

![Zuweisen eines Testversands](./images/wf-proof-assign.png)

![Zuweisen eines Testversands](./images/wf-assign-proof-2.png)

- Legen Sie sie als &quot;Reviewer &amp; Genehmiger&quot;fest:

![validierer und validierer](./images/wf-review-approve.png)

- Klicken Sie auf &quot;Testversand erstellen&quot;. Workfront benötigt einen Moment, um den Testversand zu erzeugen:

![Nachweis](./images/wf-generating-proof.png)

- Ihr Workfront-Spezialist wird jetzt über eine neue Benachrichtigung informiert, dass er über einen Nachweis zur Überprüfung und/oder Genehmigung verfügt:

![Aufgabe &quot;workfront&quot;](./images/wf-proof-task.png)

- Nachdem Sie auf die Benachrichtigung geklickt haben, wird Ihr Testversand angezeigt und kann einige Kommentare abgeben und/oder diesen Testversand validieren.

   - Wenn Anmerkungen vorhanden sind, können sie oben im Bildschirm auf &quot;Kommentar hinzufügen&quot;klicken:

   ![Kommentar hinzufügen](./images/wf-proof-add-comment.png)

   - Sie können dann nicht nur Kommentare hinzufügen, sondern auch die kleine Zeiger-Symbolleiste verwenden, um klar zu definieren, welcher Bereich geändert werden muss.

   ![Punkt-Kommentar einfügen](./images/wf-proof-comment.png)

   - Durch Hinzufügen des Kommentars können Sie wissen, dass Sie zusätzliche Arbeit an einer neuen Version des Testversands benötigen. Aktualisieren Sie Ihren Workfront-Tab. Sie erhalten eine neue Benachrichtigung, die Sie darüber informiert. Sobald Sie wissen, welche Änderungen Sie vornehmen müssen, nehmen Sie Ihre Änderungen in AEM vor und laden Sie Ihre neue Version hier hoch:

   ![neue Version hochladen](./images/wf-upload-version.png)

   - Wählen Sie Ihr aktualisiertes Asset aus (wenn im Bootcamp-Szenario keine Änderungen erforderlich sind, laden Sie einfach dasselbe Asset erneut hoch) und klicken Sie auf &quot;Link&quot;:

   ![Link-Asset](./images/wf-link-new-asset.png)

   - Klicken Sie dann auf der rechten Seite auf &#39;Testversand erstellen&#39;.

   ![Testversand erstellen](./images/create-new-proof.png)

   - Sobald der Testversand erstellt wurde (dies kann einige Augenblicke dauern), erhält Ihr Workfront-Spezialist eine Benachrichtigung und kann diese neue Version überprüfen und hoffentlich genehmigen.  Mithilfe der Schaltfläche zum Testversand-Vergleich können sie beispielsweise einen parallelen Vergleich von V1 und V2 mit allen Kommentaren sehen.

   ![Testversand](./images/wf-proof-compare.png)

   ![Entscheidungsfindung](./images/make-decision-proof.png)

   ![genehmigt](./images/approved.png)

Wir haben jetzt eine formelle Genehmigung für die Verwendung unseres Banners. Es ist einfach zu folgen, wo wir uns im Prozess befinden, und die Updates, die Sie automatisch Trigger-Benachrichtigungen durchführen, damit Sie so effizient wie möglich arbeiten können.

Nächster Schritt: [Phase 2 - Produktion: Social Media-Anzeige erstellen](./social.md)

[Gehen Sie zurück zu Phase 1 - Planung: Sonstige Vorarbeiten](../planning/prework.md)

[Zu allen Modulen zurückkehren](../../overview.md)
