---
title: Segmentaktivierung für Microsoft Azure Event Hub - Aktion
description: Segmentaktivierung für Microsoft Azure Event Hub - Aktion
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---

# 2.4.6 End-to-End-Szenario

## 2.4.6.1 Azure Event Hub-Trigger starten

Um die Payload anzuzeigen, die von der Echtzeit-Kundendatenplattform von Adobe Experience Platform bei Segmentqualifizierung an unseren Azure Event Hub gesendet wird, müssen wir unsere einfache Azure Event Hub-Trigger-Funktion starten. Diese Funktion vereinfacht die Nutzlast in der Konsole in Visual Studio Code. Beachten Sie jedoch, dass diese Funktion auf jede Weise erweitert werden kann, um mit allen möglichen Umgebungen mit dedizierten APIs und Protokollen zu arbeiten.

### Visual Studio-Code starten und Projekt starten

Stellen Sie sicher, dass Ihr Visual Studio Code-Projekt geöffnet und ausgeführt wird.

Informationen zum Starten/Stoppen/Neustart Ihrer Azure-Funktion in Visual Studio Code finden Sie in den folgenden Übungen:

- [Übung 13.5.4 - Azure-Projekt starten](./ex5.md)
- [Übung 13.5.5 - Azure-Projekt beenden](./ex5.md)

Das **Terminal** Ihres Visual Studio-Codes sollte in etwa so aussehen:

```code
[2022-02-23T05:03:41.429Z] Worker process started and initialized.
[2022-02-23T05:03:41.484Z] Debugger attached.
[2022-02-23T05:03:46.401Z] Host lock lease acquired by instance ID '000000000000000000000000D90C881B'.
```

![6-01-vsc-ready.png](./images/vsc31.png)

## 2.4.6.2 Luma-Website laden

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

## 2.4.6.3 Für Ihr Interesse am Segment Ausrüstung qualifizieren

Navigieren Sie einmal zur Seite **Ausrüstung** und **laden Sie sie nicht neu oder aktualisieren Sie sie nicht**. Diese Aktion sollte Sie für Ihr `--aepUserLdap-- - Interest in Equipment` -Segment qualifizieren.

![6-04-luma-telco-nav-sports.png](./images/luma1.png)

Öffnen Sie dazu das Bedienfeld Profil-Viewer . Sie sollten jetzt Mitglied der `--aepUserLdap-- - Interest in Equipment` sein. Wenn Ihre Segmentmitgliedschaften noch nicht in Ihrem Profil-Viewer-Bedienfeld aktualisiert wurden, klicken Sie auf die Schaltfläche &quot;Neu laden&quot;.

![6-05-luma-telco-nav-broad.png](./images/luma2.png)

Wechseln Sie zurück zu Visual Studio Code und sehen Sie sich die Registerkarte **TERMINAL** an. Sie sollten eine Liste der Segmente für Ihre spezifische **ECID** sehen. Diese Aktivierungs-Payload wird an Ihren Ereignis-Hub bereitgestellt, sobald Sie sich für das `--aepUserLdap-- - Interest in Equipment` -Segment qualifizieren.

Wenn Sie sich die Segment-Payload genauer ansehen, können Sie sehen, dass `--aepUserLdap-- - Interest in Equipment` den Status **realisiert** aufweist.

Der Segmentstatus **realisiert** bedeutet, dass unser Profil gerade in das Segment eingetreten ist. Der Status **vorhandene** bedeutet, dass sich unser Profil weiterhin im Segment befindet.

![6-06-vsc-activation-alized.png](./images/luma3.png)

## 2.4.6.4 Zum zweiten Mal die Seite &quot;Ausrüstung&quot;besuchen

Führen Sie eine feste Aktualisierung der Seite **Ausrüstung** durch.

![6-07-back-to-sports.png](./images/luma1.png)

Wechseln Sie jetzt zurück zu Visual Studio Code und überprüfen Sie Ihre Registerkarte **TERMINAL**. Sie werden sehen, dass Ihr Segment noch vorhanden ist, aber jetzt den Status **existiert** aufweist, was bedeutet, dass unser Profil weiterhin im Segment enthalten ist.

![6-08-vsc-activation-existing.png](./images/luma4.png)

## 2.4.6.5 Zum dritten Mal die Seite &quot;Sport&quot;besuchen

Wenn Sie die Seite **Sport** zum dritten Mal erneut aufrufen, findet keine Aktivierung statt, da keine Statusänderung aus Segmentsicht erfolgt.

Segmentaktivierungen treten nur dann auf, wenn sich der Status des Segments ändert:

![6-09-segment-state-change.png](./images/6-09-segment-state-change.png)

Nächster Schritt: [Zusammenfassung und Vorteile](./summary.md)

[Zurück zu Modul 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Zu allen Modulen zurückkehren](./../../../overview.md)
