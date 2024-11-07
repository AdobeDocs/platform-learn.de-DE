---
title: Foundation - Datenerfassung - Von unbekannt zu bekannt auf der Website
description: Foundation - Datenerfassung - Von unbekannt zu bekannt auf der Website
kt: 5342
doc-type: tutorial
source-git-commit: c6ba1f751f18afe39fb6b746a62bc848fa8ec9bf
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 1%

---

# 1.2.1 - Von unbekannt zu bekannt auf der Website

## Kontext

Die Journey von unbekanntem bis bekanntem ist eines der wichtigsten Themen der heutigen Marken, ebenso wie die Journey des Kunden von der Akquise bis zur Aufbewahrung.

Adobe Experience Platform spielt bei diesem Journey eine große Rolle. Plattform ist das Gehirn der Kommunikation, das Erfahrungssystem der Aufzeichnungen.

Plattform ist eine Umgebung, in der das Wort **Kunde** größer ist als nur die **bekannten** Kunden. Dies ist bei der Ansprache mit Marken sehr wichtig: Ein unbekannter Besucher auf der Website ist auch aus Platform-Sicht ein Kunde und daher wird das gesamte Verhalten als unbekannter Besucher auch an Platform gesendet. Durch diesen Ansatz kann eine Marke visualisieren, was vor diesem Zeitpunkt auch passiert ist, wenn dieser Kunde schließlich ein bekannter Kunde wird. Dies hilft aus der Sicht der Attribution und Erlebnisoptimierung.

## Was wirst du tun?

Sie erfassen jetzt Daten in Adobe Experience Platform und diese Daten werden mit Identifikatoren wie ECIDs und E-Mail-Adressen verknüpft. Das Ziel ist es, den geschäftlichen Kontext dessen zu verstehen, was Sie aus der Konfigurationsperspektive tun werden. In der nächsten Übung beginnen Sie mit der Konfiguration von allem, was Sie benötigen, um die gesamte Datenerfassung in Ihrer eigenen Sandbox-Umgebung zu ermöglichen.

### Journey-Fluss des Kunden

Wechseln Sie zu [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf Ihr Website-Projekt, um es zu öffnen.

![DSN](./../../gettingstarted/gettingstarted/images/web8.png)

Klicken Sie auf der Seite **Screens** auf **Ausführen**.

![DSN](../module1.1/images/web2.png)

Sie werden dann Ihre Demowebsite öffnen sehen. Wählen Sie die URL aus und kopieren Sie sie in die Zwischenablage.

![DSN](./../../gettingstarted/gettingstarted/images/web3.png)

Öffnen Sie ein neues Inkognito-Browserfenster.

![DSN](./../../gettingstarted/gettingstarted/images/web4.png)

Fügen Sie die URL Ihrer Demo-Website ein, die Sie im vorherigen Schritt kopiert haben. Sie werden dann aufgefordert, sich mit Ihrer Adobe ID anzumelden.


Wählen Sie Ihren Kontotyp aus und schließen Sie den Anmeldevorgang ab.


Sie sehen dann Ihre Website in einem Inkognito-Browser-Fenster geladen. Für jede Demonstration müssen Sie ein neues Inkognito-Browser-Fenster verwenden, um Ihre Demo-Website-URL zu laden.


Klicken Sie auf das Adobe-Logo-Symbol oben links im Bildschirm, um den Profilanzeige zu öffnen.

![Demo](./images/pv1.png)

Sehen Sie sich das Bedienfeld &quot;Profil-Viewer&quot;und das Echtzeit-Kundenprofil mit der **Experience Cloud-ID** als primäre ID für diesen derzeit unbekannten Kunden an.

![Demo](./images/pv2.png)

Sie können auch alle Erlebnisereignisse sehen, die basierend auf dem Kundenverhalten erfasst wurden. Die Liste ist derzeit leer, aber das wird sich bald ändern.

![Demo](../module1.2/images/pv3.png)

Gehen Sie zur Produktkategorie **Herren** . Klicken Sie anschließend auf das Produkt **Montana Wind Jacket**.

![Demo](../module1.2/images/pv4.png)

Daraufhin wird die Produktdetailseite angezeigt. Ein Erlebnisereignis vom Typ **Produktansicht** wurde jetzt mit der Web SDK-Implementierung an Adobe Experience Platform gesendet, die Sie in Modul 1 überprüft haben.

![Demo](../module1.2/images/pv5.png)

Öffnen Sie das Bedienfeld Viewer bereitstellen und sehen Sie sich Ihre **Erlebnisereignisse** an.

![Demo](../module1.2/images/pv6.png)

Gehen Sie zurück zur Kategorieseite **Frauen** und klicken Sie auf ein anderes Produkt. Ein weiteres Erlebnisereignis wurde an Adobe Experience Platform gesendet.

![Demo](../module1.2/images/pv7.png)

Öffnen Sie das Bedienfeld Profil-Viewer . Es werden nun zwei Erlebnisereignisse des Typs **Produktansicht** angezeigt. Während das Verhalten anonym ist, können wir jeden Klick verfolgen und in Adobe Experience Platform speichern. Sobald der anonyme Kunde bekannt ist, können wir das gesamte anonyme Verhalten automatisch mit dem Bekannten Profil zusammenführen.

![Demo](../module1.2/images/pv8.png)

Gehen Sie zur Seite Registrieren/Anmelden . Klicken Sie auf **KONTO ERSTELLEN**.

![Demo](../module1.2/images/pv9.png)

Füllen Sie Ihre Details aus und klicken Sie auf **Registrieren** . Danach werden Sie zur vorherigen Seite weitergeleitet.

![Demo](../module1.2/images/pv10.png)

Öffnen Sie das Bedienfeld Profil-Viewer und wechseln Sie zum Echtzeit-Kundenprofil. Im Bedienfeld &quot;Profil-Viewer&quot;sollten alle Ihre personenbezogenen Daten angezeigt werden, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](../module1.2/images/pv11.png)

Wechseln Sie im Bereich &quot;Profil-Viewer&quot;zu &quot;Erlebnisereignisse&quot;. Sie sehen die beiden Produkte, die Sie zuvor im Bereich &quot;Profil-Viewer&quot;angezeigt haben. Beide Ereignisse sind jetzt auch mit Ihrem &quot;bekannten&quot;Profil verbunden.

![Demo](../module1.2/images/pv12.png)

Sie haben jetzt Daten in Adobe Experience Platform erfasst und diese Daten mit Identifikatoren wie ECIDs und E-Mail-Adressen verknüpft. Das Ziel ist es, den geschäftlichen Kontext dessen zu verstehen, was Sie tun werden. In der nächsten Übung beginnen Sie mit der Konfiguration von allem, was Sie benötigen, um die gesamte Datenerfassung zu ermöglichen.

Nächster Schritt: [1.2.2 Schemas konfigurieren und Kennungen festlegen](./ex2.md)

[Zurück zu Modul 1.2](./data-ingestion.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
