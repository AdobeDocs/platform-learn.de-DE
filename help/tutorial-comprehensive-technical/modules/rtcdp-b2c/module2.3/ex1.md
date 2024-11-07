---
title: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Ausführen von Aktionen - Erstellen eines Segments
description: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Ausführen von Aktionen - Erstellen eines Segments
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 2%

---

# 2.3.1 Segment erstellen

In dieser Übung erstellen Sie ein Segment, indem Sie den Segment Builder von Adobe Experience Platform verwenden.

## 2.3.1.1 Kontext

In der heutigen Welt muss die Reaktion auf das Verhalten eines Kunden in Echtzeit erfolgen. Eine Möglichkeit, auf das Kundenverhalten in Echtzeit zu reagieren, besteht darin, ein Segment zu verwenden, sofern das Segment in Echtzeit qualifiziert ist. In dieser Übung müssen Sie ein Segment erstellen, unter Berücksichtigung der tatsächlichen Aktivitäten auf der Website, die wir verwendet haben.

## 2.3.1.2 Verhalten identifizieren, auf das reagiert werden soll

Wechseln Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web8.png)

Sie können nun den unten stehenden Fluss zum Zugriff auf die Website ausführen. Klicken Sie auf **Integrationen**.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web1.png)

Wählen Sie auf der Seite **Integrationen** die Datenerfassungseigenschaft aus, die in Übung 0.1 erstellt wurde.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web2.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](./../../../modules/gettingstarted/gettingstarted/images/web7.png)

In diesem Beispiel möchten Sie auf einen bestimmten Kunden reagieren, der ein bestimmtes Produkt anzeigt.
Gehen Sie von der Startseite **Luma** zu **Men** und klicken Sie auf das Produkt **PROTEUS FITNESS JACKSHIRT**.

![Datenaufnahme](./images/homenadia.png)

Wenn also jemand die Produktseite für **PROTEUS FITNESS JACKSHIRT** besucht, möchten Sie in der Lage sein, Maßnahmen zu ergreifen. Als Erstes müssen Sie eine Aktion durchführen, indem Sie ein Segment definieren.

![Datenaufnahme](./images/homenadiapp.png)

## 2.3.1.3 Segment erstellen

Wechseln Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox** auswählen. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie dazu in der blauen Zeile oben auf Ihrem Bildschirm auf den Text **[!UICONTROL Produktions-Prod]** . Nachdem Sie die entsprechende [!UICONTROL Sandbox] ausgewählt haben, sehen Sie die Bildschirmänderung und befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Navigieren Sie im Menü auf der linken Seite zu **Segmente** und gehen Sie dann zu **Durchsuchen** , wo Sie eine Übersicht über alle vorhandenen Segmente anzeigen können. Klicken Sie auf die Schaltfläche **Segment erstellen** , um mit der Erstellung eines neuen Segments zu beginnen.

![Segmentierung](./images/menuseg.png)

Wie oben erwähnt, müssen Sie ein Segment aus allen Kunden erstellen, die das Produkt **PROTEUS FITNESS JACKSHIRT** angesehen haben.

Um dieses Segment zu erstellen, müssen Sie ein Ereignis hinzufügen. Sie können alle Ereignisse finden, indem Sie in der Menüleiste **Segmente** auf das Symbol **Ereignisse** klicken.

Als Nächstes sehen Sie den Knoten **XDM ExperienceEvent** der obersten Ebene.

Um Kunden zu finden, die das Produkt **PROTEUS FITNESS JACKSHIRT** besucht haben, klicken Sie auf **XDM ExperienceEvent**.

![Segmentierung](./images/findee.png)

Scrollen Sie nach unten zu **Produktlistenelementen** und klicken Sie darauf.

![Segmentierung](./images/see.png)

Wählen Sie &quot;**Name**&quot;aus und ziehen Sie das Objekt &quot;**Name**&quot;aus dem linken Menü &quot;**Produktlistenelemente**&quot;auf die Arbeitsfläche des Segmentaufbaus in den Abschnitt &quot;**Ereignisse**&quot;.

![Segmentierung](./images/eewebpdtlname1.png)

Der Vergleichsparameter sollte **gleich** sein und im Eingabefeld `PROTEUS FITNESS JACKSHIRT` eingeben.

![Segmentierung](./images/pv.png)

Ihre **Ereignisregeln** sollten jetzt wie folgt aussehen: Jedes Mal, wenn Sie ein Element zum Segment Builder hinzufügen, können Sie auf die Schaltfläche **Schätzung aktualisieren** klicken, um eine neue Schätzung der Population in Ihrem Segment zu erhalten.

![Segmentierung](./images/ldap4.png)

Geben wir schließlich Ihrem Segment einen Namen und speichern es.

Verwenden Sie als Namenskonvention:

- `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`

Ihr Segmentname sollte wie folgt aussehen:
`vangeluw - Interest in PROTEUS FITNESS JACKSHIRT`

Klicken Sie anschließend auf die Schaltfläche **Speichern und schließen** , um Ihr Segment zu speichern.

![Segmentierung](./images/segmentname.png)

Sie werden nun zur Übersichtsseite des Segments zurückgeführt.

![Segmentierung](./images/savedsegment.png)

Nächster Schritt: [2.3.2 Überprüfen Sie, wie das DV360-Ziel mit Zielen konfiguriert wird](./ex2.md)

[Zurück zu Modul 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
