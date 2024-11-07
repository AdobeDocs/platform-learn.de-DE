---
title: Foundation - Echtzeit-Kundenprofil - Erstellen Sie ein eigenes Echtzeit-Kundenprofil - API
description: Foundation - Echtzeit-Kundenprofil - Erstellen Sie ein eigenes Echtzeit-Kundenprofil - API
kt: 5342
doc-type: tutorial
source-git-commit: 7d2f5f842559b2d6d9f115f3993268a4b36a0fe0
workflow-type: tm+mt
source-wordcount: '2637'
ht-degree: 1%

---

# 2.1.3 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - API

In dieser Übung verwenden Sie Postman und Adobe I/O, um Adobe Experience Platform-APIs abzufragen und Ihr eigenes Echtzeit-Kundenprofil anzuzeigen.

## Geschichte

Im Echtzeit-Kundenprofil werden alle Profildaten zusammen mit Ereignisdaten sowie vorhandenen Segmentmitgliedschaften angezeigt. Die angezeigten Daten können von überall kommen, von Adobe-Anwendungen und externen Lösungen. Dies ist die leistungsstärkste Ansicht in Adobe Experience Platform, dem Erlebnissystem der Aufzeichnungen.

Das Echtzeit-Kundenprofil kann von allen Adobe-Applikationen, aber auch von externen Lösungen wie Call Center oder In-store-Clienteling-Apps genutzt werden. Dazu müssen diese externen Lösungen mit den Adobe Experience Platform-APIs verbunden werden.

## 2.1.3.1 Ihre Kennungen

Im Bedienfeld &quot;Profil-Viewer&quot;auf der Website finden Sie mehrere Identitäten. Jede Identität ist mit einem Namespace verknüpft.

![Kundenprofil](./images/identities.png)

Im Röntgen-Bedienfeld können wir vier verschiedene Kombinationen von IDs und Namespaces sehen:

| Identität | Namespace |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID) | 12507560687324495704459439363261812234 |
| Email ID | woutervangeluwe+06022022-01@gmail.com |
| Mobiltelefonnummer | +32473622044+06022022-01 |

Merken Sie sich diese IDs für den nächsten Schritt.

Navigieren Sie mit diesen Kennungen im Hinterkopf zu Postman.

## 2.1.3.2 Adobe I/O-Projekt einrichten

In dieser Übung werden Sie Adobe I/O ziemlich intensiv verwenden, um die APIs von Platform abzufragen. Führen Sie die folgenden Schritte aus, um Adobe I/O einzurichten.

Wechseln Sie zu [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home)

![Adobe I/O Neue Integration](./images/iohome.png)

Wählen Sie oben rechts auf Ihrem Bildschirm die richtige Adobe Experience Platform-Instanz aus. Ihre Instanz ist `--envName--`.

![Adobe I/O Neue Integration](./images/iocomp.png)

Klicken Sie auf **Neues Projekt erstellen**.

![Adobe I/O Neue Integration](./images/adobe_io_new_integration.png) oder
![Adobe I/O Neue Integration](./images/adobe_io_new_integration1.png)

Wählen Sie **+ Zum Projekt hinzufügen** und dann **API** aus.

![Adobe I/O Neue Integration](./images/adobe_io_access_api.png)

Daraufhin sehen Sie Folgendes:

![Adobe I/O Neue Integration](./images/api1.png)

Klicken Sie auf das Symbol **Adobe Experience Platform** .
/images/api2.png)

Klicken Sie auf **Experience Platform API**.

![Adobe I/O Neue Integration](./images/api3.png)

Klicken Sie auf **Weiter**.

![Adobe I/O Neue Integration](./images/next.png)

Jetzt können Sie entscheiden, ob Sie Adobe I/O Ihr Sicherheitsschlüsselpaar generieren lassen oder ein vorhandenes Schlüsselpaar hochladen möchten.

Wählen Sie **Option 1 - Generate a key pair**.

![Adobe I/O Neue Integration](./images/api4.png)

Klicken Sie auf **Generate keypair**.

![Adobe I/O Neue Integration](./images/generate.png)

Du wirst einen Spinner für etwa 30 Sekunden sehen.

![Adobe I/O Neue Integration](./images/spin.png)

Sie sehen dies und Ihr generiertes Keypair wird als ZIP-Datei heruntergeladen: **config.zip**.

Entpacken Sie die Datei **config.zip** auf Ihrem Desktop. Sie sehen, dass sie 2 Dateien enthält:

![Adobe I/O Neue Integration](./images/zip.png)

- **certificate_pub.crt** ist Ihr Zertifikat mit öffentlichem Schlüssel. Aus sicherheitspolitischer Sicht ist dies das Zertifikat, das frei zum Einrichten von Integrationen mit Online-Anwendungen verwendet wird.
- **private.key** ist Ihr privater Schlüssel. Das sollte niemals, niemals mit jemandem geteilt werden. Der private Schlüssel dient zur Authentifizierung bei Ihrer API-Implementierung und sollte ein Geheimnis sein. Wenn Sie Ihren privaten Schlüssel für andere freigeben, können diese auf Ihre Implementierung zugreifen und die API dazu nutzen, schädliche Daten in Platform zu erfassen und alle Daten zu extrahieren, die sich in Platform befinden.

![Adobe I/O Neue Integration](./images/config.png)

Achten Sie darauf, die Datei &quot;**config.zip**&quot;an einem sicheren Speicherort zu speichern, da Sie sie für die nächsten Schritte und den zukünftigen Zugriff auf Adobe I/O- und Adobe Experience Platform-APIs benötigen.

Klicken Sie auf **Weiter**.

![Adobe I/O Neue Integration](./images/next.png)

Sie müssen nun das/die **Produktprofil(e)** für Ihre Integration auswählen.

Wählen Sie die erforderlichen Produktprofile aus.

**FYI**: In Ihrer Adobe Experience Platform-Instanz haben die Produktprofile eine andere Bezeichnung. Sie müssen mindestens ein Produktprofil mit den entsprechenden Zugriffsrechten auswählen, die in der Adobe Admin Console eingerichtet sind.

![Adobe I/O Neue Integration](./images/api9.png)

Klicken Sie auf **Konfigurierte API speichern**.

![Adobe I/O Neue Integration](./images/saveconfig.png)

Du wirst ein paar Sekunden lang einen Spinner sehen.

![Adobe I/O Neue Integration](./images/api10.png)

Als Nächstes sehen Sie Ihre Integration.

![Adobe I/O Neue Integration](./images/api11.png)

Klicken Sie auf die Schaltfläche &quot;**Für Postman herunterladen**&quot;und dann auf &quot;**Dienstkonto (JWT)**&quot;, um eine Postman-Umgebung herunterzuladen (warten Sie, bis die Umgebung heruntergeladen wurde. Dies kann einige Sekunden dauern).

![Adobe I/O Neue Integration](./images/iopm.png)

Scrollen Sie nach unten, bis Sie **Dienstkonto (JWT)** sehen. Dort finden Sie alle Integrationsdetails, die zum Konfigurieren der Integration mit Adobe Experience Platform verwendet werden.

![Adobe I/O Neue Integration](./images/api12.png)

Ihr IO-Projekt hat derzeit einen generischen Namen. Sie müssen Ihrer Integration einen benutzerfreundlichen Namen geben. Klicken Sie auf **Projekt 1** (oder einen ähnlichen Namen), wie angegeben

![Adobe I/O Neue Integration](./images/api13.png)

Klicken Sie auf **Projekt bearbeiten**.

![Adobe I/O Neue Integration](./images/api14.png)

Geben Sie einen Namen und eine Beschreibung für Ihre Integration ein. Als Namenskonvention verwenden wir `AEP API --demoProfileLdap--`. Ersetzen Sie ldap durch Ihren ldap.
Wenn Ihr ldap beispielsweise Vangeluw ist, lautet der Name und die Beschreibung Ihrer Integration AEP API Vangeluw.

Geben Sie `AEP API --demoProfileLdap--` als **Projekttitel** ein. Klicken Sie auf **Speichern**.

![Adobe I/O Neue Integration](./images/api15.png)

Ihre Adobe I/O-Integration ist jetzt abgeschlossen.

![Adobe I/O Neue Integration](./images/api16.png)

## 2.1.3.3 Postman-Authentifizierung für Adobe I/O

Wechseln Sie zu [https://www.getpostman.com/](https://www.getpostman.com/).

Klicken Sie auf **Erste Schritte**.

![Adobe I/O Neue Integration](./images/getstarted.png)

Laden Sie als Nächstes Postman herunter und installieren Sie es.

![Adobe I/O Neue Integration](./images/downloadpostman.png)

Starten Sie nach der Installation von Postman das Programm.

In Postman gibt es zwei Konzepte: Umgebungen und Sammlungen.

- Die Umgebung enthält all Ihre Umgebungsvariablen, die mehr oder weniger konsistent sind. In der Umgebung finden Sie Dinge wie IMSOrg unserer Platform-Umgebung, neben Sicherheitsberechtigungen wie Ihren privaten Schlüssel und andere. Die Umgebungsdatei ist diejenige, die Sie während des Adobe I/O-Setups in der vorherigen Übung heruntergeladen haben. Sie trägt den folgenden Namen: **service.postman_environment.json**.

- Die Sammlung enthält eine Reihe von API-Anfragen, die Sie verwenden können. Wir werden zwei Sammlungen verwenden
   - 1 Sammlung für Authentifizierung an Adobe I/0
   - 1 Sammlung für die Übungen in diesem Modul
   - 1 Sammlung für die Übungen im Real-Time CDP-Modul, für Destination Authoring

Bitte laden Sie die Datei [postman.zip](./../../../assets/postman/postman_profile.zip) auf Ihren lokalen Desktop herunter.

In dieser Datei **postman.zip** finden Sie die folgenden Dateien:

- `_Adobe I-O - Token.postman_collection.json`
- `_Adobe Experience Platform Enablement.postman_collection.json`
- `Destination_Authoring_API.json`

Dekomprimieren Sie die Datei &quot;**postman.zip**&quot;und speichern Sie diese 3 Dateien in einem Ordner auf Ihrem Desktop, zusammen mit der von Adobe I/O heruntergeladenen Postman-Umgebung. Sie müssen diese 4 Dateien in diesem Ordner haben:

![Adobe I/O Neue Integration](./images/pmfolder.png)

Gehen Sie zurück zu Postman. Klicken Sie auf **Importieren**.

![Adobe I/O Neue Integration](./images/postmanui.png)

Klicken Sie auf **Dateien hochladen**.

![Adobe I/O Neue Integration](./images/choosefiles.png)

Navigieren Sie zum Ordner auf Ihrem Desktop, in den Sie die 4 heruntergeladenen Dateien extrahiert haben. Wählen Sie diese 4 Dateien gleichzeitig aus und klicken Sie auf **Öffnen**.

![Adobe I/O Neue Integration](./images/selectfiles.png)

Nachdem Sie auf **Öffnen** geklickt haben, wird Ihnen in Postman ein Überblick über die Umgebung und Sammlungen angezeigt, die Sie importieren möchten. Klicken Sie auf **Importieren**.

![Adobe I/O Neue Integration](./images/impconfirm.png)

Sie haben jetzt alles, was Sie in Postman benötigen, um über die APIs mit Adobe Experience Platform zu interagieren.

Zunächst müssen Sie sicherstellen, dass Sie ordnungsgemäß authentifiziert sind. Um authentifiziert zu werden, müssen Sie ein Zugriffstoken anfordern.

Stellen Sie sicher, dass Sie die richtige Umgebung ausgewählt haben, bevor Sie eine Anforderung ausführen. Sie können die aktuell ausgewählte Umgebung überprüfen, indem Sie die Dropdown-Liste Umgebung oben rechts überprüfen.

Die ausgewählte Umgebung sollte einen ähnlichen Namen haben:

![Postman](./images/envselemea.png)

Klicken Sie auf das Symbol **eye** und dann auf **Bearbeiten** , um den privaten Schlüssel in der Umgebungsdatei zu aktualisieren.

![Postman](./images/gear.png)

Dann wirst du das sehen. Alle Felder sind vorausgefüllt, mit Ausnahme des Felds **PRIVATE_KEY**.

![Postman](./images/pk2.png)

Der private Schlüssel wurde beim Erstellen Ihres Adobe I/O-Projekts generiert. Sie wurde als ZIP-Datei mit dem Namen **config.zip** heruntergeladen. Extrahieren Sie diese ZIP-Datei auf Ihren Desktop.

![Postman](./images/pk3.png)

Öffnen Sie den Ordner **config** und öffnen Sie die Datei **private.key** mit Ihrem gewünschten Texteditor.

![Postman](./images/pk4.png)

Sie sehen dann etwas, das diesem ähnelt, kopieren Sie den gesamten Text in die Zwischenablage.

![Postman](./images/pk5.png)

Gehen Sie zurück zu Postman und fügen Sie den privaten Schlüssel in die Felder neben der Variablen **PRIVATE_KEY** ein. Dies gilt sowohl für die Spalten **INITIAL VALUE** als auch für den Wert **CURRENT VALUE**. Klicken Sie auf **Speichern**.

![Postman](./images/pk6.png)

Ihre Postman-Umgebung und -Sammlungen sind jetzt konfiguriert und funktionieren. Sie können sich jetzt von Postman zu Adobe I/O authentifizieren.

Dazu müssen Sie eine externe Bibliothek laden, die für die Verschlüsselung und Entschlüsselung der Kommunikation sorgt. Um diese Bibliothek zu laden, müssen Sie die Anfrage mit dem Namen **INIT: Crypto Library für RS256 laden** ausführen. Wählen Sie diese Anforderung in der Sammlung **_Adobe I/O - Token** aus, und Sie sehen sie in der Mitte Ihres Bildschirms.

![Postman](./images/iocoll.png)

![Postman](./images/cryptolib.png)

Klicken Sie auf die blaue Schaltfläche **Senden**. Nach einigen Sekunden sollte eine Antwort im Abschnitt **Hauptteil** von Postman angezeigt werden:

![Postman](./images/cryptoresponse.png)

Nachdem die Kryptobibliothek jetzt geladen ist, können wir uns beim Adobe I/O authentifizieren.

Wählen Sie in der Sammlung **\_Adobe I/O - Token** die Anforderung mit dem Namen **IMS: JWT Generate + Auth** aus. Auch hier werden die Anfragedetails in der Mitte des Bildschirms angezeigt.

![Postman](./images/ioauth.png)

Klicken Sie auf die blaue Schaltfläche **Senden**. Nach einigen Sekunden sollte eine Antwort im Abschnitt **Hauptteil** von Postman angezeigt werden:

![Postman](./images/ioauthresp.png)

Wenn Ihre Konfiguration erfolgreich war, sollte eine ähnliche Antwort mit den folgenden Informationen angezeigt werden:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| token_type | **bearer** |
| access_token | **eyJ4NXUiJpbXNfbmEx...QT7mqZkumN1tdsPEioOEl4087Dg** |
| expires_in | **86399973** |

Adobe I/O hat Ihnen ein **bearer**-Token mit einem bestimmten Wert (diesem sehr langen access_token) und einem Ablauffenster gegeben.

Das Token, das wir erhalten haben, gilt nun für 24 Stunden. Das bedeutet, dass Sie nach 24 Stunden ein neues Token generieren müssen, indem Sie diese Anfrage erneut ausführen, wenn Sie Postman zur Authentifizierung bei Adobe I/O verwenden möchten.

## 2.1.3.4 Echtzeit-Kundenprofil-API, Schema: Profil

Jetzt können Sie Ihre erste Anfrage an die Echtzeit-Kundenprofil-APIs von Platform senden.

Suchen Sie in Postman die Sammlung &quot;**_Adobe Experience Platform Enablement**&quot;.

![Postman](./images/coll_enablement.png)

In **1. Unified Profile Service**: Wählen Sie die erste Anforderung mit dem Namen **UPS - GET Profile by Entity ID &amp; NS** aus.

![Postman](./images/upscall.png)

Für diese Anfrage sind drei erforderliche Variablen erforderlich:

| Schlüssel | Wert | Definition |
|:-------------:| :---------------:| :---------------:| 
| entityId | **id** | die spezifische Kunden-ID |
| entityIdNS | **namespace** | den spezifischen Namespace, der für die ID gilt |
| schema.name | **_xdm.context.profile** | das spezifische Schema, für das Sie Informationen erhalten möchten |

Wenn Sie also die APIs von Adobe Experience Platform bitten möchten, Ihnen alle Profilinformationen für Ihre eigene ECID zurückzugeben, müssen Sie die Anfrage wie folgt konfigurieren:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| entityId | **yourECID** |
| entityIdNS | **ecid** |
| schema.name | **_xdm.context.profile** |

![Postman](./images/callecid.png)

Sie sollten auch die Felder **Kopfzeile** - Ihrer Anforderung überprüfen. Wechseln Sie zu **Kopfzeilen**. Daraufhin sehen Sie Folgendes:

![Postman](./images/callecidheaders.png)

| Schlüssel | Wert |
| ----------- | ----------- |
| x-sandbox-name | `--aepSandboxId--` |

>[!NOTE]
>
>Sie müssen den Namen der verwendeten Adobe Experience Platform-Sandbox angeben. Ihr x-sandbox-name sollte `--aepSandboxId--` sein.

Klicken Sie auf **Senden** , um Ihre Anfrage an Platform zu senden.

Sie sollten eine sofortige Antwort von Platform erhalten, die Ihnen Folgendes zeigt:

![Postman](./images/callecidresponse.png)

Dies ist die vollständige Antwort von Platform:

```javascript
{
    "A28iM3aJBJRbEQpOnUh5HOM9": {
        "entityId": "A28iM3aJBJRbEQpOnUh5HOM9",
        "mergePolicy": {
            "id": "e632ccb8-882a-4b5e-8375-96a1ba3df1aa"
        },
        "sources": [
            "61fe23c5be4b5f19485dc379",
            "profile-streaming-segment",
            "61fe23cfa07c1219489b3ba4"
        ],
        "tags": [
            "1644130566774:1542:232:va7",
            "0a1e9dd4-940a-46ec-9114-7e371cf5c4d0",
            "aep_ups_partitioned_profile_cdc_low_lag_sla_0:106:1090888313",
            "a6fed09e-2c56-403e-8692-4e99e4779dfa:IRL1",
            "1644419616318:2989:31:va7",
            "aep_ups_profile_change_event_prod_va7:71:7946633524-8361f22c-c09e-4364-b24b-b57435c4d14f"
        ],
        "identityGraph": [
            "BUF9zMKLrXq72p4HpbsHv1SSBnr0LTAxQGdtYWlsLmNvbQ",
            "GkicrkFjgmCjUg",
            "GtCbrkFjgkSOFg",
            "A2-AP9zOsakzNTe9Rqwf7Wse",
            "BkFuK4QcJpSPByuSBnr0LTAx",
            "A28jSB484ziuECF3fEoXmFlF",
            "A28iM3aJBJRbEQpOnUh5HOM9"
        ],
        "entity": {
            "_experienceplatform": {
                "individualCharacteristics": {},
                "loyaltyDetails": {
                    "level": "Basic",
                    "points": 0
                },
                "identification": {
                    "core": {
                        "phoneNumber": "+32473622044+06022022-01",
                        "email": "woutervangeluwe+06022022-01@gmail.com",
                        "loyaltyId": "5415776",
                        "ecid": "12019606991718502754997192487345616673",
                        "crmId": "1478212"
                    }
                }
            },
            "personalEmail": {
                "address": "woutervangeluwe+06022022-01@gmail.com"
            },
            "_repo": {
                "createDate": "2022-02-06T06:56:06.424Z"
            },
            "testProfile": true,
            "homeAddress": {
                "postalCode": "1831",
                "city": "Diegem",
                "street1": "Culliganlaan 2F"
            },
            "mobilePhone": {
                "number": "+32473622044+06022022-01"
            },
            "segmentMembership": {
                "ups": {
                    "bc999ded-b6d7-40d4-87a7-d3a280b950e3": {
                        "lastQualificationTime": "2022-02-09T20:38:33Z",
                        "status": "exited"
                    },
                    "23b1cd4e-d62f-44bd-8392-3095a33109c4": {
                        "lastQualificationTime": "2022-02-09T20:38:33Z",
                        "status": "exited"
                    },
                    "f0807704-a1c8-4ac4-85dd-60db2fbf18f1": {
                        "lastQualificationTime": "2022-02-09T20:38:33Z",
                        "status": "existing"
                    }
                }
            },
            "person": {
                "name": {
                    "lastName": "Van Geluwe",
                    "firstName": "Wouter"
                },
                "gender": "female",
                "birthDate": "1982-07-08"
            },
            "userActivityRegions": {
                "IRL1": {
                    "captureTimestamp": "2022-02-09T15:21:11Z"
                }
            },
            "identityMap": {
                "email": [
                    {
                        "id": "woutervangeluwe+06022022-01@gmail.com"
                    }
                ],
                "crmid": [
                    {
                        "id": "1478212"
                    }
                ],
                "ecid": [
                    {
                        "id": "12507560687324495704459439363261812234"
                    },
                    {
                        "id": "12019606991718502754997192487345616673"
                    },
                    {
                        "id": "38335942889672702722192106363935964471"
                    }
                ],
                "phone": [
                    {
                        "id": "+32473622044+06022022-01"
                    }
                ],
                "loyaltyid": [
                    {
                        "id": "5415776"
                    }
                ]
            }
        },
        "lastModifiedAt": "2022-02-09T20:38:36Z"
    }
}
```

Dies sind derzeit alle in Platform für diese ECID verfügbaren Profildaten.

Sie müssen die ECID nicht verwenden, um Profildaten vom Echtzeit-Kundenprofil von Platform anzufordern. Sie können zur Anforderung dieser Daten eine beliebige ID in einem Namespace verwenden.

Gehen wir zurück zu Postman und tun so, als wären wir das Callcenter. Senden Sie eine Anfrage an Platform, in der Sie den Namespace von **Telefon** und Ihre Mobiltelefonnummer angeben.

Wenn Sie also die Platform-APIs bitten möchten, Ihnen alle Profilinformationen für ein bestimmtes Telefon zurückzugeben, müssen Sie die Anfrage wie folgt konfigurieren:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| entityId | **Ihre Telefonnummer** |
| entityIdNS | **phone** (Ersetzen Sie ecid durch phone) |
| schema.name | **_xdm.context.profile** |

Wenn Ihre Telefonnummer Sonderzeichen wie **+** enthält, müssen Sie Ihre vollständige Telefonnummer auswählen, mit der rechten Maustaste klicken und auf **EncodeURIComponent** klicken.

![Postman](./images/encodephone.png)

Dann haben Sie Folgendes:

![Postman](./images/callmobilenr.png)

Sie sollten auch die Felder **Kopfzeile** - Ihrer Anforderung überprüfen. Wechseln Sie zu **Kopfzeilen**. Daraufhin sehen Sie Folgendes:

![Postman](./images/callecidheaders.png)

| Schlüssel | Wert |
| ----------- | ----------- |
| x-sandbox-name | `--aepSandboxId--` |

>[!NOTE]
>
>Sie müssen den Namen der verwendeten Adobe Experience Platform-Sandbox angeben. Ihr x-sandbox-name sollte `--aepSandboxId--` sein.

Klicken Sie auf die blaue Schaltfläche **Senden** und überprüfen Sie die Antwort.

![Postman](./images/callmobilenrresponse.png)

Nehmen wir dasselbe für Ihre E-Mail-Adresse vor, indem wir den Namespace von **email** und Ihre E-Mail-Adresse angeben.

Wenn Sie also die APIs von Platform bitten möchten, Ihnen alle Profilinformationen für eine bestimmte E-Mail-Adresse zurückzugeben, müssen Sie die Anfrage wie folgt konfigurieren:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| entityId | **youremail** |
| entityIdNS | **email** (ersetzen Sie Phone durch E-Mail) |
| schema.name | **_xdm.context.profile** |

Wenn Ihre E-Mail-Adresse Sonderzeichen wie **+** enthält, müssen Sie Ihre vollständige E-Mail-Adresse auswählen, mit der rechten Maustaste klicken und auf **EncodeURIComponent** klicken.

![Postman](./images/encodeemail.png)

Dann haben Sie Folgendes:

![Postman](./images/callemail.png)

Sie sollten auch die Felder **Kopfzeile** - Ihrer Anforderung überprüfen. Wechseln Sie zu **Kopfzeilen**. Daraufhin sehen Sie Folgendes:

![Postman](./images/callecidheaders.png)

| Schlüssel | Wert |
| ----------- | ----------- |
| x-sandbox-name | `--aepSandboxId--` |

>[!NOTE]
>
>Sie müssen den Namen der verwendeten Adobe Experience Platform-Sandbox angeben. Ihr x-sandbox-name sollte `--aepSandboxId--` sein.

Klicken Sie auf die blaue Schaltfläche **Senden** und überprüfen Sie die Antwort.

![Postman](./images/callemailresponse.png)

Dies ist eine sehr wichtige Art von Flexibilität, die Marken angeboten wird. Das bedeutet, dass jede Umgebung eine Anfrage mit ihrer eigenen ID und ihrem eigenen Namespace an Platform senden kann, ohne die Komplexität mehrerer Namespaces und IDs verstehen zu müssen.

Beispiel:

- Das Callcenter fordert Daten von Platform mithilfe des Namespace **phone** an.
- Das Treuesystem fordert Daten von Platform mithilfe des Namespace **email** an.
- Online-Anwendungen können den Namespace **ecid** verwenden.

Das Callcenter weiß nicht unbedingt, welche Art von Kennung im Treueprogramm-System verwendet wird, und das Treuesystem weiß nicht unbedingt, welche Art von Kennung von Online-Anwendungen verwendet wird. Jedes einzelne System kann die Informationen verwenden, die es besitzt und versteht, um die benötigten Informationen zu erhalten, wenn es sie benötigt.

## 2.1.3.5 Echtzeit-Kundenprofil-API, Schema: Profil und ExperienceEvent

Nachdem wir die Platform-APIs erfolgreich für Profildaten abgefragt haben, sollten wir nun dasselbe mit ExperienceEvent-Daten tun.

Suchen Sie in Postman die Sammlung &quot;**_Adobe Experience Platform Enablement**&quot;.

![Postman](./images/coll_enablement.png)

In **1. Unified Profile Service**: Wählen Sie die zweite Anforderung mit dem Namen **UPS - GET Profile &amp; EE by Entity ID &amp; NS** aus.

![Postman](./images/upseecall.png)

Für diese Anfrage sind vier erforderliche Variablen erforderlich:

| Schlüssel | Wert | Definition |
|:-------------:| :---------------:|  :---------------:| 
| schema.name | **_xdm.context.experienceEvent** | das spezifische Schema, für das Sie Informationen erhalten möchten. In diesem Fall suchen wir nach Daten, die dem ExperienceEvent-Schema zugeordnet sind. |
| relatedSchema.name | **_xdm.context.profile** | Während wir nach Daten suchen, die dem ExperienceEvent-Schema zugeordnet sind, müssen wir eine Identität angeben, für die wir diese Daten empfangen möchten. Das Schema, das Zugriff auf die Identität hat, ist das Profil-Schema, daher ist das relatedSchema hier das Profil-Schema. |
| relatedEntityId | **id** | spezifische Kunden-ID |
| relatedEntityIdNS | **namespace** | den spezifischen Namespace, der für die ID gilt |

Wenn Sie also die APIs von Platform bitten möchten, Ihnen alle Profilinformationen für Ihren eigenen ecid zurückzugeben, müssen Sie die Anfrage wie folgt konfigurieren:

| Schlüssel | Wert |
|:-------------:| :---------------:| 
| schema.name | **_xdm.context.experienceEvent** |
| relatedSchema.name | **_xdm.context.profile** |
| relatedEntityId | **yourECID** |
| relatedEntityIdNS | **ecid** |

![Postman](./images/eecallecid.png)

Sie sollten auch die Felder **Kopfzeile** - Ihrer Anforderung überprüfen. Wechseln Sie zu **Kopfzeilen**. Daraufhin sehen Sie Folgendes:

![Postman](./images/eecallecidheaders.png)

| Schlüssel | Wert |
| ----------- | ----------- |
| x-sandbox-name | `--aepSandboxId--` |

>[!NOTE]
>
>Sie müssen den Namen der verwendeten Adobe Experience Platform-Sandbox angeben. Ihr x-sandbox-name sollte `--aepSandboxId--` sein.

Klicken Sie auf **Senden** , um Ihre Anfrage an Platform zu senden.

Sie sollten eine sofortige Antwort von Platform erhalten, die Ihnen Folgendes zeigt:

![Postman](./images/eecallecidresponse.png)

Unten finden Sie die vollständige Antwort von Platform. In diesem Beispiel sind acht ExperienceEvents mit der ECID dieses Kunden verknüpft. Sehen Sie sich die folgenden Variablen an, um die verschiedenen Variablen für die Anforderung anzuzeigen, da die folgende Abbildung die direkte Folge Ihrer Konfiguration in Launch in vorherigen Übungen ist.

Wenn das Röntgen-Bedienfeld ExperienceEvent-Informationen anzeigt, verwendet es die folgende Payload, um Informationen wie Produktname (suchen Sie in der unten stehenden Payload nach productName) und Produktbild-URL (suchen Sie in der unten stehenden Payload nach productImageUrl ) zu analysieren und abzurufen.

```javascript
{
    "_page": {
        "orderby": "timestamp",
        "start": "d686ab8a-2d0c-4722-9ff5-bfc1020b0b55-0",
        "count": 31,
        "next": ""
    },
    "children": [
        {
            "relatedEntityId": "A28iM3aJBJRbEQpOnUh5HOM9",
            "entityId": "d686ab8a-2d0c-4722-9ff5-bfc1020b0b55-0",
            "timestamp": 1644127126596,
            "entity": {
                "environment": {
                    "ipV4": "213.118.129.117",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "vangeluw-OCUC",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC"
                    },
                    "webReferrer": {
                        "URL": "https://adobe.okta.com/"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "12507560687324495704459439363261812234"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "12507560687324495704459439363261812234",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "d686ab8a-2d0c-4722-9ff5-bfc1020b0b55-0",
                "placeContext": {
                    "localTime": "2022-02-06T06:58:46.596+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-06T05:58:46.596Z"
            },
            "lastModifiedAt": "2022-02-06T05:59:48Z"
        },
        {
            "relatedEntityId": "A28iM3aJBJRbEQpOnUh5HOM9",
            "entityId": "919a46bf-a591-4c32-9201-b72250d5f5d9-0",
            "timestamp": 1644127129876,
            "entity": {
                "environment": {
                    "ipV4": "213.118.129.117",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "vangeluw-OCUC#",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC#"
                    },
                    "webReferrer": {
                        "URL": "https://adobe.okta.com/"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "12507560687324495704459439363261812234"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "12507560687324495704459439363261812234",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "919a46bf-a591-4c32-9201-b72250d5f5d9-0",
                "placeContext": {
                    "localTime": "2022-02-06T06:58:49.876+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-06T05:58:49.876Z"
            },
            "lastModifiedAt": "2022-02-06T05:59:48Z"
        },
        {
            "relatedEntityId": "A28iM3aJBJRbEQpOnUh5HOM9",
            "entityId": "41a80489-00d4-446c-b456-8cb19c3f309a-0",
            "timestamp": 1644130597134,
            "entity": {
                "environment": {
                    "ipV4": "213.118.129.117",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 1001,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "login",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC/login"
                    },
                    "webReferrer": {
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC/login"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "12507560687324495704459439363261812234"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "12507560687324495704459439363261812234",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "41a80489-00d4-446c-b456-8cb19c3f309a-0",
                "placeContext": {
                    "localTime": "2022-02-06T07:56:37.134+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-06T06:56:37.134Z"
            },
            "lastModifiedAt": "2022-02-06T06:56:38Z"
        },
        {
            "relatedEntityId": "A28jSB484ziuECF3fEoXmFlF",
            "entityId": "8ACC7B6C-2320-4865-B414-3B0CFA01F628",
            "timestamp": 1644419615000,
            "entity": {
                "environment": {
                    "ipV4": "213.118.129.117",
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (iPhone; CPU OS 15_3 like Mac OS X; en_BE)"
                    }
                },
                "eventType": "application.login",
                "_id": "8ACC7B6C-2320-4865-B414-3B0CFA01F628",
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "mobile"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-2L6V"
                    },
                    "identification": {
                        "core": {
                            "ecid": "12019606991718502754997192487345616673",
                            "email": "woutervangeluwe+06022022-01@gmail.com"
                        }
                    }
                },
                "timestamp": "2022-02-09T15:13:35Z",
                "identityMap": {
                    "ECID": [
                        {
                            "id": "12019606991718502754997192487345616673",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                }
            },
            "lastModifiedAt": "2022-02-09T15:13:38Z"
        },
        {
            "relatedEntityId": "A28jSB484ziuECF3fEoXmFlF",
            "entityId": "54F68CE5-E9E1-4AD0-91B1-7B607A9285C4",
            "timestamp": 1644419658000,
            "entity": {
                "environment": {
                    "ipV4": "213.118.129.117",
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (iPhone; CPU OS 15_3 like Mac OS X; en_BE)"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "mobile"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-2L6V"
                    },
                    "identification": {
                        "core": {
                            "ecid": "12019606991718502754997192487345616673"
                        }
                    }
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "12019606991718502754997192487345616673",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "commerce.productViews",
                "_id": "54F68CE5-E9E1-4AD0-91B1-7B607A9285C4",
                "commerce": {
                    "productViews": {
                        "value": 1
                    }
                },
                "productListItems": [
                    {
                        "quantity": 1,
                        "productAddMethod": "Mobile",
                        "_experienceplatform": {
                            "core": {
                                "mainCategory": "Women",
                                "productURL": "product1",
                                "imageURL": "https://contentviewer.s3.amazonaws.com/helium/wh08-white_main.jpg"
                            }
                        },
                        "priceTotal": 42,
                        "name": "Cassia Funnel Sweatshirt",
                        "SKU": "product1",
                        "currencyCode": "USD"
                    }
                ],
                "timestamp": "2022-02-09T15:14:18Z"
            },
            "lastModifiedAt": "2022-02-09T15:14:21Z"
        },
        {
            "relatedEntityId": "A2-AP9zOsakzNTe9Rqwf7Wse",
            "entityId": "bfe26684-bc3b-40c5-9fe5-5aba854c3227-0",
            "timestamp": 1644420036035,
            "entity": {
                "environment": {
                    "ipV4": "193.105.139.131",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "vangeluw-OCUC",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC"
                    },
                    "webReferrer": {
                        "URL": "https://adobe.okta.com/"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "38335942889672702722192106363935964471"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "38335942889672702722192106363935964471",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "bfe26684-bc3b-40c5-9fe5-5aba854c3227-0",
                "placeContext": {
                    "localTime": "2022-02-09T16:20:36.035+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-09T15:20:36.035Z"
            },
            "lastModifiedAt": "2022-02-09T15:20:39Z"
        },
        {
            "relatedEntityId": "A2-AP9zOsakzNTe9Rqwf7Wse",
            "entityId": "0480c434-8fcd-4a80-b298-c561276ac989-0",
            "timestamp": 1644420037078,
            "entity": {
                "environment": {
                    "ipV4": "193.105.139.131",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "vangeluw-OCUC#",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC#"
                    },
                    "webReferrer": {
                        "URL": "https://adobe.okta.com/"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "38335942889672702722192106363935964471"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "38335942889672702722192106363935964471",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "0480c434-8fcd-4a80-b298-c561276ac989-0",
                "placeContext": {
                    "localTime": "2022-02-09T16:20:37.078+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-09T15:20:37.078Z"
            },
            "lastModifiedAt": "2022-02-09T15:20:39Z"
        },
        {
            "relatedEntityId": "A2-AP9zOsakzNTe9Rqwf7Wse",
            "entityId": "6b1b3983-6966-4551-a711-6b6e410fd819-0",
            "timestamp": 1644420045993,
            "entity": {
                "environment": {
                    "ipV4": "193.105.139.131",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "login",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC/login"
                    },
                    "webReferrer": {
                        "URL": "https://adobe.okta.com/"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "38335942889672702722192106363935964471"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "38335942889672702722192106363935964471",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "6b1b3983-6966-4551-a711-6b6e410fd819-0",
                "placeContext": {
                    "localTime": "2022-02-09T16:20:45.993+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-09T15:20:45.993Z"
            },
            "lastModifiedAt": "2022-02-09T15:20:47Z"
        },
        {
            "relatedEntityId": "A2-AP9zOsakzNTe9Rqwf7Wse",
            "entityId": "ae0f3551-7753-4467-8547-8fdbb66c2214-0",
            "timestamp": 1644420058565,
            "entity": {
                "environment": {
                    "ipV4": "193.105.139.131",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC/home"
                    },
                    "webReferrer": {
                        "URL": "https://adobe.okta.com/"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "38335942889672702722192106363935964471",
                            "email": "woutervangeluwe+06022022-01@gmail.com"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "38335942889672702722192106363935964471",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.login",
                "_id": "ae0f3551-7753-4467-8547-8fdbb66c2214-0",
                "placeContext": {
                    "localTime": "2022-02-09T16:20:58.565+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-09T15:20:58.565Z"
            },
            "lastModifiedAt": "2022-02-09T15:20:59Z"
        },
        {
            "relatedEntityId": "A2-AP9zOsakzNTe9Rqwf7Wse",
            "entityId": "5e67a9c9-b201-4e21-bd3a-4d10475f6156-0",
            "timestamp": 1644420058653,
            "entity": {
                "environment": {
                    "ipV4": "193.105.139.131",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "home",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC/home"
                    },
                    "webReferrer": {
                        "URL": "https://adobe.okta.com/"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "38335942889672702722192106363935964471"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "38335942889672702722192106363935964471",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "5e67a9c9-b201-4e21-bd3a-4d10475f6156-0",
                "placeContext": {
                    "localTime": "2022-02-09T16:20:58.653+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-09T15:20:58.653Z"
            },
            "lastModifiedAt": "2022-02-09T15:21:00Z"
        },
        {
            "relatedEntityId": "A2-AP9zOsakzNTe9Rqwf7Wse",
            "entityId": "33253c5a-6a7e-4858-a7d2-4e6d4a1c7901-0",
            "timestamp": 1644420061804,
            "entity": {
                "environment": {
                    "ipV4": "193.105.139.131",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "vangeluw-OCUC",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC"
                    },
                    "webReferrer": {
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC/home"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "38335942889672702722192106363935964471"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "38335942889672702722192106363935964471",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "33253c5a-6a7e-4858-a7d2-4e6d4a1c7901-0",
                "placeContext": {
                    "localTime": "2022-02-09T16:21:01.804+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-09T15:21:01.804Z"
            },
            "lastModifiedAt": "2022-02-09T15:21:03Z"
        },
        {
            "relatedEntityId": "A2-AP9zOsakzNTe9Rqwf7Wse",
            "entityId": "d8e81fb7-6de9-44c1-b9c6-60d93b520209-0",
            "timestamp": 1644420071737,
            "entity": {
                "environment": {
                    "ipV4": "193.105.139.131",
                    "type": "browser",
                    "browserDetails": {
                        "viewportHeight": 969,
                        "viewportWidth": 1920,
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.80 Safari/537.36"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "vangeluw-OCUC",
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC"
                    },
                    "webReferrer": {
                        "URL": "https://builder.adobedemo.com/run/vangeluw-OCUC/home"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-OCUC"
                    },
                    "identification": {
                        "core": {
                            "ecid": "38335942889672702722192106363935964471"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.8.0+2.9.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "38335942889672702722192106363935964471",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "d8e81fb7-6de9-44c1-b9c6-60d93b520209-0",
                "placeContext": {
                    "localTime": "2022-02-09T16:21:11.737+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2022-02-09T15:21:11.737Z"
            },
            "lastModifiedAt": "2022-02-09T15:21:14Z"
        }
    ],
    "_links": {
        "next": {
            "href": ""
        }
    }
}
```

Dies sind derzeit alle verfügbaren ExperienceEvent-Daten in Platform für diese ECID.

Sie müssen die ECID nicht verwenden, um ExperienceEvent-Daten vom Echtzeit-Profil von Adobe Experience Platform anzufordern. Sie können zur Anforderung dieser Daten eine beliebige ID in einem Namespace verwenden.

Nächster Schritt: [2.1.4 Segment erstellen - UI](./ex4.md)

[Zurück zu Modul 2.1](./real-time-customer-profile.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
