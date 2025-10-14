---
title: GenStudio for Performance Marketing Erstellen eines Amazon AWS S3-Buckets
description: GenStudio for Performance Marketing Erstellen eines Amazon AWS S3-Buckets
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 044677e4-7ca3-4dfe-9067-640983681ea7
source-git-commit: 1f9a868c5e4ef4aa0e09d7f5d73a951006ee6c5a
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 7%

---

# 1.6.2 AWS S3-Bucket erstellen

## 1.6.2.1 Erstellen eines S3-Buckets

Wechseln Sie zu [https://console.aws.amazon.com](https://console.aws.amazon.com) und melden Sie sich an.

>[!NOTE]
>
>Wenn Sie noch kein AWS-Konto haben, erstellen Sie bitte mit Ihrer persönlichen E-Mail-Adresse ein neues AWS-Konto.

![ETL](./images/awshome.png)

Nach der Anmeldung werden Sie zur **AWS Management Console** weitergeleitet.

![ETL](./images/awsconsole.png)

Suchen Sie in der Suchleiste nach **s3**. Klicken Sie auf das erste Suchergebnis: **S3 - Scalable Storage in the Cloud**.

![ETL](./images/awsconsoles3.png)

Anschließend wird die Startseite von **Amazon S3** angezeigt. Klicken Sie **Bucket erstellen**.

![ETL](./images/s3home.png)

Verwenden **im Bildschirm „Bucket erstellen** den Namen `--aepUserLdap---gspem-dam`.

![ETL](./images/bucketname.png)

Belassen Sie alle anderen Standardeinstellungen. Scrollen Sie nach unten und klicken Sie auf **Bucket erstellen**.

![ETL](./images/createbucket.png)

Anschließend wird Ihr Bucket erstellt und zur Amazon S3-Homepage weitergeleitet.

![ETL](./images/S3homeb.png)

## Berechtigungen für den Zugriff auf Ihren S3-Bucket festlegen

Der nächste Schritt besteht darin, den Zugriff auf Ihren S3-Bucket einzurichten.

Navigieren Sie dazu zu [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home).

Der Zugriff auf AWS-Ressourcen wird über Amazon Identity and Access Management (IAM) gesteuert.

Jetzt sehen Sie diese Seite.

![ETL](./images/iam.png)

Klicken Sie im linken Menü auf **Benutzer**. Anschließend wird der Bildschirm **Benutzer** angezeigt. Klicken Sie **Benutzer erstellen**.

![ETL](./images/iammenu.png)

Konfigurieren Sie anschließend Ihren Benutzer:

- Benutzername: `s3_--aepUserLdap--_gspem_dam` verwenden

Klicken Sie auf **Weiter**.

![ETL](./images/configuser.png)

Anschließend wird dieser Bildschirm mit den Berechtigungen angezeigt. Klicken Sie **Richtlinien direkt anhängen**.

![ETL](./images/perm1.png)

Geben Sie den Suchbegriff **s3** ein, um alle zugehörigen S3-Richtlinien anzuzeigen. Wählen Sie die Richtlinie **AmazonS3FullAccess**. Scrollen Sie nach unten und klicken Sie auf **Weiter**.

![ETL](./images/perm2.png)

Überprüfen Sie Ihre Konfiguration. Klicken Sie **Benutzer erstellen**.

![ETL](./images/review.png)

Sie werden es dann sehen. Klicken Sie **Benutzer anzeigen**.

![ETL](./images/review1.png)

Klicken Sie auf **Sicherheitsberechtigungen** und dann auf **Zugriffsschlüssel erstellen**.

![ETL](./images/cred.png)

Wählen Sie **Anwendung, die außerhalb von AWS ausgeführt wird**. Scrollen Sie nach unten und klicken Sie auf **Weiter**.

![ETL](./images/creda.png)

Klicken Sie **Zugriffsschlüssel erstellen**

![ETL](./images/credb.png)

Sie werden es dann sehen. Klicken Sie **Anzeigen**, um Ihren geheimen Zugriffsschlüssel anzuzeigen:

![ETL](./images/cred1.png)

Ihr **geheimer Zugriffsschlüssel** wird jetzt angezeigt.

>[!IMPORTANT]
>
>Speichern Sie Ihre Anmeldedaten in einer Textdatei auf Ihrem Computer.
>
> - Zugriffsschlüssel-ID: …
> - Geheimer Zugriffsschlüssel: …
>
> Wenn Sie auf **Fertig** klicken, werden Ihre Anmeldeinformationen nie mehr angezeigt!

Klicken Sie auf **Fertig**.

![ETL](./images/cred2.png)

Sie haben jetzt erfolgreich einen AWS S3-Bucket erstellt und eine Benutzerin bzw. einen Benutzer mit der Berechtigung zum Zugriff auf diesen Bucket erstellt.

## 1.6.2.2 Assets in Ihren S3-Bucket hochladen

Suchen Sie in der Suchleiste nach **s3**. Klicken Sie auf das erste Suchergebnis: **S3 - Scalable Storage in the Cloud**.

![ETL](./images/bucket1.png)

Klicken Sie auf , um den neu erstellten S3-Bucket zu öffnen, der den Namen `--aepUserLdap---gspem-dam` erhalten soll.

![ETL](./images/bucket2.png)

Klicken Sie **Hochladen**.

![ETL](./images/bucket3.png)

Sie sollten das dann sehen.

![ETL](./images/bucket4.png)

Sie können CitiSignal-Bilddateien ([) &#x200B;](./images/package.zip){target="_blank"}.

Exportieren Sie die Dateien auf Ihren Desktop.

![ETL](./images/bucket5.png)

Klicken Sie **Ordner hinzufügen**.

![ETL](./images/bucket6.png)

Wählen Sie den Ordner **Assets** aus dem Download-Ordner **Package**. Klicken Sie **Hochladen**.

![ETL](./images/bucket7.png)

Sie sollten das dann sehen. Klicken Sie **erneut auf** Ordner hinzufügen“.

![ETL](./images/bucket8.png)

Wählen Sie den Ordner **Miniaturen** aus dem Download-Ordner **Paket**. Klicken Sie **Hochladen**.

![ETL](./images/bucket9.png)

Sie sollten das dann sehen. Klicken Sie **Hochladen**.

![ETL](./images/bucket10.png)

Ihr Upload ist jetzt abgeschlossen. Klicken Sie auf **Schließen**.

![ETL](./images/bucket11.png)

Diese Ordnerstruktur sollte jetzt in Ihrem S3-Bucket vorhanden sein.

![ETL](./images/bucket12.png)

## Nächste Schritte

Navigieren Sie zu [Externe DAM-App erstellen](./ex3.md){target="_blank"}

Zurück zu [GenStudio for Performance Marketing - Erweiterbarkeit](./genstudioext.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
