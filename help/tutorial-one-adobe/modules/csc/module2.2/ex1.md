---
title: Erste Schritte mit Workfront
description: Erste Schritte mit Workfront
kt: 5342
doc-type: tutorial
exl-id: 7ed76d37-5d3e-49c7-b3d3-ebcfe971896d
source-git-commit: bd46be455f88007174f7e6be9a1ce5f508edc09b
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 2%

---

# 2.2.1 Erste Schritte mit Workfront

Melden Sie sich unter [https://experienceplatform.my.workfront.com/](https://experienceplatform.my.workfront.com/){target="_blank"} bei Adobe Workfront an.

Dann sehen Sie das hier.

![WF](./images/wfb1.png)

## 2.2.1.1 Konfigurieren der AEM Assets-Integration

Klicken Sie auf das 9-Punkte **Hamburger**-Symbol und wählen Sie dann **Setup** aus.

![WF](./images/wfb2.png)

Scrollen Sie im linken Menü nach unten zu **Dokumente** und klicken Sie dann auf **Experience Manager Assets**.

![WF](./images/wfb3.png)

Klicken Sie auf **+ Experience Manager-Integration hinzufügen**.

![WF](./images/wfb4.png)

Verwenden Sie für den Namen Ihrer Integration `--aepUserLdap-- - Citi Signal AEM`.

Öffnen Sie das Dropdown-**** Experience Manager-Repository und wählen Sie Ihre AEM CS-Instanz aus, die `--aepUserLdap-- - Citi Signal` benannt werden soll.

![WF](./images/wfb5.png)

Konfigurieren **unter &quot;**&quot; die folgende Zuordnung:

| Workfront-Feld | Experience Manager Assets-Feld |
| --------------- | ------------------------------ | 
| **Dokument** > **Name** | **wm:documentName** |
| **Projekt** > **Beschreibung** | **wm:projectDescription** |
| **Aufgabe** > **Name** | **wm:taskName** |
| **Aufgabe** > **Beschreibung** | **wm:taskDescription** |

Aktivieren Sie den Schalter für **Objektmetadaten synchronisieren**.

Klicken Sie auf **Speichern**.

![WF](./images/wfb6.png)

Ihre Integration zwischen Workfront und AEM Assets CS ist jetzt konfiguriert.

![WF](./images/wfb7.png)

## 2.2.1.2 Konfigurieren der AEM Sites-Integration

>[!NOTE]
>
>Dieses Plug-in befindet sich derzeit im **Early Access**-Modus und ist noch nicht allgemein verfügbar.
>
>Dieses Plug-in ist möglicherweise bereits mit Ihrer in der Workfront-Instanz installiert. Wenn es bereits installiert ist, können Sie die folgenden Anweisungen lesen, aber Sie müssen dann nichts an Ihrer Konfiguration ändern.

Navigieren Sie zu [https://experience.adobe.com/#/@experienceplatform/aem/extension-manager/universal-editor](https://experience.adobe.com/#/@experienceplatform/aem/extension-manager/universal-editor){target="_blank"}.

Stellen Sie sicher, **der** für dieses Plug-in auf &quot;**&quot;**. Klicken Sie anschließend auf das **Zahnrad**-Symbol.

![WF](./images/wfb8.png)

Es wird ein Popup **Erweiterungskonfiguration** angezeigt. Konfigurieren Sie die folgenden Felder für die Verwendung dieses Plug-ins.

| Schlüssel | Wert |
| --------------- | ------------------------------ | 
| **`IMS_ENV`** | **PROD** |
| **`WORKFRONT_INSTANCE_URL`** | **https://experienceplatform.my.workfront.com** |
| **`SHOW_CUSTOM_FORMS`** | **&#39;{„previewUrl“: true, „publishUrl“: true}&#39;** |

Klicken Sie auf **Speichern**.

![WF](./images/wfb8.png)

Gehen Sie zurück zu Ihrer Workfront-Benutzeroberfläche und klicken Sie auf das 9-Punkte **Hamburger**-Symbol. Wählen Sie **Setup** aus.

![WF](./images/wfb9.png)

Wechseln Sie im linken Menü zu **Benutzerdefinierte Forms** und wählen Sie **Formular**. Klicken Sie auf **+ Neues benutzerdefiniertes Formular**.

![WF](./images/wfb10.png)

Wählen Sie **Aufgabe** aus und klicken Sie auf **Weiter**.

![WF](./images/wfb11.png)

Anschließend wird ein leeres benutzerdefiniertes Formular angezeigt. Geben Sie den `Content Fragment & Integration ID` des Formularnamens ein.

![WF](./images/wfb12.png)

Ziehen Sie ein neues Feld **Einzeiliger Text** per Drag-and-Drop auf die Arbeitsfläche.

![WF](./images/wfb13.png)

Konfigurieren Sie das neue Feld wie folgt:

- **label**: **Inhaltsfragment**
- **Name**: **`aem_workfront_integration_content_fragment`**

![WF](./images/wfb14.png)

Fügen Sie ein neues Feld **Einzeiliger Text** auf der Arbeitsfläche hinzu und konfigurieren Sie das neue Feld wie folgt:

- **label**: **Integrations-ID**
- **Name**: **`aem_workfront_integration_id`**

Klicken Sie auf **Übernehmen**.

![WF](./images/wfb15.png)

Nun müssen Sie ein zweites benutzerdefiniertes Formular konfigurieren. Klicken Sie auf **+ Neues benutzerdefiniertes Formular**.

![WF](./images/wfb10.png)

Wählen Sie **Aufgabe** aus und klicken Sie auf **Weiter**.

![WF](./images/wfb11.png)

Anschließend wird ein leeres benutzerdefiniertes Formular angezeigt. Geben Sie den `Preview & Publish URL` des Formularnamens ein.

![WF](./images/wfb16.png)

Ziehen Sie ein neues Feld **Einzeiliger Text** per Drag-and-Drop auf die Arbeitsfläche.

![WF](./images/wfb17.png)

Konfigurieren Sie das neue Feld wie folgt:

- **label**: **Vorschau-URL**
- **Name**: **`aem_workfront_integration_preview_url`**

![WF](./images/wfb18.png)

Fügen Sie ein neues Feld **Einzeiliger Text** auf der Arbeitsfläche hinzu und konfigurieren Sie das neue Feld wie folgt:

- **label**: **Publish-URL**
- **Name**: **`aem_workfront_integration_publish_url`**

Klicken Sie auf **Übernehmen**.

![WF](./images/wfb19.png)

Anschließend sollten zwei benutzerdefinierte Formulare verfügbar sein.

![WF](./images/wfb20.png)

[Zurück zum Modul 2.2](./workfront.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
