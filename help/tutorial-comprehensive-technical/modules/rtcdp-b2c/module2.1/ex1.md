---
title: Foundation - Echtzeit-Kundenprofil - Von unbekannt zu bekannt auf der Website
description: Foundation - Echtzeit-Kundenprofil - Von unbekannt zu bekannt auf der Website
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 2%

---

# 2.1.1 Von unbekannt zu bekannt auf der Website

## Kontext

Die Journey von unbekanntem bis bekanntem ist eines der wichtigsten Themen der heutigen Marken, ebenso wie die Journey des Kunden von der Akquise bis zur Aufbewahrung.

Adobe Experience Platform spielt bei diesem Journey eine große Rolle. Plattform ist das Gehirn für Kommunikation, das &quot;Erlebnissystem der Aufzeichnungen&quot;.

Platform ist eine Umgebung, in der das Wort Kunde breiter ist als nur die bekannten Kunden. Ein unbekannter Besucher auf der Website ist auch aus Sicht von Platform ein Kunde. Daher wird das gesamte Verhalten als unbekannter Besucher auch an Platform gesendet. Durch diesen Ansatz kann eine Marke visualisieren, was vor diesem Zeitpunkt auch passiert ist, wenn dieser Besucher schließlich ein bekannter Kunde wird. Dies hilft aus der Sicht der Attribution und Erlebnisoptimierung.

## Journey-Fluss des Kunden

Wechseln Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](../../gettingstarted/gettingstarted/images/web8.png)

Klicken Sie auf der Seite **Screens** auf **Ausführen**.

![DSN](../../gettingstarted/gettingstarted/images/web2.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.

![DSN](../../gettingstarted/gettingstarted/images/web5.png)

Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.

![DSN](../../gettingstarted/gettingstarted/images/web6.png)

Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.

![DSN](../../gettingstarted/gettingstarted/images/web7.png)

Klicken Sie auf das Adobe-Logo-Symbol oben links im Bildschirm, um den Profilanzeige zu öffnen.

![Demo](../../datacollection/module1.2/images/pv1.png)

Sehen Sie sich das Bedienfeld &quot;Profil-Viewer&quot;und das Echtzeit-Kundenprofil mit der **Experience Cloud-ID** als primäre ID für diesen derzeit unbekannten Kunden an.

![Demo](../../datacollection/module1.2/images/pv2.png)

Sie können auch alle Erlebnisereignisse sehen, die basierend auf dem Kundenverhalten erfasst wurden. Die Liste ist derzeit leer, aber das wird sich bald ändern.

![Demo](../../datacollection/module1.2/images/pv3.png)

Gehen Sie zur Produktkategorie **Herren** . Klicken Sie anschließend auf das Produkt **Montana Wind Jacket**.

![Demo](../../datacollection/module1.2/images/pv4.png)

Daraufhin wird die Produktdetailseite angezeigt. Ein Erlebnisereignis vom Typ **Produktansicht** wurde jetzt mit der Web SDK-Implementierung an Adobe Experience Platform gesendet, die Sie in Modul 1 überprüft haben.

![Demo](../../datacollection/module1.2/images/pv5.png)

Öffnen Sie das Bedienfeld Viewer bereitstellen und sehen Sie sich Ihre **Erlebnisereignisse** an.

![Demo](../../datacollection/module1.2/images/pv6.png)

Gehen Sie zurück zur Kategorieseite **Frauen** und klicken Sie auf ein anderes Produkt. Ein weiteres Erlebnisereignis wurde an Adobe Experience Platform gesendet.

![Demo](../../datacollection/module1.2/images/pv7.png)

Öffnen Sie das Bedienfeld Profil-Viewer . Es werden nun zwei Erlebnisereignisse des Typs **Produktansicht** angezeigt. Während das Verhalten anonym ist, können wir jeden Klick verfolgen und in Adobe Experience Platform speichern. Sobald der anonyme Kunde bekannt ist, können wir das gesamte anonyme Verhalten automatisch mit dem Bekannten Profil zusammenführen.

![Demo](../../datacollection/module1.2/images/pv8.png)

Gehen Sie zur Seite Registrieren/Anmelden . Klicken Sie auf **KONTO ERSTELLEN**.

![Demo](../../datacollection/module1.2/images/pv9.png)

Füllen Sie Ihre Details aus und klicken Sie auf **Registrieren** . Danach werden Sie zur vorherigen Seite weitergeleitet.

![Demo](../../datacollection/module1.2/images/pv10.png)

Öffnen Sie das Bedienfeld Profil-Viewer und wechseln Sie zum Echtzeit-Kundenprofil. Im Bedienfeld &quot;Profil-Viewer&quot;sollten alle Ihre personenbezogenen Daten angezeigt werden, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](../../datacollection/module1.2/images/pv11.png)

Wechseln Sie im Bereich &quot;Profil-Viewer&quot;zu &quot;Erlebnisereignisse&quot;. Sie sehen die beiden Produkte, die Sie zuvor im Bereich &quot;Profil-Viewer&quot;angezeigt haben. Beide Ereignisse sind jetzt auch mit Ihrem &quot;bekannten&quot;Profil verbunden.

![Demo](../../datacollection/module1.2/images/pv12.png)

Sie haben jetzt Daten in Adobe Experience Platform erfasst und diese Daten mit Identifikatoren wie ECIDs und E-Mail-Adressen verknüpft. Das Ziel ist es, den geschäftlichen Kontext dessen zu verstehen, was Sie tun werden. In der nächsten Übung beginnen Sie mit der Konfiguration von allem, was Sie benötigen, um die gesamte Datenerfassung zu ermöglichen.

### Navigieren zur mobilen App

Nachdem Sie ein bekannter Kunde geworden sind, ist es an der Zeit, mit der Verwendung der App zu beginnen. Öffnen Sie die App in Ihrer iPhone und melden Sie sich dann bei der App an.

Wenn Sie die App nicht mehr installiert haben oder sich nicht mehr daran erinnern können, wie Sie sie installieren, finden Sie hier: [0.5 Verwenden Sie die mobile App](../../gettingstarted/gettingstarted/ex5.md)

Nachdem Sie die App wie angewiesen installiert haben, sehen Sie die Landingpage der App mit der geladenen Marke Luma. Klicken Sie auf das Kontosymbol im oberen linken Bereich des Bildschirms.

![Demo](./images/app_hp.png)

Melden Sie sich im Anmeldebildschirm mit der E-Mail-Adresse an, die Sie auf der Desktop-Website verwendet haben. Klicken Sie auf **Anmelden**.

![Demo](./images/app_acc.png)

Rufen Sie den Startbildschirm der App auf und klicken Sie auf , um ein beliebiges Produkt zu öffnen.

![Demo](./images/app_hp.png)

Daraufhin wird die Produktdetailseite angezeigt.

![Demo](./images/app_carst.png)

Wechseln Sie in der App zum Startbildschirm und wischen Sie auf dem Bildschirm nach links, um das Bedienfeld Profil-Viewer anzuzeigen. Anschließend werden das soeben angezeigte Produkt im Abschnitt **Erlebnisereignisse** sowie alle Produktansichten aus der Website-Sitzung angezeigt.

![Demo](./images/app_after_carst.png)

Kehren Sie nun zu Ihrem Desktop-Computer zurück und aktualisieren Sie die Startseite, nach der das Produkt auch dort angezeigt wird.

![Demo](./images/lb_x_aftermobile.png)

Sie haben jetzt Daten in Adobe Experience Platform erfasst und diese Daten mit Identifikatoren wie ECIDs und E-Mail-Adressen verknüpft. Ziel dieser Übung war es, den geschäftlichen Kontext dessen zu verstehen, was Sie tun werden. Sie haben jetzt effektiv ein echtzeitübergreifendes Kundenprofil erstellt. In der nächsten Übung werden Sie Ihr Profil in Adobe Experience Platform visualisieren.

Nächster Schritt: [2.1.2 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - UI](./ex2.md)

[Zurück zu Modul 2.1](./real-time-customer-profile.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
