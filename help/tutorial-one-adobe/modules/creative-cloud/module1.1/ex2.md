---
title: Optimieren Sie Ihren Firefly-Prozess mit Microsoft Azure und vordefinierten URLs
description: Optimieren Sie Ihren Firefly-Prozess mit Microsoft Azure und vordefinierten URLs
kt: 5342
doc-type: tutorial
exl-id: 5f9803a4-135c-4470-bfbb-a298ab1fee33
source-git-commit: 2fe7d2528132301f559f9d51faa9ad128f5d890f
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 1%

---

# 1.1.2 Optimieren Sie Ihren Firefly-Prozess mit Microsoft Azure und vordefinierten URLs

## 1.1.2.1 Erstellen eines Azure-Abonnements

>[!NOTE]
>
>Wenn Sie bereits über ein Azure-Abonnement verfügen, können Sie diesen Schritt überspringen. Bitte fahren Sie in diesem Fall mit der nächsten Übung fort.

Wechseln Sie zu [https://portal.azure.com](https://portal.azure.com){target="_blank"} und melden Sie sich mit Ihrem Azure-Konto an. Wenn Sie noch keine haben, verwenden Sie bitte Ihre persönliche E-Mail-Adresse, um Ihr Azure-Konto zu erstellen.

![Azure-Speicher](./images/02azureportalemail.png)

Nach erfolgreicher Anmeldung wird der folgende Bildschirm angezeigt:

![Azure-Speicher](./images/03azureloggedin.png)

Klicken Sie auf das linke Menü und wählen Sie **Alle Ressourcen**. Der Azure-Abonnementbildschirm wird angezeigt, wenn Sie noch kein Abonnement haben. Wählen Sie in diesem Fall **Mit einer kostenlosen Azure-Testversion beginnen**.

![Azure-Speicher](./images/04azurestartsubscribe.png)

Füllen Sie das Azure-Abonnementformular aus, stellen Sie Ihr Mobiltelefon und Ihre Kreditkarte zur Aktivierung bereit (Sie haben 30 Tage lang eine kostenlose Stufe und werden nicht belastet, es sei denn, Sie führen ein Upgrade durch).

Wenn der Anmeldeprozess abgeschlossen ist, können Sie loslegen:

![Azure-Speicher](./images/06azuresubscriptionok.png)

## 1.1.2.2 Azure-Speicherkonto erstellen

Suchen Sie nach `storage account` und klicken Sie dann auf **Speicherkonten**.

![Azure-Speicher](./images/azs1.png)

Klicken Sie auf **+ Erstellen**.

![Azure-Speicher](./images/azs2.png)

Füllen Sie die folgenden Details aus:

- Wählen Sie Ihr **Abonnement**
- Wählen (oder erstellen) Sie eine **Ressourcengruppe**
- **Speicherkontoname**: Verwenden Sie `--aepUserLdap--`

Klicken Sie **Überprüfen + Erstellen**.

![Azure-Speicher](./images/azs3.png)

Klicken Sie auf **Erstellen**.

![Azure-Speicher](./images/azs4.png)

Sie erhalten dann eine ähnliche Bestätigung. Klicken Sie **Zu Ressource wechseln**.

![Azure-Speicher](./images/azs5.png)

Ihr Azure-Speicherkonto ist jetzt einsatzbereit.

![Azure-Speicher](./images/azs6.png)

Klicken Sie **Datenspeicher** und gehen Sie dann zu **Container**. Klicken Sie auf **+ Container**.

![Azure-Speicher](./images/azs7.png)

Verwenden Sie `--aepUserLdap--` als Namen. Klicken Sie auf **Erstellen**.

![Azure-Speicher](./images/azs8.png)

Ihr Container kann jetzt verwendet werden.

![Azure-Speicher](./images/azs9.png)

## 1.1.2.3 Installieren von Azure Storage Explorer

Sie verwenden den Microsoft Azure Storage Explorer, um Ihre Dateien zu verwalten. Sie können ihn über [diesen Link](https://azure.microsoft.com/en-us/products/storage/storage-explorer#Download-4){target="_blank"} herunterladen. Wählen Sie die richtige Version für Ihr Betriebssystem aus, laden Sie sie herunter und installieren Sie sie.

![Azure-Speicher](./images/az10.png)

Öffnen Sie die Anwendung nach der Installation. Sie werden etwas Ähnliches sehen. Klicken Sie **Mit Azure anmelden**.

![Azure-Speicher](./images/az11.png)

Klicken Sie **Abonnement**.

![Azure-Speicher](./images/az12.png)

Wählen Sie **Azure** aus und klicken Sie auf **Weiter**.

![Azure-Speicher](./images/az13.png)

Wählen Sie Ihr Microsoft Azure-Konto aus und schließen Sie den Authentifizierungsprozess ab.

![Azure-Speicher](./images/az14.png)

Nach der Authentifizierung wird eine Nachricht wie die folgende angezeigt.

![Azure-Speicher](./images/az15.png)

Wechseln Sie zurück zur Microsoft Azure Storage Explorer-App. Wählen Sie Ihr Abonnement aus und klicken Sie auf **Explorer öffnen**.

>[!NOTE]
>
>Wenn Ihr Konto nicht angezeigt wird, klicken Sie auf das **Zahnradsymbol** neben Ihrer E-Mail-Adresse und wählen Sie **Filter aufheben**.

![Azure-Speicher](./images/az16.png)

Ihr Speicherkonto finden Sie dann unter **Speicherkonten**.

![Azure-Speicher](./images/az17.png)

Öffnen Sie **Blob-Container** und klicken Sie dann auf den Container, den Sie in der vorherigen Übung erstellt haben.

![Azure-Speicher](./images/az18.png)

## 1.1.2.4 Manueller Datei-Upload und Verwendung einer Grafikdatei als Stilreferenz

Sie sollten jetzt eine Bilddatei Ihrer Wahl in Ihren Container hochladen. Sie können eine beliebige Bilddatei verwenden, oder Sie können [diese Datei](./images/gradient.jpg){target="_blank"} verwenden, indem Sie sie auf Ihren Computer herunterladen.

![Azure-Speicher](./images/gradient.jpg)

Legen Sie die Bilddatei im Azure Storage Explorer in Ihrem Container ab.

Nach dem Hochladen wird sie in Ihrem Container angezeigt:

![Azure-Speicher](./images/az19.png)

Klicken Sie mit der rechten Maustaste auf den `gradient.jpg` und dann auf **Freigegebene Zugriffssignatur abrufen**.

![Azure-Speicher](./images/az20.png)

Unter **Berechtigungen** ist nur **Lesen** erforderlich. Klicken Sie auf **Erstellen**.

![Azure-Speicher](./images/az21.png)

Anschließend sehen Sie Ihre vordefinierte URL für diese Bilddatei. Kopieren Sie sie, da Sie sie für die nächste API-Anfrage zum Firefly benötigen werden.

![Azure-Speicher](./images/az22.png)

Zurück zu Postman. Öffnen Sie die Anfrage **POST - Firefly - T2I (styleref) V3**. Sie sehen dies dann in **Body**.

![Azure-Speicher](./images/az23.png)

Ersetzen Sie die Platzhalter-URL durch die vordefinierte URL für Ihre Bilddatei, die Sie aus Azure Storage Explorer kopiert haben. Dann hast du das hier. Klicken Sie auf **Senden**.

![Azure-Speicher](./images/az24.png)

Sie erhalten dann erneut eine Antwort von Firefly Services mit einem neuen Bild. Öffnen Sie die Bilddatei in Ihrem Browser.

![Azure-Speicher](./images/az25.png)

Sie sehen dann ein anderes Bild mit `horses in a field`, aber dieses Mal ähnelt der Stil der Bilddatei, die Sie als Stilreferenz bereitgestellt haben.

![Azure-Speicher](./images/az26.png)

## Programmgesteuertes 1.1.2.5 von Dateien

Um den programmgesteuerten Datei-Upload mit Azure Storage-Konten zu verwenden, müssen Sie ein neues **Shared Access Signature (SAS)-** mit Berechtigungen erstellen, die Ihnen das Schreiben einer Datei ermöglichen.

Gehen Sie dazu zurück zum Azure Storage-Explorer. Klicken Sie mit der rechten Maustaste auf den Container und dann auf **Freigegebene Zugriffssignatur abrufen**.

![Azure-Speicher](./images/az27.png)

Unter **Berechtigungen** sind die folgenden Berechtigungen erforderlich:

- **Lesen**
- **Hinzufügen**
- **Create**
- **Write**
- **Liste**

Klicken Sie auf **Erstellen**.

![Azure-Speicher](./images/az28.png)

Sie erhalten dann Ihr **SAS-Token**. Klicken Sie **Kopieren**.

![Azure-Speicher](./images/az29.png)

Sie können jetzt dieses **SAS-Token** verwenden, um eine Datei in Ihr Azure-Speicherkonto hochzuladen. Gehen Sie dazu zurück nach Postman.

Wählen Sie den Ordner **FF - Firefly Services Tech Insiders** aus, klicken Sie dann auf die 3 Punkte **…** auf dem Ordner **Firefly** und klicken Sie dann auf **Anfrage hinzufügen**.

![Azure-Speicher](./images/az30.png)

Sie erhalten dann eine leere Anfrage. Ändern Sie den Namen der Anfrage in **Datei in Azure-Speicherkonto hochladen** ändern Sie den **Anfragetyp** in **PUT** und fügen Sie die SAS-Token-URL in den URL-Abschnitt ein.

Klicken Sie dann auf **Textkörper**.

![Azure-Speicher](./images/az31.png)

Nun müssen Sie eine Datei auf Ihrem lokalen Computer auswählen. Sie können eine neue Bilddatei Ihrer Wahl verwenden, oder Sie können eine andere Bilddatei verwenden, die Sie [hier](./images/gradient2-p.jpg){target="_blank"} finden.

![Verlaufsdatei](./images/gradient2-p.jpg)

Wählen Sie **Hauptteil** die Option **Binär** und klicken Sie anschließend auf **Datei auswählen** und anschließend auf **+ Neue Datei vom lokalen Computer**.

![Azure-Speicher](./images/az32.png)

Wählen Sie die gewünschte Datei aus und klicken Sie auf **Öffnen**.

![Azure-Speicher](./images/az33.png)

Sie werden es dann sehen. Als Nächstes geben Sie den Dateinamen an, der in Ihrem Azure-Speicherkonto verwendet werden soll. Dazu müssen Sie den Cursor vor das Fragezeichen **setzen?** in der URL. Sie können dies derzeit dort sehen:

![Azure-Speicher](./images/az34.png)

Die URL sieht derzeit wie folgt aus, muss sich jedoch ändern.

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03...`

Der zu verwendende Dateiname lautet `gradient2-p.jpg`, was bedeutet, dass die URL geändert werden muss, um den Dateinamen einzuschließen, wie in diesem Beispiel:

`https://vangeluw.blob.core.windows.net/vangeluw/gradient2-p.jpg?sv=2023-01-03...`

![Azure-Speicher](./images/az34a.png)

Gehen Sie dann zu **Headers**, wo Sie eine neue Kopfzeile manuell hinzufügen müssen. Verwenden Sie diesen:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `x-ms-blob-type` | `BlockBlob` |


![Azure-Speicher](./images/az35.png)

Wechseln Sie zu **Autorisierung** und setzen Sie **Auth-Typ** auf **Keine Autorisierung**. Klicken Sie auf **Senden**.

![Azure-Speicher](./images/az36.png)

Daraufhin wird diese leere Antwort in Postman angezeigt, was bedeutet, dass der Datei-Upload gut gelaufen ist.

![Azure-Speicher](./images/az37.png)

Wenn Sie dann zum Azure Storage Explorer zurückkehren und den Inhalt Ihres Ordners aktualisieren, finden Sie dort jetzt die neu hochgeladene Datei.

![Azure-Speicher](./images/az38.png)

## 1.1.2.6 Verwendung der programmgesteuerten Datei

Um langfristig programmgesteuert Dateien aus Azure Storage-Konten lesen zu können, müssen Sie ein neues **Shared Access Signature (SAS)-**-Token mit Berechtigungen zum Lesen einer Datei erstellen. Technisch gesehen könnten Sie das in der vorherigen Übung erstellte SAS-Token verwenden, es empfiehlt sich jedoch, ein separates Token mit nur **Lese-/** und ein separates Token mit nur **Schreib**-Berechtigungen zu verwenden.

### Langfristiges SAS-Token lesen

Gehen Sie dazu zurück zum Azure Storage-Explorer. Klicken Sie mit der rechten Maustaste auf den Container und dann auf **Freigegebene Zugriffssignatur abrufen**.

![Azure-Speicher](./images/az27.png)

Unter **Berechtigungen** sind die folgenden Berechtigungen erforderlich:

- **Lesen**
- **Liste**

Legen Sie die **Ablaufzeit** auf ein Jahr fest.

Klicken Sie auf **Erstellen**.

![Azure-Speicher](./images/az100.png)

Sie erhalten dann Ihr langfristiges SAS-Token mit Leseberechtigung. Kopieren Sie die URL und schreiben Sie sie in eine Datei auf Ihrem Computer.

![Azure-Speicher](./images/az101.png)

Ihre URL sieht dann wie folgt aus:

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

Sie können aus der obigen URL mehrere Werte ableiten:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

### Langfristiges SAS-Token schreiben

Gehen Sie dazu zurück zum Azure Storage-Explorer. Klicken Sie mit der rechten Maustaste auf den Container und dann auf **Freigegebene Zugriffssignatur abrufen**.

![Azure-Speicher](./images/az27.png)

Unter **Berechtigungen** sind die folgenden Berechtigungen erforderlich:

- **Hinzufügen**
- **Create**
- **Write**

Legen Sie die **Ablaufzeit** auf ein Jahr fest.

Klicken Sie auf **Erstellen**.

![Azure-Speicher](./images/az102.png)

Sie erhalten dann Ihr langfristiges SAS-Token mit Leseberechtigung. Kopieren Sie die URL und schreiben Sie sie in eine Datei auf Ihrem Computer.

![Azure-Speicher](./images/az103.png)

Ihre URL sieht dann wie folgt aus:

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Sie können wieder einige Werte aus der obigen URL ableiten:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

### Variablen in Postman

Wie Sie im obigen Abschnitt sehen können, gibt es einige allgemeine Variablen sowohl im Lese- als auch im Schreib-Token.

Jetzt müssen Sie in Postman Variablen erstellen, die die verschiedenen Elemente der oben genannten SAS-Token speichern.
Es gibt einige Werte, die in beiden URLs identisch sind:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Bei zukünftigen API-Interaktionen ändert sich hauptsächlich der Asset-Name, während die oben genannten Variablen unverändert bleiben. In diesem Fall ist es sinnvoll, Variablen in Postman zu erstellen, sodass Sie sie nicht jedes Mal manuell angeben müssen.

Öffnen Sie dazu Postman. Klicken Sie auf **Umgebungen**, öffnen Sie das Menü **Alle Variablen** und klicken Sie auf **Umgebung**.

![Azure-Speicher](./images/az104.png)

Dann sehen Sie das hier. Erstellen Sie diese 4 Variablen in der angezeigten Tabelle und geben Sie für die Spalten **Anfangswert** und **Aktueller Wert** Ihre spezifischen persönlichen Werte ein.

- `AZURE_STORAGE_URL`: Ihre URL
- `AZURE_STORAGE_CONTAINER`: Ihr Container-Name
- `AZURE_STORAGE_SAS_READ`: Ihr SAS-Lese-Token
- `AZURE_STORAGE_SAS_WRITE`: Ihr SAS-Schreib-Token

Klicken Sie auf **Speichern**.

![Azure-Speicher](./images/az105.png)

In einer der vorherigen Übungen sah der **Body** Ihrer Anfrage **Firefly - T2I (styleref) V3** wie folgt aus:

`"url": "https://vangeluw.blob.core.windows.net/vangeluw/gradient.jpg?sv=2023-01-03&st=2025-01-13T07%3A16%3A52Z&se=2026-01-14T07%3A16%3A00Z&sr=b&sp=r&sig=x4B1XZuAx%2F6yUfhb28hF0wppCOMeH7Ip2iBjNK5A%2BFw%3D"`

![Azure-Speicher](./images/az24.png)

Sie können die URL wie folgt ändern:

`"url": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/gradient.jpg{{AZURE_STORAGE_SAS_READ}}"`

Klicken Sie **Senden**, um die vorgenommenen Änderungen zu testen.

![Azure-Speicher](./images/az106.png)

Wenn die Variablen richtig konfiguriert wurden, wird eine Bild-URL zurückgegeben.

![Azure-Speicher](./images/az107.png)

Öffnen Sie die Bild-URL, um Ihr Bild zu überprüfen.

![Azure-Speicher](./images/az108.jpg)

Nächster Schritt: [1.1.3 Adobe Firefly und Adobe Photoshop](./ex3.md){target="_blank"}

[Zurück zum Modul 1.1](./firefly-services.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
