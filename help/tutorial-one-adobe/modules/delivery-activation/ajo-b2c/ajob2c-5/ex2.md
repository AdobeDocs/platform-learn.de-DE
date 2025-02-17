---
title: Erstellen Ihrer Kampagne mit AJO Translation Services
description: Erstellen Ihrer Kampagne mit AJO Translation Services
kt: 5342
doc-type: tutorial
exl-id: 536caf45-c614-48e8-adbb-6dc67d1a9606
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '1599'
ht-degree: 9%

---

# 3.5.2 Erstellen einer Kampagne

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/). Auf **Journey Optimizer**.

![Übersetzungen](./images/ajolp1.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Stellen Sie zunächst sicher, dass Sie die richtige Sandbox verwenden. Die zu verwendende Sandbox heißt `--aepSandboxName--`.

![ACOP](./images/ajolp2.png)

>[!NOTE]
>
>Falls Sie Ihre Kopf- und Fußzeilenfragmente bereits im Rahmen der Übung ([ 3.1.2.1](./../ajob2c-1/ex2.md) und [Übung 3.1.2.2](./../ajob2c-1/ex2.md)) erstellt haben, springen Sie bitte zu Übung 3.5.2.3 Kampagne „Glasfaser erstellen“ vor. Erstellen Sie die Kopf- und Fußzeilenfragmente nicht erneut.

## 3.5.2.1 Erstellen des Header-Fragments

Klicken Sie im linken Menü auf **Fragmente**. Ein Fragment ist eine wiederverwendbare Komponente in Journey Optimizer, die Duplizierungen vermeidet und zukünftige Änderungen erleichtert, die sich auf alle Nachrichten auswirken sollten, z. B. Änderungen an einer Kopf- oder Fußzeile in einer E-Mail-Nachricht.

Klicken Sie **Fragment erstellen**.

![ACOP](./images/fragm1.png)

Geben Sie den `--aepUserLdap-- - CitiSignal - Header` ein und wählen Sie **Typ: Visuelles Fragment**. Klicken Sie auf **Erstellen**.

![ACOP](./images/fragm2.png)

Sie werden es dann sehen. Im linken Menü finden Sie die Strukturkomponenten, mit denen Sie die Struktur der E-Mail definieren können (Zeilen und Spalten).

Ziehen Sie per Drag-and-Drop eine **1:1** Spalte aus dem Menü auf die Arbeitsfläche. Dies ist der Platzhalter für das Logo-Bild.

![Journey Optimizer](./images/fragm3.png)

Als Nächstes können Sie Inhaltskomponenten verwenden, um Inhalte in diesen Blöcken hinzuzufügen. Ziehen Sie eine **Bild**-Komponente per Drag-and-Drop in die erste Zelle in der ersten Zeile. Klicken Sie auf **Durchsuchen**.

![Journey Optimizer](./images/fragm4.png)

Anschließend wird ein Popup geöffnet, in dem Ihre AEM Assets Media Library angezeigt wird. Gehen Sie zum Ordner **citi-signal-images**, klicken Sie auf das Bild **CitiSignal-Logo-White.png** und klicken Sie auf **Auswählen**.

>[!NOTE]
>
>Wenn Sie die Citi Signal-Bilder in Ihrer AEM Assets-Bibliothek nicht sehen, finden Sie sie [hier](./../../../../assets/ajo/CitiSignal-images.zip). Laden Sie sie auf Ihren Desktop herunter, erstellen Sie den Ordner **citi-signal-images** und laden Sie alle Bilder in diesem Ordner hoch.

![Journey Optimizer](./images/fragm5.png)

Sie werden es dann sehen. Ihr Bild ist weiß und wird noch nicht angezeigt. Sie sollten jetzt eine Hintergrundfarbe definieren, damit das Bild korrekt angezeigt wird. Klicken Sie **Stile** und dann auf das Feld **Hintergrundfarbe**.

![Journey Optimizer](./images/fragm6.png)

Ändern Sie im Popup den **Hex**-Farbcode in **#8821F4** und ändern Sie dann den Fokus, indem Sie in das Feld **100%** klicken. Anschließend sehen Sie die neue Farbe, die auf das Bild angewendet wurde.

![Journey Optimizer](./images/fragm7.png)

Das Bild ist im Moment auch etwas zu groß. Ändern wir die Breite, indem wir den Umschalter **Breite** auf **40 %** verschieben.

![Journey Optimizer](./images/fragm8.png)

Ihr Header-Fragment ist jetzt bereit. Klicken Sie **Speichern** und anschließend auf den Pfeil, um zum vorherigen Bildschirm zurückzukehren.

![Journey Optimizer](./images/fragm9.png)

Das Fragment muss veröffentlicht werden, bevor es verwendet werden kann. Klicken Sie auf **Veröffentlichen**.

![Journey Optimizer](./images/fragm10.png)

Nach einigen Minuten sehen Sie, dass der Status Ihres Fragments in „Live **geändert**.
Als Nächstes sollten Sie ein neues Fragment für die Fußzeile Ihrer E-Mail-Nachrichten erstellen. Klicken Sie **Fragment erstellen**.

![Journey Optimizer](./images/fragm11.png)

## 3.5.2.2 Erstellen des Fragments Fußzeile

Klicken Sie **Fragment erstellen**.

![Journey Optimizer](./images/fragm11.png)

Geben Sie den `--aepUserLdap-- - CitiSignal - Footer` ein und wählen Sie **Typ: Visuelles Fragment**. Klicken Sie auf **Erstellen**.

![Journey Optimizer](./images/fragm12.png)

Sie werden es dann sehen. Im linken Menü finden Sie die Strukturkomponenten, mit denen Sie die Struktur der E-Mail definieren können (Zeilen und Spalten).

Ziehen Sie per Drag-and-Drop eine **1:1** Spalte aus dem Menü auf die Arbeitsfläche. Dies ist der Platzhalter für den Inhalt der Fußzeile.

![Journey Optimizer](./images/fragm13.png)

Als Nächstes können Sie Inhaltskomponenten verwenden, um Inhalte in diesen Blöcken hinzuzufügen. Ziehen Sie eine **HTML**-Komponente per Drag-and-Drop in die erste Zelle der ersten Zeile. Klicken Sie auf die Komponente, um sie auszuwählen, und klicken Sie dann auf das **&lt;/>**, um den HTML-Quell-Code zu bearbeiten.

![Journey Optimizer](./images/fragm14.png)

Sie werden es dann sehen.

![Journey Optimizer](./images/fragm15.png)

Kopieren Sie das folgende HTML-Codefragment und fügen Sie es in das Fenster **HTML bearbeiten** in Journey Optimizer ein.

```html
<!--[if mso]><table cellpadding="0" cellspacing="0" border="0" width="100%"><tr><td style="text-align: center;" ><![endif]-->
<table style="width: auto; display: inline-block;">
  <tbody>
    <tr class="component-social-container">
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://www.facebook.com" data-component-social-icon-id="facebook">
        
        </a>
      </td>
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://x.com" data-component-social-icon-id="twitter">
        
        </a>
      </td>
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://www.instagram.com" data-component-social-icon-id="instagram">
         
        </a>
      </td>
    </tr>
  </tbody>
</table>
<!--[if mso]></td></tr></table><![endif]-->
```

Dann hast du das hier. In den Zeilen 7, 12 und 17 müssen Sie jetzt eine Bilddatei einfügen, indem Sie die Assets in Ihrer AEM Assets-Bibliothek verwenden.

![Journey Optimizer](./images/fragm16.png)

Vergewissern Sie sich, dass sich Ihr Cursor in Zeile 7 befindet, und klicken Sie dann im **Menü auf** Assets. Klicken Sie **Asset-Auswahl öffnen**, um Ihr Bild auszuwählen.

![Journey Optimizer](./images/fragm17.png)

Öffnen Sie den Ordner **citi-signal-images** und klicken Sie auf das Bild **Icon_facebook.png**. Klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/fragm18.png)

Stellen Sie sicher, dass sich der Cursor in Zeile 12 befindet, und klicken Sie dann auf **Asset-Auswahl öffnen**, um Ihr Bild auszuwählen.

![Journey Optimizer](./images/fragm19.png)

Öffnen Sie den Ordner **citi-signal-images** und klicken Sie auf das Bild **Icon_X.png**. Klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/fragm20.png)

Stellen Sie sicher, dass sich der Cursor in Zeile 17 befindet, und klicken Sie dann auf **Asset-Auswahl öffnen**, um Ihr Bild auszuwählen.

![Journey Optimizer](./images/fragm21.png)

Öffnen Sie den Ordner **citi-signal-images** und klicken Sie auf das Bild **Icon_Instagram.png**. Klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/fragm22.png)

Sie werden es dann sehen. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/fragm23.png)

Sie werden dann wieder im Editor angezeigt. Ihre Symbole sind noch nicht sichtbar, da der Hintergrund und die Bilddateien alle weiß sind. Um die Hintergrundfarbe zu ändern, gehen Sie zu **Stile** und klicken Sie auf das Kontrollkästchen **Hintergrundfarbe**.

![Journey Optimizer](./images/fragm24.png)

Ändern Sie den **Hex**-Farbcode in **#000000**.

![Journey Optimizer](./images/fragm25.png)

Ändern Sie die Ausrichtung so, dass sie zentriert ist.

![Journey Optimizer](./images/fragm26.png)

Fügen wir der Fußzeile einige andere Teile hinzu. Ziehen Sie eine **image**-Komponente über die soeben erstellte HTML-Komponente. Klicken Sie auf **Durchsuchen**.

![Journey Optimizer](./images/fragm27.png)

Klicken Sie auf die **`CitiSignal_Footer_Logo.png`** Bilddatei, um sie auszuwählen, und klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/fragm28.png)

Wechseln Sie zu **Stile** und klicken Sie auf das Kontrollkästchen **Hintergrundfarbe**, ändern wir es wieder in Schwarz. Ändern Sie den **Hex**-Farbcode in **#000000**.

![Journey Optimizer](./images/fragm29.png)

Ändern Sie die Breite in **20%** und stellen Sie sicher, dass die Ausrichtung zentriert ist.

![Journey Optimizer](./images/fragm30.png)

Ziehen Sie als Nächstes per Drag-and **Drop eine** Textkomponente“ unter die von Ihnen erstellte HTML-Komponente. Klicken Sie auf **Durchsuchen**.

![Journey Optimizer](./images/fragm31.png)

Kopieren Sie den folgenden Text und fügen Sie ihn ein, indem Sie den Platzhaltertext ersetzen.

```
1234 N. South Street, Anywhere, US 12345

Unsubscribe

©2024 CitiSignal, Inc and its affiliates. All rights reserved.
```

Legen Sie die **Textausrichtung** auf Zentriert fest.

![Journey Optimizer](./images/fragm32.png)

Ändern Sie die **Schriftfarbe** in Weiß, **#FFFFFF**.

![Journey Optimizer](./images/fragm33.png)

Ändern Sie die **Hintergrundfarbe** in Schwarz, **#000000**.

![Journey Optimizer](./images/fragm34.png)

Wählen Sie den Text **Abmelden** in der Fußzeile aus und klicken Sie auf das **Link**-Symbol in der Menüleiste. Legen Sie **Typ** auf **Externes Opt-out/Abmeldung** und die URL auf **https://aepdemo.net/unsubscribe.html** fest (es ist nicht zulässig, eine leere URL für den Abmelde-Link zu haben).

![Journey Optimizer](./images/fragm35.png)

Dann hast du das hier. Ihre Fußzeile ist jetzt bereit. Klicken Sie **Speichern** und anschließend auf den Pfeil, um zur vorherigen Seite zurückzukehren.

![Journey Optimizer](./images/fragm36.png)

Klicken Sie **Veröffentlichen**, um Ihre Fußzeile zu veröffentlichen, damit sie in einer E-Mail verwendet werden kann.

![Journey Optimizer](./images/fragm37.png)

Nach einigen Minuten sehen Sie, dass der Status Ihrer Fußzeile auf „Live **geändert**.

![Journey Optimizer](./images/fragm38.png)

## 3.5.2.3 Erstellen einer Fibre-Channel-Kampagne

Im Folgenden erstellen Sie eine Kampagne. Im Gegensatz zum ereignisbasierten Journey der vorherigen Übung, das auf eingehenden Erlebnisereignissen oder Zielgruppeneintritten oder -austritten beruht, um eine Journey für einen bestimmten Kunden Trigger, richten sich Kampagnen mit einzigartigen Inhalten wie Newslettern, einmaligen Werbeaktionen oder allgemeinen Informationen oder regelmäßig mit ähnlichen Inhalten, die regelmäßig gesendet werden, wie z. B. Geburtstagskampagnen und Erinnerungen.

Gehen Sie im Menü zu **Kampagnen** und klicken Sie auf **Kampagne erstellen**.

![Journey Optimizer](./images/oc43.png)

Wählen Sie **Geplant - Marketing** und klicken Sie auf **Erstellen**.

![Journey Optimizer](./images/campaign1.png)

Konfigurieren Sie im Bildschirm zur Kampagnenerstellung Folgendes:

- **Name**: `--aepUserLdap-- - CitiSignal Fiber`.
- **Beschreibung**: Fibre Campaign
- **Identitätstyp**: Ändern in E-Mail

![Journey Optimizer](./images/campaign2.png)

Scrollen Sie nach unten zu **Aktion**. Wählen Sie für **Aktion** die Option **E-Mail**.

![Journey Optimizer](./images/campaign3.png)

Wählen Sie dann eine vorhandene **E-Mail-Konfiguration**. Sie werden den Inhalt in einigen Minuten bearbeiten.

![Journey Optimizer](./images/campaign3a.png)

Scrollen Sie nach oben zu **Zielgruppe**. Klicken Sie **Zielgruppe auswählen**.

![Journey Optimizer](./images/campaign2b.png)

Wählen Sie für **Zielgruppe** die Zielgruppe aus, die Sie in [1.3.3 Erstellen einer Federated Composition](./../../datacollection/dc1.3/ex3.md) erstellt haben, die `--aepUserLdap-- - CitiSignal Eligible for Fiber` heißt. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/campaign2a.png)

Scrollen Sie nach unten zu **Zeitplan**. Wählen Sie für **Zeitplan** die Option **An einem bestimmten Datum und zu** Uhrzeit“ und legen Sie eine Uhrzeit der Wahl fest.

![Journey Optimizer](./images/campaign4.png)

Sie können jetzt mit der Erstellung der E-Mail-Nachricht beginnen. Scrollen Sie nach oben und klicken Sie auf **Inhalt bearbeiten**.

![Journey Optimizer](./images/campaign5.png)

Sie werden es dann sehen. Verwenden Sie für **Betreffzeile** Folgendes:

```
{{profile.person.name.firstName}}, here's your Fiber offer!
```

Klicken Sie anschließend auf **E-Mail-Textkörper bearbeiten**.

![Journey Optimizer](./images/campaign6.png)

Wählen Sie **Von Grund auf gestalten**.

![Journey Optimizer](./images/campaign7.png)

Sie werden es dann sehen. Im linken Menü finden Sie die Strukturkomponenten, mit denen Sie die Struktur der E-Mail definieren können (Zeilen und Spalten).

Ziehen Sie per Drag-and-Drop viermal pro **1:1** auf die Arbeitsfläche, was Ihnen diese Struktur geben sollte:

![Journey Optimizer](./images/campaign8.png)

Navigieren Sie im linken Menü zu **Fragmente**. Ziehen Sie die zuvor erstellte Kopfzeile auf die erste Komponente auf der Arbeitsfläche. Ziehen Sie die zuvor erstellte Fußzeile auf die letzte Komponente auf der Arbeitsfläche.

![Journey Optimizer](./images/campaign9.png)

Klicken Sie im linken Menü auf das Symbol **+** . Navigieren Sie zu **Inhalte**, um Inhalte zur Arbeitsfläche hinzuzufügen.

![Journey Optimizer](./images/campaign10.png)

Ziehen Sie eine **Text**-Komponente per Drag-and-Drop auf die zweite Zeile.

![Journey Optimizer](./images/campaign11.png)

Wählen Sie den Standardtext in dieser Komponente aus **Geben Sie hier Ihren Text ein.** und durch den unten stehenden Text ersetzen. Ändern Sie die Ausrichtung in **Ausrichtung zentrieren**.

```javascript
Hi {{profile.person.name.firstName}}

As a CitiSignal customer, you're in pole position to discover our new Fiber offering. Have a look at the below offer and update your contract!

Stay connected.
```

![Journey Optimizer](./images/campaign12.png)

Ziehen Sie eine Komponente **Bild** per Drag-and-Drop in die dritte Zeile. Klicken Sie auf **Durchsuchen**.

![Journey Optimizer](./images/campaign13.png)

Wählen Sie das AEM Assets-Repository aus, das Sie als Teil der vorherigen Module erstellt haben. Dieses Repository sollte `--aepUserLdap-- - Citi Signal dev` benannt werden. Klicken Sie, um die `--aepUserLdap-- - Workfront Assets` zu öffnen.

![Journey Optimizer](./images/campaign15a.png)

Klicken Sie auf das Bild **2048x2048_buynow.png**, und klicken Sie auf **Auswählen**.

![Journey Optimizer](./images/campaign14.png)

Ihre Standard-Newsletter-E-Mail ist jetzt bereit. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/ready.png)

Kehren Sie zum Kampagnen-Dashboard zurück, indem Sie auf den **Pfeil** neben dem Betreffzeilentext in der oberen linken Ecke klicken.

![Journey Optimizer](./images/campaign19.png)

Klicken Sie auf **Zum Aktivieren überprüfen**.

![Journey Optimizer](./images/campaign20.png)

Sie erhalten dann möglicherweise diesen Fehler. In diesem Fall müssen Sie möglicherweise bis zu 24 Stunden warten, bis die Zielgruppe ausgewertet wurde, und dann erneut versuchen, Ihre Kampagne zu aktivieren. Möglicherweise müssen Sie auch den Zeitplan Ihrer Kampagne aktualisieren, damit sie zu einem späteren Zeitpunkt ausgeführt wird.

![Journey Optimizer](./images/campaign21a.png)

Klicken Sie **Aktivieren**.

![Journey Optimizer](./images/campaign21.png)

Nach der Aktivierung wird die Ausführung der Kampagne geplant.

![Journey Optimizer](./images/campaign22.png)

Du hast diese Übung beendet.

## Nächste Schritte

Wechseln Sie zu [3.5.3 Hinzufügen von Sprachen zu Ihrer E-Mail](./ex3.md)

Zurück zu [Adobe Journey Optimizer: Übersetzungs-Services](./ajotranslationsvcs.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
