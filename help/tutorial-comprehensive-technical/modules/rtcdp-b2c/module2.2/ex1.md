---
title: Intelligente Dienste - Vorbereitung der Customer AI-Daten (Erfassung)
description: Customer AI - Datenvorbereitung (Erfassung)
kt: 5342
doc-type: tutorial
exl-id: 71405859-cfc6-4991-a0b0-11c94818a0fa
source-git-commit: b53ee64ae8438b8f48f842ed1f44ee7ef3e813fc
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 4%

---

# 2.2.1 Customer AI - Datenvorbereitung (Aufnahme)

Damit Intelligent Services Einblicke aus Ihren Marketing-Ereignisdaten gewinnen kann, müssen die Daten semantisch angereichert und in einer Standardstruktur verwaltet werden. Intelligent Services nutzt dazu Adobe Experience-Datenmodell (XDM)-Schemas (XDM).
Insbesondere müssen alle Datensätze, die in Intelligent Services verwendet werden, dem XDM-Schema **Consumer Experience Event** entsprechen.

## Schema erstellen

In dieser Übung erstellen Sie ein Schema, das das **Consumer Experience Event Mixin** enthält, das für den **Customer AI** Intelligent Service erforderlich ist.

Melden Sie sich bei Adobe Experience Platform an, indem Sie diese URL verwenden: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../../datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Nachdem Sie die entsprechende Sandbox ausgewählt haben, wird die Bildschirmänderung angezeigt und Sie befinden sich jetzt in Ihrer dedizierten Sandbox.

![Datenaufnahme](../../datacollection/module1.2/images/sb1.png)

Klicken Sie im linken Menü auf **Schemas** und gehen Sie zu **Durchsuchen**. Klicken Sie auf **Schema erstellen**.

![Neues Schema erstellen](./images/createschemabutton.png)

Wählen Sie im Popup **Manuell** aus und klicken Sie auf **Auswählen**.

![Neues Schema erstellen](./images/schmanual.png)

Wählen Sie als Nächstes **Erlebnisereignis** und klicken Sie auf **Weiter**.

![Neues Schema erstellen](./images/xdmee.png)

Sie müssen jetzt einen Namen für Ihr Schema angeben. Verwenden Sie als Namen für unser Schema Folgendes: `--aepUserLdap-- - Demo System - Customer Experience Event` und klicken Sie auf **Beenden**.

![Neues Schema erstellen](./images/schname.png)

Dann wirst du das sehen. Klicken Sie unter Feldergruppen auf **+ Hinzufügen** .

![Neues Schema erstellen](./images/xdmee1.png)

Suchen Sie nach den folgenden **Feldgruppen**, die Sie diesem Schema hinzufügen möchten, und wählen Sie sie aus:

- Erlebnisereignis für Verbraucher

![Neues CEE-Schema](./images/cee1.png)

- IdentityMap

Klicken Sie auf **Feldgruppen hinzufügen**.

![Neues CEE-Schema](./images/cee2.png)

Dann wirst du das sehen. Wählen Sie anschließend den Namen Ihres Schemas aus. Sie sollten Ihr Schema nun für **Profil** aktivieren, indem Sie auf den Umschalter **Profil** klicken.

![Neues Schema erstellen](./images/xdmee3.png)

Dann wirst du das sehen. Aktivieren Sie das Kontrollkästchen für **Daten für dieses Schema enthält eine primäre Identität im Feld identityMap .**. Klicken Sie auf **Aktivieren**.

![Neues Schema erstellen](./images/xdmee4.png)

Du solltest das jetzt haben. Klicken Sie auf **Speichern** , um Ihr Schema zu speichern.

![Neues Schema erstellen](./images/xdmee5.png)

## Datensatz erstellen

Klicken Sie im linken Menü auf **Datensätze** und gehen Sie zu **Durchsuchen**. Klicken Sie auf **Datensatz erstellen**.

![Datensatz](./images/createds.png)

Klicken Sie auf **Datensatz aus Schema erstellen**.

![Datensatz](./images/createdatasetfromschema.png)

Wählen Sie im nächsten Bildschirm den Datensatz aus, den Sie in der vorherigen Übung erstellt haben, nämlich **[!UICONTROL ldap - Demo System - Customer Experience Event]**. Klicken Sie auf **Weiter**.

![Datensatz](./images/createds1.png)

Verwenden Sie als Namen für Ihren Datensatz `--aepUserLdap-- - Demo System - Customer Experience Event Dataset`. Klicken Sie auf **Fertigstellen**.

![Datensatz](./images/createds2.png)

Ihr Datensatz wurde jetzt erstellt. Aktivieren Sie den Umschalter **Profil** .

![Datensatz](./images/createds3.png)

Klicken Sie auf **Aktivieren**.

![Datensatz](./images/createds4.png)

Sie sollten jetzt Folgendes haben:

![Datensatz](./images/createds5.png)

Sie können jetzt mit der Erfassung von Kundenerlebnis-Ereignisdaten beginnen und mit der Verwendung des Customer AI-Dienstes beginnen.

## Herunterladen von Erlebnisereignistestdaten

Sobald das **Schema** und **Datensatz** konfiguriert sind, können Sie jetzt Erlebnisereignisdaten erfassen. Da Customer AI spezifische Datenanforderungen erfordert, müssen Sie extern vorbereitete Daten erfassen.

Die für die Erlebnisereignisse in dieser Übung vorbereiteten Daten müssen den Anforderungen und dem Schema der [XDM-Feldergruppe für Erlebnisereignisse für Verbraucher](https://github.com/adobe/xdm/blob/797cf4930d5a80799a095256302675b1362c9a15/docs/reference/context/experienceevent-consumer.schema.md) entsprechen.

Laden Sie die ZIP-Datei mit Demodaten von diesem Speicherort herunter: [https://tech-insiders.s3.us-west-2.amazonaws.com/CUSTOM-CAI-EVENTS-WEB.zip](https://tech-insiders.s3.us-west-2.amazonaws.com/CUSTOM-CAI-EVENTS-WEB.zip).

Sie haben jetzt eine Datei mit dem Namen **CUSTOM-CAI-EVENTS-WEB.zip** heruntergeladen. Platzieren Sie die Datei auf dem Desktop des Computers und dekomprimieren Sie sie. Danach wird ein Ordner mit dem Namen **CUSTOM-CAI-EVENTS-WEB** angezeigt.

![Datensatz](./images/ingest.png)

In diesem Ordner finden Sie mehrere sequenzierte JSON-Dateien, die alle in der nächsten Übung erfasst werden müssen.

![Datensatz](./images/ingest1a.png)

## Erlebnisereignis-Testdaten erfassen

Wechseln Sie in Adobe Experience Platform zu **Datensätze** und öffnen Sie den Datensatz mit dem Namen **[!UICONTROL ldap - Demo System - Customer Experience Event Datensatz]**.

![Datensatz](./images/ingest1.png)

Klicken Sie in Ihrem Datensatz auf **Dateien auswählen** , um Daten hinzuzufügen.

![Datensatz](./images/ingest2.png)

Wählen Sie im Popup die Dateien **WEBSITE-EE-1.json** bis **WEBSITE-EE-5.json** aus und klicken Sie auf **Open**.

![Datensatz](./images/ingest3.png)

Wiederholen Sie diesen Aufnahmevorgang für die Dateien **WEBSITE-EE-6.json** und **WEBSITE-EE-7.json**.

Anschließend werden die importierten Daten angezeigt und ein neuer Batch wird im Status **Laden** erstellt. Navigieren Sie nicht von dieser Seite weg, bis die Datei hochgeladen wurde.

![Datensatz](./images/ingest4.png)

Nach dem Hochladen der Datei wird der Batch-Status von **Laden** in **Verarbeitung** geändert.

![Datensatz](./images/ingest5.png)

Die Aufnahme und Verarbeitung der Daten kann 10-20 Minuten dauern.

Sobald die Datenerfassung erfolgreich war, ändert sich der Batch-Status der verschiedenen Uploads in **Erfolg**.

![Datensatz](./images/ingest7.png)

Nächster Schritt: [2.2.2 Customer AI - Erstellen einer neuen Instanz (Konfigurieren)](./ex2.md)

[Zurück zu Modul 2.2](./intelligent-services.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
