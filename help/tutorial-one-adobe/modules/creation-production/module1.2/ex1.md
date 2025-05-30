---
title: Erste Schritte mit Workfront Fusion
description: Erfahren Sie, wie Sie Workfront Fusion und Adobe I/O verwenden, um Adobe Firefly Services-APIs abzufragen
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 42e260e0-8af0-4d71-b634-48c1966bd912
source-git-commit: 4b38b40c47b5c373f74a85261adce46f291303a8
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 1%

---

# 1.2.1 Erste Schritte mit Workfront Fusion

Erfahren Sie, wie Sie Workfront Fusion und Adobe I/O verwenden, um Adobe Firefly Services-APIs abzufragen.

## 1.2.1.1 Neues Szenario erstellen

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Öffnen Sie **Workfront Fusion**.

![WF Fusion](./images/wffusion1.png)

Navigieren Sie zu **Szenarien**.

![WF Fusion](./images/wffusion2.png)

Klicken Sie auf das Symbol **+**, um einen neuen Ordner für Ihre Arbeit zu erstellen.

![WF Fusion](./images/wffusion2a.png)

Benennen Sie den Ordner `--aepUserLdap--` und wählen Sie **Speichern**.

![WF Fusion](./images/wffusion2b.png)

Wählen Sie den Ordner aus und klicken Sie auf **Neues Szenario erstellen**.

![WF Fusion](./images/wffusion3.png)

Ein leeres Szenario wird angezeigt, wählen Sie **Tools** und dann **Mehrere Variablen festlegen** aus.

![WF Fusion](./images/wffusion4.png)

Verschieben Sie das **Uhr**-Symbol auf das neu hinzugefügte **Mehrere Variablen festlegen**.

![WF Fusion](./images/wffusion5.png)

Ihr Bildschirm sollte wie folgt aussehen.

![WF Fusion](./images/wffusion6.png)

Klicken Sie mit der rechten Maustaste auf das Fragezeichen und wählen Sie **Modul löschen**.

![WF Fusion](./images/wffusion7.png)

Klicken Sie anschließend mit der rechten Maustaste auf **Mehrere Variablen festlegen** und wählen Sie **Einstellungen** aus.

![WF Fusion](./images/wffusion8.png)

## 1.2.1.2 Konfigurieren der Adobe I/O-Authentifizierung

Jetzt müssen Sie die Variablen konfigurieren, die zur Authentifizierung bei Adobe I/O erforderlich sind. In der vorherigen Übung haben Sie ein Adobe I/O-Projekt erstellt. Die Variablen dieses Adobe I/O-Projekts müssen jetzt in Workfront Fusion definiert werden.

Die folgenden Variablen müssen definiert werden:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `CONST_client_id` | Ihre Adobe I/O-Projekt-Client-ID |
| `CONST_client_secret` | Ihr Adobe I/O-Projekt - Client-Geheimnis |
| `CONST_scope` | Ihr Adobe I/O-Projektumfang |

Suchen Sie diese Variablen, indem Sie zu [https://developer.adobe.com/console/projects wechseln ](https://developer.adobe.com/console/projects){target="_blank"} Ihr Adobe I/O-Projekt mit dem Namen `--aepUserLdap-- One Adobe tutorial` öffnen.

![WF Fusion](./images/wffusion9.png)

Wählen Sie in Ihrem Projekt **OAuth Server-zu-Server** aus, um die Werte für die oben genannten Schlüssel anzuzeigen.

![WF Fusion](./images/wffusion10.png)

Mithilfe der oben genannten Schlüssel und Werte können Sie das Objekt **Mehrere Variablen festlegen** konfigurieren. Wählen Sie **Element hinzufügen** aus.

![WF Fusion](./images/wffusion11.png)

Geben Sie den **Variablennamen**: **CONST_CLIENT_ID** und **Variablenwert** ein und wählen Sie **Hinzufügen**.

![WF Fusion](./images/wffusion12.png)

Wählen Sie **Element hinzufügen** aus.

![WF Fusion](./images/wffusion13.png)

Geben Sie **Variablenname**: **CONST_CLIENT_SECRET** und **Variablenwert** ein und wählen Sie **Hinzufügen**.

![WF Fusion](./images/wffusion14.png)

Wählen Sie **Element hinzufügen** aus.

![WF Fusion](./images/wffusion15.png)

Geben Sie **Variablenname**: **CONST_scope** und den **Variablenwert** ein und wählen Sie **Hinzufügen**.

![WF Fusion](./images/wffusion16.png)

Klicken Sie **OK**.

![WF Fusion](./images/wffusion17.png)

Bewegen Sie den Mauszeiger über **Mehrere Variablen festlegen** und wählen Sie das große **+**-Symbol aus, um ein weiteres Modul hinzuzufügen.

![WF Fusion](./images/wffusion18.png)

Ihr Bildschirm sollte wie folgt aussehen.

![WF Fusion](./images/wffusion19.png)

Geben Sie in der Suchleiste &quot;**&quot;**. Wählen Sie **HTTP** aus, um es zu öffnen.

![WF Fusion](./images/wffusion21.png)

Wählen Sie **Anfrage stellen** aus.

![WF Fusion](./images/wffusion20.png)

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `URL` | `https://ims-na1.adobelogin.com/ims/token/v3` |
| `Method` | `POST` |
| `Body Type` | `x-www-form-urlencoded` |

Wählen Sie **Element hinzufügen** aus.

![WF Fusion](./images/wffusion22.png)

Fügen Sie Elemente für jeden der folgenden Werte hinzu:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `client_id` | Ihre vordefinierte Variable für `CONST_client_id` |
| `client_secret` | Ihre vordefinierte Variable für `CONST_client_secret` |
| `scope` | Ihre vordefinierte Variable für `CONST_scope` |
| `grant_type` | `client_credentials` |

Konfiguration für `client_id`:

![WF Fusion](./images/wffusion23.png)

Konfiguration für `client_secret`.

![WF Fusion](./images/wffusion25.png)

Konfiguration für `scope`.

![WF Fusion](./images/wffusion26.png)

Konfiguration für `grant_type`.

![WF Fusion](./images/wffusion28.png)

Scrollen Sie nach unten und aktivieren Sie das Kontrollkästchen für **Antwort analysieren**. Klicken Sie **OK**.

![WF Fusion](./images/wffusion27.png)

Ihr Bildschirm sollte wie folgt aussehen. Wählen Sie **Einmal ausführen** aus.

![WF Fusion](./images/wffusion29.png)

Nach Ausführung des Szenarios sollte Ihr Bildschirm wie folgt aussehen:

![WF Fusion](./images/wffusion30.png)

Wählen Sie das **Fragezeichen** auf dem Objekt **Mehrere Variablen festlegen** um zu sehen, was bei der Ausführung dieses Objekts passiert ist.

![WF Fusion](./images/wffusion31.png)

Wählen Sie das Symbol **Fragezeichen** auf dem Objekt **HTTP -** erstellen) aus, um zu sehen, was bei der Ausführung dieses Objekts passiert ist. In **OUTPUT** wird das **access_token** von Adobe I/O zurückgegeben.

![WF Fusion](./images/wffusion32.png)

Bewegen Sie den Mauszeiger über **HTTP - Eine Anfrage stellen** und wählen Sie das Symbol **+** aus, um ein weiteres Modul hinzuzufügen.

![WF Fusion](./images/wffusion33.png)

Suchen Sie in der Suchleiste nach `tools`. Wählen Sie **Tools** aus.

![WF Fusion](./images/wffusion34.png)

Wählen Sie **Mehrere Variablen festlegen** aus.

![WF Fusion](./images/wffusion35.png)

Wählen Sie **Element hinzufügen** aus.

![WF Fusion](./images/wffusion36.png)

Legen Sie **Variablenname** auf `bearer_token` fest. Wählen Sie `access_token` als dynamischen **Variablenwert**. Wählen Sie **Hinzufügen** aus.

![WF Fusion](./images/wffusion37.png)

Ihr Bildschirm sollte wie folgt aussehen. Klicken Sie **OK**.

![WF Fusion](./images/wffusion38.png)

Wählen **erneut** Einmal ausführen“ aus.

![WF Fusion](./images/wffusion39.png)

Wählen Sie nach Ausführung des Szenarios das Symbol **Fragezeichen** im letzten Objekt **Mehrere Variablen festlegen** aus. Sie sollten sehen, dass das Zugriffstoken in der Variablen `bearer_token` gespeichert wird.

![WF Fusion](./images/wffusion40.png)

Klicken Sie anschließend mit der rechten Maustaste auf das erste Objekt **Mehrere Werte festlegen** und wählen Sie **Umbenennen**.

![WF Fusion](./images/wffusion41.png)

Legen Sie den Namen auf **Initialisierungskonstanten** fest. Klicken Sie **OK**.

![WF Fusion](./images/wffusion42.png)

Benennen Sie das zweite Objekt um **Authentifizieren bei Adobe I/O**. Klicken Sie **OK**.

![WF Fusion](./images/wffusion43.png)

Benennen Sie das dritte Objekt in &quot;**-Token“**. Klicken Sie **OK**.

![WF Fusion](./images/wffusion44.png)

Ihr Bildschirm sollte wie folgt aussehen:

![WF Fusion](./images/wffusion45.png)

Ändern Sie als Nächstes den Namen Ihres Szenarios in `--aepUserLdap-- - Adobe I/O Authentication`.

![WF Fusion](./images/wffusion46.png)

Wählen Sie **Speichern** aus.

![WF Fusion](./images/wffusion47.png)

## Nächste Schritte

Navigieren Sie zu [Verwenden von Adobe-APIs in Workfront Fusion](./ex2.md){target="_blank"}

Zurück zur [Creative-Workflow-Automatisierung mit Workfront Fusion](./automation.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
