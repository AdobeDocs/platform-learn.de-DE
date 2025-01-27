---
title: PostBuster - Adobe-Mitarbeiter
description: PostBuster - Adobe-Mitarbeiter
doc-type: multipage-overview
exl-id: 01e30878-e1a9-4f46-bcf2-0074686ec1b5
source-git-commit: 54303033e23a28c45e9ef6c7a85135b21b3e29dc
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# PostBuster

>[!IMPORTANT]
>
>Die nachfolgenden Hinweise sind nur für Adobe-Mitarbeiter gedacht.

## Installieren von PostBuster

Navigieren Sie zu [https://adobe.service-now.com/esc?id=adb_esc_kb_article&amp;sysparm_article=KB0020542](https://adobe.service-now.com/esc?id=adb_esc_kb_article&amp;sysparm_article=KB0020542).

Klicken Sie hier, um die neueste Version von **PostBuster** herunterzuladen.

![PostBuster](./assets/images/pb1.png)

Laden Sie die richtige Version für Ihr Betriebssystem herunter.

![PostBuster](./assets/images/pb2.png)

Sobald der Download abgeschlossen ist und installiert wurde, öffnen Sie PostBuster. Sie sollten das dann sehen. Klicken Sie **Importieren**.

![PostBuster](./assets/images/pb3.png)

Laden Sie [postbuster.json.zip](./assets/postman/postbuster.json.zip) herunter und extrahieren Sie es auf Ihrem Desktop.

![PostBuster](./assets/images/pbpb.png)

Klicken Sie **Datei wählen**.

![PostBuster](./assets/images/pb4.png)

Wählen Sie die Datei **postbuster.json** aus. Klicken Sie auf **Öffnen**.

![PostBuster](./assets/images/pb5.png)

Sie sollten das dann sehen. Klicken Sie auf **Scannen**.

![PostBuster](./assets/images/pb6.png)

Klicken Sie **Importieren**.

![PostBuster](./assets/images/pb7.png)

Sie sollten das dann sehen. Klicken Sie, um die importierte Sammlung zu öffnen.

![PostBuster](./assets/images/pb8.png)

Jetzt sehen Sie Ihre Sammlung. Sie müssen weiterhin eine Umgebung für einige Umgebungsvariablen konfigurieren.

![PostBuster](./assets/images/pb9.png)

Klicken Sie auf **Basisumgebung** und dann auf das Symbol **Bearbeiten**.

![PostBuster](./assets/images/pb10.png)

Sie sollten das dann sehen.

![PostBuster](./assets/images/pb11.png)

Kopieren Sie den Platzhalter unter der Umgebung und fügen Sie ihn in die **Basisumgebung** ein.

```json
{
	"CLIENT_SECRET": "",
	"API_KEY": "",
	"ACCESS_TOKEN": "",
	"SCOPES": [
		"openid",
		"AdobeID",
		"ff_apis",
		"firefly_api"
	],
	"TECHNICAL_ACCOUNT_ID": "",
	"IMS": "ims-na1.adobelogin.com",
	"IMS_ORG": "",
	"access_token": "",
	"IMS_TOKEN": "",
	"AZURE_STORAGE_URL": "",
	"AZURE_STORAGE_CONTAINER": "",
	"AZURE_STORAGE_SAS_READ": "",
	"AZURE_STORAGE_SAS_WRITE": ""
}
```

Sie sollten dann diese haben.

![PostBuster](./assets/images/pb12.png)

Nachdem Sie das Modul **Firefly-Services** durchlaufen haben, sollte Ihre Umgebung wie folgt aussehen. Sie müssen dies nicht jetzt tun. Dies wird zu einem späteren Zeitpunkt angesprochen.

![PostBuster](./assets/images/pb13.png)

>[!NOTE]
>
>![Tech Insiders](./assets/images/techinsiders.png){width="50px" align="left"}
>
>Wenn Sie Fragen haben oder ein allgemeines Feedback zu künftigen Inhalten geben möchten, wenden Sie sich bitte direkt an Tech Insiders, indem Sie eine E-Mail an **techinsiders@adobe.com senden**.

[Zurück zu „Alle Module“](./overview.md)
