---
title: Adobe Journey Optimizer - Personalisierung in einer E-Mail-Nachricht anwenden
description: In dieser Übung wird erläutert, wie die Segmentpersonalisierung in E-Mail-Inhalten verwendet wird
kt: 5342
doc-type: tutorial
exl-id: a1ad649e-d0c4-4e87-b784-1e2d99f34a2e
source-git-commit: 203590e3289d2e5342085bf8b6b4e3cd11859539
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 10%

---

# 3.4.3 Anwenden der segmentbasierten Personalisierung in einer E-Mail-Nachricht

Melden Sie sich bei Adobe Experience Cloud an, indem Sie zu [Adobe Experience Cloud wechseln](https://experience.adobe.com). Auf **Adobe Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

Sie werden zur Ansicht **Startseite** in Journey Optimizer weitergeleitet. Bevor Sie fortfahren, müssen Sie eine **Sandbox“**. Die auszuwählende Sandbox hat den Namen ``--aepTenantId--``.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.4.3.1 segmentbasierte Personalisierung

In dieser Übung verbessern Sie die in der vorherigen Übung erstellte Newsletter-E-Mail-Nachricht mit einem personalisierten Text, der auf der Segmentzugehörigkeit basiert.

Navigieren Sie zu **Kampagnen**. Suchen Sie die Newsletter-Journey, die Sie in der vorherigen Übung erstellt haben. Suchen Sie nach `--aepUserLdap-- - CitiSignal Newsletter`. Klicken Sie mit der rechten Maustaste auf die 3 Punkte **…** und klicken Sie auf **Duplizieren**.

![Journey Optimizer](./images/sbp1.png)

Sie werden es dann sehen. Verwenden Sie dies für den **Titel**: `--aepUserLdap-- - CitiSignal Newsletter (SBP)`. Klicken Sie auf **Duplizieren**.

![Journey Optimizer](./images/sbp2.png)

Klicken Sie auf die duplizierte Kampagne, um sie zu öffnen.

![Journey Optimizer](./images/sbp3.png)

Klicken Sie **Bearbeiten**, um den Inhalt zu ändern.

![Journey Optimizer](./images/sbp3a.png)

Klicken Sie **E-Mail-Textkörper bearbeiten**.

![Journey Optimizer](./images/sbp4.png)

Sie werden es dann sehen.

![Journey Optimizer](./images/sbp5.png)

Öffnen Sie **Inhaltskomponenten** und ziehen Sie eine **1:1-Spalte** über das AirPods-Angebot.

![Journey Optimizer](./images/sbp6.png)

Ziehen Sie eine **Text**-Komponente per Drag-and-Drop in diese 1:1-Spalte.

![Journey Optimizer](./images/sbp6a.png)

Wählen Sie den gesamten Standardtext aus und löschen Sie ihn. Klicken Sie dann auf die **Personalisierung hinzufügen** in der Symbolleiste.

![Journey Optimizer](./images/sbp7.png)

Sie werden es dann sehen. Klicken Sie im linken Menü auf **Zielgruppen**.

![Journey Optimizer](./images/seg1.png)

Wählen Sie die `--aepUserLdap-- - Interest in Plans` aus und klicken Sie auf das Symbol **+** , um sie zur Arbeitsfläche hinzuzufügen.

![Journey Optimizer](./images/seg3.png)

Sie sollten dann die erste Zeile so lassen, wie sie ist, und Zeile 2 und 3 durch diesen Code ersetzen:

``
    PS: It may be a good idea to check if your plan still meets your needs! Click here to be contacted by one of our experts!
{%else%}
    PS: Thanks for taking the time to read our newsletter. Here is a 10% promo code to use on the website: NEWSLETTER10
{%/if%}
``

Dann hast du das hier. Klicken Sie auf **Speichern**.

![Journey Optimizer](./images/seg4.png)

Ändern Sie die Textausrichtung in **Ausrichtung zentrieren**.

![Journey Optimizer](./images/sbp9.png)

Sie können diese Nachricht jetzt speichern, indem Sie auf die **Speichern**-Schaltfläche oben rechts klicken. Klicken Sie dann **Pfeil** neben dem Betreffzeilentext in der oberen linken Ecke.

![Journey Optimizer](./images/sbp9a.png)

Klicken Sie auf **Zum Aktivieren überprüfen**.

![Journey Optimizer](./images/oc79afff.png)

Klicken Sie **Aktivieren**.

![Journey Optimizer](./images/oc79bfff.png)

Ihr Newsletter mit segmentbasierter Personalisierung ist jetzt veröffentlicht. Ihre Newsletter-E-Mail-Nachricht wird auf der Grundlage Ihres Zeitplans gesendet und Ihr Journey wird gestoppt, sobald die letzte E-Mail gesendet wurde.

Wenn Sie sich für das verwendete Segment qualifizieren, wird dies in der E-Mail angezeigt, die Sie erhalten:

![Journey Optimizer](./images/sbp20fff.png)

Du hast diese Übung beendet.

## Nächste Schritte

Wechseln Sie zu [Zusammenfassung und Vorteile](./summary.md){target="_blank"}

Zurück zu [Adobe Journey Optimizer](journeyoptimizer.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
