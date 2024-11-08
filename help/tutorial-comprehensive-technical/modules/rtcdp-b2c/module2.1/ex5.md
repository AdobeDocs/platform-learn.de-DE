---
title: Foundation - Echtzeit-Kundenprofil - Erstellen eines Segments - API
description: Foundation - Echtzeit-Kundenprofil - Erstellen eines Segments - API
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 3%

---

# 2.1.5 Segment erstellen - API

In dieser Übung verwenden Sie Postman und Adobe I/O, um ein Segment zu erstellen und die Ergebnisse dieses Segments als Datensatz zu speichern, indem Sie Adobe Experience Platform-APIs verwenden.

## Geschichte

Im Echtzeit-Kundenprofil werden alle Profildaten zusammen mit Ereignisdaten und vorhandenen Segmentmitgliedschaften angezeigt. Die angezeigten Daten können von überall kommen, von Adobe-Anwendungen und externen Lösungen. Dies ist die leistungsstärkste Ansicht in Adobe Experience Platform, dem Erlebnissystem der Aufzeichnungen.

## 2.1.5.1 - Erstellen eines Segments über die Platform-API

Navigieren Sie zu Postman.

Suchen Sie die Sammlung: **_Adobe Experience Platform-Aktivierung**. In dieser Sammlung wird der Ordner **2 angezeigt. Segmentierung**. Wir werden diese Anfragen in dieser Übung nutzen.

![Segmentierung](./images/pmdtl.png)

Als Nächstes führen wir alle erforderlichen Schritte aus, um ein Segment über die API zu erstellen. Wir werden ein einfaches Segment erstellen: &quot;**ldap** - Alle weiblichen Kunden&quot;.

### Schritt 1: Erstellen einer Segmentdefinition

Klicken Sie auf die Anforderung **Schritt 1 - Profil: Segmentdefinition erstellen**.

![Segmentierung](./images/s1_call.png)

Wechseln Sie zum Abschnitt **Hauptteil** dieser Anfrage.

![Segmentierung](./images/s1_body.png)

Im **Hauptteil** dieser Anfrage sehen Sie Folgendes:

![Segmentierung](./images/s1_bodydtl.png)

Die für diese Anfrage verwendete Sprache heißt Profile Query Language oder **PQL**.

Weitere Informationen und Dokumentationen zu PQL [finden Sie hier](https://experienceleague.adobe.com/docs/experience-platform/segmentation/pql/overview.html?lang=de).


Achtung: Aktualisieren Sie die Variable **name** in der folgenden Anfrage, indem Sie **ldap** durch Ihre spezifische **ldap** ersetzen.

```json
{
    "name" : "ldap - API - All Female Customer",
    "expression" : {"type":"PQL", "format":"pql/json", "value":"{\"nodeType\":\"fnApply\",\"fnName\":\"in\",\"params\":[{\"nodeType\":\"fieldLookup\",\"fieldName\":\"gender\",\"object\":{\"nodeType\":\"fieldLookup\",\"fieldName\":\"person\",\"object\":{\"nodeType\":\"literal\",\"literalType\":\"XDMObject\",\"value\":\"profile\"}}},{\"literalType\":\"List\",\"nodeType\":\"literal\",\"value\":[\"female\"]}]}"},
    "createdBy": "ldap",
    "schema" : { "name" : "_xdm.context.profile"},
    "ttlInDays" : 90
}
```

Nach dem Hinzufügen Ihres spezifischen **ldap** sollte der Hauptteil in etwa wie folgt aussehen:

```json
{
    "name" : "vangeluw - API - All Female Customer",
    "expression" : {"type":"PQL", "format":"pql/json", "value":"{\"nodeType\":\"fnApply\",\"fnName\":\"in\",\"params\":[{\"nodeType\":\"fieldLookup\",\"fieldName\":\"gender\",\"object\":{\"nodeType\":\"fieldLookup\",\"fieldName\":\"person\",\"object\":{\"nodeType\":\"literal\",\"literalType\":\"XDMObject\",\"value\":\"profile\"}}},{\"literalType\":\"List\",\"nodeType\":\"literal\",\"value\":[\"female\"]}]}"},
    "createdBy": "vangeluw",
    "schema" : { "name" : "_xdm.context.profile"},
    "ttlInDays" : 90
}
```

Sie sollten auch die Felder **Kopfzeile** - Ihrer Anforderung überprüfen. Wechseln Sie zu **Kopfzeilen**. Daraufhin sehen Sie Folgendes:

![Postman](./images/s1_h.png)

| Schlüssel | Wert |
| -------------- | ------------------ |
| x-sandbox-name | `--aepSandboxName--` |

>[!NOTE]
>
>Sie müssen den Namen der verwendeten Adobe Experience Platform-Sandbox angeben. Ihr x-sandbox-name sollte `--aepSandboxName--` sein.

Klicken Sie nun auf die blaue Schaltfläche **Senden** , um das Segment zu erstellen und die Ergebnisse anzuzeigen.

![Segmentierung](./images/s1_bodydtl_results.png)

Nach diesem Schritt können Sie Ihre Segmentdefinition in der Platform-Benutzeroberfläche anzeigen. Um dies zu überprüfen, melden Sie sich bei Adobe Experience Platform an und navigieren Sie zu **Segmente**.

![Segmentierung](./images/s1_segmentdef.png)

### Schritt 2: Erstellen eines Auftrags für die SegmentPOST

In der vorherigen Übung haben Sie ein _Streaming_ -Segment erstellt. Ein Streaming-Segment bewertet kontinuierlich Qualifikationen in Echtzeit. Hier erstellen Sie ein Segment vom Typ _batch_ . Das Batch-Segment gibt Ihnen eine Vorschau darüber, wie das Segment in Bezug auf Qualifikationen aussehen könnte, aber _das nicht bedeutet, dass das Segment tatsächlich ausgeführt wurde_. Derzeit qualifiziert sich _keiner für dieses Segment_. Um Personen zu qualifizieren, muss das Batch-Segment ausgeführt werden, was wir hier tun werden.

POST eines Segmentauftrags

Navigieren Sie zu Postman.

![Segmentierung](./images/pmdtl.png)

Klicken Sie in Ihrer Postman-Sammlung auf die Anforderung **Schritt 2 - POST-Segmentauftrag** , um sie zu öffnen.

![Segmentierung](./images/s2_call.png)

Sie sollten auch die Felder **Kopfzeile** - Ihrer Anforderung überprüfen. Wechseln Sie zu **Kopfzeilen**. Daraufhin sehen Sie Folgendes:

![Postman](./images/s2headers.png)

| Schlüssel | Wert |
| -------------- | ------------------ |
| x-sandbox-name | `--aepSandboxName--` |

>[!NOTE]
>
>Sie müssen den Namen der verwendeten Adobe Experience Platform-Sandbox angeben. Ihr x-sandbox-name sollte `--aepSandboxName--` sein.

Klicken Sie auf die blaue Schaltfläche **Senden**.

Sie sollten ein ähnliches Ergebnis sehen:

![Segmentierung](./images/s2_call_response.png)

Dieser Segmentauftrag wird jetzt ausgeführt, was einige Zeit in Anspruch nehmen kann. In Schritt 3 können Sie den Status dieses Auftrags überprüfen.


### Schritt 3: Status des GET-Segmentauftrags

Navigieren Sie zu Postman.

![Segmentierung](./images/pmdtl.png)

Klicken Sie in Ihrer Postman-Sammlung auf die Anforderung mit dem Namen **Schritt 3 - GET-Segmentauftragsstatus**.

![Segmentierung](./images/s3_call.png)

Sie sollten auch die Felder **Kopfzeile** - Ihrer Anforderung überprüfen. Wechseln Sie zu **Kopfzeilen**. Daraufhin sehen Sie Folgendes:

![Postman](./images/s3headers.png)

| Schlüssel | Wert |
| -------------- | ------------------ |
| x-sandbox-name | `--aepSandboxName--` |

>[!NOTE]
>
>Sie müssen den Namen der verwendeten Adobe Experience Platform-Sandbox angeben. Ihr x-sandbox-name sollte `--aepSandboxName--` sein.

Klicken Sie auf die blaue Schaltfläche **Senden**.

Sie sollten ein ähnliches Ergebnis sehen:

![Segmentierung](./images/s3_status.png)

In diesem Beispiel ist der **Status** des Auftrags auf **QUEUED** festgelegt.

Wiederholen Sie diese Anfrage, indem Sie alle paar Minuten auf die blaue Schaltfläche **Senden** klicken, bis für den **status** der Wert **SUCCEEDED** festgelegt ist.

![Segmentierung](./images/s3_status_succeeded.png)

Sobald der Status **ERFOLGT** lautet, wurde Ihr Segmentauftrag ausgeführt und Kunden qualifizieren sich jetzt für das Segment.

Herzlichen Glückwunsch, Sie haben die Segmentierungsübung erfolgreich abgeschlossen. Sehen wir uns nun an, wie das Echtzeit-Kundenprofil im gesamten Unternehmen aktiviert werden kann.

Nächster Schritt: [2.1.6 Anzeigen des Echtzeit-Kundenprofils in Aktion im Callcenter](./ex6.md)

[Zurück zu Modul 2.1](./real-time-customer-profile.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
