---
title: Foundation - Datenerfassung - Von unbekannt zu bekannt auf der Website
description: Foundation - Datenerfassung - Von unbekannt zu bekannt auf der Website
kt: 5342
doc-type: tutorial
exl-id: 08cb7892-4e1c-4646-9e3b-8ab008dfd947
source-git-commit: 3a19e88e820c63294eff38bb8f699a9f690afcb9
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 1%

---

# 1.2.1 Von unbekannt zu bekannt auf der Website

## Kontext

Die Journey von unbekanntem bis bekanntem ist eines der wichtigsten Themen der heutigen Marken, ebenso wie die Journey des Kunden von der Akquise bis zur Aufbewahrung.

Adobe Experience Platform spielt bei diesem Journey eine große Rolle. Plattform ist das Gehirn der Kommunikation, das Erfahrungssystem der Aufzeichnungen.

Plattform ist eine Umgebung, in der das Wort **Kunde** größer ist als nur die **bekannten** Kunden. Dies ist bei der Ansprache mit Marken sehr wichtig: Ein unbekannter Besucher auf der Website ist auch aus Platform-Sicht ein Kunde und daher wird das gesamte Verhalten als unbekannter Besucher auch an Platform gesendet. Durch diesen Ansatz kann eine Marke visualisieren, was vor diesem Zeitpunkt auch passiert ist, wenn dieser Kunde schließlich ein bekannter Kunde wird. Dies hilft aus der Sicht der Attribution und Erlebnisoptimierung.

## Was wirst du tun?

Sie erfassen jetzt Daten in Adobe Experience Platform und diese Daten werden mit Identifikatoren wie ECIDs und E-Mail-Adressen verknüpft. Das Ziel ist es, den geschäftlichen Kontext dessen zu verstehen, was Sie aus der Konfigurationsperspektive tun werden. In der nächsten Übung beginnen Sie mit der Konfiguration von allem, was Sie benötigen, um die gesamte Datenerfassung in Ihrer eigenen Sandbox-Umgebung zu ermöglichen.

### Journey-Fluss des Kunden

Wechseln Sie zu [https://dsn.adobe.com](https://dsn.adobe.com). Nach der Anmeldung bei Ihrer Adobe ID sehen Sie dies. Klicken Sie auf die drei Punkte **..** im Website-Projekt und dann auf **Ausführen** , um es zu öffnen.

![DSN](./../../datacollection/module1.1/images/web8.png)

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

![Demo](./images/pv3.png)

Gehen Sie zur Produktkategorie **Telefon und Geräte** . Klicken Sie anschließend auf das Produkt **iPhone 15 Pro**.

![Demo](./images/pv4.png)

Daraufhin wird die Produktdetailseite angezeigt. Mit der Web SDK-Implementierung, die Sie im vorherigen Modul überprüft haben, wurde jetzt ein Erlebnisereignis des Typs **Produktansicht** an Adobe Experience Platform gesendet.

![Demo](./images/pv5.png)

Öffnen Sie das Bedienfeld Viewer bereitstellen und sehen Sie sich Ihre **Erlebnisereignisse** an.

![Demo](./images/pv6.png)

Kehren Sie zur Kategorieseite **Telefon &amp; Geräte** zurück und klicken Sie auf ein anderes Produkt. Ein weiteres Erlebnisereignis wurde an Adobe Experience Platform gesendet.

Öffnen Sie das Bedienfeld Profil-Viewer . Es werden nun zwei Erlebnisereignisse des Typs **Produktansicht** angezeigt. Während das Verhalten anonym ist, können wir jeden Klick verfolgen und in Adobe Experience Platform speichern. Sobald der anonyme Kunde bekannt ist, können wir das gesamte anonyme Verhalten automatisch mit dem Bekannten Profil zusammenführen.

![Demo](./images/pv7.png)

Klicken Sie auf **Anmelden** , um zur Seite &quot;Registrieren/Anmelden&quot;zu gelangen.

![Demo](./images/pv8.png)

Klicken Sie auf **Konto erstellen**.

![Demo](./images/pv9.png)

Füllen Sie Ihre Details aus und klicken Sie auf **Registrieren** . Danach werden Sie zur vorherigen Seite weitergeleitet.

![Demo](./images/pv10.png)

Öffnen Sie das Bedienfeld Profil-Viewer und wechseln Sie zum Echtzeit-Kundenprofil. Im Bedienfeld &quot;Profil-Viewer&quot;sollten alle Ihre personenbezogenen Daten angezeigt werden, z. B. Ihre neu hinzugefügten E-Mail- und Telefonkennungen.

![Demo](./images/pv11.png)

Wechseln Sie im Bereich &quot;Profil-Viewer&quot;zu &quot;Erlebnisereignisse&quot;. Sie sehen die beiden Produkte, die Sie zuvor im Bereich &quot;Profil-Viewer&quot;angezeigt haben. Beide Ereignisse sind jetzt auch mit Ihrem &quot;bekannten&quot;Profil verbunden.

![Demo](./images/pv12.png)

Sie haben jetzt Daten in Adobe Experience Platform erfasst und diese Daten mit Identifikatoren wie ECIDs und E-Mail-Adressen verknüpft. Das Ziel ist es, den geschäftlichen Kontext dessen zu verstehen, was Sie tun werden. In der nächsten Übung beginnen Sie mit der Konfiguration von allem, was Sie benötigen, um die gesamte Datenerfassung zu ermöglichen.

Nächster Schritt: [1.2.2 Schemas konfigurieren und Kennungen festlegen](./ex2.md)

[Zurück zu Modul 1.2](./data-ingestion.md)

[Zu allen Modulen zurückkehren](../../../overview.md)
