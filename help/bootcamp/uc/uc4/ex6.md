---
title: Bootcamp - Customer Journey Analytics - Vom Einblick zum Handeln
description: Bootcamp - Customer Journey Analytics - Vom Einblick zum Handeln
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Audiences
exl-id: 7a38a0a4-46e4-41f2-9a75-316dfde7128f
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# 4.6 Vom Einblick zum Handeln

## Ziele

- Verstehen, wie eine Zielgruppe basierend auf einer in Customer Journey Analytics erfassten Ansicht erstellt wird
- Diese Zielgruppe in Real-Time CDP und Adobe Journey Optimizer verwenden

## 4.6.1 Erstellen einer Zielgruppe und Veröffentlichen

In Ihrem Projekt haben Sie einen Filter mit dem Namen **Anrufgefühle** erstellt und konnten die Anzahl der Benutzer anzeigen, deren Anrufe beim Callcenter als **positiv** klassifiziert wurden. Jetzt können Sie mit diesen Benutzern ein Segment erstellen und es in Journey oder Kommunikationskanälen aktivieren.

Der erste Schritt ist: Wählen Sie im in der letzten Übung erstellten Bedienfeld Zeile **1 aus. Kontaktaufnahme - Positiv** Klicken Sie mit der rechten Maustaste und wählen Sie die Option **Zielgruppe aus Auswahl erstellen**:

![demo](./images/aud1.png)

Geben Sie als Nächstes Ihrer Zielgruppe einen Namen, der dem Modell folgt **IhrNachname - CJA-Zielgruppenaufruf fühlt sich positiv an**:

![demo](./images/aud2.png)

Beachten Sie, dass es möglich ist, eine Vorschau der erstellten Audience zu erhalten:

![demo](./images/aud3.png)

Klicken Sie abschließend auf **Publish**.

![demo](./images/aud4.png)

## 4.6.2 Verwenden Sie Ihre Zielgruppe als Teil eines Segments

Navigieren Sie zurück zur Adobe Experience Platform und gehen Sie zu **Segmente > Durchsuchen**. Dort sehen Sie, wie Ihr in CJA erstelltes Segment für Ihre Aktivierungen und Journey verwendet werden kann.

![demo](./images/aud5.png)

Verwenden wir dieses Segment jetzt in einer Facebook-Aktivierung und in einer Kunden-Journey!

## 4.6.3 Segment in Real-Time CDP in Echtzeit verwenden

Navigieren Sie in Adobe Experience Platform zu **Segmente > Durchsuchen** und suchen Sie die Zielgruppe, die Sie in CJA erstellt haben:

![demo](./images/aud6.png)

Klicken Sie auf Ihr Segment und dann auf **Für Ziel aktivieren**:

![demo](./images/aud7.png)

Wählen Sie das Ziel **bootcamp-facebook** aus und klicken Sie dann auf **Weiter**.

![demo](./images/aud8.png)

Klicken Sie **erneut** Weiter“.

![demo](./images/aud9.png)

Wählen Sie die **Herkunft Ihrer Zielgruppe** und setzen Sie sie auf **Direkt von Kunden** klicken Sie auf **Weiter**.

![demo](./images/aud10.png)

Klicken Sie auf **Fertigstellen**.

![demo](./images/aud11.png)

Ihr Segment ist jetzt mit den benutzerdefinierten Zielgruppen von Facebook verbunden. Verwenden wir nun dasselbe Segment in Adobe Journey Optimizer.

## 4.6.4 Segment in Adobe Journey Optimizer verwenden

Klicken Sie in Adobe Experience Platform auf **Journey Optimizer** und dann im Menü links auf **Journey** und beginnen Sie mit der Erstellung einer Journey durch Klicken auf **Journey erstellen**.

![demo](./images/aud20.png)

![demo](./images/aud21.png)

![demo](./images/aud22.png)

Wählen Sie dann im linken Menü unter **Ereignisse** die Option **Segmentqualifikation** und ziehen Sie sie auf die Journey:

![demo](./images/aud23.png)

Klicken Sie unter Segment auf **Bearbeiten**, um ein Segment auszuwählen:

![demo](./images/aud24.png)

Wählen Sie die zuvor in CJA erstellte Zielgruppe aus und klicken Sie auf **Speichern**.

![demo](./images/aud25.png)

Bereit! Von hier aus können Sie eine Journey für Kunden erstellen, die sich für dieses Segment qualifizieren.

[Zurück zu Benutzerfluss 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)
