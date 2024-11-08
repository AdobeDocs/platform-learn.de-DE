---
title: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln - Senden Sie Ihr Segment an ein S3-Ziel
description: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Handeln - Senden Sie Ihr Segment an ein S3-Ziel
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 5%

---

# 2.3.4 Aktion ausführen: Senden Sie Ihr Segment an ein S3-Ziel

Adobe Experience Platform kann auch Audiences für E-Mail-Marketing-Ziele wie Salesforce Marketing Cloud, Oracle Eloqua, Oracle Responsys und Adobe Campaign freigeben.

Sie können FTP oder SFTP als Teil der dedizierten Ziele für jedes dieser E-Mail-Marketing-Ziele verwenden oder AWS S3 verwenden, um Kundenlisten zwischen Adobe Experience Platform und diesen E-Mail-Marketing-Zielen auszutauschen.

In diesem Modul konfigurieren Sie ein solches Ziel, indem Sie einen AWS S3-Bucket verwenden.

## 2.3.4.1 S3-Behälter erstellen

Wechseln Sie zu [https://console.aws.amazon.com](https://console.aws.amazon.com) und melden Sie sich mit dem zuvor erstellten Amazon-Konto an.

![ETL](./images/awshome.png)

Nach der Anmeldung werden Sie zur **AWS Management Console** weitergeleitet.

![ETL](./images/awsconsole.png)

Suchen Sie im Menü **Dienste suchen** nach **s3**. Klicken Sie auf das erste Suchergebnis: **S3 - Skalierbarer Speicher in der Cloud**.

![ETL](./images/awsconsoles3.png)

Dann sehen Sie die Homepage von **Amazon S3**. Klicken Sie auf **Behälter erstellen**.

![ETL](./images/s3home.png)

Im Bildschirm **Behälter erstellen** müssen Sie zwei Elemente konfigurieren:

- Name: Verwenden Sie den Namen `aepmodulertcdp--aepUserLdap--`. Beispiel: In dieser Übung lautet der Behältername **aepmodulertcdpvangeluw**
- Region: Region **EU (Frankfurt) eu-central-1**

![ETL](./images/bucketname.png)

Behalten Sie alle anderen Standardeinstellungen bei. Scrollen Sie nach unten und klicken Sie auf **Bucket erstellen**.

![ETL](./images/createbucket.png)

Sie werden sehen, wie Ihr Bucket erstellt wird und zur Amazon S3-Homepage weitergeleitet wird.

![ETL](./images/S3homeb.png)

## 2.3.4.2 Berechtigungen für den Zugriff auf Ihren S3-Behälter festlegen

Der nächste Schritt besteht darin, den Zugriff auf Ihren S3-Bucket einzurichten.

Gehen Sie dazu zu [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home).

Der Zugriff auf AWS-Ressourcen wird über die Amazon Identity and Access Management (IAM) gesteuert.

Sie werden jetzt diese Seite sehen.

![ETL](./images/iam.png)

Klicken Sie im linken Menü auf **Benutzer**. Daraufhin wird der Bildschirm **Benutzer** angezeigt. Klicken Sie auf **Benutzer hinzufügen**.

![ETL](./images/iammenu.png)

Konfigurieren Sie dann Ihren Benutzer:

- Benutzername: Verwenden Sie `s3_--aepUserLdap--_rtcdp` als Namen, in diesem Beispiel also den Namen `s3_vangeluw_rtcdp`.
- AWS-Zugriffstyp: Wählen Sie **Zugriffsschlüssel - Programmatischer Zugriff** aus.

Klicken Sie auf **Weiter: Berechtigungen**.

![ETL](./images/configuser.png)

Dann sehen Sie diesen Berechtigungsbildschirm. Klicken Sie auf **Vorhandene Richtlinien direkt anhängen**.

![ETL](./images/perm1.png)

Geben Sie den Suchbegriff **s3** ein, um alle zugehörigen S3-Richtlinien anzuzeigen. Wählen Sie die Richtlinie **AmazonS3FullAccess** aus. Klicken Sie auf **Weiter: Tags**.

![ETL](./images/perm2.png)

Auf dem Bildschirm **Tags** müssen Sie nichts konfigurieren. Klicken Sie auf **Weiter: Überprüfen Sie**.

![ETL](./images/perm3.png)

Überprüfen Sie Ihre Konfiguration. Klicken Sie auf **Benutzer erstellen**.

![ETL](./images/review.png)

Ihr Benutzer wurde erstellt und Sie sehen Ihre Anmeldedaten für den Zugriff auf Ihre S3-Umgebung. Dies ist das einzige Mal, dass Sie Ihre Anmeldedaten sehen. Schreiben Sie sie daher bitte auf.

![ETL](./images/cred.png)

Klicken Sie auf **Anzeigen** , um Ihren geheimen Zugriffsschlüssel anzuzeigen:

![ETL](./images/cred1.png)

>[!IMPORTANT]
>
>Speichern Sie Ihre Anmeldedaten in einer Textdatei auf Ihrem Computer.
>
> - Zugriffsschlüssel-ID: ...
> - Geheimer Zugriffsschlüssel: ...
>
> Wenn Sie auf **Schließen** klicken, werden Sie Ihre Anmeldedaten nie mehr sehen!

Klicken Sie auf **Schließen**.

![ETL](./images/close.png)

Sie haben jetzt erfolgreich einen AWS S3-Bucket erstellt und einen Benutzer mit Zugriffsberechtigungen für diesen Bucket erstellt.

## 2.3.4.3 Ziel in Adobe Experience Platform konfigurieren

Wechseln Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxName--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende [!UICONTROL Sandbox] ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Wechseln Sie im linken Menü zu **Ziele** und gehen Sie dann zu **Katalog**. Daraufhin wird der **Zielkatalog** angezeigt.

![RTCDP](./images/rtcdpmenudest.png)

Klicken Sie auf **Cloud-Speicher** und dann auf der Karte **Amazon S3** auf die Schaltfläche **Einrichten** (oder je nach Umgebung auf **Segmente aktivieren** ).

![RTCDP](./images/rtcdp2.png)

Abhängig von Ihrer Umgebung müssen Sie möglicherweise auf **+ Neues Ziel konfigurieren** klicken, um Ihr Ziel zu erstellen.

![RTCDP](./images/rtcdp2a.png)

Wählen Sie als Kontotyp **Neues Konto** aus. Bitte verwenden Sie die S3-Anmeldeinformationen, die Ihnen im vorherigen Schritt zugewiesen wurden:

| Zugriffsschlüssel-ID | Geheimer Zugriffsschlüssel |
|:-----------------------:| :-----------------------:|
| AKIA... | CM5Ln.... |

Klicken Sie auf **Mit Ziel verbinden**.

![RTCDP](./images/rtcdpsfs3.png)

Daraufhin wird eine visuelle Bestätigung angezeigt, dass dieses Ziel jetzt verbunden ist.

![RTCDP](./images/rtcdpsfs3connected.png)

Sie müssen einen Namen und einen Ordner angeben, damit Adobe Experience Platform eine Verbindung zum S3-Bucket herstellen kann.

Verwenden Sie als Namenskonvention Folgendes:

| Zugriffsschlüssel-ID | Geheimer Zugriffsschlüssel |
|:-----------------------:| :-----------------------:|
| Name | `AWS - S3 - --aepUserLdap--` |
| Beschreibung | `AWS - S3 - --aepUserLdap--` |
| Behältername | `aepmodulertcdp--aepUserLdap--` |
| Ordnerpfad | / |

Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpsfs3connect2.png)

Sie können jetzt optional eine Data Governance-Richtlinie an Ihr neues Ziel anhängen. Klicken Sie auf **Weiter**.

![RTCDP](./images/rtcdpsfs3connect2gov.png)

Suchen Sie in der Segmentliste nach dem Segment, das Sie in Übung 1 erstellt haben, und wählen Sie es aus. Klicken Sie auf **Weiter**.

![RTCDP](./images/s3a.png)

Dann wirst du das sehen. Wenn Sie möchten, können Sie den Zeitplan bearbeiten, indem Sie auf das Symbol **Stift** klicken. **Zeitplan erstellen**.

![RTCDP](./images/s3bb.png)

Definieren Sie Ihren Zeitplan Ihrer Wahl. Wählen Sie **Inkrementelle Dateien exportieren** und legen Sie die Häufigkeit auf **Stündlich** alle **3 Stunden** fest. Klicken Sie auf **Erstellen**.

![RTCDP](./images/s3bbc.png)

Dann wirst du das haben. Klicken Sie auf **Weiter**.

![RTCDP](./images/s3bbca.png)

Sie können jetzt Attribute für den Export in AWS S3 auswählen. Klicken Sie auf **Neues Feld hinzufügen** und stellen Sie sicher, dass das Feld `--aepTenantId--.identification.core.ecid` hinzugefügt und als **Deduplizierungsschlüssel** markiert ist.

Optional können Sie beliebig viele weitere Felder hinzufügen.

Nachdem Sie alle Felder hinzugefügt haben, klicken Sie auf **Weiter**.

![RTCDP](./images/s3c.png)

Überprüfen Sie Ihre Konfiguration. Klicken Sie auf **Beenden** , um die Konfiguration abzuschließen.

![RTCDP](./images/s3g.png)

Sie sind dann wieder im Bildschirm Zielaktivierung und Ihr Segment wird diesem Ziel hinzugefügt.

![RTCDP](./images/s3j.png)

Wenn Sie weitere Segmentexporte hinzufügen möchten, können Sie auf **Segmente aktivieren** klicken, um den Prozess neu zu starten und weitere Segmente hinzuzufügen.

![RTCDP](./images/s3k.png)

Nächster Schritt: [2.3.5 Aktion ausführen: Segment an Adobe Target senden](./ex5.md)

[Zurück zu Modul 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
