---
title: CSC Bootcamp - Erstellen von Mobile-App-Inhalten
description: CSC Bootcamp - Erstellen von Mobile-App-Inhalten
doc-type: multipage-overview
exl-id: db4e91da-2077-4133-aca9-e3413990f4be
source-git-commit: 143da6340b932563a3309bb46c1c7091e0ab2ee2
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 0%

---

# Mobile-App-Inhalte erstellen

## Was ist Headless-Inhaltsbereitstellung?

Mit einem Headless-Content-Management-System sind Backend und Frontend jetzt entkoppelt. Der Headless-Teil ist das Inhalts-Backend, da ein Headless-CMS ein reines Backend-Content-Management-System ist, das explizit als Inhalts-Repository entwickelt und erstellt wurde, das Inhalte über eine API für die Anzeige auf jedem Gerät zugänglich macht.

Das Frontend, das unabhängig entwickelt und gepflegt wird, ruft mithilfe einer Content Delivery-API Inhalte aus dem Headless-Backend ab, normalerweise im JSON-Format. Dies könnte beispielsweise als Web-Anwendung oder in unserem Fall als Mobile App erfolgen.

Ein Headless-CMS-Backend erfordert normalerweise, dass der Inhalt basierend auf einem Modell oder Schema strukturiert ist. Dies erleichtert es Client-Programmen, die richtigen Inhalte für das Rendern eines Erlebnisses anzufordern. Einige CMS, wie AEM, können sowohl strukturierte als auch unstrukturierte Inhalte im JSON-Format bereitstellen.

Ein wesentliches Merkmal dieser Topologie ist, dass der Inhalt, der von der Headless-CMS im JSON-Format bereitgestellt wird, reiner Inhalt ohne Design- oder Layout-Informationen ist. In einer Headless-CMS-Implementierung werden alle Formatierungen und Layouts von der entkoppelten Frontend-Anwendung verwaltet.

Ein wesentlicher Vorteil einer Headless-CMS-Topologie besteht in der Möglichkeit, Inhalte über mehrere Kanäle hinweg wiederzuverwenden, wobei verschiedene Client-seitige Frontend-Implementierungen verwendet werden können. Dies kann den Frontend-Entwicklungsprozess effizienter gestalten. Aber es bedeutet auch, dass der Frontend-Erlebnisentwicklungsprozess sehr Code- und IT-orientiert werden kann, wobei die IT im Wesentlichen das Erlebnis besitzt.

## Wie funktioniert die Bereitstellung von Headless-Inhalten in AEM?

AEM as a Cloud Service ist ein flexibles Tool für das Headless-Implementierungsmodell, das drei leistungsstarke Funktionen bietet:

![Headless-Inhaltsbereitstellung](./images/prod-app-headless.png)

1. Inhaltsmodelle
   - Inhaltsmodelle sind strukturierte Darstellungen von Inhalten.
   - Inhaltsmodelle werden von Informationsarchitekten im AEM-Inhaltsfragmentmodell-Editor definiert.
   - Inhaltsmodelle dienen als Grundlage für Inhaltsfragmente.
1. Inhaltsfragmente
   - Inhaltsfragmente werden auf Grundlage eines Inhaltsmodells erstellt.
   - Erstellt von Inhaltsautoren mit dem AEM-Inhaltsfragment-Editor.
   - Inhaltsfragmente werden in AEM Assets gespeichert und in der Admin-Benutzeroberfläche von Assets verwaltet.
1. Inhalts-API für die Bereitstellung
   - Die AEM GraphQL-API unterstützt die Bereitstellung von Inhaltsfragmenten.
   - Die AEM Assets-REST-API unterstützt CRUD-Vorgänge für Inhaltsfragmente.
   - Die direkte Bereitstellung von Inhalten ist auch mit dem [JSON-Export der Inhaltsfragment-Kernkomponente) ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=en).

## Übung

Bei diesem Bootcamp konzentrieren wir uns auf den Teil „Inhalt“ - schließlich ist es die Inhaltslieferkette, die wir anstreben. Wir haben bereits ein Inhaltsmodell sowie die erforderlichen Bereitstellungs-APIs vorgesehen, damit Sie sich auf das Wichtige konzentrieren können.

Lassen Sie uns zunächst unser Inhaltsmodell untersuchen: Es ist der „Vertrag“, den wir mit dem Headless-CMS haben, damit wir wissen, welche Inhalte auf unseren Weg kommen können und in welchem Format.

- Gehen Sie zur AEM-Autoreninstanz auf [https://author-p105462-e991028.adobeaemcloud.com/](https://author-p105462-e991028.adobeaemcloud.com/) und melden Sie sich mit den von uns angegebenen Anmeldeinformationen an.

- Wählen Sie im AEM-Startmenü Tools \> Allgemein \> Inhaltsfragmentmodelle

![Menü Inhaltsfragmentmodelle](./images/prod-app-cfm.png)

- Auf dem nächsten Bildschirm erhalten Sie einen Überblick über alle Sites, die Headless-Inhalte verwenden. Auf diese Weise können Sie die Governance über mehrere Headless-Sites beibehalten, ohne befürchten zu müssen, dass sie sich gegenseitig stören. In unserem Fall arbeiten wir mit unserer Adobe-Website, also wählen Sie dieses Modell.

![verschiedene Headless-Sites](./images/prod-app-cfm-folder.png)

- In diesem Ordner können wir einige technische Headless-Inhalte sehen, die wir auf der Adobe-Website verwenden. Möchten Sie mehr erfahren? Fühlen Sie sich frei, die Hand auszustrecken. Konzentrieren wir uns vorerst auf die Aufgabe vor der Hand: die Mobile App. Bewegen Sie den Mauszeiger über die Startseitenkarte der Mobile App und klicken Sie auf das Stiftsymbol, um das Inhaltsmodell zu öffnen.

![Mobile-App-Homepage-Inhaltsmodell](./images/prod-app-created-cfm.png)

- Im Inhaltsfragmentmodell-Editor können Sie die Details eines bestimmten Inhaltsmodells sehen. In unserem Fall können wir sehen, dass die Homepage unserer mobilen App mit dem Adobe-Logo, einer Überschrift, einem optionalen freien Text und einem optionalen vorgestellten Produkt existiert. Alle diese Elemente sind einfach zu konfigurieren und zu aktualisieren, sodass Sie, wenn Ihr Inhaltsmodell zusätzliche Elemente benötigt, dies ohne Einmischung von Entwicklern auf der CMS-Seite durchführen können.

![Inhaltsmodell Details](./images/prod-app-cfm-details.png)

>[!WARNING]
>
> **Beachten Sie, dass eine Änderung des Inhaltsmodells Auswirkungen auf die Zukunft hat** da die Mobile App auf den Erhalt bestimmter Informationen angewiesen ist, um die richtigen Elemente anzeigen zu können. Seien Sie besonders vorsichtig, wenn Sie Felder aktualisieren oder entfernen. Das Hinzufügen von Feldern sollte keine Auswirkungen haben.

Jetzt, da wir eine Vorstellung davon haben, welchen Inhalt wir haben sollten, können wir unser Inhaltsfragment machen.

- Klicken Sie auf das AEM-Logo oben links im Bildschirm, um die Navigation zu öffnen, und gehen Sie dann zu Navigation \> Inhaltsfragmente .

![Menüoption „Inhaltsfragmente“](./images/prod-cf-ui.png)

- In der folgenden Benutzeroberfläche erhalten Sie einen Überblick über alle vorhandenen Inhalte in AEM. Die Filter auf der linken Seite können verwendet werden, um einzugrenzen, wenn Sie nach einem bestimmten Inhaltsfragment suchen. Um ein neues Inhaltsfragment zu erstellen, klicken wir oben rechts auf die Schaltfläche „Erstellen“.

![Schaltfläche „Inhaltsfragment erstellen“](./images/prod-app-create-cf.png)

- Im sich öffnenden Modal sehen Sie, dass einige Felder noch nicht bearbeitbar sind. Das ist logisch: Je nachdem, wo wir unser Fragment erstellen, werden verschiedene Modelle verfügbar sein.
  ![Inhaltsfragment erstellen](./images/prod-app-create-cf-details.png)
   - Wählen Sie zunächst aus, wo wir unser Fragment erstellen werden, indem Sie auf das Ordnersymbol neben dem Feld „Standort“ klicken. Erweitern Sie die Inhaltsstruktur, indem Sie auf die Ordner „adobike“ \> „en“ \> „mobile-app“ klicken, und bestätigen Sie Ihre Auswahl, indem Sie auf die Schaltfläche „Auswählen“ klicken.
     ![Wählen Sie den richtigen Speicherort aus](./images/prod-app-folder.png)
   - Sie werden feststellen, dass das Feld „Inhaltsfragmentmodell“ jetzt bearbeitbar ist. Klicken Sie auf den Pfeil neben dem Feld, um das Dropdown-Menü zu öffnen, und wählen Sie das Inhaltsmodell aus, das wir zuvor betrachtet haben: „Mobile App Homepage“.
   - Geben Sie als Nächstes Ihrem Inhaltsfragment einen aussagekräftigen Titel (Tipp: Geben Sie Ihre Team-Nummer an, damit Sie Ihren Inhalt schnell finden können). Sie werden feststellen, dass das Feld „Name“ automatisch ausgefüllt wird - dies soll Ihnen das Leben erleichtern: Es ist der Name, den das System verwendet, um Ihr Fragment zu identifizieren, und sollte nicht berührt werden.
   - Klicken Sie abschließend auf die Schaltfläche „Erstellen und öffnen“, mit der Sie das Inhaltsfragment erstellen und öffnen können, sodass Sie es sofort bearbeiten können, wie der Name schon sagt.

- Hier kann Ihr Team entscheiden, welche Inhalte Sie in der Mobile App anzeigen möchten. ![Inhaltsfragmentdetails](./images/prod-cf-details.png)
   - Wählen Sie unbedingt Ihre Team-Nummer aus, damit Sie Ihren Inhalt später in der Mobile App überprüfen können.
   - Um Bild-Assets auszuwählen, klicken Sie auf das Ordnersymbol, um AEM Assets nach dem richtigen Bild zu durchsuchen.
   - Klicken Sie für das angezeigte Produkt auf das Produktsuchsymbol, damit Sie einfach unser Commerce-Produkt „AdobeBike 1“ auswählen können, damit die Commerce-bezogenen Details in die App geladen werden.
   - Klicken Sie auf die Schaltfläche „Speichern“, wenn Sie fertig sind, um alle Ihre erstellten Inhalte zu speichern und Ihre Änderungen zu veröffentlichen.
     ![Änderungen veröffentlichen](./images/prod-app-publish.png)

Nachdem wir nun die Mobile App mit einigen Inhalten vorhergesehen haben, sind wir bereit, unsere Kampagne bereitzustellen.


Nächster Schritt: [Phase 3 - Versand: Mobile App überprüfen](../delivery/app.md)

[Zurück zu Phase 2 - Produktion: Social-Media-Anzeige erstellen](./social.md)

[Zurück zu „Alle Module“](../../overview.md)
