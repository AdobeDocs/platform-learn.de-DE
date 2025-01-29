---
title: Optimieren des Firefly-Prozesses mit Microsoft Azure und vordefinierten URLs
description: Erfahren Sie, wie Sie Ihren Firefly-Prozess mit Microsoft Azure und vordefinierten URLs optimieren können.
role: Developer
level: Beginner
jira: KT-5342
doc-type: tutorial
exl-id: 5f9803a4-135c-4470-bfbb-a298ab1fee33
source-git-commit: 8e410ad378d61f23d1d880d12e57f9d5e4e523c1
workflow-type: tm+mt
source-wordcount: '1367'
ht-degree: 1%

---

# Optimieren Sie Ihren Firefly-Prozess mit Microsoft Azure und vordefinierten URLs

Erfahren Sie, wie Sie Ihren Firefly-Prozess mit Microsoft Azure und vordefinierten URLs optimieren können.

## Erstellen eines Azure-Abonnements

>[!NOTE]
>
>Wenn Sie bereits über ein Azure-Abonnement verfügen, können Sie diesen Schritt überspringen. Bitte fahren Sie in diesem Fall mit der nächsten Übung fort.

1. Wechseln Sie zu [https://portal.azure.com](https://portal.azure.com){target="_blank"} und melden Sie sich mit Ihrem Azure-Konto an. Wenn Sie noch keine haben, verwenden Sie bitte Ihre persönliche E-Mail-Adresse, um Ihr Azure-Konto zu erstellen.

   ![Azure-Speicher](./images/02azureportalemail.png)

   Nach erfolgreicher Anmeldung sollte der folgende Bildschirm angezeigt werden:

   ![Azure-Speicher](./images/03azureloggedin.png)

1. Wählen Sie im linken Menü **Alle Ressourcen** aus. Wenn Sie noch kein Abonnement haben, wird der Azure-Abonnementbildschirm angezeigt.

1. Wenn Sie noch kein Abonnement haben, wählen Sie **Mit einer kostenlosen Azure-Testversion beginnen**.

   ![Azure-Speicher](./images/04azurestartsubscribe.png)

1. Füllen Sie das Azure-Abonnementformular aus und stellen Sie Ihr Mobiltelefon und Ihre Kreditkarte zur Aktivierung bereit (Sie haben 30 Tage lang eine kostenlose Stufe und werden nicht belastet, es sei denn, Sie führen ein Upgrade durch).

   Wenn der Abonnementprozess abgeschlossen ist, sind Sie bereit.

   ![Azure-Speicher](./images/06azuresubscriptionok.png)

## Azure-Speicherkonto erstellen

1. Suchen Sie nach `storage account` und wählen Sie **Speicherkonten** aus.

   ![Azure-Speicher](./images/azs1.png)

1. Wählen Sie **+ Erstellen** aus.

![Azure-Speicher](./images/azs2.png)

1. Wählen Sie Ihr **Abonnement** und wählen (oder erstellen) Sie eine **Ressourcengruppe**.

1. Verwenden **unter „Speicherkontoname** die `--aepUserLdap--`.

1. Wählen Sie **Überprüfen + Erstellen** aus.

   ![Azure-Speicher](./images/azs3.png)

1. Wählen Sie **Erstellen** aus.

   ![Azure-Speicher](./images/azs4.png)

1. Wählen Sie nach der Bestätigung **Zur Ressource wechseln** aus.

       ![Azure Storage](./images/azs5.png)
   
Ihr Azure-Speicherkonto ist jetzt einsatzbereit.

    ![Azure Storage](./images/azs6.png)

1. Wählen Sie **Datenspeicher** aus und navigieren Sie dann zu **Container**. Wählen Sie **+ Container**.

   ![Azure-Speicher](./images/azs7.png)

1. Verwenden Sie `--aepUserLdap--`für den Namen und wählen Sie **Erstellen**.

   ![Azure-Speicher](./images/azs8.png)

   Ihr Container kann jetzt verwendet werden.

   ![Azure-Speicher](./images/azs9.png)

## 1.1.2.3 Installieren von Azure Storage Explorer

1. [Laden Sie den Microsoft Azure Storage Explorer herunter, um Ihre Dateien zu verwalten](https://azure.microsoft.com/en-us/products/storage/storage-explorer#Download-4){target="_blank"}. Wählen Sie die richtige Version für Ihr Betriebssystem aus, laden Sie sie herunter und installieren Sie sie.

   ![Azure-Speicher](./images/az10.png)

1. Öffnen Sie die Anwendung und wählen Sie **Mit Azure anmelden** aus.

   ![Azure-Speicher](./images/az11.png)

1. Wählen Sie **Abonnement** aus.

   ![Azure-Speicher](./images/az12.png)

1. Wählen Sie **Azure** und dann **Weiter** aus.

   ![Azure-Speicher](./images/az13.png)

1. Wählen Sie Ihr Microsoft Azure-Konto aus und schließen Sie den Authentifizierungsprozess ab.

   ![Azure-Speicher](./images/az14.png)

   Nach der Authentifizierung wird diese Meldung angezeigt.

   ![Azure-Speicher](./images/az15.png)

1. Zurück in der Microsoft Azure Storage Explorer-App, wählen Sie Ihr Abonnement und dann **Explorer öffnen**.

>[!NOTE]
>
>Wenn Ihr Konto nicht angezeigt wird, klicken Sie auf das **Zahnradsymbol** neben Ihrer E-Mail-Adresse und wählen Sie **Filter aufheben**.

    ![Azure Storage](./images/az16.png)

Ihr Speicherkonto wird unter **Speicherkonten** angezeigt.

    ![Azure Storage](./images/az17.png)

1. Öffnen Sie **Blob-Container** und wählen Sie dann den Container aus, den Sie in der vorherigen Übung erstellt haben.

   ![Azure-Speicher](./images/az18.png)

## Manueller Datei-Upload und Verwendung einer Grafikdatei als Stilreferenz

1. Laden Sie eine Bilddatei Ihrer Wahl oder [diese Datei](./images/gradient.jpg){target="_blank"} in den Container hoch.

   ![Azure-Speicher](./images/gradient.jpg)

   Nach dem Hochladen wird sie in Ihrem Container angezeigt:

   ![Azure-Speicher](./images/az19.png)

1. Klicken Sie mit der rechten Maustaste auf `gradient.jpg` und wählen Sie **Freigegebene Zugriffssignatur abrufen**.

   ![Azure-Speicher](./images/az20.png)

1. Unter **Berechtigungen** ist nur **Lesen** erforderlich. Wählen Sie **Erstellen** aus.

   ![Azure-Speicher](./images/az21.png)

1. Kopieren Sie Ihre vordefinierte URL für diese Bilddatei für die nächste API-Anfrage auf Firefly.

   ![Azure-Speicher](./images/az22.png)

1. Zurück in Postman öffnen Sie die Anfrage **POST - Firefly - T2I (styleref) V3**.
Dieses wird in **Body** angezeigt.

   ![Azure-Speicher](./images/az23.png)

1. Ersetzen Sie die Platzhalter-URL durch die vordefinierte URL für Ihre Bilddatei und wählen Sie **Senden**.

   ![Azure-Speicher](./images/az24.png)

1. Öffnen Sie das neue Bild von Response Firefly Services in Ihrem Browser.

   ![Azure-Speicher](./images/az25.png)

   Mit `horses in a field` wird ein weiteres Bild angezeigt, aber dieses Mal ähnelt der Stil der Bilddatei, die Sie als Stilreferenz bereitgestellt haben.

   ![Azure-Speicher](./images/az26.png)

## Programmgesteuerter Datei-Upload

Um den programmgesteuerten Datei-Upload mit Azure Storage-Konten zu verwenden, müssen Sie ein neues **Shared Access Signature (SAS)-** mit Berechtigungen erstellen, die Ihnen das Schreiben einer Datei ermöglichen.

1. Klicken Sie im Azure Storage Explorer mit der rechten Maustaste auf Ihren Container und wählen Sie **Freigegebene Zugriffssignatur abrufen**.

   ![Azure-Speicher](./images/az27.png)

1. Wählen **unter** die folgenden erforderlichen Berechtigungen aus:

   - **Lesen**
   - **Hinzufügen**
   - **Create**
   - **Write**
   - **Liste**

1. Wählen Sie **Erstellen** aus.

   ![Azure-Speicher](./images/az28.png)

1. Nachdem Sie Ihr **SAS-Token** erhalten haben, wählen Sie **Kopieren** aus.

   ![Azure-Speicher](./images/az29.png)

   Verwenden Sie das **SAS-Token**, um eine Datei in Ihr Azure-Speicherkonto hochzuladen.

1. Zurück in Postman, wählen Sie den Ordner **FF - Firefly Services Tech Insiders** und dann **…** im Ordner **Firefly** aus und klicken Sie dann auf **Anfrage hinzufügen**.

   ![Azure-Speicher](./images/az30.png)

1. Ändern Sie den Namen der leeren Anfrage in **Datei in Azure-Speicherkonto hochladen** ändern Sie den **Anfragetyp** in **PUT** und fügen Sie die SAS-Token-URL in den URL-Abschnitt ein und wählen Sie dann **body**.

   ![Azure-Speicher](./images/az31.png)

1. Wählen Sie anschließend eine Datei auf Ihrem lokalen Computer aus oder verwenden Sie eine andere Bilddatei [hier](./images/gradient2-p.jpg){target="_blank"}.

   ![Verlaufsdatei](./images/gradient2-p.jpg)

1. Wählen **Hauptteil** die Option **Binär** dann **Datei auswählen** und wählen Sie dann **+ Neue Datei vom lokalen Computer aus**.

   ![Azure-Speicher](./images/az32.png)

1. Wählen Sie die gewünschte Datei aus und klicken Sie auf **Öffnen**.

   ![Azure-Speicher](./images/az33.png)

1. Geben Sie als Nächstes den Dateinamen an, der in Ihrem Azure-Speicherkonto verwendet werden soll, indem Sie den Cursor vor das Fragezeichen **setzen?** in der URL wie folgt aus:

   ![Azure-Speicher](./images/az34.png)

   Die URL sieht derzeit wie folgt aus, muss jedoch geändert werden.

   `https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03...`

1. Ändern Sie den Dateinamen in `gradient2-p.jpg` und ändern Sie die URL so, dass sie den Dateinamen wie folgt enthält:

   `https://vangeluw.blob.core.windows.net/vangeluw/gradient2-p.jpg?sv=2023-01-03...`

   ![Azure-Speicher](./images/az34a.png)

1. Gehen Sie dann zu **Headers**, um einen neuen Header wie den folgenden manuell hinzuzufügen:

   | Schlüssel | Wert |
   |:-------------:| :---------------:| 
   | `x-ms-blob-type` | `BlockBlob` |


   ![Azure-Speicher](./images/az35.png)

1. Wechseln Sie zu **Autorisierung** und legen Sie **Auth-Typ** auf **Keine Autorisierung** fest und wählen Sie **Senden**.

   ![Azure-Speicher](./images/az36.png)

1. Als Nächstes wird diese leere Antwort in Postman angezeigt, was bedeutet, dass Ihr Datei-Upload gut ist.

   ![Azure-Speicher](./images/az37.png)

1. Aktualisieren Sie im Azure Storage Explorer den Inhalt Ihres Ordners, und die neu hochgeladene Datei wird angezeigt.

   ![Azure-Speicher](./images/az38.png)

## Programmgesteuerte Dateiverwendung

Um langfristig programmgesteuert Dateien aus Azure Storage-Konten lesen zu können, müssen Sie ein neues **Shared Access Signature (SAS)-Token** Berechtigungen erstellen, mit denen Sie eine Datei lesen können. Technisch gesehen könnten Sie das in der vorherigen Übung erstellte SAS-Token verwenden, aber es empfiehlt sich, ein separates Token mit nur **Lese**-Berechtigungen und ein separates Token mit nur **Schreib**-Berechtigungen zu verwenden.

### Langfristiges SAS-Token lesen

1. Gehen Sie zurück zum Azure Storage-Explorer, klicken Sie mit der rechten Maustaste auf Ihren Container und wählen Sie **Freigegebene Zugriffssignatur abrufen**.

   ![Azure-Speicher](./images/az27.png)

1. Wählen **unter** die folgenden erforderlichen Berechtigungen aus:

   - **Lesen**
   - **Liste**

1. Legen Sie **Ablaufzeit** auf einen Zeitraum von 1 Jahr fest.

1. Wählen Sie **Erstellen** aus.

   ![Azure-Speicher](./images/az100.png)

1. Kopieren Sie die URL und schreiben Sie sie in eine Datei auf Ihrem Computer, um Ihr langfristiges SAS-Token mit Leseberechtigung zu erhalten.

   ![Azure-Speicher](./images/az101.png)

   Ihre URL sollte wie folgt aussehen:

   `https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

   Sie können aus der obigen URL mehrere Werte ableiten:

   - `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
   - `AZURE_STORAGE_CONTAINER`: `vangeluw`
   - `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

### Langfristiges SAS-Token schreiben

1. Gehen Sie zurück zum Azure Storage-Explorer, klicken Sie mit der rechten Maustaste auf Ihren Container und wählen Sie **Freigegebene Zugriffssignatur abrufen**.

   ![Azure-Speicher](./images/az27.png)

1. Wählen **unter** die folgenden erforderlichen Berechtigungen aus:

   - **Hinzufügen**
   - **Create**
   - **Write**

1. Legen Sie die **Ablaufzeit** auf ein Jahr fest.

1. Wählen Sie **Erstellen** aus.

   ![Azure-Speicher](./images/az102.png)

1. Kopieren Sie die URL und schreiben Sie sie in eine Datei auf Ihrem Computer, um Ihr langfristiges SAS-Token mit Leseberechtigung zu erhalten.

   ![Azure-Speicher](./images/az103.png)

   Ihre URL sollte wie folgt aussehen:

   `https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Sie können aus der obigen URL mehrere Werte ableiten:

    - `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
    - `AZURE_STORAGE_CONTAINER`: `vangeluw`
     
     
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&amp;st=2025-01-13T07%3A36%3A35Z&amp;se=2026-01-14T07%3A36%3A00Z&amp;sr=c&amp;sp=rl&amp;sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK_Uqh` `?sv=2023-01-03&amp;st=2025-01-13T07%3A38%3A59Z&amp;se=2026-01-14T07%3A38%3A00Z&amp;sr=c&amp;sp=acw&amp;sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovCoX
### Variablen in Postman

Wie Sie im obigen Abschnitt sehen können, gibt es einige allgemeine Variablen sowohl im Lese- als auch im Schreib-Token.

Als Nächstes müssen Sie Variablen in Postman erstellen, die die verschiedenen Elemente der oben genannten SAS-Token speichern. Es gibt einige Werte, die in beiden URLs identisch sind:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Für zukünftige API-Interaktionen ändert sich hauptsächlich der Asset-Name, während die oben genannten Variablen unverändert bleiben. In diesem Fall ist es sinnvoll, Variablen in Postman zu erstellen, sodass Sie sie nicht jedes Mal manuell angeben müssen.

1. Wählen Sie in Postman **Umgebungen**, öffnen Sie **Alle Variablen** und wählen Sie **Umgebung**.

   ![Azure-Speicher](./images/az104.png)

1. Erstellen Sie diese 4 Variablen in der angezeigten Tabelle und geben Sie für die Spalten **Anfangswert** und **Aktueller Wert** Ihre spezifischen persönlichen Werte ein.

   - `AZURE_STORAGE_URL`: Ihre URL
   - `AZURE_STORAGE_CONTAINER`: Ihr Container-Name
   - `AZURE_STORAGE_SAS_READ`: Ihr SAS-Lese-Token
   - `AZURE_STORAGE_SAS_WRITE`: Ihr SAS-Schreib-Token

1. Wählen Sie **Speichern** aus.

   ![Azure-Speicher](./images/az105.png)

   In einer der vorherigen Übungen sah der **Body** Ihrer Anfrage **Firefly - T2I (styleref) V3** wie folgt aus:

   `"url": "https://vangeluw.blob.core.windows.net/vangeluw/gradient.jpg?sv=2023-01-03&st=2025-01-13T07%3A16%3A52Z&se=2026-01-14T07%3A16%3A00Z&sr=b&sp=r&sig=x4B1XZuAx%2F6yUfhb28hF0wppCOMeH7Ip2iBjNK5A%2BFw%3D"`

   ![Azure-Speicher](./images/az24.png)

1. Ändern Sie die URL in:

   `"url": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/gradient.jpg{{AZURE_STORAGE_SAS_READ}}"`

1. Wählen Sie **Senden** aus, um die vorgenommenen Änderungen zu testen.

   ![Azure-Speicher](./images/az106.png)

   Wenn die Variablen richtig konfiguriert waren, wird eine Bild-URL zurückgegeben.

   ![Azure-Speicher](./images/az107.png)

1. Öffnen Sie die Bild-URL, um Ihr Bild zu überprüfen.

   ![Azure-Speicher](./images/az108.jpg)

## Nächste Schritte

Zu [Adobe Firefly- und Adobe Photoshop-APIs](./ex3.md){target="_blank"}

Zurück zu [Übersicht über Adobe Firefly-Services](./firefly-services.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}