---
title: Einrichten der Grundlage für relationale Daten
description: Einrichten der Grundlage für relationale Daten
kt: 5342
doc-type: tutorial
exl-id: 532e5f2c-971f-488f-bef4-3a8141408cc8
source-git-commit: 4d420ad101c87b58a2bcc425cd4d8da08ad04c8e
workflow-type: tm+mt
source-wordcount: '2051'
ht-degree: 9%

---

# 3.8.1 Einrichten der Grundlage für relationale Daten

Melden Sie sich unter [https://experience.adobe.com](https://experience.adobe.com) bei Adobe Journey Optimizer an. Auf **Journey Optimizer**.

![AJO OC](./images/aechome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`.

![AJO OC](./images/ajohome.png)

## 3.8.1.1 Einrichtung relationaler Schemata

Ein relationales Schema ist die formale Definition des modellbasierten Datenmodells.

Es gibt an:

- Den Satz von Tabellen
- Die Spalten der einzelnen Tabellen
- Die Einschränkungen
- Die Beziehungen zwischen Tabellen

Beim Organisieren von Schemata oder Tabellen in einem modellbasierten Datenmodell geht es um die Strukturierung Ihrer Daten in verschiedenen Tabellen. Stellen Sie sicher, dass in jeder Tabelle ein Entitäts-/Schematyp gespeichert ist.

Bei der Aufnahme von Daten in zur Verwendung mit Adobe Journey Optimizer Orchestered Campaign stehen die folgenden Quellen zur Verfügung:

- Amazon S3
- Google Cloud Storage
- SFTP
- Snowflake
- Google BigQuery
- Data Landing Zone
- Azure Databricks
- Hochladen einer lokalen Datei

Der erste Schritt in dieser Übung ist die Konfiguration Ihrer relationalen XDM-Schemata. Scrollen Sie im linken Menü nach unten zu **Daten-Management** und wählen Sie **Schemata** aus. Klicken Sie auf **+ Schema erstellen**.

![AJO OC](./images/ajoocdata1.png)

Wählen Sie **Relational** aus.

![AJO OC](./images/ajoocdata2.png)

Wählen Sie **DDL-Datei hochladen** und klicken Sie dann auf **Dateien auswählen**.

![AJO OC](./images/ajoocdata3.png)

Laden Sie die Datei [Citisignal_ddl_tables_only.sql](./assets/citisignal_ddl_tables_only.sql) auf Ihren Desktop herunter.

![AJO OC](./images/ajoocdata4.png)

Wählen Sie die **`citisignal_ddl_tables_only.sql`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdata5.png)

Sie sollten das dann sehen. Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdata6.png)

### Identität

Einige Ihrer Schemata enthalten persönliche IDs. Diese Felder sollten als &quot;**&quot; markiert**, und Sie müssen den **Namespace** auswählen, der für diesen bestimmten Identitätstyp gilt.

**`citisignal_accounts`**

Wechseln Sie für dieses Schema zum Feld **account_id** und legen Sie den **identity**-Typ auf **Demo System - CRMID** fest.

![AJO OC](./images/ajoocdata7.png)

**`citisignal_recipients`**

Wechseln Sie für dieses Schema zum Feld **account_id** und legen Sie den Typ **Identity** auf **Demosystem - CRMID** fest. Wechseln Sie dann zum Feld **email** und legen Sie den Typ **Identity** auf **Email** fest.

![AJO OC](./images/ajoocdata8.png)

### Versionierung

Um Aktualisierungen der Daten zu verfolgen, die für diese Schemata aufgenommen werden, muss ein Feld festgelegt werden, das verwendet wird, um die Version der hochgeladenen Daten zu verfolgen. Das Feld, das dafür in all diesen Schemata verwendet wird, ist das Feld **lastModified**, das einen Zeitstempel der hochgeladenen Daten enthält.

Jetzt müssen Sie in jedem dieser Schemata das Kontrollkästchen **Versionierung** für **lastModified** aktivieren.

**`citisignal_products`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata9.png)

**`citisignal_product_bundles`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata10.png)

**`citisignal_product_relationships`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata11.png)

**`citisignal_accounts`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata12.png)

**`citisignal_recipients`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata13.png)

**`citisignal_mobile_subscriptions`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata14.png)

**`citisignal_internet_subscriptions`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata15.png)

**`citisignal_tv_subscriptions`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata16.png)

**`citisignal_equipment_subscriptions`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata17.png)

**`citisignal_mobile_usage_summary`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata18.png)

**`citisignal_internet_usage_summary`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata19.png)

**`citisignal_offers`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata20.png)

**`citisignal_offer_eligibility`**

Aktivieren Sie das Kontrollkästchen für **Versionierung** für das Feld **lastModified**.

![AJO OC](./images/ajoocdata21.png)

### Schemaname

Beim Aufnehmen dieser Schemas für Aktivierungszwecke in einer freigegebenen Sandbox muss der Name jedes Schemas geändert werden, damit es in dieser spezifischen Sandbox eindeutig ist. Der Grund für diese Änderung besteht darin, Konflikte bei der Schemanamen zu vermeiden.

Für dieses Labor sollten Sie Ihren LDAP-Namen vor jedem Schemanamen hinzufügen, was bedeutet, dass jeder Schemaname dieses Präfix aufweisen sollte: `--aepUserLdap--_`

**`citisignal_products`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_products`.

![AJO OC](./images/ajoocdatan9.png)

**`citisignal_product_bundles`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_product_bundles`.

![AJO OC](./images/ajoocdatan10.png)

**`citisignal_product_relationships`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_product_relationships`.

![AJO OC](./images/ajoocdatan11.png)

**`citisignal_accounts`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_accounts`.

![AJO OC](./images/ajoocdatan12.png)

**`citisignal_recipients`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_recipients`.

![AJO OC](./images/ajoocdatan13.png)

**`citisignal_mobile_subscriptions`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_mobile_subscriptions`.

![AJO OC](./images/ajoocdatan14.png)

**`citisignal_internet_subscriptions`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_internet_subscriptions`.

![AJO OC](./images/ajoocdatan15.png)

**`citisignal_tv_subscriptions`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_internet_subscriptions`.

![AJO OC](./images/ajoocdatan16.png)

**`citisignal_equipment_subscriptions`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_equipment_subscriptions`.

![AJO OC](./images/ajoocdatan17.png)

**`citisignal_mobile_usage_summary`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_mobile_usage_summary`.

![AJO OC](./images/ajoocdatan18.png)

**`citisignal_internet_usage_summary`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_internet_usage_summary`.

![AJO OC](./images/ajoocdatan19.png)

**`citisignal_offers`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_offers`.

![AJO OC](./images/ajoocdatan20.png)

**`citisignal_offer_eligibility`**

Ändern Sie den Namen Ihres Schemas in`--aepUserLdap--_ citisignal_offer_eligibility`.

![AJO OC](./images/ajoocdatan21.png)

Ihre Schemata können jetzt gespeichert werden. Klicken Sie auf **Fertig**.

![AJO OC](./images/ajoocdata22.png)

Sie sollten das dann sehen. Klicken Sie auf **Speichern**.

![AJO OC](./images/ajoocdata23.png)

Klicken Sie **Aufträge öffnen**.

![AJO OC](./images/ajoocdata24.png)

Sie sollten das dann sehen. Sie sollten warten, bis der Auftrag erfolgreich abgeschlossen wurde, bevor Sie mit dem nächsten Schritt fortfahren.

![AJO OC](./images/ajoocdata25.png)

Sobald der Auftrag erfolgreich abgeschlossen wurde, können Sie mit dem nächsten Schritt fortfahren. Dies kann 5 bis 10 Minuten dauern.

![AJO OC](./images/ajoocdata26.png)

Nachdem Ihre relationalen XDM-Schemata konfiguriert und Daten aufgenommen wurden, können Sie in der nächsten Übung beginnen, diese Daten zur Erstellung Ihrer orchestrierten Kampagne zu verwenden.

## 3.8.1.2 Datenaufnahme

Navigieren Sie zu **Datensätze**. Anschließend sollte für jedes Schema, das Sie erstellt haben, ein Datensatz angezeigt werden.

![AJO OC](./images/ajoocdata27.png)

Laden Sie die Datei [data.zip](./assets/data.zip) auf Ihren Desktop herunter und entpacken Sie sie.

![AJO OC](./images/ajoocdata28.png)

Öffnen Sie den Ordner **data**. Es sollte eine CSV-Datei für jedes der erstellten Schemata angezeigt werden. Sie müssen diese Daten jetzt in jeden entsprechenden Datensatz hochladen. In diesem Labor werden Sie dies tun, indem Sie eine lokale Datei in jeden Datensatz hochladen.

![AJO OC](./images/ajoocdata29.png)

**`vangeluw_citisignal_products`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_products` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas9a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_products.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas9b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas9c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas9d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas9e.png)

**`vangeluw_citisignal_product_bundles`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_product_bundles` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas10a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_product_bundles.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas10b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas10c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas10d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas10e.png)

**`vangeluw_citisignal_product_relationships`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_product_relationships` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas11a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_product_relationships.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas11b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas11c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas11d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas11e.png)

**`vangeluw_citisignal_accounts`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_accounts` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas12a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_accounts.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas12b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas12c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas12d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas12e.png)

**`vangeluw_citisignal_recipients`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_recipients` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas13a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_recipients.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas13b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas13c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas13d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas13e.png)

**`vangeluw_citisignal_mobile_subscriptions`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_mobile_subscriptions` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas14a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_mobile_subscriptions.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas14b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas14c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas14d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas14e.png)

**`vangeluw_citisignal_internet_subscriptions`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_internet_subscriptions` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas15a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_internet_subscriptions.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas15b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas15c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas15d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas15e.png)

**`vangeluw_citisignal_tv_subscriptions`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_tv_subscriptions` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas16a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_tv_subscriptions.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas16b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas16c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas16d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas16e.png)

**`vangeluw_citisignal_equipment_subscriptions`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_equipment_subscriptions` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas17a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_equipment_subscriptions.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas17b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas17c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas17d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas17e.png)

**`vangeluw_citisignal_mobile_usage_summary`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_mobile_usage_summary` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas18a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_mobile_usage_summary.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas18b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas18c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas18d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas18e.png)

**`vangeluw_citisignal_internet_usage_summary`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_internet_usage_summary` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas19a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_internet_usage_summary.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas19b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas19c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas19d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas19e.png)

**`vangeluw_citisignal_offers`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_offers` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas20a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_offers.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas20b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas20c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas20d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas20e.png)

**`vangeluw_citisignal_offer_eligibility`**

Gehen Sie zu **Quellen**, suchen Sie nach `local` und klicken Sie dann unter **Lokaler Datei** auf **Daten hinzufügen**.

![AJO OC](./images/ajoocdatas10.png)

Aktivieren Sie den Umschalter für **Änderungsdatenerfassung aktivieren**.

Wählen Sie die `vangeluw_citisignal_offer_eligibility` aus.

Klicken Sie auf **Weiter**.

![AJO OC](./images/ajoocdatas21a.png)

Klicken Sie **Dateien auswählen**. Wählen Sie die **`citisignal_offer_eligibility.csv`** aus und klicken Sie auf **Öffnen**.

![AJO OC](./images/ajoocdatas21b.png)

Klicken Sie auf **Weiter**

![AJO OC](./images/ajoocdatas21c.png)

Klicken Sie auf **Fertigstellen**.

![AJO OC](./images/ajoocdatas21d.png)

Nach einigen Minuten können Sie sehen, wie die Daten in Ihren Datensatz aufgenommen werden.

![AJO OC](./images/ajoocdatas21e.png)

Alle Daten werden jetzt aufgenommen.

## 3.8.1.3 Target Dimension

Mit orchestrierten Kampagnen können Sie zielgerichtete Kommunikation auf Entitätsebene entwerfen und bereitstellen und dabei die relationalen Schemafunktionen von Adobe Experience Platform nutzen. Schemata dienen in Experience Platform zur konsistenten und wiederverwendbaren Beschreibung der Struktur von Daten. Wenn Daten in Experience Platform aufgenommen werden, werden sie nach einem XDM-Schema strukturiert.

Obwohl die Segmentierung für orchestrierte Kampagnen hauptsächlich auf relationalen Schemata erfolgt, erfolgt der tatsächliche Nachrichtenversand immer auf Profilebene.

Bei der Konfiguration der Zielgruppenbestimmung definieren Sie zwei wichtige Aspekte:

- Zielgruppenschemata: Sie geben an, welche relationalen Schemata für die Zielgruppenbestimmung geeignet sind. Standardmäßig wird das Schema mit dem Namen „Empfänger“ verwendet, Sie können jedoch Alternativen wie Besucher, Kunden usw. konfigurieren.

- Profilverknüpfung: Das System muss verstehen, wie das Zielschema dem Profilschema zugeordnet ist. Dies wird durch ein gemeinsames Identitätsfeld erreicht, das sowohl im Zielschema als auch im Profilschema vorhanden und als Identity-Namespace konfiguriert ist.

Jetzt müssen Sie Ihre Profil-Zieldimensionen konfigurieren. Wechseln Sie zu **Administration** > **Konfiguration** und klicken Sie dann **Verwalten** unter **Profile Target Dimension**.

![AJO OC](./images/ajoocptd1.png)

Sie sollten das dann sehen. Klicken Sie auf **Erstellen**.

![AJO OC](./images/ajoocptd2.png)

Wählen Sie für **Schema** die Option `--aepUserLdap--_citisignal_accounts` aus. Wählen Sie für **Identitätswert** die Option **account_id** aus.

Klicken Sie auf **Speichern**.

![AJO OC](./images/ajoocptd3.png)

Klicken **erneut auf** Erstellen“.

![AJO OC](./images/ajoocptd4.png)

Wählen Sie für **Schema** die Option `--aepUserLdap--_citisignal_recipients` aus. Wählen Sie für **Identitätswert** die Option **account_id** aus.

Klicken Sie auf **Speichern**.

![AJO OC](./images/ajoocptd5.png)

Klicken **erneut auf** Erstellen“.

![AJO OC](./images/ajoocptd6.png)

Wählen Sie für **Schema** die Option `--aepUserLdap--_citisignal_recipients` aus. Wählen Sie für **Identitätswert** die Option **E-Mail** aus.

Klicken Sie auf **Speichern**.

![AJO OC](./images/ajoocptd7.png)

Sie sollten dann diese haben.

![AJO OC](./images/ajoocptd8.png)

In der nächsten Übung beginnen Sie mit der Verwendung dieser Daten als Teil einer orchestrierten Kampagne.

## Nächste Schritte

Navigieren Sie zu [Erstellen einer orchestrierten Kampagne](./ex2.md){target="_blank"}

Zurück zu [Adobe Journey Optimizer: Orchestrierte Kampagnen](./ajocampaigns.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
