---
title: Datenerfassung - FAC - Erstellen von Schemata, Datenmodellen und Links
description: Foundation - FAC - Erstellen von Schemata, Datenmodellen und Links
kt: 5342
doc-type: tutorial
exl-id: e863ab3a-44df-4bb4-b081-a62616aaa1f1
source-git-commit: 1c91cb2129f827fd39dc065baf5d8ea067a5731a
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 5%

---

# 1.3.2 Erstellen von Schemata, Datenmodellen und Links

Sie können jetzt Ihre Federated Database in AEP konfigurieren.

Melden Sie sich über die folgende URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../module1.2/images/sb1.png)

## 1.3.2.1 Einrichten einer Federated Database in AEP

Klicken Sie **linken Menü auf** Verknüpfte Datenbanken“. Klicken Sie dann auf **Federated Database hinzufügen**.

![FAC](./images/fdb1.png)

Als **label** verwenden Sie `--aepUserLdap-- - CitiSignal Snowflake` und wählen Sie für den Typ **Snowflake**.

Unter „Details“ müssen Sie Ihre Anmeldedaten ausfüllen, die wie folgt aussehen:

![FAC](./images/fdb2.png)

**Server**:

Gehen Sie in Snowflake zu **Admin > Konten**. Klicken Sie auf die 3 **…** neben Ihrem Konto und dann auf **URLs verwalten**.

![FAC](./images/fdburl1.png)

Sie werden es dann sehen. Kopieren Sie die **Aktuelle URL** und fügen Sie sie in das Feld **Server** in AEP ein.

![FAC](./images/fdburl2.png)

**Benutzer**: Der zuvor in Übung 1.3.1.1 erstellte Benutzername
**Password**: Das zuvor in Übung 1.3.1.1 erstellte Kennwort
**Datenbank**: verwenden **CITISIGNAL**

Am Ende sollte es also so sein. Klicken Sie **Verbindung testen**. Wenn der Test erfolgreich ist, klicken Sie auf **Funktionen bereitstellen**, um Funktionen auf der Snowflake zu erstellen, die für die Workflow-Engine erforderlich sind.

Sobald die Verbindung erfolgreich getestet wurde und die Funktionen bereitgestellt sind, wird Ihre Konfiguration gespeichert.

![FAC](./images/fdb3.png)

Wenn Sie dann zurück zum Menü **Federated Datenbanken** gehen, sehen Sie Ihre Verbindung dort.

![FAC](./images/fdb4.png)

## 1.3.2.2 Erstellen von Schemata in AEP

Klicken Sie im linken Menü auf **Modelle** und gehen Sie dann zu **Schemata**. Klicken Sie **Schema erstellen**.

![FAC](./images/fdb5.png)

Wählen Sie Ihre Federated Database aus und klicken Sie auf **+ Tabellen hinzufügen**.

![FAC](./images/fdb6.png)

Sie werden es dann sehen. Wählen Sie die 5 Tabellen aus, die Sie zuvor in Snowflake erstellt haben:

- `CK_HOUSEHOLDS`
- `CK_MOBILE_DATA_USAGE`
- `CK_MONTHLY_DATA_USAGE`
- `CK_PERSONS`
- `CK_USERS`

Klicken Sie auf **Hinzufügen**.

![FAC](./images/fdb7.png)

AEP lädt dann die Informationen der einzelnen Tabellen und zeigt sie in der Benutzeroberfläche an.

Für jede Tabelle können Sie folgende Vorgänge durchführen:

- Ändern des Schema-Labels
- Hinzufügen einer Beschreibung
- Umbenennen aller Felder und Festlegen ihrer Sichtbarkeit
- Primärschlüssel für das Schema auswählen

Für diese Übung sind keine Änderungen erforderlich.

Klicken Sie auf **Erstellen**.

![FAC](./images/fdb8.png)

Sie werden es dann sehen. Sie können auf ein beliebiges Schema klicken und die Informationen überprüfen. Klicken Sie beispielsweise auf **CK_PERSONS**.

![FAC](./images/fdb9.png)

Anschließend sehen Sie dies mit der Möglichkeit, die Konfiguration zu bearbeiten. Klicken Sie **Daten**, um ein Beispiel für die Daten in der Snowflake-Datenbank anzuzeigen.

![FAC](./images/fdb10.png)

Anschließend sehen Sie ein Beispiel der Daten.

![FAC](./images/fdb11.png)

## 1.3.2.3 Erstellen eines Modells in AEP

Gehen Sie im linken Menü zu **Modelle** und dann zu **Datenmodell**. Klicken Sie **Datenmodell erstellen**.

![FAC](./images/fdb12.png)

Verwenden Sie für die Bezeichnung `--aepUserLdap-- - CitiSignal Snowflake Data Model`. Klicken Sie auf **Erstellen**.

![FAC](./images/fdb13.png)

Klicken Sie **Schemata hinzufügen**.

![FAC](./images/fdb14.png)

Wählen Sie Ihre Schemata aus und klicken Sie auf **Hinzufügen**.

![FAC](./images/fdb15.png)

Sie werden es dann sehen. Klicken Sie auf **Speichern**.

Sie können jetzt mit der Definition von Links zwischen Schemata beginnen. Um einen Link zu definieren, klicken Sie auf **Links erstellen**.

![FAC](./images/fdb16.png)

Definieren wir zunächst die Relation zwischen dem `CK_USERS` und dem `CK_PERSONS`.

Klicken Sie auf **Hinzufügen**.

![FAC](./images/fdb18.png)

Dann bist du wieder hier. Klicken Sie auf **Links erstellen**, um einen weiteren Link zu erstellen.

![FAC](./images/fdb17.png)

Als Nächstes definieren wir die Relation zwischen dem `CK_HOUSEHOLDS` und dem `CK_PERSONS`.

![FAC](./images/fdb19.png)

Dann bist du wieder hier. Klicken Sie auf **Links erstellen**, um einen weiteren Link zu erstellen.

![FAC](./images/fdb20.png)

Als Nächstes definieren wir die Relation zwischen dem `CK_MONTHLY_DATA_USAGE` und dem `CK_USERS`.

![FAC](./images/fdb21.png)

Dann bist du wieder hier. Klicken Sie auf **Links erstellen**, um einen weiteren Link zu erstellen.

![FAC](./images/fdb22.png)

Als Nächstes definieren wir die Relation zwischen dem `CK_USERS` und dem `CK_HOUSEHOLDS`.

![FAC](./images/fdb23.png)

Dann bist du wieder hier. Klicken Sie **Speichern**.
![FAC](./images/fdb24.png)

Die Einrichtung in AEP ist jetzt abgeschlossen. Sie können jetzt mit der Verwendung Ihrer Federated Data in einer Federated-Audience-Komposition beginnen.

Nächster Schritt: [1.3.3 Erstellen einer Federated Composition](./ex3.md)

[Zurück zum Modul 1.3](./fac.md)

[Zurück zu „Alle Module“](../../../overview.md)
