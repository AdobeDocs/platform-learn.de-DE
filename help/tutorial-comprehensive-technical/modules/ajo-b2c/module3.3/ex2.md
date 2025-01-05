---
title: Offer decisioning - Konfigurieren von Angeboten und Entscheidungs-ID
description: Offer decisioning - Konfigurieren von Angeboten und Entscheidungs-ID
kt: 5342
doc-type: tutorial
exl-id: 1418398b-d192-4d0b-b372-4be73fc153ed
source-git-commit: 21718a7c3a4df2793ae257a9b7cbe4466f1193f5
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 4%

---

# 3.3.2 Angebote und Entscheidungen konfigurieren

## 3.3.2.1 Personalisierte Angebote erstellen

In dieser Übung erstellen Sie vier **personalisierte Angebote**. Im Folgenden finden Sie die Details, die bei der Erstellung dieser Angebote zu berücksichtigen sind:

| Name | Datumsbereich | Bild-Link für E-Mail | Bildlink für Web | Text | Priorität | Eignung | Sprache | Begrenzungsfrequenz | Bildname |
|-----|------------|----------------------|--------------------|------|:--------:|--------------|:-------:|:-------:|:-------:|
| `--aepUserLdap-- - AirPods Max` | Heute - 1 Monat später | https://bit.ly/4a9RJ5d | Aus Assets Library auswählen | `{{ profile.person.name.firstName }}, 10% discount on AirPods Max` | 25 | Alle - Weibliche Kunden | Englisch (USA) | 3 | Apple AirPods Max - Weiblich.jpg |
| `--aepUserLdap-- - Galaxy S24` | Heute - 1 Monat später | https://bit.ly/3W8yuDv | Aus Assets Library auswählen | `{{ profile.person.name.firstName }}, 5% discount on Galaxy S24` | 15 | Alle - Weibliche Kunden | Englisch (USA) | 3 | Galaxy S24 - Weiblich.jpg |
| `--aepUserLdap-- - Apple Watch` | Heute - 1 Monat später | https://bit.ly/4fGwfxX | https://bit.ly/4fGwfxX | `{{ profile.person.name.firstName }}, 10% discount on Apple Watch` | 25 | Alle - Männliche Kunden | Englisch (USA) | 3 | Apple Watch - Male.jpg |
| `--aepUserLdap-- - Galaxy Watch 7` | Heute - 1 Monat später | https://bit.ly/4gTrkeo | Aus Assets Library auswählen | `{{ profile.person.name.firstName }}, 5% discount on Galaxy Watch 7` | 15 | Alle - Männliche Kunden | Englisch (USA) | 3 | Galaxy Watch7 - Männlich.jpg |

{style="table-layout:auto"}

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

Klicken Sie im linken Menü auf **Angebote** und gehen Sie dann zu **Angebote**. Klicken Sie auf **+ Angebot erstellen**.

![Entscheidungsregel](./images/offers1.png)

Dann sehen Sie dieses Popup. Wählen Sie **Personalisiertes Angebot** aus und klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/offers2.png)

Sie befinden sich jetzt in der Ansicht **Details**.

![Entscheidungsregel](./images/offers3.png)

In diesem Fall müssen Sie den `--aepUserLdap-- - AirPods Max` konfigurieren. Füllen Sie die Felder anhand der Informationen in der obigen Tabelle aus. In diesem Beispiel lautet der Name des personalisierten Angebots **vangeluw - AirPods Max**. Legen Sie außerdem **Startdatum und -uhrzeit** auf „Heute“ und **Enddatum und -uhrzeit** auf ein Datum in einem Monat fest.

Sobald das erledigt ist, sollten Sie es haben. Klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/offers4.png)

Sie sehen dann Folgendes:

![Entscheidungsregel](./images/constraints.png)

Wählen Sie **Nach definierter Entscheidungsregel** und klicken Sie auf das Symbol **+** , um die Regel **Alle - Weibliche Kunden“**.

Füllen Sie die **Priorität** wie in der obigen Tabelle angegeben aus. Klicken Sie anschließend auf **+ Begrenzung erstellen** um festzulegen, wie oft dieses Angebot einer Kundin oder einem Kunden angezeigt werden kann.

![Entscheidungsregel](./images/constraints1.png)

Wählen Sie für die Begrenzung Folgendes aus:

- **Begrenzungsereignis auswählen**: **Entscheidungsereignis**
- **Begrenzungstyp**: **Pro Profil (Begrenzung für jedes Profil anwenden)**
- **Anzahl der Begrenzungsereignisse**: **3**
- **Begrenzungshäufigkeit zurücksetzen**: **Täglich**
- **Jeden**: **1 Tag**

Dadurch wird sichergestellt, dass dieses Angebot nicht öfter als dreimal pro Tag und Kunde angezeigt wird.

Klicken Sie auf **Erstellen**.

![Entscheidungsregel](./images/constraints2.png)

Dann bist du wieder hier. Klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/constraints3.png)

Jetzt müssen Sie (**)**. Darstellungen sind eine Kombination aus einer **Platzierung** und einem echten Asset.

Wählen Sie für **Darstellung 1** Folgendes aus:

- Kanal: Web
- Platzierung: Web - Bild
- Inhalt: URL
- Öffentlicher Speicherort: Kopieren Sie die URL aus der Spalte **Bildlink für Web** in der obigen Tabelle

![Entscheidungsregel](./images/addcontent1.png)

Alternativ können Sie **Asset-Bibliothek** für den Inhalt auswählen und dann auf **Durchsuchen** klicken.

![Entscheidungsregel](./images/addcontent2.png)

Anschließend wird ein Popup der Assets-Bibliothek angezeigt. Wechseln Sie zum Ordner **enable-assets** und wählen Sie die Bilddatei **Apple AirPods Max - Female.jpg** aus. Klicken Sie dann auf **Auswählen**.

![Entscheidungsregel](./images/addcontent3.png)

Sie werden es dann sehen. Klicken Sie auf **+ Darstellung**.

![Entscheidungsregel](./images/addcontentrep20.png)

Wählen Sie für **Darstellung**:

- Kanal: E-Mail
- Platzierung: E-Mail - Bild
- Inhalt: URL
- Öffentlicher Speicherort: Wählen Sie **Asset-Bibliothek** aus. Klicken Sie auf **Durchsuchen**

![Entscheidungsregel](./images/addcontentrep21.png)

Anschließend wird ein Popup der Assets-Bibliothek angezeigt. Wechseln Sie zum Ordner **enable-assets** und wählen Sie die Bilddatei **Apple AirPods Max - Female.jpg** aus. Klicken Sie dann auf **Auswählen**.

![Entscheidungsregel](./images/addcontent3b.png)

Sie werden es dann sehen. Klicken Sie anschließend auf **+ Darstellung hinzufügen**.

![Entscheidungsregel](./images/addcontentrep20b.png)

Wählen Sie **Darstellung 3** Folgendes aus:

- Kanal: Nicht digital
- Platzierung: Nicht digital - Text

Als Nächstes müssen Sie Inhalte hinzufügen. In diesem Fall bedeutet dies, dass der Text hinzugefügt wird, der als Aktionsaufruf verwendet werden soll.

Wählen Sie **Benutzerdefiniert** und klicken Sie auf **Inhalt hinzufügen**.

![Entscheidungsregel](./images/addcontentrep31.png)

Dann sehen Sie dieses Popup.

![Entscheidungsregel](./images/addcontent3text.png)

Schauen Sie sich das **Text** Feld aus der obigen Tabelle an und geben Sie diesen Text hier ein, in diesem Fall: `{{ profile.person.name.firstName }}, 10% discount on AirPods Max`.

Sie werden auch feststellen, dass Sie ein beliebiges Profilattribut auswählen und es als dynamisches Feld in den Angebotstext aufnehmen können. In diesem Beispiel stellt die `{{ profile.person.name.firstName }}` sicher, dass der Vorname des Kunden, der dieses Angebot erhält, im Angebotstext enthalten ist.

Sie werden es dann sehen. Klicken Sie auf **Speichern**.

![Entscheidungsregel](./images/addcontentrep3text.png)

Jetzt hast du das. Klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/addcontentrep3textdone.png)

Anschließend sehen Sie einen Überblick über Ihr neues **personalisiertes Angebot**. Klicken Sie auf **Fertigstellen**.

![Entscheidungsregel](./images/offeroverview.png)

Klicken Sie **Speichern und genehmigen**.

![Entscheidungsregel](./images/saveapprove.png)

Anschließend wird Ihr neu erstelltes personalisiertes Angebot in der Angebotsübersicht verfügbar:

![Entscheidungsregel](./images/offeroverview1.png)

Sie sollten nun die obigen Schritte wiederholen, um die drei anderen personalisierten Angebote für die Produkte zu erstellen, die Sie in der obigen Tabelle finden.

Danach sollte der Bildschirm **Angebotsübersichten** für **Personalisierte Angebote** alle Ihre Angebote anzeigen.

![Endgültige Angebote](./images/finaloffers.png)

## 3.3.2.2 Fallback-Angebot erstellen

Nachdem Sie vier personalisierte Angebote erstellt haben, sollten Sie jetzt ein **Fallback-Angebot“**.

Stellen Sie sicher, dass Sie sich in der Ansicht **Angebote** befinden. Klicken Sie auf **+ Angebot erstellen**.

![Entscheidungsregel](./images/createoffer.png)

Dann sehen Sie dieses Popup. Wählen Sie **Fallback-Angebot** aus und klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/foffers2.png)

Sie werden es dann sehen. Geben Sie folgenden Namen für Ihr Fallback-Angebot ein: `--aepUserLdap-- - CitiSignal Fallback Offer`. Klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/foffers4.png)

Jetzt müssen Sie (**)**. Darstellungen sind eine Kombination aus einer **Platzierung** und einem echten Asset.

Wählen Sie für **Darstellung 1** Folgendes aus:

- **channel**: **web**
- **Placement**: **Web - Bild**
- **Content**: **Asset-Bibliothek**

Klicken Sie **Durchsuchen**, um Ihr Bild auszuwählen.

![Entscheidungsregel](./images/addcontent1fb.png)

Sie sehen dann ein Popup der Assets-Bibliothek, wechseln Sie zum Ordner **citi-signal-images** und wählen Sie die Bilddatei **App-Banner-Ad.jpg** aus. Klicken Sie dann auf **Auswählen**.

![Entscheidungsregel](./images/addcontent3fb.png)

Sie werden es dann sehen. Klicken Sie auf **+ Darstellung hinzufügen**.

![Entscheidungsregel](./images/addcontentrep20fb.png)

Wählen Sie für **Darstellung**:

- **channel**: **email**
- **Platzierung**: **E-Mail - Bild**
- **Content**: **Asset-Bibliothek**

Klicken Sie **Durchsuchen**, um Ihr Bild auszuwählen.

![Entscheidungsregel](./images/addcontentrep21fb.png)

Sie sehen dann ein Popup der Assets-Bibliothek, wechseln Sie zum Ordner **citi-signal-images** und wählen Sie die Bilddatei **App-Banner-Ad.jpg** aus. Klicken Sie dann auf **Auswählen**.

![Entscheidungsregel](./images/addcontent3bfb.png)

Sie werden es dann sehen. Klicken Sie auf **+ Darstellung hinzufügen**.

![Entscheidungsregel](./images/addcontentrep20bfb.png)

Wählen Sie **Darstellung 3** Folgendes aus:

- **Kanal**: **Nicht digital**
- **Platzierung**: **Nicht digital - Text**
- **content**: **custom**

Klicken Sie **Inhalt hinzufügen**.

![Entscheidungsregel](./images/addcontentrep21text.png)

Dann sehen Sie dieses Popup. Geben Sie den `{{ profile.person.name.firstName }}, download the CitiSignal app now!` ein und klicken Sie auf **Speichern**.

![Entscheidungsregel](./images/faddcontent3text.png)

Sie werden es dann sehen. Klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/faddcontentrep3.png)

Anschließend sehen Sie einen Überblick über Ihr neues **Fallback-Angebot**. Klicken Sie auf **Fertigstellen**.

![Entscheidungsregel](./images/fofferoverview.png)

Klicken Sie abschließend auf **Speichern und genehmigen**.

![Entscheidungsregel](./images/saveapprovefb.png)

Auf dem Bildschirm **Angebotsübersichten** wird nun Folgendes angezeigt:

![Endgültige Angebote](./images/ffinaloffers.png)

## 3.3.2.3 Sammlung erstellen

Eine Sammlung wird verwendet **um eine Untergruppe von Angeboten aus der personalisierten Angebotsliste** herauszufiltern) und diese als Teil einer Entscheidung zu verwenden, um den Entscheidungsprozess zu beschleunigen.

Navigieren Sie zu **Sammlungen**. Klicken Sie auf **+ Sammlung erstellen**.

![Entscheidungsregel](./images/collections.png)

Daraufhin wird dieses Popup angezeigt. Konfigurieren Sie Ihre Sammlung wie folgt. Klicken Sie auf **Weiter**.

- Sammlungsname: Verwenden Sie `--aepUserLdap-- - CitiSignal Collection`
- Wählen Sie **Statische Sammlung erstellen** aus.

Klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/createcollectionpopup1.png)

Wählen Sie im nächsten Bildschirm die vier **Personalisierten Angebote** aus, die Sie in der vorherigen Übung erstellt haben. Klicken Sie auf **Speichern**.

![Entscheidungsregel](./images/createcollectionpopup2.png)

Sie sehen dies jetzt:

![Entscheidungsregel](./images/colldone.png)

## 3.3.2.4 Entscheidung erstellen

Eine Entscheidung kombiniert Platzierungen, eine Sammlung personalisierter Angebote und ein Fallback-Angebot, das letztendlich von der Offer decisioning-Engine verwendet wird, um das beste Angebot für ein bestimmtes Profil zu finden, basierend auf den individuellen personalisierten Angebotsmerkmalen wie Priorität, Eignungsbegrenzung und Gesamtbegrenzung / Benutzerobergrenze.

Um Ihre **Entscheidung** zu konfigurieren, navigieren Sie zu **Entscheidungen**. Klicken Sie auf **+ Entscheidung erstellen**.

![Entscheidungsregel](./images/activitydd.png)

Sie werden es dann sehen. Füllen Sie die Felder wie folgt aus. Klicken Sie auf **Weiter**.

- Name: `--aepUserLdap-- - CitiSignal Decision`
- Startdatum und -uhrzeit: heute
- Enddatum und -uhrzeit: heute + 1 Monat

![Entscheidungsregel](./images/activity2.png)

Im nächsten Bildschirm müssen Sie Platzierungen zu Entscheidungsumfängen hinzufügen. Sie müssen Entscheidungsumfänge für die Platzierungen (Web **Bild),** E-**Bild** und **Nicht digital - Text** erstellen.

![Entscheidungsregel](./images/addplacements.png)

Erstellen Sie zunächst den Entscheidungsumfang für **Nicht digital - Text**, indem Sie diese Platzierung in der Dropdown-Liste auswählen. Klicken Sie dann auf **Hinzufügen**, um Bewertungskriterien hinzuzufügen.

![Entscheidungsregel](./images/activity3.png)

Wählen Sie Ihre `--aepUserLdap-- - CitiSignal Collection` aus und klicken Sie auf **Hinzufügen**.

![Entscheidungsregel](./images/activity4text.png)

Sie werden es dann sehen. Klicken Sie auf die Schaltfläche **+**, um einen neuen Entscheidungsumfang hinzuzufügen.

![Entscheidungsregel](./images/activity5text.png)

Wählen Sie die Platzierung **Web - Bild** aus und fügen Sie Ihre `--aepUserLdap-- - CitiSignal Collection` unter Auswertungskriterien hinzu. Klicken Sie dann erneut auf die Schaltfläche **+**, um einen neuen Entscheidungsumfang hinzuzufügen.

![Entscheidungsregel](./images/activity6text.png)

Wählen Sie die Platzierung **E-Mail - Bild** aus und fügen Sie Ihre `--aepUserLdap-- - CitiSignal Collection` unter „Auswertungskriterien“ hinzu. Klicken Sie dann auf **Weiter**.

![Entscheidungsregel](./images/activity4.png)

Nun müssen Sie Ihr **Fallback-Angebot** auswählen, das `--aepUserLdap-- - CitiSignal Fallback Offer` heißt. Klicken Sie auf **Weiter**.

![Entscheidungsregel](./images/activity10.png)

Überprüfen Sie Ihre Entscheidung. Klicken Sie auf **Fertigstellen**.

![Entscheidungsregel](./images/activity11.png)

Klicken Sie im Popup auf **Speichern und**.

![Entscheidungsregel](./images/activity12.png)

Und schließlich sehen Sie jetzt Ihre Entscheidung in der Übersicht:

![Entscheidungsregel](./images/activity13.png)

Sie haben Ihre Entscheidung jetzt erfolgreich konfiguriert. Ihre Entscheidung ist jetzt live und kann verwendet werden, um Ihren Kunden optimierte und personalisierte Angebote in Echtzeit bereitzustellen.

Nächster Schritt: [3.3.3 Bereiten Sie Ihre Datenerfassungs-Client-Eigenschaft und das Web-SDK-Setup für das Offer decisioning vor](./ex3.md)

[Zurück zum Modul 3.3](./offer-decisioning.md)

[Zurück zu „Alle Module“](./../../../overview.md)
