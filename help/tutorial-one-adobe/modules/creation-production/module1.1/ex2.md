---
title: Optimieren des Firefly-Prozesses mit Microsoft Azure und vordefinierten URLs
description: Erfahren Sie, wie Sie Ihren Firefly-Prozess mithilfe von Microsoft Azure und vordefinierten URLs optimieren können
role: Developer
level: Beginner
jira: KT-5342
doc-type: tutorial
exl-id: 5f9803a4-135c-4470-bfbb-a298ab1fee33
source-git-commit: a1da1c73cbddacde00211190a1ca3d36f7a2c329
workflow-type: tm+mt
source-wordcount: '1944'
ht-degree: 1%

---

# 1.1.2 Optimieren Sie Ihren Firefly-Prozess mithilfe von Microsoft Azure und vordefinierten URLs

Erfahren Sie, wie Sie Ihren Firefly-Prozess mithilfe von Microsoft Azure und vorsignierten URLs optimieren können.

## 1.1.2.1 Was sind vorsignierte URLs?

Eine vordefinierte URL ist eine URL, die Ihnen temporären Zugriff auf ein bestimmtes Objekt an einem Speicherort gewährt. Mithilfe der URL kann ein Benutzer beispielsweise entweder das Objekt LESEN oder ein Objekt SCHREIBEN (oder ein vorhandenes Objekt aktualisieren). Die URL enthält bestimmte Parameter, die von Ihrer Anwendung festgelegt werden.

Im Zusammenhang mit der Erstellung der Automatisierung der Content-Supply-Chain gibt es oft mehrere Dateivorgänge, die für einen bestimmten Anwendungsfall erfolgen müssen. Beispielsweise kann es erforderlich sein, den Hintergrund einer Datei zu ändern, den Text verschiedener Ebenen zu ändern usw. Es ist nicht immer möglich, alle Dateioperationen gleichzeitig auszuführen, was einen mehrstufigen Ansatz erforderlich macht. Nach jedem Zwischenschritt ist die Ausgabe dann eine temporäre Datei, die für die Ausführung des nächsten Schritts benötigt wird. Sobald dieser nächste Schritt ausgeführt wird, verliert die temporäre Datei schnell an Wert und wird oft nicht mehr benötigt, sodass sie gelöscht werden sollte.

Adobe Firefly Services unterstützt derzeit die folgenden Domains:

- Amazon AWS: *.amazonaws.com
- Microsoft Azure: *.windows.net
- Dropbox: *.dropboxusercontent.com

Der Grund, warum häufig Cloud-Speicherlösungen verwendet werden, ist, dass die Zwischenelemente, die erstellt werden, schnell an Wert verlieren. Das Problem, das durch vorsignierte URLs gelöst wird, lässt sich am besten mit einer Massenspeicherlösung lösen, die in der Regel einer der oben genannten Cloud-Services ist.

Innerhalb des Adobe-Ökosystems gibt es auch Speicherlösungen wie Frame.io, Workfront Fusion und Adobe Experience Manager Assets. Diese Lösungen unterstützen auch vorsignierte URLs, sodass während der Implementierung häufig eine Auswahl getroffen werden muss. Die Auswahl basiert dann oft auf einer Kombination aus bereits verfügbaren Anwendungen und Speicherkosten.

Vorsignierte URLs werden daher aus folgenden Gründen in Kombination mit Adobe Firefly Services-Vorgängen verwendet:

- Unternehmen müssen häufig mehrere Änderungen am selben Image in Zwischenschritten verarbeiten. Dazu ist ein Zwischenspeicher erforderlich.
- Der Zugriff auf das Lesen und Schreiben von Cloud-Speicherorten sollte sicher sein. In einer Server-seitigen Umgebung ist es nicht möglich, sich manuell anzumelden, sodass die Sicherheit direkt in die URL integriert werden muss.

Eine vorsignierte URL verwendet drei Parameter, um den Zugriff auf den Benutzer zu beschränken:

- Speicherort: Dies könnte ein AWS S3-Bucket-Speicherort, ein Microsoft Azure-Speicherkontospeicherort mit Container sein
- Dateiname: Die spezifische Datei, die gelesen, aktualisiert und gelöscht werden muss.
- Abfragezeichenfolgenparameter: Ein Abfragezeichenfolgenparameter beginnt immer mit einem Fragezeichen und wird von einer komplexen Reihe von Parametern gefolgt

Beispiel:

- **Amazon AWS**: `https://bucket.s3.eu-west-2.amazonaws.com/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AXXXXXXXXXX%2Feu-west-2%2Fs3%2Faws4_request&X-Amz-Date=20250510T171315Z&X-Amz-Expires=1800&X-Amz-Signature=XXXXXXXXX&X-Amz-SignedHeaders=host`
- **Microsoft Azure**: `https://storageaccount.blob.core.windows.net/container/image.png?sv=2023-01-03&st=2025-01-13T07%3A16%3A52Z&se=2026-01-14T07%3A16%3A00Z&sr=b&sp=r&sig=XXXXXX%3D`

## 1.1.2.2 Erstellen eines Azure-Abonnements

>[!NOTE]
>
>Wenn Sie bereits über ein Azure-Abonnement verfügen, können Sie diesen Schritt überspringen. Bitte fahren Sie in diesem Fall mit der nächsten Übung fort.

>[!NOTE]
>
>Wenn Sie dieses Tutorial im Rahmen eines persönlich angeleiteten Workshops oder einer angeleiteten On-Demand-Schulung durchlaufen, haben Sie wahrscheinlich bereits Zugriff auf ein Microsoft Azure-Speicherkonto. In diesem Fall müssen Sie kein eigenes Konto erstellen - verwenden Sie bitte das Konto, das Ihnen im Rahmen der Schulung bereitgestellt wurde.

Wechseln Sie zu [https://portal.azure.com](https://portal.azure.com){target="_blank"} und melden Sie sich mit Ihrem Azure-Konto an. Wenn Sie noch keine haben, verwenden Sie bitte Ihre persönliche E-Mail-Adresse, um Ihr Azure-Konto zu erstellen.

![Azure-Speicher](./images/02azureportalemail.png){zoomable="yes"}

Nach erfolgreicher Anmeldung sollte der folgende Bildschirm angezeigt werden:

![Azure-Speicher](./images/03azureloggedin.png){zoomable="yes"}

Wählen Sie im linken Menü **Alle Ressourcen** aus. Wenn Sie noch kein Abonnement haben, wird der Azure-Abonnementbildschirm angezeigt.

Wenn Sie noch kein Abonnement haben, wählen Sie **Mit einer kostenlosen Azure-Testversion beginnen**.

![Azure-Speicher](./images/04azurestartsubscribe.png){zoomable="yes"}

Füllen Sie das Azure-Abonnementformular aus und stellen Sie Ihr Mobiltelefon und Ihre Kreditkarte zur Aktivierung bereit (Sie haben 30 Tage lang eine kostenlose Stufe und werden nicht belastet, es sei denn, Sie führen ein Upgrade durch).

Wenn der Abonnementprozess abgeschlossen ist, sind Sie bereit.

![Azure-Speicher](./images/06azuresubscriptionok.png){zoomable="yes"}

## 1.1.2.3 Azure-Speicherkonto erstellen

Suchen Sie nach `storage account` und wählen Sie **Speicherkonten** aus.

![Azure-Speicher](./images/azs1.png){zoomable="yes"}

Wählen Sie **+ Erstellen** aus.

![Azure-Speicher](./images/azs2.png){zoomable="yes"}

Wählen Sie Ihr **Abonnement** und wählen (oder erstellen) Sie eine **Ressourcengruppe**.

Verwenden **unter „Speicherkontoname** die `--aepUserLdap--`.

Wählen Sie **Überprüfen + Erstellen** aus.

![Azure-Speicher](./images/azs3.png){zoomable="yes"}

Wählen Sie **Erstellen** aus.

![Azure-Speicher](./images/azs4.png){zoomable="yes"}

Wählen Sie nach der Bestätigung **Zur Ressource wechseln** aus.

![Azure-Speicher](./images/azs5.png){zoomable="yes"}

Ihr Azure-Speicherkonto ist jetzt einsatzbereit.

![Azure-Speicher](./images/azs6.png){zoomable="yes"}

Wählen Sie **Datenspeicher** aus und navigieren Sie dann zu **Container**. Wählen Sie **+ Container**.

![Azure-Speicher](./images/azs7.png){zoomable="yes"}

Verwenden Sie `--aepUserLdap--` für den Namen und wählen Sie **Erstellen**.

![Azure-Speicher](./images/azs8.png){zoomable="yes"}

Ihr Container kann jetzt verwendet werden.

![Azure-Speicher](./images/azs9.png){zoomable="yes"}

## 1.1.2.4 Installieren von Azure Storage Explorer

[Laden Sie den Microsoft Azure Storage Explorer herunter, um Ihre Dateien zu verwalten](https://azure.microsoft.com/en-us/products/storage/storage-explorer#Download-4){target="_blank"}. Wählen Sie die richtige Version für Ihr Betriebssystem aus, laden Sie sie herunter und installieren Sie sie.

![Azure-Speicher](./images/az10.png){zoomable="yes"}

Öffnen Sie die Anwendung und wählen Sie **Mit Azure anmelden** aus.

![Azure-Speicher](./images/az11.png){zoomable="yes"}

Wählen Sie **Abonnement** aus.

![Azure-Speicher](./images/az12.png){zoomable="yes"}

Wählen Sie **Azure** und dann **Weiter** aus.

![Azure-Speicher](./images/az13.png){zoomable="yes"}

Wählen Sie Ihr Microsoft Azure-Konto aus und schließen Sie den Authentifizierungsprozess ab.

![Azure-Speicher](./images/az14.png){zoomable="yes"}

Nach der Authentifizierung wird diese Meldung angezeigt.

![Azure-Speicher](./images/az15.png){zoomable="yes"}

Zurück in der Microsoft Azure Storage Explorer-App, wählen Sie Ihr Abonnement und dann **Explorer öffnen**.

>[!NOTE]
>
>Wenn Ihr Konto nicht angezeigt wird, klicken Sie auf das **Zahnradsymbol** neben Ihrer E-Mail-Adresse und wählen Sie **Filter aufheben**.

![Azure-Speicher](./images/az16.png){zoomable="yes"}

Ihr Speicherkonto wird unter **Speicherkonten** angezeigt.

![Azure-Speicher](./images/az17.png){zoomable="yes"}

Öffnen Sie **Blob-Container** und wählen Sie dann den Container aus, den Sie in der vorherigen Übung erstellt haben.

![Azure-Speicher](./images/az18.png){zoomable="yes"}

## 1.1.2.5 Manueller Datei-Upload und Verwendung einer Grafikdatei als Stilreferenz

Laden Sie eine Bilddatei Ihrer Wahl oder [diese Datei](./images/gradient.jpg){target="_blank"} in den Container hoch.

>[!NOTE]
>
>Bei Verwendung von Bildern als Stilreferenz, Kompositionsreferenz oder Bildmaske werden die folgenden Bildtypen akzeptiert:
>- image/jpeg
>- image/png
>- image/webp

![Azure-Speicher](./images/gradient.jpg)

Nach dem Hochladen wird sie in Ihrem Container angezeigt:

![Azure-Speicher](./images/az19.png){zoomable="yes"}

Klicken Sie mit der rechten Maustaste auf `gradient.jpg` und wählen Sie **Freigegebene Zugriffssignatur abrufen**.

![Azure-Speicher](./images/az20.png){zoomable="yes"}

Unter **Berechtigungen** ist nur **Lesen** erforderlich. Wählen Sie **Erstellen** aus.

![Azure-Speicher](./images/az21.png){zoomable="yes"}

Kopieren Sie Ihre vordefinierte URL für diese Bilddatei für die nächste API-Anfrage an Firefly.

![Azure-Speicher](./images/az22.png){zoomable="yes"}

Zurück in Postman öffnen Sie die Anfrage **POST - Firefly - T2I (styleref) V3**.
Dies wird in &quot;**&quot;**.

![Azure-Speicher](./images/az23.png){zoomable="yes"}

Ersetzen Sie die Platzhalter-URL durch die vordefinierte URL für Ihre Bilddatei und wählen Sie **Senden**.

![Azure-Speicher](./images/az24.png){zoomable="yes"}

Öffnen Sie das neue Firefly Services-Antwortbild in Ihrem Browser.

![Azure-Speicher](./images/az25.png){zoomable="yes"}

Mit `horses in a field` wird ein weiteres Bild angezeigt, aber dieses Mal ähnelt der Stil der Bilddatei, die Sie als Stilreferenz bereitgestellt haben.

![Azure-Speicher](./images/az26.png){zoomable="yes"}

## Programmgesteuertes 1.1.2.6 von Dateien

Um den programmgesteuerten Datei-Upload mit Azure Storage-Konten zu verwenden, müssen Sie ein neues **Shared Access Signature (SAS)-** mit Berechtigungen erstellen, die Ihnen das Schreiben einer Datei ermöglichen.

Klicken Sie im Azure Storage Explorer mit der rechten Maustaste auf Ihren Container und wählen Sie **Freigegebene Zugriffssignatur abrufen**.

![Azure-Speicher](./images/az27.png){zoomable="yes"}

Wählen **unter** die folgenden erforderlichen Berechtigungen aus:

- **Lesen**
- **Hinzufügen**
- **Create**
- **Write**
- **Liste**

Wählen Sie **Erstellen** aus.

![Azure-Speicher](./images/az28.png){zoomable="yes"}

Nachdem Sie Ihre **Shared Access Signature** erhalten haben, wählen Sie **Kopieren** aus, um die URL zu kopieren.

![Azure-Speicher](./images/az29.png){zoomable="yes"}

Verwenden Sie die **SAS-Token-URL**, um eine Datei in Ihr Azure-Speicherkonto hochzuladen.

Zurück in Postman, wählen Sie den Ordner **FF - Firefly Services Tech Insiders** und dann **…** im Ordner **Firefly** aus und klicken Sie dann auf **Anfrage hinzufügen**.

![Azure-Speicher](./images/az30.png){zoomable="yes"}

Ändern Sie den Namen der leeren Anfrage in **Datei in Azure-Speicherkonto hochladen** ändern Sie den **Anfragetyp** in **PUT** und fügen Sie die SAS-Token-URL in den URL-Abschnitt ein und wählen Sie dann **body**.

![Azure-Speicher](./images/az31.png){zoomable="yes"}

Wählen Sie anschließend eine Datei auf Ihrem lokalen Computer aus oder verwenden Sie eine andere Bilddatei [hier](./images/gradient2-p.jpg){target="_blank"}.

![Verlaufsdatei](./images/gradient2-p.jpg)

Wählen **Hauptteil** die Option **Binär** dann **Datei auswählen** und wählen Sie dann **+ Neue Datei vom lokalen Computer aus**.

![Azure-Speicher](./images/az32.png){zoomable="yes"}

Wählen Sie die gewünschte Datei aus und klicken Sie auf **Öffnen**.

![Azure-Speicher](./images/az33.png){zoomable="yes"}

Geben Sie als Nächstes den Dateinamen an, der in Ihrem Azure-Speicherkonto verwendet werden soll, indem Sie den Cursor vor das Fragezeichen **setzen?** in der URL wie folgt aus:

![Azure-Speicher](./images/az34.png){zoomable="yes"}

Die URL sieht derzeit wie folgt aus, muss jedoch geändert werden.

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03...`

Ändern Sie den Dateinamen in `gradient2-p.jpg` und ändern Sie die URL so, dass sie den Dateinamen wie folgt enthält:

`https://vangeluw.blob.core.windows.net/vangeluw/gradient2-p.jpg?sv=2023-01-03...`

![Azure-Speicher](./images/az34a.png){zoomable="yes"}

Gehen Sie dann zu **Headers**, um einen neuen Header wie den folgenden manuell hinzuzufügen:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `x-ms-blob-type` | `BlockBlob` |


![Azure-Speicher](./images/az35.png){zoomable="yes"}

Wechseln Sie zu **Autorisierung** und legen Sie **Auth-Typ** auf **Keine Autorisierung** fest und wählen Sie **Senden**.

![Azure-Speicher](./images/az36.png){zoomable="yes"}

Als Nächstes wird diese leere Antwort in Postman angezeigt, was bedeutet, dass Ihr Datei-Upload gut ist.

![Azure-Speicher](./images/az37.png){zoomable="yes"}

Aktualisieren Sie im Azure Storage Explorer den Inhalt Ihres Ordners, und die neu hochgeladene Datei wird angezeigt.

![Azure-Speicher](./images/az38.png){zoomable="yes"}

## 1.1.2.7 Verwendung der programmgesteuerten Datei

Um langfristig programmgesteuert Dateien aus Azure Storage-Konten lesen zu können, müssen Sie ein neues **Shared Access Signature (SAS)-Token** Berechtigungen erstellen, mit denen Sie eine Datei lesen können. Technisch gesehen könnten Sie das in der vorherigen Übung erstellte SAS-Token verwenden, aber es empfiehlt sich, ein separates Token mit nur **Lese**-Berechtigungen und ein separates Token mit nur **Schreib**-Berechtigungen zu verwenden.

### Langfristiges SAS-Token lesen

Gehen Sie zurück zum Azure Storage-Explorer, klicken Sie mit der rechten Maustaste auf Ihren Container und wählen Sie **Freigegebene Zugriffssignatur abrufen**.

![Azure-Speicher](./images/az27.png){zoomable="yes"}

Wählen **unter** die folgenden erforderlichen Berechtigungen aus:

- **Lesen**
- **Liste**

Legen Sie **Ablaufzeit** auf einen Zeitraum von 1 Jahr fest.

Wählen Sie **Erstellen** aus.

![Azure-Speicher](./images/az100.png){zoomable="yes"}

Kopieren Sie die URL und schreiben Sie sie in eine Datei auf Ihrem Computer, um Ihr langfristiges SAS-Token mit Leseberechtigung zu erhalten.

![Azure-Speicher](./images/az101.png){zoomable="yes"}

Ihre URL sollte wie folgt aussehen:

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

Sie können aus der obigen URL mehrere Werte ableiten:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

### Langfristiges SAS-Token schreiben

Gehen Sie zurück zum Azure Storage-Explorer, klicken Sie mit der rechten Maustaste auf Ihren Container und wählen Sie **Freigegebene Zugriffssignatur abrufen**.

![Azure-Speicher](./images/az27.png){zoomable="yes"}

Wählen **unter** die folgenden erforderlichen Berechtigungen aus:

- **Lesen**
- **Liste**
- **Hinzufügen**
- **Create**
- **Write**

Legen Sie die **Ablaufzeit** auf ein Jahr fest.

Wählen Sie **Erstellen** aus.

![Azure-Speicher](./images/az102.png){zoomable="yes"}

Kopieren Sie die URL und schreiben Sie sie in eine Datei auf Ihrem Computer, um Ihr langfristiges SAS-Token mit Lese-/Schreibberechtigungen zu erhalten.

![Azure-Speicher](./images/az103.png){zoomable="yes"}

Ihre URL sollte wie folgt aussehen:

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Sie können aus der obigen URL mehrere Werte ableiten:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

### Variablen in Postman

Wie Sie im obigen Abschnitt sehen können, gibt es einige allgemeine Variablen sowohl im Lese- als auch im Schreib-Token.

Als Nächstes müssen Sie Variablen in Postman erstellen, die die verschiedenen Elemente der oben genannten SAS-Token speichern. Es gibt einige Werte, die in beiden URLs identisch sind:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Für zukünftige API-Interaktionen ändert sich hauptsächlich der Asset-Name, während die oben genannten Variablen unverändert bleiben. In diesem Fall ist es sinnvoll, Variablen in Postman zu erstellen, sodass Sie sie nicht jedes Mal manuell angeben müssen.

Wählen Sie in Postman **Umgebungen**, öffnen Sie **Alle Variablen** und wählen Sie **Umgebung**.

![Azure-Speicher](./images/az104.png){zoomable="yes"}

Erstellen Sie diese 4 Variablen in der angezeigten Tabelle und geben Sie für die Spalten **Anfangswert** und **Aktueller Wert** Ihre spezifischen persönlichen Werte ein.

- `AZURE_STORAGE_URL`: Ihre URL
- `AZURE_STORAGE_CONTAINER`: Ihr Container-Name
- `AZURE_STORAGE_SAS_READ`: Ihr SAS-Lese-Token
- `AZURE_STORAGE_SAS_WRITE`: Ihr SAS-Schreib-Token

Wählen Sie **Speichern** aus.

![Azure-Speicher](./images/az105.png){zoomable="yes"}

### Variablen in PostBuster

Wie Sie im obigen Abschnitt sehen können, gibt es einige allgemeine Variablen sowohl im Lese- als auch im Schreib-Token.

Als Nächstes müssen Sie Variablen in PostBuster erstellen, die die verschiedenen Elemente der oben genannten SAS-Token speichern. Es gibt einige Werte, die in beiden URLs identisch sind:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Öffnen Sie PostBuster. Wählen Sie **Basisumgebung** und klicken Sie dann auf das Symbol **Bearbeiten**, um die Basisumgebung zu öffnen.

![Azure-Speicher](./images/pbbe1.png)

Anschließend werden 4 leere Variablen angezeigt. Geben Sie hier Ihre Azure Storage-Kontodetails ein.

![Azure-Speicher](./images/pbbe2.png)

Ihre Basisumgebungsdatei sollte jetzt wie folgt aussehen. Klicken Sie auf **Schließen**.

![Azure-Speicher](./images/pbbe3.png)

### Testen der Konfiguration

In einer der vorherigen Übungen sah der **Hauptteil** Ihrer Anfrage **Firefly - T2I (styleref) V3** wie folgt aus:

`"url": "https://vangeluw.blob.core.windows.net/vangeluw/gradient.jpg?sv=2023-01-03&st=2025-01-13T07%3A16%3A52Z&se=2026-01-14T07%3A16%3A00Z&sr=b&sp=r&sig=x4B1XZuAx%2F6yUfhb28hF0wppCOMeH7Ip2iBjNK5A%2BFw%3D"`

![Azure-Speicher](./images/az24.png){zoomable="yes"}

Ändern Sie die URL in:

`"url": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/gradient.jpg{{AZURE_STORAGE_SAS_READ}}"`

Wählen Sie **Senden** aus, um die vorgenommenen Änderungen zu testen.

![Azure-Speicher](./images/az106.png){zoomable="yes"}

Wenn die Variablen richtig konfiguriert waren, wird eine Bild-URL zurückgegeben.

![Azure-Speicher](./images/az107.png){zoomable="yes"}

Öffnen Sie die Bild-URL, um Ihr Bild zu überprüfen.

![Azure-Speicher](./images/az108.jpg)

## Nächste Schritte

Navigieren Sie zu [Arbeiten mit Photoshop-APIs](./ex3.md){target="_blank"}

Zurück zu [Übersicht über Adobe Firefly Services](./firefly-services.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}