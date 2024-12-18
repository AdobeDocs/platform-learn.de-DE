---
title: Intelligente Dienste - Vorbereitung der Customer AI-Daten (Erfassung)
description: Customer AI - Datenvorbereitung (Erfassung)
kt: 5342
doc-type: tutorial
exl-id: 71405859-cfc6-4991-a0b0-11c94818a0fa
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 5%

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
- Details zur Endbenutzer-ID

Klicken Sie auf **Feldgruppen hinzufügen**.

![Neues CEE-Schema](./images/cee.png)

Dann wirst du das sehen. Klicken Sie auf die Feldergruppe **Endbenutzer-ID-Details**.

![Neues Schema erstellen](./images/eui1.png)

Navigieren Sie zum Feld **endUserIDs ._experience.emailid.id**.

![Neues Schema erstellen](./images/eui2.png)

Im rechten Menü für das Feld **endUserIDs._experience.emailid.id**, scrollen Sie nach unten und aktivieren Sie das Kontrollkästchen für **Identität**, aktivieren Sie das Kontrollkästchen für **Primäre Identität** und wählen Sie den **Identitäts-Namespace** von **E-Mail** aus. Klicken Sie auf **Übernehmen**.

![Neues Schema erstellen](./images/eui3.png)

Navigieren Sie zum Feld **endUserIDs ._experience.mcid.id**. Aktivieren Sie das Kontrollkästchen für **Identität** und wählen Sie den **Identitäts-Namespace** von **ECID** aus. Klicken Sie auf **Übernehmen**.

![Neues Schema erstellen](./images/eui4.png)

Dann wirst du das haben. Wählen Sie anschließend den Namen Ihres Schemas aus. Sie sollten Ihr Schema nun für **Profil** aktivieren, indem Sie auf den Umschalter **Profil** klicken.

![Neues Schema erstellen](./images/xdmee3.png)

Dann wirst du das sehen. Klicken Sie auf **Aktivieren**.

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

Sobald das **Schema** und **Datensatz** konfiguriert sind, können Sie jetzt Erlebnisereignisdaten erfassen. Da Customer AI Daten über **2 Quartale mindestens** benötigt, müssen Sie extern vorbereitete Daten erfassen.

Die für die Erlebnisereignisse vorbereiteten Daten müssen den Anforderungen und dem Schema des [XDM-Mixins für Erlebnisereignisse für Verbraucher](https://github.com/adobe/xdm/blob/797cf4930d5a80799a095256302675b1362c9a15/docs/reference/context/experienceevent-consumer.schema.md) entsprechen.

Laden Sie die Datei mit Beispieldaten von diesem Speicherort herunter: [https://dashboard.adobedemo.com/data](https://dashboard.adobedemo.com/data). Klicken Sie auf die Schaltfläche **Herunterladen** .

![Datensatz](./images/dsn1.png)

Wenn Sie nicht auf den obigen Link zugreifen können, können Sie die Datei auch von diesem Speicherort herunterladen: [https://aepmodule10.s3-us-west-2.amazonaws.com/retail-v1-dec2020-xl.json.zip](https://aepmodule10.s3-us-west-2.amazonaws.com/retail-v1-dec2020-xl.json.zip).

Sie haben jetzt eine Datei mit dem Namen **retail-v1-dec2020-xl.json.zip** heruntergeladen. Platzieren Sie die Datei auf dem Desktop des Computers und dekomprimieren Sie sie. Danach wird eine Datei mit dem Namen **retail-v1.json** angezeigt. Sie werden diese Datei in der nächsten Übung benötigen.

![Datensatz](./images/ingest.png)

## Erlebnisereignis-Testdaten erfassen

Wechseln Sie in Adobe Experience Platform zu **Datensätze** und öffnen Sie den Datensatz mit dem Namen **[!UICONTROL ldap - Demo System - Customer Experience Event Datensatz]**.

![Datensatz](./images/ingest1.png)

Klicken Sie in Ihrem Datensatz auf **Dateien auswählen** , um Daten hinzuzufügen.

![Datensatz](./images/ingest2.png)

Wählen Sie im Popup die Datei &quot;**retail-v1.json**&quot;aus und klicken Sie auf &quot;**Open**&quot;.

![Datensatz](./images/ingest3.png)

Anschließend werden die importierten Daten angezeigt und ein neuer Batch wird im Status **Laden** erstellt. Navigieren Sie nicht von dieser Seite weg, bis die Datei hochgeladen wurde.

![Datensatz](./images/ingest4.png)

Nach dem Hochladen der Datei wird der Batch-Status von **Laden** in **Verarbeitung** geändert.

![Datensatz](./images/ingest5.png)

Die Aufnahme und Verarbeitung der Daten kann 10-20 Minuten dauern.

Sobald die Datenerfassung erfolgreich war, ändert sich der Batch-Status in **Erfolg**.

![Datensatz](./images/ingest7.png)

![Datensatz](./images/ingest8.png)

Nächster Schritt: [2.2.2 Customer AI - Erstellen einer neuen Instanz (Konfigurieren)](./ex2.md)

[Zurück zu Modul 2.2](./intelligent-services.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
