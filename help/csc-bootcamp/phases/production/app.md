---
title: CSC Bootcamp - Erstellen von Inhalten mobiler Apps
description: CSC Bootcamp - Erstellen von Inhalten mobiler Apps
doc-type: multipage-overview
source-git-commit: 989e4e2add1d45571462eccaeebcbe66a77291db
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 22%

---

# Erstellen von mobilen App-Inhalten

## Was ist die Bereitstellung Headless Content?

Mit einem Headless-Content-Management-System sind Backend und Frontend jetzt entkoppelt. Der Headless-Teil ist das Inhalts-Backend, da ein Headless-CMS ein reines Back-End-Content-Management-System ist, das explizit als Inhalts-Repository konzipiert und erstellt wurde, das Inhalte über eine API für die Anzeige auf jedem Gerät zugänglich macht.

Das Frontend, das unabhängig entwickelt und gepflegt wird, ruft mithilfe einer Content Delivery-API Inhalte aus dem Headless-Backend ab, normalerweise im JSON-Format. Dies kann beispielsweise als Web-App oder in unserem Fall als Mobile App erfolgen.

Ein Headless-CMS-Backend erfordert normalerweise, dass der Inhalt basierend auf einem Modell oder Schema strukturiert ist. Dies erleichtert es Client-Programmen, die richtigen Inhalte für das Rendern eines Erlebnisses anzufordern. Einige CMS, wie AEM, können sowohl strukturierte als auch unstrukturierte Inhalte im JSON-Format verfügbar machen.

Ein wesentliches Merkmal dieser Topologie ist, dass der von dem Headless-CMS im JSON-Format bereitgestellte Inhalt ausschließlich Inhalt ohne Design- oder Layout-Informationen ist. In einer Headless-CMS-Implementierung werden alle Formatierungen und Layouts von der entkoppelten Frontend-Anwendung verwaltet.

Ein wesentlicher Vorteil einer Headless-CMS-Topologie besteht in der Möglichkeit, Inhalte über mehrere Kanäle hinweg wiederzuverwenden, wobei verschiedene Client-seitige Frontend-Implementierungen genutzt werden können. Dadurch kann der Frontend-Entwicklungsprozess effizienter gestaltet werden. Aber es bedeutet auch, dass der Frontend-Erlebnisentwicklungsprozess sehr Code- und IT-orientiert werden kann, wobei die IT im Wesentlichen das Erlebnis besitzt.

## Wie funktioniert die Bereitstellung von Headless Content in AEM?

AEM as a Cloud Service ist ein flexibles Tool für das Headless-Implementierungsmodell, das drei leistungsstarke Funktionen bietet:

![Headless-Content-Bereitstellung](./images/prod-app-headless.png)

1. Inhaltsmodelle
   - Inhaltsmodelle sind strukturierte Darstellungen von Inhalten.
   - Inhaltsmodelle werden von Informationsarchitekten im Inhaltsfragmentmodell-Editor in AEM definiert.
   - Inhaltsmodelle dienen als Grundlage für Inhaltsfragmente.
1. Content Fragments
   - Inhaltsfragmente werden basierend auf einem Inhaltsmodell erstellt.
   - Sie werden von Inhaltsautoren mit dem Inhaltsfragment-Editor in AEM erstellt.
   - Inhaltsfragmente werden in AEM Assets gespeichert und in der Administrator-Benutzeroberfläche von Assets verwaltet.
1. Inhalts-API für die Bereitstellung
   - Die AEM-GraphQL-API unterstützt die Bereitstellung von Inhaltsfragmenten.
   - Die AEM Assets-REST-API unterstützt CRUD-Vorgänge für Inhaltsfragmente.
   - Die direkte Bereitstellung von Inhalten ist auch mit dem [JSON-Export der Inhaltsfragment-Kernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=de) möglich.

## Übung

Für dieses Bootcamp konzentrieren wir uns auf den Teil &quot;Inhalt&quot; - schließlich ist es die Inhaltslieferkette, nach der wir uns bemühen. Wir haben bereits ein Inhaltsmodell sowie die erforderlichen Bereitstellungs-APIs geplant, damit Sie sich auf das Wesentliche konzentrieren können.

Untersuchen wir zunächst unser Inhaltsmodell: Es ist der &quot;Vertrag&quot;, den wir mit dem Headless-CMS haben, sodass wir wissen, welcher Inhalt uns weiterbringen kann und in welchem Format.

- Navigieren Sie zum AEM Autor auf [https://author-p105462-e991028.adobeaemcloud.com/](https://author-p105462-e991028.adobeaemcloud.com/) und melden Sie sich mit den angegebenen Anmeldedaten an.

- Wählen Sie im AEM Startmenü Tools > Allgemein > Inhaltsfragmentmodelle aus.

![Menü für Inhaltsfragmentmodelle](./images/prod-app-cfm.png)

- Auf dem nächsten Bildschirm erhalten Sie einen Überblick über alle Sites, die Headless Content verwenden. Dadurch können Sie die Verwaltung über mehrere Headless-Sites hinweg behalten, ohne befürchten zu müssen, dass sie sich gegenseitig stören. In unserem Fall arbeiten wir mit unserer Adobe-Site. Wählen Sie daher dieses Modell aus.

![verschiedene Headless-Sites](./images/prod-app-cfm-folder.png)

- In diesem Ordner können wir einige technische Headless-Inhalte sehen, die wir auf der Adobe-Website verwenden. Möchten Sie mehr wissen? Du kannst dich gerne ausbreiten. Zunächst sollten wir uns auf die Aufgabe konzentrieren, bevor wir sie durchführen: Mobile App. Bewegen Sie den Mauszeiger über die Karte Mobile App-Homepage und klicken Sie auf das Stiftsymbol, um das Inhaltsmodell zu öffnen.

![Inhaltsmodell der mobilen App-Homepage](./images/prod-app-created-cfm.png)

- Im Inhaltsfragmentmodell-Editor können Sie die Details eines bestimmten Inhaltsmodells sehen. In unserem Fall können wir sehen, dass die Homepage unserer mobilen App das Adobe-Bike-Logo, eine Überschrift, einen optionalen freien Text und ein optionales vorgestelltes Produkt enthält. Alle diese Elemente sind einfach zu konfigurieren und zu aktualisieren, sodass, wenn Ihr Inhaltsmodell zusätzliche Elemente benötigt, dies ohne Eingriff von Entwicklern auf der CMS-Seite erfolgen kann.

![detailliertes Inhaltsmodell](./images/prod-app-cfm-details.png)

>[!WARNING]
>
> **Beachten Sie, dass eine Änderung des Inhaltsmodells weitere Auswirkungen auf die Zeile hat**, da die Mobile App auf den Empfang bestimmter Informationen angewiesen ist, um die korrekten Elemente anzeigen zu können. Gehen Sie beim Aktualisieren oder Entfernen von Feldern besonders vorsichtig vor. Das Hinzufügen von Feldern sollte keine Auswirkungen haben.

Nachdem wir nun eine Vorstellung davon haben, woraus unser Inhalt bestehen sollte, können wir unser Inhaltsfragment erstellen.

- Klicken Sie auf das AEM Logo oben links, um die Navigation zu öffnen, und navigieren Sie dann zu Navigation \> Inhaltsfragmente .

![Menüoption &quot;Inhaltsfragmente&quot;](./images/prod-cf-ui.png)

- In der folgenden Benutzeroberfläche erhalten Sie einen Überblick über alle vorhandenen Inhalte in AEM. Die Filter auf der linken Seite können verwendet werden, um die Suche nach einem bestimmten Inhaltsfragment einzugrenzen. Um ein neues Inhaltsfragment zu erstellen, klicken wir oben rechts auf die Schaltfläche &quot;Erstellen&quot;.

![Schaltfläche &quot;Inhaltsfragment erstellen&quot;](./images/prod-app-create-cf.png)

- Im sich öffnenden Modal sehen Sie, dass einige Felder noch nicht bearbeitbar sind. Dies ist logisch: Je nachdem, wo wir unser Fragment erstellen, stehen verschiedene Modelle zur Verfügung.
   ![Inhaltsfragment erstellen](./images/prod-app-create-cf-details.png)
   - Wählen Sie zunächst aus, wo das Fragment erstellt werden soll, indem Sie auf das Ordnersymbol neben dem Feld &quot;Position&quot;klicken. Erweitern Sie den Inhaltsbaum, indem Sie auf die Ordner &quot;adobike&quot; \> &quot;en&quot; \> &quot;mobile-app&quot; klicken und dann Ihre Auswahl bestätigen, indem Sie auf die Schaltfläche &quot;Auswählen&quot; klicken.
      ![die richtige Position auswählen](./images/prod-app-folder.png)
   - Sie werden feststellen, dass das Feld &quot;Inhaltsfragmentmodell&quot;jetzt bearbeitbar ist. Klicken Sie auf den Pfeil neben dem Feld, um die Dropdown-Liste zu öffnen und das Inhaltsmodell auszuwählen, das wir zuvor angesehen haben: &quot;Startseite der mobilen App&quot;.
   - Geben Sie Ihrem Inhaltsfragment als Nächstes einen aussagekräftigen Titel (Tipp: Ihre Team-Nummer einschließen, um Ihren Inhalt einfach wiederzufinden). Sie werden feststellen, dass das Feld &quot;Name&quot; automatisch ausgefüllt wird, um Ihnen das Leben zu erleichtern: Es ist der Name, den das System verwendet, um Ihr Fragment zu identifizieren, und sollte nicht berührt werden.
   - Klicken Sie abschließend auf die Schaltfläche &quot;Erstellen und öffnen&quot;, da der Name angibt, dass das Inhaltsfragment erstellt und geöffnet wird, damit Sie es sofort bearbeiten können.

- Hier kann Ihr Team entscheiden, welche Inhalte in der App angezeigt werden sollen. ![Inhaltsfragmentdetails](./images/prod-cf-details.png)
   - Stellen Sie sicher, dass Sie Ihre Team-Nummer auswählen, damit Sie Ihren Inhalt später in der Mobile App überprüfen können.
   - Klicken Sie zum Auswählen von Bild-Assets auf das Ordnersymbol, um nach AEM Assets für das richtige Bild zu suchen.
   - Klicken Sie für das vorgestellte Produkt auf das Symbol für die Produktsuche, damit Sie einfach unser &quot;AdobeBike 1&quot;-Commerce-Produkt auswählen können, sodass die Commerce-bezogenen Details in die App geladen werden.
   - Wenn Sie fertig sind, klicken Sie auf die Schaltfläche &quot;Speichern&quot;, um alle erstellten Inhalte zu speichern und Ihre Änderungen zu veröffentlichen.
      ![Veröffentlichungsänderungen](./images/prod-app-publish.png)

Nachdem wir die mobile App mit einigen Inhalten geplant haben, können wir unsere Kampagne bereitstellen.


Nächster Schritt: [Phase 3 - Versand: Mobile App überprüfen](../delivery/app.md)

[Gehen Sie zurück zu Phase 2 - Produktion: Social Media-Anzeige erstellen](./social.md)

[Zu allen Modulen zurückkehren](../../overview.md)
