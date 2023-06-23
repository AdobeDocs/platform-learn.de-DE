---
title: Bootcamp - Customer Journey Analytics - Von Einblicken zu Aktionen
description: Bootcamp - Customer Journey Analytics - Von Einblicken zu Aktionen
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 7a38a0a4-46e4-41f2-9a75-316dfde7128f
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 4.6 Von Einblicken zu Aktionen

## Ziele

- Erfahren Sie, wie Sie eine Zielgruppe basierend auf einer in Customer Journey Analytics erfassten Ansicht erstellen
- Verwenden dieser Zielgruppe in Real-Time CDP und Adobe Journey Optimizer

## 4.6.1 Erstellen und Veröffentlichen einer Audience

In Ihrem Projekt haben Sie einen Filter mit dem Namen **Aufruffunktionen** und konnten die Anzahl der Benutzer anzeigen, deren Anrufe an das Callcenter als **positive**. Sie können jetzt ein Segment mit diesen Benutzern erstellen und in Journey- oder Kommunikationskanälen aktivieren.

Der erste Schritt ist: Wählen Sie im Bedienfeld, das Sie in der letzten Übung erstellt haben, eine Zeile aus **1. Rufempfindlichkeit - positiv**, klicken Sie mit der rechten Maustaste und wählen Sie die **Erstellen einer Zielgruppe aus Auswahl** Option:

![Demo](./images/aud1.png)

Benennen Sie dann Ihre Audience entsprechend dem Modell. **yourLastName - CJA-Audience-Aufruf &quot;Empfohlen&quot;**:

![Demo](./images/aud2.png)

Beachten Sie, dass eine Vorschau der zu erstellenden Audience möglich ist:

![Demo](./images/aud3.png)

Klicken Sie abschließend auf **Veröffentlichen**.

![Demo](./images/aud4.png)

## 4.6.2 Zielgruppe als Teil eines Segments verwenden

Gehen Sie zurück zur Adobe Experience Platform, gehen Sie zu **Segmente > Durchsuchen** und Sie können sehen, dass Ihr Segment in CJA erstellt wurde und für Ihre Aktivierungen und Journey verwendet werden kann!

![Demo](./images/aud5.png)

Verwenden wir dieses Segment jetzt in einer Facebook-Aktivierung und in einer Journey!

## 4.6.3 Verwenden Sie Ihr Segment in Real-Time CDP in Echtzeit

Navigieren Sie in Adobe Experience Platform zu **Segmente > Durchsuchen** und suchen Sie die Zielgruppe, die Sie in CJA erstellt haben:

![Demo](./images/aud6.png)

Klicken Sie auf Ihr Segment und dann auf **Für Ziel aktivieren**:

![Demo](./images/aud7.png)

Wählen Sie das Ziel mit dem Namen **bootcamp-facebook** und klicken Sie anschließend auf **Nächste**.

![Demo](./images/aud8.png)

Klicken **Nächste** erneut.

![Demo](./images/aud9.png)

Wählen Sie die **Herkunft der Audience** und legen Sie sie auf **Direkt von Kunden** klicken **Nächste**.

![Demo](./images/aud10.png)

Klicken Sie auf **Fertigstellen**.

![Demo](./images/aud11.png)

Ihr Segment ist jetzt mit den benutzerdefinierten Zielgruppen von Facebook verbunden. Verwenden wir jetzt dasselbe Segment in Adobe Journey Optimizer.

## 4.6.4 Segment in Adobe Journey Optimizer verwenden

Klicken Sie in Adobe Experience Platform auf **Journey Optimizer** und klicken Sie dann im Menü links auf **Journey** und beginnen Sie mit der Erstellung einer Journey durch Klicken auf **Journey erstellen**.

![Demo](./images/aud20.png)

![Demo](./images/aud21.png)

![Demo](./images/aud22.png)

Dann im Menü links unter **Veranstaltungen** auswählen **Segmentqualifikation** und ziehen Sie es auf die Journey:

![Demo](./images/aud23.png)

Klicken Sie unter Segment auf **Bearbeiten** um ein Segment auszuwählen:

![Demo](./images/aud24.png)

Wählen Sie die zuvor in CJA erstellte Zielgruppe aus und klicken Sie auf  **Speichern**.

![Demo](./images/aud25.png)

Bereit! Von hier aus können Sie eine Journey für Kunden erstellen, die sich für dieses Segment qualifizieren.

[Zurück zum Benutzerfluss 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)
