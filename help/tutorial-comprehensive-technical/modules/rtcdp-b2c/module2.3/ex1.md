---
title: Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen - Zielgruppe aufbauen
description: Real-Time CDP - Zielgruppe aufbauen und Maßnahmen ergreifen - Zielgruppe aufbauen
kt: 5342
doc-type: tutorial
exl-id: a46b1640-769d-4fb3-97e6-beaf9706efbf
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 3%

---

# 2.3.1 Erstellen einer Zielgruppe

In dieser Übung erstellen Sie eine Zielgruppe, indem Sie den Audience Builder von Adobe Experience Platform verwenden.

## Kontext

Auf Kundeninteressen muss in Echtzeit reagiert werden. Eine der Möglichkeiten, auf Kundenverhalten in Echtzeit zu reagieren, besteht darin, eine Zielgruppe zu verwenden - unter der Bedingung, dass die Zielgruppe in Echtzeit qualifiziert ist. In dieser Übung müssen Sie eine Zielgruppe aufbauen und die reale Aktivität auf der von uns verwendeten Website berücksichtigen.

## Identifizieren Sie das Verhalten, auf das Sie reagieren möchten

Navigieren Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nachdem Sie sich mit Ihrer Adobe ID angemeldet haben, sehen Sie Folgendes. Klicken Sie auf die 3 Punkte **…** in Ihrem Website-Projekt und dann auf **Ausführen**, um es zu öffnen.

![DSN](./../../datacollection/module1.1/images/web8.png)

Anschließend wird Ihre Demo-Website geöffnet. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browser-Fenster.

![DSN](../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../gettingstarted/gettingstarted/images/web6.png)

Ihre Website wird dann in einem Inkognito-Browser-Fenster geladen. Für jede Übung müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../gettingstarted/gettingstarted/images/web7.png)

In diesem Beispiel möchten Sie einer bestimmten Kundin oder einem bestimmten Kunden antworten, die bzw. der sich ein bestimmtes Produkt ansieht.
Gehen Sie auf der **Citi Signal**-Homepage zu **Telefone &amp; Geräte** und klicken Sie auf das Produkt **Galaxy S24**.

![Datenaufnahme](./images/homegalaxy.png)

Wenn also jemand die Produktseite für **Galaxy S24** besucht, möchten Sie in der Lage sein, Maßnahmen zu ergreifen. Um aktiv zu werden, müssen Sie zunächst eine Audience definieren.

![Datenaufnahme](./images/homegalaxy1.png)

## Erstellen der Zielgruppe

Zu [Adobe Experience Platform](https://experience.adobe.com/platform). Nach dem Login landen Sie auf der Homepage von Adobe Experience Platform.

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/home.png)

Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepSandboxName--``. Nach Auswahl der entsprechenden [!UICONTROL Sandbox] wird der Bildschirm geändert und Sie befinden sich nun in Ihrer dedizierten [!UICONTROL Sandbox].

![Datenaufnahme](./../../../modules/datacollection/module1.2/images/sb1.png)

Gehen Sie im Menü auf der linken Seite zu **Zielgruppen** und dann zu **Durchsuchen**, wo Sie einen Überblick über alle bestehenden Zielgruppen erhalten. Klicken Sie auf die **Zielgruppe erstellen**, um mit der Erstellung einer neuen Zielgruppe zu beginnen.

![Segmentierung](./images/menuseg.png)

Wählen Sie **Regel erstellen** und klicken Sie auf **Erstellen**.

![Segmentierung](./images/menuseg1.png)

Wie bereits erwähnt, müssen Sie eine Zielgruppe aus allen Kunden erstellen, die das Produkt (Galaxy **24) angesehen**.

Um diese Zielgruppe zu erstellen, müssen Sie ein Ereignis hinzufügen. Sie können alle Ereignisse finden, indem Sie auf das Symbol **Ereignisse** in der Menüleiste **Zielgruppen** klicken.

Als Nächstes sehen Sie den Knoten **XDM ExperienceEvent** der obersten Ebene.

Um Kunden zu finden, die das Produkt **Galaxy S24** besucht haben, klicken Sie auf **XDM ExperienceEvent**.

![Segmentierung](./images/findee.png)

Scrollen Sie nach unten **„Produktlistenelemente** und klicken Sie darauf.

![Segmentierung](./images/see.png)

Wählen Sie **Name** aus und ziehen Sie das **Name**-Objekt aus dem linken **Produktlistenelemente**-Menü auf die Arbeitsfläche des Audience Builders in den Abschnitt **Ereignisse**.

![Segmentierung](./images/eewebpdtlname1.png)

Der Vergleichsparameter sollte **gleich** lauten und im Eingabefeld `Galaxy S24` eingeben.

![Segmentierung](./images/pv.png)

Ihre **Ereignisregeln** sollten jetzt wie folgt aussehen. Jedes Mal, wenn Sie ein Element zum Audience Builder hinzufügen, können Sie auf die Schaltfläche **Schätzung aktualisieren** klicken, um eine neue Schätzung der Population in Ihrer Audience zu erhalten.

![Segmentierung](./images/ldap4.png)

Geben Sie Ihrer Zielgruppe einen Namen und setzen Sie **Auswertungsmethode** auf **Edge**.

Verwenden Sie als Namenskonvention:

- `--aepUserLdap-- - Interest in Galaxy S24`

Klicken Sie anschließend auf die Schaltfläche **Publish**, um Ihre Audience zu speichern.

![Segmentierung](./images/segmentname.png)

Sie gelangen nun zurück zur Seite mit der Zielgruppenübersicht.

![Segmentierung](./images/savedsegment.png)

Nächster Schritt: [2.3.2 Überprüfen Sie, wie Sie das DV360-Ziel mithilfe von Zielen konfigurieren](./ex2.md)

[Zurück zum Modul 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Zurück zu „Alle Module“](../../../overview.md)
