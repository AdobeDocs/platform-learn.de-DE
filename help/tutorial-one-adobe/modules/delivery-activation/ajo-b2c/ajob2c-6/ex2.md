---
title: Landingpages in Adobe Journey Optimizer
description: Landingpages in Adobe Journey Optimizer
kt: 5342
doc-type: tutorial
exl-id: bf499aad-91d0-4fb5-a38c-db8fcd56480b
source-git-commit: 83e8418b1a9e5e0e37f97473d2c7539ccd3fd803
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 10%

---

# 3.6.2 Landingpages

Melden Sie sich bei Adobe Journey Optimizer an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`. Sie befinden sich dann in der **Startseite**-Ansicht Ihres Sandbox-`--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## Abonnement-Listen 3.6.2.1

Landingpages in Adobe Journey Optimizer funktionieren zusammen mit **Abonnementlisten**. Um Landingpages einzurichten, müssen Sie zunächst „Abonnement **Listen“**.

CitiSignal möchte seine Kunden zu ihrem Interesse an den folgenden Bereichen befragen:

- Smart Home
- Von zu Hause aus arbeiten
- Online-Gaming

Nachdem ein Kunde sein Interesse an einer dieser Domains bekundet hat, sollte dieser Kunde zu einer bestimmten Liste hinzugefügt werden, damit er später im Rahmen bevorstehender Kampagnen mit bestimmten Inhalten angesprochen werden kann.

Sie werden jetzt drei Abonnement-Listen erstellen.

Navigieren Sie im linken Menü zu **Abonnementlisten**. Klicken Sie **Abonnement-Liste erstellen**.

![Landingpages](./images/lp1.png)

Verwenden **für** Titel`--aepUserLdap--_SL_Interest_in_Smart_Home`.
Für **Beschreibung** verwenden Sie: `Interest in Smart Home`.

Klicken Sie auf **Absenden**.

![Landingpages](./images/lp2.png)

Klicken Sie **Abonnement-Liste erstellen**, um eine weitere Liste zu erstellen.

![Landingpages](./images/lp3.png)

Verwenden **für** Titel`--aepUserLdap--_SL_Interest_WFH`.
Für **Beschreibung** verwenden Sie: `Interest in Work From Home`.

Klicken Sie auf **Absenden**.

![Landingpages](./images/lp4.png)

Klicken Sie **Abonnement-Liste erstellen**, um eine weitere Liste zu erstellen.

![Landingpages](./images/lp5.png)

Verwenden **für** Titel`--aepUserLdap--_SL_Interest_Online_Gaming`.
Für **Beschreibung** verwenden Sie: `Interest in Online Gaming`.

Klicken Sie auf **Absenden**.

![Landingpages](./images/lp6.png)

Sie haben jetzt die 3 Listen erstellt, die Sie benötigen.

![Landingpages](./images/lp7.png)

## Landingpage-Voreinstellung 3.6.2.2

Um Landingpages in Adobe Journey Optimizer verwenden zu können, muss eine Voreinstellung erstellt werden.

Gehen Sie im linken Menü zu **Administration** > **Kanäle** und wählen Sie **Landingpage-Voreinstellungen**.

Klicken Sie **Landingpage-Voreinstellung erstellen**.

![Landingpages](./images/lp8.png)

Verwenden Sie für **Feld** Name: `--aepUserLdap-- - CitiSignal LP` und wählen Sie die in Ihrer Instanz verfügbare Subdomain aus.

>[!NOTE]
>
>Wenn in Ihrer Instanz keine Subdomain angezeigt wird, wenden Sie sich an Ihren AJO-Administrator, um eine Subdomain hinzuzufügen.

Klicken Sie auf **Absenden**.

![Landingpages](./images/lp9.png)

Ihre Landingpage-Voreinstellung wurde jetzt erstellt.

![Landingpages](./images/lp10.png)

## 3.6.2.3 Landingpage

Jetzt können Sie Ihre Landingpage erstellen. Wechseln Sie im linken Menü zu **Content-** > **Landingpages**.

Klicken Sie **Landingpage erstellen**.

![Landingpages](./images/lp11.png)

Verwenden Sie für **Feld** Titel`vangeluw - CitiSignal Interests`. Wählen Sie als Nächstes die **Landingpage-Voreinstellung** aus, die Sie im vorherigen Schritt konfiguriert haben.

Klicken Sie auf **Erstellen**.

![Landingpages](./images/lp12.png)

Sie sollten das dann sehen.

![Landingpages](./images/lp13.png)

Ändern Sie das Feld **Seitenname** in `--aepUserLdap-- - CitiSignal Interests`.

Geben Sie diesen benutzerdefinierten Namen unter **Zugriffseinstellungen** ein: `--aepUserLdap---citisignal-interests`.

Klicken Sie **Designer öffnen**.

![Landingpages](./images/lp14.png)

Wählen Sie **Von Grund auf gestalten**.

![Landingpages](./images/lp15.png)

Sie sollten das dann sehen.

![Landingpages](./images/lp16.png)

Fügen Sie der Arbeitsfläche eine Strukturkomponente **1:** Spalte) hinzu.

![Landingpages](./images/lp17.png)

Fügen Sie eine Inhaltskomponente **Formular** zur Arbeitsfläche hinzu.

![Landingpages](./images/lp18.png)

Aktualisieren Sie das Feld **Beschriftung** für **Kontrollkästchen 1** auf `Keep me updated about CitiSignal's offering for Smart Home`.

Stellen Sie sicher, dass das Kontrollkästchen **Opt-in, wenn aktiviert** aktiviert ist und dass **Abonnement-Liste** ausgewählt ist.

Klicken Sie dann auf **Abonnement-Liste auswählen**.

![Landingpages](./images/lp19.png)

Wählen Sie anschließend die `--aepUserLdap--_SL_Interest_in_Smart_Home` aus und klicken Sie auf **Auswählen**.

![Landingpages](./images/lp20.png)

Klicken Sie auf **+ Feld hinzufügen** wählen Sie dann **Kontrollkästchen** aus.

![Landingpages](./images/lp21.png)

Sie sollten das dann sehen.

![Landingpages](./images/lp22.png)

Aktualisieren Sie das Feld **label** für **Checkbox 2** auf `Keep me updated about CitiSignal's offering for Work From Home`.

Stellen Sie sicher, dass das Kontrollkästchen **Opt-in, wenn aktiviert** aktiviert ist und dass **Abonnement-Liste** ausgewählt ist.

Klicken Sie dann auf **Abonnement-Liste auswählen**.

![Landingpages](./images/lp23.png)

Wählen Sie anschließend die `--aepUserLdap--_SL_Interest_WFH` aus und klicken Sie auf **Auswählen**.

![Landingpages](./images/lp24.png)

Klicken Sie auf **+ Feld hinzufügen** wählen Sie dann **Kontrollkästchen** aus.

![Landingpages](./images/lp25.png)

Sie sollten das dann sehen.

![Landingpages](./images/lp26.png)

Aktualisieren Sie das Feld **label** für **Checkbox 3** auf `Keep me updated about CitiSignal's offering for Online Gaming`.

Stellen Sie sicher, dass das Kontrollkästchen **Opt-in, wenn aktiviert** aktiviert ist und dass **Abonnement-Liste** ausgewählt ist.

Klicken Sie dann auf **Abonnement-Liste auswählen**.

![Landingpages](./images/lp27.png)

Wählen Sie anschließend die `--aepUserLdap--_SL_Interest_Online_Gaming` aus und klicken Sie auf **Auswählen**.

![Landingpages](./images/lp28.png)

Sie sollten das dann sehen.

![Landingpages](./images/lp29.png)

Wechseln Sie zum Formularfeld **CALL TO ACTION**.

Aktualisieren Sie die folgenden Felder:

- **Text** - Schaltflächenbezeichnung: `Save`.
- **Bestätigungsaktion**: Wählen Sie **Bestätigungstext** aus.
- **Bestätigungstext**: Verwenden Sie: `Thanks for updating your preferences!`
- **Fehleraktion**: Wählen Sie **Fehlertext** aus.
- **Bei Fehlertext**: Verwenden Sie: `There was an error updating your preferences.`

Klicken Sie **Speichern** und dann auf den Pfeil oben links, um zum vorherigen Bildschirm zurückzukehren.

![Landingpages](./images/lp30.png)

Klicken Sie auf **Veröffentlichen**.

![Landingpages](./images/lp31.png)

Klicken **erneut auf** Veröffentlichen“.

![Landingpages](./images/lp32.png)

Ihre Landingpage ist jetzt veröffentlicht und kann in einer E-Mail verwendet werden.

![Landingpages](./images/lp33.png)

## 3.6.2.4 Landingpage in E-Mail einschließen

In Übung 3.1 haben Sie eine Journey mit dem Namen `--aepUserLdap-- - Registration Journey` erstellt.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/published.png)

Sie sollten jetzt die E-Mail-Nachricht auf dieser Journey aktualisieren, um den Link zur Landingpage aufzunehmen.

Wechseln Sie im linken Menü zu **Journey** und klicken Sie, um die Journey-`--aepUserLdap-- - Registration Journey` zu öffnen.

![Landingpages](./images/lp34.png)

Klicken Sie auf **Mehr…** und wählen Sie **Neue Version erstellen**.

![Landingpages](./images/lp35.png)

Klicken Sie **Neue Version erstellen**.

![Landingpages](./images/lp36.png)

Klicken Sie, um die Aktion **E-Mail** auszuwählen, und wählen Sie dann **Inhalt bearbeiten**.

![Landingpages](./images/lp37.png)

Klicken Sie **E-Mail-Textkörper bearbeiten**.

![Landingpages](./images/lp38.png)

Sie sollten dann so etwas sehen. Fügen Sie eine neue Strukturkomponente **1:1-Spalte** zur Arbeitsfläche hinzu.

![Landingpages](./images/lp39.png)

Fügen Sie eine neue Inhaltskomponente **Text** in die neu erstellte Strukturkomponente ein.

![Landingpages](./images/lp40.png)

Fügen Sie den folgenden Text in die Inhaltskomponente **Text** ein.

`Would you like to hear from us about Smart Home news? Do you work from home and would you like to hear our tips? Or are you an avid online gamer and do you want to receive our game reviews? Click here to update your preferences and interests!`

Gestalten Sie Ihren Text so, dass er wie folgt aussieht, und wählen Sie dann das Wort `here` aus. Klicken Sie auf **Link**-Symbol.

Legen Sie den **Typ** des Links auf **Landingpage** und das Feld **Ziel** auf **Leer** fest.

Klicken Sie auf **Bearbeiten**, um die Landingpage auszuwählen, die verknüpft werden soll.

![Landingpages](./images/lp41.png)

Wählen Sie die Landingpage-`--aepUserLdap-- - CitiSignal Interests` aus. Klicken Sie auf **Auswählen**.

![Landingpages](./images/lp42.png)

Sie sollten das dann sehen. Klicken Sie auf **Speichern**.

![Landingpages](./images/lp43.png)

Klicken Sie auf den Pfeil in der oberen linken Ecke, um zum vorherigen Bildschirm zurückzukehren.

![Landingpages](./images/lp44.png)

Klicken Sie auf den Pfeil oben links, um zum vorherigen Bildschirm zurückzukehren.

![Landingpages](./images/lp45.png)

Klicken Sie auf **Speichern**.

![Landingpages](./images/lp46.png)

Klicken Sie auf **Veröffentlichen**.

![Landingpages](./images/lp47.png)

Klicken **erneut auf** Veröffentlichen“.

![Landingpages](./images/lp48.png)

Ihre Änderungen wurden veröffentlicht, und Sie können Ihren Journey testen.

![Landingpages](./images/lp49.png)

## 3.6.2.5 Testen von Journey und Landingpage

Navigieren Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf die 3 Punkte **…** in Ihrem Website-Projekt und dann auf **Ausführen**, um es zu öffnen.

![DSN](./../../datacollection/dc1.1/images/web8.png)

Anschließend wird Ihre Demo-Website geöffnet. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../../getting-started/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browser-Fenster.

![DSN](../../../getting-started/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../../getting-started/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../../getting-started/gettingstarted/images/web6.png)

Ihre Website wird dann in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden. Navigieren Sie zu **Anmelden**

![DSN](../../../getting-started/gettingstarted/images/web7.png)

Klicken Sie **KONTO ERSTELLEN**. Füllen Sie Ihre Daten aus und klicken Sie auf **Registrieren**.

![Demo](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv9.png)

Sie werden jetzt zur Homepage weitergeleitet. Öffnen Sie das Bedienfeld Profil-Viewer und navigieren Sie zum Echtzeit-Kundenprofil. Im Profil-Viewer-Fenster sollten Sie alle Ihre personenbezogenen Daten angezeigt bekommen, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv10.png)

1 Minute nach der Erstellung Ihres Kontos erhalten Sie Ihre E-Mail zur Kontoerstellung von Adobe Journey Optimizer.

Klicken Sie auf den Link in der E-Mail, um Ihre Voreinstellungen zu aktualisieren.

![Launch-Einrichtung](./images/email.png)

Anschließend sollte das von Ihnen erstellte Formular angezeigt werden. Aktivieren Sie einige Kontrollkästchen und klicken Sie auf **Speichern**.

![Launch-Einrichtung](./images/email1.png)

Anschließend sollte eine Bestätigungsmeldung angezeigt werden.

![Launch-Einrichtung](./images/email2.png)

## Berichte zur Abonnement-Liste 3.6.2.6

Um die verfügbaren Berichte zu Abonnement-Listen anzuzeigen, gehen Sie **Abonnement-Listen** im linken Menü und klicken Sie, um eine der zuvor konfigurierten Abonnement-Listen zu öffnen.

![Landingpages](./images/lp50.png)

Klicken Sie auf **Bericht**.

![Landingpages](./images/lp51.png)

Sie sollten dann die Übersicht der Liste mit der Anzahl der Personen sehen, die sich an- oder abgemeldet haben.

![Landingpages](./images/lp52.png)

## Nächste Schritte

Wechseln Sie zu [3.6.3 AJO und GenStudio for Performance Marketing](./ex3.md)

Zurück zu [Adobe Journey Optimizer: Content-Management](./ajocontent.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
