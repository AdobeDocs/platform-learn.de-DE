---
title: AJO und GenStudio for Performance Marketing
description: AJO und GenStudio for Performance Marketing
kt: 5342
doc-type: tutorial
exl-id: 1424f649-d004-4b14-b8af-927ca1d47de5
source-git-commit: 2d5ca888eb24c1f65b4ecd48030ec8d1659b7f84
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 6%

---

# 3.6.3 AJO und GenStudio for Performance Marketing

>[!IMPORTANT]
>
>Um diese Übung abzuschließen, benötigen Sie Zugriff auf eine Adobe Journey Optimizer-Umgebung, die für die Integration mit GenStudio for Performance Marketing bereitgestellt wird, welche sich derzeit in der Beta-Phase befindet.

>[!IMPORTANT]
>
>Um diese Übung abzuschließen, benötigen Sie Zugriff auf eine Instanz, die für Adobe GenStudio for Performance Marketing bereitgestellt wird.

>[!IMPORTANT]
>
>Um alle Schritte in dieser Übung ausführen zu können, benötigen Sie Zugriff auf eine bestehende Adobe Workfront-Umgebung. In dieser Umgebung müssen Sie ein Projekt und einen Genehmigungs-Workflow erstellt haben. Wenn Sie die Übungen [Workflow-Verwaltung mit Adobe Workfront](./../../../../modules/workflow-planning/module1.2/workfront.md){target="_blank"} befolgen, stehen Ihnen die erforderlichen Einstellungen zur Verfügung.

## 1.3.4.1 Erstellen und Genehmigen von E-Mail-Erlebnissen in Adobe GenStudio

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Öffnen Sie **GenStudio**.

![GSPeM](./../../../creation-production/module1.3/images/gspem1.png)

Sie sollten das dann sehen. Navigieren Sie im linken Menü zu **Erstellen**. Wählen Sie **E-Mail** aus.

![GSPeM](./../../../creation-production/module1.3/images/gsemail1.png)

Wählen Sie die **E-Mail**-Vorlage aus, die Sie zuvor importiert haben und die `--aepUserLdap---citisignal-email-template` heißt. Klicken Sie **Verwenden**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail2.png)

Sie sollten das dann sehen. Ändern Sie den Namen Ihrer Anzeige in `--aepUserLdap-- - Email Online Gamers Fiber Max`.

![GSPeM](./../../../creation-production/module1.3/images/gsemail3.png)

Wählen **unter** die folgenden Optionen aus:

- **Marke**: `--aepUserLdap-- - CitiSignal`
- **language**: `English (US)`
- **Persona**: `--aepUserLdap-- - Smart Home Families`
- **Produkt**: `--aepUserLdap-- - CitiSignal Fiber Max`

Klicken Sie **Aus Inhalt auswählen**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail4.png)

Wählen Sie die Asset-`--aepUserLdap-- - neon rabbit.png` aus. Klicken Sie **Verwenden**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail5.png)

Geben Sie den `convince online gamers to start playing online multiplayer games using CitiSignal internet` ein und klicken Sie auf **Generieren**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail6.png)

Sie sollten dann so etwas wie das hier sehen, wobei vier E-Mail-Varianten generiert werden. Die Standardansicht zeigt die Ansicht **Mobiltelefon**. Sie können zur Desktopansicht wechseln, indem Sie auf das Symbol **Computer** klicken.

![GSPeM](./../../../creation-production/module1.3/images/gsemail7.png)

Für jede E-Mail wird automatisch ein Konformitätswert berechnet. Klicken Sie auf die Punktzahl, um weitere Details anzuzeigen.

![GSPeM](./../../../creation-production/module1.3/images/gsemail8.png)

Klicken Sie **Probleme anzeigen und beheben**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail9.png)

Anschließend können Sie mehr Details dazu sehen, was Sie tun können, um den Kompatibilitätswert zu optimieren.

![GSPeM](./../../../creation-production/module1.3/images/gsemail10.png)

Klicken Sie anschließend auf **Genehmigung anfordern**, um eine Verbindung zu Adobe Workfront herzustellen.

![GSPeM](./../../../creation-production/module1.3/images/gsemail11.png)

Wählen Sie Ihr Adobe Workfront-Projekt aus, das `--aepUserLdap-- - CitiSignal Fiber Launch` benannt werden soll. Geben Sie unter **Personen einladen** Ihre eigene E-Mail-Adresse ein und stellen Sie sicher, dass Ihre Rolle auf &quot;**&quot;** ist.

![GSPeM](./../../../creation-production/module1.3/images/gsemail12.png)

Alternativ können Sie auch einen vorhandenen Genehmigungs-Workflow in Adobe Workfront verwenden. Klicken Sie dazu auf **Vorlage verwenden** und wählen Sie die `--aepuserLdap-- - Approval Workflow` aus. Klicken Sie auf **Senden**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail13.png)

Klicken Sie **Kommentare in Workfront anzeigen**, um zur Benutzeroberfläche für den Adobe Workfront-Korrekturabzug weitergeleitet zu werden.

![GSPeM](./../../../creation-production/module1.3/images/gsemail14.png)

Klicken Sie in der Adobe Workfront-Benutzeroberfläche für Korrekturabzüge auf **Entscheidung treffen**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail15.png)

Wählen Sie **Genehmigt** und klicken Sie auf **Entscheidung treffen**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail16.png)

Klicken Sie auf **Veröffentlichen**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail17.png)

Wählen Sie Ihre Campaign-`--aepUserLdap-- - CitiSignal Fiber Launch Campaign` aus und klicken Sie auf **Veröffentlichen**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail18.png)

Klicken Sie **Im Inhalt öffnen**.

![GSPeM](./../../../creation-production/module1.3/images/gsemail19.png)

Die vier E-Mail-Erlebnisse sind jetzt unter **Inhalt** > **Erlebnisse** verfügbar.

![GSPeM](./../../../creation-production/module1.3/images/gsemail20.png)

## 1.3.4.2 Erstellen einer Kampagne in AJO

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

Im Folgenden erstellen Sie eine Kampagne. Im Gegensatz zum ereignisbasierten Journey der vorherigen Übung, das auf eingehenden Erlebnisereignissen oder Zielgruppeneintritten oder -austritten beruht, um eine Journey für einen bestimmten Kunden Trigger, richten sich Kampagnen mit einzigartigen Inhalten wie Newslettern, einmaligen Werbeaktionen oder allgemeinen Informationen oder regelmäßig mit ähnlichen Inhalten, die regelmäßig gesendet werden, wie z. B. Geburtstagskampagnen und Erinnerungen.

Gehen Sie im Menü zu **Kampagnen** und klicken Sie auf **Kampagne erstellen**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail21.png)

Wählen Sie **Geplant - Marketing** und klicken Sie auf **Erstellen**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail22.png)

Konfigurieren Sie im Bildschirm zur Kampagnenerstellung Folgendes:

- **Name**: `--aepUserLdap--  - Online Gamers CitiSignal Fiber Max`.
- **Beschreibung**: Glasfaser-Kampagne für Online-Gamer

Klicken Sie auf **Aktionen**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail23.png)

Klicken Sie auf **+ Aktion hinzufügen** wählen Sie dann **E-Mail** aus.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail24.png)

Wählen Sie dann eine vorhandene **E-Mail-Konfiguration** und klicken Sie auf **Inhalt bearbeiten**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail25.png)

Sie werden es dann sehen. Verwenden Sie für **Betreffzeile** Folgendes:

```
{{profile.person.name.firstName}}, say goodbye to delays!
```

Klicken Sie anschließend auf **Inhalt bearbeiten**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail26.png)

Klicken Sie **HTML importieren**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail27.png)

Klicken Sie anschließend auf die Schaltfläche für **Adobe GenStudio for Performance Marketing**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail28.png)

Anschließend sollte ein Popup-Fenster mit allen in GenStudio for Performance Marketing veröffentlichten E-Mail-Erlebnissen angezeigt werden. Wählen Sie eines der verfügbaren E-Mail-Erlebnisse aus und klicken Sie auf **Verwenden**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail29.png)

Wählen Sie Ihr eigenes AEM Assets CS-Repository mit dem Namen `--aepUserLdap-- - CitiSignal dev` aus und klicken Sie auf **Importieren**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail30.png)

Sie sollten das dann sehen. Wählen Sie die Schaltfläche Fehlendes Bild aus und klicken Sie auf **Asset auswählen**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail31.png)

Wechseln Sie zu dem Ordner, der wie folgt aussieht, beginnend mit **GenStudio.zip…..** und wählen Sie die `--aepUserLdap-- - neon rabbit.png` aus. Klicken Sie auf **Auswählen**

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail32.png)

Sie sollten das dann sehen.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail33.png)

Scrollen Sie nach unten zur Fußzeile, wählen Sie das Wort **Abmelden** und klicken Sie auf das Symbol **Link**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail38.png)

Legen Sie **Typ** auf **Externes Opt-out/Abmeldung** und die URL auf `https://techinsiders.org/unsubscribe.html` fest (es ist nicht zulässig, eine leere URL für den Abmelde-Link zu haben).

Klicken Sie **auf** und dann auf den **Pfeil** in der linken oberen Ecke Ihres Bildschirms, um zur Kampagnenkonfiguration zurückzukehren.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail39.png)

Navigieren Sie zu **Zielgruppe**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail34.png)

Klicken Sie **Zielgruppe auswählen**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail35.png)

Wählen Sie die Zielgruppe der Abonnement-Liste für Online-Gamer aus, die `--aepUserLdap--_SL_Interest_Online_Gaming` benannt werden soll. Klicken Sie auf **Speichern**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail36.png)

Klicken Sie auf **Zum Aktivieren überprüfen**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail37.png)

Wenn Ihre Kampagnenkonfiguration keine Probleme aufweist, können Sie auf &quot;**&quot;**.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail40.png)

Ihre Kampagne wird dann aktiviert, was einige Minuten dauert.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail41.png)

Nach einigen Minuten ist die Kampagne live und die E-Mail wird an die von Ihnen ausgewählte Abonnement-Liste gesendet.

![Journey Optimizer](./../../../creation-production/module1.3/images/gsemail42.png)

Sie haben jetzt diese Übung abgeschlossen.

## Nächste Schritte

Zurück zu [Adobe Journey Optimizer: Content-Management](./ajocontent.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
