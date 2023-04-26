---
title: CSC Bootcamp - Seite in AEM erstellen
description: CSC Bootcamp - Seite in AEM erstellen
doc-type: multipage-overview
source-git-commit: 989e4e2add1d45571462eccaeebcbe66a77291db
workflow-type: tm+mt
source-wordcount: '1917'
ht-degree: 6%

---

# Seite in AEM erstellen

AEM bietet Ihnen zwei Umgebungen: die Autorenumgebung und die Veröffentlichungsumgebung. Diese interagieren und ermöglichen es Ihnen, Inhalte auf Ihrer Website verfügbar zu machen, damit Ihre Besucher sie erleben können.

Die Autorenumgebung bietet die Mechanismen zum Erstellen, Aktualisieren und Überprüfen dieses Inhalts, bevor er tatsächlich veröffentlicht wird:

- Ein Autor erstellt und überprüft den Inhalt (dabei kann es sich um verschiedene Inhaltstypen handeln, z. B. Seiten, Assets, Veröffentlichungen usw.),
- der zu einem späteren Zeitpunkt auf Ihrer Website veröffentlicht wird.

Als Autor müssen Sie Ihre Website in AEM organisieren. Dazu gehört die Erstellung und Benennung von Inhaltsseiten, sodass:

- Sie müssen leicht in der Authoring-Umgebung auffindbar sein.
- Besucher der Website müssen sie einfach in der Veröffentlichungsumgebung durchsuchen können.

Die Struktur einer Website kann als Baumstruktur gesehen werden, die die Inhaltsseiten enthält. Die Namen dieser Inhaltsseiten werden zur Bildung der URLs verwendet. Der Titel wird zusammen mit dem Seiteninhalt angezeigt. Im folgenden Beispiel lautet die barrierefreie URL für die Seite /content/adobike/language-masters/en.html

![Seitenstruktur](./images/delivery-web-structure.png)

Im Folgenden wird beschrieben, wie Sie einer vorhandenen Website neue Seiten hinzufügen und Inhalte wiederverwenden können.

## Erstellen der Startseite

Wie im vorherigen Abschnitt erläutert, funktioniert AEM Seitenhierarchie als Baumstruktur. Das bedeutet, dass wir mit der Seite auf der höchsten Ebene beginnen werden: die Startseite.

- Navigieren Sie zum AEM Autor auf [https://author-p71057-e991028.adobeaemcloud.com/](https://author-p71057-e991028.adobeaemcloud.com/) und melden Sie sich mit den angegebenen Anmeldedaten an.

- Wählen Sie im AEM Startmenü Navigation > Sites aus.

![Sitesymbol auswählen](./images/delivery-web-aem-sites.png)

- Navigieren wir zuerst in der vorhandenen Baumstruktur zu dem Ort, an dem wir unsere Homepage erstellen möchten. Navigieren Sie zur Baumstruktur, indem Sie in der ersten Spalte &quot;AdobeBike&quot;und in der zweiten Spalte &quot;Bootcamp&quot;auswählen. Um eine Seite unter dieser Seite zu erstellen, klicken Sie auf die Schaltfläche &quot;Erstellen&quot;und wählen Sie im sich öffnenden Menü &quot;Seite&quot; aus.

![Bootcamp-Inhalte wiederfinden](./images/delivery-web-create-page.png)

- Dadurch wird ein neuer Bildschirm geöffnet und die neue Seite konfiguriert. Zuerst können wir eine Seitenvorlage auswählen. Mit Seitenvorlagen in AEM können Sie die Struktur einer Seite definieren und festlegen, welcher Inhalt auf dieser Seite verwendet werden kann. Da wir die Landingpage als Landingpage erstellen möchten, wählen wir die Landingpage-Vorlage aus und klicken dann auf die Schaltfläche &quot;Weiter&quot;, um fortzufahren.

![die richtige Vorlage auswählen](./images/delivery-web-create-page-template.png)

- Im nächsten Bildschirm können Sie Ihre Seite mit einigen anfänglichen Informationen füllen. Die wichtigste Information ist der Titel (eine obligatorische Eigenschaft, gekennzeichnet mit einem \* ), der dafür gedacht ist, dass Sie Ihrer Seite einen aussagekräftigen Namen geben. Wenn Sie den &quot;Namen&quot;nicht ausfüllen, generiert AEM automatisch die URL, auf der Ihre Seite verfügbar sein wird, entsprechend den Best Practices für SEO. In diesem Fall können Sie dieses Feld leer lassen. Auch andere Eigenschaften können ausgefüllt werden. Sie können die anderen Registerkarten durchsuchen, aber für dieses Bootcamp füllen Sie noch keine anderen Eigenschaften aus. Wenn Sie bereit sind, Ihre Seite zu erstellen, klicken Sie einfach auf die Schaltfläche &quot;Erstellen&quot;.

![Füllen Sie die Eigenschaften aus](./images/delivery-web-create-page-properties.png)

- AEM erstellt nun Ihre Seite. Danach erscheint ein Popup, in dem Sie die neu erstellte Seite öffnen können, indem Sie auf die Schaltfläche &quot;Öffnen&quot;klicken.

![Öffnen Sie die neu erstellte Seite](./images/delivery-web-create-page-success.png)

- Sie gelangen jetzt in den AEM Editor. Dies ist ein WYSIWYG-Editor, in dem Sie Komponenten per Drag-and-Drop auf eine Seite ziehen können, um Ihre Seite zu erstellen. Sehen wir uns die Navigation an:
   ![Wysiwiw-Editor von AEM](./images/delivery-web-page-editor-home.png)
   - Auf der linken Seite befindet sich das seitliche Bedienfeld mit den Assets, die Sie auf Ihren Seiten verwenden können, den Komponenten (oder Bausteinen), die Sie auf dieser Seite verwenden können, und einer praktischen Baumansicht, die Ihnen zeigt, wie Ihre Seite strukturiert ist. Klicken Sie auf eines dieser Symbole, um deren Ansicht zu öffnen.
   - Auf der rechten Seite sehen Sie den &quot;Layout-Container&quot;. In diesem Bereich können Sie die gewünschten Komponenten ablegen.
   - Füllen wir unsere Seite mit etwas Inhalt. Füllen Sie die Startseite nach Belieben aus. Im folgenden Beispiel haben wir eine Bildkomponente verwendet, die mit der Produktseite verknüpft ist, sowie zwei Teaser-Komponenten.

![die Homepage](./images/delivery-web-homepage.png)

## Erlebnisse mithilfe von Experience Fragments wiederverwenden

Wir haben nun die Homepage verfasst, die für unseren Adobe-Launch bereit ist. Allerdings können einige Inhalte, wie z.B. die einzigartigen Verkaufspunkte unseres Fahrrads, auf mehreren Seiten wiederverwendet werden.

Idealerweise möchten wir dieses einzigartige Verkaufspunkterlebnis nur einmal erstellen, damit wir es zentral verwalten und ein personalisiertes und dennoch konsistentes Erlebnis sicherstellen können. In AEM können wir dies mit &quot;Experience Fragments&quot;tun. Ein Experience Fragment ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können. Sie können jede beliebige Komponente enthalten.

Lassen Sie uns dies sofort verwenden:

- Navigieren Sie zum AEM Autor auf [https://author-p71057-e991028.adobeaemcloud.com/](https://author-p71057-e991028.adobeaemcloud.com/) und melden Sie sich mit den angegebenen Anmeldedaten an.

- Wählen Sie im AEM Startmenü die Option Navigation > Experience Fragments .

![XF-Symbol auswählen](./images/delivery-web-xf.png)

- Erstellen wir im folgenden Bildschirm einen Ordner, in dem Ihr Team seine wiederverwendbaren Erlebnisse speichern kann. Navigieren Sie in der Spaltenansicht zu Adobe \> Bootcamp und klicken Sie dann auf die Schaltflächen \> Ordner erstellen .

![Ordner erstellen](./images/delivery-web-create-xf-folder.png)

- Geben Sie im modalen Popup-Fenster den Namen Ihres Teams für Ihren Ordner an. Sie können das Namensfeld leer lassen. AEM wird es automatisch für Sie generieren. Nachdem Sie dem Ordner einen Namen gegeben haben, klicken Sie auf die Schaltfläche Erstellen , um den Ordner zu erstellen.

![Namen geben](./images/delivery-web-create-xf-folder-name.png)

- Ihr Ordner sollte nun in einem Popup angezeigt werden. Klicken Sie darauf und dann auf die Schaltflächen Erstellen \> Experience Fragment .

![Erstellen einer xf-Datei](./images/delivery-web-create-xf.png)

- Wählen wir zunächst eine Experience Fragment-Vorlage aus. Wie Seiten können auch Experience Fragments auf mehreren Vorlagen basieren, von denen jede ein vordefiniertes Erlebnis vorsieht. Da wir in unserem Fall unseren Inhalt auf unserer Website wiederverwenden möchten, wählen wir eine &quot;Experience Fragment-Webvariationsvorlage&quot;aus, indem wir das Kontrollkästchen links oben aktivieren und dann auf die Schaltfläche &quot;Weiter&quot;klicken.

![eine xf-Vorlage auswählen](./images/delivery-web-create-xf-template.png)

- Geben Sie Ihrem Experience Fragment einen aussagekräftigen Titel, z. B. &quot;Adobe USPs&quot;und klicken Sie dann auf die Schaltfläche &quot;Erstellen&quot;.

![xf einen Titel geben](./images/create-xf-properties.png)

- Nachdem Sie Ihr Experience Fragment erstellt haben, klicken Sie im Modal auf die Schaltfläche &quot;Öffnen&quot;, damit wir Inhalte in unserem Experience Fragment hinzufügen können.

![Klicken Sie auf Öffnen](./images/delivery-web-create-xf-success.png)

- Genau wie beim Bearbeiten einer Seite können Sie einen Layout-Container sehen, in dem Sie Inhalte hinzufügen können.

![xf-Editor](./images/delivery-web-xf-editor.png)

- Kopieren Sie auf der Startseite über die Komponenten. Navigieren Sie auf einer neuen Registerkarte zur Homepage, wie im vorherigen Kapitel erläutert, wählen Sie die Komponente aus, über die Sie kopieren möchten, und klicken Sie dann auf das Kopiersymbol.

![eine Komponente kopieren](./images/delivery-web-copy-from-home.png)

- Klicken Sie dann wieder in Ihrem Experience Fragment auf den Layout-Container und dann auf die Schaltfläche &quot;Einfügen&quot;.

![Einfügen der Komponente](./images/delivery-web-paste-to-xf.png)

>[!NOTE]
>
> Tipp: AEM ermöglicht die Verwendung des &quot;Layout-Modus&quot;in beliebigen Seiten oder Experience Fragments. Auf diese Weise können Sie die Größe der Komponenten ändern und Erlebnisse für jedes Gerät optimieren.

- Öffnen Sie im oberen Menü das Dropdown-Menü und wählen Sie &quot;Layout&quot;, um in den Layout-Modus zu wechseln.

![Layout-Modus ändern](./images/delivery-web-layout-mode.png)

- Anschließend können Sie eine beliebige Komponente auswählen und ihre Größe ändern, indem Sie einfach die Griffe auf beide Seiten der Komponente ziehen und an den auf dem Bildschirm sichtbaren Spalten ausrichten.

![Größe von Komponenten nach Belieben ändern](./images/delivery-web-layout-resize.png)

- Standardmäßig bearbeiten Sie alle Haltepunkte. Wenn Sie jedoch für einen bestimmten Haltepunkt bearbeiten möchten, können Sie ein passendes Gerät in der Symbolleiste am oberen Seitenrand auswählen. Der Haltepunkt, für den Sie dann das Authoring durchführen, wird dann hervorgehoben.

![Breakpoint auswählen](./images/delivery-web-bp-before.png)

- Wie Sie sehen können, sieht ein zweispaltiges Layout auf einem Mobilgerät nicht besonders gut aus. Erstellen wir ein Layout für eine Spalte auf einem Mobilgerät. Wie Sie auf dem Desktop sehen können, bleibt unser Erlebnis gleich, aber auf dem Mobilgerät haben wir jetzt ein besseres Erlebnis mit nur einer Inhaltsspalte.

![für Mobilgeräte optimieren](./images/delivery-web-bp-after.png)

- Schließlich können wir dieses Erlebnis nun auf der Homepage wiederverwenden. Ziehen Sie eine Komponente &quot;Experience Fragment&quot;per Drag-and-Drop auf die Seite an die Stelle, an der der Inhalt angezeigt werden soll. Sie können den von uns kopierten Inhalt löschen, da wir ihn aus dem Experience Fragment verwenden werden.

![Ziehen und Ablegen einer xf-Komponente](./images/delivery-web-xf-on-home.png)

- Öffnen Sie das Konfigurationsdialogfeld für die Experience Fragment-Komponente und wählen Sie mit der Pfadauswahl den Speicherort aus, an dem Sie Ihr Experience Fragment erstellt haben.

![auf das Ordnersymbol klicken](./images/delivery-web-xf-dialog.png)

![das richtige XF auswählen](./images/delivery-web-select-xf.png)

- Und schließlich haben wir unsere wiederverwendbare Erfahrung auf unserer Seite.

![die aktualisierte Homepage](./images/delivery-web-xf-result.png)

## Produktseite erstellen

Bei Verwendung von Adobe Commerce in AEM können Sie über eine generische Produktdetailseite verfügen, die beim Navigieren auf der Site aus den generierten Übersichten verwendet wird. Manchmal möchten wir jedoch auch eine inspirierende Seite vorsehen, die produktspezifische Inhalte mit inspirierenden Inhalten kombiniert. Kopieren wir über den Laden, wie von uns vorgestellt, und erstellen wir dann eine inspirierende Produktseite.

- Navigieren Sie zum AEM Autor auf [https://author-p71057-e991028.adobeaemcloud.com/](https://author-p71057-e991028.adobeaemcloud.com/) und melden Sie sich mit den angegebenen Anmeldedaten an.

- Wählen Sie im AEM Startmenü Navigation > Sites aus.

![Sitesymbol auswählen](./images/delivery-web-aem-sites.png)

- Navigieren Sie in der Spaltenübersicht zur vordefinierten Website zum Shop: AdobeBike \> Language Masters \> AdobeBike \> Shop. Wählen Sie dann die Seite Shop mit dem Kontrollkästchen aus und klicken Sie auf Erstellen \> Live Copy . Ohne zu viele Details zu berücksichtigen, wird dadurch eine Kopie der Seite erstellt, die Sie auf Ihrer Site verwenden können, damit Sie die bereits vorhandenen Seiten und Inhalte mithilfe AEM Multi-Site-Managers wiederverwenden können.

![Erstellen einer Live Copy](./images/delivery-web-create-lc.png)

- Wählen Sie im sich öffnenden Bildschirm die Site Ihrer Teams als Ziel aus, indem Sie das Kontrollkästchen neben dem Namen aktivieren. Klicken Sie dann auf die Schaltfläche Weiter .

![Ziel auswählen](./images/delivery-web-lc-destination.png)

- Da wir nicht tief in Multi Site Manager gehen werden, können Sie diese Konfiguration einfach übernehmen.\
   Titel: Shop\
   Name: shop\
   Rollout-Konfigurationen: Standard-Rollout-Konfiguration\
   Nachdem Sie die Live Copy konfiguriert haben, klicken Sie auf die Schaltfläche Erstellen .

![Live Copy konfigurieren](./images/delivery-web-lc-config.png)

>[!NOTE]
>
> Sind Sie neugierig auf Live Copies? Checkout [&quot;Erstellen und Synchronisieren von Live Copies&quot;.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/msm/creating-live-copies.html?lang=en)

- Danach sollte der Store auf Ihrer Website verfügbar sein. Wählen Sie es aus und klicken Sie dann auf Erstellen \> Seite , um unsere inspirierende Produktseite zu erstellen.

![Produktseite erstellen](./images/delivery-web-create-pdp.png)

- Da wir Produktinformationen auf der Seite anzeigen möchten, erstellen wir jetzt eine Seite mit der Produktseitenvorlage. Wählen Sie sie aus und klicken Sie auf die Schaltfläche Weiter .

![Verwenden der Produktseitenvorlage](./images/delivery-web-create-pdp-template.png)

- Füllen Sie die Metadaten der Seite aus und klicken Sie dann auf die Schaltfläche Erstellen , genau wie auf der Startseite. Nach der Erstellung können Sie die Seite öffnen, indem Sie auf die Schaltfläche Öffnen klicken. Wie Sie sehen können, ist es bereits mit einer Produktdetailkomponente ausgefüllt.

![Konfiguration abschließen](./images/delivery-web-pdp-initial.png)

- Zuerst fügen wir unser Erlebnisfragment hinzu, das wir zuvor erstellt haben. Dann können wir jeden weiteren Inhalt hinzufügen, den wir noch auf der Seite wünschen. Schließlich konfigurieren wir die Produktdetailkomponente, um unser Adobe-Produkt anzuzeigen, indem wir die Produktsuche im Konfigurationsdialogfeld auswählen, dann unsere AdobeBike-Kategorie auswählen und das Kontrollkästchen neben dem Produkt aktivieren. Klicken Sie dann auf die Schaltfläche Hinzufügen .

![Produktsuche auswählen](./images/delivery-web-configure-product.png)

![Produkt auswählen](./images/delivery-web-select-product.png)

- Wir verfügen nun über eine umfassende Inspirationsseite, einschließlich zentral verwalteter Inhalte und Produktinformationen aus Adobe Commerce.

![Die Produktseite](./images/delivery-web-pdp-result.png)

Nächster Schritt: [Phase 3 - Versand: Kampagne - GO/NO-GO](./go-nogo.md)

[Gehen Sie zurück zu Phase 3 - Versand: Mobile App überprüfen](./app.md)

[Zu allen Modulen zurückkehren](../../overview.md)
