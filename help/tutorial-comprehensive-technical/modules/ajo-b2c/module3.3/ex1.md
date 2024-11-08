---
title: Offer decisioning - Offer decisioning 101
description: Offer decisioning - Offer decisioning 101
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 4%

---

# 3.3.1 Offer decisioning 101

## 3.3.1.1 Terminologie

Um ein besseres Verständnis von Offer decisioning zu erhalten, empfehlen wir dringend, die [Übersicht](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=en) darüber zu lesen, wie der Offer decisioning Application Service mit Adobe Experience Platform funktioniert.

Beim Arbeiten mit Offer decisioning müssen Sie die folgenden Konzepte verstehen:

| Begriff | Erklärung |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Angebot** | Ein Angebot ist eine Marketing-Botschaft, der ggf. Regeln zugeordnet sind, die angeben, wer zum Anzeigen des Angebots berechtigt ist. Ein Angebot hat den Status Entwurf, Validierung oder Archivierung. |
| **Platzierung** | Die Kombination aus Position (oder Kanaltyp) und Kontext (oder Content-Typ), in dem ein Angebot für einen Endbenutzer angezeigt wird. Es handelt sich dabei um eine Kombination aus Text-, HTML-, Bild-, JSON-Dateien in mobilen, Web-, Social-, Instant Messaging- und nicht digitalen Kanälen. |
| **Regel** | Die Logik, die die Eignung von Endbenutzern für ein Angebot definiert und steuert. |
| **Personalisiertes Angebot** | Eine anpassbare Marketing-Botschaft, die auf Eignungsregeln und Einschränkungen basiert. |
| **Fallback-Angebot** | Das Standardangebot, das angezeigt wird, wenn ein Endbenutzer für keines der Angebote in der verwendeten Kollektion geeignet ist. |
| **Capping** | Wird in einer Angebotsdefinition verwendet, um festzulegen, wie oft ein Angebot insgesamt und für einen bestimmten Benutzer unterbreitet werden kann. |
| **Priorität** | Ebene zur Bestimmung der Prioritätsstufe aus einem Ergebnissatz von Angeboten. |
| **Sammlung** | Wird verwendet, um eine Untergruppe von Angeboten aus der personalisierten Angebotsliste herauszufiltern und so den offer decisioning-Prozess zu beschleunigen. |
| **Entscheidung** | Eine Kombination aus Angeboten, Platzierungen und Profilen, für die das Entscheidungsmodul das beste Angebot bereitstellen soll. |
| **AEM Assets Essentials** | Ein universelles und zentralisiertes Erlebnis zum Speichern, Suchen und Auswählen von Assets in Adobe Experience Cloud Solutions und Adobe Experience Platform. |

{style="table-layout:auto"}

## 3.3.1.2 Offer decisioning

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der Ansicht **Home** Ihrer Sandbox `--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

Klicken Sie im linken Menü auf **Angebote**. Sie sehen nun das Menü Angebote , das Angebote, Sammlungen und Entscheidungen enthält.

![Platzierungen](./images/homedec.png)

Klicken Sie auf **Komponenten**. Jetzt wird das Menü Angebote angezeigt, das Elemente wie Platzierungen, Tags, Regeln und Bewertungen enthält.

![Platzierungen](./images/components.png)

## 3.3.1.3 Praktika

Navigieren Sie zu **Platzierungen**.

![Platzierungen](./images/placements.png)

Auf der Registerkarte **Platzierungen** können Sie Ihre Platzierungen für Ihre Angebote definieren. Wenn Sie eine Entscheidung definieren, definiert die Platzierung, wo das resultierende Angebot angezeigt wird (Kanaltyp) und in welcher Form oder Form (Inhaltstyp).

Wenn keine Platzierungen in Ihrer Adobe Experience Platform-Instanz angezeigt werden, erstellen Sie sie wie unten und im Screenshot angegeben.

| Name | Kanaltyp | Content-Typ |
| ---------------------- | ------------ | ------------ |
| **Nicht digital – Text** | Nicht digital | Text |
| **Web - JSON** | Web | JSON |
| **Web - HTML** | Web | HTML |
| **Web - Text** | Web | Text |
| **Web – Bild** | Web | Bild |
| **E-Mail - JSON** | E-Mail | JSON |
| **E-Mail - HTML** | E-Mail | HTML |
| **E-Mail - Text** | E-Mail | Text |
| **E-Mail – Bild** | E-Mail | Bild |

{style="table-layout:auto"}

**Hinweis**: Bitte ändern Sie nichts an den bereits verfügbaren Platzierungen.

Klicken Sie auf eine beliebige Platzierung, um deren Einstellungen zu visualisieren.

![Platzierungen](./images/placement1.png)

Jetzt werden alle Felder der Platzierung angezeigt:

- **Name** der Platzierung
- **Platzierungs-ID**
- **Kanaltyp** für die Platzierung
- **Content-Typ** der Platzierung, der **Text**, **HTML**, **Bild** oder **JSON** sein kann
- **Beschreibung** -Feld zum Hinzufügen einer zusätzlichen Beschreibung für die Platzierung

## 3.3.1.4 Entscheidungsregeln

Eine Regel (auch als Eignungsregel bezeichnet) entspricht einem **Segment** . Eine Regel ist in der Tat ein Segment selbst mit dem einzigen Unterschied, dass eine Regel mit einem Angebot verwendet werden kann, um einem Profil in Adobe Experience Platform das beste Angebot zu unterbreiten.

Da Sie bereits wissen, wie Sie Segmente basierend auf den vorherigen Aktivierungsmodulen definieren, sollten Sie einfach die Segmentierungsumgebung schnell erneut aufrufen:

Navigieren Sie zu **Regeln**. Klicken Sie auf **+ Regel erstellen**.

![Entscheidungsregeln](./images/rules.png)

Anschließend sehen Sie die Segmentierungsumgebung von Adobe Experience Platform.

![Entscheidungsregeln](./images/createrule1.png)

Sie können jetzt auf alle Felder zugreifen, die Teil des Vereinigungsschemas für das Echtzeit-Kundenprofil sind, und eine beliebige Regel erstellen.

Interessant ist auch, dass Sie bereits definierte Segmente einfach in Adobe Experience Platform wiederverwenden können, indem Sie zu **Zielgruppen** > ``--aepTenantId--`` navigieren.

![Entscheidungsregel](./images/decisionruleaud.png)

Daraufhin sehen Sie Folgendes:

![Entscheidungsregel](./images/decisionruleaud1.png)

Bei Bedarf können Sie nun Ihre eigenen Regeln konfigurieren. Für diese Übung benötigen Sie zwei Regeln:

- all - Männliche Kunden
- all - Weibliche Kunden

Wenn diese Regeln noch nicht existieren, erstellen Sie sie bitte. Wenn sie bereits existieren, verwenden Sie bitte diese Regeln und erstellen Sie keine neuen Regeln.

Das Attribut, das zum Erstellen der Regel verwendet wird, lautet **XDM Individual Profile** > **Person** > **Geschlecht**.

Hier finden Sie beispielsweise die Regeldefinition für die Regel &quot;**all - Männliche Kunden**&quot;:

![Entscheidungsregel](./images/allmale.png)

Hier finden Sie beispielsweise die Regeldefinition für die Regel **all - Weibliche Kunden**:

![Entscheidungsregel](./images/allfemale.png)

## 3.3.1.5 Angebote

Wechseln Sie zu **Angebote** und wählen Sie **Angebote** aus. Klicken Sie auf **+ Angebot erstellen**.

![Entscheidungsregel](./images/offers1.png)

Dann sehen Sie dieses Popup.

![Entscheidungsregel](./images/offers2.png)

Erstellen Sie jetzt keine Angebote - das machen Sie in der nächsten Übung.

Sie sehen nun, dass es zwei Angebotstypen gibt:

- Personalisierte Angebote
- Fallback-Angebote

Ein personalisiertes Angebot ist ein spezifischer Inhalt, der in einer bestimmten Situation angezeigt werden soll. Ein personalisiertes Angebot wurde speziell entwickelt, um ein persönliches und kontextbezogenes Erlebnis bereitzustellen, wenn bestimmte Kriterien erfüllt sind.

Ein Fallback-Angebot ist ein Angebot, das angezeigt wird, wenn die Kriterien für personalisierte Angebote nicht erfüllt sind.

## 3.3.1.6 Beschlüsse

Eine Entscheidung kombiniert Platzierungen, eine Kollektion personalisierter Angebote und ein Fallback-Angebot, die letztendlich vom Offer decisioning-Modul verwendet werden, um das beste Angebot für ein bestimmtes Profil zu finden, basierend auf den individuellen personalisierten Angebotsmerkmalen wie Priorität, Eignungsbegrenzung und Gesamtanzahl/Benutzerobergrenze.

Um Ihre **Entscheidung** zu konfigurieren, klicken Sie auf **Entscheidungen**.

![Entscheidungsregel](./images/activity.png)

In der nächsten Übung konfigurieren Sie Ihre eigenen Angebote und Entscheidungen.

Nächster Schritt: [3.3.2 Konfigurieren Ihrer Angebote und Entscheidungen](./ex2.md)

[Zurück zu Modul 3.3](./offer-decisioning.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
