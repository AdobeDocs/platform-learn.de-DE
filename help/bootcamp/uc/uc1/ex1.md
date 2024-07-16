---
title: Bootcamp - Echtzeit-Kundenprofil - Von unbekannt bis bekannt auf der Website
description: Bootcamp - Echtzeit-Kundenprofil - Von unbekannt bis bekannt auf der Website
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 32a084a3-4c04-4367-947e-f7151fdad73b
source-git-commit: cd59a41f4533f18a54d80298ee9faf3a8ba3c6e7
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 1%

---

# 1.1 Von unbekannt zu bekannt auf der Website

## Kontext

Die Journey von unbekanntem bis bekanntem ist eines der wichtigsten Themen der heutigen Marken, ebenso wie die Journey des Kunden von der Akquise bis zur Aufbewahrung.

Adobe Experience Platform spielt bei diesem Journey eine große Rolle. Plattform ist das Gehirn der Kommunikation, das **Erlebnissystem des Datensatzes**.

Platform ist eine Umgebung, in der das Wort Kunde breiter ist als nur die bekannten Kunden. Ein unbekannter Besucher auf der Website ist auch aus Sicht von Platform ein Kunde. Daher wird das gesamte Verhalten als unbekannter Besucher auch an Platform gesendet. Durch diesen Ansatz kann eine Marke visualisieren, was vor diesem Zeitpunkt auch passiert ist, wenn dieser Besucher schließlich ein bekannter Kunde wird. Dies hilft aus der Sicht der Attribution und Erlebnisoptimierung.

## Journey-Fluss des Kunden

Wechseln Sie zu [https://bootcamp.aepdemo.net](https://publish9122.adobedemo.com/content/aep-bootcamp-experience/language-masters/en.html). Klicken Sie auf **Alle zulassen**.

![DSN](./images/web8.png)

Klicken Sie auf das Adobe-Logo-Symbol oben links im Bildschirm, um den Profilanzeige zu öffnen.

![Demo](./images/pv1.png)

Sehen Sie sich das Bedienfeld &quot;Profil-Viewer&quot;und das Echtzeit-Kundenprofil mit der **Experience Cloud-ID** als primäre Kennung für diesen derzeit unbekannten Kunden an.

![Demo](./images/pv2.png)

Sie können auch alle Erlebnisereignisse sehen, die basierend auf dem Kundenverhalten erfasst wurden. Die Liste ist derzeit leer, aber das wird sich bald ändern.

![Demo](./images/pv3.png)

Wechseln Sie zur Menüoption **Anwendungsdienste** und klicken Sie auf das Produkt **Real-Time CDP**.

![Demo](./images/pv4.png)

Daraufhin wird die Produktdetailseite angezeigt. Ein Erlebnisereignis vom Typ **Produktansicht** wurde jetzt mit der Web SDK-Implementierung an Adobe Experience Platform gesendet, die Sie in Modul 1 überprüft haben. Öffnen Sie das Bedienfeld Profil-Viewer und sehen Sie sich Ihre **Erlebnisereignisse** an.

![Demo](./images/pv5.png)

Wechseln Sie zur Menüoption **Anwendungsdienste** und klicken Sie auf das Produkt **Adobe Journey Optimizer**. Ein weiteres Erlebnisereignis wurde an Adobe Experience Platform gesendet.

![Demo](./images/pv7.png)

Öffnen Sie das Bedienfeld Profil-Viewer . Es werden nun zwei Erlebnisereignisse des Typs **Produktansicht** angezeigt. Während das Verhalten anonym ist, wird jeder Klick verfolgt und in Adobe Experience Platform gespeichert. Sobald der anonyme Kunde bekannt ist, können wir das gesamte anonyme Verhalten automatisch mit dem Bekannten Profil zusammenführen.

![Demo](./images/pv8.png)

Lassen Sie uns nun Ihr Kundenprofil analysieren und dann Ihr Verhalten verwenden, um Ihr Kundenerlebnis auf der Website zu personalisieren.

Nächster Schritt: [1.2 Visualisieren Sie Ihr eigenes Echtzeit-Kundenprofil - UI](./ex2.md)

[Zurück zum Benutzerfluss 1](./uc1.md)

[Zu allen Modulen zurückkehren](../../overview.md)
