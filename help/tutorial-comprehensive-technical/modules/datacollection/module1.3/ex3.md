---
title: Datenerfassung - FAC - Erstellen einer verbundenen Komposition
description: Foundation - FAC - Erstellen einer Verbundzusammensetzung
kt: 5342
doc-type: tutorial
exl-id: 293bf825-d0d6-48cf-9cbf-69f622597678
source-git-commit: e32d415d2997b43834e9fc2495c4394b13f4d49f
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 3%

---

# 1.3.3 Erstellen einer Verbundzusammensetzung

Sie können jetzt Ihre Federated-Audience-Komposition in AEP konfigurieren.

Melden Sie sich über die folgende URL bei Adobe Experience Platform an: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden Sandbox wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten Sandbox.

![Datenaufnahme](./../module1.2/images/sb1.png)

## 1.3.3.1 Zielgruppe erstellen

Gehen Sie im linken Menü zu **Zielgruppen** und dann zu **Verbundkompositionen**. Klicken Sie **Komposition erstellen**.

![FAC](./images/fedcomp1.png)

Verwenden Sie für die Bezeichnung Folgendes: `--aepUserLdap-- - CitiSignal Fiber`. Wählen Sie das Datenmodell aus, das Sie in der vorherigen Übung mit dem Namen `--aepUserLdap-- - CitiSignal Snowflake Data Model` erstellt haben. Klicken Sie auf **Erstellen**.

![FAC](./images/fedcomp2.png)

Sie werden es dann sehen.

![FAC](./images/fedcomp3.png)

Klicken Sie auf das Symbol **+** und dann auf **Zielgruppe erstellen**.

![FAC](./images/fedcomp4.png)

Sie werden es dann sehen. Wählen Sie **Zielgruppe erstellen** aus. Klicken Sie auf das **Suchen**-Symbol, um ein Schema auszuwählen.

![FAC](./images/fedcomp5.png)

Wählen Sie das Schema **—aepUserLdap—_HOUSEHOLDS** aus. Klicken Sie auf **Bestätigen**.

![FAC](./images/fedcomp6.png)

Klicken Sie anschließend auf **Weiter**.

![FAC](./images/fedcomp7.png)

Sie können jetzt mit der Erstellung der Abfrage beginnen, die an Snowflake gesendet wird. Klicken Sie auf das Symbol **+** und dann auf **Benutzerdefinierte Bedingung**.

![FAC](./images/fedcomp8.png)

Wählen Sie das Attribut **ISELIGIBLEFORFIBER** Klicken Sie **Bestätigen**.

![FAC](./images/fedcomp9.png)

Sie werden es dann sehen. Legen Sie das Feld **Wert** auf **True** fest. Klicken Sie **Berechnen**, um die Abfrage an Snowflake zu senden und eine Schätzung der Profile abzurufen, die jetzt qualifiziert sind.

![FAC](./images/fedcomp10.png)

Klicken Sie dann erneut auf das Symbol **+** und anschließend erneut auf **Benutzerdefinierte**), um eine weitere Bedingung hinzuzufügen.

![FAC](./images/fedcomp11.png)

Die zweite hinzuzufügende Bedingung ist: `Is the user an existing CitiSignal Mobile subscriber?`. Die Antwort auf diese Frage ist die Verwendung der Beziehung zwischen dem Haushalt und dem Hauptkunden im Haushalt, die in einer anderen Tabelle definiert ist, **—aepUserLdap—_PERSONS**. Sie können im Attributmenü mithilfe des Links **household2person** einen Drilldown durchführen.

![FAC](./images/fedcomp12.png)

Wählen Sie das Attribut **ISMOBILESUB** aus und klicken Sie auf **Bestätigen**.

![FAC](./images/fedcomp13.png)

Legen Sie das Feld **Wert** erneut auf **True** Klicken Sie **Berechnen** um die Anzahl der Profile zu aktualisieren, die angesprochen werden sollen. Klicken Sie auf **Bestätigen**.

![FAC](./images/fedcomp14.png)

Klicken Sie auf das Symbol **+** und dann auf **Audience speichern**.

![FAC](./images/fedcomp15.png)

Legen Sie die **Zielgruppentitel** auf `--aepUserLdap-- - CitiSignal Eligible for Fiber` fest.

Klicken Sie auf **+ Zielgruppen-Mapping hinzufügen**.

![FAC](./images/fedcomp16.png)

Wählen Sie **HOUSEHOLD_ID** aus und klicken Sie auf **Bestätigen**.

![FAC](./images/fedcomp17.png)

Klicken Sie auf **+ Zielgruppen-Mapping hinzufügen**.

![FAC](./images/fedcomp18.png)

Drilldown durch Klicken auf **Zielgruppendimension**.

![FAC](./images/fedcomp18a.png)

Drilldown durch Klicken auf den Link **household2person**.

![FAC](./images/fedcomp18b.png)

Wählen Sie das Feld **NAME** aus. Klicken Sie auf **Bestätigen**.

![FAC](./images/fedcomp18c.png)

Klicken Sie auf **+ Zielgruppen-Mapping hinzufügen**.

![FAC](./images/fedcomp20.png)

Drilldown durch Klicken auf **Zielgruppendimension**.

![FAC](./images/fedcomp20a.png)

Drilldown durch Klicken auf den Link **household2person**.

![FAC](./images/fedcomp20b.png)

Wählen Sie das Feld **E-MAIL** aus. Klicken Sie auf **Bestätigen**.

![FAC](./images/fedcomp20c.png)

Sie werden es dann sehen. Jetzt müssen Sie das Primäre Identitätsfeld **** auf „Household2person_**&quot;**. Legen Sie **Identity-Namespace** auf **email** fest.

Klicken Sie auf **Speichern**.

![FAC](./images/fedcomp21.png)

Deine Komposition ist jetzt fertig. Klicken Sie auf **Start**, um sie auszuführen.

![FAC](./images/fedcomp21a.png)

Die Abfrage wird jetzt nach unten an Snowflake gesendet, wo die Quelldaten abgefragt werden. Die Ergebnisse werden zurück in AEP verschoben, Quelldaten verbleiben jedoch in Snowflake.

Die Zielgruppe wird jetzt ausgefüllt und die Zielgruppe kann aus dem AEP-Ökosystem heraus angesprochen werden.

![FAC](./images/fedcomp22.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zum Modul 1.3](./fac.md)

[Zurück zu „Alle Module“](../../../overview.md)
