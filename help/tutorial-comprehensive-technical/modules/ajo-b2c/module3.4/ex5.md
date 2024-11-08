---
title: Adobe Journey Optimizer - Geschäftsereignisse
description: In diesem Abschnitt wird erläutert, wie Sie die Funktion für Geschäftsereignisse verwenden können, um einen "Artikel wieder auf Lager"Anwendungsfall auszuführen
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 8%

---

# 3.4.5 Geschäftsereignis-Journey erstellen

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud](https://experience.adobe.com) wechseln. Klicken Sie auf **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

Sie werden zur Ansicht **Home** in Journey Optimizer weitergeleitet. Vergewissern Sie sich zunächst, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Um von einer Sandbox zu einer anderen zu wechseln, klicken Sie auf **PRODUKTIONSPROD (VA7)** und wählen Sie die Sandbox aus der Liste aus. In diesem Beispiel erhält die Sandbox den Namen **AEP-Aktivierung FY22**. Sie befinden sich dann in der Ansicht **Home** Ihrer Sandbox `--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

## 3.4.5.1 Geschäftsereignis erstellen

Klicken Sie im linken Menü auf **Konfigurationen**. Klicken Sie auf die Schaltfläche **Verwalten** in der Karte **Ereignisse** .

![Journey Optimizer](./images/be1.png)

Geschäftsereignisse sind ein neuer Ereignistyp, den Sie in Journey Optimizer erstellen können. Im Gegensatz zu den **Einzelereignissen** , die Sie in vorherigen Modulen erstellt haben, werden die Geschäftsereignisse nicht vom Kunden, sondern vom Unternehmen ausgelöst. Jetzt erstellen Sie Ihr Geschäftsereignis.

Klicken Sie auf **Ereignis erstellen**.

![Journey Optimizer](./images/be2.png)

Geben Sie die folgenden Werte in das Formular Ereigniserstellung ein:

- **Name**: `--aepUserLdap--ItemBackInStock`. Beispiel: **vangeluwItemBackInStock**
- **Beschreibung**: Dieses Ereignis wird ausgelöst, wenn ein Produkt wieder auf Lager ist
- **Typ**: Wählen Sie **Unternehmen** in der Dropdown-Liste aus.

![Journey Optimizer](./images/evde.png)

Wählen Sie für das Schema **Demo-System - Ereignisschema für JO Business Events (Global v1.1) v.1**. Jetzt müssen Sie die Felder im Schema auswählen, die Sie für unseren Anwendungsfall benötigen.

![Journey Optimizer](./images/evdes.png)

Führen Sie folgende Schritte aus:

Klicken Sie auf das Symbol **Stift** im Feld, in dem das Feld **1 Feld ausgewählt ist**.

![Journey Optimizer](./images/23.8-4.png)

Wählen Sie alle verfügbaren Felder im Schema aus und klicken Sie dann auf **OK**.

![Journey Optimizer](./images/23.8-5.png)

Für die Bedingung: Sie müssen angeben, welche Datensätze in diesem Schema das Geschäftsereignis auslösen sollen.

Führen Sie folgende Schritte aus:

Klicken Sie auf das Symbol **Stift** im Feld, in dem die Meldung **Bedingung hinzufügen** angezeigt wird.

![Journey Optimizer](./images/23.8-6.png)

Erweitern Sie auf der linken Seite das Objekt `--aepTenantId--` , erweitern Sie das Objekt **joBusinessEvents** und ziehen Sie das Feld **eventName** auf die Arbeitsfläche.

![Journey Optimizer](./images/23.8-7.png)

Geben Sie für das Feld **eventName** den folgenden Wert ein: `--aepUserLdap--ItemBackInStock`. Beispiel: vangeluwItemBackInStock.
Klicken Sie auf **OK**.

![Journey Optimizer](./images/23.8-8.png)

Klicken Sie auf **OK**.

![Journey Optimizer](./images/23.8-9.png)

Schließlich sollte Ihr Formular zur Ereigniserstellung wie folgt aussehen: Klicken Sie auf **Speichern** , um Ihr Geschäftsereignis zu speichern.

![Journey Optimizer](./images/23.8-10.png)

## 3.4.5.2 Geschäftsereignis-Journey erstellen

Sie können dieses Geschäftsereignis und die Nachricht jetzt in einer Journey nutzen. Wechseln Sie zu **Journey**. Klicken Sie auf **Journey erstellen**.

![Journey Optimizer](./images/bej10.png)

Auf der rechten Seite sehen Sie ein Formular, in dem Sie den Journey-Namen und die Beschreibung angeben müssen. Geben Sie die folgenden Werte ein:

- **Name**: `--aepUserLdap-- - Item back in stock journey`. Beispiel: vangeluw - Artikel wieder in Journey
- **Beschreibung**: Diese Journey sendet eine SMS, wenn ein Artikel wieder auf Lager ist, an Besucher, die Interesse gezeigt haben.

Klicken Sie auf **OK**.

![Journey Optimizer](./images/bej11.png)

Suchen Sie im linken Menü unter **Ereignisse** nach Ihrem ldap. Sie finden das zuvor erstellte Geschäftsereignis `--aepUserLdap--ItemBackInStock`. Ziehen Sie dieses Ereignis auf die Arbeitsfläche, da dies der Ausgangspunkt der Journey sein wird.

![Journey Optimizer](./images/bej12.png)

Wie Sie sehen können, wurde der Arbeitsfläche automatisch die Aktivität **Segment lesen** hinzugefügt. Dies liegt daran, dass die Geschäftsereignisse nur einen Trigger senden, damit der Journey ein bestimmtes Segment liest, wodurch die Profilliste für diese Journey abgerufen wird.

Klicken Sie auf die Aktivität **Segment lesen** .
Die Konfiguration **Segment lesen** erwartet, dass Sie das Segment auswählen, das Sie über das gerade eingetretene Geschäftsereignis benachrichtigen möchten. Klicken Sie auf das Feld **Segment auswählen** .

![Journey Optimizer](./images/bej13.png)

Suchen Sie im Popup **Segment auswählen** nach Ihrem ldap und wählen Sie das Segment aus, das Sie in [Modul 2.3 - Echtzeit-Kundendatenplattform - Erstellen eines Segments erstellt haben. Nehmen Sie die Aktion](./../../../modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md) mit dem Namen `--aepUserLdap-- - Interest in PROTEUS FITNESS JACKSHIRT` vor. Beispiel: vangeluw - Interesse an PROTEUS FITNESS JACKSHIRT. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/bej14.png)

Klicken Sie anschließend auf **OK**.

![Journey Optimizer](./images/bej15.png)

Der nächste Schritt besteht darin, die gewünschte Aktion per Drag-and-Drop in diese Journey zu ziehen. Wählen Sie die Aktion **SMS** aus und ziehen Sie sie nach der soeben hinzugefügten Bedingung per Drag-and-Drop.

![Demo](./images/jop9.png)

Setzen Sie die **Kategorie** auf **Marketing** und wählen Sie eine SMS-Oberfläche aus, über die Sie SMS senden können. In diesem Fall ist die auszuwählende E-Mail-Oberfläche **SMS**.

![ACOP](./images/journeyactions1x.png)

Der nächste Schritt besteht darin, Ihre Nachricht zu erstellen. Klicken Sie dazu auf **Inhalt bearbeiten**.

![ACOP](./images/journeyactions2x.png)

Jetzt wird das Nachrichten-Dashboard angezeigt, in dem Sie den Text Ihrer SMS konfigurieren können. Klicken Sie auf den Bereich **Nachricht erstellen** , um Ihre Nachricht zu erstellen.

![Journey Optimizer](./images/sms3.png)

Geben Sie den folgenden Text ein: `Hi {{profile.person.name.firstName}}, the Proteus Fitness Jackshirt is back in stock at Luma.`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/sms4.png)

Gehen Sie zurück zum Nachrichten-Dashboard, indem Sie in der oberen linken Ecke auf den Pfeil **11} neben dem Betreffzeilentext klicken.**

![Journey Optimizer](./images/oc79xx.png)

Jetzt sehen Sie Ihre abgeschlossene SMS-Aktion. Klicken Sie auf **OK**.

![Journey Optimizer](./images/oc79xxy.png)

Ihre Journey kann jetzt veröffentlicht werden. Klicken Sie auf **Veröffentlichen**.

![Journey Optimizer](./images/jop13.png)

Klicken Sie erneut auf **Publish**.

![Journey Optimizer](./images/jop14.png)

Ihre Journey ist jetzt veröffentlicht, können Sie sie jetzt testen!

![Journey Optimizer](./images/jop15.png)

## 3.4.5.3 Geschäftsereignis testen Journey

Sie simulieren jetzt die Neuvorgabe eines Produkts, indem Sie ein neues Ereignis mit Postman im Format **Demo-System - Ereignisschema für JO-Geschäftsereignisse (Global v1.1) v.1** aufrufen.

Klicken Sie im linken Menü auf **Quellen** und dann auf die Registerkarte **Konten**.

![Journey Optimizer](./images/s1.png)

Auf der Registerkarte **Konten** finden Sie das Konto mit dem Namen **Journey Optimizer Business Events**. Klicken Sie darauf, um es zu öffnen.

![Journey Optimizer](./images/s2.png)

Dieses Konto hat nur einen Datenfluss, klicken Sie auf den Namen des Datenflusses, um ihn auszuwählen.

![Journey Optimizer](./images/s3.png)

Klicken Sie im rechten Menü auf **Schema-Payload kopieren** . Mit dieser Option wird der gesamte Befehl **curl** kopiert, um einen Datensatz mit dem Befehl **Demo System - Event Schema for JO Business Events (Global v1.1) v.1** in die Zwischenablage einzufügen.

![Journey Optimizer](./images/s4.png)

Fügen Sie den Befehl &quot;Curl&quot;in einen Texteditor ein.

![Journey Optimizer](./images/s5.png)

Sehen wir uns diese Anfrage genauer an,

- Die POST-Anfrage wird an die DCS-Inlet-ID gesendet
- Die Anfrage verweist auf das Schema, den Datensatz und die Organisations-ID.
- Schließlich enthält es den Knoten xdmEntity , der die Daten darstellt, die wir im Datensatz erstellen möchten.

Sie müssen nun die folgende `xdmEntity` -Zeile ersetzen..

```json
"xdmEntity": {
  "_experienceplatform": {
    "joBusinessEvents": {
      "eventDescription": "string",
      "eventName": "string",
      "stockEventId": "string"
    }
  },
  "_id": "/uri-reference",
  "eventType": "advertising.completes",
  "timestamp": "2018-11-12T20:20:39+00:00"
}
```

... überprüfen Sie in dieser Zeile das Feld eventName wie `--aepUserLdap--ItemBackInStock`, das die Bedingung darstellt, die Sie in Ihrem Geschäftsereignis für den Trigger Ihrer Journey angegeben haben.

```json
"xdmEntity": {
  "_experienceplatform": {
    "joBusinessEvents": {
      "eventDescription": "Product Proteus Fitness Jackshirt is back in stock",
      "eventName": "--aepUserLdap--ItemBackInStock",
      "stockEventId": "1"
    }
  },
  "_id": "/uri-reference",
  "eventType": "productBackInStock",
  "timestamp": "2021-04-19T15:25:39+00:00"
}
```

Der aktualisierte Befehl **curl** sollte wie folgt aussehen:

![Journey Optimizer](./images/s6.png)

Wählen Sie alles aus und kopieren Sie es in die Zwischenablage.

Öffnen Sie Postman. Klicken Sie auf der linken Seite von Postman auf **Importieren**.

![Journey Optimizer](./images/23.8-46.png)

Wählen Sie die Registerkarte **Rohtext** aus und fügen Sie den zuvor kopierten Befehl ein. Klicken Sie auf **Weiter**.

![Journey Optimizer](./images/s7.png)

Klicken Sie auf **Importieren**.

![Journey Optimizer](./images/23.8-50.png)

Postman hat den Befehl **curl** automatisch in einen REST-Befehl konvertiert, der ausgelöst werden kann. Drücken Sie einfach die Schaltfläche **Senden** , um die Erstellung dieses Datensatzes im Datensatz anzufordern.

![Journey Optimizer](./images/23.8-51.png)

Überprüfen Sie, ob Ihre Anfrage erfolgreich empfangen wurde. Suchen Sie in Postman nach dem Status &quot;**200 OK**&quot;.

![Journey Optimizer](./images/s8.png)

Es kann einige Minuten dauern, bis die SMS auf Ihrem Mobiltelefon ankommt. Ist dies nicht der Fall, enthält Ihr Segment **Interesse an Proteus Fitness Jackshirt** möglicherweise kein Profil mit einem korrekten Mobiltelefon. Wenn ja, besuchen Sie die Luma-Website, besuchen Sie das Produkt **Proteus Fitness Jackshirt** und registrieren Sie sich, während Sie sicherstellen, dass Sie die richtige Mobiltelefonnummer angeben.

![Journey Optimizer](./images/s9.png)

Du bist jetzt mit dieser Übung fertig.

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 3.4](./journeyoptimizer.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
