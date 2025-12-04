---
title: Erste Schritte mit Brand Concierge
description: Erste Schritte mit Brand Concierge
kt: 5342
doc-type: tutorial
source-git-commit: ea5fa4694205a94f63d277fdcf2018951fa31fbc
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 1%

---

# 1.4.1 Erste Schritte mit Brand Concierge

## Video

In diesem Video erhalten Sie eine Erklärung und Demonstration aller Schritte, die an dieser Übung beteiligt sind.

## Übersicht über 1.4.1.1 Brand Concierge

Beim Konfigurieren von Brand Concierge werden Sie die beiden folgenden Hauptelemente verwenden:

- **Agent Composer (Konfigurationsebene)**

  Zweck: Die primäre Benutzeroberflächen-Plattform, die zum Erstellen und Konfigurieren von konversativen KI-Erlebnissen verwendet wird.

  Hauptaufgaben:

   - Datenquellen und Wissensdatenbanken definieren und verwalten
   - Festlegen des Markenausdrucks (Ton, Stil, Leitplanken)
   - Einrichten des Meeting-Buchungsagenten

- **Agent Orchestrator (Ausführungs-Engine)**

  Zweck: Die Logik- und Orchestrierungs-Engine, die Benutzeranfragen interpretiert und die entsprechenden Agentenaktionen ausführt.

  Hauptaufgaben:

   - Interpretieren der Benutzerinteressen natürlicher Sprachen
   - Mehrstufige Argumentationspläne generieren und ausführen
   - Auswählen und Aufrufen geeigneter Operatoren/Tools
   - Durchsetzen des Markenkontexts, der Compliance und von Schutzmaßnahmen
   - Koordinieren von Workflows mit mehreren Agenten
   - Aggregieren und Zusammenstellen von Antworten aus mehreren Datenquellen

- **Brand Concierge Conversation Runtime (Service Layer)**

  Zweck: Die Dienstebene für kundenorientierte Gespräche, die Chat-Sitzungen, Kontext und Client-Interaktionen verwaltet.

  Schlüsselkomponenten:

   - Webagent (Client): Browser- oder mobile Chat-Benutzeroberfläche, die mit der Web-SDK integriert ist
   - Conversation Service (Backend): Verwaltet den Sitzungsstatus und fungiert als Orchestrierungs-Gateway

  Hauptaufgaben:

   - Verwalten von Benutzersitzungen und Gesprächstranskripten
   - Benutzerauthentifizierung und Profile verwalten
   - Weiterleiten von Nachrichten zwischen dem Client und der Agent Orchestrator
   - Beibehalten des Konversationskontexts
   - Protokollieren von Verhaltens- und Betriebsereignissen in AEP für Analysen
   - Anwenden von oberflächenspezifischen Konfigurationen

## 1.4.1.2 Brand Concierge-Instanzkonfiguration

Gehen Sie wie folgt vor, um mit der Erstellung Ihrer eigenen Brand Concierge-Instanz zu beginnen.

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Öffnen Sie **Brand Concierge**.

![Brand Concierge](./images/bc1.png)

Sie sollten das dann sehen. Klicken Sie auf das **Sandbox-Auswahl** Menü.

![Brand Concierge](./images/bc2.png)

Wählen Sie die Sandbox aus, die Ihnen zugewiesen wurde. Diese Sandbox sollte `--aepUserLdap-- - bc` benannt werden.

![Brand Concierge](./images/bc3.png)

Klicken Sie **Erste Schritte**.

![Brand Concierge](./images/bc4.png)

Verwenden Sie für den Namen Ihrer Brand Concierge-Instanz: `--aepUserLdap-- - CitiSignal Brand Concierge`.

Geben Sie den folgenden Text unter **Was soll der Concierge tun?** ein.

```javascript
Brand Concierge should help customers find their best device, plan or entertainment deal. Brand Concierge should help users discover internet plans, entertainment deals,  and help find the best available packages. Brand Concierge should also answer questions about devices such as phones and watches.
```

Klicken Sie auf **Erstellen**.

![Brand Concierge](./images/bc5.png)

Sie sollten das dann sehen. Klicken Sie **Erste Schritte** um eine Wissensquelle hinzuzufügen.

![Brand Concierge](./images/bc6.png)

Wählen Sie **Website-Links** aus und klicken Sie auf **Weiter**.

![Brand Concierge](./images/bc7.png)

Sie sollten das dann sehen. Geben Sie `CitiSignal website` als Namen für Ihre Wissensquelle ein.

Sie müssen jetzt eine CSV-Datei hochladen, die die Links Ihrer Website enthält. Laden Sie [CitiSignal Website links CSV-Datei](./assets/citisignal-website-links.csv) auf Ihren Desktop.

Klicken Sie **Dateien durchsuchen**.

![Brand Concierge](./images/bc8.png)

Öffnen Sie die Datei **Citisignal-website-links.csv** und aktualisieren Sie die Links so, dass sie auf Ihre eigene CitiSignal-Website verweisen.

![Brand Concierge](./images/bc8a.png)

Wählen Sie die Datei **Citisignal-website-links.csv** aus, die Sie gerade heruntergeladen und bearbeitet haben. Klicken Sie auf **Öffnen**.

![Brand Concierge](./images/bc9.png)

Ihre Datei wird nun dieser Wissensquelle hinzugefügt. Klicken Sie auf **Hinzufügen**.

![Brand Concierge](./images/bc10.png)

Sie sollten das dann sehen. Klicken Sie auf **Bring me home**.

![Brand Concierge](./images/bc11.png)

Sie sollten das dann sehen. Klicken Sie **&#x200B;**&#x200B;der Karte **Produktberatung für Verbraucher** auf „Erste Schritte“.

![Brand Concierge](./images/bc12.png)

Sie sollten das dann sehen. Füllen Sie die folgenden Felder mithilfe des folgenden Texts aus.

**Was sollte der Concierge über das Produkt oder das Publikum wissen, bevor er Empfehlungen gibt?**

```
CitiSignal is a telecommunications company that sells devices such as phones and watches and that sells internet services such as their lead product CitiSignal Fiber Max. On top of that, CitiSignal sells entertainment services that offer premium streaming services at a discounted price. CitiSignal is targeting these 3 personas primarily: Smart Home Families, Online Gamers and Remote Professionals.
```

**Gibt es Geschäftsregeln oder Einschränkungen, die der Concierge bei der Abgabe von Empfehlungen befolgen sollte?**

```
Prioritize positioning the CitiSignal Fiber Max offering.
```

**Gibt es bestimmte Keywords oder Phrasen, die der Concierge befolgen oder vermeiden sollte?**

```
Competitor pricing, competitor products
```

Ihre Aktualisierungen werden automatisch gespeichert. Klicken Sie auf **Pfeil**, um zum vorherigen Bildschirm zurückzukehren.

![Brand Concierge](./images/bc13.png)

Sie sollten das dann sehen. Klicken Sie **Erste Schritte** um Ihren Markenausdruck anzupassen.

![Brand Concierge](./images/bc14.png)

Sie können auf der Seite „Markenausdruck **Ihre eigenen** treffen und sicherstellen, dass für jede Frage eine Option ausgewählt ist.

![Brand Concierge](./images/bc15.png)

Scrollen Sie nach unten und wählen Sie eine beliebige Einstellung für das Feld **Antwortlänge** aus.

Ihre Aktualisierungen werden automatisch gespeichert.

![Brand Concierge](./images/bc16.png)

Scrollen Sie nach oben und klicken Sie auf den **Pfeil**, um zum vorherigen Bildschirm zurückzukehren.

![Brand Concierge](./images/bc17.png)

Dann bist du wieder hier. Klicken Sie **Wissensquellen**.

![Brand Concierge](./images/bc18.png)

Klicken Sie **Wissensquellen erstellen**.

![Brand Concierge](./images/bc19.png)

Wählen Sie **Produktkatalog** aus und klicken Sie auf **Weiter**.

![Brand Concierge](./images/bc20.png)

Sie sollten das dann sehen. Geben Sie `CitiSignal Products` als Namen für Ihre Wissensquelle ein.

![Brand Concierge](./images/bc21.png)

Sie müssen jetzt eine CSV-Datei hochladen, die die Links Ihrer Website enthält. Laden Sie [CitiSignal Produktkatalog](./assets/CitiSignal-catalog.json.zip) auf Ihren Desktop herunter und entpacken Sie ihn.

![Brand Concierge](./images/bc26.png)

Klicken Sie auf **Dateien durchsuchen** und wählen Sie dann **Durchsuchen auf Ihrem Gerät** aus.

![Brand Concierge](./images/bc22.png)

Wählen Sie die Datei **CitiSignal-catalog.json** aus und klicken Sie auf **Öffnen**.

![Brand Concierge](./images/bc23.png)

Sie sollten das dann sehen. Klicken Sie auf **Hinzufügen**.

![Brand Concierge](./images/bc24.png)

Dann bist du wieder hier.

![Brand Concierge](./images/bc25.png)

Nach 10-20 Minuten sollte **Status** beider Wissensquellen &quot;**&quot;**. Klicken Sie auf **Home**.

![Brand Concierge](./images/bc27.png)

Sie sollten das dann sehen. Klicken Sie auf **+ Verbinden** auf der Karte **Website-Links**.

![Brand Concierge](./images/bc28.png)

Wählen Sie die Wissensquelle **CitiSignal Website** und klicken Sie auf **Speichern**.

![Brand Concierge](./images/bc29.png)

Sie sollten das dann sehen. Klicken Sie auf der Karte **Produktkatalog** auf **+ Verbinden**.

![Brand Concierge](./images/bc30.png)

Wählen Sie die Wissensquelle **CitiSignal Produkte** und klicken Sie auf **Speichern**.

![Brand Concierge](./images/bc31.png)

Sie sollten das dann sehen. Klicken Sie auf **Vorschau**, um mit Ihrer Brand Concierge zu interagieren.

![Brand Concierge](./images/bc32.png)

Sie können jetzt beginnen, Fragen zu den bereitgestellten Wissensquellen zu stellen.

![Brand Concierge](./images/bc33.png)

## Onboarding-Schritte für 1.4.1.3 AEP

Brand Concierge verwendet Adobe Experience Platform, um Interaktionsdaten aus Konversationen zu speichern. Für die Verbindung zwischen Brand Concierge und Experience Platform muss ein Datenstrom konfiguriert und von Brand Concierge verwendet werden.

### Datenstrom

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Öffnen Sie **Experience Platform**.

![Brand Concierge](./images/aep1.png)

Stellen Sie sicher, dass Sie die richtige Sandbox ausgewählt haben, die `--aepUserLdap-- - bc` benannt werden sollte. Scrollen Sie im linken Menü nach unten und wählen Sie **Datenströme**.

![Brand Concierge](./images/aep2.png)

Klicken Sie **Neuer Datenstrom**.

![Brand Concierge](./images/aep3.png)

Geben Sie den **&#x200B;**&#x200B;Datenstromname`--aepUserLdap-- - Brand Concierge` ein und wählen Sie dann die **&#x200B;**&#x200B;Zuordnungsschema`cja-brand-concierge-sb-XXX` aus.

Klicken Sie auf **Speichern**.

![Brand Concierge](./images/aep4.png)

Ihr Datenstrom ist jetzt konfiguriert. Kopieren Sie den Datenstromnamen und die Datenstrom-ID und schreiben Sie sie in einer Textdatei auf Ihrem Computer auf.

![Brand Concierge](./images/aep5.png)

### Brand Concierge-Konfigurationsverwaltungs-API

Der nächste Schritt besteht darin, die Brand Concierge Configuration Management-API zu aktivieren, um den soeben erstellten Datenstrom zu konfigurieren. Dies ist erforderlich, um Dinge wie die IMS-Organisations-ID und Sandbox-Details während der Anfrageverarbeitung aufzulösen.

Dies ist derzeit ein interner Adobe-Schritt, der ausgeführt werden muss. Dieser Schritt ist erforderlich, da andernfalls die Einrichtung des Datenstroms für die Verwendung durch Brand Concierge nicht korrekt ist.

Nächster Schritt: [Implementieren von Brand Concierge auf Ihrer Website](./ex2.md){target="_blank"}

Zurück zu [Brand Concierge](./brandconcierge.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}