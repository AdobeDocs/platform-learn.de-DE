---
title: Firefly Custom Models-API
description: Arbeiten mit der Firefly Custom Models-API
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 330f4492-d0df-4298-9edc-4174b0065c9a
source-git-commit: a1da1c73cbddacde00211190a1ca3d36f7a2c329
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 0%

---

# 1.1.4 Firefly Custom Models-API

## 1.1.4.1 Was sind benutzerdefinierte Firefly-Modelle?

Mit benutzerdefinierten Firefly-Modellen können Sie mit der Funktion „Text in Bild“ Bildvarianten generieren, die Ihrer Marke entsprechen. Indem Sie diese Modelle mit Ihren eigenen Bildern trainieren, können Sie Inhalte generieren, die die Identität Ihrer Marke widerspiegeln.
Transformieren Sie Ihren Stil oder Ihr Thema, um neue Ideen zu erkunden, visualisieren Sie verschiedene Umgebungen, generieren Sie innovative Inhalte und passen Sie Inhalte an bestimmte Segmente an.

Mit benutzerdefinierten Firefly-Modellen können Sie…

- Erstellen von markeninternen Ideen und Konzepten
- Erstellen von Zeichendesigns mit konsistenten Stilen
- Erstellen konsistenter Markenstile zur schnellen Erweiterung von Kampagnen

Um dies zu erreichen, unterstützen benutzerdefinierte Firefly-Modelle:

- Benutzerdefinierte Betreffmodelle
- Benutzerdefinierte Stilmodelle

### Benutzerdefinierte Betreffmodelle

Beim Trainieren benutzerdefinierter Modelle für ein bestimmtes Subjekt - ob Objekte oder Charaktere - besteht das Ziel darin, die wesentlichen Funktionen des Subjekts zu identifizieren und dem Modell zu helfen, sie über verschiedene Kontexte und Positionen hinweg zu replizieren.

Suchen Sie beim Trainieren eines Subjektmodells nach Bildern mit den folgenden Merkmalen:

- Objektkonsistenz: Stellen Sie Bilder mit demselben Fabrikat und Modell wie das Objekt bereit, während Sie sicherstellen, dass das Objekt über Bilder hinweg nicht sehr unterschiedlich aussieht. Vermeiden Sie das Mischen mehrerer Farben und stellen Sie ein gemeinsames Design oder Muster unter den Bildern sicher. Das Motiv kann jedoch je nach Szene, Haltung, Kleidung und Hintergrund variieren.
- Objektfokus: Verwenden Sie Bilder des Objekts im klaren Fokus ohne unnötige Ablenkungen. Belassen Sie das Motiv in der Nähe der Bildmitte und stellen Sie sicher, dass es mindestens 25 % der Bildfläche einnimmt.
- Umgebungskontext: Stellen Sie Bilder des Themas in verschiedenen Ansichten und Kontexten bereit und zeigen Sie es in einer Vielzahl von Lichtbedingungen. Während Bilder mit weißem oder transparentem Hintergrund verwendet werden können, ist es am besten, auch einen Mix mit komplexeren Umgebungen zu haben.
- Andere Objekte vermeiden: Große Elemente im Hintergrund oder in Zusammenhang mit dem Zeichen vermeiden. Jedes große Element, das in den Bildern angezeigt wird, wird vom Modell gespeichert und wird in den generierten Bildern angezeigt, ähnlich wie dasselbe Element im Trainings-Datensatz.

### Benutzerdefinierte Stilmodelle

Benutzerdefinierte Modelle, die auf einem Stil trainiert wurden, identifizieren das Erscheinungsbild der Assets, um bei Aufforderung ähnliche Bilder zu generieren.

So trainieren Sie ein effektives Stilmodell:

- Für ähnliche Ästhetik sorgen: Verwenden Sie Bilder, die verschiedene Szenen und Objekte zeigen und dabei dasselbe Look-and-Feel beibehalten.
- Verschiedene Bilder verwenden: Verwenden Sie so viele Bilder wie möglich, um zu verhindern, dass sich das Modell zu sehr auf unerwünschte Objekte oder Objekte konzentriert.
- Vermeiden Sie feste Phrasen: Ein festes Muster hat eine größere Gewichtung als andere Phrasen. Wenn beispielsweise jede Beschriftung „Der Hintergrund ist einfarbig schwarz“ oder „Nette Cartoon-Stile“ enthält, hängt das Modell von dieser Phrase ab. Ohne diese Phrase werden bei jeder Testaufforderung keine gewünschten Ergebnisse generiert.

## Konfigurieren 1.1.4.2 benutzerdefinierten Modells

Navigieren Sie zu [https://firefly.adobe.com/](https://firefly.adobe.com/). Klicken Sie **Benutzerdefinierte Modelle**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm1.png){zoomable="yes"}

Möglicherweise wird diese Meldung angezeigt. Klicken Sie in diesem Fall auf **Zustimmen**, um fortzufahren.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm2.png){zoomable="yes"}

Sie sollten das dann sehen. Klicken Sie **Modell trainieren**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm3.png){zoomable="yes"}

Konfigurieren Sie die folgenden Felder:

- **Name**: `--aepUserLdap-- - Citi Signal Router Model` verwenden
- **Trainings-Modus**: Wählen Sie **Thema (technische Vorschau)**
- **Konzept**: `router` eingeben
- **Speichern unter**: Öffnen Sie die Dropdown-Liste und klicken Sie auf **+ Neues Projekt erstellen**

![Benutzerdefinierte Firefly-Modelle](./images/ffcm4.png){zoomable="yes"}

Benennen Sie das neue Projekt wie folgt: `--aepUserLdap-- - Custom Models`. Klicken Sie auf **Erstellen**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm5.png){zoomable="yes"}

Sie sollten das dann sehen. Klicken Sie auf **Fortfahren**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm6.png){zoomable="yes"}

Sie müssen jetzt die Referenzbilder für das zu trainierende benutzerdefinierte Modell bereitstellen. Klicken Sie **Bilder vom Computer auswählen**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm7.png){zoomable="yes"}

Laden Sie die Referenzbilder [hier](https://tech-insiders.s3.us-west-2.amazonaws.com/CitiSignal_router.zip) herunter. Entpacken Sie die heruntergeladene Datei, die Ihnen dies geben sollte.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm8.png){zoomable="yes"}

Navigieren Sie zu dem Ordner, der die heruntergeladenen Grafikdateien enthält. Wählen Sie sie alle aus und klicken Sie auf **Öffnen**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm9.png){zoomable="yes"}

Sie sehen dann, dass Ihre Bilder geladen werden.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm10.png){zoomable="yes"}

Nach einigen Minuten werden Ihre Bilder korrekt geladen. Möglicherweise sehen Sie, dass bei einigen Bildern ein Fehler auftritt. Dies liegt daran, dass die Bildbeschriftung nicht generiert wurde oder nicht lang genug ist. Überprüfen Sie jedes Bild mit einem Fehler und geben Sie eine Beschriftung ein, die die Anforderungen erfüllt und das Bild beschreibt.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm11.png){zoomable="yes"}

Sobald alle Bilder Beschriftungen haben, die den Anforderungen entsprechen, müssen Sie dennoch eine Eingabeaufforderung für ein Beispiel angeben. Geben Sie eine Eingabeaufforderung ein, die das Wort „Router“ enthält. Sobald Sie damit fertig sind, können Sie mit dem Training Ihres Modells beginnen. Klicken Sie **Trainieren**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm12.png){zoomable="yes"}

Sie werden es dann sehen. Das Trainieren Ihres Modells kann 20-30 Minuten oder länger dauern.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm13.png){zoomable="yes"}

Nach 20-30 Minuten ist Ihr Modell jetzt trainiert und kann veröffentlicht werden. Klicken Sie auf **Veröffentlichen**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm14.png){zoomable="yes"}

Klicken **erneut auf** Veröffentlichen“.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm15.png){zoomable="yes"}

Schließen Sie das Popup **Benutzerdefiniertes Modell freigeben**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm16.png){zoomable="yes"}

## 1.1.4.3 Benutzerdefiniertes Modell in der Benutzeroberfläche verwenden

Navigieren Sie zu [https://firefly.adobe.com/cme/train](https://firefly.adobe.com/cme/train). Klicken Sie auf das benutzerdefinierte Modell, um es zu öffnen.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm19.png){zoomable="yes"}

Klicken Sie **Vorschau und Test**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm17.png){zoomable="yes"}

Anschließend sehen Sie die Beispielaufforderung, die Sie vor der Ausführung eingegeben haben.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm18.png){zoomable="yes"}

## 1.1.4.4 Benutzerdefiniertes Modell für die Firefly Services Custom Models-API aktivieren

Sobald Ihr benutzerdefiniertes Modell trainiert wurde, kann es auch über die API verwendet werden. In Übung 1.1.1 haben Sie Ihr Adobe I/O-Projekt bereits für die Interaktion mit Firefly Services über die API konfiguriert.

Navigieren Sie zu [https://firefly.adobe.com/cme/train](https://firefly.adobe.com/cme/train). Klicken Sie auf das benutzerdefinierte Modell, um es zu öffnen.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm19.png){zoomable="yes"}

Klicken Sie auf die 3 Punkte **…** und dann auf **Freigeben**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm20.png){zoomable="yes"}

Um auf ein benutzerdefiniertes Firefly-Modell zugreifen zu können, muss das benutzerdefinierte Modell für die E-Mail-Adresse **technischen Kontos** Adobe I/O-Projekts freigegeben werden.

Um Ihre E **Mail zum technischen Konto abzurufen**, navigieren Sie zu [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects). Klicken Sie, um Ihr Projekt mit dem Namen `--aepUserLdap-- One Adobe tutorial` zu öffnen.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm24.png){zoomable="yes"}

Klicken Sie **OAuth Server-zu-Server**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm25.png){zoomable="yes"}

Klicken Sie, um Ihre E **Mail mit dem technischen Konto zu**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm23.png){zoomable="yes"}

Fügen Sie Ihre **E-Mail des technischen Kontos** ein und klicken Sie auf **Zum Bearbeiten einladen**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm21.png){zoomable="yes"}

Das **E-Mail-** des technischen Kontos) sollte jetzt auf das benutzerdefinierte Modell zugreifen können.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm22.png){zoomable="yes"}

## 1.1.4.5 Interaktion mit der Firefly Services Custom Models-API

In Übung 1.1.1 Erste Schritte mit Firefly Services haben Sie diese Datei ([postman-ff.zip](./../../../assets/postman/postman-ff.zip) auf Ihren lokalen Desktop heruntergeladen und anschließend diese Sammlung in Postman importiert.

Öffnen Sie Postman und wechseln Sie zum Ordner **FF - Custom Models API**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm30.png){zoomable="yes"}

Öffnen Sie die Anfrage **1. FF - getCustomModels** und klicken Sie auf **Senden**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm31.png){zoomable="yes"}

Sie sollten das zuvor erstellte benutzerdefinierte Modell, das `--aepUserLdap-- - Citi Signal Router Model` heißt, als Teil der Antwort sehen. Das Feld **assetId** ist die eindeutige Kennung Ihres benutzerdefinierten Modells, auf die bei der nächsten Anfrage verwiesen wird.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm32.png){zoomable="yes"}

Öffnen Sie die Anfrage **2. Bilder asynchron**. In diesem Beispiel fordern Sie zwei Varianten an, die auf Ihrem benutzerdefinierten Modell basieren. Sie können die Eingabeaufforderung aktualisieren, die in diesem Fall `a white router on a volcano in Africa` ist.

Klicken Sie auf **Senden**.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm33.png){zoomable="yes"}

Die Antwort enthält ein Feld **jobId**. Der Vorgang zum Generieren dieser beiden Bilder wird jetzt ausgeführt und Sie können den Status mit der nächsten Anfrage überprüfen.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm34.png){zoomable="yes"}

Öffnen Sie die Anfrage **3. CM-Status abrufen** auf **Senden** klicken. Anschließend sollten Sie sehen, dass der Status auf WIRD AUSGEFÜHRT steht.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm35.png){zoomable="yes"}

Klicken Sie nach einigen Minuten erneut **Senden** für die Anfrage **3. CM-Status**. Anschließend sollten Sie sehen, dass der Status in **Erfolgreich** geändert wurde, und Sie sollten zwei Bild-URLs als Teil der Ausgabe sehen. Klicken, um beide Dateien zu öffnen.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm36.png){zoomable="yes"}

Dies ist das erste Bild, das in diesem Beispiel generiert wurde.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm37.png){zoomable="yes"}

Dies ist das zweite Bild, das in diesem Beispiel generiert wurde.

![Benutzerdefinierte Firefly-Modelle](./images/ffcm38.png){zoomable="yes"}

Sie haben jetzt diese Übung abgeschlossen.

## Nächste Schritte

Wechseln Sie zu [Zusammenfassung und Vorteile](./summary.md){target="_blank"}

Kehren Sie zurück zu [Arbeiten mit Photoshop-APIs](./ex3.md){target="_blank"}

Zurück zu [Übersicht über Adobe Firefly Services](./firefly-services.md){target="_blank"}
