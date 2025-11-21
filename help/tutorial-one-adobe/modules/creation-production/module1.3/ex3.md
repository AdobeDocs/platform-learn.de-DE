---
title: GenStudio for Performance Marketing-Kampagnenaktivierung für Meta
description: GenStudio for Performance Marketing-Kampagnenaktivierung für Meta
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 2c7ef715-b8af-4a5b-8873-5409b43d7cb0
source-git-commit: 9af7cc3e221ddacd8b6ddc02a2215b7d9c134d0a
workflow-type: tm+mt
source-wordcount: '1333'
ht-degree: 1%

---

# 1.3.3 Kampagnenaktivierung für Meta

>[!IMPORTANT]
>
>Um diese Übung abzuschließen, benötigen Sie Zugriff auf eine funktionierende AEM Assets CS Author-Umgebung mit aktiviertem AEM Assets Content Hub.
>
>Es gibt zwei Optionen:
>
>- Wenn Sie am Workshop zur technischen Aktivierung von GenStudio für CSC teilnehmen, haben Ihre Kursleiter eine AEM Assets CS Author-Umgebung für Sie erstellt. Bitte überprüfen Sie mit ihnen, wie der Name lautet und wie Sie fortfahren.
>
>- Wenn Sie den vollständigen Pfad des Tutorials „One Adobe&quot; befolgen, gehen Sie zu Übung [Adobe Experience Manager Cloud Service und Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Folgen Sie den Anweisungen dort, und Sie haben Zugriff auf eine solche Umgebung.

>[!IMPORTANT]
>
>Um alle Schritte in dieser Übung ausführen zu können, benötigen Sie Zugriff auf eine bestehende Adobe Workfront-Umgebung. In dieser Umgebung müssen Sie ein Projekt und einen Genehmigungs-Workflow erstellt haben. Wenn Sie die Übungen [Workflow-Verwaltung mit Adobe Workfront](./../../../modules/workflow-planning/module1.2/workfront.md){target="_blank"} befolgen, stehen Ihnen die erforderlichen Einstellungen zur Verfügung.

>[!IMPORTANT]
>
>Wenn Sie zuvor ein AEM Assets CS-Programm mit einer Authoring- und AEM Assets-Umgebung konfiguriert haben, kann es sein, dass sich Ihre AEM CS-Sandbox im Ruhezustand befand. Da der Ruhezustand einer solchen Sandbox 10-15 Minuten dauert, ist es ratsam, den Ruhezustand jetzt zu beenden, damit Sie nicht zu einem späteren Zeitpunkt warten müssen.

## 1.3.3.1 Kampagne erstellen

GenStudio for Performance Marketing Navigieren Sie in **0** im **Menü auf der linken Seite zu „Kampagnen“.** Klicken Sie auf **+ Kampagne**.

![GSPeM](./images/gscampaign1.png)

Anschließend sollte eine leere Kampagnenübersicht angezeigt werden.

![GSPeM](./images/gscampaign2.png)

Verwenden Sie für den Feldnamen `--aepUserLdap-- - CitiSignal Fiber Launch Campaign`.

Verwenden Sie für **Feld** Beschreibung“ den folgenden Text.

```
The CitiSignal Fiber Launch campaign introduces CitiSignal’s flagship fiber internet service—CitiSignal Fiber Max—to key residential markets. This campaign is designed to build awareness, drive sign-ups, and establish CitiSignal as the go-to provider for ultra-fast, reliable, and future-ready internet. The campaign will highlight the product’s benefits for remote professionals, online gamers, and smart home families, using persona-driven messaging across digital and physical channels.
```

Verwenden Sie für **Feld „Ziel** den folgenden Text.

```
Generate brand awareness in target regions
Drive early sign-ups and pre-orders for CitiSignal Fiber Max
Position CitiSignal as a premium, customer-first fiber internet provider
Educate consumers on the benefits of fiber over cable or DSL
```

Verwenden Sie für das Feld **Key Messaging** den folgenden Text.

```
Supporting Points:
Symmetrical speeds up to 2 Gbps
Whole-home Wi-Fi 6E coverage
99.99% uptime guarantee
24/7 concierge support
No data caps or throttling
 Channels:
Digital Advertising: Google Display, YouTube pre-roll, Meta (Facebook/Instagram), TikTok (for gamers)
Email Marketing: Persona-segmented drip campaigns
Social Media: Organic and paid posts with testimonials, speed demos, and influencer partnerships
Out-of-Home (OOH): Billboards, transit ads in suburban commuter corridors
Local Events: Pop-up booths at tech expos, family festivals, and gaming tournaments
Direct Mail: Personalized flyers with QR codes for early sign-up discounts
 
Target Regions:
Primary Launch Markets:
Denver Metro Area, CO
Austin, TX
Raleigh-Durham, NC
Salt Lake City, UT
Demographic Focus:
Suburban neighborhoods with high remote work density
Areas with high smart home adoption
Zip codes with underserved or dissatisfied cable customers
```

Sie sollten dann Folgendes haben:

![GSPeM](./images/gscampaign3.png)

Scrollen Sie nach unten, um weitere Felder anzuzeigen:

![GSPeM](./images/gscampaign4.png)

Wählen Sie für **Feld** das heutige Datum aus.

Legen Sie für das Feld **Ende** das Datum in einem Monat fest.

Legen Sie für **Feld** Status“ auf **Aktiv** fest.

Legen Sie das Feld **Kanäle** auf **Meta**, **Email**, **Paid Media**, **Display** fest.

Wählen Sie für **Feld** Regionen“ eine Region Ihrer Wahl aus.

Für das Feld Für das Feld **Verweise** > **Produkte** wählen Sie die `--aepUserLdap-- - CitiSignal Fiber Max`.

**Verweise** > **Personas**: Wählen Sie die `--aepUserLdap-- - Remote Professionals`, `--aepUserLdap-- - Online Gamers`, `--aepUserLdap-- - Smart Home Families` aus

Sie sollten dies dann sehen:

![GSPeM](./images/gscampaign5.png)

Ihre Kampagne ist jetzt bereit. Klicken Sie auf den **Pfeil**, um zurückzukehren.

![GSPeM](./images/gscampaign6.png)

Ihre Kampagne wird dann in der Liste angezeigt. Klicken Sie auf das Symbol Kalenderansicht , um die Ansicht zum Kampagnenkalender zu ändern.

![GSPeM](./images/gscampaign7.png)

Anschließend sollte ein Kampagnenkalender angezeigt werden, der einen visuelleren Eindruck davon vermittelt, welche Kampagnen zu welchem Zeitpunkt aktiv sind.

![GSPeM](./images/gscampaign8.png)

## 1.3.3.2 Setup-Verbindung mit Meta

>[!IMPORTANT]
>
>Um Ihre Verbindung mit Meta einzurichten, müssen Sie über ein Meta-Benutzerkonto verfügen und dieses Benutzerkonto muss einem Meta Business-Konto hinzugefügt werden.

Um die Verbindung zu Meta herzustellen, klicken Sie auf die **mit den drei Punkten…** und wählen Sie **Einstellungen**.

![GSPeM](./images/gsconnection1.png)

Klicken Sie **Verbinden** für **Meta Ads**.

![GSPeM](./images/gsconnection2.png)

Melden Sie sich mit Ihrem Meta-Konto an. Klicken Sie auf **Fortfahren**.

![GSPeM](./images/gsconnection3.png)

Wenn Ihr Konto mit einem Meta Business-Konto verknüpft ist, können Sie das in Meta konfigurierte Geschäftsportfolio auswählen.

![GSPeM](./images/gsconnection5.png)

Nachdem die Verbindung erfolgreich hergestellt wurde, klicken Sie auf die Zeile, in der **X verbundene(s) Konto(e)** steht.

![GSPeM](./images/gsconnection4.png)

Sie sollten dann die Details des Meta Business-Kontos sehen, das mit GenStudio for Performance Marketing verbunden ist.

![GSPeM](./images/gsconnection6.png)

## 1.3.3.3 Neues Asset erstellen

Navigieren Sie zu [https://firefly.adobe.com/](https://firefly.adobe.com/){target="_blank"}. Geben Sie den `a neon rabbit running very fast through space` ein und klicken Sie auf **Generieren**.

![GSPeM](./images/gsasset1.png)

Anschließend werden mehrere Bilder generiert. Wählen Sie das Bild aus, das Ihnen am besten gefällt, klicken Sie auf das Symbol **Freigeben** auf dem Bild und wählen Sie dann **In Adobe Express öffnen**.

![GSPeM](./images/gsasset2.png)

Anschließend wird das soeben generierte Bild in Adobe Express zur Bearbeitung verfügbar. Jetzt müssen Sie das CitiSignal-Logo auf dem Bild hinzufügen. Navigieren Sie dazu zu **Marken**.

![GSPeM](./images/gsasset3.png)

Anschließend sollte die in GenStudio for Performance Marketing erstellte CitiSignal-Markenvorlage in Adobe Express angezeigt werden. Klicken Sie, um Ihre Markenvorlage auszuwählen, die `--aepUserLdap-- - CitiSignal` benannt werden soll.

![GSPeM](./images/gsasset4.png)

Gehen Sie zu **Logos** und klicken Sie auf das **weiß** Citisignal-Logo, um es auf dem Bild abzulegen.

![GSPeM](./images/gsasset5.png)

Positionieren Sie das CitiSignal-Logo oben auf Ihrem Bild, nicht zu weit von der Mitte entfernt.

![GSPeM](./images/gsasset6.png)

Klicken Sie anschließend auf **Freigeben**.

![GSPeM](./images/gsasset7.png)

**AEM Assets**.

![GSPeM](./images/gsasset8.png)

Klicken Sie **Ordner auswählen**. Ändern Sie den Namen des Assets in `--aepUserLdap-- - neon rabbit`.

![GSPeM](./images/gsasset9.png)

Wählen Sie Ihr AEM Assets CS-Repository mit dem Namen `--aepUserLdap-- - CitiSignal` und dann die `--aepUserLdap-- - CitiSignal Fiber Campaign` aus. Klicken Sie auf **Auswählen**.

![GSPeM](./images/gsasset11.png)

Sie sollten das dann sehen. Klicken Sie **1 Asset hochladen**. Ihr Bild wird jetzt in AEM Assets CS hochgeladen.

![GSPeM](./images/gsasset12.png)

Navigieren Sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Öffnen Sie **Experience Manager Assets**.

![GSPeM](./images/gsasset13.png)

Wählen Sie Ihre AEM Assets CS-Umgebung aus, die `--aepUserLdap-- - CitiSignal dev` benannt werden soll.

![GSPeM](./images/gsasset14.png)

Wechseln Sie zu **Assets** und doppelklicken Sie dann auf die `--aepUserLdap-- - CitiSignal Fiber Campaign`.

![GSPeM](./images/gsasset15.png)

Sie sollten dann etwas Ähnliches sehen. Doppelklicken Sie auf die `--aepUserLdap-- - neon rabbit`.

![GSPeM](./images/gsasset16.png)

Das `--aepUserLdap-- - neon rabbit` wird dann angezeigt. Ändern Sie **Status** in **Genehmigt** und klicken Sie dann auf **Speichern**

>[!IMPORTANT]
>
>Wenn der Status eines Bildes nicht auf **Genehmigt** festgelegt ist, ist das Bild in GenStudio for Performance Marketing nicht sichtbar. In GenStudio for Performance Marketing sind nur genehmigte Assets verfügbar.

![GSPeM](./images/gsasset17.png)

Wechseln Sie zurück zu GenStudio for Performance Marketing. Wechseln Sie im linken Menü zu **Assets** und wählen Sie Ihr AEM Assets CS-Repository aus, das `--aepUserLdap-- - CitiSignal` benannt werden soll. Das soeben erstellte und genehmigte Bild wird dann in GenStudio for Performance Marketing verfügbar.

![GSPeM](./images/gsasset18.png)

## 1.3.3.4 Erstellen und Genehmigen von Meta-Anzeigen

Navigieren Sie im linken Menü zu **Erstellen**. **Meta**.

![GSPeM](./images/gsad1.png)

Wählen Sie die zuvor importierte Vorlage **0}Meta-Anzeige“ aus, die** heißt. `--aepUserLdap---citisignal-meta-ad` Klicken Sie **Verwenden**.

![GSPeM](./images/gsad2.png)

Sie sollten das dann sehen. Ändern Sie den Namen Ihrer Anzeige in `--aepUserLdap-- - Meta Ad Fiber Max`.

Wählen **unter** die folgenden Optionen aus:

- **Marke**: `--aepUserLdap-- - CitiSignal`
- **language**: `English (US)`
- **Persona**: `--aepUserLdap-- - Smart Home Families`
- **Produkt**: `--aepUserLdap-- - CitiSignal Fiber Max`

Klicken Sie **Aus Inhalt auswählen**.

![GSPeM](./images/gsad3.png)

Wählen Sie die Asset-`--aepUserLdap-- - neon rabbit.png` aus. Klicken Sie **Verwenden**.

![GSPeM](./images/gsad4.png)

Geben Sie den `focus on lightning fast internet for big families` ein und klicken Sie auf **Generieren**.

![GSPeM](./images/gsad5.png)

Sie sollten dann so etwas sehen. Ihre Anzeigen können jetzt überprüft und genehmigt werden. Klicken Sie dazu auf **Genehmigung anfordern**, um eine Verbindung zu Adobe Workfront herzustellen.

![GSPeM](./images/gsad6.png)

Wählen Sie Ihr Adobe Workfront-Projekt aus, das `--aepUserLdap-- - CitiSignal Fiber Launch` benannt werden soll. Geben Sie unter **Personen einladen** Ihre eigene E-Mail-Adresse ein und stellen Sie sicher, dass Ihre Rolle auf &quot;**&quot;** ist.

![GSPeM](./images/gsad7.png)

Alternativ können Sie auch einen vorhandenen Genehmigungs-Workflow in Adobe Workfront verwenden. Klicken Sie dazu auf **Vorlage verwenden** und wählen Sie die `--aepuserLdap-- - Approval Workflow` aus. Klicken Sie auf **Senden**.

![GSPeM](./images/gsad8.png)

Klicken Sie **Kommentare in Workfront anzeigen**, um zur Benutzeroberfläche für den Adobe Workfront-Korrekturabzug weitergeleitet zu werden.

![GSPeM](./images/gsad9.png)

Klicken Sie in der Adobe Workfront-Benutzeroberfläche für Korrekturabzüge auf **Entscheidung treffen**.

![GSPeM](./images/gsad10.png)

Wählen Sie **Genehmigt** und klicken Sie auf **Entscheidung treffen**.

![GSPeM](./images/gsad11.png)

Klicken Sie auf **Veröffentlichen**.

![GSPeM](./images/gsad12.png)

Wählen Sie Ihre Campaign-`--aepUserLdap-- - CitiSignal Fiber Launch Campaign` aus und klicken Sie auf **Veröffentlichen**.

![GSPeM](./images/gsad13.png)

Klicken Sie **Im Inhalt öffnen**.

![GSPeM](./images/gsad14.png)

Die 4 Meta-Anzeigen sind jetzt unter **Inhalt** > **Erlebnisse** verfügbar.

![GSPeM](./images/gsad15.png)

## 1.3.3.5 Anzeigen in Meta veröffentlichen

Wählen Sie eine der Anzeigen aus und klicken Sie dann auf **Aktivieren**.

![GSPeM](./images/gsmetaad1.png)

Wählen Sie eine **Call to action** aus der Liste aus und geben Sie eine Beispiel-URL ein. Klicken Sie auf **Weiter**.

![GSPeM](./images/gsmetaad3.png)

Wählen Sie das Meta-Konto, die verknüpfte Facebook-Seite, die Meta-Kampagne und das Meta-Anzeigenset aus.

Geben Sie Ihrem Add einen Namen und verwenden Sie `--aepUserLdap-- Fiber Max Ad`.

Klicken Sie auf **Weiter**.

![GSPeM](./images/gsmetaad4.png)

Klicken Sie auf **Veröffentlichen**.

![GSPeM](./images/gsmetaad5.png)

Klicken Sie auf **OK**.

![GSPeM](./images/gsmetaad6.png)

Der Status Ihrer Anzeige ist jetzt auf &quot;**&quot;**, was einige Minuten dauern kann.

![GSPeM](./images/gsmetaad7.png)

Nach einigen Minuten ändert sich der Status der Anzeige in &quot;**&quot;**. Das bedeutet, dass die Anzeige von GenStudio for Performance Marketing an Meta gesendet wurde. Das bedeutet nicht, dass die Anzeige bereits in Meta veröffentlicht wurde! Im Geschäftskonto von Meta müssen Sie noch eine Reihe von Schritten ausführen, um die Anzeige zu erstellen und zu veröffentlichen, damit sie für die Benutzenden auf den verschiedenen Meta-Plattformen sichtbar ist.

Klicken Sie **Details anzeigen**.

![GSPeM](./images/gsmetaad8.png)

Klicken Sie **Öffnen**, um zu Ihrem Meta Business-Konto zu gelangen.

>[!IMPORTANT]
>
>Wenn Sie keinen Zugriff auf das mit Ihrer Umgebung verbundene Meta Business-Konto haben, können Sie diese Anzeige in Meta nicht visualisieren.

![GSPeM](./images/gsmetaad9.png)

Hier ist ein Überblick über die Anzeige, die Sie gerade erstellt haben, jetzt aber in Meta.

![GSPeM](./images/gsmetaad10.png)

Sie haben jetzt diese Übung abgeschlossen.

## Nächste Schritte

Wechseln Sie zu [Zusammenfassung und Vorteile](./summary.md){target="_blank"}

Zurück zu [GenStudio for Performance Marketing](./genstudio.md){target="_blank"}

Zurück zu [Alle Module](./../../../overview.md){target="_blank"}
