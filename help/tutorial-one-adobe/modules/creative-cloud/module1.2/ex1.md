---
title: Erste Schritte mit Workfront Fusion
description: Erste Schritte mit Workfront Fusion
kt: 5342
doc-type: tutorial
exl-id: 42e260e0-8af0-4d71-b634-48c1966bd912
source-git-commit: f1f70a0e4ea3f59b5b121275e7db633caf953df9
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 3%

---

# 1.2.1 Erste Schritte mit Workfront Fusion

In dieser Übung verwenden Sie Workfront Fusion und Adobe I/O, um Adobe Firefly Services-APIs abzufragen.

## 1.2.1.1 Neues Szenario erstellen

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/). Klicken, um **Workfront Fusion** zu öffnen.

![WF Fusion](./images/wffusion1.png)

Sie sollten das dann sehen. Navigieren Sie zu **Szenarien**.

![WF Fusion](./images/wffusion2.png)

Klicken Sie auf das Symbol **+** , um einen neuen Ordner zu erstellen.

![WF Fusion](./images/wffusion2a.png)

Verwenden Sie für den Ordnernamen: `--aepUserLdap--`. Klicken Sie auf **Speichern**.

![WF Fusion](./images/wffusion2b.png)

Wählen Sie Ihren Ordner aus und klicken Sie dann auf **Neues Szenario erstellen**.

![WF Fusion](./images/wffusion3.png)

Anschließend sehen Sie ein leeres Szenario. Klicken Sie auf **tools** und wählen Sie **Mehrere Variablen festlegen** aus.

![WF Fusion](./images/wffusion4.png)

Jetzt müssen Sie das Symbol **Uhr** auf das neu hinzugefügte Symbol **Mehrere Variablen festlegen** verschieben.

![WF Fusion](./images/wffusion5.png)

Sie werden es dann sehen.

![WF Fusion](./images/wffusion6.png)

Klicken Sie dann mit der rechten Maustaste auf das Fragezeichen und wählen Sie **Modul löschen**.

![WF Fusion](./images/wffusion7.png)

Klicken Sie anschließend mit der rechten Maustaste auf das Objekt **Mehrere Variablen festlegen** und wählen Sie **Einstellungen** aus.

![WF Fusion](./images/wffusion8.png)

## 1.2.1.2 Konfigurieren der Adobe I/O-Authentifizierung

Nun müssen Sie die Variablen konfigurieren, die für die Authentifizierung beim Adobe I/O benötigt werden. In der vorherigen Übung haben Sie ein Adobe I/O-Projekt erstellt. Die Variablen dieses Adobe I/O-Projekts müssen jetzt in Workfront Fusion definiert werden.

Die folgenden Variablen müssen definiert werden:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `CONST_client_id` | Ihre Adobe I/O-Projekt-Client-ID |
| `CONST_client_secret` | Ihr Adobe I/O-Projekt Client Secret |
| `CONST_scope` | Umfang Ihres Adobe I/O-Projekts |

Sie können diese Variablen finden, indem Sie zu [https://developer.adobe.com/console/projects wechseln ](https://developer.adobe.com/console/projects) Ihr Adobe I/O-Projekt öffnen, das `--aepUserLdap-- Firefly` heißt.

![WF Fusion](./images/wffusion9.png)

Klicken Sie in Ihrem Projekt auf **OAuth Server-zu-Server**, um die Werte für die oben genannten Schlüssel anzuzeigen.

![WF Fusion](./images/wffusion10.png)

Mit den obigen Schlüsseln und Werten können Sie das Objekt **Mehrere Variablen festlegen** konfigurieren. Klicken Sie **Element hinzufügen**.

![WF Fusion](./images/wffusion11.png)

Geben Sie den **Variablennamen**: **CONST_CLIENT_ID** und dessen **Variablenwert** ein und klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion12.png)

Klicken Sie **Element hinzufügen**.

![WF Fusion](./images/wffusion13.png)

Geben Sie den **Variablennamen**: **CONST_CLIENT_SECRET** und dessen **Variablenwert** ein und klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion14.png)

Klicken Sie **Element hinzufügen**.

![WF Fusion](./images/wffusion15.png)

Geben Sie den **Variablennamen**: **CONST_scope** und den **Variablenwert** ein und klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion16.png)

Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion17.png)

Bewegen Sie den Mauszeiger über Ihr **Mehrere Variablen festlegen**-Objekt und klicken Sie auf das große **+**-Symbol, um ein weiteres Modul hinzuzufügen.

![WF Fusion](./images/wffusion18.png)

Sie sollten das dann sehen.

![WF Fusion](./images/wffusion19.png)

Geben Sie in der Suchleiste &quot;**&quot;**. Wählen Sie **HTTP** aus, um es zu öffnen.

![WF Fusion](./images/wffusion21.png)

und wählen Sie dann **Anfrage stellen** aus.

![WF Fusion](./images/wffusion20.png)

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `URL` | `https://ims-na1.adobelogin.com/ims/token/v3` |
| `Method` | `POST` |
| `Body Type` | `x-www-form-urlencoded` |

Klicken Sie **Element hinzufügen**.

![WF Fusion](./images/wffusion22.png)

Fügen Sie Elemente für jeden der folgenden Werte hinzu:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| `client_id` | Ihre vordefinierte Variable für `CONST_client_id` |
| `client_secret` | Ihre vordefinierte Variable für `CONST_client_secret` |
| `scope` | Ihre vordefinierte Variable für `CONST_scope` |
| `grant_type` | `client_credentials` |

Konfiguration für `client_id`.

![WF Fusion](./images/wffusion23.png)

Konfiguration für `client_secret`.

![WF Fusion](./images/wffusion25.png)

Konfiguration für `scope`.

![WF Fusion](./images/wffusion26.png)

Konfiguration für `grant_type`.

![WF Fusion](./images/wffusion28.png)

Konfigurationsübersicht. Scrollen Sie nach unten und aktivieren Sie das Kontrollkästchen für **Antwort analysieren**. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion27.png)

Sie sollten das dann sehen. Klicken Sie **Einmal ausführen**.

![WF Fusion](./images/wffusion29.png)

Sobald das Szenario ausgeführt wurde, sollte Folgendes angezeigt werden.

![WF Fusion](./images/wffusion30.png)

Klicken Sie auf das **Fragezeichen** auf dem Objekt **Mehrere Variablen festlegen** um zu sehen, was bei der Ausführung dieses Objekts passiert ist.

![WF Fusion](./images/wffusion31.png)

Klicken Sie auf das **Fragezeichen** auf dem Objekt **HTTP -** ausführen“, um zu sehen, was beim Ausführen dieses Objekts passiert ist. In **OUTPUT** sehen Sie, dass das **access_token** von Adobe I/O zurückgegeben wird.

![WF Fusion](./images/wffusion32.png)

Bewegen Sie den Mauszeiger über **Objekt „HTTP -**&quot; und klicken Sie auf das Symbol **+** , um ein weiteres Modul hinzuzufügen.

![WF Fusion](./images/wffusion33.png)

Suchen Sie in der Suchleiste nach `tools`. Wählen Sie **Tools** aus.

![WF Fusion](./images/wffusion34.png)

Wählen Sie **Mehrere Variablen festlegen** aus.

![WF Fusion](./images/wffusion35.png)

Wählen Sie **Element hinzufügen** aus.

![WF Fusion](./images/wffusion36.png)

Legen Sie den **Variablennamen** auf `bearer_token` fest. Wählen Sie `access_token` als dynamischen **Variablenwert**. Klicken Sie auf **Hinzufügen**.

![WF Fusion](./images/wffusion37.png)

Sie sollten dann diese haben. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion38.png)

Klicken Sie **erneut auf &quot;** ausführen“.

![WF Fusion](./images/wffusion39.png)

Nachdem das Szenario ausgeführt wurde, klicken Sie auf das Symbol **Fragezeichen** im letzten Objekt **Mehrere Variablen festlegen**. Sie sollten dann sehen, dass das Zugriffs-Token in der Variablen `bearer_token` gespeichert wird.

![WF Fusion](./images/wffusion40.png)

Klicken Sie anschließend mit der rechten Maustaste auf das erste Objekt **Mehrere Werte festlegen** und wählen Sie **Umbenennen**.

![WF Fusion](./images/wffusion41.png)

Legen Sie den Namen auf **Initialisierungskonstanten** fest. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion42.png)

Benennen Sie das zweite Objekt um und legen Sie für den Namen **Authentifizieren für Adobe I/O** fest. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion43.png)

Benennen Sie das dritte Objekt um und setzen Sie den Namen auf **Bearer-Token festlegen**. Klicken Sie auf **OK**.

![WF Fusion](./images/wffusion44.png)

Sie sollten dann diese haben.

![WF Fusion](./images/wffusion45.png)

Ändern Sie als Nächstes den Namen Ihres Szenarios in `--aepUSerLdap-- - Adobe I/O Authentication`.

![WF Fusion](./images/wffusion46.png)

Klicken Sie auf **Speichern**.

![WF Fusion](./images/wffusion47.png)

Nächster Schritt: [1.2.2 Verwenden Sie Adobe-APIs in Workfront Fusion](./ex2.md)

[Zurück zum Modul 1.2](./automation.md)

[Zurück zu „Alle Module“](./../../../overview.md)
