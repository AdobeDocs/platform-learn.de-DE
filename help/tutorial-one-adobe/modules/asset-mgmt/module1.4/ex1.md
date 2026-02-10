---
title: Erstellen von Assets und Dynamic Media-Vorlagen
description: Erstellen von Assets und Dynamic Media-Vorlagen
kt: 5342
doc-type: tutorial
exl-id: 3867f23b-9b88-4971-a892-5821800e39ac
source-git-commit: 8f746831d4a1481f8ccc14539273c4b16ca5170b
workflow-type: tm+mt
source-wordcount: '2241'
ht-degree: 1%

---

# 1.4.1 Erstellen von Assets und Dynamic Media-Vorlagen

>[!IMPORTANT]
>
>Um diese Übung abzuschließen, benötigen Sie Zugriff auf eine funktionierende AEM Assets CS-Autorenumgebung mit aktiviertem AEM Assets Dynamic Media.
>
>Wenn Sie keine solche Umgebung haben, navigieren Sie zu [Adobe Experience Manager Cloud Service und Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Folgen Sie den Anweisungen dort, und Sie haben Zugriff auf eine solche Umgebung.

>[!IMPORTANT]
>
>Wenn Sie zuvor ein AEM CS-Programm mit einer AEM Assets CS-Umgebung konfiguriert haben, kann es sein, dass Ihre AEM CS-Sandbox in den Ruhezustand versetzt wurde. Da der Ruhezustand einer solchen Sandbox 10-15 Minuten dauert, ist es ratsam, den Ruhezustand jetzt zu beenden, damit Sie nicht zu einem späteren Zeitpunkt warten müssen.

## 1.4.1.1 Erstellen eines Dynamic Media-Unternehmens

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Die gewünschte Organisation ist `--aepImsOrgName--`.

![AEM Assets Dynamic Media](./images/aaemassdmcomp1.png)

Scrollen Sie nach unten zu **Dynamic Media-Unternehmen**. Klicken Sie auf das Symbol **+** , um ein neues Dynamic Media-Unternehmen zu erstellen.

![AEM Assets Dynamic Media](./images/aaemassdmcomp2.png)

Folgende Angaben sind erforderlich:

- **Firmenname**: `--aepUserLdap---CitiSignal`.
- **Unternehmensregion**: Wählen Sie die Region aus, die Ihnen am nächsten liegt.
- **E-Mails an Unternehmensadministrator**: Geben Sie Ihre Admin-E-Mail ein.

Klicken Sie auf **Erstellen**.

![AEM Assets Dynamic Media](./images/aaemassdmcomp3.png)

Sie sollten das dann sehen.

![AEM Assets Dynamic Media](./images/aaemassdmcomp4.png)

Sie sollten jetzt eine E-Mail wie die folgende erhalten, die Ihr temporäres Kennwort enthält. Um Ihr Kennwort zu ändern oder abzurufen, falls Sie keine E-Mail erhalten haben, sollten Sie die **Adobe Dynamic Media Classic Desktop App** installieren. Installationsanweisungen finden Sie hier: [https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app](https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app).

Folgen Sie den Anweisungen dort und kehren Sie hierher zurück, sobald die App auf Ihrem System installiert ist.

Öffnen Sie das **Adobe Dynamic Media Classic-Desktop-Programm**. Wenn Sie Ihr Passwort kennen, geben Sie es bitte hier ein und befolgen Sie die Anweisungen, um es bei der ersten Anmeldung zu ändern.

Wenn Sie Ihr Kennwort nicht kennen, klicken Sie auf den Link **Kennwort vergessen** und folgen Sie der Anleitung zum Zurücksetzen Ihres Kennworts, um dann hierher zurückzukehren und sich anzumelden.

![AEM Assets Dynamic Media](./images/aaemassdmcomp5.png)

Nach erfolgreicher Anmeldung sollte ein Bildschirm ähnlich dem folgenden angezeigt werden.

![AEM Assets Dynamic Media](./images/aaemassdmcomp6.png)

## Konfigurieren von Dynamic Media in AEM 1.4.1.2

Navigieren Sie zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Die gewünschte Organisation ist `--aepImsOrgName--`.

Klicken Sie hier, um Ihr Cloud Manager-Programm zu öffnen, das `--aepUserLdap-- - CitiSignal AEM+ACCS` heißen sollte.

![AEM Assets Dynamic Media](./images/accsaemassets1.png)

Klicken Sie auf Ihre Umgebung.

![AEM Assets Dynamic Media](./images/accsaemassets3.png)

Klicken Sie auf die URL Ihrer Umgebung.

![AEM Assets Dynamic Media](./images/accsaemassets2.png)

Wechseln Sie zu **Tools**, **Cloud Services** und dann zu **Dynamic Media-Konfiguration**.

![AEM Assets Dynamic Media](./images/accsaemassets4.png)

Wählen Sie **global** (Kontrollkästchen nicht aktivieren) aus und klicken Sie dann auf **Erstellen**.

![AEM Assets Dynamic Media](./images/accsaemassets5.png)

Folgende Angaben sind erforderlich:

- **Titel**: Verwenden Sie diesen Titel: `--aepUserLdap-- - CitiSignal`.
- **E-Mail**: Geben Sie Ihre E-Mail-Adresse ein.
- **Kennwort**: Geben Sie Ihr Kennwort für das Dynamic Media-Konto ein
- **Region**: Wählen Sie die Region aus, die Sie beim Erstellen Ihres Dynamic Media-Unternehmens ausgewählt haben, in diesem Beispiel **Europa**.

Klicken Sie **Mit Dynamic Media verbinden**.

![AEM Assets Dynamic Media](./images/accsaemassets6.png)

Sie sollten das dann sehen. Konfigurieren Sie Folgendes:

- Wählen Sie die **Firma**: `--aepUserLdap-- - CitiSignal`.
- Setzen **Assets veröffentlichen** auf **Sofort**.
- Markieren Sie das Kontrollkästchen **Alle Inhalte synchronisieren**.

Klicken Sie auf **Speichern**.

![AEM Assets Dynamic Media](./images/accsaemassets7.png)

Ihre Dynamic Media-Konfiguration ist jetzt abgeschlossen. Klicken Sie auf **OK**.

![AEM Assets Dynamic Media](./images/accsaemassets8.png)

## 1.4.1.3 Exportieren von Assets

Laden Sie diese Datei [Citisignal-fiber-max-is-coming.psd](./assets/citisignal-fiber-max-is-coming.psd){target="_blank"} herunter und öffnen Sie sie mit Adobe Photoshop.

Sie sollten das dann sehen. CitiSignal plant den Ausbau von Fiber Max in drei Städten: New York, Paris und Dubai.

Durch Ein- oder Ausblenden bestimmter Ebenen können Sie das von den Designern erstellte Bild anzeigen.

Im Folgenden finden Sie die Anweisungen zum Exportieren der Bilddateien aus der Photoshop PSD-Vorlage. Wenn Sie es vorziehen, können Sie auch die fertigen Bilder hier [Citisignal-dm-email-assets.zip](./assets/citisignal-dm-email-assets.zip){target="_blank"} herunterladen und die Datei auf Ihren Desktop entpacken.

Das ist die Version für New York.

![AEM Assets Dynamic Media](./images/aemdm1.png)

Das ist die Version für Dubai.

![AEM Assets Dynamic Media](./images/aemdm2.png)

Das ist die Version für Paris.

![AEM Assets Dynamic Media](./images/aemdm3.png)

Es wird möglicherweise viele andere Städte geben, in denen CitiSignal Fiber Max ausbauen wird, sodass in Zukunft neue Ebenen in dieser Datei erstellt werden können. Vorerst liegt der Fokus auf den drei bereits erwähnten Städten.

Um diese Varianten in Kombination mit AEM Assets Dynamic Media zu verwenden, sollten die Ebenen für jede Stadt separat als Bilder ohne die Hintergrunddatei exportiert werden. Außerdem sollte ein weiterer Export für die Hintergrundebene ohne Städte durchgeführt werden.

Sie sollten jetzt nur eine der Ebenen ausblenden und anzeigen. Die erste Ebene, die angezeigt wird, ist **Ebene** Paris“, und alle anderen Ebenen sollten ausgeblendet sein.

Um diese Ebene zu exportieren, gehen Sie **Datei** > **Exportieren** > **Exportieren als…**.

![AEM Assets Dynamic Media](./images/aemdm4.png)

Sie sollten das dann sehen. Wählen Sie den Dateityp **PNG**, stellen Sie sicher, **Transparenz** aktiviert ist, und klicken Sie dann auf **Exportieren**.

![AEM Assets Dynamic Media](./images/aemdm5.png)

Ändern Sie den Dateinamen in `citisignal-fiber-max-is-coming-paris.png`und klicken Sie auf **Exportieren**.

![AEM Assets Dynamic Media](./images/aemdm6.png)

Die nächste Ebene, die angezeigt werden soll **ist die Ebene &quot;**&quot;, und alle anderen Ebenen sollten ausgeblendet sein.

Um diese Ebene zu exportieren, gehen Sie **Datei** > **Exportieren** > **Exportieren als…**.

![AEM Assets Dynamic Media](./images/aemdm4a.png)

Sie sollten das dann sehen. Wählen Sie den Dateityp **PNG**, stellen Sie sicher, **Transparenz** aktiviert ist, und klicken Sie dann auf **Exportieren**.

![AEM Assets Dynamic Media](./images/aemdm5a.png)

Ändern Sie den Dateinamen in `citisignal-fiber-max-is-coming-dubai.png`und klicken Sie auf **Exportieren**.

![AEM Assets Dynamic Media](./images/aemdm6a.png)

Die nächste Ebene, die angezeigt wird, **die**-Ebene, und alle anderen Ebenen sollten ausgeblendet sein.

Um diese Ebene zu exportieren, gehen Sie **Datei** > **Exportieren** > **Exportieren als…**.

![AEM Assets Dynamic Media](./images/aemdm4b.png)

Sie sollten das dann sehen. Wählen Sie den Dateityp **PNG**, stellen Sie sicher, **Transparenz** aktiviert ist, und klicken Sie dann auf **Exportieren**.

![AEM Assets Dynamic Media](./images/aemdm5b.png)

Ändern Sie den Dateinamen in `citisignal-fiber-max-is-coming-newyork.png`und klicken Sie auf **Exportieren**.

![AEM Assets Dynamic Media](./images/aemdm6b.png)

Als Nächstes wird die Ebene **Hintergrund** angezeigt, und alle anderen Ebenen sollten ausgeblendet sein.

Um diese Ebene zu exportieren, gehen Sie **Datei** > **Exportieren** > **Exportieren als…**.

![AEM Assets Dynamic Media](./images/aemdm4c.png)

Sie sollten das dann sehen. Wählen Sie den Dateityp **PNG**, stellen Sie sicher, **Transparenz** aktiviert ist, und klicken Sie dann auf **Exportieren**.

![AEM Assets Dynamic Media](./images/aemdm5c.png)

Ändern Sie den Dateinamen in `citisignal-fiber-max-is-coming-background`und klicken Sie auf **Exportieren**.

![AEM Assets Dynamic Media](./images/aemdm6c.png)

Diese Dateien sollten dann an dem von Ihnen ausgewählten Exportspeicherort verfügbar sein.

![AEM Assets Dynamic Media](./images/aemdm7.png)

## 1.4.1.4 Hochladen von Assets in AEM Assets CS

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Zu **Experience Manager Assets**.

![AEM Assets Dynamic Media](./images/aemdm8.png)

Wählen Sie Ihr Repository aus, das `--aepUserLdap-- - CitiSignal AEM + ACCS` benannt werden soll.

![AEM Assets Dynamic Media](./images/aemdm9.png)

Wechseln Sie zu **Assets** und klicken Sie dann auf **Ordner erstellen**.

![AEM Assets Dynamic Media](./images/aemdm10.png)

Verwenden Sie für den Ordner den Namen: `--aepUserLdap-- - CitiSignal Dynamic Media`. Klicken Sie auf **Erstellen**.

![AEM Assets Dynamic Media](./images/aemdm11.png)

Doppelklicken Sie, um den soeben erstellten Ordner zu öffnen.

![AEM Assets Dynamic Media](./images/aemdm12.png)

Klicken Sie **Assets hinzufügen**.

![AEM Assets Dynamic Media](./images/aemdm13.png)

Klicken Sie auf **Durchsuchen** und wählen Sie dann **Dateien durchsuchen** aus.

![AEM Assets Dynamic Media](./images/aemdm15.png)

Wählen Sie die 4 PNG-Dateien aus, die Sie im vorherigen Schritt exportiert haben.

![AEM Assets Dynamic Media](./images/aemdm16.png)

Klicken Sie **Hochladen**.

![AEM Assets Dynamic Media](./images/aemdm17.png)

Ihre Bilder sind jetzt in AEM Assets CS verfügbar.

![AEM Assets Dynamic Media](./images/aemdm18.png)

Warten Sie einige Minuten und öffnen Sie dann das **Adobe Dynamic Media Classic-Desktop-Programm**. Jetzt sollten Sie auch sehen, wie die hochgeladenen Bilder in Dynamic Media verfügbar werden.

![AEM Assets Dynamic Media](./images/aemdm19.png)

## Konfigurieren 1.4.1.5 Dynamic Media-Vorlage

Wechseln Sie im linken Menü zu **Dynamic Media Assets**. Klicken Sie, um Ihre `--aepUserLdap-- - CitiSignal Dynamic Media` zu öffnen. Klicken Sie dann auf **Vorlage erstellen**.

![AEM Assets Dynamic Media](./images/aemdm20.png)

Folgende Angaben sind erforderlich:

- **Vorlagenname**: `--aepUserLdap-- - CitiSignal Fiber Max Launch Email Assets`
- **Arbeitsfläche Breite**: `600px`
- **Canvas-Höhe**: `600px`

Klicken Sie auf **Erstellen**.

![AEM Assets Dynamic Media](./images/aemdm21.png)

Sie sollten das dann sehen. Klicken Sie auf **Symbol** Bild hinzufügen“.

![AEM Assets Dynamic Media](./images/aemdm22.png)

Ziehen Sie die Datei **Citisignal-Fibre-Max-is-Coming_Citisignal-background.png** auf die Arbeitsfläche und passen Sie sie an die Arbeitsfläche an.

![AEM Assets Dynamic Media](./images/aemdm23.png)

Ziehen Sie als Nächstes die Datei **Citisignal-fiber-max-is-coming_citsignal-newyork.png** auf die Arbeitsfläche und passen Sie sie an die Arbeitsfläche an.

![AEM Assets Dynamic Media](./images/aemdm24.png)

Ziehen Sie als Nächstes die Datei **Citisignal-fiber-max-is-coming_citsignal-dubai.png** auf die Arbeitsfläche und passen Sie sie an die Arbeitsfläche an.

![AEM Assets Dynamic Media](./images/aemdm25.png)

Ziehen Sie als Nächstes die Datei **Citisignal-fiber-max-is-coming_citsignal-paris.png** auf die Arbeitsfläche und passen Sie sie an die Arbeitsfläche an.

![AEM Assets Dynamic Media](./images/aemdm26.png)

Sie haben jetzt alle 3 Varianten in der Vorlage als unterschiedliche Ebenen gleichzeitig. Sie können bestimmte Ebenen ein- oder ausblenden, indem Sie auf das Symbol **Ebenen** klicken, wo Sie sehen, dass alle Ebenen derzeit sichtbar sind.

![AEM Assets Dynamic Media](./images/aemdm27.png)

Durch das Ausblenden einiger Ebenen können Sie steuern, wie das Bild aussieht. In diesem Beispiel sind nur die Ebene für **Paris** und die Hintergrundebene sichtbar.

![AEM Assets Dynamic Media](./images/aemdm28.png)

Als Nächstes müssen Sie eine Textebene hinzufügen. Klicken Sie auf **Symbol** Textebene“.

![AEM Assets Dynamic Media](./images/aemdm29.png)

Sie sollten das dann sehen.

![AEM Assets Dynamic Media](./images/aemdm30.png)

Sie können das Textfeld nach Belieben anpassen. Hier ein Beispiel. Vergessen Sie nicht, die Option &quot;**Textgröße ändern“ zu aktivieren** damit der echte Text, der zu einem späteren Zeitpunkt eingefügt wird, gut aussieht.

![AEM Assets Dynamic Media](./images/aemdm31.png)

Fügen Sie eine zweite Textebene hinzu und lassen Sie sie wie folgt aussehen. Vergessen Sie nicht, die Option &quot;**Textgröße ändern“ zu aktivieren** damit der echte Text, der zu einem späteren Zeitpunkt eingefügt wird, gut aussieht.

![AEM Assets Dynamic Media](./images/aemdm32.png)

Wählen Sie die erste Textebene aus. Klicken Sie auf die 3 Punkte **…** und wählen Sie **Bearbeiten**.

![AEM Assets Dynamic Media](./images/aemdm33.png)

Sie sollten das dann sehen. Scroll down.

![AEM Assets Dynamic Media](./images/aemdm34.png)

Klicken Sie auf **Umschalter**-Symbol, sodass das Feld **Text** aktiviert ist. Ändern Sie **Parametername** in `title`.

![AEM Assets Dynamic Media](./images/aemdm35.png)

Wählen Sie die zweite Textebene aus. Klicken Sie auf die 3 Punkte **…** und wählen Sie **Bearbeiten**.

![AEM Assets Dynamic Media](./images/aemdm36.png)

Sie sollten das dann sehen. Scroll down.

![AEM Assets Dynamic Media](./images/aemdm37.png)

Klicken Sie auf **Umschalter**-Symbol, sodass das Feld **Text** aktiviert ist. Ändern Sie **Parametername** in `body`.

![AEM Assets Dynamic Media](./images/aemdm38.png)

Wählen Sie die Ebene für **Paris**. Klicken Sie auf die 3 Punkte **…** und dann auf **Bearbeiten**.

![AEM Assets Dynamic Media](./images/aemdm39.png)

Navigieren Sie zu **Parameter**. Aktivieren Sie das Feld **Ausblenden** und geben Sie den **Parameternamen** ein: `city_paris`. Klicken Sie auf **Speichern**.

![AEM Assets Dynamic Media](./images/aemdm40.png)

Wählen Sie die Ebene für **Dubai**. Klicken Sie auf die 3 Punkte **…** und dann auf **Bearbeiten**.

![AEM Assets Dynamic Media](./images/aemdm41.png)

Navigieren Sie zu **Parameter**. Aktivieren Sie das Feld **Ausblenden** und geben Sie den **Parameternamen** ein: `city_dubai`. Klicken Sie auf **Speichern**.

![AEM Assets Dynamic Media](./images/aemdm42.png)

Wählen Sie die Ebene für **New York** aus. Klicken Sie auf die 3 Punkte **…** und dann auf **Bearbeiten**.

![AEM Assets Dynamic Media](./images/aemdm43.png)

Navigieren Sie zu **Parameter**. Aktivieren Sie das Feld **Ausblenden** und geben Sie den **Parameternamen** ein: `city_ny`. Klicken Sie auf **Speichern**.

![AEM Assets Dynamic Media](./images/aemdm44.png)

Klicken Sie auf **Vorschau**.

![AEM Assets Dynamic Media](./images/aemdm45.png)

Aktivieren Sie den Umschalter für **Alle Parameter einschließen** und ändern Sie einige Eingabevariablen, wie im Screenshot angegeben. Sie sollten sehen, wie sich Ihr Bild basierend auf der bereitgestellten Eingabe dynamisch ändert. Für die Felder **city_paris**, **city_dubai** und **city_ny** bedeutet der Wert 0, dass dieses Bild NICHT ausgeblendet wird, und der Wert 1 bedeutet, dass dieses Bild ausgeblendet wird.

![AEM Assets Dynamic Media](./images/aemdm46.png)

Wenn Sie einige Variablen ändern, sehen Sie jetzt ein anderes Bild, das angezeigt wird.

![AEM Assets Dynamic Media](./images/aemdm47.png)

Wenn Sie weitere Variablen ändern, sehen Sie jetzt, dass ein anderes Bild angezeigt wird.

Um diese Vorlage mit Adobe Journey Optimizer verwenden zu können und die Anforderungen dieses Anwendungsfalls zu erfüllen, sollten Sie eine weitere Ebene hinzufügen, mit der der Pfad der anzuzeigenden Datei basierend auf einem Feld, das Teil des Echtzeit-Kundenprofils in Adobe Experience Platform ist, dynamisch geändert wird.

Während der Datenvorbereitung wurde im des Adobe Experience Platform-Schemas ein Feld erstellt, in dem die **nächste Rollout-Stadt“ für** Kunden gespeichert wird. Der Pfad des Felds wird `--aepTenantId--.individualCharacteristics.fiber_rollout.closest_rollout_city`.

>[!NOTE]
>
>Der folgende Screenshot des Adobe Experience Platform-Schemas dient nur zu Informationszwecken. Sie müssen nicht zu AEP navigieren, um dies selbst zu visualisieren.

![AEM Assets Dynamic Media](./images/aemdm50.png)

In der nächsten Übung verwenden Sie dieses Feld, um dynamisch auszuwählen, welches Bild welchem Kunden angezeigt werden soll.

Um dies zu ermöglichen, sollten Sie eine neue Bildebene hinzufügen.

Blenden wir zunächst die anderen Ebenen aus, die Bilder für die Rollout-Städte enthalten.

![AEM Assets Dynamic Media](./images/aemdm51.png)

Gehen Sie dann zu **Bilder** und wählen Sie ein zufälliges Bild einer Stadt aus, fügen Sie es der Arbeitsfläche hinzu und stellen Sie sicher, dass es in die gesamte Arbeitsfläche passt. Es spielt keine Rolle, welches Stadtbild Sie auswählen, da der Pfad in der nächsten Übung von AJO dynamisch geändert wird.

![AEM Assets Dynamic Media](./images/aemdm52.png)


![AEM Assets Dynamic Media](./images/aemdm53.png)

Navigieren Sie zu **Parameter**.

Klicken Sie auf das **Umschalter**-Symbol, sodass das Feld **Ausblenden** aktiviert ist. Ändern Sie **Parametername** in `dynamic_city_hide`.

Klicken Sie auf das **Umschalter**-Symbol, sodass das Feld **Ausblenden** aktiviert ist. Ändern Sie **Parametername** in `dynamic_city_image`.

Klicken Sie auf **Speichern**.

![AEM Assets Dynamic Media](./images/aemdm54.png)

Klicken Sie auf **Vorschau**.

![AEM Assets Dynamic Media](./images/aemdm55.png)

Sie sollten das dann sehen. Aktivieren Sie das Symbol „Umschalter“, um **Alle Parameter einschließen**. Ändern Sie einige Eingabevariablen, wie im Screenshot angegeben. Sie sollten sehen, wie sich Ihr Bild basierend auf der bereitgestellten Eingabe dynamisch ändert. Die statischen Felder **city_paris**, **city_dubai** und **city_ny** sollten auf 1 gesetzt werden, was bedeutet, dass diese Bilder ausgeblendet werden.

Das Feld **dynamic_city_hide** sollte auf 0 gesetzt sein, was bedeutet, dass es angezeigt wird.

Das Feld **dynamic_city_image** enthält jetzt die URL zum Bild von Paris, das wie folgt aussieht: `vangeluwCitiSignalDM/citisignal-fiber-max-is-coming_citisignal-paris-1`.

![AEM Assets Dynamic Media](./images/aemdm56.png)

Wählen Sie das Wort **Paris** in der URL aus.

![AEM Assets Dynamic Media](./images/aemdm57.png)

Ändern Sie **paris** in `newyork` und klicken Sie dann auf eine andere Stelle in der Benutzeroberfläche, um die Bildänderung zum Bild von New York City anzuzeigen.

![AEM Assets Dynamic Media](./images/aemdm58.png)

Wählen Sie das Wort **newyork** aus und ändern Sie es in `dubai`. Klicken Sie dann auf eine andere Stelle in der Benutzeroberfläche, um die Bildänderung für das Bild der Stadt Dubai anzuzeigen.

Klicken Sie abschließend auf **Veröffentlichen**.

![AEM Assets Dynamic Media](./images/aemdm60.png)

Sie sollten das dann sehen. Klicken Sie **Ja**.

![AEM Assets Dynamic Media](./images/aemdm61.png)

Ihre Dynamic Media-Vorlage ist jetzt konfiguriert und erfolgreich veröffentlicht. In der nächsten Übung verwenden Sie diese Vorlage in Kombination mit einer E-Mail-Kampagne in Adobe Journey Optimizer.

## Nächste Schritte

Nächster Schritt: [Verwenden Sie Ihre Dynamic Media-Vorlage mit Adobe Journey Optimizer](./ex2.md){target="_blank"}

Zurück zu [Adobe Experience Manager Assets und Dynamic Media](./aemassetsdm.md){target="_blank"}

[Zurück zu „Alle Module“](./../../../overview.md){target="_blank"}
