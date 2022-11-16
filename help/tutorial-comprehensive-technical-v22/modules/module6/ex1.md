---
title: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Ausführen von Aktionen - Erstellen eines Segments
description: Echtzeit-Kundendatenplattform - Erstellen eines Segments und Ausführen von Aktionen - Erstellen eines Segments
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: c0778e81-4282-433d-9e02-37e32bf370ef
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 2%

---

# 6.1 Segment erstellen

In dieser Übung erstellen Sie ein Segment, indem Sie den Segment Builder von Adobe Experience Platform verwenden.

## 6.1.1 Kontext

In der heutigen Welt muss die Reaktion auf das Verhalten eines Kunden in Echtzeit erfolgen. Eine Möglichkeit, auf das Kundenverhalten in Echtzeit zu reagieren, besteht darin, ein Segment zu verwenden, sofern das Segment in Echtzeit qualifiziert ist. In dieser Übung müssen Sie ein Segment erstellen, unter Berücksichtigung der tatsächlichen Aktivitäten auf der Website, die wir verwendet haben.

## 6.1.2 Verhalten identifizieren, auf das reagiert werden soll

Navigieren Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](../module0/images/web8.png)

Sie können nun den unten stehenden Fluss ausführen, um auf die Website zuzugreifen. Klicken **Integrationen**.

![DSN](../module0/images/web1.png)

Im **Integrationen** müssen Sie die Datenerfassungseigenschaft auswählen, die in Übung 0.1 erstellt wurde.

![DSN](../module0/images/web2.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../module0/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](../module0/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../module0/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../module0/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../module0/images/web7.png)

In diesem Beispiel möchten Sie auf einen bestimmten Kunden reagieren, der ein bestimmtes Produkt anzeigt.
Aus dem **Luma** homepage, navigieren Sie zu **Männer** und klicken Sie auf das Produkt **PROTEUS FITNESS JACKSHIRT**.

![Datenaufnahme](./images/homenadia.png)

Wenn also jemand die Produktseite besucht für **PROTEUS FITNESS JACKSHIRT**, möchten Sie aktiv werden können. Als Erstes müssen Sie ein Segment definieren, um eine Aktion durchzuführen.

![Datenaufnahme](./images/homenadiapp.png)

## 6.1.3 Segment erstellen

Navigieren Sie zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach der Anmeldung landen Sie auf der Startseite von Adobe Experience Platform.

![Datenaufnahme](../module2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox**. Die auszuwählende Sandbox heißt ``--aepSandboxId--``. Klicken Sie hierzu auf den Text **[!UICONTROL Produktionsprodukt]** in der blauen Zeile auf Ihrem Bildschirm. Nach Auswahl der entsprechenden [!UICONTROL Sandbox], sehen Sie die Änderung des Bildschirms und befinden sich jetzt in Ihrem [!UICONTROL Sandbox].

![Datenaufnahme](../module2/images/sb1.png)

Gehen Sie im Menü auf der linken Seite zu **Segmente** und gehen Sie dann zu **Durchsuchen** wo Sie eine Übersicht über alle vorhandenen Segmente sehen können. Klicken Sie auf **Segment erstellen** -Schaltfläche, um mit der Erstellung eines neuen Segments zu beginnen.

![Segmentierung](./images/menuseg.png)

Wie oben erwähnt, müssen Sie ein Segment aus allen Kunden erstellen, die das Produkt angesehen haben **PROTEUS FITNESS JACKSHIRT**.

Um dieses Segment zu erstellen, müssen Sie ein Ereignis hinzufügen. Klicken Sie auf die Schaltfläche **Veranstaltungen** im **Segmente** Menüleiste.

Als Nächstes sehen Sie die oberste Ebene **XDM ExperienceEvent** Knoten.

So suchen Sie Kunden, die die **PROTEUS FITNESS JACKSHIRT** Produkt, klicken Sie auf **XDM ExperienceEvent**.

![Segmentierung](./images/findee.png)

Scrollen Sie nach unten zu **Produktlistenelemente** und klicken Sie darauf.

![Segmentierung](./images/see.png)

Auswählen **Name** und ziehen Sie die **Name** Objekt von links **Produktlistenelemente** auf der Arbeitsfläche des Segmentaufbaus in der **Veranstaltungen** Abschnitt.

![Segmentierung](./images/eewebpdtlname1.png)

Der Vergleichsparameter sollte **gleich** und geben Sie im Eingabefeld `PROTEUS FITNESS JACKSHIRT`.

![Segmentierung](./images/pv.png)

Ihre **Ereignisregeln** sollte nun so aussehen. Jedes Mal, wenn Sie ein Element zum Segment Builder hinzufügen, können Sie auf die **Schätzung aktualisieren** -Schaltfläche, um eine neue Schätzung der Population in Ihrem Segment zu erhalten.

![Segmentierung](./images/ldap4.png)

Geben wir schließlich Ihrem Segment einen Namen und speichern es.

Verwenden Sie als Namenskonvention:

- `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`

Ihr Segmentname sollte wie folgt aussehen:
`vangeluw - Interest in PROTEUS FITNESS JACKSHIRT`

Klicken Sie anschließend auf das **Speichern und schließen** zum Speichern des Segments.

![Segmentierung](./images/segmentname.png)

Sie werden nun zur Übersichtsseite des Segments zurückgeführt.

![Segmentierung](./images/savedsegment.png)

Nächster Schritt: [6.2 Überprüfen der Konfiguration des DV360-Ziels mithilfe von Zielen](./ex2.md)

[Zurück zu Modul 11](./real-time-cdp-build-a-segment-take-action.md)

[Zu allen Modulen zurückkehren](../../overview.md)
