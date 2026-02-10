---
title: Verwenden Ihrer Dynamic Media-Vorlage mit Adobe Journey Optimizer
description: Verwenden Ihrer Dynamic Media-Vorlage mit Adobe Journey Optimizer
kt: 5342
doc-type: tutorial
exl-id: 0dd499cc-ec3b-42c3-9c08-6512ea5b9377
source-git-commit: 8f746831d4a1481f8ccc14539273c4b16ca5170b
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 9%

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

Sie sollten das dann sehen. Du auch. Beachten Sie **PARAMETER** mit denen Sie die Parameter der Dynamic Media-Vorlage ändern können.

![Journey Optimizer](./images/gsemail33.png)

## 1.4.2.2 Personalisieren der Dynamic Media-Vorlage

Wie in der vorherigen Übung erläutert, muss AJO jetzt dynamisch entscheiden, welche Werte Teil der Dynamic Media-Vorlage werden sollen.

Genau wie im **Vorschau**-Schritt in der vorherigen Übung sollten die Felder **city_paris**, **city_dubai** und **city_ny** auf 1 gesetzt werden, was bedeutet, dass diese Bilder ausgeblendet werden.

Klicken Sie für **Feld** Titel“ auf das Personalisierungssymbol.

![Journey Optimizer](./images/gsemail34.png)

Ersetzen Sie den Standardtext durch: `Hi {{profile.person.name.firstName}}`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/gsemail35.png)

Klicken Sie für **Feld** body) auf das Personalisierungssymbol.

![Journey Optimizer](./images/gsemail36.png)

Ersetzen Sie den Standardtext durch: `CitiSignal is coming to {{profile.homeAddress.city}}!`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/gsemail37.png)

Stellen Sie sicher, dass das Feld **`dynamic_city_hide`** auf 0 gesetzt ist. Klicken Sie auf das Personalisierungssymbol für die **`dynamic_city_image`**.

![Journey Optimizer](./images/gsemail38.png)

Ersetzen Sie den Standardtext durch: `--aepUserLdap--CitiSignalDM/citisignal-fiber-max-is-coming_citisignal-{{profile._experienceplatform.individualCharacteristics.fiber_rollout.closest_rollout_city}}-1`. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/gsemail39.png)

Sie sollten das dann sehen. Das Bild wird hier nicht mehr gerendert. Dies wird erwartet, da die dynamischen Variablen im Kontext des E-Mail-Editors nicht verfügbar sind.

Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/gsemail40.png)

Um Ihre Konfiguration zu testen, klicken Sie auf **Inhalt simulieren** und wählen Sie dann **Inhalt simulieren**.

![Journey Optimizer](./images/gsemail41.png)

Sie sollten dann so etwas sehen. Wenn Sie keine Testprofile zur Verfügung haben, können Sie diese hinzufügen, indem Sie zu **Testprofile verwalten** wechseln.

Sobald Testprofile verfügbar sind, die die zum Testen dieses Anwendungsfalls erforderlichen Daten enthalten, können Sie von einem Profil zum anderen wechseln, um die Änderungen dynamisch anzuzeigen.

Hier ist ein Profil, das mit der Rollout-Stadt New York verknüpft ist.

![Journey Optimizer](./images/gsemail42.png)

Hier ist ein Profil, das mit der Rollout-Stadt Paris verknüpft ist.

![Journey Optimizer](./images/gsemail43.png)

Hier ist ein Profil, das mit der Rollout-Stadt Dubai verknüpft ist.

Klicken Sie auf **Schließen**.

![Journey Optimizer](./images/gsemail44.png)

Sie haben jetzt diese Übung beendet. Sie müssen Ihre E-Mail-Kampagne nicht veröffentlichen.

## Nächste Schritte

Zurück zu [Adobe Experience Manager Assets und Dynamic Media](./aemassetsdm.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}