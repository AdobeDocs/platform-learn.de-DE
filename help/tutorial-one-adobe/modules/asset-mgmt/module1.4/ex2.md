---
title: Verwenden Ihrer Dynamic Media-Vorlage mit Adobe Journey Optimizer
description: Verwenden Ihrer Dynamic Media-Vorlage mit Adobe Journey Optimizer
kt: 5342
doc-type: tutorial
source-git-commit: 261475b85bfb15f7e9f630d1c5203732c2d4c254
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 8%

---

# 1.4.2 Verwenden Ihrer Dynamic Media-Vorlage mit Adobe Journey Optimizer

## 1.4.2.1 Erstellen einer Kampagne in Adobe Journey Optimizer

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./images/acoptriglp.png)

Im Folgenden erstellen Sie eine Kampagne. Im Gegensatz zum ereignisbasierten Journey der vorherigen Übung, das auf eingehenden Erlebnisereignissen oder Zielgruppeneintritten oder -austritten beruht, um eine Journey für einen bestimmten Kunden Trigger, richten sich Kampagnen mit einzigartigen Inhalten wie Newslettern, einmaligen Werbeaktionen oder allgemeinen Informationen oder regelmäßig mit ähnlichen Inhalten, die regelmäßig gesendet werden, wie z. B. Geburtstagskampagnen und Erinnerungen.

Gehen Sie im Menü zu **Kampagnen** und klicken Sie auf **Kampagne erstellen**.

![Journey Optimizer](./images/gsemail21.png)

Wählen Sie **Geplant - Marketing** und klicken Sie auf **Erstellen**.

![Journey Optimizer](./images/gsemail22.png)

Konfigurieren Sie im Bildschirm zur Kampagnenerstellung Folgendes:

- **Name**: `--aepUserLdap-- - CitiSignal Fiber Max DM Email Campaign`.

Klicken Sie auf **Aktionen**.

![Journey Optimizer](./images/gsemail23.png)

Klicken Sie auf **+ Aktion hinzufügen** wählen Sie dann **E-Mail** aus.

![Journey Optimizer](./images/gsemail24.png)

Wählen Sie dann eine vorhandene **E-Mail-Konfiguration** und klicken Sie auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/gsemail25.png)

Sie werden es dann sehen. Verwenden Sie für **Betreffzeile** Folgendes:

```
{{profile.person.name.firstName}}, say hello to CitiSignal Fiber Max!
```

Klicken Sie anschließend auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/gsemail26.png)

Wählen Sie **Von Grund auf gestalten**.

![Journey Optimizer](./images/gsemail27.png)

Sie sollten das dann sehen.

![Journey Optimizer](./images/gsemail28.png)

Fügen Sie der **2x :11** Spalte hinzu.

![Journey Optimizer](./images/gsemail29.png)

Wechseln Sie zu **Fragmente**, ziehen Sie das Fragment **Kopfzeile** in die erste :1 Spalte und ziehen Sie dann das Fragment **Fußzeile** in die zweite 1:1 Spalte.

![Journey Optimizer](./images/gsemail30.png)

Fügen Sie eine neue 1:1-Spalte zwischen den 2 Fragmenten hinzu und fügen Sie dann ein **Bild** in diese 1 :1 Spalte ein. Klicken Sie dann auf **Durchsuchen**.

![Journey Optimizer](./images/gsemail31.png)

Navigieren Sie zu dem Ordner, in dem Sie Ihre Dynamic Media-Vorlage gespeichert haben. Wählen Sie Ihre Dynamic Media-Vorlage aus und klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/gsemail32.png)

Sie sollten das dann sehen.

![Journey Optimizer](./images/gsemail33.png)

## Nächste Schritte

Zurück zu [Adobe Experience Manager Assets und Dynamic Media](./aemassetsdm.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
