---
title: Foundation - Echtzeit-Kundenprofil - Von unbekannt bis bekannt auf der Website
description: Foundation - Echtzeit-Kundenprofil - Von unbekannt bis bekannt auf der Website
kt: 5342
doc-type: tutorial
exl-id: ddbf97c2-8105-42b6-b9bf-209b1df6a3b5
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 2%

---

# 2.1.1 Von unbekannt zu bekannt auf der Website

## Kontext

Die Journey von Unbekannt zu Bekanntem ist heutzutage eines der wichtigsten Markenthemen, ebenso wie die Kunden-Journey von der Akquise bis zur Bindung.

Adobe Experience Platform spielt bei dieser Journey eine große Rolle. Plattform ist das Gehirn für Kommunikation, das „Erlebnissystem der Aufzeichnung“.

Platform ist eine Umgebung, in der das Wort Kunde weiter gefasst ist als nur die bekannten Kunden. Ein unbekannter Besucher auf der Website ist auch aus Sicht von Platform ein Kunde. Daher wird das gesamte Verhalten eines unbekannten Besuchers ebenfalls an Platform gesendet. Dank dieses Ansatzes kann sich eine Marke, wenn dieser Besucher schließlich ein bekannter Kunde wird, auch vor diesem Moment vorstellen, was passiert ist. Dies hilft aus Sicht der Attribution und Erlebnisoptimierung.

## Kunden-Journey-Fluss

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

Klicken Sie auf das Adobe-Logo oben links im Bildschirm, um den Profil-Viewer zu öffnen.

![Demo](../../datacollection/module1.2/images/pv1.png)

Sehen Sie sich das Bedienfeld Profil-Viewer und das Echtzeit-Kundenprofil mit der **Experience Cloud-ID** als primäre Kennung für diesen derzeit unbekannten Kunden an.

![Demo](../../datacollection/module1.2/images/pv2.png)

Sie können auch alle Erlebnisereignisse sehen, die basierend auf dem Verhalten des Kunden erfasst wurden. Die Liste ist derzeit leer, aber das wird sich bald ändern.

![Demo](../../datacollection/module1.2/images/pv3.png)

Navigieren Sie zur Produktkategorie **Telefone und Geräte** . Klicken Sie anschließend auf das Produkt **iPhone 15 Pro**.

![Demo](../../datacollection/module1.2/images/pv4.png)

Anschließend wird die Produktdetailseite angezeigt. Ein Erlebnisereignis vom Typ **Produktansicht** wurde jetzt mithilfe der Web-SDK-Implementierung, die Sie in Modul 1 überprüft haben, an Adobe Experience Platform gesendet.

![Demo](../../datacollection/module1.2/images/pv5.png)

Öffnen Sie das Bedienfeld Profil-Viewer und sehen Sie sich Ihre **Erlebnisereignisse“**.

![Demo](../../datacollection/module1.2/images/pv6.png)

Gehen Sie zurück zur Kategorieseite **Telefone und Geräte** und klicken Sie auf ein anderes Produkt. Ein weiteres Erlebnisereignis wurde an Adobe Experience Platform gesendet. Öffnen Sie das Bedienfeld Profil-Viewer . Es werden jetzt zwei Erlebnisereignisse vom Typ **Produktansicht** angezeigt. Während das Verhalten anonym ist, können Sie bei ordnungsgemäßem Einverständnis jeden Klick verfolgen und in Adobe Experience Platform speichern. Sobald der anonyme Kunde bekannt wird, können wir das gesamte anonyme Verhalten automatisch mit dem bekannten Profil zusammenführen.

![Demo](../../datacollection/module1.2/images/pv7.png)

Navigieren Sie zur Anmelde-/Anmeldeseite. Klicken Sie auf **Anmelden**.

![Demo](../../datacollection/module1.2/images/pv8.png)

Klicken Sie **Konto erstellen**.

![Demo](../../datacollection/module1.2/images/pv9.png)

Füllen Sie Ihre Daten aus und klicken Sie **Registrieren**, woraufhin Sie zur vorherigen Seite weitergeleitet werden.

![Demo](../../datacollection/module1.2/images/pv10.png)

Öffnen Sie das Bedienfeld Profil-Viewer und navigieren Sie zum Echtzeit-Kundenprofil. Im Profil-Viewer-Fenster sollten Sie alle Ihre personenbezogenen Daten angezeigt bekommen, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](../../datacollection/module1.2/images/pv11.png)

Wechseln Sie im Bedienfeld Profil-Viewer zu Erlebnisereignisse . Die beiden Produkte, die Sie zuvor angezeigt haben, werden im Bedienfeld Profil-Viewer angezeigt. Beide Ereignisse sind jetzt auch mit Ihrem „bekannten“ Profil verbunden.

![Demo](../../datacollection/module1.2/images/pv12.png)

Sie haben jetzt Daten in Adobe Experience Platform aufgenommen und diese Daten mit Kennungen wie ECIDs und E-Mail-Adressen verknüpft. Das Ziel ist, den Geschäftskontext von dem zu verstehen, was Sie tun werden. In der nächsten Übung beginnen Sie mit der Konfiguration aller erforderlichen Elemente, um die gesamte Datenaufnahme zu ermöglichen.

### Navigieren in der Mobile App

Nachdem Sie ein bekannter Kunde geworden sind, ist es an der Zeit, die Mobile App zu verwenden. Öffnen Sie die Mobile App auf Ihrem iPhone und melden Sie sich bei der App an.

Wenn Sie die App nicht mehr installiert haben oder Sie sich nicht mehr an die Installation erinnern können, schauen Sie bitte hier: [Verwenden Sie die Mobile App](../../gettingstarted/gettingstarted/ex5.md)

Nachdem Sie die App wie angewiesen installiert haben, sehen Sie die Landingpage der App, auf der die Marke Citi Signal geladen ist. Klicken Sie auf das Konto -Symbol oben links im Bildschirm.

![Demo](./images/app_hp1.png)

Melden Sie sich auf dem Anmeldebildschirm mit der auf der Desktop-Website verwendeten E-Mail-Adresse an. Klicken Sie **Anmelden**.

![Demo](./images/app_acc.png)

Gehen Sie zum Startbildschirm der App und klicken Sie darauf, um ein beliebiges Produkt zu öffnen.

![Demo](./images/app_hp.png)

Anschließend wird die Produktdetailseite angezeigt.

![Demo](./images/app_galaxy.png)

Wechseln Sie zum Startbildschirm in der App und wischen Sie auf dem Bildschirm nach links, um das Bedienfeld Profil-Viewer anzuzeigen. Anschließend sehen Sie das soeben angezeigte Produkt im Abschnitt **Erlebnisereignisse** zusammen mit allen Produktansichten, die in der vorherigen Website-Sitzung generiert wurden.

>[!NOTE]
>
>Es kann einige Minuten dauern, bis Sie die konsolidierte Ansicht in der App und auf der Website sehen.

![Demo](./images/app_after_galaxy.png)

Gehen Sie nun zurück zu Ihrem Desktop-Computer und aktualisieren Sie die Homepage. Danach wird das Produkt auch dort angezeigt.

>[!NOTE]
>
>Es kann einige Minuten dauern, bis Sie die konsolidierte Ansicht in der App und auf der Website sehen.

![Demo](./images/web_x_aftermobile.png)

Sie haben jetzt Daten in Adobe Experience Platform aufgenommen und diese Daten mit Kennungen wie ECIDs und E-Mail-Adressen verknüpft. Das Ziel dieser Übung war es, den Geschäftskontext von dem zu verstehen, was Sie tun werden. Sie haben jetzt effektiv ein geräteübergreifendes Echtzeit-Kundenprofil erstellt. In der nächsten Übung visualisieren Sie Ihr Profil in Adobe Experience Platform.

Nächster Schritt: [2.1.2 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - Benutzeroberfläche](./ex2.md)

[Zurück zum Modul 2.1](./real-time-customer-profile.md)

[Zurück zu „Alle Module“](../../../overview.md)
